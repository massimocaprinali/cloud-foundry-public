---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}


# Configure bound services
{: #auto_config}

You can bind various services to your Liberty for Java app. Services can be container-managed, app-managed, or both, depending on what the developer wants.

An app-managed service is a service that is managed entirely by the app, without any assistance from Liberty. The app typically reads VCAP_SERVICES to obtain information about the bound service and accesses the service directly. The app provides all necessary client access code. There is no dependency on Liberty features or the `server.xml` file configuration. The Liberty buildpack automatic configuration does not apply to services of this type.

A container-managed service is a service that is managed by the Liberty runtime. In some cases, the app might look up the bound service in JNDI, while in others the service is used directly by Liberty itself. The Liberty buildpack reads VCAP_SERVICES to obtain information about the bound services. For each container-managed service, the buildpack performs three functions.

* Generates [cloud variables](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#accessing_info_of_bound_services) for the bound service.
* Installs Liberty features and client access codes that are required to access the bound service.
* Generates or updates `server.xml` file stanzas that are required by the service.

This process is referred to as automatic configuration.

The Liberty buildpack provides automatic configuration for the following service types:

* [ClearDB MySQL Database](https://w2.cleardb.net/developers/){: external}
* [{{site.data.keyword.cloudant}}](/docs/Cloudant?topic=Cloudant-getting-started-with-cloudant)
* [{{site.data.keyword.composeForMongoDB}}](/docs/ComposeForMongoDB?topic=ComposeForMongoDB-about)
* [{{site.data.keyword.composeForMySQL}}](/docs/ComposeForMySQL?topic=ComposeForMySQL-about)
* [{{site.data.keyword.composeForPostgreSQL}}](/docs/ComposeForPostgreSQL?topic=ComposeForPostgreSQL-about)
* [{{site.data.keyword.dashdbshort}}](/docs/Db2whc?topic=Db2whc-getting-started)
* [ElephantSQL](/docs/ElephantSQL)
* [{{site.data.keyword.ssoshort}}](/docs/appid?topic=appid-cd-sso)

The Compose services can be either container managed or app managed. By default, the Liberty buildpack assumes that these services are container managed, and automatically configures them. If you want the app to manage the service, you can opt out of automatic configuration for the service by setting the `services_autoconfig_excludes` environment variable. For more information, see [Opting out of service auto-configuration](#opting_out).

## Installation of Liberty features and client access code
{: #installation_of_liberty_features}

When you bind to a container-managed service, the service might require Liberty features to be configured in the `featureManager` stanza in the `server.xml` file. The Liberty buildpack updates the `featureManager` stanza and installs the required supporting binary files. If the service requires client driver `JAR` files, the files are downloaded to a well-known location in the Liberty installation.

See the [Opting out of service auto-configuration](#opting_out) section for more details about the bound service types.

## Generating or updating `server.xml` configuration stanzas
{: #generating_or_updating_serverxml}

The Liberty buildpack can automatically generate or update configuration stanzas in your `server.xml` file when you push a stand-alone app, depending on how your app is bound to services and whether you have an existing `server.xml` file.

When you push a stand-alone app, the Liberty buildpack generates the `server.xml` configuration stanza, as described in [Options for Pushing Liberty Apps](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing), to {{site.data.keyword.cloud_notm}}.

When you push a stand-alone app and bind to container-managed services, the Liberty buildpack generates the necessary `server.xml` stanzas for the bound services.

When you provide a `server.xml` file and bind to container-managed services, the Liberty buildpack will either generate or update the configuration stanzas.

* If the provided `server.xml` file does not contain configuration stanzas for the bound services, Liberty generates the configuration for the bound services.
* If the provided `server.xml` file contains configuration stanzas for the bound services, Liberty updates the configuration for the bound services.

See the documentation for the bound service type for more details.

## Opting out of service auto-configuration
{: #opting_out}

In some cases, you might not want the Liberty buildpack to automatically configure the services that have been bound. Consider the following scenarios.

* My app uses `dashDB`, but I want the app to directly manage the connection to the database. The app contains the necessary client driver `JAR` file. I do not want the Liberty buildpack to automatically configure the `dashDB` service.
* I am providing a `server.xml` file and I provided the configuration stanzas for the `cloudant` instance because I require a non-standard datasource configuration. I do not want the Liberty buildpack to update my `server.xml` file, but I still require the Liberty buildpack to ensure that the appropriate supporting software is installed.

To opt out of automatic service configuration, use the services_autoconfig_excludes environment variable. You can include this environment variable in a manifest.yml or set it using the {{site.data.keyword.cloud_notm}} client.

You can opt out of automatic configuration of services on a per-service-type basis. You can choose to completely opt out (as in the `dashDB` scenario) or opt out of only the `server.xml` file configuration updates (as in the `cloudant` scenario). The value that you specify for the services_autoconfig_excludes environment variable is a string as shown below.

* The string can contain opt-out specifications for one or more services.
* The opt-out specification for a specific service is service_type=option, where:
    * The service_type is the label for the service as displayed in VCAP_SERVICES.
    * The option is either `all` or `config`.
* If the String contains an opt-out specification for more than one service, the individual opt-out specifications must be separated by a single white-space character.

See the following example of `services_autoconfig_excludes` string grammar:

```text
    Opt_out_string :: <service_type_specification[<delimiter>service_type_specification]*
    <service_type_specification> :: <service_type>=<option>
    <service_type> :: service type (service label as it appears in VCAP_SERVICES)
    <option> :: all | config
    <delimiter> :: one white space character
```
{: codeblock}

**Important**: The service type that you specify must match the services label as it appears in the VCAP_SERVICES environment variable. White space is not allowed.
**Important**: No white space is allowed within a `<service_type_specification>`. The only allowed use of white space is to separate multiple `<service_type_specification>` instances.

Use the **all** option to opt out of all automatic configuration actions for a service, as in the `dashDB` scenario above. Use the **config** option to opt out of only the configuration update actions as in the `cloudant` scenario above.

Here are sample opt-out specifications in a `manifest.yml` file for the `dashDB` and `cloudant` scenarios.

```yaml
    env:
      services_autoconfig_excludes: dashDB=all

    env:
      services_autoconfig_excludes: cloudant=config

    env:
      services_autoconfig_excludes: cloudant=config dashDB=all
```
{: codeblock}

Here are examples of how to set the `services_autoconfig_excludes` environment variable for the app `myapp` by using the command-line interface.

```text
    ibmcloud cf set-env myapp services_autoconfig_excludes cloudant=config
```
{: pre}

```text
    ibmcloud cf set-env myapp services_autoconfig_excludes "cloudant=config dashDB=all"
```
{: pre}

To find the *label* for a service in VCAP_SERVICES issue a command like the following example:

```text
    ibmcloud cf env myapp
```
{: pre}

The output includes text similar to the following, where you can see the `label` field with value `elephantsql`:

```text
   "elephantsql": [
   {
      "credentials": {
      "max_conns": "5",
      "uri":      "..."
   },
   "label": "elephantsql",

```
{: codeblock}

## Overriding service configuration
{: #override_service_config}

In some cases, you might want to override the default configuration for a service generated by automatic configuration.
You can use the `LBP_SERVICE_CONFIG_xxxx` environment variable to override a service configuration. See the following tables for complete environment variable names and example syntax to override them. For example, to override the default version of the `elephantSQL` service and set it to version 8.3.4., issue a command such as:

```text
ibmcloud cf set-env myapp LBP_SERVICE_CONFIG_POSTGRESQL "{driver: { version: 8.3.4.+ }}"
```
{: pre}

This table shows the mapping of **service_type** to **LBP_SERVICE_CONFIG_xxxx** environment variable names.

|service_type             | Environment Variable Name |
|-------------------------|----------------------------------------|
|`Auto-Scaling`           | `LBP_SERVICE_CONFIG_AUTO-SCALING`|
|`cleardb`                | `LBP_SERVICE_CONFIG_MYSQL`|
|`cloudantNoSQLDB`        | `LBP_SERVICE_CONFIG_CLOUDANTNOSQLDB`|
|`compose-for-mongodb`    | `LBP_SERVICE_CONFIG_COMPOSE_MONGO`|
|`compose-for-mysql`      | `LBP_SERVICE_CONFIG_COMPOSE_MYSQL`|
|`compose-for-postgresql` | `LBP_SERVICE_CONFIG_COMPOSE_POSTGRESQL`|
|`elephantsql`            | `LBP_SERVICE_CONFIG_POSTGRESQL`|
|`SingleSignOn`           | `LBP_SERVICE_CONFIG_SINGLESIGNON`|

The table that follows shows syntax for overriding some service configuration options:

|Environment Variable Name               | Configuration Syntax |
|----------------------------------------|-----------------------------------------------------------|
|`LBP_SERVICE_CONFIG_MYSQL`              | `"{driver: { version: x.y.z }, connection_pool_size: 15}"` |
|`LBP_SERVICE_CONFIG_COMPOSE_MYSQL`      | `"{driver: { version: x.y.z }, connection_pool_size: 15}"` |
|`LBP_SERVICE_CONFIG_COMPOSE_POSTGRESQL` | `"{driver: { version: x.y.z }}"` |
|`LBP_SERVICE_CONFIG_POSTGRESQL`         | `"{driver: { version: x.y.z }}"` |



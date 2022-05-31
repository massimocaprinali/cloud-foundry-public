---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Environment variables
{: #environment_variables}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Environment variables supported by Liberty for Java.


Environment Variable Name              | Description
---------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
`BLUEMIX_APP_MGMT_ENABLE`              | Enable [App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management).
`BLUEMIX_APP_MGMT_INSTALL`             | Install [App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management).
`IBM_LIBERTY_MONTHLY`                  | Enable [Liberty monthly release runtime](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_monthly_runtime).
`JAVA_OPTS`                            | Set [Java&trade; options](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre).
`JBP_CONFIG_DYNATRACEAPPMONAGENT`      | Configure the [Dynatrace agent location information](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_dynatrace).
`JBP_CONFIG_IBMJDK`                    | Configure the [{{site.data.keyword.IBM}} JRE version](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre).
`JBP_CONFIG_LIBERTY`                   | Configure Liberty runtime options that include [features for WAR or EAR files](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#stand_alone_apps).
`JBP_CONFIG_OPENJDK`                   | Configure the [OpenJDK version](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre).
`JBP_CONFIG_OPENJ9`                    | Configure the [OpenJ9 version](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre).
`JBP_CONFIG_SPRINGAUTORECONFIGURATION` | Disable the [Spring Auto-Reconfiguration framework](https://github.com/cloudfoundry/java-buildpack/blob/main/docs/framework-spring_auto_reconfiguration.md){: external}. To disable, set value to enabled: false.
`JBP_LOG_LEVEL`                        | Set logging level of the buildpack. Values include `DEBUG`, `INFO` (default), `WARN`, `ERROR`, or `FATAL`.
`JVM`                                  | Select the [JRE type](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre).
`JVM_ARGS`                             | Set the [JVM arguments](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre).
`LBP_SERVICE_CONFIG_xxxx`              | [Override service configuration](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config#override_service_config).
`HTTP_PROXY`                           | Set proxy server information.
`HTTPS_PROXY`                          | Set proxy server information.
`services_autoconfig_excludes`         | Disable service [auto-configuration.](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config#opting_out).
{: caption="Table 1. Environment variables available for Liberty for Java" caption-side="top"}

## Disabled attributes in the Liberty for Java buildpack

Some attributes are automatically disabled by the Liberty buildpack and cannot be changed. The following environment variables and attributes are disabled.

### Disabled attribute table


Disabled attribute         | Element
---------------------------|-----------------
`host`                     | `httpEndpoint`
`httpPort`                 | `httpEndpoint`
`trustHostHeaderPort`      | `webContainer`
`andextractHostHeaderPort` | `webContainer`
`logDirectory`             | `logging`
`consoleLogLevel`          | `logging`
`enableWelcomePage`        | `httpDispatcher`
{: caption="Table 2. Attributes disabled by Liberty for Java" caption-side="top"}



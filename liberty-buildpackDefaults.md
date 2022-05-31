---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Liberty for Java buildpack defaults
{: #buildpack_defauts}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

The Liberty buildpack is updated frequently in {{site.data.keyword.cloud}}. Each release might contain security fixes or feature enhancements.

The buildpack has default values for settings such as the Java version or Liberty feature set for WAR or EAR apps. Some of the default values might change between the buildpack release, which might adversely impact the app. To prevent the app from being affected by the change in buildpack defaults, take steps to configure your app to avoid relying on the buildpack defaults.

## Liberty versions
{: #liberty_versions}

The buildpack provides two versions of the Liberty runtime:
1. A long-term stable release
    * It is the default Liberty runtime.
    * It does not provide any [beta features](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_beta_features).
    * Typically updated on a quarterly basis.

2. The monthly release
    * It must be explicitly enabled by setting the **JBP_CONFIG_LIBERTY** environment variable with the **"version: +"** value and the **IBM_LIBERTY_MONTHLY** environment variable with **true**.
    * It provides [monthly features](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_monthly_runtime).
    * Typically updated every 4 weeks.

## Liberty features
{: #default_liberty_features}

When you deploy WAR or EAR files, the buildpack provides a configuration for the app with a default set of Liberty features. Although rare, that default set of Liberty features might change between the buildpack releases. The change in the default feature set might adversely affect the app. There are options to ensure that the app is not affected by the change in the feature defaults.

* Set the JBP_CONFIG_LIBERTY environment variable to explicitly specify a list of enabled features for the app. For more information, see [Stand-alone Apps](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#stand_alone_apps).
* Deploy your app as a [server directory](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#server_directory) or a [packaged server](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#packaged_server). Provide a custom `server.xml` file that specifies the exact set of features that are needed by your app.

Apps that are deployed as a server directory or a packaged server are unaffected by the change in the Liberty features default.

## Java version
{: #java_version}

The buildpack provides a default JRE for the app. The major or minor version of the JRE might change between the buildpack releases. The minor version of the JRE might be updated frequently while the major version is rarely updated. The change in the major version of the JRE might adversely affect the app.

To ensure that the app is not affected by the major version change, set the environment variable with the appropriate JRE version as described in [Customizing the JRE](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre). For best results, adopt Java 8 for your apps.



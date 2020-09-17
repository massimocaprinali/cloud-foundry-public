---

copyright:
  years: 2015, 2020
lastupdated: "2020-09-16"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{:beta: .beta}
{:codeblock: .codeblock}
{:deprecated: .deprecated}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:gif: data-image-type='gif'}
{:help: data-hd-content-type='help'}
{:important: .important}
{:java: data-hd-programlang="java"}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note: .note}
{:pre: .pre}
{:preview: .preview}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:support: data-reuse='support'}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}


# Environment variables
{: #environment_variables}

Environment variables supported by Liberty for Java.


Environment Variable Name              | Description
---------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
`BLUEMIX_APP_MGMT_ENABLE`              | Enable [App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management)
`BLUEMIX_APP_MGMT_INSTALL`             | Install [App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management)
`IBM_LIBERTY_MONTHLY`                  | Enable [Liberty monthly release runtime/](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_monthly_runtime)
`JAVA_OPTS`                            | Set [Java options](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)
`JBP_CONFIG_DYNATRACEAPPMONAGENT`      | Configure the [Dynatrace agent location information](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_dynatrace)
`JBP_CONFIG_IBMJDK`                    | Configure the [{{site.data.keyword.IBM}} JRE version](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)
`JBP_CONFIG_LIBERTY`                   | Configure a variety of Liberty runtime options including [features for WAR or EAR files](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#stand_alone_apps)
`JBP_CONFIG_OPENJDK`                   | Configure the [OpenJDK version](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)
`JBP_CONFIG_OPENJ9`                    | Configure the [OpenJ9 version](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)
`JBP_CONFIG_SPRINGAUTORECONFIGURATION` | Disable the [Spring Auto-Reconfiguration framework](https://github.com/cloudfoundry/java-buildpack/blob/main/docs/framework-spring_auto_reconfiguration.md){: external}. To disable, set value to enabled: false.
`JBP_LOG_LEVEL`                        | Set logging level of the buildpack. Possible values: `DEBUG`, `INFO` (default), `WARN`, `ERROR`, or `FATAL`
`JVM`                                  | Select the [JRE type](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)
`JVM_ARGS`                             | Set the [JVM arguments](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)
`LBP_SERVICE_CONFIG_xxxx`              | [Override service configuration](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config#override_service_config)
`HTTP_PROXY`                           | Set proxy server information
`HTTPS_PROXY`                          | Set proxy server information
`services_autoconfig_excludes`         | Disable service [auto-configuration.](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config#opting_out)

{: caption="Table 1. Environment variables available for Liberty for Java" caption-side="top"}

## Disabled attributes in the Liberty for Java buildpack

There are some attributes that are automatically disabled by the Liberty buildpack, that you cannot override. The following environment variables and attributes are disabled.

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

{: caption="Table 1. Attributes disabled by Liberty for Java" caption-side="top"}



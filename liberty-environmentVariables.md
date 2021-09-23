---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-23"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:audio: .audio}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: .ph data-hd-programlang='c#'}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: #curl .ph data-hd-programlang='curl'}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: .external target="_blank"}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: #java .ph data-hd-programlang='java'}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:middle: .ph data-hd-position='middle'}
{:navgroup: .navgroup}
{:new_window: target="_blank"}
{:node: .ph data-hd-programlang='node'}
{:note: .note}
{:objectc: .ph data-hd-programlang='Objective C'}
{:objectc: data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: .ph data-hd-programlang='PHP'}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:release-note: data-hd-content-type='release-note'}
{:right: .ph data-hd-position='right'}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:step: data-tutorial-type='step'} 
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:topicgroup: .topicgroup}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Environment variables
{: #environment_variables}

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



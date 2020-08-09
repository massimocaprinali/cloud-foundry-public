---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-09"

keywords: cloud foundry

subcollection: cloud-foundry-public



---



{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
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
{:new_window: target="_blank"}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
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
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vb.net: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Environment variables
{: #environment_variables}

Environment variables supported by Liberty for Java.

<table>
<tr>
<th align="left">Environment Variable Name</th>
<th align="left">Description</th>
</tr>

<tr>
<td>BLUEMIX_APP_MGMT_ENABLE</td>
<td>Enable [App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management)</td>
</tr>

<tr>
<td>BLUEMIX_APP_MGMT_INSTALL</td>
<td>Install [App Management utilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management)</td>
</tr>

<tr>
<td>IBM_LIBERTY_MONTHLY</td>
<td>Enable [Liberty monthly release runtime/](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_monthly_runtime)</td>
</tr>

<tr>
<td>JAVA_OPTS</td>
<td>Set [Java options](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)</td>
</tr>

<tr>
<td>JBP_CONFIG_DYNATRACEAPPMONAGENT</td>
<td>Configure the [Dynatrace agent location information](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_dynatrace)</td>
</tr>

<tr>
<td>JBP_CONFIG_IBMJDK </td>
<td>Configure the [IBM JRE version](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)</td>
</tr>

<tr>
<td>JBP_CONFIG_LIBERTY</td>
<td>Configure a variety of Liberty runtime options including [features for WAR or EAR files](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#stand_alone_apps)</td>
</tr>

<tr>
<td>JBP_CONFIG_OPENJDK</td>
<td>Configure the [OpenJDK version](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)</td>
</tr>

<tr>
<td>JBP_CONFIG_OPENJ9</td>
<td>Configure the [OpenJ9 version](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)</td>
</tr>

<tr>
<td>JBP_CONFIG_SPRINGAUTORECONFIGURATION </td>
<td>Disable the [Spring Auto-Reconfiguration framework](https://github.com/cloudfoundry/java-buildpack/blob/master/docs/framework-spring_auto_reconfiguration.md). To disable, set value to enabled: false. </td>
</tr>

<tr>
<td>JBP_LOG_LEVEL</td>
<td>Set logging level of the buildpack. Possible values: <b>DEBUG</b>, <b>INFO</b> (default), <b>WARN</b>, <b>ERROR</b>, or <b>FATAL</b></td>
</tr>

<tr>
<td>JVM</td>
<td>Select the [JRE type](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)</td>
</tr>

<tr>
<td>JVM_ARGS</td>
<td>Set the [JVM arguments](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre)</td>
</tr>

<tr>
<td>LBP_SERVICE_CONFIG_xxxx</td>
<td>[Override service configuration](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config#override_service_config)</td>
</tr>

<tr>
<td>HTTP_PROXY</td>
<td>Set proxy server information</td>
</tr>

<tr>
<td>HTTPS_PROXY</td>
<td>Set proxy server information</td>
</tr>

<tr>
<td>services_autoconfig_excludes</td>
<td>Disable service [auto-configuration.](/docs/cloud-foundry-public?topic=cloud-foundry-public-auto_config#opting_out)</td>
</tr>
</table>
{: caption="Table 1. Environment variables available for Liberty for Java" caption-side="top"}

## Disabled attributes in the Liberty for Java buildpack

There are some attributes that are automatically disabled by the Liberty buildpack, that you cannot override. The following environment variables and attributes are disabled.

### Disabled attribute table

<table>
<tr>
<th>Disabled attribute </th>
<th>Element</th>
</tr>

<tr>
<td>host</td>
<td>httpEndpoint</td>
</tr>

<tr>
<td>httpPort</td>
<td>httpEndpoint</td>
</tr>

<tr>
<td>trustHostHeaderPort</td>
<td>webContainer</td>
</tr>

<tr>
<td>andextractHostHeaderPort</td>
<td>webContainer</td>
</tr>

<tr>
<td>logDirectory</td>
<td>logging</td>
</tr>

<tr>
<td>consoleLogLevel</td>
<td>logging</td>
</tr>

<tr>
<td>enableWelcomePage</td>
<td>httpDispatcher</td>
</tr>
</table>
{: caption="Table 1. Attributes disabled by Liberty for Java" caption-side="top"}



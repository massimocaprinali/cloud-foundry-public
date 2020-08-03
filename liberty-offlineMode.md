---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-03"

keywords: cloud foundry



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


# Use the offline mode for Liberty
{: #offline_mode}

When a Liberty application is pushed to {{site.data.keyword.cloud}}, the Liberty buildpack can access sites external to {{site.data.keyword.Bluemix_notm}}
to acquire artifacts required by the application.  The following are the external sites that the Liberty buildpack can access.  In [{{site.data.keyword.Bluemix_dedicated_notm}}](/docs/dedicated/index.html#dedicated) and
[{{site.data.keyword.Bluemix_local_notm}}](/docs/local/index.html#local) environments, these sites might need to be *whitelisted*.

* https://download.run.pivotal.io, and https://java-buildpack.cloudfoundry.org are used to access components for:
  * [AppDynamics agent ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.appdynamics.com/)
  * [MariaDB JDBC driver ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://mariadb.com/)
  * [New Relic agent](/docs/runtimes/liberty/monitoring?topic=liberty-new_relic)
  * [OpenJDK](/docs/cloud-foundry?topic=cloud-foundry-customizing_jre#OpenJDK)
  * [PostgreSQL JDBC driver ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.postgresql.org)
* https://dl.zeroturnaround.com/jrebel/ is used to access components for [JRebel ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://zeroturnaround.com/software/jrebel/).
* https://download.ruxit.com/agent/paas/cloudfoundry/java is used to access components for [Dynatrace Ruxit agent](dynatrace.html).
* http://downloads.dynatracesaas.com/cloudfoundry/buildpack/java/  is used to access the [Dynatrace agent](dynatrace.html).

## Working with a proxy
{: #liberty-working_with_proxy}

In some environments, such as [{{site.data.keyword.Bluemix_dedicated_notm}}](/docs/dedicated/index.html#dedicated) and
[{{site.data.keyword.Bluemix_local_notm}}](/docs/local/index.html#local), a proxy can be configured. See
[Working with a proxy](/docs/cloud-foundry?topic=cloud-foundry-working_with_proxy) for more details.



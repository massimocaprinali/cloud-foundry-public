---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-07"

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



# Dependencies on other services
{: #dependencies}

{{site.data.keyword.ibmcf_full}} uses several services.  How {{site.data.keyword.ibmcf_notm}} connects to these services and how they are used depends on the service. 

|Service name|Description|
|---------|--------------------|
|{{site.data.keyword.at_short}}|{{site.data.keyword.ibmcf_notm}} integrates with {{site.data.keyword.at_short}} to forward workspace audit events to the {{site.data.keyword.at_short}} service instance that is set up and owned by the {{site.data.keyword.ibmcf_notm}} user. For more information, see [{{site.data.keyword.at_full_notm}} events](/docs/cloud-foundry-public?topic=cloud-foundry-public-at-events). Additionally, the {{site.data.keyword.ibmcf_notm}} service team uses {{site.data.keyword.at_short}} to monitor service-internal audit events.|
|Business Support Service (BSS) for {{site.data.keyword.cloud_notm}}| The BSS component is used to access information about the {{site.data.keyword.cloud_notm}} account, service subscription, service usage, and billing.|
|{{site.data.keyword.IBM_notm}} DataPower Gateway|This service is used to provide the global load balancer and firewall for {{site.data.keyword.ibmcf_notm}} in a region.|
|Identity and Access Management (IAM)| To authenticate requests to the service and authorize user actions, {{site.data.keyword.ibmcf_notm}} implements service access roles in Identity and Access Management (IAM). For more information about required IAM permissions to work with the service, see [Managing Cloud Foundry access](/docs/cloud-foundry-public?topic=account-mngcf).|
|{{site.data.keyword.la_full_notm}}|{{site.data.keyword.ibmcf_notm}} sends service logs to {{site.data.keyword.la_full_notm}}. These logs are monitored and analyzed by the {{site.data.keyword.ibmcf_notm}} service team to detect service issues and malicious activities.|
|{{site.data.keyword.cos_full_notm}}|This service is used to store data used by {{site.data.keyword.ibmcf_notm}}; for example, from an `ibmcloud cf push` command. All data is encrypted by using [Server-Side Encryption with Key Protect](/docs/cloud-object-storage?topic=cloud-object-storage-encryption) in transit and at rest.|




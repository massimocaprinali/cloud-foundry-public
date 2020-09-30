---

copyright:
  years: 2015, 2020
lastupdated: "2020-09-30"

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



# Dependencies to other services
{: #dependencies}

{{site.data.keyword.ibmcf_full}} uses several services.  How {{site.data.keyword.ibmcf_notm}} connects to these services and how they are used depends on the service. 

|Service name|Description|
|---------|--------------------|
|{{site.data.keyword.at_short}}|{{site.data.keyword.ibmcf_notm}} integrates with {{site.data.keyword.cloudaccesstrailshort}} to forward workspace audit events to the {{site.data.keyword.cloudaccesstrailshort}} service instance that is set up and owned by the {{site.data.keyword.ibmcf_notm}} user. For more information, see [IBM Cloud Activity Tracker with LogDNA events](/docs/cloud-foundry-public?topic=cloud-foundry-public-at-events). Additionally, the {{site.data.keyword.ibmcf_notm}} service team uses {{site.data.keyword.cloudaccesstrailshort}} to monitor service-internal audit events.|
|Akamai |Akamai provides intrusion and Denial-of-Service (DDOS) protection, as well as other security services, for {{site.data.keyword.ibmcf_notm}}.|
|Business Support Service for {{site.data.keyword.cloud_notm}} (BSS)| The BSS component is used to access information about the {{site.data.keyword.cloud_notm}} account, service subscription, service usage, and billing.|
|Certificate Manager|This service is used to store and manage the TLS certificates for the {{site.data.keyword.ibmcf_notm}} domains.|
|{{site.data.keyword.cloud_notm}} Command Line (CLI)|When {{site.data.keyword.ibmcf_notm}} runs CLI commands, the service connects to the service API endpoint over the public service endpoint.|
|{{site.data.keyword.IBM_notm}} DataPower Gateway|This service is used to provide the global load balancer and firewall for {{site.data.keyword.ibmcf_notm}} in a region.|
|Domain Name System (DNS) |{{site.data.keyword.ibmcf_notm}} uses DNS to allow users to connect to apps using Internet domain names and searchable URLs rather than numerical Internet protocol addresses. |
|{{site.data.keyword.cloud_notm}} Infrastructure (IaaS)|The IaaS service is used to provision and update classic {{site.data.keyword.cloud_notm}} infrastructure resources that are used by {{site.data.keyword.ibmcf_notm}}.|
|Identity and Access Management (IAM)| To authenticate requests to the service and authorize user actions, {{site.data.keyword.ibmcf_notm}} implements service access roles in Identity and Access Management (IAM). For more information about required IAM permissions to work with the service, see [Managing Cloud Foundry access](/docs/cloud-foundry-public?topic=account-mngcf).|
|{{site.data.keyword.loganalysisshort}} with LogDNA|{{site.data.keyword.ibmcf_notm}} sends service logs to {{site.data.keyword.loganalysisfull_notm}}. These logs are monitored and analyzed by the {{site.data.keyword.ibmcf_notm}} service team to detect service issues and malicious activities.|
|Messages for RabbitMQ|RabbitMQ is used to synchronize {{site.data.keyword.ibmcf_notm}} user records across {{site.data.keyword.ibmcf_notm}} locations.|
|Object Storage (COS)|This service is used to store data used by {{site.data.keyword.ibmcf_notm}}; for example, from an `ibmcloud cf push` command. All data is encrypted by using [Server-Side Encryption with Key Protect](/docs/cloud-object-storage?topic=cloud-object-storage-encryption#encryption-kp) in transit and at rest.|


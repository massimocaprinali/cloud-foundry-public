---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}


# Dependencies on other services
{: #dependencies}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

{{site.data.keyword.ibmcf_full}} uses several services.  How {{site.data.keyword.ibmcf_notm}} connects to these services and how they are used depends on the service. 

|Service name|Description|
|---------|--------------------|
|{{site.data.keyword.at_short}}|{{site.data.keyword.ibmcf_notm}} integrates with {{site.data.keyword.at_short}} to forward workspace audit events to the {{site.data.keyword.at_short}} service instance that is set up and owned by the {{site.data.keyword.ibmcf_notm}} user. For more information, see [{{site.data.keyword.at_full_notm}} events](/docs/cloud-foundry-public?topic=cloud-foundry-public-at-events). Additionally, the {{site.data.keyword.ibmcf_notm}} service team uses {{site.data.keyword.at_short}} to monitor service-internal audit events.|
|Business Support Service (BSS) for {{site.data.keyword.cloud_notm}}| The BSS component is used to access information about the {{site.data.keyword.cloud_notm}} account, service subscription, service usage, and billing.|
|{{site.data.keyword.IBM_notm}} DataPower Gateway|This service is used to provide the global load balancer and firewall for {{site.data.keyword.ibmcf_notm}} in a region.|
|Identity and Access Management (IAM)| To authenticate requests to the service and authorize user actions, {{site.data.keyword.ibmcf_notm}} implements service access roles in Identity and Access Management (IAM). For more information about required IAM permissions to work with the service, see [Managing Cloud Foundry access](/docs/cloud-foundry-public?topic=account-mngcf).|
|{{site.data.keyword.la_full_notm}}|{{site.data.keyword.ibmcf_notm}} sends service logs to {{site.data.keyword.la_full_notm}}. These logs are monitored and analyzed by the {{site.data.keyword.ibmcf_notm}} service team to detect service issues and malicious activities.|
|{{site.data.keyword.cos_full_notm}}|This service is used to store data used by {{site.data.keyword.ibmcf_notm}}; for example, from an `ibmcloud cf push` command. All data is encrypted by using [Server-Side Encryption with Key Protect](/docs/cloud-object-storage?topic=cloud-object-storage-encryption) in transit and at rest.|


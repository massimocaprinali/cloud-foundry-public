---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Run the Node.js app locally
{: #hints}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Set a port number to run your Node.js app locally without causing conflicts when you run it on {{site.data.keyword.cloud}}.
{: shortdesc}

When the app is running on {{site.data.keyword.cloud_notm}}, the PORT environment variable is allocated by Cloud Foundry. However, when the app is running locally, PORT is not defined, so you can define the port for your app. To avoid conflicts, define the port that your app listens to locally something different than the port used by {{site.data.keyword.cloud_notm}}.

In the following example for a **js** file, **3000** is used as the port number. By using **3000**, you can run the app locally for testing purposes and on {{site.data.keyword.cloud_notm}} without making changes.

```text
var port = (process.env.PORT || 3000);
```
{: codeblock}



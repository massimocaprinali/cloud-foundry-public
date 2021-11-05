---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Run the Node.js app locally
{: #hints}

Set a port number to run your Node.js app locally without causing conflicts when you run it on {{site.data.keyword.cloud}}.
{: shortdesc}

When the app is running on {{site.data.keyword.cloud_notm}}, the PORT environment variable is allocated by Cloud Foundry. However, when the app is running locally, PORT is not defined, so you can define the port for your app. To avoid conflicts, define the port that your app listens to locally something different than the port used by {{site.data.keyword.cloud_notm}}.

In the following example for a **js** file, **3000** is used as the port number. By using **3000**, you can run the app locally for testing purposes and on {{site.data.keyword.cloud_notm}} without making changes.

```text
var port = (process.env.PORT || 3000);
```
{: codeblock}



---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-31"

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


# Run the Node.js app locally
{: #hints}

Set a port number to run your Node.js app locally without causing conflicts when you run it on {{site.data.keyword.cloud}}.
{: shortdesc}

When the app is running on {{site.data.keyword.cloud_notm}}, the PORT environment variable is allocated by Cloud Foundry. However, when the app is running locally, PORT is not defined, so you can define the port for your app. To avoid conflicts, define the port that your app listens to locally something different than the port used by {{site.data.keyword.cloud_notm}}.

In the following example for a **js** file, **3000** is used as the port number. By using **3000**, you can run the app locally for testing purposes and on {{site.data.keyword.cloud_notm}} without making changes.

```
var port = (process.env.PORT || 3000);
```
{: codeblock}



---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-14"

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


# SDK for Node.js
{: #nodejs_runtime}

The Node.js runtime on {{site.data.keyword.cloud}} is powered by the sdk-for-nodejs buildpack.
The sdk-for-nodejs buildpack provides a complete runtime environment for Node.js apps.
{: shortdesc}

The sdk-for-nodejs buildpack is used when the application contains a **package.json** file in the root directory.

The application must listen on the port that is assigned to it through the PORT environment variable.
```
var port = (process.env.PORT || 3000);
```
{: codeblock}

## Starter application
{: #nodejs-starter_application}

{{site.data.keyword.cloud_notm}} provides a Node.js starter applications.  The Node.js starter application is a simple Node.js app that provides a template that you can use for your app. You can experiment with the starter app, and make and push changes to the {{site.data.keyword.cloud_notm}} environment.

## App Management (deprecated)
{: #nodejs-app_management}

**Deprecation Note**:  As of version 4.0, the SDK for Node.js buildpack no longer supports App Management.    

{{site.data.keyword.cloud_notm}} provides a number of utilities for managing and debugging your Node.js app.  See [App Management](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) for complete details.  



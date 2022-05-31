---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# SDK for Node.js
{: #nodejs_runtime}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

The Node.js runtime on {{site.data.keyword.cloud}} is powered by the `sdk-for-nodejs` buildpack.
The `sdk-for-nodejs` buildpack provides a complete runtime environment for Node.js apps.
{: shortdesc}

The `sdk-for-nodejs` buildpack is used when the app contains a **package.json** file in the root directory.

The app must listen on the port that is assigned to it through the PORT environment variable.

```text
var port = (process.env.PORT || 3000);
```
{: codeblock}

## Starter app
{: #nodejs-starter_app}

{{site.data.keyword.cloud_notm}} provides a Node.js starter apps.  The Node.js starter app is a simple Node.js app that provides a template that you can use for your app. You can experiment with the starter app, and make and push changes to the {{site.data.keyword.cloud_notm}} environment.

## App Management (deprecated)
{: #nodejs-app_management}

**Deprecation Note**:  As of version 4.0, the SDK for Node.js buildpack no longer supports App Management.    

{{site.data.keyword.cloud_notm}} provides a number of utilities for managing and debugging your Node.js app.  See [App Management](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management) for complete details.  



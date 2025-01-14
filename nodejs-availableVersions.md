---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Available versions
{: #available_versions}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

{{site.data.keyword.cloud}} provides all [the currently available Node.js runtimes](http://nodejs.org/dist/){: external}. Of the available runtimes, {{site.data.keyword.IBM_notm}} provides specific versions that contain enhancements and bug fixes. See [Latest updates to the Node.js buildpack](/docs/cloud-foundry-public?topic=cloud-foundry-public-nodejs-latest_updates) for more information about the supported versions.
{: shortdesc}

The {{site.data.keyword.IBM_notm}} Node.js buildpack caches the {{site.data.keyword.IBM_notm}} runtime versions. If you use {{site.data.keyword.IBM_notm}} SDK for Node.js runtime in your app, your app performs faster when you push it to {{site.data.keyword.cloud_notm}}.

## Specifying a version

* Use the **node** option in the **engines** section in the **package.json** file to specify the version of Node.js runtime that you want to run.

* If you need to specify a version of `npm` other than the version bundled with Node.js, use the `npm` option in the `engines` section in the `package.json` file.  

See the following example:

```text
{
  "name": "myapp",
  "description": "this is my app",
  "version": "0.1",
  "engines": {
     "node": "4.2.4",
     "npm": "3.10.10"
  }
}
```
{: codeblock}

**Note:** Always specify a node version in the `package.json` file. If a version is not specified, the latest node version is used.



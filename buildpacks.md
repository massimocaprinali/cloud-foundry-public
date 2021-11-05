---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.ibmcf_notm}} buildpacks
{: #available_buildpacks}

{{site.data.keyword.ibmcf_full}} buildpacks provide the runtime support for apps in the {{site.data.keyword.ibmcf_notm}} environment. When you deploy an app to {{site.data.keyword.cloud}} using {{site.data.keyword.ibmcf_notm}}, {{site.data.keyword.ibmcf_notm}} starts a buildpack that supports your app type. {{site.data.keyword.cloud_notm}} provides Cloud Foundry buildpack support for Java EE, Node.js, ASP.Net, Swift, and other app types.
You can use the buildpacks included with {{site.data.keyword.cloud_notm}} to deploy apps and bind them to services.
{: shortdesc}

*  Cloud Foundry

    Cloud Foundry is an open source platform for app lifecycle automation.  {{site.data.keyword.ibmcf_notm}} is built on top of the open source Cloud Foundry platform as a service. Check out the [Cloud Foundry website](https://www.cloudfoundry.org/){: external} to learn more about the Cloud Foundry platform.

*  Cloud Foundry App

    A cloud foundry app or app, is any app intended to be instantiated by on one of the buildpacks provided by {{site.data.keyword.ibmcf_notm}}.

*  Buildpack

    A buildpack is a typically language specific package of software provided by {{site.data.keyword.ibmcf_notm}}. When an app is deployed to the {{site.data.keyword.cloud_notm}} a buildpack appropriate for the app is chosen. The buildpack provisions the runtime environment for the app.  You can see the set of buildpacks provided by {{site.data.keyword.ibmcf_notm}} by issuing the `ibmcloud cf buildpacks` command from the command line.

*  Runtime

    A runtime is the set of software components which provide the execution environment for an app.  The terms *runtime* and *buildpack* are sometimes used interchangeably.  When a buildpack has completed deploying an app the runtime environment is established.

*  Starter

    A starter is a simple app designed for a particular runtime. The starters provide templates or samples of the language and runtime specific app types. You can use a starter to begin development of more sophisticated apps.

*  Service

    A service is an {{site.data.keyword.cloud_notm}} provided facility which can be coupled with an app.



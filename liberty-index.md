---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Liberty for Java
{: #liberty_runtime}

Liberty for Java apps on {{site.data.keyword.cloud}} are powered by the liberty-for-java buildpack. The liberty-for-java buildpack provides a complete runtime environment for running Jakarta EE, Eclipse MicroProfile, Java EE, and OSGi apps on top of WebSphere Liberty. It supports popular frameworks like Spring and includes the {{site.data.keyword.IBM_notm}} JRE. Liberty enables rapid app development that is well suited to the cloud.
{: shortdesc}

## Detection
{: #liberty-detection}

The Liberty buildpack is used when the following kinds of apps are deployed:
* [`WAR` files](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#stand_alone_apps)
* [`EAR` files](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#stand_alone_apps)
* [Liberty server directory](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#server_directory)
* [Liberty packaged server](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#packaged_server)
* [Java main](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#java_main)
* [`Distzip`](https://github.com/cloudfoundry/ibm-websphere-liberty-buildpack/blob/master/docs/container-distZip.md){: external}

## Starter app
{: #liberty-starter_app}

{{site.data.keyword.cloud_notm}} provides several Liberty starter apps.  The Liberty starter apps are simple Liberty apps that provide a template that you can use. You can experiment with the starter apps, and make and push changes to the {{site.data.keyword.cloud_notm}} environment.



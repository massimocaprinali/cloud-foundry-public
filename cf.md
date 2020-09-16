---

copyright:
  years: 2015, 2020
lastupdated: "2020-09-16"

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

# How Cloud Foundry works with {{site.data.keyword.cloud_notm}}
{: #howwork}



When you deploy an app to Cloud Foundry, you must configure {{site.data.keyword.cloud}} with enough information to support the app.

* For a mobile app, {{site.data.keyword.cloud_notm}} contains an artifact that represents the mobile app's back end, such as the services that the mobile app uses to communicate with a server.
* For a web app, you must ensure that information about the runtime and framework is communicated to {{site.data.keyword.cloud_notm}}, so that {{site.data.keyword.cloud_notm}} can set up the appropriate execution environment to run the app.

Each execution environment, including both mobile and web, is isolated from the execution environment of other apps. The execution environments are isolated even though these apps are on the same physical machine. The following figure shows the basic flow of how Cloud Foundry manages the deployment of apps in {{site.data.keyword.cloud_notm}}:

![Deploying an app](images/deploy.png "An app developer deploys an app with a runtime and framework to {{site.data.keyword.cloud_notm}} where it is deployed to one or more Diego cell."){: caption="Figure 1. Deploying an app" caption-side="bottom"}

When you create an app and deploy it to Cloud Foundry, the {{site.data.keyword.cloud_notm}} environment determines an appropriate virtual server to send the app, or the artifacts that the app represents, to. For a mobile app, a mobile back-end projection is created on {{site.data.keyword.cloud_notm}}. Any code for the mobile app running in the cloud eventually runs in the {{site.data.keyword.cloud_notm}} environment. For a web app, the code running in the cloud is the app itself that the developer deploys to {{site.data.keyword.cloud_notm}}. The determination of the virtual server is based on several factors, including:

* The load already on the machine
* Runtimes or frameworks supported by that virtual server.

After a virtual server is chosen, an app manager on each virtual server installs the appropriate framework and runtime for the app. Then, the app can be deployed into that framework. When the deployment completes, the app artifacts are started.

The following figure shows the structure of a virtual server, also known as a Diego cell, that has multiple apps deployed to it:

![Design of a virtual server](images/container-diego.png "A Diego cell contains one or more containers. A container contains a framework, which contains a runtime, which contains an app. "){: caption="Figure 2. Design of a virtual server" caption-side="bottom"}

In each virtual server, an app manager communicates with the rest of the {{site.data.keyword.cloud_notm}} infrastructure, and manages the apps that are deployed to this virtual server. Each virtual server has containers to separate and protect apps. In each container, {{site.data.keyword.cloud_notm}} installs the appropriate framework and runtime that are required for each app.

When the app is deployed, if it has a web interface (as for a Java web app), or other REST-based services (such as mobile services exposed publicly to the mobile app), users of the app can communicate with it by using normal HTTP requests.

![Invoking an {{site.data.keyword.cloud_notm}} app](images/execute.png "The user of an app access the app by using a URL which then communicates to the app running in the Diego cell."){: caption="Figure 3. Invoking an {{site.data.keyword.cloud_notm}} app" caption-side="bottom"}

Each app can have one or more URLs associated with it, but they must all point to the {{site.data.keyword.cloud_notm}} endpoint. When a request comes in, {{site.data.keyword.cloud_notm}} examines the request, determines which app it is intended for, then selects an instance of the app to receive the request.


## Cloud Foundry architecture in {{site.data.keyword.cloud_notm}}
{: #architecture}

In general, you don't have to worry about the operating system and infrastructure layers when running apps on {{site.data.keyword.cloud_notm}} in Cloud Foundry. Layers such as root file systems and middleware components are abstracted so that you can focus on your app code. However, you can learn more about these layers if you need specifics on where your app is running.

See [Viewing {{site.data.keyword.cloud_notm}} infrastructure layers](/docs/cloud-foundry-public?topic=cloud-foundry-public-howwork#viewinfra) for details.

As a developer, you can interact with the {{site.data.keyword.cloud_notm}} infrastructure by using a browser-based user interface. You can also use a Cloud Foundry command line interface, called cf, to deploy web apps.

Clients--which can be mobile apps, apps that run externally, apps that are built on {{site.data.keyword.cloud_notm}}, or developers that are using browsers--interact with the {{site.data.keyword.cloud_notm}}-hosted apps. Clients use REST or HTTP APIs to route requests through {{site.data.keyword.cloud_notm}} to one of the app instances or the composite services.

The following figure shows the high-level Cloud Foundry architecture on {{site.data.keyword.cloud_notm}}.

![{{site.data.keyword.cloud_notm}} architecture](images/arch.png "A mobile or web app client accesses an app by using a REST HTTP API.  The REST API communicates with the Diego cell that is running the app.  The app can use {site.data.keyword.cloud_notm}} services.  The app developer can use either a browser or command line to deploy an app.  When deploying an app using a browser, the app developer uses the {site.data.keyword.cloud_notm}} console that uses a router to communicate with the VM running the Diego cell.  An app developer can also use a CLI that makes REST HTTP calls to the router to deploy apps to the Diego cell.  All these services run on on the provisioned infrastructure."){: caption="Figure 4. Cloud Foundry architecture on {{site.data.keyword.cloud_notm}}" caption-side="bottom"}

You can deploy your apps to different {{site.data.keyword.cloud_notm}} regions, for latency or security considerations. You can choose to deploy either to one region or across multiple regions.


![Multi-region app development](images/multi-region.png "A user can access an app that is deployed in one or more regions over the internet."){: caption="Figure 5. Multi-region app deployment" caption-side="bottom"}


{{site.data.keyword.cloud_notm}} infrastructure layers
{: #infralayers}


{{site.data.keyword.cloud_notm}} abstracts and hides operating system and infrastructure layers, so that you don't need to manage them. However, sometimes you might want to know more about the operating system and middleware for your app.
{: shortdesc}

### Viewing {{site.data.keyword.cloud_notm}} infrastructure layers
{: #viewinfra}

You can run the **ibmcloud cf stacks** command to show the available stacks, or root file systems, that your apps are to be deployed to. You can also specify the stack when you use the **ibmcloud cf push** command with the *-s* option and the *stack_name*, where the stack_name is the root file system. {{site.data.keyword.ibmcf_notm}} only supports `cflinuxfs3` currently:

```
ibmcloud cf push <APP_NAME> -s STACK
```
{: pre}

You can use the `ibmcloud cf buildpacks` command to show the available buildpacks, such as Liberty for Java and SDK for Node.js, that are available as runtimes for your app to run in. And you can specify the runtime environment for your app by using the following command:

```
ibmcloud cf push <APP_NAME> -b BUILDPACK_NAME
```
{: pre}



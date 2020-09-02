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


# Creating apps with the Node-RED Starter
{: #gettingstarted-nodered}



Node-RED provides a browser-based flow editor that makes it easy to connect devices, APIs, and online services by using the wide range of nodes in the palette. You can deploy the flows to the Node.js runtime environment with a single click. This starter app provides a version of Node-RED that is customized to run in {{site.data.keyword.cloud}}.   
{: shortdesc}

Use the editor to create flows right away. You can also customize Node-RED itself. For more information, see the [Node-RED site](http://nodered.org/){: external}.

## Using Node-RED
{: #usingNodeRed}

Complete the following steps to use the Node-RED starter app from the {{site.data.keyword.cloud_notm}} console.

1. Create a Node-RED starter app and download the starter code:
  1. Click **Create App** to deploy a Node-RED starter app.
  2. Provide the app name and host in the prompt.
2. After your app starts, click **Routes URL** or enter the following URL in a browser to display the Node-RED landing page.
  ```
    http://<varname>&lt;yourhost></varname>.mybluemix.net
  ```

3. Click **Go to your Node-RED flow editor** to open the browser-based flow editor. The editor makes it easy to connect devices, APIs, and online services by using the wide range of nodes that are included in the palette.

## Customizing your Node-RED instance
{: #customizingNodeRed}

You can customize your Node-RED instance for your needs. For example, you can replace the landing page with your own page, add http authentication to the flow editor, or add new nodes to the palette.

1. Download the app code by clicking **Start Coding > Download Starter Code** on the app's overview page.
2. Ensure that the Cloud Foundry command-line interface (CLI) is installed. See [the instructions for installing the command line interface](/docs/cloud-foundry-public?topic=cloud-foundry-public-cf-deploy-cli) for more information.
3. Log in to the {{site.data.keyword.cloud_notm}} environment.
  ```
  ibmcloud cf login -a https://api.<ph conref="cloudoeconrefs.dita#cloudoeconrefs/domainname"></ph> -u <varname props="keyref(user_ID)">&lt;your user ID></varname> -p <varname>*****</varname> -o <varname props="keyref(org_name)">&lt;your org name></varname> -s <varname
  props="keyref(space_name)">&lt;your space name></varname>
  ```
  {: codeblock}
4. Modify the app, and deploy it again. The default app landing page describes some of the customization. Nodes and packages can be added to your instance of NodeRED by adding them to the list of dependencies.  After you complete your changes, use the CLI to deploy the app to {{site.data.keyword.cloud_notm}} again.

  For example, run the following command in the root directory of the app:
  ```
  ibmcloud cf push <varname>&lt;yourappname></varname>
  ```
  {: pre}

## Access the VCAP_SERVICES environment
{: #VCAP}

To access the VCAP_SERVICES environment from a Node-RED flow, you must add the environment variable to the Function node's global context.

1. Edit your "bluemix-settings.js" and add an entry to the *functionGlobalContext* property to parse VCAP_SERVICES.
2. Redeploy your Node-RED app.

  ```
  functionGlobalContext: { VCAP_SERVICES: JSON.parse(process.env.VCAP_SERVICES)}
  ```
  {: pre}

After you redeploy Node-RED, you can  access VCAP_SERVICES in a Function node as the *context.global.VCAP_SERVICES* variable.



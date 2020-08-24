---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-24"

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



# Start coding with Node-RED
{: #startNodeRed}



Before you can start coding with Node-RED, you must first configure the editor.
{: shortdesc}

## Open the Node-RED flow editor
{: #openEditor}

1. After your application starts, click **Routes URL** or enter the following URL in a browser to display the Node-RED landing page.
```
    http://<varname>&lt;yourhost></varname>.mybluemix.net
```
2. Click **Go to your Node-RED flow editor** to open the browser-based flow editor. The editor makes it easy to connect devices, APIs, and online services by using the wide range of nodes that are included in the palette.

## Customizing your Node-RED instance
{: #customize_instance}

Before you begin, install the [Cloud Foundry command-line interface](https://github.com/cloudfoundry/cli/releases){: external}.

1. {: hide-in-docs}[Download and extract your starter code](https://cloud.ibm.com/){: external} to set up your development environment.

2. Change to your new directory.
```
cd <varname>directory_name</varname></codeblock>
```
{: pre}
3. Connect to {{site.data.keyword.cloud}}.
```
ibmcloud cf api https://api.{DomainName}/
```
{: pre}
4. Log in to {{site.data.keyword.cloud_notm}}.
```
ibmcloud cf login -u <varname props="keyref(user_ID)">user_name</varname>
ibmcloud cf target -o <varname props="keyref(org_name)">org_name</varname> -s <varname props="keyref(space_name)">space_name</varname>
```
{: codeblock}
5. Deploy your app to {{site.data.keyword.cloud_notm}}.
```
ibmcloud cf push <varname props="keyref(app_name)">app_name</varname>
```
{: pre}
6. Access your app to see your changes.
```
<varname props="keyref(host)">host</varname>.<keyword conref="cloudoeconrefs.dita#cloudoeconrefs/Appdomainname"/>
```
{: pre}


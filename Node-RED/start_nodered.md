---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}


# Start coding with Node-RED
{: #startNodeRed}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Before you can start coding with Node-RED, you must first configure the editor.
{: shortdesc}

## Open the Node-RED flow editor
{: #openEditor}

1. After your app starts, click **Routes URL** or enter the following URL in a browser to display the Node-RED landing page.

    ```text
    http://<varname>&lt;yourhost></varname>.mybluemix.net
    ```
    {: codeblock}

2. Click **Go to your Node-RED flow editor** to open the browser-based flow editor. The editor makes it easy to connect devices, APIs, and online services by using the wide range of nodes that are included in the palette.

## Customizing your Node-RED instance
{: #customize_instance}

Before you begin, install the [Cloud Foundry command-line interface](https://github.com/cloudfoundry/cli/releases){: external}.

1. [Download and extract your starter code](https://cloud.ibm.com/){: external} to set up your development environment.

2. Change to your new directory.

    ```text
    cd <varname>directory_name</varname></codeblock>
    ```
    {: pre}

3. Connect to {{site.data.keyword.cloud}}.

    ```text
    ibmcloud cf api https://api.{DomainName}/
    ```
    {: pre}

4. Log in to {{site.data.keyword.cloud_notm}}.

    ```text
    ibmcloud cf login -u <varname props="keyref(user_ID)">user_name</varname>
    ibmcloud cf target -o <varname props="keyref(org_name)">org_name</varname> -s <varname props="keyref(space_name)">space_name</varname>
    ```
    {: codeblock}

5. Deploy your app to {{site.data.keyword.cloud_notm}}.

    ```text
    ibmcloud cf push <varname props="keyref(app_name)">app_name</varname>
    ```
    {: pre}

6. Access your app to see your changes.

    ```text
    <varname props="keyref(host)">host</varname>.<keyword conref="cloudoeconrefs.dita#cloudoeconrefs/Appdomainname"/>
    ```
    {: pre}
    


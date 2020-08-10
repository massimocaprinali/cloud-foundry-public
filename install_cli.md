---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-09"

keywords: cloud foundry

subcollection: cloud-foundry-public



---



{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: #java .ph data-hd-programlang='java'}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vb.net: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Download, modify, and redeploy your Cloud Foundry app with the command-line interface
{: #cf-deploy-cli}

<!-- This file is reused in the CF Public subcollection. -->

Use the {{site.data.keyword.cloud}} command-line interface (CLI) to download, modify, and redeploy your Cloud Foundry applications and service instances.
{: shortdesc}

Before you begin, [download and install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started).


After you install the CLI, you can get started:

  1. Change to the directory where your code is located.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  2.  Make changes to your app code as you see fit. For example, if you are using a {{site.data.keyword.cloud_notm}} sample application and your app contains the `src/main/webapp/index.html` file, you can modify it and edit "Thanks for creating ..." to say something new. Ensure the app runs locally before you deploy it back to {{site.data.keyword.cloud_notm}}.

    Take note of the `manifest.yml` file. When deploying your app back to {{site.data.keyword.cloud_notm}}, this file is used to determine your application’s URL, memory allocation, number of instances, and other crucial parameters. You can [read more about the manifest file ![External link icon](../icons/launch-glyph.svg "External link icon")](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html){: new_window} in the Cloud Foundry documentation.

    Also pay attention to the `README.md` file, which contains details such as build instructions if applicable.

    Note: If your application is a Liberty app, you must build it before redeploying.

  3. Log in to {{site.data.keyword.cloud_notm}} with your IBMid. If you have multiple accounts, you are prompted to select which account to use. If you do not specify a region with the `-r` flag, you must also select a region.
  ```
  ibmcloud login
  ```
  {: pre}

  If your credentials are rejected, you might be using a federated ID. To log in with a federated ID, use the `--sso` flag. See [Logging in with a federated ID](/docs/account?topic=account-federated_id) for more details.
  {: tip}

  4. To access Cloud Foundry services, you must specify a Cloud Foundry org and space. You can run the following command to interactively identify the org and space:
  ```
  ibmcloud target --cf
  ```
  {: pre}

  Or, if you know which org and space that the service belongs to, you can use the following command:
  ```
  ibmcloud target -o <value> -s <value>
  ```
  {: pre}

   5. From `your_new_directory`, redeploy your app to {{site.data.keyword.cloud_notm}} by using the **`ibmcloud cf push`** command. For more information, see [**`ibmcloud cf push`**](/docs/cli?topic=cli-ibmcloud_commands_apps#ibmcloud_app_push).

  6. Access your app by browsing to the app URL.


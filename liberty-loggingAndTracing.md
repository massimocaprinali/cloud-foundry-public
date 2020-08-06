---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-06"

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

# Configure logging and tracing
{: #logging_tracing}

## Log files
{: #log_files}

The standard Liberty logs, such as `messages.log` or the `ffdc` directory, are available in {{site.data.keyword.cloud}} in the `logs` directory of each application instance. These logs can be accessed from the {{site.data.keyword.cloud_notm}} console or via the {{site.data.keyword.cloud_notm}} CLI. For example:

* To access recent logs for an app, run the following command:

  ```
  ibmcloud cf logs --recent <appname>
  ```
  {: codeblock}


* To see the `messages.log` file of an app, run the following command:

  ```
  ibmcloud cf ssh <appname> -c "cat logs/messages.log"
  ```
  {: codeblock}

The log level and other trace options can be set through the Liberty configuration file. For more information, see [Troubleshooting Liberty: Logging and Trace](http://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_logging.html).

## Using the trace and dump capabilities
{: #using_trace_and_dump}

### Using trace and dump in {{site.data.keyword.cloud_notm}} console (Deprecated)

The Liberty tracing configuration can be adjusted for a running application directly from the {{site.data.keyword.cloud_notm}} console. The console also provides capability for requesting and downloading thread and heap dumps. In order to adjust the tracing configuration or request a dump, select a Liberty application in the {{site.data.keyword.cloud_notm}} console and choose the `Runtime` menu in the navigation. In the `Runtime` view, select an instance and press the *TRACE* or *DUMP* button. If adjusting the trace level, see [Troubleshooting Liberty: Logging and Trace](http://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_logging.html) for the details of the syntax of the trace specification.

### Changing trace configuration via SSH

When you push the application, the server.xml file includes the default properties  **updateTrigger** set to **polled** and **monitorInterval** set to 1 minute. The Liberty server is automatically configured to check for updates to the server.xml file each minute.

See [Push Liberty apps with server.xml](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#options_for_pushing) for options to push Liberty apps with a customized `server.xml` file.

See [Controlling Dynamic Updates](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_setup_dyn_upd.html){: new_window} for how to set up dynamic update in the server.xml file.

Follow these steps to change tracing configuration:

1. SSH to your app

  ```
 ibmcloud cf ssh <appname> [-i instance_index]
  ```
  {: codeblock}

2. Edit `<logging traceSpecification="xxxx"/>` in the server.xml to set your desired trace specification,  for example using *vi*:

  ```
vi /app/wlp/usr/servers/defaultServer/server.xml
  ```
  {: codeblock}

Note: The server.xml change will be lost on a restage or restart and is only valid for the instance you ssh into.

See [Troubleshooting Liberty: Logging and Trace](http://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_logging.html){: new_window} for the details of the syntax of the trace specification.

### Triggering dumps via SSH

Use the command below to trigger a thread and heap dump via {{site.data.keyword.cloud_notm}} CLI using the SSH feature:

  ```
 ibmcloud cf ssh <appname> -c "pkill -3 java"
  ```
  {: codeblock}

See the documentation below for details on downloading the generated dump files.

## Download dump files
{: #download_dumps}

By default, the various dump files are placed in the `dumps` directory of the application container. Use {{site.data.keyword.cloud_notm}} CLI `ibmcloud cf ssh` to view and download the dump files.

* To see the generated dumps, run the following command:

  ```
  ibmcloud cf ssh <appname> -c "ls -l dumps"
  ```
  {: codeblock}

* To download a dump file, run the following command:

  ```
  ibmcloud cf ssh <appname> -i <instance_id> -c "cat dumps/<dump_file_name>" > <local_dump_file_name>
  ```
  {: codeblock}

It is also possible to use `scp` and other similar tools to view and download the dump files. Refer to [Accessing Apps with SSH  ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.cloudfoundry.org/devguide/deploy-apps/ssh-apps.html) for more information.



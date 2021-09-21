---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-21"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:audio: .audio}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: .ph data-hd-programlang='c#'}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: #curl .ph data-hd-programlang='curl'}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: .external target="_blank"}
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
{:middle: .ph data-hd-position='middle'}
{:navgroup: .navgroup}
{:new_window: target="_blank"}
{:node: .ph data-hd-programlang='node'}
{:note: .note}
{:objectc: .ph data-hd-programlang='Objective C'}
{:objectc: data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: .ph data-hd-programlang='PHP'}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:release-note: data-hd-content-type='release-note'}
{:right: .ph data-hd-position='right'}
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
{:step: data-tutorial-type='step'} 
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:topicgroup: .topicgroup}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Managing Liberty apps
{: #app_management}

App Management is a set of development and debugging utilities that can be enabled for your Liberty apps on {{site.data.keyword.cloud}}.
{: shortdesc}

## {{site.data.keyword.cloud_notm}} console and CLI

### Managing app through {{site.data.keyword.cloud_notm}} console

The {{site.data.keyword.cloud_notm}} console provides the ability to start, stop and restart app from the *Action* tab on your app from the console.

### Managing the app by using the ibmcloud cf CLI

You can also manage your app by using the command line.  In the commands replace `<myApp>` with your app name.

To start the app:

```text
ibmcloud cf start <myApp>
```
{: pre}

To stop an app:

```text
ibmcloud cf stop <myApp>
```
{: pre}

To restart an app:

```text
ibmcloud cf restart <myApp>
```
{: pre}

## App management by using an SSH shell session

Apps can be managed and debugged after accessing the app by using the `ssh` command. This can be accomplished through {{site.data.keyword.cloud_notm}} console and `ibmcloud cf` CLI.

### {{site.data.keyword.cloud_notm}} console

User can `ssh` into the app by using the {{site.data.keyword.cloud_notm}} console. Navigate to the Runtime tab on your app and then click `SSH` to manage.

### Command Line CLI

To use `ssh` to access your app from the command line use:

```text
ibmcloud cf ssh <myApp>
```
{: pre}

## App Management utilities
{: #Utilities}

### Liberty utilities

* [`proxy`](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management#proxy)

* [`noproxy`](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management#noproxy)

* [`hc`](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management#hc)

* [`jmx`](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management#jmx)

* [`localjmx`](/docs/cloud-foundry-public?topic=cloud-foundry-public-app_management#localjmx)

## How to configure App Management
{: #configure}

To enable App Management utilities, set the value of the `BLUEMIX_APP_MGMT_ENABLE` environment variable to the utility or list of utilities you want to enable, then restage your app. You can enable multiple utilities by separating them with a `+`.

For example, to enable `hc`, `debug` and `trace` utilities, run the following command:

```text
ibmcloud cf set-env <myApp> BLUEMIX_APP_MGMT_ENABLE hc+debug+trace
```
{: pre}

Restage your app after you set the environment variable:

```text
ibmcloud cf restage <myApp>
```
{: pre}

If you do not want the App Management utilities to be installed with your app, set the `BLUEMIX_APP_MGMT_INSTALL` environment variable to `false` and restage your app.

For example, run the following commands to stage your app without App Management utilities:

```text
ibmcloud cf set-env <myApp> BLUEMIX_APP_MGMT_INSTALL false
ibmcloud cf restage <myApp>
```
{: pre}

## Restrictions
{: #restrictions}

Changes that you make to your app by using App Management are transient and are lost after you exit this mode. This mode is only for temporary development use and is not intended to be used as a production environment due to performance.

### Liberty utilities
{: #liberty_utilities}

#### jmx
{: #jmx}

The `jmx` utility enables the JMX REST Connector to allow a remote JMX client to manage the app by using {{site.data.keyword.cloud_notm}} user credentials.

You can monitor multiple instances of an app by using JMX, but it requires a separate JMX connection for each instance. The default is to monitor instance 0. To monitor instance 1, you can use the following:

```text
ibmcloud cf ssh -i 1 -N -T -L 5000:127.0.0.1:5001
```
{: pre}

For more information on configuring a JMX connector, see [Configuring secure JMX connection to the Liberty profile](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_admin_restconnector.html){: external}.

The `jmx` utility does not start `proxy`.
{: important}

#### `localjmx`
{: #localjmx}

The `localjmx` utility enables the [localConnector-1.0](http://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_feature_localConnector-1.0.html){: external} Liberty feature. Combined with local port forwarding, `localjmx` acts an alternate way of allowing a remote JMX client to manage the app.

`localjmx` requires you to install JConsole.
{: note}

To use `localjmx`, first establish port forwarding by using the `ibmcloud cf ssh` command. For example:

```text
ibmcloud cf ssh -N -T -L 5000:127.0.0.1:5000 <appName>
```
{: pre}

Next, to connect with JConsole, choose **Remote Process**, specify `127.0.0.1:5000`, and use an insecure connection.

#### proxy
{: #proxy}

The `proxy` utility provides minimal app management between your app and {{site.data.keyword.cloud_notm}}.

When enabled, the buildpack starts a proxy agent that is located between your app's runtime and container.  The `proxy` utility handles all requests that the app receives. Based on the type of request, it either takes an App Management action or forwards the request to your app. By using `proxy`, your app container continues to live even if the app crashes. The proxy agent also allows for incremental file updates, which enables the *Live Edit* mode.

Some App Management utilities require you to use the `proxy` utility with your app, and can start `proxy` automatically.

#### `noproxy`
{: #noproxy}

The `noproxy` utility disables the `proxy` utility when it is automatically started by another utility.  With Diego, the proxy is not necessary because Diego provides the capability to `ssh` directly to your app and set up port forwarding.

The `noproxy` utility only applies to apps that run in a Diego cell.

#### hc
{: #hc}

The (`hc`) Health Center agent enables your app to be monitored by the Health Center client.

When you have the Health Center agent enabled, you can analyze the performance of your Liberty apps by using the {{site.data.keyword.IBM_notm}} Monitoring and Diagnostic Tools. For more information see [How to analyze the performance of Liberty Java in {{site.data.keyword.cloud_notm}}](https://www.ibm.com/blogs/cloud-archive/2015/07/how-to-analyze-performance-in-bluemix/){: external}.

The `hc` utility starts `proxy`.
{: important}

**Using `hc` with `noproxy` **

The `hc` utility can be used in conjunction with `noproxy`. To use Health Center with `noproxy`, first establish port forwarding by using the `ibmcloud cf ssh` command. For example:

```text
ibmcloud cf ssh -N -T -L 1883:127.0.0.1:1883 <appName>
```
{: pre}

To connect with the Health Center client, use a [MQTT connection](http://www.ibm.com/support/knowledgecenter/SS3KLZ/com.ibm.java.diagnostics.healthcenter.doc/topics/connectingtojvm.html){: external} and specify the host as `127.0.0.1` and port as `1883`.



---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-14"

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


# Working with a proxy
{: #working_with_proxy}

In some environments a proxy might be configured that affects the
behavior of your application during staging and run time.

You can configure your application to work with the proxy by using the following environment variables:
  * [http_proxy](https://docs.cloudfoundry.org/buildpacks/proxy-usage.html){: external}
  * [https_proxy](https://docs.cloudfoundry.org/buildpacks/proxy-usage.html){: external}
  * [no_proxy](http://www.gnu.org/software/wget/manual/html_node/Proxies.html){: external}

You can set these environment variables using `**bluemix app env-set**` or via the `manifest.yml` file.  Depending on how you configure your proxy environment variables, if your application downloads resources from the internet during staging, your resources might download using the proxy. For example, if you have a Nodejs application in an environment with `http_proxy` set to `yourProxyURL` and you want to allow `npm` to download modules from the internet **but not the proxy**.  To download without using the proxy, set `no_proxy` to `npmjs.org`.

You might want your application to use the proxy during runtime, after staging.  Runtime proxy use is entirely dependent on the application and is not affected by either the buildpack or the proxy environment variables.
{: note}

## Java applications
{: #java_apps}

For [Liberty for Java](/docs/cloud-foundry-public?topic=cloud-foundry-public-liberty_runtime) and the [java_buildpack](/docs/cloud-foundry-public?topic=cloud-foundry-public-getting-started-tomcat){: external} applications, the proxy settings can be passed to the runtime via the **JAVA_OPTS** environment variable.  For example you can issue the command and then restage your application:
```
   ibmcloud app env-set myApp JAVA_OPTS "-Dhttp.proxyHost=yourProxyURL -Dhttp.proxyPort=yourProxyPort"
```
{: pre}

Your application then uses the specified proxy settings at runtime. See [Java Networking and Proxies](https://docs.oracle.com/javase/8/docs/technotes/guides/net/proxies.html){: external} for more information about the Java proxy options.



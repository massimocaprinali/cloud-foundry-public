---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Working with a proxy
{: #working_with_proxy}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

In some environments a proxy might be configured that affects the
behavior of your app during staging and run time.

You can configure your app to work with the proxy by using the following environment variables:
* [http_proxy](https://docs.cloudfoundry.org/buildpacks/proxy-usage.html){: external}
* [https_proxy](https://docs.cloudfoundry.org/buildpacks/proxy-usage.html){: external}
* [no_proxy](http://www.gnu.org/software/wget/manual/html_node/Proxies.html){: external}

You can set these environment variables using `ibmcloud app env-set` or using the `manifest.yml` file.  Depending on how you configure your proxy environment variables, if your app downloads resources from the internet during staging, your resources might download using the proxy. For example, if you have a Node.js app in an environment with `http_proxy` set to `yourProxyURL` and you want to allow `npm` to download modules from the internet **but not the proxy**.  To download without using the proxy, set `no_proxy` to `npmjs.org`.

You might want your app to use the proxy during runtime, after staging.  Runtime proxy use is entirely dependent on the app and is not affected by either the buildpack or the proxy environment variables.
{: note}

## Java apps
{: #java_apps}

For [Liberty for Java](/docs/cloud-foundry-public?topic=cloud-foundry-public-liberty_runtime) and the [java_buildpack](/docs/cloud-foundry-public?topic=cloud-foundry-public-getting-started-tomcat){: external} apps, the proxy settings can be passed to the runtime via the **JAVA_OPTS** environment variable.  For example you can issue the command and then restage your app:

```text
ibmcloud app env-set myApp JAVA_OPTS "-Dhttp.proxyHost=yourProxyURL -Dhttp.proxyPort=yourProxyPort"
```
{: pre}

Your app then uses the specified proxy settings at runtime. See [Java Networking and Proxies](https://docs.oracle.com/javase/8/docs/technotes/guides/net/proxies.html){: external} for more information about the Java proxy options.



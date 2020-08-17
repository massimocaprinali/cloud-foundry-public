---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-17"

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


# Use the offline mode for Liberty
{: #offline_mode}

When a Liberty application is pushed to {{site.data.keyword.cloud}}, the Liberty buildpack can access sites external to {{site.data.keyword.cloud_notm}}
to acquire artifacts required by the application.  

* https://download.run.pivotal.io, and https://java-buildpack.cloudfoundry.org are used to access components for:
  * [AppDynamics agent](https://www.appdynamics.com/){: external}
  * [MariaDB JDBC driver](https://mariadb.com/){: external}
  * [New Relic agent](/docs/cloud-foundry-public?topic=cloud-foundry-public-new_relic)
  * [OpenJDK](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre#openjdk)
  * [PostgreSQL JDBC driver](https://www.postgresql.org){: external}
* https://dl.zeroturnaround.com/jrebel/ is used to access components for [JRebel](https://www.jrebel.com/products/jrebel){: external}.
* https://files.dynatrace.com/downloads/appmon/cloudfoundry/buildpack/java/ is used to access the [Dynatrace agent](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_dynatrace).

## Working with a proxy
{: #liberty-working_with_proxy}

In some environments a proxy might be required. See
[Working with a proxy](/docs/cloud-foundry-public?topic=cloud-foundry-public-working_with_proxy) for more details.



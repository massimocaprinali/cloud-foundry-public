---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Use the offline mode for Liberty
{: #offline_mode}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

When a Liberty app is pushed to {{site.data.keyword.cloud}}, the Liberty buildpack can access sites external to {{site.data.keyword.cloud_notm}}
to acquire artifacts required by the app.  

* `https://download.run.pivotal.io` and `https://java-buildpack.cloudfoundry.org` are used to access components for:
    * [AppDynamics agent](https://www.appdynamics.com/){: external}
    * [MariaDB JDBC driver](https://mariadb.com/){: external}
    * [New Relic agent](/docs/cloud-foundry-public?topic=cloud-foundry-public-new_relic)
    * [OpenJDK](/docs/cloud-foundry-public?topic=cloud-foundry-public-customizing_jre#openjdk)
    * [PostgreSQL JDBC driver](https://www.postgresql.org){: external}
* `https://dl.zeroturnaround.com/jrebel/` is used to access components for [JRebel](https://www.jrebel.com/products/jrebel){: external}.
* `https://files.dynatrace.com/downloads/appmon/cloudfoundry/buildpack/java/` is used to access the [Dynatrace agent](/docs/cloud-foundry-public?topic=cloud-foundry-public-using_dynatrace).

## Working with a proxy
{: #liberty-working_with_proxy}

In some environments a proxy might be required. See
[Working with a proxy](/docs/cloud-foundry-public?topic=cloud-foundry-public-working_with_proxy) for more details.



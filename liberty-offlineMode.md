---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Use the offline mode for Liberty
{: #offline_mode}

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



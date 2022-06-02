---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Best practices for running apps in production
{: #production}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Cloud Foundry is an excellent platform for running cloud-ready apps in production. These best practices can help with running production Cloud Foundry apps with {{site.data.keyword.cloud}}.
{: shortdesc}

## Multiple instances
{: #multiple_instances}

Cloud-ready apps are horizontally scalable, and are therefore able to dynamically add or remove app instances. Run at least three instances of each app to help avoid unexpected downtime in the event of isolated incidents or platform maintenance.

## Monitoring options
{: #monitoring-bps}

{{site.data.keyword.cloud_notm}} makes it easy to monitor your app with services like [{{site.data.keyword.mon_full_notm}}](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-getting-started) and [New Relic](http://newrelic.com/){: external}. Check out [Integrated logging capabilities](/docs/cloud-foundry-public?topic=cloud-foundry-public-monitoring_logging_cloud_foundry_apps) for more information.

## Support options
{: #support}

{{site.data.keyword.cloud_notm}} paid pricing plan offers a number of different account types with optional paid support.  No matter the type of your account, if you plan to bring an app to production on {{site.data.keyword.cloud_notm}}, consider enrolling in this option.

With or without paid support, you can get help as described at [Getting support](/docs/get-support), but paying for support will help  ensure that your support tickets will be given the level attention that they deserve.



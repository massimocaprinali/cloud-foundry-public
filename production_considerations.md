---

copyright:
  years: 2015, 2020
lastupdated: "2020-09-08"

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

# Best practices for running apps in production
{: #production}



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



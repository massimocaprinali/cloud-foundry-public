---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Logging and Monitoring
{: #monitoring_logging_cloud_foundry_apps}

{{site.data.keyword.cloud}} has a built-in logging mechanism to produce log files for your apps as they are running. In the logs, you can view the errors, warnings, and informational messages that are produced for your app. In addition, you can also configure your app to write log messages to the log file. For more information about log formats and how to view logs, see [Collecting and analyzing logs from {{site.data.keyword.ibmcf_notm}} resources](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-monitor_cfapp_logs).

Monitoring your app enables you to see and control your app deployment. With monitoring, you can accomplish the following tasks:

* Collect and monitor performance information for app instances, and check whether they are functional.
* Gain insight on app operations, for example, detect the potential bottlenecks or when upgrades are required.
* Estimate resource usage and charges.

For stable operations of your deployments on {{site.data.keyword.cloud_notm}} platform, you want to detect problems promptly and determine causes efficiently. To accomplish this objective, keep troubleshooting in mind when you design your apps, and use services or tools for monitoring and logging when your app is deployed to {{site.data.keyword.cloud_notm}}.

To retain logs for a longer period and advanced analysis, services like [{{site.data.keyword.cos_short}}](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-archiving) can be used.

For more information about how to monitor {{site.data.keyword.ibmcf_notm}} apps, see [Monitoring Cloud Foundry metrics](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-monitor-cf-sysdig).

{{site.data.keyword.ibmcf_notm}} apps can configure and expose metrics that can be monitored using {{site.data.keyword.mon_full}}. For more information, see [Monitoring Cloud Foundry metrics](/docs/Monitoring-with-Sysdig?topic=Monitoring-with-Sysdig-monitor-cf-sysdig).




---

copyright:
  years: 2019
lastupdated: "2019-04-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Autoscaling applications
{: #autoscale_cloud_foundry_apps}

Auto-scaling support for Cloud Foundry applications is available on {{site.data.keyword.Bluemix}}.  This capability is built on the open-source [App-Autoscaler project][autoscaler_project], and allows you to adjust the number of application instances automatically through operational metrics and/or time period.

## Getting started with autoscaling on Cloud Foudry Public

The easiest way to explore the auto-scaling functionality is through the {{site.data.keyword.Bluemix}} user interface.

If you already have an application deployed on Cloud Foundry,  access the autoscaling page with the following steps:

1. From the [{{site.data.keyword.cloud_notm}} console ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}){: new_window}, click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg), and select **Resource List**.
2. On the **Resource List** page, click **Cloud Foundry Apps**.
3. Click the application to view its **Overview** page.
4. Select the **Autoscaling** in the left navigation pane.
5. In the **Policy** tab configure your scaling policy for the application.

If you don't have an Cloud Foundry application running on {{site.data.keyword.Bluemix}}, [deploy a Cloud Foundry application][deploy_app] to {{site.data.keyword.Bluemix}} first. 

## Getting started with autoscaling on Cloud Foundry Enterprise Environment (CFEE)

Refer to [application auto-scaling documentation for CFEE][autoscaling_cfee_doc].

## Policy configuration

Autoscaling determines when and how to scale your application's capacity according to the autoscaling policy that you defined.  You can create the autoscaling policy from scratch or import it from an existing JSON file.  

To create a policy from scratch, follow steps below:

1. Click  **Create Auto-Scaling policy**
2. Set **Default Instance Limits** of your application with **Minimum Instance Count** and **Maximum Instance Count** to restrict the scope of resource consumption 
3. Create a series of **Dynamic Scaling Rules** with selected metric types, thresholds and adjustment strategies.  The following describes related fields in the dynamic scaling rule.
      
   **Metric types:** The following metric types are supported in dyanmic scaling rule:
   * **Memory used** represents the absolute value of the used memory of your application. The unit of _memory utilization_ unit is "MB".
   * **Memory utilization**, a short name of `memory utilization`, is the used memory of the total memory allocated to the application in percentage. For example, if the memory usage of the application is 100MB  and memory quota is 200MB, the value of _memory utilization_ is 50%.   
   * **CPU** , a short name of `cpu utilization`, is the cpu percentage used by the application. The unit of **cpu** is "%".  
      _Note_: `cpu utilization` may be affected by the total workload of the hosting hardware and other factors.
   * **Response time** represents the average amount of time the application takes to respond to a request in a given time period.  The unit of _Response time_ is "ms" (milliseconds).
   * **Throughput** is the total number of the processed requests  in a given time period. The unit of _throughput_ is "rps" (requests per second).

   **Operator**, **Threshold**, **Breach Duration** , **Adjustment** and **Cooldown**: 

   Once the **threshold** is continuously breached during the **breach duration** period,  App Autoscaler will trigger a scaling action to ** adjust** application instance number unless **Cool down** setting is not fulfilled. 
   
   * **Operator** could be defined as `>=`, `>`, `<=` or `<`.
   * **Threshold** must be defined as a numeric value.  
   * **Breach duration** is defined in `seconds`. 
   * **Adjustment** defines how to change the number of application instances in each scaling action.  You can specify an absolute number or a percentage of insatnces to add or remove.
   * **Cooldown** defines the time duration to wait before the next scaling action takes place. A cooldown period helps to ensure that your application does not launch new instances or terminate old instances before your application becomes stable. **Cooldown** is defined in `seconds`
    
4. (Optional) Define **Schedules** to scale your application during a set of time periods.

   You can define _Schedules_ to prepare enough instances for peak hours. The schedule policy overwrites the default instance limits and set the instance number to **Initial Minimum Instance Count** to enforce the instance number at the beginning of a schedule. 

   To define **Schedules**:

   * Select a **Time Zone** in which a schedule will take place.
   * Define either **Recurring schedules**  which execute periodically, or **Specific schedules** that take effect only once during specific time periods. 

   _Note_: during these scheduled time periods, all dynamic scaling rules are still effective. 

You can also import a policy file in JSON through **Import From JSON**.  Refer to [policy specification][autoscaler_user_guide] for the details of JSON format of autosacling policy. This function is particularly helpful when you [migrate from the legacy Auto-scaling service][migrate_guide].

## Metric statistics

Once a policy is defined with dynamic scaling rules, you will be able to view the latest metric values, and  metrics history in in the past 2 hours. 

_Note_: the metric value is not the raw data from each application instance but averaged over all the application instances. 
    
## Scaling history

The **Scaling history** tab allows you to query the scaling events within the past 30 days. It also shows the error messages if the scaling attempt failed. 

## Further reading

- Use [command line interface][autoscaler_cli] to manage auto-scaling policies, query metrics and events.
- [Migrate] from legacy Auto-Scaling service to this new autoscaler[migrate_guide]


## Contact us

Any questions and feature request, please contact us through slack channel[autoscaler@cloudfoundry](https://cloudfoundry.slack.com/messages/autoscaler)


[autoscaler_project]: https://github.com/cloudfoundry/app-autoscaler
[autoscaler_user_guide]: https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/Readme.md
[autoscaling_policy]:https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/policy.md
[autoscaler_cli]: https://github.com/cloudfoundry/app-autoscaler-cli-plugin#cloud-foundry-cli-autoscaler-plug-in-
[autoscaling_cfee_doc]: https://{DomainName}/docs/cloud-foundry?topic=cloud-foundry-autoscale_cloud_foundry_apps#autoscale_cloud_foundry_apps
[metric_type]: https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/Readme.md#metric-types
[deploy_app]: https://{DomainName}/docs/cloud-foundry/deploy-apps.html#dep_apps
[legacy-autoscaling-catalog]: https://{DomainName}/catalog/services/auto-scaling
[legacy-autoscaling-cli]: https://{DomainName}/docs/cli?topic=auto-scaling-cli-autoscalingcli#bx_as_policy_show
[migrate_guide]: https://{DomainName}/docs/cloud-foundry-public?topic=cloud-foundry-public-autoscale_migration
[autoscaler_cli]: https://{DomainName}/docs/cloud-foundry-public?topic=cloud-foundry-public-autoscale_cli

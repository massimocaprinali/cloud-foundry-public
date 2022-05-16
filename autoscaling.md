---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-11"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Autoscaling
{: #autoscale_cloud_foundry_apps}

{{site.data.keyword.cloud}} has built-in autoscaling support for {{site.data.keyword.ibmcf_full}} apps that adjust app instance numbers automatically by:

* Dynamic scaling instances based on app performance metrics.

* Scheduled scaling of instances based on date and time.

This capability is based on the [App AutoScaler](https://github.com/cloudfoundry/app-autoscaler){: external} Cloud Foundry open source project. See the [App AutoScaler User Guide](https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/Readme.md){: external} to get started.

## Managing autoscaling from the console

Autoscaling can be defined for apps that are deployed on {{site.data.keyword.ibmcf_notm}}. If you don't have an {{site.data.keyword.ibmcf_notm}} app running on {{site.data.keyword.cloud}}, [deploy a Cloud Foundry app](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) to {{site.data.keyword.cloud}} before you configure autoscaling.  

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click the **menu** icon ![Menu icon](../icons/icon_hamburger.svg), and select **Resource List**.

2. On the **Resource List** page, click **Cloud Foundry apps**.

3. Click the app to view its **Overview** page.

4. Click **Autoscaling**.

5. In the **Policy** tab, configure your scaling policy for the app.

### Creating autoscaling policies
{: #console_autoscaling_policies}

Autoscaling determines when and how your app's capacity is changed according to the autoscaling policy that you define.  You can create the autoscaling policies directly by using the console or by importing them from a JSON file.  

#### Defining autoscaling policies by using the console

1. Click  **Create Auto-Scaling policy**.

2. Set the **Default Instance Limits** of your app with a **Minimum Instance Count** and **Maximum Instance Count**.  These values restrict the scope of your app's resources.

3. Create the **Scaling Rules** with metric types, thresholds, and adjustment strategies.  

    The following metric types are supported:
  
    * `Memoryused` is the amount of memory that is used by your app. `Memoryused` is specified in MB.
   
    * `Memoryutil` specifies the memory that is used by the app as a percentage of the total memory quota that is allocated to the app.  For example, if the app is using 100 MB, and the memory quota is 200 MB, the memory utilization is 50%.   

    * `Cpu`, is the CPU percentage that is used by the app. `Cpu` is specified in percentage.  The CPU utilization can be affected by the total workload of the hosting hardware and other factors.
   
    * `Responsetime` is the average amount of time that the app takes to respond to a request.  `Responsetime` is specified in `ms` (milliseconds).
   
    * `Throughput` is the total number of the requests that are processed in a time period. `Throughput` is specified in `rps` (requests per second).
   
    * `Custom_metric` is your own custom metric. The `Custom_metric` name can be any alphanumeric value. Autoscaling is triggered when the corresponding metric is emitted to the App Autoscaler. For more information, see the [custom metric usage guide](https://github.com/cloudfoundry/app-autoscaler/tree/develop/docs#auto-scale-your-application-with-custom-metrics){: external}.

    In addition to specifying the metric type, specify an operator, threshold, breach duration, adjustment, and cooldown period values. 

    When the threshold is continuously breached during the breach duration period, and beyond  the cooldown period, the App AutoScaler triggers the defined autoscaling action.  The number or percentage of app instances is adjusted. 

    * The operator can be `>=`, `>`, `<=`, or `<`.
   
    * The threshold must be a numeric value.  
   
    * The breach duration is defined in `seconds`.  The default value is 120 seconds.
   
    * The adjustment value specifies how the number of app instances change in each scaling action.  You can specify an absolute number or a percentage of instances to add or remove.
   
    * The cooldown period specifies the time to wait before the taking the next autoscaling action. A cooldown period ensures that your app does not launch new instances or stop existing instances before your app is stable. The cooldown period is specified in `seconds`. The default cooldown period is 300 seconds.

4. (Optional) Define **Schedules** to scale your app during a set time period.

    You can define specific time periods when you know that your app requires different numbers of instances to handle peak loads. The schedule policy overwrites the default instance limits and sets the number of instances to the **Initial Minimum Instance Count** value for the scheduled period. 

    To define a schedule, complete the following steps. You can define multiple schedules.

    1. Open **Schedules**.
   
    2. Select the **Time Zone** where the schedule is defined.
   
    3. Indicate whether the schedule is always in effect (recurring schedules), or is only in effect for the specified date range (specific schedules).
   
    4. For recurring schedules, select whether the schedule is repeated weekly or monthly. 
   
    5. For recurring schedules, select the days of the week or month when the schedule applies.
   
    6. Specify the start and end time of the schedule, the minimum number of instances to be run, the initial minimum instances, and the maximum instances that are run during the period.

    During the scheduled time periods, all other autoscaling rules are still in effect.
    {: note}

### Importing a JSON policy file

You can import a JSON policy file by clicking **Import From JSON**.  See the [policy specification](https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/Readme.md){: external} for the autoscaling policy JSON format. 

### Metric statistics
{: #metric_statistics_console}

After a policy is defined with autoscaling rules, you can view the metric values and metrics history for the previous 2 hours.

The metric value is not the raw data from each app instance, but the metric values averaged over all the app instances.
{: note}

### Scaling history
{: #scaling_history_console}

Use the **Scaling history** tab to view the autoscaling events for the past 30 days. If autoscaling attempts failed, the tab also shows the error messages.

## Managing autoscaling from the CLI

You can also use the App Autoscaler command-line interface (also known as the AutoScaler CLI) to manage policies, query metrics, and view the scaling history.

### Installing or updating the AutoScaler CLI

Use the following command to install the `AutoScaler CLI`, which is a plug-in to the {{site.data.keyword.ibmcf_notm}} CLI.  

```text
ibmcloud cf install-plugin -r CF-Community app-autoscaler-plugin
```
{: pre}

If the `AutoScaler CLI` plug-in is already installed, you can use the same command to update the plug-in to the latest version.

### Using the AutoScaler CLI

If you are already logged in to an {{site.data.keyword.ibmcf_notm}} environment on {{site.data.keyword.cloud}} and have running apps in your space as described in the [deploying apps guide](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps), do the following to create a scaling policy for your app, access query metrics, and view the autoscaling history.

#### Creating autoscaling policies

1. (Optional) Confirm that the App Autoscaler API endpoint is set correctly.  

    If the {{site.data.keyword.ibmcf_notm}} API endpoint is `api.<DOMAIN>`, the App Autoscaler API endpoint must be `autoscaler.<DOMAIN>`.  

    To check the App Autoscaler API endpoint setting, run the following command:

    ```text
    ibmcloud cf asa
    ```
    {: pre}

    If the App Autoscaler API endpoint is incorrect, set it with the following command.

    ```text
    ibmcloud cf asa autoscaler.<DOMAIN>
    ```
    {: pre}

2.  Create a JSON policy file on your local machine.  The following code is an example policy file.  You can define the same [scaling policy specifications](#console_autoscaling_policies) in the console and in the JSON policy file.

    ```text
    cat > <YOUR_POLICY_FILE> << EOF
    {
            "instance_min_count": 1,
            "instance_max_count": 5,
            "scaling_rules": [
                    {
                            "metric_type": "memoryutil",
                            "breach_duration_secs": 120,
                            "threshold": 80,
                            "operator": ">=",
                            "cool_down_secs": 120,
                            "adjustment": "+1"
                    },
                    {
                            "metric_type": "memoryutil",
                            "breach_duration_secs": 120,
                            "threshold": 10,
                            "operator": "<",
                            "cool_down_secs": 120,
                            "adjustment": "-1"
                    }
            ]
    }
    EOF
    ```
    {: codeblock}

    This example policy triggers autoscaling based on memory utilization when the defined threshold is breached for at least 120 seconds.  See the [App AutoScaler User Guide](https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/Readme.md){: external} for more information about how to create your own autoscaling policy.

3. Attach the policy to your app by running the following command:

    ```text
    ibmcloud cf aasp <YOUR_APP> <YOUR_POLICY_FILE>
    ```
    {: pre}

#### Metric statistics
{: #metric_statistics_cli}

You can query the most recent aggregated metrics for your app. The App Autoscaler supports multiple [metric types](https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/Readme.md#metric-types){: external}, but you can retrieve only the metrics that are defined in your policy.  For example, `memoryutil` in the previous CLI example.  

```text
ibmcloud cf asm <YOUR_APP> <METRIC_TYPE> --desc
```
{: pre}


#### Scaling history
{: #scaling_history_cli}

You can use the following command to query autoscaling history for an app.

```text
ibmcloud cf ash <YOUR_APP> --desc
```
{: pre}


## More information about autoscaling

* [Cloud Foundry App Autoscaler CLI plug-in guide](https://github.com/cloudfoundry/app-autoscaler-cli-plugin#cloud-foundry-cli-autoscaler-plug-in-){: external}

* [Best practices when setting up autoscaling policies](https://www.ibm.com/cloud/blog/autoscale-your-cloud-foundry-applications-on-ibm-cloud){: external}

* [Bring Your Own Metrics to Autoscale Your {{site.data.keyword.ibmcf_notm}} Apps](https://www.ibm.com/cloud/blog/bring-your-own-metrics-to-autoscale-your-ibm-cloud-foundry-applications){: external}



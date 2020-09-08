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

# Migrating from the legacy Auto-Scaling service
{: #autoscale_migration}

This new App Autoscaler offering is a replacement of the legacy. By migrating to the new autoscaler, you will have the following benefits:

* Simplified experience: No service creation and binding are needed to use the auto-scaling feature. You can directly configure the policy through the UI or CLI.

* No need to re-stage your app: You do not need to re-stage your {{site.data.keyword.ibmcf_full}} apps to make the auto-scaling take effect.

* Runtime independent: The app-autoscaler works for all language runtimes with the same user experience and same set of supported metrics.

* No code injection: The new autoscaler does not require an autoscaler agent to be included in your code if you are using IBM runtimes and buildpacks. You simply set the policy and after a while,  the autoscaler will start collecting metrics and scale your app based on the metrics you defined in the policy.

* Matching pace with the Cloud Foundry community: Future features of the app-autoscaler open-source project, will be available without delay in {{site.data.keyword.cloud}}.

We provide similar user experience between the legacy offering and the new one, including the policy definition, metric statistics and scaling history retrieving.

Running with both offering simultaneously may lead to unexpected scaling behavior, so we recommend you to migrate from the legacy Auto-Scaling service to the new App Autoscaler.  You can achieve this from the {{site.data.keyword.cloud}} user interface with below steps:

## Migrate through web UI

1. (Optional) Convert the autoscaling policy

  The policy definition in new autoscaler is different than the one in legacy Auto-Scaling service. If you want to reuse the existing policy, you will need to convert it to the new format. A simple policy migration utility is also provided to help convert the policy.

  - From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg), and select **Resource List**.
  - On the **Resource List** page, click **Cloud Foundry Apps**.
  - Click the app to view its **Overview** page.
  - Select **Connections** in the left navigation pane, and hover the legacy **Auto-Scaling** service instance entry
  - Click on **Auto-Scaling** service instance link to view its service dashboard,  then select **Policy** tab.
  - Click the button **Policy Migration**, copy the new `App Autoscaler` policy on the right side to your clipboard and save it as a local file.

  **Note**: The new Autoscaler doesn't support **HeapUsage** metric particularly for Liberty and Node.js runtime. As a result, the _Heap Usage_ related rules will be discarded during the conversion.  You need to use other metrics, such as "cpu", "memoryused", "memoryutil", "response" or "throughput" in the new  `App Autocaler`.

  Refer to [legacy Auto-Scaling policy JSON specification][legacy_autoscaling_policy] and [App Autoscaler policy JSON specification][autoscaling_policy] to get the detailed policy definitions.

2. Unbind legacy **Auto-scaling** service

   - Go back to the **Connections** view, and hover over the legacy **Auto-Scaling** service instance entry.
   - Click on the **menu** button in the right of the legacy **Auto-Scaling** service instance entry.
   - From the drop-down list, select **Unbind service** or **Delete service** as applicable.

3. Create a scaling policy in the new App Autoscaler offering.

   - Select the **Autoscaling** menu from the left navigation pane to access the new App-Autoscaler dashboard.
   - If you want to use the exported `App-Autoscaler` policy that was converted from the legacy Auto-Scaling service in previous steps, select **Import From JSON** to create a autoscaling policy. Or use **Create Auto-Scaling policy** to create a new one from scratch. Refer to the [get started][autoscaler-get-started] guide for details.

## Migrate through command line interface

Alternatively, you can use command lines to migrate over.

1. Create a App-Autoscaler policy

   - If you already exported the converted new policy as described in above steps, just save it to a local file.
   - If you would like to convert the policy by yourself, take the below steps:
      - Retrieve the existing policy using [Auto-scaling service CLI plugin][legacy-autoscaling-cli]:
        ```
        ibmcloud as policy-show <APP_NAME> [--json]
        ```
        {: pre}
        ```
      - Covert the policy manually to new format.

    Refer to [legacy Auto-Scaling policy JSON specification][legacy_autoscaling_policy] and [App Autoscaler policy JSON specification][autoscaling_policy] for the detailed policy format.

2. Unbind the legacy service instance from your app with Cloud Foundry Command Line tool:

   ```
   ibmcloud cf unbind-service <YOUR_APP> <YOUR_SERVICE_INSTANCE>
   ```
   {: pre}

3. Attach policy to enable new autoscaling experience.

   Now you can attach the new policy to your app through the new [AutoScaler CLI]:   

   ```
   ibmcloud cf aasp <YOUR_APP> <YOUR_POLICY_FILE>
   ```
   {: pre}


[autoscaler_project]: https://github.com/cloudfoundry/app-autoscaler
[autoscaler_user_guide]: https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/Readme.md
[autoscaling_policy]:https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/policy.md
[autoscaler_cli]: https://github.com/cloudfoundry/app-autoscaler-cli-plugin#cloud-foundry-cli-autoscaler-plug-in-
[metric_type]:https://github.com/cloudfoundry/app-autoscaler/blob/master/docs/Readme.md#metric-types
[deploy_app]: https://{DomainName}/docs/cloud-foundry-public/deploy-apps.html#dep_apps
[autoscaler-get-started]: https://{DomainName}/docs/cloud-foundry-public?topic=cloud-foundry-public-autoscale_cloud_foundry_apps#autoscale_cloud_foundry_apps



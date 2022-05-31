---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Use the monthly runtime
{: #using_monthly_runtime}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

The Liberty monthly runtime provides the latest version and access to new functionality and programming models.

To use the Liberty monthly runtime in {{site.data.keyword.cloud_notm}}, you will need to do the following:

Set the `JBP_CONFIG_LIBERTY` environment variable to `"version: +"` and `IBM_LIBERTY_MONTHLY` environment variable to `true`. These variables enable the [Liberty monthly runtime](/docs/cloud-foundry-public?topic=cloud-foundry-public-buildpack_defauts#liberty_versions). For example:

* Using the {{site.data.keyword.cloud_notm}} CLI tool:
      
    ```text
    ibmcloud cf set-env <yourappname> JBP_CONFIG_LIBERTY "version: +"
    ```
    {: .pre}
    
    ```text
    ibmcloud cf set-env <yourappname> IBM_LIBERTY_MONTHLY true
    ```
    {: .pre}

* Or, using the `manifest.yml` file:
    
    ```yaml
    env:
        JBP_CONFIG_LIBERTY: "version: +"
        IBM_LIBERTY_MONTHLY: true
    ```
    {: codeblock}

    ```yaml
    env:
        JBP_CONFIG_LIBERTY: "[version: +, app_archive: {features: [javaee-8.0]}]"
        IBM_LIBERTY_MONTHLY: true
    ```
    {: .codeblock}

If you are enabling the monthly runtime on an existing app you may need to delete and re-push your app after you set the environment variables.



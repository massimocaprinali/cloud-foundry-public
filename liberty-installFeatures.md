---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Install Liberty features
{: #install-features}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

The Liberty for Java runtime includes [a subset of features](/docs/cloud-foundry-public?topic=cloud-foundry-public-liberty_features#liberty_features) that are available in Liberty. You can install features that are not included in the runtime by running the Liberty `installUtility` command as a Cloud Foundry pre-runtime hook when the app is pushed to {{site.data.keyword.cloud_notm}}.

For a full list of available features, see [Liberty features](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/rwlp_feat.html){: external}.

For information on using pre-runtime hooks, see [Configure Pre-Runtime Hooks](https://docs.cloudfoundry.org/devguide/deploy-apps/deploy-app.html#profile){: external} in the Cloud Foundry documentation.

1. In the root directory of the app that you want to push to {{site.data.keyword.cloud_notm}}, create a `.profile.d` directory.

2. In the `.profile.d` directory, create a script file that runs the `installUtility` command as shown in the following example.

    This example installs the `audit-1.0` feature.

    ```text
    #!/bin/sh
    echo "Installing audit-1.0"
    export PATH=$PATH:$HOME/app/.java/jre/bin

    $HOME/app/.liberty/bin/installUtility install audit-1.0 --acceptLicense
    ```
    {: codeblock}

    You can install multiple features by specifying additional features names separated by spaces.
    {: tip}

3. Push your app to {{site.data.keyword.cloud_notm}}, using the `-p` option to specify the app's root directory.

   For example, run the following command to push your app:

   ```text
   ibmcloud cf push myApp -p /<path-to-app>
   ```
   {: codeblock}

4. Verify that the feature installed successfully by viewing the app's recent log.

    For example, run the following command to display the log:
  
    ```text
    ibmcloud cf logs myApp --recent
    ```
    {: codeblock}

    If the feature was installed, the output shows the following messages:

    ```text
    2018-09-18T13:01:17.61-0400 [APP/PROC/WEB/0] OUT Installing audit-1.0
    2018-09-18T13:01:19.13-0400 [APP/PROC/WEB/0] OUT Establishing a connection to the configured repositories ...
    2018-09-18T13:01:19.13-0400 [APP/PROC/WEB/0] OUT This process might take several minutes to complete.
    2018-09-18T13:01:21.28-0400 [APP/PROC/WEB/0] OUT Successfully connected to all configured repositories.
    2018-09-18T13:01:21.28-0400 [APP/PROC/WEB/0] OUT Preparing assets for installation. This process might take several minutes to complete.
    2018-09-18T13:01:25.87-0400 [APP/PROC/WEB/0] OUT The --acceptLicense argument was found. This indicates that you have
    2018-09-18T13:01:25.87-0400 [APP/PROC/WEB/0] OUT accepted the terms of the license agreement.
    ```
    {: screen}



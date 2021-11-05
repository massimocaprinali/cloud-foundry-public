---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Download, modify, and redeploy your Cloud Foundry app with the command-line interface
{: #cf-deploy-cli}



Use the {{site.data.keyword.ibmcf_full}} command-line interface (CLI) to download, modify, and redeploy your Cloud Foundry apps and service instances.
{: shortdesc}

Before you begin, [download and install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started).

Then install the {{site.data.keyword.ibmcf_notm}} CLI by running the following command:

```text
ibmcloud cf install
```
{: pre}


After you install the CLI, you can get started:

1. Change to the directory where your code is located.

    ```text
    cd <your_new_directory>
    ```
    {: pre}

2. Make changes to your app code as you see fit. For example, if you are using an {{site.data.keyword.cloud_notm}} sample app and your app contains the `src/main/webapp/index.html` file, you can modify it and edit "Thanks for creating ..." to say something new. Ensure the app runs locally before you deploy it back to {{site.data.keyword.cloud_notm}}.

    When deploying your app back to {{site.data.keyword.cloud_notm}}, the `manifest.yml` is used to determine your app’s URL, memory allocation, number of instances, and other crucial options . You can [read more about the manifest file](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html){: external} in the Cloud Foundry documentation.

    Also pay attention to the `README.md` file, which contains details such as any applicable build instructions.

    If your app is a Liberty app, you must build it before redeploying.
    {: note}

3. Log in to {{site.data.keyword.cloud_notm}} with your IBMid. If you have multiple accounts, you will be prompted to select the account to use. If you do not specify a region with the `-r` flag, you must also select a region.

    ```text
    ibmcloud login
    ```
    {: pre}

    If your credentials are rejected, you might be using a federated ID. To log in with a federated ID, use the `--sso` flag. See [Logging in with a federated ID](/docs/account?topic=account-federated_id) for more details.
    {: tip}

4. To access Cloud Foundry services, you must specify a Cloud Foundry org and space. You can run the following command to be prompted to indicate your org and space:

    ```text
    ibmcloud target --cf
    ```
    {: pre}

    Or, if you know the org and space the service belongs to, you can use the following command:

    ```text
    ibmcloud target -o <org name> -s <space name>
    ```
    {: pre}

5. From `<your_new_directory>`, redeploy your app to {{site.data.keyword.cloud_notm}} by using the `ibmcloud cf push` command. For more information, see [`ibmcloud cf push`](/docs/cli?topic=cli-ibmcloud_commands_apps#ibmcloud_app_push).

6. Access your app by browsing to the app URL.



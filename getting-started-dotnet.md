---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Getting started with ASP.NET Core
{: #getting_started-dotnet}

Congratulations, you deployed a Hello World sample app on {{site.data.keyword.cloud}}!  To get started, follow this step-by-step guide. Or, [download the sample code](https://github.com/IBM-Cloud/get-started-aspnet-core){: external} and explore on your own.


By following this getting started tutorial, you'll set up a development environment, deploy an app locally and on {{site.data.keyword.cloud}}, and integrate an {{site.data.keyword.cloud}} database service in your app. The ASP.NET core is complied into a .dll package. You can deploy the app with the code or with the precompiled file (.DLL) of your app.
{: shortdesc}

## Before you begin
{: #prereqs-dotnet}

You'll need the following:
* [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/registration){: external}
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started)
* [Git](https://git-scm.com/downloads){: external}
* Install .NET Core SDK 3.1 from the [.NET Core downloads website](https://dotnet.microsoft.com/download){: external}.

## Step 1: Clone the sample app
{: #clone}

First, clone the sample app GitHub repo.

```text
git clone https://github.com/IBM-Cloud/get-started-aspnet-core
```
{: pre}


## Step 2: Run the app locally
{: #run_locally}

1. On the command line, change the directory to where the sample app is located.

    ```text
    cd get-started-aspnet-core/src/GetStartedDotnet
    ```
    {: pre}

2. Run the app locally by running the following commands.

    ```text
    dotnet restore
    ```
    {: pre}

    ```text
    dotnet run
    ```
     {: pre}

3. View your app at: `http://localhost:5000/`.

## Step 3: Prepare the app for deployment
{: #prepare-dotnet}

To deploy to {{site.data.keyword.cloud_notm}}, it can be helpful to set up a `manifest.yml` file. The `manifest.yml` file includes basic information about your app, such as the name, how much memory to allocate for each instance and the route. We've provided a sample manifest.yml file in the `get-started-dotnet` directory.

Open the manifest.yml file, and change the `name` from `GetStartedDotnet` to your app name, `app_name`.

```yaml
apps:
- name: GetStartedDotnet
  random-route: true
  memory: 512M
```
{: codeblock}

In this `manifest.yml` file, `random-route: true` generates a random route for your app to prevent your route from colliding with others.  If you choose to, you can replace `random-route: true` with `host: myChosenHostName`, supplying a host name of your choice.
{: tip}

## Step 4: Deploy the app
{: #deploy}

You can use the {{site.data.keyword.cloud_notm}} CLI to deploy apps.

1. Log in to your {{site.data.keyword.cloud_notm}} account, and select an API endpoint.
  
    ```text
    ibmcloud login
    ```
    {: pre}

    If you have a federated user ID, instead use the following command to log in with your single sign-on ID. See [Logging in with a federated ID](/docs/account?topic=account-federated_id) to learn more.
 
    ```text
    ibmcloud login --sso
    ```
    {: pre}

2. Target a Cloud Foundry org and space:
 
    ```text
    ibmcloud target --cf
    ```
    {: pre}

    If you don't have an org or a space set up, see [Adding orgs and spaces](/docs/account?topic=account-orgsspacesusers).
    {: tip}

3. **Be sure you are in the main directory, `get-started-aspnet-core`, for your app**  then push your app to {{site.data.keyword.cloud_notm}}:
 
    ```text
    ibmcloud cf push
    ```
    {: pre}

    This can take a minute. If there is an error in the deployment process, you can use the command `ibmcloud cf logs <Your-App-Name> --recent` to troubleshoot.

When deployment completes, you should see a message indicating that your app is running.  View your app at the URL listed in the output of the push command.  You can also issue the following command to view your app's status and to see the URL.
 
```text
ibmcloud cf apps
```
{: pre}

You can also go to the {{site.data.keyword.cloud_notm}} [Resource List](https://cloud.ibm.com/resources){: external} to view your app.

## Step 5: Add a database
{: #add_database}

Next, we'll add an {{site.data.keyword.cloudant_short_notm}} NoSQL database to this app and set up the app so that it can run locally and on {{site.data.keyword.cloud_notm}}.

1. In your browser, log in to {{site.data.keyword.cloud_notm}} and go to the Dashboard. Select **Create resource**.

2. Search for **{{site.data.keyword.cloudant_short_notm}}**, and select the service.

3. For **Available authentication methods**, select **Use both legacy credentials and IAM**. You can leave the default settings for the other fields. Click **Create** to create the service.

4. In the navigation, go to **Connections**, then click **Create connection**. Select your app, and click **Connect**.

5. Using the default values, click **Connect & restage app** to connect the database to your app. Click **Restage** when prompted.

    {{site.data.keyword.cloud_notm}} will restart your app and provide the database credentials to your app using the `VCAP_SERVICES` environment variable. This environment variable is available to the app only when it is running on {{site.data.keyword.cloud_notm}}.

Environment variables enable you to separate deployment settings from your source code. For example, instead of specifying a database password in your source code, you can store it in an environment variable that you reference in your source code.
{: tip}

## Step 6: Use the database locally
{: #use_database}

We're now going to update your local code to point to this database. We'll store the credentials for the services in a JSON file. This file will get used ONLY when the app is running locally. When running in {{site.data.keyword.cloud_notm}}, the credentials will be read from the `VCAP_SERVICES` environment variable.

1. In the `src/GetStartedDotnet` directory, create a `vcap-local.json` file.

2. Copy and paste the following JSON object into the `vcap-local.json` file, and save your changes.

    ```json
    {
      "services": {
        "cloudantNoSQLDB": [
          {
            "credentials": {
              "url":"CLOUDANT_DATABASE_URL"
            },
            "label": "cloudantNoSQLDB"
          }
        ]
      }
    }
    ```
    {: codeblock}

3. Find your app in the {{site.data.keyword.cloud_notm}} [Resource List](https://cloud.ibm.com/resources){: external}. On the Service Details page for your app, click **Connections** in the sidebar. Click the {{site.data.keyword.cloudant_short_notm}} menu icon (**&hellip;**) and select **View credentials**.

4. Copy and paste just the `url` value from the credentials to the `url` field of the `vcap-local.json` file, replacing `CLOUDANT_DATABASE_URL`.

5. From the `get-started-aspnet-core/src/GetStartedDotnet` directory, restart your app by running the following command.

    ```text
    dotnet run
    ```
    {: pre}

6. Refresh your browser view at `http://localhost:5000/`. Any names you enter into the app will now get added to the database.

Your local app and the {{site.data.keyword.cloud_notm}} app share the database.  View your {{site.data.keyword.cloud_notm}} app at the URL listed in the output of the `ibmcloud cf push` command.  Names you add from either app should appear in both when you refresh the browsers.

Remember, if you don't need your app live, stop it so you don't incur any unexpected charges.
{: tip}

## Next Steps

* [Samples](https://ibm-cloud.github.io){: external}

* [Architecture Center](https://www.ibm.com/cloud/architecture/architectures){: external}



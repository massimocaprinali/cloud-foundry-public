---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Getting started with Ruby
{: #getting-started-ruby}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Congratulations, you deployed a Hello World sample app on {{site.data.keyword.cloud}}!  To get started, follow this step-by-step guide. Or, [download the sample code](https://github.com/IBM-Cloud/get-started-ruby){: external} and explore on your own.


By following this getting started tutorial, you'll set up a development environment, deploy an app locally on {{site.data.keyword.cloud}}, and integrate a database service in your app.
{: shortdesc}

Throughout these docs, references to the Cloud Foundry CLI are now updated to the {{site.data.keyword.cloud_notm}} CLI! The {{site.data.keyword.cloud_notm}} CLI has the same familiar Cloud Foundry commands, but with better integration with {{site.data.keyword.cloud_notm}} accounts and other services. Learn more about getting started with the {{site.data.keyword.cloud_notm}} CLI in this tutorial.
{: tip}

## Before you begin
{: #prereqs-ruby}

You'll need the following:

* [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/registration){: external}
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli)
* [Git](https://git-scm.com/downloads){: external}
* [Ruby](https://www.ruby-lang.org/en/downloads/){: external}
* [`rbenv`](https://github.com/rbenv/rbenv#installation){: external}

## Step 1: Clone the sample app
{: #clone-ruby}

First, clone the repo and change the directory to where the sample app is located.

```text
git clone https://github.com/IBM-Cloud/get-started-ruby
```
{: pre}

```text
cd get-started-ruby
```
{: pre}


## Step 2: Run the app locally (optional)
{: #run_locally-ruby}

1. Run the app locally by running the following commands.
 
    ```text
    rbenv install 2.3.0
    ```
    {: pre}

    ```text
    rbenv local 2.3.0
    ```
    {: pre}

    ```text
    gem install bundler
    ```
    {: pre}

    ```text
    bundle install
    ```
    {: pre}

    ```text
    rails server
    ```
    {: pre}

2. View your app at the following URL: `http://localhost:3000`

## Step 3: Prepare the app for deployment
{: #prepare-ruby}

To deploy to {{site.data.keyword.cloud_notm}}, it can be helpful to set up a `manifest.yml` file. The `manifest.yml` file includes basic information about your app, such as the name, how much memory to allocate for each instance and the route. We've provided a sample `manifest.yml` file in the `get-started-ruby` directory.

Open the `manifest.yml` file, and change the `name` from `GetStartedRuby` to your app name, `app_name`.

```yaml
apps:
- name: GetStartedRuby
  random-route: true
  memory: 128M
```
{: codeblock}

In this `manifest.yml` file, `random-route: true` generates a random route for your app to prevent your route from colliding with others.  If you choose to, you can replace `random-route: true` with `host: myChosenHostName`, supplying a host name of your choice.
{: tip}

## Step 4: Deploy the app
{: #deploy-ruby}

You can use the {{site.data.keyword.Bluemix_short}} CLI to deploy apps.

1. Log in to your {{site.data.keyword.Bluemix_short}} account, and select an API endpoint.

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

3. From within the `get-started-node` directory, push your app to {{site.data.keyword.Bluemix_short}}.

    ```text
    ibmcloud cf push
    ```
    {: pre}

    This can take a minute. If there is an error in the deployment process you can use the command `ibmcloud cf logs <Your-App-Name> --recent` to troubleshoot.

When deployment completes you should see a message indicating that your app is running.  View your app at the URL listed in the output of the push command.  You can also issue the following command to view your apps status and see the URL.

```text
ibmcloud cf apps
```
{: pre}

You can also go to the {{site.data.keyword.cloud_notm}} [resource list](https://cloud.ibm.com/resources){: external} to view your app.

## Step 5: Add a database
{: #add_database-ruby}

Next, we'll add an {{site.data.keyword.cloudant_short_notm}} NoSQL database to this app and set up the app so that it can run locally and on {{site.data.keyword.cloud_notm}}.

1. In your browser, log in to {{site.data.keyword.cloud_notm}} and go to the Dashboard. Select **Create resource**.

2. Search for **{{site.data.keyword.cloudant_short_notm}}**, and select the service.

3. For **Available authentication methods**, select **Use both legacy credentials and IAM**. You can leave the default settings for the other fields. Click **Create** to create the service.

4. In the navigation, go to **Connections**, then click **Create connection**. Select your app, and click **Connect**.

5. Using the default values, click **Connect & restage app** to connect the database to your app. Click **Restage** when prompted.

    {{site.data.keyword.cloud_notm}} will restart your app and provide the database credentials to your app using the `VCAP_SERVICES` environment variable. This environment variable is available to the app only when it is running on {{site.data.keyword.cloud_notm}}.

Environment variables enable you to separate deployment settings from your source code. For example, instead of specifying a database password in your source code, you can store it in an environment variable that you reference in your source code.
{: tip}

## Step 6: Use the database
{: #use_database-ruby}

We're now going to update your local code to point to this database. We'll create a `.env` file that will store the credentials for the services the app will use. This file will get used ONLY when the app is running locally. When running in {{site.data.keyword.cloud_notm}}, the credentials will be read from the VCAP_SERVICES environment variable.

1. Create a file called `.env` in the `get-started-ruby` directory with the following content:

    ```text
    CLOUDANT_URL=
    ```
    {: codeblock}

2. Find your app in the {{site.data.keyword.cloud_notm}} [resource list](https://cloud.ibm.com/resources){: external}. On the Service Details page for your app, click **Connections** in the sidebar. Click the {{site.data.keyword.cloudant_short_notm}} menu icon (**&hellip;**) and select **View credentials**.

3. Copy and paste just the `url` from the credentials to the `CLOUDANT_URL` field of the `.env` file and save the changes.  The result will be something like:

    ```text
    CLOUDANT_URL=https://123456789 ... bluemix.cloudant.com
    ```
    {: codeblock}

4. Run your app locally.

    ```text
    rails server
    ```
    {: pre}

    View your app at: `http://localhost:3000`. Any names you enter into the app will now get added to the database.

    Your local app and the {{site.data.keyword.cloud_notm}} app are sharing the database.  View your {{site.data.keyword.cloud_notm}} app at the URL listed in the output of the push command from above.  Names you add from either app should appear in both when you refresh the browsers.

    If you don't need your app live, stop it so you don't incur any unexpected charges.
    {: tip}

## Next steps
{: #nextsteps-ruby}

* [Samples](https://ibm-cloud.github.io){: external}
* [Architecture Center](https://www.ibm.com/cloud/architecture/architectures){: external}



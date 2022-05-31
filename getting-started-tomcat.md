---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Getting started with Tomcat
{: #getting-started-tomcat}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Congratulations, you deployed a Hello World sample app on {{site.data.keyword.cloud}}!  To get started, follow this step-by-step guide. Or, [download the sample code](https://github.com/IBM-Cloud/get-started-tomcat){: external} and explore on your own.


By following this getting started tutorial, you'll set up a development environment, deploy an app locally on {{site.data.keyword.cloud}}, and integrate a database service in your app.
{: shortdesc}

Throughout these docs, references to the Cloud Foundry CLI are now updated to the {{site.data.keyword.cloud_notm}} CLI! The {{site.data.keyword.cloud_notm}} CLI has the same familiar Cloud Foundry commands, but with better integration with {{site.data.keyword.cloud_notm}} accounts and other services. Learn more about getting started with the {{site.data.keyword.cloud_notm}} CLI in this tutorial.
{: tip}

## Before you begin
{: #prereqs-tomcat}

You'll need the following:

* [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/registration){: external}
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli)
* [Git](https://git-scm.com/downloads){: external}
* [Maven](https://maven.apache.org/download.cgi){: external}
* [Apache Tomcat version 8.0.41](https://tomcat.apache.org/download-80.cgi#8.0.41 ){: external}


## Step 1: Clone the sample app
{: #clone-tomcat}

Clone the repository and change to the directory to where the sample app is located.

```text
git clone https://github.com/IBM-Cloud/get-started-tomcat
```
{: pre}

```text
cd get-started-tomcat
```
{: pre}

Review the files in the `get-started-tomcat` directory to familiarize yourself with the contents.

## Step 2: Run the app locally
{: #run_locally-tomcat}

You must install the dependencies and build a `.war` file as defined in the `pom.xml` file to run the app.

1. Install the dependencies.
  
    ```text
    mvn clean install  
    ```
    {: pre}

2. Copy the `GetStartedTomcat.war` file from the `target` directory into your `tomcat-install-dir` `webapps` directory.

3. Run the app.  
  
    ```text
    <tomcat-install-dir>/bin/startup.bat|.sh
    ```
    {: pre}

4. View your app the following URL: `http://localhost:8080/GetStartedTomcat/`

    Use `shutdown.bat|.sh` to stop your app.  Note you may need to give the commands execute permission.
    {: tip}

## Step 3: Prepare the app for {{site.data.keyword.cloud_notm}} deployment
{: #prepare-tomcat}

To deploy to {{site.data.keyword.cloud_notm}}, it can be helpful to set up a `manifest.yml` file. The `manifest.yml` file includes basic information about your app, such as the name, how much memory to allocate for each instance and the route. We've provided a sample `manifest.yml` file in the `get-started-tomcat` directory.

Open the `manifest.yml` file, and change the `name` from `GetStartedTomcat` to your app name, `app_name`.

```yaml
apps:
- name: GetStartedTomcat
  random-route: true
  memory: 256M
  path: target/GetStartedTomcat.war
  buildpack: java_buildpack
```
{: codeblock}

In this `manifest.yml` file, `random-route: true` generates a random route for your app to prevent your route from colliding with others.  If you choose to, you can replace `random-route: true` with `host: myChosenHostName`, supplying a host name of your choice.
{: tip}

## Step 4: Deploy the app
{: #deploy-tomcat}

You can use the {{site.data.keyword.cloud}} CLI to deploy apps.

1. Log in to your {{site.data.keyword.cloud}} account, and select an API endpoint.

    ```text
    ibmcloud login
    ```
    {: pre}

    If you have a federated user ID, instead use the following command to log in with your single sign-on ID. See [Logging in with a federated ID](/docs/account?topic=account-federated_id) for more information.

    ```text
    ibmcloud login --sso
    ```
    {: pre}

2. Next, target a Cloud Foundry org and space:
  
    ```text	  
    ibmcloud target --cf
    ```
    {: pre}

    If you don't have an org or a space set up, see [Adding orgs and spaces](/docs/account?topic=account-orgsspacesusers).
    {: tip}

3. From within the `get-started-tomcat` directory, push your app to {{site.data.keyword.cloud_notm}}

    ```text
    ibmcloud cf push
    ```
    {: pre}

    This can take around two minutes. If there is an error in the deployment process you can use the command `ibmcloud cf logs <Your-App-Name> --recent` to troubleshoot.

When deployment completes you should see a message indicating that your app is running.  View your app at the URL listed in the output of the push command.  You can also issue the following command to view your apps status and see the URL.

```text
ibmcloud cf apps
```
{: pre}

You can also go to the {{site.data.keyword.cloud_notm}} [resource list](https://cloud.ibm.com/resources){: external} to view your app.

## Step 5: Add a database
{: #add_database-tomcat}

Next, we'll add an {{site.data.keyword.cloudant_short_notm}} NoSQL database to this app and set up the app so that it can run locally and on {{site.data.keyword.cloud_notm}}.

1. In your browser, log in to {{site.data.keyword.cloud_notm}} and go to the dashboard. Select **Create resource**.

2. Search for **{{site.data.keyword.cloudant_short_notm}}**, and select the service.

3. For **Available authentication methods**, select **Use both legacy credentials and IAM**. You can leave the default settings for the other fields. Click **Create** to create the service.

4. In the navigation, go to **Connections**, then click **Create connection**. Select your app, and click **Connect**.

5. Using the default values, click **Connect & restage app** to connect the database to your app. Click **Restage** when prompted.

    {{site.data.keyword.cloud_notm}} will restart your app and provide the database credentials to your app using the `VCAP_SERVICES` environment variable. This environment variable is available to the app only when it is running on {{site.data.keyword.cloud_notm}}.

Environment variables enable you to separate deployment settings from your source code. For example, instead of specifying a database password in your source code, you can store it in an environment variable that you reference in your source code.
{: tip}

## Step 6: Use the database
{: #use_database-tomcat}

We're now going to update your local code to point to this database. We'll store the credentials for the services in a properties file. This file will get used ONLY when the app is running locally. When running in {{site.data.keyword.cloud_notm}}, the credentials will be read from the `VCAP_SERVICES` environment variable.

1. Find your app in the {{site.data.keyword.cloud_notm}} [resource list](https://cloud.ibm.com/resources){: external}. On the Service Details page for your app, click **Connections** in the sidebar. Click the {{site.data.keyword.cloudant_short_notm}} menu icon (**&hellip;**) and select **View credentials**.

2. Copy and paste just the `url` from the credentials to the `url` field of the `cloudant.properties` file, and save the changes.
  
    ```text
    cloudant_url=https://123456789 ... bluemix.cloudant.com
    ```
    {: codeblock}

3. Restart the server

Refresh your browser view at: `http://localhost:8080/GetStartedTomcat/`. Any names you enter into the app will now get added to the database.

Your local app and the {{site.data.keyword.cloud_notm}} app are sharing the database. Names you add from either app will appear in both when you refresh the browsers.

Remember, if you don't need your app live on {{site.data.keyword.cloud_notm}}, stop the app so you don't incur any unexpected charges.
{: tip}  

## Next steps
{: #nextsteps-tomcat}

* [Samples](https://ibm-cloud.github.io){: external}
* [Architecture Center](https://www.ibm.com/cloud/architecture/architectures){: external}



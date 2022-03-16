---

copyright:
  years: 2015, 2022
lastupdated: "2022-03-08"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Getting started with SDK for Node.js
{: #getting-started-node}



Congratulations, you deployed a Hello World sample app on {{site.data.keyword.cloud}}!  To get started, follow this step-by-step guide. Or, [download the sample code](https://github.com/IBM-Cloud/get-started-node){: external} and explore on your own.


By following this tutorial, you'll set up a development environment, deploy an app locally on {{site.data.keyword.cloud}}, and integrate an {{site.data.keyword.cloud_notm}} database service in your app.
{: shortdesc}

Throughout these docs, references to the Cloud Foundry CLI are now updated to the {{site.data.keyword.cloud_notm}} CLI! The {{site.data.keyword.cloud_notm}} CLI has the same familiar Cloud Foundry commands, but with better integration with {{site.data.keyword.cloud_notm}} accounts and other services. Learn more about getting started with the {{site.data.keyword.cloud_notm}} CLI in this tutorial.
{: tip}

## Before you begin
{: #prereqs-node}

Note the [Node.js buildpack change](http://ibm.biz/cf-buildpack-node-change){: external} details regarding buildpack types and build order.
{: important}


You'll need the following accounts and tools:

* [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/registration){: external}
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-install-ibmcloud-cli)
* [Git](https://git-scm.com/downloads){: external}
* [Node](https://nodejs.org/en/){: external}


## Step 1: Clone the sample app
{: #clone-node}

First, clone the Node.js *hello world* sample app GitHub repo.

```text
git clone https://github.com/IBM-Cloud/get-started-node
```
{: pre}

## Step 2: Run the app locally
{: #run_locally-node}

Use the NPM package manager to install dependencies and run your app.

1. On the command line, change the directory to where the sample app is located.
  
    ```text
    cd get-started-node
    ```
    {: pre}

2. Install the dependencies listed in the [package.json](https://docs.npmjs.com/files/package.json){: external} file to run the app locally.  
  
    ```text
    npm install
    ```
    {: pre}

3. Run the app.
 
    ```text
    npm start  
    ```
    {: pre}

4. View your app at the following URL: `http://localhost:3000`

Use [`nodemon`](https://nodemon.io/){: external} for automatic restarting of app on file changes.
{: tip}

## Step 3: Prepare the app for deployment
{: #prepare-node}

To deploy to {{site.data.keyword.cloud_notm}}, it can be helpful to set up a `manifest.yml` file. The `manifest.yml` file includes basic information about your app, such as the name, how much memory to allocate for each instance and the route. We've provided a sample `manifest.yml` file in the `get-started-node` directory.

Open the `manifest.yml` file, and change the `name` from `GetStartedNode` to your app name, `app_name`.

```yaml
apps:
- name: GetStartedNode
  random-route: true
  memory: 128M
```
{: codeblock}

In this `manifest.yml` file, `random-route: true` generates a random route for your app to prevent your route from colliding with others.  If you choose to, you can replace `random-route: true` with `host: <myChosenHostName>`, supplying a host name of your choice.
{: tip}

## Step 4: Deploy the app
{: #deploy-node}

You can use the {{site.data.keyword.cloud_notm}} CLI to deploy apps to {{site.data.keyword.cloud_notm}}.

1. Log in to your {{site.data.keyword.cloud_notm}} account, and select an API endpoint.

    ```text
    ibmcloud login
    ```
    {: pre}

    If you have a federated user ID, instead use the following command to log in with your single sign-on ID. See [Logging in with a federated ID](/docs/account?topic=account-federated_id) for more information.
  
    ```text
    ibmcloud login --sso
    ```
   
    Target a Cloud Foundry org and space:

    ```text	  
    ibmcloud target --cf
    ```
    {: pre}

    If you don't have an org or a space set up, see [Adding orgs and spaces](/docs/account?topic=account-orgsspacesusers).
    {: tip}

2. From within the `get-started-node` directory, push your app to {{site.data.keyword.cloud_notm}}.

    ```text
    ibmcloud cf push
    ```
    {: pre}

Deploying your app can take a few minutes. When deployment completes, you'll see a message that your app is running. View your app at the URL listed in the output of the push command, or view both the app deployment status and the URL by running the following command:

```text
ibmcloud cf apps
```
{: pre}

You can also go to the {{site.data.keyword.cloud_notm}} [resource list](https://cloud.ibm.com/resources){: external} to view your app.

You can troubleshoot errors in the deployment process by using the `ibmcloud cf logs <Your-App-Name> --recent` command.
{: tip}

## Step 5: Add a database
{: #add_database-node}

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
{: #use_database-node}

We're now going to update your local code to point to this database. We'll create a JSON file that will store the credentials for the services the app will use. This file will get used ONLY when the app is running locally. When running in {{site.data.keyword.cloud_notm}}, the credentials will be read from the `VCAP_SERVICES` environment variable.

1. In the `get-started-node` directory, create a file called `vcap-local.json` with the following content:

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

2. Find your app in the {{site.data.keyword.cloud_notm}} [resource list](https://cloud.ibm.com/resources){: external}. On the Service Details page for your app, click **Connections** in the sidebar. Click the {{site.data.keyword.cloudant_short_notm}} menu icon (**&hellip;**) and select **View credentials**.

3. Copy and paste just the `url` from the credentials to the `url` field of the `vcap-local.json` file, replacing `CLOUDANT_DATABASE_URL`.

4. Run your app locally.
  
    ```text
    npm start  
    ```
    {: pre}

    View your local app at `http://localhost:3000`. Any names you enter into the app will now get added to the database.

**Avoid trouble**: {{site.data.keyword.cloud_notm}} defines the PORT environment variable when your app runs on the cloud. When you run your app locally, the PORT variable is not defined, so 3000 is used as the port number. See [Run your app locally](/docs/cloud-foundry-public?topic=cloud-foundry-public-hints) for more information.

Your local app and the {{site.data.keyword.cloud_notm}} app are sharing the database. Names you add from either app will appear in both when you refresh the browsers.

Remember, if you don't need your app live on {{site.data.keyword.cloud_notm}}, stop the app so you don't incur any unexpected charges.
{: tip}

## Next steps
{: #nextsteps-node}

[Manage your Node.js app](/docs/cloud-foundry-public?topic=cloud-foundry-public-nodejs_runtime). Some example tasks include configuring caching and integrating third-party services.


Check out the following resources:

* [Samples](https://ibm-cloud.github.io){: external}
* [Architecture Center](https://www.ibm.com/cloud/architecture/architectures){: external}



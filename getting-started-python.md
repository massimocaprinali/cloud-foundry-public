---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-09"

keywords: cloud foundry

subcollection: cloud-foundry-public



---



{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: #java .ph data-hd-programlang='java'}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vb.net: .ph data-hd-programlang='vb.net'}
{:video: .video}

# Getting started with Python
{: #getting-started-python}

<!-- This file is reused in the CF Public subcollection. -->

Congratulations, you deployed a Hello World sample application on {{site.data.keyword.cloud}}!  To get started, follow this step-by-step guide. Or, [download the sample code](https://github.com/IBM-Cloud/get-started-python) and explore on your own.
{: hide-in-docs}

By following the Python getting started tutorial, you'll set up a development environment, deploy an app locally on {{site.data.keyword.cloud}}, and integrate a database service in your app.

Throughout these docs, references to the Cloud Foundry CLI are now updated to the {{site.data.keyword.cloud_notm}} CLI! The {{site.data.keyword.cloud_notm}} CLI has the same familiar Cloud Foundry commands, but with better integration with {{site.data.keyword.cloud_notm}} accounts and other services. Learn more about getting started with the {{site.data.keyword.cloud_notm}} CLI in this tutorial.
{: tip}

## Before you begin
{: #prereqs-python}

You'll need the following:

* [{{site.data.keyword.cloud_notm}} account](https://cloud.ibm.com/registration)
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/reference/ibmcloud?topic=cloud-cli-install-ibmcloud-cli)
* [Git](https://git-scm.com/downloads){: external}
* [Python](https://www.python.org/downloads/){: external}

## Step 1: Clone the sample app
{: #clone-python}

First, clone the repo and change to the directory where the sample app is located.

  ```
git clone https://github.com/IBM-Cloud/get-started-python
  ```
  {: pre}

  ```
cd get-started-python
  ```
  {: pre}

Peruse the files in the *get-started-python* directory to familiarize yourself with the contents.

## Step 2: Run the app locally
{: #run_locally-python}

See [The Hitchhiker’s Guide to Python! ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://docs.python-guide.org/en/latest/) for help setting up Python on your system.
{: tip}

Install the dependencies listed in the [requirements.txt ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://pip.readthedocs.io/en/stable/user_guide/#requirements-files) file to be able to run the app locally.

You can optionally use a [virtual environment ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://packaging.python.org/installing/#creating-and-using-virtual-environments) to avoid having these dependencies clash with those of other Python projects or your operating system.

  ```
pip install -r requirements.txt
  ```
  {: pre}

Alternatively with Python3 you can issue

  ```
python3 -m pip install -r requirements.txt
  ```
  {: pre}

Run the app.
  ```
python hello.py
  ```
  {: pre}

 View your app at: http://localhost:8000


## Step 3: Prepare the app for deployment
{: #prepare-python}

To deploy to {{site.data.keyword.cloud_notm}}, it can be helpful to set up a manifest.yml file. The manifest.yml includes basic information about your app, such as the name, how much memory to allocate for each instance and the route. We've provided a sample manifest.yml file in the `get-started-python` directory.

Open the manifest.yml file, and change the `name` from `GetStartedPython` to your app name, <var class="keyword varname" data-hd-keyref="app_name">app_name</var>.
{: download}

  ```
  applications:
  - name: GetStartedPython
    random-route: true
    memory: 128M
  ```
  {: codeblock}

In this manifest.yml file, **random-route: true** generates a random route for your app to prevent your route from colliding with others.  If you choose to, you can replace **random-route: true** with **host: myChosenHostName**, supplying a host name of your choice.
{: tip}

## Step 4: Deploy the app
{: #deploy-python}

You can use the {{site.data.keyword.cloud_notm}} CLI to deploy apps.

1. Log in to your {{site.data.keyword.cloud_notm}} account, and select an API endpoint.

  ```
ibmcloud login
  ```
  {: pre}

  If you have a federated user ID, instead use the following command to log in with your single sign-on ID. See [Logging in with a federated ID](/docs/account?topic=account-federated_id) for more information.

  ```
ibmcloud login --sso
  ```
  {: pre}

1. Target a Cloud Foundry org and space:

  ```	  
ibmcloud target --cf
  ```
  {: pre}

  If you don't have an org or a space set up, see [Adding orgs and spaces](/docs/account?topic=account-orgsspacesusers).
  {: tip}

1. From within the *get-started-python* directory push your app to {{site.data.keyword.cloud_notm}}

  ```
ibmcloud cf push
  ```
  {: pre}

  This can take a minute. If there is an error in the deployment process you can use the command `ibmcloud cf logs <Your-App-Name> --recent` to troubleshoot.

When deployment completes you should see a message indicating that your app is running.  View your app at the URL listed in the output of the push command.  You can also issue the following command to view your apps status and see the URL.

  ```
ibmcloud cf apps
  ```
  {: pre}

You can also go to the {{site.data.keyword.cloud_notm}} [resource list ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/resources){: new_window} to view your app.

## Step 5: Add a database
{: #add_database-python}

Next, we'll add an {{site.data.keyword.cloudant_short_notm}} NoSQL database to this application and set up the application so that it can run locally and on {{site.data.keyword.cloud_notm}}.

1. In your browser, log in to {{site.data.keyword.cloud_notm}} and go to the Dashboard. Select **Create resource**.
1. Search for **{{site.data.keyword.cloudant_short_notm}}**, and select the service.
1. For **Available authentication methods**, select **Use both legacy credentials and IAM**. You can leave the default settings for the other fields. Click **Create** to create the service.
1. In the navigation, go to **Connections**, then click **Create connection**. Select your application, and click **Connect**.
1. Using the default values, click **Connect & restage app** to connect the database to your application. Click **Restage** when prompted.

   {{site.data.keyword.cloud_notm}} will restart your application and provide the database credentials to your application using the `VCAP_SERVICES` environment variable. This environment variable is available to the application only when it is running on {{site.data.keyword.cloud_notm}}.

Environment variables enable you to separate deployment settings from your source code. For example, instead of hardcoding a database password, you can store it in an environment variable that you reference in your source code.
{: tip}

## Step 6: Use the database
{: #use_database-python}

We're now going to update your local code to point to this database. We'll create a JSON file that will store the credentials for the services the application will use. This file will get used ONLY when the application is running locally. When running in {{site.data.keyword.cloud_notm}}, the credentials will be read from the VCAP_SERVICES environment variable.

1. Create a file called `vcap-local.json` in the `get-started-python` directory with the following content:

  ```
{
  "services": {
    "cloudantNoSQLDB": [
      {
        "credentials": {
          "username":"CLOUDANT_DATABASE_USERNAME",
          "password":"CLOUDANT_DATABASE_PASSWORD",
          "host":"CLOUDANT_DATABASE_HOST"
        },
        "label": "cloudantNoSQLDB"
      }
    ]
  }
}
  ```
  {: codeblock}

2. Find your app in the {{site.data.keyword.cloud_notm}} [resource list ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/resources){: new_window}. On the Service Details page for your app, click **Connections** in the sidebar. Click the {{site.data.keyword.cloudant_short_notm}} menu icon (**&hellip;**) and select **View credentials**.

3. Copy and paste the `username`, `password`, and `host` from the credentials to the same fields of the `vcap-local.json` file replacing **CLOUDANT_DATABASE_USERNAME**, **CLOUDANT_DATABASE_PASSWORD**, and **CLOUDANT_DATABASE_HOST**.

4. Run your application locally.

  ```
python hello.py
  ```
  {: pre}

View your app at: http://localhost:8000. Any names you enter into the app will now get added to the database.

Your local app and  the {{site.data.keyword.cloud_notm}} app are sharing the database.  View your {{site.data.keyword.cloud_notm}} app at the URL listed in the output of the push command from above.  Names you add from either app should appear in both when you refresh the browsers.

Remember, if you don't need your app live, stop it so you don't incur any unexpected charges.
{: tip}

## Next steps
{: #nextsteps-python}

* [Tutorials](/docs?tab=tutorials)
* [Samples ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm-cloud.github.io){: new_window}
* [Architecture Center ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/garage/category/architectures){: new_window}



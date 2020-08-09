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


# Getting started with Cloud Foundry Public
{: #getting-started}

<!-- Revamp the getting started to guide the user from the CF overview page in the console, starting with selecting Public. One of the prereqs should be setting up the IBM Cloud environment and point to the Determining your organization architecture topic. -->

{: shortdesc}

## Developing your app
{: #develop}

There are three ways to develop your app:

* With the Continuous Delivery service
* In the IBM Cloud console
* At the Cloud Foundry command line

## Developing and deploying your apps by using toolchains and the {{site.data.keyword.contdelivery_short}} service
{: #ee_cd}

[Add a toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started#creating_a_toolchain_from_an_app) that includes the {{site.data.keyword.contdelivery_full}} service to your app. Then, [use the toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains-using#toolchains-using) to develop and deploy your app.

Try the [Develop a Cloud Foundry app](https://www.ibm.com/cloud/architecture/tutorials/introduce-develop-cloud-foundry-app-toolchain) tutorial to learn about using toolchains to modify and continuously deliver a simple "Hello World" sample Cloud Foundry app.
{: tip}

## Creating your web app with the {{site.data.keyword.cloud_notm}} console
{: #ee_appui}

After signing up, start to build your first app by using the {{site.data.keyword.cloud_notm}} catalog and console.

In {{site.data.keyword.cloud_notm}} apps are associated with {{site.data.keyword.cloud_notm}} organizations and spaces. An organization is owned and used by multiple collaborators. Initially, you get a default organization that is named after your user name and you are the only collaborator. You also get a space within this organization. The space is an environment to run your apps; for example, you can have a `dev` space as a development environment, a `test` space as a test environment, and a `production` space as a production environment. Each of the environments belong to a region. With {{site.data.keyword.cloud_notm}}, you can deploy your apps to a specific geographical region for lower network latency, data privacy, and better availability.

For this scenario, you want to develop a web app by using Node.js. Assume that you are in the US and most of your app users are also in the US. For lower network latency you decide to build and run your app close to your user base. After logging in to {{site.data.keyword.cloud_notm}}, click the **user account preferences** link and select the **US South** region. Then, you can take the following steps to create an app:

  1. Click **Catalog** in the {{site.data.keyword.cloud_notm}} toolbar.
  2. Click **Cloud Foundry Apps** and choose the **Cloud Foundry** tile.
  3. Click **Public Applications** to select **Region** and **Runtime**.
  4. Type a unique name for your app and click **Create**. The app name must be unique in the whole {{site.data.keyword.cloud_notm}} environment.

Once created, a **Getting started** page is added to the left navigation pane. Follow the instructions in that page to download the starter code of your app, modify, and deploy it.

The app is created with one instance and 512 MB memory quota by default. You can increase the memory, or add more instances to get high availability of your app, for example, three instances with 1 GB memory per instance. Click **Overview** to specify your app instances and memory quota. For example, type 3 for instances and 1 GB for memory quota, and click **Save**. You can also see the files, logs, and environment variables to troubleshoot your problems.

### Binding a service by using {{site.data.keyword.cloud_notm}} console
{: #ee_bindui}

After creating your app, connect to a database with your app. You can store and retrieve the app data by using a database query language. In this scenario, you decide to use the {{site.data.keyword.cloudant}} service that is provided by {{site.data.keyword.cloud_notm}}.

To use {{site.data.keyword.cloud_notm}} with your Cloud Foundry app, create a service instance and bind your app to the service instance:

  1. In the {{site.data.keyword.cloud_notm}} catalog, select the {{site.data.keyword.cloudant}} service. Add a unique name for your {{site.data.keyword.cloudant}} service and click **Create**. In the Cloudant Manage panel, launch the service by clicking **Launch**.
  2. Click **Connections**. Then, click **Create connection**.
  3. Click **Connect** next to your app.
  4. The Restage App window is displayed. Click **Restage**.

Now your app is bound to the {{site.data.keyword.cloudant}} service. The <VCAP_SERVICES> environment variable contains the data that is required for the app to communicate with the service instance.
Because {{site.data.keyword.cloud_notm}} hosts several apps on the same virtual machine, multiple apps cannot use the same HTTP port number to receive incoming requests. To avoid conflicts, each app is given a unique port number. This port number is available in the <VCAP_APP_PORT> variable.

Follow these steps to see the list of <VCAP_SERVICES> values associated with your app in the console.

  1. Click the menu in the {{site.data.keyword.cloud_notm}} toolbar.
  2. Click **Dashboard**.
  3. Click your app.
  4. Click **Runtimes** and select the **Environment Variables** tab.

This environment variable is the serialization of a JSON object with one entry for each service instance that the app is bound to. The amount and type of data that each service instance provides are service-specific. When your app does not use a service, <VCAP_SERVICES> is an empty JSON object. This environment variable is used only when you add a service to your app.
{: note}

## Building your app by using the Cloud Foundry CLI
{: #ee_cf}

{{site.data.keyword.cloud_notm}} provides several tools for you to start coding your app, for example, the `cf` command line interface and Eclipse tools. In this example you will use the `cf` command line interface to start coding your app.

  1. First, download and develop your app code.

    1. Click **Getting started** in your app dashboard.
    2. Click the **Download the sample code** link to download your app code.
    3. Extract the downloaded file to a directory.
    4. Develop the code with your locally integrated development environment.

  2. Install the `cf` command line interface (CLI).

    1. Download the `cf` command line tool installation program for your operating system.
    2. Follow the tool wizard to complete the installation.
    3. Use the `cf -v` command to verify the version of the `cf` command line interface.

    **Requirement:** Make sure that you always use the latest version of the `cf` command line tool.

  3. After you install the `cf` command line interface, you must specify which {{site.data.keyword.cloud_notm}} region you want to work with by using the `cf api` command. The API endpoint for the US South region is `api.us-south.cf.cloud.ibm.com`. Additional API endpoints for other regions can be found [here](/docs/cloud-foundry-public?topic=cloud-foundry-public-endpoints). Enter the following command to connect to {{site.data.keyword.cloud_notm}}:

  ```
  cf api api.us-south.cf.cloud.ibm.com
  ```

  To find other API endpoints, see [Regions and Endpoints](/docs/cloud-foundry-public?topic=cloud-foundry-public-endpoints). After you specify the {{site.data.keyword.cloud_notm}} region, the location information that you specified is saved.

  4. Next, log in to {{site.data.keyword.cloud_notm}} by using the `cf login` command.

  ```
  cf login -u <your_user_ID> -p <password> -o <your_org_name> -s <your_space_name>
  ```
  {: pre}

  If your organization uses single sign on, use `cf login -sso`.

  5. After you are logged in to {{site.data.keyword.cloud_notm}}, you are ready to deploy your app back to {{site.data.keyword.cloud_notm}}. From your app directory, enter the following command:

  ```
  cf push <your_appname>
  ```
  {: pre}

  For more information, see the [`cf push` command](/docs/cli/reference/ibmcloud?topic=cf-cli-plugin-cf-cli-plugin#cf_push).

  6. Now, you can access the app by entering the following app URL in a browser:
  ```
  http://<your_app>.us-south.cf.appdomain.cloud
  ```
  {: codeblock}

You can also choose other tools to build your app, such as Eclipse tools. For more information, see the Getting started page of your app in the {{site.data.keyword.cloud_notm}} console.

### Binding a service by using the cf cli
{: #ee_cfbind}

You can also bind a service by using the `cf` command line interface. This example assumes that you want to add the {{site.data.keyword.cloudant}} service to your app with the `cf` command line interface.

To use the {{site.data.keyword.cloudant}} service within your app, create a {{site.data.keyword.cloudant}} service instance, bind your app to the service instance, and then use the service instance. The same procedure applies to all the other services.

  1. Create a {{site.data.keyword.cloudant}} NoSQL DB service instance.

  Use the `cf create-service` command to create a new instance of a service. In this example, <Lite> is the name of the plan. For example:

  ```
  cf create-service cloudantNoSQLDB <Lite> <your_name_for_your_cloudant_service>
  ```
  {: pre}

  You can also use the `cf services` command to see the list of service instances that you created.

  ```
  cf services
  ```
  {: pre}

  After a service instance is created, it is available for any of your apps to bind and use.

  2. Bind the service instance to your app.

  To use a service instance, you must bind it to your app. Use the `cf bind-service` command to bind a service instance to an app by specifying the app name and the service instance that you created.

  ```
  cf bind-service <your_app_name> <your_name_for_your_cloudant_service>
  ```
  {: pre}

  Binding a service instance to an app enables {{site.data.keyword.cloud_notm}} to communicate to the service, and to specify that a new app will communicate with that service instance. For different services, {{site.data.keyword.cloud_notm}} might process the app and the service instance differently during the binding. For example, some services might create a new tenant for each app that communicates to the service instance. The service responds back to {{site.data.keyword.cloud_notm}} with information, such as credentials, that must be passed to the app allowing communication between the app and the service.

  If the app is running when it is bound to a service instance, the <VCAP_SERVICES> environment variable is not updated until the app is restarted. To restart your app, use the `cf restart` command.
  {: note}

  3. Use the service instance.

  In this scenario, the <VCAP_SERVICES> environment variable includes information, such as the following items, that an app can use to connect to this instance of {{site.data.keyword.cloudant}}:

  <dl><dt>username</dt>
  <dd>d72837bb-b341-4038-9c8e-7f7232916197-bluemix</dd>
  <dt>password</dt>
  <dd>secret</dd>
  <dt>url</dt>
  <dd>https://d72837bb-b341-4038-9c8e-7f7232916197-bluemix:b6fc4708942b70a88853177ee52a528d07a43fa8575a69abeb8e044a7b0a7424@d72837bb-b341-4038-9c8e-7f7232916197-bluemix.cloudant.com</dd></dl>

  For example, your Node.js app might access this information as follows:
  ```
  if (process.env.VCAP_SERVICES) {
        var env = JSON.parse(process.env.VCAP_SERVICES);
        var cloudant = env['cloudantNoSQLDB'][0].credentials;
  } else {
        var cloudant = {
                "username" : "user1",
                "password" : "secret",
                "url" : "https://user1:secret@localhost:25002"
                }
        };
  ```
  {: codeblock}

  As the sample code shows, to connect to a {{site.data.keyword.cloudant}} service instance, you can check whether the <VCAP_SERVICES> environment variable exists first. If it exists, the app can use the {{site.data.keyword.cloudant}} variable's properties to access the database. However, if the <VCAP_SERVICES> environment variable is not present, the local {{site.data.keyword.cloudant}} service instance is used with the provided default values.
  {: note}

  4. Interact with the service instance.

  You can interact with the service instance by using the credential information. The actions that you can take include read, write, and update. The following example demonstrates how to insert a JSON object into the {{site.data.keyword.cloudant}} service instance:

  ```
  // create a new message
var create_message = function(req, res) {
  require('cloudantdb').connect(cloudant.url, function(err, conn) {
    var collection = conn.collection('messages');

    // create message record
    var parsedUrl = require('url').parse(req.url, true);
    var queryObject = parsedUrl.query;
    var name = (queryObject["name"] || 'Bluemix');
    var message = { 'message': 'Hello, ' + name, 'ts': new Date()
};
    collection.insert(message, {safe:true}, function(err){
      if (err) { console.log(err.stack); }
      res.writeHead(200, {'Content-Type': 'text/plain'});
      res.write(JSON.stringify(message));
      res.end('\n');
    });
  });
}
  ```
  {: codeblock}

  5. **Optional:** Unbind or delete a service instance.

  You might want to unbind or delete a service instance when it is no longer used or when you want to free up some spaces. To unbind a service instance from your app, use the `cf unbind-service command`.  To delete a service instance, use the `cf delete-service` command.

  For more information about services, see Services. For more information about the `cf` options that you can use to manage your apps in the {{site.data.keyword.cloud_notm}} environment, run `cf --help` in the `cf` command line interface.

  Make sure you no longer require a service instance before you delete it. Deleting a service instance erases all data that is associated with that instance of the service. Any app that is bound to a deleted service cannot have its <VCAP_SERVICES> environment variable updated until the app is restarted.
  {: important}

## Calculating your app cost
{: #ee_billing}

If your 30-day free trial has expired, and you want to continue to use {{site.data.keyword.cloud_notm}}, you must add your credit card information for a Pay As You Go account or a Subscription account. However, {{site.data.keyword.cloud_notm}} still provides free allowances for the community runtime frameworks (Python, PHP, Go, Ruby, Tomcat) and services even after you convert to a pay account. You are not charged by {{site.data.keyword.cloud_notm}} unless the usage is beyond the free allowances.

{{site.data.keyword.cloud_notm}} provides an estimator and calculator for you to see your app cost. You can see the cost of your app in the following ways:

  * In your console, click your app. Then, in the Overview page, click **estimate the cost of this app** to see the price of **SDK for Node.js** runtime and Support, and the total monthly price of your app.

  * Or, in the Pricing Sheet page, type the monthly usage of the runtime and services of your app. For example, 3 instances of **SDK for Node.js** with 1 GB memory for each instance. The monthly price is calculated and displayed.

You can also calculate your app cost manually by adding up the prices of your runtimes and services and deducting the free allowance. For more information, see Calculating your costs manually.

## Removing apps
{: #ee_removing}

As you build more apps, the quota might approach your limits. However, some apps that you might no longer use still occupy the quota. It’s easy to delete apps to free up some spaces in {{site.data.keyword.cloud_notm}} at any time.

In the {{site.data.keyword.cloud_notm}} console, go to the app Overview page, click the menu icon, and delete the app that you no longer use. You can also use the `cf delete` command to delete apps.



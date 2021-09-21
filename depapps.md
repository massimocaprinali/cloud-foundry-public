---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-21"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:audio: .audio}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: .ph data-hd-programlang='c#'}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: #curl .ph data-hd-programlang='curl'}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: .external target="_blank"}
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
{:middle: .ph data-hd-position='middle'}
{:navgroup: .navgroup}
{:new_window: target="_blank"}
{:node: .ph data-hd-programlang='node'}
{:note: .note}
{:objectc: .ph data-hd-programlang='Objective C'}
{:objectc: data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: .ph data-hd-programlang='PHP'}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:release-note: data-hd-content-type='release-note'}
{:right: .ph data-hd-position='right'}
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
{:step: data-tutorial-type='step'} 
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:topicgroup: .topicgroup}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Deploying apps
{: #deployingapps}

You can deploy apps to {{site.data.keyword.cloud}} with the command line interface or the integrated development environments (IDEs). You can also use app manifests to deploy apps. When you use an app manifest, you reduce the number of deployment details that you must specify every time that you deploy an app to {{site.data.keyword.cloud_notm}}.
{: shortdesc}

## App deployment
{: #appdeploy}

Deploying an app to {{site.data.keyword.cloud_notm}} includes two phases, staging the app and starting the app.

### Staging an app
{: #diego}

During the staging phase, {{site.data.keyword.cloud_notm}} takes care of the app container orchestration. When you push an app, the Cloud Controller sends a staging request to {{site.data.keyword.cloud_notm}}, which takes over the task of allocating the app instances. The {{site.data.keyword.cloud_notm}} backend orchestrates app containers to ensure fault-tolerance and long-term consistency.

All apps are deployed to the Diego architecture. To stage an app, deploy the app with the `ibmcloud app push` command:

```text
ibmcloud app push <appname>
```
{: pre}

For more details, see [`ibmcloud push`](/docs/cli?topic=cli-ibmcloud_commands_apps#ibmcloud_app_push).

### Starting an app
{: #startapp}

When an app is started, the instance or instances of the app container are created. You can use the `ibmcloud cf ssh` or `ibmcloud cf scp` command to access the app container file system which includes the logs. The `ibmcloud cf files` command does not work for apps running on the Diego architecture.

If the app fails to start, the app is stopped, the contents of your app container are removed, and the log files are not  available. 
{: note}

If you can't access the logs for the app by using the `ibmcloud cf ssh` or `ibmcloud cf scp` command, you can use the `ibmcloud cf logs` command to see the cause of the staging errors in the app container. The `ibmcloud cf logs` command uses the {{site.data.keyword.ibmcf_full}} log aggregator to collect the details of your app logs and system logs, and you can see what the log aggregator saved. For more information about the log aggregator, see [Logging in Cloud Foundry](http://docs.cloudfoundry.org/devguide/deploy-apps/streaming-logs.html){: external}.

The buffer size is limited. If an app runs for a long time and is not restarted, logs might not be displayed when you run the `ibmcloud cf app logs appname --recent` command because the log buffer might have been cleared. To debug staging errors for a large app, use the `ibmcloud cf app logs appname` command on a separate command line from the `ibmcloud cf` command line interface to track the logs while you deploy the app.
{: note}

## Deploying apps by using the `ibmcloud cf` command
{: #dep_apps}

When you deploy your apps to {{site.data.keyword.cloud_notm}} from the command line interface, a buildpack provides the runtime environment that is appropriate for your app language and framework. You can also use the Delivery Pipeline service to deploy apps to {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} [provides buildpacks](/docs/cloud-foundry-public?topic=cloud-foundry-public-available_buildpacks) supporting Java and Node.js among others. If you are using these languages and frameworks, you don't need to specify the buildpack when you deploy your app by using the command line interface. Because {{site.data.keyword.cloud_notm}} is built on Cloud Foundry, the command defaults to these buildpacks.

If you use an external buildpack, when deploying your app you must specify the URL of the buildpack by using the `-b` option.

* To deploy Liberty server packages to {{site.data.keyword.cloud_notm}}, use the following command from your source directory:

    ```text
    ibmcloud cf push
    ```
    {: pre}

    For more information about Liberty Buildpack, see [Liberty for Java](/docs/cloud-foundry-public?topic=cloud-foundry-public-getting-started-liberty).

* To deploy Java Tomcat apps to {{site.data.keyword.cloud_notm}}, use the following command:

    ```text
    ibmcloud cf push <appname> -b https://github.com/cloudfoundry/java-buildpack.git -p <app_path>
    ```
    {: pre}

* To deploy WAR packages to {{site.data.keyword.cloud_notm}}, use the following command:

    ```text
    ibmcloud cf push <appname> -p app.war
    ```
    {: pre}

    Or, you can specify a directory that contains your app files by using the following command:

    ```text
    ibmcloud cf push <appname> -p "./app"
    ```
    {: pre}

* To deploy Node.js apps to {{site.data.keyword.cloud_notm}}, use the following command:

    ```text
    ibmcloud cf push <appname> -p <app_path>
    ```
    {: pre}

    A `package.json` file must be in your Node.js app for the app to be recognized by the Node.js buildpack. The `app.js` file is the entry script for the app, and can be specified in the `package.json` file. The following example shows a simple `package.json` file:

    ```json
    {
          "name": "MyUniqueNodejs01",
          "version": "0.0.1",
          "description": "A sample package.json file",
          "dependencies": {
                  "express": ">=3.4.7 <4",
                  "jade": ">=1.1.4"
          },
          "scripts": {
                  "start": "node app.js"
          },
          "engines": {
                  "node": ">=0.10.0"
          },
          "repository": {}
    }
    ```
    {: codeblock}

    For more information about the `package.json` file, see [Creating a package.json file](https://docs.npmjs.com/creating-a-package-json-file){: external}.

* To deploy PHP, Ruby, or Python apps to {{site.data.keyword.cloud_notm}}, use the following command from the directory that contains your app source:

    ```text
    ibmcloud cf push <appname>
    ```
    {: pre}

### Deploying an app in multiple spaces

An app is specific to the space where it is deployed. You can't move or copy an app from one space to another in {{site.data.keyword.cloud_notm}}. To deploy an app in multiple spaces, you must deploy your app in each space where you want to use the app by the following steps:

1. Switch to the space where you want to deploy your app by using the `ibmcloud cf target` command with the `-s` option:

    ```text
    ibmcloud cf target -s <space_name>
    ```
    {: pre}

2. Go to your app directory and deploy your app by using the `ibmcloud cf app push` command, where `<appname>` must be unique within your domain.

    ```text
    ibmcloud cf app push <appname>
    ```
    {: pre}

## App manifest
{: #appmanifest}

App manifests contain options that are applied to the `ibmcloud cf push` command. You can use an app manifest to reduce the number of deployment details that you must specify every time you push an app to {{site.data.keyword.cloud_notm}}.

In app manifests you can specify options such as the number of app instances to create, the amount of memory and disk quota to allocate to apps, and other environment variables for the app. You can also use app manifests to automate app deployments. The default name of a manifest file is `manifest.yml`.

### Supported options in the manifest file

The following table shows the supported options that you can use in an app manifest file. If you choose to use a file name other than `manifest.yml`, you must use the `-f` option with the `ibmcloud cf push` command. In the following example, `appManifest.yml` is the file name:

``` text
ibmcloud cf push -f appManifest.yml
```
{: pre}

|Options	|Description	|Usage or example|
|----------|--------------|---------------|
|**buildpack**	|The URL or name of the custom buildpack.	|`buildpack:` *buildpack_URL*|
|**disk_quota**	|The disk quota that is allocated for an app. The default value is 1GB.	|`disk_quota: 500MB`|
|**domain**	|The domain name of the app in {{site.data.keyword.cloud_notm}}.	|`domain: ng.mybluemix.net`|
|**host**	|The host name of the app in {{site.data.keyword.cloud_notm}}. This value must be unique in the {{site.data.keyword.cloud_notm}} environment.	|`host:` *host_name*|
|**name**	|The app name in {{site.data.keyword.cloud_notm}}. This value must be unique in the {{site.data.keyword.cloud_notm}} environment.	|`name: appname`|
|**path**	|The location of your app. This value can be a relative path or absolute path.	|`path:` *path_to_app*|
|**command**	|The custom start command for your app, or the command to run script files.	|`command:` *custom_command* `command:` *`bash ./run.sh`*|
|**memory**	|The amount of memory to allocate for the app. The default value is 1GB.	|`memory: 512MB`|
|**instances**	|The number of instances to create for your app.	|`instances: 2`|
|**timeout**	|The maximum amount of time in seconds that is used to start the app. The default value is 60 seconds.	|`timeout: 80`|
|**no-route**	|A Boolean value to prevent a route from being assigned to the app if the app is running in the background. The default value is **false**.	|`no-route: true`|
|**random-route**	|A Boolean value to assign a random route to the app. The default value is **false**.	|`random-route: true`|
|**services**	|The services to bind to the app.	|`services: - mysql_maptest`|
|**env**	|The custom environment variables for the app.|`env: DEV_ENV: production`|
{: caption="Table 1. Supported options in the manifest YAML file" caption-side="top"}

### A sample manifest.yml file

The following example shows a manifest file for a Node.js app that uses the built-in community Node.js buildpack in {{site.data.keyword.cloud_notm}}.

```text
---
- name: myNodejsapp
  memory: 256M
  disk_quota: 512M
  path: /dev/myNodejsApp
  buildpack: nodejs_buildpack
  host: nodejs001
  domain: mybluemix.net
  command: node app.js
  timeout: 80
  services:
  - mongo_8917
  env:
    env_type: production
```
{: codeblock}

## Environment variables
{: #app_env}



Environment variables contain the environment information of a deployed app on {{site.data.keyword.cloud_notm}}. Besides environment variables set by Diego and buildpacks, you can also set app-specific environment variables for apps on {{site.data.keyword.cloud_notm}}.

You can view the following environment variables of a running {{site.data.keyword.cloud_notm}} app by using the `ibmcloud app env` command or from the {{site.data.keyword.cloud_notm}} user interface:

* User-defined variables that are specific to an app. For more information, see [Adding user-defined environment variables](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps#ud_env).

* The VCAP_SERVICES variable, which contains connection information to access a service instance. If your app is bound to multiple services, the VCAP_SERVICES variable includes the connection information for each service instance. For example:

```text
{
 "VCAP_SERVICES": {
  "AppScan Dynamic Analyzer": [
   {
    "credentials": {
     "bindingid": "0ab3162a-867e-4137-a2e7-39346a89472e",
     "password": "xxxxxxxxxxxxxx"
    },
    "label": "AppScan Dynamic Analyzer",
    "name": "AppScan Dynamic Analyzer-9q",
    "plan": "standard",
    "tags": [
     "Security",
     "security",
     "ibm_created"
    ]
   }
  ],
  "mysql-5.5": [
   {
    "credentials": {
     "host": "23.246.200.38",
     "hostname": "23.246.200.38",
     "name": "d296abcc06c9e418b94cbaaafdf547620",
     "password": "xxxxxxxxxxxxxxx",
     "port": 3307,
     "uri": "mysql://uzpGf7eGJ7mtB:peRiYCG4ZYqu3@23.246.200.38:3307/d296abcc06c9e418b94abcaafdf547620",
     "user": "uzpGf7eGJ7mtB",
     "username": "uzpGf7eGJ7mtB"
    },
    "label": "mysql-5.5",
    "name": "mysql-ix",
    "plan": "300",
    "tags": [
     "mysql",
     "relational",
     "data_management",
     "ibm_experimental"
    ]
   }
  ]
 }
}
```
{: codeblock}

You also have access to the environment variables that are set by Diego and the buildpacks.

The following variables are defined by Diego:

<dl>
  <dt><strong>HOME</strong></dt>
  <dd>The root directory of the deployed app.</dd>
  <dt><strong>MEMORY_LIMIT</strong></dt>
  <dd>The maximum amount of memory that each instance of your app can use. You can specify the value in an app <span class="ph filepath">manifest.yml</span> file, or on the command line when you push the app.</dd>
  <dt><strong>PORT</strong></dt>
  <dd>The port on Diego for communication with the app. Diego allocates a port to the app at staging time.</dd>
  <dt><strong>PWD</strong></dt>
  <dd>The current working directory that is running the buildpack.</dd>
  <dt><strong>TMPDIR</strong></dt>
  <dd>The directory where temporary and staging files are stored.</dd>
  <dt><strong>USER</strong></dt>
  <dd>The user ID that is running Diego.</dd>
  <dt><strong>VCAP_APP_HOST</strong></dt>
  <dd>The IP address of the Diego host.</dd>
  <dt><strong>VCAP_APP</strong></dt>
  <dd>A JSON string that contains information about the deployed app. The information includes the app name, URIs, memory limits, time stamp when the app achieved its current state, and other values. For example:
  <pre class="pre codeblock"><code>
  {
    "limits": {
        "mem": 512,
        "disk": 1024,
        "fds": 16384
    },
    "application_version": "df111903-7d95-4c20-96d9-aad4e97d2a9a",
    "application_name": "testapp",
    "application_uris": [
        "testapp.AppDomainNamestage1.mybluemix.net"
    ],
    "version": "df111903-7d95-4c20-96d9-aad4e97d2a9a",
    "name": "testapp",
    "space_name": "dev",
    "space_id": "c6ed3a8e-436b-43ac-9f96-b676ee335000",
    "uris": [
        "testapp.AppDomainNamestage1.mybluemix.net"
    ],
    "users": null,
    "application_id": "e984bb73-4c4e-414b-84b7-c28c87f84003",
    "instance_id": "09f50e22848d4ec0b943e9e487c23569",
    "instance_index": 0,
    "host": "0.0.0.0",
    "port": 61399,
    "started_at": "2015-01-16 06:50:51 +0000",
    "started_at_timestamp": 1421391051,
    "start": "2015-01-16 06:50:51 +0000",
    "state_timestamp": 1421391051
}
</code></pre></dd>
  <dt><strong>VCAP_SERVICES</strong></dt>
  <dd>A JSON string that contains information about the service bound to the deployed app. For example:
  <pre class="pre codeblock"><code>
  {
    "mysql-5.5": [
        {
            "name": "mysql-ix",
            "label": "mysql-5.5",
            "tags": [
                "mysql",
                "relational",
                "data_management",
                "ibm_experimental"
            ],
            "plan": "300",
            "credentials": {
                "name": "d296abcc06c9e418b94abcaafdf547620",
                "hostname": "23.246.200.38",
                "host": "23.246.200.38",
                "port": 3307,
                "user": "uzpGf7eGJ7mtB",
                "username": "uzpGf7eGJ7mtB",
                "password": "xxxxxxxxxxxxxxx",
                "uri": "mysql://uzpGf7eGJ7mtB:peRiYCG4ZYqu3@23.246.200.38:3307/d296abcc06c9e418b94abcaafdf547620"
            }
        }
    ]
}
</code></pre></dd>

</dl>

Variables that are defined by buildpacks are different for each buildpack. For other compatible buildpacks, see [the buildpack information for Cloud Foundry](https://github.com/cloudfoundry-community/cf-docs-contrib/wiki/Buildpacks){: external}.

<ul>
    <li>The following variables are defined by the Liberty Buildpack:

	  <dl>
	  <dt><strong>JAVA_HOME</strong></dt>
	  <dd>The location of Java SDK that runs the app.</dd>
	  <dt><strong>IBM_JAVA_OPTIONS</strong></dt>
	  <dd>The Java SDK options to use when running the app.</dd>
	  <dt><strong>IBM_JAVA_COMMAND_LINE</strong></dt>
	  <dd>The Java command to start up a Liberty profile server instance in Diego.</dd>
	  <dt><strong>WLP_USR_DIR</strong></dt>
	  <dd>The location of shared resources and server definitions when starting up a Liberty profile server instance in Diego.</dd>
	  <dt><strong>WLP_OUTPUT_DIR</strong></dt>
	  <dd>The location of generated output such as log files and working directory of a running Liberty profile server instance.</dd>
	  </dl>
</li>
<li>The following variables are defined by the Node.js Buildpack:
	<dl>
	<dt><strong>BUILD_DIR</strong></dt>
	<dd>The directory of the Node.js runtime environment.</dd>
	<dt><strong>CACHE_DIR</strong></dt>
	<dd>The directory that the Node.js runtime environment uses for caching.</dd>
	<dt><strong>PATH</strong></dt>
	<dd>The system path that is used by the Node.js runtime environment.</dd>
	</dl>
</li>
</li>
</ul>

You can use the following sample Node.js code to get the value of the VCAP_SERVICES environment variable:

```text
if (process.env.VCAP_SERVICES) {
    var env = JSON.parse (process.env.VCAP_SERVICES);
    myvar = env.foo[bar].foo;
}
```
{: codeblock}

For more information about each environment variable, see [Cloud Foundry Environment Variables](http://docs.cloudfoundry.org/devguide/deploy-apps/environment-variable.html){: external}.

## Customizing app deployments
{: #customize_dep}

You can customize deployment tasks for your apps. For example, you can specify the start commands for your apps and configure your app startup environment.
{: shortdesc}

### Specifying start commands

To specify start commands for your app, you can use one of the following options. The start commands that you specify  overwrite the default start commands that are provided by the buildpack.

If you want the buildpack start commands to take precedence, specify `null` as the start command.
{: note}

* Use the `ibmcloud cf push` command and specify the `-c` option. For example, when you deploy a Node.js app, you can specify the `node app.js` start command on the `-c` option:

```text
ibmcloud cf push appname -p app_path -c "node app.js"
```
{: pre}

* Use the command option in the `manifest.yml` file. For example, when you deploy a Node.js app, you can specify the `node app.js` start command in the manifest file:

```text
command: node app.js
```
{: codeblock}


### Adding user-defined environment variables
{: #ud_env}

User-defined environment variables are specific for an app. You have the following options to add a user-defined environment variable to a running app:

* Use the {{site.data.keyword.cloud_notm}} user interface. 
  
    1. On the {{site.data.keyword.cloud_notm}} Dashboard, click your app tile. The app details page is displayed.

    2. Click **Runtime** > **Environment Variables**.
  
    3. Click **USER-DEFINED**, then click **ADD**.
  
    4. Fill in the required fields, then click **SAVE**.

* Use the `ibmcloud cf` command line interface. Add a user-defined variable by using the `ibmcloud cf env-set` command. For example:

    ```text
    ibmcloud cf env-set appname <environment_variable_name> <environment_variable_value>
    ```
    {: pre}

* Use the `manifest.yml` file. Add value pairs in the file. For example:

    ```text
  	env:
        VAR1:<environment_variable_name>
        VAR2:<environment_variable_value>
    ```
    {: codeblock}

* After you add a user-defined environment variable, you can use the following sample Node.js code to get the value of the defined variable:

    ```text
    var myEnv = process.env.<environment_variable_name>;
    console.log("My user defined = " + myEnv);
    ```
    {: codeblock}

### Configuring the startup environment

To configure the startup environment for your app, you can add shell scripts into the `/.profile.d` directory. The `/.profile.d` directory is under the build directory of your app. Scripts in the `/.profile.d` directory are run by {{site.data.keyword.cloud_notm}} before the app is run. For example, you can set the NODE_ENV environment variable to **production** by putting a `node_env.sh` file that contains the following content under the `/.profile.d` directory:

```text
export NODE_ENV=production;
```
{: pre}

### Preventing files and directories from being uploaded

When you use the `ibmcloud cf` command line interface to deploy an app, you can save upload time by skipping certain files and directories that {{site.data.keyword.cloud_notm}} can obtain elsewhere. To prevent these files and directories from being uploaded to {{site.data.keyword.cloud_notm}}, you can create a `.cfignore` file at the root directory of your app.

The `.cfignore` file must be in `UTF-8` format.
{: note}

The `.cfignore` file contains the names of files and directories that you want to ignore, one name per line. You can use an asterisk (*) as a wildcard character. When you specify a directory, all files and subdirectories under that directory are also ignored. For example, the following content in the `.cfignore` file indicates that all the `.swp` files and all files and subdirectories under the `tmp/` directory won't be uploaded to {{site.data.keyword.cloud_notm}}.

```text
*.swp
tmp/
```
{: codeblock}



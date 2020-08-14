---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-14"

keywords: cloud foundry

subcollection: cloud-foundry-public



---



{:beta: .beta}
{:codeblock: .codeblock}
{:deprecated: .deprecated}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:gif: data-image-type='gif'}
{:help: data-hd-content-type='help'}
{:important: .important}
{:java: data-hd-programlang="java"}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note: .note}
{:pre: .pre}
{:preview: .preview}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:support: data-reuse='support'}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}

# Troubleshooting for Cloud Foundry apps
{: #ts-cf-apps}

General problems with creating Cloud Foundry apps might include apps that can't be updated, or double-byte characters that aren't displayed. In many cases, you can recover from these problems by following a few easy steps.
{: shortdesc}

## Cloud Foundry API endpoints
{: #ts_endpoints}
{: troubleshoot}

While the legacy `api.*.bluemix.net` Cloud Foundry API endpoints are still available, you can update scripts and infrastructure automation to use the following updated Cloud Foundry API endpoints for your region:

* api.us-south.cf.cloud.ibm.com (previously api.ng.bluemix.net)
* api.eu-gb.cf.cloud.ibm.com (previously api.eu-gb.bluemix.net)
* api.us-east.cf.cloud.ibm.com (previously api.us-east.bluemix.net)
* api.eu-de.cf.cloud.ibm.com (previously api.eu-de.bluemix.net)
* api.au-syd.cf.cloud.ibm.com (previously api.au-syd.bluemix.net)

<!-- Don't know whether to include this section in CF-->
## Automatic failover between {{site.data.keyword.cloud_notm}} regions isn't available
{: #ts_failover}
{: troubleshoot}

You can't use automatic failover between {{site.data.keyword.cloud}} regions. However, you can use a DNS provider that supports failover among many IP addresses as a workaround.

When an {{site.data.keyword.cloud_notm}} region becomes unavailable, the apps that are running in that region are also unavailable, even if the same apps are running in another {{site.data.keyword.cloud_notm}} region.
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} doesn't yet provide automatic failover from one region to another.
{: tsCauses}

You can use a DNS provider that supports intelligent failover among many ID addresses, and manually configure your DNS settings to enable the automatic failover between {{site.data.keyword.cloud_notm}} regions. DNS providers with this feature include NSONE, Akamai, and Dyn.
{: tsResolve}

When you configure your DNS settings, you must specify the public IP addresses of the {{site.data.keyword.cloud_notm}} regions that your apps are running in. To get the public IP address of an {{site.data.keyword.cloud_notm}} region, use the `nslookup` command. For example, you can type the following command in a command line window.
```
nslookup cloud.ibm.com
```
{: pre}

## Can't reuse names of deleted apps
{: #ts_reuse_appname}
{: troubleshoot}

After you delete an app, you can reuse the app name only after you delete the app route.

When you try to reuse the app name, you receive the following message:
{: tsSymptoms}

`The name is already used by another app.`

When an app is deleted, its route, which is the URL for the app, isn't automatically deleted and it's not available for reuse. You must go to the space where the app was created to delete the route so that it can be reused.
{: tsCauses}

Complete the following steps to delete the unused route:
{: tsResolve}

  1. Check whether the route belongs to the current space by entering the following command:
    ```
    ibmcloud cf routes
    ```
    {: pre}

  2. If the route doesn't belong to the current space, switch to the space or org that it belongs to by entering the following command:
    ```
    ibmcloud cf target -o org_name -s space_name
    ```
    {: pre}

  3. Delete the app route by entering the following command:
    ```
    ibmcloud cf delete-route domain_name -n host_name
    ```
    {: pre}

  For example:
  ```
  ibmcloud cf delete-route cf.cloud.ibm.com -n app001
  ```
  {: pre}

## Can't retrieve spaces in the org
{: #ts_retrieve_space}
{: troubleshoot}

You can't create an app or a service if your current organization doesn't have a space that is associated with it.

When you try to create an app in {{site.data.keyword.cloud_notm}}, you see the following error message:
{: tsSymptoms}

`BXNUI0515E: The spaces in the org weren't retrieved. Either a network connection problem occurred, or your current organization does not have a space associated with it.`

This error often occurs the first time that you try to create an app or a service from the catalog when a space isn't created yet.
{: tsCauses}

Ensure that you created a space in your current organization. To create a space, use one of the following methods:
{: tsResolve}

* From the menu bar, click **Manage > Account**, and select **Cloud Foundry orgs**. Click the name of the organization that you want to create the space in, and click **Add a space**.
* In the Cloud Foundry command-line interface, type `cf create-space <space_name> -o <organization_name>`.

Try again. If this message occurs again, go to the [{{site.data.keyword.cloud_notm}} status](http://ibm.biz/bluemixstatus){: external} page to check whether a service or component has an issue.

## Can't perform requested actions
{: #ts_authority}
{: troubleshoot}

You can't complete actions without appropriate access authority.

When you try to perform actions for a service instance or an app instance, you can't complete the requested actions and see one of the following error messages:
{: tsSymptoms}

`BXNUI0514E: You are not a developer for any of the spaces in the <orgName> organization.`

`Server error, status code: 403, error code: 10003, message: You are not authorized to perform the requested action.`

You don't have the appropriate level of authority to perform the actions.
{: tsCauses}

To get the appropriate authority level, use one of the following methods.
{: tsResolve}

* Select another organization and space for which you have the Developer role.
* Ask the org manager to change your role to Developer or to create a space and then assign you a Developer role. See [Cloud Foundry access](/docs/account?topic=account-mngcf) for details.

## Disk quota is exceeded
{: #ts_disk_quota}
{: troubleshoot}

If you run out of disk space, you can manually modify the disk quota to get more disk space.

When you run out of disk space, you might see a message that states that the disk quota is exceeded. To resolve the problem, you might have tried scaling up your app instance to get more disk space. For example, you might scale from 256 - 1256 MB by changing the memory quota on the app details page. However, because the disk quota remained the same, you didn't get more disk space.
{: tsSymptoms}

The default disk quota that is allocated for an app is 1 GB. If you need more disk space, you must manually specify the disk quota.
{: tsCauses}

Use one of the following methods to specify your disk quota. The maximum disk quota that you can specify is 2 GB. If 2 GB is still not enough, try an external service such as [Cloud Object Storage](/docs/cloud-object-storage?topic=cloud-object-storage-getting-started-cloud-object-storage).
{: tsResolve}

  * In the `manifest.yml` file, add the following item:
  ```
  disk_quota: <disk_quota>
  ```
  {: codeblock}

  * Use the `-k` option with the `ibmcloud cf push` command when you push your app to {{site.data.keyword.cloud_notm}}:

  ```
  ibmcloud cf push appname -p app_path -k <disk_quota>
  ```
  {: pre}

## Org's services limit is exceeded
{: #ts_servicelimit}
{: troubleshoot}

If you are a Lite account user, you might be unable to create an app in {{site.data.keyword.cloud_notm}} if you exceeded your organization's services limit.

When you try to create an app in {{site.data.keyword.cloud_notm}}, the following error message is displayed:
{: tsSymptoms}

`BXNUI2032E: The <service_instances> resource wasn't created. While Cloud Foundry was being contacted to create the resource, an error occurred. Cloud Foundry message: "You have exceeded your organization's services limit."`

This error occurs when you exceed the limit on the number of service instances that you can have for your account.
{: tsCauses}

Delete any services instances that aren't needed, or remove the limit on the number of service instances that you can have.
{: tsResolve}

  * To delete a services instance, you can use the {{site.data.keyword.cloud_notm}} console or the command line interface.

    To use the {{site.data.keyword.cloud_notm}} console to delete a service instance, complete the following steps:
	  1. In the resource list, click the **Actions** menu for the service that you want to delete.
	  2. Click **Delete Service**. You are prompted to restage the app that the service instance was bound to.

    To use the command line interface to delete a service instance, complete the following steps:
	  3. Unbind the service instance from an app. Enter `ibmcloud cf unbind-service <appname> <service_instance_name>`.
	  4. Delete the service instance. Enter `ibmcloud cf delete-service <service_instance_name>`.
	  5. After you delete the service instance, you might want to restage your app that the service instance was bound to. Enter `ibmcloud cf restage <appname>`.

  * To remove the limit on the number of service instances that you can have, upgrade your Lite account to a billable account. For more information, see [Upgrading your account](/docs/account?topic=account-upgrading-account).

## Executable files can't be run on {{site.data.keyword.cloud_notm}}
{: #ts_executable}
{: troubleshoot}

You might be unable to run executable files on {{site.data.keyword.cloud_notm}} when those executables were developed and built in a different environment.

You can't run executables on {{site.data.keyword.cloud_notm}} when those executables were developed and built in a different environment.
{: tsSymptoms}

If the content that you want to push to {{site.data.keyword.cloud_notm}} is already an executable, the content was previously built and doesn't need to be built on {{site.data.keyword.cloud_notm}}. In this case, no buildpack is required for the executable to be run on {{site.data.keyword.cloud_notm}}. You must explicitly indicate to {{site.data.keyword.cloud_notm}} that no buildpack is required.
{: tsCauses}

When you push the executable to {{site.data.keyword.cloud_notm}}, you must specify a `null-buildpack`, which indicates that no buildpack is required. Specify a `null-buildpack` by using the `-b` option with the `ibmcloud cf push` command:
{: tsResolve}

```
ibmcloud cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
{: pre}

For example:
```
ibmcloud cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```
{: pre}

## Org's memory limit is exceeded
{: #ts_outofmemory}
{: troubleshoot}

If you are a Lite account user, you might be unable to deploy an app to {{site.data.keyword.cloud_notm}} if you have exceeded the memory limit of your organization. You can either reduce the memory that your apps use or increase the memory quota of your account. The maximum memory quota for a Lite account is 256 MB and can be increased only by upgrading to a billable account.

When you deploy an app to {{site.data.keyword.cloud_notm}},the following error message is displayed:
{: tsSymptoms}

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

This error occurs when the amount of memory that is remaining for your organization is less than the amount of memory that is required by the app that you want to deploy. The maximum memory quota for a Lite account is 256 MB.
{: tsCauses}

You can either increase the memory quota of your account, or reduce the memory that your apps use.
{: tsResolve}

  * To increase the memory quota of your account, upgrade your Lite account to a billable account. For more information, see [Upgrading your account](/docs/account?topic=account-upgrading-account).
  * To reduce the memory that your apps use, use either the {{site.data.keyword.cloud_notm}} console or the Cloud Foundry command line interface.

    If you use the {{site.data.keyword.cloud_notm}} console, complete the following steps:

    1. Select your app from the resource list. The app details page opens.
    2. In the runtime pane, you can reduce the maximum memory limit or the numbers of app instances, or both, for your app.

    If you use the command line interface, complete the following steps:

    1. Check how much memory is being used for your apps:
  	  ```
	  ibmcloud cf list
	  ```
      {: pre}

	  The `ibmcloud cf list` command lists all the apps that you deployed in your current space. The status of each app is also displayed.

    2. To reduce the amount of memory that is used by your app, reduce the number of app instances or the maximum memory limit, or both:
	  ```
	  ibmcloud cf push appname -p app_path -i instance_number -m memory_limit
      ```
      {: pre}

    3. Restart your app for the changes to take effect.

## Apps aren't automatically restarted
{: #ts_apps_not_auto_restarted}
{: troubleshoot}

An app isn't automatically restarted when a service that you bind to the app stops working.

When a service that you bind to an app crashes, problems such as outages, exceptions, and connection failures might occur on the app. {{site.data.keyword.cloud_notm}} doesn't automatically restart the app to recover from these problems.
{: tsSymptoms}

This behavior is by design of Cloud Foundry.
{: tsCauses}

You can manually restart an app that is already deployed by typing the following command in the command-line interface:
{: tsResolve}

```
ibmcloud cf restart <APPNAME>
```
{: pre}

In addition, you can code the app to identify and recover from problems such as outages, exceptions, and connection failures.

## Orgs can't be found on {{site.data.keyword.cloud_notm}}
{: #ts_orgs}
{: troubleshoot}

You might not be able to locate your organization on {{site.data.keyword.cloud_notm}} when working on an {{site.data.keyword.cloud_notm}} region.

You can log in to the {{site.data.keyword.cloud_notm}} console successfully, but you can't push apps by using the Cloud Foundry command line interface.
{: tsSymptoms}

When you try to push an application to {{site.data.keyword.cloud_notm}} by using the Cloud Foundry command line interface, you see one of the following error messages with the organization name that is specified in the message:

`Error finding org`

`Organization not found`

This problem occurs because the API endpoint of the region that you want to work with isn't specified, and the organization you're looking for might be in a different region.
{: tsCauses}

If you are pushing your application to {{site.data.keyword.cloud_notm}} by using the Cloud Foundry command line interface, enter the `ibmcloud cf api` command and specify the API endpoint of the region. For example, enter the following command to connect to the {{site.data.keyword.cloud_notm}} Europe United Kingdom region:
{: tsResolve}

```
ibmcloud cf api https://api.eu-gb.cf.cloud.ibm.com
```
{: pre}

## App routes can't be created
{: #ts_hostistaken}
{: troubleshoot}

When you deploy an app to {{site.data.keyword.cloud_notm}}, the route of the app can't be created if the host name that you specified is already being used.

When you deploy an app to {{site.data.keyword.cloud_notm}}, you see the following error message:
{: tsSymptoms}

`Creating route hostname.domainname ... FAILED Server error, status code: 400, error code: 210003, message: The host is taken: hostname`

This problem occurs if the host name that you specified is already being used.
{: tsCauses}

The host name that you specify must be unique within the domain that you are using. To specify a different host name, use one of the following methods:
{: tsResolve}

  * If you deploy your application by using the `manifest.yml` file, specify the host name in the host option.
    ```
    host: host_name
	```
    {: codeblock}

  * If you deploy your application from the command prompt, use the `ibmcloud cf push` command with the `-n` option.
    ```
    ibmcloud cf push appname -p app_path -n host_name
    ```
    {: pre}

## WAR apps can't be pushed by using the ibmcloud cf push command
{: #ts_cf_war}
{: troubleshoot}

You might not be able to use the `ibmcloud cf push` command to deploy an archived web app to {{site.data.keyword.cloud_notm}} if the app location isn't specified correctly.

When you upload a WAR app to {{site.data.keyword.cloud_notm}} by using the `ibmcloud cf push` command, you see the following error message:
{: tsSymptoms}
`Staging error: cannot get instances since staging failed.`

This problem might happen if the WAR file isn't specified, or if the path to the WAR file isn't specified.
{: tsCauses}

Use the `-p` option to specify a WAR file or add the path to the WAR file. For example:
{: tsResolve}

```
ibmcloud cf push MyUniqueAppName01 -p app.war
```
{: pre}

```
ibmcloud cf push MyUniqueAppName02 -p "./app.war"
```
{: pre}

For more information about the `ibmcloud cf push` command, enter `ibmcloud cf push -h`.

## Node.js apps can't be deployed
{: #ts_nodejs_deploy}
{: troubleshoot}

You might experience problems when you update a Node.js app or deploy a Node.js app to {{site.data.keyword.cloud_notm}}.

When you update a Node.js app or deploy your Node.js app to {{site.data.keyword.cloud_notm}}, you might see one of the following error messages:
{: tsSymptoms}

`An app was not successfully detected by any available buildpack.`

`Instance (index 0) failed to start accepting connections.`

`Cannot get instances since staging failed.`

Possible causes are as follows:
{: tsCauses}

  * The start command isn't specified.
  * Files that are required to deploy a Node.js app are either missing from the app or in a folder other than the root directory.

Use one of the following methods, depending on the cause of the problem:
{: tsResolve}

  * Specify the start command by one of the following methods:
     * Use the Cloud Foundry command line interface. For example:
      ```
	  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
	  ```
      {: pre}

    * Use the [package.json](https://www.npmjs.com/package/jsonfile){: external} file. For example:
	    ```
		  {
        ...
  	    "scripts": {
	 		  "start": "node app.js"
 	    }
	    }
	    ```
        {: codeblock}

    * Use the `manifest.yml` file. For example:
	  ```
		  applications:
      name: MyUniqueNodejs01
      ...
      command: node app.js
      ...
      ```
      {: codeblock}

  * Ensure that a `package.json` file exists in your Node.js app so that the Node.js buildpack can recognize the app. Ensure that this file is in the root directory of your app.
    The following example shows a simple `package.json` file:
	```
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```
    {: codeblock}

For more tips about Node.js apps, see [Tips for Node.js Applications](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: external}.



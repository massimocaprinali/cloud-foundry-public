---

copyright:
  years: 2015, 2022
lastupdated: "2022-06-02"


keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# {{site.data.keyword.ibmcf_notm}} application deployment analysis
{: #deprecation_deploy_analysis}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Before migrating your applications to another IBM Cloud compute type, look at your applications in your {{site.data.keyword.ibmcf_full}} hosting environment. 
{: shortdesc}

For most cloud hosted applications, internal application code makes up most of the effort for that application. Where it is hosted, how it is connected, how traffic flows, services connections, and so on is a thin layer on top of or connected to the application. As you migrate your applications, only the thin layer should need to be addressed.  Most of your application will function the same on any hosting compute service.

There are a few things you need to determine and decide before you migrate your set of applications to a new IBM Cloud location. You might already know most of the details about your {{site.data.keyword.ibmcf_full}} application deployments, especially if your organization planned the deployment and set up the hosting environment for the applications.

For those users wanting to confirm their application hosting layout, or investigate what they currently have deployed to {{site.data.keyword.ibmcf_full}}, there are several methods to analyze their current deployment.

## {{site.data.keyword.ibmcf_full}} CLI
{: #cf_depanal1}

The {{site.data.keyword.ibmcf_full}} CLI method is comprehensive in that it has complete access to all your {{site.data.keyword.ibmcf_full}} deployment details. The CLI allows you to output command results to files, visually on the screen and in JSON output. This gives the most data to analyze. 


## The IBM Cloud console
{: #cf_depanal3}

The [IBM Cloud web console](http://cloud.ibm.com){: external} is a good way to fully investigate the details of your your {{site.data.keyword.ibmcf_full}} environments and deployments, it can give you all the same information as the CLI method. This page will not go into details using that method, since we do so below with the CLI method, but you can use this as a double check or if you prefer to do it that way.  


## Investigating your application deployments
{: #cf_depanal4}

These steps show you how to investigate your {{site.data.keyword.ibmcf_full}} application deployments and capture data that you can use to evaluate how to set up your migration hosting target.

Run CLI commands to extract details related to what was returned by the {{site.data.keyword.ibmcf_full}} Analysis Tool. These commands allow you to save the details to files to do examine.

**Set up CLI access**
{: #dep_anal3}

If not installed previously on your local machine, [install the {{site.data.keyword.ibmcf_full}} CLI plugin](/docs/cli?topic=cli-ibmcloud_cli#ibmcloud_cf). Ensure you can login to the IBM Cloud and access the appropriate {{site.data.keyword.ibmcf_full}} regions. After confirming you have access, run `ibmcloud cf apps`, and the {{site.data.keyword.ibmcf_full}} applications running on IBM Cloud are displayed for that Org and space.

## Application analysis categories and steps
{: #application-analysis}

The following sections help you analyze your {{site.data.keyword.ibmcf_full}} environment using various commands. The resulting data from thes steps will help you with the decisions you need to take for migration to a new IBM Cloud compute service.

### Prerequisite setup
{: #prereq-description}

You need to connect to the proper MZR and Cloud Foundry Org and Space to be able to collect information, just like you do when you deploy an application.

#### Commands
{: #prereq-commands}

1. Authenticate to the IBM Cloud and a specific domain.

   ```text
   ibmcloud target --cf-api mccp.us-south.cf.cloud.ibm.com
   ```
   {: pre}

2. List the Orgs and Spaces in your account.

   ```text
   ibmcloud cf orgs
   ```
   {: pre}

   ```text
   ibmcloud cf spaces
   ```
   {: pre}

3. Target the proper Org and Space to target your additional commands.

   ```text
   ibmcloud target -o <ORG> -s <SPACE>
   ```
   {: pre}

#### Output
{: #prereq-output}

No output specific to {{site.data.keyword.ibmcf_full}} migration for this command. You will need to run the command for each region to collect the information for the deployment in that region.

#### Migration steps
{: #prereq-migration-steps}

You need to understand the layout for your global application deployments to know how to deploy a similar or modified deployment in your new compute service.

### Role-based Access Control (RBAC)
{: #rbac-description}

You will need to know what users have access to which {{site.data.keyword.ibmcf_full}} orgs and spaces.

For more information on IAM Roles, see [roles](/docs/account?topic=account-userroles).

#### Commands
{: #rbac-commands}

These commands will list the orgs, spaces, and the users who have access to them. Use the output of the commands to specify the <ORG> and <SPACE> values in the subsequent commands.

```text
ibmcloud cf orgs

ibmcloud cf spaces <ORG>

ibmcloud cf org-users <ORG>

ibmcloud cf space-users <ORG> <SPACE>
```
{: pre}

#### Output
{: #rbac-putput}

These commands will return the org, space, and user hierarchy. Repeat for each space in each org and organize into saved files as you need.

#### Migration steps
{: #rbac-migration-steps}

You will need this information to set up similar Role-based Access Control (RBAC) in your new compute service, however the new service handles these settings.

### Applications
{: #applications-description}

Determine application details for all the workloads you have deployed.

#### Commands
{: #applications-commands}

Run the following commands to get a list of all the apps under that space. The commands show you the deployed values of your applications.

To select each space where your applications are running, run:

```text
ibmcloud cf space-users <ORG> <SPACE>
```
{: pre}

Then run:

```text
ibmcloud cf apps -v
```
{: pre}

To gather information from that space. Repeat these commands for all orgs and spaces.

#### Output
{: #applications-output}

Redirect the output to files appropriate for your org and space layout. The information you will want to capture includes:

* running status
* number of instances
* memory size
* disk size
* the allocated URL
* buildpack (returned with -v)
* routes (returned with -v)
* domains (returned with -v)

#### Migration steps
{: #applications-migration-steps}

The collected information can factor into how you migrate your applications to your new compute platform.

For example, it is important to know the buildback version your app is using, if not the default. You should try to not use a specific buildpack version and keep your application updated so that the latest language buildpack is used.

### Application Auto-scaling
{: #application-autoscaling-description}

Determine how you are using dynamically scaling in your application instances to handle various workloads over time and usage.

#### Commands
{: #application-autoscaling-commands}

Use these references from the Cloud Foundry foundation for the auto-scaling capability to investigate how you are using this capability for your applications.
* [https://cloud.ibm.com/docs/cloud-foundry-public?topic=cloud-foundry-public-autoscale_cloud_foundry_apps](https://cloud.ibm.com/docs/cloud-foundry-public?topic=cloud-foundry-public-autoscale_cloud_foundry_apps){: external}
* [https://github.com/cloudfoundry/app-autoscaler-release](https://github.com/cloudfoundry/app-autoscaler-release){: external}

#### Output
{: #application-autoscaling-output}

You will see how your applications are automatically scaling.

#### Migration steps
{: #application-autoscaling-migration-steps}

This will factor into how you set up your scaling capabilities in your new hosting location.

Ensure that the same parameters that cause up and down auto-scaling are working for your new hosting environment.

### Application Variables
{: #application-variables-description}

You need to know the variables your application is using to access values in your current compute environment and are needed in your new compute environment. See the following for more information:

* [Cloud Foundry environment variables reference](https://docs.cloudfoundry.org/devguide/deploy-apps/environment-variable.html){: external}

* [Environment variables in IBM Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps#app_env)

#### Commands
{: #application-variables-commands}

The following command shows the system-provided and and user-defined variables your application can access.

```text
ibmcloud cf env <appname>
```
{: pre}

The following is an example command showing how your application uses these variables internally:

```text
cf env jc-hello-world | awk '/VCAP_SERVICES/{flag=1} /^}/{flag=0} flag' | sed 's/"VCAP_SERVICES"://' > vcap.json
```
{: pre}

#### Output
{: #application-variables-output}

Review how your application reads the system and user-defined variables. You will need to ensure that your application continues to have access to these variables.

#### Migration steps
{: #application-variables-migration-steps}

Your application uses these variables for various purposes. You will need to ensure that the small pieces of code that gather these variables for use inside your application are modified to continue to get this information in your new compute service.

### Application access, routes, domains
{: #application-access-description}

You probably know how you access any application you have in production, but if needed, this step will help you summarize how your applications are mapped and accessed.

You also need to know if your application is directly accessed using DNS, or using a load balancer such as IBM Cloud Internet Service or Akamai.  For more information, see the following:
* [Cloud Foundry Routes and Domains](https://docs.cloudfoundry.org/devguide/deploy-apps/routes-domains.html){: external}
* [Adding and using a custom domain](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains)
* [Managing Cloud Foundry routes and domains](https://www.ibm.com/support/pages/commands-manage-cloud-foundry-applications-domains-or-routes){: external}
* [Multi-Zone Region (MZR) overview](/docs/loadbalancer-service?topic=loadbalancer-service-multi-zone-region-mzr-overview)

#### Commands
{: #application-access-commands}

Commands to pull the needed information:

The following command lists all the routes that are used to access your applications.

```text
ibmcloud cf routes
```
{:pre}

The following command lists all the domains that are being used in those potential routes.

```text
ibmcloud cf domains
```
{: pre}

If you use the IBM Cloud Internet Service for routing, or to check, install the CIS command plug-in using the following command.

```text
ibmcloud plugin install cis
```
{: pre}

Then use commands in the [IBM Cloud Internet Service documentation](/docs/cis?topic=cis-cli-plugin-cis-cli) to see what you are using in IBM Cloud Internet Service

#### Output
{: #application-access-output}

Capture the route and domain information and make sure that you know how each critical application is access from the internet.

#### Migration steps
{: #application-access-migration-steps}

You will need to ensure that you set up similar routes and domain access in your new compute environment.

* If you have a custom domain setup (such as `xyzcompany.com`) you might need to upload a certificate into IBM Cloud Secrets Manager to allow that custom domain to work and enable that properly with your application hosting service.
* If you use load balancing, be sure to make note of the load balancing information for the new compute environment.

### Services and service bindings
{: #services-description}

You need to understand the services you are using that are bound to an application with permission to use that service.
* [Cloud Foundry application bindings](https://docs.cloudfoundry.org/devguide/services/application-binding.html){: external}

#### Commands
{: #services-commands}

The following command list the IBM Cloud services you have mapped to be used in your {{site.data.keyword.ibmcf_full}} applications.

```text
ibmcloud cf services
```
{: pre}

The following command lists any "customer user provided services" you might have set up.

```text
ibmcloud cf cups
```
{: pre}

#### Output
{: #services-output}

These are provided in `VCAP_APPLICATION` and `VCAP_SERVICES` variable groups in Cloud Foundry, but different services do these different ways.

#### Migration steps
{: #services-migration-steps}

In the IBM Cloud, you can use the same services with your new compute service as you have been with Cloud Foundry, there should be no need to move or migrate data. Your application can continue accessing those services once the basic connections have been made.

In the new IBM Cloud compute service, bind the compute service to the other IBM Cloud services you are using, and allow the necessary applications to access those services.

### Network policies
{: #network-description}

Determine the container-2-container communication for your application and any other network policies you have set up.

References:

* [IBM Cloud Foundry container-to-comtainer networking](https://www.ibm.com/cloud/blog/cloud-foundry-container-to-container-networking){: external}
* [Cloud Foundry networking](https://docs.cloudfoundry.org/devguide/deploy-apps/cf-networking.html){: external}
* [Cloud Foundry understanding networking](https://docs.cloudfoundry.org/concepts/understand-cf-networking.html){: external}

#### Commands
{: #network-commands}

The following command lists all the current network policies you have in place in your {{site.data.keyword.ibmcf_full}} org and space.

```text
ibmcloud cf network-policies
```
{: pre}

#### Output
{: #network-output}

Record the interconnections between your {{site.data.keyword.ibmcf_full}} applications, making note of what applications needs to talk to other applications.

#### Migration steps
{: #network-migration-steps}

Communicating directly between running containers or micro-services can be important for operational load, speed, and security. Be sure to understand the needs for the compute type you are moving to to ensure smooth ongoing operations.

### User responsibilities
{: #user-responsibilities-description}

What are the responsibilities for users for ongoing {{site.data.keyword.ibmcf_full}} applications?

* [Understanding your responsibilities when using IBM Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfp_responsibilities)

#### Commands
{: #user-responsibilities-commands}

{{site.data.keyword.ibmcf_full}} typically requires less user responsibilities than other application compute service models.

In {{site.data.keyword.ibmcf_full}} you generally need to ensure that your application has enough instances to run at the availability level you need, and ensure that your application is properly monitored for that availability level.

#### Output
{: #user-responsibilities-output}

Evaluate how your application development and operations team interact with the {{site.data.keyword.ibmcf_full}} system and your applications. Decide what steps need to be taken in the new migration environment, if any, that are different from what you do now.

#### Migration steps
{: #user-responsibilities-migration-steps}

User responsibilities might change with different hosting services. Different cloud hosting methods have different responsibilities for on-going management and monitoring of applications and infrastructure. Be sure to understand the needs for the compute type you are moving to to ensure smooth ongoing operations.




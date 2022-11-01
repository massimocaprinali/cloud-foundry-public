---

copyright:
  years: 2015, 2022
lastupdated: "2022-10-31"

keywords: cloud foundry, deprecation, deprecated

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Deprecation of IBM Cloud Foundry 
{: #deprecation}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. 
{: deprecated}

## Overview
{: #dep_ov}

{{site.data.keyword.cloud}} is announcing the full deprecation of {{site.data.keyword.ibmcf_notm}} on June 1, 2023. At that time, any {{site.data.keyword.ibmcf_notm}} application runtime instances running {{site.data.keyword.ibmcf_notm}} applications will be permanently disabled and deprovisioned. See the [deprecation details](#dep_details) for specific implications.
{: shortdesc}

{{site.data.keyword.cloud}} was started on Cloud Foundry, and has hosted many millions of gigabyte-hours of Cloud Foundry customer workloads over many years. At the time, Cloud Foundry brought the simplest ease-of-use and cloud PaaS deployment possible for our users. But as technology moves on, newer and more sophisticated technologies have become available for our {{site.data.keyword.cloud}} users.

The following describes the details of the deprecation, possible migration targets for your applications, and additional information.

## Timeline
{: #dep_timeline}

The timeline for this deprecation is as follows:

| Stage | Date | Description |
| ---------------- | ----------------- | ------------------------------------------------------------ |
| Announcement     | 31 May 2022      | Announcement of the {{site.data.keyword.ibmcf_notm}} deprecation. All current {{site.data.keyword.ibmcf_notm}} users as of early June 2022, will receive an email with information about the deprecation. Notifications will be put into the {{site.data.keyword.cloud}} console and related screens. |
| End-of-Marketing | 30 November 2022 | All {{site.data.keyword.cloud}} users, other than those who have an {{site.data.keyword.ibmcf_notm}} application deployed, will be blocked from new application deployments. As of 30 November 2022, new Cloud Foundry Organizations (Orgs) cannot be created by any user. |
| Reminders        | Ongoing           | Periodic reminders will be sent to all users with running {{site.data.keyword.ibmcf_notm}} applications that the end-of-support date is coming, with increasing frequency as the date approaches. |
| End-of-Support   | 1 June 2023      | All instances of running {{site.data.keyword.ibmcf_notm}} applications will be permanently disabled and deprovisioned. |
{: caption="Table 1. Deprecation timeline" caption-side="bottom"}

## {{site.data.keyword.ibmcf_notm}} deprecation details
{: #dep_details}

Some details of this announcement:

* A "deprecation" is a process, and we've announced the beginning of that process. It begins with the "Announcement" (this page), continues with "End-of-Marketing", and ends with "End-of-Support". Nothing happens until those announced dates above.

* At the "End-of-Marketing", users that don't have {{site.data.keyword.ibmcf_notm}} running workloads will be blocked from deploying new applications. All users that have Cloud Foundry application instances deployed can still keep deploying and re-deploying applications normally and as needed. Also at this time, new Cloud Foundry Organizations (Orgs) cannot be created by any user.

* At the "End-of-Support", all {{site.data.keyword.ibmcf_notm}} applications will, in a short period of time, be stopped and the deployed runtime applictions deleted.

* All other services you have been using in IBM Cloud, possibly from your {{site.data.keyword.ibmcf_notm}} applications, are unaffected - the {{site.data.keyword.ibmcf_notm}} deprecation refers only to the specific {{site.data.keyword.ibmcf_notm}} application runtime instances you have running, not services you might use with your {{site.data.keyword.ibmcf_notm}} applications.

* If you move to another IBM Cloud compute service, you should be able to connect to those previous connected services and continue using them normally.

* All {{site.data.keyword.ibmcf_notm}} application instances running on {{site.data.keyword.cloud}}, and all services and components that use {{site.data.keyword.ibmcf_notm}} capabilities, will remain fully functional until the End-of-Support date.

* Reminders of the approaching "End-of-Support" date will continue to be sent periodically by email to all users that have {{site.data.keyword.ibmcf_notm}} application runtime instances still running. To stop those emails, stop your applications so no instances are running.  When your running application instances reach zero, the reminder emails stop.

## {{site.data.keyword.ibmcf_notm}} user next steps
{: #dep_nextsteps}

Since all {{site.data.keyword.ibmcf_notm}} users need to decide where to move their Cloud Foundry workload applications prior to the {{site.data.keyword.ibmcf_notm}} "End-of-Support" date, review the following migration checklist and {{site.data.keyword.cloud}} compute service options in this announcement to help you decide which {{site.data.keyword.cloud}} application hosting service is right for your organization.

* Looking for the next level of easy application deployment? [{{site.data.keyword.codeenginefull_notm}}](/docs/codeengine?topic=codeengine-getting-started) provides the next level of technology from Cloud Foundry.
* Looking for increased experience and capability? [{{site.data.keyword.cloud}} Kubernetes Service](/docs/containers?topic=containers-getting-started) might be a good choice for your applications.
* Need greater efficiency and revolutionary delivery? [{{site.data.keyword.openshiftlong_notm}}](/docs/openshift?topic=openshift-getting-started) might be your solution.

Further information in this announcement will point to additional information to help you decide which application hosting service is right for your organization. All {{site.data.keyword.ibmcf_notm}} users need to decide where to move their Cloud Foundry workload applications prior to the {{site.data.keyword.ibmcf_notm}} "End-of-Support" date.

The following is a suggested checklist to plan your migration:

1. Understand and plan for the timeline and key milestone dates.
2. Evaluate the {{site.data.keyword.cloud}} compute migration options.
3. Pick an {{site.data.keyword.cloud}} service migration compute target that best meets your requirements and goals.
4. Deploy your applications to the target {{site.data.keyword.cloud}} service and compare the operation of your applications.
5. When ready, move application traffic as appropriate. It is suggested that you use a load balancer to slowly adjust workload during the migration. This way you can control your customer engagement with the migrated applications and do complete testing.
6. Stop your {{site.data.keyword.ibmcf_notm}} application instances, and when ready, delete the applications prior to the End-of-Support date.

Note: Reminders will be sent to you as long as you have running {{site.data.keyword.ibmcf_notm}} applications. Those reminders will end when all of your applications have been stopped and your usage of {{site.data.keyword.ibmcf_notm}} is at zero.

## {{site.data.keyword.cloud}} compute service options
{: #dep_opts}

{{site.data.keyword.cloud}} users have a choice of several modern application hosting runtime platforms on the {{site.data.keyword.cloud}}.

* [{{site.data.keyword.codeenginefull_notm}}](https://www.ibm.com/cloud/code-engine) is a fully managed, serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs. {{site.data.keyword.codeenginefull_notm}} even builds container images for you from your source code. Because these workloads are all hosted within the same Kubernetes infrastructure, all of them can seamlessly work together. The {{site.data.keyword.codeenginefull_notm}} experience is designed so that you can focus on writing code and not on the infrastructure that is needed to host it.

* [{{site.data.keyword.cloud}} Kubernetes Service](https://www.ibm.com/cloud/kubernetes-service) is an open source platform for managing containerized workloads and services across multiple hosts, and offers management tools for deploying, automating, monitoring, and scaling containerized apps with minimal to no manual intervention.

* [{{site.data.keyword.openshiftlong_notm}}](https://www.ibm.com/cloud/openshift) is a Kubernetes container platform that provides a trusted environment to run enterprise workloads. It extends the Kubernetes platform with built-in software to enhance app lifecycle development, operations, and security. With OpenShift, you can consistently deploy your workloads across hybrid cloud providers and environments.

For a comparison of these options, see [Migration options comparison](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation_option_comparison)

All of the {{site.data.keyword.cloud}} compute service options share the latest technology capabilities:

* Latest generation of VPC networking
* Latest Kubernetes delivery infrastructure
* Automatically securing apps with TLS
* Access to Kubernetes infrastructure and APIs for Kubernetes users
* Choice of public/internet-facing workloads or private ones
* The ability to build container images using Dockerfiles or use [Paketo buildpacks](https://paketo.io/){: external}
* The ability to deploy container images from public or private image registries

No matter which {{site.data.keyword.cloud}} compute you choose, you will have the latest cloud technology capabilities.

To learn more about migration details for potential migration targets for your existing {{site.data.keyword.ibmcf_notm}} applications, see: 

* [{{site.data.keyword.codeenginefull_notm}}](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation_code_engine) migration details
* [{{site.data.keyword.containerlong_notm}}](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation_iks) migration details
* [{{site.data.keyword.openshiftlong_notm}}](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation_openshift) migration details

To better understand your {{site.data.keyword.ibmcf_notm}} application deployment in preparation for migration, see [{{site.data.keyword.ibmcf_notm}} application deployment analysis.](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation_deploy_analysis)

See [{{site.data.keyword.ibmcf_notm}} migration tooling.](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation_migration_tooling) for additional information on tools to assist in migration.

## Migrating applications
{: #dep_migapp}

Review the suggested steps for migrating your {{site.data.keyword.ibmcf_notm}} applications to a new {{site.data.keyword.cloud}} compute service.

### Step 1: Investigate & review your current {{site.data.keyword.ibmcf_notm}} application deployments
{: #dep_s1}

Review [{{site.data.keyword.ibmcf_notm}} application deployment analysis](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation_deploy_analysis) to understand your current {{site.data.keyword.ibmcf_notm}} application deployments, including deployment details such as routes, domains, application instances, and sizes. This first key step is to survey what you currently have deployed before you begin your migration.

### Step 2: Investigate which {{site.data.keyword.cloud}} compute services on which to host your new application workload
{: #dep_s2}

Research which {{site.data.keyword.cloud}} compute service is the best fit for your application hosting needs. As you look into each one, use what you learned in the [previous step](#dep_s1), including how your application is deployed and the things your application needs and uses (services, routes, domains, and so on).


### Step 3: Deploy your application to your chosen {{site.data.keyword.cloud}} compute services
{: #dep_s3}

Deploy your application to that service and test the basic function and capabilities meet your needs.

### Step 4: Balance your incoming application traffic between the {{site.data.keyword.cloud}} compute types
{: #dep_s4}

Once you have deployed your applications to a new {{site.data.keyword.cloud}} hosting compute environment, there are several ways to move your user's routing from the {{site.data.keyword.ibmcf_notm}} hosted application to your application running on your selected IBM compute service.

* You can redirect traffic from the {{site.data.keyword.ibmcf_notm}} domain or host to the new location.
* If you are using a load balancer you can use it to send your traffic to your {{site.data.keyword.ibmcf_notm}} hosted app. Then, you can slowly change the percentage of traffic from the {{site.data.keyword.ibmcf_notm}} hosted app to your application running on your selected IBM compute service. By slowly migrating you can ensure that your application is operating properly on the new service and can that it can handle the workload. 

### Step 5: Shutting down {{site.data.keyword.ibmcf_notm}} applications
{: #dep_s5}

After you have migrated your applications to the new {{site.data.keyword.cloud}} compute service and your traffic is being handled 100% by the new service, you are ready to turn off your {{site.data.keyword.ibmcf_notm}} application usage. Stop your {{site.data.keyword.ibmcf_notm}} applications and delete them. After deleting your applications, your migration is complete.

## Migration assistance
{: #dep_mig_assist}

If you feel your organization needs help with your {{site.data.keyword.ibmcf_notm}} migration, or wants to engage another organization to assist you, here are some internal and external IBM partners that have a great deal of skill and experience with cloud application migrations and cloud native development improvements and transformations. Contact them if needed to discuss your specific requirements.

These are for-pay migration assistance options by IBM teams and third-party partners that are available to you.  IBM does not provide support for the listed third-party partners and is providing their information for your information and use as you see fit.
{: note}

{{site.data.keyword.cloud}} Expert Labs

* IBM Cloud Expert Labs is the IBM Cloud Platform Professional Services team providing deep technical expertise and a proven approach to modernize applications on IBM Cloud platform technologies. For your Cloud Foundry journey, we offer both Advisory Services to assess, recommend, and plan your Cloud Foundry modernization approach and Migration Services to assist with application remediation and migration. See [this document](https://cloud.ibm.com/media/docs/downloads/cloud-foundry-public/IBM%20Cloud%20Expert%20Labs%20-%20Migration%20Experts.pdf){: external} for more information and contacts to get started.

HCL Technologies

* The Kubernetes Migration Platform or KMP from HCL Technologies’ Cloud Native Labs is a SaaS-based application that can migrate hundreds of applications from Cloud Foundry or Kubernetes to any Kubernetes distribution with only three clicks, fully automated. KMP can migrate your Cloud Foundry applications to native containers on Red Hat OpenShift on IBM Cloud, seamlessly and efficiently. It provides effortless migration without prior application knowledge, no production outages, avoids vendor lock-in, is repeatable, and includes a complete data migration, often in minutes, using HCL's proprietary automated tooling. See [HCL - Kubernetes Migration Platform (KMP)](https://cloud.ibm.com/media/docs/downloads/cloud-foundry-public/KMP%20-%20Kubernetes%20Migration%20Platform%20by%20HCL.pdf){: external} for more information and contacts to get started.

Tata Consultancy Services

* TCS is a multinational information technology services and consulting company with significant experience in application and container technology.  Areas of experience include Cloud Foundry, Kubernetes, Cloud Native platform including  OpenShift, PaaS on IBM Cloud, Container-as-a-Service, and PaaS solutions on hyperscalers and private cloud. TCS migration of Cloud Foundry applications to Cloud Native platforms starts with an automated application assessment.  The assessment aims to reduce technical debt and modernize the application and security stack using the TCS Modernization framework and various assets and accelerators. See [TCS Migration Details](https://cloud.ibm.com/media/docs/downloads/cloud-foundry-public/TCS-RHOCP-Services-Capabilities%20-%20New%20Template%20-%202022%20-%20V1.1.pdf){: external} for more information and contacts to get started.

## **Customer support**
{: #dep_custsup}

These materials and resources should help you through your {{site.data.keyword.ibmcf_notm}} migration. If you have questions, or need help, contact [{{site.data.keyword.cloud}} Customer Support](https://www.ibm.com/cloud/support){: external} for additional information and assistance.




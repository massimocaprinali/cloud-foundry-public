---

copyright:

  years: 2018

lastupdated: "2018-11-27"

---


# Roles and responsibilities
{: #rolesresponsibilities}

If you deploy an instance of {{site.data.keyword.cfee_full}} for your organization you will also identify the people in your organization that will take care of administrative and operational tasks or decide to leave the majority of these tasks to {{site.data.keyword.IBM}} via the {{site.data.keyword.cfee_short}} managed service. This page gives an overview on roles and responsibilities surrounding an {{site.data.keyword.cfee_full}}.

## Roles
{: #roles}

![{{site.data.keyword.cfee_full_notm}}](img/ICFEE_HighLevelRoles.png  "Screen cap that shows the high level roles in an {{site.data.keyword.cfee_full_notm}}")

The following list shows the roles and responsibilities:

<dl>
<dt>**IBM Cloud Account Admin (manage the onboarding and support of users to IBM Cloud)**</dt>
  <ol type="a">
    <li>Add users to IBM Cloud account</li>
    <li>Onboard users to {{site.data.keyword.cfee_short}} and supporting services (IAM, public CF orgs)</li>
    <li>setup proper resource groups, IAM groups, IAM policies</li>
    <li>Responsible for the overall account resources (including {{site.data.keyword.cfee_short}} instances)</li>
  </ol>

<dt>**Cloud Foundry Administrator - manage the day to day requirements of development teams and Cloud Foundry users:**</dt>
  <ol type="a">
    <li>creates orgs</li>
    <li>assigns users and roles to orgs</li>
    <li>gives permissions inside of {{site.data.keyword.cfee_short}}</li>
    <li>has CF Admin access (aka cc.admin authority)</li>
  </ol>

<dt>**{{site.data.keyword.cfee_short}} "Stack" Administrator - Manage all elements of a {{site.data.keyword.cfee_short}} Instance(s):**</dt>
  <ol type="a">
    <li>Availability, health and performance monitoring</li>
    <li>Version management (upgrading to new {{site.data.keyword.cfee_short}} versions.  Includes communicating, negotiating and defining with stakeholders the decision and timing of updates).</li>
    <li>Capacity management of {{site.data.keyword.cfee_short}} (scaling up new cells/nodes)</li>
    <li>has {{site.data.keyword.cfee_short}} admin access (aka cc.admin authority)</li>
    <li>Troubleshooting and ticket filing of services consumed by developers (creating/adding a service to a {{site.data.keyword.cfee_short}}, or binding it to an app in the {{site.data.keyword.cfee_short}}).</li>
    <li>Infrastructure management
      <ol type="i">
        <li>Network mgmt as related to a {{site.data.keyword.cfee_short}} instance</li>
        <li>Storage mgmt as related to a {{site.data.keyword.cfee_short}} instance</li>
      </ol></li>
    <li>Management of {{site.data.keyword.cfee_short}} pre-req services (plan upgrades, availability)
      <ol type="i">
        <li>Kubernetes</li>
        <li>VMs hosting IKS workers</li>
        <li>Cloud Object Store</li>
        <li>Postgres</li>
      </ol></li>
      <li>Incident management for Cloud Foundry, {{site.data.keyword.cfee_short}}, IaaS (as related to a {{site.data.keyword.cfee_short}} instance)</li>
    <li>note: being a "stack" owner there is a large number of IaaS related responsibilities - for customers who use a significant amount of IBM Cloud resources, there is a tendancy to break up this Role between a {{site.data.keyword.cfee_short}} role and an IaaS role</li>
  </ol>

<dt>**Application Developer & Administrator - Lifecycle management of customer owned applications:**</dt>
  <ol type="a">
    <li>has developer access to org/space</li>
    <li>pushes apps</li>
    <li>provisioning & binding services</li>
    <li>Manage space membership and roles</li>
    <li>Manage domains and SSL certificates</li>
  </ol>
</dl>

<dl>
<dt>**Procurement focal**</dt>
~~<dd>Works with the IBM representative on establishing your {{site.data.keyword.Bluemix_dedicated_notm}} environment, including identifying the right people in your organization to work on any aspect of the project. The person assigned to this role takes on a project management role and oversees pattern selection, commercial arrangements, and arrangement of access to customer resources. The procurement focal is the overall contact for setting up the dedicated instance and tracking the process of the deployment.</dd>~~
<dt>**Compliance officer**</dt>
~~<dd>Works with the IBM representative to select a topology and deployment option that meets your security requirements. The person assigned to this role works with the IBM compliance consultant to determine which deployment patterns achieve the compliance goals.</dd>~~
<dt>**Network specialist**</dt>
~~<dd>Works with the IBM representative on the network plans for the {{site.data.keyword.Bluemix_notm}} deployment. The person assigned to this role reviews the required networking specifications required by IBM and works together with IBM on an implementation plan. At the end of the installation and verification phase, the person assigned to this role approves that the network configuration is in compliance with corporate standards.</dd>~~
<dt>**DevOps focal**</dt>
~~<dd>Works with the IBM representative to plan and apply the maintenance updates that are needed for the {{site.data.keyword.Bluemix_notm}} platform, services, and runtimes. The person assigned to this role also works with the IBM representative on the configuration of your {{site.data.keyword.Bluemix_dedicated_notm}} instance.</dd>~~
<dt>**Operations focal**</dt>
~~<dd>Works with the IBM support team as needed once the environment is up and running. This is someone with Superuser access to the Administration console who can approve and schedule maintenance updates for the {{site.data.keyword.Bluemix_notm}} environment and be available at all times in the event of a critical incident. The person assigned to this role must have technical knowledge of the {{site.data.keyword.Bluemix_notm}} environment and be in a position to reach others within company that have expert skills in an area that might be affected including networking or security, for example.</dd>~~
</dl>

~~Your customer representatives work with IBM specialists that work together to ensure that you always have the support that you need. You can upgrade to the Premium support tier to work with a dedicated Technical Account Manager (TAM) for your account. For more information about the different support tiers, see [Types of support](/docs/get-support/getstarttssup.html#typesofsupport).The TAM completes the following types of tasks:~~

<ul>
<li>~~Enables rapid adoption of your {{site.data.keyword.Bluemix_dedicated_notm}} environment.~~</li>
<li>~~Delivers valuable education and enablement materials to improve your self-sufficiency.~~</li>
<li>~~Cultivates a long-term relationship between you and {{site.data.keyword.Bluemix_notm}} development, support, and services that you use.~~</li>
</ul>

~~The {{site.data.keyword.Bluemix_notm}} support and operations team that works with you on your {{site.data.keyword.Bluemix_notm}} instance might access your local environment, but does so only for the following reasons.~~

<ul>
<li>~~To respond to alerts and perform operational maintenance~~</li>
<li>~~To attempt to reproduce a problem that is reported on a support ticket~~</li>
</ul>

## Responsibilities
{: #responsibilities}

From setting up your environment to continued maintenance, a variety of tasks must be completed. The following tables outline the required
tasks and the owner for completing the task throughout the deployment, progression and completion phases.

| **Task** | **Task details** | **{{site.data.keyword.cfee_short}} unmanaged responsible party** | **{{site.data.keyword.cfee_short}} managed responsible party** |
|----------|------------------|------------------------------------------------------------------|----------------------------------------------------------------|
| **Provisioning Phase** | The provisioning phase is used to establish the {{site.data.keyword.cfee_full_notm}}. The primary goals of this phase include the following: | <ul><li>~~Configure the {{site.data.keyword.cfee_full_notm}}.~~</li><li>~~Create the {{site.data.keyword.cfee_full_notm}} and provide access to runtimes and services.~~</li><li>~~Define and establish network connectivity between your corporate network and {{site.data.keyword.cfee_full_notm}} operations.~~</li><li>~~Identify and assign roles for your administrative team.~~</li></ul>  |   |
| Meet compliance standards | Create security and integration plan that includes costs, scheduling, and resources that are required to achieve security compliance. Certify {{site.data.keyword.cfee_short}} for government, industry and proprietary corporate standards and publish obtained certifications. | IBM + Customer | IBM |
| Compliance requirements   | Verify that the compliance certifications match the intended workload.  | Customer  | Customer  |
| Design solution| Architectural decisions surrounding one or multiple {{site.data.keyword.cfee_short}}, like choosing the location. | Customer | Customer <br></br> (Consulting services are available) |
| Configure environment | Configure environment based on predefined choices. | Customer |IBM + Customer|
| Deploy environment | The deployment process of an {{site.data.keyword.cfee_full_notm}} is completely automated. | Customer | Customer |
| **Completion Phase** | The final stage of completion represents the end of the relationship between you and IBM {{site.data.keyword.Bluemix_notm}}. The primary tasks for this phase include the following:  | <ul><li>~~Ending of the financial agreement.~~</li><li>~~Removing all network connections.~~</li><li>~~Recycling infrastructure.~~</li></ul> |   |
| End managed service agreement | Discuss and agree to an end to the CFEE managed service  contract. | N/A | IBM + Customer |
| Final backup   | Please refer to the backup task.  | Customer  | Customer  |
| Delete environment | Deleting the environment can be triggered by the customer. It will also clean up the prerequirements, i.e. the instance of the IBM Kubernetes Service, the instance of Compose for PostgreSQL and the instance of IBM Cloud Object Storage that were created during the deployment of the {{site.data.keyword.cfee_full_notm}}.  | Customer | Customer |
| Remove customer network firewall rules | Remove the firewall rules enabling network connectivity between IBM and the customer environment. | Customer | Customer |
| Recycle infrastructure | The services required to operate your CFEE (e.g IBM Cloud Object Store or Compose Databases) will be recycled based on the {{site.data.keyword.BluSoftlayer}}-defined processes. | IBM | IBM |
{: caption="Table 1. IBM Cloud Account Administrator tasks" caption-side="top"}

| **Task** | **Task details** | **{{site.data.keyword.cfee_short}} unmanaged responsible party** | **{{site.data.keyword.cfee_short}} managed responsible party** |
|----------|------------------|------------------------------------------------------------------|----------------------------------------------------------------|
| **Progression Phase** | Next is the progression phase. The progression phase describes the on-going, collaborative relationship between you and IBM Cloud. The primary goals for this phase include the following: | <ul><li>Review capacity and coordinate necessary adjustments.</li><li>Review maintenance and platform improvements.</li><li>Coordinate the activities for problem resolution and root cause analysis.</li></ul> |   |
| Perform administrative tasks | Perform adminstrative tasks for {{site.data.keyword.cfee_short}} like creating organizations, spaces, assign Cloud Foundry roles to users and give permissions to access {{site.data.keyword.cfee_short}} as well as the prerequired services like {{site.data.keyword.containershort}}, {{site.data.keyword.databases-for-postgresql_full_notm}} and {{site.data.keyword.cos_full_notm}}| Customer  | Customer  |
{: caption="Table 2. Cloud Foundry Administrator tasks" caption-side="top"}

| **Task** | **Task details** | **{{site.data.keyword.cfee_short}} unmanaged responsible party** | **{{site.data.keyword.cfee_short}} managed responsible party** |
|----------|------------------|------------------------------------------------------------------|----------------------------------------------------------------|
| **Progression Phase** | Next is the progression phase. The progression phase describes the on-going, collaborative relationship between you and IBM Cloud. The primary goals for this phase include the following: | <ul><li>Review capacity and coordinate necessary adjustments.</li><li>Review maintenance and platform improvements.</li><li>Coordinate the activities for problem resolution and root cause analysis.</li></ul> |   |
| Create and execute disaster recovery plan | Define the disaster recovery requirements, the disaster recovery plan and execute the plan in case of a disaster. | Customer | IBM + Customer |
| Create backup and recovery plan | Create a backup and recovery plan that defines the frequency and the requirements for on-and-off site distribution of the backup. You back up any application-specific data that you are responsible for. | Customer |IBM + Customer|
| Identify tools for event detection and problem determination | Identify IBM and third-party tools used for event detection and problem determination at the {{site.data.keyword.cfee_full_notm}} platform level. | Customer | IBM |
| Define escalation plan | Define the escalation plan to triage and resolve events detected from the monitoring components. | Customer | IBM |
| Install and configure security and audit components | Install and configure security components that are tied into the monitoring and escalation plan, e.g. Logging Service or Activity Tracker. | Customer | IBM |
| Configure and mantain network connectivity | Establish initial network configuration including firewall rules and DNS | Customer | IBM + Customer |
| Customize external solution components | Customize load balancers, e.g. for disaster recovery scenarios. | Customer | Customer |
| Track status for security, compliance and audit controls  | Track status up to the point where all tools and processes are in place to achieve identified compliance. | Customer | IBM |
| Continous capacity planning and execution   | Monitor capacity and add or remove capacity as your needs change.   | Customer   | IBM |
| Curate upgrade resp. maintenance versions (IKS, Postgres, COS)  | Curate, package and validate {{site.data.keyword.cfee_short}} install and upgrade images, incl. fixes for security vulnerabilities  | IBM  | IBM |
| Publish upcoming updates and maintenance | Create documentation for the required maintenance | IBM | IBM |
| Schedule and apply maintenance | Work with IBM to schedule required maintenance within a 21-day window. You can provide dates that might not work for you in the 21-day window, and IBM works to schedule the maintenance accordingly. | Customer | IBM + Customer |
| Address provisioning failures | Fix provisioning failures, if they occur, for customer-created services that are deployed to the Catalog. | Customer | IBM |
| Perform network and IP scans | Perform daily and monthly network and IP scans. | Customer | Customer |
| Conduct testing | Conduct periodic key controls over operations testing and third-party penetration testing. | Customer | IBM + Customer |
| Compliance execution    |  Make sure the overall solution (Application + {{site.data.keyword.cfee_short}} Platform) is compliant regarding required certifcations | Customer  | IBM + Customer  |
| Status reporting, audit coordination, and compliance meetings  | Complete status reporting, external audit coordination, and representation at compliance review status meetings. | Customer | IBM |
| Employment and business need verification | Complete quarterly employment verification and verification of continued business need for IBM representatives that have access to the customer environment. | Customer | IBM + Customer|
{: caption="Table 3. {{site.data.keyword.cfee_short}} Stack Administrator tasks" caption-side="top"}

| **Task** | **Task details** | **{{site.data.keyword.cfee_short}} unmanaged responsible party** | **{{site.data.keyword.cfee_short}} managed responsible party** |
|----------|------------------|------------------------------------------------------------------|----------------------------------------------------------------|
| **Progression Phase** | Next is the progression phase. The progression phase describes the on-going, collaborative relationship between you and IBM Cloud. The primary goals for this phase include the following: | <ul><li>Review capacity and coordinate necessary adjustments.</li><li>Review maintenance and platform improvements.</li><li>Coordinate the activities for problem resolution and root cause analysis.</li></ul> |   |
| Deploy and manage Applications | Deploy, scale, update, delete applications on top of {{site.data.keyword.cfee_short}} |  Customer | Customer  |
{: caption="Table 4. Application Developer & Administrator tasks" caption-side="top"}

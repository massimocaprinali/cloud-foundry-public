---

copyright:
  years: 2015, 2022
lastupdated: "2022-06-10"

keywords: cloud foundry, deprecation, deprecated

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Migration options comparison
{: #deprecation_option_comparison}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

The following is a comparison of the IBM Cloud compute service options to help you decide which target compute type is appropriate for your applications.  For example, how the application is hosted, delivered, and managed, as well as costs, integrations, and the skills needed.
{: shortdesc}


## Implementation and operational comparison 
{: #cf_depop1}

The following table gives a comparison of the implementation and operations of the IBM hosting services.

| Implementation or operation                                      | {{site.data.keyword.codeenginefull_notm}}                                      | {{site.data.keyword.containerlong_notm}}                                   | {{site.data.keyword.openshiftlong_notm}}                                   |
| ------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Delivered as                          | Multi-tenant IBM Cloud Service                               | Single-tenant or multi-tenant IBM Cloud Service              | Single-tenant or multi-tenant IBM Cloud Service              |
| Tenancy                               | Multi-tenant (shared clusters)                               | Single-tenant (dedicated cluster)                            | Single-tenant (dedicated cluster)                            |
| Cost                                  | [Only pay for when workloads run (GB-sec, vCPU-sec & invocations)](https://www.ibm.com/cloud/code-engine/pricing){: external} | [Cluster (size of cluster * time) + integrations (GB-time) + load balancers (cost * time)](https://www.ibm.com/cloud/kubernetes-service/pricing){: external} | [OCP license + Cluster (size of cluster * time) + integrations (GB-time) + load balancers (cost * time) Can obtain an OCP license if you get Cloud Paks](https://www.ibm.com/cloud/openshift/pricing){: external} |
| Management                            | Managed Application or Container                              | Managed Cluster                                              | Managed Cluster                                              |
| Skills                                | No container, cluster, networking, or infrastructure skills required | Networking and infrastructure skills required                | Networking and infrastructure skills required                |
| Integrations with IBM and third-party | [Integrations](/docs/codeengine?topic=codeengine-supported-integrations) | [Integrations](/docs/containers?topic=containers-supported_integrations) | [Integrations](/docs/openshift?topic=openshift-supported_integrations) |
| Responsibilities                      | [Responsibilites](/docs/codeengine?topic=codeengine-responsibilities-ce) | [Responsibilities](/docs/containers?topic=containers-responsibilities_iks) | [Responsibilities](https://cloud.ibm.com/docs/openshift?topic=openshift-responsibilities_iks) |
{: caption="Table 1. Implementation and operational comparison" caption-side="bottom"}

## Features and functional comparison
{: #cf_depop2}

The following is a comparison of the IBM Cloud compute service options to help you decide which target compute type is appropriate for your applications.  For example, detailed delivery questions, operations, and functional capabilities.

| Feature or function                                      | {{site.data.keyword.codeenginefull_notm}}                                      | {{site.data.keyword.containerlong_notm}}                                   | {{site.data.keyword.openshiftlong_notm}}                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Auto-scaling of your application based on load               | Auto-scaling based on number of HTTP requests is built in.   | In {{site.data.keyword.containerlong_notm}}, applications are synonymous to pods. With Kubernetes, you can automatically [scale up or down your pods based on CPU or memory.](/docs/containers?topic=containers-update_app#app_scaling) | In {{site.data.keyword.openshiftlong_notm}}, applications are synonymous to pods. With Kubernetes, you can automatically scale up or down your pods based on CPU or memory. [Open Shift has a "Serverless add-on which allows load-based auto-scaling.](/docs/openshift?topic=openshift-update_app) |
| "Scale-to-zero" of applications when idle                    | Yes, Scale-to-zero is built in.                              | No, minimum of pod replicas must be <= 1.                    | No, minimum of pod replicas must be <= 1.     Open Shift has a "serverless add-on" which allows scale to zero |
| Deployment of specific workload types                        | Almost anything that can be containerized, web apps, event-driven serverless functions, micro-services, batch jobs | [Types of typical workloads being moved to {{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-strategy)  \n [Use cases](/docs/containers?topic=containers-cs_uc_intro)  \n Can integrate {{site.data.keyword.codeenginefull_notm}} with {{site.data.keyword.containerlong_notm}}. | [Types of typical workloads being moved to {{site.data.keyword.openshiftlong_notm}}](/docs/openshift?topic=openshift-strategy)  \n [Use cases](/docs/openshift?topic=openshift-cs_uc_intro) |
| "Push your code" from local disk developer experience        | Yes                                                          | Yes                             | Yes                             |
| Complete cluster management experience through the {{site.data.keyword.containerlong_notm}} automation tools (API, CLI, console) | No - {{site.data.keyword.codeenginefull_notm}} is a multi-tenant service based on Kubernetes, and therefore only namespace-scoped operations are allowed (not entire cluster management) | Yes                                                          | Yes                                                          |
| Worldwide availability in single and multi-zones             | Multi-zone Regions                                           | Yes                                                          | Yes                                                          |
| Access to all IBM Cloud services                             | Yes                                                          | Yes                                                          | Yes                                                          |
| Can additional persistent storage be attached to application containers? | No                                                           | Yes                                                          | Yes                                                          |
| Isolation through IBM Cloud Virtual Private Cloud (VPC)      | Yes                                                          | Yes                                                          | Yes                                                          |
| Free level of service                                        | [Yes, free tier available, that re-sets every month](https://www.ibm.com/cloud/code-engine/pricing){: external} | [Yes, free limited cluster](/docs/containers?topic=containers-cs_ov) | No                                                           |
| Latest community Kubernetes distribution                     | Yes. {{site.data.keyword.codeenginefull_notm}} is built on {{site.data.keyword.containerlong_notm}}.         | Yes                                                          | Partially. Support is as close as possible to the latest major version.For example, right now OpenShift 4.10 is on Kubernetes 1.23, but we offer OpenShift 4.9 right now, which is on Kubernetes 1.22. Support is typically offered on the Kubernetes N-1 version. |
| Scope IBM Cloud IAM access policies to access groups for service access roles that sync to cluster RBAC | Yes                                                          | Yes                                                          | No                                                           |
| Classic infrastructure cluster on only the private network   | Not applicable, built on Gen2 infrastructure.                | Yes                                                          | No                                                           |
| GPU bare metal worker nodes                                  | No                                                           | Yes (but only for Classic, not for VPC)                      | Yes (but only for Classic, not for VPC)                      |
| Integrated IBM Cloud Paks and middleware                     | Not applicable                                               | Not applicable                                               | Yes                                                          |
| Built-in containers, builds, and tooling                     | Yes                                                          | No                                                           | Yes                                                          |
| Integrated CI/CD                                             | Yes (with IBM Cloud Toolchain)                               | No                                                           | Yes (with Jenkins)                                           |
| Stricter app security context set up by default              | Yes                                                          | No                                                           | Yes                                                          |
| Simplified Kubernetes developer experience, with an app console that is suited for beginners | Yes                                                          | No                                                           | Yes                                                          |
| Supported operating system                                   | Worker node OS same as IKS Container level OS (if using Docker) is what is supplied in the dockerfile Container level OS (if using buildpack) supports all runtimes available on paketo.io | Ubuntu 18.04 x86_64, 16.04 x86_64 (deprecated)               | Red Hat Enterprise Linux 7 (RHEL); however, as of 4.9, it will be CoreOS (RHCOS) |
| Secured routes encrypted with Hyper Protect Crypto Services  | No                                                           | No                                                           | Yes                                                          |
| Subscribe to event producers, such as Cloud Object Storage and Cron | Yes                                                          | Yes                                                          | Yes                                                          |
{: caption="Table 2. Features and functions comparison" caption-side="bottom"}



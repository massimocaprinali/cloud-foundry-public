---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Integrate third-party services using hooks
{: #hooks}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

You can use hooks to easily integrate third-party services in the SDK for Node.js buildpack. Note that {{site.data.keyword.IBM}} does not provide support for any third-party services that you integrate. For more information about support, see [Third-party services](/docs/cloud-foundry-public?topic=cloud-foundry-public-buildpack_support_statement).

The SDK for Node.js buildpack includes the Dynatrace hook. Dynatrace enables app monitoring of Node.js apps. Learn more about using the Dynatrace hook in the buildpack in the [Dynatrace documentation](https://www.dynatrace.com/support/help/technology-support/cloud-platforms/cloud-foundry/other-deployments-and-configurations/deploy-oneagent-on-pivotal-web-services-for-application-only-monitoring/){: external}.


When following instructions in third-party documentation, remember to use the `ibmcloud cf` command instead of `cf` to run commands for your {{site.data.keyword.cloud_notm}} buildpack.
{: tip}



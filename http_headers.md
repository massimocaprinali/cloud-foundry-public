---

copyright:
  years: 2015, 2022
lastupdated: "2022-11-01"

keywords: cloud foundry, custom domain

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# HTTP headers
{: #http-headers}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

When an HTTP or HTTPS request is sent to an application running on {{site.data.keyword.ibmcf_full}}, HTTP headers are added to the request.
{: shortdesc}

| Header | Contains |
| -------------- | ---------- |
| `x-client-ip` | IP address of the client |
| `x-forwarded-for` | IP address of the client and the {{site.data.keyword.ibmcf_full}} server routing the request |
| `x-forwarded-host` | Host specified in the client request |
| `x-forwarded-port` | Port specified in the client request |
| `x-forwarded-proto` | Protocol specified in the client request |
| `x-forwarded-scheme` | Protocol specified in the client request |
| `x-real-ip` | IP address of the client |
{: caption="Table 1. HTTP/HTTPS headers" caption-side="bottom"}

See [HTTP headers](https://docs.cloudfoundry.org/concepts/http-routing.html#http-headers){: external} for more information.


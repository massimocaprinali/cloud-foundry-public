---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Disable the NuGet Package Cache
{: #disabling_the_nuget_package_cache}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

In some situations, it might be necessary to clear the NuGet package cache for your app.  Doing so clears any existing cached NuGet packages and prevent the buildpack from caching any new packages.

You can clear the cache by setting the `CACHE_NUGET_PACKAGES` environment variable to `false` using the {{site.data.keyword.cloud_notm}} CLI:

```text
ibmcloud cf set-env <app_name> CACHE_NUGET_PACKAGES false
```
{: pre}

Alternatively, you can set the `CACHE_NUGET_PACKAGES` environment variable to `false` in your app's `manifest.yml` file:

```yaml
---
apps:
- name: sample-aspnetcore-app
  memory: 512M
  env:
    CACHE_NUGET_PACKAGES: false
```
{: codeblock}



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

# Disable the NuGet Package Cache
{: #disabling_the_nuget_package_cache}

In some situations, it might be necessary to clear the NuGet package cache for your application.  Doing so clears any existing cached NuGet packages and prevent the buildpack from caching any new packages.

You can clear the cache by setting the `CACHE_NUGET_PACKAGES` environment variable to `false` using the {{site.data.keyword.cloud_notm}} CLI:

```
ibmcloud cf set-env <app_name> CACHE_NUGET_PACKAGES false
```
{: pre}

Alternatively, you can set the `CACHE_NUGET_PACKAGES` environment variable to `false` in your application's `manifest.yml` file:

```
---
applications:
- name: sample-aspnetcore-app
  memory: 512M
  env:
    CACHE_NUGET_PACKAGES: false
```
{: codeblock}



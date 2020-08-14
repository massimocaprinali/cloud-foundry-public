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


# ASP.NET Core
{: #dotnet_core}

The ASP.NET Core runtime on {{site.data.keyword.cloud}} is powered by the ASP.NET Core buildpack. ASP.NET Core
is a modular open source framework for building .NET web applications.
.Net Core is a small, cross-platform runtime that can be targeted by ASP.NET Core applications.
They combine to enable modern, cloud-based web applications.
{: shortdesc}

## Detection
{: #dotnet-detection}
The {{site.data.keyword.cloud}} ASP.NET Core buildpack is used if there are one or more folders containing both a `project.json` and at least one `.cs` file anywhere in the application,
 or if the application is pushed from the output directory of the `dotnet publish` command.

## Starter application
{: #dotnet-starter_application}

{{site.data.keyword.cloud_notm}} provides an ASP.NET Core starter application.  The ASP.NET Core starter application is a simple app that provides a template that you can use. You can experiment with the starter app, and make and push changes to the {{site.data.keyword.cloud_notm}} environment.



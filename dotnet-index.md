---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-11"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# ASP.NET Core
{: #dotnet_core}

The ASP.NET Core runtime on {{site.data.keyword.cloud}} is powered by the ASP.NET Core buildpack. ASP.NET Core
is a modular open source framework for building .NET web apps.
.Net Core is a small, cross-platform runtime that can be targeted by ASP.NET Core apps.
They combine to enable modern, cloud-based web apps.
{: shortdesc}

## Detection
{: #dotnet-detection}

The {{site.data.keyword.cloud}} ASP.NET Core buildpack is used if there are one or more folders containing both a `project.json` and at least one `.cs` file anywhere in the app,
 or if the app is pushed from the output directory of the `dotnet publish` command.

## Starter app
{: #dotnet-starter_app}

{{site.data.keyword.cloud_notm}} provides an ASP.NET Core starter app.  The ASP.NET Core starter app is a simple app that provides a template that you can use. You can experiment with the starter app, and make and push changes to the {{site.data.keyword.cloud_notm}} environment.



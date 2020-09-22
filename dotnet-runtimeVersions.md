---

copyright:
  years: 2015, 2020
lastupdated: "09-15-2020"

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


# Runtime Versions
{: #runtime_versions}

## Supported versions
{: #supported_versions}

This buildpack supports the following versions, those marked as deprecated will be removed in a future buildpack release.  See [Microsoft's .NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/){: external}.


### .NET SDK version

| .NET SDK version        | Default          |
|-------------------------|------------------|
| 3.1.402                 |   Yes            |
| 3.1.401                 |   No             |
| 2.1.810                 |   No             |
| 2.1.809                 |   No             |
| 2.1.701                 |   No             |
| 2.1.606                 |   No             |
| 2.1.605                 |   No             |
| 2.1.509                 |   No             |
| 2.1.508                 |   No             |
| 2.1.403                 |   No             |


### .NET Core runtime versions

| .NET Core runtime version | Release type      |
|---------------------------|-------------------|
| 3.1.8                     | Current           |
| 3.1.7                     | Normal            |
| 2.1.21                    | Normal            |
| 2.1.22                    | Normal            |



### .NET ASP.NET Core versions

| .NET ASP.NET Core version | Release type      |
|---------------------------|-------------------|
| 3.1.8                     | Current           |
| 3.1.7                     | Normal            |
| 2.1.21                    | Normal            |





## Specifying the .NET SDK version

Control the .NET SDK version with an optional `global.json` file in the app's root directory. For example:
```
   {
      "sdk": {
        "version": "3.1.402"
      }
   }
```
{: codeblock}

If not specified, the latest MSBuild tooling is used.  To use project.json tooling, you can specify one of the listed project.json versions, but keep in mind that these versions will be removed in the future.  If the specified version is not included in the buildpack, the default version is used, and a warning appears in staging logs.



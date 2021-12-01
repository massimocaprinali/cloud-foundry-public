---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public


---


{{site.data.keyword.attribute-definition-list}}

# Runtime Versions
{: #runtime_versions}

## Supported versions
{: #supported_versions}

This buildpack supports the following versions, those marked as deprecated will be removed in a future buildpack release.  See [Microsoft's .NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/){: external}.


### .NET SDK version

| .NET SDK version        | Default          |
|-------------------------|------------------|
| 5.0.201                 |   Yes            |
| 5.0.200                 |   No             |
| 3.1.407                 |   No             |
| 3.1.406                 |   No             |
| 2.1.814                 |   No             |
| 2.1.813                 |   No             |


### .NET Core runtime versions

| .NET Core runtime version | Release type      |
|---------------------------|-------------------|
| 5.0.4                     | Current           |
| 5.0.3                     | Normal            |
| 3.1.13                    | Normal            |
| 3.1.12                    | Normal            |
| 2.1.26                    | Normal            |
| 2.1.25                    | Normal            |


### .NET ASP.NET Core versions

| .NET ASP.NET Core version | Release type      |
|---------------------------|-------------------|
| 5.0.4                     | Current           |
| 5.0.3                     | Normal            |
| 3.1.13                    | Normal            |
| 3.1.12                    | Normal            |
| 2.1.26                    | Normal            |
| 2.1.25                    | Normal            |


## Specifying the .NET SDK version

Control the .NET SDK version with an optional `global.json` file in the app's root directory. For example:

```json
   {
      "sdk": {
        "version": "5.0.201"
      }
   }
```
{: codeblock}

If not specified, the latest MSBuild tooling is used.  To use project.json tooling, you can specify one of the listed project.json versions, but keep in mind that these versions will be removed in the future.  If the specified version is not included in the buildpack, the default version is used, and a warning appears in staging logs.



---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}
 
# Compile, Publish, and Deploy Apps
{: #publish_configure_deploy}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

## Compiling your app in Release configuration (MSBuild only)
{: #compiling_in_release_configuration}

MSBuild-based projects are published by using the `dotnet publish` command during staging.  By default, the buildpack publishes your app in `Debug` configuration.
To publish your app in `Release` configuration, set the `PUBLISH_RELEASE_CONFIG` environment variable to `true`.

You can set the `PUBLISH_RELEASE_CONFIG` environment variable by using the following command:

```text
ibmcloud cf set-env <app_name> PUBLISH_RELEASE_CONFIG true
```
{: pre}

Alternatively, you can set the variable in your app's `manifest.yml` file:

```yaml
---
apps:
- name: sample-aspnetcore-app
  memory: 512M
  env:
    PUBLISH_RELEASE_CONFIG: true
```
{: codeblock}

## Pushing a Published App
{: #pushing_published_app}

If you want your app to contain all its required binary information so that the buildpack does not download any
external binary files, you can push a published *self-contained* app.  For more information on self-contained apps see [.NET Core App Types](https://docs.microsoft.com/en-us/dotnet/articles/core/app-types){: external}
.

To publish an app, issue a command similar to the following.

```text
dotnet publish -r ubuntu.14.04-x64
```
{: pre}

For self-contained apps, the app can then be pushed from the `bin/<Debug|Release>/<framework>/<runtime>/publish` directory.

For portable apps, the app can be pushed from the `bin/<Debug|Release>/<framework>/publish` directory.

If you are using a `manifest.yml` file in your app, you can specify the path to the publish output folder in your `manifest.yml` file.  Specifying the path eliminates the need to be in the folder when you push the app.

## Deploying apps with multiple projects
{: #developing_apps_with_multiple_projects}

To deploy an app containing multiple projects, you need to specify which project you want the buildpack to run as the main project. The main project is specified in a `.deployment` file in the root folder of the solution which sets the path to the main project. The path to the main project can be specified as the project folder or the project file (`.xproj` or `.csproj`).

For example, if a solution contains three projects, `MyApp.DAL`, `MyApp.Services`, and `MyApp.Web` in the `src` folder, and `MyApp.Web` is the main project, the format of the `.deployment` file is as follows:

```text
  [config]
  project = src/MyApp.Web/MyApp.Web.csproj
```
{: codeblock}

In this example, the buildpack automatically compiles the `MyApp.DAL` and `MyApp.Services` projects if they are listed as dependencies in the `project.json` file for `MyApp.Web`.  However, the buildpack only attempts to run the main project, `MyApp.Web`, when running `-p src/MyApp.Web`.



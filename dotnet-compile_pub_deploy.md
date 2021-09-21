---

copyright:
  years: 2015, 2021
lastupdated: "2021-09-21"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:audio: .audio}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: .ph data-hd-programlang='c#'}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: #curl .ph data-hd-programlang='curl'}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: .external target="_blank"}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: #java .ph data-hd-programlang='java'}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:middle: .ph data-hd-position='middle'}
{:navgroup: .navgroup}
{:new_window: target="_blank"}
{:node: .ph data-hd-programlang='node'}
{:note: .note}
{:objectc: .ph data-hd-programlang='Objective C'}
{:objectc: data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: .ph data-hd-programlang='PHP'}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:release-note: data-hd-content-type='release-note'}
{:right: .ph data-hd-position='right'}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:step: data-tutorial-type='step'} 
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:topicgroup: .topicgroup}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}

 
# Compile, Publish, and Deploy Apps
{: #publish_configure_deploy}

## Compiling your app in Release configuration (MSBuild only)
{: #compiling_in_release_configuration}

MSBuild-based projects are published by using the `dotnet publish` command during staging.  By default, the buildpack publishes your app in `Debug` configuration.
To publish your app in `Release` configuration, set the `PUBLISH_RELEASE_CONFIG` environment variable to `true`.

You can set the `PUBLISH_RELEASE_CONFIG` environment variable by using the following command:

```
ibmcloud cf set-env <app_name> PUBLISH_RELEASE_CONFIG true
```
{: pre}

Alternatively, you can set the variable in your app's `manifest.yml` file:

```
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
```
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
```
  [config]
  project = src/MyApp.Web/MyApp.Web.csproj
```
{: codeblock}

In this example, the buildpack automatically compiles the `MyApp.DAL` and `MyApp.Services` projects if they are listed as dependencies in the `project.json` file for `MyApp.Web`.  However, the buildpack only attempts to run the main project, `MyApp.Web`, when running `-p src/MyApp.Web`.



---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-03"

keywords: cloud foundry

subcollection: cloud foundry

---



{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
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
{:new_window: target="_blank"}
{:note: .note}
{:objectc data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
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
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: #swift .ph data-hd-programlang='swift'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vb.net: .ph data-hd-programlang='vb.net'}
{:video: .video}

# IBM Cloud Foundry buildpacks
{: #available_buildpacks}

Cloud Foundry buildpacks provide the runtime support for applications in the Cloud Foundry environment. When you deploy an application to {{site.data.keyword.cloud}}, it starts a buildpack that supports your application type. {{site.data.keyword.cloud_notm}} provides Cloud Foundry buildpack support for Java EE, Node.js, ASP.Net, Swift, and other application types.
You can use the buildpacks included with {{site.data.keyword.cloud_notm}} to deploy applications and bind them to services.

*  Cloud Foundry

    Cloud Foundry is an open source platform for application lifecycle automation.  {{site.data.keyword.cloud}} is built on top of the Cloud Foundry platform as a service. Check out the [Cloud Foundry documentation](https://www.cloudfoundry.org/learn/) to learn more.

*  Cloud Foundry Application

   A cloud foundry application or app, is any application intended to be instantiated by on one of the buildpacks provided by {{site.data.keyword.Bluemix_notm}}.

*  Buildpack

   A buildpack is a typically language specific package of software provided by {{site.data.keyword.Bluemix_notm}}. When an application is deployed to {{site.data.keyword.Bluemix_notm}} a buildpack appropriate for the application is chosen. The buildpack provisions the runtime environment for the application.  You can see the set of buildpacks provided by {{site.data.keyword.Bluemix_notm}} by issuing the `ibmcloud cf buildpacks` command from the command line.

*  Runtime

   A runtime is the set of software components which provide the exectuion environment for an application.  The terms *runtime* and *buildpack* are sometimes used interchangeably.  When a buildpack has completed deploying an application the runtime environment is established.

*  Starter

   A starter is a simple application designed for a particular runtime. The starters provide templates or samples of the language and runtime specific application types. You can use a starter to begin development of more sophisticated applications.

*  Service

   A service is a {{site.data.keyword.Bluemix_notm}} provided facility which can be coupled with an application.



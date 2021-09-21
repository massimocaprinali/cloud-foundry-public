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


# Determine your spaces
{: #determinespaces}



Within an organization, spaces provide an extra level of boundary enforcement and abstraction.
{: shortdesc}

A space is a reserved area in the organization where users can develop and run apps and services. You can create any number of spaces in an organization, and you can control the users that have access to a space. See [Spaces](/docs/account?topic=account-orgsspacesusers) for more details.

If you plan to define many spaces, you might want to create an app to help manage the spaces. When the number of spaces exceeds sixty, you might want to consider defining another organization.

## Spaces for single-organization versus multi-organization
{: #spaceconsiderations}

When you adopt a single-organization architecture, the level of segregation and abstraction is provided by the spaces that you define within the organization. Consider the following guidance when you define spaces:

* Define a space to host a service that requires provisioning and configuring only once in the organization.

* Define spaces based on the delivery lifecycle.

    For example, you can define one or more spaces for apps that are being developed, one or more spaces for apps that are in the test phase, and one or more   spaces for apps that are in production.

* If the delivery lifecycle boundary is not sufficient, you can achieve more segregation by defining one or more spaces per LOB and delivery phase.

* Identify if you need to enforce boundaries for different users groups.

    For example, your developers cannot develop the app and test it. You require a different set of users to test the app. In this scenario, you create two spaces, one for   developers of the app and one for testers of the app. Then, grant each set of users access to the correct space.

    When you implement a multi-organization architecture, you can segregate each organization by the LOB, the delivery lifecycle, or both. You can then define multiple spaces, which are based on the number of apps or projects that are delivered by the same department in the company. Consider the following guidance when you plan the spaces in an organization:

* Define a space to host a service that requires provisioning and configuring only once in the organization.

* Define a space per app, per group of related apps, or for a specific project.

* If you need to enforce boundaries for different users, define a space for each set of users. When a user is granted a developer role in a space, that user has full access to any resources and {{site.data.keyword.cloud_notm}} services) that are provisioned and running in that space. When you need to enforce tighter security to prevent users controlling every resource, consider defining different spaces. Within any of these spaces, you can provision {{site.data.keyword.cloud_notm}} services that are used by the apps running in that space.

## Space naming, restrictions, and management
{: #spaceadmin}

To define the different spaces for your cloud organization, consider the following guidance:

* Define and enforce a naming convention. For example, define a naming convention where the space name includes information about where the organization is located and the type of cloud. You can change the name of a space after it is created. If a space name is altered, notify all of the space team members about the change.

* Define the restrictions that apply to the space. For example, define the type of apps that can be developed, managed, and deployed in each space.

* Identify the manager of the space. You might want to delegate the space administration to more than one person.



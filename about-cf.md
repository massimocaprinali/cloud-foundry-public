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


# What is Cloud Foundry?
{: #what-is-cloud-foundry}

[Cloud Foundry](https://www.cloudfoundry.org/){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") is the premier industry standard Platform-as-a-Service (PaaS), that ensures the fastest, easiest, and most reliable deployment of cloud-native applications. Cloud Foundry ensures that the build and deploy aspects of coding remain carefully coordinated with any attached services — resulting in quick, consistent and reliable iterating of applications.

Check out the following [video](https://www.youtube.com/watch?v=lH6EY761wgc){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") to learn more about all the compute options available on {{site.data.keyword.cloud_notm}}.
{: shortdesc}

## Benefits of Cloud Foundry
{: #key-benefits-of-cloud-foundry}

**Choose your own language** - {{site.data.keyword.cloud}} Foundry includes runtimes for Java, Node.js, PHP, Python, Ruby, Swift and Go; plus, Cloud Foundry community build packs are also available. Combined with DevOps services, the application runtimes enable a delivery pipeline that automates much of the iterative development process.

**Fault tolerant** - Runtimes facilitate developing applications as stateless processes that quickly: start and stop, replicate if an instance fails, and duplicate if sustained or increased performance requires.

**Extend apps with services** - Runtimes link {{site.data.keyword.cloud_notm}} services to applications as endpoints, giving any instance of an application embedded knowledge of how to manage relevant calls and data. In fact, runtimes manage all linked resources this way: SDKs, APIs (whether made available as cloud services or exposed from within a traditional enterprise as custom services), and also applications themselves when used as resources by other applications.

**Access control** - Fine grain assignment/dispensing of compute capacity to development teams.

**Automatic placement** - Applications are automatically placed across multiple data-center PODs fpr maximum reliability.

**Automatic health management** - Crashing applications will restart automatically.

**Automatic routing** - Internet reachable routes are automatically created for your applications.

**High availability** - Supports full high availability for extremely high application availability.

**Automatic deployment scaling** - The Auto-Scaling for {{site.data.keyword.cloud_notm}} service enables you to automatically increase or decrease the compute capacity of your application, to rapidly adjust to dynamic loading needs.

## {{site.data.keyword.cloud_notm}} Foundry offerings
{: #ibmcf-offerings}

IBM offers the Cloud Foundry PaaS in several hosting models, allowing you to customize your PaaS experience and balance a range of considerations, including price, deployment speed, and security.

### Public
{: #ibmcf-public}

Run your cloud-native app using Cloud Foundry for simple stand-up and powerful scaling and traffic management. Consumption is by hour and changes dynamically based on usage.  For more information see the {{site.data.keyword.cloud_notm}} Public documentation [here](https://cloud.ibm.com/docs/cloud-foundry-public){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").  

### Enterprise Environment
{: #ibmcf-ee}

Allows you to create and manage isolated environments for hosting Cloud Foundry applications exclusively for your enterprise. It provides self-service deployment and elastic consumption,  rapid provisioning, complete access to Cloud Foundry admin operations, and is fully integrated with the vast catalog of {{site.data.keyword.cloud}} services, enabling you to building complex applications with a wide range of services.

### Private
{: #ibmcf-private}

An on-premises Cloud Foundry platform that runs in your data-center on your infrastructure, giving the highest level of isolation security for your application hosting.



---

copyright:
  years: 2015, 2021
lastupdated: "2021-10-20"

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
{:step: data-tutorial-type='step'} <!-- Apply to steps for automatic numbering -->
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


# What are the possible network addresses that Cloud Foundry apps can be running on?
{: #network-address}

When you deploy Cloud Foundry apps, there are a known list of possible network addresses that the app will be deployed on depending on the region.
{: shortdesc}

Network addresses are subject to change from time to time. 
{: important}

<!--- Everything below this line is refreshed periodically --->
In the Dallas (us-south) region, the following network addresses are in use:
```
169.46.101.192/27
169.46.101.64/27
169.46.101.96/27
169.46.104.128/27
169.46.105.64/27
169.46.106.224/27
169.46.108.32/27
169.46.115.96/27
169.46.120.96/27
169.46.95.16/29
169.47.196.0/27
169.47.199.64/27
169.47.200.160/27
169.47.201.32/27
169.47.205.32/27
169.48.166.64/26
169.61.155.160/27
169.61.175.128/26
169.61.179.128/25
169.61.185.0/24
169.62.152.32/27
169.62.171.0/24
169.62.205.128/25
169.62.231.0/24
```

In the Washington DC (us-east) region, the following network addresses are in use:
```
169.60.80.160/27
169.60.82.128/26
169.60.84.128/25
169.61.82.224/27
169.61.87.128/25
169.61.87.64/26
169.63.78.192/26
169.63.80.128/25
169.63.83.0/24
```

In the London (eu-gb) region, the following network addresses are in use:
```
141.125.69.128/25
141.125.69.64/27
141.125.76.64/26
158.175.103.128/25
158.175.120.160/27
158.175.85.64/26
158.176.68.64/26
158.176.84.128/27
158.176.87.0/25
```

In the Frankfurt (eu-de) region, the following network addresses are in use:
```
149.81.126.96/27
149.81.69.192/26
159.122.84.160/27
161.156.69.0/27
161.156.72.64/26
169.50.23.96/27
169.50.24.160/27
169.50.39.128/27
169.50.40.128/27
169.50.44.128/26
```

In the Sydney (au-syd) region, the following network addresses are in use:
```
130.198.71.64/27
130.198.80.64/26
130.198.81.128/25
135.90.65.64/26
135.90.70.0/27
168.1.31.96/27
168.1.40.64/27
168.1.40.96/27
168.1.44.160/27
168.1.44.64/27
168.1.45.0/27
168.1.45.64/27
168.1.45.96/27
168.1.8.32/27
```


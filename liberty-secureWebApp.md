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


# Write secure Java web apps
{: #secure_java_web_app}

All web apps and their runtime environments must be designed and coded with security in mind to avoid introducing severe security vulnerabilities.  Review [Securing Liberty and its apps](https://www.ibm.com/support/knowledgecenter/en/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_sec.html){: external} to learn about implementing security best practices such as password encryption, authentication, and enabling secure communications.
{: shortdesc}

{{site.data.keyword.cloud}} provides a secure starter app to help you write more secure Liberty Java code and avoid most of the Cross-Site Scripting (XSS) issues. You may download this [secure starter app](https://github.com/IBM-Cloud/java-secure-app){: external}, build it and deploy it locally and on {{site.data.keyword.cloud_notm}}.

## Why write secure web apps
{: #why}

A security vulnerability can be exploited by various security attacks. An attack might steal credentials, cause loss of data and function, disrupt services, and damage the reputation and revenue of a business. Cross-Site-Scripting, XSS, is one of the common security vulnerabilities found in most web apps that must be avoided.

Instead of learning the theory of XSS attacks and remedial techniques before you start  web app development, you can use this [secure starter app](https://github.com/IBM-Cloud/java-secure-app){: external}. The secure starter app includes coding examples of key secure coding practices that prevent XSS so you can start developing while you learn and apply XSS prevention techniques.

## How to use the secure sample app
{: #how}

You can use the [secure starter app](https://github.com/IBM-Cloud/java-secure-app){: external} as a starting point for new Liberty app development. Start by learning the XSS countermeasure code in the app and then apply it to the operations of the app API. The countermeasures in the secure starter app help prevent malicious user input from damaging your app both on the server and browser by mitigating or preventing XSS attacks.

First, download this secure starter app, then build and deploy it on {{site.data.keyword.cloud_notm}} or locally the same way as you do with the [getting-started-java](https://github.com/IBM-Cloud/get-started-java){: external} sample app.  Go to [Getting started with Liberty on {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry-public?topic=cloud-foundry-public-getting-started-liberty) to learn more about building and deploying apps on {{site.data.keyword.cloud_notm}}.  To get started, you can use these steps to clone, build, and run the app.

```
git clone https://github.com/IBM-Cloud/java-secure-app
```
{: pre}

```
cd java-secure-app
```
{: pre}

```
mvn install liberty:run-server
```
{: pre}

View the app at `http://localhost:9080/GetStartedSecureJava/`

## Enforce HTTPS on all pages in your app
{: #liberty-enforce_https}

To enforce HTTPS instead of HTTP on all pages in your app, the following changes need to be made.

Modify your `server.xml` to enable the `appSecurity-2.0` feature:

```
<featureManager>
  <feature>appSecurity-2.0</feature>
</featureManager>
```
{: codeblock}

Modify your `web.xml` file to include the following security constraint:

```
<security-constraint>
  <web-resource-collection>
    <web-resource-name>Entire Application</web-resource-name>
    <url-pattern>/*</url-pattern>
  </web-resource-collection>
  <user-data-constraint>
    <transport-guarantee>CONFIDENTIAL</transport-guarantee>
  </user-data-constraint>
</security-constraint>
```
{: codeblock}

This makes your app force all connections to use HTTPS automatically and will not allow any HTTP connections.

## Secure starter app contents
{: more}
The secure starter app contains **BadServlet.java**. This app shows an example of insecure code that developers might write if care is not taken.

The secure starter app also contains **GoodServlet.java**, which includes a number of good secure coding practices such as input validation, output encoding, secure HTTP Header settings, and Content Security Policy. These practices are key countermeasures against XSS. Applying them can also mitigate other vulnerabilities such as some injection and directory traversal.

## XSS cheat sheet

See the [XSS Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html){: external} to learn more about XSS and its countermeasures.



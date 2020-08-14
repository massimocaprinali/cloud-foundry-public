---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-14"

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

# Write secure Java web applications
{: #secure_java_web_app}

All web applications and their runtime environments must be designed and coded with security in mind to avoid introducing severe security vulnerabilities.  Review [Securing Liberty and its applications](https://www.ibm.com/support/knowledgecenter/en/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_sec.html){: external} to learn about implementing security best practices such as password encryption, authentication, and enabling secure communications.
{: shortdesc}

{{site.data.keyword.cloud}} provides a secure starter application to help you write more secure Liberty Java code and avoid most of the Cross-Site Scripting (XSS) issues. You may download this [secure starter application](https://github.com/IBM-Cloud/java-secure-app){: external}, build it and deploy it locally and on {{site.data.keyword.cloud_notm}}.

## Why write secure web apps
{: #why}

A security vulnerability can be exploited by various security attacks. An attack might steal credentials, cause loss of data and function, disrupt services, and damage the reputation and revenue of a business. Cross-Site-Scripting, XSS, is one of the common security vulnerabilities found in most web applications that must be avoided.

Instead of learning the theory of XSS attacks and remedial techniques before you start  web application development, you can use this [secure starter application](https://github.com/IBM-Cloud/java-secure-app){: external}. The secure starter application includes coding examples of key secure coding practices that prevent XSS so you can start developing while you learn and apply XSS prevention techniques.

## How to use the secure sample app
{: #how}

You can use the [secure starter application](https://github.com/IBM-Cloud/java-secure-app){: external} as a starting point for new Liberty application development. Start by learning the XSS countermeasure code in the app and then apply it to the operations of the application API. The countermeasures in the secure starter application help prevent malicious user input from damaging your application both on the server and browser by mitigating or preventing XSS attacks.

First, download this secure starter application, then build and deploy it on {{site.data.keyword.cloud_notm}} or locally the same way as you do with the [getting-started-java](https://github.com/IBM-Cloud/get-started-java){: external} sample application.  Go to [Getting started with Liberty on {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry-public?topic=cloud-foundry-public-getting-started-liberty) to learn more about building and deploying applications on {{site.data.keyword.cloud_notm}}.  To get started, you can use these steps to clone, build, and run the app.

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
View the app at http://localhost:9080/GetStartedSecureJava/

## Enforce HTTPS on all pages in your application
{: #liberty-enforce_https}

To enforce HTTPS instead of HTTP on all pages in your application, the following changes need to be made.

Modify your server.xml to enable the `appSecurity-2.0` feature:

```
  <featureManager>
    <feature>appSecurity-2.0</feature>
  </featureManager>
```
{: codeblock}

Modify your web.xml file to include the following security constraint:

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

This makes your application force all connections to use HTTPS automatically and will not allow any HTTP connections.

## More Info
{: more}
The secure starter application contains **BadServlet.java**. This application shows an example of insecure code that developers might write if care is not taken.

The secure starter application also contains **GoodServlet.java**, which includes a number of good secure coding practices such as input validation, output encoding, secure HTTP Header settings, and Content Security Policy. These practices are key countermeasures against XSS. Applying them can also mitigate other vulnerabilities such as some injection and directory traversal.

Refer to the [XSS Prevention Cheat Sheet](https://www.owasp.org/index.php/XSS){: external} to learn more about XSS and its countermeasures.



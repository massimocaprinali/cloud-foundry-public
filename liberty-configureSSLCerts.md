---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-31"

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

# Security Considerations

If you want to add your own certificates to the Liberty keystore, there are a few considerations to note. When a stand-alone app is deployed, a default Liberty configuration is provided for the app. You would need to configure an on premises Liberty server and use one of the following methods for pushing your app: [server directory](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#server_directory) or [packaged server](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#packaged_server).

## Adding trusted certificates to Liberty
In the IBM Knowledge Center there are a few resources that will help guide you to create certificates in the Liberty keystore.

- [Creating the Liberty keystore and certificate](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_sec_ssl.html){: external} : outlines the steps needed to use a self-signed certificate and creating a keystore that can then be used in a production environment.
- [Adding trusted certificates in Liberty](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_add_trust_cert.html){: external} : this doc outlines the process of adding trusted certificates to Liberty truststore to secure communications with Liberty
- [Enabling SSL communication in Liberty](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_sec_ssl.html){: external} : This section outlines the steps needed to add SSL configuration options including creating Liberty supported keystores i.e. Java Keystore (JKS) and setting SSL defaults in Liberty
- [SSL certificates for WAS Liberty Profile](https://www.ibm.com/support/knowledgecenter/en/SSZJPZ_11.7.0/com.ibm.swg.im.iis.found.admin.common.doc/topics/admin_mg_certs_waslib.html){: external} : found under managing certificates section, this details changing the SSL server key for WAS Liberty profile and generating new keys.



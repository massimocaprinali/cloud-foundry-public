---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Adding certificates to the Libery keystore

When a stand-alone app is deployed, a default Liberty configuration is provided for the app. If you want to add your own certificates to the Liberty keystore, you need to configure an on premises Liberty server and use one of the following methods for pushing your app: [server directory](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#server_directory) or [packaged server](/docs/cloud-foundry-public?topic=cloud-foundry-public-options_for_pushing#packaged_server).

## Adding trusted certificates to Liberty
The {{site.data.keyword.IBM}} Knowledge Center has resources that will help you to create certificates in the Liberty keystore.

- [Creating the Liberty keystore and certificate](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_sec_ssl.html){: external} outlines the steps that are needed to use a self-signed certificate and creating a keystore that can then be used in a production environment.
- [Adding trusted certificates in Liberty](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_add_trust_cert.html){: external outlines the process of adding trusted certificates to Liberty truststore to secure communications with Liberty.
- [Enabling SSL communication in Liberty](https://www.ibm.com/support/knowledgecenter/SSEQTP_liberty/com.ibm.websphere.wlp.doc/ae/twlp_sec_ssl.html){: external} outlines the steps that are needed to add SSL configuration options that include creating Liberty supported keystores; for example, Java&trade; Keystore (JKS) and setting SSL defaults in Liberty.
- [SSL certificates for WebSphere Application Server Liberty Profile](https://www.ibm.com/support/knowledgecenter/en/SSZJPZ_11.7.0/com.ibm.swg.im.iis.found.admin.common.doc/topics/admin_mg_certs_waslib.html){: external} under the managing certificates section, details how to change the SSL server key for WebSphere Application Server Liberty profile and generating new keys.



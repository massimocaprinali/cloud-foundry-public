---

copyright:
  years: 2015, 2022
lastupdated: "2022-08-31"

keywords: cloud foundry, ssl, certificates, access, restrict access, csr, upload, import, csr, certificate signing request

subcollection: cloud-foundry-public

---

{{site.data.keyword.attribute-definition-list}}

# Creating certificate signing requests
{: #ssl_csr}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

You can secure your applications by uploading SSL certificates and restricting access to the applications. 
{: shortdesc}

## Creating a certificate signing request
{: #create_csr}

Before you can upload the SSL certificates to which you’re entitled with {{site.data.keyword.cloud}}, you must create a certificate signing request (CSR) on your server. A CSR is a message that is sent to a certificate authority to request the signing of a public key and associated information. Most commonly, CSRs are in PKCS #10 format. The CSR includes a public key, a common name, organization, city, state, country, and email. SSL certificate requests are accepted only with a CSR key length of 2048 bits.

The methods for creating a CSR vary depending on your operating system. The following example shows how to create a CSR by using [the OpenSSL command-line tool](https://www.openssl.org/){: external}:

```text
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privatekey.key
```
{: codeblock}

OpenSSL SHA-512 implementation depends on compiler support for 64-bit integer type. You can use the SHA-1 option for apps that have compatibility issues with the SHA-256 certificate.
{: tip}

Be sure to submit a single request to delete or create crypto, and then expect a wait time of at least 10 minutes before you submit another request. If you don't allow for sufficient time between requests, it's possible for requests to be crossed or errors to occur in creating or updating the crypto.
{: note}

### Required CSR contents
{: #csr_contents}

For the CSR to be valid, the following information must be entered when you create the CSR:

* **Country name**: A two-digit code for the country or region. For example, `US` is the country code for the United States. For other countries or regions, before you create the CSR, check the [list of ISO country codes](https://www.iso.org/obp/ui/#search){: external}.
* **State or province**: The full, unabbreviated name of the state or province.
* **Locality**: The full name of the city or town.
* **Organization**: The full name of the business or company, as legally registered in your locality, or personal name. For companies, be sure to include the registration suffix, such as Ltd., Inc., or NV.
* **Organization unit**: The branch name of your company that is ordering the certificate, such as accounting or marketing.
* **Common name**: The fully qualified domain name (FQDN) for which you’re requesting the SSL certificate. Wildcards are not supported in the common name.

You can use Subject Alternative Names (SAN), but the provided host names must not be issued in other deployed certificates to prevent CN collisions.
{: note} 

A certificate is issued by a certificate authority and is digitally signed by that authority. After you create the CSR, you can generate your SSL certificate on a public certificate authority.

## Uploading SSL certificates
{: #ssl_certificate}

You can apply a security protocol to provide communication privacy for your app to prevent eavesdropping, tampering, and message forgery. If you have a Lite account, you must upgrade your account to upload a certificate.

In order to use TLS certificates in IBM Cloud Foundry custom domains you need to perform few steps:
1. Obtain, if not already having it,  a valid certificate from a Certificate Authority (via CSR creation) [Ref](/docs/cloud-foundry-public?topic=cloud-foundry-public-ssl_csr#create_csr)
2. Upload certificates into a {{site.data.keyword.secrets-manager_full_notm}} instance [Ref](/docs/cloud-foundry-public?topic=cloud-foundry-public-ssl_csr#ssl_import)
3. Authorise IBM Cloud Foundry service to  access uploaded certificates [Ref](/docs/cloud-foundry-public?topic=cloud-foundry-public-ssl_csr#ssl_cert_auth)
4. Let custom domain uses the uploaded certificate by mapping its CRN.[Ref](/docs/cloud-foundry-public?topic=cloud-foundry-public-ssl_csr#ssl_cert_custom_domain)

SSL certificate mapping is a region specific operation. If you are using the same custom domain and SSL cert across multiple regions, you need to map certificate for each one.
{: note}

When an expired or expiring certificate must be renewed, and after the new certificate is ready, delete the existing certificate and then add the new one.
{: note}

When you use a custom domain to serve the SSL certificate, use the following region endpoints to provide the URL route for your organization in {{site.data.keyword.cloud_notm}}:

| Region | Endpoint |
| ------ | -------- |
| US-South | `custom-domain.us-south.cf.cloud.ibm.com` |
| US-East | `custom-domain.us-east.cf.cloud.ibm.com` |
| EU-DE | `custom-domain.eu-de.cf.cloud.ibm.com` |
| EU-GB | `custom-domain.eu-gb.cf.cloud.ibm.com` |
| AU-SYD | `custom-domain.au-syd.cf.cloud.ibm.com` | 
{: caption="Table 1. Cloud Foundry custom domain region endpoints" caption-side="top"}

To upload a certificate for your Cloud Foundry app, complete the following steps:

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click **Manage**, and select **Account**.
2. Click **Cloud Foundry orgs**.
3. From the Actions column, click the Actions icon ![More Actions icon](../icons/action-menu-icon.svg), and select **Domains**.
4. Click **Upload** for your custom domain.
5. Select an option, upload the file, and click **Add**.
  
    * Certificate: A digital document that binds a public key to the identity of the certificate owner, which enables the certificate owner to be authenticated. A certificate is issued by a certificate authority and is digitally signed by that authority. A certificate is generally issued and signed by a certificate authority. However, for testing and development purposes, you might use a self-signed certificate.
    * Private key: An algorithmic pattern that is used to encrypt messages that only the corresponding public key can decrypt. The private key is also used to decrypt messages that were encrypted by the corresponding public key. The private key is kept on the user system and is protected by a password.
    * Intermediate certificate (optional): A subordinate certificate that is issued by the trusted root certificate authority (CA) specifically to issue end-entity server certificates. The result is a certificate chain that begins at the trusted root CA, passes through the intermediate certificate, and ends with the SSL certificate issued to the organization. Use an intermediate certificate to verify the authenticity of the main certificate. Intermediate certificates are typically obtained from a trusted third party. You might not require an intermediate certificate when you test your app before you deploy it to production.
    * Enable request of client certificate: When you enable this option, a user who tries to access an SSL protected domain is requested to provide a client-side certificate. For example, in a web browser, when a user tries to access an SSL protected domain, the web browser prompts the user to provide a client certificate for the domain.   
    * Client certificate truststore (optional): Includes the client certificates for the users who you want to allow access to your app. Upload a client certificate truststore file to enable the option to request a client certificate.
  
    You can set up mutual authentication by uploading a client certificate truststore that includes a public key in its metadata.
    {: tip}

## Importing SSL certificates into {{site.data.keyword.secrets-manager_full_notm}}
{: #ssl_certificate_secrets_manager}

You can apply a security protocol to provide communication privacy for your app to prevent eavesdropping, tampering, and message forgery. If you have a Lite account, you must upgrade your account to upload a certificate.

When an expired or expiring certificate must be renewed, and after the new certificate is ready, delete the existing certificate and then add the new one.
{: note}

### Import your existing credentials into {{site.data.keyword.secrets-manager_full_notm}}
{: #ssl_import}

{{site.data.keyword.ibmcf_notm}} uses customer owned {{site.data.keyword.secrets-manager_full_notm}} to manage [SSL certificates.](/docs/secrets-manager?topic=secrets-manager-certificates) permitting customers to have better control of their secrets.  If you are using custom domains,{{site.data.keyword.secrets-manager_full_notm}}  will be used as storage for your SSL certificates and you will have control of certificates access via IAM service authorizations.
We suggest you, to store your custom domains TLS certificates in a dedicated secrets group because will give increased flexibility when configuring [service to service authorization.](/docs/account?topic=account-serviceauth)

Before configuring {{site.data.keyword.ibmcf_notm}} to use {{site.data.keyword.secrets-manager_full_notm}}, you need to [import your existing certificates into {{site.data.keyword.secrets-manager_full_notm}}.](/docs/secrets-manager?topic=secrets-manager-certificates#import-certificates)

### Authorizing {{site.data.keyword.ibmcf_notm}} to operate on imported certificates
{: #ssl_cert_auth}

Before you can map your SSL certificate to a custom domain, you must authorize {{site.data.keyword.ibmcf_notm}} to use certificates [in {{site.data.keyword.secrets-manager_full_notm}}.](/docs/secrets-manager?topic=secrets-manager-certificates#import-certificates)

1. [Log in the IBM Cloud.](https://cloud.ibm.com/){: external}

2. Click **Manage** > **Access(IAM)** > **Authorizations**.

3. Click **Create**.

4. For *Source account* select *This account*.

5. For *Source service* select *Cloud Foundry for Custom Domain* and leave *How do you want to scope the access?* as *All resources*.

6. For *Target service* select *Secrets Manager*.

7. Select *Resource based on selected attributes*.

8. Select *Resource Type* and set string equals to `secret-group`.

9. Select *Resource* and set string equals to the the group ID found in the {{site.data.keyword.secrets-manager_full_notm}} instance, **Secret Groups** section.

10. For secret access, select `SecretsReader`.

11. Click **Authorize**.



### Mapping the SSL certificate to a custom domain
{: #ssl_cert_custom_domain}

After authorizing {{site.data.keyword.ibmcf_notm}} to operate on imported certificates you can map your SSL certificate to a custom domain.

1. [Log in the IBM Cloud.](https://cloud.ibm.com/){: external}

2. Click **Manage** > **Account** > **Cloud Foundry Orgs**.

3. Open your Org and switch to the **Domains** tab.

4. Next to the name of your custom domain, click *Map to a certificate*.

5. Copy the [CRN from {{site.data.keyword.secrets-manager_full_notm}}](/docs/secrets-manager?topic=secrets-manager-certificates) for your SSL certificate into the text field.

You can also map your SSL certificate using the CLI::

```text
ibmcloud account domain-cert-map YOUR_CUSTOM_DOMAIN SSL_CERT_CRN -o YOUR_ORG_GUID
```
{: pre}


### Unmap an SSL certificate from a Custom domain
{: #ssl_cert_unamp}

If your want to have a Cloud Foundry custom domain to not use anymore a mapped SSL certificate, you can unmap it:

1. Click the *More actions* icon and click **Unmap SSL certificate**.

2. Click **Confirm**.

You can also determine the SSL certificates in use  by running the [following command:](/docs/data-virtualization?topic=cli-ibmcloud_commands_account#ibmcloud_account_domain_cert)

```text
ibmcloud account domain-cert YOUR_CUSTOM_DOMAIN
```
{: pre}

In addition to IBM Cloud console you may also uses latest version  IBM command line to perform unmap of SSL certificate

```text
ibmcloud account domain-cert-unmap YOUR_CUSTOM_DOMAIN
```

## Other Actions 

### Removing existing SSL certificate from Datapower 
{: #ssl_cert_datapower_rm}

If your SSL certificate has already been uploaded to Cloud Foundry custom domain and you want to remove it w/o performing migration to Secret manager,
use IBM command line to perform removal of SSL certificate via command line using the following command (this will permit to remove certificate from Datapower): 

```text
ibmcloud account domain-cert-remove YOUR_CUSTOM_DOMAIN
```
 
You can  determine the SSL certificates uploaded by running the [following command:](/docs/data-virtualization?topic=cli-ibmcloud_commands_account#ibmcloud_account_domain_cert)

```text
ibmcloud account domain-cert YOUR_CUSTOM_DOMAIN
```
{: pre}


### Upload  SSL certificate into Datapower 
{: #ssl_cert_datapower_domain-cert-add}

If you have a urgent need to refresh your SSL certificate  but you are not ready to migrate to Secret Manager, you can uploaded new cert for custom domain with the same procedure you were using in the past.

Use IBM command line to perform removal of older SSL certificate (this will remove certificate from Datapower) :

```text
ibmcloud account domain-cert-remove YOUR_CUSTOM_DOMAIN
```

and then import the new version of certificate  via command (this will import new version of  certificate into Datapower): 


```text
ibmcloud account domain-cert-add  YOUR_CUSTOM_DOMAIN 
```

You can  determine the SSL certificates uploaded by running the [following command:](/docs/data-virtualization?topic=cli-ibmcloud_commands_account#ibmcloud_account_domain_cert)

```text
ibmcloud account domain-cert YOUR_CUSTOM_DOMAIN
```
{: pre}

This is an emergency procedure, you will still be required to migrate your certificate to Secret Manager in the required timeline.
{: note}



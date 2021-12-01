---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Updating your domain
{: #update-domain}

Domains provide the URL route that is allocated to your organization in {{site.data.keyword.cloud}}. For Cloud Foundry apps, you can migrate your domain from `mybluemix.net` to `appdomain.cloud` by using either the {{site.data.keyword.cloud_notm}} console or the command-line interface.
{: shortdesc}

The default shared domain is `mybluemix.net`, but `appdomain.cloud` is another domain option that you can use.
{: tip}

## Updating domains from the {{site.data.keyword.cloud_notm}} console
{: #update-domain-console}

Complete these steps to update the domain for your Cloud Foundry org by using the console:

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg), and select **Resource List**.
2. On the **Resource List** page, click **Cloud Foundry Apps**.
3. Click the app that you want to change the domain for. The app's **Overview** page is displayed.
4. Select the **Routes** menu, notice the current domain, such as `<myapp.mybluemix.net>`, and click **Edit routes**.
5. Select the list of domains, and then click the domain that you want to use, such as `us-south.cf.appdomain.cloud`.
6. Confirm your updates by clicking **Save**.
7. Confirm that you want to replace the old domain, and click **Remove**.
8. To verify that the new route is working, click **Visit App URL**.

## Updating domains from the {{site.data.keyword.cloud_notm}} command-line interface
{: #update-domain-cli}

1. Connect to your targeted Cloud Foundry API endpoint by typing the following command:

    ```text
    ibmcloud target --cf-api <CF_ENDPOINT>
    ```
    {: pre}

    **Cloud Foundry API endpoints:**
    * US-SOUTH - `api.us-south.cf.cloud.ibm.com`
    * US-EAST - `api.us-east.cf.cloud.ibm.com`
    * EU-DE - `api.eu-de.cf.cloud.ibm.com`
    * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
    * AU-SYD - `api.au-syd.cf.cloud.ibm.com`

2. Add the route with the new domain to an app by typing the following command:
   
    ```text
    ibmcloud app route-map <APPNAME> <DOMAIN> -n <HOSTNAME>
    ```
    {: pre}



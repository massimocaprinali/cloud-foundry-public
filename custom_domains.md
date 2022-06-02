---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Adding and using a custom domain
{: #custom-domains}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

Domains provide the URL route that is allocated to your organization in {{site.data.keyword.cloud}}. Custom domains direct requests for your apps to a URL that you own. A custom domain can be a shared domain, a shared subdomain, or a shared domain and host. Unless a custom domain is specified, {{site.data.keyword.cloud_notm}} uses a default shared domain in the route to your app. You can create and use a custom domain by using either the {{site.data.keyword.cloud_notm}} console or the command-line interface.
{: shortdesc}

The default shared domain is `mybluemix.net`, but `appdomain.cloud` is another domain option that you can use. For more information about migrating to `appdomain.cloud`, see [Updating your domain](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).
{: tip}

To use a custom domain, you must register the custom domain on a public DNS server, and then configure the custom domain in {{site.data.keyword.cloud_notm}}. Next, you must map the custom domain to the {{site.data.keyword.cloud_notm}} system domain on the public DNS server. After your custom domain is mapped to the system domain, requests for your custom domain are routed to your app in {{site.data.keyword.cloud_notm}}.

## Adding a custom domain from the {{site.data.keyword.cloud_notm}} console
{: #custom-domain-console}

Complete these steps to add a custom domain for your org by using the console:

1. Go to **Manage > Account**, and select **Cloud Foundry orgs**.

2. Click the name of the org for which you're creating a custom domain.

3. Click the **Domains** tab to view a list of available domains.

4. Click **Add a domain**, enter your domain name, and select the region.

5. Confirm your updates, and click **Add**.

## Adding the route with the custom domain to an app

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg), and select **Resource List**.

2. On the **Resource List** page, click **Cloud Foundry Apps**.

3. Click the app that you want to add the route to. The app's **Overview** page is displayed.

4. Select the **Routes** menu, and select **Edit routes**.

5. Click **Add route**, and specify the route that you want to use for the app.

6. Confirm your updates by clicking **Save**.

As an example, you can use `*.mycompany.com` to associate the route `www.mybluemix.net` to your app. You can also use `example.mycompany.com` to associate the route `www.example.bluemix.net` to your app.
{: tip}

## Adding a custom domain from the {{site.data.keyword.cloud_notm}} command-line interface
{: #custom-domain-cli}

1. For Cloud Foundry apps, connect to your targeted Cloud Foundry API endpoint by typing the following command:

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

2. Create a custom domain for your organization by typing the following command:
   
    ```text
    ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
    ```
    {: pre}

3. Add the route with the custom domain to an app.

    For Cloud Foundry apps, run the following command:
   
    ```text
    ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
    ```
    {: pre}

## Mapping the custom domain to the system domain
{: #mapcustomdomain}

After you configure the custom domain in {{site.data.keyword.cloud_notm}}, map the custom domain to the {{site.data.keyword.cloud_notm}} system domain on your registered DNS server:

1. Set up a 'CNAME' record for the custom domain name on your DNS server. Steps for setting up the CNAME record vary depending on your DNS provider. For example, if you use GoDaddy, you follow the [Domains Help](https://www.godaddy.com/help/add-a-cname-record-19236){: external} guidance from GoDaddy.

2. Map the custom domain name to the secure endpoint for the {{site.data.keyword.cloud_notm}} region where your app is running. Use the following region endpoints to provide the URL route that is allocated to your organization in {{site.data.keyword.cloud_notm}}. For example, point your CNAME to `custom-domain.us-east.cf.cloud.ibm.com.`

    **Cloud Foundry endpoints:**
   
    * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
    * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
    * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
    * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
    * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## Accessing your app
{: #access-app}

In a browser, enter the following URL to access your app, where `hostname` is your host name, and `mydomain` is your domain name:

```text
http://hostname.mydomain
```
{: codeblock}

## Removing an orphaned route
{: #remove-orphaned-route}

To remove an orphaned route, run the following command:

```text
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: pre}

In that example, `MY_DOMAIN` is the name of your domain, and `MY_HOSTNAME` is the host name of the route for your app. For more information about the `ibmcloud app route-delete` command, enter the command `ibmcloud app route-delete -h`.



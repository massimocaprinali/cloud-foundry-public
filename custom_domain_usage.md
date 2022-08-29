---

copyright:
  years: 2015, 2022
lastupdated: "2022-08-29"

keywords: cloud foundry, custom domain

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}

# Custom Domain update required for Cloud Foundry Applications
{: #custom_domain_usage}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. 
{: deprecated}

In addition to the [IBM Cloud Foundry deprecation announcement](https://ibm.biz/ibmcf-announce), all IBM Cloud Foundry users that have and are using a custom domain forward pointing to an {{site.data.keyword.ibmcf_notm}} application will need to upload a new application SSL certificate before the deadline of 29 September 2022.
{: shortdesc}

## Custom domain forwarding change needed for applicable IBM Cloud Foundry applications
{: #custom_domain_change_needed}

Security changes require IBM Cloud Foundry to store SSL certificates using a different storage technology. This means that any IBM Cloud Foundry application that is being forwarded to as a custom domain, and has an SSL certificate uploaded to properly terminate that forward, needs to upload that SSL certificate again.

The upload process will put it in the proper place and the forward will keep working like it does today.

Some notes about this process
* You do not need to regenerate a new SSL certificate if it is still valid, you just need to upload it again
* Be sure to upload it into the account that hosts your IBM Cloud Foundry application - multiple people can have access to an IBM Cloud account for deployment of applications, so be sure to use the one that holds that certificate currently.
* If you uploaded certificates for multiple specific IBM Cloud regions, you need to upload them to the same regions again
* Some users in their DNS forwarding to these custom domains are using only A records, or specific IP addresses, and not CNAME records, like "custom-domain.us-south.cf.cloud.ibm.com" like instructions explain. If you use A record IP addresses ONLY in your DNS forwarding, then this change may cause your application to not forward, even if you upload the SSL certificates.


## Cloud Foundry domains
{: #custom_domain_domaininfo}

You can examine which domains you currently have set up on your IBM Cloud account that might be served by IBM Cloud Foundry applications, using one of the methods below.

### UI method
{: #cf_domain_ui}

1. Log into [cloud.ibm.com](cloud.ibm.com){: external}

2. Go to [https://cloud.ibm.com/account/cloud-foundry](https://cloud.ibm.com/account/cloud-foundry){: external}

3. For each isted org:

	a. Click on the ![Actions icon](../../icons/action-menu-icon.svg "Actions") on the right side, and select "Domains". That will show you the custom domains you have set up for each region pointing to that org.

### CLI method
{: #cf_domain_cli}

1. Login to the ibmcloud using `ibmcloud login`

2. For each region pointed to by a custom domains:

	a. Target an IBM Cloud region using the  `ibmcloud target --cf-api api.<region>.cf.cloud.ibm.com` and reference [Region list](/docs/cloud-foundry-public?topic=cloud-foundry-public-endpoints) if needed.

	b. After targetting a region, run the command `ibmcloud cf orgs`.

	c. For each org that is listed, target the org using the `ibmcloud target -o <orgname>` command.

	d. Run the command `cf domains | grep -v shared`.  This command returns all of your "private" or "owned" domains for this region and org, and are the ones you might be using for custom domain forwarding.


### CLI method #2
{: #cf_domain_cli2}

If you want to check that you've examined all your Cloud Foundry Orgs in all the IBM Cloud regions, you can run this command after proper IBM Cloud authentication.

`ibmcloud resource search 'type:cf-organization'`

This will list all the Orgs in all the regions you have them specified, and then you can check that you've iterated over each of them.

You can also try this set of commands (this will require installing [this package](https://stedolan.github.io/jq){: external} or something similar) to get a list of Orgs across all domains in a single list.

```text
export jsonFile="orgs.json"
ibmcloud resource search 'type:cf-organization' --output json > $jsonFile
cat $jsonFile | jq '.items[] | {family, type, region, name} | join(" ")' | sed 's/\"//g'
```
{: pre}



### Next Steps
{: #cf_comain_next}

For each custom domain you discovered that you wish to continue using with an IBM Cloud Foundry application, upload the SSL certificates using the instructions below.



## Security Storage
{: #custom_domain_usage_security}

The new method for securely storing SSL certificates for {{site.data.keyword.ibmcf_notm}} applications uses the IBM Cloud [Secrets Manager](https://www.ibm.com/cloud/secrets-manager){: external}. All users who want to continue directing their custom domain to their {{site.data.keyword.ibmcf_notm}} application need to create a Secrets Manager service instance, authorize its use, and upload the required SSL certificates. This is a one time change and can then be used for all the custom domains you wish to forward to {{site.data.keyword.ibmcf_notm}} applications.

There are different levels of [Secrets Manager plans](https://cloud.ibm.com/catalog/services/secrets-manager){: external} - Trial and Standard. You should pick the plan most appropriate for your needs.

### Standard Plan
{: #cd_standard}

- $299.00 / month
- Can store unlimited secrets
- No expiration timeframe

If you intend to use Secrets Manager in other capacities and with other IBM Cloud services, in addition to the need for {{site.data.keyword.ibmcf_notm}} application certificates, then you should choose this plan for continued use.


### Trial Plan 
{: #cd_trail}

- Free to use
- Expires after 30 days

If you do not intend to use Secrets Manager after changing your {{site.data.keyword.ibmcf_notm}} custom domain certificates, select this plan. You will create the Secrets Manager service and follow the normal instructions uploading the certificates you need.  {{site.data.keyword.ibmcf_notm}} will then retrieve the certificates. After {{site.data.keyword.ibmcf_notm}} retrieves the certificates from Secrets Manager, you no longer need the Secrets Manager instance, unless you need to update your certificates in the future. If you do need to update your custom domain SSL certificate, repeat the procedure with the Trial Secrets Manager instance plan and repeat the custom domain upload procedure. If you don't need to update your certificate again, simply let the Secrets Manager instance Trial plan elapse.


## Timeline
{: #cd_timeline}

All users that intend to have their custom domain continue to be served by their {{site.data.keyword.ibmcf_notm}} application need to upload SSL certificates. If the SSL certificate is not uploaded, the custom domain routing to that {{site.data.keyword.ibmcf_notm}} application will no longer work.


### Announcement - 29 August 2022
{: #cd_announce}

The announcement is posted and emails sent to all customers with custom domains registered with {{site.data.keyword.ibmcf_notm}}.

### Deadline - Depends on region
{: #cd_deadline}

There will be a rolling deadline for different IBM Cloud regions to make this change - the deadlines are listed here. After these dates, previous custom domain routing will stop working for the custom domains in those regions. Only custom domains which have followed this procedure will continue working. If you have a custom domain in multiple regions, we recommend you update them all at the same time for the earliest deadline listed. Although notifications and emails have stated a deadline of 29 September, 2022 for all regions, there is extra time for some regions.

- Frankfurt (eu-de) - 29 September 2022
- Sydney (au-sy) - 14 October 2022
- Washington (us-east) - 14 October 2022
- London (eu-gb) - 14 November 2022
- Dallas (us-south) - 14 November 2022


## Instructions
{: #cd_instructions}

If you already have a valid SSL certificate for your custom domain, you need to upload it into a Secret Manager instance an authorise Cloud Foundry service to access it as per instructions in [Importing SSL certificates into IBM Cloud Secrets Manager](/docs/cloud-foundry-public?topic=cloud-foundry-public-ssl_csr#ssl_certificate_secrets_manager).

If you don't have a valid SSL certificate for your customs domains, you need to order one via a Certificate Authority before you can proceed with operations. Use the instructions in [Creating certificate signing requests](/docs/cloud-foundry-public?topic=cloud-foundry-public-ssl_csr) to order it. Upon you will have the certificate, please follow instruction reported above in this paragraph.

Upload your application's custom domain SSL certificate before the deadline. 

When done, ensure your custom domain URL redirect is working and your required steps are completed.

SSL certificate import is a region specific operation. If you are using the same custom domain and SSL cert across multiple regions, you need to update certificate for each one.


## FAQ
{: #custom_domain_usage_faq}

How does this relate to the IBM Cloud Foundry Deprecation announcement? I still have until June 1, 2023 to run my IBM Cloud Foundry applications, right?
:   Yes, this step is separate from the IBM Cloud Foundry Deprecation announcement. This custom domain SSL certificate upload step needs to be done by the [deadline as listed above.](#cd_deadline) The IBM Cloud Foundry End-of-Support date is still 1 June 2023, as described in this [IBM Cloud Foundry deprecation announcement](https://ibm.biz/ibmcf-announce).

Does each application that has a custom domain forward SSL certificate need to be updated, or just one for the IBM Cloud account in which the application is running?
:   This is per domain, but you can have several applications associated to a single domain. For example, if you have applications running as app1.example.com, app2.example.com and app3.example.com then you only need to setup an SSL certificated for “example.com”.

Do I need to regenerate a new SSL certificate?
:   No, not if you have the existing SSL certificate you uploaded previously, and it has not expired. You can simply upload that still valid SSL certificate like you had before.

I'm a developer that is pushing Cloud Foundry applications to another IBM Cloud account that I have access to and belongs to my development organization. Where is this SSL certificate supposed to be uploaded and configured? Who is able to upload it?
:   The SSL certificate belongs to the account where the Cloud Foundry applications are deployed. Make sure that the account that has those applications is connected to these SSL certificates. If you were to do all of this in your own IBM Cloud account, this won't work properly, the account owner would need to run these steps for you.

If I have more than one IBM Cloud Foundry application with a custom domain forward, how do I handle this case with these steps?
:   Create a single Secrets Manager instance and upload all of your SSL certificates following the given instructions. This will properly apply all the certificates into the Secrets Manager and the custom domain forwarding software.

I have my applications servicing these forwarded domains in multiple IBM Cloud regions. Do I need to upload the certificate again for each region?
:   Yes, you need to repeat the steps for SLL certificate upload for each region like was previous done. For example, if you have a domain "myapp.mybluemix.net" as the custom domain and they are being hosted in both the eu-gb region and the eu-de region, you would need to make sure and upload  SSL certificates for "https://myapp.eu-gb.mybluemix.net" and "https://myapp.eu-de.mybluemix.net" as well as "https://myapp.mybluemix.net".

How do I check your warning about DNS "A records" versus "CNAME records".
:    When you run a common command to look up public DNS registry records, like "dig mydomain.com" or "dig app.mydomain.com", you get back the DNS record which looks similar to this

:    - app.mydomain.com.	300	IN	CNAME	custom-domain.us-south.cf.cloud.ibm.com.
:    - custom-domain.us-south.cf.cloud.ibm.com. 33 IN A 169.62.254.80
:    - custom-domain.us-south.cf.cloud.ibm.com. 33 IN A 169.46.89.151
:    - custom-domain.us-south.cf.cloud.ibm.com. 33 IN A 169.47.124.23

:    This is a correctly set up DNS entry, using the CNAME (custom-domain.us-south.cf.cloud.ibm.com) and A records auto retrieved (169.62.254.80, 169.46.89.151, 169.47.124.23). If however you get back something similar to this

:    app.mydomain.com.	3600	IN	A	169.62.254.80

:    then you only have a hard-coded "A record", and no "CNAME record". This means that when we change the IP addresses that our CNAMES point to, your DNS record forwarding will point to an incorrect IP address and fail. You need to ensure that using the instructions that you add "CNAME records" to your DNS registry, to ensure that your application receives the proper forwarding information. Without fixing this potential problem, your domain will stop receiving traffic, even if you complete the SSL certificate upload steps. So this is a second general step to correct an incorrectly designated DNS record forward.

What happens if I don't update this custom domain redirect by the deadline?
:   Your custom domain URL redirect will stop working on the deadline listed.

If my custom domain URL redirect stopped working because the deadline has passed, how can I fix it?
:   Follow the listed instructions, it will begin working again after completing the steps.


## Customer Support
{: #custom_domain_usage_customersupport}

These materials and resources should help you through your IBM Cloud Foundry migration. If you have questions, or need help, contact [IBM Cloud® Customer Support](https://www.ibm.com/cloud/support){: external} for additional information and assistance.




---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-31"

keywords: cloud foundry

subcollection: cloud-foundry-public

---

{{site.data.keyword.attribute-definition-list}}

# Securing your data in {{site.data.keyword.ibmcf_notm}}
{: #mng-data}

{{site.data.keyword.ibmcf_full}} is deprecated. As of 30 November 2022 new {{site.data.keyword.ibmcf_full}} applications cannot be created and only existing users will be able to deploy applications. End-of-support happens on 1 June 2023. Any instances that still exist on 1 June 2023 will be deleted. For more information, see [the deprecation details](/docs/cloud-foundry-public?topic=cloud-foundry-public-deprecation).
{: deprecated}

To ensure that you can securely manage your data when you use {{site.data.keyword.ibmcf_full}}, it is important to know exactly what data is stored and encrypted and how you can delete any stored personal data. 
{: shortdesc}

## How your data is stored and encrypted in {{site.data.keyword.ibmcf_notm}}
{: #data-storage}

{{site.data.keyword.ibmcf_notm}} does not store customer or application user data.  Data related to {{site.data.keyword.ibmcf_notm}} apps is stored encrypted in {{site.data.keyword.cloud}} object storage using a key defined by {{site.data.keyword.ibmcf_notm}}.

## Deleting your data in {{site.data.keyword.ibmcf_notm}}
{: #data-delete}

When an app is deleted from {{site.data.keyword.ibmcf_notm}} the app and any associated data stored in {{site.data.keyword.ibmcf_notm}} is deleted.  All app data should be deleted when the app is deleted unless there is an error during the app deletion.  In the case of an error any remaining data will be cleaned up by Cloud Foundry during [automatic cleanup](https://docs.cloudfoundry.org/concepts/architecture/cloud-controller.html#automatic-clean){: external}.

## Restoring deleted data for {{site.data.keyword.ibmcf_notm}}
{: #data-restore}

An app that was deleted from {{site.data.keyword.ibmcf_notm}} cannot be restored.  If you need to restore a deleted app, redeploy the app.


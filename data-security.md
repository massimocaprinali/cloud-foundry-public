---

copyright:
  years: 2015, 2021
lastupdated: "2021-11-05"

keywords: cloud foundry

subcollection: cloud-foundry-public

---

{{site.data.keyword.attribute-definition-list}}

# Securing your data in {{site.data.keyword.ibmcf_notm}}
{: #mng-data}

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


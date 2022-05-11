---

copyright:
  years: 2015, 2022
lastupdated: "2022-05-11"

keywords: cloud foundry

subcollection: cloud-foundry-public



---


{{site.data.keyword.attribute-definition-list}}


# Managing connections
{: #connect_app}

You can connect a service to an existing or new {{site.data.keyword.cloud}} app from the **Connections** tab on your service dashboard. Connecting a Cloud Foundry service to a Cloud Foundry app creates a binding between them, and you can unbind, add additional connections, or delete connections from the **Connections** tab.
{: shortdesc}

However, when you connect a service instance that is managed by {{site.data.keyword.iamlong}} (IAM) to a Cloud Foundry app, an alias of the service managed by IAM is automatically created in the corresponding Cloud Foundry space with the binding information that you specified. This alias is represented as a Cloud Foundry service instance of your IAM-managed service.


## What is an alias?
{: #what_is_alias}

An alias is a connection between your IAM-managed service within a resource group and a Cloud Foundry app within an org or a space. In the {{site.data.keyword.cloud_notm}} console, the connection (alias) is represented as a Cloud Foundry service instance. You can manage your alias by modifying the service instance that represents your connection.

Aliases are like symlinks that hold references to remote resources and enable interoperability and reuse of an instance across the platform. For example, you can create an instance of a service in a resource group and then reuse it from any available Cloud Foundry region by creating an alias in an org or space in those regions.

The following rules apply to aliases:

* There is no extra charge for an alias, but each alias counts against your quota in your Cloud Foundry organization.

* You can create only one alias per Cloud Foundry space in the {{site.data.keyword.cloud_notm}} console. However, more than one alias per space can be created using the {{site.data.keyword.cloud_notm}} CLI. For more information, see [Working with resource groups and resources](/docs/cli?topic=cli-ibmcloud_commands_resource).

* You can create multiple connections between your IAM-managed service and any Cloud Foundry app in any space, organization, and region in the same account if you have permission.

* Multiple connections made in the same space to different Cloud Foundry apps from an IAM-managed service instance will use the same alias.

* Un-binding an IAM-managed service instance *will not* delete the Cloud Foundry service instance that represents the alias.

* Deleting the Cloud Foundry app that your IAM-managed service instance is connected to *will not* delete the Cloud Foundry instance that represents the alias.

* Deleting an IAM-managed service instance *will* delete the Cloud Foundry service instance that represents the alias.

## Creating a connection (alias) between an IAM-managed service and a Cloud Foundry app
{: #creating_alias}

To connect your IAM-managed service instance to a Cloud Foundry app:

1. Go to your dashboard.

2. Click the name of your app to open the app details view.

3. Click **Connect existing** and choose from your existing Cloud Foundry app. Or click **Create Connection** to create a Cloud Foundry app to connect to.

4. Specify the **Access Role for Connection**. This value sets the IAM service access role. For more information, see [IAM access](/docs/account?topic=account-userroles#service_access_roles).

5. Optionally, you can provide a **Service ID for Connection** by either allowing IAM to generate a unique value for you, or by providing an existing service ID. For more information, see [Creating and working with service IDs](/docs/account?topic=account-serviceids).

6. Click **Create**.

## Viewing an alias

After you create a connection between an IAM-managed service and a Cloud Foundry app, the alias is displayed on the **Connections** tab of the connected Cloud Foundry app. Additionally, the alias is displayed as a running Cloud Foundry service instance on your dashboard, and contains a **Connections** tab only when you open it.

1. Go to your dashboard.

2. From the **Cloud Foundry Services** table, click the name of the service instance to open the service details view. If it only has a **Connections** tab, it is an alias.

## Deleting an alias

The easiest way to delete the alias is to delete the IAM-managed service instance. However, you can maintain your IAM-managed service instance and instead delete the alias directly.

1. Go to your dashboard.

2. From the  **Cloud Foundry Services** table, click the name of the service instance to open the service details view. If it only has a **Connections** tab, it is an alias.

3. Delete the instance.

## Creating a connection between multiple Cloud Foundry services
{: #cf}

For more details about binding a Cloud Foundry service to another Cloud Foundry service, see [Using services in another region](/docs/account?topic=account-cross_region_service).



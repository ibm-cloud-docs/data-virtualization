---

copyright:
  years: 2021, 2022
lastupdated: "2021-06-08"

subcollection: data-virtualization

keywords: deprovision data-virtualization, deprovisioning parameters, delete

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external .external}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important .important}


# Deleting your deployment and removing your data
{: #deprovisioning}

{{site.data.keyword.dv_short}} instances are soft-deleted in production whenever you delete or deprovision the instance in {{site.data.keyword.cloud_notm}}. 

The deployment stays in the "soft-delete" state for up to 3 days before it's fully deleted {{site.data.keyword.cloud_notm}}.  If your instance has not yet been fully deleted, you can re-enable the existing soft-deleted instance.

## Deleting your deployment in the user interface 
To delete your deployment instance from the Resource list section dashboard of the IBM Cloud dashboard, select your deployment. Next, using the menu icon, choose `Delete` from the dropdown list. 

## Deleting your deployment by using the CLI
You can delete your existing {{site.data.keyword.dv_short}} instance through the CLI with the [`ibmcloud resource service-instance-delete`](https://cloud.ibm.com/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_service_instance_delete) command:
```
ibmcloud resource service-instance-delete my-service-instance
```
{: .pre}

Using the `ibmcloud resource reclamation-delete` command deletes a reclaimed resource so that the resource can no longer be restored.
{: .note}

## Cryptoshredding keys

{{site.data.keyword.keymanagementserviceshort}} provides for a [force delete](/docs/key-protect?topic=key-protect-delete-keys) of a key that is in use by {{site.data.keyword.cloud}} services, including your {{site.data.keyword.databases-for}} deployments. This action is called cryptoshredding. 

Cryptoshredding is a destructive action. When the key is deleted, your data is unrecoverable, even from a soft-delete state.
{: .important}

## Removing backups

Backups cannot be manually deleted. However, if you delete your deployment, its backups are deleted automatically within 30 days. 

## Reenabling from a soft-delete
{: #reclamation}

To discover available soft-deleted instances, use the {{site.data.keyword.cloud_notm}} CLI [`ibmcloud resource reclamations`](https://cloud.ibm.com/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamations) command.

You can then "undelete", recover, or reclaim an available soft-deleted instance by using the {{site.data.keyword.cloud_notm}} CLI [`ibmcloud resource reclamation-restore`](https://cloud.ibm.com/docs/cli?topic=cli-ibmcloud_commands_resource#ibmcloud_resource_reclamation_restore) command.

```
ibmcloud resource reclamation-restore resource_ID
```

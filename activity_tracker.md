---

copyright:
  years: 2014, 2021
lastupdated: "2021-04-14"

keywords: 

subcollection: data-virtualization

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}

# Activity Tracker integration
{: #activity-tracker}

Data Virtualization deployments are integrated with Activity Tracker events in [IBM Cloud Activity Tracker with LogDNA](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-getting-started), so you can view service-level events.

Currently, Activity Tracker with Log Analysis integration is available for Data Virtualization deployments in the regions according to the following table: 

| Deployment region | Activity Tracker region |
|----------|-----------|
| Dallas | us-south |
| Washington | us-east |
| Frankfurt | eu-de |
| London | eu-gb |
| Sydney | au-syd |
| Tokyo | jp-tok |
{: caption="Table 1. Activity Tracker regions" caption-side="top"}


## Activity Tracker through Log Analysis
{: #at_logdna}

After you provision the service, events are automatically forwarded from all of your Data Virtualization deployments in the same region.

The service can be provisioned from its [catalog page](https://cloud.ibm.com/catalog/services/logdna?callback=%2Fobserve%2Flogging%2Fcreate){: external} or from an existing [Observability Dashboard](https://cloud.ibm.com/observe/activitytracker){: external}.

The Activity Tracker with Log Analysis service has a Lite plan that is free to use, but it only offers streaming events. To take advantage of the tagging, export, retention, and other features, you need to use one of the [paid plans](/docs/log-analysis?topic=log-analysis-service_plans)<!-- [paid plans](/docs/Log-Analysis-with-LogDNA?topic=LogDNA-about#overview_pricing_plans) -->.

### Using the Log Analysis Activity Tracker
{: #at_use}

You can access Activity Tracker with Log Analysis through the **Observability** tab of your deployment's **Manage** page. The **Manage Activity Tracker** button links to the main list of all Activity Tracker instances in your {{site.data.keyword.cloud_notm}} account. Select the instance where you set your database logs to be forwarded. Click **View Activity Tracker** to view the events.

After the event activity is forwarded to the service, each event can be expanded to a detailed view by clicking the arrow to the left of the time stamp.

The Log Analysis service offers [searching](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-view_logs#view_logs_step6), [filtering](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-view_logs#view_logs_step5), and [export](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-export#export) of events so you can customize retention for your use case. You can also use it to configure [alerts](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-alerts).

## Event fields
{: #at_ev_fields}

A description of the common fields for an Activity Tracker event is on the [Event fields](/docs/Activity-Tracker-with-LogDNA?topic=Activity-Tracker-with-LogDNA-event) page.

## List of events
{: #at_list_ev}

The following table lists the events that get sent to Activity Tracker from Data Virtualization deployments:

| Action | Description |
|-------|-------|
| `<service_id>.user.create`| A user was created. A "-failure" flag is included in the message if the attempt to create a user failed. |
| `<service_id>.backup.create`| A backup was created. If the attempted restore failed, a "-failure" flag is included in the message. |
| `<service_id>.user.delete`| A user was deleted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.user.modify`| A user was modified. A "-failure" flag is included in the message if the attempt to create a user failed. |
| `<service_id>.resources.scale`| A scaling operation was performed. If the scaling operation failed, a "-failure" flag is included in the message. |
| `<service_id>.whitelisted-ips-list.update`| The allowlist was modified. A "-failure" flag is included in the message if the attempt to modify the allowlist failed. |
{: caption="Table 2. List of events and event descriptions" caption-side="top"}

The `<service_id>` field indicates the type of Cloud databases deployment. For example, `data-virtualization` or `messages-for-rabbitmq`.


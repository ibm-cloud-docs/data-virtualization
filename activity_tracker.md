---

copyright:
  years: 2021, 2022
lastupdated: "2022-02-01"

keywords: 

subcollection: data-virtualization

---

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

{{site.data.keyword.dv_short}} deployments are integrated with Activity Tracker events in [IBM Cloud Activity Tracker with LogDNA](/docs/Log-Analysis-with-LogDNA?topic=Log-Analysis-with-LogDNA-getting-started), so you can view service-level events.

Currently, Activity Tracker with Log Analysis integration is available for {{site.data.keyword.dv_short}} deployments in the regions according to the following table: 

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

After you provision the service, events are automatically forwarded from all of your {{site.data.keyword.dv_short}} deployments in the same region.

The service can be provisioned from its [catalog page](https://cloud.ibm.com/catalog/services/logdna?callback=%2Fobserve%2Flogging%2Fcreate){: external} or from an existing [Observability Dashboard](https://cloud.ibm.com/observe/activitytracker){: external}.

The Activity Tracker with Log Analysis service has a Lite plan that is free to use, but it only offers streaming events. To take advantage of the tagging, export, retention, and other features, you need to use one of the [paid plans](/docs/log-analysis?topic=log-analysis-service_plans).

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

The following table lists the events that get sent to Activity Tracker from {{site.data.keyword.dv_short}} deployments:

| Action                           | Procedure                        | Description                        |
|----------------------------------|----------------------------------|------------------------------------|
| data-virtualization.constellation.create | DEFINE_CONSTELLATION | Define a Constellation |
| data-virtualization.data-source-connection.create | SETRDBCX | Define a new data source connection |
| data-virtualization.data-source-connection.delete | REMOVERDBCX | Remove a data source connection  |
| data-virtualization.jdbc-url.get| BUILDURLANDDRIVER | Generate the JDBC URL and JDBC Driver string |
| data-virtualization.connector-config-hash.create| GENERATECONFIGHASH | Generate the configuration |
| data-virtualization.remote-gaian-node.update| UPDATEREMOTECONNECTOR | Upgrade the remote connectors |
| data-virtualization.virtualized-table.create| VIRTUALIZETABLE | Virtualize a table  |
| data-virtualization.virtualized-file.create| VIRTUALIZEFILE | Virtualize a table  from a file |
| data-virtualization.table.delete| DROPTABLE | Remove a table |
| data-virtualization.config-data.restore| RESTORECONFIG | Restore config data  |
| data-virtualization.RCAC-on-catalog-tables.update| TOGGLE_RCAC_ON_CATALOG_TABLES | Enable/disable row access control on Db2 catalog tables  |
| data-virtualization.config-properties10.update| SETCONFIGPROPERTIES | Set up to 10 configuration properties  |
| data-virtualization.config-propertiy.update| SETCONFIGPROPERTY | Set a configuration property  |
| data-virtualization.log-level.update| SETADMINLOGLEVEL | Set the log level  |
| data-virtualization.performance-metrics.get| GETPERFORMANCE | Get the performance metrics |
| data-virtualization.query-stats-cache.backup| ARCHIVEQUERYSTATS |  Archive the content of the DVSYS.QUERYSTATS view |
| data-virtualization.execution-info.get| GETEXECUTIONINFO | Return a String with execution details for a query  |
| data-virtualization.logged-queries.get| GETLOGGEDQUERIES | Get a resultset mapping query IDs to the query text |
| data-virtualization.logs-with-marker.backup| ARCHIVELOGS | Archive the current logs  |
| data-virtualization.ccid.update| UPDATECCID | Update the CCID of all connection |
| data-virtualization.config.update| TOGGLECONFIGAPIS, TOGGLEWKCPOLICYENFORCEMENT,  TOGGLESTRICTFLAG, SETDEFAULTCATALOGGUID | Toggle the key value in the INSTANCE_INFO table  |
| data-virtualization.config.delete| DELETEDEFAULTCATALOGGUID, SETCATALOGPUBLISHSERVICE | Delete the DEFAULT_CATALOG_GUID value or the CATALOG_PUBLISH_SERVICE_ID and CATALOG_PUBLISH_SERVICE_API_KEY values|
| data-virtualization.encrypted-config.update| SETCATALOGPUBLISHSERVICE | Encrypt and set the CATALOG_PUBLISH_SERVICE_ID and CATALOG_PUBLISH_SERVICE_API_KEY values |
| data-virtualization.CIDs-for-virtual-table.list | RETRIEVECIDSFORVIRTUALTABLES | Retrieve the CID information for Virtual Tables |
{: caption="Table 2. List of events and event descriptions" caption-side="top"}

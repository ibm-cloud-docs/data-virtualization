---

copyright:
  years: 2021, 2022
lastupdated: "2021-06-08"

keywords: monitoring for code engine, performance metrics, monitor, metrics, requests, pods, application, attributes, jobrun, panic mode

subcollection: data-virtualization

---

{:DomainName: data-hd-keyref="APPDomain"}
{:DomainName: data-hd-keyref="DomainName"}
{:android: data-hd-operatingsystem="android"}
{:api: .ph data-hd-interface='api'}
{:apikey: data-credential-placeholder='apikey'}
{:app_key: data-hd-keyref="app_key"}
{:app_name: data-hd-keyref="app_name"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:authenticated-content: .authenticated-content}
{:beta: .beta}
{:c#: data-hd-programlang="c#"}
{:cli: .ph data-hd-interface='cli'}
{:codeblock: .codeblock}
{:curl: .ph data-hd-programlang='curl'}
{:deprecated: .deprecated}
{:dotnet-standard: .ph data-hd-programlang='dotnet-standard'}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:fuzzybunny: .ph data-hd-programlang='fuzzybunny'}
{:generic: data-hd-operatingsystem="generic"}
{:generic: data-hd-programlang="generic"}
{:gif: data-image-type='gif'}
{:go: .ph data-hd-programlang='go'}
{:help: data-hd-content-type='help'}
{:hide-dashboard: .hide-dashboard}
{:hide-in-docs: .hide-in-docs}
{:important: .important}
{:ios: data-hd-operatingsystem="ios"}
{:java: .ph data-hd-programlang='java'}
{:java: data-hd-programlang="java"}
{:javascript: .ph data-hd-programlang='javascript'}
{:javascript: data-hd-programlang="javascript"}
{:new_window: target="_blank"}
{:note: .note}
{:objectc: data-hd-programlang="objectc"}
{:org_name: data-hd-keyref="org_name"}
{:php: data-hd-programlang="php"}
{:pre: .pre}
{:preview: .preview}
{:python: .ph data-hd-programlang='python'}
{:python: data-hd-programlang="python"}
{:route: data-hd-keyref="route"}
{:row-headers: .row-headers}
{:ruby: .ph data-hd-programlang='ruby'}
{:ruby: data-hd-programlang="ruby"}
{:runtime: architecture="runtime"}
{:runtimeIcon: .runtimeIcon}
{:runtimeIconList: .runtimeIconList}
{:runtimeLink: .runtimeLink}
{:runtimeTitle: .runtimeTitle}
{:screen: .screen}
{:script: data-hd-video='script'}
{:service: architecture="service"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:service_name: data-hd-keyref="service_name"}
{:shortdesc: .shortdesc}
{:space_name: data-hd-keyref="space_name"}
{:step: data-tutorial-type='step'}
{:subsection: outputclass="subsection"}
{:support: data-reuse='support'}
{:swift: .ph data-hd-programlang='swift'}
{:swift: data-hd-programlang="swift"}
{:table: .aria-labeledby="caption"}
{:term: .term}
{:terraform: .ph data-hd-interface='terraform'}
{:tip: .tip}
{:tooling-url: data-tooling-url-placeholder='tooling-url'}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}
{:tutorial: data-hd-content-type='tutorial'}
{:ui: .ph data-hd-interface='ui'}
{:unity: .ph data-hd-programlang='unity'}
{:url: data-credential-placeholder='url'}
{:user_ID: data-hd-keyref="user_ID"}
{:vbnet: .ph data-hd-programlang='vb.net'}
{:video: .video}


# Monitoring for {{site.data.keyword.dv_short}}
{: #monitor}

Get insight into your {{site.data.keyword.dv_short}} instance. Metrics can help you find bottlenecks or predict possible production problems.

You can use the IBM Cloud® Monitoring service to monitor your {{site.data.keyword.dv_short}} instance. {{site.data.keyword.dv_short}} forwards selected information about your instance to Monitoring so that you can monitor specific metrics such as cpu and memory utilization.

## Set up your {{site.data.keyword.dv_short}} service instance
{: #setup-monitor}

To set up Monitoring for {{site.data.keyword.dv_short}}, you must create a service instance and then enable Platform Metrics in the same region as the {{site.data.keyword.dv_short}} instance  that you want to monitor. If you have deployments in more than one region, you must provision Monitoring and enable platform metrics for each region.

To set up {{site.data.keyword.mon_short}},

1. From the {{site.data.keyword.cloud_notm}} navigation menu, select **Observability**.
2. Select **Monitoring**.
3. Either use an existing {{site.data.keyword.mon_short}} service instance or create a new one.
4. After the instance is ready, enable platform metrics by clicking **Configure platform metrics**.
5. Select a region and then a {{site.data.keyword.mon_short}} instance from that region. If you have deployments in more than one region, you must provision {{site.data.keyword.mon_short}} and enable platform metrics for each region.

## Accessing your {{site.data.keyword.mon_full_notm}} metrics
{: #access-monitor}

To see your {{site.data.keyword.dv_short}} customer metrics dashboards in {{site.data.keyword.mon_short}}:

1. From the {{site.data.keyword.cloud_notm}} navigation menu, select **Observability**.
2. Select **Monitoring**.
3. Select **View {{site.data.keyword.mon_full_notm}}** to open the dashboard.

For more information, see [{{site.data.keyword.mon_short}} Getting started tutorial](/docs/monitoring?topic=monitoring-getting-started).

## Metrics available by Service Plan
{: #metrics-by-plan}

| Metric Name |
|-----------|
| [Average CPU utilization](#ibm_data_virtualization_ep_avg_cpu_util) | 
| [Average Heap memory utilization](#ibm_data_virtualization_ep_avg_heapmem_util) | 
| [CPU utilization](#ibm_data_virtualization_adm_cpu_util) | 
| [Disk IOPS Read Total](#ibm_data_virtualization_ibm_disk_iops_read_total) | 
| [Disk IOPS Write Total](#ibm_data_virtualization_ibm_disk_iops_write_total) | 
| [Disk utilization percent](#ibm_data_virtualization_ibm_disk_io_utilization_percent) | 
| [Heap memory utilization](#ibm_data_virtualization_adm_heapmem_util) | 
| [How long was the disk waiting because of a log being saved](#ibm_data_virtualization_log_disk_wait) | 
| [Maximum CPU utilization](#ibm_data_virtualization_ep_max_cpu_util) | 
| [Maximum Heap memory utilization](#ibm_data_virtualization_ep_max_heapmem_util) | 
| [Minimum CPU utilization](#ibm_data_virtualization_ep_min_cpu_util) | 
| [Minimum Heap memory utilization](#ibm_data_virtualization_ep_min_heapmem_util) | 
| [Number of active connections](#ibm_data_virtualization_active_conn) | 
| [Number of datasource connection status](#ibm_data_virtualization_datasource_conn_status) | 
| [Number of idle connections](#ibm_data_virtualization_idle_conn) | 
| [Number of select statements](#ibm_data_virtualization_select_stmts) | 
| [Status of BigSQL Scheduler](#ibm_data_virtualization_bigsql_scheduler_status) | 
| [Worker Average CPU utilization](#ibm_data_virtualization_wkr_node_avg_cpu_util) | 
| [Worker Average Heap memory utilization](#ibm_data_virtualization_wkr_node_avg_heapmem_util) | 
| [Worker Maximum CPU utilization](#ibm_data_virtualization_wkr_node_max_cpu_util) | 
| [Worker Maximum Heap memory utilization](#ibm_data_virtualization_wkr_node_max_heapmem_util) | 
| [Worker Minimum CPU utilization](#ibm_data_virtualization_wkr_node_min_cpu_util) | 
| [Worker Minimum Heap memory utilization](#ibm_data_virtualization_wkr_node_min_heapmem_util) | 
{: caption="Table 1: Metrics Available by Plan Names" caption-side="top"}

### Average CPU utilization
{: #ibm_data_virtualization_ep_avg_cpu_util}

Average CPU utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_ep_avg_cpu_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 2: Average CPU utilization metric metadata" caption-side="top"}

### Average Heap memory utilization
{: #ibm_data_virtualization_ep_avg_heapmem_util}

Average Heap memory utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_ep_avg_heapmem_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 3: Average Heap memory utilization metric metadata" caption-side="top"}

### CPU utilization
{: #ibm_data_virtualization_adm_cpu_util}

CPU utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_adm_cpu_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 4: CPU utilization metric metadata" caption-side="top"}

### Disk IOPS Read Total
{: #ibm_data_virtualization_ibm_disk_iops_read_total}

Disk IOPS Read Total

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_ibm_disk_iops_read_total`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 5: Disk IOPS Read Total metric metadata" caption-side="top"}

### Disk IOPS Write Total
{: #ibm_data_virtualization_ibm_disk_iops_write_total}

Disk IOPS Write Total

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_ibm_disk_iops_write_total`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 6: Disk IOPS Write Total metric metadata" caption-side="top"}

### Disk utilization percent
{: #ibm_data_virtualization_ibm_disk_io_utilization_percent}

Disk utilization percent

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_ibm_disk_io_utilization_percent`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 7: Disk utilization percent metric metadata" caption-side="top"}

### Heap memory utilization
{: #ibm_data_virtualization_adm_heapmem_util}

Heap memory utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_adm_heapmem_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 8: Heap memory utilization metric metadata" caption-side="top"}

### How long was the disk waiting because of a log being saved
{: #ibm_data_virtualization_log_disk_wait}

How long was the disk waiting because of a log being saved

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_log_disk_wait`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 9: How long was the disk waiting because of a log being saved metric metadata" caption-side="top"}

### Maximum CPU utilization
{: #ibm_data_virtualization_ep_max_cpu_util}

Maximum CPU utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_ep_max_cpu_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 10: Maximum CPU utilization metric metadata" caption-side="top"}

### Maximum Heap memory utilization
{: #ibm_data_virtualization_ep_max_heapmem_util}

Maximum Heap memory utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_ep_max_heapmem_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 11: Maximum Heap memory utilization metric metadata" caption-side="top"}

### Minimum CPU utilization
{: #ibm_data_virtualization_ep_min_cpu_util}

Minimum CPU utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_ep_min_cpu_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 12: Minimum CPU utilization metric metadata" caption-side="top"}

### Minimum Heap memory utilization
{: #ibm_data_virtualization_ep_min_heapmem_util}

Minimum Heap memory utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_ep_min_heapmem_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 13: Minimum Heap memory utilization metric metadata" caption-side="top"}

### Number of active connections
{: #ibm_data_virtualization_active_conn}

Number of active connections

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_active_conn`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 14: Number of active connections metric metadata" caption-side="top"}

### Number of datasource connection status
{: #ibm_data_virtualization_datasource_conn_status}

Number of datasource connection status

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_datasource_conn_status`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 15: Number of datasource connection status metric metadata" caption-side="top"}

### Number of idle connections
{: #ibm_data_virtualization_idle_conn}

Number of idle connections

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_idle_conn`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 16: Number of idle connections metric metadata" caption-side="top"}

### Number of select statements
{: #ibm_data_virtualization_select_stmts}

Number of select statements

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_select_stmts`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 17: Number of select statements metric metadata" caption-side="top"}

### Status of BigSQL Scheduler
{: #ibm_data_virtualization_bigsql_scheduler_status}

Status of BigSQL Scheduler

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_bigsql_scheduler_status`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 18: Status of BigSQL Scheduler metric metadata" caption-side="top"}

### Worker Average CPU utilization
{: #ibm_data_virtualization_wkr_node_avg_cpu_util}

Worker Average CPU utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_wkr_node_avg_cpu_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 19: Worker Average CPU utilization metric metadata" caption-side="top"}

### Worker Average Heap memory utilization
{: #ibm_data_virtualization_wkr_node_avg_heapmem_util}

Worker Average Heap memory utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_wkr_node_avg_heapmem_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 20: Worker Average Heap memory utilization metric metadata" caption-side="top"}

### Worker Maximum CPU utilization
{: #ibm_data_virtualization_wkr_node_max_cpu_util}

Worker Maximum CPU utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_wkr_node_max_cpu_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 21: Worker Maximum CPU utilization metric metadata" caption-side="top"}

### Worker Maximum Heap memory utilization
{: #ibm_data_virtualization_wkr_node_max_heapmem_util}

Worker Maximum Heap memory utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_wkr_node_max_heapmem_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 22: Worker Maximum Heap memory utilization metric metadata" caption-side="top"}

### Worker Minimum CPU utilization
{: #ibm_data_virtualization_wkr_node_min_cpu_util}

Worker Minimum CPU utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_wkr_node_min_cpu_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 23: Worker Minimum CPU utilization metric metadata" caption-side="top"}

### Worker Minimum Heap memory utilization
{: #ibm_data_virtualization_wkr_node_min_heapmem_util}

Worker Minimum Heap memory utilization

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_data_virtualization_wkr_node_min_heapmem_util`|
| `Metric Type` | `gauge` |
| `Value Type`  | `none` |
| `Segment By` | `Service instance` |
{: caption="Table 24: Worker Minimum Heap memory utilization metric metadata" caption-side="top"}

## Attributes for Segmentation
{: #attributes}

### Global Attributes
{: #global-attributes}

The following attributes are available for segmenting all of the metrics listed above

| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Cloud Type` | `ibm_ctype` | The cloud type is a value of public, dedicated or local |
| `Location` | `ibm_location` | The location of the monitored resource - this may be a region, data center or global |
| `Resource` | `ibm_resource` | The resource being measured by the service - typically a indentifying name or GUID |
| `Resource Type` | `ibm_resource_type` | The type of the resource being measured by the service |
| `Resource group` | `ibm_resource_group_name` | The resource group where the service instance was created |
| `Scope` | `ibm_scope` | The scope is the account, organization or space GUID associated with this metric |
| `Service name` | `ibm_service_name` | Name of the service generating this metric |
{: caption="Table 25: Global attributes for segmenting metris" caption-side="top"}

### Additional Attributes
{: #additional-attributes}

The following attributes are available for segmenting one or more attributes as described in the reference above.  Please see the individual metrics for segmentation options.

| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Service instance` | `ibm_service_instance` | The service instance segment identifies the instance the metric is associated with |
{: caption="Table 25: Attributes for segmenting attributes" caption-side="top"}
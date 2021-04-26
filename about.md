---

copyright:
  years: 2021, 2021
lastupdated: "2021-04-26"

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

# About
{: #about}

{{site.data.keyword.dv_short}} is a fully managed public cloud service on {{site.data.keyword.cloud_notm}}. It delivers the ability to view, access, manipulate, and analyze data without the need to know its physical format or location, and without having to move or copy it.
{: shortdesc}

## Key features
{: #ab_key_features}

{{site.data.keyword.dv_short}} is available as an on-demand licensing and delivery model with the following features:

- {{site.data.keyword.dv_short}} is a fully managed service on IBM Cloud that you can use to easily and securely access data across many data sources.

- You can create virtual objects, manage data source connections, virtualize data, and join virtual tables and views.
- You can manage access to objects with defined Manager, Steward, Engineer, and User roles.
- You can enable personal credentials on IBM Cloud so that they can be used when you create connections.

## Plans and configurations
{: #ab_plans_cfgs}

### Enterprise plan

Some features are limited in the {{site.data.keyword.dv_short}} beta. See [Beta limitations](#ab_plans_limits)
{: note}

- One highly available {{site.data.keyword.dv_short}} instance with a minimum of 3 head and 3 worker nodes. 
- {{site.data.keyword.dv_short}} instances have a minimum of 4 vCPU and 32 GB RAM per node.
- Three HADR nodes spanning multiple availability zones.

 #### Beta limitations
 {:#ab_plans_limits}

- HADR is not supported in the {{site.data.keyword.dv_short}} beta.
- Only one head is availaible in the beta.


<!-- ### Enterprise non-High Availability Disaster Recovery (non-HADR) plan

- Base instances start at 4 vCPU x 16 GB RAM x 20 GB storage on dedicated compute slices
- Runs the latest release of Db2, version 11.5
- Single node in one availability zone
- 1 TB of free backup storage for up to 14 days of backups
- Self-service managed backup with point-in-time restore

### Standard High Availability Disaster Recovery (HADR) plan

- Base instances start at 8 GB RAM x 20 GB storage on shared compute slices
- Runs the latest release of Db2, version 11.5
- Three HADR nodes spanning multiple availability zones
- 100 GB of free backup storage for up to 14 days of backups
- Self-service managed backup with point-in-time restore -->

## Supported data centers
{: #ab_sup_dcs}

### Multi-zone region (MZR) 

- **Dallas** - (Dal10, Dal12, Dal13)

<!-- ### Single-zone region (SZR)

### Standard non-High Availability Disaster Recovery (non-HADR) plan

- Base instances start at 8 GB RAM x 20 GB storage on shared compute slices
- Runs the latest release of Db2, version 11.5
- Single node in one availability zone
- 100 GB of free backup storage for up to 14 days of backups
- Self-service managed backup with point-in-time restore -->


<!-- SZRs support 3 node HA in a single data center in that region
{: note} -->

<!-- 
## Plans and configurations

{: #plans_cfgs} -->
<!--
You can choose a {{site.data.keyword.dv_short}} plan that is configured and optimized for the work that you need to do:
{: shortdesc}

   * A Flex plan (recommended) in which you can independently scale RAM, storage, and compute resources
   * Precise Performance plans that provide fixed resources and bare metal servers
   * Each plan can be configured for high availability and Oracle compatibility.

For heavy analytics or warehousing workloads, consider [{{site.data.keyword.dashdblong}}](https://www.ibm.com/cloud/db2-warehouse-on-cloud){:external}.

If you don't see a configuration in the catalog that you need, contact [{{site.data.keyword.IBM_notm}} Sales](https://www.ibm.com/connect/ibm/us/en/?lnk=fcw){:external} to discuss other options.

## Pricing
{: #pricing}

Prices are stated in monthly terms (for example, $189 USD per month) for an activated service. 

If the activated service is terminated before the month ends, the monthly price reflects the portion of the month during which the service remained activated.

### Billing examples
{: #billing_examples}

In the following billing examples, an example plan charge of $189 USD per month is used.

**Example 1: Monthly billing**

While the service remains activated for each monthly billing period, a charge of $189 USD per month is billed even if the service sits idle.

**Example 2: Daily billing**

Billing for Flex plans is based on peak daily usage. For example, if you scale up from 2 to 8 cores for one hour of a day, you are billed for 8 cores for only that day, and 2 cores for all of the other days of the month.

**Example 3: Prorated billing**

If an activated service with a monthly charge of $189 USD per month was used for 20 days out of the 30 days in the month before the service was terminated, the bill for the usage would be $189 USD x 20/30 = $126 USD.
-->


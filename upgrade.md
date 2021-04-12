---

copyright:
  years: 2021, 2021
lastupdated: "2021-04-12"

keywords: upgrade, Db2 on Cloud, Standard plan, Enterprise plan, legacy

subcollection: Db2onCloud

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
{:support: data-reuse='support'}
{:faq: data-hd-content-type='faq'}
{:video: .video}

# Migrating from {{site.data.keyword.Db2_on_Cloud_short}} lite
{: #upgrade_plans}

{{site.data.keyword.Db2_on_Cloud_short}} legacy plans must be upgraded to current Standard or Enterprise plans because we are deprecating support for our legacy plans. Upgrades run from **August, 2020** until **November, 2020**.
{: shortdesc}

This documentation has been updated to reflect the fact that you can no longer initiate online migrations of your legacy instances. General information about the upgrade and FAQs are still available in the following sections.

For more information about the affected legacy plans and the new replacement plans, see [Deprecation of the Db2 on Cloud Legacy Plans and Availability of New Replacement Plans](https://www.ibm.com/cloud/blog/announcements/deprecation-of-the-db2-on-cloud-legacy-plans-and-availability-of-new-replacement-plans){: external}.

Henceforth, the existing legacy plan instance is referred to as the "source" and the newly provisioned Standard or Enterprise plan instance for the upgrade is referred to as the "target".

## Self-initiated upgrade phases
{: #ug_phases}

The upgrade from the legacy {{site.data.keyword.Db2_on_Cloud_short}} plans to the current **Standard** and **Enterprise** plans is a self-service and online process. It is initiated the moment a target plan is ordered along with a source CRN input. The upgrade goes through multiple phases and for most of them no user action is required.

### Phase 0 - Provisioning target
{: #ug_prov_tgt}

The target plan is provisioned and scaled automatically to the appropriate level. The values that are used for scale depend on the current configuration of the source. No user action is required for this phase.

### Phase 1 - Preparing upgrade
{: #ug_prep}

The prerequisite steps required to upgrade the source to the target plan are run during this phase. No user action is required for this phase.

### Phase 2 - Metadata migration
{: #ug_meta_mig}

The metadata such as DDL and the database user information that exists on the source are migrated to the target during this phase. No user action is required for this phase.

### Phase 3 - Data migration
{: #ug_data_mig}

The data from the source is migrated to the target. No user action is required for this phase.

### Phase 4 - Data migration complete
{: #ug_data_mig_cmplt}

User action is required for this phase.
{: important}

The data was migrated from the source to the target. Any transactions on the source continue to be replicated on the target, but it is possible to transition to the target. After the upgrade reaches this phase, a **Transition** button is now available on the source plan on {{site.data.keyword.cloud_notm}} where the upgrade is tracked. To proceed to the next phase, user action is required to initiate the transition.

### Phase 5 - Transition in progress
{: #ug_trans_inprog}

Certain post-migration tasks are run on the target during this phase. No user action is required for this phase.

### Phase 6 - Transition and upgrade complete
{: #ug_trans_inprog_cmplt}

The upgrade is complete. The **Transition** button is now disabled. The target plan is now available to use. Any further transactions on the source are **not** replicated on the target.

## Self-initiated upgrade features and recommendations
{: #ug_feat_recom}

The upgrade process can be self-initiated only one time per source. After the new {{site.data.keyword.Db2_on_Cloud_short}} instance is created, you must be prepared to complete all of the upgrade phases. If the target instance is deleted after the upgrade is started and before all of the upgrade phases are completed, the source cannot be upgraded a second time.
{: important}

- The upgrade process is a self-service, online process.
- Users can continue to use their source plan while the upgrade proceeds.
- Every upgrade is monitored by the {{site.data.keyword.Db2_on_Cloud_short}} Operations team who are available 24x7x365.
- The data replication is unidirectional - from the source to the target.
- Any users who are created or modified on the source DURING or AFTER the upgrade process might not be migrated to the target. Do not make any user administration actions on the source after the upgrade is initiated.
- Any DDL changes on the source DURING or AFTER the upgrade process might not be replicated on the target. Do not make any DDL changes on the source after the upgrade is initiated.
- Do not insert, update, or delete any data on the target during the upgrade. Any read operation is possible and can be used to verify the data migration.
- Users can continue using the source until transition is initiated. The average transition period is about 2 minutes. In case the transition was not completed even after 30 minutes, you are recommended to continue using the source. The {{site.data.keyword.Db2_on_Cloud_short}} Operations team is alerted if there is an issue with the transition and the button is re-enabled when it is possible to transition again.
- After the upgrade and transition to the new instance is completed, delete your legacy system. This is a final step to initiate, otherwise, the upgraded legacy instances will be blocked after **November 15, 2020**, and decommissioned in November if upgrades were successfully completed; unless a support case was opened to request an extension.

## Billing during the upgrade
{: #ug_billing}

- You are NOT billed for the target during the upgrade. You are billed for the source as usual.
- If you do not initiate transition after a period of 2 weeks since the option was available and you have 2 active systems, you might be billed for the target.
- After the upgrade is complete, you will be billed for the target and will NOT be billed for the source.
- If you do not delete the source plan before the end of the 2-week grace period that follows completion of the upgrade, you might then be billed for the source again.

## FAQs - Upgrading to Standard and Enterprise plans
{: #faq_db2oc_upgrade}

This section is a collection of frequently asked questions (FAQ) about upgrading the {{site.data.keyword.Db2_on_Cloud_long}} plans. [Create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} if you have any questions about the upgrade and migration.

### Which instances are legacy instances that must be updated?
{: #q_which_legacy}
{: faq}
{: support}

The following plan instances must be upgraded to the Standard or Enterprise plan: 
   - IBM Db2 on Cloud Flex
   - IBM Db2 on Cloud Precise Performance 2.8.500 (small)
   - IBM Db2 on Cloud Precise Performance 12.128.1400 (large)

If your instance name begins with the string `dashdb-txn-flex`, `dashdb-txn-small`, `dashdb-txn-large`, or one of those strings with `txnha` in place of `txn`, it is a legacy instance and must be upgraded.

Lite plan instances do not require an upgrade. Lite plan instance names contain the string `dashdb-txn-sbox`.

### How much do the Standard and Enterprise plans cost?
{: #q_cost}
{: faq}
{: support}

Prices are detailed by plan in the [{{site.data.keyword.cloud_notm}} catalog](https://cloud.ibm.com/catalog/services/db2){: external}

### Will I be billed for two plans during the upgrade?
{: #q_bill_two}
{: faq}
{: support}

After you begin the upgrade, you have 14 days to move to the new plan. The upgrade timeline starts when you provision a {{site.data.keyword.Db2_on_Cloud_short}} Standard or Enterprise plan and provide your CRN from your legacy plan in the upgrade details on the **Service create** page in the {{site.data.keyword.cloud_notm}} catalog. If you don't complete the upgrade during that 14-day period, you might be charged for both source and target plans.

### What will I need to change after the upgrade to a new plan?
{: #q_change}
{: faq}
{: support}

See [Differences between legacy and current plans](/docs/Db2onCloud?topic=Db2onCloud-plan_diffs){: external}.

### Can I use the new HADR feature in the new plans in place of our existing DR node solution in the legacy plans? 
{: #q_leverage_ha}
{: faq}
{: support}

The new plans offer a High Availability Disaster Recovery (HADR) feature with 3 nodes that are located in different independent availability zones and the failover is managed for you by IBM. This feature avoids any service disruption that is caused by a data center disaster, failure, or maintenance. For more information about {{site.data.keyword.cloud_notm}} Multi-Zone Regions (MZR), see [Why Deploy Applications on IBM Cloud Availability Zones?](https://www.ibm.com/cloud/blog/why-deploy-applications-on-ibm-cloud-availability-zones){: external}.

A few of you might require legacy-style disaster recovery (DR) instead of the new HADR feature. Legacy-style disaster recovery (DR) is planned to be supported in all locations by **March 15, 2021**. [Create a support case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} and have a conversation with our Development Operations team if you require this Cross-Region DR-specific feature.

### I have a non-HA plan, but want to upgrade to Standard or Enterprise HADR (or vice versa). Can I do that?
{: #q_noha_ha}
{: faq}
{: support}

Yes, you can move from any legacy plan (Flex, Small, and Large) to any {{site.data.keyword.Db2_on_Cloud_short}} Standard and Enterprise plan. You can move from non-HA to HADR, or from HA to non-HADR. See the following question about HADR information in Standard and Enterprise plans.

### How is the high availability disaster recovery (HADR) feature done in Standard and Enterprise plans?
{: #q_dr}
{: faq}
{: support}

Standard and Enterprise plans provide automated redundancy across 3 different data centers with the HADR option. These data centers are physically isolated from each other and do not share any infrastructure. The reference design for different data centers within a multi-zone region (MZR) is that they are separated by at least 10 km or 6 mi. This is a significant improvement from our legacy plans in which you can have only 2 nodes that are in a single data center. In addition, Standard and Enterprise HADR plans also provide `Read on standby` capability. {{site.data.keyword.Db2_on_Cloud_short}} also provides backups, which can be restored to a new region if all data centers are unrecoverable. These backups, and archive logs, are geo-replicated across several regions (more than 400 km or 250 mi away from the MZR), protecting you from even the worst natural disasters. In many cases, this suffices instead of having a DR node in a different region.

### Is HIPAA supported by Standard and Enterprise plans?
{: #q_hipaa}
{: faq}
{: support}

As of **October 20, 2020**, both the Standard and Enterprise plans support the **Health Information Portability and Accountability Act** of 1996 ("HIPAA"). 

For more information about restrictions, consult the [Service Description](http://www-03.ibm.com/software/sla/sladb.nsf/sla/bm-7519-14){: external}.

### What if I'm not receiving emails that are related to this legacy plan upgrade?
{: #q_no_emails}
{: faq}
{: support}

The owner of your {{site.data.keyword.cloud_notm}} account that is associated with the legacy {{site.data.keyword.Db2_on_Cloud_short}} plan instance must [create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} to add additional email addresses to the {{site.data.keyword.cloud_notm}} account.

### How can I learn more?
{: #q_learn_more}
{: faq}
{: support}

- For more information about the plan upgrades, see [Upgrading {{site.data.keyword.Db2_on_Cloud_short}} plans](#upgrade_plans).
- For information about our Standard and Enterprise plans, see [About: Plans and configurations](/docs/Db2onCloud?topic=Db2onCloud-about#ab_plans_cfgs)
- [Blog post that announces new Enterprise HA plan](https://www.ibm.com/cloud/blog/announcements/db2-on-cloud-announces-new-enterprise-high-availability-plan){: external}
- [Blog post announcing new Standard HA plan](https://www.ibm.com/cloud/blog/announcements/db2-on-cloud-standard-plan){: external}
- [What's New](https://www.ibm.com/support/pages/node/739537){: external} about the {{site.data.keyword.Db2_on_Cloud_short}} Standard and Enterprise plans now available in 6 data centers, including support for Oracle compatibility

---

copyright:
  years:  2021, 2022
lastupdated: "2021-06-07"

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

# Auditing
{: #auditing}

You can monitor data access in your {{site.data.keyword.dv_short}}  instance with the built-in Db2 audit facility. Use the Db2 audit facility to generate and maintain an audit trail for a series of predefined data events, including attempts to access or manipulate data objects, user authentication, SQL statement execution, and even access to the audit log. You can use the audit log to reveal usage patterns that would identify system misuse, and in turn, take action to eliminate such misuse.
{: shortdesc}

For more information about auditing for {{site.data.keyword.dv_short}} , see [Audit policy guidelines](https://dataplatform.cloud.ibm.com/docs/content/dvaas/dv-object-management.html){: external}.


You can also audit and track changes to your database by using the following method:
* By creating a `CHANGE HISTORY` event monitor, you can query the event monitor table to determine what was done within the database and by whom. For more information, see [`CHANGE HISTORY` event monitor](https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.1.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059363.html){: external}.

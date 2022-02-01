---

copyright:
  years: 2021, 2022
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

# Data security and encryption
{: #encryption}

The {{site.data.keyword.dv_short}} service has security built into all levels of its architecture.
{: shortdesc}

The following methods are used to secure your data:
-  The default keys are managed by [Key Protect](/docs/key-protect?topic=key-protect-importing-keys). Bring-your-own-key [(BYOK)](/docs/Db2onCloud?topic=Db2onCloud-key-protect-v2) for encryption is also available through Key Protect integration.
- Data in motion is encrypted through SSL/TLS. The current supported version of this encryption is TLS 1.2.
- All {{site.data.keyword.dv_short}} storage is provided on storage encrypted by using AES-256 encryption.
- Backplane network connectivity is supported through {{site.data.keyword.cloud}} Service Endpoints

Administrators can make encrypted connections mandatory. For more information, see [SSL connectivity](/docs/Db2onCloud?topic=Db2onCloud-ssl_support).
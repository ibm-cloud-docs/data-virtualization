---

copyright:
  years: 2021, 2023
lastupdated: "2023-03-08"

keywords: 

subcollection: data-virtualization

content-type: faq

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
{:support: data-reuse='support'}
{:faq: data-hd-content-type='faq'}
{:video: .video}

# FAQs - General
{: #faq_dv}

This is a collection of frequently asked questions (FAQ) about the {{site.data.keyword.dv_short}} service.
{: shortdesc}

## How do I generate credentials for my instance?
{: #q_creds}
{: faq}
{: support}

1. Log into [IBM Cloud](https://cloud.ibm.com){: external}.
2. Open your [**Resource list**](https://cloud.ibm.com/resources){: external}.
3. Under **Databases**, locate your {{site.data.keyword.dv_short}} instance and click on the service name.  
   This list includes all instances that were created under a resource group or that were migrated into a resource group.
4. Click **Service credentials > New credentials > Add** to generate your {{site.data.keyword.dv_short}} Manager credentials.
5. Expand **View credentials**, which displays your service connectivity information including your credentials (username and password).
6. The Manager credentials can be used to connect to both {{site.data.keyword.dv_short}} and the web console.


## Now that I've generated credentials, how do I access my {{site.data.keyword.dv_short}} instance?
{: #q_access}
{: faq}
{: support}

You can access your {{site.data.keyword.dv_short}} instance by using a dedicated **Data virtualization** workspace in IBM Cloud Pak for Data as a Service 
and the [{{site.data.keyword.dv_short}} Rest APIs](https://{DomainName}/apidocs/data-virtualization-on-cloud){: external}.

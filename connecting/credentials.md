---

copyright:
  years: 2021, 2022
lastupdated: "2022-06-06"

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

# Database details and connection credentials
{: #db_details_cxn_creds}

To configure your local development environment and to connect applications and tools to your {{site.data.keyword.dv_short}} instance, you need to know the database details and connection credentials.
{: shortdesc}

## Database details
{: #db_details}

There are important database details that are needed for connecting applications and tools to your database:

- *Host name* - The host name of the server.
- *Port number* - Used by the database manager for TCP/IP communication. (Note that your service is provisioned with connections that use Secure Socket Layer (SSL).)

   If needed, you can get the IP address of your server by using the ping command or the nslookup command, specifying your host name.
- *Database name* - The {{site.data.keyword.dv_short}} instance name, usually BLUDB.

## Connection credentials
{: #cxn_creds}

There are three types of credentials:

- *IBMid* - If you use {{site.data.keyword.Bluemix_notm}}, this is the ID that you would use to log in to {{site.data.keyword.Bluemix_notm}}. Only the IBMID can be used to manage users by accessing **User Management** in the web console. This is not what you use to connect applications or tools to your {{site.data.keyword.dv_short}} instance.
- *{{site.data.keyword.dv_short}} instance credentials* - These credentials are generated when you create **New credential** under **Service credentials** for the service in {{site.data.keyword.Bluemix_notm}}.
- *IBMid-created users* - These IBMid-created user IDs and passwords can be used to log directly into the web console URL and to connect to the {{site.data.keyword.dv_short}} instance from applications or tools.

## Where to find database details and connection credentials
{: #location}

You can collect this information from the following places:

- *The Service Owner* - If you are not the owner of your {{site.data.keyword.dv_short}} instance, you can get your database details and connect credentials from the owner.
- *{{site.data.keyword.dv_short}} web console* - Database details and credentials are available in the web console.
- If you are using {{site.data.keyword.Bluemix_notm}}: 
   
   - *{{site.data.keyword.Bluemix_notm}} Dashboard* - When you view your service on your {{site.data.keyword.Bluemix_notm}} dashboard, you can view the database details, the database user ID, and password. To retrieve your service credentials, select the **Service credentials** tab from your service page, click the **New credential** button, then select **View credentials**.
   - *`VCAP_SERVICES`* - `VCAP_SERVICES` is an environment variable in {{site.data.keyword.Bluemix_notm}} that contains database details and credentials in JSON format. When you view the service credentials for your service in your {{site.data.keyword.Bluemix_notm}} dashboard, the contents of `VCAP_SERVICES` is what is displayed. When you bind other {{site.data.keyword.Bluemix_notm}} services or apps to your service, those other services or apps can access database details and credentials programmatically by reading `VCAP_SERVICES`.

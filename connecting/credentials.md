---

copyright:
  years: 2021, 2022
lastupdated: "2022-11-24"

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

To configure your local environment and to connect applications and tools to your {{site.data.keyword.dv_short}} instance, you need to know the database details and connection credentials.
{: shortdesc}

## Database details
{: #db_details}

There are important database details that are needed for connecting applications and tools to your database:

- *Host name* - The host name of the server.
- *Port number* - Used by the database manager for TCP/IP communication. (Note that your service is provisioned with connections that use Secure Socket Layer (SSL).)

   If needed, you can get the IP address of your server by using the ping command or the nslookup command, specifying your host name.
- *Database name* - The database name for the {{site.data.keyword.dv_short}} service instance is BLUDB.

## Connection credentials
{: #cxn_creds}

To connect to {{site.data.keyword.dv_short}}, you must use API keys or access tokens that are obtained for IBMids that have access to the {{site.data.keyword.dv_short}} service instance. Any passwords or API keys of those users are managed through IBM Access and Identity management.

- *IBMid* - If you use {{site.data.keyword.Bluemix_notm}}, this is the ID that you would use to log in to {{site.data.keyword.Bluemix_notm}}. Only the IBMID can be used to manage users by accessing **User Management** in the web console. This is not what you use to connect applications or tools to your {{site.data.keyword.dv_short}} instance.
- *{{site.data.keyword.dv_short}} instance credentials* - These credentials are generated when you create **New credential** under **Service credentials** for the service in {{site.data.keyword.Bluemix_notm}}.
- *IBMid-created users* - These IBMid-created user IDs and passwords can be used to log directly into the web console URL and to connect to the {{site.data.keyword.dv_short}} instance from applications or tools.
- You can generate credentials from the **Service Credentials** page for the service instance. If you have existing IAM users, you can add them and assign roles to each user by accessing the {{site.data.keyword.dv_short}} UI (from the Manage page).  Select **User Management** from the service menu and assign the appropriate role (Manager, Steward, Engineer or Viewer) for each user.

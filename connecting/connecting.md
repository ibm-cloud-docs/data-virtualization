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

# Connecting overview
{: #connect_ov}

You can connect command-line interfaces, IBM® or third-party applications and tools, or apps that you create to your {{site.data.keyword.dv_short}} instance. 
{: shortdesc}

## Prerequisites
{: #prereqs}

Before attempting to connect to your {{site.data.keyword.dv_short}} instance, verify that you have the prerequisites. 

- Collect database details and credentials

   To connect to your database, you need database details (such as the host name), and credentials (such as a user ID and password.) You can collect this connection information from the **Service credentials** table of the {{site.data.keyword.dv_short}} service instance or from the {{site.data.keyword.dv_short}} web console.

- Verify that a supported driver is installed

   - If your application or tool already contains the Db2 v11.5 IBM Data Server Driver Package, then your application or tool is able to connect to your {{site.data.keyword.dv_short}} instance by using that driver.
   - Otherwise, install the Db2 driver package, which you can download from [here](https://www.ibm.com/support/pages/node/387577){: external}.

- Configure your environment

  - Add entries to the driver configuration file, `db2dsdriver.cfg`, for your database.
  - Secure Sockets Layer (SSL)

    Connection details, such as which port to use and the connection string, depend on whether you use SSL connections. SSL is the default connection method.

    To use SSL connections, you need a CA certificate:
    - If you use the most recent {{site.data.keyword.dv_short}} driver package, the certificate file is bundled with the package and is used for connections.
    - If you use the IBM Data Server Driver Package, you can download the SSL certificate from the {{site.data.keyword.dv_short}} web console.

- Confirm that ports are available

   If your network is behind a firewall, confirm that communications are permitted on the port that is needed to connect to the {{site.data.keyword.dv_short}} service. The port number can be found in the connection information from the **Service credentials** table of the {{site.data.keyword.dv_short}} service instance or from the {{site.data.keyword.dv_short}} web console.


### Collecting connection information
{: #collect_info}

- [Database details and connection credentials](/docs/Db2onCloud/connecting?topic=Db2onCloud-db_details_cxn_creds)


### Downloading and installing driver package
{: #dl_install}

- [Download driver package](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg)
- [Installing on Linux or PowerLinux](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_install_linux)
- [Installing on Mac OS X](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_install_mac)
- [Installing on Windows](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_install_windows)


### Configuring your environment
{: #cfg_env}

- [Configuring your environment](/docs/Db2onCloud/connecting?topic=Db2onCloud-drvr_pkg#drvr_cfg_loc_env)
- [SSL connectivity](/docs/Db2onCloud/connecting?topic=Db2onCloud-ssl_support)


## Connectivity options
{: #connect_opts}

{{site.data.keyword.dv_short}} offers multiple secure connectivity options depending on your application connection requirements.  
{: shortdesc}

See [Connectivity options](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_options).

### Data integration
{: #di}

- Connect your {{site.data.keyword.Bluemix_short}} applications that need an analytics database.
- [DataStage](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#datastage)
- [InfoSphere Data Replication](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#idr)
- [Segment](https://segment.com/docs/destinations/db2/){: external}
- [Data Studio](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#data_studio)
- [Data Server Manager](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#dsm)
- [CLPPLUS](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#clpplus)
- [InfoSphere Data Architect to design and deploy your database schema](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#ida)


### Data visualization & BI
{: #dvis_bi}

- [Looker](https://docs.looker.com/setup-and-management/connecting-to-db){: external}
- [Tableau](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#tableau)
- [Microsoft Excel](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#excel)


### Data science
{: #dsci}

- [Watson Studio (formerly IBM Data Science Experience)](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#watson_studio)
- [SPSS Statistics](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_ibm#spss_stats)
- [SAS](/docs/Db2onCloud/connecting?topic=Db2onCloud-connect_3rd_party#sas)

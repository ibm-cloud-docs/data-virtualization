---

copyright:
  years: 2021, 2022
lastupdated: "2022-12-19"

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

# Connectivity options
{: #connect_options}

{{site.data.keyword.dv_short}} offers multiple secure connectivity options that depend on your application connection requirements.  
{: shortdesc}

## Connecting to a public endpoint (default option)
{: #pub_endpt}

As with any public cloud service, you can connect your application by way of a public host name that is provided to you at the time that your service is provisioned. Access to your data is protected by strong authentication, vast Db2 authorization options and access controls, encryption over the wire and at rest, and IBM security and compliance practices for development and operations. 

### How to connect to a public endpoint:
{: #pub_endpt_steps}

The easiest way to connect to your data is by way of the public host name that was provided in your welcome letter. You can also obtain your host name and credentials in the following ways:

#### From the console
{: #pub_console}

1. Log in to {{site.data.keyword.dv_short}} and click your service instance.
2. Click **Manage**.
3. Click **Open Console**, then click **Administration**.
4. Select **Connections**.
5. The public and private endpoints will be displayed under **Connection Configuration Resources** by selecting the respective radio button.

#### From service credentials
{: #pub_sc}

1. Log in to {{site.data.keyword.dv_short}} and click your service instance.
2. Click **Service credentials**.
3. Click **New credential**, then click **Add**.
4. After the credentials are created, click the down arrow beside the credential names to view the credentials.
5. In the resulting JSON document, you will see the "apikey", which contains the API key that can be used to connect as the generated user. The JSON also contains db2cli, jdbc, and legacy information to connect to the system using a Db2 driver or client of your choosing.

#### Service credentials breakdown
{: #pub_endpt_current}

| Field Name | Index | Description |
|----------|--------|-----------|
| `apikey` | Type of connection - "URI" |
| `connection` | Scheme for a URI - "db2" |
| `iam_apikey_description` | Path for a URI - Database name. The default is `bludb`. |
| `iam_apikey_name` | The user name that you use to connect |
| `iam_role_crn` | A password for the user |
| `iam_serviceid_crn` | How authentication takes place; "direct" authentication is handled by the driver |
| `instance_administration_api` | A host name and port to connect to |
{: caption="Table 1. Service Credentials information" caption-side="top"}


##### Connection section
{: #pub_connection}

The "connection" section contains information that is suited to applications that make connections to `{{site.data.keyword.dv_short}}`.

| Field Name |  Description |
|----------|-----------|
| `clpplus` | Information for connecting using clpplus |
| `db2cli` | Information for connecting db2cli |
| `jdbc`  | Information for connecting using JDBC |
| `legacy` | Information for connecting using applications that do not support APIKEY or ACCESSTOKEN connectivity |
{: caption="Table 2. Connection information" caption-side="top"}

`0...` indicates that there might be one or more of these entries in an array.

#### Example Service Credential JSON
{: #pub_example_service_cred}

The following VCAP Services json file can be used to make connections to your {{site.data.keyword.dv_short}} service instances:

```sh
{
  "apikey": "<APIKEY>>",
  "connection": {
    "clpplus": {
      "arguments": [
        [
          "CONNECT",
          "@<DSN>",
          "using",
          "(",
          "apikey",
          "<APIKEY>",
          ")"
        ]
      ],
      "bin": "clpplus",
      "composed": [
        "CONNECT @<HOST> using ( apikey <APIKEY> )"
      ],
      "environment": {},
      "type": "clpplus"
    },
    "db2cli": {
      "arguments": [
        [
          "writecfg",
          "add",
          "-dsn",
          "<DSN>",
          "-database",
          "bludb",
          "-host",
          "<HOSTNAME>",
          "-port",
          "<PORT>",
          "-parameter",
          "\"Authentication=GSSPLUGIN;SecurityTransportMode=SSL\""
        ]
      ],
      "bin": "db2cli",
      "composed": [
        "db2cli writecfg add -dsn <DSN> -database bludb -host <HOSTNAME> -port <PORT> -parameter \"Authentication=GSSPLUGIN;SecurityTransportMode=SSL\""
      ],
      "environment": {},
      "type": "cli"
    },
    "jdbc": {
      "environment": {},
      "jdbc_url_accesstoken": [
        "jdbc:db2://<HOSTNAME>:<PORT>/bludb:securityMechanism=15;accessToken=<ACCESSTOKEN>;sslConnection=true;"
      ],
      "jdbc_url_api_key": [
        "jdbc:db2://<HOSTNAME>:<PORT>/bludb:securityMechanism=15;apiKey=<APIKEY>;sslConnection=true;"
      ],
      "type": "uri"
    },
    "legacy": {
      "certificate": {
        "certificate_base64": "<BASE64_ENCODED_CERT>",
        "name": "<NAME>"
      },
      "database": "bludb",
      "hosts": [
        {
          "hostname": "<HOSTNAME>",
          "port": <PORT>
        }
      ],
      "legacyuser": [
        {
          "password": "<APIKEY>",
          "username": "IBM_SUBSTTOKEN_APIKEY"
        }
      ],
      "type": "uri"
    }
  },
  "iam_apikey_description": "<IAM_APIKEY_DESCRIPTION",
  "iam_apikey_name": "<IAM_APIKEY_NAME>",
  "iam_role_crn": "crn:v1:bluemix:public:data-virtualization::::serviceRole:manager-generated-service-credentials-only",
  "iam_serviceid_crn": "<SERVICE_ID_CRN>",
  "instance_administration_api": {
    "deployment_id": "<CRN>",
    "instance_id": "<CRN>",
    "root": "<API ROOT_URL>"
  }
}
```

## Connecting to a private endpoint: IBM Cloud service endpoint
{: #priv_endpt}

{{site.data.keyword.dv_short}} supports private connectivity through an [{{site.data.keyword.cloud_notm}} service endpoint](/docs/account?topic=account-service-endpoints-overview). {{site.data.keyword.cloud_notm}} service endpoints securely route network traffic between different {{site.data.keyword.cloud_notm}} services through the {{site.data.keyword.cloud_notm}} private backplane network. When you configure your {{site.data.keyword.dv_short}} instance with {{site.data.keyword.cloud_notm}} service endpoint connectivity, traffic between your cloud database and applications deployed on your {{site.data.keyword.cloud_notm}} account will not traverse any public networks.

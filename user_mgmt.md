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

# Managing users
{: #user_mgmt}

## Current plans
{: #um_current_plans}

Access to {{site.data.keyword.dv_short}} service instances for users in your account is controlled by [Identity and access management (IAM) on IBM Cloud](/docs/data-virtualization?topic=data-virtualization-iam) and database access is provided by standard access controls provided by the database. 

For more information about IAM, see [What is IBM Cloud Identity and Access Management?](/docs/account?topic=account-iamoverview).

### User types
{: #um_user_types} 

#### IAM users
{: #um_iam_users}

IAM is only integrated with high-level service access, which governs privileges and operations available in the {{site.data.keyword.dv_short}} console and database. Access to the database by these IAM users is provided by allowing an IAM user or service ID access to a specific Db2 user, as mentioned earlier.

### Roles and access
{: #um_roles_access}

Users can use JDBC or any Db2 client to connect to their database. There are two ways that users can access the database: 
- Use their database user name and password associated with their account 
- Use the IAM token (or APIKey, which gets the token) that is mapped to the associated database user 

IAM authentication is performed as the authentication mechanism. Permissions are not controlled by IAM. Permissions are controlled by database level privileges of the associated user. 

## {{site.data.keyword.dv_short}} roles

{: @dv_roles}

There are four roles in {{site.data.keyword.dv_short}}: Manager (service administrator), Engineer, Steward, and User. Each of these roles can take advantage of different capabilities. These roles apply to a user's access to a {{site.data.keyword.dv_short}} as a service instance, which is also known as **Service access**. 

There are also Platform roles that apply to the user's **Platform access**, which affects scaling and monitoring of {{site.data.keyword.dv_short}}.

You must assign one of the following {{site.data.keyword.dv_short}} roles for a user to have access to the service:

### {{site.data.keyword.dv_short}} Manager

The {{site.data.keyword.dv_short}} Manager role is automatically assigned to the user who provisions the {{site.data.keyword.dv_short}} service. After the provisioning the service, the {{site.data.keyword.dv_short}} Manager can grant other users access.

The {{site.data.keyword.dv_short}} Manager assigns appropriate {{site.data.keyword.dv_short}} roles to Cloud Pak for Data users.

### {{site.data.keyword.dv_short}} Engineer

The {{site.data.keyword.dv_short}} Engineer configures data sources, virtualizes data, and manages access to virtual objects. Users with this role can create or view a virtual table and grant any {{site.data.keyword.dv_short}} user access to it. 

By default, every virtual object created in {{site.data.keyword.dv_short}} is private. Access to private virtual objects must be granted to users other than its creator.

Data source administrators are expected to provide access to a {{site.data.keyword.dv_short}} Engineer to virtualize data.

### {{site.data.keyword.dv_short}} User

Users with this role can create views of virtual tables to which they have access.

### {{site.data.keyword.dv_short}} Steward

{{site.data.keyword.dv_short}} Stewards can access data in all user tables and views. Additionally, Stewards hold the Db2® DATAACCESS authority on the database.

The following table summarizes the {{site.data.keyword.dv_short}} menu functions that each of the {{site.data.keyword.dv_short}} user roles is able to access.

| Menu | Capabilities | Manager | Engineer | Steward | User | Platform administrator | Platform operator | Platform editor | Platform viewer |
|--------|---------|---------|--------|--------|---|---|---|----|----|
| Virtualization      | Data source	       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      |        |   |   |   |    |    |
|        | Virtualize       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      |        |   |   |   |    |    |
|        | My virtualized data	       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      |        |   |   |   |    |    |
| Monitor dashboard      | Summary       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)   | ![checkmark](images/checkmark.png)   | ![checkmark](images/checkmark.png)
|        | Database partitions       | ![checkmark](images/checkmark.png)       |        |        |   |   |   |    |    |
|        | Statement       | ![checkmark](images/checkmark.png)       |        |        |   |   |   |    |    |
|        | Applications       | ![checkmark](images/checkmark.png)       |        |        |   |   |   |    |    |
|        | Throughput       | ![checkmark](images/checkmark.png)       |        |        |   |   |   |    |    |
|        | Buffer pools       | ![checkmark](images/checkmark.png)       |        |        |   |   |   |    |    |
|        | Table performance       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      |        |   |   |   |    |    |
|        | Storage       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      |        |   |   |   |    |    |
| Run SQL      | Run SQL       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)  |   |   |    |    |
| Explorer      | Tables       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)  |   |   |    |    |
|        | Views       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)  |   |   |    |    |
|        | Remote tables       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)   |   |   |    |    |
|        | Aliases       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)        | ![checkmark](images/checkmark.png)   |   |   |    |    |
|        | MQTs       | ![checkmark](images/checkmark.png)       |       |        |   |   |   |    |    |
|        | Schemas       | ![checkmark](images/checkmark.png)       |       |        |   |   |   |    |    |
|        | Authorization       | ![checkmark](images/checkmark.png)       |        |        |   |   |   |    |    |
|        | Sequences       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)   |   |   |    |    |
|        | Application objects       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)  |   |   |    |    |
| User management      | User management       |         |        |        |   | ![checkmark](images/checkmark.png)   |   |    |    | ![checkmark](images/checkmark.png)
| Connection details      | Connection details       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)  |   |   |    |    |
| Service settings      | Service settings->General       | ![checkmark](images/checkmark.png)       | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)      | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)   | ![checkmark](images/checkmark.png)   | ![checkmark](images/checkmark.png)   | ![checkmark](images/checkmark.png)   |
|        | Service settings->Governance       | ![checkmark](images/checkmark.png)       |        |        |   |   |   |    |    |
|        | Service settings->Scaling       |         |        |        |   | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)   |    |
|        | Service settings->Maintenance update       |         |        |        |   | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)   |    |
|        | Service settings->Access restriction       |         |        |        |   | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)  | ![checkmark](images/checkmark.png)   |    |
{: caption="Table 1. {{site.data.keyword.dv_short}} menu functions that each of the {{site.data.keyword.dv_short}} user roles is able to access" caption-side="top"}

#### {{site.data.keyword.dv_short}} permissions

| Roles | Permissions   |
|---|-----|
| {{site.data.keyword.dv_short}} Manager | Administer the service, Administer the database, Access data, Manage data sources, Manage users and assign {{site.data.keyword.dv_short}} roles, Create and share any schema, Manage data caches, Manage data queries
| {{site.data.keyword.dv_short}} Engineer | Access connection details, Manage data sources, Create virtual tables and views, Create and manage private schema |
| {{site.data.keyword.dv_short}} User | Access connection details, Create virtual views over existing virtual tables and views, Create and manage private schema |
| {{site.data.keyword.dv_short}} Steward | Access connection details, Access data, Create virtual views over existing virtual tables and views, Create and manage private schema |
<!-- 
{: caption="Table 2. Permissions associated with each {{site.data.keyword.dv_short}} role." caption-side="top"} -->
---

copyright:
  years: 2014, 2021
lastupdated: "2021-04-15"

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

Access to Data Virtualization service instances for users in your account is controlled by [Identity and access management (IAM) on IBM Cloud](/docs/data-virtualization?topic=data-virtualization-iam) and database access is provided by standard access controls provided by the database. 

For more information about IAM, see [What is IBM Cloud Identity and Access Management?](/docs/account?topic=account-iamoverview).

### User types
{: #um_user_types} 

#### IAM users
{: #um_iam_users}

IAM is only integrated with high-level service access, which governs privileges and operations available in the Data Virtualization console and database. Access to the database by these IAM users is provided by allowing an IAM user or service ID access to a specific Db2 user, as mentioned earlier.

### Roles and access
{: #um_roles_access}

Users can use JDBC or any Db2 client to connect to their database. There are two ways that users can access the database: 
- Use their database user name and password associated with their account 
- Use the IAM token (or APIKey, which gets the token) that is mapped to the associated database user 

IAM authentication is performed as the authentication mechanism. Permissions are not controlled by IAM. Permissions are controlled by database level privileges of the associated user. 

#### Console access
{: #um_console_access}

Console access is controlled by IAM. An IAM user can be assigned access by the IAM interface to all Db2 service instances, all Db2 service instances in a resource group, or a specific service instance. Within these parameters, IAM users can be assigned platform and service-level access.


| Role         | User mgmt | SQL editor/tables | Monitoring info | Settings (includes scale, backup, etc.) | Info panels |
|--------------|-----------|-------------------|-----------------|-----------------------------------------|-------------|
| IAM - Platform - Viewer       | No | No (unless mapped to Db2 user) | Yes | No  | Yes |
| IAM - Platform - Operator     | No | No (unless mapped to Db2 user) | Yes | Yes | Yes |
| IAM - Platform - Editor       | No | No (unless mapped to Db2 user) | Yes | Yes | Yes |
| IAM - Platform - Administrator | Yes | No (unless mapped to Db2 user) | Yes | Yes | Yes |
| Non-IAM, but autheticate with JDBC | Only "Change password" | Yes | No | No | Yes |
{: caption="Table 1. Roles and console permissions" caption-side="top"}

## Data Virtualization roles

{: @dv_roles}

There are four roles in Data Virtualization: Manager (service administrator), Engineer, Steward, and User. Each of these roles can take advantage of different capabilities. These roles apply to a user's access to a Data Virtualization as a service instance, which is also known as **Service access**. 

There are also Platform roles that apply to the user's **Platform access**, which affects scaling and monitoring of Data Virtualization.

You must assign one of the following Data Virtualization roles for a user to have access to the service:

### Data Virtualization Manager

The Data Virtualization Manager role is automatically assigned to the user who provisions the Data Virtualization service. After the provisioning the service, the Data Virtualization Manager can grant other users access.

The Data Virtualization Manager assigns appropriate Data Virtualization roles to Cloud Pak for Data users.

### Data Virtualization Engineer

The Data Virtualization Engineer configures data sources, virtualizes data, and manages access to virtual objects. Users with this role can create or view a virtual table and grant any Data Virtualization user access to it. 

By default, every virtual object created in Data Virtualization is private. Access to private virtual objects must be granted to users other than its creator.

Data source administrators are expected to provide access to a Data Virtualization Engineer to virtualize data.

### Data Virtualization User

Users with this role can create views of virtual tables to which they have access.

### Data Virtualization Steward

Data Virtualization Stewards can access data in all user tables and views. Additionally, Stewards hold the Db2® DATAACCESS authority on the database.

The following table summarizes the Data Virtualization menu functions that each of the Data Virtualization user roles is able to access.

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
|        |         |         |        |        |   |   |   |    |    |

{: caption="Table 1. Data Virtualization menu functions that each of the Data Virtualization user roles is able to access" caption-side="top"}

#### Data Virtualization permissions

| Roles | Permissions   |
|---|-----|
| Data Virtualization Manager | Administer the service, Administer the database, Access data, Manage data sources, Manage users and assign Data Virtualization roles, Create and share any schema, Manage data caches, Manage data queries
| Data Virtualization Engineer | Access connection details, Manage data sources, Create virtual tables and views, Create and manage private schema |
| Data Virtualization User | Access connection details, Create virtual views over existing virtual tables and views, Create and manage private schema |
| Data Virtualization Steward | Access connection details, Access data, Create virtual views over existing virtual tables and views, Create and manage private schema |
{: caption="Table 2. Permissions associated with each Data Virtualization role." caption-side="top"}

<!-- Management of users that were given access to the database is the sole responsibility of the user or users with the administrator role. The administrator has the responsibility to manage how other users in your organization access your database.
{: shortdesc}

The database administrator role manages the following types of user access: 
* Web console. From the web console, users can run queries against the database.
* Database. The administrator can grant granular access permissions to the database, including being able to access only certain tables, schemas, or even rows or columns. 

For more information about user management, see [Database user management](https://www.ibm.com/support/knowledgecenter/SSFMBX/com.ibm.swg.im.dashdb.security.doc/doc/user_mgmnt.html){:external} -->

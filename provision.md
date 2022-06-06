---

copyright:
  years: 2021, 2022
lastupdated: "2022-06-06"

keywords: provision cloud database, provisioning parameters, data virtualization

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
{:video: .video}

# Provision a service instance
{: #provisioning}

To deploy an {{site.data.keyword.dv_short}} service, you need to create a {{site.data.keyword.dv_short}} service instance. 
{: shortdesc}

You can provision a deployment by visiting the service's catalog page or by specifying the service ID to the command line or to the API. The deployment type is determined by the service ID, which you must specify when you create a {{site.data.keyword.dv_short}} deployment by using the command line or API.

You can choose one of the following plans in {{site.data.keyword.dv_short}}.

**Enterprise:** Use this plan to create a dedicated and highly available {{site.data.keyword.dv_short}} instance with flexible scaling of worker nodes. Head nodes have 8 vCPU and 32 GB RAM per node. 4 vCPUs per head node are allocated to service management and monitoring and are not included in the Virtual Processor Core-Hour charge. Worker nodes have 4 vCPU and 32 GB RAM per node. Each month comes with 250 free Virtual Processor Core-Hours.

**Lite:** Use this plan to create a single tenant {{site.data.keyword.dv_short}} instance. The {{site.data.keyword.dv_short}} instance includes one Head node with 4 vCPU and 16 GB RAM and one worker node with 4 vCPU and 16 GB RAM. You cannot take advantage of scaling and high availability.

| Deployment Type | Catalog Page | Service ID | Plan IDs |
|-----------------|--------------|------------|----------|
| {{site.data.keyword.dv_short}} (Enterprise) |[Link](https://cloud.ibm.com/catalog/services/data-virtualization){: external} | data-virtualization | data-virtualization-enterprise |
| {{site.data.keyword.dv_short}} (Lite) |[Link](https://cloud.ibm.com/catalog/services/data-virtualization){: external} | data-virtualization | data-virtualization-lite |
{: caption="Table 1: Plans in {{site.data.keyword.dv_short}}" caption-side="top"}

## Using the catalog
{: #prov_catalog}

When you create the deployment from the catalog, you need to specify the following parameters.

1. **Service name** - The name can be any string and is the name that is used on the web and in the command line to identify the new deployment.

1. **Resource group** - If you are organizing your services into resource groups, you can specify the resource group in this field. Otherwise, you can leave it at default.

1. **Head Node** - For the Enterprise plan, you can only select the **8 Cores/32GB Memory** option. For the Lite plan, you can only select the **4 Cores/16GB Memory** option

1. **Worker Node Size** - For the Enterprise plan, you can only select the **4 Cores/32GB Memory** option. For the Lite plan, you can only select the **4 Cores/16GB Memory** option

1. **Worker Nodes** - Choose the initial number of worker nodes. You can select between 3 and 9 worker nodes if using the Enterprise Plan. If using the Lite plan, only 1 worker node will be available.

1. **Service Endpoints**  - Select the **Public** or **Private** endpoint option. Public endpoints provide a connection to your deployment on the public network and are the default selection. Private endpoints route traffic through the IBM Cloud Private network, avoiding expose to the public internet.

1. **Key Protect instance** and **disk encryption key** - If you use Key Protect, an instance and key can be selected to encrypt the deployment's disk. If you do not use your own key, the deployment automatically creates and manages its own disk encryption key.

After selecting the appropriate settings, click **Create** to start the provisioning process.

## Using the command line
{: #prov_cl}

The {{site.data.keyword.cloud_notm}} CLI tool is what you use to communicate with {{site.data.keyword.cloud_notm}} from your terminal or command line. For more information, see [Download and install {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cli-getting-started).

To create a {{site.data.keyword.databases-for}} deployment, you use the CLI to request a service instance with the service ID of the database (or messaging queue) that you want to provision.

Run the following command template:

```
ibmcloud resource service-instance-create <service-name> <service-id> <service-plan-id> <region> --service-endpoints <SERVICE_ENDPOINTS_TYPE>
```
{: codeblock}

More general information about this command is available in the CLI reference for resource groups.

When the command is run, the database deployment begins. The database takes some time to deploy. You can check on its progress on your {{site.data.keyword.cloud_notm}} dashboard or you can run the following command:

```
ibmcloud resource service-instance-create <service-name>
```
{: codeblock}

This command reports the current state of the service instance.

## Additional flags and parameters
{: #prov_flags_parms}

The `--service-endpoints` flag allows you to specify which types of service endpoints to include in your deployment. Its default is that connections to your deployment can be made from the public network. Possible values are `public`, `private`, `public-and-private`. If the flag is omitted, the default is a `public` endpoint.

The following example command specifies a service endpoint:
```
ibmcloud resource service-instance-create <service-name> --service-endpoints <endpoint-type>
```
{: codeblock}

The `service-instance-create` command supports a `-p` flag, which allows [additional parameters](#prov_add_parms) to be passed to the provisioning process. The parameters are in JSON format. One such parameter value is the Cloud Resource Name (CRN), which uniquely identifies a resource in the cloud. All parameter names and values are passed as strings.

## Provisioning through the Resource Controller API
{: #prov_rc_api}

You can provision new deployments by using the Resource Controller API. However, in order to use the Resource Controller API, you need some additional preparation.

1. Obtain an IAM token from your API token.
1. You must know the ID of the resource group to which you would like to deploy. This information is available through the {{site.data.keyword.cloud_notm}} CLI. You can find a list of resource groups with `ibmcloud resource groups` and the ID of a resource group with `ibmcloud resource group`.
1. You must know the region to which you would like to deploy.

After you have all of the information, the following create request is a `POST` to the `https://resource-controller.cloud.ibm.com/v2/resource_instances` endpoint:

```
curl -X POST \
  https://resource-controller.cloud.ibm.com/v2/resource_instances \
  -H 'Authorization: Bearer <>' \
  -H 'Content-Type: application/json' \
    -d '{
    "name": "my-instance",
    "target": "bluemix-us-south",
    "resource_group": "5g9f447903254bb58972a2f3f5a4c711",
    "resource_plan_id": "dash
  }'
```
{: codeblock}

The parameters `name`, `target`, `resource_group`, and `resource_plan_id` are all required. If needed, you can send [additional parameters](#prov_add_parms) in the request body.

More information on the Resource Controller API is found in its API Reference.

## Provisioning through Cloud Pak for Data as a Service
{: #prov_through_cpd}

Follow these steps to provision {{site.data.keyword.dv_short}} for Cloud Pak for Data as a Service.

1. If necessary, upgrade your IBM Cloud account to Pay-as-you-go. For more information, see [Upgrading your account
](https://cloud.ibm.com/docs/account?topic=account-upgrading-account).
1. From the Cloud Pak for Data as a Service console, go to **Services** > **Services catalog**.
1. Select **Watson Query** and choose a service plan.


## List of additional parameters
{: #prov_add_parms}

- `disk_encryption_key_crn` - The CRN of a [Key Protect key](docs/data-virtualization?topic=data-virtualization-key-protect-v2), which is then used for disk encryption. A Key Protect CRN is in the format `crn:v1:<...>:key:<id>`.
- `service-endpoints` - Selects the types [Service Endpoints](docs/data-virtualization?topic=data-virtualization-endpts) supported on your deployment. Options are `public`, `private`, or `public-and-private`. If omitted, the default is `public`. Note that in the CLI, `service-endpoints` is a flag, and not a parameter.
- `worker_count` - Selects the number of worker nodes.

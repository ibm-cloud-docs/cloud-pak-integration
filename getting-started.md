---

copyright:
  years: 2019, 2021
lastupdated: "2021-04-14"

keywords: getting started tutorial, getting started, Cloud Pak for Integration, integration

subcollection: cloud-pak-integration

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:external: target="_blank" .external}


# Getting started with IBM Cloud Pak for Integration
{: #getting-started}

Every enterprise in today's markets must offer robust digital products and services, often requiring integration of complex capabilities and systems to deliver one coherent whole. IBM® Cloud Pak for Integration offers a simplified solution to this integration challenge, allowing the enterprise to modernize its processes while positioning itself for future innovation. Once installed, IBM Cloud Pak for Integration eases monitoring, maintenance and upgrades, helping the enterprise stay ahead of the innovation curve.
{: shortdesc}

## What's inside this Cloud Pak
{: #whatsinside}

IBM Cloud Pak for Integration includes the following components:

- Platform UI - Design, deploy, and manage instances while easily navigating between them.
- Automation assets - Store, manage, and retrieve integration assets.
- Integration assemblies - Deploy multiple instances and components from the same YAML file in a simplified way.
- API management - Manage your APIs with API Connect.
- Integration design - Create integration flows with App Connect Designer.
- Integration dashboard - Deploy integration servers with App Connect Dashboard.
- Messaging - Get robust, reliable messaging services with MQ Advanced.
- Event Endpoint Management - Describe your application that produces events to Kafka topics as an event source, and socialize the event source details with application developers.
- Kafka cluster - Stream your Kafka events.
- Enterprise gateway - Access security, control, and a full range of additional services with DataPower® Gateway.
- High speed transfer server - Transfer files of any size quickly, reliably, and securely with Aspera® HSTS.
- IBM Cloud Pak foundational services - Access services for authentication, as well as features for managing users and user profile settings.


## Before you begin
{: #before}

This documentation applies to installing the Cloud Pak on managed Red Hat OpenShift clusters provided by {{site.data.keyword.cloud}} only. For more information about other methods of installation, see [Installing](https://www.ibm.com/docs/en/cloud-paks/cp-integration/latest?topic=installing).

Before you can install the Cloud Pak on {{site.data.keyword.cloud}}, you must set up a Red Hat OpenShift cluster using the [Red Hat OpenShift on IBM Cloud](https://cloud.ibm.com/kubernetes/catalog/openshiftcluster){: external} service.

For full details on the minimum required resources to deploy instances, see the [Compute resources for development environments](https://www.ibm.com/docs/en/cloud-paks/cp-integration/latest?topic=requirements-compute-resources-development-environments){: external} and the [Cloud Pak for Integration Readme](https://cloud.ibm.com/catalog/content/ibm-cp-integration#about){: external}.

Installation of Cloud Pak for Integration on IBM Cloud using the IBM software catalog does not support MZR clusters. See [Known limitations](#known-limitations) for more details.

## Step 1. Obtain a license
{: step1}

If you don't already have a license, you can:

- Purchase a license through [IBM Passport Advantage](https://www.ibm.com/software/passportadvantage/index.html){: external}
- [Register](https://www.ibm.com/account/reg/signup?formid=urx-46640){: external} for a 60-day trial license of IBM Cloud Pak for Integration

  **Important**: The trial is for IBM Cloud Pak for Integration software only. The trial does not include entitlement to the Red Hat OpenShift Container Platform.

## Step 2. Assign a license
{: step2}

To assign your license, follow these steps:

1. Sign up to, or log in to your [IBM Cloud account](https://cloud.ibm.com/login){: external}.
2. Navigate to **Manage > Account** and then click **Licenses and entitlements** in the navigation menu.
3. If there are no licenses to assign on the Licenses and entitlements page, click **Check IBM Passport Advantage**.
4. Select the appropriate license and click **Assign**.

## Step 3. Select your cluster
{: step3}

Open [Cloud Pak for Integration from the IBM Cloud Catalog](https://cloud.ibm.com/catalog/content/ibm-cp-integration).

Select the target OpenShift Cluster. You can filter the table by entering the name of the cluster created in the Before you Begin step in the search field.

In the Project field, select from an existing project or create a new one by entering a unique project name. A project is a Kubernetes cluster namespace, and the list is populated from your Red Hat OpenShift environment.  This project name is used as the namespace for the Platform Navigator.

## Step 4. Configure your schematics workspace
{: step4}

IBM Cloud Paks use the [Schematics](https://www.ibm.com/cloud/schematics){: external} service on {{site.data.keyword.cloud}} to automate the installation. The automation runs in a schematics workspace. A suggested name is provided for this workspace. The schematics workspace is only used during the installation process.

## Step 5. Set the deployment values
{: step5}

You must enter a value for the **csDefaultAdminPassword**.  Do not lose this value, you will need it to log into the Platform Navigator.

The password should be at least 32 characters, and can only include letters, numbers, and `-`.

## Step 6. Install
{: step6}

Check the box verifying you have read the license agreements.  Click **Install**.

The namespace you use for installation of the Platform UI should match the name you set for the project.


## Next steps
{: #next}

Once the installation completes, click **Offering Dashboard** to open the Platform UI.

You can also discover the host URL for the Platform UI with the following command.

`oc get route -n ${NAMESPACE} ${NAMESPACE}-navigator-pn -o json | jq -r .spec.host`

The full URL will then resemble "https://(project-name)-navigator-pn.(cluster-name).(region).containers.appdomain.cloud".

The Platform UI home page offers the ability to create instances.

See the full documentation in [IBM Documentation](https://www.ibm.com/docs/en/cloud-paks/cp-integration){: external}.  See **Deploying instances.**


## Known limitations
{: known-limitations}

The IBM Cloud software catalog installer for Cloud Pak for Integration does not support;
- Multi-zone region (MZR) clusters in IBM Cloud Classic infrastructure
- Clusters deployed in IBM Cloud VPC, in either single zone or multi-zone topologies

This restriction is because those environments do not natively provide the replicated File storage that is required to deploy Cloud Pak for Integration in a resilient fashion.

**Installation into MZR Classic clusters and IBM Cloud VPC is supported by manual installation of Cloud Pak for Integration** (i.e. not using the software catalog installer) which enables the user to specify your choice of replicated storage provider that has been separately made available for use in the cluster, such as Portworx. Customers wishing to manually install Cloud Pak for Integration in this way can find instructions in [IBM Documentation here](https://www.ibm.com/docs/en/cloud-paks/cp-integration/2021.1?topic=installing){: external}.


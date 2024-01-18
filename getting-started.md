---

copyright:
  years: 2019, 2024
lastupdated: "2024-01-26"

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


# Getting started with IBM Cloud Pak for Integration on IBM Cloud
{: #getting-started}

IBM Cloud Pak® for Integration is a comprehensive set of software integration tools within a single, unified experience. With this tool set, you can connect your applications, data, systems, and services, across cloud or on-premises environments, as part of a managed, scalable, and secure deployment that is based on Red Hat OpenShift. You can install Cloud Pak for Integration alongside other IBM Cloud Paks to help you quickly build and modernize applications across any cloud or IT infrastructure.
{: shortdesc}

This product guide covers the installation process and trial license for Cloud Pak for Integration on a managed Red Hat OpenShift cluster that is provided by {{site.data.keyword.cloud}}. For other information, including more information about the product and installation processes for other environments, see the full product documentation in [IBM Documentation](https://www.ibm.com/docs/en/cloud-paks/cp-integration/latest?topic=overview){: external}.


## Before you begin
{: #before}

Use this documentation only if you are installing the Cloud Pak on a managed Red Hat OpenShift cluster that is provided by {{site.data.keyword.cloud}}. If you want to install the Cloud Pak in other environments, see [Installing](https://www.ibm.com/docs/en/cloud-paks/cp-integration/latest?topic=installing) in IBM Documentation.

Before you can install the Cloud Pak on {{site.data.keyword.cloud}}, you must set up a Red Hat OpenShift cluster by using the [Red Hat OpenShift on IBM Cloud](https://cloud.ibm.com/kubernetes/catalog/openshiftcluster){: external} service.

For information about resource requirements, see [Compute resources for development environments](https://www.ibm.com/docs/en/cloud-paks/cp-integration/latest?topic=requirements-compute-resources-development-environments){: external} in IBM Documentation and the **About** tab of the Cloud Pak for Integration entry in the [IBM Cloud catalog](https://cloud.ibm.com/catalog/content/ibm-cp-integration#about){: external}.

The IBM Cloud software catalog installer does not support the installation of Cloud Pak for Integration on MZR clusters. For more information, see [Known limitations](#known-limitations).

## Step 1. Obtain a license
{: step1}

If you don't already have a license, use one of the following methods to obtain one:

- Purchase a license through [IBM Passport Advantage](https://www.ibm.com/software/passportadvantage/index.html){: external}
- [Register](https://www.ibm.com/account/reg/signup?formid=urx-46640){: external} for a 60-day trial license of IBM Cloud Pak for Integration

  > **Important**: The trial is for IBM Cloud Pak for Integration software only. The trial does not include entitlement to the Red Hat OpenShift Container Platform.

## Step 2. Assign a license
{: step2}

To assign your license, follow these steps:

1. Sign up to, or log in to, your [IBM Cloud account](https://cloud.ibm.com/login){: external}.
2. In the IBM Cloud banner, click **Manage > Account** to open the Account page. 
3. In the navigation menu, click **Licenses and entitlements** under **Account resources**.
3. If no licenses are available to assign, click **Check IBM Passport Advantage** to open the **Your licenses** dialog.
4. Select the appropriate license, then click **Assign**.

## Step 3. Configure installation settings
{: step3}

Open the **Create** tab for Cloud Pak for Integration from the [IBM Cloud Catalog](https://cloud.ibm.com/catalog/content/ibm-cp-integration). Configure the following settings:

  1. In the **Select your cluster** section, select the target Red Hat OpenShift Cluster. You can filter the table by entering the name of the Red Hat OpenShift cluster that you created earlier (see [Before you Begin](#before-you-begin)) in the search field.

  2. In the **Select a project** section, select an existing project, or create a new one by entering a unique project name. A project is a Kubernetes cluster namespace, and the list is populated from your Red Hat OpenShift environment. This project name is used as the namespace for the Platform UI.

  3. In the **Configure your workspace** section, accept the default settings. IBM Cloud Paks use a Schematics workspace to automate the installation. This workspace is used only during the installation process.

  4. In the **Set the input variables** section, set the default administrator password by updating the `csDefaultAdminPassword` parameter. Either select from an existing secret or enter a new password. Do not lose this value; you need it to log in to the Platform UI.

      The password must be at least 32 characters long and can include letters, numbers, or dashes (-).

## Step 6. Install
{: step6}

Review the information in the **Summary** pane on the right. Read and accept the Cloud Pak for Integration license agreement, then click **Install**.


## Next steps
{: #next}

After the installation completes, click **Offering Dashboard** to open the Platform UI.

You can also find the host URL for the Platform UI by running the following command:

```
oc get route -n ${NAMESPACE} ${NAMESPACE}-navigator-pn -o json | jq -r .spec.host
```

The URL has the following format:

```
https://<project-name>-navigator-pn.<cluster-name>.<region>.containers.appdomain.cloud
```

From the Platform UI home page you can view, manage, and create instances of Cloud Pak for Integration components and services. For information about deploying instances, see [Deploying instances](https://www.ibm.com/docs/en/cloud-paks/cp-integration/2023.4?topic=installing-deploying-instances){: external} in IBM Documentation.


## Known limitations
{: known-limitations}

The IBM Cloud software catalog installer for Cloud Pak for Integration does not support installation in the following environments:

- Multi-zone region (MZR) clusters in IBM Cloud Classic infrastructure
- Clusters that are deployed in IBM Cloud VPC, in either single-zone or multi-zone topologies

These environments do not provide the replicated file storage that is required to deploy Cloud Pak for Integration in a resilient way. 

You can install into these environments by following a manual installation process instead. During manual installation, you can specify appropriate storage from a replicated file storage provider such as Portworx. For more information, see [Storage considerations](https://www.ibm.com/docs/en/cloud-paks/cp-integration/latest?topic=requirements-storage-considerations){: external} in IBM Documentation.


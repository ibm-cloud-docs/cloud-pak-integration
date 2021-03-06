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
{:shortdesc}

## What's inside this Cloud Pak
{: #whatsinside}

IBM Cloud Pak for Integration includes the following components.

  - Platform Navigator - Get centralized management and control of all Cloud Pak for Integration components with this integration-specific user interface.
  - Asset Repository - Achieve accelerated development through reuse of integration assets across capabilities.
  - [Common Services](https://www.ibm.com/support/knowledgecenter/SSHKN6/kc_welcome_cs.html){: external} - Get logging, metering, monitoring and many other key foundational services with IBM Common Services, a set of private cloud platform services that provide the benefits of the public cloud from the safety of your firewall-protected data center. Entitlement to IBM Common Services is included in Cloud Pak for Integration to facilitate the transition to OpenShift.
  - [API Connect](https://www.ibm.com/support/knowledgecenter/en/SSMNED_2018/mapfiles/getting_started.html){: external} - Create, secure, manage, share and monetize APIs across clouds while you maintain continuous availability. Take control of your API ecosystem and drive digital business with a robust API strategy that can meet the changing needs of your users.
  - [App Connect Enterprise](https://www.ibm.com/support/knowledgecenter/en/SSTTDS_11.0.0/com.ibm.ace.home.doc/help_home.htm){: external} - Integrate all of your business data and applications more quickly and easily across any cloud, from the simplest SaaS application to the most complex systems — without worrying about mismatched sources, formats or standards.
  - [MQ Advanced](https://www.ibm.com/support/knowledgecenter/en/SSFKSJ_9.1.0/com.ibm.mq.helphome.v91.doc/WelcomePagev9r1.htm){: external} - Simplify, accelerate and facilitate the reliable exchange of data with a flexible and security-rich messaging solution that’s trusted by some of the world’s most successful enterprises. Ensure you receive the information you need, when you need it — and receive it only once.
  - [Event Streams](https://ibm.github.io/event-streams/){: external} - Use Apache Kafka to deliver messages more easily and reliably and to react to events in real time. Provide more personalized customer experiences by responding to events before the moment passes.
  - [DataPower Gateway](https://www.ibm.com/support/knowledgecenter/SS9H2Y_7.7.0/com.ibm.dp.doc/welcome.html){: external} - Create persistent, security-rich connections between your on-premises and cloud environments. Quickly set up and manage gateways, control access on a per-resource basis, configure TLS encryption and mutual authentication, and monitor all of your traffic.
  - [Aspera High Speed Transfer Server](https://www.ibm.com/blogs/bluemix/2018/12/enable-hybrid-cloud-data-movement-with-aspera-for-ibm-cloud-private/){: external} - Send large files and data sets virtually anywhere, reliably, and at maximum speed. Accelerate collaboration and meet the demands of complex global teams, without compromising performance or security.


## Before you begin
Before you can install the Cloud Pak on {{site.data.keyword.cloud}}, you must set up a [Red Hat OpenShift Cluster](https://cloud.ibm.com/kubernetes/catalog/openshiftcluster){: external}.

The smallest cluster size that should be created to run CP4I is 1 worker with 32 vCPUs & 128GB memory.  This will give you enough capacity to run Cloud Pak for Integration Common Services, Platform Navigator and a few small capabilities.  For full details on the minimum required resources to run capabilities, see the [Cloud Pak for Integration Readme](https://cloud.ibm.com/catalog/content/ibm-cp-integration#about){: external}.

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

## Step 4. Configure your workspace
{: step4}

Enter a name for the workspace.  A suggested name is provided.  You can change this value.

## Step 5. Set the deployment values
{: step5}

You must enter a value for the **csDefaultAdminPassword**.  Do not lose this value.

## Step 6. Install
{: step6}

Check the box verifying you have read the license agreements.  Click **Install**.

The namespace you use for installation of the Platform Navigator should match the name you set for the project.


## Next steps

Once the installation completes, click **Offering Dashboard** to open the Platform Navigator.

You can also discover the host URL for the Platform Navigator with the following command.

`oc get route -n ${NAMESPACE} ${NAMESPACE}-navigator-pn -o json | jq -r .spec.host`

The full URL will then resemble "https://(project-name)-navigator-pn.(cluster-name).(region).containers.appdomain.cloud".

The Platform Navigator home page offers the ability to create instances of the various components.

See the full documentation in [IBM Documentation](https://www.ibm.com/support/knowledgecenter/SSGT7J_20.3/welcome.html){: external}.  See **Capability deployment.**


## Known limitations
{: known-limitations}

The IBM Cloud software catalog installer for Cloud Pak for Integration does not support;
- Multi-zone region (MZR) clusters in IBM Cloud Classic infrastructure
- Clusters deployed in IBM Cloud VPC, in either single zone or multi-zone topologies

This restriction is because those environments do not natively provide the replicated File storage that is required to deploy Cloud Pak for Integration in a resilient fashion.

**Installation into MZR Classic clusters and IBM Cloud VPC is supported by manual installation of Cloud Pak for Integration** (i.e. not using the software catalog installer) which enables the user to specify your choice of replicated storage provider that has been separately made available for use in the cluster, such as Portworx. Customers wishing to manually install Cloud Pak for Integration in this way can find instructions in [IBM Documentation here](https://www.ibm.com/docs/en/cloud-paks/cp-integration/2021.1?topic=installing){:external}.


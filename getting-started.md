---

copyright:
  years: 2019
lastupdated: "2019-09-30"

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

  - Platform Navigator, a simple integrated user interface spanning components
  - Asset Repository, allows the user to store, manage, retrieve and search integration assets
  - [Cloud Private](https://www.ibm.com/support/knowledgecenter/en/SSBS6K_3.2.0/kc_welcome_containers.html){: external}, providing platform services such as logging.
  - [API Connect](https://www.ibm.com/support/knowledgecenter/en/SSMNED_2018/mapfiles/getting_started.html){: external}, implementing managed APIs
  - [App Connect Enterprise](https://www.ibm.com/support/knowledgecenter/en/SSTTDS_11.0.0/com.ibm.ace.home.doc/help_home.htm){: external}, providing integration workflows
  - [MQ Advanced](https://www.ibm.com/support/knowledgecenter/en/SSFKSJ_9.1.0/com.ibm.mq.helphome.v91.doc/WelcomePagev9r1.htm){: external}, for robust guaranteed transport
  - [Event Streams](https://ibm.github.io/event-streams/){: external}, for event handling based on Kafka
  - [DataPower Gateway](https://www.ibm.com/support/knowledgecenter/SS9H2Y_7.7.0/com.ibm.dp.doc/welcome.html){: external}, for gateway services.
  - [Aspera High Speed Transfer Server](https://www.ibm.com/blogs/bluemix/2018/12/enable-hybrid-cloud-data-movement-with-aspera-for-ibm-cloud-private/){: external}, for large file transfers


## Before you begin
Before you can install the Cloud Pak on {{site.data.keyword.cloud}}, you must set up a Red Hat OpenShift Cluster. Go to [Red Hat OpenShift Cluster](https://cloud.ibm.com/kubernetes/catalog/openshiftcluster){: external}.  You need to create a cluster.

You must purchase a license through [IBM Passport Advantage](https://www.ibm.com/software/passportadvantage/index.html){: external}. 


## Step 1. Assign a license
{: step1}

The license purchased through IBM Passport Advantage appears in the list of available entitlements. Click an entitlement block to select it.  Click **Assign**.

## Step 2. Configure your installation environment
{: step2}

Enter the identifier for the OpenShift cluster you have available in the RedHat OpenShift cluster field.

In the Project field, select from an existing project or create a new one by entering a unique project name. A project is similar to a Kubernetes cluster namespace, and the list is populated from your Red Hat OpenShift environment.  Note this project name is used as the namespace for the Platform Navigator.

## Step 3. Configure your workspace
{: step3}

Enter a name for the workspace.  A suggested name is provided.  You can change this value.

## Step 4. Run pre-installation script
{: step4}

Click **Run script**.

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

`oc get route icp-proxy -n kube-system -o jsonpath='{.spec.host}'`

The full URL will then resemble "https://icp-proxy-host/icp4i".

The Platform Navigator home page offers the ability to create instances of the various components.

See the full documentation at the [Knowledge Center](https://www.ibm.com/support/knowledgecenter/SSGT7J_19.3/welcome.html){: external}.  See **Capability deployment.**


# Understand Concepts Related to Management Agent Installation

## Introduction

This lab walks you through the key concepts that need to be understood before installing a management agent on your compute instance host as part of the set up for Java Management Service (JMS).

Estimated Time: 15 minutes

### Objectives

In this lab, you will:

* Understand important concepts in preparation for installation of Management agents on non-OCI hosts that are either on-premises or in the Cloud
* Understand important concepts in preparation for installation of Management agents on OCI Compute Instance hosts

### Prerequisites

* You have signed up for an account with Oracle Cloud Infrastructure and have received your sign-in credentials.
* You are using an Oracle Linux image on your host machine or compute instance for this workshop.
* Access to the cloud environment and resources configured in Lab 2


## Task 1: Understand Concepts Related to Management Agent Installation on non-OCI hosts

Before the set up of the Management Agent, it is important to understand the concepts behind the Java Management Service:

* **Java Management Service (JMS)**: A reporting and management infrastructure integrated with Oracle Cloud Infrastructure Platform services to observe and manage your use of Java SE (on-premises or in the Cloud). It enables you to observe and manage the use of Java in your enterprise.

* **Management Agents**: Can be installed on a host to allow a service plug-in to collect data from the host where you installed the Management Agent. In the case of JMS, the management agent allows the JMS plug-in to collect data about Java Applications, Java Runtimes and Installations from the host which can be either on-premises or in the Cloud. If you are using a **non-OCI compute instance**, we will need a **response file** to set up a Management Agent. This response file contains an **install key**.


* **Install Key**: A token required by the **Management Agent** installation. It authorises the Management Agent to communicate with the Oracle Cloud Infrastructure. You can use a single agent install key for multiple Management Agent installations.
This key has been automatically created for you in Lab 2, where the "Create New Management Agent Configuration" box was checked during Fleet creation.

  ![image of create fleet options page](/../images/create-fleet.png)

* **Response File**: For Management Agent installation to take place, a response file is also required. In Lab 2, we clicked **Download Install Key** during the creation of our fleet. The file that we downloaded is the response file which contains the install key, as observed in the `ManagementAgentInstallKey` field. The line in our response file `Service.plugin.jms.download=true` will also download and enable the JMS plugin.

  ![image of input rsp file](/../images/input-rsp-updated.png)

## Task 2: Understand Concepts Related to Management Agent Installation OCI Compute Instance hosts

Before the set up of the Management Agent, it is important to understand the concepts behind the Java Management Service:

* **Java Management Service (JMS)**: A reporting and management infrastructure integrated with Oracle Cloud Infrastructure Platform services to observe and manage your use of Java SE (on-premises or in the Cloud). It enables you to observe and manage the use of Java in your enterprise.

* **Management Agents**: Can be installed on a host to allow a service plug-in to collect data from the host where you installed the Management Agent. In the case of JMS, the management agent allows the **Java Usage Tracking service plugin** to track your use of Java.

  As part of the set up of JMS on an OCI compute instance, you will need to deploy the Management Agent. This can be deployed through the **Management Agent plugin** in the **Oracle Cloud Agent**.
    ![image of oca with management agent plugin](/../images/oca-management-agent-plugin.png)

* **Oracle Cloud Agent (OCA)**: A lightweight process that manages **OCA plugins** running on compute instances.

* **Management Agent OCA plugin**: Helps to collect data from resources such as OSs, applications, and infrastructure resources for Oracle Cloud Infrastructure services that are integrated with Management Agent. Data can include observability, log, configuration, capacity, and health data.

* **Java Usage Tracking service plugin**: A service plugin that collects data about Java Applications, Java Runtimes and Installations from the host which can be either on-premises or in the Cloud. It is important to note that this is a service plugin that is deployed as part of the Management Agent, and is different from OCA plugins.
  ![image of java usage tracking service plugin](/../images/java-usage-tracking-service-plugin.png)

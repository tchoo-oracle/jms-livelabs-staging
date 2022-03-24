# Understand Concepts Related to Management Agent Installation

## Introduction

This lab walks you through the steps to install a management agent on your compute instance host and set up tags for the agent and compute instance to allow Java usage tracking by the Java Management Service (JMS).

Estimated Time: 15 minutes

### Objectives

In this lab, you will:

* Configure a response file
* Install a management agent on a Linux / Windows compute instance host
* Verify management agent
* Configure Java Usage Tracker
* Tag Management Agent and Compute Instance
* Monitor the Java runtime(s) and Java application(s) in JMS

### Prerequisites

* You have signed up for an account with Oracle Cloud Infrastructure and have received your sign-in credentials.
* You are using an Oracle Linux image on your host machine or compute instance for this workshop.
* Access to the cloud environment and resources configured in Lab 2


## Task 1: Understand Concepts Related to Management Agent Installation

Before the set up of the Management Agent, it is important to understand the concepts behind the Java Management Service:

* **Java Management Service (JMS)**: A reporting and management infrastructure integrated with Oracle Cloud Infrastructure Platform services to observe and manage your use of Java SE (on-premises or in the Cloud). It enables you to observe and manage the use of Java in your enterprise.

* **Management Agents**: Can be installed on a host to allow a service plug-in to collect data from the host where you installed the Management Agent. In the case of JMS, the management agent allows the JMS plug-in to collect data about Java Applications, Java Runtimes and Installations from the host which can be either on-premises or in the Cloud. If you are using a **non-OCI compute instance**, we will need a **response file** to set up a Management Agent. This response file contains an **install key**. 

    >**Note**: If you are using an **OCI compute instance** and setting up your Management Agent using the Oracle Cloud Agent, the response file and install key are not required.


* **Install Key**: A token required by the **Management Agent** installation. It authorises the Management Agent to communicate with the Oracle Cloud Infrastructure. You can use a single agent install key for multiple Management Agent installations.
This key has been automatically created for you in Lab 3, where the "Create New Management Agent Configuration" box was checked during Fleet creation.

  ![image of create fleet options page](/../images/create-fleet.png)

* **Response File**: For Management Agent installation to take place, a response file is also required. In Lab 3, we clicked **Download Install Key** during the creation of our fleet. The file that we downloaded is the response file which contains the install key, as observed in the `ManagementAgentInstallKey` field. The last line of our response file `Service.plugin.jms.download=true` will also download and enable the JMS plugin.

  ![image of input rsp file](/../images/input-rsp-updated.png)


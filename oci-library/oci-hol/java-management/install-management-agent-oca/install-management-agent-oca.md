# Install Management Agent on OCI-computes - Oracle Cloud Agent (OCA)

## Introduction

This lab walks you through the steps to set up a management agent on your OCI compute instance host using the Oracle Cloud Agent to allow Java usage tracking by the Java Management Service (JMS).

Estimated Time: 15 minutes

### Objectives

In this lab, you will:

* Enable Management Agents on Compute Instances
* Deploy the JMS service plug-in on Management Agents
* Associate the management agent with your fleet

### Prerequisites

* You have signed up for an account with Oracle Cloud Infrastructure and have received your sign-in credentials.
* You are using an Oracle Linux image on your host machine or compute instance for this workshop.
* Access to the cloud environment and resources configured in Lab 2

## Task 1: Enable Management Agents on Compute Instances

1. In the Oracle Cloud Console, open the navigation menu, click **Compute**, and then click **Instances**.
Select the instance that you are interested in.

![image of console navigation to compute instances](/../images/console-navigation-jms.png)

2. Click the Oracle Cloud Agent tab. The list of plugins is displayed.

3. Toggle the Enabled switch for the Management Agent plugin.

![image of oracle cloud agent tab](/../images/check-fleet-ocid-page.png)

4. Ensure that the status of the Management Agent plugin is set to **Running**.
![image of enabled management agent plugin](/../images/check-fleet-ocid-page.png)

5. We will need to verify that our agent is enabled successfully. In the Oracle Cloud Console, open the navigation menu, click **Observability & Management**, and under **Management Agent**, click **Agents**.

![image of enabled management agent plugin](/../images/check-fleet-ocid-page.png)

6. Ensure that your agent is in the list of agents. The name of the Agent should be of the form: **Agent(<YOUR-INSTANCE-NAME>)**.


## Task 2: Deploy Java Management Service plugin


## Task 3: Associate Management Agent with your fleet



## Troubleshoot Management Agent Installation Issues using Oracle Cloud Agent

**For Task 1**
* If you are unable to download the management agent software using `wget`, you may download the software from the Oracle Cloud Console to your local machine and transfer it over to your compute using Secure Copy Protocol (SCP).

* First, open the navigation menu, click **Observability & Management**, and then click **Fleets** under **Java Management**. Select the fleet that you have created.
  ![image of console navigation to java management service](/../images/console-navigation-jms.png)

* Click **Set Up Management Agent**.
  ![image of fleet details page](/../images/fleet-details-page.png)
* Click **Download management agent software**.
  ![image of set up management agent page](/../images/fleet-set-up-management-agent.png)
* Open up a **Terminal** or **Command Prompt** window in the local machine where the management agent software file is saved.
* Enter the following command to transfer the management agent software file via scp into the remote host compute instance.

    ```
    <copy>
    scp <full_path_of_file_to_be_transferred_on_local_host> opc@<public_IP_Address>:<full_path_of_remote_directory_transferred_to>
    </copy>
    ```
  * In your compute instance, verify that the file transfer is successful by entering the following. You should see your management agent software file.
    ```
    <copy>
    ls
    </copy>
    ```

**For Task 2**

* Ensure that /usr/share folder has write permissions.
* Uninstall and reinstall the management agent after permissions for the /usr/share folder have been updated.

**For Task 3**

* Transfer the response file to /tmp folder where read permissions are allowed.

## Want to Learn More?
* Refer to the [Management Agent Concepts](https://docs.oracle.com/en-us/iaas/management-agents/doc/you-begin.html), [Installation of Management Agents](https://docs.oracle.com/en-us/iaas/management-agents/doc/install-management-agent-chapter.html) and
[JMS Plugin for Management Agents](https://docs.oracle.com/en-us/iaas/jms/doc/installing-management-agent-java-management-service.html) sections of the JMS documentation for more details.

* Use the [Troubleshooting](https://docs.oracle.com/en-us/iaas/jms/doc/troubleshooting.html#GUID-2D613C72-10F3-4905-A306-4F2673FB1CD3) chapter for explanations on how to diagnose and resolve common problems encountered when installing or using Java Management Service.

* If the problem still persists or if the problem you are facing is not listed, please refer to the [Getting Help and Contacting Support](https://docs.oracle.com/en-us/iaas/Content/GSG/Tasks/contactingsupport.htm) section or you may open a a support service request using the **Help** menu in the OCI console.

## Acknowledgements

* **Author** - Esther Neoh, Java Management Service
* **Last Updated By** - Xin Yi Tay, February 2022

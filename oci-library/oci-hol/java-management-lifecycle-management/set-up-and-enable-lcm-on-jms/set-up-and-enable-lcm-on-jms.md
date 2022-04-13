# Set up and enable Lifecycle Management operations on Java Management Service

## Introduction

Before you can start using Lifecycle Management operations, you must ensure that your Oracle Cloud Infrastructure environment is set up correctly by following [Set up Oracle Cloud Infrastructure for Java Management Service, Lab from Workshop 1](../../java-management/workshops/freetier/index.html?lab=set-up-oci-for-jms/set-up-oci-for-jms#Introduction). These OCI Resources allow the communication between all the required components and cloud services.


<em>Estimated Time:</em> 30 minutes

### Objectives

In this lab, you will:

  *  Configure an existing OCI or non-OCI host to enable LCM operations.
  *  View and identify installed Java Runtimes
  *  Understand various specifications of Java Runtimes





### Prerequisites

 * You have signed up for an account with Oracle Cloud Infrastructure and have received your sign-in credentials.
 * You are using an Oracle Linux image on your host machine or compute instance for this workshop.
 * You have successfully completed the installation of the Management Agent on your OCI or non-OCI hosts following steps in [Workshop 1: Manage Java Runtimes, Applications and Managed Instances Inventory with JMS](../../java-management/workshops/freetier/index.html?lab=understand-concepts-related-to-management-agent/understand-concepts-related-to-management-agent).

## Task 1: Configure an existing OCI or non-OCI host to enable LCM operations

After you have installed the Management Agent, follow the steps below to verify and enable LCM operations.

### **Existing OCI Compute Instance host**
If you are using an OCI compute instance and it already has the Management Agent installation using OCA and plugin deployed, then follow the steps to verify the OCA installation package version and update it, if an update is available, and enable Oracle Java Management plugin.

  1. In the Oracle Cloud console, click **Instances** under **Compute**, and select the instance that you are interested in.

  ![image of navigate from OCI console menu to computer instances](/../images/navigate-to-computer-instance.png)

  Click the **Oracle Cloud Agent** tab. The list of plugins is displayed. Verify that the **Oracle Java Management Service** OCA plugin is enabled. If it is disabled, toggle the Enabled switch for the Oracle Java Management Service plugin and ensure that the status is set to **Running**. This may take 5 to 10 minutes. Do not disturb the set up in the meantime. This will enable the LCM operations for chosen OCI Compute Instance.

  ![image of disabled oracle java management service oca plugin](/../images/oracle-jms-oca-plugin-disabled.png)

  2. Next, in the Oracle Cloud Console, open the navigation menu, click **Observability & Management**, and under **Management Agent**, click **Agents**. Select the agent you are interested in.

  ![image of console navigation to access management agent overview](/../images/management-agent-overview.png)

  In your agent, click **Deploy plug-ins**.
  ![image of agent with deploy plug-ins button](/../images/agent-deploy-plugins.png)

  Ensure that the **Java Usage Tracking** box is checked.
  ![image of checking java usage tracking box](/../images/agent-check-java-usage-tracking.png)

If you have verified that both the **Oracle Java Management Service OCA plugin** and **Java Usage Tracker service plugin** have been deployed, proceed to verify the OCA installation package version and update it.

3. Access OCI Computer Instance via SSH.

4. Check the version of the current OCA installation package.
    ```
    <copy>
    yum info oracle-cloud-agent
    </copy>
    ```
  If current version of the OCA installation package is the latest one, then no further steps are required. Else you should see output something like this:
    ![image of terminal showing how to check for available oca packages](/../images/oca-version-checking-console.png)

5. Update the OCA Installation Package.
    ```
    <copy>
    rpm -qa | grep oracle-cloud-agent

    yum update oracle-cloud-agent -y
    </copy>
    ```
    

### **Existing non-OCI Host**
If you are using a non-OCI Host and it has the Management Agent installation done following the steps in the [Workshop 1](../../java-management/workshops/freetier/index.html?lab=understand-concepts-related-to-management-agent/understand-concepts-related-to-management-agent), then you just need to make a few changes to start using LCM features.


1. Open the `/etc/sudoers` file.
    ```
    <copy>
    sudo nano /etc/sudoers
    </copy>
    ```

  Add the following lines to the end of the file:
    ```
    <copy>
    #To change ownership of the Java Management Service plugin to root
    mgmt_agent ALL=(ALL) NOPASSWD:/opt/oracle/mgmt_agent/agent_inst/bin/chown_recursive_ep.sh
    #To run the Java Management Service plugin under root user
    mgmt_agent ALL=(root) NOPASSWD: ALL
    </copy>
    ```

2. To save the file, press **CTRL+x**. Before exiting, nano will ask you if you wish to save the file: Type **y** to save and exit, type **n** to abandon your changes and exit.

3. Login to OCI Console.

4. In the Oracle Cloud Console, open the navigation menu, click **Observability & Management**, and then click **Agents** under **Management Agent**.
  ![image of console navigation to access management agent overview](/../images/management-agent-overview.png)

5. From the Agents list, select for the agent that was recently installed.
   ![image of agents main page](/../images/agents-main-page.png)

6. In order to enable LCM operations `Java Management Service` Plug-in is required to be enabled. Take note of `Service Plug-ins` field. If `Java Management Service` plug-in missing then follow the next steps, else if `Java Management Service` and `Java Usage Tracker` both plug-ins are available then you can move to the next Task.

  ![image of agent detail page](/../images/check-deploy-plug-ins.png)


7. To enable `Java Management Service` plug-in, click on **Deploy plug-ins** button.

  ![image of click on deploy plug-in button](/../images/deploy-plug-in-button.png)

8. Check `Java Management Service` option and click on Update button.
  ![image of updating the plug-in](/../images/deploy-jms-plug-in.png)

9. After 5-10 minutes, you should see the `Java Management Service` plug-in enabled under `Service Plug-ins` field.
  ![image of updated plug-in](/../images/deploy-jms-plug-in-done.png)








## Task 2: View and identify installed Java Runtimes

1. Sign in to the Oracle Cloud Console as an administrator using the credentials provided by Oracle, as described in [Signing into the Console](https://docs.oracle.com/en-us/iaas/Content/GSG/Tasks/signingin.htm).

2. In the Oracle Cloud Console, open the navigation menu, click **Observability & Management**, and then click **Fleets** under Java Management.

  ![image of oci console to navigate to fleet](/../images/oci-console-navigation-fleet.png)

3. Select the compartment created for JMS resources in [Workshop 1: Manage Java Runtimes, Applications and Managed Instances Inventory with JMS](../../java-management/workshops/freetier/index.html?lab=setup-a-fleet/setup-a-fleet). In this case, it should be Fleet_Compartment, and then click on the fleet name.

  ![image of fleet dashboard where user is instructed to select compartment and then appropriate fleet](/../images/fleet-selection-page.png)

  You will be able to view the detailed fleet page.

4. Now, click in **Java Runtimes** option under **Resources**.
  ![image of fleet page with all the fleet metrics](/../images/fleet-details-page.png)

   You will be able to see details of all the **Java Runtimes** in a table form.
  ![image of Java Runtimes table](/../images/java-runtimes-viewtable.png)


  The information available in Java Runtimes Table:
    * Version, such as 1.8.0_322
    * Name of distribution to which it belongs, such as OpenJDK Runtime Environment
    * Security state, one of: Unknown, Upgrade Required, Update Available, or Up to Date
    * Vendor, such as Oracle Corporation
    * Date and time when it was first reported
    * Date and time when it was last reported

5. If you want to learn more about the available Java Runtimes in detail, you can click on one of them.
  ![image of selection of one of the available Java RunTimes](/../images/individual-java-runtimes-details.png)

    You will be able to see a new page with details of selected Java Runtime.

    ![image of details of selected Java Runtime](/../images/java-runtime-mertics.png)

<!--
  A brief definition of various details available for **Java Runtime**:

    * **Java Runtime metrics:** Provides you with an insight into the behavior of the Java Runtime during a specified time period.  

    * **Java Runtime Installations:** The Java Runtime installations data is aggregated daily and presented in a table.

    * **Applications:** Presents a list of applications that have been started and run for more than one second during a specified time period.

    * **Managed Instances:** Presents a list of managed instances that have reported the presence of a Java installation or the start of a Java application. -->




You may now **proceed to the next lab.**

## Want to Learn More?

* Refer to the [Managing Plugins with Oracle Cloud Agent ](https://docs.oracle.com/en-us/iaas/Content/Compute/Tasks/manage-plugins.htm#console)
* Refer to the [Installation of Management Agents ](https://docs.oracle.com/en-us/iaas/management-agents/doc/install-management-agent-chapter.htm). It has details of installation of Management Agent on various Operating Systems.
* Refer to the [Viewing a Java Runtime](https://docs.oracle.com/en-us/iaas/jms/doc/fleet-views.html#GUID-F57179D9-C736-4058-B381-9ECAC776895F) for details of all the field shown in Java Runtime table.


## Acknowledgements

* **Author** - Bhuvesh Kumar, Java Management Service
* **Last Updated By** - Bhuvesh Kumar, April 2022

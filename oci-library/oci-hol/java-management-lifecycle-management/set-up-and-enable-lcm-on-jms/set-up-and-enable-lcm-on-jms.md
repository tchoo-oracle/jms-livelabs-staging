# Set up and enable Lifecycle Management operations on Java Management Service

## Introduction

Before you can use Lifecycle Management operations, you must ensure that your Oracle Cloud Infrastructure environment is set up correctly to allow the communication flow between all required components and cloud services. 


<em>Estimated Time:</em> 30 minutes

### Objectives

In this lab, you will:

  *  Configure an existing OCI or non-OCI host to enable LCM operations.
  *  View and identify installed Java Runtimes
  *  Understanding various specifications of Java Runtimes



  

### Prerequisites
 
 * You have signed up for an account with Oracle Cloud Infrastructure and have received your sign-in credentials.
 * You are using an Oracle Linux image on your host machine or compute instance for this workshop.
 * Access to the cloud environment and resources configured in [Workshop 1](../../java-management/workshops/freetier/index.html?lab=set-up-oci-for-jms/set-up-oci-for-jms).
 * You have successfully completed setup of Install Management task in [Workshop 1](../../java-management/workshops/freetier/index.html?lab=understand-concepts-related-to-management-agent/understand-concepts-related-to-management-agent) and installed Management Agent on your OCI host or non-OCI host.

## Task 1: Configure an existing OCI or non-OCI host to enable LCM operations

As mentioned in prerequisites, the Host should have setup and installed Management Agent successfully. Please complete the [Workshop 1](../../java-management/workshops/freetier/index.html?lab=understand-concepts-related-to-management-agent/understand-concepts-related-to-management-agent), if you have not finished Management Agent Installation yet. Otherwise, follow the steps below to verify and enable LCM operations.

### **Existing OCI Compute Instance host**
If you are using an OCI compute instance and it already has the Management Agent installation using OCA and plugin deployed, then you can already start using LCM features.

The below given steps will help you verify the OCA installation package version and update it, if an update is available.

1. Access OCI Computer Instance via SSH.

2. Check the version of current OCA installation package.
    ```
    <copy>
    yum info oracle-cloud-agent
    </copy>
    ```
  If current version of the OCA installation package is the latest one, then no further steps are required. Else you should see output something like this:
    ![image of terminal showing how to check for available oca packages](/../images/oca-version-checking-console.png)

3. Update the OCA Installation Package.
    ```
    <copy>
    rpm -qa | grep oracle-cloud-agent

    yum update oracle-cloud-agent -y
    </copy>
    ```

### **Existing non-OCI Host**
If you are using a non-OCI Host and it has the Management Agent installation done following the steps in the [Workshop 1](../../java-management/workshops/freetier/index.html?lab=understand-concepts-related-to-management-agent/understand-concepts-related-to-management-agent), then you just need to make a few changes to start using LCM features.

1. Uninstall the Management Agent.

    ```
    <copy>
    sudo rpm -e oracle.mgmt_agent
    </copy>
    ```

2. Edit the response file and add `Service.plugin.jm.download=true` at the bottom and then save the file. Please refer to instructions in [Understand Concepts Related to Management Agent Installation lab](../../java-management/workshops/freetier/index.html?lab=understand-concepts-related-to-management-agent/understand-concepts-related-to-management-agent) on how to create a response file.

3. Open the `/etc/sudoers` file 
    ```
    <copy>
    sudo nano /etc/sudoers
    </copy>
    ```

  Add the following to the end of the file:
    ```
    <copy>
    #To change ownership of the Java Management Service plugin to root 
    mgmt_agent ALL=(ALL) NOPASSWD:/opt/oracle/mgmt_agent/agent_inst/bin/chown_recursive_ep.sh 
    #To run the Java Management Service plugin under root user 
    mgmt_agent ALL=(root) NOPASSWD: ALL
    </copy>
    ```

    To save the file, press **CTRL+x**. Before exiting, nano will ask you if you wish to save the file: Type **y** to save and exit, type **n** to abandon your changes and exit.

4. Reinstall the Management Agent following the steps in [Install Management Agent on non-OCI Hosts - Linux  lab](../../java-management/workshops/freetier/index.html?lab=set-up-of-management-agent-linux/set-up-of-management-agent-linux).


## Task 2: View and identify installed Java Runtimes

1. Sign in to the Oracle Cloud Console as an administrator using the credentials provided by Oracle, as described in Signing into the Console. See Using the Console for more information.  

2. In the Oracle Cloud Console, open the navigation menu, click **Observability & Management**, and then click **Fleets** under Java Management.

  ![image of oci console to navigate to fleet](/../images/oci-console-navigation-fleet.png)

3. Select the compartment created for JMS resources in Workshop 1, in this case, it should be Fleet_Compartment, and then click on the fleet name.

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


  A brief definition of various details available for **Java Runtime**: 

    * **Java Runtime metrics:** Provides you with an insight into the behavior of the Java Runtime during a specified time period.  

    * **Java Runtime Installations:** The Java Runtime installations data is aggregated daily and presented in a table. 
        
    * **Applications:** Presents a list of applications that have been started and run for more than one second during a specified time period.
        
    * **Managed Instances:** Presents a list of managed instances that have reported the presence of a Java installation or the start of a Java application.




You may now **proceed to the next lab.**

## Want to Learn More?

* [Managing Plugins with Oracle Cloud Agent ](https://docs.oracle.com/en-us/iaas/Content/Compute/Tasks/manage-plugins.htm#console)
* [Install Management Agents ](https://docs.oracle.com/en-us/iaas/management-agents/doc/install-management-agent-chapter.htm)
* [Viewing a Java Runtime](https://docs.oracle.com/en-us/iaas/jms/doc/fleet-views.html#GUID-F57179D9-C736-4058-B381-9ECAC776895F)

 
## Acknowledgements

* **Author** - Bhuvesh Kumar, Java Management Service
* **Last Updated By** - Bhuvesh Kumar, April 2022

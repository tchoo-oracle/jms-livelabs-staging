# Transform your Data into Insights

![Data Science](images/ds_banner.jpg)

## Introduction

**Oracle Data Science**: Build high-quality models faster and easier. Automated machine learning capabilities rapidly examine the data and recommend the optimal data features and best algorithms. Additionally, automated machine learning tunes the model and explains the model’s results.

[](youtube:_Z5PdpdEklI)


Estimated Time: 15 minutes.

### Objectives

In this section, you will:

- Create Policies.
- Create Policies for Data Science.
- Create a Data Science Project.
- Install libraries.
- Create Jupyter Notebook environment.

### Prerequisites

- All previous sections have been successfully completed.

## Task 1: Create Policies

1. Create **Dynamic Group**, go to **Menu**, **Identity & Security** and then click **Dynamic Groups**.

> Note: If you can't see **Dynamic Groups** under **Identity & Security** section, please select **Domains**, **Default (Current domain)** and then click **Dinamycs Group**.
 
   ![](images/ds_dynamic_group_menu.png)

2. Click **Create Dynamic Group**.

   ![](images/ds_dynamic_group_create_button.png)

3. Set the following **Values**:

      - Name: `datascience`
      - Description: `Data Science Dynamic Group`
      - Rule 1 (Matching Rules):
         ```
         <copy>ALL { resource.type = 'datasciencenotebooksession' }</copy>
         ```

4. Click **Create**.

   ![](images/ds_dynamic_group_create.png)

5. The **Dynamic Group** for Data Science has been created.

   ![](images/ds_dynamic_group_review.png)

---

## Task 2: Create Policies for Data Science

1. Go to **Menu**, **Identity & Security** and then click **Policies**.

   ![](images/identity_policies_menu.png)

2. Click **Create Policy**.

   Make sure you are in the `root` compartment.

   ![](images/ds_policies_create_button.png)

3. Use the following information:

      - Name: `datascience`
      - Description: `Data Science to use network resources`
      - Policy Builder:
      - Toggle **Show manual editor**

         ```
         <copy>allow service datascience to use virtual-network-family in tenancy</copy>
         ```

         ```
         <copy>allow dynamic-group datascience to manage data-science-family in tenancy</copy>
         ```

4. Click **Create**.

   ![](images/ds_policies_create.png)

5. The **Policy** for Data Science has been created.

   ![](images/ds_policies_create_review.png)

   > Note: If you have created an **Oracle Cloud Account** to do the workshop, you are already the Administrator. You DO NOT NEED TO DO THIS STEP.
   >
   > In case you are a **Non-admin user**, you will need to set up some more policies to allow the group you belong to. Ask your administrator.
   >
   > ```
    <copy>allow group [data-scientists] to use virtual-network-family in tenancy</copy>
   ```
   >
   > ```
    <copy>allow group [data-scientists] to manage data-science-family in tenancy</copy>
   ```

---

## Task 3: Create a Data Science Project

1. Go to **Menu**, **Analytics & AI** and then click **Data Science**.

   ![](images/ds_menu.png)

2. Click **Create Project**.

   ![](images/ds_create_project_button.png)

3. Set the **Name** and **Description** as follows:

      - Name: `Nature`
      - Description: `Fish Survey notebook`

4. Click **Create**.

   ![](images/ds_create_project.png)

5. The next step is to create a **Notebook**, click **Create Notebook Session**.

   ![](images/ds_create_notebook.png)

6. Set the following **Values**:

      - Name: `Fish Survey`
      - Compute Instance Shape (but other compatible shapes would work as well): `VM.Standard.E2.2`
      - Block Storage Size: `50`
      - Networking resources > Custom networking
      - VCN: `nature`
      - Subnet: `Private Subnet-nature`

7. Click **Create**.

   ![](images/ds_create_notebook_create.png)

8. The **Status** icon will change from Creating to Active:

   ![Creating](images/datascience-creating.png)

   ![Active](images/datascience-active.png)

9. When the Notebook is active, click **Open**.

   ![](images/ds_create_notebook_open.png)

10. Log-in into your Notebook. Click **Continue** and you should be in your notebook as you are using your same OCI Web Console user. Otherwise, log in with your specific user.

   ![](images/ds_notebook_login.png)

---

## Task 4: Install Libraries

1. Welcome to your **Jupyter Notebook**. Click **Terminal**.

   ![](images/ds_notebook_terminal_launcher_new.png)

2. Type the following command:

   ```
      <copy>pip install mysql-connector-python pandas seaborn</copy>
   ```

   ![](images/ds_notebook_terminal_install.png)

3. Wait for the installation to **complete**.

---

## Task 5: Create Jupyter Notebook Environment

1. **Download** the Notebook <a href="https://objectstorage.eu-frankfurt-1.oraclecloud.com/p/accWutecVkW3_TtuapnHBzeCEGkAYiFijcU4slJLVBBZwoO00Bxicgreqs1mBFGQ/n/fruktknlrefu/b/workshop-marine-life/o/mds-di-ds-FishSurvey.ipynb" target="\_blank">here</a>.

2. Click **Upload files**.

   ![](images/ds_notebook_upload.png)

3. **Select** `mds-di-ds-FishSurvey.ipynb` from your disk. Wait for the upload to **complete**.

4. Your `mds-di-ds-FishSurvey.ipynb` will be **loaded** on the side panel.

   ![](images/ds_notebook_fish_notebook.png)

5. **Double click** on **mds-di-ds-FishSurvey.ipynb**.

6. Make sure you **modify** `PRIVATE_IP` and **passwd** on the following code in the **Notebook** with the **Private IP and Password from MySQL Database Service**.

   ```
   cnx = mysql.connector.connect(
      host="PRIVATE_IP",
      user="root",
      passwd="<your_password>",
      database="nature"
   )
   ```

   ![](images/ds_notebook_fish_notebook_run.png)

7. **Select** the first paragraph (called Cell) with all the `import` statements in the Notebook and run the **Notebook** cell by cell by clicking the **Play** icon over and over until you reach the end.

   ![](images/ds_notebook_fish_notebook_head.png)

8. Check the **plot** where you can see the population of fish by water depth.

   ![](images/ds_notebook_fish_notebook_plot.png)

Congratulations! Well done!

Continue to the Next Steps for more information!

---

## **Acknowledgements**

- **Author** - Victor Martin, Technology Product Strategy Director
- **Contributors** - Priscila Iruela
- **Last Updated By/Date** - Priscila Iruela, April 2022
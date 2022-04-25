# Create an App from a Spreadsheet

## Introduction

In this lab, you will learn how to create an APEX App on top of data imported from a spreadsheet. To simplify the lab, you will use sample data that's built into APEX. However, the sequence will be the same when uploading your own data.

Now that you are logged into your workspace, you can start creating APEX applications. In this lab, you will build a simple application based on a spreadsheet. Keep in mind that APEX is great for a variety of apps, from simple ones like this to large, sophisticated apps based on local database objects, REST enabled SQL objects, and even REST APIs.

While APEX developers spend the majority of their time in the App Builder, you should also investigate the SQL Workshop, where you can create and maintain database objects, Team Development, where you can track large APEX development projects, and the App Gallery, which contains numerous productivity and sample apps that can be installed within minutes.

## Task 1: Loading project and tasks data  

1.  From your APEX workspace home page, click **App Builder**. Sign in to your account if prompted.
2.  Click **Create a New App**.

    ![](images/create-a-new-app.png " ")

3.  Click **From a File**.

    ![](images/from-a-file.png " ")

    When creating an application from a file, APEX allows you to upload CSV, XLSX, XML, or JSON files, and then build apps based on their data. Alternatively, you can also copy and paste CSV data or load sample data.

4.  Within the Load Data wizard, click the **Copy and Paste** option at the top.

    ![](images/copy-paste.png " ")

5. Select **Project and Tasks** from the sample data set list and then click **Next**.

    ![](images/copy-paste-projects-tasks.png " ")

6.  Review the parsed data. Set Table Name to **PROJECT_TASKS** and click **Load Data**.

    ![](images/new-table-name.png " ")

    After clicking **Load Data**, you will see a spinner until the wizard finishes loading the data. Continue to STEP 2 at that point.

## Task 2: Creating an application

The Data Load wizard has created a new table and populated that table with the records from the sample data. Now you can create an app based on this new table.

1.  In the Load Data dialog, verify that 73 rows have been loaded into the **PROJECT_TASKS** table, then click **View Table**.

    ![](images/continue-to-view-object.png " ")

[//]: # (click **Create Application**. )
[//]: # (images/continue-to-create-application-wizard.png " ")

[//]: # (Remove Steps 2 and 3)
2. In the Object Browser, review the table structure.   
    In the Table toolbar, click **Create App**.

    ![](images/object-browser.png " ")

3. On the Create Application page, click **Create App**.

2. In the Create Applicatin page, review the pages listed. Click the **Edit** button for a page to review more details.

    Click **Check All** for Features, and then click **Create Application**.

    ![](images/name-for-application.png " ")
    ![](images/create-application.png " ")

    When the wizard finishes creating the application, you will be redirected to the application's home page in the App Builder.

## Task 3: Running and exploring the new app

1.  Click **Run Application**. This will open the runtime application in a new browser tab, allowing you to see how end users will view the app.

    ![](images/run-application.png " ")

2.  Enter your user credentials and click **Sign In**.

    *Note: Use the same Username and Password you used to sign into the APEX Workspace.*

    ![](images/sign-in.png " ")

3.  Explore the application a little. Click **Dashboard** (in the home menu or the navigation menu) to view the charts created. Click **Project Tasks Search**, in the navigation menu, to play with the faceted search. Click **Project Tasks Report** to view an interactive report, then click the edit icon for a record to display the details in an editable Project Task "form" page. Next, navigate to the **Calendar** page and review the data displayed (*Note: You may need to scroll back several months to see data, only May 2020 - December 2020 has data*). Finally, review features available under **Administration**.

    ![](images/new-app.png " ")


## **Summary**

This completes Lab 2. You now know how to create an application from a spreadsheet by either dragging and dropping a file or loading sample data for training purposes. [Click here to navigate to Lab 3](?lab=lab-3-improve-faceted-search)


## Learn More / Troubleshooting: How to change a page's name
If you want to change a page's name after you create an application, the process is involved. Here are the instructions on how you can change a page's name.

1. In *App Builder*, click you Project. In you Project home page, click the page you want to edit. In *Page Designer*, change **Identification > Name** and **Identification > Title** to the new name. Click **Save and Run Page**. In the runtime environment, you will see the tab's name is updated.

    ![](../../../common/change-page-name/images/change_name.png " ")

2. In your Project home page, click **Shared Component** in the development toolbar.
    ![](../../../common/change-page-name/images/shared_component.png " ")

    In Shared Component home page, under **Navigation**, click **Breadcrumbs**. Click **Breadcrumbs** again, click the page you want to edit.
    ![](../../../common/change-page-name/images/shared_component_menu.png " ")

    Change **Entry > Short Name** to the new name. Click **Apply Changes**. In the runtime environment, you will see the title of the page is updated.
    ![](../../../common/change-page-name/images/breadcrumb.png " ")

3. In Shared Component home page, under **Navigation**, click **Navigation Menu**, click **Desktop Nagivation Menu**. Click the page you want to edit, change **Entry > List Entry Label** to the new name. Click **Apply Changes**. You will see the page's name is updated on the left navigation menu.

    ![](../../../common/change-page-name/images/navigation_menu.png " ")

4. In Shared Component home page, under **Navigation**, click **Lists**, then click **Page Navigation**. Click the page you want to edit, change **Entry > List Entry Label** to the new name. Click **Apply Changes**. You will see the page's name is updated in the Home page of you application.

    ![](../../../common/change-page-name/images/page_navigation.png " ")


## **Acknowledgements**

 - **Author** -  David Peake, Consulting Member of Technical Staff 
 - **Last Updated By/Date** - Arabella Yao, Product Manager Intern, Database Mangement, July 2020


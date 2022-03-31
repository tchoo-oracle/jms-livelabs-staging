# Lab 2: Create and Validate an RDF Graph User in Graph Studio

## Introduction
In this demo, we will create and validate an RDF Graph User in Graph Studio.

Estimated Time: 30 minutes

### Objectives
- Create a Graph User to Access RDF in Graph Studio
- Enable RDF for the Graph User
- Create RDF Graph in Graph Studio
- Validate the RDF Graph
- Execute SPARQL Queries on the Playground Page

### Prerequisites
This lab assumes you have:
- An Oracle Free Tier or Paid Cloud Account
- You have completed:
  - Lab 1: Get Started with RDF

## **Task 1:** Create a graph user to access RDF in Graph Studio

In order to work with RDF Graphs in Graph Studio, you must create graph users with granted roles. You can create Graph users with the correct set of roles and privileges using Oracle Database Actions.

Navigate to your Autonomous Database instance and create a graph user by following the steps below or as explained in [Create a Graph User](https://docs.oracle.com/en/cloud/paas/autonomous-database/csgru/create-graph-user.html)

1. Navigate to your Autonomous Database and click on your database display name to view its details.

  ![The Oracle Cloud Autonomous Database screen highlighting the database actions button](./images/autonomous-database.png "")

2. Open up **Database Actions** from the toolbar.

  ![The Oracle Cloud Autonomous Database screen showing the Autonomous Database for Graph Studio.](./images/adb-details.png "")

3. From the Database Actions Launchpad, click **Database Users** from **Administration**.

  ![The screen of the database actions launchpad, highlighting the database users page under administration](./images/database-actions-launchpad.png "")

4. Click **Create User** on the Database Users Page in the **All Users** area.

  ![The database users page highlighting the 'create user' button](./images/database-users.png "")

5. Enter a user name and password. Make sure your password is greater than 12 characters, contains an uppercase letter, a lowercase letter, and a number. *Your password cannot contain special characters.*

  *Write down or save your username and password as this will be needed in a later exercise.*

  ![The create user page showing the create a username and password section, an unlimited quota on tablespace DATA, and enabled graph and web access features](./images/create-user.png "")

6. Enable **Graph**

7. Enable **Web Access** and expand Web Access Advanced Features, make sure authorization is required, your user name is the same as your REST Alias, and the URL Mapping Type is BASE_PATH.

8. Set the **Quota on Tablespace DATA** to Unlimited.

9. Click **Create User**.

You should now be able to see your created user in the **All Users** section of the **Database Users** page or when you search for your user.

  ![The database users page showing the created database user accessible under 'all users'](./images/graph-user-created.png "")

## **Task 2:** Enable RDF for the graph user

You can enable RDF for the newly created graph user by performing the following steps:

1. In the Database Actions Launchpad, open up **SQL** from the **Development Section**.

  ![The database actions launchpad highlighting SQL under the 'development' section](./images/database-actions-launchpad-2.png "")

2. In SQL, select your graph-user name from the dropdown menu in the Navigator column.

  ![The database actions SQL page highlighting the 'Navigator' tab and selected user from the dropdown menu](./images/sql-workspace.png "")

3. Execute the following SQL statements in the SQL worksheet by copying the statement into the worksheet and running it with the green play button.
In the following code, <graph-user> is the user schema to which you are logged into using Database Actions. Replace <graph-user> with the graph-user name you selected in the Navigator column.

    ```
    <copy>CREATE TABLE <graph-user>.ADB_GRAPH_SETTINGS$ (
    key VARCHAR2(255) NOT NULL,
    value VARCHAR2(255) NOT NULL,
    CONSTRAINT adb_graph_settings_pk PRIMARY KEY(key));
    INSERT INTO <graph-user>.ADB_GRAPH_SETTINGS$ VALUES ('RDF_ENABLED', 'true');</copy>
    ```

    If the record already exists with a 'false' value, then you can update the record as shown.

    ```
    <copy>UPDATE <graph-user>.ADB_GRAPH_SETTINGS$ set value = 'true' where key = 'RDF_ENABLED';</copy>
    ```

    The Script Output should look like this:

    ```
    Table <graph-user>.ADB_GRAPH_SETTINGS$ created.
    Elapsed: 00:00:00.036
    ```

  ![Successful execution of SQL query resulting in the creation of a user's ADB_GRAPH_SETTINGS table](./images/sql-graph-user-settings.png "")

## **Task 3:** Create RDF graph in Graph Studio

Before we can create an RDF graph we must first import RDF data into Graph Studio.

1. Navigate to your Autonomous Database in the Oracle Cloud Infrastructure Console and open Tools.

  ![Autonomous Database details showing the link to Graph Studio, accessible under 'Tools'](./images/database-tools.png "")

2. Open Graph Studio and log in with the user name and password you created in Lab 2, Task 1, Step 5.

3. Click on Graphs on the navigation menu from the left to navigate the Graphs page.

  ![The 'get started' page for Graph Studio. On the left-hand navigation bar, the button for 'Graphs' is highlighted](./images/graph-studio-home.png "")

4. In the Graph Type dropdown menu select RDF and then click the Create button on the top-right corner of the interface.

  ![The Graph Studio page graph type dropdown menu displays PG and RDF graph options](./images/graph-studio-graphs.png "")

5. Create RDF Graph Wizard opens as shown:

  ![The 'create RDF graph' page.](./images/create-rdf-graph.png "")

6. Enter the OCI Object Storage URI path to the RDF file in your OCI bucket.
    The format should be similar to:

    ```
    https://objectstorage.us-ashburn-1.oraclecloud.com/n/ogcs/b/rdfdata_bucket/o/moviestream_rdf.nt
    ```

7. Click **Create Credential**.

8. Enter **Credential Name**.

9. Enter **OCI User Name**.

10. Enter your **Auth Token**.

11. Click **Next**.
    The follow dialog should appear, enter "MOVIESTREAM" for Graph Name:

  ![The 'create RDF graph' second page](./images/create-rdf-graph-2.png "")

12. Click **Create**.

    The RDF graph creation job will be initiated. Since the RDF file contains 139461 records, the process may take 3 to 4 minutes. You can monitor the job on the **Jobs** page in Graph Studio.

  ![The 'jobs' page of Graph Studio displays a job 'Create a RDF Graph - MOVIESTREAM' still in progress](./images/graph-studio-jobs.png "")

    When succeeded, the status will change from pending to succeeded and Logs can be viewed by clicking on the three dots on the right side of the job row and selecting **See Log**. The log for the job displays details as shown below:

    ```
    Tue, Mar 1, 2022 08:21:04 AM
    Finished execution of task Graph Creation - MOVIESTREAM.

    Tue, Mar 1, 2022 08:21:04 AM
    Graph MOVIESTREAM created successfully

    Tue, Mar 1, 2022 08:21:04 AM
    Optimizer Statistics Gathered successfully

    Tue, Mar 1, 2022 08:20:50 AM
    External table <graph-user>_TAB_EXTERNAL dropped successfully

    Tue, Mar 1, 2022 08:20:49 AM
    Data successfully bulk loaded from ORACLE_ORARDF_STGTAB

    Tue, Mar 1, 2022 08:20:39 AM
    Model MOVIESTREAM created successfully

    Tue, Mar 1, 2022 08:20:37 AM
    Network RDF_NETWORK created successfully

    Tue, Mar 1, 2022 08:20:24 AM
    Data loaded into the staging table ORACLE_ORARDF_STGTAB from <graph-user>_TAB_EXTERNAL

    Tue, Mar 1, 2022 08:20:19 AM
    External table <graph-user>_TAB_EXTERNAL created successfully

    Tue, Mar 1, 2022 08:20:19 AM
    Using the Credential MOVIES_CREDENTIALS

    Tue, Mar 1, 2022 08:20:19 AM
    Started execution of task Graph Creation - MOVIESTREAM.
    ```

## **Task 4:** Validate the RDF graph

You can explore and validate the newly created RDF graph on the **Graphs** page in Graph Studio as shown:

1. Navigate to the **Graphs** page and set the **Graph Type** to RDF using the dropdown menu. Select the MOVIESTREAM graph row from the available RDF graphs, sample statements (triples or quads should appear), use the three horizontal dots to resize these statements and bring them into view. Sample statements (triples or quads) from the RDF Graph are displayed on the bottom panel as shown:

  ![Sample statements from the RDF graph 'MOVIESTREAM' are displayed in triplets](./images/graph-sample-statements.png "")

2. After selecting the MOVIESTREAM Graph, scroll to the bottom of the page and verify that you see 500 rows of RDF triples have been retrieved.

  ![Sample statements from the MOVIESTREAM RDF graph](./images/sample-statements.png "")

## **Task 5:** Execute SPARQL queries on the playground page

You can execute SPARQL Queries on the RDF Graph from the **Query Playground** page.

1. On the **Graphs** page select the **RDF** from the Graph Type dropdown menu and click the **Query** button to navigate to the Query Playground page.

  ![Graphs page with RDF graph type selected and the query button highlighted](./images/graph-type.png "")

2. If you have multiple graphs in graph studio, you will have to choose the graph to query. In the Graph Name menu, select the MOVIESTREAM from the dropdown menu.

  ![Query playground displays the graph name 'MOVIESTREAM' selected from the dropdown menu](./images/query-playground.png "")

3. Execute the following query for the RDF Graph.

   ```
   <copy>
    PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX ms: <http://www.example.com/moviestream/>

    SELECT DISTINCT ?gname
    WHERE {
        ?movie ms:actor/ms:name "Keanu Reeves" ;
            ms:genre/ms:genreName ?gname .
    }
    ORDER BY ASC(?gname)
    </copy>
    ```

When the query is executed successfully the query output will be displayed as shown:

  ![Query playground displays the successful execution of a query on the MOVIESTREAM RDF graph and displays query results](./images/query-playground-script.png "")

## Acknowledgements

- **Author** - Melliyal Annamalai, Product Manager, Oracle Spatial and Graph
- **Contributor** - Malia German, Solution Engineer, Santa Monica Specialist Hub
- **Last Updated By/Date** - Malia German, Santa Monica Specialist Hub, March 2021

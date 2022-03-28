#Predict On Time Delivery

## Introduction

This lab walks you through the steps to understand on-time delivery analysis through visualizations that blend data from distribution centers, logistics and shipping.

Estimated Time: XXXX

### Objectives

In this lab, we will be taking a deeper look into On-Time Delivery by channel to understand why some channels have lower on-time delivery rates than the other.

We will be utilizing Oracle Analytics Server's ability to pull cross-functional data together from different lines business and to report on it in a single place.

This lab will also utilize Oracle Analytic Server's machine learning capabilities to predict future delivery rates.

In this lab, you will:

* View Dashboard and Analyze On-Time Delivery KPIs
* Utilize One-Click Explain to view Computer Generated Insights
* Create a Combination Bar and Line Chart
* Create a Bar Chart to view On Time Delivery by Channel
* Create a Visual Map Layer to view States with the highest Ship Late Quantities
* Create Pie Chart to view Late Shipment Distributions by Channel
* Create a Horizontal Bar chart to view Ship Late Percentage by Product Name
* Create a Pivot Table to view Ship Late Percentage by Channel Product Name
* Build a Machine Learning Model to Predict On-Time Delivery


### Prerequisites

This lab assumes you have:

* An Oracle account
* All previous labs successfully completed
* Access to a data visualization instance





## **Task 1**: Utilizing One-Click Explain

  Lets drill into visibility to on-time delivery performance from the various nodes across our distribution network — perhaps we can uncover some insights into why some of our distribution channels are low.

  1. **Navigate back to the main dashboard** and locate the KPI card that displays **'On-Time Delivery by Channel'**.

  ![main dashboard](images/headcount-card.png)

  We can see that Direct Channel is the lowest, and is performing below the other distribution channels on Time Delivery. Let's create a self-service visualization canvas to look deeper into on-time delivery to understand why this may be occuring.

  In this task, we will be demonstrating how to utilize **Oracle One Click Explain**. With One-Click Explain, data analysts can quickly leverage ML scripts to profile selected data elements and illustrate basic key insights and relationships.


  2. **Select** the plus symbol to open an empty canvas so we can build out our visualizations.

  ![empty canvas](images/empty-dashboard-red-box.png)

  3. **Rename** the canvas by tapping the arrow, and hitting 'rename'. Rename the canvas to **'On Time Delivery Analysis'**

  ![rename canvas](images/rename-canvas.png)

  Now that we have an empty canvas, we can begin to get a better understanding of On-time delivery statistics. Now is a great time to activate One-Click explain to get a snapshot of On-Time Delivery.

  4. **Navigate** to the visualizations menu and select **"Supply Chain Underlying Dashboard Data"**

  ![open visualizations menu](images/view-supply-chain-data.png)

  5. **Right Click** the variable **'On Time Delivery'** and select **'Explain On Time Delivery'**

  ![one click explain on time delivery](images/explain-on-time-delivery.png)

  6. Oracle Machine Learning will now traverse all of the relevant relationships and display **Basic Facts**, **Anomalies**, and not pictured here, **Segments**, and **Key Drivers**.

  ![one click explain output](images/explain-on-time-delivery-display.png)

  ![one click explain further output](images/explain-on-time-delivery-display-two.png)

  These insights are machine generated in real time. Here we can see which states, dates, months, shipping modes and product names bring in late results that way we can begin investigating.

  You can also select the visualization, then click 'add selected' and immediately begin to use Data Visualizations project editor to customize to drill further.

  ![add to canvas](images/explain-display-add-to-canvas.png)

  Now that we've taken a high level view of On-Time delivery as a starting point, let's start creating some of our own visuals to get a deeper look at what is affecting on-time delivery.


## **Task 2**: Create a Combination Bar and Line Chart
Now we can start building our self-service visualization canvas that breaks down on-time delivery statistics.


  1. View the empty canvas named **'On Time Delivery Analysis'** Let's begin creating our first visual.

  ![view empty canvas](images/empty-dashboard-two.png)


  2. **Navigate** to the visualizations menu on the left side of the screen and expand the files named **"Supply Chain Underlying Dashboard Data"** and **"Underlying Dashboard Data 5"**

  ![view visualizations menu](images/visual-data-one.png)

  3. Under **"Supply Chain Underlying Dashboard Data"** click and drag **Ordered Quantity** to the canvas.  

  ![drag value to canvas](images/order-quantity-tile.png)


  4. **Click to View Visualization Types** and select **'combo'**

  ![select combo graph](images/choose-combo-graph.png)


  5. Now expand 'date' under **"Supply Chain Underlying Dashboard Data"**. **Click and Drag** the variable **'Quarter'** to the **'X-Axis'**.

  ![add quarter](images/quarter-in-visual.png)

  6. Now **Click and Drag** the variable **'Quarter'** to the **Filters** tab. Filter to display all quarters except for '<NULL>', 'Q1 2019', and 'Q3 2021'. This will remove the quarters that are not as important to us.

  ![add filter](images/add-filter.png)

  7. **Navigate** to the file named **"Underlying Dashboard Data 5"** and click and drag **'On-Time Delivery'** into the **'Y-Axis'**.

  ![drag variables to canvas](images/combo-visual-before-change.png)

  8. **Format** the visual by right clicking on **'Ordered Quantity'** and selecting **Bar** and right clicking on **'On Time Delivery'** and selecting **Line**

  ![format visual](images/combo-visual-select-bar.png)

  You should now have a combination bar and line chart that represents order quantities compared to on-time delivery rate.

  ![combination bar chart](images/combination-line-and-bar.png)

  9. Now, let's change the color assignments for this visual. **Right Click** on the visual on canvas, and hover over **'color'** and select **'manage assignments'**.

  ![change color assignments](images/change-combo-color.png)


  10. **Scroll Down** to find **'On Time Delivery'** variable.

  ![find on time delivery](images/find-variable-color-combo.png)


  11. **Change the Color** assignment of 'On Time Delivery' to **green**.

  ![change color assignment to green](images/combo-change-color-green.png)


  You have now successfully created a combination bar and line graph to compare order quantity and on time delivery quantity by quarter.

  ![created combo bar chart](images/combo-visualization-complete.png)

  Here we see the green on-time delivery trendline has been steadily declining over the last few quarters.


## **Task 3**: Create a Bar Chart to view On-Time Delivery by Channel

  Now, let's create a bar chart to view On Time Delivery quantity by Channel

  1. **Navigate** to **"Supply Chain Underlying Dashboard Data"**. Hold Ctrl/Cmmnd and Select **'On Time Delivery'** and **'Channel'**. Then right click the highlighted variables and select **'Pick Visualization...'**

  ![pick visualization from options](images/create-bar-chart-visual.png)

  2. **Select** the option **'Bar Chart'** from the visualization types.

  ![select bar chart](images/select-bar-chart.png)

  ![bar chart on canvas](images/create-bar-chart.png)

  3. **Navigate** to **"Supply Chain Underlying Dashboard Data"** and drag **'Channel'** into **'Filters'** on the bottom of the visualization tool pane.

  ![channel into filter](images/channel-filter.png)

  4. Select **'DC'**, **'Distributor'**, and **'Supplier'** as the only channels to display on this bar chart.

  ![select channels](images/filters-selected-bar-chart.png)

  You have now successfully created a bar chart to visualize On-Time Delivery by Channel.

  ![created bar chart](images/bar-chart-viz-complete.png)

## **Task 4**: Create a Visual Map Layer to View Late Shipment Areas

  Now, let's create a Visual Map Layer to view Ship Late Quantity by State.

  1. **Navigate** to **"Supply Chain Underlying Dashboard Data"**. Hold Ctrl/Cmmnd and Select **'State'** and **'Ship Late Quantity'**. Then right click the highlighted variables and select **'Pick Visualization...'**

  ![pick new visualization](images/pick-visual-map.png)

  2. **Select 'Map'** from the visualization types.

  ![select map](images/pick-map-type.png)

  ![map created](images/map-on-canvas.png)

  3. **Click and drag** the visualization to the **right** of the On-Time Delivery Bar Chart.

  ![map created](images/map-on-canvas-copy.png)

  ![drag visualization](images/map-view-complete.png)

  We can see the PENNSYLVANIA Distribution Center has the highest late delivery percentage—accounting for 70% of all the late deliveries.

  You have now successfully created a map layer to visualize ship late quantities by state.

## **Task 5**: Create a Pie Chart to View Late Shipment Distributions

  Now, let's create a Pie Chart to view late shipment distributions by delivery channel.

  1. **Navigate** to **"Underlying Dashboard Data 5"**. Hold Ctrl/Cmmnd and Select **'Channel'** and **'Ship Late Quantity'**. Then right click the highlighted variables and select **'Pick Visualization...'**

  ![pick new visualization](images/variable-pick-pie.png)

  2. **Select 'Pie'** from the visualization types.

  ![Pie chart](images/pick-pie-visualization.png)

  ![pie chart on canvas](images/pie-chart-complete.png)

  You have now successfully created a pie chart to visualize ship late quantities by channel.

## **Task 6**: Create a Horizontal Bar Chart to View Ship Late Percentage

  Now, let's create a Horizontal Bar Chart to look at which products have the greatest Ship Late Percentage.

  Let's first create a custom calculation to represent 'Ship Late Percentage'

  1. **Scroll Down** to the bottom of the visualizations menu and locate the **'My Calculations'** folder. **Right Click** that folder and select **'Add Calculation'**

  ![Add calculation](images/add-calculation.png)

  2. **Rename** the calculation to **'Ship Late Percentage'**

  ![ship late percentage](images/rename-calc.png)

  3. In the field, begin typing **'Ship Late Quantity'** and select the variable that is located in **"Supply Chain Underlying Dashboard Data"**.

  ![select ship late quantity](images/ship-late-quantity-calc.png)

  4. Now, add the division opperand '/'. In the field, begin typing **'Ordered Quantity'** and select the variable that is located in **"Supply Chain Underlying Dashboard Data"**. Here we are Dividing Ship Late Quantity by Order Quantity.

  ![select ordered quantity](images/ordered-quantity-calc.png)

  5. **Click 'Validate'** to run the script and check for errors. Then **Press Save** to exit.

  ![validate](images/create-calculation-formula.png)

  6. **Navigate** to **'My Calculations'**. Hold Ctrl/Cmmnd and Select **'Ship Late Percentage'** and **'Product Name'** from **"Underlying Dashboard Data 5"**. Then right click the highlighted variables and select **'Pick Visualization...'**

  ![pick new visualization](images/select-horizontal-bar.png)

  7. **Select 'Horizontal Bar'** from the visualization types.

  ![select horizontal bar](images/select-horizontal-bar-menu.png)

  ![horizontal bar on canvas](images/horizontal-bar-unformatted.png)

  8. Now, **drag 'Ship Late Percentage'** into the **'color' pane** to adjust the color based on Ship Late Percentage.

  ![ship late in color pane](images/color-ship-late.png)

  9. Now, let's sort the graph based on highest ship late Percentage. **Right Click** the horizontal bar graph, hover over **'Sort by'** and then hover over **'Ship Late Percentage'**.

  ![sort horizontal](images/sort-horizontal.png)

  10. Then click from **'High to Low'** to complete the sort.

  ![sort high to low](images/sort-horizontal-done.png)

  ![sort complete](images/horizontal-bar-done.png)

  We can clearly see from the horizontal bar graph that Fries have the largest ship late percentage.

  You have now successfully created a horizontal bar chart to visualize ship late percentage by product.

## **Task 7**: Create a Pivot Table to View Ship Late Percentage by Channel & Product Name

  Now, let's create a Pivot Table to view ship late percentage by delivery channel as well as product.

  1. **Navigate** to **'My Calculations'**. Hold Ctrl/Cmmnd and Select **'Ship Late Percentage'** and **'Product Name'** + **'Channel'** from **"Underlying Dashboard Data 5"**. Then right click the highlighted variables and select **'Pick Visualization...'**

  ![pick new visualization pivot](images/select-variables-pivot.png)

  2. **Select 'Pivot'** from the visualization types.

  ![select pivot table](images/pivot-pick-tool.png)

  ![pivot table on file](images/pivot-on-canvas.png)

  3. **Drag 'Product Name'** to **'Rows'** section so we can view ship late percentage by product via each distribution center.

  ![ship late percentage by product](images/channel-product-same-row.png)

  4. **Drag 'Ship Late Percentage'** to **'Color'** section to view ship late percentage by color.

  ![ship late to color](images/pivot-with-color.png)

  5. Now **Tap the down arrow** on the **'Ship Late Percentage'** column to **sort from highest to lowest** ship late percentage.

  ![ship late sort highest to lowest](images/sort-pivot.png)

  ![ship late sort complete](images/pivot-complete.png)

  You have now successfully created a pivot table to visualize ship late quantities by product and channel.

  We can see Fries have the highest late shipping - this is not a good sign given that we know Potato French Fries are one of the most popular items on the menu. We need to meet with the Direct Channel, Pennsylvania, to work out an improvement strategy regarding Fries. Let’s navigate back to the main dashboard to continue our analysis.

## **Task 8**: Build a Machine Learning Model to Predict On-Time Delivery

  Now that we have completed our drill downs, let's build a machine learning model to better predict on time delivery percentage.

  Oracle Analytics built in predictive models use several embedded machine learning algorithms to mine your datasets, predict a target value, or identify classes of records. Use the data flow editor to create, train, and apply predictive models to your data. You can also register and use Oracle machine learning models from Oracle Database or Oracle Autonomous Data Warehouse to score data in Oracle Analytics.

  Data flows enable you to organize and integrate your data to produce curated datasets that your users can visualize. To build a data flow, you add steps. Each step performs a specific function, for example, add data, join tables, merge columns, transform data, apply model, save your data.

  Let's use the data flow editor to configure a predictive machine learning model.

  1. Download the dataset **"bobbysburgerdataset.csv"** - This dataset contains the historical data that OAS can use to create a machine learning model with.

  2. **Navigate** to the Oracle Analytics Server home page.

  ![view homepage](images/introp.png)

  3. **Tap the menu** item in the top right corner, then press **Create Data Flow**

  ![tap menu create dataflow](images/home-screen-create-df.png)

  4. **Upload the dataset** named **"bobbysburgerdataset.csv"** into the DataFlow Editor then **unselect** variables **'Date'** and **'Year'**.

  ![create data set](images/create-dataset-df.png)

  ![drop data file](images/input-dataset-df.png)

  ![add data](images/dataset-inputted.png)

  ![add data](images/unselect-date.png)

  ![add data](images/unselect-year.png)

  5. **Click the plus icon** and select the option **'Train Numeric Prediction'**

  ![select numeric prediction](images/train-numeric.png)

  6. Select **'Linear Regression for model training'** then press 'okay'

  ![select CART algorithm](images/select-lrm-alg.png)

  7. Choose the **Target column** to be **'On Time Delivery'**

  ![select target](images/select-target.png)

  ![pick target variable](images/select-target-two.png)

  8. Save the model as **'Bobbys Burgers LRM ML Model'** and press the **play button** in the top right corner. Name the DataFlow **'Bobbys Burgers LRM ML Model DF'**

  ![save model](images/move-save-model.png)

  ![name model](images/save-df.png)

  9. Navigate back to the Oracle Analytics Server home page. Tap the menu in the top left corner, and tap **'Machine Learning'**

  ![navigate to homepage](images/main-screen-menu.png)

  10. Hover over the model named **'Bobbys Burgers LRM ML Model'** and tap **inspect**

  ![find model](images/locate-model.png)

  ![inspect model](images/inspect-model.png)

  11. Here we can view the **Quality, details, and outputs**. Navigate to **Click on Quality** - We see that the Coefficient of Determination or R^2 is 43% showing us this model has a decent fit.

  ![view general details](images/view-details.png)

  ![view model quality](images/view-quality.png)


  Now, let's apply the model we just built.

  12. Download the dataset **"bobbyscustomerdataset.csv"**

  13. **Navigate** to the Oracle Analytics Server home page.

  ![oracle analytics home page](images/oas-home.png)

  14. **Tap the menu** item in the top right corner, then press **Create Data Flow**

  ![create data flow](images/home-screen-create-df.png)

  15. Upload the dataset **"bobbyscustomerdataset.csv"** into the DataFlow

  ![create dataset](images/create-dataset-df.png)

  ![drag in dataset](images/input-dataset-df.png)

  ![add dataset](images/add-customer-data.png)

  16. Tap the **Plus Icon** and select **'Apply Model'**

  ![apply model](images/apply-model.png)

  17. Select the model **'Bobbys Burgers LRM ML Model'**

  ![select the model](images/select-created-model.png)

  18. Rename the PredictedValue to **'Predicted On Time Delivery'**. Scroll down and tap **'Select a column'** and then tap **'QTR'** to make the necessary mapping.

  ![rename output](images/update-predicted-value.png)

  ![map one column](images/select-qtr.png)

  19. Tap the **plus icon** and select **'Save Data'**

  ![save data](images/save-data-output.png)

  20. Save the outputted dataset as **'bobbysburgersMLoutputdata'** and press **'Play'** to run the DataFlow. Save the dataflow as **'bobbysburgersMLoutputDF'**

  ![outputted dataset from ML](images/save-ml-output.png)

  21. **Navigate Back to Home** and select the menu icon in the top left, and Select **'Data'**

  ![Navigate to home](images/view-data.png)

  22. Locate the saved dataset **'bobbysburgerMLoutputdata'** and right click select **'Create Project'**

  ![locate dataset](images/ml-output.png)

  ![create project from dataset](images/create-project.png)

  23. Hold Ctrl/Command and select **'Predicted On Time Delivery'**, **'Channel'**, **'Product Name'**, **'State'** and select **'Bar'**. Add **'State'** to Trellis Rows, **'Predicted On Time Delivery'** to **'Y Values'**, **'Channel'** to **'X Axis'**, and **'Product Name'** to **'Color'**. This will display the predictions for On Time Delivery from our model.

  ![select variable](images/ml-project-bar.png)

  ![select bar chart](images/select-bar.png)

  ![view Ml output visual](images/ml-visualization-incomplete.png)


  24. Now let's filter out our unwanted values. **Click and Drag** the **'Channel'** variable to the **'Filter'** section. Select all the channels except for '<NULL>'

  ![select variable](images/ml-channel-filter.png)

  ![select bar chart](images/ml-select-channel-filter.png)


  25. Now let's truncate some values so we can clearly see the differences by product. **Select** the visual and tap the **'Grid Line' icon** on the bottom left menu.

  ![select grid line icon](images/click-gridline.png)

  26. Expand the **'Value Axis'** and scroll down to **'Start'**. Set this value to 50 and press enter. This only shows us values from 50 and beyond.

  ![set start value to 50](images/final-viz.png)

  27. Now let's sort our view. **Right Click** on 'Predicted On Time Delivery' and hover over 'Sort By'. Then select **Low to High** to view products with the lowest on time delivery percentages first.

  ![right click predicted on time delivery](images/final-viz-two.png)

  ![hover over sort by](images/final-viz-three.png)

  ![select low to high sort](images/final-viz-four.png)

  Here we can see a distribution of the centers, states, and products and which are predicted to have the lowest ship ontime delivery percentages. This is especially useful if management wants to catch products that have lower on-time ship quantities resulting in more late shipments.

  We have now successfully created a machine learning model and applied it's results to our project.

  **This concludes the lab**

## Learn More

* [Read More About Oracle Analytics Predictive Models and Oracle Machine Learning Models](https://docs.oracle.com/en/middleware/bi/analytics-server/user-oas/use-oracle-analytics-predictive-models-and-oracle-machine-learning-models.html)

## Acknowledgements
* **Authors** - Killian Lynch, Nagwang Gyamtso, Luke Wheless, Akash Dharamshi, Solution Engineer Specialist Hub Team, NA Technology
* **Contributors** -  Akash Dharamshi, Solution Engineer Specialist Hub Team, NA Technology
* **Last Updated By/Date** - Akash Dharamshi, Solution Engineer Specialist Hub Team, NA Technology, March 2022

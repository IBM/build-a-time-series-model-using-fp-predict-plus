# How to build time series model using FP Predict Plus operator hosted on Red Hat Marketplace

Time series analysis includes methods for analyzing time series data in order to extract meaningful statistics and other characteristics of the data. Time series allows you to analyze major patterns related to trends, seasonality, cyclicity, and irregularity. Wiht time-series forecasting, you can use a model to predict future values based on previously observed values. Time series are widely used for non-stationary data, like economic, weather, stock price, and retail sales.

This tutorial demonstrates how to quickly build a time-series model using the FP Predict Plus operator using a dataset that shows the how the prices differ over a period of time at a paricular retail store outlet.

## Learning objectives

* Use the FP Predict + Operator from Red Hat Marketplace
* Set up a time-series model on FP Predict +
* Learn how to configure the training and forecast parameters
* View and analyze the time-series results

## Prerequisites

To complete the steps in this tutorial, you need to install the FP Predict + operator from Red Hat Marketplace. Please refer to the tutorial [Get started with Findability Predict Plus on Red Hat Marketplace](https://developer.ibm.com/tutorials/get-started-findability-platform-predict-plus-red-hat-marketplace/) for instructions.

## Estimated time

Completing this tutorial should take about 40 minutes.

## Steps to build the time series model

### Step 1. Create a new time-series job

1. Log in to your FP Predict + Operator instance.

    ![](doc/src/images/login.png)

1. Click on `+ Start` button

    ![](doc/src/images/start_button.png)

1. A prompt will pop up asking if your data contains a time stamp. Select **Yes**.

    ![](doc/src/images/create_job.png)

1. Another prompt will pop up asking if you will be predicting values. Select **Yes**.

    ![](doc/src/images/predict_prompt.png)

### Step 2. Configure the time-series model

1. To configure the time-series model for this tutorial, we created two sample CSV files for you to work with. You will need to download them before you can start.

    * Download the dataset [train.csv](https://github.com/IBM/build-a-time-series-model-using-fp-predict-plus/blob/main/datasets/train.csv)
    * Download the dataset [test.csv](https://github.com/IBM/build-a-time-series-model-using-fp-predict-plus/blob/main/datasets/test.csv)

1. Enter the details as follows:

  1. For Job Name, enter `TS`. (Avoid special characters in the name)
  2. Set the Dataset location to be `local`.
  3. For Daily Interval, set as `Daily`.
  4. For Tasks, select `Model + Forecast`.
  5. For the training file, upload the file from the downloaded `train.csv`. file.
  6. Set the Target Variable as `item_price`.

      ![](doc/src/images/training_config.png)

  7. Upload the forecast file from the downloaded file `sales_test.csv`.
  8. Set the Timestamp variable as `date`.
  9. Set the Timestamp Format as `dd/mm/yyyy`.
  10. Select `Run`.
  
  ![](doc/src/images/forecast_config.png)
  
**Note: It will take about 10 minutes to set up the model, please wait and don't refresh the page until it's over.**

### Step 3. Analyze your output

After the model is set up completely, you will receive an output like the graph below that shows the time-series of prices over the time period 2013 to 2015:

    ![](doc/src/images/output.png)

Select the **Analytics** icon to analyze your results.

  ![](doc/src/images/analytics_icon.png)
  
  #### Analysis description
  
  1. The first table on the top left corner depicts the actual vs. predicted time intervals and the difference in prediction for each time interval. Note that it provides only the head values of the result table.
  2. The graph on the top right represents the same output as received on the dashboard.
  3. The `Modeling Metrics` and `Forecast Metrics` provides measures of the trained model using techniques such as Mean Error, Root Mean Square, Mean Percentage Error, Mean Absolute Percentage Error ,and Mean Absolute Scaled Error. These measures allow you to evaluate how well the underlying model is trained and how well it forecasts.
  4. The log table provides metadata of the trained file, such as the number of rows and the time it takes to train.
  5. The last table is about the `Important Rows` since ours is a time-series model with only one underlying feature distribution.

  ![](doc/src/images/analyze_results.png)

  ![](doc/src/images/analyze_results_2.png)
  
## Important pointers on the datasets 

* There should only be 2 other columns apart from the date &mdash; Row sequence number and Target Variable.
* Ensure the time interval is correctly maintained through the training and forecast data. For exmaple, if you set the time interval as "daily", your dataset **must** contain only one record for a particular day.
* Additionally, if your interval is set to "daily", your forecast data **must** have a forecast for every day without a gap.

If you encounter the following error, clear your browser cache or try in another browser.
  
  ![](doc/src/images/Error.png)
  
For further reference, look at the datasets used in this tutorial.
  

## Summary

In summary, this tutorial helps you to understand how to perform time-series analysis with Red Hat Market Place using the FP Predict + Operator.

## Related links

* [Predict fraud using FP Predict Plus](https://developer.ibm.com/patterns/predict-fraudulent-transactions-findability-platform-predict-plus/)
* [Predict sales using FP Predict Plus](https://developer.ibm.com/patterns/use-redhat-marketplace-operator-fp-predict-plus-to-predict-sales/)


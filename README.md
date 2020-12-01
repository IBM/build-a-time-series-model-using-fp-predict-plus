---
#Front matter (metadata).
abstract:             Time-Series Model using FP Predict +   # REQUIRED

authors:                # REQUIRED - Note: can be one or more
  - name: Smruthi Raj Mohan
    email: smrraj32@in.ibm.com
    
  - name: Manjula G Hosurmath
    email: mhosurma@in.ibm.com

completed_date:         # REQUIRED - Note: date format is YYYY-MM-DD

components:
# For a full list of options see https://github.ibm.com/IBMCode/Definitions/blob/master/components.yml
# Use the "slug" value found at the link above to include it in this content.
# Example (remove the # to uncomment):
 # - "aix"

draft: true|false       # REQUIRED

excerpt:                # REQUIRED

keywords:               Time-Series, RHM, FPPredict +# REQUIRED - comma separated list

last_updated:           # REQUIRED - Note: date format is YYYY-MM-DD

primary_tag:         Data Science  # REQUIRED - Note: Choose only only one primary tag. Multiple primary tags will result in automation failure. Additional non-primary tags can be added below.

pta:                    # REQUIRED - Note: can be only one
# For a full list of options see https://github.ibm.com/IBMCode/Definitions/blob/master/primary-technology-area.yml
# Use the "slug" value found at the link above to include it in this content.
# Example (remove the # to uncomment):
 # - "cloud, container, and infrastructure"

pwg:                    # REQUIRED - Note: can be one or many
# For a full list of options see https://github.ibm.com/IBMCode/Definitions/blob/master/portfolio-working-group.yml
# Use the "slug" value found at the link above to include it in this content.
# Example (remove the # to uncomment):
# - "containers"

related_content:        # OPTIONAL - Note: zero or more related content
  - type: announcements|articles|blogs|patterns|series|tutorials|videos
    slug:

related_links:           # OPTIONAL - Note: zero or more related links
  - title:
    url:
    description:

runtimes:               # OPTIONAL - Note: Select runtimes from the complete set of runtimes below. Do not create new runtimes. Only use runtimes specifically in use by your content.
# For a full list of options see https://github.ibm.com/IBMCode/Definitions/blob/master/runtimes.yml
# Use the "slug" value found at the link above to include it in this content.
# Example (remove the # to uncomment):
 # - "asp.net 5"

series:                 # OPTIONAL
 - type:
   slug:

services:               # OPTIONAL - Note: please select services from the complete set of services below. Do not create new services. Only use services specifically in use by your content.
# For a full list of options see https://github.ibm.com/IBMCode/Definitions/blob/master/services.yml
# Use the "slug" value found at the link above to include it in this content.
# Example (remove the # to uncomment):
# - "blockchain"

subtitle:               # REQUIRED

tags:
# Please select tags from the complete set of tags below. Do not create new tags. Only use tags specifically targeted for your content. If your content could match all tags (for example cloud, hybrid, and on-prem) then do not tag it with those tags. Less is more.
# For a full list of options see https://github.ibm.com/IBMCode/Definitions/blob/master/tags.yml
# Use the "slug" value found at the link above to include it in this content.
# Example (remove the # to uncomment):
 # - "blockchain"

title:                  # REQUIRED

translators:             # OPTIONAL - Note: can be one or more
  - name:
    email:

type: tutorial|howto    # REQUIRED

---


This tutorial demonstrates a time-series on FP Predict +, Using a dataset that shows the how the prices differ over a period of time at a paricular retail store outlet.

## Learning objectives

* Users will learn how to operate with RHM FP Predict + Operator
* Setup a Time-Series Model on FP Predict + 
* Learn how to configure the Training and Forecast parameters
* View and analyze the time-series results

## Prerequisites

List pre-reqs here.

* RHM FP Predict + operator

## Estimated time

Completing this tutorial should take about 20 minutes.

## Steps

### Create a new Time-Series Job

* Login to your FP Predict + Operator

![](doc/src/images/login.png)

* Click on `+ Start` button

![](doc/src/images/start_button.png)

* A prompt will pop-up asking if your data contains Time-Stamp. Select `Yes`.

![](doc/src/images/create_job.png)

* Another prompt will pop-up asking if you will be predicting values. Select `Yes`.

![](doc/src/images/predict_prompt.png)

### Configure the Time-Series Model

* Download the dataset [train.csv](https://github.ibm.com/smrraj32/fppredict-plus-time-series/blob/master/dataset/train.csv)

* Download the dataset [test.csv](https://github.ibm.com/smrraj32/fppredict-plus-time-series/blob/master/dataset/sales_test.csv)

* Enter the details as follows-

  * Enter `Job Name` as `TS` (Pls avoid special characters in the name)
  * Dataset location must be `local`
  * Daily Interval set as `Daily`
  * Tasks `Model + Forecast`
  * Upload training file from the downloaded file `train.csv`
  * Set Target Variable as `item_price`
  
  ![](doc/src/images/training_config.png)

  * Upload the forecast file from the downloaded file `sales_test.csv`
  * Set Timestamp variable as `date`
  * Set Timestamp Format as `dd/mm/yyyy`
  * Click on `Run`
  
  ![](doc/src/images/forecast_config.png)
  
*** Note: It will take about 10 minutes to setup the model, pls wait and don't refresh the page until it's over ****  

### Analyze your Output

After the completion you will receive an output as given below-

  ![](doc/src/images/output.png)

The above graph shows the time-series of prices over the time period 2013 to 2015.

Click on the `analytics` icon to analyze your results

  ![](doc/src/images/analytics_icon.png)
  
  #### Analysis Description
  
  1. The first table on the top left corner, depcits the actual v/s predicted and the difference in prediction for each time        interval. Note that it provides only the head values of the result table
  2. The graph on the top right represents the same output as received on the dashboard
  3. The `Modeling Metrics` and `Forecast Metrics` provides measures of the trained model using techniques such as Mean            Error, Root Mean Square,Mean Percentage Error, Mean Absolute Percentage Error and Mean Absolute Scaled Error. These will      allow us to evaluate how well the underlying model is trained and forecasts.
  4. Log table provides metadata of the trained file, such as the number of rows and time taken to train.
  5. The last table is about the `Important Rows` since ours is a time-series model with only one underlying feature       
     distribution.

  ![](doc/src/images/analyze_results.png)

  ![](doc/src/images/analyze_results_2.png)
  
## Troubleshooting


* Must have only 2 other columns apart from the date - Row sequence number and Target Variable
* Ensure the time interval is correctly maintained through the training and forecast data. Eg: If you put the time interval     as Daily, your dataset MUST contain only one record for a particular day.
* Additionally, if you set Daily as interval, your forecast data MUST have a forecast for everyday without a gap.
* If you encounter the below error-
  
  ![](doc/src/images/Error.png)
  
  Clear your browser cache or try in another browser.

For further reference, look at the datasets used in this tutorial.
  

## Summary

In summary, this tutorial helps you to understand how to perform time-series analysis with Red Hat Market Place using the FP Predict + Operator.


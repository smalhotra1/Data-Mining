Open Close Sanitation Requests Vs Public Health Indicators
=========================================================

Overall Goal
------------
Our overall goal is to combine two data sets, Open and Closed Sanitation Requests & Public Health Indicators, and combine the data sets after cleaning (See output of running Main for what our dataset should look like.)
Using this dataset, we can run create a data model based on _closed Sanitation requests_ and predict how long a request will take to complete based on other attributes such as community name, percentage of people living in poverty, etc. Using this model we can then begin to test the model on open requests in the Chicago area and explore whether there are some neighborhoods which are neglected more than others, or whether there is any correlation between communities and their requests.

Preliminary Steps
-----------------
~~- _Remove Duplicate Request IDs_: As of the moment we found that there are Duplicate Requests ID's. Having Done Some research, we found the meta data does not have any information as to why supposedly different requests are actually different. To solve this issue, we must remove any duplicate request IDs, because our dataset contains 10,000+ rows, it should not affect our dataset, but we must not that this was a judgement call.~~
~~- _Remove Empty Rows_: there are rows in the dataset which are missing crucial data for our analysis, to cope with this the step-1 rapid miner process should remove any rows which are missing data.~~
~~- _Discretize Nature of code Violation_: the data set has several different types of code violations, but they are awkwardly named, we must rename these attributes to something which is more self-descriptive.~~
~~- _Save All Open Sanitation Requests into its own excel file_: We will be using this dataset as our test dataset once we have our data model. Our Open Sanitation Requests Model should look fairly similar to the data set for the closed Sanitation Requests *after* it has been joined to the heath indicators dataset.~~
~~- _Compute the Duration of all Closed Sanitation Requests_: Generate An attribute which is the duration of how long it takes to complete a requests as a new attribute.~~
~~- _Transpose the Violation Types into their own columns as attributes_: We will have to make each type of violation its own column so that we can aggregate the count of each request by community ID~~
~~- _Aggregate Requests by Community ID_: We will then have to make a rapid miner process which will aggregate the dataset by community ID so that it looks like this:~~

| Community ID 	| Garbage in Alley Reqs 	| Garbage in Alley Req Duration 	| ...And so on... 	|
|--------------	|-----------------------	|-------------------------------	|-----------------	|
| ...          	| ...                   	| ...                           	| ...             	|
| ...          	| ...                   	| ...                           	| ...             	|
| ...          	| ...                   	| ...                           	| ...             	|

~~- _Discretize Duration_: The decision tree, which we are trying to build, requires **Nominal Attributes** to work. Thus because our dataset uses numeric for Days, we need to Discretize the duration columns into bins. So for example in the above table, we would say (1-3 days) instead of 2 days.~~
- _**See Subsection on 'Tangent'**_: At this stage we would be ready to run our first correlation on this dataset. We wanna build association rules based on the current dataset to see if there are corrections between the current attributes we have right now. **This should be its own separate rapid Miner Process**
~~- _Join Dataset to Public Health Indicators Dataset on Community ID_: We now have to join the resulting dataset from the previous step to the public health Indicators dataset. We will be joining the dataset on an attribute called 'Community ID' **This should be its own RapidMiner Process**~~
- _Create a Rapid Miner Process which will generate a Decision Tree Model based on the resulting Dataset_: We will have to generate a decision tree based on **Nominal Attributes** to create Model based on Attributes. This model should be tested on our completed datasets because we already know when they were closed. We preferable will use the performance attributes or cross validation.
- _Apply the Model_: We now have to apply the model on the Open Requests. **Remember: our Open Requests Dataset must also be joined to the Public Heath Indicators in order for the model to work. See the section on TODOs for open dataset**.

Preparing Open Requests Datasets for running it through the model as a test dataset
==========================================================
In order for us to be able use our model on the open Requests to see how good our dataset is, our dataset must be cleaned similarly to hour our closed dataset was processed. This includes:
- _Discretize Nature of code Violation_
- _Compute the Duration of all Open Sanitation Requests_
- _Transpose the Violation Types into their own columns as attributes_
- _Aggregate Requests by Community ID_
- _Discretize Duration_
- _Join Dataset to Public Health Indicators Dataset on Community ID_


First Tangent: Correlation / Association Rules for Open/Closed Sanitation Requests
===================================================
At this point in the project, we must have a dataset which has aggregated the dataset and cleaned it. At this point, we an create a rapid miner process that will find association rules between the attributes we have in the table right now. Seeing how closely related attributes are with each other will help us also decide whether our data shows that some associations make sense, such as how longer days of completion are related to harder jobs like construction Site cleanliness. This should be its own process.

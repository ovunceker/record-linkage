# Overview

Here I want to explain what we have done. First of all, the main goal of this project is to find the linkage between three data sets using full pipeline of data science. Let me first give the links where one can obtain the data sets.

*Data Set A:* https://catalog.data.gov/dataset/medicare-physician-other-practitioners-by-provider-and-service-b156e

*Data Set B:* https://openpaymentsdata.cms.gov/datasets/download

*Data Set C:* https://data.cms.gov/provider-characteristics/medicare-provider-supplier-enrollment/medicare-fee-for-service-public-provider-enrollment/data

*Data Set C+:* https://data.cms.gov/sites/default/files/2025-10/PPEF_Practice_Location_Extract_2025.10.01.csv 

Here data set C+ includes some additional information about data set C. It will be joined with data set C at the pre-processing step. 

## Pre-Processing
Pre-processing part of this project was done in R. We first started pre-processing by sampling the data. Original three files is over 12GB. That's why we took random 1 million rows from each data sets. Next we dropped some unnecessary columns and chage the names of some columns. Later we did brief exploratory analysis on over data sets. We realized that the three common columns that are almost never empty are first/last names and state. That's why those three columns are the main columns for our blocking methods. Then we split the 1 million rows into training and testing data sets. Training sets inlude 700k rows and testing sets include 300k rows.

## Blocking
Rest of this project is done on Python. We first uploaded the 6 training and test data sets we obtained at R script. Then we started by applying blocking methods. The idea behind the blocking methods are very smart. There are 700k rows on each training data sets. Keep in mind that we will train the model using pairs coming from each of these different data sets. That means to compare data set A and B we would have to consider $700000^2$, so there are 490 billion pairs. We cannot consider all of them that's why we have to put some constraints on the pairs. We considered only two blocking methods in this project. One was exact blocking and the other was sorted neigborhood blocking. 



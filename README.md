# Palmora-PowerBI-Analysis
Detailed Documentation on my analysis on DSA Palmora Capstone Project
## Overview
This repository contains an Exploratory Data Analysis (EDA) performed on [Palmora Group HR Analysis]. The analysis was conducted using PowerBI.
## EDA Steps
1. [Data Import](#Data-Import)
2. [Data Cleaning and Transformation](#Data-Cleaning-and-Transformation)
3. [Descriptive Statistics](#Descriptive-Statistics)
4. [Data Visualisation](#Data-Visualisation)
5. [Insights and Conclusions](Insights-and-Conclusions)

### Data Import
I launched PowerBI Desktop. After launching, I clicked on home,get data, Ichose the data source as excel and clicked 'connect'. I selected the dataset 'Palmora Group Emp-Data' and loaded it into PowerBI. I did the same for the CSV file 'Palmora Group Bonus Rules_083311'. I did the same for the dataset 'Bonus Mapping'.
### Data Cleaning and Transformation
After the data was fully loaded, I transformed the data (took it to the mechanic's workshop) by using the Power Query Editor through the following steps:
    a. I filtered the rows to remove duplicate datasets (names of employees)
    b. I added a conditional column with the heading as 'Region' to split all the complany locations, namely; South West, North West and North Central and I reorded the new conditional column and placed it beside the locaion clomun.
    c. I filtered the department and salary columns to remove all 'Nulls' from the dataset.
    d. I added two other conditional columns namely 'Salary Band' and 'Rating sort'.
    e. I ensured that the datatype is exactly the same with the type of data in each column.
After all these steps, I clicked on 'Apply & Close' and loaded the data completely into PowerBI.
### Descriptive Statistics

    

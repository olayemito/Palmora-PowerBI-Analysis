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
I used the modellling tab to create new measures for key statistics:
    - Gender Count: 'Gender Count = COUNT('Palmoria Group emp-data_083200'[Gender])'

    - Employees Below Minimum Salary: 'Employees Below Minimum Salary = COUNTROWS(FILTER('Palmoria Group emp-data_083200', 
    'Palmoria Group emp-data_083200'[Salary] < 90000))'

    - Gender Percentage: 'Gender Percentage = DIVIDE(CALCULATE(COUNT('Palmoria Group emp-data_083200'[Gender])),
    CALCULATE(COUNT('Palmoria Group emp-data_083200'[Gender]), ALL('Palmoria Group emp-data_083200'[Gender])))' 
    
    - Amount as Bonus: 'Amount as Bonus = SUMX('Palmoria Group emp-data_083200', 
    'Palmoria Group emp-data_083200'[Salary] * SWITCH('Palmoria Group emp-data_083200'[Rating], 
    "Very Poor", LOOKUPVALUE('bonus mapping'[Very Poor],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department]), 
    "Poor", LOOKUPVALUE('bonus mapping'[Poor],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department]), 
    "Average", LOOKUPVALUE('bonus mapping'[Average],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department]), 
    "Good", LOOKUPVALUE('bonus mapping'[Good],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department]), 
    "Very Good", LOOKUPVALUE('bonus mapping'[Very Good],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department])
    ,0))'

    - New Salary: 'New Salary = SUMX('Palmoria Group emp-data_083200','Palmoria Group emp-data_083200'[Salary] + 'Palmoria Group emp-data_083200'[Amount as Bonus])'
I tested all the measures above by visualising them in cards and a table to ensure they worked.

### Data Visualisation
In this stage, I started to visualise all my already transformed data through the use of charts:
    

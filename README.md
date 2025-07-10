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
 I filtered the rows to remove duplicate datasets (names of employees).
I added a conditional column with the heading as 'Region' to split all the complany locations, namely; South West, North West and North Central and I reorded the new conditional column and placed it beside the locaion clomun.
3. I filtered the department and salary columns to remove all 'Nulls' from the dataset.
    d. I inserted a generic gender (female) to all employees that did not reveal their gender.
    e. I added two other conditional columns namely 'Salary Band' and 'Rating sort'.
    f. I ensured that the datatype is exactly the same with the type of data in each column.
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
a. **Gender Distribution:** For this, I used pie chart and column charts as well as cards and a slicer to visualise this dataset.
b. **Insights on Ratings based on Gender:** I used a clustered column chart to visualise this.
c. **Company’s Salary Structure:** I used a clustered column chart to visualise the salary structure based on gender by region and department and a stacked bar chart to visualise the average salary by gender. I used a slicer to be able to visualise based on gender.
d. **Minimum Salary Requirement:** I used a card to view the number of emloyees that are paid below the minimum salary of $90,0000 and I used a stacked bar chart to visualise the number of employee by salary band ($10,000 - $20,000, $20,000 - $30,000 and so on) and the number of employees below the minimum salary payment. I used a slicer to be able to visualise this by regions.
e. **Bonus Payment and New Salary based on Performance:** I used a tablt to visualise the bonus and new salary (bonus + fromer salary) to be paid to each employee based on the perforance, rating and department of each emolyee. I used a stacked column chart to visualise the total amount of the new salary to be paid to all employee based on regions and a card to view the total amount to be paid company-wide to all employees.

### Insights and Conclusions
Based on the data analysed and visualised, I found out that gender distribution of the company is almost evenly distributed with males making 49.26% of the total population and females 50.74% , this shows that the news headlines were wrong about Palomora's bias against females and females dominate based on the data analysed.
Although Palmora does well in the gender department, most employees are average on the ratings possibly due to current working conditions and this can be improved possibly by having an inclusive training session across all regions. 
Palmora does not meet the minimum payment requirement based on the new regulation for manufacturing companies, based in the data analysed, females are more affected than males in this area. This should also be looked into and wokrked upon. 
Lastly, The salary for the South West region should be increased as they are the least paid across all regions even after the bonus and new salary has been implemented.

Below is the file of the analysis named [Download Palmora Data Analysis](Palmora-PowerBI-Analysis/Palmora-Data-Analysis.pbix)

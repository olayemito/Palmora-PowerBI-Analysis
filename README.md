# Palmora-PowerBI-Analysis
Comprehensive Documentation of My Analysis for the DSA Palmora Capstone Project

## Overview
This repository presents an Exploratory Data Analysis (EDA) conducted on the [Palmora Group HR Analysis] dataset using Power BI.

## EDA Steps
1. [Data Import](#data-import)
2. [Data Cleaning and Transformation](#data-cleaning-and-transformation)
3. [Descriptive Statistics](#descriptive-statistics)
4. [Data Visualization](#data-visualization)
5. [Insights and Conclusions](#insights-and-conclusions)

### Data Import
I opened Power BI Desktop and initiated the data import process by selecting "Get Data" from the home menu. I chose Excel as the data source and clicked 'Connect'. After selecting the dataset 'Palmora Group Emp-Data', I loaded it into Power BI. I repeated this process for the CSV file 'Palmora Group Bonus Rules_083311'.

### Data Cleaning and Transformation
Once the data was fully loaded, I used the Power Query Editor to transform it through the following steps:
- Removed duplicate entries based on employee names.
- Created a conditional column titled 'Region' to categorize all company locations into South West, North West, and North Central, placing this new column adjacent to the location column.
- Filtered out 'Null' values from the department and salary columns.
- Assigned a generic gender (female) to employees who did not disclose their gender.
- Added two additional conditional columns: 'Salary Band' and 'Rating Sort'.
- Verified that the data types matched the content of each column.

After completing these steps, I clicked 'Apply & Close' to fully load the data into Power BI.

### Descriptive Statistics
In the modeling tab, I created new measures for key statistics:
- **Gender Count**: `Gender Count = COUNT('Palmoria Group emp-data_083200'[Gender])`
- **Employees Below Minimum Salary**: `Employees Below Minimum Salary = COUNTROWS(FILTER('Palmoria Group emp-data_083200', 'Palmoria Group emp-data_083200'[Salary] < 90000))`
- **Gender Percentage**: `Gender Percentage = DIVIDE(CALCULATE(COUNT('Palmoria Group emp-data_083200'[Gender])), CALCULATE(COUNT('Palmoria Group emp-data_083200'[Gender]), ALL('Palmoria Group emp-data_083200'[Gender])))`
- **Amount as Bonus**: `Amount as Bonus = SUMX('Palmoria Group emp-data_083200', 'Palmoria Group emp-data_083200'[Salary] * SWITCH('Palmoria Group emp-data_083200'[Rating], "Very Poor", LOOKUPVALUE('bonus mapping'[Very Poor],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department]), "Poor", LOOKUPVALUE('bonus mapping'[Poor],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department]), "Average", LOOKUPVALUE('bonus mapping'[Average],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department]), "Good", LOOKUPVALUE('bonus mapping'[Good],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department]), "Very Good", LOOKUPVALUE('bonus mapping'[Very Good],'bonus mapping'[Department],'Palmoria Group emp-data_083200'[Department]), 0))`
- **New Salary**: `New Salary = SUMX('Palmoria Group emp-data_083200','Palmoria Group emp-data_083200'[Salary] + 'Palmoria Group emp-data_083200'[Amount as Bonus])`

I verified the accuracy of these measures by visualizing them using cards and tables.

### Data Visualization
In this phase, I visualized the transformed data using various charts:
- **Gender Distribution**: I employed pie charts, column charts, cards, and slicers for this analysis.
- **Insights on Ratings by Gender**: A clustered column chart was used for this visualization.
- **Company Salary Structure**: I utilized a clustered column chart to display the salary structure by gender and region, along with a stacked bar chart for average salary visualization. Slicers were implemented for gender-based filtering.
- **Minimum Salary Requirement**: I used a card to show the count of employees earning below the minimum salary of $90,000, complemented by a stacked bar chart for salary band distribution. Slicers were applied for regional filtering.
- **Bonus Payment and New Salary Based on Performance**: I created a table to visualize bonuses and new salaries (original salary + bonus) per employee, along with a stacked column chart for total new salary amounts by region and a card for company-wide totals.

### Insights and Conclusions
The analysis revealed that the gender distribution within the company is nearly balanced, with males representing 49.26% and females 50.74%. This contradicts the narratives about gender bias at Palmora, suggesting that females actually hold a slight majority.

While Palmora performs well regarding gender representation, most employees received average performance ratings, likely due to current working conditions. Enhancing workplace inclusivity through training sessions across all regions could improve this.

Additionally, the company does not comply with the new minimum payment requirements for manufacturing firms. The data indicates that females are disproportionately affected in this regard, warranting immediate attention.

Lastly, salaries in the South West region should be increased, as they are the lowest across all regions, even after accounting for bonuses and new salary adjustments.

You can download the analysis file named Palmora Data Analysis [here](Palmora-Data-Analysis.pbix).

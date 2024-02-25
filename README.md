# Call-Centre-Trend-Analysis

## Table of Content

- [Project Description](#project-description)
- [Data Source](#data-source)
- [Data Preparation](#data-preparation)
- [Data Cleaning](#data-cleaning)
- [Dax](dax)
- [Insights](#insights)
- [Recommendations](#recommendations)
#### Project Description
The aim of this project is to build a Power BI dashboard that reflects the key performance indicators and Metrics in the Dataset. 
Possible KPI includes (but not limited to):
* Overall customer satisfaction
* Overall calls answered/abandoned
* Calls by Time
* Average Speed of Answer
* Agent's performance quadrant- average handle time(talk duration) vs calls answered

#### Data Source:
Dataset used for this task was given by [Pwc](https://www.pwc.ch/en/careers-with-pwc/students/virtual-case-experience.html)

#### Data Set: [Call Centre Trends](https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2Fcdn.theforage.com%2Fvinternships%2Fcompanyassets%2F4sLyCPgmsy8DA6Dh3%2F01%2520Call-Center-Dataset.xlsx&wdOrigin=BROWSELINK)

#### Data Preparation:
Started by connecting to excel datasource then loaded the dataset into Power Bi desktop.
The dataset has 10 columns amd 5000 rows to be observed.

#### Data Cleaning:
The dataset was transformed with Power Query Editor as follows:
- Replacing Null values with Zero
- Each of the columns in the table was validated to have correct data type.
- Created a calculated column in powerBI table view for average speed of Answer in Seconds
  
#### Data Analysis(DAX) 
The following Dax was used in Analysing the call centre dataset.
  ``` Power BI
Total calls = CALCULATE('call centre data'[Total calls Answered]) + 'call centre data'[Total calls unanswered]);
  ```
  ```
Total calls Answered = COUNTX(FILTER('call centre data', 'call centre data'[Answered(Yes/No)] ="Yes"), 'call centre data'[Answered(Yes/No)]);
  ```
  ```
Total calls unanswered = COUNTX(FILTER('call centre data', 'call centre data'[Answered(Yes/No)] = "No"), 'call centre data'[Answered(Yes/No)]);
  ```
  ```
Total resolved = COUNTX(FILTER('call centre data', 'call centre data'[Resolved] = "Yes"), 'call centre data'[Resolved]);
  ```
  ```
Total unresolved = COUNTX(FILTER('call centre data', 'call centre data'[Resolved] = "No"), 'call centre data'[Resolved]);
  ```
  ```
Total satisfied = CALCULATE(COUNT('call centre data'[Satisfaction rating]),FILTER('call centre data' ,'call centre data'[Satisfaction rating]), {3,4,5});

  ```
  ```
Average satisfaction = DIVIDE([sum of satisfaction],[Total satisfied]);
 ```
 ```
AVERAGE SPEED OF ANSWER = DIVIDE('call centre data'[Speed of answer in seconds], [Total calls Answered])
 ```

#### Data Visualization(Dashboard):
Data visualization for data analysis(DAX) was done with Microsoft Power BI Desktop:
Shows visualisation from call Centre Trends

#### Insights

- Total calls received was 5000 in which number calls answered and calls unanswered was 4054 and 946 respectively.
- 3646 represents Resolved calls while unresolved calls were 1354.
- The average speed of answer(seconds) is 67.52
- Average customer satisfaction rating is 3.40.
- The agent with the highest number of answered calls is Jim (536 calls) while Stewart had the least answered calls with 477 calls.
- The month of January had the highest Total calls answered followed by February and March. Also, the Month of February had the highest total calls unanswered.
- More People had streaming, technical support and payment related issues respectively hence making them have the highest number of calls.

#### Recommendations
- Rigorous test for quality assurance is recommended. This can be done through call monitoring and scoring.
- Good behaviour should be rewarded, and work incentives are proven to have positive effect on employee engagement and morale.

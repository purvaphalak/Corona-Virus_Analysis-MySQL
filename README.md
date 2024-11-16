# "Corona-Virus Analysis" using MySQL

► As a part of Data Analyst  Internship at Mentorness, I have been tasked to analyse Corona-Virus Dataset using MySQL.

### 𝐓𝐚𝐬𝐤 𝟐 : Corona-Virus Analysis using MySQL

### ➡️ Objective of the Project :

- The objective of coronavirus analysis is to monitor how COVID-19 spreads and affects people by looking at data on cases, recoveries, and and deaths deaths in  differe different areas over time.

This includes:

- Monitoring the number of confirmed cases, deaths, and recoveries.
- Analyzing the geographical spread of the virus using latitude and longitude.
- Providing a time series of the pandemic's progression.
  
- This dataset can be used for various analyses, such as:

- Visualizing the spread of COVID-19 on a map.
- Identifying trends and patterns in the number of cases, deaths, and recoveries over time.
- Comparing the impact of the virus in different regions.
- Modeling and forecasting the future course of the pandemic based on historical data. ​

### ➡️Project Description :

✦ The dataset contains a total of 78,000 rows, the data spans from 22 January 2020 to 13 June 2021. This period covers a significant part of the COVID-19 pandemic, including initial outbreaks, various waves, and the rollout of vaccines.

✦ There are 12 months of data present within the date range. This indicates that the dataset might have monthly aggregated data or data recorded over a year's span.

### ➡️ Dataset Includes :

The dataset appears to be a COVID-19 dataset, providing detailed information about the progression of the pandemic. Here are the key features and their descriptions:

- Province: The province or state within the country.

- Country/Region: The country or region where the data was recorded.

- Latitude: Latitude coordinate for the location.

- Longitude: Longitude coordinate for the location.

- Date: The date when the data was recorded.

- Confirmed: The number of confirmed COVID-19 cases.

- Deaths: The number of deaths due to COVID-19.

- Recovered: The number of recovered cases from COVID-19.

### ➡️ SQL Queries and Insights :

![4](https://github.com/user-attachments/assets/e6bac246-a892-44ae-897e-24e32b865586)

#### ➤ Explanation: 
This query checks the dataset for missing values (NULL) in critical columns. Missing values could affect analysis accuracy.

#### ➤ Insight: 
Identifying and addressing missing data ensures the dataset is clean and reliable for further analysis.

![5](https://github.com/user-attachments/assets/364f7c67-780a-4af9-9b6a-edd4cdf35011)

#### ➤ Explanation: 
This query replaces any missing (NULL) values in the Confirmed, Deaths, and Recovered columns with 0 using the COALESCE function. 
The SET sql_safe_updates = 0 command allows updates without strict conditions.

#### ➤ Insight: 
Ensures that no data gaps interfere with numerical computations or aggregations.

![6](https://github.com/user-attachments/assets/a97002cf-6640-4f5e-a140-85c923cc7d18)

#### ➤ Explanation: 
This query counts the total number of records (rows) in the table.

#### ➤ Insight: 
Provides a quick overview of the dataset size and scope.

![7](https://github.com/user-attachments/assets/23a55366-5a4e-48b2-a3ac-6c1ab9be2699)

#### ➤ Explanation: 
Finds the earliest and latest dates in the dataset using the MIN and MAX functions.

#### ➤ Insight: 
The data spans a specific time period, helping to understand the timeline of the pandemic's impact.

![8](https://github.com/user-attachments/assets/1938043a-9228-465f-82c4-506743dcc010)

#### ➤ Explanation: 
Extracts the month from the Date column and counts unique months to determine the dataset's temporal coverage.

#### ➤ Insight: 
Understanding the span of months allows analysis of seasonal or monthly trends.

![9](https://github.com/user-attachments/assets/69534dec-32b7-49a8-bb16-cba951a5a77a)

- The query aims to calculate the monthly average of confirmed COVID-19 cases, deaths, and recoveries from a dataset called corona_virus.

#### 💠SQL Query Breakdown:

#### 1] Extract Month and Year:

 #### ✅ Syntax :
EXTRACT(MONTH FROM STR_TO_DATE(Date, '%Y-%m-%d')) AS Month,
EXTRACT(YEAR FROM STR_TO_DATE(Date, '%Y-%m-%d')) AS Year,


STR_TO_DATE(Date, '%Y-%m-%d') : converts the Date field from a string format to a date format.

EXTRACT(MONTH FROM ...) : extracts the month from the date.

EXTRACT(YEAR FROM ...) : extracts the year from the date.

The extracted month and year are aliased as Month and Year respectively.

#### 2] Calculate Averages:

#### ✅ Syntax :

AVG(Confirmed) AS Avg_Confirmed,
AVG(Deaths) AS Avg_Deaths,
AVG(Recovered) AS Avg_Recovered,

AVG(Confirmed) : calculates the average number of confirmed cases and aliases it as Avg_Confirmed.

AVG(Deaths) : calculates the average number of deaths and aliases it as Avg_Deaths.

AVG(Recovered) : calculates the average number of recoveries and aliases it as Avg_Recovered.

#### 3] Specify the Data Source:

#### ✅ Syntax :

FROM corona_virus

The data is being retrieved from the corona_virus table.

#### 4] Group by Month and Year:

#### ✅ Syntax :
GROUP BY Month, Year;

The results are grouped by both the extracted month and year. This ensures that the averages are calculated for each month within each year.

#### 5] Result Table Explanation:
The result table shows the monthly averages for confirmed cases, deaths, and recoveries. Each row corresponds to a specific month and year combination.

Example Results Interpretation:

#### ➤ Row 1:

Month: January 2020
Avg_Confirmed: 4.1455
Avg_Deaths: 0.1234
Avg_Recovered: 0.0929

This means that in January 2020, the average number of confirmed cases was approximately 4.15, the average number of deaths was approximately 0.12, and the average number of recoveries was approximately 0.09.

#### ➤ Row 2:

Month: February 2020
Avg_Confirmed: 15.2960
Avg_Deaths: 0.5936
Avg_Recovered: 7.0320

- This indicates that in February 2020, the average number of confirmed cases was approximately 15.30, the average number of deaths was approximately 0.59, and the average number of recoveries was approximately 7.03.


![10](https://github.com/user-attachments/assets/1d657952-5e9f-47bc-a33a-dcea7ec005a3)

- The query aims to find the maximum number of confirmed COVID-19 cases, deaths, and recoveries per year.

#### 💠 SQL Query Breakdown:

#### 1] Extract Year:

EXTRACT(YEAR FROM str_to_date(Date, '%Y-%m-%d')) AS Year,
str_to_date(Date, '%Y-%m-%d') converts the Date field from a string format to a date format.
EXTRACT(YEAR FROM ...) extracts the year

#### 2] Calculate Maximum Values:

MAX(Confirmed) AS Max_Confirmed,
MAX(Deaths) AS Max_Deaths,
MAX(Recovered) AS Max_Recovered,
MAX(Confirmed): calculates the maximum number of confirmed cases and aliases it as Max_Confirmed.
MAX(Deaths) : calculates the maximum number of deaths and aliases it as Max_Deaths.
MAX(Recovered): calculates the maximum number of recoveries and aliases it as Max_Recovered.

#### 3] Specify the Data Source:

FROM corona_virus
The data is being retrieved from the corona_virus table.

#### 4] Group by Year:

GROUP BY Year
The results are grouped by the extracted year. This ensures that the maximum values are calculated for each year.

#### 5] Order by Year:

ORDER BY Year;
The results are ordered by the year to provide a chronological view of the data.

#### 6] Result Table Explanation:

The result table shows the maximum values for confirmed cases, deaths, and recoveries for each year.

Example Results Interpretation:
- Year 2020:

Max_Confirmed: 823225
Max_Deaths: 3752
Max_Recovered: 1123456
This indicates that in 2020, the highest number of confirmed cases in a single entry was 823,225, the highest number of deaths was 3,752, and the highest number of recoveries was 1,123,456.

- Year 2021:

Max_Confirmed: 414188
Max_Deaths: 7374
Max_Recovered: 422436
This indicates that in 2021, the highest number of confirmed cases in a single entry was 414,188, the highest number of deaths was 7,374, and the highest number of recoveries was 422,436.


![11](https://github.com/user-attachments/assets/4e3f957c-23d9-448b-ad7e-b2c5fe18f933)

#### ➤ Explanation: 
Calculates the smallest and largest values for each metric annually using MIN and MAX functions.

#### ➤ Insight: 
Identifies outlier years or extreme points during the pandemic.

![12](https://github.com/user-attachments/assets/c8b90b67-5646-480f-b50a-27c0477f8a40)

#### ➤ Explanation: 
Calculates the smallest and largest values for each metric annually using MIN and MAX functions.

#### ➤ Insight:
Identifies outlier years or extreme points during the pandemic.

![13](https://github.com/user-attachments/assets/8e9c5c97-7ab4-4663-aa6c-01da2991292c)

 #### ➤ Explanation: 
 Aggregates total confirmed cases, deaths, and recoveries for each month using the SUM function.
 
#### ➤ Insight: 
Identifies monthly cumulative trends and critical periods.

![14](https://github.com/user-attachments/assets/be622844-9c39-4faa-b902-e0f9fc9e3618)

 #### ➤ Explanation: 
Calculates the total, average, variance, and standard deviation of confirmed cases, deaths, or recoveries.

 #### ➤ Insight: 
Measures the spread and variability of the data, essential for understanding consistency and volatility.

![15](https://github.com/user-attachments/assets/97584577-b408-4442-95a5-f7d61dc5b635)

 #### ➤ Explanation: 
Calculates the total, average, variance, and standard deviation of confirmed cases, deaths, or recoveries.

 #### ➤ Insight: 
Measures the spread and variability of the data, essential for understanding consistency and volatility.

![16](https://github.com/user-attachments/assets/5f864bd1-ff00-4d70-af8a-233ee9466838)

 #### ➤ Explanation: 
Calculates the total, average, variance, and standard deviation of confirmed cases, deaths, or recoveries.

 #### ➤ Insight: 
Measures the spread and variability of the data, essential for understanding consistency and volatility.

![17](https://github.com/user-attachments/assets/cdc316e7-786f-4058-909d-1abff3857157)

 #### ➤ Explanation:
Identifies the country with the highest total confirmed cases using SUM and LIMIT.

 #### ➤Insight: 
 Reveals which country was most affected.

![18](https://github.com/user-attachments/assets/1dfd4d8b-0cab-451d-b0a9-908965eb6c3f)

Explanation: Finds the country with the lowest total deaths using a Common Table Expression (CTE) and RANK.
Insight: Highlights regions with minimal fatalities.


![19](https://github.com/user-attachments/assets/b8c411c9-786b-49c7-a669-757bfd03492b)

Explanation: Lists the top 5 countries with the highest recoveries using SUM and LIMIT.
Insight: Recognizes regions with strong recovery efforts.

![20](https://github.com/user-attachments/assets/7a9e75e4-b18b-4b1e-878e-c3f5b0cf6a7b)
![21](https://github.com/user-attachments/assets/e4b52d00-6824-46e8-8315-162b023c6637)
![22](https://github.com/user-attachments/assets/738edb03-6ad8-45ec-a9b5-540213deca0f)
![23](https://github.com/user-attachments/assets/ab75b6ff-5a6c-441a-a76e-6ec35baa9155)



### ➡️ Overall  Insights :

#### ➤ Higher Confirmed Cases:
The United States has the highest number of confirmed cases. This reflects the significant impact of COVID-19 on the US, particularly during the peak periods of the pandemic.

#### ➤ Lowest Death Cases:
Countries like Dominica, Kiribati, Marshall Islands, and Samoa have the lowest number of death cases. These countries may have managed to control the spread of the virus effectively or have smaller populations, leading to fewer deaths.

#### ➤ Highest Recovered Cases :
The top five countries with the highest number of recovered cases are India, Brazil, the US, Turkey, and Russia. These countries likely experienced high numbers of cases overall, leading to high recovery numbers as well.

### ➡️ 𝐒𝐮𝐦𝐦𝐚𝐫𝐲 :

#### ➤ Pandemic Coverage :
The date range indicates that the dataset covers critical phases of the pandemic, making it valuable for trend analysis and understanding the progression and impact over time.

#### ➤ Geographical Impact:
The US having the highest confirmed cases is consistent with global reports of the pandemic's severe impact on the country. Conversely, the countries with the lowest death cases are small island nations, which might have implemented strict measures early on to prevent the spread of the virus.

#### ➤ Recovery Rates :
High recovery numbers in populous countries like India, Brazil, and the US are expected given their large populations and significant numbers of confirmed cases. The high recovery rate can provide insights into healthcare response effectiveness and the overall trajectory of the pandemic in these regions.

✨ These insights can help in understanding the global impact of COVID-19, the effectiveness of different countries' responses, and the overall trends in confirmed, death, and recovery cases during the specified period.


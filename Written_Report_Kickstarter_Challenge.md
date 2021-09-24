# Kickstarting with Excel

## Overview of Project

### Purpose

Louise’s play Fever came close to its fundraising goal in a short amount of time. Now, she wants to know how different campaigns fared in relation to their launch dates and their funding goals. Using the Kickstarter dataset the main goal is to visualize campaign outcomes based on their launch dates and their funding goals. 

The purpose of this analysis is identifying the relation between different campaigns fared in relation to their launch dates and funding goals compare to the play called Fever. 
The analysis is focused in two main visualizations: Theater Outcomes by Launch Dates and the Outcomes Based on Fundraising Goals. The development of these visual analysis will head to the define the relation between Louise’s play Fever with other plays available in the set of data collected under the Kickstarted file.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

For the Theater Outcomes by Launch date a pivot table was developed considering all the Outcomes (Successful, Failed and Canceled) versus the Date Created Conversion by each month. As a filter the Parent Category was included to filter just the data related with Theater and the Years available. Finally, all the values are related with the count of the outcomes in order to list amount of successful, failed and canceled plays were completed by month. Then, a graph was develop using a line chart; since there is an study of data over a time, having a visual representation of the outcomes by launch date to understand how is the trend of the outcomes based on the launch date.

The graph represent the tren from January to December considering data for 9 consecutive years, representing the trend for Canceled (blue line), Failes (orange line), successful (yellow line) over the time. 

![Outcomes Based on Launch Date]/kickstarter-analysis/Resources/Outcomes_Based_on_Launch_Date.png

### Analysis of Outcomes Based on Goals

To analyze the Outcome based on goals; a new sheet was developed adding new columns to determine numbers of successful, failed, and canceled outcomes utilizing the function “COUNTIFS” and having as conditions the specific outcome (“successful”, “failed”, “canceled”), the specific Parent Category (“Plays”) and the specific goal range included in the first column  and the percentage of each category based on the total outcome by each month. 

Additionally, a column with range of goals was added as reference to define the total outcomes in the count based on the range pre establish for the analysis; using for example =COUNTIFS( Kickstarter!$F:$F, "successful", Kickstarter!$R:$R, "plays", Kickstarter!$D:$D, "<1000") for values less than $1000 as a goal. For other specific ranges a new condition was add to combine the specific range between two values, for example =COUNTIFS( Kickstarter!$F:$F, "successful", Kickstarter!$R:$R, "plays", Kickstarter!$D:$D, ">=5000 ", Kickstarter!$D:$D, "<=9999 " ) for values greater than $5,000 and less than $9,999

Finally, a percentage was calculate by each outcome respect the total outcomes by each range to identify the portion of “successful”, “Canceled” and Fail” play were assign by each range and ensuring the total outcomes % by range was equals to 100%. After the generation of this table for each type of condition, a line chart was created to establish the relation between the range and the percentage to easy identify how was the trend over different ranges and the % of successful, or failed plays based on the goals of funding to generate the conclusions from it.

The line chart represent the percentage of sucessful (blue line), percentage of canceled (grey line) and percentage of failed (orange line) over 12 different ranges from Less than 1000 to Greater than 5000 dollars for collection as a goal to drive conclusions about this performance. 

![Outcomes Based on Goals]!(https://github.com/mdpalaciot/kickstarter-analysis/blob/main/Resources/Outcomes_Based_on_Goals.png)

### Challenges and Difficulties Encountered

#### Challenges Outcomes Based on Launch Date

Part of the challenges related with the development of this study was related with data not readable.  The data in some columns look like dates, but they were not in a readable format. In this way, it was required to convert it to make it readable. Specifically, the “Deadline” and “Launched_at” columns contain Unix timestamps rather than dates in a standard format. For this, a verification was made using timestamp converter to verify data were Unix Timestamps not random numbers, and then a new column was created to define "Date Created Conversion." following formula, =(((J2/60)/60)/24)+DATE(1970,1,1)  to figure out how many days, minutes, and seconds the timestamp translates to, and then  adding it to the January 1, 1970 to have dates in human readable format

Another challenge was to address errors like divisions over zero with the “If Error’ Function after the implementation of round function to determinate the average donation of each play; using for example formula  =IFERROR(ROUND(E2/L2,2),0)

#### Challenges Outcomes Based on Goals

Major challenges for this graph generation was the calculation using different conditional based on the goals range and the outcomes, since each variable in each cell have an specific configuration that need to be validated to ensure no data was not considered in the calculation, creating possible errors in the interpretation. 

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

The first five month of the year represent the highest increment in successful plays with a peak in May while the last 7 months of the year represent a decreased on successful rate with the lowest value in December.

May and October have the highest rate of failed for the plays, but considering the peak in May for successful plays, October represent the most critical time a value of 50 plays compared with just 65 successful plays in the same month with zero canceled plays. 

Also, having December as a month with equal rate for successful and failed rate compare to a minimal canceled rate of plays during the whole year


- What can you conclude about the Outcomes based on Goals?

The percentage of Failed increase over the ranges while percentage of successful play decrease over the increment of funding goals. 

For the ranges “less that $19,999” and “$35,000 to $44,999” the percentage of successful funding was greater than the failed while “$20,000 to $34,999” and “greater than $40,000” have a greater rate of failed compared to successful.

For goals of $45,000, the rate of failure reach a peak with 0% of successful plays while less than $5,000 seems to be have the most highest rate 


- What are some limitations of this dataset?

Limitations could be related with any inconsistencies and/or errors existing in the data during the collection, as well any duplicates or outliers in the data that could be studied determining the descriptive statistics of the data as Quartile Limits based on the range fundings developed and the possible outcomes. In the same way, response bias during the collection based on other Parent Categories like television or journalism that could influence the trend of the data regarding plays. A further study is recommended to analyze this relation. Finally the establish of the goals could be a limitation since this variable define if a play is successful or not in the study, having the same goals for the set of data regarding 9 years.

- What are some other possible tables and/or graphs that we could create?

Outcomes by year instead of months to identify any trend over the time and see if there is any change or recommendation.
Outcomes over year but considering a comparison between plays and other Parent Categories. A pareto could be develop with a bar graph to identify the most successful Categories and using the top 5, compare the trend with the plays over a time line to identify any relation during specific season.
Goals Range by countries, defining “play” as Subcategory to generate an stack bar to understand the trend by each country having a possible conclusion about where and when Louise’s play could obtain a higher successful rate.  


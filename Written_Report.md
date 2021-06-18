# Kickstarting with Excel

## Overview of Project
The dataset 
(remember to insert link to excel file)
### Purpose
Analyze Kickstarter data to explore variety of trends.
This report will focus on:
1.	parent category *Theatre* outcomes based on launch date
2.	subcategory *Plays* outcomes based on goal.

## Analysis and Challenges
### Analysis of Outcomes Based on Launch Date
![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/84211948/122508235-56529580-cf9d-11eb-81ac-d506fe7b7a6e.png)

### Analysis of Outcomes Based on Goals
![Outcomes_vs_Goals](https://user-images.githubusercontent.com/84211948/122508247-5b174980-cf9d-11eb-9590-7810d5e73158.png)

### Challenges and Difficulties Encountered
1.	It is always a good practice to ensure the correctness of the data and result by double checking other charts, table or worksheet. There are a large number of categories and subcategories, it is essential to ensure all the factors and filters are selected correctly. I encountered once where the data didn’t match between sheets, I double checked and made necessary corrections on filters and ensured the sufficiency of results.
2.  During first attempt using ```COUNTIFS``` function to get *Number Successful, Number Failed and Number Canceled* for variety ranges of goals, I received “0” as result for all cells. I went back and double check formula and noticed that I need to type **“plays”** to filter the correct subcategory, not “play” or “Play”. So, we always need to ensure the elements matches among data sets.
3.  For the very last range _“Greater than 50000”_, I first typed “>50000”. I noticed that the result it came out is 4 less than the data came out from previous pivot table, which means there’s something wrong with the formulas. Then I noticed that “50000” was not covered by any of the range and this is where I missed 4 Failed Campaigns. Even though “_Greater than 50000_” sounds like >50000, we always need to make sure whether it’s correct when transform into a function or formula.
4.	I found it quite time consuming to type and adjust formulas in each cell. In addition, it could be lack of accuracy when manually enter the ranges with double quotation marks into each formular. It not only takes extra time to enter, but also costs more time to double checking. 
My solution to overcome this challenge is to create a Range Set on the side as references. (_As shown in screenshot below_)

![range_reference](https://user-images.githubusercontent.com/84211948/122509738-f9a4aa00-cf9f-11eb-8087-110b6996c8e0.png)

Advantages of doing so are following:
  - It takes very little time to create such list. After inputting >=0 and >=1000, the list can be completed simply by dragging down. Same for both Lower and Upper Range.
  - When inputting formulas, it is much easier and more accurate to click the reference cells instead of manually typing 5-digits numbers.
      - Before: ```=COUNTIFS(Kickstarter!$D:$D,">=15000",Kickstarter!$D:$D,"<=19999",Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays")```
      - After: ```=COUNTIFS(Kickstarter!$D:$D,'Outcomes Based on Goals2'!$J6,Kickstarter!$D:$D,'Outcomes Based on Goals2'!$K6,Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays")```
  - If analysis by different ranges is needed, it can be done by adjusting the reference list without touching the formulas.

In conclusion, I believe the solution above is a good practice of spending few second to save much more time.

## Results
- **What are two conclusions you can draw about the Outcomes based on Launch Date?**
  - Campaigns launched in May and June have significant higher rate of success than other months. But then we see the a down trend of success right after and reached similar amount with April. This outcome might be affected by the fact that there are more total numbers of campaign launched in May and June than other months.
  - The numbers of failed campaign launched in May and June are also slightly higher than other months. In addition, October also has a slightly higher number of failed cases.
  If Louise launch campaign during May or June, there might be a bigger chance to success, but other factors need to be considered.
- **What can you conclude about the Outcomes based on Goals?**
  - From above percentage, we can see an overall trend that higher goals lead to a lower success rate and lower goals lead to a higher success rate. In another word, goal and success rate is negative correlated.
Louise may consider listing her campaign with a reasonable goal and avoid setting an extreme high goal.
- **What are some limitations of this dataset?**
  1.  This dataset is solely focused on parent category “Theater” and subcategory “Plays”, it might be helpful to conduct a thorough analysis in other categories   and examine other possible trends as well. Different categories may still have similar trends.
  2.  This analysis does not focus on one single country as a launching location. Different markets may contain significantly different fund-raising behavior. Louise should decide on a market then conduct another analysis of that market.
  3.  This report includes outcomes only based on “Launch Date” and “Goals”, however, there are many factors in the original data that could affect decision. For example, is duration a key to success? Is longer duration the reason why some campaign succeeded? Does the trend change year over year? Are theater campaigns more popular in 2015 than in 2016? There are many other factors worth to explore. 
- **What are some other possible tables and/or graphs that we could create?**
  1.  For above limitations, we can create trend charts on other categories or subcategories, same outcome charts of different markets, and a success rate vs. duration table/graphs. In addition, for the same months, especially for peak months (May and June), we can create and compare tables and graphs of same period in different years to conclude whether peak months take place in same months every year.
  2.  A box and whisker plot or a table of IQR can be create on goals of successfully funded plays to examine outliers. 





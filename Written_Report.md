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
-	What are two conclusions you can draw about the Outcomes based on Launch Date?
-	What can you conclude about the Outcomes based on Goals?
-	What are some limitations of this dataset?
-	What are some other possible tables and/or graphs that we could create?






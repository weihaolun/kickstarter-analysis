# Kickstarting with Excel

## I. Overview of Project
Louise is planning to launch her play campaign _“Fever”_ on Kickstarter crowdfunding platform. We need to help her to conduct variety trending analysis on Kickstarter campaign [dataset](https://github.com/weihaolun/kickstarter-analysis/blob/d468114fb10abc7cadd8638a2e20543b9ebc9fe5/Kickstarter_Challenge.xlsx) and provide her suggestions based on the findings.
The dataset includes raw data of 4113 campaigns. In order to conduct further analysis for this project, I have completed following adjustments to the dataset:
1.	Added filters to the dataset so that campaigns can be correctly categorized and subcategorized.
2.	Converted Unix Timestamps to readable format so that we can clearly filter data by years and months.
3.	Created pivot tables to summarize category and subcategory data. This step is useful for overall analysis and data auditing.

### Purpose
Analyze Kickstarter data to explore the **relationship between outcomes and launch time** and **relationship between outcomes and goals** to provide Louise more insight of proper timing and goal to launch her play "_Fever_".

This report includes analysis focused on:
1.	parent category *Theatre* outcomes based on launch dates
2.	subcategory *Plays* outcomes based on goals.

## II. Analysis and Challenges
### Analysis of Outcomes Based on Launch Date
  In order to analyze the relationship between outcomes and launch dates, I created another pivot table to match outcomes with months. Select _Parent Category_ and _Years_ as filters, _Launch Date_ (group to show months only) as row, and _Outcomes_ as column and value.
  
  After setting _Theater_ as the parent category, we will see a table (as shown below) to show the number of campaigns succeeded, failed and canceled in each month under “Theater” category. 
  
 ![Theater_Outcomes_vs_Launch_pivot](https://user-images.githubusercontent.com/84211948/122661954-1caf9500-d12b-11eb-859d-072fb7e25a5c.png) 
  
  Next, I created a line chart (as shown below) to see the trend between each type of outcomes and months, and how are the outcomes distributed through out the year.
![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/84211948/122508235-56529580-cf9d-11eb-81ac-d506fe7b7a6e.png)

### Analysis of Outcomes Based on Goals
  In this part of analysis, we focused on the subcategory of “_Plays_”. First, I broke down the goals of all plays into 12 ranges. Then used ```COUNTIFS``` function to count the numbers of campaigns succeeded, failed and canceled within each goal range. Next, I calculated percentage of successful, failed and canceled campaigns using above numbers. (See table below)
  
  ![Outcomes_vs_Goals_table](https://user-images.githubusercontent.com/84211948/122662132-4fa65880-d12c-11eb-86ec-328bd05634e3.png)

  For the last step, a line chart (as shown below) was created to suggest relationships between goal ranges and percentage of each type of outcomes.

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/84211948/123181382-e7f05600-d428-11eb-8d90-cdfe21d20057.png)

### Challenges and Difficulties Encountered
1.	It is always a good practice to audit the data and result by double checking with other charts, tables or worksheets within the dataset. There is a large number of categories and subcategories, it is essential to ensure all the factors and filters are selected correctly. I encountered once where the data didn’t match between sheets, I double checked and made necessary corrections on filters to ensure the accuracy of results.

2.  For the very last range _“Greater than 50000”_ when using ```COUNTIFS``` function, I first typed “>50000”. I noticed that the result came out was 4 less than the data from previous pivot table, which means there’s something wrong with the formulas. Then I noticed that “50000” was not covered by any of the ranges and this is where I missed the 4 Failed Campaigns. Therefore, the formula should be _">=50000”_ instead. Even though “_Greater than 50000_” sounds like >50000, we always need to make sure it’s correct when transforming text to a function or formula. 
3.	Also when using ```COUNTIFS```, I found it quite time consuming to type and adjust formulas in each cell. In addition, there could be lack of accuracy when typing each cell manually. It not only takes extra time to enter, but also costs more time to double checking. 
My solution to overcome this challenge is to create a Range Set on the side as a reference. (_As shown in screenshot below_)

![range_reference](https://user-images.githubusercontent.com/84211948/122509738-f9a4aa00-cf9f-11eb-8087-110b6996c8e0.png)

Advantages of such reference set:
  - It takes very little time to create a such list. After inputting the first 4 ranges, the list can be completed simply by dragging down. Same for both Lower and Upper Range.
  - When inputting formulas, it is much easier and more accurate to click the reference cells instead of manually typing 5-digit numbers.
      - Before: ```=COUNTIFS(Kickstarter!$D:$D,">=15000",Kickstarter!$D:$D,"<=19999",Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays")```
      - After: ```=COUNTIFS(Kickstarter!$D:$D,'Outcomes Based on Goals'!$J6,Kickstarter!$D:$D,'Outcomes Based on Goals'!$K6,Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays")```
  - If another analysis by different ranges is needed, it can be done by adjusting the reference list without touching the formulas.

In conclusion, I believe the solution above is a good practice of spending few second to save much more time.

## III. Results
- **What are two conclusions you can draw about the Outcomes based on Launch Date?**
  - There are more successful campaigns launched between April and August. Success number reached to a peak in May (111) and remained high in June (100). Then it dropped to 72 in August, which is similar to 71 in April. These five months, especially May to July, contains more successful campaigns.
  - The range for failed campaigns is from 31 to 50, while the range for successful campaigns is from 37 to 111. Therefore, the number of failed campaigns remain relatively stable through the year. This trend can also be concluded from the line graph. We don’t see a significant peak period as we see for successful campaigns. The numbers of failed campaigns between April to August and October are slightly higher than other months, this could be caused by the fact that there are more total number of campaigns launched in these months.
  - If Louise launch campaign during May or June, there might be a higher chance to succeed, but other factors need to be considered as well.
- **What can you conclude about the Outcomes based on Goals?**
  - There is one exception on the line graph that the successful rate reached 67% between $35000 to $44999. There is where even though the goal is high, the successful rate is still high. This outcome is caused by the fact that the total of projects for this range is super low and the data might not be necessarily sufficient.
  - Louise may consider listing her campaign with a reasonable goal and avoid setting an extreme high goal.
- **What are some limitations of this dataset?**
  1.  This dataset is solely focused on parent category “Theater” and subcategory “Plays”, it might be helpful to conduct a thorough analysis in other categories   and examine other possible trends as well. Different categories may still have similar trends.
  2.  This analysis does not focus on one single country as a launching location. Different markets may contain significantly different fund-raising behavior. Louise should decide on a market then conduct another analysis of that specific market.
  3.  This report includes outcomes only based on “Launch Date” and “Goals”, however, there are many other factors in the original dataset that could affect decisions. For example, is duration a key to success? Is longer duration the reason why some campaigns succeeded? Does the trend change year over year? Are theater campaigns more popular in 2015 than in 2016? There are many other possibilities worth to be explored. 
- **What are some other possible tables and/or graphs that we could create?**
  1.  For above limitations, we can create trend charts on other categories or subcategories, outcome charts of different markets, and a success rate vs. duration table/graphs. In addition, for the same months, especially for peak months (May and June), we can compare tables and graphs of same period in different years to conclude whether peak months take place at the same time every year.
  2.  A box and whisker plot or a table of IQR can be create on goals of successfully funded plays to examine outliers. 





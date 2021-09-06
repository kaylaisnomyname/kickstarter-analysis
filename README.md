
# Kickstarting with Excel

## Overview of Project
The background of this project is that play, *Fever*,  is geting close to its fundraising goal. The playwrite, Louise, wants to predict how likely her campaign will be successful. Analysis of the given Kickstarter dataset of all compaign performances over the years could help Louise draw the prediction.  
### Purpose 
 The purpose of this project is to apply the Excel knowledge we learned to find out how the campain outcomes of theater differed based on launch date, and how the campain outcomes of plays varied based the goal.  
     
       

   
## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date  

To aquire an overview of theater outcomes based on lauch date, first use year() function to aquire the launch years. In the raw data, launch date was in Timestamp format. Convert the timestamp format to readable date format and store the date in date_created column using :
```
(((timestamp_cell/60)/60)/24) + date(1970,1,1)
```
With the result of date_created column, use year() to get year value and store in column Years:
```
year(date_created_cell)
```
With the whole data to create a pivot table, filter with *Parent category* and *Years*, unselect the *live* outcome, filter *Parent category* with "theater": obtain the result pivot table as shown in Image 1 below. 
Based on the pivot table, create a line chart showing the relation of theater outcomes based on launch date, as shown in Image 2 below.
  
##### Image 1 : Theater outcomes based on launch date
![Pivot table of theater outcomes based on launch date](https://github.com/kaylaisnomyname/kickstarter-analysis/blob/main/Screenshot-of-theater-outcomes-based-on-launch-date.png?raw=true)  

##### Image 2 : Line chart of Theater Outcomes Based on Launch Date  
![Theater Outcomes Based on Launch Date](https://github.com/kaylaisnomyname/kickstarter-analysis/blob/main/resources/Theater_Outcomes_vs_Launch.png?raw=true)  


 
### Analysis of Outcomes Based on Goals 
To find out how the relation between the outcomes and the goals, first categorize the goals into different groups. For each goal group, aquire the numbers of outcomes using function countifs(). The use of countifs() is as:

 ```
=COUNTIFS(criteriaRange1, "count_this_value1", criteriaRange2,"count_this_condition2",criteriaRange3,"count_this_condition3")
```
     
 To find successful numbers in goal less than $1k, criteriaRange 1 is the whole data of outcomes column in sheet Kickstarter, "count_this_value" is "successful". CriteriaRange2 is the goal group, condition2 is " <1000". CriteriaRange3 is the subcategory in sheet Kickstarter and condition3 is "plays": the function is :    
 ```  
=COUNTIFS(Kickstarter!$F$1:$F$4115,"successful",Kickstarter!$D$1:$D$4115,"<1000",Kickstarter!$R$1:$R$4115,"plays")
```
For other groups, change criteriaRange2 to each conditions. For numbers of failed and canceled outcomes, change criteriaRange1 as needed. Use sum() function to populate the total numbers of outcomes for each goal group.
After finding the numbers of outcomes, sum up the total numbers using function sum(), calculate the percentage of each outcomes. Use the percentage results and goal groups to create a line chart shown as Image 3 below.   



#### Image 3 : Plays Outcomes Based on Goals 
![Outcomes Based on Goal](https://github.com/kaylaisnomyname/kickstarter-analysis/blob/main/resources/Outcomes_vs_Goals.png?raw=true)   

  

### Challenges and Difficulties Encountered
Both Excel function usages and Markdown syntax are challenges. When encoutered challenges, I went to my best friend, Google. The following are reference links where I get info from. Overall, more excersices are needed to get familiar with the syntax.
-  [Excel documentations](https://support.microsoft.com/en-us/office/countifs-function-dda3dc6e-f74e-4aee-88bc-aa8c2a866842?ui=en-us&rs=en-us&ad=us)
-   [Markdown reference](https://guides.github.com/features/mastering-markdown/)


## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?  
Image 2 shows the trends of theater outcomes based on launch date. As showed in the line chart, the most successful counts were launched in May. The biggest difference between successful and failed counts is in May. Therefore, the theather campaign launch in May has a higher chance to be successful. Also, December has the lowest count for successful campaigns and average count of failed campaigns. This inplies that December might not be a good time to launch a new theater campaign. 

- What can you conclude about the Outcome based on Goals?    
Image 3 shows the trend of plays campaign outcomes based on goals. When the goal amount is less than $30k, the lower goal amount has higher successful rate. 


- What are some limitations of this dataset?  


- What are some other possible tables and/or graphs that we could create?  
Besides line chart, stacked column chart can also clearly show the outcomes based on goal, since the outcomes are in percentage type.   

##### Image 4 : Stacked Column Chart for Outcomes Based on Goal  

![stacked column chart](https://github.com/kaylaisnomyname/kickstarter-analysis/blob/main/outcomes-based-on-goals-stackedColumn.png?raw=true)


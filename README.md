# DSA-PROJECT-DOCUMENTATION-II

It is a  project that focus mainly on PowerBI for analysis

## PROJECT TOPIC: PALMORA GROUP HR ANALYSIS

### PROJECT OVERVIEW

This Data analysis project aims to generate insight on the issues of Gender inequality between its employees associated with this manufacturing company across its three (3) regions. By analyzing the various parameters in the data received. We seek to gather enough insight to make a well-considered decision. Which then enable us to tell compelling stories around our data from understanding gotten, giving the best outcome.

### DATA SOURCES

The primary source of Data used here is HR data.csv and excel file containing the bonus rules/mapping from the DSA team

### TOOLS USED

Power BI [download](https://www.microsoft.com/en-us/power-platform/products/power-bi/downloads)

Cleaning data, Analysis of Data and Visualization of result

### DATA CLEANING/PREPARATION

In the initial data preparation phase, we performed the following tasks
-	Data loading and inspection
-	Handling missing values and blank spaces
-	Data munching and formatting

### EXPLORATORY DATA ANALYSIS

We explored the HR data to answer key questions, such as
1. What is the gender distribution in the organization?
2. What is the performance ratings base on gender
3. How is the Company Salary structure, is there a gender pay gap in what department and region
4. Does the manufacturing company meet up the recent regulation of $90,000 salary threshold 
5. How much bonus is to be paid to each employee

### DATA ANALYSIS

This Include the following process: 

Creating calculated columns
- **Total amount of salary for each employee**
```dax
 Total Salary = Palmoria group emp-data[] + Palmoria group emp-data[Bonus Amount]
```
- **Bonus Amount to be paid to each employee**
```dax
 Bonus Amount = Palmoria group emp-data[Salary]* IF(Palmoria group emp-data[Rating]="Very Good",RELATED{'Bonus Rules'[Very Good]),
 IF(Palmoria group emp-data[Rating]="Very Poor",RELATED('Bonus rules'[Very Poor]),IF(Palmoria group emp-data[Rating]="Poor",RELATED('Bonus Rules'[Poor]),
 IF(Palmoria group emp-data[Rating]="Good",RELATED('Bonus Rules'[Good]),IF(Palmoria group emp-data[Rating]="Average",RELATED('Bonus Rules'[Average])'
 BLANK())))))
```

Creating Group e.g Salary Bin (bin size of $10,000)

Creating Slicers (Regions, Gender)

Creating Measures
- **Average Salary**
```dax
 Average Salary= AVERAGE(Palmoria group emp-data[Salary])
```
- **Average Rating**
```dax
Average Rating= AVERAGE(Palmoria group emp-data[Rating])
```
- **Employee Above minimum threshold**
```dax
Employee above threshold= CALCULATE(COUNTROWS('Palmoria group emp-data'),'Palmoria group emp-data[Salary] > 90000)
```

Creating charts
   - Pie chart for over all gender distribution
   - Matrix for gender count by salary and count of Employee above minimum threshold
   - Donut chart for salary distribution of minimum threshold
   - Column chart rating salary distribution and distribution of salary by gender
   - Bar Chart for average salary distribution,department and Sum of bonus,gender distribution
   - Table to show employee names and their calculated bonus amount

### RESULT/FINDINGS 

This analysis is summarized as follows:

we are working with three(3) gender with our focus mainly on the male and the female gender, some employee did not specify theirs. Here we got to see the Male gender is more in number than the female folks since it is a manufacturing company, it is said to be a male dominated industry that explains the high number of the male gender compare to female and others.

Base on rating work performance among employee by the management,the Male gender were rated more in the Average,Poor and Very Poor category while the Female were rated in theGood, Very Good category and some were not even rated at all. Clearly showing base on this rating system, we can say the Female gender are getting the job done

We get to see that different regions within the same department do get paid the same amount. A clear example is the Accounting department where the Average Salary for the South West region is higher by $93,494 compare to the North West region with Average Salary $66,987 within the same department. Using same example we found out that the average salary for male gender is more than the female same goes for other department except in marketing and training(which by statistics is 60-70% women in the field) where the Female earn more. Also the gender that earned relatively high base on average salary was not specified.

Only about 292 people meet up the minimum threshold regulation which is about 30.87% of the total employee, with more from the male gender.
Bonus Payment for the company is outline base on performance rating of each employee, depending on the category they fall into hence,bonus amount. Going by our calculation the Northwest Region(Kaduna) was the highest followed by North Central(Abuja) and the least is South West region(Lagos).



  
 

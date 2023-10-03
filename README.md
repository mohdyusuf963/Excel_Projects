# Excel_Projects
HR Dashboard (Excel)

Project Summary: An Excel dashboard that analyses the data to enable the extraction of valuable insights across a range of diverse metrics.

Stakeholders:
•	HR Managers and Teams
•	Executives and Leadership Teams
•	Department Managers
•	Recruitment Teams
•	Legal and Compliance Teams

Project Links: mohdyusuf963/Excel_Projects (github.com)

Business Problem & Key Questions: 
The client wants to have a dashboard that shows valuable insights across a range of diverse metrics. This will provide them with insights into the following requirements:

Primary KPI’s- 
Total number of active employees, encompassing both existing staff and new hires.

Secondary KPI’s- 
Total number of active employees with respect to Ethnic group and Gender
Average Tenure Months with respect to Ethnic group and Gender
Separations encompassing both Separations and Bad Hires
Voluntary and Involuntary Termination with respect to Year
Total number of active employees with respect to Region and Full/Part Time

Data Preparation:
To acquire the data, I conducted an online search to obtain a small company’s 4 year data

There were 48 CSV file with following metadata:
File extension: .csv
No. of Rows: 200+
No. of fields: 16

I used Excel to prepare my data for the analysis.

Approach:
Here’s the approach I used:

Data Processing:
•	Used Power Query to get the data and consolidate it into one table, so that it can be analysed
•	In Power Query Editor:
o	removed the column named ‘Source.Name’
o	changed the data type of a column named 'TermDate’ to Date datatype
o	changed the data type of a column named 'TermReason’ to Text datatype

Measures:
1. EmpCount: =CALCULATE(COUNT([EmpID]),FILTER(ALL('HR Data'[Date]),[Date]=MAX([Date])))
Calculates the count of employees (EmpID) based on the latest available date in the 'HR Data' table.

2. Active Employees: =CALCULATE([EmpCount],FILTER('HR Data',ISBLANK('HR Data'[TermDate])))
Uses the EmpCount measure to calculate the count of employees who are currently active. It filters the 'HR Data' table to include only records where the TermDate is blank (indicating that the employee is still active).

3. New Hires: =CALCULATE(COUNT([EmpID]),FILTER('HR Data','HR Data'[isNewHire]="Yes"))
Calculates the count of employees (EmpID) who are classified as new hires in the 'HR Data' table, where the 'isNewHire' column is marked as "Yes."

4. Avg. Tenure Months: 
=CALCULATE(AVERAGE('HR Data'[TenureMonths]),FILTER(ALL('HR Data'[Date]),[Date]=MAX([Date])))
Calculates the average tenure in months for employees in the 'HR Data' table, based on the latest available date in the data.

5. Separations: =CALCULATE(COUNT([EmpID]),FILTER('HR Data',NOT(ISBLANK(('HR Data'[TermDate])))))
Calculates the count of employees (EmpID) who have separated from the company. It filters the 'HR Data' table to include records where the TermDate is not blank.

6. TO%: =DIVIDE([Separations],[Active Employees])
Calculates the turnover percentage by dividing the count of separations by the count of active employees. It's a measure used to assess the turnover rate within the organization.

Results & Key Takeaways:
1. The highest number of active employees, with a headcount of 658, was in October 2018, during the fourth quarter (Q4).
2. The lowest number of active employees, totaling 228, was in January 2015, during the first quarter (Q1).
3. The highest number of new hires, totaling 118, occurred in June 2018, during the second quarter (Q2).
4. The low hiring rate remained consistent during the first quarter (Q1) of 2015, with only one new employee hired in each of the three months.
5. The highest number of employees, categorized by ethnic group, in male is of Group C, with a count of 50. They are employed in part-time positions.
6. The highest number of employees, categorized by ethnic group, in female is of Group E, with a count of 27. They are employed in full-time positions.
7. In 2018, the highest number of bad hires occurred, totaling 676.
8. In 2018, the highest number of terminations occurred on a voluntary basis, with a headcount of 228, while involuntary terminations had 772 headcounts.
9. In the North region, the highest number of active employees, totaling 124, includes both full-time and part-time workers.
10. The Midwest region has the fewest active employees, with only 62.
11. The ethnic group with the highest average tenure is Group C, with 210 employees.





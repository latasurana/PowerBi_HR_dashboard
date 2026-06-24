# PowerBi_HR_dashboard
HR Analytics Dashboard Project
Project Overview
This HR Analytics Dashboard was developed to analyze employee demographics, workforce distribution, employee satisfaction, compensation patterns, and attrition trends. The objective is to identify the major factors contributing to employee turnover and provide actionable recommendations to improve employee retention.
Data Transformation (Power Query)
Before building the dashboard, several data cleaning and transformation steps were performed:
1. Data Quality Checks
•	Verified 1,480 employee records. 
•	Checked for duplicate Employee IDs. 
•	Validated data types for numerical and categorical fields. 
•	Standardized text values across categorical columns. 
2. Data Cleaning
•	Removed unnecessary spaces and formatting inconsistencies. 
•	Converted age, salary, and experience columns to numeric format. 
•	Handled missing values in manager-related fields. 
•	Ensured consistent Yes/No values in Attrition and Overtime columns. 
3. Feature Engineering
Created business-friendly categories:
Age Groups
•	18–25 
•	26–35 
•	36–45 
•	46–55 
•	55+ 
Salary Slabs
•	Upto 5K 
•	5K–10K 
•	10K–15K 
•	Above 15K 
Attrition Measures
•	Attrition Count 
•	Active Employees 
•	Attrition Rate % 
________________________________________
Data Modeling
A Star Schema approach was followed.
Fact Table
FactEmployee
Contains:
•	Employee ID 
•	Attrition 
•	Monthly Income 
•	Department 
•	Job Role 
•	Overtime 
•	Experience 
•	Performance Metrics 
Dimension Tables
DimEmployee
•	Employee Number 
•	Gender 
•	Marital Status 
•	Education 
DimDepartment
•	Department 
•	Job Role 
DimTime (Optional)
Created for trend reporting if historical snapshots are available.
Relationships
•	One-to-Many relationships established. 
•	Single-direction filtering used for performance optimization. 
DAX Measures
Total Employees
Total Employees = COUNT(Employee[EmpID])
Attrition Count
Attrition Count =
CALCULATE(
COUNT(Employee[EmpID]),
Employee[Attrition]="Yes"
)
Active Employees
Active Employees =
[Total Employees]-[Attrition Count]
Attrition Rate
Attrition Rate =
DIVIDE([Attrition Count],[Total Employees],0)*100
Average Monthly Income
Average Income =
AVERAGE(Employee[MonthlyIncome])
________________________________________
Numerical Analysis
Workforce Overview
KPI	Value
Total Employees	1,480
Active Employees	1,242
Employees Left	238
Attrition Rate	16.08%
Average Monthly Income	₹6,505
________________________________________
Attrition Analysis
Overall Attrition
Metric	Value
Employees Left	238
Attrition Rate	16.08%
Insight
Approximately 1 out of every 6 employees has left the organization, indicating moderate employee turnover.
________________________________________
Department-wise Attrition
Department	Attrition Count
Research & Development	133
Sales	93
Human Resources	12
Insight
•	Research & Development contributes the highest number of employee exits. 
•	Sales department shows the second-highest attrition level. 
•	Combined, these two departments account for over 94% of total attrition. 
________________________________________
Gender Analysis
Gender	Attrition Count
Male	151
Female	87
Insight
•	Male employees contribute approximately 63% of total attrition. 
•	Retention initiatives may need additional focus on male workforce segments. 
________________________________________
Age Group Analysis
Age Group	Attrition Count
18–25	44
26–35	116
36–45	43
46–55	27
55+	8
Insight
•	Employees aged 26–35 years experience the highest attrition. 
•	Nearly half of all resignations come from this age group. 
•	This indicates career growth and compensation may be major concerns. 
________________________________________
Job Role Analysis
Highest Attrition Roles
Job Role	Attrition Count
Laboratory Technician	62
Sales Executive	58
Research Scientist	47
Sales Representative	33
Human Resources	12
Insight
•	Laboratory Technicians and Sales Executives face the highest turnover. 
•	These roles may require better career progression opportunities and engagement programs. 
________________________________________

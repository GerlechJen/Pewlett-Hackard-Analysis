# Pewlett Hackard Analysis
## Overview of the Analysis
Pewlett Hackard, a large company with several thousand employees is seeing its staff begin to retire at a rapid rate.  The company wants to handle this by offering retirement package for those who meet certain criteria and also wants to know which positions will need to be filled soon as there will be thousands of job openings following the retirements. They want to future-proof the company and stay prepared for the many vacancies that will be created. Using SQL, an employee database was created from six CSV files to determine employees who will be retiring in the next few years, and, of those employees, who is eligible for a retirement package, as well as how many positions will need to be filled by Pewlett Hackard.

In this project, the number of retiring employees per title will be determined. Employees who are eligible to participate in a mentorship program will also be identified. 

## Results 
Using the code: 
```SQL
SELECT COUNT(emp_no) as Total_employees
FROM employees;
```
The total number of employees at Pewlett Hackard was found to be 300,024. 

```SQL
SELECT COUNT(emp_no)
FROM unique_titles;
```
The code above also generates 72,458 employees as retiring employees.

* Out of the 300,024 total employees at Pewlett Hackard if 72,458 employees will be retiring, that implies 24.15% of total employees will be retiring soon. 

* Of the 72,458 employees likely to retire soon, about 70% of them are Senior Engineers and Senior Staff. 25,916 Senior Engineers which represents (35.77%) and 24,926 Senior Staff which represents (34.4%) will be retiring soon.

* 1,549 employees are eligible to participate in Pewlett Hackard’s mentorship program. Therefore, the ratio of mentor to employee is 1:47.
* 
## Summary 

How many roles will need to be filled as the "silver tsunami" begins to make an impact?
As the "silver tsunami" begins to make an impact, 72,458 roles will need to be filled.

Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
No there are not enough qualified, retirement-ready employees to mentor the next generation of employees. The ratio of mentor to mentee obtained was 1:47 which is too high if we want a successful mentorship program. 


recommendation- find the retiring people by departments.write teh querry and resulting table for that. 

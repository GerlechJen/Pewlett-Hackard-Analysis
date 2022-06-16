# Pewlett Hackard Analysis
## Overview of the Analysis
Pewlett Hackard, a large company with several thousand employees is seeing its staff begin to retire at a rapid rate.  The company wants to handle this by offering retirement package for those who meet certain criteria.The company would also want to know which positions will need to be filled soon as there will be thousands of job openings following the retirements. Pewlett Hackard wants to be future-proof and stay prepared for the many vacancies that will be created. Using SQL, an employee database was created from six CSV files to determine employees who will be retiring in the next few years, and, of those employees, which of them are eligible for a retirement package, as well as how many positions will need to be filled by Pewlett Hackard.

The purpose of this further analysis in this project is to determine the number of retiring employees per title and identify employees who are eligible to participate in a mentorship program. An employee database will be built with SQL by applying data modeling, engineering and analysis skills.

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
The code above also generates 72,458 employees as the number of retiring employees who were born between 1952 and 1955.

* Out of the 300,024 total employees at Pewlett Hackard if 72,458 employees will be retiring, that represents 24.15% of total employees who will be retiring soon. 

* As ssen from th etable above, of the 72,458 employees likely to retire soon, about 70% of them are Senior Engineers and Senior Staff. Thenumber of Senior Engineers retiring soon is  25,916  which represents 35.77% and the number of Senior Staff retiring soon is 24,926 which represents 34.4%.

* From the mentorship eligibility table above, using the code
```SQL
SELECT COUNT(emp_no)
FROM mentorship_eligibility;
```

the count of eligible retiring employees who can participate in Pewlett Hackard’s mentorship program is 1,549 employees. The number of retiring employees obtained earlier was 72,458. Therefore, the ratio of mentor to mentee is 1:47.
* 
## Summary 

How many roles will need to be filled as the "silver tsunami" begins to make an impact?
As the "silver tsunami" begins to make an impact 72,458 roles will need to be filled.

Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?
No there are not enough qualified, retirement-ready employees to mentor the next generation of employees. The ratio of mentor to mentee obtained was 1:47 which is too high if we want a successful mentorship program. 

Using the code below:
```SQL
SELECT COUNT(e.emp_no),
	d.dept_name
INTO mentorship_departments
FROM employees as e
INNER JOIN dept_emp as de
ON e.emp_no = de.emp_no
INNER JOIN departments as d
ON d.dept_no = de.dept_no
WHERE (de.to_date = '9999-01-01')
AND (e.birth_date BETWEEN '1965-01-01' AND '1965-12-31')
GROUP BY d.dept_name
ORDER BY count DESC;
```
a mentorship by department table was obtained. The table provides us with additional information on the number of mentors available per department for the mentorship program. 

recommendation- find the retiring people by departments.write teh querry and resulting table for that. 

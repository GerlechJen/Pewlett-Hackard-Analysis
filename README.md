# Pewlett Hackard Analysis
## Overview of the Analysis
Pewlett Hackard, a large company with several thousand employees is seeing its staff begin to retire at a rapid rate.  The company wants to handle this by offering retirement package for those who meet certain criteria.The company would also want to know which positions will need to be filled soon as there will be thousands of job openings following the retirements. Pewlett Hackard wants to be future-proof and stay prepared for the many vacancies that will be created. Using SQL, an employee database was created from six CSV files by applying data modeling, engineering and analysis skills. The number of employees who will be retiring in the next few years, and, of those employees, which of them are eligible for a retirement package, as well as how many positions will need to be filled by Pewlett Hackard were determined.

In this project, further analysis will be performed on the employee database to determine the number of retiring employees per title and also identify employees who are eligible to participate in a mentorship program. A report will also be written to summarize the analysis so that the company will be well prepared for this "silver-tsunami".

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

* Out of the 300,024 total employees at Pewlett Hackard 72,458 employees will be retiring. This represents 24.15% of total employees who will be retiring soon. 

![image3](https://github.com/GerlechJen/Pewlett-Hackard-Analysis/blob/main/IMAGES/retiring_titles.png)

* As seen from the table above, of the 72,458 employees likely to retire soon, about 70% of them fall under Senior Engineers and Senior Staffs. The number of Senior Engineers retiring soon is  25,916  which represents 35.77% and the number of Senior Staff retiring soon is 24,926 which represents 34.4%. There were just 2 Managers who would be retiring soon.

* The number of employees who are eligible for the mentorship program was counted using the code below:

```SQL
SELECT COUNT(emp_no)
FROM mentorship_eligibility;
```

  The number of eligible retiring employees who can participate in Pewlett Hackard’s mentorship program is 1,549 employees. 

* The number of retiring employees obtained earlier is 72,458 and the number of employees who are eligible for the mentorship program is 1,549. Therefore, the ratio of mentor to mentee is 1:47.
 
## Summary 

1. How many roles will need to be filled as the "silver tsunami" begins to make an impact?

From the analysis performed, as the "silver tsunami" begins to make an impact 72,458 roles will need to be filled. This is based on if all the current employees who were born between the years 1952 and 1955 actually retire as that was the basis of the analysis. 

2. Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees?

The ratio of mentor to mentee obtained from our calculations was 1:47 which is too high if we want a successful mentorship program. So there are not enough qualified, retirement-ready employees to mentor the next generation of employees. To ensure that the mentees are gaining the required knowledge, skills, experience, information, and advice mentors should be more. This can be attained by including other year groups instead of limiting the mentors to just those who were born between January 1, 1965 and December 31, 1965.

Some additional tables have been created to provide more insight into the analysis. Using the code below:

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

A mentorship by department table was created. The table provides us with additional information on the number of mentors available per department for the mentorship program. 

![image1](https://github.com/GerlechJen/Pewlett-Hackard-Analysis/blob/main/IMAGES/mentorship_departments.png)

Another table, retirement_departments was created using the code below:

```SQL
SELECT COUNT(e.emp_no),
	d.dept_name
INTO retirement_departments
FROM employees as e
INNER JOIN dept_emp as de
ON e.emp_no = de.emp_no
INNER JOIN departments as d
ON d.dept_no = de.dept_no
WHERE (e.birth_date BETWEEN '1952-01-01' AND '1955-12-31')
AND (to_date = '9999-01-01')
GROUP BY dept_name
ORDER BY count DESC;
```
The retirement_departments table which shows the number of employees retiring from each department is shown below:

![image2](https://github.com/GerlechJen/Pewlett-Hackard-Analysis/blob/main/IMAGES/retirement_departments.png)

Looking at the employees likely to retire soon based on department, the majority of the employees work in the Development Department, followed by Production, Sales, Customer Service, Research, Quality Management, Marketing, Human Resources and Finance Departments.
The retirement_departments and mentorship_departments tables help us to have a clear picture of the number of employees likely to retire from each department and also the number of mentors available per department. From these two tables we can find the ratio of mentor to mentee for a specific department.


----

**Completed by:** Jennifer Anno-Kusi

**Email:** jannokusi@gmail.com 

# SQL_querry
Learning place 

### SQL Query to define top earning salary multiply months 
```
select max(salary*months) AS TOTAL, count(employee_id) 
from employee 
where (salary*months) = (select max(salary*months)from employee)
```

### Query to Roud data with AVG inside
```
SELECT ROUND(AVG(Columsname) ,0) AS "Rounded Avg."
FROM TableName;
```

### Example Query CEIL, AVG , and Replace
```
SELECT CEIL((AVG(salary)) - (AVG(REPLACE(salary, '0', '')))) AS avg_salary FROM employees;
```
REPLACE() : used to remove 0 from salary.
AVG() : used to calculate average salary.
CEIL() : used to get next rounded integer.

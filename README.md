# SQL_querry
Learning place 

##SQL querry to define top earning salary multiply months 

---
select max(salary*months) AS TOTAL, count(employee_id) from employee where (salary*months) = (select max(salary*months)from employee)
---

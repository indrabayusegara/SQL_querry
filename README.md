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

### Example Query to Round and sum with decimal in inside 
```
select round(sum(lat_n),2), round(sum(long_w),2) from station
```
### Example Query sum with (AND) conditions 
```
SELECT ROUND(SUM(lat_n),4) 
FROM station 
WHERE lat_n > 38.7880 AND lat_n < 137.2345; 
```
### Example Using Query MAX with Decimal 
```
SELECT ROUND(MAX(LAT_N),4) FROM station where LAT_N < 137.2345; 
```
### Example Using Query to Search Max value and Using Where (SUB Select)
```
SELECT ROUND(MAX(LONG_W),4) FROM station WHERE LAT_N = (select MAX(LAT_N) FROM station WHERE LAT_N < 137.2345)
```
### Example Using Query to Search Min Value and using Where
```
SELECT ROUND(MIN(LAT_N),4) FROM station WHERE LAT_N > 38.7780
```
### Example Using Query to search MIN Value Using Where (SUB Select)
```
SELECT ROUND(MIN(LONG_W),4) FROM Station where LAT_N = (SELECT MIN(LAT_N) FROM station WHERE LAT_N > 38.7780)
```
### Example Using Query Between Point P1 and P2 
Consider P1 (a, b) and P2 (c, d) to be two points on a 2D plane.
• a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
• b happens to equal the minimum value in Western Longitude (LONG_W in STATION)
• c happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
• d happens to equal the maximum value in Western Longitude (LONG_W in STATION).
Query the Manhattan Distance between points P, and P2 and round it
to a scale of 4 decimal places.
```
SELECT ROUND(ABS(MIN(LAT_N)-MAX(LAT_N))+ABS(MIN(LONG_W)-MAX(LONG_W)),4)
FROM STATION;
```
### Example query Using SQRT AND POWER 
The purpose of the SQL POWER function is to raise one number to the power of another number.
In other words, this could be n1^n2
It’s useful for squaring or cubing numbers.
The purpose of the SQL SQRT function is to find and return the square root of a provided number.
The square root of a particular number answers this question:
“Which number, when multiplied by itself, will give me my original number?”
For example, the square root of 25 is equal to 5. This is because 5 * 5 = 25.
The square root of 9 is 3, because 3 * 3 = 9.
It doesn’t always have to be a whole number, as you’ll see in the examples section below.
This function exists in Oracle, SQL Server, MySQL, and Postgres. In MySQL, the POWER function is the same as the POW function. 

EXAMPLE 1 :
```
SELECT
    ROUND(SQRT(
        POWER(MAX(LAT_N)  - MIN(LAT_N),  2)
      + POWER(MAX(LONG_W) - MIN(LONG_W), 2)
    ), 4)
FROM 
    STATION;
```
EXAMPLE 2 : 
```
SELECT ROUND(SQRT(POWER(MIN(LAT_N)-MAX(LAT_N),2)+POWER(MIN(LONG_W)-MAX(LONG_W),2)),4)
FROM STATION;
```
### Example MEDIAN in Query 
```
SELECT ROUND(S.LAT_N, 4) 
FROM STATION S 
WHERE
(SELECT COUNT(LAT_N) FROM STATION WHERE LAT_N > S.LAT_N) = (SELECT COUNT(LAT_N) FROM STATION WHERE LAT_N < S.LAT_N);
```

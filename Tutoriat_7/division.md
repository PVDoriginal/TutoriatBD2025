# Division 

[Division](https://www.geeksforgeeks.org/sql-division/) is an abstract operation used when we want to get entities that meet certain conditions based on 'all' entities from another set. 

There are generally 2 ways to write division: 
  - **Not exists** - we get all entities from the set for which there doesn't exist a condition they're not meeting.
  - **Union and Minus** - we substract and add entities repeatedly to get the right ones. 

# Exercises

Ex 1
```
Get employees that had only high-paying jobs (min_salary >= 10.000).
Should be 100. 
```


<details>
  <summary> Solution 1 </summary>
  
  ```sql
SELECT *
FROM employees e
WHERE NOT EXISTS(
    SELECT *
    FROM jobs j JOIN job_history h ON (j.job_id = h.job_id)
    WHERE j.min_salary < 10000 AND h.employee_id = e.employee_id
);
  ```
</details>

<details>
  <summary> Solution 2 </summary>
  
  ```sql
SELECT employee_id
FROM employees

MINUS

SELECT e.employee_id
FROM employees e
JOIN job_history h ON (h.employee_id = e.employee_id)
JOIN jobs j ON (j.job_id = h.job_id)
WHERE j.min_salary < 10000;
  ```
</details>

Ex 2 
```
Get departments for which all employees have salaries greater than the average salary of employees in at least 3 other departments. 
```

Ex 3 
```
Get departments for which all employees are on their first job (no entries in job_history)
```

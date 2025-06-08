# Views

## Definition

Views are virtual tables whose content is defined by a query. The data is not actually stored inside of them, but it is referenced from the other tables. Everything is determined on runtime so if a column from a view uses an aggregate function(SUM, AVG etc) on a column from another table, and the referenced table is changed, than the values for that column can change as well.

## Uses

- Intermediate steps for a big query(as will be seen below)
- Re-use if a query(or part of it) appears in multiple places

## Exercises

### Ex1

```
Employees who work in a city starting with the letter S,
that have a salary that's greater that the average between the min salary and max salary of their job and
that work in a department that has at least 5 employees
```

<details>
  <summary> Solution </summary>

```sql
/* SOLUTION 1, no views*/
SELECT e.employee_id, l.city, e.salary, (j.min_salary + j.max_salary) / 2 AS "job_avg_salary"  FROM employees e 
JOIN departments d ON e.department_id = d.department_id
JOIN locations l ON l.location_id = d.location_id
JOIN jobs j ON j.job_id = e.job_id
WHERE UPPER(l.city) LIKE 'S%' AND e.department_id IN(
    SELECT department_id FROM employees
    GROUP BY department_id HAVING department_id IS NOT NULL AND COUNT(employee_id) > 5)
    AND e.salary > (j.min_salary + j.max_salary) / 2;

/* SOLUTION 2, with views*/
CREATE OR REPLACE VIEW dep_at_least_5_emp AS
SELECT department_id FROM employees
GROUP BY department_id HAVING department_id IS NOT NULL AND COUNT(employee_id) > 5;

CREATE OR REPLACE VIEW emp_from_city_starts_with_S AS
SELECT e.employee_id ,l.city, e.department_id FROM employees e 
JOIN departments d ON e.department_id = d.department_id
JOIN locations l ON l.location_id = d.location_id
WHERE UPPER(l.city) LIKE 'S%';

CREATE OR REPLACE VIEW emp_with_salary_greater_than_job_avg AS
SELECT e.employee_id, e.salary, e.job_id, (j.min_salary + j.max_salary) / 2 AS "AVG_SALARY" FROM employees e
JOIN jobs j ON j.job_id = e.job_id
WHERE e.salary > (j.min_salary + j.max_salary) / 2;

SELECT e.employee_id, e.city, d.department_id, ej.avg_salary FROM emp_from_city_starts_with_S e
JOIN dep_at_least_5_emp d ON d.department_id = e.department_id
JOIN emp_with_salary_greater_than_job_avg ej ON ej.employee_id = e.employee_id;

```

</details>

## Ex2

```
Fetch all departments that have the total salary of the employees greater than the average of all total salaries of the departmens

```

<details>
  <summary> Solution </summary>

```sql
CREATE OR REPLACE VIEW dep_tot_sal AS 
SELECT department_id, SUM(salary) total_salary FROM employees
GROUP BY department_id HAVING department_id IS NOT NULL;

SELECT department_id, total_salary FROM dep_tot_sal
WHERE total_salary > (SELECT AVG(total_salary) FROM dep_tot_sal);

```

</details>
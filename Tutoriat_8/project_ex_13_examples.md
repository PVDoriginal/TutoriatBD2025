# Citing from the project's exercises:

`13. Implementarea a 3 operații de actualizare și de suprimare a datelor utilizând subcereri.`

in english

`13. Implement 3 delete and update operations that use subqueries`

## Examples using HR-diagram

Note: The rollback is not neccesary(as in not part of the exercises), but recommended, it's only reverts back the changes done on the database

### Ex 1

```
Eliminate employees that have salary below the average
```

<details>
  <summary> Solution </summary>

```sql
    DELETE FROM employees e
    WHERE salary < (
        SELECT AVG(salary) FROM employees
    );

    ROLLBACK;
```
</details>

### Ex 2

```
Eliminate departments that have no employees
```

<details>
  <summary> Solution</summary>

```sql
DELETE FROM departments 
WHERE department_id NOT IN 
    (SELECT DISTINCT department_id FROM employees WHERE department_id IS NOT NULL);

ROLLBACK;
```

</details>

### Ex 3

```
Give 1.10 bonus to the salary of the employees that work in the biggest department(the one that has the most employees)
```

<details>
  <summary> Solution</summary>

```sql
UPDATE employees
SET salary = salary * 1.10
WHERE department_id = (
    SELECT department_id
    FROM (
        SELECT department_id
        FROM employees
        GROUP BY department_id
        ORDER BY COUNT(*) DESC
    )
    WHERE ROWNUM = 1
);

ROLLBACK;
```

</details>

### Ex 4

```
Set salary of employees to min_salary if below the average of their job and to max_salary otherwise
```

<details>
  <summary> Solution</summary>

```sql
UPDATE employees e
SET salary = (
    SELECT CASE
        WHEN e.salary < (j.min_salary + j.max_salary) / 2 THEN j.min_salary
        ELSE j.max_salary
    END
    FROM jobs j
    WHERE e.job_id = j.job_id
);

ROLLBACK;
```

</details>

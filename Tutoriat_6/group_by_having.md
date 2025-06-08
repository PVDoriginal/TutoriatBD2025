# Filtering group by using having

## Some background

Remember group by literally groups by information based on the columns we group by, usually paired together with aggregate functions on some columns not used in a group by.

Just like we have WHERE in SELECT clauses, we have HAVING in GROUP BY clauses, they filter by conditions using the columns used for grouping or any other aggregate function on any other column

Note: WHERE is always **BEFORE** GROUP BY and HAVING,
you first select what you need(SELECT), filter it(WHERE), group it (GROUP BY) and then filter what you have grouped (HAVING)

## Exercises

### Ex1

```

Sa se afiseze departamentele(id-ul) si numarul de angajatii din acele departamente,
doar pentru departamentle cu mai mult de 20 de angajati
```

<details>
  <summary> Solutie </summary>

```sql
SELECT department_id, COUNT(employee_id) AS employee_count FROM employees
GROUP BY department_id HAVING COUNT(employee_id) > 20;
```

</details>

### Ex2

```
Sa se afiseze departamentele(numele) si salariul cumulat al angajatilor din departamentele respective,
pentru departamentele ce incep cu litera 'T'
```

<details>
  <summary> Solutie </summary>

```sql
SELECT d.department_name, SUM(e.SALARY) "salary_sum" FROM employees e
JOIN departments d ON d.department_id = e.employee_id
GROUP BY d.department_name HAVING d.department_name LIKE 'T%';
```

</details>

### Ex3

```
Sa se afiseze joburile(id-ul) si numarul de angajati cu joburile respective, pentru toate joburile care au 
   prima litera a titlului de job 'S'
job_id and number of employees for all jobs that start with the letter 'S'
```

<details>
  <summary> Solutie </summary>

```sql
SELECT job_id, COUNT(employee_id) FROM employees
GROUP BY job_id HAVING job_id IN (SELECT job_id FROM jobs WHERE job_title LIKE 'S%');
```

</details>

### Ex4

```
Select the number of employees, their summed salary and the city in which their department is situated, taking into account only cities that have the employee salary sum greater than average
```
<details>
  <summary> Solutie </summary>

```sql
select count(EMPLOYEE_ID) "NR. ANGAJATI", CITY, SUM(salary) "SUMA SALARIILOR"
from LOCATIONS l join DEPARTMENTS d on (d.LOCATION_ID = l.LOCATION_ID)
join EMPLOYEES e on (e.DEPARTMENT_ID = d.DEPARTMENT_ID)
group by CITY having SUM(salary) > AVG(salary);
```

</details>
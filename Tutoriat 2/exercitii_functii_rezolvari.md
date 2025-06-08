# Rezolvari si observatii

Note: Nu toate exercitiile sunt rezolvate, sa va bateti putin capu (am pierdut rezolvarile)

## Ex1

```sql
/*TO_DATE converteste arg2 la tipul de date DATE folosind formatul de la arg1*/
/* Using default format*/
SELECT * FROM job_history WHERE start_date >= '12-JUN-1993';
/*No conversion*/
SELECT * FROM job_history WHERE start_date >= '12/06/1993';
/*Conversion*/
SELECT * FROM job_history WHERE start_date >= TO_DATE('12/06/1993', 'DD/MM/YYYY');

```

## Ex2

```sql
/*NVL pune arg2 in locul lui arg1 daca arg1 e NULL si incearca sa converteasca arg2 la tipul lui arg1*/

SELECT department_id, manager_id FROM departments;
/* No covnersion*/
SELECT department_id, nvl(manager_id, 'NO MANAGER') FROM departments;
/* Conversion*/
SELECT department_id, nvl(to_char(manager_id), 'NO MANAGER') FROM departments;

```

## Ex3 - nu chiar, dar asemanator

Note: Ex 3, 4, 5 sunt pe acelasi principiu ca cel de mai jos, dar cel de mai jos nu e rezolvarea niciunuia

```sql
/* Sa se afiseze toate joburile al caror id incepe cu ST*/
/* Like face pattern matching, _ tine locul unui caracter oarecare, % tine locul a oricate caractere*/
SELECT * FROM jobs WHERE job_id LIKE 'ST%';
```

## Ex7 - nu chiar, dar asemanator

Note: Ex7 e fix asta doar ca asta e putin mai complicat (va puteti da seama de ce?)

```sql
/* Decode e short circuit, tipul lui expr si al search-urilor sunt determinate de primul search
valoare returnata este convertita la primul result. Daca result e CHAR sau NULL, tipul sau devine VARCHAR2
NULL = NULL*/
SELECT employee_id, DECODE(
           SIGN(salary - (SELECT AVG(salary) FROM employees)), 
           -1, 'Low', 
            0, 'Medium',
            1, 'High'
       ) AS salary_category FROM employees;
```

## Ex8

```sql
/* CASE e if-ul din orice limbaj imperativ ca C/C++*/
SELECT job_id, CASE 
            WHEN max_salary - min_salary <= 3000 THEN 'SMALL GAP'
            WHEN max_salary - min_salary BETWEEN 3000 AND 5000 THEN 'MEDIUM GAP'
            WHEN max_salary - min_salary >= 5000 THEN 'MEDIUM GAP'
        END
        AS salary_gap_category FROM jobs;
```

## Ex10 - Dumnezeu cu mila

```sql
/* BIG EXAMPLE*/
SELECT employee_id, first_name || ' ' || last_name AS full_name, nvl(to_char(department_id), 'NO DEPARTMENT') AS department,
       CASE 
            WHEN commission_pct IS NULL THEN 'NO COMMISSION'
            WHEN commission_pct < 0.2 THEN 'SMALL COMMISSION'
            WHEN commission_pct BETWEEN 0.2 AND 0.3 THEN 'MEDIUM COMMISSION'
            ELSE 'BIG COMMISSION'
        END commission_category,
        DECODE(
           SIGN((sysdate - hire_date) - (SELECT AVG(sysdate - hire_date) FROM employees)), 
               -1, 'LOW', 
                0, 'MEDIUM', 
                1, 'HIGH'
        ) AS work_experience_category
        FROM employees 
        WHERE hire_date >= TO_DATE('24.03.1990', 'DD.MM.YYYY') AND
              phone_number LIKE '515%' OR
              last_name LIKE '%G' 
        ORDER BY first_name, last_name;
```

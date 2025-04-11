Exercitiile se fac pe [diagrama HR](https://github.com/PVDoriginal/TutoriatBD2025/blob/Sapt-1/Diagrama%20HR/diagrama_HR.pdf).

## Reminder

Exista [mai multe tipuri de join](https://www.oracletutorial.com/oracle-basics/oracle-joins/): 
- join 
- join on [conditie]
- full (outer) join 
- left / right join
- natural join

Ex 1
```
Afisati numele anjajatilor din departamentul 50. 
```
<details>
  <summary> Solutie </summary>
  
  ```SQL
  SELECT first_name, last_name, DEPARTMENT_ID
  FROM EMPLOYEES
  WHERE DEPARTMENT_ID = 50;
  ```

</details>


Ex 2
```
Afisati nuemele angajatilor cu salariul intre 5000 si 6000.
```
<details>
  <summary> Solutie </summary>
  
  ```SQL
  SELECT first_name, last_name, SALARY
  FROM EMPLOYEES
  WHERE 5000 <= SALARY AND SALARY <= 6000;
  ```

</details>


Ex 3
```
Afisati numele angajatilor care lucreaza in departamentul "Administration".
```
<details>
  <summary> Solutie </summary>
  
  ```SQL
  SELECT first_name, last_name, DEPARTMENT_NAME, EMPLOYEES.DEPARTMENT_ID
  FROM EMPLOYEES JOIN DEPARTMENTS ON (EMPLOYEES.DEPARTMENT_ID = DEPARTMENTS.DEPARTMENT_ID)
  WHERE LOWER(DEPARTMENT_NAME) = 'administration';
  ```

</details>

Ex 5
```
Afisati numele departamentelor si a angajatilor ce lucreaza in ele. 
```
<details>
  <summary> Solutie </summary>
  
  ```SQL
  SELECT FIRST_NAME, DEPARTMENT_NAME
  FROM EMPLOYEES FULL JOIN DEPARTMENTS ON (EMPLOYEES.DEPARTMENT_ID = DEPARTMENTS.DEPARTMENT_ID);
  ```

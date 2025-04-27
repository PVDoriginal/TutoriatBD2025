Exercitiile se fac pe [diagrama HR](https://github.com/PVDoriginal/TutoriatBD2025/blob/Sapt-1/Diagrama%20HR/diagrama_HR.pdf).

Documentatie Group By: 
  - [W3Schools](https://www.w3schools.com/sql/sql_groupby.asp)
  - [Oracle](https://docs.oracle.com/en/database/other-databases/nosql-database/24.3/sqlreferencefornosql/group-clause.html)

Ex 1 
```
Sa se afiseze maximul salariilor angajatilor din fiecare departament.  
```
![image](https://github.com/user-attachments/assets/765c7495-e4e2-4edf-be5e-5805b1706c5c)

<details>
  <summary> Solutie </summary>
  
  ```SQL
  select DEPARTMENT_ID, MAX(SALARY)
  from EMPLOYEES
  group by DEPARTMENT_ID;
  ```

</details>


Ex 2
```
Sa se afiseze numarul de departamente pentru fiecare oras.
```
![image](https://github.com/user-attachments/assets/c87889aa-1730-463d-8738-fc71f031daa1)
<details>
  <summary> Solutie </summary>
  
  ```SQL
  select count(DEPARTMENT_ID) "NR. DEPARTAMENTE", CITY
  from LOCATIONS l join DEPARTMENTS d on (d.LOCATION_ID = l.LOCATION_ID)
  group by CITY;
  ```

</details>

Ex 3 
```
Sa se afiseze numarul de angajati din fiecare oras.
```
![image](https://github.com/user-attachments/assets/b5d9ed0e-68e7-47cb-af96-1622fc5d0e45)
<details>
  <summary> Solutie </summary>
  
  ```SQL
  select count(EMPLOYEE_ID) "NR. ANGAJATI", CITY
  from LOCATIONS l join DEPARTMENTS d on (d.LOCATION_ID = l.LOCATION_ID)
                   join EMPLOYEES e on (e.DEPARTMENT_ID = d.DEPARTMENT_ID)
  group by CITY;
  ```

</details>

Ex 4 
```
Sa se afiseze cel mai mic salariu din fiecare oras. 
```
![image](https://github.com/user-attachments/assets/8d708a4b-8f69-4b33-866b-05e080dfa159)
<details>
  <summary> Solutie </summary>
  
  ```SQL
  select min(SALARY), CITY
  from LOCATIONS l join DEPARTMENTS d on (d.LOCATION_ID = l.LOCATION_ID)
                   join EMPLOYEES e on (e.DEPARTMENT_ID = d.DEPARTMENT_ID)
  group by CITY;
  ```

</details>




Exercitiile se fac pe [diagrama HR](https://github.com/PVDoriginal/TutoriatBD2025/blob/Sapt-1/Diagrama%20HR/diagrama_HR.pdf).

#### Linkuri folositoare:
- [LIKE](https://docs.oracle.com/cd/B13789_01/server.101/b10759/conditions016.htm)
- [DECODE](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/DECODE.html)
- [CASE](https://docs.oracle.com/cd/B19306_01/server.102/b14200/expressions004.htm)
- [NVL](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/NVL.html)
- [SIGN](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/SIGN.html)
- [TO_DATE](https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/TO_DATE.html)
- [ORDER BY](https://docs.oracle.com/en/database/other-databases/nosql-database/22.3/sqlreferencefornosql/order-clause.html)
- [AVG](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/AVG.html)
- [BETWEEN](https://docs.oracle.com/en/database/oracle/oracle-database/23/sqlrf/BETWEEN-Condition.html)

Ex1: 

```
Selectati toate istoricele de posturi(job_history) ce au ca data de inceput 12 iunie 1993.
```

Ex2:

```
Selectati codul de departament si codul managerului din acesta, inlocuind NULL cu 'NO MANAGER'.
```

Ex3

```
Selectati angajatii al caror nume de familie incepe cu S.
```

Ex4

```
Selectati angajatii al caror email incepe cu S si are a 3 litera e.
```

Ex5

```
Selectati angajatii al caror titlu incepe cu M (titlul e parte din job_id, pentru PU_CLERK este CLERK, pt HR_REP este REP)
```

Ex6

```
Selectati angajatii care au o zecimala la comision(ce se intampla cand vede null?)
```

Ex7

```
Selectati codul angajatilor si asignati salarilor o eticheta conform urmatoarelor reguli:
    salary < 3000 -> 'Low',
    salary = 3000 -> 'Medium',
    salary > 3000 -> 'High'
    hint: Puteti folosi SGN(expr)
```

Ex8

```
Selectati codul joburilor si asignati o eticheta diferentelor dintre salariul maxim si salariul minim conform urmatoarelor reguli
    salary_gap <= 3000 -> 'SMALL GAP'
    salary_gap apartine (3000, 5000) -> 'MEDIUM GAP'
    salary_gap >= 5000 -> 'HIGH GAP'

```

Ex9

```
Selectati numele complet al angajatului, salariul, numarul de ani experienta, codul de departament si
   asignati o eticheta de bonus conform urmatoarelor reguli:
            salary < 3000 AND ani_experienta < 2 -> 'No Bonus'
            salary < 3000 AND ani_experienta >= 2 -> '5% Bonus'
            salary apartine (3000, 7000) -> '7% Bonus'
            salary apartine (3000, 7000) AND department_id = 100 -> '10% Bonus'
            salary > 7000 AND ani_experienta > 5 -> '15% Bonus'
    hint: date1 - date2 -> nr de zile (in format fractionar) dintre date1 si date2
```

Ex10

```
 Selectati codul angajatului, numele complet, numarul de telefon, codul de departament(daca nu are, afisati mesajul 'NO DEPARTMENT'),
    asignati o categorie punctelor de comision conform urmatoarelor reguli:
        fara commission_pct -> 'NO COMMISSION'
        commission_pct < 0.2 -> 'SMALL COMMISSION'
        commission_pct apartine(0.2, 0.3) -> 'MEDIUM COMMISSION'
        altfel -> 'BIG COMMISSION'
    asignati o categorie experientei de munca(nr de zile lucrate pana in prezent)
    conform urmatoarelor reguli(hint: folositi subquery pentru avg_work_exp):
        work_exp < avg_work_exp -> 'LOW', 
        work_exp = avg_work_exp -> 'MEDIUM', 
        work_exp > avg_work_exp -> 'HIGH'
    pentru angajatii care s-au angajat dupa data de 24 martie 1990 si (al caror nr de tel incepe cu 515 
    sau pentru care prenumele incepe cu G).
    Ordonati crescator dupa numele de familie, iar in caz de egalitate dupa prenume
```

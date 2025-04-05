## Linkuri folositoare

[Tipuri de comenzi SQL](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/Types-of-SQL-Statements.html#GUID-E1749EF5-2264-44DF-99EF-AEBEB943BED6)

[Tranzactii](https://docs.oracle.com/cd/E11882_01/server.112/e40540/transact.htm)

## Tipuri de comenzi SQL

- DDL
- DML
- TCS

## DDL - Data Definition Language

Comenzile DDL actioneaza asupra obiectelor din schema unui user(tabele, indecsi, view-uri, etc...), avand posibilitatea(in principal) de a creea, sterge, vizualiza sau altera obiectele. Atat inainte cat si dupa fiecare comanda de tipul asta se ruleaza `COMMIT` implicit de catre Oracle.

## DML - Data Manipulation Language

Comenzile DML actioneaza asupra datelor din tabele, avand posibilitatea(in principal) de a insera, sterge, vizualiza sau actualiza date. Spre deosebire de DDL, inaintea(sau dupa)comenzile DML nu se ruleaza `COMMIT`.

## TCS - Transaction Control Statements

Comenzile TCS actioneaza asupra tranzactilor create de comenzile DML.

### Ce e o tranzactie?

#### Definitie

O tranzactie reprezinta o unitate atomica, logica de lucru ce contine comenzi SQL. Ea se asigura ca un grup de comenzi ori sunt aplicate toate bazei de date ori niciuna.

#### Analogie

Va puteti gandi la o tranzactie ca fiind o copie a starii curente a bazei de date asupra careia sunt aplicate niste comenzi.

Cand SQL vede prima comanda DML face o "poza" starii curente a bazei de date asupra careia urmeaza sa faca toate modificarile.

#### COMMIT si ROLLBACK
Cand e rulat `COMMIT` aceasta stare devine starea reala a bazei de date, iar cand e rulat `ROLLBACK` schimbarile facute asupra starii intermediare sunt anulate si tranzactia e "distrusa".

#### SAVEPOINT

Imparte tranzactia in mai multe bucati la care putem da rollback in loc sa dam la intreaga tranzactie(ROLLBACK TO SAVEPOINT nume_savepoint).

### TL;DR

- COMMIT salveaza modificarile facute asupra bazei de date
- ROLLBACK anuleaza modificarile facute asupra bazei de date pana la ultimul COMMIT sau ROLLBACK
- SAVEPOINT ofera posibilitatea de a da rollback doar pana intr-un punct ales de noi

# Curs 1 - Introducere

Nimic interesant :( 

# Curs 2 - Diagrame

## Notatii 

- Tabele si Entitati inseamna in practica acelasi lucru.
- Cheie Primara = PK
- Cheie Straina = FK 
- Many = M 


## Cardinalitati Maxime(Minime)

![image](https://github.com/user-attachments/assets/be3d8207-3576-4e39-a164-e362077e8306)

Cardinalitatea din dreptul angajatului, M(1), ne spune ca un departament poate avea mai multi angajati, dar trebuie sa aibe minim 1. 
Similar, 1(0) in dreptul departamentului ne spune ca un angajat poate apartine unui departament, dar poate sa nu apartina niciunuia. 

Daca cardinalitatile minime si maxime coincid, se scrie direct cardinalitatea, fara paranteza. 

Cardinalitate Maxima <=> Cardinalitate Optionala
Cardinalitate Minima <=> Cardinalitate Obligatorie

## Tipuri de relatii

![image](https://github.com/user-attachments/assets/ede854ea-b074-4dbd-a736-1f536e19924b)

Relatia Serial - Episod este o relatie **One-to-Many**, iar Cont_Bancar - Card este **One-to-One**. 
Putem avea si relatii **Many-to-Many** si **Relatii de Tip 3** (vedeti mai jos).

## Subentitati si Superentitati

![image](https://github.com/user-attachments/assets/82e5b6aa-b5da-466b-a9cc-4fd4585db462)

In exemplul asta, avem o entitate Cont, care poate fi de doua tipuri, Curent sau Economii.
Cont se numeste supraentitate, Curent si Economii sunt subentitati, iar relatia dintre ele se numeste ISA ("is a" in engleza). 
Subentitatile vor avea toate atributele supraentitatii, iar cheia lor primara va fi o cheie straina simpla ce referentiaza cheia primara a supratabelului. 

Cardinalitatea vine de la faptul ca, Curent este un singur Cont, iar un Cont poate fi sau nu curent, rezultand in 1 si 1(0). 

## Entitati dependente 
Entitatile pot fi independente (strong) sau depdendente (weak). 
- Cele **dependente** depind de o alta entitate. De exemplu, entitatea Task nu ar putea exista exista fara entitatea Proiect din care face parte.
- Entitatile dependente au o cheie primara compusa din cheia primara a entitatii de care sunt dependente, plus alte atribute proprii (note: daca ar avea cheia primara formata doar din cheia celeilalte entitati, atunci ar fi subtabele).
- Acestea se deseneaza cu linie dubla.
- Daca nu e dependenta, e independenta,

## Exemplu de diagrama

![image](https://github.com/user-attachments/assets/b717ddbc-8fce-40ea-a041-6b5dae9affbe)

- Tehnologii - Programe este o relatie de tipul Many-to-Many. 
- Programe e supertabel, cu subtabelele Intership si Stagiu_Practica.
- Intre Studenti, Companii si Programe exista o relatie de tip 3, deoarece toate sunt conectate prin Many. Relatia se va desena ca un romb, iar in diagrama conceptuala se va transforma intr-un tabel asociativ. 
- Atestari este o entitate dependenta.

# Curs 3 - Caching

Nimic super interesant. Voi actualiza daca devine ceva de aici relevant.




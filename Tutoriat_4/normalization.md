# Normalizare si denormalizare

## Normalizarea

- Procesul prin care sunt eliminate redundantele dintr-o baza de date pentru evitarea anomaliilor la inserarea, actualizarea si stergerea datelor si folosirea unui nivel mai mic de stocare.

### Forme Normale

#### FN1 - Forma Normala 1

Fiecare coloana al fiecarui rand din baza de date are o singura valoare

Exemplu:

Inainte de normalizare

Pozitii_juc




![](FN1_before.png)

Dupa normalizare

Pozitii_juc




![](FN1_after.png)

#### FN2 - Forma Normala 2

Coloanele(dintr-un tabel) care nu fac parte din cheia primara sunt dependente de intreaga cheie primara

Exemplu:

Inainte de normalizare

Medic




![](FN2_before.png)

Dupa normalizare

Medic




![](FN2_after_medic.png)

Specializare




![](FN2_after_spec.png)

#### FN3 - Forma Normala 3

Coloanele care nu fac parte din cheia primara sunt dependente de intreaga cheie primara si doar de ea.

Exemplu:

Inainte de normalizare

Medic




![](FN3_before.png)

Dupa normalizare

Medic




![](FN3_after_medic.png)

Specializare




![](FN3_after_spec.png)

## Denormalizare

Procesul invers normalizarii, folositor cand vrem o baza de date mai simpla cu acces mai rapid la date (o baza de date care face mai multe read-uri decat write-uri).
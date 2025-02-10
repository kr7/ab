# Tervezési Feladat Minta

Tervezze meg egy sípálya adatbázisát, egy relációs adatbázist! 

(a) Adja meg a legfontosabb 3-5 adattáblát, ezek attribútumait (oszlopait), valamint ezek közötti kapcsolatokat egy egyed-kapcsolat (entitázs-relációs) diagramon.

(b) Adja meg az adattáblák létrehozásához szükséges SQL parancsokat!

(c) Adja meg egy Ön által üzletileg relevánsnak tartott lekérdezés SQL kódját! 

## Megoldás

![image](https://github.com/kr7/ab/assets/7807330/a3c08c9a-54a9-45de-a617-c4ca3e8ee69d)

(b)

```
create database sipalya;
use sipalya;


create table Ugyfel (
  azonosito varchar(10),
  nev varchar(20),
  lakcim varchar(20),
  primary key (azonosito) );


create table Felszereles (
  azonosito varchar(10),
  meret DECIMAL(3,1),
  primary key (azonosito) );


create table Berel (
  tol DATETIME,
  ig DATETIME, 
  ugyfel_azonosito varchar(10),
  felszereles_azonosito varchar(10), 
  foreign key (ugyfel_azonosito) 
    references Ugyfel(azonosito),
  foreign key (felszereles_azonosito) 
    references Felszereles(azonosito)
  );

```

A további entitázsokak és relációknak megfelelő táblák létrehozása a fentiekkel analóg módon történik.


(c) 

Lekérdezzük, hogy átlagosan mennyi időre bérelte ki az ügyfél a felszerelést:

```
select avg((ig-tol)/10000) as berles_hossza_oraban from Berel;
```

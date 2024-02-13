# Pekseg
Ez az adatbázis egy képzeletbeli pékség adatbázisa. Ez egy minimalisztikus példa, amely SQL lekérdezések tanulására és gyakorlására szolgál. 
Az alábbi SQL utasítások közvetlenül végrehajthatók MySQL-ben. 

A gyakorlatokon a MySQL szerver és kliens (MySQL Workbench) ugyanazon asztali gépre van telepítve. 
Ehhez a minimalisztikus példához bőven elég egy asztali gép teljesítménye.

# Az adatbázis létrehozása

```
create database Pekseg;

use Pekseg;

create table Aruk (
  cikkszam varchar(10) unique,
  megnevezes varchar(20),
  tomeg int,
  ar float,
  primary key (cikkszam) );

insert into Aruk values ("001","kifli", 50, 0.49);
insert into Aruk values ("002","zsemle", 60, 0.59);
insert into Aruk values ("003","kenyer", 500, 2.79);
insert into Aruk values ("004","nagy kenyer", 1000, 3.69);
insert into Aruk values ("005","tej", 500, 3.19);
insert into Aruk values ("006","kakao", 500, 4.99);
insert into Aruk values ("007","szendvics", 500, 5.99);

create table Vasarlok (
  vasarlo_id varchar(10) unique,
  nev varchar(20),
  cim varchar(50),
  primary key (vasarlo_id) );

insert into Vasarlok values ("V01", "Szupermarket Kft.", "1062 Budapest, Nyugati tér. 1.");
insert into Vasarlok values ("V02", "Pista Bacsi", "2400 Dunaujvaros, Kossuth Lajos u. 15.");
insert into Vasarlok values ("V03", "Eva neni", "2459 Racalmas, Petőfi Sándor u. 2.");

create table Tranzakciok (
  tranzakcio_id varchar(10),
  datum date,
  vevo varchar(10) null,
  termek varchar(10),
  mennyiseg int,
  foreign key (termek) references Aruk(cikkszam),
  foreign key (vevo) references Vasarlok(vasarlo_id));

insert into Tranzakciok values ("T0001", "2024-02-09", null, "001", 5);
insert into Tranzakciok values ("T0001", "2024-02-09", null, "005", 2);
insert into Tranzakciok values ("T0002", "2024-02-09", null, "007", 1);
insert into Tranzakciok values ("T0003", "2024-02-09", "V02", "003", 1);
insert into Tranzakciok values ("T0004", "2024-02-09", "V03", "002", 3);
insert into Tranzakciok values ("T0004", "2024-02-09", "V03", "005", 2);
insert into Tranzakciok values ("T0005", "2024-02-10", null, "002", 6);
insert into Tranzakciok values ("T0005", "2024-02-10", null, "005", 1);
insert into Tranzakciok values ("T0006", "2024-02-10", "V01", "007", 50);
insert into Tranzakciok values ("T0006", "2024-02-10", "V01", "007", 25);
insert into Tranzakciok values ("T0007", "2024-02-10", null, "007", 1);
insert into Tranzakciok values ("T0008", "2024-02-11", "V01", "007", 35);
insert into Tranzakciok values ("T0008", "2024-02-12", "V01", "007", 15);
```

# A MySQL szerveren található adatbázisok listázása

```
show databases;
```

# A "Pekseg" adatbázis tábláinak listázása

```
use pekseg;
show tables;
``` 

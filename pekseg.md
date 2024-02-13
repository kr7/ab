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

# Adatok lekérdezése, sorok és oszlopok kiválasztása, az eredmény rendezése

```
select * from Aruk;
select * from Aruk where ar > 1;
select megnevezes, ar from Aruk where ar > 1;
select megnevezes, ar from Aruk where ar > 1 order by ar;
select megnevezes, ar from Aruk where ar > 1 order by ar desc;
```

Ahhoz, hogy az eredményt rendezetten kapjuk, meg kell adnunk, hogy mi szerint rendezünk. Ennek hiányában az eredménytábla sorainak sorrendjére nincs semmilyen garancia (nem biztos, hogy pl. cikkszám szerint, vagy bármi más szerint, rendezettek):
```
select * from Aruk order by megnevezes;
```

```
select * from Vasarlok;
select * from Vasarlok where cim = '2459';
select * from Vasarlok where cim like '2459%';

select * from Tranzakciok limit 5;
select * from Tranzakciok where tranzakcio_id = 'T0001';
```

# Új sor (rekord, példány) beszúrása az adattáblába

Végrehajtható-e az alábbi utasítás? Miért? Tipp: lásd az adattábla létrehozását!
```
insert into Aruk values ('001','alma','100','1.99');
```

És az alábbi?
```
insert into Aruk values ('008','alma','100','1.99');
```

# Több táblára vonatkozó lekérdezések 

A "T0001" azonosítójú tranzakció mellé "odaírjuk" a termék megnevezését illetve árát:

```
select Tranzakciok.*, Aruk.megnevezes from Tranzakciok, Aruk 
where tranzakcio_id = 'T0001' and Tranzakciok.termek = Aruk.cikkszam;

select Tranzakciok.*, Aruk.megnevezes, Aruk.ar from Tranzakciok, Aruk 
where tranzakcio_id = 'T0001' and Tranzakciok.termek = Aruk.cikkszam;
```

Az alábbiak közül melyik lekérdezés adja azt, hogy mennyit költött a vevő?
Miért használjuk a round függvényt?

```
select sum(Aruk.ar) from Tranzakciok, Aruk 
where tranzakcio_id = 'T0001' and Tranzakciok.termek = Aruk.cikkszam; 

select Tranzakciok.*, Aruk.megnevezes, Aruk.ar, round(Aruk.ar*mennyiseg, 2) from Tranzakciok, Aruk 
where tranzakcio_id = 'T0001' and Tranzakciok.termek = Aruk.cikkszam;

select Tranzakciok.*, Aruk.megnevezes, 
Aruk.ar as egysegar, 
round(Aruk.ar*mennyiseg, 2) as teljes_ar 
from Tranzakciok, Aruk 
where tranzakcio_id = 'T0001' and Tranzakciok.termek = Aruk.cikkszam;
```

A tranzakció végösszegének kiszámítása minden egyes tranzakcióra:

```
select tranzakcio_id, sum(round(Aruk.ar*mennyiseg, 2)) as vegosszeg 
from Tranzakciok, Aruk 
where Tranzakciok.termek = Aruk.cikkszam
group by tranzakcio_id;
```

Miért szükséges a min függvény, ha a tranzakció dátumát illetve a vevő kódját is meg akarjuk jeleníteni?

```
select tranzakcio_id, min(datum), sum(round(Aruk.ar*mennyiseg, 2)) as vegosszeg 
from Tranzakciok, Aruk 
where Tranzakciok.termek = Aruk.cikkszam
group by tranzakcio_id;

select tranzakcio_id, min(datum),  min(vevo), sum(round(Aruk.ar*mennyiseg, 2)) as vegosszeg 
from Tranzakciok, Aruk 
where Tranzakciok.termek = Aruk.cikkszam and vevo is not null
group by tranzakcio_id;

select tranzakcio_id, min(datum),  min(vevo), sum(round(Aruk.ar*mennyiseg, 2)) as vegosszeg 
from Tranzakciok, Aruk 
where Tranzakciok.termek = Aruk.cikkszam and vevo is not null
group by tranzakcio_id
order by vegosszeg desc;

select tranzakcio_id, min(datum),  min(vevo) as vevo, sum(round(Aruk.ar*mennyiseg, 2)) as vegosszeg 
from Tranzakciok, Aruk 
where Tranzakciok.termek = Aruk.cikkszam and vevo is not null
group by tranzakcio_id
having vegosszeg > 5
order by vegosszeg desc;
```

# A lekérdezés eredményének használata egy másik lekérdezésben

A vevők összes költésének lekérdezése:

```
select vevo, sum(vegosszeg) as vevo_osszes_koltese from
(select tranzakcio_id, min(datum),  min(vevo) as vevo, sum(round(Aruk.ar*mennyiseg, 2)) as vegosszeg 
from Tranzakciok, Aruk 
where Tranzakciok.termek = Aruk.cikkszam and vevo is not null
group by tranzakcio_id
order by vegosszeg desc) as tranzakciok_vegosszeggel
group by vevo;
```

Tranzakciók naponkénti darabszámának meghatározása

```
select distinct tranzakcio_id, datum from Tranzakciok;
select count(*) from Aruk

select count(*) from
(select distinct tranzakcio_id, datum from Tranzakciok) as tranzakcio_datum;

select datum, count(*) from
(select distinct tranzakcio_id, datum from Tranzakciok) as tranzakcio_datum
group by datum;
```

Napi forgalom

```
select * from Tranzakciok;

select *, ar as egysegar from Tranzakciok, Aruk 
where Aruk.cikkszam = termek; -- MI LENNE HA ELFELEJTENENK A WHERE FELTÉTELT?

select Tranzakciok.*, ar as egysegar from Tranzakciok, Aruk 
where Aruk.cikkszam = termek;

select Tranzakciok.*, ar as egysegar, round(ar*mennyiseg,2) as teljes_ar from Tranzakciok, Aruk 
where Aruk.cikkszam = termek;

select round(sum(teljes_ar),2), datum from
(select Tranzakciok.*, ar as egysegar, round(ar*mennyiseg,2) as teljes_ar from Tranzakciok, Aruk 
where Aruk.cikkszam = termek) as tranzakciok_arakkal
group by datum
order by datum;
```

# Adatok változtatása és törlése

Az alábbi utasítások közül melyik működik? Miért?

```
update Vasarlok set nev = 'Éva neni' where vasarlo_id = 'V03';
update Vasarlok set nev = 'Pista Bácsi' where nev = 'Pista Bacsi';  
update Vasarlok set nev = 'Pista Bácsi'; 
delete from Aruk where cikkszam = '008';
delete from Aruk;
```

# Tranzakciók tábla normalizálása

```
create table tranzakciok_alapadatai 
(select distinct tranzakcio_id, datum, vevo from tranzakciok);

ALTER TABLE tranzakciok_alapadatai ADD PRIMARY KEY (tranzakcio_id);

create table tranzakcio_termekek as 
(select tranzakcio_id, termek, mennyiseg from tranzakciok); 

drop table tranzakciok;
```

# Vásárlók címének normalizálása, adatok elérése Java-ból

SQL:
```
create table Vasarlok1 (
  vasarlo_id varchar(10) unique,
  nev varchar(20),
  irszam varchar(4),
  utca_hsz varchar(50),
  primary key (vasarlo_id) );

create table Varosok (
  irszam varchar(4) unique,
  varos varchar(30),
  primary key (irszam) );
```

Java:
```
import java.sql.*;
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World' :-)");
        try{
            Class.forName("com.mysql.cj.jdbc.Driver");
            Connection con=DriverManager.getConnection(
                    "jdbc:mysql://localhost:3306/pekseg","krisztian","daniel");
            //here sonoo is database name, root is username and password
            Statement stmt=con.createStatement();
            ResultSet rs=stmt.executeQuery("select vasarlo_id, nev, cim from Vasarlok");
            while(rs.next()) {
                String vasarlo_id = rs.getString(1);
                String nev = rs.getString(2);
                String cim = rs.getString(3);
                String irsz = cim.substring(0,4);
                String varosnev = cim.substring(5, cim.indexOf(","));
                String utca_hsz = cim.substring(cim.indexOf(",")+1).trim();

                System.out.println(vasarlo_id+"|"+nev+"|"+irsz+"|"+varosnev+"|"+utca_hsz);

                stmt=con.createStatement();
                stmt.executeUpdate("insert into Varosok values (\""+irsz+"\",\""+varosnev+"\")");
                stmt.executeUpdate("insert into Vasarlok1 values (\""+vasarlo_id+"\",\""+nev+"\",\""+irsz+"\",\""+utca_hsz+"\")");
            }
            con.close();
        }catch(Exception e){ System.out.println(e);}
    }
}
```

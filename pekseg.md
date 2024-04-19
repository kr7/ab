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

# Entitázs-relációs diagram

Alább látható a fentiekben létehozott adatbázis entitázs-relációs diagramja. Figyelem: az adatbázis nincs normalizálva, a diagram aktuális állapota igyekszik minél pontosabban leképezni a fenti, normalizálatlan adatbázist. Külön entitázsnak tekinthetnénk a tranzakciókat és ekkor a *vásárlás* reláció teremtene kapcsolatot a *vásárlók (vevők)*, *áruk* és *tranzakciók* között.  

![image](https://github.com/kr7/ab/assets/7807330/ca6b15e5-4e8c-4a32-8e84-b6a850ea3fb5)


# A MySQL szerveren található adatbázisok listázása

```
show databases;
```

# A "Pekseg" adatbázis tábláinak listázása

```
use pekseg;
show tables;
show columns from Aruk;
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

select distinct(tranzakcio_id) from Tranzakciok
```
Legkisebb áru termék megnevezésének lekérdezése

```
select megnevezes from Aruk 
where ar = (select min(ar) from Aruk);
```

# Új sor (rekord, példány) beszúrása az adattáblába

Végrehajtható-e az alábbi utasítás? Miért? Tipp: lásd az adattábla létrehozását!
```
insert into Aruk values ('001','alma','100','1.99');
```

És az alábbiak?
```
insert into Aruk values ('008','alma','100','1.99');

insert into Aruk values ('010', 'banan', 350, 1.99),  ('011', 'korte', 350, 1.99)

insert into Aruk(cikkszam, megnevezes) values ('012', 'narancs') 

create table furcsa_megnevezesek 
(select megnevezes from Aruk
where megnevezes like 't%');

insert into furcsa_megnevezesek 
(select megnevezes from Aruk where megnevezes like "k%")

```

# Több táblára vonatkozó lekérdezések, join

A "T0001" azonosítójú tranzakció mellé "odaírjuk" a termék megnevezését illetve árát:

```
select Tranzakciok.*, Aruk.megnevezes from Tranzakciok, Aruk 
where tranzakcio_id = 'T0001' and Tranzakciok.termek = Aruk.cikkszam;

select Tranzakciok.*, Aruk.megnevezes, Aruk.ar from Tranzakciok, Aruk 
where tranzakcio_id = 'T0001' and Tranzakciok.termek = Aruk.cikkszam;
```

Az alábbiak közül melyik lekérdezés adja azt, hogy mennyit költött a vevő az egyes tranzakciokban?
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


Join

```
select Tranzakciok.*, Vasarlok.nev 
from Tranzakciok, Vasarlok
where Tranzakciok.vevo = Vasarlok.vasarlo_id;

select Tranzakciok.*, Vasarlok.nev 
from Tranzakciok JOIN Vasarlok
on Tranzakciok.vevo = Vasarlok.vasarlo_id;

select Tranzakciok.*, Vasarlok.nev 
from Tranzakciok LEFT OUTER JOIN Vasarlok
on Tranzakciok.vevo = Vasarlok.vasarlo_id;

select Tranzakciok.*, Vasarlok.nev 
from Tranzakciok RIGHT OUTER JOIN Vasarlok
on Tranzakciok.vevo = Vasarlok.vasarlo_id;
```

# Union

```
select * from Tranzakciok where termek = '001';
union
select * from Tranzakciok where termek = '003';
union
select * from Tranzakciok where termek = '006';
```


# A lekérdezés eredményének használata egy másik lekérdezésben

A Tranzakciok tábla azon sorainak lekérdezése, amelyek 'k'-val kezdődő megnevezésű termékekre vonatkoznak:

```
select * from Tranzakciok where termek in 
(select cikkszam from Aruk where megnevezes like "k%");
```

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

Napi bevétel

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

Írjunk egy olyan lekérdezést, amely megadja vevőnként a tranzakciók számát. Az eredménytáblában a vevő neve és a hozzá tartozó tranzakciók száma szerepeljen!

```
select nev, count(*) from
	(select tranzakcio_id, min(nev) as nev
	from Tranzakciok, Vasarlok
	where Tranzakciok.vevo = Vasarlok.vasarlo_id
	group by tranzakcio_id) tranzakcio_nev
group by nev;

select nev, tranzakciok_szama from Vasarlok,  
	(select vevo, count(*) as tranzakciok_szama from
		(select tranzakcio_id, min(vevo) as vevo 
		from Tranzakciok
		where vevo is not null
		group by tranzakcio_id) as tranzakcio_id_vevo
	group by vevo) as tranzakcioszamok_vevokoddal
where tranzakcioszamok_vevokoddal.vevo = Vasarlok.vasarlo_id
```
A fenti két megoldás közül melyik "jobb"? Mi van, ha két különböző vásárlónak azonos a neve (Varga Béla)?

# Adatok változtatása és törlése

Az alábbi utasítások közül melyik működik? Miért?

```
update Vasarlok set nev = 'Éva neni' where vasarlo_id = 'V03';
update Vasarlok set nev = 'Pista Bácsi' where nev = 'Pista Bacsi';  
update Vasarlok set nev = 'Pista Bácsi'; 
delete from Aruk where cikkszam = '008';
delete from Aruk;
```

# Oszlop típusának megváltoztatása

Változtassuk meg az "Aruk" tábla "ar" oszlopának típusát DECIMAL(5,2)-re: 

```
alter table Aruk modify ar decimal(5,2);
```

Mi a külöbség a FLOAT és a DECIMAL típus között? Ön melyik típust használná ebben az esetben?


# Tárolt lekérdezések (más néven: nézettáblák, virtuális táblák, view-ok)

"A lekérdezés eredményének használata egy másik lekérdezésben" c. részben szereplő utolsó feladatot megoldjuk nézettáblákkal is.

A feladat "eredeti" megoldása az alábbi:

```
select nev, tranzakciok_szama from Vasarlok,  
	(select vevo, count(*) as tranzakciok_szama from
		(select tranzakcio_id, min(vevo) as vevo 
		from Tranzakciok
		where vevo is not null
		group by tranzakcio_id) as tranzakcio_id_vevo
	group by vevo) as tranzakcioszamok_vevokoddal
where tranzakcioszamok_vevokoddal.vevo = Vasarlok.vasarlo_id
```

A megoldás nézettáblákkal: 

```
create view tranzakcio_id_vevo as 
(select tranzakcio_id, min(vevo) as vevo 
from Tranzakciok
where vevo is not null
group by tranzakcio_id);

create view tranzakcioszamok_vevokoddal as
(select vevo, count(*) as tranzakciok_szama
from tranzakcio_id_vevo
group by vevo);

select nev, tranzakciok_szama from Vasarlok, tranzakcioszamok_vevokoddal
where tranzakcioszamok_vevokoddal.vevo = Vasarlok.vasarlo_id;
```

Mi történik, ha a Tranzakciók tábla változása (példaként az alábbi, új tranzakció felvitele után) után újra kiadjuk az utolsó, Vasarlok és tranzakcioszamok_vevokoddal táblákra vonatkozó lekérdezést?   

```
insert into Tranzakciok values 
('T0010','2024-03-18','V01','001',1)
```

Beszúrás nézettáblákba:

```
create view Aruk_alapadatai as
(select cikkszam, megnevezes, ar from Aruk)

create view DragaAruk as 
(select cikkszam, megnevezes, ar from Aruk where ar > 1);

select * from DragaAruk;
insert into DragaAruk values ('008','pizza', 8.99);

create view FelkilosAruk as
(select cikkszam, megnevezes, ar from Aruk where tomeg = 500);

insert into FelkilosAruk values 
('020','Orias kakaoscsiga','15.00');
```
Melyik (nézet)táblába került az "Orias kakaoscsiga"? Aruk? Aruk_alapadatai? DragaAruk? FelkilosAruk?  


Az "Orias kakaoscsiga" FelkilosArukból való "eltűnését" feloldhatjuk az alábbi módon:

```
drop view FelkilosAruk;

create view FelkilosAruk as
(select * from Aruk where tomeg = 500);
 
select * from FelkilosAruk;

insert into FelkilosAruk values 
('021','Orias kakaoscsiga','500','15.00');
```

# Indexek

```
create index MegnevezesSzerintiIndex on Aruk(megnevezes);

select * from Aruk where megnevezes = 'kifli';

show columns from Aruk;

drop index MegnevezesSzerintiIndex on Aruk;

show columns from Aruk;
```





# Tranzakciók tábla normalizálása

```
create table tranzakciok_alapadatai 
(select distinct tranzakcio_id, datum, vevo from tranzakciok);

ALTER TABLE tranzakciok_alapadatai ADD PRIMARY KEY (tranzakcio_id);

create table vasarlas as 
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
package mysql_hozzaferes;
import java.sql.*;
public class PentekDelutaniMySQLHozzaferes {
    public static void main(String[] args) {       
        try ( Connection con=DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/pekseg","hallgato","h411gato"); 
              Statement stmt=con.createStatement();
              ResultSet rs=stmt.executeQuery(
                    "select vasarlo_id, nev, cim from Vasarlok") ) 
        {
            while (rs.next()) {
                String vasarlo_id = rs.getString(1);
                String nev = rs.getString(2);
                String cim = rs.getString(3);
                
                System.out.println(vasarlo_id+"|"+nev+"|"+cim);
                
                String irsz = cim.substring(0,4);
                String varos = cim.substring(5, cim.indexOf(','));
                String utca_hsz = cim.substring(cim.indexOf(',')+2);
                
                System.out.println(" --> "+irsz+";"+varos+";"+utca_hsz);
                
                String sql1 = "insert into Varosok values (\""+irsz+"\",\""+varos+"\") ";
                String sql2 = "insert into Vasarlok1 values "+
                        "(\""+vasarlo_id+"\",\""+nev+"\", \""+irsz+"\", \""+utca_hsz+"\") ";
                
                System.out.println(sql1);
                System.out.println(sql2);
                
                try (Statement stmt2=con.createStatement())
                {
                    stmt2.executeUpdate(sql1);
                    stmt2.executeUpdate(sql2);
                } catch (Exception e) {
                    e.printStackTrace();                
                }               
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }    
}

```

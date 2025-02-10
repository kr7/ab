# Gyakorló feladatok

1. Kérdezze le az Aruk táblából az "l" betűt tartalmazó megnevezésű termékeket!

```
select * from Aruk where megnevezes like '%l%';
```

2. Kérdezze le az Aruk táblából az "a" betűt tartalmazó megnevezésű termékek átlagos tömegét!

```
select avg(tomeg) from Aruk where megnevezes like '%a%';
```


3. Kérdezze le az Aruk táblából a legolcsóbb termék megnevezését és cikkszámát!

```
select megnevezes, cikkszam from Aruk order by ar limit 1;
```

```
select megnevezes, cikkszam from Aruk where ar = (select min(ar) from Aruk);
```

Minden esetben ugyanazt az eredményt adja-e a fenti két lekérdezés? (Segítség: mi történik abban az esetben, ha több térméknek is azonos az ára, 
és így több legolcsóbb termék is van az adatbázisban?
  
4. Kérdezze le a Tranzakciok tábla azon sorait, amelyek az előbbi lekérdezés eredményeként kapott legolcsóbb termékre vonatkoznak!

```
select * from Tranzakciok
where termek in 
  (select cikkszam from Aruk
   where ar = (select min(ar) from Aruk));
```

5. Rendezze a vásárlók adatait tartalmazó táblát a vásárlók neve szerinti ABC-sorrendbe.

```
select * from Vasarlok order by nev;
```

   
6. Írjon egy olyan lekérdezést, amely megadja, hogy melyik termékből összesen mennyit vásároltak!

```
select termek, Aruk.megnevezes, sum(mennyiseg) 
from Tranzakciok, Aruk
where Tranzakciok.termek = Aruk.cikkszam
group by termek;
```

7. Az ügyfél az várja el, hogy a Tranzakciok táblában hatékonyan lehessen keresni a dátum szerint. Mit javasol? Írja meg a javaslatot megvalósító SQL kódot is!

```
create index ViccesElnevezesuIndex on Tranzakciok(datum);
```

8. A pékség információkat szolgáltat egyik partnere számára, ugyanakkor a vezetőség azt szeretné, hogy a partner csak az áruk megnevezéséhez és árához férhessen hozzá, más információkat (pl. cikkszám, tömeg) ne lásson az árukkal kapcsolatban. Hozza létre azt a nézettáblát, amely az előbb említett adatokat tartalmazza!

```
create view MegosztottAdatok as select megnevezes, ar from Aruk;
```

9. Írjon egy olyan lekérdezést, amely megadja, hogy melyik termékből havonta mennyit vásároltak! (Segítség: (a) az eredménytábla tehát három oszlopot tartalmazzon: (i) melyik hónapról van szó, (ii) melyik termékről van szó, (iii) mennyit adtak el belőle; (b) a dátum feldolgozásához keressen megfelelő SQL függvényt!)

```
select extract(YEAR_MONTH from datum) as ho,
       termek, sum(mennyiseg) 
from Tranzakciok
group by ho, termek;
```

10. Írjon egy olyan lekérdezést, amely megadja, hogy melyik vevő milyen termékeket vásárolt. Az eredménytábla egyik oszlopa a vevő nevét, a másik pedig a termék megnevezését tartalmazza. Egy vevő-termék páros csak egyszer szerepeljen az eredménytáblában. Ha van olyan termék, amit senki sem vásárolt, az is szerepeljen az eredménytáblában (értelemszerűen az ilyen termékek esetében a vevő neve üres).

```
select distinct Vasarlok.nev, Aruk.megnevezes
from Aruk LEFT OUTER JOIN 
   (Tranzakciok JOIN Vasarlok
    on Tranzakciok.vevo = Vasarlok.vasarlo_id) 
on Tranzakciok.termek = Aruk.cikkszam;
```

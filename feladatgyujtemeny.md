# Adatbázisrendszerek feladatgyűjtemény

Ez a ***folyamatosan bővülő(!)*** feladatgyűjtemény olyan tesztkérdéseket tartalmaz, amelyek ***hasonlóak(!)*** azokhoz a kérdésekhez, amelyekre a hallgatóim számíthatnak 
az Adatbázisrendszerek gyakorlathoz kapcsolódó számonkérésen (zárthelyi dolgozatban, azaz ZH-ban).

A feladatok témakörönként szerepelnek a gyűjteményben, a feladatgyűjtemény végén megadjuk az egyes feladatok megoldásait, estenként indoklással. 

Visszajelzéseket, javaslatokat, hibák jelzését örömmel várom a buza.krisztian@uni-bge.hu e-mail címen.

*Buza Krisztián*

# 1. Algoritmuselméleti alapozás

**1.1. Kinek a nevéből származik az algoritmus szavunk?**

(A) Al Gore

(B) Al Dzsazíra

(C) Al-Hvárizmi

(D) Aladdin


**1.2. Az alábbiak közül melyik írja le legjobban az algoritmus szó jelentését?**

(A) Megadott gyakorisággal (ritmusban) ismételt lépések sorozata.

(B) Egy jól definiált, mechanikus lépéssorozat valamilyen feladat megoldására.

(C) Egy SQL lekérdezés.

(D) Nagy számításigényű eljárás, amelynek végrehajtása a legmodernebb számítógéppel is sokáig, legalább 2 óráig, tart.


**1.3. Tekinthető-e egy étel elkészítését leíró recept algoritmusnak?**

(A) Igen.

(B) Nem. 

(C) Csak akkor, ha az étel legalább 3 ember számára készül.

(D) Csak akkor, ha az elkészítéshez valamilyen elektronikus eszköz (tűzhely, mikrosütő, konyhai robotgép, stb.) szükséges.


**1.4. A buborékrendezés (bubble sort) komplexitása...**

(A) $O(log n)$

(B) $O(n)$

(C) $O(n log n)$

(D) $O(n^2)$


**1.5. Egy $O(n^2)$ komplexitású rendezőalgoritmussal rendezünk egy 100 sorból álló adattáblát, és ez 0.01 másodpercig tart. Nagyságrendileg mennyi ideig fog tartani egy ugyanolyan jellegű, de 5000 soros adattábla rendezése ugyanezzel az algoritmussal?**

(A) $50 \times 0.01 = 0.5$ másodpercig

(B) $50 \times 50 \times 0.01 = 25$ másodpercig

(C) $\sqrt{50} \times 0.01 = 0.07$ másodpercig

(D) $5000 \times 0.01 = 50$ másodpercig


**1.6. Egy $O(n log_2 n)$ komplexitású rendezőalgoritmussal rendezünk egy 1000 sorból álló adattáblát, és ez 0.01 másodpercig tart. Nagyságrendileg mennyi ideig fog tartani egy ugyanolyan jellegű, de 1000000 soros adattábla rendezése ugyanezzel az algoritmussal?**

(A) $1000 \times log_2 1000 \times 0.01 = 100$ másodpercig

(B) $1000 \times 0.01 = 10$ másodpercig

(C) $1000 \times log_2 1000000 / log_2 1000 \times 0.01 = 1000 \times 2 \times 0.01 = 20$ másodpercig  

(D) $1000 \times 1000 \times 0.01 = 10000$ másodpercig


**1.7. Az alábbi állítások közül melyik igaz a rendezőalgoritmusokra?**

(A) A buborékrendezése komplexitása $O(n^2)$.

(B) Nem létezik a buborékrendezésnél hatékonyabb rendezőalgoritmus.

(C) A buborékrendezése komplexitása $O(n log n)$.

(D) Az előbbi három állítás közül egyik sem igaz.


**1.8. Az alábbi állítások keresőalgoritmusokra vonatkoznak. Melyik hamis?**

(A) Rendezett adatokban lényegesen gyorsabban tudunk keresni, mint rendezetlen adatokban.

(B) Rendezett adatokban tudunk $O(log n)$ komplexitással keresni.

(C) Rendezetelen adatokban történő keresés esetére nem létezik $O(n log n)$ komplexitásúnál hatékonyabb algoritmus.

(D) A rendezetlen adatokban történő keresés $O(n)$ komplexitással megoldható.


**1.9. Egy lineáris, azaz $O(n)$ komplexitású keresőalgoritmus 1000 elem között átlagosan 0.3 másodperc alatt találja meg a keresett elemet. 
Ugyanezen algoritmus nagyságrendileg mennyi idő alatt fogja megtalálni a keresett elemet 1 millió elem között?**

(A) $1 000 000 \times 0.3 = 300 000$ másodperc alatt.

(B) $1 000 \times 0.3 = 300$ másodperc alatt.

(C) $1000 \times 1000 \times 0.3 = 300 000$ másodperc alatt.

(D) $log_2 1000 \times 0.3 = 3$ másodperc alatt.


**1.10. Egy logaritmikus, azaz $O(log_2 n)$ komplexitású keresőalgoritmus 1000 elem között átlagosan 0.3 másodperc alatt találja meg a keresett elemet. 
Ugyanezen algoritmus nagyságrendileg mennyi idő alatt fogja megtalálni a keresett elemet 1 millió elem között?**

(A) $1 000 000 \times 0.3 = 300 000$ másodperc alatt.

(B) $1 000 \times 0.3 = 300$ másodperc alatt.

(C) $1000 \times 1000 \times 0.3 = 300 000$ másodperc alatt.

(D) $log_2 1000 \times 0.3 = 3$ másodperc alatt.



# 2. SQL

**2.1. Egy oszlop típusát DECIMAL(6,2)-re választotta meg. Ez mit jelent?**

(A) Az oszlop 6 karakterből álló karaktersorozatot képes tárolni, amelyben legfeljebb 2 különleges karakter (?, !, $, stb.) lehet. 

(B) Az oszlop olyan számot tárol, amelynek egészrésze legfeljebb 6 jegyű és ezen kívül legfeljebb 2 számjeggyel rendelkezik a tizedesvessző után. 

(C) Az oszlop olyan számot tárol, amelynek egészrésze legfeljebb 4 jegyű és ezen kívül legfeljebb 2 számjeggyel rendelkezik a tizedesvessző után. 

(D) Az oszlop csak olyan 6-jegyű számokat képes tárolni, amelyek százasokra kerekítettek, azaz 2 nullára végződnek, pl. 1200.


**2.2. Az alábbiak közül melyik SQL paranccsal tudjuk a "Termekek" tábla "ar" oszlopának típusát egész számról (int) egy 2 tizedesjeggyel rendelkező számra változtatni?**

(A) alter table Termekek modify ar decimal(8,2);

(B) update table Termekek modify ar from int to decimal(8,2);

(C) modify table Termekek change ar from int to decimal(8,2);

(D) change table Termekek modify ar decimal(8,2);


**2.3. Mi a különbség az UPDATE és ALTER SQL utasítások között?**

(A) Semmi. Ezek a kulcsszavak egymás szinonímáiként használhatók, azaz UPDATE helyett ALTER-t is használhatunk és fordítva.

(B) Az UPDATE a táblában lévő adatokat változtatja, az ALTER a tábla szerkezetét (pl. oszlopokat vagy azok típusát).

(C) Az ALTER a táblában lévő adatokat változtatja, az UPDATE a tábla szerkezetét (pl. oszlopokat vagy azok típusát).

(D) Az UPDATE utasítással az oszlopok típusát régebbi típusokról lehet újabb, modernebb típusokra változtatni; az ALTER-rel a újabb típusok változtathatók régebbiekre.


**2.4. Adott egy termékek adatait tartalmazó, "arucikk" elnevezésű adattábla, melyből ki szeretné választani az 1000 Ft és 2000 Ft közötti árú termékeket és az eredménytáblában meg szeretné jeleníteni az ezen termékekről nyilvántartott összes információt. Az alábbiak közül melyik lekérdezést használná ehhez?**

(A) select * from aruk where ar > 1000 and ar < 2000

(B) select * from arucikk where ar > 1000 and ar < 2000

(C) select megnevezes, cikkszam, ar from arucikk where ar > 1000 and ar < 2000 

(D) select * from arucikk where ar > 1000 union select * from arucikk where ar < 2000


**2.5. Adott egy termékek adatait tartalmazó, "arucikk" elnevezésű adattábla, amelynek "ar" oszlopában tartjuk nyilván az egyes termékek árait. Mit eredményez az alábbi lekérdezés?**

**select * from arucikk where ar > 1000 union select * from arucikk where ar < 2000**

(A) Az összes terméket tartalmazó adattáblát, amelyben néhány termék akár kétszer is szerepelhet.

(B) Azon termékeket tartalmazó adattáblát, amelyek ára 1000 Ft és 2000 Ft közötti.

(C) Azon termékeket tartalmazó adattáblát, amelyek ára 1000 Ft-nál nagyobb.

(D) Azon termékeket tartalmazó adattánlát, amelyek ára 2000 Ft-nál kisebb.


**2.6. Adott egy repülőjáratokat tartalmazó *jaratok* elnevezesű adattábla, mely az alábbi oszlopokkal rendelkezik: (i) *jaratszam*, (ii) *honnan*: kiindulási reptér, (iii) *hova*: érkezési reptér, (iv) *indulas*: indulás időpontja (datetime), (v) *erkezes*: érkezés időpontja (datetime). Kérdezze le azon városok listáját, ahová (eszerint az adatázis szerint) Budapestről valaha repült járat, egy város csak egyszer szerepeljen az eredményként kapott listában!**

(A) select honnan from jaratok where hova = "Budapest"

(B) select hova from jaratok where honnan = "Budapest"

(C) select distinct honnan from jaratok where hova = "Budapest"

(D) select distinct hova from jaratok where honnan = "Budapest"


**2.7. Adott egy repülőjáratokat tartalmazó *jaratok* elnevezesű adattábla, mely az alábbi oszlopokkal rendelkezik: (i) *jaratszam*, (ii) *honnan*: kiindulási reptér, (iii) *hova*: érkezési reptér, (iv) *indulas*: indulás időpontja (datetime), (v) *erkezes*: érkezés időpontja (datetime). Ez a tábla az indulási és érkezési reptereket a légi forgalomban szokásos 3 betűs kódokkal (pl. BUD = Budapest, CLJ = Kolozsvár, stb.) tartalmazza. Adott egy másik tábla, amely a repterek kódjai és a városnevek közötti kapcsolatokat tartalmazza, ennek elnevezése *varosok* és két oszlopa van: (i) *kod*, (ii) *varosnev*. Kérdezze le azon városok listáját, ahová (eszerint az adatázis szerint) Budapestről valaha repült járat, egy város csak egyszer szerepeljen az eredményként kapott listában, de a városokat a hétköznapi megnevezéssel adja meg, ne a kódjaikkal!**

(A) select distinct varosok.varosnev from jaratok, varosok where jaratok.honnan = "Budapest" and jaratok.hova = varosok.kod

(B) select distinct varosok.varosnev from jaratok, varosok where jaratok.honnan = "BUD" and jaratok.hova = varosok.kod

(C) select distinct varosok.varosnev from jaratok, varosok where jaratok.honnan = "BUD" or jaratok.hova = varosok.kod

(D) select distinct varosok.varosnev from jaratok, varosok where jaratok.honnan = "Budapest" or jaratok.hova = varosok.kod


**2.8. Adott egy termékek adatait tartalmazó, "arucikk" elnevezésű adattábla, amelynek "ar" oszlopában tartjuk nyilván az egyes termékek árait. Mely termékeket fogja duplán tartalmazni az alábbi lekérdezés eredményeként kapott tábla?**

**select * from arucikk where ar > 1000 union select * from arucikk where ar < 2000**

(A) Az összes terméket. 

(B) Azon termékeket, amelyek ára 1000 Ft és 2000 Ft közötti.

(C) Egyetlen terméket sem fog duplán tartalmazni.

(D) Az 1000 Ft-nál nagyobb árú és 2000 Ft-nál kisebb árú termékek közül egy véletlenszerűen választottat.


**2.9. Adott egy termékek adatait tartalmazó, "arucikk" elnevezésű adattábla, amelynek "ar" oszlopában tartjuk nyilván az egyes termékek árait. Mely termékeket fogja duplán tartalmazni az alábbi lekérdezés eredményeként kapott tábla?**

**select distinct * from arucikk where ar > 1000 union select distinct * from arucikk where ar < 2000**

(A) Az összes terméket. 

(B) Azon termékeket, amelyek ára 1000 Ft és 2000 Ft közötti.

(C) Egyetlen terméket sem fog duplán tartalmazni.

(D) Az 1000 Ft-nál nagyobb árú és 2000 Ft-nál kisebb árú termékek közül egy véletlenszerűen választottat.


**2.10. Adott egy termékek adatait tartalmazó, "arucikk" elnevezésű adattábla, amelynek "ar" oszlopában tartjuk nyilván az egyes termékek árait. Mely termékeket fogja duplán tartalmazni az alábbi lekérdezés eredményeként kapott tábla?**

**select distinct * from (select distinct * from arucikk where ar > 1000 union select distinct * from arucikk where ar < 2000) as belso_tabla**

(A) Az összes terméket. 

(B) Azon termékeket, amelyek ára 1000 Ft és 2000 Ft közötti.

(C) Egyetlen terméket sem fog duplán tartalmazni.

(D) Az 1000 Ft-nál nagyobb árú és 2000 Ft-nál kisebb árú termékek közül egy véletlenszerűen választottat.


**2.11. Adott egy termékek adatait tartalmazó, "arucikk" elnevezésű adattábla, amelynek "ar" oszlopában tartjuk nyilván az egyes termékek árait. Mely termékeket fogja duplán tartalmazni az alábbi lekérdezés eredményeként kapott tábla?**

**select distinct * from (select * from arucikk where ar > 1000 union select * from arucikk where ar < 2000) as belso_tabla**

(A) Az összes terméket. 

(B) Azon termékeket, amelyek ára 1000 Ft és 2000 Ft közötti.

(C) Egyetlen terméket sem fog duplán tartalmazni.

(D) Az 1000 Ft-nál nagyobb árú és 2000 Ft-nál kisebb árú termékek közül egy véletlenszerűen választottat.


**2.12. Mit értünk idegen kulcs alatt?**

(A) Egy külföldi felhasználó által birtokolt jelszót, amellyel hozzáférhet az adatbázishoz.

(B) Egy adattábla olyan oszlopát (vagy oszlopait), amely(ek)ben tárolt értékekkel egy másik adattábla sorait egyedileg azonosítani tudjuk.

(C) Egy adattábla olyan oszlopát, amelyben minden sor esetében egyedi érték szerepel, és ezért segítségével az adattábla sorai egyedileg azonosíthatók.

(D) Az adattábla olyan sorát, amelyben minden cella értéke különböző.


**2.13. Mit értünk kulcs alatt?**

(A) Egy külföldi felhasználó által birtokolt jelszót, amellyel hozzáférhet az adatbázishoz.

(B) Egy adattábla olyan oszlopát (vagy oszlopait), amely(ek)ben tárolt értékekkel egy másik adattábla sorait egyedileg azonosítani tudjuk.

(C) Egy adattábla olyan oszlopát, amelyben minden sor esetében egyedi érték szerepel, és ezért segítségével az adattábla sorai egyedileg azonosíthatók.

(D) Az adattábla olyan sorát, amelyben minden cella értéke különböző.


**2.14. SELECT ... lekérdezésekben milyen kulcsó után adhatjuk meg, hogy az adattábla melyik sorait kívánjuk lekérdezni?**

(A) FROM

(B) WHERE

(C) ORDER BY

(D) GROUP BY


**2.15. SELECT ... lekérdezésekben milyen kulcsó után adhatjuk meg, hogy melyik adattáblából kívánunk lekérdezni adatokat?**

(A) FROM

(B) WHERE

(C) ORDER BY

(D) GROUP BY


**2.16. SELECT ... lekérdezésekben milyen kulcsó után adhatjuk meg, hogy melyik oszlop szerint kívánunk rendezni a lekérdezett adatokat?**

(A) FROM

(B) WHERE

(C) ORDER BY

(D) GROUP BY


**2.17. Az alábbiak közül melyik nem aggregációs függvény?**

(A) SUM

(B) AVG

(C) MIN

(D) ROUND


**2.18. Adott egy *Aruk* elnevezésű adattábla, amely tartalmaz egy megnevezés oszlopot. Mi a különbség az alábbi két lekérdezés között?**

(1) SELECT COUNT(*) FROM ARUK

(2) SELECT COUNT(MEGNEVEZES) FROM ARUK

(A) Semmi, ugyanazt az eredményt adják.

(B) Az első megszámolja a tábla sorait, a második pedig azokat a sorokat számolja meg, ahol a MEGNEVEZES mező kitöltött (azaz nem hiányzó érték).

(C) A második megszámolja a tábla sorait, az első pedig azokat a sorokat számolja meg, ahol a MEGNEVEZES mező kitöltött (azaz nem hiányzó érték).

(D) Az első megszámolja a tábla sorait, a második hibát ad.


**2.19. Egy hiba folytán néhány ügyfél többször is belekerült az UGYFEL adattáblába (pontosan ugyanazon adatokkal). Az alábbiak közül melyik lekérdezéssel tudja lekérdezni a különböző ügyfeleket?**

(A) SELECT UNIQUE * FROM UGYFEL

(B) SELECT DISJOINT * FROM UGYFEL

(C) SELECT DISTINCT * FROM UGYFEL

(D) SELECT DIFFERENT * FROM UGYFEL


**2.20. Melyik utasítással lehet nézettáblát (más néven: virtuális tábla, tárolt lekérdezés) létrehozni?**

(A) CREATE VIEW [nézettábla neve] AS [lekérdezés]

(B) MAKE VIEW [nézettábla neve] AS [lekérdezés]

(C) CONSTRUCT VIEW [nézettábla neve] AS [lekérdezés]

(D) INITIALIZE VIEW [nézettábla neve] AS [lekérdezés]


**2.21. Melyik utasítással lehet nézettáblát (más néven: virtuális tábla, tárolt lekérdezés) eltörölni?**

(A) DELETE VIEW [nézettábla neve]

(B) DROP VIEW [nézettábla neve]

(C) DESTRUCT VIEW [nézettábla neve]

(D) ERASE VIEW [nézettábla neve]


**2.22. Melyik utasítással lehet egy táblát eltörölni?**

(A) DELETE TABLE [nézettábla neve]

(B) DROP TABLE [nézettábla neve]

(C) DESTRUCT TABLE [nézettábla neve]

(D) ERASE TABLE [nézettábla neve]


**2.23. Mi történik, amikor insert into-val egy új rekordot próbálunk beszúrni egy nézettáblába?**

(A) Hibaüzenetet kapunk.

(B) Amennyiben a beszúrás visszavezethető az eredeti táblába (amelyre vonatkozóan a nézettáblát létrehoztuk) történő beszúrásra, akkor az új rekord az eredeti táblába kerül beszúrásra.

(C) Az új rekord bekerül a nézettáblába, de az eredeti táblába nem.

(D) Semmi (nem kapunk hibaüzenetet, de a rekord nem is kerül be egy táblába sem).


**2.24. Le szeretné kérdezni egy adattáblából azon hallgatók nevét egy neptun kódját, akiknek egyik keresztneve Péter. A teljes nevet egy oszlopban tároljuk. Melyik lekérdezést használja? (Féltételezheti, hogy az adattábla és a lekérdezésben hivatkozott oszlopok léteznek.)**

(A) SELECT NEV, NEPTUN FROM HALLGATOK WHERE NEV = "%Péter%"

(B) SELECT NEV, NEPTUN FROM HALLGATOK WHERE NEV is "%Péter%"

(C) SELECT NEV, NEPTUN FROM HALLGATOK WHERE NEV LIKE "%Péter%"

(D) SELECT NEV, NEPTUN FROM HALLGATOK WHERE NEV LIKE "\*Péter\*"


**2.25. A lekérdezésünk egy túlságosan nagy adattáblát eredményez, ugyakkor valójában csak az adattábla első néhány sorára van szükségünk. Milyen kulcsszó használatával érhető el az eredménytábla első 15 sorra történő korlátozása?**

(A) RESTRICT 15

(B) HEAD 15

(C) LIMIT 15

(D) AT MOST 15 RECORDS


**2.26. Mire használjuk az indexeket?**

(A) Adott oszlop szerinti keresés (lekérdezés) felgyorsítására.

(B) Az adatok tömörítésére.

(C) Az adatok titkosítására.

(D) Az adatokhoz való hozzáférés szabályozására.


**2.27. Tegyük fel, hogy az UGYFELEK adattáblát indexáltuk a NEV oszlop szerint. Ennek hatására...**

(A) ... a NEV szerinti keresés (NEV oszlopra vonatkozó lekérdezések) végrehajtási ideje csökken.

(B) ... a NEV szerinti keresés (NEV oszlopra vonatkozó lekérdezések) végrehajtási ideje nem változik.

(C) ... a NEV szerinti keresés (NEV oszlopra vonatkozó lekérdezések) végrehajtási ideje növekszik.


**2.28. Tegyük fel, hogy az UGYFELEK adattáblát indexáltuk a NEV oszlop szerint. Ennek hatására...**

(A) ... az adattáblába történő beszúrás (insert into) végrehajtási ideje csökken.

(B) ... az adattáblába történő beszúrás (insert into) végrehajtási ideje nem változik.

(C) ... az adattáblába történő beszúrás (insert into) végrehajtási ideje növekszik.


**2.29. Az UGYFELEK adattáblát indexálni szeretné NEV oszlop szerint. Melyik utasítást használja?**

(A) DEFINE INDEX NEV_SZERINTI_INDEX FOR UGYFELEK(NEV)

(B) CREATE INDEX NEV_SZERINTI_INDEX FOR UGYFELEK(NEV)

(C) DEFINE INDEX NEV_SZERINTI_INDEX ON UGYFELEK(NEV)

(D) CREATE INDEX NEV_SZERINTI_INDEX ON UGYFELEK(NEV)


**2.30. Hogyan tudja az előbbi feladatban létrehozott indexet eltörölni?**

(A) DELETE INDEX NEV_SZERINTI_INDEX FOR UGYFELEK

(B) DROP INDEX NEV_SZERINTI_INDEX FOR UGYFELEK

(C) DELETE INDEX NEV_SZERINTI_INDEX ON UGYFELEK

(D) DROP INDEX NEV_SZERINTI_INDEX ON UGYFELEK


**2.31. Mi történik az alábbi utasítás hatására, ha nem "safe" módban használjuk a MySQL-t?**

**DELETE FROM ARUK**

(A) Hibaüzenetet kapunk.

(B) Eltöröljük az ARUK adattáblát.

(C) Az összes sort kitöröljük az ARUK adattáblából, de magát a táblát nem töröljük el.

(D) Az ARUK tábla első sorát kitöröljük.


**2.32. A DATETIME típusú adat...**

(A) ...dátumot és időt tárol

(B) ...dátumot vagy időt tárol, de egyszerre csak egyiket, nem mind a kettőt

(C) ...azt tárolja, hogy egy dátum melyik időzóna szerint értendő

(D) ...kifejezetten a randik (angolul: date) időpontjának tárolására használatos.


**2.33. Mit eredményez a MAX aggregációs függvény szöveges adatokra alkalmazva?**

(A) Hibaüzenetet, mert csak számokra értelmezett.

(B) Az adott oszlop ÁBC sorrend szerinti utolsó elemét.

(C) Az adott oszlop elemeinek számát.

(D) Nullát.


**2.34. Arra vagyunk kíváncsiak, hogy egy hallgató szerepel-e a megvédett tervezési feladatokat nyilvántartó adattáblában, azonban a Neptun kódját nem tudjuk pontosan elolvasni, mert egy "0" (nulla) vagy "O" betű szerepel benne. Az alábbiak közül melyik lekérdezést használná?**

(A) select count(*) from megvedett_tervezesi_feladatok where neptun like "AB_123"

(B) select count(*) from megvedett_tervezesi_feladatok where neptun line "AB%123"

(C) select count(*) from megvedett_tervezesi_feladatok where neptun = "AB0123" or neptun = "ABO123"

(D) select count(*) from megvedett_tervezesi_feladatok where neptun = "AB0123" and neptun = "ABO123"


**2.35. Arra vagyunk kíváncsiak, hogy egy hallgató szerepel-e a megvédett tervezési feladatokat nyilvántartó adattáblában, azonban a Neptun kódjának negyedik karakterét nem tudjuk elolvasni. Az alábbiak közül melyik lekérdezést használná?**

(A) select count(*) from megvedett_tervezesi_feladatok where neptun like "ABC_12"

(B) select count(*) from megvedett_tervezesi_feladatok where neptun line "ABC%"

(C) select count(*) from megvedett_tervezesi_feladatok where neptun = "ABCA12" or neptun = "ABCB12" or neptun = "ABCC12" or neptun = "ABCD12" ... és így tovább folytatva, végül: ... or "AVCZ12"  

(D) select count(*) from megvedett_tervezesi_feladatok where neptun = "ABCA12" and neptun = "ABCB12" and neptun = "ABCC12" and neptun = "ABCD12" ... és így tovább folytatva, végül: ... and "AVCZ12" 


**2.36. Milyen SQL utasítással tudatjuk a MySQL szerverrel, hogy a következő utasítások egy tranzakciót alkotnak?**

(A) COMMIT

(B) START TRANSACTION

(C) INITIALIZE TRANSACTION

(D) ROLLBACK


**2.37. Adott az alábbi, HALLGATOK elnevezésű adattábla:**

| Név     | Neptun   | Matek   | Fizika | Info |
|---------|----------|---------|--------|------|
| Anna    | ABC012   |   5     |   4    |  5   |
| Péter   | DEF345   |   4     |   3    |  5   |
| Kata    | GHI678   |   3     |   4    |  3   |

**Mely hallgatók adatait adja vissza az alábbi lekérdezés?**

**SELECT * FROM HALLGATOK WHERE MATEK > 3 and FIZIKA > 3**

(A) Anna, Péter, Kata

(B) Anna, Péter

(C) Péter, Kata

(D) Anna


**2.38. Az előbbi adattáblából mely hallgatók adatait adja vissza az alábbi lekérdezés?**

**SELECT * FROM HALLGATOK WHERE MATEK > 3 OR FIZIKA > 3**

(A) Anna, Péter, Kata

(B) Anna, Péter

(C) Péter, Kata

(D) Anna


**2.39. Mit történik, ha egy tranzakcióba tartozó SQL utasítások végrehajtása közben hirtelen áramszünet adódik és ezért nem lehet végrehajtani az összes utasítást?**

(A) Amennyit végrehajtottunk, azoknak a hatása látszik az adatbázisban, a többi utasítás elveszik.

(B) Az adatbázisszerver használhatatlan lesz.

(C) Az adatbázisszerver letiltja a tranzakciót végző felhasználót.

(D) A kiadott utasítások visszavonásra kerülnek (az adatbázis a tranzakció kezdete előtti állapotba tér vissza).


**2.40. Milyen programozási nyelven írt kódból tudunk kapcsolódni egy MySQL szerverhez?**

(A) Java

(B) Python

(C) PHP

(D) Mindhárom előbbi nyelv esetében.


**2.41. Milyen SQL adatbázishoz tudunk kapcsolódni Java nyelven írt programból?**

(A) MySQL

(B) Oracle

(C) SQLite

(D) Mindhárom előbbihez.


**2.42. Hogyan védekezhetünk az SQL injection támadás ellen?**

(A) Nem kapcsolódunk adatbáziszerverhez saját készítésű kódból.

(B) El kell fogadnunk, hogy nem lehet minden támadás ellen védekezni.

(C) Amennyire lehetséges, elkerüljük, hogy felhasználó által megadott adatokat behelyettesítsünk egy SQL utasításba; ha ez nem lehetséges, akkor legalább ellenőrizzük a felhasználó által megadott adatokat mielőtt behelyettesítenénk egy SQL utasításba.

(D) Az SQL externalisation technikával.


**2.43. Jó ötlet-e a MySQL adatbázisszerverhez való csatlakozáshoz szükséges jelszót beírni egy általunk készített kódba, amely csatlakozik az adatbázisszerverhez?**

(A) Igen, mert így elkerüljük a kód túlbonyolítását, a kód megfelel a KISS (keep it simple stupid) elvnek.

(B) Nem jó ötlet, de nincs más lehetőségünk, mert egy SQL szerverhez csatalkozáshoz szükség van a jelszóra, a keletkező kódot ezért csak megízható személlyel oszthatjuk meg.

(C) A jelszó szerepeltetése a kódban nem gond, mert a jelszót ígyis-úgyis titkosított csatornán kereszül küldi el a Java virtuális gép a MySQL szervernek.

(D) Jobb ötlet a jelszó tárolása egy környezeti változóban, és a környezeti változóból történő kiolvasása, amikor szükség van rá, így nyugodtan megoszthatjuk az általunk készített kódot a kollégáinkkal.


# 3. Relációs algebra

**3.1. Kinek a nevéből származik az algebra szavunk?**

(A) Al-Hvárizmi

(B) Al Gore

(C) Al Dzsazíra

(D) Aladdin


**3.2. Mit nevezünk algebrának?**

(A) A matematika műveletekkel ellátott halmazokkal foglalkozó területét.

(B) Al-Hvárizmi munkásságának feldolgozásával foglalkozó tudományterületet.

(C) Egész számok összeadását.

(D) Az adattáblák oszlopainak típusait.


**3.3. Miért nevezzük *relációnak* az adattáblákat?**

(A) Mert párkapcsolati állapotra vonatkozó információkat tárolhatunk bennük.

(B) Mert az egyes oszlopok értelmezési tartománya, mint halmaz között teremtenek kapcsolatot.

(C) Mert relációsjelekkel leírhatóak az adattáblán végzett műveletek (pl. táblák sorainak párosítása).

(D) Mert az idegen kulcsok kapcsolatot teremtenek különböző adattáblák között.


**3.4. Mit nevezünk *relációnak*?**

(A) Az adattáblák tárolására használt eszközt (pl. mágneslemez vagy SSD).

(B) Az adattáblák oszlopait.

(C) Az adattáblák oszlopainak értelmezési tartományait.

(D) Az adattáblát.


**3.5. A relációs algebra...**

(A) ... a matematika párkapcsolatok szimulációjával foglalkozó területe.

(B) ... az SQL elméleti háttere.

(C) ... az adattáblákat rendező algoritmusok hatékony implementálásának technikája.

(D) ... az adattáblákban hatékony keresést lehetővé tevő technika.


# 4. Egyed-kapcsolat modellezés, egyed-kapcsolat diagramok

**4.1. Mit jelölünk téglalappal az egyed-kapcsolat diagramokon?**

(A) Az egyedeket

(B) A kapcsolatokat

(C) Az attribútumokat

(D) A kulcsokat


**4.2. Mit jelölünk ellipszissel az egyed-kapcsolat diagramokon?**

(A) Az egyedeket

(B) A kapcsolatokat

(C) Az attribútumokat

(D) A kulcsokat


**4.3. Mit jelölünk rombusszal az egyed-kapcsolat diagramokon?**

(A) Az egyedeket

(B) A kapcsolatokat

(C) Az attribútumokat

(D) A kulcsokat


**4.4. Mit jelölünk aláhúzással az egyed-kapcsolat diagramokon?**

(A) Az egyedeket

(B) A kapcsolatokat

(C) Az attribútumokat

(D) A kulcsokat


**4.5. Amennyiben az egyed-kapcsolat diagramon, egy egyedhalmaz több attribútumát is aláhúzással jelöltük, ennek a jelentése, hogy...**

(A) Minden aláhúzott attribútum külön-külön egy-egy kulcs.

(B) Az aláhúzott attribútumok együttesen alkotnak egy kulcsot.

(C) Az adattáblát minden egyes aláhúzott attribútum szerint külön-külön indexáltuk.

(D) Az aláhúzott attribútumok különösen fontosak az alkalmazás szempontjából, az adatbázis létrehozása során beállítjuk, hogy nem törölhetőek.


**4.6. Hogyan jelöljük az egyed-kapcsolat diagramokon az idegen kulcsot?**

(A) Szagatott aláhúzással.

(B) Dőlt betűvel.

(C) Duplán keretezett ellipszissel.

(D) Sehogy.


**4.7. Hogyan jelöljük az egyed-kapcsolat diagramokon az indexeket?**

(A) Szagatott aláhúzással.

(B) Dőlt betűvel.

(C) Duplán keretezett ellipszissel.

(D) Sehogy.


**4.8. Mit jelölünk az egyed-kapcsolat diagramon duplán keretezett ellipszissel?**

(A) A kitüntetett jelentőségű attribútumokat.

(B) A többszörös értékű attribútumokat.

(C) A kitüntetett jelentőségű egyedhalmazokat.

(D) A gyenge egyedhalmazokat.


**4.9. Mit jelölünk az egyed-kapcsolat diagramon duplán keretezett téglalappal?**

(A) A kitüntetett jelentőségű attribútumokat.

(B) A többszörös értékű attribútumokat.

(C) A kitüntetett jelentőségű egyedhalmazokat.

(D) A gyenge egyedhalmazokat.


**4.10. Hogyan fordítaná szakszerűen az *entitázs* kifejezést?**

(A) Izé

(B) Képtár vagy múzeum

(C) Egyedhalmaz

(D) Adattábla


# További témák

**5.1. Mit jelent az *adatbányászat*?**

(A) Adatok keresését ("bányászatát").

(B) Rejtett összefüggések keresését nagy adathalmazokban.

(C) Bitcoin bányászatát.

(D) Adatok indexálását.


**5.2. A MongoDB az adatokat...**

(A) ...kulcs-érték párokban...

(B) ...táblázatokban...

(C) ...listákban...

(D) ...halmazokban...

tárolja.


**5.3. A MongoDB kulcs-érték párjaiban egy érték**

(A) csak egész szám lehet,

(B) csak valós szám lehet,

(C) csak egy szöveges érték (karaktersotozat, string) lehet,

(D) szám, szöveges érték vagy akár egy kulcs-érték párokat tartalmazó szótár is lehet.


**5.4. Hogyan tudunk lekérdezéseket definálni MS Access-ben?**

(A) A grafikus lekérdezéstervezővel

(B) SQL-ben

(C) A grafikus lekérdezéstervezővel és SQL-ben egyaránt

(D) AccessQL nyelven


**5.5. Az adatbányászati technikák közül a regresszió...**

(A) egy egyenest illeszt egy koordinátarendszer pontjaira.

(B) becslést vagy előrejelzést végez folytonos skálán.

(C) előre meghatározott csoportok valamelyikébe besorol egy új adatpéldányt.

(D) csoportokat keres (csoportosítja a példányokat, a csoportok nincsenek előre meghatározva).


**5.6. Az adatbányászati technikák közül az osztályozás...**

(A) egy egyenest illeszt egy koordinátarendszer pontjaira.

(B) becslést vagy előrejelzést végez folytonos skálán.

(C) előre meghatározott csoportok valamelyikébe besorol egy új adatpéldányt.

(D) csoportokat keres (csoportosítja a példányokat, a csoportok nincsenek előre meghatározva).


**5.7. Az adatbányászati technikák közül a klaszterezés...**

(A) egy egyenest illeszt egy koordinátarendszer pontjaira.

(B) becslést vagy előrejelzést végez folytonos skálán.

(C) előre meghatározott csoportok valamelyikébe besorol egy új adatpéldányt.

(D) csoportokat keres (csoportosítja a példányokat, a csoportok nincsenek előre meghatározva).


**5.8. Az alábbiak közül melyiket érdemes elvégeznünk, ha ChatGPT-t (vagy ahhoz hasonló co-pilot rendszert) használunk (szeretnénk használni) SQL lekérdezések generálására?**

(A) A generált kód "code review" jellegű ellenőrzése ("értelmes"-e a kód).

(B) A generált kód "unit teszt" jellegű ellenőrzése (kipróbálása minimalisztikus példák esetén).

(C) Annak ellenőrzése, hogy vállalati policy engedi-e a rendszer használatát (kikerülhetnek-e bizalmas adatok, kódok a rendszer használata során a vállalaton kívülre).

(D) Mindhárom fenti ellenőrzést érdemes (szükséges) elvégeznünk.





# Megoldások

1.1. C
1.2. B
1.3. A
1.4. D
1.5. B
1.6. C
1.7. A
1.8. C
1.9. B
1.10. D

2.1. C
2.2. A
2.3. B
2.4. B
2.5. A
2.6. D
2.7. B
2.8. B
2.9. B
2.10. C
2.11. C
2.12. B
2.13. C
2.14. B
2.15. A
2.16. C
2.17. D
2.18. B
2.19. C
2.20. A
2.21. B
2.22. B
2.23. B
2.24. C
2.25. C
2.26. A
2.27. A
2.28. C
2.29. D
2.30. D
2.31. C
2.32. A
2.33. B
2.34. C
2.35. A
2.36. B
2.37. D
2.38. A
2.39. D
2.40. D
2.41. D
2.42. C
2.43. D


3.1. A
3.2. A
3.3. B
3.4. D
3.5. B


4.1. A
4.2. C
4.3. B
4.4. D
4.5. B
4.6. D
4.7. D
4.8. B
4.9. D
4.10. C


5.1. B
5.2. A
5.3. D
5.4. C
5.5. B
5.6. C
5.7. D
5.8. D

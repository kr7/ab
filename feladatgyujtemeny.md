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


**1.6. Egy $O(n log_2 n)$ komplexitású rendezőalgoritmussal rendezünk egy 100 sorból álló adattáblát, és ez 0.01 másodpercig tart. Nagyságrendileg mennyi ideig fog tartani egy ugyanolyan jellegű, de 100000 soros adattábla rendezése ugyanezzel az algoritmussal?**

(A) $1000 \times log_2 1000 \times 0.01 = 100$ másodpercig

(B) $1000 \times 0.01 = 10$ másodpercig

(C) $100000 \times log_2 100000 \times 0.01 = 1661$ másodpercig

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


3.1. A
3.2. A
3.3. B
3.4. D

...nemsokára itt lesznek az első kérdések megoldásai...

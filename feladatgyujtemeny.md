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


# 3. Relációs algebra

**3.1. Kinek a nevéből származik az algebra szavunk?**

(A) Al-Hvárizmi

(B) Al Gore

(C) Al Dzsazíra

(D) Aladdin

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

3.1. A

...nemsokára itt lesznek az első kérdések megoldásai...

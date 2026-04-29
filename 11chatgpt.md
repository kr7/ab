# ChatGPT által készített kód ellenőrzése unit teszt jelleggel

1.	Tudjuk, hogy:
(i) a hallgatók adatait (neptun kód, név, születési adatok, stb.) egy „hallgatok” elnevezésű adattábla tartalmazza, valamint
(ii) a tantárgyak adatait (tantárgykód, elnevezés, tantárgy mintatanterv szerinti feléve, milyen szakon kötelező tárgy, stb.) egy „tantargyak” elnevezésű adattábla tartalmazza, továbbá
(iii) a „vizsgaeredmenyek” adattábla oszlopai: neptun kód, tantárgykód, dátum, elért jegy.
Írassunk ChatGPT-vel egy olyan SQL lekérdezést, amely tárgyanként lekérdezi a tárgy teljesítési arányát figyelembe véve, hogy egy hallgató egy tárgyból többször is vizsgázhat és ilyen esetben mindig az utoljára szerzett érdemjegy számít! Hozzunk létre egy minimalisztikus adatbázist, amelyen „unit teszt” jelleggel ellenőrizni tudjuk, hogy ChatGPT által adott lekérdezés helyes-e! Adjuk meg, hogy a minimalisztikus adatbázis esetében mi a lekérdezés „elvárt” eredménye, és hasonlítsuk össze a ténylegesen kapott eredménytáblát ezzel az „elvárt” eredménytáblával. Amennyiben a kettő nem azonos, javítsuk a ChatGPT-től visszakapott lekérdezést.
 
2.	Tudjuk, hogy:
(i) a vízóraállásokat egy „vizoraallas” elnevezésű adattábla tartalmazza, amelyenek oszlopai: ugyfel_id, datum, vizoraallas,
(ii) az ugyfelek adatait (ugyfel_id, név, cím, stb.) egy „ugyfelek” elnevezésű adattábla tartalmazza.
Írassunk ChatGPT-vel egy olyan lekérdezést, amely minden egyes ügyfél esetében kiszámolja a legutolsó kettő vízóraállás különbségét és ezt megjeleníti ügyfelenként, az eredménytáblában pedig az ügyfél azonosítószámát és nevét is megjeleníti. Hozzunk létre egy minimalisztikus adatbázist, amelyen „unit teszt” jelleggel ellenőrizni tudjuk, hogy ChatGPT által adott lekérdezés helyes-e! Adjuk meg, hogy a minimalisztikus adatbázis esetében mi a lekérdezés „elvárt” eredménye, és hasonlítsuk össze a ténylegesen kapott eredménytáblát ezzel az „elvárt” eredménytáblával. Amennyiben a kettő nem azonos, javítsuk a ChatGPT-től visszakapott lekérdezést.

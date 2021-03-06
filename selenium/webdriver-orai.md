# Selenium WebDriver Pythonnal

[Hogyan gondolkozz úgy, mint egy informatikus: Tanulás Python 3 segítségével](https://mtmi.unideb.hu/pluginfile.php/554/mod_resource/content/1/thinkcspy3.pdf)

A feladatok esetén, ha a Locations alkalmazásra történik hivatkozás, a http://www.learnwebservices.com/locations/server
címet használd.

## Változódeklaráció, típusok

* Szintaktika/szemantika
* Megjegyzések
* Változó, típus
* Kulcsszavak

### Feladat

* A Locations alkalmazásban olvasd be Dobogókő koordinátáját! Írd ki a típusát?
* A Locations alkalmazásban olvasd be Alattyán azonosítóját! Írd ki a típusát!
* A Locations alkalmazásban olvasd be a 9277 azonosítójú település nevét! Írd ki a típusát!

## Típuskonverziós függvények

* `int()`, `float()`, `str()`

* Próbáld meg Bakonybánk azonosítóját egész számmá konvertálni, és írd ki a változó típusát!
* Próbáld meg Zsámbék koordinátáját lebegőpontos számmá konvertálni! Mi történik?

## Műveletek

* Operátor, operandus, precedencia
* `len()`
* Szeletelés
* `replace()`
* `upper()`
* `lower()`
* `split()`
* `in`

* Kérdezd le Velence és Báta azonosítóját, majd add össze!
* Keresd ki a 9876 azonosítójú település nevét, majd írd ki az első három karakterét!
* Keresd ki a 9898 azonosítójú település nevét, majd írd ki visszafele!
* Keresd ki a 9742 azonosítójú település nevét, majd írd ki a hosszát, hogy hány karakterből áll!
* Keresd ki a 11115 azonosítójú település nevét, majd írd ki a csupa nagy és csupa kisbetűvel!
* Keresd ki a 11116, 11117, 11118 azonosítójú település nevét, majd írd ki egymástól kötőjelekkel elválasztva!
* Írd ki Tolmács koordinátáit, de space-szel elválasztva, és tizedespont helyett tizedes vesszővel!
* Keresd ki a Tiszakerecseny és Tiszarád koordinátáit! Add értékül négy lebegőpontos változónak!
* Az előző két településnek vond ki egymásból a szélességi és hosszúsági koordinátáit!
* Írd ki, hogy a 11262 azonosítójú településben szerepel-e a `margit` szó (`True` vagy `False`!
* Bónusz: számold ki a két település távolságát km-ben!

### Saját függvények

* Írj egy függvényt, ami paraméterül kap egy nevet, és kiírja a település koordinátáját!
* Írj egy függvényt, ami paraméterül kap egy nevet, és visszaadja a település koordinátáját!
* Írj egy függvényt, mely paraméterül kap egy azonosítót, és kikeresi a nevet!
* Írj egy függvényt, mely paraméterül kap egy azonosítót, és kikeresi a koordinátáját!
* Írj egy függvényt, mely a paraméterül kapott értékekkel (név, koordináta kitölti az űrlapot, és felvesz egy kedvenc helyet! 
* Módosítsd az előző függvényt, hogy három paramétere legyen, külön kelljen megadni a lat és lon értékeket!
* Legyen default értéke a koordinátáknak (`47.21283333` és `16.8435`)!
* Írj egy függvényt, mely a megadott id-jú helyet módosítja a paraméterként megadott értékekre!


## Feltételes utasítások

* Írj egy függvényt, mely a paraméterként megadott település nevének ismeretében kiírja, hogy szélességi koordinátája
 nagyobb-e mint 48!
* Írj egy függvényt, mely a paraméterként megadott település nevének ismeretében kiírja, hogy szélességi koordinátája
 48.2 és 48.4 közé esik-e!
* Írj egy függvényt, mely a paraméterként megadott település azonosítójának ismeretében kiírja, hogy hossza nagyobb-e mint
8 karakter!


## Ciklusok és a lista adatszerkezet

* Vegyél fel `ZZZ_Sajátnév` névvel öt helyet!
* Vegyél fel `ZZZ_Sajátnév` névvel öt helyet, ahol a lat rendre 1, 2, 3, 4, 5, és a lon koordináta rendre 1, 4, 9, 16, 25!
* Írd ki a konzolra az összes nevet!
* Vegyél fel egy listát három névvel, és ezeket vedd fel helyként!
* Keresd ki egy listában megadott három névhez a koordinátájukat!
* Lapozz az utolsó oldalra! (Kérdezd le a Next feliratú összes elemet, és addig lapozz, míg ennek mérete nem nulla!)

## Fájlbeolvasás

## Programozási tételek

1. Összegzés tétele
2. Számlálás tétele
3. Szélsőérték keresés tétele
4. Eldöntés tétele

* Keresd ki a leghosszabb nevű települést!
* Keresd ki a leghosszabb és legrövidebb nevű települést, anélkül, hogy kétszer járnád be a listát!
* Számold meg, hány `Á` betűvel kezdődő település van!
* Keresd ki a legkeletebbi és legészakabbi települést!

## Page object és default values

## Pytest

* `@pytest.fixture`
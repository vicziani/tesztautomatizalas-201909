# Selenium WebDriver gyakorlás

## Alkalmazás leírása

Adott egy alkalmazás, mely egy állatorvosi rendelő üzleti folyamatait
segíti. Gyakorlatilag rögzíteni lehet az ügyfeleket, háziállataikat és
hogy mikor jártak az állatorvosi rendelőben.

A következő üzleti funkciókkal rendelkezik:

* Listázni lehet az gazdikat
* Szűrni lehet az gazdikra a családi név, vagy annak egy részlete alapján (ha egy találat van, akkor azonnal a gazdi jelenik meg)
* Meg lehet nézni az gazdik részletes adatait
* Meg lehet nézni, hogy a gazdiknak milyen kis kedvenceik vannak, milyen adatokkal
* Kedvenchez látogatást lehet felvenni
* Új gazdit lehet létrehozni
* Szerkeszteni lehet a gazdik adatait
* Új háziállatot lehet felvenni
* Szerkeszteni lehet a háziállatok adatait
* Ki lehet listázni az állatorvosokat

## Alkalmazás származása

Az alkalmazás eredetileg egy Spring Boot technológiát demonstráló
projekt, melynek forrása elérhető a https://github.com/spring-projects/spring-petclinic
címen.

## Alkalmazás telepítése

Az alkalmazást érdemes mindenkinek a saját gépén futtatnia, hiszen így nem
keverednek össze a tesztadatok. Az alkalmazás saját beépített adatbázissal
rendelkezik, mely az alkalmazás újraindítása után újraépül. (A futtatás során
  felvitt adatok újraindításkor elvesznek.)

A futtatható alkalmazás letölthető a https://raw.githubusercontent.com/vicziani/tesztautomatizalas-201909/master/selenium/spring-petclinic-2.2.0.BUILD-SNAPSHOT.jar címről.

Az alkalmazás futtatásához Java 13 szükséges, mely letölthető a https://www.oracle.com/technetwork/java/javase/downloads/jdk13-downloads-5672538.html címről (`jdk-13.0.1_windows-x64_bin.exe`). A feltelepítés után a következő paranccsal indítható, Windows
parancssorból, abból a könyvtárból, melyben a letöltött `jar` állomány van:

```
"C:\Program Files\Java\jdk-13.0.1\bin\java.exe" -jar spring-petclinic-2.2.0.BUILD-SNAPSHOT.jar
```

A konzolon a `Started PetClinicApplication` szövegnek kell megjelennie. Ezután az alkalmazás
elérhető a `http://localhost:8080` címen.

## Feladatok

Az alkalmazás teljes funkcionalitását automata Selenium WebDriver tesztekkel kell lefedni.

A `petclinic_test.py` állományba dolgozz! A szkript a fő részben inicializálja a `driver`
változót, és navigáljon a `http://localhost:8080` oldalra!

* Megjelenik-e a főoldal?
  * Írj egy `assert_title_is(title)` függvényt, amely azt ellenőrzi, hogy a megjelent oldal címe a
    paraméterként átadott érték-e!
  * Írj egy `assert_header_is(title)` függvényt, mely azt ellenőrzi, hogy az oldalon az első címsor (`h1`)
    megegyezik-e a paraméterként átadott értékkel!
  * Írj egy `assert_image_is_present(image)` függvényt, amely azt ellenőrzi, hogy a paraméterként
    megadott kép megjelenik-e a képernyőn! (Azt, hogy megjelenik-e valami, úgy tudod ellenőrizni, hogy
      a `driver.find_elements()` függvényét hívod, és ellenőrzöd, hogy amit visszaad, annak hossza nagyobb, mint 0.
      Használd a `len()` függvényt!)      
  * Írj egy `test_home_page()` függvényt, mely az előző három függvéynt hívja, ellenőrzi a
    címet, a címsort és a képet, hogy megjelenik-e!
* Váltás az oldalak között
  * Írj egy `goto_home_page()`, `goto_find_owners()` és egy `goto_veterinarians()`
    függvényt, melyek a megfelelő oldalakra navigálnak!
  * Írj egy `test_find_owners_page()` függvényt, mely vizsgálja a _Find owners_ oldal
    oldal címét, címsorát, valamint megvizsgálja, hogy van-e rajta _Last name_
    címke, és egy hozzá tartozó beviteli mező!
* Veterinarians oldal: a következő függvények mindegyike hívja meg a `goto_veterinarians()` függvényt!
  * Írj egy `print_veterinarian_count()` függvényt, mely kiírja az orvosok számát!
  * Írj egy `print_veterinarian_names()` függvényt, mely kiírja konzolra az összes állatorvos nevét!
  * Írj egy `print_veterinarian_with_specialities(speciality)` függvényt, mely kiírja
    a megadott szakterületen dolgozó orvosokat! Vigyázz, Linda Douglasnek kettő is meg van adva!
  * Írj egy `print_veterinarian_skill_count()` függvényt, mely kiírja az orvosokat,
    és mellé egy számot, hogy mennyi szakterülettel rendelkezik! (Használd a `split()` függvényt,
    mely elemekre bontja a szakterületet, majd a `len()` függvényt, mely megszámolja!)

Ennek megoldása nagyon érdekes lehet! Először XPath-szal kérd le a sorokat (`tr`), mely
egy listát ad vissza. Menj végig a visszaadott WebElement objektumokon, és
annak hívd meg a `find_element()` függvényét! Ez az adott részfán, az adott Node-on belül keres.

```python
rows = driver.find_elements(By.XPATH, "//tr")
for row in rows:
  name = row.find_element(By.XPATH, "//td[1]")
  print(name)
```

* Veterians folytatás (programozási tételek):
    * Írj egy `get_veterinarian_names()` függvényt, mely visszaadja a nevek listáját!  Ehhez végig kell
    menni a WebElement listán, és csak a neveket áttenni egy másik listába, és azzal visszatérni. A következő
    módon lehet egy listát létrehozni, és a végre egy új elemet felvenni.

```Python
names = [] ## Üres lista létrehozása
names.append("Joe") ## Új elem hozzáadása
print(names)
print(names[0])
```

* Veterians folytatás (programozási tételek):
    * Írj egy `print_veterinarian_name_contains(part)` függvényt, mely meghívja a `goto_veterinarians()`
    függvényt, majd a `get_veterinarian_names()` függvényt, és a visszatérési értékek közül kiírja
    azt, amelyik név tartalmazza a paraméterként megadott értéket. Azaz ne XPath-szal old meg a feladatot!
    Azt, hogy egy string tartalmaz-e egy másikat, a következőképp vizsgálható: `if ('a' in 'xxyxaxyx')`
    * Írj egy `print_veterinarian_longer_than(number_of_characters)` függvényt, ami kiírja
    az összes olyan állatorvost, akinek a neve hosszabb, mint a paraméterként megadott egész szám!
    * (Opcionális) Írj egy `print_longest_name()` függvényt, mely kiírja az első leghosszabb nevű állatorvost! Meghívja a `goto_veterinarians()` függvényt, majd a `get_veterinarian_names()` függvényt.

Ez egy un. szélsőérték keresés, melyre példa lentebb. Be kell vezetni egy ideiglenes változót, mely
az eddig talált leghosszabb nevű elemet tartalmazza, és ha hosszabbat találunk, kicseréljük arra.

```python
names = ['a', 'bb', 'ccc', 'd', 'ee']
name_max_length = ''
for name in names:
    if len(name) > len(name_max_length):
        name_max_length = name
print(name_max_length)
```

* _Find owners_ tesztelés
    * Írj egy `search_with(name)` függvényt, mely behozza a _Find owners_ lapot, és
    kitölti a keresőmezőt a paraméterként átadott értékkel, majd rákattint a _Find Owner_ gombra!        
    * Írj egy `assert_owner_with_name(name)` függvényt, mely ellenőrzi, hogy a paraméterként
    megadott nevű gazdi szerepel-e az oldalon!
    * Írj egy `count_number_of_owners()` függvényt, mely megszámolja, hogy hány gazdi van a
    találati oldalon!
    * Írj egy `test_find_owners()` függvényt, mely üresen hagyja a keresőmezőt!
    Eredményül 10 sornak kell megjelennie, és ellenőrizd, hogy a megjelenik _Maria Escobito_!    
    * Írj egy `test_find_owners_no_result()` függvényt, mely `Jeff` értéket ír be,
    és ellenőrizd, hogy azt írja ki, hogy _has not been found_.
    * Írj egy `test_find_owners_with_one_result()`, ami `Franklin` értéket ír be, és
    az eredmény képernyőn megjelenik, hogy _Owner Information_ és _Name_: _George Franklin_!
    * Keress _Davis_ értékre, és egy két sort tartalmazó táblázatot kell visszaadnia!
* _Add owner_ tesztelés
    * Írj egy `add_owner(first_name, last_name, address, city, telephone)` függvényt,
    amely felvesz egy gazdit!    
    * Írj egy `test_add_owner()` függvényt, mely felvesz egy gazdit, és leellenőrzi, hogy
    megjelenik-e a listában!
    * Írj egy `test_add_owner_with_error()` függvényt, mely üresen hagyja a `First Name`
    mezőt, és ellenőrzi hogy kiír-e egy hibaüzenetet! Írj egy
    `assert_error_message_exists(message)` segédfüggvényt!
* _Edit owner_
    * `Betty Davis` szerkesztése. Azt is ellenőrizd, hogy a mezők fel vannak-e töltve a megfelelő
    értékekkel!    
* Háziállatok tesztelése, az előzőek alapján írd meg a teszteseteket:
    * _George Franklin_ háziállata _Leo_
    * Új háziállat hozzáadása. Azt is ellenőrizd, hogy megjelenik-e a gazdi neve!
    * Új háziállat, de kutyus legyen!
    * Háziállat szerkesztése
    * Ciklusban adj hozzá 5 háziállatot, és vizsgáld, hogy megjelentek-e! A főoldalon is le kell vizsgálni, hogy
      megjelentek-e a háziállatok!
* Látogatás hozzáadása
    * Teszteld, hogy hozzá lehet-e adni látogatást!
    * Ciklusban adj hozzá 5 látogatást! Ellenőrizd, hogy megjelent-e az 5 látogatás!

Gondold át a teszteseteket, hogy találsz-e még olyat, amit érdemes lenne implementálni!
# Metrika, pregled i statička analiza

## LOC metrika

Broj linija koda (LOC) za kompletan projekat:

- Calculator.java – 134 LOC
- Start.java – 19 LOC

Ukupno: 153 LOC

## Neformalni pregled i statička analiza koda

Calculator.java - linija 6 - Promenljiva `finalResult` je statička promenljiva na nivou klase. Ovakav način čuvanja rezultata predstavlja globalno stanje i može otežati održavanje i testiranje koda.

Calculator.java - linija 18 - Metoda `ToString()` nije imenovana u skladu sa Java konvencijom. Nazivi metoda bi trebalo da počinju malim slovom, npr. `toString()`.

Calculator.java - linija 24 - Metoda `Run()` takođe nije imenovana u skladu sa Java konvencijom. Pogodnije ime bi bilo `run()`.

Calculator.java - linije 32–33 - Koristi se `expression.charAt(0)` bez prethodne provere da li je prosleđeni string prazan. U slučaju praznog unosa može doći do greške `StringIndexOutOfBoundsException`.

Calculator.java - linija 37 - Izraz se deli pomoću regularnog izraza koji se dinamički formira od operatora. Ovaj deo koda je teže čitljiv i mogao bi biti jasnije organizovan.

Calculator.java - linije 41–46 - Provera operatora sadrži više ponovljenih uslova. Ova logika bi mogla biti izdvojena u posebnu metodu radi bolje čitljivosti.

Calculator.java - linija 51 - Za brojeve se koristi tip `Float`. Kod računanja decimalnih vrednosti može doći do problema sa preciznošću.

Calculator.java - linije 60–63 - Hvata se generički `Exception`. Bolje bi bilo hvatati konkretnu grešku, na primer `NumberFormatException`.

Calculator.java - linija 73 - Metoda `Calculate()` nije imenovana prema Java naming konvenciji. Naziv bi trebalo da bude `calculate()`.

Calculator.java - linije 73–182 - Metoda `Calculate()` je veoma duga i sadrži veliki broj uslovnih grana. To otežava čitanje, testiranje i održavanje koda.

Calculator.java - linije 85–178 - Kod za obradu sabiranja, oduzimanja, množenja i deljenja se ponavlja na više mesta. Ovo predstavlja dupliranje koda.

Calculator.java - linije 94, 104, 116, 127, 143, 153, 167 i 178 - Metoda `Calculate()` se rekurzivno poziva veliki broj puta. Kod veoma dugih izraza ovo može dovesti do velikog broja rekurzivnih poziva.

Calculator.java - linije 97 i 121 - Deljenje se vrši bez eksplicitne provere da li je delilac nula. Kod `float` vrednosti to može dovesti do rezultata `Infinity` ili `NaN`, što možda nije očekivano ponašanje kalkulatora.

Start.java - linija 6 - Naziv promenljive `Expression` počinje velikim slovom. Prema Java konvenciji lokalne promenljive bi trebalo da počinju malim slovom, npr. `expression`.

Start.java - linija 12 - Novi `Scanner` objekat se kreira pri svakom prolasku kroz `while` petlju. Efikasnije je napraviti jedan `Scanner` pre petlje i koristiti ga tokom celog rada programa.

Start.java - linija 15 - Provera `Expression.equals("exit")` je osetljiva na velika i mala slova, pa unos poput `EXIT` ili `Exit` neće završiti program.

Start.java - linija 16 - `Scanner` se zatvara samo kada korisnik unese `exit`. Upravljanje resursom bi moglo biti bolje rešeno pomoću `try-with-resources` konstrukcije.

## Zaključak

Kod je relativno mali i pregledan, ali statičkom analizom su uočeni problemi vezani za Java konvencije imenovanja, dupliranje koda, dugu i kompleksnu metodu `Calculate()`, korišćenje globalnog stanja, nedovoljnu validaciju korisničkog unosa i upravljanje resursima.

Predložena poboljšanja bi povećala čitljivost, održivost i pouzdanost programa.

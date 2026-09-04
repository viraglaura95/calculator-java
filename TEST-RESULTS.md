# TEST RESULTS

## Black-box testiranje

Testiranje je urađeno metodom crne kutije, tako što su unošeni različiti izrazi i proveravani dobijeni rezultati.

| Test | Ulaz | Očekivani rezultat | Dobijeni rezultat | Status |
|---|---|---|---|---|
| 1 | `4+5` | `9` | `9.0` | PASS |
| 2 | `10-3` | `7` | `7.0` | PASS |
| 3 | `5*4` | `20` | `20.0` | PASS |
| 4 | `20/5` | `4` | `4.0` | PASS |
| 5 | `10+5*4` | `30` | `30.0` | PASS |
| 6 | `10*5+4` | `54` | `54.0` | PASS |
| 7 | `10-2*3` | `4` | `4.0` | PASS |
| 8 | `10/2+3` | `8` | `8.0` | PASS |
| 9 | `-5+3` | `-2` | `-2.0` | PASS |
| 10 | `+5+3` | `8` | `8.0` | PASS |
| 11 | `5.5+2.5` | `8` | `8.0` | PASS |
| 12 | `5/0` | poruka o grešci | `Infinity` | FAIL |
| 13 | `0/0` | poruka o grešci | `NaN` | FAIL |
| 14 | `abc` | poruka o grešci | `ERROR` | PASS |
| 15 | `5+a` | poruka o grešci | `ERROR` | PASS |
| 16 | prazan unos | poruka o grešci | dolazi do greške | FAIL |
| 17 | `5++2` | poruka o grešci | `ERROR` | PASS |
| 18 | `5+` | poruka o grešci | izraz nije pravilno obrađen | FAIL |

## Zapažanja

1. Kod deljenja nulom program ne prikazuje jasnu grešku, nego rezultat može biti `Infinity`.

2. Kod izraza `0/0` rezultat može biti `NaN`.

3. Prazan unos nije dobro obrađen i može dovesti do greške.

4. Nepotpuni izrazi, kao na primer `5+`, nisu dovoljno dobro provereni.

5. Rezultati se prikazuju kao decimalni brojevi, na primer `9.0` umesto `9`.

6. Kod pogrešnog tekstualnog unosa program prikazuje `ERROR`, što je u redu, ali bi poruka mogla biti jasnija.

## Jedinični test

Primer JUnit testa:

```java
import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.jupiter.api.Test;

public class CalculatorTest {

    @Test
    public void testCalculation() {
        String result = Calculator.Run("10+5*4");
        assertEquals("30.0", result);
    }
}

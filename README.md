# Integracija Solo.com.hr API-ja za izradu računa u Next.js aplikaciji

Ovaj projekt prikazuje integraciju Solo.com.hr API-ja za kreiranje računa iz Next.js aplikacije.

---

## Opis

Solo.com.hr pruža REST API za izdavanje fiskalnih računa, a ovaj primjer demonstrira kako iz frontend Next.js komponente poslati račun putem serverless API rute (`app/api/tvoj-api-endpoint/route.ts`) i prikazati status korisniku.

### Parametri i tip podataka:


| Parametar        | Tip podatka         | Opis                                        | Napomena                          |
|------------------|--------------------|---------------------------------------------|----------------------------------|
| `tip_usluge`     | `string`           | Tip usluge (npr. 1 za uslugu, 0 za robu)    | Obavezno                         |
| `prikazi_porez`  | `string` (0 ili 1) | Prikazati li porez na računu                 | Obavezno                         |
| `tip_racuna`     | `string`            | Tip računa (npr. "faktura")                   | Obavezno                         |
| `nacin_placanja` | `string`            | Način plaćanja (npr. "gotovina")              | Obavezno                         |
| `proizvodi`      | `Array` objekata    | Lista stavki računa                           | Obavezno, najmanje jedna stavka  |
| `kupac_naziv`    | `string`            | Naziv kupca                                  | Opcionalno                       |
| `kupac_adresa`   | `string`            | Adresa kupca                                 | Opcionalno                       |
| `kupac_oib`      | `string`            | OIB kupca                                   | Opcionalno                       |
| `datum_racuna`   | `string` (ISO datum) | Datum računa                                | Opcionalno                       |
| `rok_placanja`   | `string` (ISO datum) | Rok plaćanja                                | Opcionalno                       |
| `datum_isporuke` | `string` (ISO datum) | Datum isporuke                              | Opcionalno                       |
| `napomene`       | `string`            | Napomene na računu                           | Opcionalno                       |
| `ponavljanje`    | `string`            | Broj ponavljanja računa                      | Opcionalno                       |
| `iban`           | `string`            | IBAN broj                                   | Opcionalno                       |
| `jezik_racuna`   | `string`            | Jezik računa (npr. "HR")                     | Opcionalno                       |
| `valuta_racuna`  | `string`            | Valuta računa (npr. "HRK")                    | Opcionalno                       |
| `tecaj`          | `string`            | Tečaj valute                                | Opcionalno                       |
| `status`         | `string`            | Status računa                               | Opcionalno                       |
| `fiskalizacija`  | `string` (0 ili 1)   | Treba li fiskalizirati račun                 | Opcionalno                       |

---

### Struktura objekta `usluge` (stavke računa):

| Polje          | Tip podatka  | Opis                                    |
|----------------|--------------|-----------------------------------------|
| `opis_usluge`  | `string`     | Opis usluge ili proizvoda               |
| `jed_mjera`    | `string`     | Jedinica mjere (npr. "kom")             |
| `cijena`       | `string`     | Cijena po jedinici (format nnnn,nn sa zarezom) |
| `kolicina`     | `number`     | Količina stavke                         |
| `popust`       | `number`     | Popust u postotku (0 ako nema)          |
| `porez_stopa`  | `number`     | Porezna stopa (npr. 25)                 |

---

# nextjs-solo-stripe

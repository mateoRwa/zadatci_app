# zadatci_app

# Zadatci App - Vježba 2

- **Ime i prezime:** Mateo Hrkać
- **Operacijski sustav:** Windows
- **Verzija Fluttera / Darta:** (provjeri s `flutter --version`)
- **Uređaj:** Chrome / Android Emulator

### Provedene izmjene:
- Izrađen model `Zadatak` s metodama `fromJson`, `toJson` i `kopiraj` (`lib/zadatak.dart`).
- Izrađen repozitorij `ZadatakRepozitorij` koji simulira mrežni dohvat s kašnjenjem i iznimkama (`lib/repozitorij.dart`).
- Implementiran `FutureBuilder` i `ListView` u `lib/main.dart` za prikaz svih stanja (učitavanje, uspjeh, pogreška s ponovnim pokušajem, prazan popis).

### Odgovori na pitanja za provjeru razumijevanja:
1. **Zašto polja modela nisu promjenjiva (final) i što bi se dogodilo da polje naslov nedostaje u JSON-u?**  
   Polja su final jer osiguravaju nepromjenjivost (immutability) objekta nakon stvaranja, čime se izbjegavaju neželjene promjene stanja. Ako polje `naslov` (koje se čita kao `as String`) nedostaje u JSON-u i ima vrijednost `null`, bacila bi se iznimka tipa `TypeError` jer `null` nije podtip tipa `String`.
2. **Što se događa kad iznimku iz Futurea ne uhvatimo ni na jednom mjestu?**  
   Neuhvaćena iznimka u Asynchronous kodu (Future) rezultira neobrađenom pogreškom (unhandled asynchronous exception), što može uzrokovati rušenje aplikacije ili ispis greške u konzoli (u obliku zone errora).
3. **Zašto se Future stvara u polju, a ne u metodi build, i navedite tri stanja koja svaki zaslon s podacima mora prikazati?**  
   Future se stvara u polju (ili `initState`-u) jer se metoda `build` poziva vrlo često (prilikom svakog renderiranja widgeta). Da se stvara u `build`-u, svaki bi ispis ili promjena stanja ponovno pokretali mrežni zahtjev u beskonačnoj petlji. Tri obavezna stanja su: stanje učitavanja (loading), stanje uspjeha (success/podaci) i stanje pogreške (error).

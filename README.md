# zadatci_app

Zašto Always Free instanca?
Oracle Cloud Infrastructure (OCI) u sklopu svog Always Free paketa omogućava besplatno korištenje resursa koji premašuju standardne probne pakete drugih računalnih oblaka. Konkretno, omogućava korištenje Ampere A1 Flex procesora (ARM arhitektura) do 4 OCPU-a i 24 GB RAM-a potpuno besplatno, što korisnicima pruža snažan, stabilan i besplatan poslužitelj za razvoj i produkciju manjih aplikacija.

Zašto se za Supabase ne smije odabrati Micro shape?
Ograničenje memorije (RAM): Supabase zahtijeva minimalno 4 GB RAM-a za stabilno pokretanje svih svojih servisa i kontejnera.  
Nedostatak resursa na Micro shape-u: Shape poput VM.Standard.E2.1.Micro nudi svega 1 GB RAM-a, što je premalo za pokretanje Supabase-a te će uzrokovati rušenje servisa zbog nedostatka memorije (Out Of Memory / OOM).  
Optimalan izbor: Iz tog razloga se bira VM.Standard.A1.Flex sa 2 OCPU-a i 12 GB RAM-a, čime se u potpunosti zadovoljavaju hardverski zahtjevi unutar besplatnih limita. 

Razlika između Docker slike (image) i kontejnera: Docker slika je statički, nepromjenjivi (read-only) predložak ili nacrt koji sadrži kod, knjižnice i ovisnosti potrebne za pokretanje aplikacije. S druge strane, Docker kontejner je pokrenuta, dinamična instanca te slike u kojoj aplikacija stvarno izvršava svoje procese.

Zašto se podaci baze moraju držati u volumenu: Budući da su Docker slike i sami kontejneri nepromjenjivi i privremeni (svakim gašenjem ili brisanjem kontejnera gube se podaci unutar njega), volumeni (volumes) služe za trajno spremanje podataka na hard disk poslužitelja. Time osiguravamo da podaci baze podataka ostanu sačuvani i nepromijenjeni čak i ako se kontejner ugasi, ponovno pokrene ili nadogradi.

Postgres: Temeljni sustav za upravljanje relacijskom bazom podataka (RDBMS) u kojem se pohranjuju svi podaci, tablice i provode sigurnosne politike (RLS).

REST (PostgREST): Poslužitelj koji automatski pretvara PostgreSQL bazu podataka u čist, spreman RESTful API, omogućujući aplikacijama dohvaćanje i upravljanje podacima putem HTTP zahtjeva.

Auth: Servis zadužen za upravljanje korisnicima, autentifikaciju (prijava, registracija, tokeni) i sigurnost temelji na JSON Web Tokenima (JWT).

Storage: Servis za pohranu, upravljanje i preuzimanje datoteka i medijskih sadržaja (poput slika ili dokumenata).

Studio: Grafičko web sučelje (Dashboard) koje omogućuje jednostavno upravljanje bazom podataka, pregled tablica, izradu upita i konfiguraciju sustava

Gateway na portu 8000: Ulazna točka (često implementirana kroz Kong ili Envoy proxy) koja preusmjerava, štiti i prosljeđuje sve dolazne mrežne zahtjeve prema odgovarajućim unutrašnjim Supabase servisima.
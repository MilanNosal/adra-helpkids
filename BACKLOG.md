# HELPKIDS — produktový backlog

Dokument pre tím. Vlastník je Product Owner, poradie epikov a položiek meníte len vy.

**Ako to čítať.** Zoznam je usporiadaný — čo je vyššie, robí sa skôr. Epiky 0–3 majú
akceptačné kritériá a sú pripravené na plánovanie. Epiky 4–9 sú zámerne hrubé; rozpíšu sa,
až keď sa k nim priblížime. Rozpisovať ich teraz je premrhaná práca, pretože sa do tej doby
zmenia.

**Čo tu nie je.** Odhady, priradenie ľuďom a rozdelenie na technické úlohy. To je vec tímu.
Rovnako tu nie je, *ako* sa má čokoľvek implementovať — kritériá hovoria, čo musí platiť.
Ak niektoré kritérium predpisuje riešenie, je to chyba v zadaní, nahláste ju.

**Nevyriešené otázky.** Položky označené `⨯ blokuje <ID>` sa nesmú vziať do sprintu, kým
PO nedodá odpoveď. ID odkazuje na `OTAZKY-PRE-ADRA.md`.

---

## Obmedzenia, ktoré nie sú predmetom diskusie

Tri z nich sú rozhodnutia zadávateľa, ostatné vyplývajú z toho, že systém pracuje s dátami
detí a s reálnymi peniazmi.

**O1 — Verejný web zostáva na WordPresse.** Systém negeneruje verejný web, iba **export**
profilu dieťaťa (HTML/Markdown + fotky) na vloženie do WordPressu. Export je jednosmerný.
WordPress nemá a nesmie mať prístup k databáze systému ani k jeho úložisku súborov. Vlastný
verejný web nie je v rozsahu.

**O2 — Zdrojom pravdy o peniazoch je účtovníctvo ADRA.** Systém neúčtuje, neintegruje sa
s bankou a nepáruje platby. Drží len prevádzkový fakt „sponzorstvo × trimester = zaplatené
/ nezaplatené, potvrdil ten a ten vtedy“. Systém nikdy nedrží platobné údaje darcov.

**O3 — Import z existujúcich Excelov je súčasť zadania**, nie jednorazová migrácia. Ústi
do tej istej schvaľovacej fronty ako formulár od školy.

**O4 — Škola nikdy nepíše priamo do produkčných dát.** Medzi podkladom od školy a záznamom
dieťaťa je vždy schvaľovací a redakčný krok ADRA.

**O5 — Prístupové práva sa vynucujú na serveri.** Skrytie v UI sa nepočíta. Škola vidí
svoje deti, darca svoje dieťa, nič viac.

**O6 — Fotky detí, vysvedčenia a PDF zmlúv nesmú byť dostupné na uhádnuteľnej adrese**
a nesmú ležať v priestore, odkiaľ sa dá súbor spustiť. Typ prílohy sa validuje.

**O7 — Celý stav systému je v databáze a v súboroch.** Nič podstatné nesmie žiť len
v nastaveniach hostingu alebo v pluginoch WordPressu. Konfigurácia ide cez premenné
prostredia, žiadne údaje napevno v kóde. Dôvod: ADRA musí byť schopná systém presunúť
k inému poskytovateľovi.

**O8 — Žiadne produkčné dáta v testovacom prostredí.** Kým PO nepovie inak, pracuje sa
výhradne na vymyslených dátach.

---

## Definition of Done

Položka je hotová, keď:

1. Akceptačné kritériá sú splnené a PO ich videl na Sprint Review.
2. Kritériá označené `[test]` majú automatizovaný test, ktorý padá, keď sa pravidlo poruší.
3. Kód prešiel review iného člena tímu.
4. Prístupové práva sú vynútené na serveri (O5).
5. Zmeny citlivých polí zapisujú audit.
6. Je nasadené na testovacom prostredí automatizovaným nasadením, nie ručne.
7. Neobsahuje produkčné dáta (O8).

---

# Epik 0 — Nasadená prázdna aplikácia

Cieľ: v prvom sprinte vedieť, či zvolený hosting tento projekt unesie. Prekvapenia
z hostingu majú prísť teraz, nie v poslednom týždni.

### 0.1 Prázdna aplikácia beží na reálnom hostingu

Ako tím chceme mať od prvého sprintu nasadenú aplikáciu na tej infrastruktúre, na ktorej
systém nakoniec pobeží, aby sme jej limity zistili skôr, než na nich postavíme návrh.

- Na produkčnej adrese je dostupná stránka z nasadenej aplikácie, cez HTTPS
- Konfigurácia (databáza, úložisko, tajomstvá) ide cez premenné prostredia (O7)
- Existuje oddelené testovacie prostredie
- V repozitári je popísané, ako sa aplikácia nasadí od nuly

### 0.2 Automatizované nasadenie a testy

- Nasadenie na testovacie prostredie sa spúšťa bez ručných krokov
- Testy bežia automaticky pri každej zmene
- Nasadenie na produkciu je jeden vedomý krok, nie kopírovanie súborov cez FTP

### 0.3 Overenie limitov hostingu

Preskúmavacia položka s písomným výstupom, nie funkcia. Treba zistiť a zapísať: limit počtu
súborov (inodov), dostupnosť a minimálny interval plánovaných úloh, či sú povolené
odchádzajúce spojenia na cudzie služby, dostupné knižnice na prácu s obrázkami, reálny
`max_execution_time`. Výstup: krátky zápis v repozitári a informácia PO, ak niečo z toho
mení predpoklady.

### 0.4 Uloženie a výdaj súboru s kontrolou prístupu

Ako pracovník ADRA chcem nahrať fotku dieťaťa a vidieť ju, a chcem mať istotu, že sa
k nej nedostane nikto, kto na ňu nemá právo.

- Súbor sa nedá získať bez overenia oprávnenia [test]
- Adresa súboru sa nedá uhádnuť ani odvodiť z identifikátora dieťaťa [test] (O6)
- Riešenie musí uniesť cieľový objem podľa odpovede na otázku B11
- Pri uploade sa validuje typ súboru [test]
- `⨯ blokuje B11` (len pre voľbu riešenia, nie pre prototyp)

---

# Epik 1 — Dieťa, škola, roly

Základ, na ktorom stojí všetko ostatné.

### 1.1 Prihlásenie a roly

- Existujú role: administrátor ADRA, škola, darca
- Používateľ vidí výhradne to, čo jeho rola dovoľuje, a vynucuje to server [test] (O5)
- Škola nevidí identitu darcu ani jeho platby [test] *(invariant 5)*
- Darca vidí výhradne dieťa, ktoré podporuje [test]

### 1.2 Záznam dieťaťa

Ako pracovník ADRA chcem viesť úplný záznam o dieťati, aby sa tie isté údaje neprepisovali
na viacerých miestach.

- Rozsah polí podľa `Formulár dieťaťa.docx`: osobné údaje, situácia rodiny, kto sa o dieťa
  stará, podmienky a prostredie bývania, pôvod, príbeh, finančná situácia, potrebný typ
  podpory
- Záznam má stav podľa životného cyklu (schválené → zverejnené → rezervované → podporované
  → pozastavené / ukončené)
- Kód dieťaťa je jednoznačný a nemenný
- `⨯ blokuje B3` (kto prideľuje kód a či je stabilný)

### 1.3 Záznam školy a programov

- Škola: názov, adresa, popis situácie, kontaktná osoba, ponúkané programy
- Program podpory = škola + rozsah (len strava / školné / školné + strava / + internát)
  s cenou za trimester
- Cena programu je vedená v čase: zmena ceny neovplyvní už podpísané sponzorstvá [test]
  *(invariant 4)*
- `⨯ blokuje A3, B7, B8` (cenník, mena, kto smie meniť ceny)

### 1.4 Zmena bankového spojenia školy

Ako koordinátor ADRA chcem, aby zmenu bankového spojenia školy musel potvrdiť druhý človek,
aby prepísané číslo účtu nemohlo presmerovať reálne peniaze.

Toto je najcennejší cieľ útoku v celom systéme. Nie preto, že by bol systém slabý — stačí
presvedčivý e-mail a oprávnený používateľ prepíše údaj sám.

- Zmena sa neuplatní, kým ju nepotvrdí druhý používateľ ADRA [test] *(invariant 10)*
- Škola si bankové spojenie nemení sama [test]
- O zmene je notifikovaný aj druhý človek v ADRA, tichá zmena nie je možná
- Zmena sa zapíše do auditu: kto, kedy, z čoho na čo
- Audit sa nedá z aplikácie prepísať ani zmazať [test]
- `⨯ blokuje E1, E2` (mená dvoch konkrétnych ľudí a spôsob overenia)

### 1.5 Dvojfaktorové overenie pre administrátorov ADRA

### 1.6 Evidencia súhlasov

Ako pracovník ADRA chcem mať súhlasy vedené ako samostatné záznamy, aby som pri zverejnení
profilu vedel, či ho smiem zverejniť.

- Typy súhlasu podľa `Formulár dieťaťa.docx`: zaradenie do programu, spracovanie údajov,
  zverejnenie príbehu a fotiek, poskytovanie výsledkov darcovi
- Každý súhlas má dátum, platnosť a sken podpisu
- Súhlas sa dá odvolať a odvolanie je viditeľné
- `⨯ blokuje D2, D3, D4` (existujúce súhlasy, forma, kto podpisuje za sirotu)

### 1.7 Opatrovník a domácnosť

- Z jednej domácnosti môže byť v programe viac detí a profil rodiny sa zdieľa
- `⨯ blokuje B10`

---

# Epik 2 — Generovanie zmlúv

Najvyššia hodnota za najmenej práce: odstraňuje ručné vypisovanie bez toho, aby sa čokoľvek
muselo zmeniť na strane škôl, darcov alebo webu. Stačí mu epik 1.

### 2.1 Zmluva ADRA–darca

Ako pracovník ADRA chcem vygenerovať zmluvu s darcom zo šablóny, aby som ju nemusel
vypisovať ručne a aby v nej nemohla byť chyba v sume ani v mene dieťaťa.

- Zmluva sa generuje do PDF zo šablóny a z údajov, ktoré systém už má
- Suma v zmluve je suma programu platná v čase podpisu [test] *(invariant 4)*
- Zmluva sa generuje výhradne zo schválených dát, nikdy zo surového podkladu školy [test]
  *(invariant 3)*
- Vygenerované PDF sa uloží k sponzorstvu a dá sa znovu stiahnuť
- `⨯ blokuje A1` (šablóna)

### 2.2 Zmluva ADRA–škola · `⨯ blokuje A1`

### 2.3 Zmluva škola–opatrovník · `⨯ blokuje A1`

### 2.4 Stav zmluvy

- Zmluva má stav (vygenerovaná → podpísaná) a dátum
- Podpísaný sken sa dá priložiť

---

# Epik 3 — Fronta podkladov a schvaľovanie

Ruší prepisovanie do Excelu a vytvára zdroj pravdy. Excel zostáva ako export, nie ako
databáza.

### 3.1 Fronta podkladov pre ADRA

Ako pracovník ADRA chcem vidieť, ktoré podklady čakajú na moje schválenie, aby som nemusel
držať stav procesu v hlave.

- Fronta zobrazuje podklady v stavoch odoslaný / vrátený na doplnenie
- Pri každom podklade je škola, dátum odoslania a počet dní čakania
- Fronta je jediné miesto, kam ústia podklady z formulára školy aj z importu (O3)

### 3.2 Editácia a schválenie podkladu

Ako pracovník ADRA chcem podklad pred schválením redakčne upraviť, aby sa do databázy
dostal preložený a prepísaný text, nie surový vstup zo školy.

- Podklad sa dá editovať pred schválením (preklad, preformulovanie príbehu)
- Schválením vzniká alebo sa aktualizuje záznam dieťaťa (O4)
- Pôvodný podklad zostáva čitateľný a nemenný — je vidieť, čo prišlo a čo sme z toho
  urobili [test]
- `⨯ blokuje C7` (kto prekladá, jazyk vstupu)

### 3.3 Vrátenie podkladu na doplnenie

- Podklad sa dá vrátiť škole s poznámkou, čo chýba
- Škola vidí, čo sa od nej žiada

---

# Epik 4 — Import z Excelov

`⨯ blokuje A2` (vzorka), `D2` (súhlasy pri importovaných deťoch)

- 4.1 Import zoznamu detí s mapovaním stĺpcov, tolerantný k nekonzistentným dátam
- 4.2 Report toho, čo sa nenaimportovalo a prečo
- 4.3 Import ústi do schvaľovacej fronty, nie priamo do databázy (O3, O4)
- 4.4 Naimportované dieťa bez evidovaného súhlasu sa nedá zverejniť *(invariant 1)*

---

# Epik 5 — Export profilu a rezervácia

Odstraňuje ručné skladanie stránok aj riziko, že ADRA prisľúbi jedno dieťa dvom darcom.

- 5.1 Export profilu dieťaťa pre WordPress (HTML/Markdown + fotky), **opakovateľný** —
  pri zmene sa vygeneruje znovu a prepíše (O1)
- 5.2 Export nikdy neobsahuje presnú adresu dieťaťa ani plné meno opatrovníka
  *(invariant 7)*
- 5.3 Profil sa nedá exportovať bez evidovaného súhlasu so zverejnením *(invariant 1)*
- 5.4 Stav dostupnosti dieťaťa nie je súčasťou exportu a žije výhradne v systéme
  *(invariant 8)*
- 5.5 Sponzorský formulár, do ktorého darca prichádza odkazom z WordPressu
- 5.6 Rezervácia dieťaťa: najviac jedna aktívna naraz *(invariant 2)*, s lehotou, po ktorej
  sa dieťa vracia do ponuky aj vtedy, keď medzitým na serveri nič nebežalo
- 5.7 Verejne dostupný formulár je obmedzený na počet pokusov a neprezradí nič nad rámec
  toho, čo je už na verejnom profile
- 5.8 Zoznam „na úpravu vo WordPresse“ pre prípady, keď dieťa získa podporu alebo sa odvolá
  súhlas
- `⨯ blokuje C1` (lehota rezervácie), `C8` (kto upravuje WordPress)

---

# Epik 6 — Trimestre, platby, prehľady

Prevádzkové prehľady, nie účtovníctvo (O2).

- 6.1 Trimestre s konkrétnymi dátumami, na ne sa viažu platby, vysvedčenia a prehľady
- 6.2 Sponzorstvo: darca ↔ dieťa ↔ program, s dátumom začiatku, dĺžkou v trimestroch,
  dohodnutou sumou a stavom
- 6.3 Pracovník ADRA zaznačí, že platba darcu za trimester prišla
- 6.4 Prehľad „koľko treba poslať ktorej škole za tento trimester“
- 6.5 Prehľad „ktoré deti sú pokryté zmluvou, ale nezaplatené“ — rozdiel medzi tým, čo ADRA
  dlží škole, a tým, čo darcovia zaplatili, musí byť viditeľný, nie skrytý *(invariant 6)*
- 6.6 Prehľady sú označené ako prevádzkové; pri rozpore vyhráva účtovníctvo ADRA
  *(invariant 9)*
- 6.7 Zachytenie prechodu podporované → hľadá podporu, keď darca prestane platiť, a to včas,
  nie až pri trimestrálnom účtovaní
- `⨯ blokuje B5` (dátumy trimestrov), `C2`, `C3`, `C4`

---

# Epik 7 — Formulár pre školy

Najväčší dlhodobý efekt, ale najrizikovejší krok: vyžaduje zmenu správania ľudí v Ugande,
slabé pripojenie a prácu na mobile.

- 7.1 Štruktúrovaný formulár dieťaťa pre školu, použiteľný na mobile a pri slabom pripojení
- 7.2 Validácia pri zadaní, aby chýbajúce polia neodhalila až ADRA
- 7.3 Upload fotiek a vysvedčení školou
- 7.4 Systém musí uniesť aj to, že podklad zadá pracovník ADRA namiesto školy
- 7.5 Prehľad registrovaných a sponzorovaných detí pre školu, so sumami za trimester
  a bez údajov o darcovi *(invariant 5)*
- `⨯ blokuje C11` (konektivita a zariadenia), `C12`

---

# Epik 8 — Darcovský portál

Nie úspora práce, ale retencia darcov — teda stabilita financovania. Darca, ktorý je po
podpise v tme, odíde, a jeho odchod znamená dieťa bez financovania v rozbehnutom roku.

- 8.1 Prístup darcu ku karte „svojho“ dieťaťa
- 8.2 Vysvedčenia, hodnotenia a priebežné fotky po trimestroch
- 8.3 Prehľad vlastných platieb
- 8.4 Upozornenie darcovi, keď pribudne nové vysvedčenie alebo fotky
- `⨯ blokuje E4` (režim prístupu darcu), `C6` (ako často škola nahráva)

---

# Epik 9 — Prevádzka a prevzatie

**Beží priebežne od prvého sprintu, nie na konci.** Priorita je trvácnosť dát, nie vysoká
dostupnosť: keď systém pár hodín nebeží, nestane sa nič, ale ak sa stratí týždeň zadaných
podkladov, ADRA si ich už nemá odkiaľ vziať.

- 9.1 Automatické zálohovanie databázy **aj súborov** — fotky, vysvedčenia a PDF zmlúv sú
  rovnako dôležité ako záznamy
- 9.2 Aspoň raz vyskúšaná obnova na čistom stroji, s napísaným postupom. Neodskúšaná záloha
  je presvedčenie, nie záloha.
- 9.3 Kópia zálohy mimo hostingu, na účte vo vlastníctve ADRA
- 9.4 Dokumentácia pre ADRA a zaškolenie ľudí, ktorí systém budú používať
- 9.5 Prevzatie: kto systém prevádzkuje, kto drží prístupy, kto platí faktúry
- `⨯ blokuje F1, F2, F3, F4, F5`

---

## Čo nie je v rozsahu

Pomenované, aby sa to nepýtalo opakovane:

- Vlastný verejný web (O1)
- Účtovníctvo, vydávanie účtovných dokladov, bankové integrácie, párovanie platieb,
  spracovanie platieb kartou (O2)
- Dvojsmerná synchronizácia s WordPressom
- Prístup opatrovníka do systému — opatrovník nebude používateľom nikdy
- Dobeh historických sponzorstiev (`⨯ otázka F6`; predbežne: systém začne od aktuálneho
  školského roka)
- Mobilná aplikácia

# HELPKIDS — produktový backlog

Dokument pre tím. Za obsah a poradie zodpovedá Product Owner; tím počas refinementu
navrhuje rozdelenie, technické riešenie, závislosti a zmeny poradia podľa toho, čo zistí.

**Ako to čítať.** Zoznam je usporiadaný podľa produktovej priority. Epiky 0–3 sú
podrobnejšie a sú určené na prvé refinementy; konkrétna položka je pripravená na výber do
sprintu až vtedy, keď spĺňa Definition of Ready v `backlog_tickets.md`. Epiky 4–9 sú
zámerne hrubé a spresnia sa až pred ich realizáciou.

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
s bankou a nepáruje platby. Drží len prevádzkový fakt „sponzorstvo × mesiac = zaplatené
/ nezaplatené, potvrdil ten a ten vtedy“. Systém nikdy nedrží platobné údaje darcov.

**O3 — Import z existujúcich Excelov je súčasť zadania**, nie jednorazová migrácia. Ústi
do tej istej schvaľovacej fronty ako formulár od školy.

**O4 — Škola nikdy nepíše priamo do produkčných dát.** Medzi podkladom od školy a záznamom
dieťaťa je vždy schvaľovací a redakčný krok ADRA.

**O5 — Prístupové práva sa vynucujú na serveri.** Skrytie v UI sa nepočíta. Škola vidí
svoje deti, darca svoje deti, nič viac.

**O6 — Fotky detí, vysvedčenia a PDF zmlúv nesmú byť dostupné na uhádnuteľnej adrese**
a nesmú ležať v priestore, odkiaľ sa dá súbor spustiť. Typ prílohy sa validuje. Platí pre
všetky súbory v systéme. Jedinou výnimkou sú fotky, ktoré ADRA pri dieťati výslovne označí
na zverejnenie: ich kópia ide v exporte profilu (O1) a vo WordPresse je zámerne verejná.
Reporty (vysvedčenia, priebežné fotky) a zmluvy sa nikdy neexportujú.

**O7 — Celý stav systému je v databáze a v súboroch.** Nič podstatné nesmie žiť len
v nastaveniach hostingu alebo v pluginoch WordPressu. Konfigurácia ide cez premenné
prostredia, žiadne údaje napevno v kóde. Dôvod: ADRA musí byť schopná systém presunúť
k inému poskytovateľovi.

**O8 — Žiadne produkčné dáta v testovacom prostredí.** Kým PO nepovie inak, pracuje sa
výhradne na vymyslených dátach.

**O9 — Časované udalosti nesmú závisieť od návštevy aplikácie.** Expirácia rezervácie,
upozornenia na čakanie a omeškané platby sa spracujú automaticky. Opakované spracovanie
nesmie vytvoriť duplicitný stav ani poslať ten istý e-mail viackrát.

---

## Definition of Done

Položka je hotová, keď:

1. Akceptačné kritériá sú splnené a výsledok sa dá predviesť na testovacom prostredí.
2. Kritériá označené `[test]` majú automatizovaný test, ktorý padá, keď sa pravidlo poruší.
3. Kód prešiel review iného člena tímu.
4. Prístupové práva sú vynútené na serveri (O5).
5. Zmeny citlivých polí a stavov zapisujú audit. Minimálne: bankové spojenie, ceny,
   suma a periodicita sponzorstva, stav zmluvy a sponzorstva, potvrdenie alebo oprava
   platby, zoznam trimestra, rola a deaktivácia účtu, označenie fotky na zverejnenie,
   schválenie alebo vrátenie podkladu, schválenie reportu a prestup dieťaťa do inej školy.
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
`max_execution_time` a praktický limit veľkosti uploadu. Tím s PO zároveň zapíše merateľný
test cieľového objemu 50 škôl a 5 000 detí vrátane predpokladaného počtu a veľkosti súborov.
Výstup: krátky zápis v repozitári a informácia PO, ak niečo z toho mení predpoklady.

### 0.4 Uloženie a výdaj súboru s kontrolou prístupu

Ako pracovník ADRA chcem nahrať fotku dieťaťa a vidieť ju, a chcem mať istotu, že sa
k nej nedostane nikto, kto na ňu nemá právo.

- Súbor sa nedá získať bez overenia oprávnenia [test]
- Adresa súboru sa nedá uhádnuť ani odvodiť z identifikátora dieťaťa [test] (O6)
- Riešenie prejde testom cieľového objemu definovaným v 0.3 [test]
- Pri uploade sa validuje typ súboru [test]

---

# Epik 1 — Dieťa, škola, roly

Základ, na ktorom stojí všetko ostatné.

### 1.1 Prihlásenie a roly

- Existujú role: admin ADRA, pracovník ADRA, škola, darca
- Admin ADRA môže všetko, čo pracovník, a navyše spravuje používateľské účty
- Používateľ vidí výhradne to, čo jeho rola dovoľuje, a vynucuje to server [test] (O5)
- Účet sa dá deaktivovať; deaktivovaný účet sa neprihlási a jeho existujúce relácie prestanú
  platiť [test]. Deaktivácia mení len prístup, nie dáta: deti, podklady, sponzorstvá
  a história zostávajú bez zmeny [test] *(predpoklad PO)*
- Používateľ si vie obnoviť zabudnuté heslo cez jednorazový odkaz s expiráciou [test]
- Škola nevidí identitu darcu ani jeho platby [test] *(invariant 5)*
- Darca vidí výhradne deti, ktoré podporuje [test]
- Rozhranie je pripravené na preklad; prvá verzia je v angličtine

### 1.2 Záznam dieťaťa

Ako pracovník ADRA chcem viesť úplný záznam o dieťati, aby sa tie isté údaje neprepisovali
na viacerých miestach.

- Rozsah polí podľa `Formulár dieťaťa.docx`: osobné údaje, situácia rodiny, kto sa o dieťa
  stará, podmienky a prostredie bývania, pôvod, príbeh, finančná situácia, potrebný typ
  podpory, fotky, dátumy (vyplnenie, zverejnenie, začiatok podpory)
- Sekcia „Osobné súhlasy“ z formulára sa **nevytvára**: súhlasy sú súčasťou zmluvy
  škola–opatrovník a systém ich neeviduje (viď Čo nie je v rozsahu)
- Pri každej fotke sa dá označiť, či smie ísť do verejného exportu (O6)
- Záznam má stav podľa životného cyklu (schválené → zverejnené → rezervované → podporované
  → ukončené)
- Kód dieťaťa generuje systém, je jednoznačný a nemenný [test]
- Prestup do inej školy: systém prestup zaznamená, dieťa zostáva jedno s rovnakým kódom
  a sponzorstvom; v novej škole je aktuálnym žiakom, v histórii trimestrov starej školy naň
  zostáva odkaz [test]

### 1.3 Záznam školy a programov

- Škola: názov, sídlo a korešpondenčná adresa, popis situácie, kontaktná osoba, bankové spojenie, ponúkané programy
- Program podpory = škola + rozsah (len strava / školné / školné + strava / + internát)
  s cenou za trimester v eurách
- Mesačná suma programu je vždy 3 × aktuálna cena za trimester / 12; zmenou ceny za
  trimester sa zmení aj ona [test]
- Cenník mení ADRA; zmena platí pre nové sponzorstvá a nemení sumu existujúcich darcov
  [test] *(invariant 4)*

### 1.4 Zmena bankového spojenia školy

- Bankové spojenie mení len ADRA; škola ho zmeniť nemôže [test] *(invariant 10)*.
  Potvrdené PO: odpoveď ADRA „zmena je v rukách školy“ (E1) znamená, že zmenu iniciuje
  škola, nie že ju v systéme zapisuje
- Škola o zmenu žiada mimo systému; ADRA pri zmene priloží dodatok k zmluve
- Zmena sa zapíše do histórie: kto, kedy, z čoho na čo; históriu sa nedá z aplikácie
  prepísať ani zmazať [test]

### 1.5 Dvojfaktorové overenie pre používateľov ADRA

- Admin aj pracovník ADRA sa bez druhého faktora neprihlásia [test]
- Škola a darca druhý faktor nepotrebujú
- Pri strate druhého faktora ho používateľovi resetuje admin, nie samoobsluha cez e-mail
  [test]; pre prípad, že ho stratí jediný admin, existuje napísaný postup obnovy

### 1.7 Súrodenci

- Deti sa dajú prepojiť ako súrodenci; nejde o spoločný profil rodiny, každé dieťa má
  vlastné údaje

### 1.8 Pozvanie školy

- Školu do systému pozýva ADRA e-mailom; škola si cez pozvánku doplní údaje a nastaví
  prístup
- Škola môže mať viac používateľov, každý s vlastným účtom; každého pozýva ADRA. Všetci
  používatelia školy vidia to isté *(predpoklad PO)*
- Pozvánka je jednorazová, má konfigurovateľnú expiráciu a po použití ani po expirácii sa
  nedá znovu použiť [test]
- Verejná registrácia škôl neexistuje [test]

### 1.9 Darca a sponzorstvo

Základ pre zmluvy (epik 2) aj platby (epik 6).

- Darca: kontaktné a fakturačné údaje, adresa trvalého pobytu (u firmy sídlo)
  a korešpondenčná adresa, účet s heslom
- Sponzorstvo darca ↔ dieťa, striktne 1:1 — dieťa má najviac jedného darcu, darca môže mať
  viac detí [test]
- Sponzorstvo nesie mesačnú sumu, periodicitu splácania (mesačne / štvrťročne / polročne /
  ročne) a stav (čaká na schválenie → aktívne → ukončené)
- Splátkový kalendár sa počíta od schválenia zmluvy [test]

### 1.10 Údaje ADRA

- Názov, IČO, štatutárny zástupca, sídlo, korešpondenčná adresa, IBAN, kontakt; spravuje
  ich ADRA v systéme a šablóny zmlúv ich preberajú odtiaľ, nie sú v nich natvrdo
- Zmena sa zapíše do histórie a nemení už vygenerované zmluvy [test]

---

# Epik 2 — Generovanie zmlúv

Mechanizmus generovania zo schválených údajov sa dá postaviť hneď po epiku 1. Produkčná
zmluva ADRA–darca sa však automaticky vytvára až pri rezervácii v epiku 5; zmluvy so školou
a opatrovníkom sa dajú používať samostatne.

### 2.1 Zmluva ADRA–darca

Ako pracovník ADRA chcem, aby systém zmluvu s darcom vygeneroval zo šablóny sám, aby som ju
nemusel vypisovať ručne a aby v nej nemohla byť chyba v sume ani v mene dieťaťa.

- Zmluva sa generuje do PDF zo šablóny a z údajov, ktoré systém už má
- Systém zmluvu vygeneruje okamžite pri vzniku rezervácie (5.6), bez zásahu pracovníka
  ADRA, a darca si ju hneď môže stiahnuť [test]
- Zmluva je na neurčito s mesačnou výpovednou lehotou a obsahuje splátkový kalendár
  (mesačne / štvrťročne / polročne / ročne)
- Suma darcu je suma programu platná v čase vzniku rezervácie, keď sa zmluva generuje;
  zmena cenníka počas lehoty rezervácie ani neskôr ju nemení [test] *(invariant 4)*
- Zmluva sa generuje výhradne zo schválených dát, nikdy zo surového podkladu školy [test]
  *(invariant 3)*
- Vygenerované PDF sa uloží k sponzorstvu a dá sa znovu stiahnuť
- `⨯ blokuje A1` (šablóna)

### 2.2 Zmluva ADRA–škola · `⨯ blokuje A1`

### 2.3 Zmluva škola–opatrovník · `⨯ blokuje A1`

- Škola si vygenerovanú zmluvu stiahne a podpísanú nahrá späť

### 2.4 Stav zmluvy

- Zmluva má stav (vygenerovaná → podpísaná) a dátum
- Podpísaný sken sa dá priložiť

### 2.5 Dodatky k zmluvám

- K zmluve sa dá vygenerovať dodatok (zmena sumy darcu, zmena bankového spojenia školy)
- Zmena sumy darcu sa uplatní len dodatkom a len z rozhodnutia ADRA — nikdy automaticky
  [test] *(invariant 4)*

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
dostal upravený text, nie surový vstup zo školy.

- Podklad sa dá editovať pred schválením (preformulovanie príbehu, úprava fotiek,
  kontrola vysvedčení)
- Schválením vzniká alebo sa aktualizuje záznam dieťaťa (O4)
- Pôvodný podklad zostáva čitateľný a nemenný — je vidieť, čo prišlo a čo sme z toho
  urobili [test]

### 3.3 Vrátenie podkladu na doplnenie

- Podklad sa dá vrátiť škole s poznámkou, čo chýba
- Škola vidí, čo sa od nej žiada

---

# Epik 4 — Import z Excelov

`⨯ blokuje A2` (vzorka)

- 4.1 Import zoznamu detí s mapovaním stĺpcov, tolerantný k nekonzistentným dátam
- 4.2 Report toho, čo sa nenaimportovalo a prečo
- 4.3 Import ústi do schvaľovacej fronty, nie priamo do databázy (O3, O4)
- 4.5 Voliteľne: read-only import historických sponzorstiev (nice-to-have)

---

# Epik 5 — Export profilu a rezervácia

Odstraňuje ručné skladanie stránok aj riziko, že ADRA prisľúbi jedno dieťa dvom darcom.

- 5.1 Export profilu dieťaťa pre WordPress (HTML/Markdown + fotky označené na zverejnenie,
  O6), **opakovateľný** —
  pri zmene sa vygeneruje znovu a prepíše (O1). Export je v angličtine, do slovenčiny ho
  prekladá pracovník ADRA
- 5.2 Export nikdy neobsahuje presnú adresu dieťaťa ani plné meno opatrovníka
  *(invariant 7)*
- 5.4 Stav dostupnosti dieťaťa nie je súčasťou exportu a žije výhradne v systéme
  *(invariant 8)*
- 5.5 Sponzorský formulár, do ktorého darca prichádza odkazom z WordPressu. Nový darca si
  pri ňom založí účet s heslom; existujúci darca sa prihlási a ďalšie dieťa rezervuje pod
  tým istým účtom. E-mail darcu je unikátny, druhý účet s tým istým e-mailom nevznikne
  [test]. Rezervácia vznikne až po potvrdení e-mailu nového darcu; do potvrdenia zostáva
  dieťa voľné a vymyslený e-mail ho nezablokuje [test] *(predpoklad PO)*
- 5.6 Rezervácia dieťaťa: najviac jedna aktívna naraz *(invariant 2)*, s lehotou 7
  kalendárnych dní, po ktorej sa dieťa vracia do ponuky aj vtedy, keď medzitým na serveri
  nič nebežalo [test]. Lehota je rozhodnutie PO; ADRA v C1 navrhla 5 pracovných dní
- 5.7 Verejne dostupný formulár má konfigurovateľný limit počtu pokusov za časové okno,
  predvolene 5 odoslaní za hodinu z jednej adresy alebo pre jeden e-mail.
  Po prekročení limitu ďalší pokus odmietne bez prezradenia stavu dieťaťa [test]
- 5.8 Zoznam „na úpravu vo WordPresse“ pre prípady, keď dieťa získa podporu
- 5.9 Keď darca v lehote nahrá podpísanú zmluvu, lehota sa zastaví; rezerváciu potom zruší
  už len ADRA alebo darca zrušením zmluvy [test]. Nahratá zmluva čaká vo fronte ADRA
  s počtom dní čakania; ak ju ADRA neposúdi do 3 dní, systém ADRA upozorní. Dieťa sa
  automaticky neuvoľní, rozhoduje vždy ADRA [test]
- 5.10 Po vypršaní rezervácie dostane darca e-mail
- 5.13 Ak ADRA nahratú zmluvu odmietne, rezervácia sa zruší, dieťa sa vráti do ponuky
  a darca dostane e-mail [test]
- 5.11 Pri dieťati je vidieť jeho súrodencov; jedným krokom sa dajú rezervovať všetci voľní,
  pričom vznikne samostatná rezervácia a zmluva pre každé dieťa
- 5.12 ADRA schváli darcu po obdržaní podpísanej zmluvy; tým vzniká aktívne sponzorstvo
  a darcovi sa sprístupní karta dieťaťa

---

# Epik 6 — Trimestre, platby, prehľady

Prevádzkové prehľady, nie účtovníctvo (O2). Platby darcov a platby školám sú dva úplne
oddelené toky.

- 6.1 Trimester otvára explicitne pracovník ADRA a označí ho `ROK/mesiac`; označenie je
  unikátne [test]
- 6.2 Trimester v príprave: systém pre každú školu navrhne zoznam jej žiakov s aktívnym
  sponzorstvom (schválenou zmluvou) — rezervácia ani nahratá zmluva nestačí [test].
  Otvorením sa zoznam zmrazí a za deti v ňom ADRA škole zaplatí celý trimester
  *(invariant 6)* [test]
- 6.2a Pred otvorením môže pracovník ADRA dieťa s darcom zo zoznamu vyradiť a pridať
  dieťa bez darcu, ktoré financuje ADRA. Pri každom dieťati v trimestri je vidieť, či je
  kryté darcom alebo ADRA; škola to nevidí [test]
- 6.3 Zoznam otvoreného trimestra sa dá opraviť; oprava sa zapíše do histórie
- 6.4 Dieťa, ktoré získa darcu po otvorení trimestra, sa započíta od ďalšieho [test]
- 6.5 Trimester explicitne uzatvára pracovník ADRA. Otvorený je najviac jeden trimester
  naraz a ďalší sa dá otvoriť až po uzavretí predchádzajúceho [test]. Uzavretím sa nemení
  zoznam detí ani platba škole; škola môže reporty k uzavretému trimestru nahrať aj neskôr
- 6.6 Pracovník ADRA zaznačí platbu darcu po mesiacoch, aj viac mesiacov vopred naraz
- 6.7 Upozornenie pre ADRA, keď platba nie je potvrdená 7 dní po splatnosti podľa
  splátkového kalendára (1.9) — aj keď darca nezaplatil ani prvú platbu [test]
- 6.8 E-mail darcovi o nezaplatenej platbe zo šablóny
- 6.9 Prehľad „koľko treba poslať ktorej škole za tento trimester“
- 6.10 Prehľad pre ADRA: kde darca platí menej, než ADRA posiela škole, a kto mešká
  s platbou — rozdiel je viditeľný len pre ADRA *(invariant 6)*
- 6.11 Vrátenie dieťaťa do ponuky je rozhodnutie ADRA, nie automat; škola to uvidí až
  v ďalšom otvorenom trimestri [test]
- 6.12 Prehľady sú označené ako prevádzkové; pri rozpore vyhráva účtovníctvo ADRA
  *(invariant 9)*

---

# Epik 7 — Formulár pre školy

Najväčší dlhodobý efekt, ale najrizikovejší krok: vyžaduje zmenu správania ľudí v Ugande.

- 7.1 Štruktúrovaný formulár dieťaťa pre školu, použiteľný bez horizontálneho posúvania
  od šírky 360 px aj na počítači
- 7.2 Validácia pri zadaní, aby chýbajúce polia neodhalila až ADRA
- 7.3 Upload fotiek a vysvedčení školou; nahraté reporty čakajú na schválenie ADRA
- 7.4 Systém musí uniesť aj to, že podklad zadá pracovník ADRA namiesto školy
- 7.5 Prehľad pre školu: aktuálni žiaci, história trimestrov (read-only) a aktuálny
  otvorený trimester — ktoré deti majú darcu a koľko za ne škola dostane; bez údajov
  o darcovi a jeho platbách *(invariant 5)* [test]
- 7.6 Kópia formulára pre súrodenca — zmení sa len to, čo sa líši
- 7.7 Pri uzavretí trimestra (6.5) dostane škola e-mail so zoznamom detí, ku ktorým za
  trimester nenahrala vysvedčenie ani fotky (vysvedčenie raz na konci trimestra, fotky
  kedykoľvek) [test]
- 7.8 ADRA môže upraviť názov a popis reportu alebo nahratý súbor nahradiť; pôvodná verzia
  zostáva dohľadateľná. Súčasťou zadania nie je editor PDF ani fotografií v prehliadači.
  ADRA musí report schváliť; darca vidí len schválené reporty [test] *(invariant 11)*

---

# Epik 8 — Darcovský portál

Nie úspora práce, ale retencia darcov — teda stabilita financovania. Darca, ktorý je po
podpise v tme, odíde, a jeho odchod znamená dieťa bez financovania v rozbehnutom roku.

- 8.1 Prístup darcu cez vlastný účet s heslom ku kartám detí, ktoré podporuje. Po
  ukončení sponzorstva darca prístup ku karte dieťaťa stráca; vlastné platby vidí ďalej
  *(predpoklad PO)*
- 8.2 Schválené vysvedčenia, hodnotenia a priebežné fotky po trimestroch
- 8.3 Prehľad vlastných platieb
- 8.4 Upozornenie darcovi, keď pribudne nové vysvedčenie alebo fotky
- 8.5 Keď dieťa odíde z programu alebo dokončí stupeň, darca dostane upozornenie s návrhom
  iných detí z ponuky

---

# Epik 9 — Prevádzka a prevzatie

**Beží priebežne od prvého sprintu, nie na konci.** Priorita je trvácnosť dát, nie vysoká
dostupnosť: keď systém pár hodín nebeží, nestane sa nič, ale ak sa stratí týždeň zadaných
podkladov, ADRA si ich už nemá odkiaľ vziať.

- 9.1 Denné automatické zálohovanie databázy **aj súborov** — fotky, vysvedčenia a PDF
  zmlúv sú rovnako dôležité ako záznamy
- 9.2 Aspoň raz vyskúšaná obnova na čistom stroji, s napísaným postupom. Neodskúšaná záloha
  je presvedčenie, nie záloha.
- 9.3 Kópia zálohy mimo hostingu, na účte vo vlastníctve ADRA · `⨯ blokuje F4`
- 9.4 Dokumentácia pre ADRA a zaškolenie ľudí, ktorí systém budú používať (aspoň jeden
  admin a jeden pracovník); systém prevádzkuje po odovzdaní ADRA sama
- 9.5 Hosting, domény a úložisko vedené na organizačný účet ADRA

---

## Čo nie je v rozsahu

Pomenované, aby sa to nepýtalo opakovane:

- Vlastný verejný web (O1)
- Účtovníctvo, vydávanie účtovných dokladov, bankové integrácie, párovanie platieb,
  spracovanie platieb kartou (O2)
- Potvrdenia o dare na daňové účely
- Evidencia a kontrola súhlasov opatrovníka — je to vec ADRA
- Automatické mazanie alebo anonymizácia údajov
- Dvojsmerná synchronizácia s WordPressom
- Prístup opatrovníka do systému — opatrovník nebude používateľom nikdy
- Dobeh historických sponzorstiev — systém začne od nového trimestra
- Mobilná aplikácia

# HELPKIDS — popis problému a hrubý doménový návrh

Pracovný dokument. Zdroje: `Formulár dieťaťa.docx` (autoritatívny zdroj pre dátové polia),
`Štruktúra webu.docx` (role, prístupy, prepojenia), verejná stránka programu na adra.sk
(momentálne len prezentačná vrstva pre donora), popis súčasného manuálneho procesu.

---

## 1. O čom program je

ADRA Slovensko spája slovenských donorov s konkrétnymi deťmi v Ugande. Donor pravidelnou
platbou hradí dieťaťu vzdelanie, stravu, prípadne internát v jednej z partnerských škôl.
Deti sú siroty alebo pochádzajú zo sociálne slabých rodín — z utečeneckého tábora Kyaka II
alebo zo slumov na predmestí Kampaly.

Partnerské školy a programy (verejný cenník, mesačne na dieťa):

| Škola | Program | Suma |
|---|---|---|
| Youth Initiative Primary School (tábor Kyaka II) | strava | 12 € |
| Youth Initiative Primary School | školné + strava | 20 € |
| Treasure Junior School (Kampala) | školné + strava | 35 € |
| Treasure Junior School | internát + školné a strava | 60 € |

Voči škole sa počíta **na trimester** (4 mesiace) — to je školský takt programu. Mesačná
suma pre donora je ročná suma (3 × trimester) rozdelená na 12 mesiacov. Zmluva s donorom
je na neurčito s mesačnou výpovednou lehotou; minimálna dĺžka podpory neexistuje.

Podstatné pre návrh: nejde o anonymný fundraising, ale o **dlhodobý vzťah 1:1** medzi
donorom a dieťaťom, ktorý musí byť roky udržiavaný dôkazmi (vysvedčenia, fotky, platby).
Z toho vyplýva väčšina požiadaviek — systém nie je katalóg ponúk, ale evidencia dlhodobých
vzťahov, ktoré treba roky obsluhovať.

---

## 2. Ako to funguje dnes

```
Rodič/opatrovník
    │  prihlási dieťa, ústne / na papieri
    ▼
Škola (Uganda)
    │  zozbiera údaje, napíše neštruktúrovaný dokument, nafotí deti
    │  pošle cez WhatsApp / email, po anglicky, nepravidelne
    ▼
ADRA — pracovník
    │  prečíta, doplní chýbajúce (spätné otázky cez WhatsApp, dni až týždne)
    │  prepíše do excelovských zoznamov detí
    │  preloží a preformuluje príbeh
    │  ručne založí stránku dieťaťa na webe (WordPress)
    ▼
Web — ponuka detí
    │  donor vidí profil, vyplní formulár
    ▼
Email s obsahom formulára
    │  pracovník ADRA ručne vypíše zmluvu ADRA–donor
    │  ručne vypíše zmluvu ADRA–škola, škola ručne zmluvu s rodičom
    │  ručne označí dieťa na webe ako podporené
    ▼
Excel
       platby od donorov, platby školám za trimestre, zoznamy detí,
       vysvedčenia a fotky posielané donorovi ad hoc emailom
```

Tie isté údaje o jednom dieťati sa dnes prepisujú **minimálne štyrikrát**: dokument od
školy → Excel → web → zmluva. Každý prepis je manuálna práca aj miesto na chybu, a každá
neskoršia zmena (dieťa zmení školu, prestúpi na vyšší stupeň, donor prestane platiť) sa
musí vykonať na všetkých miestach nezávisle.

---

## 3. Čo je na tom rozbité

**P1 — Neštruktúrovaný vstup.** Škola posiela voľný text. Nedá sa validovať pri zadaní,
takže chýbajúce polia sa objavia až v ADRA, a doplnenie znamená ďalší kolotoč cez WhatsApp.
Kvalita podkladov závisí od toho, kto ich na škole práve písal.

**P2 — Neexistuje zdroj pravdy.** Excel, web a podpísané zmluvy sú tri nezávislé kópie
tých istých dát. Keď sa rozchádzajú, nie je definované, ktorá vyhrá.

**P3 — Proces nie je nikde viditeľný.** Na otázku „v akom stave je dieťa UGA 127 a kto
čaká na koho?“ neexistuje odpoveď inak než z pamäte konkrétneho človeka. Rovnako sa nedá
povedať, koľko detí čaká na podporu a ako dlho.

**P4 — Riziko dvojitého prisľúbenia dieťaťa.** Dieťa je na webe verejne dostupné; ak sa
ozvú dvaja donori, dnes to rieši len to, kto skôr čítal email. Neexistuje rezervácia.

**P5 — Zmluvy sa píšu ručne.** Tri typy (ADRA–donor, ADRA–škola, škola–rodič), všetky
z údajov, ktoré systém už má. Čistá prepisovacia práca s priestorom na chybu v sume,
v dátume začiatku podpory či v mene dieťaťa.

**P6 — Financie v Exceli.** Dva toky — príjmy od donorov a platby školám za trimestre — sa
párujú ručne. Nedá sa rýchlo odpovedať „platí donor X?“, „koľko dlžíme škole za tento
trimester?“, „ktoré deti sú pokryté zmluvou, ale nezaplatené?“.

**P7 — Osobné údaje detí v neriadených kanáloch.** Ide o mimoriadne citlivú kategóriu:
deti, siroty, utečenci, sociálna situácia rodiny, fotografie. Dnes putujú cez WhatsApp a
osobné mailboxy.

**P8 — Donor je po podpise v tme.** Vysvedčenia a fotky chodia ad hoc, ak na ne niekto
myslí. Pri podpore, ktorá má trvať roky, je to priamy dôvod na odchod donora — a odchod
donora znamená dieťa bez financovania v rozbehnutom školskom roku.

**P9 — Práca rastie lineárne s počtom detí.** Model funguje pri desiatkach detí a dvoch
školách. Akékoľvek rozšírenie programu naráža priamo na kapacitu jedného človeka v ADRA.

---

## 4. Cieľový stav v jednej vete

Jedna štruktúrovaná databáza, do ktorej škola zadáva podklady sama, ADRA ich schvaľuje a
edituje (neprepisuje), a z ktorej sa **generuje** všetko ostatné: profil dieťaťa na
zverejnenie, všetky tri zmluvy, trimestrálne prevádzkové prehľady a donorský pohľad
na dieťa.

Kľúčový princíp z `Štruktúra webu.docx`, ktorý treba zachovať: **škola nikdy nepíše priamo
do produkčných dát.** Medzi podkladom od školy a databázou je vždy schvaľovací krok ADRA,
ktorý je nielen kontrolou, ale aj editorskou prácou — preformulovanie príbehu, úprava fotiek,
kontrola vysvedčení, redakcia toho, čo sa smie zverejniť.

Verejnú prezentáciu systém nepreberá — zostáva na existujúcom WordPresse (viď R1 v časti 11).

```
Škola ──štruktúrovaný formulár──┐
                                ├──▶ PODKLAD ──schválenie + redakcia ADRA──▶ ZÁZNAM DIEŤAŤA
Import z existujúcich Excelov ──┘                                                 │
                                                                                  │
            ┌────────────────────┬──────────────────────┬──────────────────────────┴──┐
            ▼                    ▼                      ▼                             ▼
   EXPORT PROFILU           ZMLUVY (3×)        PREVÁDZKOVÉ PREHĽADY             DONORSKÝ
   pre WordPress            zo šablón          podľa trimestra                   POHĽAD
            │
            └──▶ WordPress zobrazí profil a odkliká donora späť do systému (rezervácia)
```

---

## 5. Aktéri

| Aktér | Čo robí | Čo vidí |
|---|---|---|
| **Opatrovník** (rodič, príbuzný, ústav) | prihlási dieťa, podpíše zmluvu so školou | nič v systéme — vstupuje cez školu |
| **Škola** | zadáva podklady o deťoch, nahráva fotky a vysvedčenia po trimestroch | svojich aktuálnych žiakov, históriu trimestrov (read-only) a aktuálny otvorený trimester: ktoré deti majú donora a koľko za ne dostane — **bez** údajov o donorovi a jeho platbách |
| **ADRA — pracovník** | pozýva školy, spravuje ich bankové spojenie, schvaľuje a edituje podklady a reporty (príbehy, fotky, vysvedčenia), exportuje profily, generuje zmluvy, schvaľuje donora po obdržaní zmluvy, otvára trimestre, eviduje platby, komunikuje s donorom | všetko |
| **ADRA — admin** | všetko, čo pracovník, a navyše spravuje používateľské účty | všetko |
| **Donor** | vyplní sponzorský formulár, podpíše zmluvu, platí | svoje deti: údaje, príbeh, fotky, vysvedčenia, vlastné platby |

Nie každý aktér je používateľ systému. Opatrovník ním nebude nikdy. Pri školách
nepredpokladáme obmedzenia konektivity ani zariadení — bežný je mobil aj počítač.

---

## 6. Doménové entity

Zoradené podľa toho, ako dôležité sú pre pochopenie, nie podľa implementácie.

**Dieťa** — jadro celej domény. Nesie osobné údaje, rodinnú a sociálnu situáciu, podmienky
a prostredie bývania, pôvod (miestny / utečenec + krajina), príbeh, potrebný typ podpory,
fotografie a stav v procese. Rozsah polí definuje `Formulár dieťaťa.docx` a je
výrazne širší než to, čo sa zverejňuje na webe — väčšina slúži na posúdenie oprávnenosti,
nie na prezentáciu.

**Podklad zo školy** — samostatná entita, nie stav dieťaťa. Surový záznam od školy, ktorý
má vlastný životný cyklus (odoslaný → vrátený na doplnenie → schválený) a po schválení sa
z neho stane alebo sa doňho zapíše záznam dieťaťa. Oddelenie je podstatné: vďaka nemu môže
škola zadávať bez rizika a ADRA má auditovateľné „čo prišlo vs. čo sme z toho urobili“.

**Verejný profil** — redigovaná verzia dieťaťa určená na zverejnenie: príbeh
pre web, vybrané fotky, zobrazená mesačná suma. Nie stránka, ktorú by prevádzkoval tento
systém, ale **export do WordPressu** (viď R1). Verejný web nikdy nečíta interný záznam a
export neobsahuje presnú adresu ani plné meno opatrovníka.

Dôsledok, s ktorým treba vedome pracovať: exportom vzniká kópia dát mimo systému, teda
presne to, čo popisuje P2. Aby to nebolelo, musí export byť **opakovateľný** — pri zmene sa
profil vygeneruje znovu a prepíše — a **stav dostupnosti dieťaťa nesmie žiť vo WordPresse.**
Tam patrí len text, fotky a odkaz; či dieťa ešte hľadá podporu, rozhoduje systém v momente,
keď donor na odkaz klikne.

**Opatrovník** — vzťah k dieťaťu, podpisuje zmluvu so školou.

**Súrodenci** — len prepojenie detí, nie spoločný profil rodiny. Každé dieťa má vlastný
formulár a vlastné údaje o domácnosti; formulár sa dá skopírovať pre súrodenca a upraviť
len to, čo sa líši. Ponúka sa vždy jednotlivé dieťa; pri dieťati je vidieť jeho súrodencov
a donor ich môže jedným krokom rezervovať všetkých voľných — vznikne ale samostatná
rezervácia, sponzorstvo a zmluva pre každé dieťa.

**Škola** — názov, adresa, príbeh a fotky (má vlastnú prezentáciu na webe), kontaktná
osoba, bankové spojenie, zmluva s ADRA, ponúkané programy. Školu do systému **pozýva
ADRA**; verejná registrácia škôl neexistuje. Bankové spojenie mení **len ADRA**: škola
o zmenu požiada iným kanálom mimo systému, ADRA ju v systéme zapíše a doloží dodatkom
k zmluve; zmena sa zapíše do histórie.

Škola má **aktuálnych žiakov** a **históriu trimestrov** — v každom trimestri deti, za
ktoré bola alebo nebola zaplatená. Keď dieťa prestúpi do inej školy, systém to zaznamená:
dieťa (kód, príbeh, sponzorstvo) zostáva jedno, v novej škole je aktuálnym žiakom a
v histórii starej školy naň zostáva odkaz, len už u nej nie je.

**Program podpory** — kombinácia školy a rozsahu (len strava / školné / školné + strava /
+ internát) s cenou za trimester, ktorú ADRA platí škole. Cenník mení ADRA; zmena platí
pre nové sponzorstvá.

**Trimester** — os, na ktorú sa viažu platby školám, vysvedčenia a prehľady pre školu.
Nemá kalendárne dátumy: trimester **explicitne otvára pracovník ADRA** a označí ho
unikátnym `ROK/mesiac` (napr. `2026/09`) a rovnako explicitne ho aj **uzatvára**; otvorený
je najviac jeden naraz. Pri uzavretí systém upozorní školy na chýbajúce vysvedčenia a fotky.
Otvorením systém pre každú školu zmrazí zoznam
jej žiakov, ktorí majú v tom momente **aktívne sponzorstvo** (schválenú zmluvu) —
rezervácia ani nahratá zmluva nestačí. ADRA tým potvrdzuje, že za ne škole zaplatí. Zoznam sa dá po
otvorení opraviť, oprava sa zapíše do histórie.

**Donor** — kontaktné a fakturačné údaje, komunikačné preferencie. Má vlastný účet
s heslom; účet sa založí pri sponzorskom formulári a sprístupní deti po tom, čo ADRA
schváli zmluvu.

**Rezervácia** (záujem o dieťa) — vzniká vyplnením sponzorského formulára, ktorý už beží
v systéme (donor sa doňho dostane odkazom z WordPressu), a dieťa blokuje **7 kalendárnych
dní**. Zmluvu ADRA–donor systém vygeneruje okamžite pri vzniku rezervácie, bez zásahu
pracovníka ADRA, aby celá lehota patrila donorovi. Keď donor v lehote nahrá podpísanú zmluvu, lehota sa zastaví a zrušiť rezerváciu
môže už len ADRA alebo donor zrušením zmluvy. Ak ADRA nahratú zmluvu neposúdi do 3 dní,
systém ju upozorní; dieťa sa automaticky neuvoľní. Ak ADRA nahratú zmluvu odmietne, dieťa sa
uvoľní. Po expirácii aj po odmietnutí sa dieťa vracia do ponuky a donor dostane e-mail. Toto je priama odpoveď na P4.

**Sponzorstvo** — centrálna entita systému: vzťah donor ↔ dieťa, striktne 1:1 (donor môže
mať viac detí, dieťa najviac jedného donora). Nesie mesačnú sumu donora, splátkový
kalendár a stav. Je na neurčito s mesačnou výpovednou lehotou. Pri prestupe dieťaťa do
inej školy pokračuje.

**Splátkový kalendár** — rozpis očakávaných platieb donora podľa zvolenej periodicity
(mesačne / štvrťročne / polročne / ročne), počítaný **od schválenia zmluvy**. Mení sa
dodatkom (zmena sumy alebo periodicity).

**Zmluva** — dokument vygenerovaný zo šablóny, s vlastným stavom a uloženým PDF. Tri typy:
ADRA–donor, ADRA–škola, škola–opatrovník. Zmluvy podporujú **dodatky** (zmena sumy donora,
zmena bankového spojenia školy). Jazyk je vecou šablóny.

**Potvrdenie platby od donora** a **platba škole** — dva úplne oddelené toky; ADRA stojí
medzi nimi a nesie riziko rozdielu. Systém nie je účtovníctvo (viď R2):
- Platby donora eviduje pracovník ADRA **po mesiacoch** (aj viac mesiacov vopred naraz).
  Očakávané platby vychádzajú zo splátkového kalendára; 7 dní po splatnosti bez
  potvrdenia systém ADRA upozorní a ponúkne e-mail donorovi zo šablóny. Upozornenie teda
  príde aj vtedy, keď donor nezaplatí ani prvú platbu.
- Platby školám idú podľa zoznamu otvoreného trimestra. Škola nikdy nevidí, či donor
  platí — vidí len, či dieťa má na aktuálny trimester donora.

**Dve ceny pri dieťati** — cena programu za trimester (čo ADRA platí škole a čo sa
zobrazuje v ponuke) a mesačná suma donora zo zmluvy. **Nemusia si zodpovedať**: mesačná
suma sa mení len dodatkom, keď sa tak ADRA rozhodne, a kde donor platí menej, ADRA
dopláca. Systém rozdiel ukazuje ADRA, nepovažuje ho za chybu.

**Report o dieťati** — vysvedčenie, hodnotenie, priebežné fotky za trimester; to, čo
udržiava donora v programe. Nahráva ho škola, ADRA ho môže upraviť a **musí ho schváliť**,
až potom ho vidí donor.

---

## 7. Životné cykly

**Podklad zo školy**

```
odoslaný ──▶ vo spracovaní ADRA ──▶ schválený (vznikne / aktualizuje sa záznam dieťaťa)
   ▲                 │
   └── vrátený na ◀──┘
       doplnenie
```

**Dieťa**

```
schválené (v internej databáze)
   └─▶ zverejnené — hľadá podporu
          └─▶ rezervované (donor vyplnil formulár)
                 └─▶ podporované
                        └─▶ ukončené (dokončilo stupeň / odišlo)
```

Návratová hrana **podporované → hľadá podporu** nastane, len keď o tom rozhodne ADRA
(napr. donor prestal platiť). Škola sa to dozvie až pri otvorení ďalšieho trimestra; už
otvorený trimester zostáva pre ňu zaplatený a rozdiel rieši ADRA.

Keď dieťa z programu odíde alebo dokončí stupeň, systém upozorní donora a navrhne mu iné
deti z ponuky.

**Prestup do inej školy:** systém prestup zaznamená; dieťa zostáva jedno s rovnakým kódom
a sponzorstvom, história starej školy naň ďalej odkazuje (viď Škola). ADRA sa rozhodne, či
donorovi ponechá pôvodnú sumu, alebo mu navrhne dodatok.

**Sponzorstvo**

```
rezervácia → zmluva vygenerovaná → podpísaná a nahratá → schválená ADRA → aktívne
                                                                            ├─▶ zmenené dodatkom
                                                                            └─▶ ukončené
```

---

## 8. Pravidlá, ktoré má systém držať

Sú to tie miesta, kde dnes chyba vzniká najčastejšie:

1. Súhlasy opatrovníka systém **neeviduje ani nekontroluje**. Sú súčasťou zmluvy
   škola–opatrovník a zodpovednosť za ne, vrátane odvolania, nesie výhradne ADRA.
2. Dieťa môže mať v danom momente najviac jednu aktívnu rezerváciu.
3. Zmluva sa generuje výhradne zo schválených dát, nikdy zo surového podkladu školy.
4. Suma donora v zmluve sa nemení zmenou cenníka — len dodatkom k zmluve.
5. Škola vidí len minulé trimestre (read-only) a aktuálny otvorený trimester: ktoré deti
   majú donora a koľko za ne dostane. Nevidí identitu donora ani to, či platí.
6. Otvorený trimester je pre školu zaplatený za všetky deti v jeho zozname, aj keď donor
   medzitým prestane platiť. Rozdiel vidí len ADRA. Dieťa, ktoré získa donora po otvorení,
   sa započíta od ďalšieho trimestra.
7. Export pre WordPress nikdy neobsahuje presnú adresu dieťaťa ani plné meno opatrovníka.
8. Stav dostupnosti dieťaťa (hľadá podporu / rezervované / podporované) žije **výhradne
   v systéme**. WordPress ho nedrží ani nemení; rezerváciu potvrdzuje systém.
9. Systém nevydáva účtovné doklady a jeho finančné prehľady sú prevádzkové. Pri rozpore
   vyhráva účtovníctvo ADRA.
10. Bankové spojenie školy mení len ADRA, škola nie. Zmena sa zapíše do histórie (kto,
    kedy, z čoho na čo). Platby posiela ADRA ručne mimo systému.
11. Report o dieťati (vysvedčenie, fotky) vidí donor až po schválení ADRA.

---

## 9. Bezpečnosť a spoľahlivosť

Toto nie sú „technické detaily na neskôr“ — menia, ako sa systém navrhne.

### 9.1 Čo chránime

**Bankové spojenie školy** mení len ADRA na žiadosť školy doručenú mimo systému a zmena
je doložená dodatkom k zmluve. Systém peniaze neposiela — platbu robí pracovník ADRA ručne
vo svojej banke. Systému stačí zmenu zapísať do histórie; história citlivých polí je
**append-only**.

Hlavná kategória sú osobné údaje detí: príbehy, sociálna situácia, fotografie. Tu je
najlepšou ochranou to, čo systém vôbec nemá — a z rozhodnutia R2 vyplýva príjemná vec:
**systém nikdy nedrží platobné údaje donorov** (čísla kariet, prístup k účtom), lebo platby
prechádzajú mimo neho. To odrezáva celú jednu kategóriu rizika.

### 9.2 Ako držať útočnú plochu malú

- **WordPress nesmie mať prístup k databáze systému.** WordPress je najčastejšie napádaná
  vec v celej zostave a raz kompromitovaný bude. Keďže export podľa R1 je jednosmerný,
  napadnutý WordPress neotvára cestu do systému — to je dôvod navyše držať sa tohto modelu
  a neprepájať ich obojsmerne.
- Verejne dostupný je zo systému len **rezervačný formulár**. Musí byť limitovaný na počet
  pokusov a nesmie prezradiť nič nad rámec toho, čo už je na verejnom profile.
- Fotky detí a vysvedčenia **nesmú byť dostupné na uhádnuteľnej adrese** (žiadne
  `.../fotky/127.jpg`). Toto je najčastejší reálny spôsob, akým takéto dáta unikajú — bez
  akéhokoľvek „hacku“.
- Prílohy od škôl (fotky, PDF vysvedčení) sú klasický vstup pre útok: validovať typ, nikdy
  neukladať do priestoru, odkiaľ sa dá súbor spustiť.
- Prístupy podľa role, ktoré už časť 5 definuje, musia byť vynútené na serveri, nie len
  skryté v UI. Škola vidí svoje deti, donor svoje deti, nič viac.
- Prístup ADRA (admin aj pracovník) s dvojfaktorovým overením.
- **Žiadne produkčné dáta v testovacom prostredí** a žiadne exporty do osobných zariadení
  či WhatsAppu — dnešný kanál je zároveň dnešný únik.

Prístup donora „cez heslo“ zo `Štruktúra webu.docx` je riešený vlastným účtom donora
s heslom, nie zdieľaným heslom na profil.

### 9.3 Spoľahlivosť: dáta sa nesmú stratiť

Užitočný rámec pre tento program: **program beží v trimestroch, nie v sekundách.** Keď
systém pár hodín nebeží, nestane sa nič — obeh detí, zmlúv a platieb je pomalý. Ak sa ale
stratí týždeň zadaných podkladov, ADRA si ich už nemá odkiaľ vziať, lebo pôvodné správy sú
v chaotickom WhatsApp vlákne. **Priorita je teda trvácnosť dát, nie vysoká dostupnosť** — čo
je dobrá správa, pretože trvácnosť je výrazne lacnejšia.

Z toho konkrétne:

- **Hotové zálohovanie od poskytovateľa databázy** je postačujúce a žiaduce — nemá zmysel
  písať vlastné skripty. Stačí denná automatická záloha (strata jedného dňa je
  akceptovateľná) a obnova na niekoľko kliknutí, nie ručný postup.
- **Záloha zahŕňa aj súbory, nie len databázu.** Fotky, vysvedčenia a PDF zmlúv sú rovnako
  dôležité ako záznamy. Samotný dump databázy by po obnove ukazoval na neexistujúce
  fotografie — a PDF zmlúv sú právne dokumenty.
- **Záloha musí byť aspoň raz vyskúšaná obnovením.** Neodskúšaná záloha je presvedčenie,
  nie záloha.
- **Kópia zálohy mimo hostingu, vo vlastníctve ADRA.** Ak sa stratí hosting kvôli zrušenému
  účtu, nezaplatenej faktúre alebo zaniknutému dodávateľovi, zmiznú s ním aj zálohy, ktoré
  ležia v tom istom účte. Pre malú organizáciu bez vlastného IT je toto pravdepodobnejší
  scenár než útok.

### 9.4 Prenositeľnosť: strata hostingu nesmie byť koniec

Požiadavka „ľahko premigrovať na nový hosting bez straty stavu“ sa dá naplniť len tak, že sa
dopredu odmietne uzamknutie na dodávateľa **v dátovej vrstve**:

- Bežná, všade hostovateľná databáza (napr. PostgreSQL) namiesto proprietárneho úložiska,
  ktoré existuje len u jedného poskytovateľa.
- Aplikácia zabalená tak, aby sa dala spustiť inde bez prepisovania (kontajner, konfigurácia
  cez premenné prostredia, žiadne údaje napevno v kóde).
- Súbory v štandardnom objektovom úložisku, prenositeľné skopírovaním.
- Celý stav systému musí byť obsiahnutý v **databáze + súboroch**. Nič podstatné nesmie žiť
  len v nastaveniach hostingu alebo v pluginoch WordPressu.
- Napísaný a raz vyskúšaný postup obnovy na čistom stroji. To je zároveň test prenositeľnosti
  a test zálohy v jednom.

---

## 10. Kde je najväčší efekt automatizácie

Poradie je odhad podľa „ušetrená manuálna práca a odstránené riziko / náročnosť a závislosť
od tretej strany“:

1. **Generovanie zmlúv zo šablón** — plne v rukách ADRA, okamžitá úspora, žiadna zmena
   správania škôl ani donorov.
2. **Jediná databáza detí + schvaľovacia obrazovka pre ADRA** — ruší prepis do Excelu a
   vytvára zdroj pravdy. Excel zostáva ako export, nie ako databáza.
3. **Export profilu do WordPressu + rezervácia v systéme** — vlastný verejný web netreba,
   existujúci WordPress funguje dobre a zostáva. Stačí vygenerovať profil dieťaťa
   (Markdown/HTML + fotky) na vloženie a v ňom odkaz, ktorý donora privedie do systému.
   Za výrazne menej práce než vlastný web tým padá ručné skladanie stránok aj dvojité
   prisľúbenie dieťaťa.
4. **Import z existujúcich Excelov** — nielen jednorazová migrácia, ale aj priebežný vstupný
   kanál (formát aktuálnych tabuliek bude dodaný neskôr). Nepotrebuje vlastnú logiku: import
   je len ďalší zdroj **podkladov** a môže ísť do tej istej schvaľovacej fronty ako formulár
   školy. Zároveň je to náhradný vstup, kým školy formulár nepoužívajú.
5. **Štruktúrovaný formulár pre školy** — najväčší dlhodobý efekt, ale najrizikovejší krok:
   vyžaduje zmenu správania ľudí v Ugande. Systém musí uniesť aj to, že podklad doňho zadá
   pracovník ADRA namiesto školy.
6. **Donorský portál** (vysvedčenia, fotky, platby) — nie úspora práce, ale retencia
   donorov, teda stabilita financovania.
7. **Trimestrálne prevádzkové prehľady** — nad potvrdeniami platieb, ktoré zadáva pracovník
   ADRA: kto nezaplatil, koľko treba poslať ktorej škole. Nie účtovníctvo.

Body 1–4 sa dajú urobiť bez toho, aby sa čokoľvek zmenilo na strane škôl, donorov alebo
webu — a už tie odstraňujú väčšinu prepisovania. To je prirodzená prvá fáza.

---

## 11. Zafixované rozhodnutia

**R1 — Verejný web zostáva na WordPresse; systém preň len exportuje profily.**
Existujúci WordPress funguje dobre a nie je dôvod ho nahrádzať. Systém teda negeneruje
verejný web, ale export profilu dieťaťa (Markdown/HTML + fotky) na vloženie do WordPressu,
a ten odkazuje späť do systému na rezerváciu dieťaťa. Vlastný verejný web je nice-to-have,
nie súčasť zadania.
*Dôsledky:* export musí byť opakovateľný; stav dostupnosti dieťaťa zostáva v systéme
(invarianty 7–8); odkaz z WordPressu musí nesť identifikátor dieťaťa, aby rezervačný
formulár vedel, o koho ide.

**R2 — Zdrojom pravdy o peniazoch zostáva účtovníctvo ADRA.**
Systém platby neúčtuje. Pracovník ADRA v admin rozhraní len zaznačí, že platba donora za
daný mesiac (alebo viac mesiacov) prišla.
*Dôsledky:* žiadna banková integrácia ani automatické párovanie; systém drží len stav
„zaplatené / nezaplatené“ na sponzorstvo a mesiac, z ktorého stavia prevádzkové prehľady;
tieto prehľady nie sú účtovný výstup (invariant 9). Potvrdenia o dare na daňové účely sú
mimo systému.

**R3 — Import z existujúcich Excelov je súčasť zadania.**
Nie len jednorazová migrácia, ale aj priebežný vstupný kanál. Detaily aktuálneho formátu
budú dodané neskôr.
*Dôsledky:* import ústi do tej istej fronty podkladov ako formulár školy, teda prechádza
rovnakým schvaľovaním; musí byť tolerantný k nekonzistentným dátam a umožniť mapovanie
stĺpcov, keď sa formát tabuliek zmení.

**R4 — Jazyk.** Systém je pripravený na viac jazykov; prvá verzia je len v angličtine,
slovenčina sa doplní neskôr. Príbeh pre WordPress prekladá pracovník ADRA. Jazyk zmlúv
určuje šablóna.

**R5 — Osobné údaje.** Prevádzkovateľom osobných údajov je ADRA. Systém nič automaticky
nemaže ani neanonymizuje. Súhlasy opatrovníka systém nerieši (invariant 1).

**R6 — Štart.** Systém začína od nového trimestra; read-only import historických dát je
nice-to-have. Reálne dáta sa do systému vložia až pri odovzdaní.

---

## 12. Otvorené otázky

- Kde bude uložená kópia zálohy mimo hostingu a na koho účet v ADRA je vedená?
- Šablóny troch zmlúv a vzorky Excelov — ADRA ich dodá.
- Cenník za trimester — zadá ADRA v systéme, nie je blokujúci.

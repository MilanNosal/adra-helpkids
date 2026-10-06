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

Jedna štruktúrovaná databáza, ktorá nahradí excelovskú tabuľku „TABUĽKA management
HELPKIDS“. Najprv ju vedie pracovník ADRA ručne, postupne doňho zadávajú školy a darcovia
sami. Z nej sa potom odvodí všetko ostatné: ponuka voľných detí, rezervácie, darcovský
pohľad, trimestre a vyúčtovanie pre školy, evidencia podpísaných zmlúv a nakoniec aj
generovanie zmlúv.

Kľúčový princíp z `Štruktúra webu.docx`, ktorý treba zachovať: **škola nikdy nepíše priamo
do schválených dát.** Dieťa, ktoré pridá škola, je viditeľné až po schválení ADRA, a
schválenie nie je len kontrola, ale aj redakčná práca (preformulovanie príbehu, kontrola
údajov). Rovnako report o dieťati vidí darca až po schválení ADRA.

Verejnú prezentáciu systém nepreberá — zostáva na existujúcom WordPresse (viď R1 v časti 11).

```
Pracovník ADRA ──ručne──────────────────────────┐
Import z Excelov ──vytvorí tie isté záznamy─────┤
Škola ──pridá dieťa──▶ schválenie ADRA ─────────┴──▶ DATABÁZA (školy, deti, darcovia,
                                                     sponzorstvá, platby)
                                                              │
     ┌──────────────────┬──────────────────┬─────────────────┼──────────────────┐
     ▼                  ▼                  ▼                 ▼                  ▼
  PONUKA A          DARCOVSKÝ         TRIMESTRE A       PODPÍSANÉ          EXPORT PROFILU
  REZERVÁCIA        POHĽAD            VYÚČTOVANIE       ZMLUVY →           pre WordPress
                                      PRE ŠKOLU         neskôr generovanie
```

---

## 5. Aktéri

| Aktér | Čo robí | Čo vidí |
|---|---|---|
| **Opatrovník** (rodič, príbuzný, ústav) | prihlási dieťa, podpíše zmluvu so školou | nič v systéme — vstupuje cez školu |
| **Škola** | zaregistruje sa (ADRA ju potvrdí), pridáva deti, nahráva reporty a podpísané zmluvy s opatrovníkmi | svoje deti a stav ich schválenia, svoj aktuálny trimester s vyúčtovaním a minulé trimestre, svoje zmluvy s ADRA — **bez** údajov o darcoch a ich platbách |
| **ADRA — pracovník** | zakladá školy, deti, darcov a sponzorstvá, pozýva ich do systému, potvrdzuje školy, schvaľuje deti a reporty, potvrdzuje rezervácie, zaznačuje platby, vedie trimestre, nahráva zmluvy, exportuje profily | všetko |
| **ADRA — admin** | všetko, čo pracovník, a navyše spravuje účty ADRA a pregeneruje heslo aj aktivovanému účtu | všetko |
| **Darca** | zaregistruje sa, rezervuje deti, zvolí splátkový kalendár, platí, môže dať výpoveď | ponuku voľných detí, svoje sponzorované deti, ich reporty z obdobia svojho sponzorstva, vlastné platby a zmluvy |

Nie každý aktér je používateľ systému. Opatrovník ním nebude nikdy. Pri školách
nepredpokladáme obmedzenia konektivity ani zariadení — bežný je mobil aj počítač.

**Účty.** Školu aj darcu môže vytvoriť pracovník ADRA (nielen admin). Taký účet má náhodné
heslo, ktoré nikto nevidí, a je **neaktivovaný** — existuje len ako záznam. Keď sa
pracovník rozhodne používateľa pozvať, systém vygeneruje nové heslo a pošle ho e-mailom;
heslo nevidí pracovník ani admin. Prvým prihlásením sa účet **aktivuje** a odvtedy heslo
pregeneruje už len admin. Aktivovaný používateľ si vie heslo obnoviť sám.

Okrem toho existuje **verejná registrácia** chránená captchou: škola sa zaregistruje a
pridávať deti môže až po potvrdení pracovníkom ADRA; darca sa zaregistruje bez potvrdenia.

---

## 6. Doménové entity

Zoradené podľa toho, ako dôležité sú pre pochopenie, nie podľa implementácie.

**Dieťa** — jadro celej domény. Nesie osobné údaje, rodinnú a sociálnu situáciu, podmienky
a prostredie bývania, pôvod (miestny / utečenec + krajina), príbeh, opatrovníka, potrebný
typ podpory, fotografie a stav. Rozsah polí definuje `Formulár dieťaťa.docx` a je výrazne
širší než to, čo sa zverejňuje — väčšina slúži na posúdenie oprávnenosti, nie na
prezentáciu. Kód dieťaťa (napr. `UGA01`) prideľuje systém a je nemenný.

Dieťa má **históriu škôl** (ktorú školu navštevovalo v akom období) a **históriu podpory**
(kto ho kedy a za koľko podporoval). Obe sa dajú zadať aj spätne ako historické záznamy.

**Dieťa navrhnuté školou** — keď dieťa pridá škola, čaká na schválenie ADRA a dovtedy ho
nevidí nikto okrem školy a ADRA. Pracovník ADRA ho môže upraviť, schváliť alebo vrátiť
škole s poznámkou, čo chýba. Schválený záznam škola priamo nemení.

**Verejný profil** — redigovaná verzia dieťaťa určená na zverejnenie: príbeh, fotky
označené na zverejnenie, mesačná suma. Nie stránka, ktorú by prevádzkoval tento systém,
ale **export do WordPressu** (viď R1) s odkazom na rezerváciu v systéme. Export
neobsahuje presnú adresu ani meno opatrovníka.

Dôsledok, s ktorým treba vedome pracovať: exportom vzniká kópia dát mimo systému, teda
presne to, čo popisuje P2. Aby to nebolelo, musí export byť **opakovateľný** a **stav
dostupnosti dieťaťa nesmie žiť vo WordPresse.** Či dieťa ešte hľadá podporu, rozhoduje
systém. Darca vidí ponuku voľných detí aj priamo v systéme.

**ADRA** — vlastné údaje, ktoré vstupujú do zmlúv: názov, IČO, štatutárny zástupca,
sídlo, korešpondenčná adresa, IBAN, kontakt. Potrebné až pri generovaní zmlúv.

**Opatrovník** — vzťah k dieťaťu, podpisuje zmluvu so školou.

**Súrodenci** — len prepojenie detí, nie spoločný profil rodiny. Každé dieťa má vlastné
údaje; pri dieťati je vidieť jeho súrodencov.

**Škola** — názov, sídlo a korešpondenčná adresa, popis, kontaktná osoba, bankové
spojenie, programy s cenami, zmluvy s ADRA. Vzniká registráciou s potvrdením ADRA alebo
ju založí pracovník ADRA. Bankové spojenie mení **len ADRA**: škola o zmenu požiada mimo
systému; každá zmena sa zapíše do histórie, ktorá sa nedá prepísať.

Keď dieťa prestúpi do inej školy, systém to zaznamená: dieťa (kód, príbeh, sponzorstvo)
zostáva jedno, v novej škole je aktuálnym žiakom a v histórii starej školy naň zostáva
odkaz.

**Program podpory** — kombinácia školy a rozsahu (strava / školné + strava / internát…)
s cenou. Ceny sa vedú **historicky s obdobím platnosti**: vždy je jasná aktuálna cena aj
to, aká platila kedykoľvek v minulosti. Cenník mení ADRA; zmena nemení sumu existujúcich
sponzorstiev.

**Darca** — kontaktné a fakturačné údaje, adresa trvalého pobytu (u firmy sídlo)
a korešpondenčná adresa. Má účet (viď časť 5): neaktivovaný, ak ho založila ADRA a ešte ho
nepozvala, alebo aktívny po registrácii či prvom prihlásení.

**Sponzorstvo** — centrálna entita systému: darca podporuje **jedno alebo viac detí**
s mesačnou sumou, obdobím a číslom zmluvy. Darca môže mať viac sponzorstiev; dieťa má
v danom čase **najviac jedného darcu**. Vzniká ručne pracovníkom ADRA alebo potvrdením
rezervácie. Je na neurčito; darca ho môže ukončiť výpoveďou s lehotou jeden mesiac odo dňa
výpovede, alebo ju
zadá ADRA za neho. Po skončení sa dieťa **automaticky vráti do ponuky**. Pri prestupe
dieťaťa do inej školy sponzorstvo pokračuje.

**Rezervácia** — darca si v systéme rezervuje jedno alebo viac voľných detí a zvolí si
splátkový kalendár. Dieťa je blokované **7 kalendárnych dní** a má najviac jednu aktívnu
rezerváciu. Rezervácia sama potvrdenie ADRA nepotrebuje, ale **pridelenie dieťaťa áno**:
potvrdením rezervácie pracovníkom ADRA vzniká sponzorstvo. Lehotu zastaví **výhradne
potvrdenie ADRA**; nepotvrdená rezervácia po lehote vyprší a dieťa sa vráti do ponuky. Toto je priama odpoveď na P4.

Postupne sa k rezervácii pridáva zmluva: najprv ju ADRA rieši mimo systému, neskôr darca
nahrá podpísanú zmluvu a ADRA potvrdí až po nej (nahratie lehotu nezastaví), nakoniec systém zmluvu pri rezervácii
vygeneruje sám.

**Splátkový kalendár** — periodicita platieb (mesačne / štvrťročne / polročne / ročne),
ktorú volí darca pri rezervácii (pri ručne založenom sponzorstve ju zadá ADRA), a dátum
prvej platby, ktorý navrhne systém. Z neho systém vie, kedy má darca platiť.

**Potvrdenie platby od darcu** a **platba škole** — dva úplne oddelené toky; ADRA stojí
medzi nimi a nesie riziko rozdielu. Systém nie je účtovníctvo (viď R2):
- Platby darcu potvrdzuje pracovník ADRA vyklikaním, aj za viac období naraz. Systém
  ukazuje, kto podľa splátkového kalendára nezaplatil. Neskôr na to upozorní pracovníka a
  ten jedným klikom pošle upomienku darcovi.
- Platby školám idú podľa zoznamu trimestra školy. Škola nikdy nevidí, či darca platí.

**Trimester** — os, na ktorú sa viažu platby školám a vyúčtovanie pre školu. **Každá škola
má trimestre samostatne**: pracovník ADRA začne trimester pre konkrétnu školu a priradí
doň deti, za ktoré ADRA škole zaplatí. Systém navrhne všetky deti školy, ktoré majú
aktuálne sponzora; ADRA môže dieťa odobrať alebo pridať. Zoznam sa dá opraviť (oprava sa
zapíše do histórie) a trimester sa uzatvára.

Dieťa v trimestri je pre školu zaplatené za celý trimester. Ak dieťa darcu nemá (ADRA ho
pridala bez darcu) alebo ho počas trimestra stratí, platí tie mesiace **ADRA** — v tabuľke
dnes stĺpec „Podpora z réžie ADRA“. Pracovník ADRA vidí, za ktoré deti a mesiace to platí;
škola vidí len, že dieťa je zaplatené.

**Dve ceny pri dieťati** — cena programu (čo ADRA platí škole) a mesačná suma darcu zo
sponzorstva. **Nemusia si zodpovedať**: suma darcu sa zmenou cenníka nemení, a kde darca
platí menej, ADRA dopláca. Systém rozdiel ukazuje ADRA, nepovažuje ho za chybu.

**Zmluva** — najprv len **podpísaný dokument nahratý do systému** a priradený: ADRA–darca
(k sponzorstvám, vidí ju darca aj ADRA), ADRA–škola (vidí ju škola aj ADRA), škola–
opatrovník (k dieťaťu, vidí ju škola aj ADRA). Zmluvy majú **dodatky**. Až neskôr systém
zmluvy a dodatky **generuje** zo šablón. Jazyk je vecou šablóny.

**Report o dieťati** — vysvedčenie, hodnotenie, priebežné fotky; to, čo udržiava darcu
v programe. Nahráva ho škola, ADRA ho môže upraviť a **musí ho schváliť**. Darca vidí len
reporty z obdobia, keď dieťa sponzoroval.

---

## 7. Životné cykly

**Účet školy a darcu**

```
neaktivovaný (založila ADRA) ──pozvanie──▶ pozvaný ──prvé prihlásenie──▶ aktivovaný
verejná registrácia darcu ──overenie e-mailu─────────────────────────▶ aktivovaný
verejná registrácia školy ──potvrdenie ADRA──────────────────────────▶ aktivovaný
```

**Dieťa**

```
navrhnuté školou ──▶ schválené ADRA ──▶ voľné (v ponuke)
   ▲        │        (alebo založené       │
   └ vrátené┘         priamo ADRA)         ▼
     na doplnenie                       rezervované ──vypršanie / zamietnutie──▶ voľné
                                           │
                                           ▼ potvrdenie ADRA
                                        podporované ──koniec sponzorstva──▶ voľné
                                           │
                                           ▼
                                        ukončené (dokončilo stupeň / odišlo z programu)
```

Keď sponzorstvo skončí počas trimestra, dieťa sa vráti do ponuky, ale v trimestri školy
zostáva zaplatené; zvyšné mesiace platí ADRA.

**Prestup do inej školy:** systém prestup zaznamená; dieťa zostáva jedno s rovnakým kódom
a sponzorstvom, história starej školy naň ďalej odkazuje.

**Sponzorstvo**

```
rezervácia ──potvrdenie ADRA──▶ aktívne ──výpoveď (mesiac od výpovede)──▶ ukončené
(alebo založené ručne ADRA)       └─▶ zmenené dodatkom
```

---

## 8. Pravidlá, ktoré má systém držať

1. Súhlasy opatrovníka systém **neeviduje ani nekontroluje**. Sú súčasťou zmluvy
   škola–opatrovník a zodpovednosť za ne nesie výhradne ADRA.
2. Dieťa môže mať v danom momente najviac jednu aktívnu rezerváciu a najviac jedného
   darcu.
3. Dieťa od školy ani report nevidí darca ani verejnosť, kým ich ADRA neschváli.
4. Suma darcu sa nemení zmenou cenníka — len dodatkom k zmluve.
5. Škola vidí svoj aktuálny trimester s vyúčtovaním a minulé trimestre. Nevidí identitu
   darcu ani to, či platí.
6. Dieťa v trimestri je pre školu zaplatené za celý trimester, aj keď darca medzitým
   skončí. Mesiace bez darcu platí ADRA a vidí ich len ADRA.
7. Export pre WordPress nikdy neobsahuje presnú adresu dieťaťa ani meno opatrovníka.
8. Stav dostupnosti dieťaťa (voľné / rezervované / podporované) žije **výhradne
   v systéme**. Dieťa bez darcu sa automaticky vracia do ponuky.
9. Systém nevydáva účtovné doklady a jeho finančné prehľady sú prevádzkové. Pri rozpore
   vyhráva účtovníctvo ADRA.
10. Bankové spojenie školy mení len ADRA, škola nie. Zmena sa zapíše do histórie (kto,
    kedy, z čoho na čo). Platby posiela ADRA ručne mimo systému.
11. Darca vidí reporty dieťaťa len z obdobia, keď ho sponzoroval.
12. Heslo, ktoré vygeneruje systém, nevidí nikto okrem príjemcu e-mailu.

---

## 9. Bezpečnosť a spoľahlivosť

Toto nie sú „technické detaily na neskôr“ — menia, ako sa systém navrhne.

### 9.1 Čo chránime

**Bankové spojenie školy** mení len ADRA na žiadosť školy doručenú mimo systému. Systém
peniaze neposiela — platbu robí pracovník ADRA ručne vo svojej banke. Systému stačí zmenu
zapísať do histórie; história citlivých polí je **append-only**.

Hlavná kategória sú osobné údaje detí: príbehy, sociálna situácia, fotografie. Tu je
najlepšou ochranou to, čo systém vôbec nemá — a z rozhodnutia R2 vyplýva príjemná vec:
**systém nikdy nedrží platobné údaje darcov** (čísla kariet, prístup k účtom), lebo platby
prechádzajú mimo neho. To odrezáva celú jednu kategóriu rizika.

### 9.2 Ako držať útočnú plochu malú

- **WordPress nesmie mať prístup k databáze systému.** WordPress je najčastejšie napádaná
  vec v celej zostave a raz kompromitovaný bude. Keďže export podľa R1 je jednosmerný,
  napadnutý WordPress neotvára cestu do systému.
- Verejne dostupné sú zo systému len **registrácie škôl a darcov**. Sú chránené captchou
  a limitom počtu pokusov a nesmú prezradiť, či e-mail už existuje.
- Fotky detí a vysvedčenia **nesmú byť dostupné na uhádnuteľnej adrese** (žiadne
  `.../fotky/127.jpg`). Toto je najčastejší reálny spôsob, akým takéto dáta unikajú — bez
  akéhokoľvek „hacku“.
- Prílohy od škôl (fotky, PDF vysvedčení a zmlúv) sú klasický vstup pre útok: validovať
  typ, nikdy neukladať do priestoru, odkiaľ sa dá súbor spustiť.
- Prístupy podľa role z časti 5 musia byť vynútené na serveri, nie len skryté v UI. Škola
  vidí svoje deti, darca svoje deti, nič viac.
- Prístup ADRA (admin aj pracovník) s dvojfaktorovým overením — v poradí realizácie až na
  konci.
- **Žiadne produkčné dáta v testovacom prostredí** a žiadne exporty do osobných zariadení
  či WhatsAppu — dnešný kanál je zároveň dnešný únik.

### 9.3 Spoľahlivosť: dáta sa nesmú stratiť

Užitočný rámec pre tento program: **program beží v trimestroch, nie v sekundách.** Keď
systém pár hodín nebeží, nestane sa nič — obeh detí, zmlúv a platieb je pomalý. Ak sa ale
stratí týždeň zadaných údajov, ADRA si ich už nemá odkiaľ vziať. **Priorita je teda
trvácnosť dát, nie vysoká dostupnosť** — čo je dobrá správa, pretože trvácnosť je výrazne
lacnejšia.

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

## 10. Poradie realizácie

Poradie určuje PO (podrobne v `BACKLOG.md`, dôvody v `notes.md`). Princíp: najprv to, čo
nahrádza najviac ručnej práce, a všetko ďalšie sa na to nabaľuje.

1. **Jadro — náhrada tabuľky „TABUĽKA management HELPKIDS“.** Školy s cenami, deti,
   darcovia, sponzorstvá, história, splátkové kalendáre a zaznačovanie platieb. Všetko
   zakladá pracovník ADRA ručne; to na prvý prototyp stačí.
2. **Samoobsluha:** registrácia škôl a darcov, škola pridáva deti so schválením ADRA.
3. **Ponuka a rezervácia:** darca vidí voľné deti, rezervuje ich, ADRA potvrdzuje.
4. **Darcovský portál:** moje deti, reporty od školy, výpoveď sponzorstva.
5. **Fotky a export profilu do WordPressu.**
6. **Trimestre a vyúčtovanie pre školu** — náhrada „List Helpkids support for trimester“,
   upomienky darcom.
7. **Podpísané zmluvy:** darca, potom škola–ADRA, potom škola–opatrovník.
8. **Súrodenci, prestup, odchod z programu.**
9. **Import z Excelov** — automaticky vytvára tie isté záznamy, ktoré vie založiť ADRA.
10. **Generovanie zmlúv a dodatkov, notifikácie.**
11. **2FA.**

Infraštruktúra (nasadenie, zálohy, audit, úložisko súborov) je na začiatku, pred prvými
reálnymi dátami.

---

## 11. Zafixované rozhodnutia

**R1 — Verejný web zostáva na WordPresse; systém preň len exportuje profily.**
Existujúci WordPress funguje dobre a nie je dôvod ho nahrádzať. Systém teda negeneruje
verejný web, ale export profilu dieťaťa (Markdown/HTML + fotky) na vloženie do WordPressu,
a ten odkazuje späť do systému na rezerváciu dieťaťa. Vlastný verejný web je nice-to-have,
nie súčasť zadania.
*Dôsledky:* export musí byť opakovateľný; stav dostupnosti dieťaťa zostáva v systéme
(invariant 8); odkaz z WordPressu musí nesť identifikátor dieťaťa.

**R2 — Zdrojom pravdy o peniazoch zostáva účtovníctvo ADRA.**
Systém platby neúčtuje. Pracovník ADRA len zaznačí, že platba darcu za dané obdobie
prišla.
*Dôsledky:* žiadna banková integrácia ani automatické párovanie; systém drží len stav
„zaplatené / nezaplatené“ podľa splátkového kalendára, z ktorého stavia prevádzkové
prehľady; tie nie sú účtovný výstup (invariant 9). Potvrdenia o dare na daňové účely sú
mimo systému.

**R3 — Import z existujúcich Excelov je súčasť zadania, ale druhoradý.**
Import len automaticky vytvára tie isté záznamy (školy, deti, darcovia, sponzorstvá), ktoré
vie od začiatku ručne založiť pracovník ADRA, a hlási, čo sa nenaimportovalo a prečo. Je
rozdelený po častiach a v poradí je až pred generovaním zmlúv.

**R4 — Jazyk.** Systém je pripravený na viac jazykov; prvá verzia je len v angličtine,
slovenčina sa doplní neskôr. Príbeh pre WordPress prekladá pracovník ADRA. Jazyk zmlúv
určuje šablóna.

**R5 — Osobné údaje.** Prevádzkovateľom osobných údajov je ADRA. Systém nič automaticky
nemaže ani neanonymizuje. Súhlasy opatrovníka systém nerieši (invariant 1).

**R6 — Štart.** Historické podpory a školy dieťaťa sa dajú zadať ako historické záznamy.
Reálne dáta sa do systému vložia až pri odovzdaní.

**R7 — Sponzoruje sa školné, nie podiel na ňom.** Cena za dieťa je v danom čase rovnaká
pre všetky deti v tom istom programe tej istej školy. Spolufinancovanie rodinou (zmienka
„% for family / % for donors“ vo formulári dieťaťa) systém nerieši; vo formulári môže
zostať ako informácia, systém z nej nič nepočíta.

**R8 — Sponzorstvo pokrýva 1…N detí.** Darca môže mať viac sponzorstiev (zmlúv) a jedno
sponzorstvo môže pokrývať viac detí. Dieťa má v danom čase najviac jedného darcu.

**R9 — Trimestre sú per škola.** Každá škola má vlastný trimester, ktorý ADRA začína
a uzatvára samostatne.

---

## 12. Otvorené otázky

- Kde bude uložená kópia zálohy mimo hostingu a na koho účet v ADRA je vedená?
- Šablóny troch zmlúv a vzorky Excelov — ADRA ich dodá.

---

## 13. Pravidlá pre realizáciu

Platia pre každý ticket v `BACKLOG.md`.

**Obmedzenia**

- **WordPress** nemá a nesmie mať prístup k databáze ani k úložisku systému. Export je
  jednosmerný.
- **Peniaze:** systém neúčtuje, neintegruje sa s bankou, nepáruje platby a nikdy nedrží
  platobné údaje darcov.
- **Prístupové práva** sa vynucujú na serveri. Skrytie v UI sa nepočíta.
- **Súbory** (fotky, reporty, zmluvy) nie sú na uhádnuteľnej adrese ani v spustiteľnom
  priestore a ich typ sa validuje. Výnimkou sú len kópie fotiek označených na zverejnenie
  v exporte. Reporty a zmluvy sa nikdy neexportujú.
- **Celý stav** je v databáze a v súboroch; konfigurácia cez premenné prostredia, žiadne
  údaje napevno v kóde.
- **Žiadne produkčné dáta** v testovacom prostredí.
- **Časované udalosti** (expirácia rezervácie, koniec výpovednej lehoty, upozornenia)
  nezávisia od návštevy aplikácie a ich opakované spracovanie nevytvorí duplicitu.

**Definition of Done**

1. Ticket sa dá predviesť na testovacom prostredí.
2. Pravidlá, ktoré ticket zavádza, majú automatizovaný test, ktorý padá, keď sa pravidlo
   poruší.
3. Kód prešiel review iného člena tímu.
4. Prístupové práva sú vynútené na serveri.
5. Zmeny citlivých polí a stavov zapisujú audit — minimálne bankové spojenie, ceny, suma a
   splátkový kalendár sponzorstva, stav sponzorstva a rezervácie, potvrdenie platby,
   zoznam trimestra, rola a deaktivácia účtu, pozvanie a pregenerovanie hesla, označenie
   fotky na zverejnenie, schválenie dieťaťa a reportu, prestup dieťaťa.
6. Je nasadené na testovacom prostredí automatizovaným nasadením.
7. Neobsahuje produkčné dáta.

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

Interne sa ale počíta **na trimester** (4 mesiace) — to je aj minimálna dĺžka podpory a
zároveň účtovný a školský takt celého programu. Mesačná suma na webe je len odvodené číslo.

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
osobné mailboxy, súhlasy existujú na papieri a nie sú nijako spárované s údajmi, ktoré
pokrývajú. Zverejnenie fotky dieťaťa bez dohľadateľného súhlasu je reálne riziko, nie
teoretické.

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
ktorý je nielen kontrolou, ale aj editorskou prácou — preklad z angličtiny, preformulovanie
príbehu pre slovenského čitateľa, redakcia toho, čo sa smie zverejniť.

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
| **Opatrovník** (rodič, príbuzný, ústav) | prihlási dieťa, podpíše súhlasy a zmluvu so školou | nič v systéme — vstupuje cez školu |
| **Škola** | zadáva podklady o deťoch, nahráva fotky a vysvedčenia po trimestroch | svoje deti, prehľad registrovaných a sponzorovaných, sumy za trimester — **bez** údajov o donorovi |
| **ADRA — koordinátor/admin** | schvaľuje a edituje podklady, publikuje profily, generuje zmluvy, eviduje platby, komunikuje s donorom | všetko |
| **Donor** | vyplní sponzorský formulár, podpíše zmluvu, platí | svoje dieťa: údaje, príbeh, fotky, vysvedčenia, vlastné platby |

Nie každý aktér je používateľ systému. Opatrovník ním nebude nikdy; škola v Ugande je
používateľ s obmedzenou konektivitou a pravdepodobne na mobile.

---

## 6. Doménové entity

Zoradené podľa toho, ako dôležité sú pre pochopenie, nie podľa implementácie.

**Dieťa** — jadro celej domény. Nesie osobné údaje, rodinnú a sociálnu situáciu, podmienky
a prostredie bývania, pôvod (miestny / utečenec + krajina), príbeh, potrebný typ podpory,
fotografie, súhlasy a stav v procese. Rozsah polí definuje `Formulár dieťaťa.docx` a je
výrazne širší než to, čo sa zverejňuje na webe — väčšina slúži na posúdenie oprávnenosti,
nie na prezentáciu.

**Podklad zo školy** — samostatná entita, nie stav dieťaťa. Surový záznam od školy, ktorý
má vlastný životný cyklus (odoslaný → vrátený na doplnenie → schválený) a po schválení sa
z neho stane alebo sa doňho zapíše záznam dieťaťa. Oddelenie je podstatné: vďaka nemu môže
škola zadávať bez rizika a ADRA má auditovateľné „čo prišlo vs. čo sme z toho urobili“.

**Verejný profil** — redigovaná a preložená verzia dieťaťa určená na zverejnenie: príbeh
pre web, vybrané fotky, zobrazená mesačná suma. Nie stránka, ktorú by prevádzkoval tento
systém, ale **export do WordPressu** (viď R1). Verejný web nikdy nečíta interný záznam a
export neobsahuje presnú adresu ani plné meno opatrovníka.

Dôsledok, s ktorým treba vedome pracovať: exportom vzniká kópia dát mimo systému, teda
presne to, čo popisuje P2. Aby to nebolelo, musí export byť **opakovateľný** — pri zmene sa
profil vygeneruje znovu a prepíše — a **stav dostupnosti dieťaťa nesmie žiť vo WordPresse.**
Tam patrí len text, fotky a odkaz; či dieťa ešte hľadá podporu, rozhoduje systém v momente,
keď donor na odkaz klikne.

**Opatrovník / domácnosť** — vzťah k dieťaťu, podpisovateľ súhlasov. Dôležité: z jednej
domácnosti môže byť v programe viac detí, takže profil rodiny a jej situácia sa zdieľajú.

**Škola** — názov, adresa, príbeh a fotky (má vlastnú prezentáciu na webe), kontaktná
osoba, bankové spojenie, zmluva s ADRA, ponúkané programy.

**Program podpory** — kombinácia školy a rozsahu (len strava / školné / školné + strava /
+ internát) s cenou za trimester. Musí byť verzionovaný v čase: ceny sa menia, ale
existujúce sponzorstvá držia sumu, s ktorou bola podpísaná zmluva.

**Trimester** — kalendárna os systému. Viažu sa na ňu platby, vysvedčenia, prehľady aj
minimálna dĺžka podpory. Ugandský školský rok má tri trimestre; treba potvrdiť, či sú pre
obe školy rovnaké.

**Donor** — kontaktné a fakturačné údaje, jazyk, komunikačné preferencie.

**Rezervácia** (záujem o dieťa) — vzniká vyplnením sponzorského formulára, ktorý už beží
v systéme (donor sa doňho dostane odkazom z WordPressu), a dieťa **časovo obmedzene
blokuje**, kým sa nepodpíše zmluva. Po expirácii sa dieťa vracia do ponuky. Toto je priama
odpoveď na P4 a v dokumentoch je naznačené ako „zablokovanie dieťaťa na webe“.

**Sponzorstvo** — centrálna entita systému: vzťah donor ↔ dieťa ↔ program, s dátumom
začiatku, dĺžkou v trimestroch, dohodnutou sumou a stavom (čaká na podpis / aktívne /
pozastavené / ukončené). Všetky financie, dokumenty a reporty visia na ňom.

**Zmluva** — dokument vygenerovaný zo šablóny, s vlastným stavom a uloženým PDF. Tri typy:
ADRA–donor, ADRA–škola, škola–opatrovník.

**Potvrdenie platby od donora** a **platba škole** — dva oddelené toky, viazané na
sponzorstvo a trimester; ADRA stojí medzi nimi a nesie riziko rozdielu. Systém ale nie je
účtovníctvo (viď R2): nedrží sumy z bankového výpisu, len prevádzkový fakt „sponzorstvo ×
trimester = zaplatené / nezaplatené, potvrdil ten a ten vtedy a vtedy“.

**Report o dieťati** — vysvedčenie, hodnotenie, priebežné fotky za trimester; to, čo
udržiava donora v programe.

**Súhlas** — typ (spracovanie údajov, zverejnenie príbehu a fotiek, poskytovanie výsledkov
donorovi), dátum, sken podpisu, platnosť. Nie poznámka v poli — samostatná entita, na ktorú
sa systém pri publikovaní pozerá.

---

## 7. Životné cykly

**Dieťa**

```
podklad odoslaný školou
   └─▶ vo spracovaní ADRA ──(vrátené na doplnenie)──┐
           └─▶ schválené (v internej databáze)      │
                  └─▶ zverejnené — hľadá podporu ◀──┘
                         └─▶ rezervované (donor vyplnil formulár)
                                └─▶ podporované
                                       ├─▶ pozastavené
                                       └─▶ ukončené (dokončilo stupeň / odišlo)
```

Návratová hrana, ktorá bolí najviac: **podporované → hľadá podporu**, keď donor prestane
platiť v rozbehnutom školskom roku. Škola už s peniazmi počítala. Systém to musí vedieť
zachytiť včas a nie až pri trimestrálnom účtovaní.

**Sponzorstvo**

```
žiadosť → zmluva vygenerovaná → podpísaná → aktívne ⇄ obnovené (ďalší trimester/rok)
                                                    └─▶ ukončené
```

---

## 8. Pravidlá, ktoré má systém držať

Sú to tie miesta, kde dnes chyba vzniká najčastejšie:

1. Profil dieťaťa sa **nesmie** zverejniť bez dohľadateľného súhlasu opatrovníka so
   zverejnením príbehu a fotografií.
2. Dieťa môže mať v danom momente najviac jednu aktívnu rezerváciu.
3. Zmluva sa generuje výhradne zo schválených dát, nikdy zo surového podkladu školy.
4. Suma v zmluve je suma programu platná v čase podpisu a nemení sa zmenou cenníka.
5. Škola vidí sumy za trimester, ktoré jej ADRA platí — nevidí identitu ani platby donora.
6. Trimester musí byť pre školu pokrytý za všetky aktívne sponzorstvá, aj keď donor ešte
   nezaplatil; systém má tento rozdiel zviditeľniť, nie ho skryť.
7. Export pre WordPress nikdy neobsahuje presnú adresu dieťaťa ani plné meno opatrovníka.
8. Stav dostupnosti dieťaťa (hľadá podporu / rezervované / podporované) žije **výhradne
   v systéme**. WordPress ho nedrží ani nemení; rezerváciu potvrdzuje systém.
9. Systém nevydáva účtovné doklady a jeho finančné prehľady sú prevádzkové. Pri rozpore
   vyhráva účtovníctvo ADRA.
10. Zmena bankového spojenia školy vyžaduje potvrdenie druhou osobou a zapíše sa do auditu
    (viď časť 9). Platba sa nikdy neodošle podľa údaja, ktorý sa zmenil bez potvrdenia.

---

## 9. Bezpečnosť a spoľahlivosť

Toto nie sú „technické detaily na neskôr“ — obe požiadavky menia, ako sa systém navrhne,
a jedna z nich je čiastočne procesná, nie programátorská.

### 9.1 Čo je vlastne cenný cieľ

Intuitívne sa zdá, že najcennejšie sú osobné údaje detí. Vážnejší cieľ je ale **bankové
spojenie školy**: je to jediné miesto, kde zmena jedného poľa presmeruje reálne peniaze.
Ide o presne ten istý vzorec ako podvody s prepísanými faktúrami, a v praxi naň nestačí
„mať dobre zabezpečený systém“ — útočník ho často ani nemusí hacknúť, stačí mu poslať
presvedčivý email a nechať údaj prepísať oprávneného používateľa.

Preto platí:

- Bankové spojenie školy je **zmenovo riadené pole**: každá zmena sa zapíše do auditu
  (kto, kedy, z čoho na čo) a vyžaduje potvrdenie druhou osobou z ADRA.
- Škola si bankové spojenie **nemení sama**. Mení ho ADRA po overení mimo systému —
  telefonátom na už známy kontakt, nie na číslo z emailu, ktorý o zmenu žiada.
- Pri zmene dostane notifikáciu aj druhý človek v ADRA, aby tichá zmena nebola možná.
- Audit citlivých polí je **append-only** — nedá sa prepísať ani zmazať z aplikácie.

Druhá kategória je osobné údaje detí: príbehy, sociálna situácia, fotografie. Tu je
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
  skryté v UI. Škola vidí svoje deti, donor svoje dieťa, nič viac.
- Admin prístup ADRA s dvojfaktorovým overením.
- **Žiadne produkčné dáta v testovacom prostredí** a žiadne exporty do osobných zariadení
  či WhatsAppu — dnešný kanál je zároveň dnešný únik.

Poznámka k zadaniu: `Štruktúra webu.docx` počíta s prístupom donora „cez heslo“ ku karte
dieťaťa. Spoločné či zdieľané heslo na profil je slabý vzor — časom sa rozšíri a nikdy sa
nemení. Lepšie je buď riadny účet donora, alebo podpísaný odkaz s expiráciou.

### 9.3 Spoľahlivosť: dáta sa nesmú stratiť

Užitočný rámec pre tento program: **program beží v trimestroch, nie v sekundách.** Keď
systém pár hodín nebeží, nestane sa nič — obeh detí, zmlúv a platieb je pomalý. Ak sa ale
stratí týždeň zadaných podkladov, ADRA si ich už nemá odkiaľ vziať, lebo pôvodné správy sú
v chaotickom WhatsApp vlákne. **Priorita je teda trvácnosť dát, nie vysoká dostupnosť** — čo
je dobrá správa, pretože trvácnosť je výrazne lacnejšia.

Z toho konkrétne:

- **Hotové zálohovanie od poskytovateľa databázy** je postačujúce a žiaduce — nemá zmysel
  písať vlastné skripty. Podmienka je automatické zálohovanie s obnovou do bodu v čase
  a obnova na niekoľko kliknutí, nie ručný postup.
- **Záloha zahŕňa aj súbory, nie len databázu.** Fotky, vysvedčenia a PDF zmlúv sú rovnako
  dôležité ako záznamy. Samotný dump databázy by po obnove ukazoval na neexistujúce
  fotografie — a PDF zmlúv sú právne dokumenty.
- **Záloha musí byť aspoň raz vyskúšaná obnovením.** Neodskúšaná záloha je presvedčenie,
  nie záloha.
- **Kópia zálohy mimo hostingu, vo vlastníctve ADRA.** Ak sa stratí hosting kvôli zrušenému
  účtu, nezaplatenej faktúre alebo zaniknutému dodávateľovi, zmiznú s ním aj zálohy, ktoré
  ležia v tom istom účte. Pre organizáciu, ktorá systém neprevádzkuje sama, je toto
  pravdepodobnejší scenár než útok.

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
   vyžaduje zmenu správania ľudí v Ugande, slabé pripojenie, prácu na mobile. Systém musí
   uniesť aj to, že podklad doňho zadá pracovník ADRA namiesto školy.
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
Systém platby neúčtuje. Pracovník ADRA v admin rozhraní len zaznačí, že platba za daný
trimester prišla.
*Dôsledky:* žiadna banková integrácia ani automatické párovanie; systém drží len stav
„zaplatené / nezaplatené“ na sponzorstvo a trimester, z ktorého stavia prevádzkové prehľady;
tieto prehľady nie sú účtovný výstup (invariant 9).

**R3 — Import z existujúcich Excelov je súčasť zadania.**
Nie len jednorazová migrácia, ale aj priebežný vstupný kanál. Detaily aktuálneho formátu
budú dodané neskôr.
*Dôsledky:* import ústi do tej istej fronty podkladov ako formulár školy, teda prechádza
rovnakým schvaľovaním; musí byť tolerantný k nekonzistentným dátam a umožniť mapovanie
stĺpcov, keď sa formát tabuliek zmení.

---

## 12. Otvorené otázky

Dátový model:
- Môže mať dieťa viac donorov naraz (jeden platí stravu, druhý školné), alebo je vzťah
  striktne 1:1?
- Kto prideľuje kód dieťaťa (`UGA 127`) a je stabilný na celý čas programu?
- Čo sa deje pri prestupe dieťaťa na vyšší stupeň alebo do inej školy — mení sa program,
  cena, a teda aj zmluva?
- Sú trimestre pre obe školy totožné?

Proces:
- Aká je lehota a postup, keď donor prestane platiť — kto a kedy informuje školu?
- Kto prekladá príbeh dieťaťa do slovenčiny a má byť web dvojjazyčný (SK/EN)?
- **Kto a ako upraví profil vo WordPresse**, keď dieťa získa podporu alebo keď opatrovník
  odvolá súhlas so zverejnením? Export je jednosmerný, takže zásah do WordPressu zostáva
  ručný — systém vie k tomu maximálne vygenerovať zoznam „na úpravu“. Pri odvolanom súhlase
  je to právne riziko, nie kozmetika, takže tento krok potrebuje jasného vlastníka.

Právne a bezpečnostné:
- Kto je prevádzkovateľ osobných údajov — ADRA, škola, alebo obe spoločne? Existuje
  zmluvné ošetrenie prenosu údajov z Ugandy do EU?
- Súhlasy: papier + sken, alebo digitálny podpis?
- Ako dlho sa uchovávajú údaje a fotky po ukončení podpory?

Bezpečnosť a prevádzka:
- **Kto v ADRA smie meniť bankové spojenie školy a kto je tá „druhá osoba“, ktorá zmenu
  potvrdzuje?** Bez menovaných ľudí je invariant 10 len text.
- Koľko ľudí má mať admin prístup a čo sa stane, keď taký človek z ADRA odíde? Kto potom
  drží prístup k hostingu a zálohám?
- Aká strata dát je ešte akceptovateľná — deň zadávania, hodina? Od toho závisí, či stačí
  denná záloha alebo treba obnovu do bodu v čase.
- Kde bude uložená kópia zálohy mimo hostingu a na koho účet v ADRA je vedená?
- Aký je režim prístupu donora — riadny účet, alebo odkaz s expiráciou? (`Štruktúra
  webu.docx` hovorí o „prístupe cez heslo“.)
- Prevádzkuje systém ADRA sama, alebo externý dodávateľ? Kto reálne obnoví systém po havárii?
- Aká je reálna konektivita a zariadenia na školách?
- Beží popri importe z Excelu aj dobeh starých dát, alebo sa historické sponzorstvá
  dosledujú po starom a systém začne od aktuálneho školského roka?

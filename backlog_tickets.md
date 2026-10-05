# HELPKIDS — návrh produktového backlogu pre tím

Rozpad `BACKLOG.md` na kandidátske Product Backlog Items. Dokument prináša Product Owner
na refinement; nie je to hotový Sprint Backlog ani záväzok, čo sa stihne v konkrétnom
sprinte. Tím položky odhaduje, navrhuje ich technické rozdelenie a upozorňuje na chýbajúce
závislosti. Product Owner po diskusii drží výsledné poradie podľa hodnoty a rizika.

Položky sú nižšie zoskupené podľa oblastí, aby sa dali dohľadať. Poradie dodania určujú
produktové prírastky v nasledujúcej časti, nie číslo oblasti ani súvislý rozsah ID.

## Produktový cieľ a prírastky

**Prvý releasable produktový cieľ:** pracovník ADRA vie na testovacom prostredí zadať
podklad dieťaťa, schváliť ho do hlavnej databázy a pripraviť z neho profil na zverejnenie.
Tým sa prvýkrát odstráni reálne prepisovanie údajov.

Kandidátske prírastky v poradí produktovej priority:

1. **ADRA spracuje jedno dieťa od podkladu po schválený záznam.** Minimálne nasadenie,
   prihlásenie ADRA, škola, bezpečné súbory, podklad, schválenie a audit.
2. **Profil sa exportuje do WordPressu.**
3. **Darca bezpečne rezervuje dieťa a systém mu okamžite vygeneruje reálnu zmluvu.**
   Vyžaduje A1.
4. **ADRA otvorí trimester a eviduje platby a rozdiely voči školám.**
5. **Školy zadávajú podklady a reporty samy; darcovia vidia schválené výsledky.**

Prvý releasable cieľ pokrývajú prírastky 1 a 2.

### Kandidátske položky prírastku 1

Najbližšie položky na refinement, v navrhovanom poradí. Ostatné položky sa spresnia až pred
svojím prírastkom.

| Položka | Prečo je v prírastku 1 | Rozsah |
|---|---|---|
| HK-01 | Kostra a CI | celá |
| HK-02 | Testovacie prostredie na hostingu ADRA | celá; produkcia môže zostať prázdna |
| HK-03 | Automatizované nasadenie (DoD 6) | celá |
| HK-04 | Limity hostingu, kým je zmena lacná | celá |
| HK-06 | Prihlásenie ADRA | len roly admin a pracovník ADRA |
| HK-08 | 2FA pre ADRA | celá |
| HK-09 | Audit (DoD 5) | len polia, ktoré prírastok mení |
| HK-10 | Fotky v podklade | celá |
| HK-12 | Dieťa patrí škole | bez bankového spojenia a programov |
| HK-16 | Štruktúra schváleného záznamu | celá |
| HK-17 | Kód dieťaťa | celá |
| HK-18 | Stav dieťaťa | len stav „schválené“ |
| HK-31 | Pracovník ADRA zadá podklad | celá |
| HK-32 | Fronta podkladov | celá |
| HK-33 | Editácia a schválenie | celá |
| HK-23 | Vymyslené dáta na predvedenie | len školy, podklady a deti |

Zámerne nie sú v prírastku 1: HK-34 (vrátenie na doplnenie potrebuje formulár školy
HK-54), darca a sponzorstvo, e-maily a časované udalosti.

Každý prírastok sa má na refinementoch deliť na najmenšie end-to-end položky, ktoré tím
vie dokončiť a predviesť. Prierezové technické práce sa robia v rozsahu potrebnom pre
aktuálny prírastok a potom sa rozširujú.

## Definition of Ready

Položka sa môže vybrať do sprintu, keď:

1. Je jasné, komu a akú hodnotu alebo zníženie rizika prináša.
2. Má overiteľné akceptačné kritériá bez neurčitých slov typu „použiteľné“ alebo
   „dostatočne rýchle“ bez meradla.
3. Má dostupné vstupy a nemá otvorený blocker.
4. Tím rozumie dátam, oprávneniam a väzbám na existujúce stavy.
5. Tím verí, že sa zmestí do jedného sprintu; inak ju na refinement-e rozdelí.
6. Je známe, ako sa výsledok predvedie na vymyslených dátach.

Položky označené `⨯` sú **Blocked**. Neoznačené položky sú kandidáti na refinement, nie
automaticky **Ready**.

## Odchýlky od poradia epikov

Vychádza sa z poradia epikov v `BACKLOG.md`, s týmito úpravami:

- **Prierezové veci sa nerobia vopred ako samostatná vrstva.** Audit, súbory, e-maily,
  časované udalosti a zálohy vznikajú v prvom prírastku, ktorý ich potrebuje, a len
  v rozsahu, ktorý ten prírastok potrebuje.
- **Epik 9 je rozptýlený.** Hosting na účte ADRA je súčasťou prvého prírastku, aby sa
  limity hostingu ukázali hneď. Zálohy a skúška obnovy musia byť hotové pred prvým
  produkčným použitím. Na konci zostáva len odovzdanie.
- **Prestup do inej školy (1.2)** je posunutý za otvorenie trimestra, lebo potrebuje
  históriu trimestrov.
- **Generovanie zmlúv je rozdelené.** Mechanizmus s provizórnou šablónou (HK-25) nie je
  blokovaný. Napojenie reálnych šablón (HK-28 až HK-30) čaká na A1. Vďaka tomu sa dá
  rezervácia postaviť skôr, než ADRA dodá šablóny.

## Značky

- `⨯ <ID>` — ticket sa nesmie vziať do sprintu, kým PO nezabezpečí chýbajúci vstup alebo
  rozhodnutie označené príslušným ID v `OTAZKY-PRE-ADRA.md`
- `[test]` — kritérium vyžaduje automatizovaný test (DoD 2)
- **Zdroj** — položka v `BACKLOG.md`
- **Závisí od** — tickety, ktoré musia byť hotové skôr

Každý ticket musí spĺňať Definition of Done z `BACKLOG.md`. Odhady dopĺňa tím až po
refinemente.

---

## Oblasť 0 — Nasadená prázdna aplikácia

### HK-01 · Kostra aplikácie a CI
Zdroj: 0.2, 1.1 · Závisí od: —
- Repozitár s kostrou aplikácie; testy bežia automaticky pri každej zmene
- Používateľské texty nie sú napevno vo view alebo komponentoch; používajú jeden
  prekladový mechanizmus. Prvý dodaný jazyk je angličtina

### HK-02 · Hosting na účte ADRA, testovacie a produkčné prostredie
Zdroj: 0.1, 9.5 · Závisí od: HK-01
- Hosting, doména a úložisko sú od prvého dňa vedené na organizačný účet ADRA, nie na
  osobný účet
- Produkčná adresa cez HTTPS ukazuje stránku z nasadenej aplikácie
- Oddelené testovacie prostredie
- Databáza, úložisko a tajomstvá sa konfigurujú cez premenné prostredia (O7)

### HK-03 · Automatizované nasadenie
Zdroj: 0.1, 0.2 · Závisí od: HK-02
- Nasadenie na testovacie prostredie prebehne bez ručných krokov
- Nasadenie na produkciu je jeden vedomý krok
- V repozitári je popísané, ako sa aplikácia nasadí od nuly

### HK-04 · Prieskum limitov hostingu
Zdroj: 0.3 · Závisí od: HK-02
- Písomný zápis v repozitári: limit súborov (inodov), plánované úlohy a ich minimálny
  interval, odchádzajúce spojenia a odosielanie e-mailov, knižnice na prácu s obrázkami
  a s PDF, reálny `max_execution_time` a praktický limit veľkosti uploadu
- Tím s PO zapíše merateľný test cieľového objemu pre 50 škôl a 5 000 detí vrátane
  predpokladaného počtu a veľkosti súborov
- PO je informovaný, ak niečo z toho mení predpoklady

### HK-05 · Denná automatická záloha
Zdroj: 9.1 · Závisí od: HK-02
- Databáza **aj súbory** sa zálohujú denne a automaticky
- Ak to poskytovateľ ponúka, použije sa jeho zálohovanie

---

## Oblasť 1 — Bezpečný základ

### HK-06 · Prihlásenie a roly
Zdroj: 1.1 · Závisí od: HK-01
- Roly: admin ADRA, pracovník ADRA, škola, darca
- Admin môže všetko, čo pracovník, a navyše spravuje používateľské účty
- Prístup sa vynucuje na serveri pre každú rolu [test] (O5)
- Používateľ školy A sa nedostane k záznamu ani súboru školy B [test]
- Darca A sa nedostane k dieťaťu ani súboru darcu B [test]

### HK-07 · Správa používateľských účtov
Zdroj: 1.1 · Závisí od: HK-06
- Admin zakladá účty ADRA, mení ich rolu a môže deaktivovať ľubovoľný používateľský účet
- Pracovník ADRA účty spravovať nemôže [test]
- Deaktivovaný účet sa neprihlási a jeho existujúce relácie prestanú platiť [test]
- Deaktivácia mení len prístup: deti, podklady, sponzorstvá a história zostávajú bez
  zmeny [test] *(predpoklad PO)*

### HK-08 · Dvojfaktorové overenie pre ADRA
Zdroj: 1.5 · Závisí od: HK-06
- Admin aj pracovník ADRA sa bez druhého faktora neprihlásia [test]
- Škola a darca druhý faktor nepotrebujú
- Pri strate druhého faktora ho resetuje admin, nie samoobsluha cez e-mail [test]
- Pre prípad, že druhý faktor stratí jediný admin, existuje napísaný postup obnovy

### HK-09 · Audit zmien citlivých polí
Zdroj: DoD 5, 1.4 · Závisí od: HK-06
- Zmena citlivého poľa zapíše, kto, kedy a z čoho na čo zmenil
- Záznam auditu sa nedá z aplikácie prepísať ani zmazať [test]
- Audit sa týka minimálne polí a udalostí vymenovaných v DoD 5 v `BACKLOG.md`

### HK-10 · Uloženie a výdaj súborov s kontrolou prístupu
Zdroj: 0.4 · Závisí od: HK-06
- Súbor sa nedá získať bez overenia oprávnenia [test]
- Adresa súboru sa nedá uhádnuť ani odvodiť z identifikátora dieťaťa [test] (O6)
- Pri uploade sa validuje typ súboru [test]; súbory neležia v priestore, odkiaľ sa dajú
  spustiť
- Riešenie prejde testom cieľového objemu definovaným v HK-04 [test]
- Platí pre všetky súbory v systéme; verejné sú len kópie fotiek v exporte (HK-37)

### HK-11 · Odosielanie e-mailov zo šablón
Zdroj: predpoklad pre 1.8, 5.10, 5.13, 6.8, 7.7, 8.4, 8.5 · Závisí od: HK-04
- Systém posiela e-mail zo šablóny s dosadenými údajmi
- Predmet a telo šablóny používajú rovnaký prekladový mechanizmus ako aplikácia
- Pri odoslanom e-maile sa dá dohľadať príjemca, typ šablóny, čas a výsledok odoslania

### HK-11A · Automatické spracovanie časovaných udalostí
Zdroj: O9, 5.6, 5.9, 6.7 · Závisí od: HK-04, HK-11
- Splatné udalosti sa spracujú bez toho, aby niekto otvoril aplikáciu [test]
- Opakované spracovanie tej istej udalosti nevytvorí duplicitnú zmenu ani nepošle ten istý
  e-mail druhýkrát [test]
- Neúspešné spracovanie sa zaznamená a dá sa bezpečne zopakovať

### HK-20A · Obnova hesla
Zdroj: 1.1 · Závisí od: HK-06, HK-11
- Používateľ si vyžiada obnovu hesla bez toho, aby systém prezradil, či e-mail existuje
  [test]
- Odkaz na obnovu je jednorazový, má konfigurovateľnú expiráciu a po použití ani po
  expirácii nefunguje [test]
- Zmenou hesla prestanú platiť existujúce relácie používateľa [test]

---

## Oblasť 2 — Škola, dieťa, darca (Epik 1)

### HK-12 · Záznam školy
Zdroj: 1.3 · Závisí od: HK-06
- Názov, sídlo a korešpondenčná adresa, popis situácie, kontaktná osoba, ponúkané programy

### HK-12A · Údaje ADRA
Zdroj: 1.10 · Závisí od: HK-06, HK-09
- Názov, IČO, štatutárny zástupca, sídlo, korešpondenčná adresa, IBAN, kontakt; šablóny
  zmlúv ich preberajú odtiaľ
- Zmena sa zapíše do histórie a nemení už vygenerované zmluvy [test]

### HK-13 · Programy podpory a cenník
Zdroj: 1.3 · Závisí od: HK-12
- Program = škola + rozsah (len strava / školné / školné + strava / + internát) s cenou za
  trimester v eurách
- Mesačná suma programu je vždy 3 × aktuálna cena za trimester / 12 [test]
- Zmena cenníka sa netýka existujúcich darcov [test] *(invariant 4)*

### HK-14 · Bankové spojenie školy
Zdroj: 1.4 · Závisí od: HK-09, HK-10, HK-12
- Bankové spojenie mení len ADRA, škola nie [test] *(invariant 10)*
- Pri zmene ADRA priloží dodatok k zmluve
- Zmena sa zapíše do histórie, ktorá je len na pridávanie [test]

### HK-15 · Pozvanie školy
Zdroj: 1.8 · Závisí od: HK-11, HK-12
- ADRA pozve školu e-mailom; škola si cez pozvánku doplní údaje a nastaví prístup
- Pozvánka je jednorazová, má konfigurovateľnú expiráciu a po použití ani po expirácii sa
  nedá znovu použiť [test]
- Škola môže mať viac používateľov, každého pozýva ADRA; všetci vidia to isté
  *(predpoklad PO)*
- Verejná registrácia škôl neexistuje [test]

### HK-16 · Štruktúra schváleného záznamu dieťaťa
Zdroj: 1.2 · Závisí od: HK-10, HK-12
- Polia podľa `Formulár dieťaťa.docx`: osobné údaje, situácia rodiny, kto sa o dieťa
  stará, podmienky a prostredie bývania, pôvod, príbeh, finančná situácia, potrebný typ
  podpory, fotky, dátumy (vyplnenie, zverejnenie, začiatok podpory)
- Sekcia „Osobné súhlasy“ z formulára sa nevytvára, súhlasy systém neeviduje
- Pri každej fotke sa dá označiť, či smie ísť do verejného exportu
- Dieťa patrí aktuálnej škole
- Ticket definuje výsledný schválený záznam; nezavádza samostatnú cestu, ktorou by sa
  produkčné dieťa vytvorilo bez schválenia podkladu v HK-33

### HK-17 · Kód dieťaťa
Zdroj: 1.2 · Závisí od: HK-16
- Kód generuje systém; je jednoznačný a nemenný [test]

### HK-18 · Stav dieťaťa
Zdroj: 1.2 · Závisí od: HK-16
- Stavy: schválené → zverejnené → rezervované → podporované → ukončené
- Nepovolený prechod systém odmietne [test]

### HK-19 · Súrodenci
Zdroj: 1.7 · Závisí od: HK-16
- Deti sa dajú prepojiť ako súrodenci, každé má vlastné údaje
- Pri dieťati je vidieť jeho súrodencov

### HK-20 · Darca
Zdroj: 1.9 · Závisí od: HK-06
- Kontaktné a fakturačné údaje, adresa trvalého pobytu (u firmy sídlo) a korešpondenčná
  adresa, účet s heslom
- Darca vidí výhradne deti s aktívnym sponzorstvom; po ukončení sponzorstva stráca prístup
  ku karte dieťaťa, vlastné platby vidí ďalej [test] *(predpoklad PO)*

### HK-21 · Sponzorstvo
Zdroj: 1.9 · Závisí od: HK-16, HK-20
- Vzťah darca ↔ dieťa striktne 1:1: dieťa má najviac jedného darcu, darca môže mať viac
  detí [test]
- Sponzorstvo nesie mesačnú sumu, periodicitu (mesačne / štvrťročne / polročne / ročne)
  a stav (čaká na schválenie → aktívne → ukončené)
- Škola nevidí identitu darcu ani jeho platby [test] *(invariant 5)*

### HK-22 · Splátkový kalendár
Zdroj: 1.9 · Závisí od: HK-21
- Kalendár očakávaných platieb sa počíta od schválenia zmluvy podľa periodicity [test]

### HK-23 · Vymyslené testovacie dáta
Zdroj: O8 · Závisí od: HK-12 až HK-22
- Jedným príkazom sa naplní testovacie prostredie vymyslenými školami, deťmi, darcami
  a fotkami
- Rozširuje sa spolu s modelom

### HK-24 · Skúška obnovy na čistom stroji
Zdroj: 9.2 · Závisí od: HK-05, HK-23
- Zo zálohy sa na čistom stroji obnoví databáza aj súbory a aplikácia na nich beží
- Postup je napísaný v repozitári
- Pred odovzdaním sa skúška zopakuje (HK-65)

---

## Oblasť 3 — Zmluvy (Epik 2)

### HK-25 · Generovanie PDF zo šablóny
Zdroj: 2.1 (rozdelené) · Závisí od: HK-10, HK-21
- Systém vygeneruje PDF zo šablóny a z údajov, ktoré už má; zatiaľ s provizórnou šablónou
- Generuje sa výhradne zo schválených dát, nikdy zo surového podkladu [test]
  *(invariant 3)*
- Vygenerované PDF sa uloží a dá sa znovu stiahnuť
- Jazyk zmluvy určuje šablóna

### HK-26 · Stav zmluvy a podpísaný sken
Zdroj: 2.4 · Závisí od: HK-25
- Zmluva má stav (vygenerovaná → podpísaná) a dátum
- K zmluve sa dá priložiť podpísaný sken

### HK-27 · Dodatky k zmluvám · `⨯ A1` (šablóna dodatku)
Zdroj: 2.5 · Závisí od: HK-25, HK-14
- K zmluve sa dá vygenerovať dodatok: zmena sumy darcu, zmena periodicity, zmena
  bankového spojenia školy
- Suma darcu sa mení len dodatkom z rozhodnutia ADRA, nikdy automaticky [test]
  *(invariant 4)*
- Dodatkom k zmluve s darcom sa prepočíta splátkový kalendár

### HK-28 · Zmluva ADRA–darca · `⨯ A1`
Zdroj: 2.1 · Závisí od: HK-25
- Reálna šablóna od ADRA
- Zmluva je na neurčito s mesačnou výpovednou lehotou a obsahuje splátkový kalendár
- Suma darcu je suma programu platná v čase vzniku rezervácie; zmena cenníka počas
  lehoty rezervácie ani neskôr ju nemení [test] *(invariant 4)*

### HK-29 · Zmluva ADRA–škola · `⨯ A1`
Zdroj: 2.2 · Závisí od: HK-25, HK-12
- Zmluva sa vygeneruje z reálnej šablóny a z údajov školy, jej programov a bankového
  spojenia, ktoré v systéme vedie ADRA
- Vygenerované PDF sa uloží pri škole a dá sa znovu stiahnuť
- Zmena údajov školy spätne nezmení už vygenerované PDF [test]

### HK-30 · Zmluva škola–opatrovník · `⨯ A1`
Zdroj: 2.3 · Závisí od: HK-25, HK-26
- Zmluva sa vygeneruje z reálnej šablóny a zo schválených údajov dieťaťa, opatrovníka
  a školy
- Škola si vygenerovanú zmluvu stiahne a podpísanú nahrá späť
- Vygenerovaná aj podpísaná verzia zostanú uložené a dohľadateľné

---

## Oblasť 4 — Fronta podkladov (Epik 3)

### HK-31 · Podklad ako samostatný záznam
Zdroj: 3.2, 7.4 · Závisí od: HK-10, HK-12
- Podklad má vlastný životný cyklus: odoslaný → vo spracovaní → vrátený na doplnenie →
  schválený
- Pracovník ADRA vie zadať podklad namiesto školy, a to je prvý vstupný kanál
- Škola nikdy nezapisuje priamo do záznamu dieťaťa [test] (O4)

### HK-32 · Fronta podkladov pre ADRA
Zdroj: 3.1 · Závisí od: HK-31
- Zobrazuje podklady v stavoch odoslaný / vrátený na doplnenie
- Pri každom podklade je škola, dátum odoslania a počet dní čakania
- Do fronty ústia všetky zdroje podkladov (O3)

### HK-33 · Editácia a schválenie podkladu
Zdroj: 3.2 · Závisí od: HK-16, HK-32
- Pred schválením sa dá podklad redakčne upraviť (príbeh, fotky, vysvedčenia)
- Schválením vznikne záznam dieťaťa alebo sa aktualizuje existujúci
- Pôvodný podklad zostáva čitateľný a nemenný [test]

### HK-34 · Vrátenie podkladu na doplnenie
Zdroj: 3.3 · Závisí od: HK-15, HK-32, HK-54
- Podklad sa dá vrátiť škole s poznámkou, čo chýba
- Škola vidí, čo sa od nej žiada, a podklad doplní

---

## Oblasť 5 — Import z Excelov (Epik 4) · `⨯ A2`

### HK-35 · Import zoznamu detí · `⨯ A2`
Zdroj: 4.1, 4.3 · Závisí od: HK-32
- Mapovanie stĺpcov, ktoré sa dá zmeniť, keď sa zmení formát tabuľky
- Tolerantný k nekonzistentným dátam
- Výsledkom sú podklady vo fronte, nie záznamy detí [test] (O3, O4)

### HK-36 · Report z importu · `⨯ A2`
Zdroj: 4.2 · Závisí od: HK-35
- Po importe je vidieť, čo sa nenaimportovalo a prečo

---

## Oblasť 6 — Export profilu a rezervácia (Epik 5)

### HK-37 · Export profilu pre WordPress
Zdroj: 5.1, 5.2, 5.4 · Závisí od: HK-16, HK-13
- HTML/Markdown + fotky označené na zverejnenie + odkaz na sponzorský formulár s identifikátorom dieťaťa
- Export je opakovateľný: pri zmene sa vygeneruje znovu
- Neobsahuje presnú adresu ani plné meno opatrovníka [test] *(invariant 7)*
- Neobsahuje stav dostupnosti dieťaťa *(invariant 8)*
- Neobsahuje fotky bez označenia na zverejnenie, reporty ani zmluvy [test] (O6)

### HK-38 · Sponzorský formulár
Zdroj: 5.5, 5.7 · Závisí od: HK-11, HK-20, HK-37
- Darca prichádza odkazom z WordPressu
- Nový darca si pri formulári založí účet s heslom; existujúci sa prihlási a rezervuje
  pod tým istým účtom
- E-mail darcu je unikátny, druhý účet s tým istým e-mailom nevznikne [test]
- Nový darca musí potvrdiť e-mail; rezervácia vznikne až po potvrdení, do toho zostáva dieťa
  voľné [test] *(predpoklad PO)*
- Limit počtu pokusov a časové okno sú konfigurovateľné, predvolene 5 odoslaní za hodinu
  z jednej adresy alebo pre jeden e-mail; po prekročení formulár ďalší pokus odmietne [test]
- Neprezradí nič nad rámec verejného profilu, ani to, či je dieťa voľné, kým darca
  formulár neodošle

### HK-39 · Rezervácia dieťaťa
Zdroj: 5.6, 2.1 · Závisí od: HK-11A, HK-38, HK-25, HK-18
- Dieťa má najviac jednu aktívnu rezerváciu [test] *(invariant 2)*, aj keď dva formuláre
  prídu naraz [test]
- Rezervácia blokuje dieťa 7 kalendárnych dní; potom sa dieťa vráti do ponuky, aj keď
  medzitým na serveri nič nebežalo [test]
- Pri vzniku rezervácie systém okamžite vygeneruje zmluvu ADRA–darca a darca si ju môže
  stiahnuť [test]
- Pre produkciu treba reálnu šablónu (HK-28)

### HK-40 · Nahratie podpísanej zmluvy darcom
Zdroj: 5.9 · Závisí od: HK-11A, HK-39, HK-26
- Nahratím podpísanej zmluvy v lehote sa lehota zastaví [test]
- Zrušiť rezerváciu potom môže už len ADRA, alebo darca zrušením zmluvy [test]
- Nahratá zmluva čaká vo fronte ADRA s počtom dní čakania; ak ju ADRA neposúdi do 3 dní,
  systém ADRA upozorní. Dieťa sa automaticky neuvoľní [test]

### HK-41 · Schválenie alebo odmietnutie zmluvy
Zdroj: 5.12, 5.13 · Závisí od: HK-40, HK-11, HK-22
- Schválením vznikne aktívne sponzorstvo, začne sa splátkový kalendár a darcovi sa
  sprístupní karta dieťaťa
- Odmietnutím sa rezervácia zruší, dieťa sa vráti do ponuky a darca dostane e-mail [test]

### HK-42 · E-mail po vypršaní rezervácie
Zdroj: 5.10 · Závisí od: HK-11A, HK-39, HK-11
- Po vypršaní rezervácie dostane darca e-mail

### HK-43 · Rezervácia súrodencov jedným krokom
Zdroj: 5.11 · Závisí od: HK-39, HK-19
- Darca jedným krokom rezervuje všetkých voľných súrodencov
- Pre každé dieťa vznikne samostatná rezervácia, sponzorstvo a zmluva [test]

### HK-44 · Zoznam na úpravu vo WordPresse
Zdroj: 5.8 · Závisí od: HK-41
- ADRA vidí deti, ktorých profil vo WordPresse treba upraviť, napríklad lebo získali
  podporu, a vie ich odškrtnúť ako vybavené

---

## Oblasť 7 — Trimestre, platby, prehľady (Epik 6)

### HK-45 · Otvorenie trimestra
Zdroj: 6.1, 6.2, 6.2a, 6.4 · Závisí od: HK-21
- Trimester otvára pracovník ADRA a označí ho `ROK/mesiac`; označenie je unikátne [test]
- Trimester v príprave: systém pre každú školu navrhne zoznam žiakov s aktívnym
  sponzorstvom; rezervácia ani nahratá zmluva nestačia [test]
- Pred otvorením môže pracovník ADRA dieťa s darcom vyradiť a pridať dieťa bez darcu,
  ktoré financuje ADRA; pri dieťati je vidieť, či je kryté darcom alebo ADRA, škola to
  nevidí [test]
- Otvorením sa zoznam zmrazí; za deti v ňom ADRA škole zaplatí celý trimester [test]
  *(invariant 6)*
- Dieťa, ktoré získa darcu po otvorení, sa započíta až od ďalšieho trimestra [test]

### HK-45A · Uzavretie trimestra
Zdroj: 6.5 · Závisí od: HK-45
- Trimester explicitne uzatvára pracovník ADRA; otvorený je najviac jeden naraz a ďalší sa
  dá otvoriť až po uzavretí predchádzajúceho [test]
- Uzavretím sa nemení zoznam detí ani platba škole

### HK-46 · Oprava zoznamu trimestra
Zdroj: 6.3 · Závisí od: HK-45, HK-09
- Zoznam otvoreného trimestra sa dá opraviť; oprava sa zapíše do histórie

### HK-47 · Prestup do inej školy
Zdroj: 1.2 · Závisí od: HK-45
- Dieťa zostáva jedno, s rovnakým kódom a sponzorstvom
- V novej škole je aktuálnym žiakom; v histórii trimestrov starej školy naň zostáva
  odkaz [test]

### HK-48 · Zaznačenie platby darcu
Zdroj: 6.6 · Závisí od: HK-22
- Pracovník ADRA zaznačí platbu po mesiacoch, aj viac mesiacov vopred naraz
- Zaznamená sa, kto a kedy platbu potvrdil

### HK-49 · Upozornenie na nepotvrdenú platbu
Zdroj: 6.7 · Závisí od: HK-11A, HK-48
- ADRA dostane upozornenie, keď platba nie je potvrdená 7 dní po splatnosti podľa
  splátkového kalendára, aj keď darca nezaplatil ani prvú platbu [test]

### HK-50 · E-mail darcovi o nezaplatenej platbe
Zdroj: 6.8 · Závisí od: HK-49, HK-11
- Z upozornenia sa dá jedným krokom poslať darcovi e-mail zo šablóny

### HK-51 · Prehľad platieb školám
Zdroj: 6.9, 6.12 · Závisí od: HK-45
- Prehľad, koľko treba za trimester poslať ktorej škole
- Prehľad je označený ako prevádzkový *(invariant 9)*

### HK-52 · Prehľad rozdielov a meškaní
Zdroj: 6.10, 6.12 · Závisí od: HK-48, HK-51
- ADRA vidí, kde darca platí menej, než ADRA posiela škole, a kto mešká s platbou
- Prehľad vidí len ADRA [test] *(invariant 6)*; je označený ako prevádzkový

### HK-53 · Vrátenie dieťaťa do ponuky
Zdroj: 6.11 · Závisí od: HK-45
- O vrátení rozhoduje ADRA, nikdy automat
- Škola zmenu uvidí až v ďalšom otvorenom trimestri [test]

---

## Oblasť 8 — Formulár a prehľady pre školy (Epik 7)

### HK-54 · Formulár dieťaťa pre školu
Zdroj: 7.1, 7.2 · Závisí od: HK-15, HK-31
- Formulár sa dá dokončiť od šírky 360 px bez horizontálneho posúvania a všetky ovládacie
  prvky sú dostupné klávesnicou
- Validácia pri zadaní: chýbajúce povinné polia neprejdú
- Výsledkom je podklad vo fronte [test] (O4)

### HK-55 · Kópia formulára pre súrodenca
Zdroj: 7.6 · Závisí od: HK-54, HK-19
- Formulár sa dá skopírovať pre súrodenca a zmeniť v ňom len to, čo sa líši

### HK-56 · Prehľad pre školu
Zdroj: 7.5 · Závisí od: HK-15, HK-45
- Aktuálni žiaci, história trimestrov (len na čítanie) a aktuálny otvorený trimester:
  ktoré deti majú darcu a koľko za ne škola dostane
- Bez údajov o darcovi a jeho platbách [test] *(invariant 5)*

### HK-57 · Upload reportov školou
Zdroj: 7.3 · Závisí od: HK-10, HK-15, HK-45
- Škola nahrá vysvedčenie (raz na konci trimestra) a fotky (kedykoľvek) k dieťaťu
- Nahraté reporty čakajú na schválenie ADRA

### HK-58 · Schválenie reportu
Zdroj: 7.8 · Závisí od: HK-57
- ADRA môže upraviť názov a popis reportu alebo súbor nahradiť; pôvodná verzia zostáva
  dohľadateľná. Editor PDF ani fotografií v prehliadači nie je súčasťou ticketu
- ADRA musí report schváliť
- Darca vidí len schválené reporty [test] *(invariant 11)*

### HK-59 · Upozornenie škole na chýbajúci report
Zdroj: 7.7 · Závisí od: HK-45A, HK-57, HK-11
- Pri uzavretí trimestra dostane škola e-mail so zoznamom detí, ku ktorým za trimester
  nenahrala vysvedčenie ani fotky [test]

---

## Oblasť 9 — Darcovský portál (Epik 8)

### HK-60 · Karta dieťaťa pre darcu
Zdroj: 8.1, 8.2 · Závisí od: HK-41, HK-58
- Darca vidí karty detí, ktoré podporuje: údaje, príbeh a schválené vysvedčenia,
  hodnotenia a fotky po trimestroch

### HK-61 · Prehľad vlastných platieb
Zdroj: 8.3 · Závisí od: HK-48, HK-60
- Darca vidí svoje potvrdené aj očakávané platby

### HK-62 · Upozornenie na nový report
Zdroj: 8.4 · Závisí od: HK-58, HK-11
- Keď ADRA schváli nové vysvedčenie alebo fotky, darca dostane upozornenie

### HK-63 · Odchod dieťaťa z programu
Zdroj: 8.5 · Závisí od: HK-18, HK-11
- Keď dieťa odíde z programu alebo dokončí stupeň, darca dostane upozornenie s návrhom
  iných detí z ponuky

---

## Oblasť 10 — Odovzdanie

### HK-64 · Kópia zálohy mimo hostingu · `⨯ F4`
Zdroj: 9.3 · Závisí od: HK-05
- Kópia záloh je na účte vo vlastníctve ADRA, mimo hostingu
- Hneď ako PO dodá odpoveď na F4, tento ticket ide navrch

### HK-65 · Dokumentácia a zaškolenie
Zdroj: 9.4 · Závisí od: HK-24 a všetky položky zahrnuté do odovzdávanej verzie
- Dokumentácia pre ADRA: používanie, prevádzka, obnova
- Zaškolený aspoň jeden admin a jeden pracovník
- Zopakovaná skúška obnovy (HK-24) na aktuálnej verzii

### HK-66 · Read-only import historických sponzorstiev · nice-to-have · `⨯ A2`
Zdroj: 4.5 · Závisí od: HK-35
- Historické sponzorstvo sa importuje ako záznam len na čítanie
- Import nezmení aktuálny stav dieťaťa, nevytvorí očakávané platby a nezaradí dieťa do
  otvoreného trimestra [test]
- Po importe je vidieť odmietnuté riadky a dôvod odmietnutia

---

## Orientačný release forecast

Toto nie je rozdelenie do sprintov. Je to poradie výsledkov, ktoré chce PO dostať do
produkčne použiteľného stavu. Konkrétny obsah a počet sprintov vzniknú až po refinemente
a odhadoch tímu.

| Poradie | Produktový prírastok | Kandidátske oblasti |
|---|---|---|
| 1 | ADRA spracuje podklad do schváleného záznamu dieťaťa | Položky v tabuľke „Kandidátske položky prírastku 1“ |
| 2 | ADRA pripraví profil na vloženie do WordPressu | HK-37 + nevyhnutné závislosti |
| 3 | Darca rezervuje dieťa a dostane zmluvu | Oblasti 3 a 6 + darca a sponzorstvo z oblasti 2 |
| 4 | Trimestre, platby a finančné rozdiely | Oblasť 7 |
| 5 | Samoobsluha škôl a darcov | Oblasti 8 a 9 |
| pred prvým produkčným použitím | Zálohy a vyskúšaná obnova | HK-05, HK-24, HK-64 |
| na konci | Dokumentácia a prevzatie | HK-65 |

**Kritická cesta:** rezerváciu možno vyvíjať s provizórnou šablónou, ale bez A1 sa nedá
pustiť do produkcie, pretože produkčné dokončenie HK-39 vyžaduje HK-28. A1 zahŕňa aj
šablóny dodatkov pre HK-27. Tickety blokované A2 (HK-35, HK-36, HK-66) a F4 (HK-64) sa
zoradia hneď, ako príde odpoveď a prejdú refinementom.

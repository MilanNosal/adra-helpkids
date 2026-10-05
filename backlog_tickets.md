# HELPKIDS — tickety

Rozpad `BACKLOG.md` na tickety. Každý ticket musí spĺňať Definition of Done z `BACKLOG.md`.

- `⨯ A1` — blokované, čaká na odpoveď s daným ID v `OTAZKY-PRE-ADRA.md`
- `[test]` — vyžaduje automatizovaný test
- Doménové tickety začínajú vetou „kto a prečo“; technické ju nemajú.
- Ticket je pripravený do sprintu, keď má jasné kritériá, žiadny blocker a zmestí sa do sprintu.

## Poradie

1. **Podklad → schválený záznam dieťaťa:** HK-01, 02, 03, 04, 06 (len roly ADRA), 08,
   09 (len dotknuté polia), 10, 12 (bez programov a bankového spojenia), 16, 17,
   18 (len stav „schválené“), 31, 32, 33, 23 (len školy, podklady, deti)
2. **Export profilu do WordPressu:** HK-37 + závislosti
3. **Rezervácia a zmluva darcu:** oblasti 3 a 6, darca a sponzorstvo z oblasti 2.
   Do produkcie treba A1.
4. **Trimestre a platby:** oblasť 7
5. **Samoobsluha škôl a darcov:** oblasti 8 a 9
- **Pred prvým produkčným použitím:** HK-05, HK-24, HK-64
- **Na konci:** HK-65

---

## 0 — Nasadenie

### HK-01 Kostra aplikácie a CI
- Testy bežia automaticky pri každej zmene
- Texty idú cez prekladový mechanizmus, nie napevno; prvý jazyk je angličtina

### HK-02 Hosting, testovacie a produkčné prostredie
Závisí od: HK-01
- Hosting, doména a úložisko sú na organizačnom účte ADRA
- Produkcia beží cez HTTPS, testovacie prostredie je oddelené
- Databáza, úložisko a tajomstvá sa nastavujú cez premenné prostredia

### HK-03 Automatizované nasadenie
Závisí od: HK-02
- Na test sa nasadzuje automaticky, na produkciu jedným krokom
- V repozitári je postup nasadenia od nuly

### HK-04 Limity hostingu
Závisí od: HK-02
- Zápis v repozitári: limit súborov (inodov), cron a jeho minimálny interval, odchádzajúce
  spojenia, odosielanie e-mailov, knižnice na obrázky a PDF, `max_execution_time`, limit
  uploadu
- Test objemu pre 50 škôl a 5 000 detí vrátane počtu a veľkosti súborov

### HK-05 Denná záloha
Závisí od: HK-02
- Databáza aj súbory sa zálohujú denne a automaticky

---

## 1 — Prístup, audit, súbory, e-maily

### HK-06 Prihlásenie a roly
Ako používateľ sa chcem prihlásiť a vidieť len to, čo patrí mojej role.

Závisí od: HK-01
- Roly: admin ADRA, pracovník ADRA, škola, darca. Admin môže to isté čo pracovník
  a navyše spravuje účty
- Oprávnenia sa kontrolujú na serveri [test]
- Škola A nevidí záznamy ani súbory školy B [test]
- Darca A nevidí deti ani súbory darcu B [test]

### HK-07 Správa účtov
Ako admin ADRA chcem spravovať účty, aby k systému mali prístup len správni ľudia.

Závisí od: HK-06
- Admin zakladá účty ADRA, mení rolu a deaktivuje ľubovoľný účet; pracovník nie [test]
- Deaktivovaný účet sa neprihlási a jeho relácie skončia [test]
- Deaktivácia nemení dáta (deti, podklady, sponzorstvá, história) [test]

### HK-08 2FA pre ADRA
Ako ADRA chcem druhý faktor pri prihlásení, aby sa k údajom detí nedostal nikto s ukradnutým heslom.

Závisí od: HK-06
- Admin aj pracovník ADRA sa bez druhého faktora neprihlásia [test]; škola a darca 2FA nemajú
- Stratený druhý faktor resetuje admin, nie e-mail [test]
- Postup obnovy, keď 2FA stratí jediný admin

### HK-09 Audit citlivých polí
Závisí od: HK-06
- Zapisuje sa kto, kedy, z čoho na čo
- Audit sa nedá prepísať ani zmazať [test]
- Rozsah polí podľa DoD 5 v `BACKLOG.md`

### HK-10 Súbory s kontrolou prístupu
Závisí od: HK-04, HK-06
- Súbor sa stiahne len s oprávnením [test]
- Adresa súboru sa nedá uhádnuť ani odvodiť z ID dieťaťa [test]
- Pri uploade sa kontroluje typ súboru [test]; súbory sa nedajú spustiť
- Prejde testom objemu z HK-04 [test]
- Verejné sú len kópie fotiek v exporte (HK-37)

### HK-11 E-maily zo šablón
Závisí od: HK-04
- E-mail sa posiela zo šablóny s doplnenými údajmi, cez prekladový mechanizmus
- Pri každom e-maile sa eviduje príjemca, šablóna, čas a výsledok

### HK-11A Časované udalosti
Závisí od: HK-11
- Splatné udalosti sa spracujú bez toho, aby niekto otvoril aplikáciu [test]
- Ani pri opakovanom spracovaní nevznikne duplicitná zmena ani e-mail [test]
- Chyba sa zaznamená a spracovanie sa dá zopakovať

### HK-20A Obnova hesla
Ako používateľ chcem obnoviť zabudnuté heslo bez pomoci ADRA.

Závisí od: HK-06, HK-11
- Systém neprezradí, či e-mail existuje [test]
- Odkaz je jednorazový a s nastaviteľnou platnosťou [test]
- Po zmene hesla skončia všetky relácie [test]

---

## 2 — Škola, dieťa, darca

### HK-12 Škola
Ako pracovník ADRA chcem evidovať školy, ku ktorým deti patria.

Závisí od: HK-06
- Názov, sídlo, korešpondenčná adresa, popis situácie, kontaktná osoba

### HK-12A Údaje ADRA
Ako admin ADRA chcem mať údaje organizácie na jednom mieste, aby sa v zmluvách nemuseli prepisovať.

Závisí od: HK-06, HK-09
- Názov, IČO, štatutár, sídlo, korešpondenčná adresa, IBAN, kontakt; berú sa odtiaľto
  do zmlúv
- Zmena ide do histórie a nemení už vygenerované zmluvy [test]

### HK-13 Programy a cenník
Ako pracovník ADRA chcem evidovať programy škôl a ich ceny, aby sa z nich počítala suma pre darcu.

Závisí od: HK-12
- Program = škola + rozsah (strava / školné / školné + strava / + internát) + cena za
  trimester v €
- Mesačná suma = 3 × cena za trimester / 12 [test]
- Zmena cenníka nemení sumu existujúcich darcov [test]

### HK-14 Bankové spojenie školy
Ako pracovník ADRA chcem viesť bankové spojenie školy, aby peniaze išli na správny účet.

Závisí od: HK-09, HK-10, HK-12
- Mení ho len ADRA [test] a pri zmene priloží dodatok
- História sa dá len dopĺňať [test]

### HK-15 Pozvanie školy
Ako pracovník ADRA chcem pozvať školu do systému, aby si údaje zadávala sama.

Závisí od: HK-11, HK-12
- ADRA pozve školu e-mailom; škola si doplní údaje a nastaví prístup
- Pozvánka je jednorazová a s nastaviteľnou platnosťou [test]
- Škola môže mať viac používateľov a všetci vidia to isté (predpoklad)
- Verejná registrácia škôl neexistuje [test]

### HK-16 Záznam dieťaťa
Ako pracovník ADRA chcem mať všetky údaje o dieťati v jednom zázname namiesto Wordov a Excelov.

Závisí od: HK-10, HK-12
- Polia podľa `Formulár dieťaťa.docx`: osobné údaje, rodina, kto sa stará, bývanie,
  pôvod, príbeh, financie, typ podpory, fotky, dátumy (vyplnenie, zverejnenie, začiatok
  podpory)
- Bez sekcie „Osobné súhlasy“
- Pri každej fotke sa dá nastaviť, či smie ísť do exportu
- Dieťa patrí aktuálnej škole
- Záznam vzniká len schválením podkladu (HK-33)

### HK-17 Kód dieťaťa
Ako pracovník ADRA chcem, aby každé dieťa malo jedinečný kód, podľa ktorého ho dohľadám.

Závisí od: HK-16
- Kód generuje systém, je jedinečný a nemenný [test]

### HK-18 Stav dieťaťa
Ako pracovník ADRA chcem vidieť, v akom stave je dieťa, od schválenia po ukončenie podpory.

Závisí od: HK-16
- Stavy: schválené → zverejnené → rezervované → podporované → ukončené
- Nepovolený prechod systém odmietne [test]

### HK-19 Súrodenci
Ako pracovník ADRA chcem vidieť súrodencov dieťaťa, aby sa dali ponúknuť spolu.

Závisí od: HK-16
- Deti sa dajú prepojiť ako súrodenci a pri dieťati vidno jeho súrodencov

### HK-20 Darca
Ako darca chcem mať účet so svojimi údajmi a deťmi, ktoré podporujem.

Závisí od: HK-06
- Kontaktné a fakturačné údaje, trvalý pobyt alebo sídlo, korešpondenčná adresa, účet
  s heslom
- Vidí len deti s aktívnym sponzorstvom; po ukončení stratí prístup ku karte dieťaťa,
  svoje platby vidí naďalej [test] (predpoklad)

### HK-21 Sponzorstvo
Ako pracovník ADRA chcem evidovať, ktorý darca podporuje ktoré dieťa a akou sumou.

Závisí od: HK-13, HK-16, HK-20
- Dieťa má najviac jedného darcu, darca môže mať viac detí [test]
- Mesačná suma, periodicita (mesačne / štvrťročne / polročne / ročne), stav (čaká na
  schválenie → aktívne → ukončené)
- Škola nevidí darcu ani jeho platby [test]

### HK-22 Splátkový kalendár
Ako pracovník ADRA chcem vedieť, kedy má darca zaplatiť.

Závisí od: HK-21
- Počíta sa od schválenia zmluvy podľa periodicity [test]

### HK-23 Testovacie dáta
Závisí od: HK-12, HK-16; rozširuje sa s modelom
- Jedným príkazom sa vytvoria vymyslené školy, deti, darcovia a fotky

### HK-24 Skúška obnovy
Závisí od: HK-05, HK-23
- Databáza a súbory sa obnovia zo zálohy na čistom stroji a aplikácia na nich beží
- Postup je v repozitári

---

## 3 — Zmluvy

### HK-25 Generovanie PDF zo šablóny
Závisí od: HK-10, HK-21
- PDF vznikne zo šablóny (zatiaľ provizórnej) a údajov v systéme
- Používajú sa len schválené dáta, nikdy podklad [test]
- PDF sa uloží a dá sa znovu stiahnuť; jazyk určuje šablóna

### HK-26 Stav zmluvy a podpísaný sken
Ako pracovník ADRA chcem vedieť, či je zmluva podpísaná, a mať pri nej podpísaný sken.

Závisí od: HK-25
- Stav vygenerovaná → podpísaná, s dátumom; k zmluve sa dá nahrať podpísaný sken

### HK-27 Dodatky · `⨯ A1`
Ako pracovník ADRA chcem vygenerovať dodatok, keď sa zmení suma, periodicita alebo účet školy.

Závisí od: HK-14, HK-25
- Dodatky pre zmenu sumy darcu, periodicity a bankového spojenia školy
- Suma darcu sa mení len dodatkom z rozhodnutia ADRA, nikdy automaticky [test]
- Dodatok prepočíta splátkový kalendár

### HK-28 Zmluva ADRA–darca · `⨯ A1`
Ako darca chcem dostať zmluvu s ADRA so sumou a splátkovým kalendárom.

Závisí od: HK-12A, HK-25
- Zmluva na neurčito s mesačnou výpovednou lehotou a splátkovým kalendárom
- Suma je cena programu v čase vzniku rezervácie a zmena cenníka ju nemení [test]

### HK-29 Zmluva ADRA–škola · `⨯ A1`
Ako pracovník ADRA chcem vygenerovať zmluvu so školou bez ručného prepisovania.

Závisí od: HK-12A, HK-13, HK-14, HK-25
- Vzniká z údajov školy, programov a bankového spojenia; ukladá sa pri škole
- Zmena údajov školy nezmení už vygenerované PDF [test]

### HK-30 Zmluva škola–opatrovník · `⨯ A1`
Ako škola chcem stiahnuť zmluvu s opatrovníkom a nahrať ju podpísanú.

Závisí od: HK-15, HK-25, HK-26
- Vzniká zo schválených údajov dieťaťa, opatrovníka a školy
- Škola zmluvu stiahne a nahrá podpísanú; uložené zostanú obe verzie

---

## 4 — Podklady

### HK-31 Podklad
Ako pracovník ADRA chcem zadať údaje o novom dieťati ako podklad, ktorý pred zápisom skontrolujem.

Závisí od: HK-10, HK-12
- Stavy: odoslaný → vo spracovaní → vrátený na doplnenie → schválený
- Podklad za školu zadáva pracovník ADRA (prvý vstupný kanál)
- Škola nikdy nezapisuje priamo do záznamu dieťaťa [test]

### HK-32 Fronta podkladov
Ako pracovník ADRA chcem vidieť všetky podklady, ktoré čakajú na spracovanie, a ako dlho čakajú.

Závisí od: HK-31
- Podklady v stave odoslaný alebo vrátený, so školou, dátumom odoslania a počtom dní
  čakania
- Do fronty prichádzajú podklady zo všetkých zdrojov

### HK-33 Úprava a schválenie podkladu
Ako pracovník ADRA chcem podklad upraviť a schváliť, aby z neho vznikol záznam dieťaťa.

Závisí od: HK-16, HK-17, HK-32
- Pred schválením sa dá upraviť príbeh, fotky aj vysvedčenia
- Schválením sa vytvorí alebo aktualizuje záznam dieťaťa
- Pôvodný podklad zostane nezmenený [test]

### HK-34 Vrátenie na doplnenie
Ako pracovník ADRA chcem vrátiť neúplný podklad škole, aby ho doplnila.

Závisí od: HK-15, HK-32, HK-54
- Podklad sa vráti škole s poznámkou, škola ho doplní

---

## 5 — Import z Excelov · `⨯ A2`

### HK-35 Import zoznamu detí · `⨯ A2`
Ako pracovník ADRA chcem naimportovať deti z dnešných Excelov, aby som ich nemusel zadávať ručne.

Závisí od: HK-32
- Nastaviteľné mapovanie stĺpcov, tolerancia nekonzistentných dát
- Import vytvára podklady vo fronte, nie záznamy detí [test]

### HK-36 Report z importu · `⨯ A2`
Ako pracovník ADRA chcem vidieť, čo sa pri importe nepodarilo a prečo.

Závisí od: HK-35
- Ukáže, ktoré riadky sa nenaimportovali a prečo

---

## 6 — Export a rezervácia

### HK-37 Export profilu pre WordPress
Ako pracovník ADRA chcem vygenerovať profil dieťaťa, ktorý len vložím do WordPressu.

Závisí od: HK-13, HK-16
- HTML/Markdown + fotky povolené na zverejnenie + odkaz na sponzorský formulár s ID dieťaťa
- Pri zmene sa dá vygenerovať znovu
- Bez presnej adresy a plného mena opatrovníka [test]
- Bez stavu dostupnosti dieťaťa
- Bez nepovolených fotiek, reportov a zmlúv [test]

### HK-38 Sponzorský formulár
Ako darca chcem z profilu na webe vyplniť formulár a prejaviť záujem o dieťa.

Závisí od: HK-11, HK-20, HK-37
- Nový darca si založí účet, existujúci sa prihlási
- E-mail darcu je jedinečný [test]
- Rezervácia vznikne až po potvrdení e-mailu, dovtedy je dieťa voľné [test] (predpoklad)
- Limit pokusov je nastaviteľný, predvolene 5 za hodinu na IP alebo e-mail [test]
- Pred odoslaním formulára neprezradí, či je dieťa voľné

### HK-39 Rezervácia
Ako darca chcem si dieťa rezervovať, aby mi ho nikto nevzal, kým podpíšem zmluvu.

Závisí od: HK-11A, HK-18, HK-25, HK-38
- Dieťa má najviac jednu aktívnu rezerváciu, aj pri súbežných formulároch [test]
- Rezervácia trvá 7 kalendárnych dní, potom sa dieťa samo uvoľní [test]
- Pri rezervácii sa hneď vygeneruje zmluva ADRA–darca na stiahnutie [test]
- Do produkcie treba HK-28

### HK-40 Darca nahrá podpísanú zmluvu
Ako darca chcem nahrať podpísanú zmluvu, aby rezervácia nevypršala.

Závisí od: HK-11A, HK-26, HK-39
- Nahratím v lehote sa lehota zastaví [test]
- Potom rezerváciu zruší už len ADRA alebo darca zrušením zmluvy [test]
- Zmluva čaká vo fronte ADRA; ak ju ADRA do 3 dní neposúdi, príde upozornenie. Dieťa sa
  samo neuvoľní [test]

### HK-41 Schválenie / odmietnutie zmluvy
Ako pracovník ADRA chcem zmluvu schváliť alebo odmietnuť, aby sa sponzorstvo spustilo alebo dieťa uvoľnilo.

Závisí od: HK-11, HK-22, HK-40
- Schválenie: sponzorstvo sa aktivuje, začne splátkový kalendár a darca uvidí kartu dieťaťa
- Odmietnutie: rezervácia sa zruší, dieťa sa vráti do ponuky a darca dostane e-mail [test]

### HK-42 E-mail po vypršaní rezervácie
Ako darca chcem vedieť, že mi rezervácia vypršala.

Závisí od: HK-11A, HK-39
- Darca dostane e-mail

### HK-43 Rezervácia súrodencov naraz
Ako darca chcem podporiť súrodencov naraz, bez opakovania formulára.

Závisí od: HK-19, HK-39
- Jedným krokom sa rezervujú všetci voľní súrodenci
- Každé dieťa má vlastnú rezerváciu, sponzorstvo a zmluvu [test]

### HK-44 Zoznam úprav vo WordPresse
Ako pracovník ADRA chcem vedieť, ktoré profily vo WordPresse treba upraviť.

Závisí od: HK-41
- Zoznam detí, ktorým treba upraviť profil vo WordPresse (napr. získali podporu);
  položky sa odškrtávajú

---

## 7 — Trimestre a platby

### HK-45 Otvorenie trimestra
Ako pracovník ADRA chcem otvoriť trimester a určiť, za ktoré deti zaplatíme školám.

Závisí od: HK-21
- Pracovník ADRA otvorí trimester s označením `ROK/mesiac`, ktoré je jedinečné [test]
- Systém pre každú školu navrhne deti s aktívnym sponzorstvom; rezervácia ani nahratá
  zmluva nestačí [test]
- Pred otvorením sa dá dieťa vyradiť alebo pridať dieťa bez darcu (platí ADRA). Kto dieťa
  financuje, vidí len ADRA [test]
- Otvorením sa zoznam zmrazí a ADRA zaplatí škole celý trimester [test]
- Darca získaný po otvorení sa ráta až od ďalšieho trimestra [test]

### HK-45A Uzavretie trimestra
Ako pracovník ADRA chcem trimester uzavrieť, aby sa dal otvoriť ďalší.

Závisí od: HK-45
- Trimester ručne uzatvára pracovník ADRA; otvorený je najviac jeden [test]
- Uzavretie nemení zoznam ani platbu

### HK-46 Oprava zoznamu trimestra
Ako pracovník ADRA chcem opraviť chybu v zozname otvoreného trimestra.

Závisí od: HK-09, HK-45
- Zoznam otvoreného trimestra sa dá opraviť; oprava ide do histórie

### HK-47 Prestup do inej školy
Ako pracovník ADRA chcem zaznamenať prestup dieťaťa bez straty jeho histórie a darcu.

Závisí od: HK-45
- Dieťa si ponechá kód aj sponzorstvo
- V novej škole je aktuálnym žiakom a v histórii starej školy zostane [test]

### HK-48 Zaznačenie platby darcu
Ako pracovník ADRA chcem zaznačiť prijatú platbu od darcu.

Závisí od: HK-22
- Platby sa zaznačujú po mesiacoch, aj viac mesiacov naraz
- Eviduje sa, kto a kedy platbu potvrdil

### HK-49 Upozornenie na nepotvrdenú platbu
Ako pracovník ADRA chcem vedieť, kto nezaplatil načas.

Závisí od: HK-11A, HK-48
- ADRA dostane upozornenie 7 dní po splatnosti, aj keď darca nezaplatil ani prvú platbu
  [test]

### HK-50 E-mail darcovi o nezaplatení
Ako pracovník ADRA chcem jedným krokom pripomenúť darcovi nezaplatenú platbu.

Závisí od: HK-11, HK-49
- Z upozornenia sa jedným krokom pošle e-mail zo šablóny

### HK-51 Prehľad platieb školám
Ako pracovník ADRA chcem vedieť, koľko mám poslať ktorej škole.

Závisí od: HK-13, HK-45
- Suma, ktorú treba za trimester poslať každej škole; označené ako prevádzkový prehľad

### HK-52 Rozdiely a meškania
Ako pracovník ADRA chcem vidieť, kde ADRA dopláca a kto mešká s platbou.

Závisí od: HK-48, HK-51
- Ukazuje, kde darca platí menej, než ADRA posiela škole, a kto mešká
- Vidí to len ADRA [test]; označené ako prevádzkový prehľad

### HK-53 Vrátenie dieťaťa do ponuky
Ako pracovník ADRA chcem vrátiť dieťa do ponuky, keď stratí darcu.

Závisí od: HK-45
- Rozhoduje ADRA, nikdy automat
- Škola zmenu uvidí až v ďalšom trimestri [test]

---

## 8 — Školy

### HK-54 Formulár dieťaťa pre školu
Ako škola chcem zadať nové dieťa cez formulár, aj z mobilu.

Závisí od: HK-15, HK-31
- Dá sa vyplniť od šírky 360 px bez horizontálneho posúvania a ovládať klávesnicou
- Bez povinných polí sa neodošle
- Vytvorí podklad vo fronte [test]

### HK-55 Kópia formulára pre súrodenca
Ako škola chcem pri súrodencovi nevypĺňať všetko znova.

Závisí od: HK-19, HK-54
- Formulár sa skopíruje a upraví sa len to, čo sa líši

### HK-56 Prehľad pre školu
Ako škola chcem vidieť svojich žiakov v programe a koľko za nich dostanem.

Závisí od: HK-13, HK-15, HK-45
- Aktuálni žiaci, história trimestrov (len na čítanie), otvorený trimester: ktoré deti majú
  darcu a koľko za ne škola dostane
- Bez údajov o darcoch a platbách [test]

### HK-57 Reporty od školy
Ako škola chcem nahrať vysvedčenia a fotky detí.

Závisí od: HK-10, HK-15, HK-45
- Škola nahráva vysvedčenie na konci trimestra a fotky kedykoľvek
- Reporty čakajú na schválenie ADRA

### HK-58 Schválenie reportu
Ako pracovník ADRA chcem report pred zverejnením darcovi skontrolovať.

Závisí od: HK-57
- ADRA môže upraviť názov a popis alebo nahradiť súbor; pôvodná verzia zostane. Editor PDF
  ani fotiek nie je súčasťou
- Darca vidí len schválené reporty [test]

### HK-59 Upozornenie na chýbajúci report
Ako škola chcem vedieť, ku ktorým deťom mi chýba report.

Závisí od: HK-11, HK-45A, HK-57
- Pri uzavretí trimestra dostane škola e-mail so zoznamom detí bez vysvedčenia alebo fotiek
  [test]

---

## 9 — Darcovia

### HK-60 Karta dieťaťa pre darcu
Ako darca chcem vidieť, ako sa darí dieťaťu, ktoré podporujem.

Závisí od: HK-41, HK-58
- Údaje, príbeh a schválené vysvedčenia, hodnotenia a fotky po trimestroch

### HK-61 Platby darcu
Ako darca chcem vidieť, čo som zaplatil a čo ma čaká.

Závisí od: HK-48, HK-60
- Darca vidí potvrdené aj očakávané platby

### HK-62 Upozornenie na nový report
Ako darca chcem vedieť, keď pribudne nové vysvedčenie alebo fotky.

Závisí od: HK-11, HK-58
- Darca dostane upozornenie po schválení nového reportu

### HK-63 Odchod dieťaťa z programu
Ako darca chcem vedieť, že dieťa odišlo z programu, a dostať návrh iného dieťaťa.

Závisí od: HK-11, HK-18, HK-21, HK-37
- Darca dostane upozornenie s návrhom iných detí z ponuky

---

## 10 — Odovzdanie

### HK-64 Záloha mimo hostingu · `⨯ F4`
Ako ADRA chcem mať zálohy aj mimo hostingu, aby sme o dáta neprišli pri výpadku poskytovateľa.

Závisí od: HK-05
- Kópia záloh je na účte ADRA mimo hostingu

### HK-65 Dokumentácia a zaškolenie
Ako ADRA chceme vedieť systém používať a prevádzkovať bez dodávateľa.

Závisí od: HK-24 a všetky odovzdávané tickety
- Dokumentácia: používanie, prevádzka, obnova
- Zaškolený aspoň jeden admin a jeden pracovník
- Skúška obnovy (HK-24) zopakovaná na aktuálnej verzii

### HK-66 Import historických sponzorstiev · nice-to-have · `⨯ A2`
Ako pracovník ADRA chcem vidieť históriu sponzorstiev z obdobia pred systémom.

Závisí od: HK-35
- Historické sponzorstvá sú len na čítanie
- Import nezmení stav dieťaťa, nevytvorí očakávané platby a nezaradí dieťa do trimestra
  [test]
- Ukáže odmietnuté riadky a dôvod

# HELPKIDS — backlog

Tickety sú zoradené podľa priority a v tomto poradí sa realizujú. Každý ticket sa nabaľuje
na predchádzajúce. Doména, pravidlá a Definition of Done sú v `DOMENOVY-NAVRH.md`, dôvody
poradia v `notes.md`. Značka `⨯ X` znamená, že ticket čaká na odpoveď X z
`OTAZKY-PRE-ADRA.md`.

---

## Infraštruktúra

**HK-01 Kostra aplikácie a CI.** Testy bežia automaticky pri každej zmene. Texty idú cez
prekladový mechanizmus, prvý jazyk je angličtina.

**HK-02 Hosting, testovacie a produkčné prostredie.** Produkcia beží cez HTTPS, testovacie
prostredie je oddelené. Konfigurácia ide cez premenné prostredia. Hosting, doména a
úložisko sú na organizačnom účte ADRA.

**HK-03 Automatizované nasadenie.** Na test sa nasadzuje automaticky, na produkciu jedným
krokom. Postup nasadenia od nuly je v repozitári.

**HK-04 Limity hostingu.** Zápis v repozitári: limit súborov (inodov), cron a jeho
interval, odchádzajúce spojenia, odosielanie e-mailov, knižnice na obrázky a PDF,
`max_execution_time`, limit uploadu. Test objemu 50 škôl a 5 000 detí.

**HK-05 Denná záloha.** Databáza aj súbory sa zálohujú denne a automaticky.

**HK-06 Skúška obnovy.** Záloha je aspoň raz obnovená na čistom stroji podľa napísaného
postupu.

**HK-07 Kópia zálohy mimo hostingu** · `⨯ F4`. Kópia leží na účte vo vlastníctve ADRA.

**HK-08 Audit citlivých polí.** Zmeny sa zapisujú (kto, kedy, z čoho na čo) a z aplikácie
sa nedajú prepísať ani zmazať.

**HK-09 E-maily zo šablón.** Systém posiela e-maily zo šablón a eviduje príjemcu, šablónu,
čas a výsledok.

**HK-10 Časované úlohy.** Splatné udalosti (expirácia, výpoveď) sa spracujú bez toho, aby
niekto otvoril aplikáciu. Opakované spracovanie nevytvorí duplicitu.

**HK-11 Úložisko súborov.** Súbor sa stiahne len s oprávnením, adresa sa nedá uhádnuť, typ
sa pri uploade validuje a súbor sa nedá spustiť.

**HK-12 Testovacie dáta.** Vymyslené školy, deti, darcovia a sponzorstvá na demo a testy;
nikdy produkčné dáta.

---

## Jadro — náhrada Excelu „TABUĽKA management HELPKIDS“

**HK-13 Roly a účty ADRA.** Ako admin ADRA chcem zakladať účty pracovníkov ADRA, meniť im
rolu a deaktivovať ich, aby k dátam mali prístup len správni ľudia. Oprávnenia sa
vynucujú na serveri.

**HK-14 Obnova hesla.** Ako aktivovaný používateľ si chcem obnoviť zabudnuté heslo sám cez
jednorazový odkaz, bez pomoci ADRA.

**HK-15 Škola.** Ako pracovník ADRA chcem založiť školu s adresou, popisom a kontaktnou
osobou, aby som mal všetky partnerské školy na jednom mieste.

**HK-16 Programy a ceny školy.** Ako pracovník ADRA chcem pri škole viesť programy (strava,
školné + strava, internát…) s cenou a obdobím jej platnosti, aby bolo vidieť aktuálnu
cenu aj to, aká platila kedykoľvek v minulosti.

**HK-17 Bankové spojenie školy.** Ako pracovník ADRA chcem zadať a meniť bankové spojenie
školy. Každá zmena sa zapíše do histórie, ktorú nikto nevie prepísať, a škola ho sama
zmeniť nevie.

**HK-18 Záznam dieťaťa.** Ako pracovník ADRA chcem založiť dieťa so všetkými údajmi z
formulára dieťaťa vrátane príbehu a opatrovníka, aby som ho už neviedol v Exceli. Kód
dieťaťa prideľuje systém a je nemenný.

**HK-19 História škôl dieťaťa.** Ako pracovník ADRA chcem pri dieťati zaznamenať, na ktoré
školy a v akom období chodilo, vrátane historických záznamov.

**HK-20 Darca.** Ako pracovník ADRA chcem založiť darcu s kontaktnými údajmi. Vznikne
neaktivovaný účet s náhodným heslom, ktoré nikto nevidí, a darca sa zatiaľ neprihlási.

**HK-21 Sponzorstvo.** Ako pracovník ADRA chcem zaznamenať, že darca podporuje jedno alebo
viac detí, s mesačnou sumou, obdobím a číslom zmluvy, aby som videl, kto koho podporuje.
Darca môže mať viac sponzorstiev, dieťa má v danom čase najviac jedného darcu.

**HK-22 História podpory dieťaťa.** Ako pracovník ADRA chcem pri dieťati vidieť, kto ho kedy
a za koľko podporoval, vrátane historických záznamov zadaných ručne.

**HK-23 Prehľad detí.** Ako pracovník ADRA chcem zoznam všetkých detí so školou, programom,
cenou, aktuálnym darcom a stavom (voľné / rezervované / podporované), s filtrom a
vyhľadávaním, aby som nahradil hárok „Prehľad detí“.

**HK-24 Splátkový kalendár.** Ako pracovník ADRA chcem pri sponzorstve nastaviť
periodicitu platieb (mesačne / štvrťročne / polročne / ročne) a dátum prvej platby, aby
systém vedel, kedy má darca platiť.

**HK-25 Zaznačenie platby.** Ako pracovník ADRA chcem pri darcovi vyklikať potvrdenie
prijatej platby za jedno alebo viac období naraz.

**HK-26 Prehľad nezaplatených platieb.** Ako pracovník ADRA chcem vidieť, ktorí darcovia
podľa splátkového kalendára niečo nezaplatili a odkedy.

**HK-27 Pozvanie darcu.** Ako pracovník ADRA chcem darcu pozvať do systému: systém mu
vygeneruje nové heslo a pošle ho e-mailom, pričom ho nikto v ADRA nevidí. Prvým
prihlásením sa účet aktivuje. Odvtedy heslo vie pregenerovať už len admin.

---

## Samoobsluha škôl

**HK-28 Účet školy vytvorený ADRA.** Ako pracovník ADRA chcem škole vytvoriť účet a pozvať
ju rovnako ako darcu (HK-20, HK-27).

**HK-29 Registrácia školy.** Ako škola sa chcem zaregistrovať sama cez verejný formulár s
captchou. Kým ma pracovník ADRA nepotvrdí, nemôžem pridávať deti.

**HK-30 Potvrdenie školy.** Ako pracovník ADRA chcem vidieť školy čakajúce na potvrdenie a
potvrdiť alebo zamietnuť ich.

## Samoobsluha darcov

**HK-31 Registrácia darcu.** Ako darca sa chcem zaregistrovať sám cez verejný formulár s
captchou, bez potvrdenia ADRA. E-mail je unikátny a musí byť overený.

## Deti od školy

**HK-32 Škola pridá dieťa.** Ako potvrdená škola chcem pridať dieťa cez formulár dieťaťa.
Dieťa nie je nikde inde vidieť, kým ho ADRA neschváli.

**HK-33 Schválenie dieťaťa.** Ako pracovník ADRA chcem vidieť deti čakajúce na schválenie,
upraviť ich (napr. preformulovať príbeh) a schváliť ich. Škola schválený záznam priamo
nemení.

**HK-34 Vrátenie na doplnenie.** Ako pracovník ADRA chcem dieťa vrátiť škole s poznámkou,
čo chýba. Ako škola chcem vidieť svoje deti a stav ich schválenia.

## Ponuka a rezervácia

**HK-35 Ponuka voľných detí.** Ako darca chcem vidieť schválené deti, ktoré nemajú darcu
ani aktívnu rezerváciu, s príbehom, školou a mesačnou sumou.

**HK-36 Rezervácia.** Ako darca si chcem rezervovať jedno alebo viac detí a zvoliť si
splátkový kalendár. Rezervácia drží dieťa 7 dní, dieťa má najviac jednu rezerváciu naraz a
po vypršaní sa automaticky vráti do ponuky.

**HK-37 Potvrdenie rezervácie.** Ako pracovník ADRA chcem rezerváciu potvrdiť alebo
zamietnuť. Potvrdením vznikne sponzorstvo so splátkovým kalendárom a navrhnutým dátumom
prvej platby.

## Darcovský portál

**HK-38 Moje deti.** Ako darca chcem vidieť deti, ktoré sponzorujem, s ich údajmi a
príbehom.

**HK-39 Moje platby.** Ako darca chcem vidieť svoj splátkový kalendár a potvrdené platby.

**HK-40 Report od školy.** Ako škola chcem k dieťaťu nahrať report (vysvedčenie,
hodnotenie, fotky).

**HK-41 Schválenie reportu.** Ako pracovník ADRA chcem report pred zobrazením darcovi
upraviť alebo nahradiť súbor a schváliť ho. Pôvodná verzia zostáva dohľadateľná.

**HK-42 Reporty pre darcu.** Ako darca chcem vidieť schválené reporty mojich detí z obdobia,
keď som ich sponzoroval.

**HK-43 Výpoveď sponzorstva.** Ako darca chcem ukončiť podporu dieťaťa s výpovednou
lehotou jeden mesiac odo dňa výpovede. Po skončení podpory sa dieťa automaticky vráti do ponuky. Pracovník
ADRA vie výpoveď zadať aj za darcu.

## Fotky a WordPress

**HK-44 Fotky dieťaťa.** Ako pracovník ADRA chcem k dieťaťu nahrať fotky a pri každej
označiť, či smie byť zverejnená.

**HK-45 Export profilu do WordPressu.** Ako pracovník ADRA chcem jedným krokom vygenerovať
profil dieťaťa (text a fotky na zverejnenie) na vloženie do WordPressu, s odkazom na
rezerváciu v systéme. Export sa dá zopakovať a nikdy neobsahuje adresu dieťaťa ani meno
opatrovníka.

---

## Trimestre — náhrada Excelu pre školu

**HK-46 Trimester školy.** Ako pracovník ADRA chcem pre konkrétnu školu začať trimester
nezávisle od ostatných škôl a priradiť doň deti. Systém navrhne všetky deti s aktuálnym
sponzorom, ADRA môže dieťa odobrať alebo pridať.

**HK-47 Krytie ADRA.** Ako pracovník ADRA chcem pri trimestri vidieť, za ktoré deti a
mesiace nie je darca a platí ich ADRA, či už dieťa darcu nemalo, alebo ho stratilo počas
trimestra.

**HK-48 Oprava a uzavretie trimestra.** Ako pracovník ADRA chcem opraviť zoznam detí v
otvorenom trimestri (oprava sa zapíše do histórie) a trimester uzavrieť.

**HK-49 Vyúčtovanie trimestra.** Ako pracovník ADRA chcem vidieť, koľko mám poslať ktorej
škole za trimester a za ktoré deti, aby som nahradil „List Helpkids support for
trimester“.

**HK-50 Trimester pre školu.** Ako škola chcem vidieť svoj aktuálny trimester s
vyúčtovaním a minulé trimestre. Identitu darcov ani ich platby nevidím.

**HK-51 Upomienky.** Ako pracovník ADRA chcem, aby ma systém upozornil na nezaplatenú
platbu, a jedným klikom poslať darcovi upomienku zo šablóny.

---

## Podpísané zmluvy

**HK-52 Zmluvy darcu.** Ako pracovník ADRA chcem k darcovi nahrať podpísanú zmluvu alebo
dodatok a priradiť ich k jeho sponzorstvám, aby som pri každom darcovi videl jeho platné
zmluvy.

**HK-53 Moje zmluvy.** Ako darca chcem v systéme vidieť svoje platné zmluvy a dodatky.

**HK-54 Zmluva pri rezervácii.** Ako darca chcem k rezervácii nahrať podpísanú zmluvu. ADRA
rezerváciu potvrdí až po jej nahratí. Nahratie lehotu rezervácie nezastaví — zastaví ju
len potvrdenie ADRA.

**HK-55 Zmluvy ADRA–škola.** Ako pracovník ADRA chcem ku škole nahrať podpísanú zmluvu a
dodatky. Škola ich vidí tiež.

**HK-56 Zmluvy škola–opatrovník.** Ako škola chcem k dieťaťu nahrať podpísanú zmluvu s
opatrovníkom. Vidí ju škola a ADRA.

---

## Súrodenci, prestup, odchod

**HK-57 Súrodenci.** Ako pracovník ADRA chcem deti prepojiť ako súrodencov, aby bolo pri
dieťati vidieť jeho súrodencov, aj v ponuke pre darcu.

**HK-58 Prestup do inej školy.** Ako pracovník ADRA chcem zaznamenať prestup dieťaťa. Dieťa
zostáva jedno s rovnakým kódom a sponzorstvom a v histórii starej školy naň zostáva odkaz.

**HK-59 Odchod z programu.** Ako pracovník ADRA chcem ukončiť účasť dieťaťa v programe
(dokončilo stupeň, odišlo). Ukončí sa aj jeho sponzorstvo a dieťa sa už neponúka.

---

## Import z Excelov · `⨯ A2`

Import len automaticky vytvára tie isté záznamy, ktoré vie ručne vytvoriť pracovník ADRA.
Ku každému importu patrí prehľad, čo sa nenaimportovalo a prečo.

**HK-60 Import škôl.** Ako pracovník ADRA chcem naimportovať školy a ich programy s cenami
z Excelu.

**HK-61 Import detí.** Ako pracovník ADRA chcem naimportovať deti z Excelu, s mapovaním
stĺpcov.

**HK-62 Import darcov.** Ako pracovník ADRA chcem naimportovať darcov z Excelu ako
neaktivované účty.

**HK-63 Import sponzorstiev.** Ako pracovník ADRA chcem naimportovať sponzorstvá a históriu
podpory z Excelu.

---

## Generovanie zmlúv a notifikácie

**HK-64 Údaje ADRA.** Ako pracovník ADRA chcem v systéme spravovať údaje ADRA (názov, IČO,
štatutár, adresa, IBAN), z ktorých čerpajú šablóny zmlúv.

**HK-65 Generovanie zmluvy ADRA–darca** · `⨯ A1`. Ako darca chcem pri rezervácii hneď
dostať vygenerovanú zmluvu na podpis.

**HK-66 Generovanie zmluvy ADRA–škola** · `⨯ A1`. Ako pracovník ADRA chcem zmluvu so školou
vygenerovať zo šablóny.

**HK-67 Generovanie zmluvy škola–opatrovník** · `⨯ A1`. Ako škola chcem zmluvu s
opatrovníkom vygenerovať zo šablóny.

**HK-68 Generovanie dodatkov** · `⨯ A1`. Ako pracovník ADRA chcem vygenerovať dodatok k
zmluve (zmena sumy, splátkového kalendára, bankového spojenia).

**HK-69 Notifikácie darcovi.** Ako darca chcem dostať e-mail, keď pribudne nový report,
keď vyprší moja rezervácia a keď moje dieťa odíde z programu.

**HK-70 Notifikácie škole a ADRA.** Ako škola chcem upozornenie na chýbajúce reporty za
trimester. Ako pracovník ADRA chcem upozornenie na rezervácie a deti čakajúce na
schválenie.

---

## Na záver

**HK-71 2FA pre ADRA.** Ako ADRA chcem druhý faktor pri prihlásení pracovníkov a adminov.
Stratený faktor resetuje admin.

**HK-72 Dokumentácia a zaškolenie.** Dokumentácia pre ADRA a zaškolenie aspoň jedného
admina a jedného pracovníka.

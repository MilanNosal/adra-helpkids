# Otázky pre ADRA pred začiatkom projektu

Podklad na rozhovor s kontaktnou osobou v ADRA. Cieľ nie je zodpovedať všetko — cieľ je
odblokovať prvé sprinty a vedieť, čo zostáva otvorené.

**Ako to použiť.** Časť A sú veci, ktoré treba fyzicky získať, nie otázky; bez nich tím
premrhá prvý sprint. Časti B–C blokujú dátový model a treba ich uzavrieť pred začiatkom.
Časti D–F môžu dobehnúť počas prvých týždňov, ale majú menovaného vlastníka.

Je toho veľa na jedno sedenie. Rozdeľte to: **prvé stretnutie A–C** (vecné, s človekom,
ktorý program prevádzkuje), **druhé stretnutie D–F** (právne a prevádzkové, možno s iným
človekom v ADRA).

Kde je uvedený **Návrh**, ADRA nemusí nič vymýšľať — stačí potvrdiť alebo odmietnuť.
Ak na otázku nemá ADRA názor ani po druhom stretnutí, rozhodne PO a zapíše to ako
predpoklad. Nezodpovedaná otázka nesmie zastaviť prácu.

Čo sa ADRA **nepýtame**: technológie, hosting, databáza, podoba obrazoviek. To rozhoduje
tím.

---

## A. Čo treba priniesť zo stretnutia (nie otázky)

Bez týchto štyroch vecí je najhodnotnejšia funkcia — generovanie zmlúv — zablokovaná.

**A1. Tri existujúce zmluvy ako šablóny:** ADRA–darca, ADRA–škola, škola–opatrovník.
Ideálne vo formáte, v akom sa dnes vypisujú (Word), aj s jedným reálnym vyplneným
príkladom, aby bolo vidieť, ktoré polia sa naozaj menia.

**A2. Vzorku súčasných Excelov** — zoznam detí, zoznam platieb od darcov, prehľad platieb
školám. Stačia anonymizované, ale so zachovanými stĺpcami a formátmi. Bez toho sa nedá
navrhnúť import (R3).

**A3. Cenník za trimester** pre všetky štyri programy. Vo `Formulár dieťaťa.docx` sú tie
polia prázdne, takže autoritatívne trimestrálne číslo dnes neexistuje.

**A4. Vzory súhlasov**, ktoré dnes opatrovníci podpisujú, a informáciu, či sú podpísané
u všetkých detí, ktoré sú už v programe.

**A5. Prístup k dnešnému WordPressu** (aspoň ukázať, ako vzniká stránka dieťaťa) a meno
človeka, ktorý ho spravuje.

---

## B. Dátový model — treba uzavrieť pred prvým sprintom

**B1. Môže mať jedno dieťa viac darcov naraz?** Napríklad jeden platí stravu a druhý
školné, alebo dvaja darcovia po polovici.
Blokuje: jadro dátového modelu, nedá sa odložiť ani obísť.
Návrh: začať striktne 1:1, ale model postaviť tak, aby N:1 nevyžadovalo prepísanie.

**B2. Môže darca podporovať viac detí?**
Návrh: áno, bez obmedzenia počtu.

**B3. Kto prideľuje kód dieťaťa (`UGA 127`) — ADRA alebo škola?** Je kód stabilný na celý
čas programu, aj keď dieťa zmení školu? Môže sa kód po odchode dieťaťa znovu použiť?

**B4. Čo sa deje pri prestupe dieťaťa do inej školy alebo na vyšší stupeň?** Mení sa
program, cena, a teda aj zmluva s darcom? Pokračuje ten istý darca?

**B5. Sú trimestre pre obidve školy totožné?** Potrebujeme konkrétne dátumy začiatku
a konca pre aktuálny a nasledujúci školský rok. Trimester je kalendárna os celého systému.

**B6. Ako presne sa mesačná suma na webe vzťahuje k trimestrálnej?** Je 12 €/mesiac presne
48 €/trimester, alebo je mesačná suma zaokrúhlená a záväzná je trimestrálna?

**B7. V akej mene je zmluva so školou?** ADRA prijíma eurá a škole platí pravdepodobne
v ugandských šilingoch — ak je v zmluve so školou fixovaná suma v UGX a darca platí fixne
v EUR, kurzové riziko nesie ADRA. Kto ho nesie a je suma školy fixná na celý školský rok?
Blokuje: invariant „suma v zmluve sa nemení zmenou cenníka“ potrebuje vedieť, ktorá suma
a v akej mene je zamknutá.

**B8. Kto smie meniť cenník a ako často?** Potvrdzujeme, že existujúce sponzorstvá držia
sumu, s ktorou bola podpísaná zmluva, a zmena cenníka na ne nemá vplyv?

**B9. Aká je minimálna a typická dĺžka podpory?** Minimum je jeden trimester — aký je ale
bežný záväzok, ktorý sa píše do zmluvy? Jeden školský rok? Do dokončenia stupňa?

**B10. Ako sa rieši viac detí z jednej domácnosti?** Zdieľa sa profil rodiny a jej
situácia, alebo sa údaje o rodine vypisujú pri každom dieťati samostatne?

**B11. Koľko škôl a detí je cieľ a v akom horizonte?** Dnes sú dve školy a stovky detí;
z návrhu vyplýva zámer ísť do tisícok. Konkrétne číslo a horizont potrebujeme na
dimenzovanie úložiska pre fotky a vysvedčenia — to je jediné miesto, kde sa veľkosť
programu naozaj prejaví v technickom riešení.

---

## C. Proces — treba uzavrieť pred prvým sprintom

**C1. Ako dlho má platiť rezervácia dieťaťa, kým sa podpíše zmluva?** Potrebujeme
konkrétny počet dní. Čo sa stane, keď darca nikdy nepodpíše — vráti sa dieťa automaticky
do ponuky a dozvie sa o tom niekto?
Blokuje: bez čísla sa nedá implementovať ochrana proti dvojitému prisľúbeniu dieťaťa.

**C2. Ako darca reálne platí?** Trvalý príkaz, jednorazové platby, variabilný symbol na
dieťa? Kto a ako v ADRA zistí, že platba prišla?

**C3. Kto v ADRA zaznačuje prijatú platbu do systému a ako často?** Raz za trimester,
priebežne?

**C4. Čo sa stane, keď darca prestane platiť?** Aká je lehota, kto a kedy informuje školu,
a kto rozhoduje o tom, že dieťa ide späť do ponuky? Toto je najbolestivejší prechod
v celom procese — škola už s peniazmi počítala.

**C5. Musí ADRA škole zaplatiť aj vtedy, keď darca nezaplatil?** Potvrdzujeme, že systém
má tento rozdiel zviditeľniť, nie ho skryť?

**C6. Ako často musí škola nahrať vysvedčenia a priebežné fotky?** Raz za trimester? Je to
vynútiteľná povinnosť zo zmluvy so školou, alebo len prianie? Má systém školu upozorniť,
keď to nespraví?

**C7. Kto prekladá príbeh dieťaťa do slovenčiny?** Má byť systém alebo web dvojjazyčný
(SK/EN)? V akom jazyku zadáva podklady škola — predpokladáme angličtinu?

**C8. Kto upraví profil vo WordPresse**, keď dieťa získa podporu alebo keď opatrovník
odvolá súhlas so zverejnením? Export do WordPressu je jednosmerný, takže tento zásah
zostáva ručný a potrebuje menovaného vlastníka. Pri odvolanom súhlase je to právne riziko,
nie kozmetika.

**C9. Čo sa stane, keď dieťa dokončí stupeň alebo z programu odíde?** Ponúkne sa darcovi
iné dieťa? Kto ho kontaktuje?

**C10. Potrebuje darca potvrdenie o dare na daňové účely?** Ak áno, vydáva ho dnes ADRA
ručne a má ho generovať systém, alebo to zostáva mimo systému?

**C11. Aká je reálna konektivita a zariadenia na školách v Ugande?** Mobil alebo počítač?
Stabilné pripojenie alebo mobilné dáta? Kto konkrétne na škole bude formulár vypĺňať a ako
je technicky zdatný?

**C12. Má systém uniesť aj to, že podklad zadá pracovník ADRA namiesto školy?** (Očakávaná
odpoveď je áno — školy formulár nezačnú používať hneď.)

---

## D. Právne a osobné údaje

**D1. Kto je prevádzkovateľ osobných údajov — ADRA, škola, alebo obe spoločne?** Existuje
zmluvné ošetrenie prenosu údajov z Ugandy do EU?

**D2. Sú súhlasy podpísané u všetkých detí, ktoré sú dnes v programe?** Toto je zásadné
pre import z Excelu: ak sa naimportuje dieťa bez dohľadateľného súhlasu so zverejnením,
systém ho nesmie publikovať. Potrebujeme vedieť, koľkých detí sa to týka.

**D3. Súhlasy: papier a sken, alebo digitálny podpis?** Kto sken nahráva do systému —
škola alebo ADRA?

**D4. Kto podpisuje súhlas za sirotu v ústavnej starostlivosti?**

**D5. Smie sa zverejniť plné meno dieťaťa a fotografia tváre?** Čo presne je dnes na
adra.sk zverejnené a je to v súlade s tým, čo opatrovníci podpísali?

**D6. Ako dlho sa uchovávajú údaje, fotky a vysvedčenia po ukončení podpory?** Po tejto
lehote sa majú zmazať, alebo anonymizovať?

**D7. Čo sa stane, keď opatrovník odvolá súhlas počas aktívnej podpory?**

---

## E. Bezpečnosť a peniaze

**E1. Kto v ADRA smie meniť bankové spojenie školy a kto je tá druhá osoba, ktorá zmenu
potvrdzuje?** Potrebujeme dve konkrétne mená. Bez nich je pravidlo o štvorručnom
potvrdení len text v dokumente. Toto je jediné pole v systéme, ktorého prepísanie
presmeruje reálne peniaze.

**E2. Ako sa dnes overuje žiadosť o zmenu bankového spojenia?** Návrh: telefonátom na už
známy kontakt školy, nikdy na číslo z e-mailu, ktorý o zmenu žiada.

**E3. Koľko ľudí v ADRA má mať administrátorský prístup?** Čo sa stane, keď taký človek
z ADRA odíde — kto mu prístup odoberie?

**E4. Aký má byť režim prístupu darcu k údajom o dieťati?** `Štruktúra webu.docx` hovorí
o „prístupe cez heslo“.
Návrh: riadny účet darcu s vlastným heslom. Spoločné či zdieľané heslo na profil sa časom
rozšíri a nikdy sa nemení.

**E5. Smie škola vidieť identitu darcu alebo jeho platby?** (Očakávaná odpoveď je nie —
škola vidí len sumy, ktoré jej platí ADRA.)

---

## F. Prevádzka a prevzatie systému

Toto je časť, ktorú je najjednoduchšie odložiť a najdrahšie neriešiť. Tím po projekte
odíde.

**F1. Kto bude systém prevádzkovať po odchode tímu?** ADRA sama, externý dodávateľ, alebo
nikto? Kto reálne obnoví systém po havárii?

**F2. Na koho účet bude vedený hosting, domény a úložisko?** Musí to byť organizačný účet
ADRA, nie osobný účet zamestnanca alebo člena tímu. Kto platí faktúry?

**F3. Aká strata dát je ešte akceptovateľná — deň zadávania, hodina?** Od toho závisí, či
stačí denná záloha, alebo treba obnovu do bodu v čase.

**F4. Kde bude uložená kópia záloh mimo hostingu a na koho účet v ADRA je vedená?** Ak sa
stratí hosting kvôli zrušenému účtu alebo nezaplatenej faktúre, zmiznú s ním aj zálohy,
ktoré ležia v tom istom účte.

**F5. Kto v ADRA bude systém reálne používať a koľko ich je?** Jeden človek, alebo viac?
Kto ich zaškolí a kto prevezme dokumentáciu?

**F6. Beží popri importe z Excelu aj dobeh historických dát?** Alebo sa staré sponzorstvá
dosledujú po starom a systém začne od aktuálneho školského roka?
Návrh: začať od aktuálneho školského roka, historické dáta naimportovať len ako read-only
záznam, ak vôbec.

**F7. Kedy sa do systému vložia reálne dáta detí?** Do toho momentu tím pracuje výhradne
na vymyslených dátach — produkčné dáta v testovacom prostredí nemajú čo robiť.

---

## Ako zaznamenať výsledok

Ku každej otázke patrí jedna z troch vecí:

1. **Odpoveď od ADRA** — zapísať priamo k otázke, s dátumom a menom človeka.
2. **Rozhodnutie PO s predpokladom** — keď ADRA odpoveď nemá. Označiť ako predpoklad, aby
   sa vedelo, čo treba prehodnotiť, ak sa ukáže ako nesprávny.
3. **Odloženie s termínom a vlastníkom** — keď odpoveď zatiaľ nič neblokuje.

Čo nesmie zostať: otázka bez jednej z týchto troch vecí.

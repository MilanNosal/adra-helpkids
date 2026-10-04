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

**A1. Existujúce zmluvy a dodatky ako šablóny:** ADRA–darca, ADRA–škola,
škola–opatrovník a používané dodatky, minimálne pre zmenu sumy darcu a bankového spojenia
školy. Ideálne vo formáte, v akom sa dnes vypisujú (Word), aj s jedným reálnym vyplneným
príkladom každého typu, aby bolo vidieť, ktoré polia sa naozaj menia.

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
Ma byt jedna k jednej.

**B2. Môže darca podporovať viac detí?**
Ano.

**B3. Kto prideľuje kód dieťaťa (`UGA 127`) — ADRA alebo škola?** Je kód stabilný na celý
čas programu, aj keď dieťa zmení školu? Môže sa kód po odchode dieťaťa znovu použiť?
ADRA si ho generuje sama

**B4. Čo sa deje pri prestupe dieťaťa do inej školy alebo na vyšší stupeň?** Mení sa
program, cena, a teda aj zmluva s darcom? Pokračuje ten istý darca?
Nic sa nemeni

**B5. Sú trimestre pre obidve školy totožné?** Potrebujeme konkrétne dátumy začiatku
a konca pre aktuálny a nasledujúci školský rok. Trimester je kalendárna os celého systému.
Dajme tomu ze hej

**B6. Ako presne sa mesačná suma na webe vzťahuje k trimestrálnej?** Je 12 €/mesiac presne
48 €/trimester, alebo je mesačná suma zaokrúhlená a záväzná je trimestrálna?
Suma je 3x suma na trimester, rozdelena 12 na 12 mesiacov v roku, zmluva je na neurcito s 
mesacnou vypovednou lehotou.
Sucastou zmluvy je aj splatkovy kalendar, platby mozu byt mesacne, stvrtocne, polrocne, alebo rocne.

**B7. V akej mene je zmluva so školou?** ADRA prijíma eurá a škole platí pravdepodobne
v ugandských šilingoch — ak je v zmluve so školou fixovaná suma v UGX a darca platí fixne
v EUR, kurzové riziko nesie ADRA. Kto ho nesie a je suma školy fixná na celý školský rok?
Blokuje: invariant „suma v zmluve sa nemení zmenou cenníka“ potrebuje vedieť, ktorá suma
a v akej mene je zamknutá.
V Eure.

**B8. Kto smie meniť cenník a ako často?** Potvrdzujeme, že existujúce sponzorstvá držia
sumu, s ktorou bola podpísaná zmluva, a zmena cenníka na ne nemá vplyv?
Cennik moze menit ADRA, ked sa cennik zmeni, meni sa pre novych donorov. ADRA ako administrator
by mala mat moznost zmenit cenu aj pre existujuceho donora formou dodatku k zmluve. Zmluvy
by mali podporovat i dodatky.

**B9. Aká je minimálna a typická dĺžka podpory?** Minimum je jeden trimester — aký je ale
bežný záväzok, ktorý sa píše do zmluvy? Jeden školský rok? Do dokončenia stupňa?
Zmluva je na neurcito s mesacnou vypovednou lehotou.

**B10. Ako sa rieši viac detí z jednej domácnosti?** Zdieľa sa profil rodiny a jej
situácia, alebo sa údaje o rodine vypisujú pri každom dieťati samostatne?
Formular je pre kazde dieta osve, ale deti by mali mat moznost vyjadrit vztah rodiny,
tzn. yb bola vhodna nejaka abstrakcia rodiny (surodenci, mozno aj brantranci?).
Donor si napr moze vybrat ze chce podporit celu rodinu.
Opatrovnik/skola by mala mat moznost vyplnit formular dietata raz, nahrat ho, a nechat si 
urobit kopiu formulara, kde len zmenia co treba, napr. iba krstne meno.

**B11. Koľko škôl a detí je cieľ a v akom horizonte?** Dnes sú dve školy a stovky detí;
z návrhu vyplýva zámer ísť do tisícok. Konkrétne číslo a horizont potrebujeme na
dimenzovanie úložiska pre fotky a vysvedčenia — to je jediné miesto, kde sa veľkosť
programu naozaj prejaví v technickom riešení.
max 50 skol a 5000 deti vseobecme, teraz su 2 skoly a 150 deti, ocakavame v par dalsich rokoch 
rast na mozno 10 skol a mozno dokopy 1000 deti

---

## C. Proces — treba uzavrieť pred prvým sprintom

**C1. Ako dlho má platiť rezervácia dieťaťa, kým sa podpíše zmluva?** Potrebujeme
konkrétny počet dní. Čo sa stane, keď darca nikdy nepodpíše — vráti sa dieťa automaticky
do ponuky a dozvie sa o tom niekto?
Blokuje: bez čísla sa nedá implementovať ochrana proti dvojitému prisľúbeniu dieťaťa.
Povedzme do 5 pracovnych dni

**C2. Ako darca reálne platí?** Trvalý príkaz, jednorazové platby, variabilný symbol na
dieťa? Kto a ako v ADRA zistí, že platba prišla?
To system nezaujima, pracovnik ADRA potvrdi ze platba za dany mesiac (pripadne za x mesiacov dopredu)
dosla

**C3. Kto v ADRA zaznačuje prijatú platbu do systému a ako často?** Raz za trimester,
priebežne?
Uctovnik, proste ADRA admin systemu. malo by to mat granularitu mesacnu

**C4. Čo sa stane, keď darca prestane platiť?** Aká je lehota, kto a kedy informuje školu,
a kto rozhoduje o tom, že dieťa ide späť do ponuky? Toto je najbolestivejší prechod
v celom procese — škola už s peniazmi počítala.
Administrator by mal cez ssytem umoznit upozornit donora ze nezaplatil. Idealne nejaka sablona
mailu.
Skola by mala vidiet iba to, ci ma alebo nema dany student donora, skola nevidi, ci donor plati alebo nie, to riesi ADRA. ADRA ked sa rozhodne dat dieta naspat na "trh", az vtedy vidi skola v systeme, ze uz to dieta donora nema.

**C5. Musí ADRA škole zaplatiť aj vtedy, keď darca nezaplatil?** Potvrdzujeme, že systém
má tento rozdiel zviditeľniť, nie ho skryť?
zodpoveda predchadzajuca otazka. Skola vidi ze ma donora, a ked to vidi, ADRA plati, a skola
nevie, odkial peniaze skutocne prisli. Je vecou ADRA ako to vyriesi. Skola vidi zaplatene trimestre.
Aktualizacia donorov a deti sa deje na zaklade trimestrov, tzn. skola vzdy vlastne vidi, ze tento 
najblizsi trimester ma toto dieta donora, alebo nema. Rozdiel, ak donor prestane platit, je 
transparentny z hladiska skoly, riesi si to adra svojou cestou. Inymi slovami, dieta sa moze dostat
naspat do ponuky, ale ak uz zacalo plateny trimester, z pohladu skoly by malo byt pre dany trimester
proste dotovany.

**C6. Ako často musí škola nahrať vysvedčenia a priebežné fotky?** Raz za trimester? Je to
vynútiteľná povinnosť zo zmluvy so školou, alebo len prianie? Má systém školu upozorniť,
keď to nespraví?
Aspon raz za trimester (vysvedcenie raz na konci, fotky kedykolvek), ak ani raz - treba upozornit skolu mailom.

**C7. Kto prekladá príbeh dieťaťa do slovenčiny?** Má byť systém alebo web dvojjazyčný
(SK/EN)? V akom jazyku zadáva podklady škola — predpokladáme angličtinu?
System v ENG, ak bude export pribehu do SVK, tak to je nice to have.

**C8. Kto upraví profil vo WordPresse**, keď dieťa získa podporu alebo keď opatrovník
odvolá súhlas so zverejnením? Export do WordPressu je jednosmerný, takže tento zásah
zostáva ručný a potrebuje menovaného vlastníka. Pri odvolanom súhlase je to právne riziko,
nie kozmetika.
Pracovnik adra manualne

**C9. Čo sa stane, keď dieťa dokončí stupeň alebo z programu odíde?** Ponúkne sa darcovi
iné dieťa? Kto ho kontaktuje?
Automaticke upozornenie zo systemu mozno aj s navrhmi nejakych novych deti, ktore si moze vziat 

**C10. Potrebuje darca potvrdenie o dare na daňové účely?** Ak áno, vydáva ho dnes ADRA
ručne a má ho generovať systém, alebo to zostáva mimo systému?
Mimo system

**C11. Aká je reálna konektivita a zariadenia na školách v Ugande?** Mobil alebo počítač?
Stabilné pripojenie alebo mobilné dáta? Kto konkrétne na škole bude formulár vypĺňať a ako
je technicky zdatný?
Mobil je bezny, pocitac by mal byt ok, nepredpokladajme ziadne obmedzenia

**C12. Má systém uniesť aj to, že podklad zadá pracovník ADRA namiesto školy?** (Očakávaná
odpoveď je áno — školy formulár nezačnú používať hneď.)
Ano

---

## D. Právne a osobné údaje

**D1. Kto je prevádzkovateľ osobných údajov — ADRA, škola, alebo obe spoločne?** Existuje
zmluvné ošetrenie prenosu údajov z Ugandy do EU?
Preco toto riesis? ADRA

**D2. Sú súhlasy podpísané u všetkých detí, ktoré sú dnes v programe?** Toto je zásadné
pre import z Excelu: ak sa naimportuje dieťa bez dohľadateľného súhlasu so zverejnením,
systém ho nesmie publikovať. Potrebujeme vedieť, koľkých detí sa to týka.
Zmluva s opatrovnikom obsahuje klauzulu so suhlasom, takze ano

**D3. Súhlasy: papier a sken, alebo digitálny podpis?** Kto sken nahráva do systému —
škola alebo ADRA?
opat je to zmluva, takze skola nahra podpisanu vygenerovanu zmluvu

**D4. Kto podpisuje súhlas za sirotu v ústavnej starostlivosti?**
Opatrovnik

**D5. Smie sa zverejniť plné meno dieťaťa a fotografia tváre?** Čo presne je dnes na
adra.sk zverejnené a je to v súlade s tým, čo opatrovníci podpísali?
Ano

**D6. Ako dlho sa uchovávajú údaje, fotky a vysvedčenia po ukončení podpory?** Po tejto
lehote sa majú zmazať, alebo anonymizovať?
System nema nic automaticky mazat ani anonymizovat

**D7. Čo sa stane, keď opatrovník odvolá súhlas počas aktívnej podpory?**
Nic

---

## E. Bezpečnosť a peniaze

**E1. Kto v ADRA smie meniť bankové spojenie školy a kto je tá druhá osoba, ktorá zmenu
potvrdzuje?** Potrebujeme dve konkrétne mená. Bez nich je pravidlo o štvorručnom
potvrdení len text v dokumente. Toto je jediné pole v systéme, ktorého prepísanie
presmeruje reálne peniaze.
Zmena je len v rukach skoly a jej vysledkom musi byt dodatok k zmluve (tzn. musi byt k tomu nejaky doklad).

**E2. Ako sa dnes overuje žiadosť o zmenu bankového spojenia?** Návrh: telefonátom na už
známy kontakt školy, nikdy na číslo z e-mailu, ktorý o zmenu žiada.
Vid odpoved vyssie

**E3. Koľko ľudí v ADRA má mať administrátorský prístup?** Čo sa stane, keď taký človek
z ADRA odíde — kto mu prístup odoberie?
Moze byt viac, takze ADRA ma dva typy roly, admin moze vsetko a robit nove ucty, regularny
pracovnik moze vsetko co adra, ale nemoze spravovat ucty

**E4. Aký má byť režim prístupu darcu k údajom o dieťati?** `Štruktúra webu.docx` hovorí
o „prístupe cez heslo“.
Návrh: riadny účet darcu s vlastným heslom. Spoločné či zdieľané heslo na profil sa časom
rozšíri a nikdy sa nemení.
Adra pracovnik edituje fotky, kontroluje vysvedcenia, edituje pribehy (formalre/data dietata),
schvaluje zaregistrovane skoly, schvaluje pridane deti, scvaluje donora (po obdrzani zmluvy)

**E5. Smie škola vidieť identitu darcu alebo jeho platby?** (Očakávaná odpoveď je nie —
škola vidí len sumy, ktoré jej platí ADRA.)
Nie

---

## F. Prevádzka a prevzatie systému

Toto je časť, ktorú je najjednoduchšie odložiť a najdrahšie neriešiť. Tím po projekte
odíde.

**F1. Kto bude systém prevádzkovať po odchode tímu?** ADRA sama, externý dodávateľ, alebo
nikto? Kto reálne obnoví systém po havárii?
ADRA sama - trebalo by nejaku dokumentaciu po tom, co to tim odovzda

**F2. Na koho účet bude vedený hosting, domény a úložisko?** Musí to byť organizačný účet
ADRA, nie osobný účet zamestnanca alebo člena tímu. Kto platí faktúry?
ADRA

**F3. Aká strata dát je ešte akceptovateľná — deň zadávania, hodina?** Od toho závisí, či
stačí denná záloha, alebo treba obnovu do bodu v čase.
Staci asi kludne raz za den

**F4. Kde bude uložená kópia záloh mimo hostingu a na koho účet v ADRA je vedená?** Ak sa
stratí hosting kvôli zrušenému účtu alebo nezaplatenej faktúre, zmiznú s ním aj zálohy,
ktoré ležia v tom istom účte.
To musime vymysliet

**F5. Kto v ADRA bude systém reálne používať a koľko ich je?** Jeden človek, alebo viac?
Kto ich zaškolí a kto prevezme dokumentáciu?
Potencialne viac ludi. Bude urcite aspon jeden admin, a aspon jeden pracovnik, pravdepodbne len
v tomto zlozeni

**F6. Beží popri importe z Excelu aj dobeh historických dát?** Alebo sa staré sponzorstvá
dosledujú po starom a systém začne od aktuálneho školského roka?
Návrh: začať od aktuálneho školského roka, historické dáta naimportovať len ako read-only
záznam, ak vôbec.
staci zacat novy trimester, ale ak bude aj readonly zaznam z minoulosti, bude to fajn

**F7. Kedy sa do systému vložia reálne dáta detí?** Do toho momentu tím pracuje výhradne
na vymyslených dátach — produkčné dáta v testovacom prostredí nemajú čo robiť.
Ked sa system odovzda

---

## Ako zaznamenať výsledok

Ku každej otázke patrí jedna z troch vecí:

1. **Odpoveď od ADRA** — zapísať priamo k otázke, s dátumom a menom človeka.
2. **Rozhodnutie PO s predpokladom** — keď ADRA odpoveď nemá. Označiť ako predpoklad, aby
   sa vedelo, čo treba prehodnotiť, ak sa ukáže ako nesprávny.
3. **Odloženie s termínom a vlastníkom** — keď odpoveď zatiaľ nič neblokuje.

Čo nesmie zostať: otázka bez jednej z týchto troch vecí.

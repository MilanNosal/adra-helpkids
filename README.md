# adra-helpkids

## Názov

HELPKIDS

---

## Opis projektu

ADRA Slovensko spája slovenských darcov s konkrétnymi deťmi v Ugande: darca pravidelnou
platbou 12–60 € mesačne hradí dieťaťu školu, stravu a niekedy aj internát. Deti sú siroty
alebo pochádzajú z rodín, ktoré na školu nemajú — z utečeneckého tábora Kyaka II, kde žije
120 000 ľudí, a zo slumov na predmestí Kampaly. Nie je to anonymná zbierka, ale dlhodobý
vzťah jeden na jedného, ktorý treba roky obsluhovať vysvedčeniami, fotkami a vyúčtovaním.
Nie je to cvičná úloha: za každým záznamom je konkrétne dieťa, ktoré bez podpory nechodí do
školy, a reálne peniaze, ktoré musia doputovať na správny účet v správnom trimestri.

Dnes to celé beží ručne. Škola v Ugande pozbiera údaje o dieťati od rodičov, napíše ich do
voľného dokumentu, nafotí deti a pošle to cez WhatsApp. V ADRA to niekto prečíta, doplní
chýbajúce údaje, prepíše do excelu, preloží príbeh dieťaťa do slovenčiny a ručne založí
stránku dieťaťa na webe. Keď sa ozve darca, príde email s obsahom formulára — a z neho
niekto ručne vypíše zmluvu. Rovnako zmluvu so školou a zmluvu medzi školou a rodičom.
Tie isté údaje o jednom dieťati sa prepisujú niekoľkokrát a konkrétny stav dieťaťa sa 
drží iba v hlave zamestnanca ADRA.

Úlohou tímu je postaviť systém, ktorý by mal celý proces maximálne automatizovať.
Systém umožní škole zadať podklady priamo do systému,
pracovník ADRA ich schváli a redakčne upraví — a z databázy sa potom vygeneruje všetko ostatné:
profil dieťaťa na zverejnenie, tri typy zmlúv v PDF, prehľady platieb po trimestroch a darcovský
pohľad na „svoje“ dieťa. Darca dostane prístup do systému, kde po trimestroch sleduje výsledky
dieťaťa — vysvedčenia, hodnotenia a priebežné fotky — a vlastné platby; dnes to chodí ad hoc
emailom. Systém by mal umožniť import aktuálnych dát z ADRA excelov. Momentálne
je počet zapojených detí a škôl obmedzený časom zamestnanca, cieľom systému je umožniť násobný
nárast kapacity organizácie a sprístupniť tak vyššiu kvalitu života čo najviac deťom.

Na prvý pohľad to môže vyzerať ako CRUD, ale nie je. Dieťa sa musí dať rezervovať na obmedzený
čas, kým sa podpíše zmluva — keď to zlyhá, ADRA prisľúbi jedno dieťa dvom darcom. A najcennejším
cieľom útoku nie sú osobné údaje, ale bankové spojenie školy: jedno prepísané pole presmeruje reálne
peniaze niekam inam. A čo je hlavné, systém chceme využívať v praxi, takže ho potrebujeme v produkčnej
kvalite a je ho potrebné dotiahnuť do detailov.

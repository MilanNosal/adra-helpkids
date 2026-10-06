# Poznámky — prepracovanie priorít backlogu (2026-10-06)

Záznam rozhovoru, z ktorého vychádza poradie v `BACKLOG.md` a úpravy v `DOMENOVY-NAVRH.md`.

---

## Zadanie od PO

> ok, potrebujem aby si prepracoval backlog aj backlog tickets, lebo momentalne je to dost
> zle. potrebujeme to staviat s low hanging fruit first, tzn to co je najdolezitejsie najprv
> a nestaviat priority na menej podstatnych veciach...
>
> najpodstatnejsie je nahradenie excel dokumentu management deti, kde je vlastne databaza
> (vid example doc).. excel s reportom pre skolu o tom, kolko dostane penazi za semester je
> druhorade.
>
> ukladanie dokumentov ako su podpisane zmluvy je tiez druharade, cca s rovnakou prioritou
> ako excel pre skolu.
>
> generovanie zmluv a dodatkov k zmluvam je tretorade a ma byt na konci
>
> cize nahradenie tejto excel DB je najdolezitejsia vec, je to jadro systemu. to si
> samozrejme bude vyzadovat roly, atd., ale kedze ADRA pracovnik vie administrovat vsetko,
> tak vie manualne vytvorit skolu s detmi a aj zaznamy a ucty pre aktualnych donorov (import
> z excelu by bol lepsi, ale na prvy prototyp toto by malo postacit).. dalsie features sa
> maju na to nabalovat, tzn dalsi feature bude to ze sa skola vie sama zaregistrovat, potom
> ze sa donor vie sam zaregistrovat, potom ze skola vie pridavat deti (ktore ale musi
> schvalit ADRA), potom ze donor vidi neobsadene a nerezervovane deti, potom ze si ich vie
> sam rezervovat a pracovnik adra vie rezervaciu potvrdit, potom ze donor vie vidiet svoje
> donovane deti, potom ze vie zrusit podporu deti ktore sponzoruje (s mesacnou vypovednou
> lehotou), potom ze sa da pridat novy trimester (trimeseter pre skolu, tzn pre kazdu skolu
> vieme zacat trimester separatne) - kde do trimestra vie adra priradit studentov ktori budu
> adrou sponzorovani (by default system navrhne vsetky deti, ktore maju aktualne sponzora),
> potom ze skola vie vidiet svoj aktualny trimester aj s vyuctovanim (tj az teraz sa
> dostavame k nahrade excelu pre skolu), potom ze system je schopny prijat a parovat
> podpisane zmluvy s donormi (tzn ze kazdy donor si vie v systeme pozriet svoje aktualne
> platne zmluvy a dodatky, a ze adra pracovnik si vie pozriet to iste ku kazdemu donorovi),
> potom ze to iste vie system urobit pre skoly medzi skolou a adrou, a potom to iste pre
> skoly medzi skolou a opatrovnikmi. az potom sa dostavame k tomu, ze system umozni
> automaticke generovanie zmluv postupne pre tieto situacie..

---

## Otázky a odpovede — 1. kolo

**1. ADRA podpora.** Tabuľka má stĺpec „Podpora z réžie ADRA bez podpory donorov“. Má jadro
hneď vedieť, že dieťa platí ADRA bez darcu?
> Dieťa je podporované ADRA vtedy, keď ho ADRA pridá do trimestra, ale dieťa nemá donora,
> resp. ak stratí donora počas trimestra. Kým nemáme vyriešený trimester, táto otázka je
> nepodstatná.

**2. Obdobia podpory.** Má jadro hneď držať históriu sponzorstiev s číslom DZ a dodatku?
> Bolo by to fajn, ale asi to nie je nevyhnutné — možno stačí nejaký historicky pridaný
> záznam o podpore pre dieťa, zároveň nejaký historický záznam o tom, na ktorú školu to
> dieťa chodilo.

**3. Darca s viacerými deťmi.** Je väzba „1 zmluva → N detí“ správna?
> Môže a nemusí. Môže mať viac zmlúv na viac detí, ale môže byť aj jedna zmluva pre viac
> detí, tzn. 1…n.

**4. Platby darcov.** Kam patrí zaznačovanie platieb?
> Platby od donorov zaznačuje pracovník ADRA, ale systém má mať možnosť, kde si zamestnanec
> ADRA pre každého donora pozrie, aký má splátkový kalendár (ten si vyberie donor, keď si
> rezervuje dieťa), a vie si v čase od rezervácie a od dátumu prvej platby (navrhnutej
> systémom) vyklikávať potvrdenie platby. Systém vie ukázať, ktorí donori niečo nezaplatili,
> a vie automaticky poslať upomienku najprv pracovníkovi a potom cez preklik v systéme
> pracovníkom aj donorovi.

**5. Účty darcov v prvom kroku.** Prihlasovacie účty, alebo len záznamy?
> Hneď ako prihlasovacie účty. Keď to nebola registrácia, ale účet vytvorený pracovníkom
> ADRA (aj pracovník, nielen admin vie taký účet vytvoriť), heslo je vygenerované náhodne a
> nevidí ho nikto. Na akciu pracovníka vie systém vygenerovať nové heslo a poslať ho na
> e-mail darcu (pracovník ani admin nikdy nevidí ani vygenerované heslo). V prvom kroku
> záznam existuje ako účet darcu, ale „neaktivovaný“, teda len „historický“. Až keď sa
> pracovník rozhodne darcu pozvať do systému, urobí ten krok, a až keď sa darca prvýkrát
> prihlási, účet sa stane aktivovaným a heslo už pracovník nevie pregenerovať (iba admin).

**6. Registrácia školy a darcu.** Otvorená, alebo na pozvánku?
> Škola vie byť vytvorená pracovníkom rovnako ako darca v bode 5, ale normálne to bude
> otvorená registrácia s potvrdením od pracovníka ADRA. Až keď to pracovník potvrdí, škole
> je umožnené pridávať deti (ktoré tiež musia byť potvrdené, než ich je vidieť). Pre donorov
> bude registrácia otvorená bez potvrdenia pracovníkom, ale alokovanie dieťaťa musí byť
> potvrdené (rezervácia nie). Všetky vytvorenia účtov majú byť chránené captchou.

**7. Rezervácia.** Časový limit? Je potvrdenie ADRA rovno vznik sponzorstva?
> Áno, rezervácia má časový limit 7 dní, potvrdenie ADRA je potrebné, akurát sa nerieši
> zmluva. Neskôr sa pred potvrdením ADRA bude očakávať nahratie zmluvy, po ktorom sa môže
> potvrdiť, a ešte neskôr generovanie zmluvy.

**8. Výpoveď.** Vráti sa dieťa automaticky do ponuky?
> Dieťa bez donora sa vracia automaticky do ponuky. Z pohľadu školy však zostáva v trimestri
> ako platené, platí to vtedy ADRA (čiže ADRA musí vidieť, že mesiace XY nemá donora, ale
> platí ho ADRA).

**9. Ceny programov.** Majú byť v jadre?
> Áno, ceny nech sú tam už pred trimestrom, hneď so školou. Potrebujeme ale historické
> vedenie, tzn. vedieť, v akých obdobiach aké boli ceny na škole. Najpodstatnejšia je však
> aj tak aktuálna cena.

**10. Import z Excelu.**
> Druhoradý — môže byť niekde na konci priorít ku generovaniu. Import má len automaticky
> vytvoriť tie záznamy, ktoré od začiatku vie vytvárať pracovník ADRA. Môže byť rozbitý na
> časti: import škôl, detí, donorov atď.

**11. Fotky, príbeh, export do WordPressu.**
> Príbeh a dáta o dieťati majú byť súčasťou vytvorenia záznamu. Nahrávanie fotiek a
> vytvorenie WordPress profilu je ďalšia user story, niekde v strede priorít.

**12. Reporty od školy.**
> Vytváranie a nahrávanie reportov zo školy má byť po tom, čo si donor vie pozrieť svoje
> sponzorované deti. Ďalšia user story je, že si vie pozerať reporty detí z času, keď ich
> sponzoroval.

**13. Infra a bezpečnosť.**
> 2FA až na koniec priorít, zvyšok nech ostane na začiatku.

**14. Súrodenci, prestup, odchod, notifikácie.**
> Súrodenci, prestup a odchod na začiatok nižších priorít — pred generovanie zmlúv, ale za
> ostatné. Notifikácie môžu ísť na koniec ku generovaniu zmlúv.

**15. Formát dokumentov.**
> `OTAZKY-PRE-ADRA.md` nechať. Nový `notes.md` s týmto rozhovorom. `backlog_tickets.md`
> zmazať, `BACKLOG.md` úplne prepísať — len zoznam usporiadaných ticketov: infraštruktúrne
> tickety bez user stories a potom tickety z tejto komunikácie v tomto poradí, formulované
> ako krátke jednovetné, niekedy niekoľkovetné user stories.

---

## Otázky a odpovede — 2. kolo

**Platby — kam zaradiť zaznačovanie a prehľad dlžníkov?**
> Rozdeliť na zaznačovanie a prehľad (v jadre), upomienky až neskôr.

**Môže si aktivovaný používateľ obnoviť heslo sám cez „zabudnuté heslo“?**
> Áno.

**Captcha chráni len verejné registrácie, nie účty vytvorené pracovníkom?**
> Áno.

**`DOMENOVY-NAVRH.md` — nechať, alebo zosúladiť?**
> Opraviť.

**Jazyk backlogu?**
> Slovenčina.

---

## Otázky a odpovede — 3. kolo

**Presná výpovedná lehota: koniec podpory k poslednému dňu nasledujúceho mesiaca, alebo
mesiac odo dňa výpovede?** (HK-43)
> Mesiac odo dňa výpovede.

**Zastaví nahratie podpísanej zmluvy 7-dňovú lehotu rezervácie, alebo musí ADRA potvrdiť
v rámci nej?** (HK-54)
> Rezerváciu vždy zastaví až potvrdenie od ADRA.

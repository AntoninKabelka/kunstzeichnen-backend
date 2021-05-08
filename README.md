# kunstzeichnen-backend

# Harmonogram

|  tyden | Frontend  | Backend  | Admin  | Ostantni  |
|---|---|---|---|---|
| 1 (do 9.5.) | rozvrzeni a priprava prostredi  | vytvoreni zarodku aplikace  |  rozvrzeni a priprava prostredi |  rozvrzeni a priprava prostredi |
| 2 (do 16.5.) |  zpracovani infrasturktury aplikace a pridani formularu pro prihlasky | zapracovani sekce prihlasek, kurzu, knihy a newsletteru  | navrzeni administracniho prostredi pro spravu prihlasek a obsahu s tim spojenych + vytvoreni zarodku  |  dalsi rozvrhovani  |
| 3 (do 23.5.) | CMS - system na spravu obsahu a vytvareni stranek  | CMS - system na spravu obsahu a vytvareni stranek  |  CMS - system na spravu obsahu a vytvareni stranek |   |
| 4 (do 30.5.) |  prace na menu a paticce a zbylych obsahovych typech  |  zapracovani menu a paticky a zbylych obsahovych typu | prace na menu a paticce a zbylych obsahovych typech  |   |
| 5 (do 6.6.) |  stylovani frontendu - pridavani letadla animaci atd  |   | dodatecne prace an adminu  |   |

*po tydnu 3 uvidime jak na tom budeme, trosku se obavam ze obsah tydnu 2 a 3 je celkem ambicionzni - zacatek jeste bude celkem o nastavovani prostredi aplikaci a praci na zakladech aplikaci, ktera se muze protahnout, po tydnu 3 uz to bude pouze pridavani obsahu do jiz zpracovane infrastruktury

# Struktura

## Frontend

- Nuxt + Vue aplikace 
- url: www.host.de
- zpracovana podle navrhu


## Backend API
- Flask api 
- url: api.host.de
- CRUD na kazdy datovy typ
- autentifikace pro PUT, DELETE a POST (krome prihlasek) endpointy


## Admin
- Nuxt + Vue + Vuetify 
- url: admin.host.de
- CMS sekce - obsahove stranky
- Sekce s kurzy a prihlaskami
- Sekce s knihou a objednavkami
- Sekce s aktualitami
- Newsletter sekce
- Nastaveni webu sekce (uprava menu a paticky)

# Hosting
Pro vyvoj budu pouzivat asi heroku (kvuli jednoduchosti uploadu behem vyvoje), mam take vps od Wedosu na kterem muzu otestovat finalni setup. Koupime potom spolecne nejaky VPS hosting az budeme mit aplikace pripravene a ja vam to tam pak rozjedu - na hosting se pripoji vase domeny a to bude 


# database - models

## prihlasky / formulare 

**prihlaska do kurzu**
- kurz
- jmeno objednavajiciho
- prijmeni objednavajiciho
- gender objednavajiciho
- telefon objednavajiciho
- email objednavajiciho
- ulice
- cislo popisne
- mesto
- psc
- zeme
- zprava
- typ (normalni, darek, dite) - u normalni se data prihlaseneho = data objednavajiciho
- jmeno prihlaseneho
- prijmeni prihlaseneho
- telefon prihlaseneho - u deti
- datum narozeni prihlaseneho - u deti
- send by post - u darku
- stav (vytvorena, potrvzena, zaplacena, stornovana) - funcionalita do admina 
- timestamp (datum a cas vytvoreni prihlasky)

**prihlaska na knihu**
- jmeno
- prijmeni
- ulice
- cislo
- mesto
- psc
- zeme
- telefon
- email
- zprava
- stav (vytvorena, zaplacena, odeslana)
- timestamp (datum a cas vytvoreni prihlasky)

**Newsletter prihlaska**
- email
- timestamp (datum a cas vytvoreni prihlasky)

**Prihlaska na individualni hodiny ?**
- obdobne jako prihlaska na kurz (v db by se idividualni hodiny mohli ukladat jako workshopy pro jednu osobu, kdyz si nekdo zazada a zaplati tak se vyrobi workshop s tim jednim clovekem)

## hlavni funcni prvky

**Kurz**
- opakujici (ano= kurz, ne=workshop) (v adminu to muze byt rozdelene ale v datech to dava smysl mit ulozene pospolu)
- nazev
- kratky popis
- cena
- datum (u kurzu den v tydnu)
- cas
- pocet mist
- detailni stanka/popis (obsahova stranka)
- prihlasky - (seznam prihlasek) 
- kategorie kurzu

**Kategorie Kurzu**
- nazev
- popis
- seznam kurzu

**Kniha**
- obrazek
- popis
- nadpis
- cena
- obrazky do menu (prevraceni knihy v menu pri kliknuti)
+ potrebne texty do formulare atd

**Newsletter**
- prihlaseni (seznam prihlasek do newsletteru)

**Aktualita**
- obrazek
- text
- kratky text (zobrazujici se na homepagi)
- nadpis

**Galerie**
- bloky obrazku

**Blok obrazku**
- obrazky
- nadpis
- popis

**Obrazek** / mozna nahradim obsahovym blockem obrazek
- soubor
- alt
- popis

## CMS

**Obsahova stranka**
- obsahove bloky 
- nazev
- slug (kunstzeichnen.de/obsah/<slug> - definuje url stranky)

**Obsahovy blok**
- typ - podle toho si drzi data

**obsahovy block text**
- text (wysiwyg- formatovatelny text - mozna postaci na vsechno)

**obsahovy blok nadpis**
- text
- uroven 

**obsahovy blok obrazek**
- soubor
- altetnativni text
- popis

**obsahovy block video**
- url

**obsahovy block citat**
- text
- autor

*obsahove bloky se daji pridavat podle potreby webu 

## mixiny - funkcionalita co se da pridat ke kazdemu datovemu prvku

**viditelnost na webu**
- viditelny (ano/ne)

**vaha**
- cislena hodnota (urcuje poradi vypisu na webu)


## configuracni prvky 

**hlavni menu**
- seznam rubrik

**rubrika**
- nazev
- je odkaz (ano/ne)
- url odkazu
- seznam podrubrik

**podrubrika**
- nazev
- ikona
- url odkazu

**paticka**
- odkazy na obsah

**odkaz na obsah**
- nazev
- url






# Sandpit (nerelevantni pro vas, tady si jen zkousim veci)

config / content type / (atomic)

- infopages -> content{ blocks(img, text, video)}
- course 
- categories
- menu -> 1stlvl{ (text), image-hp(file), [2ndlvl{title(text), [icon-link{ image(file), title(text), reference{config}]}]}
- menu -> 1stlvl{[icon-link]}
- galery -> image-group{ desc(), title() [image{(file), alt(text), description(text)}]}
- homepage 

- prihlaska na kurz

- prihlaska do newsletteru

- kniha

- prihlaska pro knihu 

- aktualita()





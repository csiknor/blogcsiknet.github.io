---
author: csiknor
comments: true
date: 2013-05-02 16:21:47+00:00
layout: post
link: http://blog.csik.net/2013/05/02/latszodj-te-is-szellemkent-a-weben/
slug: latszodj-te-is-szellemkent-a-weben
title: Látszódj te is szellemként a weben
wordpress_id: 169495872
categories:
- Lifehack
- Tech
- Vélemény
tags:
- böngésző
- cookie
- ghostery
- magánszféra
- privát
- süti
---

Ahogy talán jobb nem belegondolni abba sem, hogy az élelmiszeripar mit tol le a torkunkon sonka, tej, üdítőital vagy éppen párizsi néven, talán jobb abba sem belegondolni, hogy mit tudnak rólunk az internet nagytestvérei, a Google, a Facebook és még sok más hirdetésekkel foglalkozó szervezet.


<blockquote>De ha már belegondoltunk, akkor viszont érdemes azon is elgondolkodni, hogy mit tehetünk ellene. (Az élelmiszeripart viszont most kihagynám a körből.)</blockquote>




## Számos eszköz a megfigyelésre


A weboldalak számos eszközt használnak arra, hogy kövessenek minket. Ilyenek a követő sütik, amiket a weboldalak különböző okokból kifolyólag helyeznek el a böngészőkben. Egyrészt azért, hogy segítsenek, pl. azzal, hogy ne kelljen újból belépni. Másrészt azért, hogy tudják kik vagyunk, mit csináltunk korábban, milyenek a szokásaink.

Mondhatjuk erre, hogy rendben, de rengeteg oldal van, kit érdekel, ha kismillió oldal külön-külön tud egy-egy szelet információt rólam? Ez igaz, viszont kismillió oldal használja ugyanazt a szolgáltatást a látogatottság mérésre, vagy akár a hirdetések megjelenítésére. Így ezek a központinak nevezhető háttérszolgáltatások már önmagukban képesek arra, hogy remek képet alkossanak rólunk a szokásaink alapján.

Aztán ott vannak még a látszólagos szolgáltatást adó közösségi megosztást, tetszésnyilvánítást, hozzászólást lehetővé tévő komponensek. A Facebook hozzászólás, vagy tetszésnyilvánító dobozok, hivatkozások tulajdonképpen minden oldalon megtalálhatóak. Mindenki láthatja, hogy ezek tudják, hogy ki a belépett felhasználó, így még pontosabb képet tudnak alkotni.


## A politikai megoldás


Nem olyan régen [elfogadták az EU-ban (U.K.?)](http://www.wired.co.uk/news/archive/2012-05/25/cookies-made-simple), hogy minden böngésző sutit használni kívánó oldalnak lehetőséget kell biztosítania a látogatóknak arra, hogy ne kérjenek ezekből a sütikből. Ez jól hangzik, csak sajnos teljesen hasztalan.

Azt érték el ugyanis, hogy minden oldal kitett egy figyelmeztetést az új látogatóknak, hogy ők bizony sütiket használnak, hogy fokozzák az élményt, teljesítményt mérjenek, egyezz bele, vagy magadra vess/húzz a fenébe. Az átlagfelhasználónak köze sincs a böngésző sütikhez, a design is olyan, hogy a beleegyezés a hangsúlyosabb (profik ezek, ebből élnek!), simán kapja mindenki tovább a sütit.


## Kulturált megoldás, ritka, mint a fehér holló


Üdítő, hogy vannak olyan, elsősorban szaklapok, mint a HWSW, ahol nem aktív a Facebook, Google+ és társai tetszésnyilvánító és megosztást végző gombjai, azokat külön be kell kapcsolni.


<blockquote>Piros pont érte!</blockquote>


Általánosságban elmondható viszont, hogy a valós megoldásért persze nekünk, a felhasználóknak kell tennünk.


## A radikális megoldás (?)


Lehetünk radikálisak, hogy szépen töröljük magunkat minden szociális hálóról és örökké privát böngészést használva minden alkalommal töröljük a nyomokat. (Ennél még radikálisabb, ha Tor hálózathoz kapcsolt böngészőt használunk, így IP cím alapján sem tudnak minket azonosítani.)

Persze ez meg túl radikális, hiszen így mindig mindenhova újra és újra be kell lépni, a sok webes szolgáltatás és két szintű azonosítás mellett – mert ugye mindenki ilyet használ!? – ez egy kész rémálom.


## „Légyszi ne kövess”


Majd' elfelejtettem, hogy a modern böngészőkben már be lehet állítani, hogy szóljon a weboldalaknak, ha nem akarjuk, hogy kövessenek. Persze, az hogy erre hallgat-e a weboldal, az már nem a böngésző dolga.

Ez kb. olyan, mintha kiírnám a postaládámra, hogy nem kérek szórólapot. _Ó, várj csak!_


## Legyen belőled is szellem!


Számomra a megoldást a [Ghostery](http://www.ghostery.com/) böngésző plugin hozta el. Ez a kis eszköz úgy működik, hogy rendelkezik egy, a plugin készítői által menedzselt adatbázissal, amiben csúnya, rossz követő sütik és JavaScript kódok vannak. Ezeket szépen rendszerezik, elnevezik, le is írják, hogy melyik mire szolgálna.

Futás közben ezt az adatbázist felhasználva tiltja az oldalak ilyen irányú kéréseit. Így megakadályozza, hogy a különböző szkriptek lefussanak, különböző követő böngésző sütik települjenek.

Például, ha be vagy lépve Facebookra, és átsétálsz egy másik oldalra, ahol van Tetszik gomb, akkor az a gomb nem fog látszódni. Így a Facebook nem fogja tudni, hogy ott jársz. Ebből már lehet is sejteni a megoldás legnagyobb hátrányát. Ugyanis, ha pl. Facebook hozzászólás van az adott oldalon, akkor nem fognak látszódni a hozzászólások sem és te sem tudsz hozzászólni.

Persze van erre is megoldás, ideiglenesen lehet engedélyezni a szkriptet, ami a Facebook hozzászólást lehetővé teszi, viszont ilyenkor kibújunk a lepel alól egy kis időre és a Facebook látni fogja, hogy kik vagyunk, merre járunk.


<blockquote>Alternatív megoldásként ilyenkor lehet nyitni egy privát böngésző munkamenetet, ahol betöltjük ugyanezt az oldalt. Ilyenkor a Facebook nem tudja, hogy kik vagyunk, mert a privát böngésző munkamenetben nem vagyunk belépve a közösségi oldalra, viszont azért az IP címünk alapján ki tudja sakkozni, hogy talán mégis kik vagyunk.</blockquote>


De nem csak a Facebook ellen védekezünk így, hanem a Google+, Google Analytics, Google AdSense, AdOcean és még számos egyéb leskelődő ellen.

Egy népszerű magyar blog oldalán például a következő dolgokat blokkolja:



	
  * Adverticum

	
  * Etarget

	
  * Facebook Connect

	
  * Facebook Social Plugins

	
  * Gemius

	
  * Google +1

	
  * Google Analytics

	
  * iWiW Widgets

	
  * Median

	
  * Twitter Button

	
  * Whos.among.us


Ezek nélkül természetesen gyorsabban is jelenik meg az oldal, hiszen le sem futnak, nem zabálják egyáltalán az erőforrást.

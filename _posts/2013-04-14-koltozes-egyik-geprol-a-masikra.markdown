---
author: csiknor
comments: true
date: 2013-04-14 07:55:42+00:00
layout: post
link: http://blog.csik.net/2013/04/14/koltozes-egyik-geprol-a-masikra/
slug: koltozes-egyik-geprol-a-masikra
title: Költözés egyik gépről a másikra
wordpress_id: 169495854
categories:
- Tech
tags:
- os x
- Time Machine
- visszaállítás
---

Ahogy korábban már volt róla szó, [lecseréltem a régi asztali gépem egy újabbra](http://blog.csik.net/2013/03/22/imac-csere-vegre/). Az új gép megvásárlása egyrészt jó alkalom volt, másrészt a szükség is úgy hozta, hogy újratelepítsem az egész operációs rendszert.

Mivel nem volt nálam egyszerre a régi és az új gép is, így több eszköz közbeiktatásával kellett a költözést megoldani, szem előtt tartva, hogy közben ne veszítsek el fontos adatokat.


## A fájlok biztonságba helyezése


Bár rendelkezem széleskörű biztonsági mentéssel (pl.: Time Machine), nem az volt a célom, hogy ennek segítségével állítsam vissza a korábbi rendszert az új gépen. Egyrészt azért, mert a váltással egyúttal operációs rendszer verziót is váltottam (Lion ➝ Mountain Lion), másrészt azért, mert bármennyire okos az OS X, egy idő után felgyülemlik a szemét és lassabb lesz a rendszer működése, mint egy tisztán telepített gép esetében.

A régi gépről minden általam fontosnak ítél könyvtáramat átmásoltam két különböző helyre: egy külső merevlemezre és egy laptopra. Ezeket kiegészítettem még a saját felhasználóm komplett könyvtárával, ami így tartalmazta a felhasználóm _Library_ könyvtárát is, ami minden beállítást tartalmaz. Mint utólag kiderült, sajnos kihagytam a gyökérkönyvtárban lévő _Library_ könyvtárat, de nem volt belőle probléma, hiszen, mint írtam, volt biztonsági mentésem, így abból gond nélkül kiszedtem a szükséges fájlokat. (Csak pár dolog kellett.)

Így a költözés után megállapítható, hogy ha az embernek van egy teljes Time Machine mentése, ami redundáns tárolón van, akkor felesleges külön másolgatással szórakozni. Én is inkább csak azért választottam ezt az utat, mert egyrészt nem volt minden adatom a Time Machine-ban, másrészt egy egyszerű külső merevlemezen van tárolva, ami cseppet sem redundáns. Meg aztán az a biztos, amit én csinálok kézzel, nem az, amit holmi automatizmus!


## Telepítés után a fájlok visszamásolása


Sok alkalmazásnál nincs is szükség semmilyen másolásra, hiszen minden beállítást a felhőben tárolnak. Így ezek (Chrome, Dropbox, Skype, Evernote, Wunderlist) a telepítés és bejelentkezés után szépen letöltötték az aktuális adatokat.

Az egyszerű fájlok, dokumentumok visszamásolása nem problémás, feltéve, ha szem előtt tartjuk, hogy hálózatról másolni sokkal gyorsabb, ha nem Wifi-t, hanem vezetékes kapcsolatot használunk: 5 MB helyett 50 MB-ot tudott így másolni másodpercenként.

Szerencsére az egyes alkalmazásokhoz tartozó fájlok visszaállítása sem nagyobb munka, csak annyival másabb, hogy ott jobban kell figyelni, hogy mit, hova másolunk vissza. Az iTunes esetében csak a _Music/iTunes_ könyvtárat, a Final Cut Pro X esetében a _Movies/Final Cut Pro_ könyvtárat kellett a helyén tartani. A Lightroom is simán beolvasta a korábbi katalógusát, csak meg kellett nyitnom. Mindhárom esetben viszont különösen fontos volt, hogy a hivatkozott fájlok (zenék, videók, fényképek) az eredeti elérési útjukon fellelhetőek legyenek.


## Régi új biztonsági mentés


Mivel a teljes rendszert a nulláról újrahúztam, így logikusnak tűnt, hogy a Time Machine-t is nulláról indítsam. Persze a korábbit archiváltam szépen egy DMG fájlba, ha netán kéne belőle valami, még elérhető legyen.

A [mentésem másik részét viszont az EMC Retrospect végzi](http://blog.csik.net/2011/11/01/a-time-machine-nem-tamogatja-a-halozati-megos/), ennek a konfigurációját nem szerettem volna nulláról újra elkészíteni, így szépen visszaállítottam a régi beállításokat. Ehhez sem kellett többet tenni, mint a _/Library/Application Support/Retrospect_ könyvtár tartalmát a korábbi mentésből visszatölteni.

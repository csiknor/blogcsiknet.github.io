---
author: csiknor
comments: true
date: 2011-09-21 17:01:00+00:00
excerpt: 'Folytatódik az otthoni média rendszer összeállítása. Beszerzésre került
  a NAS. Beszerzésre került a korábban tervezett NAS: D-Link DNS-320. Hozzá egyelőre
  csak 1 darab Samsung SpinPoint F4EG 2TB (HD204UI) merevlemez. (Utóbbi pusztán megszorításból...'
layout: post
link: http://blog.csik.net/2011/09/21/otthoni-media-szerver-a-nas/
slug: otthoni-media-szerver-a-nas
title: 'Otthoni média szerver: a NAS'
wordpress_id: 71514421
categories:
- Kategória nélkül
tags:
- center
- film
- média
- nas
---

_Folytatodik az [otthoni media rendszer](/otthoni-media-szerver-a-terv) osszeallitasa. Beszerzesre kerult a NAS._

Beszerzesre kerult a korabban tervezett NAS: D-Link DNS-320. Hozza egyelőre csak 1 darab Samsung SpinPoint F4EG 2TB (HD204UI) merevlemez. (Utobbi pusztan megszoritasbol, egyelőre nem tartozik az alapellatasba a NAS.)

[![Dns-320_l]({{site.baseurl}}/images/dns-320_l-scaled1000-w=300.jpg)]({{site.baseurl}}/images/dns-320_l-scaled1000.jpg)

A termek osszeszerelese szerintem barkinek menne, aki nem ilyed meg a nyomtatott aramkor latvanyatol, annyira egysszerű:

  1. NAS tetejet levenni
  2. Vinyot betolni (nincs kabel)
  3. NAS tetejet visszarakni
  4. NAS-t a LAN-ba
  5. NAS-t az aramhalozatba

A konfiguralas sem sokkal bonyolultabb, azert nemi kerdest felvetett a termek bevezetese.

  * Egy vinyot nyilvan nem lehet RAID 1-be kotni, de mi lesz, ha jon a masodik vinyo, ugye **tud ugy RAID 1-et epiteni, hogyne vesszenek el a meglevő adatok a regi vinyon?** Szerencser igen.
  * **Mi a tokom az a CIFS?** Hamar rajottem, hogy az a Samba, igy mar rogton kepben voltam.
  * **Nem tudok tobb particiot letrehozni?** Amennyire sikerult megtudnom nem. Sebaj, majd kulon halozati konyvtarakat csinalok, nekem az is jo lesz, sőt jobb, legalabb az egyes konyvtaraknak nem lesz tarhely korlatuk, csak a teljes NAS-nak.

A migralas sosem egyszerű, meg egy ilyen, otthoni kornyezetbe szant esetnel sem.

  * A fenykepeket a Lightroom-mal kell mozgatnom, hogy a kapcsolodo metaadatok is megmaradjanak.
  * A zeneket az iTunes-zal kell mozgatnom, hogy a kapcsolodo metaadatok is megmaradjanak. (Az Apple [biztosit ehhez egy leirast](http://carryflag.blogspot.com/2010/06/imovie-event-library-on-network-drive.html).)
  * A nyers videofelveteleimet iMovie-val kell mozgatnom, hogy a kapcsolodo metaadatok megmaradjanak. (Az iMovie egyebkent nem tamogatja a halozati konyvtarakat, egy felkialtojellel jelzi, hogy az nem fogja hasznalni. Szerencsere [ra lehet birni](http://carryflag.blogspot.com/2010/06/imovie-event-library-on-network-drive.html), hogy ezt a rossz szokasat felejtse el.)
  * Minden mast szerencsere lehet "siman" masolni.

Alapvetően korlatozni szeretnem a NAS-hoz tortenő hozzaferest. A tarolt tartalom nem atlagos felhasznalasra van megtervezve, igy teljesen jogos dolog, hogy nem mindenkinek van irasi, olvasasi joga.

Alapvetően ket reszre vannak bontva a tartalmak:

  * Storage: altalanos fajlok, csak es kizarolag szamitogepes felhasznalasra
  * Media: media fajlok szamitogepes es media lejatszos felhasznalasra

Felhasznalok tekinteteben negy csoportot kulonboztetek meg:

  * sajat magam: teljes hozzaferes a Storage-ra, olvasasi jog (!) a Media-ra
  * gepesz: teljes hozzaferes a Media-ra
  * nező: olvasasi jog a Media-ra
  * vendeg: olvasasi jog a Storage-ra es a Media-ra

A gepesz egy technikai felhasznalo, akivel csak akkor akarok belepni, ha uj tartalmat viszek a Media tarhelyre, ezzel is vedve az ott tarolt tartalmat. Termeszetesen minden felhasznalo jelszoval vedett, nincs anonim hozzaferes.

_Ez egy sorozat resze. Olvasd el az egeszet:_

  * [_Otthoni media szerver: a terv_](http://blog.csik.net/otthoni-media-szerver-a-terv)
  * [_Digitalis atallas: TV_](http://blog.csik.net/digitalis-atallas-tv)
  * _Otthoni media szerver: a NAS_
  * _[Digitalis atallas: TV Antenna](http://blog.csik.net/digitalis-atallas-tv-antenna)_

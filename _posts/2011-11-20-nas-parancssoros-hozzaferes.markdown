---
author: csiknor
comments: true
date: 2011-11-20 21:42:59+00:00
excerpt: Hogy miért van egyáltalán szükséges parancssoros hozzáférésre a NAS-hoz?
  Jó kérdés, tulajdonképpen eddig nem is volt. Viszont mégiscsak egy linux szerver
  az egész, miért ne? Persze azért nem akarok weboldalt futtatni rajta (pedig lehetne).
  Igazábó...
layout: post
link: http://blog.csik.net/2011/11/20/nas-parancssoros-hozzaferes/
slug: nas-parancssoros-hozzaferes
title: 'NAS: Parancssoros hozzáférés'
wordpress_id: 81005555
categories:
- Kategória nélkül
tags:
- dns-320
- fun plug
- nas
- ssh
---

Hogy miert van egyaltalan szukseges parancssoros hozzaferesre a NAS-hoz? Jo kerdes, tulajdonkeppen eddig nem is volt. Viszont megiscsak egy linux szerver az egesz, miert ne? Persze azert nem akarok weboldalt futtatni rajta (pedig lehetne). Igazabol ket ok miatt kellett:

  1. szerettem volna checksum ellenőrzeseket gyorsan vegrehajtani (nem halozaton keresztul letoltve, lokalis gepen)
  2. szerettem volna fajlokat tomoriteni gyorsan (nem halozaton keresztul letoltve, lokalis gepen)

**Telepites**

Az egesz pofon egyszerű, csak kovetni kell a [leirast](http://nas-tweaks.net/40/installation-of-the-fonz-funplug-0-5-for-ch3snas-ch3mnas-dns-323-and-many-more/). Aztan miutan az ember elert az SSH prompthoz gyakorlatilag egy szokasos linux előtt talalja magat.

**Embedded linux**

Azert nem teljesen szokasos, ugyanis ez a DNS-320 flash memoriajaba embeddalt linux, tehat marhara nem pont olyan, mint mas linuxok. Persze marhara hasonlit.

A legtobb dolgot a szokasos parancsokkal erhetjuk el, de itt ezt egyetlen fajlba sűritett [BusyBox](http://busybox.net/)-on keresztul tehetjuk meg. (Egyebkent ezt alig lehet eszrevenni, ugyanis minden parancsra van egy symbolic link a bin-ben.)

Azert van par parancs, ami hianyzott nekem: unrar, cksfv (ez utobbi letezik a BusyBox-ban is, de sajnos nem ette meg a fajlt, amit kuldtem neki).

**Bővitő csomagok**

Szerencsere a kozosseg mar joval előttem jar, igy Fonz es Uli uraknak hala tobb letolthető csomag all a [rendelkezesunkre](http://nas-tweaks.net/82/installing-and-uninstalling-packages-and-activation-and-deactivation-of-daemons-in-fonz-fun_plug/), igy eleg meresz dolgokat is kitalalhatunk.

Én Uli ur [archivalas](http://ffp.wolf-u.li/additional/app-arch/) csomagjaibol telepitettem a vonatkozokat.

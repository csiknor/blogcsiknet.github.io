---
author: csiknor
comments: true
date: 2011-11-01 11:48:03+00:00
excerpt: Az otthoni média rendszerem kialakítása során kellett szembesülnöm azzal,
  hogy az eddigi biztonsági mentésem motorja, a Time Machine nem támogatja a hálózati
  megosztásokat. Írni még csak-csak tud rá, ha a 'defaults write com.apple.systempreference...
layout: post
link: http://blog.csik.net/2011/11/01/a-time-machine-nem-tamogatja-a-halozati-megos/
slug: a-time-machine-nem-tamogatja-a-halozati-megos
title: A Time Machine és a NAS
wordpress_id: 72640596
categories:
- Kategória nélkül
tags:
- biztonsági mentés
- mac
- Retrospect
- Time Machine
---

Az [otthoni media rendszerem kialakitasa](http://blog.csik.net/otthoni-media-szerver-a-terv) soran kellett szembesulnom azzal, hogy az eddigi biztonsagi mentesem motorja, a Time Machine nem tamogatja a halozati megosztasokat.

Írni meg csak-csak tud ra, ha a '_defaults write com.apple.systempreferences TMShowUnsupportedNetworkVolumes 1_' paranccsal rabirjuk. Viszont halozati megosztasrol mentest kesziteni sehogysem szeretne.

Pedig nekem pont erre lenne szuksegem, az adataim ugyanis az iMac belső meghajtojan es ket halozati megosztason keresztul egy NAS-on vannak. A Time Machine-nak pedig az iMac-hez csatlakoztatott kulső Western Digital merevlemezre kellene mentenie.

**Alternativ mentes**

Épp ezert egy alternativ megoldast kellett talalnom, amivel ezt a problemat meg tudom oldani. Az eredmeny a [Roxio Retrospect 8](http://www.roxio.com/enu/products/retrospect/retrospect-mac/default.html) lett, ami egy verprofi biztonsagi mentest keszitő szoftver. Gyakorlatilag mindent meg lehet vele csinalni, amit az ember szeretne:

  * minden platfromot tamogat: Mac, Windows, Linux
  * halozati meghajtorol is tud menteni
  * egyszerre kepes tobb gepről menteni
  * ki lehet valasztani kezzel, hogy pontosan mit szeretnenk menteni
  * lehet szűrőket definialni, hogy bizonyos dolgokat ne mentsen (vagy, hogy csak bizonyos dolgokat mentsen)
  * lehet vele menteni lemezre, szalagra, optikai meghajtora, halozatra es ezek tetszőleges kombinaciojara

[![Retrospect_dashboard]({{site.baseurl}}/images/retrospect_dashboard.png)]({{site.baseurl}}/images/retrospect_dashboard.png)[![Retrospect_sources]({{site.baseurl}}/images/retrospect_sources-scaled1000-w=300.png)]({{site.baseurl}}/images/retrospect_sources-scaled1000.png)[![Retrospect_media_sets]({{site.baseurl}}/images/retrospect_media_sets-scaled1000-w=300.png)]({{site.baseurl}}/images/retrospect_media_sets-scaled1000.png)

Gyakorlatilag ez a legnagyobb baja is, hogy tul sokat tud. Mire az ember megismeri, beuzemeli lemegy a nap. Nem is egyszer.

**Kiegeszitik egymast**

Mivel a NAS-on viszonylag ritkan valtozo fajlok vannak, ezert kulon lehet kezelni ezek menteset a gepen levő, gyakran valtozo fajloketol. Így ugy dontottem, hogy a Retrospect es a Tima Machine egymas mellett, kulonboző feladatokra lesz hasznalvi:

  * a Retrospect menti a NAS-rol az adatokat
  * a Time Machine mentni az iMac-en tarolt adatokat

Az előbbiről csak nehany, kivalasztott dolgot, az utobbirol pedig mindent, kiveve nehany aprosagot.

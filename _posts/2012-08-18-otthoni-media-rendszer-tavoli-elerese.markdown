---
author: csiknor
comments: true
date: 2012-08-18 11:55:00+00:00
excerpt: Tekintve, hogy sikerült egy jó gyors (20/10) internet kapcsolatot létesíteni
  otthon, úgy gondoltam, hogy a már beterezett eszközöket lehetne még több mindenre
  használni. Egyrészt igény volna arra, hogy a család többi tagja is elérje a NAS-t,
  mert ...
layout: post
link: http://blog.csik.net/2012/08/18/otthoni-media-rendszer-tavoli-elerese/
slug: otthoni-media-rendszer-tavoli-elerese
title: Otthoni hálózat biztonságos távoli elérése (avagy OpenVPN és a DD-WRT)
wordpress_id: 154728037
categories:
- Kategória nélkül
tags:
- dd-wrt
- openvpn
- router
- vpn
- wifi
---

Tekintve, hogy sikerult egy jo gyors (20/10) internet kapcsolatot letesiteni otthon, ugy gondoltam, hogy a mar beterezett eszkozoket lehetne meg tobb mindenre hasznalni. Egyreszt igeny volna arra, hogy a csalad tobbi tagja is elerje a NAS-t, mert vannak ott olyan fajlok, kepek, videok, zenek, amik őket is erdekelhetik. Masreszt en is szeretnem, ha tavolrol hozzaferhető lenne az otthoni dolgok joresze.

Mivel a NAS egesz nap megy, az internet eleg gyors, mar csak azt mellett megoldanom, hogyan tudom biztonsagosan elerni az otthoni halozatot. Erre adodott is hamar a valasz: virtualis maganhalozatot (VPN) kell letesitenem a WiFi router segitsegevel.

[![Vpngraphic_final51]({{site.baseurl}}/images/vpngraphic_final51-scaled1000-w=300.png)]({{site.baseurl}}/images/vpngraphic_final51-scaled1000.png)

**DD-WRT a TP-LINK WR1043ND WiFi Router-re**

Ahhoz, hogy VPN-t tudjon kiszolgalni a WiFi router kell, hogy a szoftvere ezt tamogassa. Sajnos a beepitett szoftver csak VPN klienskent tudott volna műkodni, ezert ugy dontottem, hogy a meltan nepszerű [DD-WRT](http://www.dd-wrt.com) firmware-t telepitem a WiFi routerre a gyari helyett.

A [DD-WRT forumaban](http://www.dd-wrt.com/wiki/index.php/Installation) kimeritően hosszu leiras van a telepitesről es a buktatoirol - kicsit paraztam is miatta -, de en egy rovidebb verziot kovettem [Samiux blogjarol](http://samiux.blogspot.hu/2010/03/howto-dd-wrt-on-tp-link-tl-wr1043nd.html?m=1).

  1. DD-WRT letoltese: a [kereső](http://www.dd-wrt.com/site/support/router-database) hasznalataval letoltottem a `factory-to-ddwrt.bin` fajlt (a masik frissiteskor, nem telepiteskor kell)
  2. Beleptem a WiFi router webes feluleten
  3. A gyari szoftver frissitesenel megadtam a DD-WRT firmware fajlat.
  4. Amikor kesz lett, beleptem a router-re parancssorbol (`root` a felhasznalonev, `admin` a jelszo):  
`telnet 192.168.1.1`  
Kiadtam a parancsot:  
`mtd -r erase nvram`  
Ami ujrainditotta a routert.
  5. Az ujraindulas utan mar a DD-WRT fogadott, ahol megadtam az uj admin felhasznalonevet es jelszot es mar keszen is voltam.

**OpenVPN daemon konfiguralas a DD-WRT-ben**

Az OpenVPN beallitasa sajnos nem setagalopp, de azt hiszem vallalkozo kedvű emberkent barki nekikezdhet - főleg egy DD-WRT telepites utan!

Én a [How-To Geek cikket](http://www.howtogeek.com/64433/how-to-install-and-configure-openvpn-on-your-dd-wrt-router/) hasznaltam, mint elsődleges forrast, nagyon hasznos. Meg a hozzaszolasok is! A lepeseket ide nem masolom be, mert eleg sok van belőluk, es kellően jol vannak leirva, illusztralva.

**Egy dologra hivnam fel rogton a figyelmet:** a cikkből masolni es beszurni parancssoros dolgokat nagy korultekintest igenyel, ugyanis az idezőjelek, dupla gondolatjelek a weboldalon nem egyeznek meg a parancssoros valtozattal. Én kezzel javitottam mindenhol az idezőjelet (`"`) es a dupla gondolatjelet (`--`), hogy műkodjon a dolog. Erre a hozzaszolasokban is reszletesen kiternek.

A cikk egyebkent a DD-WRT telepitesevel kezd, tehat akar ezt is lehet kovetni, nekem mar nem kellett, igy azt a reszt nem probaltam.

**Felhasznalas**

Lehet szuttyogni az OpenVPN klienssel is a csatlakozaskor, ha hasznalni akarom az itthoni halozatot, de a kovetkező lepes az lesz, hogy a nagyszulőknel levő WiFi routeren beallitom, hogy csatlakozzon a VPN-hez, mint kliens, es otthonrol is ugy fogom latni a NAS-t, mintha csak a szomszed szobaban lenne!

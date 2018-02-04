---
author: csiknor
comments: true
date: 2013-12-29 16:25:19+00:00
layout: post
link: http://blog.csik.net/2013/12/29/wifi-jelerosito-keszitese-dd-wrt-vel/
slug: wifi-jelerosito-keszitese-dd-wrt-vel
title: Wifi jelerősítő készítése DD-WRT-vel
wordpress_id: 169495988
categories:
- Hogyan
- Tech
tags:
- dd-wrt
- jelerősítés
- wifi
---

Adott egy Wifi-fel lefedett ház, ahol a wifi router helye fix az UTP végpontok miatt. Viszont a hely nem ideális a rádiójelek terjedésének (alacsonyan van, körbe véve vasbetonnal, vastag téglával), így vannak olyan szobák a házban, ahol nincs jel, vagy nagyon gyenge. A probléma nem kicsi, a hálószobai ágyban nincs mindenhol vétel, valamint a fürdőszobában sem megy a Bogyó és Babóca a YouTube-ról!

A megoldás egy Wifi jelerősítő beépítése a rendszerbe. Lehet ilyeneket kapni is, viszont nekem úgy esett, hogy visszakerült hozzám egy régi TP-Link TL-WR741ND Wifi routerem, gondoltam ezzel majd megoldom a jelerősítést. Persze, ágyúval verébre, de ha épp ilyen van itthon, hát épp ilyen van itthon.

[![Repeater_Bridge](/images/repeater_bridge-w=580.jpg)](/images/repeater_bridge.jpg)

Segítségül hívtam a DD-WRT adta lehetőségeket és már úton is voltam a [Repeater Bridge](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge) építése felé.


## Telepítés


Első lépésként a gyári TP-Link szoftvert lecseréltem egy éppen aktuális, a routerhez illő DD-WRT verzióra. Ehhez mindössze a következő lépések kellettek ([alap DD-WRT telepítés](http://www.dd-wrt.com/wiki/index.php/Installation)):



	
  * [hard reset (30/30/30)](http://www.dd-wrt.com/wiki/index.php/Hard_reset_or_30/30/30) a routeren, hogy minden beállítás az alapértékekre álljon

	
  * a számítógépet ideiglenesen leveszem a belső hálózatról

	
  * a router csatlakoztatása a géphez egy UTP kábellel, a DHCP kliens már ki is osztja az IP címeket

	
  * belépés a router webes admin felületére (a reset után 192.168.1.1 és admin/admin az alapértelmezett beállítás)

	
  * a rendszerbeállítások alatt a firmware frissítés menüpontnál feltöltöttem a DD-WRT-t

	
  * pár másodperc és egy automatikus újraindulás után már a DD-WRT jelszóváltoztató felülete fogad, ami után készen is vagyok az első résszel.


A következő a Repeater Bridge építése. A lépések itt is [adottak](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge#Instructions), nem is részletezem. Hacsaknem annyit, hogy a Wireless -> Basic Settings alatt a Wireless Mode: Repeater Bridge opciónál rögtön problémába is futottam, ugyanis nekem ilyen beállítás nem volt. Aztán egy kis keresés után hamar kiderült, hogy azért, mert nekem Atheros chipes routerem van, ott kicsit [más a beállítás](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge#Atheros). Nem minden beállítást sikerült megtalálni és beállítani a leírásnak megfelelően, de próbáltam mindenhol a legtöbb előírt értéket beállítani. Gondolom attól függően, hogy milyen build a DD-WRT és pontosan milyen típus a router, más és más opciók jönnek elő a webes admin felületen.


## Használat


Gyakorlatilag első pöccre működött minden. Szépen újraindult, beállt a router, el is kezdett dolgozni. Lehetett is látni mindkét router admin felületén a másik MAC address-ét, így bíztam benne, hogy a kapcsolat létrejött és működik is.

A teszteléshez is a webes admin felületet használtam. Amikor egy Wifi kliens csatlakozott valamelyik routerhez, szépen követtem, hogy melyiknél jelent meg az új kliens MAC address-e. Aztán, miután jónak tűnt a konfiguráció, szépen elhelyeztem az új routert a tervezett helyére és immár a problémás területeken is ki tudtam próbálni a javulást. Ami szépen jelentkezett is, így nagyon elégedett vagyok az eredménnyel.


### Egyetlen érdekesség


Egyelőre úgy tűnik, hogy az új Wifi alkotta hálózat valamiféleképp külön működik, ugyanis a régi routerre csatlakozva nem látható az új router webes admin felülete, viszont az új routerre csatlakozva látszik a régi router webes admin felülete is. Elképzelhető, hogy ez csak egy beállítás az új routeren, hogy ne védje magát ennyire, talán majd utánaolvasok. Így ugyanis eléggé körülményes bármit is állítani rajta, hiszen először kell egy eszköz, amivel arra a hálózatra csatlakozok, mert csak arról tudom elérni a webes admin felületet. Majd az ágyból eljátszadozom vele. Csak el ne rontsam.

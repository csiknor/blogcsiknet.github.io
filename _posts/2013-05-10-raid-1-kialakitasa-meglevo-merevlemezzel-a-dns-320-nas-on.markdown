---
author: csiknor
comments: true
date: 2013-05-10 16:21:36+00:00
layout: post
link: http://blog.csik.net/2013/05/10/raid-1-kialakitasa-meglevo-merevlemezzel-a-dns-320-nas-on/
slug: raid-1-kialakitasa-meglevo-merevlemezzel-a-dns-320-nas-on
title: RAID 1 kialakítása meglévő merevlemezzel a DNS-320 NAS-on
wordpress_id: 169495889
categories:
- Tech
tags:
- dns-320
- lassú
- nas
- raid
---

<blockquote>Nekem nem sikerült.</blockquote>


Legalábbis a könnyű módszer nem működött. Elvileg van egy olyan lehetőség, hogy az ember azt választja a webes adminisztrációs felületen, hogy formázza le az új merevlemezt a NAS és alakítsa ki a RAID 1 tömböt a régin lévő adatok megtartásával. Csak sajnos nekem ez a kijelölő négyzet nem volt aktív, így nem tudtam ezt választani, amikor ennél a lépésnél jártam.


## Az új lemez formázása sikertelen


De enélkül sem volt egyszerű a helyzet. Elvileg, ha ezt nem választom ki, akkor mint egy független második merevlemez kerül formázásra az új diszk és használhatom a meglévő mellett. Gondoltam meglépem ezt, hátha utána lesznek értelmes választási lehetőségeim a RAID 1 tömb kialakítására. Viszont az inicializáció nálam a formázás során lefagyott. Legalábbis annyira lassú lett, hogy egy éjszaka alatt nem volt képes a 0%-ot átlépni.

[Utánaolvasva](http://forums.dlink.com/index.php?topic=39044.0) látszódott, hogy nem vagyok egyedül a problémával, mások is szembesültek vele. A megoldás sajnos nem volt túlzottan az ínyemre: vegyem ki a régi lemezt, rakjam be az újat, úgy formázzam. Aztán tegyem be a régit és akkor majd mindkettő szépen látszódni fog. Szerencsére ez így működött is.

Viszont továbbra sem volt RAID 1 tömböm. Sőt, sajnos ezek után már nem is lehet kialakítani a tömböt, csak úgy, hogy a tömb készítése közben formázza mindkét lemezt. Ehhez viszont biztonságba kellett helyeznem az adatokat a formázás idejére.


## Két terabyte másolása nem túl gyors


Sajnos nem volt más választásom, így fogtam magam, felkaptam a NAS-t és bevittem a céghez, ahol volt elég tároló kapacitás, hogy ideiglenesen átpakoljam az adatokat. Itt vettem észre a következő problémát. (Pontosabban kicsit előtte.)

Ugyanis 2 TB adatot átmásolni hálózaton keresztül még az elméleti 1 Gbps sebeséggel is négy és fél óra, az én D-Link DNS-320 NAS-ommal viszont ennél hatszor több, mert az olvasási sebesség csak 20-30 MiB/s körül van. A másolás közben viszont azt tapasztaltam, hogy ez a gyakorlatban csak 5-6 MiB/s, ami rettentően kevés.

Kis nyomozás után [kiderült](http://prohardver.hu/tema/dns-320/hsz_292-292.html), hogy a probléma okozója a nagyszerű [fun_plug](http://blog.csik.net/2011/11/20/nas-parancssoros-hozzaferes/). Ha telepítve van, akkor drasztikusan csökken az olvasási sebesség, miközben az írási nem változik! Ki látott már ilyet?! Gyorsan ki is iktattam a képletből az eszközt, rögtön felgyorsult a másolás.


<blockquote>A fun_plug egyébként egy remek eszköz, de rejtély, hogy miért ilyen lassú. Ennek még utána kell járni. Egyelőre nem játszottam vele, van rajta MySQL és P2P kliens is, tehát bőven akad ok, ami lassíthatja. Viszont egyik sem volt aktív, így adódik a kérdés, hogy mi okozza. Teszek pár próbát, még egy USB meghajtóra is kitelepítem a fun_plug-ot – amit régóta tervezek –, hátha ettől felgyorsul az olvasás. (Külön fura, hogy csak az olvasás lassul be, de az írás nem.)</blockquote>


Így csak 24 óra volt az egész. Oda. Aztán 30 óra vissza.

A másolás egyébként esemény nélkül történt, leszámítva talán azt, hogy az ember ne lepődjön meg, ha egy Ext3-as partícióban, amit elsősorban OS X-ből ér el előfordul, hogy kis- és nagybetű különbségektől eltekintve ugyanaz két könyvtár neve, ami kiveri a biztosítékot a Windows-os gépen, ahová ideiglenesen másolja az anyagot.

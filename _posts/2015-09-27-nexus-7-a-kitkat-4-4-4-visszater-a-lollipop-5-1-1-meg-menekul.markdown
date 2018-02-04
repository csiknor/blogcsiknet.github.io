---
author: csiknor
comments: true
date: 2015-09-27 18:12:00+00:00
layout: post
link: http://blog.csik.net/2015/09/27/nexus-7-a-kitkat-4-4-4-visszater-a-lollipop-5-1-1-meg-menekul/
slug: nexus-7-a-kitkat-4-4-4-visszater-a-lollipop-5-1-1-meg-menekul
title: Nexus 7 – a KitKat (4.4.4) visszatér, a Lollipop (5.1.1) meg menekül
wordpress_id: 169496010
categories:
- Hogyan
- Tech
tags:
- android
- kitkat
- leírás
- lollipop
- nexus
---

Alapvetően nem használjuk a Nexus 7-et, de néha a gyerekek előveszik, hogy videót nézzenek rajta, vagy egy-egy játékkal játszanak. Ezek egyikéhez sem kell kimagaslóan nagy teljesítmény, de már a menüben való járkálásnál érezhetően lassú volt a Lollipop. Bár [a cache partíció törlése](http://9to5google.com/2014/11/19/2012-edition-nexus-7-running-slow-after-installing-lollipop-this-might-help/) javított a dolgon, a problémát gyökeresen mégsem oldotta meg.


<blockquote>Ezért úgy döntöttem, hogy mennie kell, jöjjön vissza a KitKat (4.4.4).</blockquote>


Szerencsére a visszatelepítés nem egy vészes mutatvány, én is az egyik Google kereséssel megtalált [leírással](http://www.gottabemobile.com/2015/01/30/how-to-downgrade-android-5-0/) dolgoztam.


<blockquote>Annyit mindenféleképp érdemes szem előtt tartani, hogy az összes adat és alkalmazás törlésre kerül az eszközről.</blockquote>


A telepítés a következő lépések szerint zajlott:



	
  1. Le kell tölteni a megfelelő eredeti szoftvert a [Google weboldaláról](https://developers.google.com/android/nexus/images). Ki kell választani a megfelelő eszközt, nálam ez a **"nakasi" for Nexus 7 (Wi-Fi)** eszköz **4.4.4 (KTU84P)** verziója volt. A letöltött fájl tömörítsük ki egy tetszőleges helyre.

	
  2. Fel kell telepíteni az ADB szoftvert, ami a számítógép és az eszköz közötti kommunikációt végzi. Mivel Mac-et használok, én az [XDA oldalán lévő leírás](http://forum.xda-developers.com/showthread.php?t=2564453) alapján végeztem a telepítést az alábbi paranccsal, de [ugyanott azt írják Windows alatt](http://forum.xda-developers.com/showthread.php?t=2588979&__utma=248941774.236267929.1403796127.1403796127.1403796127.1&__utmb=248941774.4.10.1403796127&__utmc=248941774&__utmx=-&__utmz=248941774.1403796127.1.1.utmcsr=google%7Cutmccn=%28organic%29%7Cutmcmd=organic%7Cutmctr=%28not%20provided%29&__utmv=-&__utmk=25906750) is megy a dolog.

    
    bash <(curl -s https://raw.githubusercontent.com/corbindavenport/nexus-tools/master/install.sh)




	
  3. Ahhoz, hogy USB-n keresztül lehessen vezérelni a készüléket, be kell kapcsolni a megfelelő opciót. Ez egy fejlesztői beállítás, ezért először azt kell aktiválni a **Beállítások > A táblagépről** opció alatt a **Build-szám**ra koppintva egymás után párszor (szépen mutatja, mennyi kell még). Ezután elérhetővé válik a **Beállítások > Fejlesztői lehetőségek > USB hibakeresés** opció, amit be kell kapcsolni.

	
  4. Ki kell kapcsolni a készüléket.

	
  5. Tartsuk lenyomva _bekapcsoló_ és a _hangerő le_ gombokat, amíg meg nem jelenik a _Fastboot_ menü

	
  6. Csatlakoztassuk a készüléket a számítógéphez egy USB kábellel

	
  7. Egy terminál ablakból (parancssor) ki kell nyitni a _bootloader_-t (a sudo parancs miatt meg kell adni a számítógépen használt felhasználó jelszavát)

    
    sudo fastboot oem unlock<em>
    </em>




	
  8. A hangerő gombokkal erősítsük meg a műveletet a készüléken, majd a bekapcsoló gombbal hajtsuk végre

	
  9. A terminál ablakkal oda kell navigálni, ahová le lett töltve az eredeti Android 4.4.4, majd ott el kell indítani a újratelepítést a következő paranccsal

    
     sudo ./flash-all.sh





Amikor elkészül, automatikusan újraindul a készülék és már készen is vagyunk.

A telepítés során én csak egyetlen problémával találkoztam, valamiért sehogy sem akartak felmászni az adatok a készülékre, mindig valamilyen USB olvasási hibára hivatkozott. Mint kiderült csak valamilyen USB csatlakozási probléma volt, egyszerűen egy másik USB aljzatot használva gond nélkül ment minden.

Képekért nyugodtan nézzétek meg a hivatkozott leírásokat, vagy egyszerűen [keressetek rá a témára a YouTube-on](https://www.youtube.com/results?search_query=nexus+7+downgrade+to+4.4).

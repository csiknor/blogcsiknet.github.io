---
author: csiknor
comments: true
date: 2015-10-05 06:21:00+00:00
layout: post
link: http://blog.csik.net/2015/10/05/a-nas-biztonsagi-mentese/
slug: a-nas-biztonsagi-mentese
title: A NAS biztonsági mentése
wordpress_id: 169496028
categories:
- Hogyan
- Tech
tags:
- biztonsági mentés
- ffp
- fun_plug
- nas
---

Az embernek van egy NAS-a tükrözött merevlemezekkel és azt hihetné, hogy az adatai biztonságban vannak. De persze nem, hiszen bármikor véletlenül letörölheti, felülírhatja a fontos fájljait, ami ellen nem véd semmiféle tükrözés. Persze trükközni lehet (bocs).


<blockquote>Biztonsági mentés márpedig a NAS-on tárolt adatokhoz is kell.</blockquote>


Eddig manuálisan végeztem a mentést egy, az iMac-hez csatolt külső meghajtóra, de úgy alakult, hogy elfogyott rajta a hely (a Time Machine is oda dolgozott), ezért változtatnom kellett. Azt találtam ki, hogy mehet a NAS-ra a Time Machine, a DNS-320 úgyis beépítetten támogatja ezt a funkciót, így több hely marad a NAS mentésnek a külső merevlemezen.

Viszont, ha már így belenyúltam, gondoltam elviszem innen az asztalról ezt a zörgő dögöt – mármint a külső meghajtót – és közvetlenül a NAS-hoz csatlakoztatom. Már csak valami jó kis automatizált, inkrementális biztonsági mentést végző szoftvert kellett találnom.

Gyakran a legegyszerűbbek a legjobb megoldások, ezért fogtam magam és felkerestem a régi ismerősömet, az [rdiff-backup](http://www.nongnu.org/rdiff-backup/)-ot. Ez a kis parancssoros alkalmazás egész ügyesen bánik a biztonsági mentéssel, megbízhatóan készít inkrementális mentéseket, méghozzá úgy, hogy a fájlokat változatlanul, az eredeti könyvtárstruktúrának megfelelően tárolja. Így a visszaállítás gyakorlatilag csak egy másolás a mentésből az eredeti helyre.


## Telepítés


Először győződjünk meg róla, hogy minden szükséges csomagkezelő be van regisztrálva. Az _uwsiteloader.sh_ paranccsal legyenek bekonfigurálva a következők: _fonz, Mijzef, Uli, Kylek, barmalej2_.


### Python és a függőségei


Mivel az _rdiff-backup_ egy python szkript, ezért először az interpretert kell telepíteni ([részletesebben](http://forum.nas-central.org/viewtopic.php?f=249&t=10879)):

    
    slacker -Uui br2:python/
    
    slacker -ui s:bzip2 s:zlib br2:expat s:gcc-solibs uli:gdbm-1.10 br2:gettext br2:libiconv br2:libffi br2:ncurses s:openssl br2:readline mz:sqlite-3.7.10 s:uClibc-solibs
    
    slacker -ui s:autoconf s:automake s:binutils s:bison s:flex br2:intltool s:gcc s:gmp s:linux-headers s:make-3.81 s:mpfr s:pkg-config s:uClibc


Ha az alábbi parancs üres kimenetet produkál, azaz nem ad semmi hibát, akkor rendben felment:

    
    python -c "import site"




### rdiff-backup


Jöhet maga az rdiff-backup szkript. Ez sajnos nem érhető el egyelőre egyik csomagkezelőn keresztül sem, de a csomagot kézzel letöltve és telepítve gyorsan elérhetővé tehetjük:

    
    wget http://downloads.zyxel.nas-central.org/Users/barmalej2/ffp/0.7/arm/packages/testing/rdiff-backup-1.2.8-arm-1.txz
    
    funpkg -i rdiff-backup-1.2.8-arm-1.txz
    
    rm rdiff-backup-1.2.8-arm-1.txz




## Használat


A biztonsági mentés készítése annyira egyszerű, mint az alábbi parancs, csak meg kell adni, hogy honnan-hova szeretnénk menteni:

    
    rdiff-backup /mnt/HD/HD_a2/<könyvtár> /mnt/USB/HD_c1/<könyvtár>


Ezt aztán kézzel futtathatjuk amikor akarjuk, vagy egy ütemezett feladatot is beállíthatunk a cron segítségével.

Hogy ne nőjön túlságosan nagyra a biztonsági mentés mérete ajánlott a régi mentéseket törölni a következő paranccsal (ez az egy hónapnál régebbi mentéseket törli):

    
    rdiff-backup --remove-older-than 1M --force /mnt/USB/HD_c1/<könyvtár>

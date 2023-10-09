---
author: csiknor
layout: post
date: 2023-10-08 14:00:00+02:00
title: Viszlát D-Link, Helló Synology NAS!
categories:
- Hogyan
- Tech
tags:
- NAS
- Plex
- Restic
- Docker
---

A D-Link DNS-320 NAS már több, mint 12 éve szolgált minket. Gyakorlatilag alig változott valami, amióta megvettem: bár próbálkoztam parancssoros hozzáféréssel, és egyéb szolgáltatások telepítésével, végül az eredeti szoftverrel, és ugyanazzal a két Samsung merevlemezzel fejezte be a pályafutását.

Az ok a cserére, elég prózai, az egyik nap azt vettem észre, hogy

> hiányzik az utóbbi egy év összes fotója! 

Nem kicsit lettem ideges, főleg, amikor láttam, hogy a cloud backup sem tartalmazza (ennek mondjuk más oka volt). Kis nyomozás után kiderült, hogy nem vesztek el az adatok, csak sajnos a NAS egy-egy újraindítás után nem tudta mindkét merevlemezt életre kelteni, így hol az egyikkel, hol a másikkal indult el. Tehát a fájlok megvoltak, csak éppen nem mindkét merevlemezen – ennyit a RAID 1-ről. Már korábban is tapasztaltam, hogy nehezen indult el a NAS, de mindig azt hittem, hogy a RAID-del nincs probléma.

Mivel más okból kifolyólag is szerettem volna új NAS-t, ezért úgy döntöttem, hogy nyugdíjazom a jó örgeg D-Link tárolót, és jöhet egy új. Az új eszközzel szemben az elvárások a következőek voltak:
* a régi merevlemezeket gond nélkül tudjam használni (bár elég idősek, úgy döntöttem, hogy még bizalmat szavazok nekik)
* természetesen támogasson RAID 1 tárolást
* gyors hálózati sebességet várok el tőle (a mostani egyáltalán nem volt képes kihozni a maximumot sem a meghajtókból, sem a hálózat sebességéből, még olvasáskor sem)
* sok funkcióra és aktívan fejlesztett szoftverre van szükségem (a régi alig kapott frissítéseket, és – bár egész sok funkcióval rendelkezett – nem fedte le minden igényem)
* Plex média szervert akarok futtatni rajta
* a Restic biztonsági mentéseket a B2 Cloud-ba közbetlenül a NAS-ról akarom futtatni
* torrent kliensre van szükségem
* adott esetben távolról is hozzáférhető legyen
* képes legyen tetszőleges szoftver futtatására

A választás végül a Synology DS220+ NAS-ra esett, a következő indokok miatt:
* szerepel a Plex támogatott NAS eszközök listáján, rááadásul hardveres transcoding támogatással (Kétmagos, 2,0 GHz-es Intel Celeron J4025, 2 GB DDR4 integrált memória, ami 6 GB-ig bővíthető)
* gond nélkül megeszi a két Samsung merevlemezt
* 2 db gigabites LAN csatlakozóval rendelkezik (bár nekem egy is elég lesz)
* sajnos nem értek hozzá eléggé, de a leírások alapján a Btrfs fájlrendszer és a Synology Hybrid RAID elég meggyőzően hangzott
* saját csomagként elérhető Plex szerver, torrent kliens, stb.
* Docker támogatás, amin keresztül gyakorlatilag bármi futtatható, számomra pl. a Restic kliens
* Rengeteg egyéb funkció, távoli Synology account, amikkel még csak ismerkedem

Egyelőre maximálisan meg vagyok elégedve az eszközzel. Hihetetlenül kézre áll minden, mind hardveres, mind szoftveres értelemben. Nagyon kényelmes, és gyors, egyelőre még nem ütköztem bele a korlátaiba. Különösebb gond nélkül telepítettem a Plex szervert és a Restic klienst is. Az előbbinél ugyan kicsit nehezebben találtam meg a belső felhasználót, aminek jogot kell adnom a fájlokat tartalmazó könytárakra. Az utóbbi viszont meglepően könnyen ment, [`restic-backup-docker`](https://github.com/lobaro/restic-backup-docker) segítségével.

Egyetlen apró problémába ütköztem a Synology DSM felületének használata közben, amikor a Docker konténert igyekeztem konfigurálni: az üres környezeti változókat nem akarta elfogadni, holott ez a kép pont ezt várta el. A megoldás az lett, hogy exportáltam a konténer beállításokat JSON-ba, ott átírtam a környezeti változók értékét üresre, majd importáltam őket.

A következő lépés a Plex további használata lesz, már most elérhetőek rajta a családi videók, a következő a fényképek lesznek – bár nem arra találták ki, meglepően jó támogatása van.
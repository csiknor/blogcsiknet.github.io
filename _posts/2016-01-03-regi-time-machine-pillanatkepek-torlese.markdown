---
author: csiknor
comments: true
date: 2016-01-03 10:04:27+00:00
layout: post
link: http://blog.csik.net/2016/01/03/regi-time-machine-pillanatkepek-torlese/
slug: regi-time-machine-pillanatkepek-torlese
title: Régi Time Machine pillanatképek törlése
wordpress_id: 169496041
categories:
- Hogyan
- Tech
tags:
- os x
- Time Machine
---

Kézzel törölni pillanatképeket a Time Machine biztonsági mentésből kétféleképpen is lehet. A legegyszerűbb természetesen, ha fogjátok magát a Time Machine grafikus felületét, kiválasztjátok a jobboldali idősávban a kívánt mentést, majd a fogaskerék ikonra kattintva kéritek a pillanatkép törlését.

![backup-2]({{site.baseurl}}/images/backup-2.png)

Sok pillanatkép esetében viszont ez elég fárasztó lehet, ilyenkor a jó öreg parancssoros felület siet a segítségünkre. A Terminal alkalmazást elindítva a következő paranccsal kilistázható az összes pillanatkép.

    
    tmutil listbackups


Ezek közül már szabadon törölhetünk az alábbi paranccsal - értelemszerűen az útvonalat a megfelelőre kell változtatni, hogy pontosan mire, azt az előző parancs adta meg. Törölni csak rendszergazdai jogokkal lehet, ezért a sudo parancs kérni fogja a jelszavad.

    
    sudo tmutil delete "/Volumes/Time Machine Backups/Backups.backupdb/iMac/2015-10-03-224551"


Ez persze még mindig egyesével töröl, de mivel a parancssorban remek szkripteket lehet írni, könnyen lehet automatizálni.

Abban az esetben, ha ti is egy hálózati meghajtóra mentetek - nem pedig egy külső lemezre, ami pl. USB-vel van csatlakoztatva - akkor a fenti törléssel még nem nyertetek szabad helyet. Ez azért van, mert az OS X ún. [sparse image](https://en.wikipedia.org/wiki/Sparse_image)-ben tárolja a mentést, ami alapesetben csak nő, ahogy a tartalma nő, viszont nem csökken, ha törlünk róla - mint ahogy tettük az előbb, amikor a pillanatképeket töröltük.

Szerencsére erre is van egy parancs, az alábbi, ami a felesleges területet felszabadítja, ezáltal végre a hálózati meghajtón is jelentkezik a szabad hely.

    
    hdiutil compact /Volumes/TimeMachine/iMac.sparsebundle


Minderre főleg olyankor lehet szükség, ha ti sem tudtok külön kvótát megadni a Time Machine mentésnek a hálózati meghajtón, mint ahogy minden D-Link ShareCenter felhasználó.

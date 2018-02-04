---
author: csiknor
comments: true
date: 2016-12-10 13:18:00+00:00
layout: post
link: http://blog.csik.net/2016/12/10/time-machine-takaritas/
slug: time-machine-takaritas
title: Time Machine takarítás
wordpress_id: 169496093
categories:
- Hogyan
- Tech
tags:
- backup
- mac
- os x
- Time Machine
---

A biztonsági mentés gyakori téma, szeretem amennyire lehet biztonságban tudni az adataim. Viszont hamar túl méretesre tudnak nőni a mentett archívumok, különösen inkrementális mentés esetén.

Így van ez a Time Machine esetében is, különösen, ha hálózati meghajtóra ment az ember. A DNS-320 biztosít egy Mac OS X kompatibilis Time Capsule funkciót, egyetlen hátránya, hogy nem tudom korlátozni a méretét. Ez azt jelenti, hogy pont akkorára nőhet, mint a teljes tárhely. Ez pedig egyáltalán nincs összhangban a Time Machine filozófiájával, miszerint addig őrzi a régi mentéseket, amíg van szabad hely.

Szerencsére van megoldás, még ha manuális is. Enrico [körüljárta](http://thegreyblog.blogspot.hu/2014/03/shrink-your-time-machine-backups-and.html) a problémát és készített is egy hasznos kis [szkriptet](https://github.com/emcrisostomo/Time-Machine-Cleanup), amivel a régi mentéseket törölni tudjuk.

Telepítés után csak kiadjuk a parancsot, és máris (pár perc azért kellhet hozzá) oda vannak a régi mentések, csak a frissek maradtak.

    
    $ sudo tm-cleanup.sh -d 30


Egy dologról nem szabad viszont megfeledkezni, ahogy a cikkben Enrico is megjegyzi, ezzel még nem nyertünk szabad helyet. Ez azért van, mert a Sparse Bundle, amit a Mac OS X használ nem lett kisebb. Ehhez egy külön parancsot kell lefuttatni, miután kész a törlés – ne felejtsük el, hogy le kell választani a nyitott köteget; nekem ez úgy ment legkönnyebben, hogy kijelentkeztem.

    
    sudo hdiutil compact /Volumes/TimeCapsule/<a mentés neve>.sparsebundle

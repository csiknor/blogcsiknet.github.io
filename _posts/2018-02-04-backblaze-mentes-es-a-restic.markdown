---
author: csiknor
layout: post
date: 2018-02-04 20:26:12+01:00
title: A Backblaze mentés és a Restic
categories:
- Hogyan
- Tech
tags:
- restic
- backblaze
- biztonsági mentés
---

Már egy ideje tervezem, hogy a biztonsági mentéseket külső szolgáltatóra bízzam. Mivel nem kis adatmennyiségről van szó (>500 GB), nem volt triviális, hogy melyik szolgáltatót válasszam. Számtalan olyan megoldás létezik, ahol korlátlan helyet kaphat az ember a mentéseinek, de a legtöbb ilyen úgy biztosítja be magát, hogy csak a saját szoftverén keresztül lehet feltölteni. Ez pedig az esetek nagy százalékban nem működik az én esetemben, nekem ugyanis a NAS-on vannak a mentendő fájlok.

Végül a [Backblaze](https://backblaze.com) mellett döntöttem, mert kellően olcsó, és meglehetősen jó integrációk léteznek hozzá. Ez utóbbiak közül én a [Restic](https://restic.net) mellett döntöttem. Elsősorban azért, mert pont azt az inkrementális mentést tudja, amit korábbad az [rdiff-backup](http://www.nongnu.org/rdiff-backup/) kapcsán megszerettem, valamint azért, mert támogatja a kliens oldali titkosítást. Ez utóbbi nélkülözhetetlen egy felhős mentés esetén.

Bár létezik ARM architektúrára is fordított bináris, a NAS túl gyengének bizonyult, hogy az töltse fel a fájlokat, maradtam inkább a Mac-nél. A szkript meglehetősen egyszerű, csak arra kell felkészülni, hogy a `restic` megkapja a megfelelő környezeti változókat, illetve, hogy a NAS fel van csatolva, mint hálózati mappa.

## Előkészületek

Elsőként a `Backblaze` fiók és azon belül egy "bucket" létrehozása a feladat. 

![Bucket létrehozása]({{site.baseurl}}/images/backblaze-bucket.png)

{{site.baseurl}}

Ne felejtsük el kiolvasni a fiókhoz tartozó azonosítót és titkos kulcsot sem. 

![Account ID kiolvasás]({{site.baseurl}}/images/backblaze-account-id.png)

## Szükséges szoftverek telepítése

A telepítés rém egyszerű, hála a homebrew csomagkezelőnek.

```bash
$ brew install restic
```

## Biztonsági mentés készítése

Ezeket a környezeti változókat fogja keresni a `restic` a futás közben, hogy beazonosítsa a `Backblaze` fiókot és titkosítsa a mentést.

```bash
export B2_ACCOUNT_ID="<a backblaze fiók azonosítója>"
export B2_ACCOUNT_KEY="<a backblaze fiók kulcsa>"
export RESTIC_PASSWORD="<a mentés jelszava>"
```

Az első lépés a mentés inicializálása – ez még nem fog feltölteni semmit sem. A "bucket"-en belül külön könyvtárakat hozok létre, így a különböző dolgokat egymástól függetlenül tudom kezelni. A `b2.connections` számomra kicsit gyorsabbá tette a feltöltést, ezért használom.

```bash
restic -o b2.connections=100 -r "b2:$B2_BUCKET_NAME:/$BACKUP_DIR" init
```

Ha kész az inicializálás, lehet kezdeni a mentést.

```bash
restic -o b2.connections=100 -r "b2:$B2_BUCKET_NAME:/$BACKUP_DIR" backup "$BACKUP_HOST/$BACKUP_DIR"
```

Ez valószínűleg jó sokáig fog tartani, ugyanis a feltöltés nem túl gyors, nekem 2-5 MB/s sebességgel kúszott fel. De ha bármikor megszakítjuk, ugyanezzel a paranccsal képes a `restic` folytatni a munkát amíg készen nem lesz. Ebből áll majd az inkrementális mentés is.
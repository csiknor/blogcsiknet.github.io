---
author: csiknor
comments: true
date: 2013-03-11 07:29:00+00:00
excerpt: A NAS beszerzése után kezdett fájni a fejem, hogy most akkor milyen protokollon
  keresztül és hogyan csatoljam fel a megosztott meghajtókat a Mac alá. Alapvetően
  az AFP irányba hajlottam, mondván mégiscsak az a natív Apple megoldás. Aztán a Mac
  OS ...
layout: post
link: http://blog.csik.net/2013/03/11/autofs-vs-mounted-by-user/
slug: autofs-vs-mounted-by-user
title: 'Mac OS X: hálózati meghajtó csatolása'
wordpress_id: 87159414
categories:
- Tech
tags:
- afp
- autofs
- mount
- nas
- nfs
- smb
---

A NAS beszerzése után kezdett fájni a fejem, hogy most akkor milyen protokollon keresztül és hogyan csatoljam fel a megosztott meghajtókat a Mac alá.

Alapvetően az AFP irányba hajlottam, mondván mégiscsak az a natív Apple megoldás. Aztán a Mac OS X Lion tett róla, hogy felejtsem el az AFP-t, így próbálkoztam SMB (CIFS) irányban.

Viszont mindkettőnél ugyanaz a probléma többször felmerült: hogyan legyen csatolva a meghajtó? Olyan megoldást kerestem, ahol nem kell folyton kézzel csatolni, csak rábökök a könyvtárra és jön a tartalom, ha kell maga csatolja.

Mondván, ez egy okos rendszer gyorsan utána is olvastam.


# Finder


Van ugye a Finder alap szolgáltatása a Connect to server, amivel gyorsan lehet csatlakozni, sőt még az adott felhasználó Login items-ei közé is lehet helyezni így automatikusan megy a csatolás.

Nem volt igazán kielégítő számomra, mert bár nagyon hatékony és mindig felcsatolja a mappát, alapvetően nem mindig ugyanazt a könyvtárat használja a fájlrendszeren a csatoláshoz, így nem lehet különböző programokből fiyen hivatkozni rá.


# NFS


Van egy remek NFS támogatás is a Mac OS X-ben, kár hogy az NFS annyira béna (legalábbis az általam használt verzió), hogy autentikálás, mint olyan nincs benne. (Viccesen úgy is szokták mondani a betűszót, hogy No File Security.) Valamint valamilyen rejtélyes okból kifolyólag azokat a szóközöket, amiket nem a Mac OS X-ből raktam a könyvtárakba egyszerűen nem volt hajlandó megkajáln a Finder és hibát dobott az olvasásnál. Érdekes módon a Terminál ugyanekkor nem problémázott, probléma nélkül olvasott mindenféle könytárból.


# AutoFS


Szerencsére a Mac OS X egy ideje már támogatja azt a megoldást, ahol szépen parancssorból beállítva képes a hálózati meghajtók automatikus csatolására, ha egy könytárba tévedek. Ezt a linux rendszerekhez hasonlóan az fstab-ból is lehet vezérelni, de azért biztos, ami sicher csináltak egy autofs konfigurációt is, mégiscsak több lehetsőget tárnak elénk.

Szépen meg is csináltam, ahogy kell: az auto_master fájlban hivatkoztam egy általam készített (előbb auto_afp, majd SMB-re térés után) auto_smb fájlra, ahová felvittem a szükséges parancsokat.

Úgy működött, mint egy álom, ha kattintottam, jött a könyvtár, tudtam használni, aztán jött a DE.


## Mounted by user


Egyrészt ugyanis néha úgy gondolta, hogy nem az én felhasználóm nevében, hanem inkább a root felhasználó nevében kéne csatolni, ilyenkor én már hiába látogattam meg az uminózus könytárat, egyszerűen le lettem koptatva: nincs jogom a könyvtárhoz.

Ezt lokálisan orvosolni lehetett egy sudo umount /Volumes/Storage utasítással, de ez hosszú távon nem volt járható.

Sok helyen problémáztak ezzel a felhasználók, de nekem volt egy gyanúm, hogy ez nem feltétlenül bug. Ugyanis a root user csak akkor mountolhatta ezt fel, ha egy folyamat megpróbálta elérni ezt a könyvtárat úgy, hogy az root joggal fusson.

Na ilyen folyamatból elég kevés lehet a rendszerben, ugyanis ezeket a könytárakat főleg én használom. Egy kivétel volt: a Retrospect Enginge. Így hát kikapcsoltam nem is oly régen, és azóta mindig rendben megy a mount.

DE.


## Írásvédett csatolás


Sajnos néha úgy csatolja fel ez a szerencsétlen a megosztásokat, hogy nem lehet bele írni. Ennél még furcsább, hogy könyvtár hozható létre, de fájlt már nem tudok másolni.

Egyelőre itt még egy megkerülő megoldással dolgozom: ha nincs jogom írni, akkor jöhet a Finder és kapcsolódok a szerverhez ismét, ahol már minden rendben van, tudok írni is.


# Fenébe az egészet


A végén annyira kerestem már a jó megoldást, hogy annyi munkaórát raktam bele, hogy nem értelme az egésznek. Így most visszatértem a legegyszerűbb megoldáshoz: kézzel csatolom fel őket, amikor szükség van rájuk. Mivel az esetek túlnyomó többségében csak alvó állapotba teszem az iMac-et, így csak a maradék elenyésző esetben, kikapcsolás után kell felcsatolnom a köteteket.

---
author: csiknor
comments: true
date: 2013-05-12 15:30:26+00:00
layout: post
link: http://blog.csik.net/2013/05/12/nas-okositas-fonz-fun_plug-modra-transmission-mysql-mindez-usb-rol-futtatva/
slug: nas-okositas-fonz-fun_plug-modra-transmission-mysql-mindez-usb-rol-futtatva
title: 'NAS okosítás Fonz fun_plug módra: Transmission, MySQL – mindez USB-ről futtatva'
wordpress_id: 169495905
categories:
- Hogyan
- Tech
tags:
- dns-320
- fun_plug
- mysql
- nas
- torrent
- transmission
- usb
---

A D-Link DNS-320 felturbózása nem nagy művészet, egy jól megírt leírás alapján mindenkinek könnyen mehet. Van is ilyenből jópár, a magamét csak azért írom meg, hogy én is emlékezzek rá, ha mit, hogyan csináltam.


<blockquote>Aki nem tudná, arról van itt szó, hogy a NAS-on futó operációs rendszer lehetővé teszi, hogy minden egyes induláskor lefusson egy ún. "fun_plug" szkript. Ez egy amolyan funkció plugin, amit ügyes emberek arra használtak ki, hogy a gépben lévő ARM processzort, 128 MiB memóriát és a gépen lévő linux disztribúciót arra használják, amire csak lehet.

Webszerver, adatbázis-szerver, médiaszerver, P2P szerver és még sorolhatnám az elérhető funkciókat, mert annyi van belőlük. Persze ne feledjük, hogy ez egy nem egy erőgép, csak korlátozott mértékben alkalmas különböző szolgáltatások üzemeltetésére.

Én a Fonz fun_plug 0.7-es verzióját használom.</blockquote>


Nem szájbarágós a leírás, alap tudást és ismereteket feltételezek linuxról, hálózatról az egyes szolgáltatásokról, amikről szó lesz.


## Fonz fun_plug telepítése HDD-re


Első lépésként hagyományos módon telepítettem a Fonz fun_plug 0.7-es verzióját a gépre. A "hivatalos" dokumentációban található [leírást](http://nas-tweaks.net/371/hdd-installation-of-the-fun_plug-0-7-on-nas-devices/) követtem. Érdemes megnézni, ha esetleg elakadnál, sok speciális esetet én nem írok le, mert nálam egyszerűen nem jött elő.


<blockquote>**FIGYELEM!** Alapvető hiba volt, hogy nem állítottam be jól a hálózatot a NAS-on és amikor telepítés közben akartam valamit letölteni vele, akkor nem sikerült. Ezért az admin felületen állítsuk be a hálózati címet, DNS-t, valamint a routeren a tűzfalat úgy, hogy a NAS képes legyen az internetről adatokat letölteni.</blockquote>




### Letöltés, telepítés


A program két fájlból áll: a _fun_plug_ szkriptből, illetve a _fun_plug.tgz_ fájlból. Előbbi fut le minden indítás után, utóbbi tartalmazza az egyéb fájlokat.

Letöltés után a _Volume_1_ könyvtárba kell helyezni mindkettőt, innen fogja indítani a NAS a fun_plug szkriptet. (OS X és Safari esetén érdemes odafigyelni, hogy a letöltés után a Safari automatikusan kicsomagolja tgz fájlból a tar fájlt, amire viszont nem számít a Fonz fun_plug az első induláskor, így nem is sikerül neki a telepítés.)

Az egyetlen dolog, amire ilyenkor oda kell figyelni, hogy legyen jog bőven a szkriptre: állítsuk nyugodtan 777-re a _fun_plug_ fájl jogait.

Ezután egy újraindítás és már automatikusan lefut és települ is a Fonz fun_plug. Persze ez egy kis időbe telik, onnan fogjuk észrevenni, hogy készen van, hogy látjuk, hogy eltűnik a tgz fájl. Ha ezt nem tenné, akkor nézzük meg a _fun_plug.log_ fájlt, amiben szépen le van írva, hogy mi történt.


### Parancssoros hozzáférés konfigurálása: ssh


Nyissunk a számítógépünkön egy terminál ablakot és először a telnet segítségével lépjünk be a gépre. Ehhez semmilyen felhasználónév, jelszó nem szükséges, csak a gép IP címe a telnet parancsnak.

Ezután adjuk ki a következő parancsokat a root felhasználó könyvtárának és jelszavának kialakítása érdekében:

    
    usermod -s /ffp/bin/sh root
    mkdir -p /ffp/home/root/
    sed -ie 's#:/home/root:#:/ffp/home/root:#g' /etc/passwd
    pwconv


Ha olyan üzeneteket kapunk, hogy _"usermod: no changes"_, vagy _"pwconv: failed to change the mode of /etc/passwd- to 0600"_, akkor ne aggódjunk, ez teljesen normális.

Ezután hozzuk létre a root felhasználó jelszavát és jelentkezzünk is be vele:

    
    passwd
    login


Mivel egy ramdisk-en fut a NAS operációs rendszere, a jelszó csak ott kerül tárolásra, ergo egy újraindítás után elfelejti a gép. A következő szkripttel tudjuk permanensen tárolni:

    
    wget http://wolf-u.li/u/172/ -O /ffp/sbin/store-passwd.sh
    store-passwd.sh


Állítsuk be automatikus indításra és indítsuk is el az ssh démont:

    
    chmod a+x /ffp/start/sshd.sh
    sh /ffp/start/sshd.sh start


Egy új terminál ablakot nyitva a számítógépünkön próbáljunk ssh paranccsal csatlakozni a NAS-hoz. Ha sikerült, állítsuk is le a telnet démont, nincs rá szükség:

    
    chmod -x /ffp/start/telnetd.sh
    sh /ffp/start/telnetd.sh stop




### Programok telepítése: a csomagkezelő


Ahhoz, hogy új programokat tudjunk könnyen telepíteni a NAS-ra a legegyszerűbb, ha van egy csomagkezelő telepítve. Ezt kell letölteni, majd a megfelelő csomag kiszolgálókat kiválasztani (én a _fonz_, mijzelf, _uli_, _kylek_ kiszolgálókat választottam):

    
    wget http://wolf-u.li/u/441 -O /ffp/bin/uwsiteloader.sh
    chmod a+x /ffp/bin/uwsiteloader.sh
    uwsiteloader.sh




### P2P, torrent: akkor Transmission


A kedvenc torrent kliensem asztali környezetben is a Transmission, külön jó, hogy hála a webes kezelőfelületnek, szerver oldali alkalmazásként is nagyszerűen használható.

A telepítés a csomagkezelőn keresztül történik a [leírás](http://bernaerts.dyndns.org/appliance/226-dns325-ffp7-transmission) szerint. A Transmission-ön kívül a curl csomagra is szükség van, ezt használja a torrent kliens:

    
    slacker -a Transmission
    slacker -a curl
    slacker -a libevent


Egy kis konfigurálás, hogy indításkor melyik könyvtárba dolgozzon:

    
    mkdir /ffp/var/transmission
    chown -R nobody /ffp/var/transmission


Ezt rögzíteni kell az indító szkripten is. Megnyitjuk szerkesztésre, és az elején átírjuk a könyvtár értékét:

    
    vi /ffp/start/transmission.sh



    
    <em>TRANSMISSION_HOME=/ffp/var/transmission</em>


Ezután el kell indítani, hogy létrehozza az alapértelmezett konfigurációs fájlt.

    
    sh /ffp/start/transmission.sh start


Sok mindent át lehet írni, én csak az alábbiakat alakítottam:

    
    vi /ffp/var/transmission/settings.json





	
  * _download-dir_: ide tölti a fájlokat (ne felejtsük el létrehozni a könyvtárat, ezt megtehetjük a saját gépről is egy fájl kezelővel; pl.: /mnt/HD/HD_a2/torrent/)

	
  * _rpc-whitelist_: ezekről az IP címekről lehet elérni a webes klienst (vesszővel elválasztott lista, pl.: 192.168.*.* minden helyi hálózaton található gépről elérhetővé teszi a felületet)

	
  * _umask_: ilyen maszkkal látja el a fájlokat a hozzáférés szempontjából (én a 0-t választottam, így minden joga megvan bárkinek)


A titkosított kommunikációhoz a Transmission szeretne véletlen számokat generálni, ezért hozzáférést kell adni a véletlenszám generátorhoz. Módosítsuk az inicializáló fájlt azzal, hogy hozzáadjuk az alábbi sort:

    
    vi /ffp/etc/fun_plug.init



    
    <em>chmod o+r /dev/random /dev/urandom</em>


A Transmission-t is beállítjuk automatikusan induló szolgáltatásnak, majd újraindítjuk:

    
    chown -R nobody /ffp/var/transmission
    chmod a+x /ffp/start/transmission.sh
    /ffp/start/transmission.sh start


Ezzel készen is vagyunk, egy böngészőből már el is indíthatjuk a klienst (használd a NAS-od IP címét): http://192.168.0.107:9091/


### MySQL adatbázis-kezelő telepítése


Szükségem volt még egy MySQL adatbázisra is, így azt is telepítenem kellett. A [leírással](http://nas-tweaks.net/96/installation-and-configuration-of-mysql-on-fonz-fun_plug/) ellentétben, mivel legalább az 5.5-ös verzió kellett, ezért a kylek csomag kiszolgálóból kellett letöltenem:

    
    slacker -a mysql-5.5


A konfigurálás során először létre kellett hozni a konfigurációs fájlt, és a szükséges könyvtárakat, ahová a MySQL a fájlokat pakolja:

    
    cp /ffp/etc/examples/mysql/my.cnf /ffp/etc/
    mkdir -p /ffp/opt/srv/mysql
    mkdir -p /ffp/opt/srv/tmp/mysql
    ln -s /ffp/opt/srv/ /srv


Ez utóbbit szintén permanensé kell tenni, hogy újraindítás után is megmaradjon. A fájl végére szerkesszük be a parancsot:

    
    vi /ffp/etc/fun_plug.init



    
    <em># create custom link to the server-folder
    ln -s /ffp/opt/srv/ /srv</em>


A MySQL számára létre kell hozni az alap rendszertáblákat:

    
    cd /ffp
    mysql_install_db


Ahhoz, hogy másik gépről is el lehessen érni az adatbázist, módosítani kell a konfigurációt. Egyrészt az indító szkriptben ki kell venni, a hálózati működés tiltását, másrészt a konfigurációs fájlban be kell állítani, hogy a NAS IP címére kösse magát a szolgáltatás:

    
    vi /ffp/start/mysqld.sh



    
    <em># Removed: --skip-networking 
    mysqld_flags="--user=root"</em>



    
    vi /ffp/etc/my.cnf



    
    <em>bind-address = 192.168.xxx.xxx</em>


A MySQL-t is automatikusan induló szolgáltatásnak állítjuk és el is indítjuk:

    
    chmod a+x /ffp/start/mysqld.sh
    /ffp/start/mysqld.sh start


Jó pár dolgot lehet még a MySQL konfigurálásánál végezni, én adtam jelszót a root felhasználónak:

    
    /ffp/bin/mysqladmin -u root password 'new-password'
    /ffp/bin/mysqladmin -u root -h ShareCenter-1 password 'new-password'




## Fonz fun_plug futtatása USB-ről


Több szempontból is érdekes lehet a Fonz fun_plug USB meghajtóról történő futtatása. Elsősorban azért, mert így az FFP nem mozgatja a merevlemezeket, ha írni akar valamelyik fájljába (pl. naplófájlok), azok tudnak kikapcsolt állapotban pihenni. Ez a halk és energiatakarékos működés miatt fontos lehet.


<blockquote>Sajnálattal, de nem túl nagy meglepetéssel tapasztaltam ez nem jelentett megoldást arra, hogy durván belassul az olvasás a NAS-ról, ha fut a Fonz fun_plug. Erre még keresni kell egy megoldást, mert tűrhetetlen, hogy 40 MiB/s helyett 6 MiB/s sebességgel tudok csak olvasni.</blockquote>


Ezt a folyamatot is egy [leírás](http://bernaerts.dyndns.org/dns325/242-dns325-ffp7-move-usb-key) alapján végeztem, szokás szerint a részletekért érdemes megnézni azt is. Volt viszont egy apró különbség. Tekintve, hogy csomagkezelőt használok, próbáltam itt is úgy dolgozni, hogy meglévő csomagokat teszek fel, ahol szükséges. Az egyetlen ilyen pont az volt, hogy módosítani kell a beépített chmod parancsot, mert egy bug miatt minden USB eszköz tartalmát 777 joggal látja el a NAS.

Ezért telepítettem [a megkerülő megoldást](http://nas-tweaks.net/434/uwchmod-fix-for-a-issue-with-the-firmware-of-some-d-link-devices/):

    
    slacker -a uwchmod


Leválasztottam az USB meghajtót, hogy tudjam particionálni és formázni:

    
    umount /dev/sdc1


Viszont a particionálás nem sikerült, ugyanis sem az _fdisk_, sem a _cfdisk_ nem akart futni. Elindultak, de rögtön ki is léptek. Szerencsémre viszont a formázást a már meglévő partíción is el lehetett végezni, így gond nélkül átugrottam ezt a lépést, és már készítettem is az Ext2 fájlrendszert a meghajtóra:

    
    mke2fs /dev/sdc1


Felcsatoltam és átmásoltam a teljes FFP könyvtárat az USB meghajtóra:

    
    mount /dev/sdc1 -t ext2 /mnt/USB/HD_c1 -o noatime
    cp -a /mnt/HD/HD_a2/ffp /mnt/USB/HD_c1


Ahhoz, hogy az induláskor a Fonz fun_plug ezt a könyvtárat használja, szólni kell. Erre használja az FFP a _.bootstrap/setup.sh_ szkriptet:

    
    mkdir /mnt/HD/HD_a2/.bootstrap
    chmod 777 /mnt/HD/HD_a2/.bootstrap
    vi /mnt/HD/HD_a2/.bootstrap/setup.sh




_[Tartalma a Pastebin-en!](http://pastebin.com/p9RFftsU)_


Ujraindítás után már az USB-ről indult el a Fonz fun_plug.


<blockquote>A _setup.sh_ szkript képes még arra is, hogy biztonsági mentést készítsen az USB meghajtóról, hiszen most minden változást oda rögzít. A biztonsági mentést a NAS lemezeire készíti, ami azért is hasznos, mert úgy működik az indítás, hogy ha az USB meghajtó nem elérhető, akkor a Fonz fun_plug a merevlemezen lévő könyvtárat használja.</blockquote>

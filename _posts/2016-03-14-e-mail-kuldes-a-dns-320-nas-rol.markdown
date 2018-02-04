---
author: csiknor
comments: true
date: 2016-03-14 20:28:13+00:00
layout: post
link: http://blog.csik.net/2016/03/14/e-mail-kuldes-a-dns-320-nas-rol/
slug: e-mail-kuldes-a-dns-320-nas-rol
title: E-mail küldés a DNS-320 NAS-ról
wordpress_id: 169496070
categories:
- Hogyan
- Tech
tags:
- e-mail
- fun_plug
- nas
---

Alapvetően maga a NAS is tud e-mailt küldeni különböző események bekövetkeztekor, mint például a merevlemezek időszakos ellenőrzése. Ehhez nem kell mást tenni, mint beállítani a megfelelő postafiók adatokat a


<blockquote>Management -> System Management -> Notifications oldal Email Settings részénél.</blockquote>


A különös rész ott kezdődik, ha a Fonz Fun_Plug telepítése után parancssorból, vagy egy szkriptből szeretnénk e-mailt küldeni. Szerencsére a kettőt viszonylag könnyű kombinálni. Ha a korábban említett webes adminisztrációs felületen sikerült beállítani a levélküldést, akkor lesz két fájl a fájlrendszeren, amit használhatunk:

    
    /etc/.msmtprc
    /etc/.muttrc


Ez a két fájl tartalmazza ugyanis azokat a beállításokat, amikkel az e-mail elküldhető. Ahhoz, hogy ezeket használjuk csak meg kell adnunk a levél tárgyát és tartalmát, valamint természetesen a címzett címét a mutt parancsnak, miközben hivatkozunk ezekre a fájlokra:

    
    echo "Ez a levelem tartalma" | mutt -F /etc/.muttrc -s "A levél tárgya" valaki@postafiok.hu


Az echo parancs helyett akár egy fájl teljes tartalmát is elküldhetjük a cat parancs segítségével, innentől ez már csak rajtunk áll.

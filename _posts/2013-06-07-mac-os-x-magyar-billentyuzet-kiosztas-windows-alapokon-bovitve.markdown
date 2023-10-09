---
author: csiknor
comments: true
date: 2013-06-07 18:29:35+00:00
layout: post
link: http://blog.csik.net/2013/06/07/mac-os-x-magyar-billentyuzet-kiosztas-windows-alapokon-bovitve/
slug: mac-os-x-magyar-billentyuzet-kiosztas-windows-alapokon-bovitve
title: 'Mac OS X: magyar billentyűzet kiosztás Windows alapokon – bővítve!'
wordpress_id: 169495936
categories:
- Lifehack
- Tech
tags:
- írásjelek
- billentyűzet
- gondolatjel
- idézőjel
- kiosztás
- mac
- magyar
- os x
---

Módosítottam a [korábbi billentyűzet kiosztásom](http://blog.csik.net/2011/07/07/mac-magyar-billentyuzet-kiosztas-windows-modr/). Egyrészt pótoltam néhány hiányzó karaktert, másrészt kibővítettem olyanokkal, amiket kellene használni, de alapesetben nincs a billentyűzeten. Lásd a [magyar írásjelekről szóló korábbi bejegyzésem](http://blog.csik.net/2013/05/30/pusztulnak-az-irasjelek-ha-nincsenek-a-billentyuzeten/)!

[![Alt módosítóval](/images/alt-w=580.png)](/images/alt.png)

Alt (⌥) módosítóval bekerült még pár hasznos deviza karakter, és kikerült, ami nem tartozik oda.

A megvalósításban segítségemre volt, hogy megtudtam azt, hogy az AltGr módosító mellett más nyelvek alkalmazzák az AltGr+Shift kombinációt is. Ilyenkor egy billentyű négy karaktert tud megjeleníteni:



	
  * módosító nélkül

	
  * Shift módosítóval

	
  * AltGr módosítóval

	
  * AltGr+Shift módosítóval


Így alkalmazva az Alt (⌥) és Shift (⇧) kombinációt újabb karaktereket vezettem be. Elsősorban olyanokat, amiket a magyar nyelvben és úgy általában a mindennapokban kell használnunk.

[![Alt Shift](/images/alt-shift-w=580.png)](/images/alt-shift.png)

Ezzel a módosító párral elérhetővé válnak a következő karakterek:



	
  * idézőjelek minden szinten: „bla »bla ’bla bla’ bla« bla bla”

	
  * gondolatjel, hármaspont: –, …

	
  * fok, perc (vagy hüvelyk), másodperc: °, ″, ′

	
  * matematikai jelek: ¬, ±, ⋅, ‰, √

	
  * pár hasznos karakter: ⌥, ⌘, ©, ®, ™



Sajnos van vele gond is, ugyanis sok helyen – mint például itt, a Wordpress szerkesztőjében – vannak olyan billentyűkombinációk, amik valamilyen parancsot hajtanak végre.

A telepítés nagyságrendileg nem változott:


<blockquote>Sorstársak kedvéért csatoltam a kiosztást a post-hoz, melyet egyszerűen a `Keyboard Layouts` könyvtárba kell rakni a `/Library` vagy a `~/Library` könyvtáron belül, majd bekapcsolni a`System Preferences`, `International` moduljának `Input` fülén.</blockquote>


[A magyar billentyűzet kiosztás letöltése](https://dl.dropboxusercontent.com/u/430331/Hungarian%20Windows.keylayout)

---
author: csiknor
comments: true
date: 2011-07-07 20:23:00+00:00
excerpt: Ez egy régi bejegyzés, de a népszerűsége miatt úgy gondoltam, hogy újra meg
  kell osztanom veletek. Vannak dolgok, amik nagyon mások a Mac OS-X alatt, mint ahogy
  megszoktam Windows alatt. Az egyik ilyen dolog a billentyűzet. Az egy dolog, hogy
  a bi...
layout: post
link: http://blog.csik.net/2011/07/07/mac-magyar-billentyuzet-kiosztas-windows-modr/
slug: mac-magyar-billentyuzet-kiosztas-windows-modr
title: 'Mac: Magyar billentyűzet kiosztás Windows módra'
wordpress_id: 60041830
categories:
- Kategória nélkül
tags:
- billentyűzet
- mac
- magyar
- ukelele
---

<blockquote>**Figyelem! **Bővítettem a kiosztást, egy [újabb bejegyzésben elérhetőek a változások](http://blog.csik.net/2013/06/07/mac-os-x-magyar-billentyuzet-kiosztas-windows-alapokon-bovitve/).</blockquote>


Ez egy régi bejegyzés, de a népszerűsége miatt úgy gondoltam, hogy újra meg kell osztanom veletek.

Vannak dolgok, amik nagyon mások a Mac OS-X alatt, mint ahogy megszoktam Windows alatt. Az egyik ilyen dolog a billentyűzet. Az egy dolog, hogy a billentyűzet német, ezt még megértem, mert kint vettem a gépet. Miután átváltok magyar billentyűzet kiosztásra, tökéletesen mennek az ékezetes betűk ezzel nincs is semmi hiba.

A probléma inkább az egyéb speciális karakterekkel van, mint a szögletes zárójel, a kisebb-, nagyobb jel, vagy a kukac. Ezeket nap, mint nap használom, és már be van égve a helye a kezembe, sőt, bent a cégnél lévő PC-ken is ezt használom továbbra is, tehát nincs sok értelme új helyeket megtanulni. Az egyetlen megoldás a billentyűzet kiosztás meváltoztatása.

Természetesen, mint mindenre erre is van megoldás. Egy kis Google keresés után rá is találtam az [Ukelele](http://scripts.sil.org/ukelele) alkalmazásra, ami lehetővé teszi, hogy könnyen, grafikus felületen tudjuk szerkeszteni a Mac OS-X XML alapú billentyűzet-kiosztását. Egy kis kattingatás után el is készítettem a Windows-os kisztásnak megfelelő magyar billentyűzetemet, úgyhogy immár a megszokott rutinoknak megfelelően tudok speciális karaktereket írni a Mac-en is.

Sorstársak kedvéért csatoltam a kiosztást a post-hoz, melyet egyszerűen a `Keyboard Layouts` könyvtárba kell rakni a `/Library` vagy a `~/Library` könyvtáron belül, majd bekapcsolni a `System Preferences`, `International` moduljának `Input` fülén.

Fájl letöltése: [Hungarian WIN.keylayout](http://dl.dropbox.com/u/430331/csiknet/Hungarian%20WIN.keylayout)

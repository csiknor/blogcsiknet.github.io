---
author: csiknor
comments: true
date: 2011-11-15 22:27:12+00:00
excerpt: 'Figyelem! Mélyen szakmai tartalmú, ún. geek poszt.Megjegyzés: A poszt címéből
  következő 1-2. rész nem létezik írásos formában. Annak idején az első voltam az
  ismerőseim körében, aki Mozilla Firefoxról Google Chromera váltott. Nagyon megtetszett
  má...'
layout: post
link: http://blog.csik.net/2011/11/15/bongeszo-haboru-chrome-vs-firefox/
slug: bongeszo-haboru-chrome-vs-firefox
title: 'Böngésző háború: Chrome vs. Firefox - 3. rész'
wordpress_id: 80275261
categories:
- Kategória nélkül
tags:
- böngésző
- chrome
- firefox
- mac
- memória
- os x
---

_Figyelem! Melyen szakmai tartalmu, un. geek poszt._  
_Megjegyzes: A poszt cimeből kovetkező 1-2. resz nem letezik irasos formaban._

Annak idejen az első voltam az ismerőseim koreben, aki Mozilla Firefoxrol Google Chromera valtott. Nagyon megtetszett mar első latasra a bongesző letisztult felulete, gyorsasaga es funkcioi.

[![Google_chrome](http://csiknet.files.wordpress.com/2011/11/google_chrome-scaled1000.png?w=300)](http://csiknet.files.wordpress.com/2011/11/google_chrome-scaled1000.png)

Aztan nem is olyan regen, talan par honapja - amikor a Mozilla kicsit eszbe kapott es nagyobb fokozatra kapcsolta a fejlesztest - visszatertem a jo oreg Firefoxra, mert ugy ereztem, hogy a Chrome tul sok memoriat zabal.

Nagy megelegedessel hasznaltam a Firefox-ot ismet, viszont par dolog azert zavart:

  * a Chrome sokkal, de tenyleg sokkal gyorsabb
  * a Chrome kenyelmesebben kezeli a privat bongeszest, mint a Firefox
  * a Chrome tovabbra is [a legszebb bongesző](http://csiknor.posterous.com/a-legszebb-bongeszo-google-chrome-for-mac-os)

Most, hogy [bővitettem a memoriat az iMac-ben](http://blog.csik.net/memoriabovites-imac-msi-wind), ugy gondoltam nem lehet akadaly az sem, ha kicsit tobbet eszik a Chrome, megeri. (Tekintsunk most el attol az aprosagtol, hogy egy gepen, egy felhasznalo alatt ket profilt kezelni szepen Mac OS X alatt nem olyan egyszerű. Egy ora alatt megoldottam, hogy Anita es en is sajat Chrome bongeszőt hasznaljunk egymas mellett.)

A memoria foglalas a Chrome tekinteteben nem egy egyszerűen szamithato ertek. Firefoxnal konnyű dolga van az embernek, van ket folyamat: a Firefox es a PluginContainer, amit merni kell (utobbi a Flash plugin miatt). Ezzel szemben Chrome eseteben rengeteg folyamat van: a bongeszőnek egy, minden fulnek kulon-kulon egy, minden kiterjesztesnek kulon-kulon egy. Sok.

Hasznalhatnam a Chrome belső folyamat kezelőjet, ahol szepen osszesitve is elerhető a memoriafoglalas, de az [a Google szerint sem pontos](http://code.google.com/p/chromium/issues/detail?id=25454). Mivel osszeadogatni nem volt kedvem az egyes folyamatokat ugy dontottem, hogy inkabb a Mac OS X beepitett Activity Monitor alkalmazasaval merem a memoria foglalast.

A tesztelt kornyezet:

  * nagyjabol ugyanazok a kiterjesztesek voltak elerhetők mindket bongeszőre
  * mindegyiken ugyanazokat az oldalakat nyitottam meg: Facebook, Gmail, Google Reader, Koponyeg, Twitter
  * mindket bongeszőt nullarol inditottam

Az eredmeny:

  * Firefox: 410 MB memoria foglalas
  * Chrome: 420 MB memoria foglalas (sajat bevallasa szerint 690 MB, a kettő kulonbsege valoban alatamasztja a Google velemenyet, miszerint alaposan elszamoljak a sajat meresuket)

A kulonbseg szamomra meglepő (azt hittem a Chrome tenyleg tobbet eszik), viszont abszolut elfogadhato, igy matol ismet Chrome felhasznalo vagyok.

Abba most ne menjunk bele, hogy minek egy bongeszőnek cirka fel gigabajt memoria, hiszen ebből egy komplett operacios rendszes is kepes elfutni.

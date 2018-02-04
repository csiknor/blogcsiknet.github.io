---
author: csiknor
comments: true
date: 2015-09-29 06:28:00+00:00
layout: post
link: http://blog.csik.net/2015/09/29/meghekkeltek-a-wifi-router-dns-beallitasat/
slug: meghekkeltek-a-wifi-router-dns-beallitasat
title: Meghekkelték a WiFi router DNS beállítását
wordpress_id: 169496006
categories:
- Tech
tags:
- dns
- hack
- router
---

Táv segítséggel „irtottam vírust” a minap. A probléma az volt, hogy internetezés közben mindenféle felugró ablakokban különböző reklámok jelentek meg. Ami fura volt, hogy számítógéptől függetlenül mindenhol jelentkezett a probléma, még mobilon is.

Ezek alapján már esélyes volt, hogy nem lokális problémáról van szó, a WiFi router megvizsgálása után pedig egyértelmű volt, hogy ott van a probléma.


<blockquote>Gyakorlatilag a DNS szerver címe lett átírva a WiFi router beállításaiban.</blockquote>


Tekintve, hogy a 195.238.181.164 egy ukrán IP-cím esélytelen volt, hogy egy valós Invitel cím legyen.

Természetesen a root jelszót átírta maga mögött a hacker, ami valószínűleg egy bot volt, ami sérülékeny routerek után kutatott a neten. Így kizárva más eszköz nem maradt, csak az, hogy hardveresen resetelni kellett a szoftvert, mindent visszaállítani a gyári beállításokra és újrakezdeni.

A vicc az volt, hogy én nem voltam a helyszínen, sőt, sosem láttam a készüléket, de még a helyik topológiát sem. Ez picit megnehezítette a dolgot, főleg, miután kiderült, hogy minden fogyasztó WiFi-n keresztül csatlakozott a routerhez, ezért a gyári beállítások visszaállítása után senki nem tudott csatlakozni hozzá, lévén a WiFi is alapértelmezésbe került. Így távsegítséggel UTP kábelt kellett találni, sőt, el kellett magyarázni, hogy mi az, hogy néz ki, hova kell bedugni.

Aztán persze sok-sok perc telefonálás és guglizás után (kellettek képek arról, hogy néz ki a router menürendszere, úgy mondtam, hogy hova kell kattintani!) végre sikerült mindent beállítani és még a root jelszót is megváltoztattuk. Persze gőzöm sincs, hogy azóta erre emlékszik-e bárki.

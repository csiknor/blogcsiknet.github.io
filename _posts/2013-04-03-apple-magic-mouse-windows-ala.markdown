---
author: csiknor
comments: true
date: 2013-04-03 20:28:49+00:00
layout: post
link: http://blog.csik.net/2013/04/03/apple-magic-mouse-windows-ala/
slug: apple-magic-mouse-windows-ala
title: Apple Magic Mouse Windows alá
wordpress_id: 169495829
categories:
- Hogyan
- Tech
tags:
- apple
- driver
- magic mouse
- windows
---

Magam sem tudom, hogy miért akartam ezt megcsinálni. De mivel adott volt egy Windows-os laptop és nem akartam vezetékes egérrel bíbelődni, amikor itt van egy Bluetooth-os, gondoltam miért ne?

Ahogy utánaolvastam kiderült, hogy annyira azért nem támogatott, de megoldott. Van Windows-os meghajtó, hiszen a Boot Camp miatt készített egyet az Apple, viszont ez nem érhető el külön, csak a Boot Camp-pel együtt. Arra viszont nincs szükség, így okos emberek kiszedték a Boot Camp-ből a meghajtót, amit így már lehet telepíteni. Töltsétek csak le a [Magic Tools for Windows](http://www.trackpadmagic.com/magic-mouse/download) oldaláról. (Ez tulajdonképpen leszedi a teljes Boot Camp-et, amiből aztán csak a meghajtót telepíti fel.)

Miután feltelepítette magát, a Vezérlőpultban lévő Bluetooth eszköz keresés segítségével rá kell keresni az egérre. Miután megtalálta, ki kell választani a listából, majd a rendszer szépen használatba veszi a szükséges meghajtót sok-sok töltögetés után. Bal gomb, jobb gomb, görgetés, minden frankón működik.

A Magic Mouse Utilites-t én nem telepítettem, mert bár érdekelne a Natural Scroll, de a vírusirtóm "_módosult Win32/Packed.Themida kéretlen alkalmazás_" miatt figyelmeztetett. Úgy döntöttem, inkább kihagyom.

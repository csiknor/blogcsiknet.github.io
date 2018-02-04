---
author: csiknor
comments: true
date: 2013-05-14 06:51:22+00:00
layout: post
link: http://blog.csik.net/2013/05/14/az-ffp-extra-terhelese-miatt-lassu-az-olvasas-a-nas-on/
slug: az-ffp-extra-terhelese-miatt-lassu-az-olvasas-a-nas-on
title: A Fonz fun_plug extra terhelése miatt lassú az olvasás a NAS-on
wordpress_id: 169495918
categories:
- Tech
tags:
- dns-320
- fonz
- fun_plug
- lassú
- nas
---

Mint ahogy [korábban](http://blog.csik.net/2013/05/12/nas-okositas-fonz-fun_plug-modra-transmission-mysql-mindez-usb-rol-futtatva/) [már írtam](http://blog.csik.net/2013/05/10/raid-1-kialakitasa-meglevo-merevlemezzel-a-dns-320-nas-on/), nagyon lassú az olvasás a D-Link DNS-320 NAS-on, ha fut a Fonz fun_plug. Annyira, hogy az elvárható 30 MiB/s helyett csak 5-6 MiB/s az olvasási sebesség. Írásban érdekes módon nincs lassulás.

A miértre egyelőre nincs válasz, de az ok egyértelmű: minél több extra funkció fut, annál gyorsabb az olvasás. Ahogy sorra kapcsoltam ki a szolgáltatásokat (MySQL, Transmission, SSH, Fonz fun_plug) lett egyre gyorsabb. Tette mindezt annak ellenére, hogy egyáltalán nem terhelték ezek a szolgáltatások a NAS-t, mert egyetlen aktív kapcsolata sem volt egyiknek sem. De úgy látszik, hogy a memória terhelésük akkora volt, hogy ez belassított.

<blockquote>Viszont, mivel elsősorban a NAS fő szolgáltatása a hálózati meghajtó maradéktalan kiszolgálása, ezért úgy döntöttem, hogy leállítom a szolgáltatásokat.
> 
> </blockquote>

A nagyobb érvágás kétségtelenül a Transmission, ugyanis nagyon kényelmes a letöltés vele. Távolról, egy webes felületen is elérhető, nem kell folyton bekapcsolva hagyni a számítógépet, hiszen a NAS mindig megy. Ezért utána is néztem gyorsan, és úgy néz ki, hogy bár nem túl egyszerűen, de megoldható, hogy a TP-Link TL-WR1043ND wifi routeren futó DD-WRT segítségével is képes leszek futtatni a Transmission-t. Igaz ilyenkor csak egy USB meghajtóra, de talán jobb is ez így, akkor legalább nem megy folyton a NAS-ban lévő merevlemez.

Remélem nem fogja túlterhelni szegény kicsikét, már [így is van dolga bőven](http://blog.csik.net/2012/08/18/otthoni-media-rendszer-tavoli-elerese/), legalábbis adtam neki DDNS és OpenVPN kezelési utasításokat a sima PPPoE, DHCP és WiFi routerkedés mellett.

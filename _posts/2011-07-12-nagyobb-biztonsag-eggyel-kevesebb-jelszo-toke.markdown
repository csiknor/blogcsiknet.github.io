---
author: csiknor
comments: true
date: 2011-07-12 20:21:04+00:00
excerpt: Az online banki ügyintézés mindig is kedves volt számomra, mert úgy lehet
  pénzügyeket intézni, hogy közben nem kell bankba menni, sorszámot húzni, várni,
  és a nem túl felkészült ügyintézővel beszélgetni. Viszont az interneten elérhető
  szolgáltatás...
layout: post
link: http://blog.csik.net/2011/07/12/nagyobb-biztonsag-eggyel-kevesebb-jelszo-toke/
slug: nagyobb-biztonsag-eggyel-kevesebb-jelszo-toke
title: 'Nagyobb biztonság, eggyel kevesebb jelszó: tokenes bejelentkezés a bankba'
wordpress_id: 60673428
categories:
- Kategória nélkül
tags:
- bank
- biztonság
- token
---

Az online banki ugyintezes mindig is kedves volt szamomra, mert ugy lehet penzugyeket intezni, hogy kozben nem kell bankba menni, sorszamot huzni, varni, es a nem tul felkeszult ugyintezővel beszelgetni.

Viszont az interneten elerhető szolgaltatasoknal mindig ott lebeg felettunk, hogy fel is torthetik, vissza is elhetnek vele, ez pedig egy banki rendszernel eleg huzos, leven penzről van szo.

A legtobb bank megoldja ezt kulonboző eszkozokkel, de mivel nem akarjak nagyon terhelni a felhasznalokat, elsősorban olyan megoldasokat alkalmaznak, amik lathatatlanok, technikai jellegűek, csak sajnos ilyenkepp sebezhetőek is. Az egyetlen, amivel a felhasznalokat nyaggatjak a jelszo, amit raadasul parhavonta meg is kell valtoztatni.

Mivel a jelszo egy eleg rossz eszkoz (kitalalhato, visszafejthető, leirhato) celszerű olyan megoldast alkalmazni, ami ezt kivaltja. Az egyik elterjedt megoldas a felhasznalonev, jelszo parost kiegeszitő SMS-ben erkező kod. Nem vagyok nagy biztonsagi szakember, de azt hiszem nem tevedek nagyot, ha ugy gondolom, hogy alkalmas eszkozzel ezek a mobilra erkező informaciok lehallgathatok. Bar nagy mertekben javitjak a jelszoval elerhető biztonsagot atlagos felhasznalas eseten, de megsem adnak kellő biztonsagot.

![Dp250_hires](/images/dp250_hires-scaled500.jpg)

Egy masik megoldas az un. [token](http://en.wikipedia.org/wiki/Security_token) alkalmazasa. Ez egy kis szamologephez hasonlo eszkoz (gombokkal, vagy anelkul), ami egy előre meghatarozott algoritmus alapjan egy pszeudoveletlen kodot general. Az előre meghatarozott algoritmus segitsegevel ugyanezt a kodot a bank is legeneralja a szerverein, igy azonosit be minket. Segitsegevel a szo szerint a kezunkben tudjuk tartani a belepő kulcsot a bankba.

Ami kis tovabbi pluszt ad az SMS-ben erkező kodhoz kepest, hogy nincs szukseg kulon jelszora, igy arra emlekezni sem kell, elfelejteni sem tudjuk es nem kell parhavonta megvaltoztatni.

Az egyetlen veszely, ha elhagyjuk, ilyen esetekre szolgal a gombokkal ellatott verziokon a PIN kod kerese hasznalat előtt.

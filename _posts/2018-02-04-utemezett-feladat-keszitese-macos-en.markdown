---
author: csiknor
layout: post
date: 2018-02-04 20:41:12+01:00
title: Ütemezett feladat készítése MacOS-en
categories:
- Hogyan
- Tech
tags:
- Mac
- OS X
- MacOS
- launchd
---

A célravezető eszköz a `launchd` használata, ha időzítetten szeretnénk szkriptet futtatni MacOS-en. Szerencsére nem kell kézzel megírni a `plist` fájlt, elég használni a [launchd generátort](http://launched.zerowidth.com).

Megadjuk a parancs nevét, a szkript útvonalát és az időzítést, meg pár extra opciót, ha akarjuk és már mehet is a generálás. Letöltés után pedig dönthetünk, hogy milyen hatókörbe helyezzük el az ideális futtatás kedvéért.

```bash
/Library/LaunchDaemons/ # felhasználó bejelentkezése nélkül lefut
/Library/LaunchAgents/  # bármilyen felhasználó belépése esetén lefut
~/Library/LaunchAgents/ # saját felhasználónk belépése esetén lefut
```
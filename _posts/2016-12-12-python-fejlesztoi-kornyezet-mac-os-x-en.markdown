---
author: csiknor
comments: true
date: 2016-12-12 07:11:41+00:00
layout: post
link: http://blog.csik.net/2016/12/12/python-fejlesztoi-kornyezet-mac-os-x-en/
slug: python-fejlesztoi-kornyezet-mac-os-x-en
title: Python 2 és 3 fejlesztői környezetek Mac OS X-en
wordpress_id: 169496115
categories:
- Hogyan
- Tech
tags:
- fejlesztés
- IDE
- mac
- os x
- python
---

Ott kezdődött az egész, hogy szerettem volna megtanulni egy funkcionális nyelvet, lehetőleg valami olyat, amit tudok is használni a gyakorlatban, meg kellően távol áll a Java-tól.

Egyéb érdeklédősi köreim mentén haladva a [Python](https://www.python.org) lett a kiválasztott.

A nyelve nehézsége, a rendelkezésre álló eszközök száma egy dolog, ha nincs épkézláb fejlesztői környezet, akkor meg vagyunk lőve. Kicsit itt is nyitni akartam, ezért [PyDev](http://www.pydev.org) és a [PyCharm](https://www.jetbrains.com/pycharm/) alapból kiestek a pixisből – bár utóbbi nagyon vonzó volt. Szerettem volna a ma oly trendi bővíthető fejlesztői környezetek felé nyitni, mint az [Atom](https://atom.io), a [Sublime Text](https://www.sublimetext.com), vagy épp a [Visual Studio Code](https://code.visualstudio.com).

Ez utóbbi mellett döntöttem, elsősorban külső körülmények miatt: céges környezetben is elérhető, jó TypeScript támogatást mondanak róla – ez még később akár hasznos is lehet.

Az már elsőre látszott, hogy itt nem kapok egy kész fejlesztői környezetet, nekem kell összevadásznom a szükséges elemeket. Ez jelentett egyrészt egy [Python plugin](http://donjayamanne.github.io/pythonVSCode/)-t a VS Code-ba, valamint pár parancssoros eszközt, amire a plugin épít.

Ilyen a [PyLint](https://www.pylint.org) is, ami egy kódelemző, programozói hibák után kutat.

Csakhogy a Python is egy olyan nyelv, hogy minden elérhető hozzá, csak éppen telepíteni kell. A PyLint telepítéséhez nem kell más csak a [pip](https://pip.pypa.io/en/stable/) csomagkezelő. Ez meg normál esetben a Python mellett található, kivéve a Mac OS X beépített Python verzióját.

Nincs probléma, telepítjük a pip csomagkezelőt együtt a Python aktuális változatával egy másik csomagkezelő, a [Homebrew](http://brew.sh) segítségével – ez a Mac OS X-re készített egyedi csomagkezelő.

    
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"


Ezzel tulajdonképpen készen is lennénk, ha nem lenne a Python olyan, hogy egyszerre két főverziót gondoz: 2.x és 3.x. Természetesen mindkettő telepíthető a Homebrew segítségével, csak sajnos ezek képesek és összeakadnak.

Erre viszont megoldás a [PyEnv](https://github.com/yyuu/pyenv), ami képes különböző verziókat elkülönítetten kezelni. Teszi mindezt úgy, hogy lehet egy verziót definiálni globálisan, egyet lokális az adott könyvtárra és akár még egyet az adott shell session-re.

    
    brew install pyenv
    
    pyenv install 2.7.12
    
    pyenv install 3.5.2


Ezek után már csak a megfelelő környezetet kiválasztva a pip segítségével telepíteni kellett a PyLint-et.

    
    pyenv shell 2.7.12
    
    pip install pylint


A csodás az egészben pedig az, hogy mindez tökéletesen működik együtt, azaz a VS Code szépen használja azt a Python verziót, amit a PyEnv-vel beállítottam az adott projekt könyvtárára.

    
    pyenv local 2.7.12

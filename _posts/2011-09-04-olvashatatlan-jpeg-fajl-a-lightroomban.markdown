---
author: csiknor
comments: true
date: 2011-09-04 10:41:44+00:00
excerpt: Történt, hogy a fényképezőről kártyaolvasó segíségével beolvastam JPEG fájlokat
  az Adobe Lightroom-mal. Látszólag semmi probléma nem volt, a kép bekerült a megfelelő
  könyvtárba, az előképe szépen látszott is. Viszont, amikor szerkeszteni szerettem...
layout: post
link: http://blog.csik.net/2011/09/04/olvashatatlan-jpeg-fajl-a-lightroomban/
slug: olvashatatlan-jpeg-fajl-a-lightroomban
title: Olvashatatlan JPEG fájl a Lightroomban
wordpress_id: 68326921
categories:
- Kategória nélkül
tags:
- adobe
- exif
- fényképezés
- hiba
---

Tortent, hogy a fenykepezőről kartyaolvaso segisegevel beolvastam JPEG fajlokat az Adobe Lightroom-mal. Latszolag semmi problema nem volt, a kep bekerult a megfelelő konyvtarba, az előkepe szepen latszott is.

[![Lightroom_-_the_file_appears_to_be_unsupported_or_damaged](http://csiknet.files.wordpress.com/2011/09/lightroom_-_the_file_appears_to_be_unsupported_or_damaged-scaled1000.png?w=300)](http://csiknet.files.wordpress.com/2011/09/lightroom_-_the_file_appears_to_be_unsupported_or_damaged-scaled1000.png)

Viszont, amikor szerkeszteni szerettem volna, az Adobe Lightroom felhivta a figyelmem arra, hogy _"the file appears to be unsupported or damaged"_. Mivel egyszerű JPEG fajlrol volt szo, inkabb az utobbira gyanakodtam, igy megneztem a fajlt mas eszkozzel is: Xee es Adobe Photoshop.

Mindkettő tokeletesen kezelte.

A serules kizarva, igy jott a szokasos Google kereses. Tobb forumbejegyzes alapjan kezdtem gyanakodni arra, hogy az EXIF adatokkal (vagy esetleg mas metaadatokkal) lehet a baj. A forumokban altalaban a Picasa-t jeloltek meg, mint a hibat okozo programot. Viszont azt en nem hasznalom, igy csak probakepp probaltam ki, amit [The Random Moose](http://www.flickr.com/photos/randommoose/) [ajanlott](http://www.flickr.com/groups/adobe_lightroom/discuss/72157626346473344/72157626224642563/) a Flickr-en: manipulaljam a metaadatokat az [ExifTool](http://www.sno.phy.queensu.ca/~phil/exiftool/)-lal.

A dokumentacio olvasgatasa soran ugy veltem, hogy a leghelyesebb lesz az, ha minden adatot torlok, majd a biztonsagos EXIF adatokat visszamasolom a fajlba:

exiftool -all= -tagsfromfile @ -exif:all -unsafe P5052594.JPG

Szerencsere bejott, a szamomra lenyeges EXIF adatok megtartasa mellett, a JPEG fajl kepi reszenek adatvesztese nelkul sikerult olyan fajlt produkalnom, amit kepes kezelni a Lightroom.

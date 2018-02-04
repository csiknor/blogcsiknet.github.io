---
author: csiknor
comments: true
date: 2011-04-28 20:10:36+00:00
excerpt: Mostanában egyre gyakrabban érzem azt, hogy egy-egy számomra korábban érdekes
  újság, blog elkezdett olyan cikkeket közreadni, ami engem a legkevésbé sem érdekel.
  Erre megoldásként nagyon jól működött eleinte az, hogy a Google Reader-ben készítette...
layout: post
link: http://blog.csik.net/2011/04/28/rss-csatornak-adatok-szurese-formazasa-yahoo/
slug: rss-csatornak-adatok-szurese-formazasa-yahoo
title: 'RSS csatornák, adatok szűrése, formázása: Yahoo! Pipes'
wordpress_id: 51145196
categories:
- Kategória nélkül
tags:
- google reader
- rss
- yahoo pipes
---

Mostanában egyre gyakrabban érzem azt, hogy egy-egy számomra korábban érdekes újság, blog elkezdett olyan cikkeket közreadni, ami engem a legkevésbé sem érdekel. Erre megoldásként nagyon jól működött eleinte az, hogy a Google Reader-ben készítettem egy "kötelező" címkét, és alá pakoltam azokat az RSS csatornákat, amik számomra általában érdekes tartalmakat hoznak és használtama  Google Reader mágikus rendezési algoritmusát, ami - elvileg - érdekesség alapján előreteszi a fontosabb cikkeket.  


Most viszont eljutottam oda, hogy amit a Google Reader (vagyis amit az olvasók egy része) érdekesnek tart és elolvas, az engem nemhogy hidegen hagy, de kifejezetten felbőszít. Ilyen például a remek comment:com blog ValóVilág-os cikkei.

Szerencsére a mai világban mindenre van megoldás, így gyorsan kerestem is egy olyan eszközt, ahol ezeket az RSS csatornákat szűrni lehet. Így lyukadtam ki a Yahoo! Pipes alkalmazásnál, ami egy egész bonyolult eszköz, inkább programozási, mintsem általános felhasználásra való eszköz. Szerencsére ezzel a problémával én játszi könnyedséggel megbirkózom.

Hamar el is készítettem pár általam rendszeresen olvasott RSS csatorna szűrt változatát:

  * a [comment:com](http://pipes.yahoo.com/pipes/pipe.info?_id=a6839a0bbfd5e2879885de5e19dcb4c1) ValóVilág nélkül
  * a [Plastik](http://pipes.yahoo.com/pipes/pipe.info?_id=efe8f86c267670b9be188782fa36b074) iPhone, iPad és MineCraft nélkül, de belevéve @angelday Flickr képeit
  * az [FN technológia és tudomány rovatának](http://pipes.yahoo.com/pipes/pipe.info?_id=83be93ead04434ec967430cd2b536dae) egyesítése duplikációk és reklám nélkül

Ahogy egyre jobban ismerkedtem a Yahoo! Pipes tudásával rájöttem, hogy másra is lehet ezt használni. Fogtam a Portfolio.hu napi OTP részvényárait tartalmazó CSV formátumú adatszolgáltatását és készítettem belőle egy [szűrt RSS](http://pipes.yahoo.com/pipes/pipe.info?_id=522c4dfa76be18479087ad971721d8e9) csatornát: csak azokat a napokat tartalmazza az elmúlt két hónapból, ahol kimagasló forgalom, vagy kimagasló mozgás volt. Ezzel egy olyan ritkán tőzsdéző ember, mint én, napi olvasnivalójában csempésztem be a száraz tőzsdei mozgásokat.

Aztán képes XML és JSON adatokat is kezelni, így sok webes oldal API-ját tudja befogadni: Facebook, Twitter, stb. Készítettem is [egy olyat, ahol a ManU FB oldalát](http://pipes.yahoo.com/pipes/pipe.info?_id=9394fa7e682de6ea5b9e3de66260b3d0) kapom meg RSS-ben.

Nagyon hasznos eszköz tud lenni a Yahoo! Pipes, egyetlen hibája, ami nekem inkább előny, hogy elég mély szakmai ismeretek kellenek hozzá, így nagyon kérdéses, hogy egyáltalán meddig lesz még elérhető ez a szolgáltatás. Főleg mostanában, hogy a Yahoo! sorra zárja be a számára nem kifizetődő szolgáltatásokat.

Ez már most is meglátszik sajnos rajta, egyre több sebből vérzik maga a felület is, meg az egyes elemek is. Pl.: néha a debug mód hibával tér vissza, de ha mentés után lefuttatom, minden gond nélkül szalad. Bizonyos esetekben a JSON -> RSS átalakítás nem tökéletes, egy-egy speciális karakter konvertálásánál hibát vét. Ezek apró, de olyan problémák, amik megakadályozzák a rendeltetésszerű használatot. Remélhetőleg idővel megjavul a dolog.

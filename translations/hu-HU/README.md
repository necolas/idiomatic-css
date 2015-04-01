# A következetes és formakövető CSS alapjai

Ez a dokumentum egy praktikus CSS formázási szabályzatot vázol fel.
Erősen javasoljuk már meglévő irányelvek, bevett, gyakori szokások használatát.
Ha valaki saját formaszabályzatot készít, ezeket érdemes szükség szerint átdolgozni.

Ez a leírás folyamatosan változik, bővül, így szívesen várjuk
bárki közreműködését, ötleteit, kiegészítéseit. Tegyél hozzá bátran te is!


## Tárgymutató

1. [Általános alapelvek](#general-principles)
2. [Térköz](#whitespace)
3. [Megjegyzések](#comments)
4. [Formázás](#format)
5. [Gyakorlati példa](#example)

[Köszönet](#acknowledgements)

[Licenc](#license)


<a name="general-principles"></a>
## 1. Általános alapelvek

> „Ha jó csapatjátékos akarsz lenni egy sikeres projekten belül, rá kell jönnöd
> arra, hogy Rossz ötlet™ magad számára írni a kódot. Ha emberek ezrei használják
> amit írsz, kiváltképp törekedj az érthetőségre, és ne a megszokásaidat
> tartsd szem előtt, meg azt, hogy milyen jól tudsz lavírozni
> a specifikáción belül.” - Idan Gazit

* Ne akard idő előtt optimalizálni a kódot; legyen átlátható és világos.
* Egy kódbázison belül minden úgy nézzen ki, mintha egy ember írta volna,
  még akkor is, ha máskülönben rengetegen dolgoztak rajta.
* Mindenki tartsa be a közösen megbeszélt, előre lefektetett formázást.
* Ha valamit nem tudod hogyan formázz, mindenképp már meglévő mintákhoz fordulj.

<a name="whitespace"></a>
## 2. Térköz

Kizárólag egy formázás legyen egy projekten belül. Használj térközöket, és
használd ezeket következetesen, hogy átláthatóbb legyen a a munkád.

* Beljebbezésnél (indent) _soha_ ne használj vegyesen szóközt és tabulátort.
* Mi a szóközt javasoljuk, de rendes tabulátorokat is használhatsz.
  A lényeg, hogy tartsd magad ahhoz, amelyiket választottad.
* Ha szóközöket használsz, döntsd el, hogy hány szóköz lesz egy beljebbezés.
  (Ajánlott: 4 szóköz)

Tipp: állítsd be a szövegszerkesztőt, hogy mutassa a rejtett karaktereket,
illetve, hogy automatikusan törölje a sor végi szóközöket.

Tipp: használj egy [EditorConfig](http://editorconfig.org/) fájlt
(vagy ennek egy másik megfelelőjét), hogy egységben tartsd a térközöket
az egész projekten belül.


<a name="comments"></a>
## 3. Megjegyzések

A jól kommentált kód rendkívül fontos. Vedd a fáradtságot, hogy leírást adj a
kódrészekről, azok működéséről, korlátjairól és felépítéséről. Ne hagyd,
hogy a csoporton belül másoknak találgatni kelljen, hogy egy adott kódrészlet
pontosan mit és hogyan csinál.

A projekten belül a megjegyzések formázása legyen egyszerű és következetes.

* A megjegyzéseket külön sorba, a hozzájuk tartozó kód fölé írd.
* A sorhosszúságot szabd meg ésszerűen, pl., 80 karakter.
* A megjegyzésekkel tagold a kódot különálló bekezdésekre.
* A megjegyzéseket mondatokban írd, és egységesen beljebbezd.

Tipp: állítsd be a szövegszerkesztőt, hogy érzékelje a megjegyzések formázását
és automatikusan odaugorjon ezekhez, illetve váltani tudjon közöttük.

Példa:

```css
/* ==========================================================================
   Bekezdés
   ========================================================================== */

/* Albekezdés
   ========================================================================== */

/**
 * Rövid leírás Doxygen féle kommentformázással
 *
 * Ennek a hosszabb leírásnak az első mondata itt kezdődik, folytatódik
 * egy darabig, amíg végül be nem fejeződik ennek a sornak a végén.
 *
 * Egy ilyen formázás ideális részletesebb magyarázatokhoz és
 * dokumentációkhoz. Tartalmazhat HTML példakódot, URL-eket, vagy bármilyen
 * szükséges, hasznos információt.
 *
 * @tag Ez egy 'tag', ami a 'tag' elnevezést kapta
 *
 * TODO: Ez egy todo megjegyzés, amiben feladatok leírásai vannak, amit később
 *   el kell végezni. 80 karakter után sortörés jön. Az utána lévő
 *   sorok 2 szóközzel beljebb kezdődnek.
 */

/* Sima, alap megjegyzés */
```


<a name="format"></a>
## 4. Formázás

A választott formázás legyen: könnyen átlátható; egyszerűen lehessen
megjegyzéseket írni hozzá; minimalizálja a hibák lehetőségét;
végül pedig érthető, átlátható git diff-eket és blame-eket ad ki.

* Több egymás utáni kiválasztónál (selector) mindegyiket külön sorba írd.
* Hagyj egy szóközt a nyitó kapcsos zárójel előtt.
* Minden egyes tulajdonságot (declaration) külön sorba írj.
* Minden tulajdonságot egy szinttel beljebb kezdj.
* A tulajdonság utáni kettőspont mögött hagyj egy szóközt.
* Használj kisbetűket és rövidített hexadecimális értékeket, pl., `#aaa`.
* Használj egységesen sima vagy dupla idézőjelet.
  A dupla idézőjelet javasoljuk, pl., `content: ""`.
* Kiválasztóknál rakd idézőjelbe az attribútumok értékeit,
  pl., `input[type="checkbox"]`.
* _Ahol lehetséges_, a nulla értékek után ne tedd ki a mértékegységet,
  pl., `margin: 0`.
* Minden vessző után tegyél szóközt.
* Ne hagyd le a pontosvesszőt az utolsó tulajdonságnál.
* A tulajdonságokat lezáró kapcsos zárójel a kiválasztóval függőlegesen
  essen egybe.
* Minden nagyobb rész után hagyj ki egy sort.

```css
.kivalaszto-1,
.kivalaszto-2,
.kivalaszto-3[type="text"] {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    font-family: helvetica, arial, sans-serif;
    color: #333;
    background: #fff;
    background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.kivalaszto-a,
.kivalaszto-b {
    padding: 10px;
}
```

#### Tulajdonságok sorrendje

Ha a tulajdonságokat következetesen akarod sorba rakni, ezt egy
egyszerű elgondolás alapján tedd.

Kisebb csapatoknál, cégeknél könnyebb lehet az összefüggő tulajdonságokat
(pl. pozicionálás és dobozmodell) egymás mellé tenni.

```css
.kivalaszto {
    /* Pozicionálás */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Megjelenítés és dobozmodell */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Egyéb */
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

Nagyobb csapatoknál, cégeknél az ábécé sorrend lehet a célrvezetőbb, mivel
ebben az esetben egyetlen egy logika érvényesül.

#### Kivételek és apróbb szabályszegések

Abban az esetben, ha egymás után több kiválasztó csak egy tulajdonsággal
rendelkezik, ezeket lehet egymás alá írni. Ebben az esetben rakj egy szóközt
a nyitó kapcsos zárójel után, és a záró kapcsos zárójel elé.

```css
.kivalaszto-1 { width: 10%; }
.kivalaszto-2 { width: 20%; }
.kivalaszto-3 { width: 30%; }
```

A hosszabb, vesszővel elválasztott tulajdonságok értékeit – színátmenetek,
árnyékok – rendezhetjük több sorba, hogy átláthatóbbak
legyenek és hasznosabb diff-eket kapjunk. Többféle formázás
is használható; itt egy lehetséges példa.

```css
.kivalaszto {
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
}
```

### Előfeldolgozók: további formázási szempontok

A különböző CSS előfeldolgozók más funkciókkal, működéssel és szintaxissal
rendelkeznek. A formázás kialakításánál ezeket vegyük figyelembe.
A következő irányelvek a Sass nyelvre vonatkoznak.

* Korlátozd az egymásba ágyazást 1 szintre. Gondolj újra mindent, ami 2
  szintél mélyebbre van ágyazva. Ezzel megelőzöd a túlspecifikált
  kiválasztókat.
* Kerüld a nagyszámú egymásba ágyazást. Válaszd szét őket, amikor már
  kezdenek átláthatatlanná válni. Javasolt elkerülni midnent, ami
  20 sornál hosszabb.
* Mindig az `@extend` hivatkozások szerepeljenek először.
* Ahol lehetséges, csoportosítsd az `@include` hivatkozásokat a
  tulajdonságblokk elején, közvetlen az `@extend` hivatkozások után.
* Érdemes ellátni a saját függvényeidet `x-` vagy valami egyéb jelzéssel.
  Így sosem fogod összekeverni a saját függvényeidet a CSS beépített
  függvényeivel, és ezek nem fognak ütközni más könyvtárak függvényeivel sem.

```scss
.kivalaszto-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // egyéb tulajdonságok
}
```


<a name="example"></a>
## 5. Gyakorlati példa

Végül itt egy példa a felsorolt javaslatokra.

```css
/* ==========================================================================
   Rácshálózat (Grid layout)
   ========================================================================== */

/**
 * Oszlopos elrendezés vízszintes csúszkával.
 *
 * Ez egy sor teljes magasságú oszlopot generál, amiken belül a sorok nem
 * törhetnek meg, és vízszintesen lehet őket böngészni a szülő elemükön belül.
 *
 * Példa HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 * </div>
 */

/**
 * Oszlopok tartóeleme
 *
 * Csak `.cell` osztályú gyerekeket tartalmazhat.
 *
 * 1. Törli az oszlopok közötti térközt
 * 2. Megakadályozza az inline-block oszlopok sortörését
 */

.grid {
    height: 100%;
    font-size: 0; /* 1 */
    white-space: nowrap; /* 2 */
}

/**
 * Oszlopok
 *
 * Nincs meghatározott alap szélesség. Ezt a `.cell-n` osztályokkal módosítsd.
 *
 * 1. Beállítja az oszlopok közti térközt
 * 2. Visszaállítja a `.grid` után örökölt white-space értékét
 * 3. Visszaállítja a `.grid` után örökölt font-size értékét
 */

.cell {
    position: relative;
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    height: 100%;
    padding: 0 10px; /* 1 */
    border: 2px solid #333;
    vertical-align: top;
    white-space: normal; /* 2 */
    font-size: 16px; /* 3 */
}

/* Oszlop állapotok */

.cell.is-animating {
    background-color: #fffdec;
}

/* Oszlopok méretezése
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Oszlopok módosítása
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="acknowledgements"></a>
## Köszönet

Köszönet minden fordítónak, és mindazoknak, akik hozzájárultak az
[idiomatic.js](https://github.com/rwldrn/idiomatic.js) dokumentumhoz.
Rengeteg inspirációnak, hivatkozásnak és irányelvnek lett ez a forrása.


<a name="license"></a>
## Licenc

Nicolas Gallagher: _A következetes és formakövető CSS alapjai_ a következő
licenc alatt áll: [Creative Commons Attribution 3.0 Unported License]
(http://creativecommons.org/licenses/by/3.0/). Ez érvényes a repóban
lévő összes dokumentumra és fordításra.

Ez a fordítás a következő munkán alapszik:
[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).

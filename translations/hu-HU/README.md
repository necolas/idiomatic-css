# A következetes és formakövető CSS alapjai

A következő dokumentum egy célszerű formaszabályzatot vázol fel CSS
fejlesztéshez. Ezek az irányelvek erősen javasolják már meglévő, gyakori
és ésszerű minták használatát. Ezeket javasolt szükség szerint átdolgozni,
ha saját formaszabályzatot írsz.

Ez egy élő dokumentum, mindig szívesen fogadunk új ötleteket. Működj
közre te is.


## Tárgymutató

1. [Általános alapelvek](#general-principles)
2. [Térköz](#whitespace)
3. [Kommentálás](#comments)
4. [Formázás](#format)
5. [Gyakorlati példa](#example)

[Köszönetnyilvánítás](#acknowledgements)

[Licenc](#license)


<a name="general-principles"></a>
## 1. Általános alapelvek

> „Ha jó csapatjátékos akarsz lenni egy sikeres projekten belül, fel kell
> ismerned azt, hogy Rossz ötlet™, ha magad számára írod a kódot. Ha emberek
> ezrei használják azt, amit írsz, törekedj a maximális érthetőségre, ne pedig
> a személyes preferenciádat tarts szem előtt, hogy mennyire vagy
> jártas a specifikáción belül.” - Idan Gazit

* Ne próbáld idő előtt optimalizálni a kódot; legyen átlátható és érthető.
* Egy kódbázison belül minden kód úgy nézzen ki, mintha egy ember munkája
  lenne, még akkor is, ha rengeteg ember dolgozik rajta.
* Szigorúan tartasd be a közösen megegyezett formát.
* Ha a formát illetően kétségeid akadnak, használj már meglévő, gyakori
  mintákat.

<a name="whitespace"></a>
## 2. Térköz

Kizárólag egy fajta formázás éljen a kódbázison belül. A térközökkel tedd
átláthatóbbá a kódot és használd őket következetesen.

* Indentálásnál _soha_ ne használj együtt szóközt és tabulátort.
* Válaszd a puha indentálást (szóközök), vagy a rendes tabulátorokat.
  Hűen tartsd magad a választásodhoz. (Ajánlott: szóközök)
* Ha szóközöket használsz, válaszd meg az indentálási szint karakterszámát.
  (Ajánlott: 4 szóköz)

Tipp: állítsd be a szerkesztőt, hogy mutassa a rejtett karaktereket,
vagy, hogy automatikusan törölje a sor végi szóközöket.

Tipp: használj egy [EditorConfig](http://editorconfig.org/) fájlt
(vagy egy ennek megfelelőt), hogy segítsen egységben tartani a térközöket
az egész kódbázison belül.


<a name="comments"></a>
## 3. Kommentálás

A jól kommentált kód rendkívül fontos. Vedd a fáradtságot, hogy leírást adj a
kódrészekről, azok működéséről, korlátjairól és felépítéséről. Ne hagyd,
hogy a csoporton belül mások találgatásra szoruljanak a szabályostól
eltérő, vagy nem világos kód célját illetően.

A kódbázison belül a megjegyzések formázása legyen egyszerű és következetes.

* A megjegyzéseket külön sorba írd, a hozzájuk tartozó kód fölé.
* A sorhosszúságnak szabj meg egy ésszerű felső határt, pl., 80 karakter.
* Fordítsd hasznodra a megjegyzéseket, és tagold a kódot külön bekezdésekre.
* A megjegyzéseket mondatok formájában írd, és egységesen indentáld.

Tipp: állítsd be a szerkesztődet, hogy gyors elérést nyújtson a megegyezett
kommentálási mintákhoz.

Példa:

```css
/* ==========================================================================
   Bekezdés komment blokk
   ========================================================================== */

/* Albekezdés komment blokk
   ========================================================================== */

/**
 * Rövid leírás, ami a Doxygen féle kommentformázást veszi alapul
 *
 * A hosszú leírás első mondata itt kezdődik, folytatódik ezen a soron
 * egy darabig, amíg végül be nem fejeződik ennek a bekezdésnek a végén.
 *
 * A hosszú leírás ideális részletesebb magyarázatokhoz és
 * dokumentációkhoz. Tartalmazhat HTML példakódot, URL-eket, vagy bármilyen
 * szükséges, vagy hasznos információt.
 *
 * @tag Ez egy 'tag', ami a 'tag' elnevezést kapta
 *
 * TODO: Ez egy todo megjegyzés, ami leír egy részfeladatot, amit majd később
 *   kell megcsinálni. 80 karakter után sortörés következik, és az utána lévő
 *   sorok 2 szóközzel beljebb kezdődnek.
 */

/* Alap komment */
```


<a name="format"></a>
## 4. Formázás

A választott kódformázásnak biztosítania kell, hogy a kód: könnyen átlátható;
egyszerűen lehet érthetően kommentálni; minimalizálja a hibalehetőségeket;
és hasznos diff-eket és blame-eket eredményez.

* Több egymást követő kiválasztó esetén minden kiválasztót külön sorba írj.
* Hagyj egy szóközt a nyitó kapcsos zárójel előtt.
* Minden egyes tulajdonságot külön sorba írj.
* Minden tulajdonságot egy indentálási szinttel beljebb kezdj.
* A tulajdonságot követő kettőspont után hagyj egy szóközt.
* Használj kisbetűs és rövidített hexadecimális értékeket, pl., `#aaa`.
* Használj egységesen szimpla, vagy dupla idézőjeleket.
  Ajánlott a dupla idézőjel, pl., `content: ""`.
* Kiválasztóknál rakd idézőjelbe az attribútumok értékeit,
  pl., `input[type="checkbox"]`.
* _Ahol szabad_, a nulla értékek után hagyd el a mértékegységet,
  pl., `margin: 0`.
* Minden vessző után rakj szóközt a vesszővel elválasztott tulajdonságok és
  függvények értékeinél.
* Egymás után több tulajdonság megadásánál rakj pontosvesszőt az utolsó
  tulajdonság után.
* A tulajdonságokat lezáró kapcsos zárójel a kiválasztók elejével essen egybe.
* Minden CSS meghatározás blokk után hagyj ki egy sort.

```css
.kiválasztó-1,
.kiválasztó-2,
.kiválasztó-3[type="text"] {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    font-family: helvetica, arial, sans-serif;
    color: #333;
    background: #fff;
    background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.kiválasztó-a,
.kiválasztó-b {
    padding: 10px;
}
```

#### Tulajdonságok sorrendje

Ha a tulajdonságokat következetesen akarjuk sorba rendezni, ezt egyetlen egy,
egyszerű szisztéma alapján tegyük.

Kisebb csapatoknál előnyösebb lehet az összefüggő tulajdonságokat
(pl. pozicionálás és dobozmodell) egybevenni.

```css
.kiválasztó {
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

Nagyobb csapatok lehet ábécé sorrend mellett döntenek annak egyszerűsége
és könnyű karbantarthatósága miatt.

#### Kivételek és apróbb szabályszegések

Abban az esetben, ha egymás után sok kiválasztónak csak egy tulajdonsága van,
ezeket lehet közvetlen egymás alá írni. Ebben az esetben hagyj egy szóközt
a nyitó kapcsos zárójel után, és a záró kapcsos zárójel előtt.

```css
.kiválasztó-1 { width: 10%; }
.kiválasztó-2 { width: 20%; }
.kiválasztó-3 { width: 30%; }
```

Hosszú, vesszővel elválasztott tulajdonságértékeknél – mint több színátmenet
vagy árnyék esetében – ezeket rendezhetjük több sorba, hogy átláthatóbbak
legyenek és hasznosabb diff-eket kapjunk. Többféle formázás
is használható; itt egy lehetséges megoldás.

```css
.kiválasztó {
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
rendelkeznek. A formázás kialakításánál mindenképpen vegyük figyelembe ezek
sajátosságait. A következő irányelvek a Sass nyelvre vonatkoznak.

* Korlátozd az egymásba ágyazást 1 szintre. Gondolj újra mindent, ami 2
  szintél mélyebbre van ágyazva. Ezzel elejét veszed a túlspecifikált
  kiválasztóknak.
* Kerüld a nagyszámú egymásba ágyazást. Válaszd szét őket, amikor már
  kezdenek átláthatatlanná válni. Ajánlatos elkerülni a 20 sornál hosszabb
  egymásba ágyazást.
* Mindig az `@extend` hivatkozások szerepeljenek legelöl.
* Ahol lehetséges, csoportosítsd az `@include` hivatkozásokat a
  tulajdonságblokk elején, közvetlen az `@extend` hivatkozások után.
* Érdemes ellátni a saját függvényeidet `x-` vagy valami egyéb előjellel.
  Így sosem fogod összekeverni a saját függvényeidet a natív CSS
  függvényekkel, és nem fognak ütközni más könyvtárak függvényeivel sem.

```scss
.kiválasztó-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // egyéb tulajdonságok
}
```


<a name="example"></a>
## 5. Gyakorlati példa

Egy példa a különböző konvenciókra.

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
## Köszönetnyilvánítás

Köszönet minden fordítónak, és mindazoknak, akik hozzájárultak az
[idiomatic.js](https://github.com/rwldrn/idiomatic.js) dokumentumhoz.
Rengeteg inspirációnak, hivatkozásnak és irányelvnek lett ez a szülőhelye.


<a name="license"></a>
## Licenc

Nicolas Gallagher: _A következetes és formakövető CSS alapjai_ a következő
licenc alatt áll: [Creative Commons Attribution 3.0 Unported License]
(http://creativecommons.org/licenses/by/3.0/). Ez érvényes a repóban
lévő összes dokumentumra és fordításra.

Jelen írás a következő munkán alapszik:
[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).

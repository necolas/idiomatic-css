# Principper for at skrive konsistent, idiomatisk CSS

Dette dokument skitserer en række fornuftige og logiske retningslinjer til CSS udvikling.
Det er ikke ment som et asolut regelsæt og jeg ønsker ikke at presse min måde at
skrive CSS på ned over andres kode. Ikke desto mindre så indbyder disse principper
til at benytte allerede eksisterende og logiske kodemønstre.

Dette dokument er levende og nye tilføjelser og idéer er altid velkomne.

## Oversættelser

* [Dansk](https://github.com/necolas/idiomatic-css/tree/master/translations/da-DK)
* [Italiano](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [日本語](https://github.com/necolas/idiomatic-css/tree/master/translations/ja-JP)
* [Nederlands](https://github.com/necolas/idiomatic-css/tree/master/translations/nl-NL)
* [Português (Brasil)](https://github.com/necolas/idiomatic-css/tree/master/translations/pt-BR)
* [Srpski](https://github.com/necolas/idiomatic-css/tree/master/translations/sr)
* [Türkçe](https://github.com/necolas/idiomatic-css/tree/master/translations/tr-TR)
* [简体中文](https://github.com/necolas/idiomatic-css/tree/master/translations/zh-CN)


## Indholdsfortegnelse

1. [Generelle principper](#general-principles)
2. [Mellemrum](#whitespace)
3. [Kommentarer](#comments)
4. [Formatering](#format)
5. [Navngivning](#naming)
6. [Praktisk eksempel](#example)
7. [Organisering](#organization)
8. [Build og udrulning](#build-and-deployment)

[Anerkendelser](#acknowledgements)


<a name="general-principles"></a>
## 1. Generelle principper

> "En del af det at være en god forvalter af et succésfuldt projekt er at indse,
> at det at skrive kode til én selv er En Dårlig Idé™. Hvis tusindvis af mennesker
> bruger din kode, bør du optimere din kode til maksimal læsevenlighed, ikke til
> dine personlige preferencer og sjove eller underlige forkortelser." - Idan Gazit

* Al kode i kode-basen bør se ud som om, kun én person har skrevet det hele, uanset hvor
  mange der rent faktisk har leveret indhold.
* Håndhæv den aftalte stil strengt.
* Hvis der er tvivl bør eksisterende, bredt accepterede kodemønstre benyttes.

<a name="whitespace"></a>
## 2. Mellemrum

Kun én stil bør eksistere på tværs af hele dit projekts kilde. Vær altid konsistent i
din brug af mellemrum. Brug mellemrum og ekstra linjeskift til at forbedre læsbarheden.

* Du må _aldrig_ blande mellemrum og tablatorer ved indrykning.
* Vælg mellem bløde indrykninger (mellemrum) eller tabulatorer. Stå ved dit valg uden
  forbehold. (Anbefales: mellemrum)
* Hvis du bruger mellemrum, vælges et antal der bruges pr. indrykningsniveau.
  (Anbefales: 4 mellemrum)

Tip: Indstil din CSS-editor til at vise skjulte tegn. Dette giver dig mulighed for, at
slette mellemrum i slutningen af kodelinjer, slette uønskede dobbelt-mellemrum og dermed
undgå at "forurene" kode-commits.

<a name="comments"></a>
## 3. Kommentarer

Velkommenteret (og dermed veldokumenteret) kode er virkelig vigtigt. Brug tid på at
beskrive komponenter, hvordan de virker, deres begrænsninger og måden hvorpå de er
konstrueret. Overlad det ikke til andre i teamet at gætte sig frem til, hvad usædvanlig
eller ikke-indlysende kode skal bruges til.

Kommentar-stilen bør være simpel og konsistent på tværs er hele kode-basen.

* Placér kommentarer på en ny linje over den kode, de beskriver.
* Undgå kommentarer for enden af kodelinjer.
* Hold kommentarlinjer fornuftigt korte, fx 80 karakterer.
* Vær gavmild med kommentarer til at bryde CSS'en op i mindre sektioner.
* Brug korrekt grammetik i kommentarer og vær konsistent med tekst-indrykning.

Tip: Indstil din CSS-editor til at give dig genveje til at indsætte tekststumper med
de aftalte kommentar-mønstre.

#### CSS-eksempel:

```css
/* ==========================================================================
   Afsnit kommentar-blok
   ========================================================================== */

/* Underafsnit kommentar-blok
   ========================================================================== */

/*
 * Gruppe kommentar-blok.
 * Idéel til fler-linjede forklaringer og dokumentation.
 */

/* Simpel kommentar */
```

#### SCSS-eksempel:

```scss
// ==========================================================================
// Afsnit kommentar-blok
// ==========================================================================

// Underafsnit kommentar-blok
// ==========================================================================

//
// Gruppe kommentar-blok.
// Idéel til fler-linjede forklaringer og dokumentation.
//

// Simpel kommentar
```


<a name="format"></a>
## 4. Formatering

Det valgte kodeformat skal tilsikre at koden er: nem at læse; nem at kommentere klart;
minimere risikoen for at introducere fejl ved et tilfælde; og resulterer i brugbare diffs
og blames (https://git.wiki.kernel.org/index.php/Textconv#Blame_and_diff)

1. Én diskret selector pr. linje i multi-selector regelsæt.
2. Ét enkelt mellemrum før krøllet start-parentes i regelsæt.
3. Én erklæring pr. linje i regelsæt.
4. Ét indrykningsniveau på regelsæt.
5. Ét enkelt mellemrum efter kolon i hver erklæring.
6. Afslut _alle_ erklæringer med et semikolon - også den sidste.
7. Placér den krøllede slut-parentes på samme indrykningsniveau som det første tegn
   i regelsættet.
8. Opdel de enkelte regelsæt med en tom linje.

```css
.selector-1,
.selector-2,
.selector-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    color: #333;
    background: #fff;
}
```

#### Erklæringers rækkefølge

Erklæringer bør sorteres i overensstemmelse med et simpelt princip. Mit foretrukne
princip er at gruppere relaterede egenskaber sammen, og strukturmæssigt vigtigt
egenskaber (fx positionering og box-modellen) erklæring inden typografi, baggrund og
farveegenskaber.

```css
.selector {
    position: relative;
    display: block;
    width: 50%;
    height: 100px;
    padding: 10px;
    border: 0;
    margin: 10px;
    color: #fff
    background: #000;
}
```

Alfabetisk rækkefølge er også populær, men ulempen er, at denne sortering adskiller
relaterede egenskaber. For eksempel vil positioneringsegenskaber ikke længere være
samlet i en gruppe, og box-modellens egenskaber kan ende med at blive spredt ud over
hele regelsættet.

#### Undtagelser og små afvigelser

Store blokke af enkelt-linje erklæringer kan benytte et enkeltlinje-format. I dette
tilfælde bør der inkluderes et enkelt mellemrum før krøllet start-parentes og inden
krøllet slut-parentes.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Lange, kommaseparerede egenskaber - fx samlinger af farveforløb eller skygger - kan
arrangeres over flere linjer, i en betræbelse på, at forbedre læsbarheden og producere
mere brugbare diffs. Det er flere forskellige formater der kan benyttes; en måde at gøre
det på kan ses herunder.

```css
.selector {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```

#### Diverse

* Brug små bogstaver i hex værdier, fx `#aaa`.
* Brug enkelt- eller dobbelt-anførselstegn konsistent. Dobbelt-anførselstegn foretrækkes,
  fx `content: ""`.
* Brug altid anførselstegn i selctorers egenskaber, fx `input[type="checkout"]`.
* _Hvor det er muligt_ bør du undgå at specificere enheder for nul-værdier, fx
  `margin: 0`.

### Preprocessors: Ekstra overvejelser i forbindelse med formatering

Forskellige CSS preprocessors har forskellige egenskaber, funktionalitet og syntaks.
Dine konventioner bør udvides og tilpasses, således at de imødekommer de forhold, der er
i de proprocessors der benyttes af gruppen. De efterfølgende guidelines relaterer sig til
SASS.

* Begræns indlejring til 1 niveau. Genovervej alle indlejringer der er mere end 2
  niveauer dyb. Dette forhindrer alt for specifikke CSS selektorer.
* Undgå et højt antal indlejrede regler. Bryd dem op når læsbarheden begynder at blive
  påvirket. Det anbefales at undgå indlejringer der breder sig over mere end 20 linjer.
* Placér altid `@extend`-erklæringer på første linje i regelsæt.
* Hvis det er muligt, placeres `@include` i toppen af regelsættet, lige efter
  `@extend`-erklæringer.
* Overvej at starte brugerdeficerede funktioner med `x-` eller lignende. Dette hjælper
  med at undgå, at dine funktioner konflikter med (eller overskriver) standard
  CSS-funktioner fra biblioteker og frameworks.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // andre erklæringer
}
```


<a name="naming"></a>
## 5. Navngivning

Du er ikke en menneskelig compiler/compressor, så lad være med at prøve at være en sådan.

Brug klare og logiske navne til dine HTML-class'er. Vælg et forståelig og konstistent
navngivningsmønster der giver mening i både HTML- og CSS-filer.

```css
/* Eksempel på kode med dårlig navngivning */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Eksempel på kode med god navngivning */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="example"></a>
## 6. Praktisk eksempel

Et eksempel på en række forskellige konventioner.

```css
/* ==========================================================================
   Gitter layout
   ========================================================================== */

/*
 * HTML-eksempel:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Undgå at "inline-block"-celler ombrydes */
    white-space: nowrap;
    /* Fjerner mellemrum mellem celler */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Angiver mellemrum mellem celler */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Nulstil white-space */
    white-space: normal;
    /* Nulstil font-size */
    font-size: 16px;
}

/* Cellers tilstande */

.cell.is-animating {
    background-color: #fffdec;
}

/* Cellers dimensioner
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Celle-ændringer
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organization"></a>
## 7. Organisering

Organisering af kode er en vigtig del af enhver CSS kodebase, og livsnødvendig for
store kodebaser.

* Lav en logisk separering mellem særskilte stumper af kode.
* Brug separate filer (sammenkædes i et build) for at bryde koden op i særskilte
  komponenter.
* Hvis du bruger en preprocessor, opsættes fælles kode i variabler for farver, typografi
  osv.

<a name="build-and-deployment"></a>
## 8. Builds og udrulning

Forud for brug i live-miljøer, bør projekter altid forsøge at inkludere en generisk
metode til at linte, teste, komprimere og versionere koden. Til dette formål er
[grunt](https://github.com/cowboy/grunt) af Ben Alman et fremragende værktøj.


<a name="acknowledgements"></a>
## Anerkendelser

Tak til alle der har bidraget til 

Thanks to everyone who has contributed to
[idiomatic.js](https://github.com/rwldrn/idiomatic.js). I har været en fantastisk kilde
til inspiration, noteringer og retningslinjer.
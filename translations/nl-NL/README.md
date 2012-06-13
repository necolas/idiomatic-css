# Principes voor het schrijven van consistente, idiomatische CSS

Het volgende document schetst een logische stijlgids voor het schrijven van CSS. Het is niet normatief bedoeld en ik wens niet mijn stijlvoorkeuren op te dringen aan andermans code. Deze richtlijnen zijn echter een sterke aanmoediging voor het gebruik van bestaande, algemene, verstandige patronen.

Dit is een document in ontwikkeling en nieuwe ideeën zijn altijd welkom. Draag alstublieft bij!


## Vertalingen

* [Italian](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [Portuguese](https://github.com/necolas/idiomatic-css/tree/master/translations/pt-BR)
* [Serbian](https://github.com/necolas/idiomatic-css/tree/master/translations/sr)
* [Turkish](https://github.com/necolas/idiomatic-css/tree/master/translations/tr_TR)
* [Dutch](https://github.com/necolas/idiomatic-css/tree/master/translations/nl-NL)


## Inhoudsopgave

1. [Algemene principes](#general-principles)
2. [Witruimte](#whitespace)
3. [Commentaar](#comments)
4. [Opmaak](#format)
5. [Naamgeving](#naming)
6. [Praktisch voorbeeld](#example)
7. [Ordening](#organization)
8. [Build en deployment](#build-and-deployment)

[Dank](#acknowledgements)


<a name="general-principles"></a>
## 1. Algemene principes

> "Het zijn van een goed rentmeester van een succesvol project is deels het
> realiseren dat het schrijven van code voor jezelf een Slecht Idee™ is. Als 
> duizenden mensen je code gebruiken schrijf je code dan voor maximale 
> duidelijkheid, niet je persoonlijke voorkeur slim om te gaan binnen de 
> specificatie." - Idan Gazit


* Alle code in elke codebase zou getypt moeten lijken door een enkel persoon, ongeacht hoeveel personen een bijdrage leverden.
* Dwing de afgesproken stijl streng af.
* Gebruik bij twijfel bestaande, algemene patronen.


<a name="whitespace"></a>
## 2. Witruimte

In de hele broncode van uw project zou slechts één stijl moeten bestaan. Wees altijd consistent in het gebruik van witruimte. Gebruik witruimte om de leesbaarheid te bevorderen.

* Wissel _nooit_ het gebruik van tabs en spaties voor het inspringen van tekst af.
* Kies tussen zacht inspringen (spaties) of echte tabs. En blijf daarbij (voorkeur: spaties).
* Als u spaties gebruikt, kies het aantal karakters per niveau van inspringen (voorkeur: 4 spaties)

Tip: Stel uw tekstverwerker in om "onzichtbare tekens te tonen". Dit stelt u in staat witruimte aan regeleinden en onbedoelde witregels te verwijderen en voorkomt vervuilde commits.


<a name="comments"></a>
## 3. Commentaar

Goed becommentarieerde code is extreem belangrijk. Neem de tijd om componenten te beschrijven. Hoe deze werken, de beperkingen en de manier waarom deze zijn samengesteld. Laat anderen in het team niet raden naar het doel van ongewone of onduidelijke code.

De stijl van commentaar binnen broncode zou simpel en consistent moeten zijn.

* Plaats commentaar op een nieuwe regel boven het onderwerp.
* Vermijd commentaar aan het einde van een regel.
* Houdt regellengte tot een verstandig maximum: b.v. 80 kolommen.
* Maak ruim gebruik van commentaar om CSS-code op te breken in aparte secties.
* Gebruik "standaard kapitalen"-commentaar en het consistent inspringen van tekst.

Tip: Stel uw tekstverwerker in met toetscombinaties om de afgesproken algemene patronen te genereren.


#### CSS-voorbeeld:

```css
/* ==========================================================================
   Sectie commentaarblok
   ========================================================================== */

/* Subsectie commentaarblok
   ========================================================================== */

/*
 * Groep commentaarblok.
 * Ideaal voor uitleg over meerdere regels en documentatie.
 */

/* Standaard commentaar */
```

#### SCSS-voorbeeld:

```scss
// ==========================================================================
// Sectie commentaarblok
// ==========================================================================

// Subsectie commentaarblok
// ==========================================================================

//
// Groep commentaarblok
// Ideaal voor uitleg over meerdere regels en documentatie.
//

// Standaard commentaar
```


<a name="format"></a>
## 4. Opmaak

De gekozen code-opmaak moet verzekeren dat de code: makkelijk te lezen en te becommentariëren is. Dit vermindert de kans op de onbedoelde introductie van fouten en resulteert in bruikbare diffs en blames.

1. Eén aparte selector per regel en in multi-selector rulesets.
2. Eén afzonderlijke spatie voor de openings-accolade van een ruleset.
3. Eén declaratie per regel in een declaratieblok.
4. Eén inspringniveau voor elke declaratie.
5. Eén afzonderlijke spatie na de dubbele punt van een declaratie.
6. Voeg altijd een puntkomma aan het eind van de laatste declaratie in een declaratieblok.
7. Plaats de afsluitende accolade van een ruleset in dezelfde kolom als het eerste karakter van de ruleset.
8. Scheidt elke ruleset door een witregel.

```css
.selector-1,
.selector-2,
.selector-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: blok;
    color: #333;
    background: #fff;
}
```

#### Volgorde van declaraties

Declaraties dienen geordend te worden overeenkomstig een enkel principe. Mijn voorkeur is dat gerelateerde eigenschappen gegroepeerd worden en dat structureel belangrijke eigenschappen (b.v. positionering en box-model) voor typografische-, achtergronds- en kleureigenschappen gedeclareerd worden.

```css
.selector {
    position: relative;
    display: blok;
    width: 50%;
    height: 100px;
    padding: 10px;
    border: 0;
    margin: 10px;
    color: #fff
    background: #000;
}
```
Alfabetische volgorde is ook populair, maar het nadeel is dat dit gerelateerde eigenschappen afzondert. Bijvoorbeeld: positie-afstanden zijn niet langer gegroepeerd en box-modeleigenschappen kunnen door het hele declaratieblok verspreid worden. 

#### Uitzonderingen en kleine afwijkingen

Grote blokken alleenstaande declaraties kunnen een enigszins andere, enkele-regel-opmaak gebruiken. In dit geval zou een spatie toegevoegd kunnen worden na de openingsaccolade en voor de sluitende accolade.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Lange, kommagescheiden eigenschapwaarden - zoals sets aan verlopen of schaduwen - kunnen gerangschikt kunnen worden over meerdere regels om de leesbaarheid en beter bruikbare diffs te bevorderen. Er zijn verschillende opmaakstijlen die gebruikt zouden kunnen worden; een voorbeeld is hieronder getoond.

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

#### Diversen

* Gebruik onderkast hex waarden, b.v., `#aaa`.
* Gebruik consistent enkele of dubbele aanhalingstekens. Dubbele aanhalingstekens hebben de voorkeur, b.v. `content: ""`.
* Gebruik altijd aanhalingstekens bij attribuutwaarden in selectors, b.v. `input[type="checkout"]`.
* Vermijd, _indien toegestaan_, specifieke eenheden voor nulwaarden b.v. `margin: 0`.

### Preprocessors: extra opmaakoverwegingen

Verschillende CSS preprocessors hebben verschillende kenmerken, functionaliteit en syntaxis. Uw conventies zullen moeten worden afgestemd op de unieke kenmerken van de gebruikte preprocessors. De volgende richtlijnen hebben betrekking op Sass.

* Beperk geneste regels tot 1 niveau diep. Bekijk sets dieper dan 2 niveaus opnieuw. Dit voorkomt te specifieke CSS-selectors.
* Voorkom grote aantallen geneste regels. Splits ze wanneer de leesbaarheid verminderd. De voorkeur is om geneste regels van meer dan 20 regels te vermijden.
* Plaats `@extend`-statements altijd op de eerste regel van een declaratieblok.
* Groepeer `@include`-statements waar mogelijk bovenaan een declaratieblok, na mogelijke `@extend`-statements.
* Overweeg een voorvoegsel van `x-` of een andere namespace voor eigen functies. Dit voorkomt mogelijke verwarring van uw functies met een CSS-eigen functie of een conflict met functies van andere libraries.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // andere declaraties
}
```


<a name="naming"></a>
## 5. Naamgeving

U bent geen menselijke codecompiler/compressor; probeer dit dan ook niet te zijn.

Gebruik duidelijke en doordachte namen voor HTML classes. Kies een begrijpelijk en consistent patroon voor naamgeving dat zowel in de HTML- als CSS-bestanden voor zich spreekt.

```css
/* voorbeeld van code met slechte naamgeving */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Voorbeeld van code met betere naamgeving */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="example"></a>
## 6. Praktisch voorbeeld

Een voorbeeld van verschillende conventies.

```css
/* ==========================================================================
   Grid lay-out
   ========================================================================== */

/*
 * Voorbeeld HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Voorkom het omslaan van inline-block cellen */
    white-space: nowrap;
    /* Verwijder witruimte tussen cellen */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Bepaal de ruimte tussen cellen */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Herstel witruimte */
    white-space: normal;
    /* Herstel font-size */
    font-size: 16px;
}

/* Cel states */

.cell.is-animating {
    background-color: #fffdec;
}

/* Celafmetingen
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Celaanpassingen
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organization"></a>
## 7. Ordening

Code-organisatie is een belangrijk onderdeel van elke CSS codebase en cruciaal voor grotere codebases.

* Verdeel logisch afzonderlijke codeonderdelen.
* Gebruik afzonderlijke bestanden (samengevoegd door een buildproces) om code voor aparte componenten op te breken.
* Abstraheer algemene code in variabelen voor kleur, typografie enz. als gebruik gemaakt wordt van een preprocessor.


<a name="build-and-deployment"></a>
## 8. Build en deployment

Projecten dienen altijd een generieke manier te bevatten om broncode te linten, testen, comprimeren en van versienummer te voorzien in voorbereiding op gebruik in productie. [grunt](https://github.com/cowboy/grunt) door Ben Alman is hiervoor een uitstekende oplossing.


<a name="acknowledgements"></a>
## Dank

Dank voor iedereen die bijgedragen heeft aan  [idiomatic.js](https://github.com/rwldrn/idiomatic.js). Het was een bron van inspiratie, citaties en richtlijnen.

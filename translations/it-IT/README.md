# Princìpi per la scrittura di CSS consistente ed idiomatico

Il seguente documento espone una ragionevole guida di stile per lo sviluppo in CSS. Esso non è inteso per essere un rigido regolamento e non voglio imporre le mie preferenze di stile sul codice degli altri. A parte tutto, queste linee guida incoraggiano fortemente l'utilizzo di ragionevoli modelli comuni e già esistenti.

Questo è un documento in continua evoluzione e nuove idee sono le benvenute. Per favore contribuite.

## Tavola dei contenuti

1. [Princìpi generali](#1-general-principles)
2. [Spazio vuoto](#2-whitespace)
3. [Commenti](#3-comments)
4. [Formato](#4-format)
5. [Nomenclatura](#5-nomenclatura)
6. [Esempio pratico](#6-practical-example)
7. [Organizzazione](#7-organization)
8. [Generazione e distribuzione](#8-build-and-deployment)

[Ringraziamenti](#acknowledgments)

## 1. Princìpi generali

> "Parte dell'essere un buon amministratore per un progetto di successo è capire che la scrittura di codice per sé stessi è una Cattiva Idea™. Se migliaia di persone usano il tuo codice, allora scrivi il tuo codice in modo che abbia la massima chiarezza, e non seguendo i tuoi gusti personali su come renderlo chiaro all'interno delle specifiche" - Idan Gazit

* Tutto il codice, in qualsiasi linguaggio sia, dovrebbe sembrare come scritto da una sola persona, non importa quante persone abbiano contribuito.
* Rispettare al massimo lo stile concordato.
* Se nel dubbio, usare modelli comuni ed esistenti.


# 2. Spazio vuoto

Dovrebbe esistere solo uno stile in tutto il sorgente del vostro progetto. Siate sempre consistenti nell'uso dello spazio vuoto. Usate questo spazio per migliorare la leggibilità.

* _Mai_ mischiare spazi e tabulazioni per i rientri.
* Scegliete tra rientri soft (spazi) o tabulazioni reali. Mantenete quella scelta (preferenza: spazi).
* Se usate gli spazi, scegliete il numero di caratteri usati per il livello di rientro (preferenza: 4 spazi).

Suggerimento: configurate il vostro editor in modo da "visualizzare i caratteri invisibili". Questo vi permetterà di eliminare spazi vuoti di fine linea, eliminare linee vuote ed evitare commit pasticciati.


## 3. Commenti

Un codice ben commentato è estremamente importante. Prendete tempo per descrivere i componenti, come funzionano, i loro limiti, ed il modo in cui sono costruiti. Non mettete altri nel team nella situazione di dover cercare di immaginare lo scopo di codice non comune o poco chiaro.

Lo stile di un commento dovrebbe essere semplice e consistente all'interno di una singola base di codice.

* Mettete i commenti su di una nuova linea che preceda il relativo soggetto.
* Evitate commenti a fine linea.
* Mantenete una lunghezza massima per le linee, es. 80 colonne.
* Fate libero uso di commenti per spezzare il codice CSS in sezioni più piccole.
* Usate commenti "sentence case" e rientri del testo consistenti.

Suggerimento: configurate il vostro editor così che vi fornisca delle scorciatoie per la stampa dei modelli di commento scelti.

#### Esempio CSS:

```css
/* ====================================================================
   Sezione blocco commento
   ==================================================================== */

/* Sotto sezione blocco commento
   ==================================================================== */

/*
 * Gruppo blocco commento.
 * Ideale per spiegazioni e documentazione multi linea.
 */

/* Commento base */
```

#### Esempio SCSS:

```scss
// ====================================================================
// Sezione blocco commento
// ====================================================================

// Sotto sezione blocco commento
// ====================================================================

//
// Gruppo blocco commento
// Ideale per spiegazioni e documentazione multi linea.
//

// Commento base
```


## 4. Formato

Il formato del codice scelto deve far sì che il codice: sia facile da leggere; sia facile da commentare in modo chiaro; minimizzi la possibilità di introdurre accidentalmente errori; risulti in utili diff e blame.

1. Un solo selettore per linea in set di regole con più selettori.
2. Un singolo spazio prima della parentesi graffa di apertura di un set di regole.
3. Una dichiarazione per linea di un blocco dichiarazioni.
4. Un livello di rientro per ogni dichiarazione.
5. Un singolo spazio dopo i due-punti di una dichiarazione.
6. Includete sempre un punto-e-virgola alla fine dell'ultima dichiarazione in un blocco dichiarazione.
7. Mettete la parentesi graffa di chiusura di un set di regole, nella stessa colonna del primo carattere del set di regole.
8. Separate ogni set di regole con una linea vuota.

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

#### Ordine di dichiarazione

Le dichiarazioni dovrebbero essere ordinate seguendo un unico principio. Sebbene l'ordinazione alfabetica venga a volte usata, la preferenza è quella di raggruppare insieme proprietà correlate ed ordinare proprietà strutturalmente importanti (come il posizionamento e il box-model) prima delle proprietà tipografiche, dello sfondo e del colore di primo piano.

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

#### Eccezioni e piccole deviazioni

Grossi blocchi di dichiarazioni da una sola linea, possono usare un formato a linea singola leggermente differente. In questo caso, uno spazio dovrebbe essere messo dopo la parentesi graffa di apertura e prima della parentesi graffa di chiusura (vedere il seguente esempio completo).

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Valori di proprietà molto lunghi - come una complessa collezione di sfumature o ombre - possono essere suddivisi su più linee nel tentativo di migliorare la leggibilità e produrre diff più utili.

#### Varie

* Usate valori esadecimali con lettere minuscole, es. `#aaa`.
* Usate in modo consistente gli apici singoli o doppi. La preferenza è per i doppi apici, es. `content: ""` o `input[type="checkout"]`.
* _Dove permesso_, evitate di specificare l'unità di misura per i valori pari a zero, es. `margin: 0`.

### Preprocessori: considerazioni aggiuntive sul formato

Preprocessori differenti hanno differenti caratteristiche, funzionalità e sintassi. Le vostre convenzioni dovrebbero essere estese per venire incontro alle particolarità del preprocessore utilizzato. Le seguenti linee guida fanno riferimento a Sass.

* Limitate la nidificazione ad 1 livello di profondità. Riarrangiate qualsiasi livello di nidificazione che sia più di 2 livelli di profondità. Questo previene selettori CSS eccessivamente specifici.
* Evitate di usare un numero elevato di regole nidificate. Spezzettatele in più parti quando vedete che la leggibilità inizia ad essere compromessa. La preferenza è di evitare nidificazioni che coinvolgano piùdi 20 linee.
* Mettete sempre l'istruzione `@extend` alla prima linea del blocco dichiarazioni.
* Dove possibile, raggruppate le istruzioni `@include` in cima al blocco dichiarazioni, dopo tutte le istruzioni `@extend`.
* Considerate di prefissare le funzioni proprietarie con una `x-` o altro namespace. Questo vi aiuterà ad evitare ogni possibilità di confondere la vostra funzione con una funzione CSS nativa, o andare a scontrarsi con le funzioni di altre librerie.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // altre dichiarazioni
}
```


## 5. Nomenclatura

Non siete dei compilatori/compressori umani di codice, perciò non provate ad esserlo.

Usate nomi chiari ed esplicativi per le classi HTML. Scegliete un modello di nomenclatura che sia capibile e consistente, e che abbia un senso sia per i file HTML che CSS.

```css
/* Esempio di codice con nome non corretti */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Esempio di codice con nomi corretti */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


## 6. Esempio pratico

Un esempio di varie convenzioni.

```scss
/* =====================================================================
   Grid layout
   ===================================================================== */

/*
 * HTML d'esempio:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    @include box-sizing(border-box);
    overflow: visible;
    height: 100%;
    // Previene il ritorno a capo nelle celle con inline-block
    white-space: nowrap;
    // Rimuove lo spazio vuoto tra le celle
    font-size: 0;
}

.cell {
    @include box-sizing(border-box);
    @include transition(box-shadow, 0.25s, ease-in-out, 0s);
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    // Imposta lo spazio tra le celle
    padding: 0 $grid-gutter;
    border: 2px solid #333;
    vertical-align: top;
    // Reimposta white-space
    white-space: normal;
    // Reimposta font-size
    font-size: $fontsize-default;

    /* Stati della cella */

    &.is-animating {
        background-color: $cell-highlight-color
    }
}

/* Dimensioni cella
   ===================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Modificatori cella
   ===================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


## 7. Organizzazione

L'organizzazione del codice è una parte importante di ogni base di codice CSS, ed è cruciale per basi di codice ampie.

* Separate logicamente parti distinte di codice.
* Usate file separati (concatenati in un passaggio durante la generazione) per aiutarvi a suddividere il codice in componenti distinte.
* Se usate un preprocessore, astraete in variabili il codice comune per colore, tipografia, ecc.


## 8. Generazione e distribuzione

I progetti dovrebbero sempre cercare di includere un qualche meccanismo grazie al quale possano essere verificati (linted), testati, e versionati in preparazione per l'uso in produzione. Per questo lavoro, [grunt](https://github.com/cowboy/grunt) di Ben Alman è un eccellente strumento.


## Ringraziamenti

Grazie a tutti coloro che hanno contribuito a [idiomatic.js](https://github.com/rwldrn/idiomatic.js). È stato una fonte di ispirazione, citazioni e linee guida.

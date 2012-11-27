# Princìpi per la scrittura di CSS consistente ed idiomatico

L'intento di questo documento è quello di esporre una ragionevole guida allo 
stile per lo sviluppo del CSS. Queste linee guida incoraggiano al riutilizzo di
pattern già esistenti ed ampiamente testati dalla comunità. Si dovrebbe cercare,
infine, di adattare questi pattern alle proprie necessità in modo da creare
proprie regole ed un proprio stile.

Questo è un documento in continua evoluzione e nuove idee sono sempre bene 
accette. Per favore contribuite.


## Tavola dei contenuti

1. [Princìpi generali](#general-principles)
2. [Spazio vuoto](#whitespace)
3. [Commenti](#comments)
4. [Formato](#format)
5. [Esempio pratico](#example)

[Ringraziamenti](#acknowledgments)

[Licenza](#license)


<a name="general-principles"></a>
## 1. Princìpi generali

> "Parte dell'essere un buon amministratore in un progetto votato al successo è
> capire che la scrittura di codice per sé stessi è una Cattiva Idea™. Se
> migliaia di persone usano il tuo codice, allora scrivi il tuo codice in modo
> che abbia la massima chiarezza, e non seguendo i tuoi gusti personali su come
> renderlo chiaro all'interno delle specifiche" - Idan Gazit

* Non siete un compilatore/compressore umano di codice, quindi non cercate di 
esserlo.
* Tutto il codice, in qualsiasi linguaggio sia, dovrebbe sembrare come scritto
  da un'unica persona, non importa quante persone vi abbiano contribuito.
* Rispettate al massimo lo stile prescelto.
* Nel dubbio, usate pattern comuni già esistenti e collaudati.


<a name="whitespace"></a>
# 2. Spazio vuoto

Dovrebbe esistere solo uno stile in tutto il sorgente del vostro progetto.
Siate sempre consistenti nell'uso dello spazio vuoto. Usate questo spazio per
migliorare la leggibilità.

* _Mai_ mischiare spazi e tabulazioni per i rientri.
* Scegliete tra rientri soft (spazi) o tabulazioni reali. Mantenete quella
  scelta (preferenza: spazi).
* Se usate gli spazi, scegliete il numero di caratteri usati per il livello di
  rientro (preferenza: 4 spazi).

Suggerimento: configurate il vostro editor in modo da "visualizzare i caratteri
invisibili". Questo vi permetterà di eliminare spazi vuoti di fine linea e
linee vuote indesiderate, ed evitare commit pasticciati.


<a name="comments"></a>
## 3. Commenti

Un codice ben commentato è estremamente importante. Prendetevi il tempo 
necessario per descrivere i vari componenti, come funzionano, i loro limiti, 
ed il modo in cui sono stati costruiti. Non create una situazione nella quale
altri membri del vostro team debbano cercare di immaginare il motivo ed il
funzionamento di codice non comune o poco chiaro.

Lo stile di un commento dovrebbe essere semplice e consistente all'interno di
una singola base di codice.

* Mettete i commenti su di una nuova linea che preceda il relativo soggetto.
* Mantenete una lunghezza massima per le linee, es. 80 colonne.
* Fate libero uso di commenti per spezzare il codice CSS in sezioni logiche più
  piccole.
* Fate un uso corretto e consistente della grammatica, delle maiuscole e dei 
  rientri.

Suggerimento: configurate il vostro editor in modo che vi fornisca delle
scorciatoie per la gestione di pattern predefiniti per i commenti.

Esempio:

```css
/* ==========================================================================
   Sezione blocco commento
   ========================================================================== */

/* Sotto sezione blocco commento
   ========================================================================== */

/**
 * Breve descrizione utilizzando un formato nei commenti in stile Doxygen
 *
 * La prima frase di una lunga descrizione inizia qui e continua su questa
 * linea per un po' fino alla sua conclusione qui alla fine di questo paragrafo.
 *
 * Una lunga descrizione è ideale per una più dettagliata spiegazione e
 * documentazione. Essa può includere esempi in HTML, URL o qualsiasi altra
 * informazione che riteniate importante o utile.
 *
 * @tag Questo è un 'tag'
 *
 * @todo Questa è una dichiarazione 'todo' che descrive un'attività necessaria
 *   che dovrà essere completata in un momento successivo. Essa va a capo dopo
 *   80 caratteri e le linee successive vengono rientrare di 2 spazi.
 */

/* Commento base */
```


<a name="format"></a>
## 4. Formato

Il formato scelto deve far sì che il codice: sia facile da leggere;
sia facile da commentare in modo chiaro; minimizzi la possibilità di introdurre
accidentalmente errori; dia risultati utili nei diff e blame.

* Un solo selettore per linea in set di regole con più selettori.
* Un singolo spazio prima della parentesi graffa di apertura di un set di
  regole.
* Una dichiarazione per linea in un blocco dichiarativo.
* Un livello di rientro per ogni dichiarazione.
* Un singolo spazio dopo i due-punti di una dichiarazione.
* Usate valori esadecimali in minuscolo ed in forma abbreviata, es. `#aaa`.
* Usate apici e doppi apici in modo uniforme. La preferenza è per i doppi apici,
  es. `content: ""`.
* Racchiudete in doppi apici i valori nei selettori, es. `input[type="checkbox"].
* _Dove possibile_, evitate di specificare l'unità di misura per valori uguali a
  zero, es. `margin: 0`.
* Includete uno spazio dopo ogni virgola, per le liste di proprietà separate da
  virgola o per i valori nelle funzioni.
* Includete un punto-e-virgola alla fine dell'ultima dichiarazione in
   un blocco dichiarativo.
* Mettete la parentesi graffa di chiusura di un set di regole, nella stessa
  colonna del primo carattere del set di regole.
* Separate ogni set di regole con una linea vuota.

```css
.selector-1,
.selector-2,
.selector-3[type="text"] {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    font-family: helvetica, arial, sans-serif;
    color: #333;
    background: #fff;
    background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.selector-a,
.selector-b {
    padding: 10px;
}
```

#### Ordine di dichiarazione

Se le dichiarazioni devono essere ordinate in modo logico, esse dovrebbero
seguire un semplice ed unico criterio. Io preferisco che la dichiarazione di
proprietà strutturalmente importanti (cioè, posizionamento e box-model) avvenga
prima di tutto il resto.

```css
.selector {
    /* Posizionamento */
    position: relative;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Visualizzazione e box-model */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Altro */
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

Piuttosto popolare è anche l'ordinamento alfabetico, ma lo svantaggio è che così
facendo si vanno a separare proprietà in relazione tra di loro. Ad esempio, gli
offset di posizionamento non sono più raggruppati, e le proprietà del box-model
possono finire spalmate lungo tutto il blocco dichiarativo.

#### Eccezioni e piccole deviazioni

Grossi blocchi di dichiarazioni di una sola linea, possono usare un formato
leggermente differente, a linea singola. In questo caso, uno spazio dovrebbe
essere messo dopo la parentesi graffa di apertura e prima di quella di
chiusura.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Lunghe liste di valori di proprietà separate da virgole - come una collezione di
sfumature od ombre - possono essere suddivisi su più linee nel tentativo di
migliorarne la leggibilità e produrre diff più utili. Ci sono vari formati che
potrebbero essere usati; di seguito ne viene mostrato un esempio.

```css
.selector {
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
}
```

### Preprocessori: ulteriori considerazioni sul formato

Ogni preprocessore per CSS ha le sue caratteristiche, funzionalità e sintassi.
Le vostre convenzioni dovrebbero adattarsi per venire in contro alle 
particolarità del preprocessore in uso. Quelle che seguono sono le linee guida
prendendo come riferimento Sass.

* Limitate la nidificazione ad 1 livello di profondità. Riarrangiate ogni
  nidificazione con 2 o più livelli di profondità. Questo previene la creazione
  di selettori CSS inutilmente troppo specifici.
* Evitate un numero elevato di regole nidificate. Spezzatele in blocchi logici
  più piccoli quando cominciate a rendervi conto che la leggibilità inizia a
  risentirne. Preferite di evitare nidificazioni che siano più lunghe di 20
  linee.
* Come prima cosa in un blocco dichiarativo, mettete sempre le dichiarazioni
  `@extend`.
* Dove possibile, raggruppate le dichiarazioni `@include` all'inizio di un
  blocco dichiarativo, subito dopo le dichiarazioni `@extend`.
* Considerate l'idea di anteporre una `x-` o un altro namespace alle funzioni
  personalizzate. Questo vi aiuterà ad evitare ogni potenziale errore dato dalla
  confusione della vostra funzione con una funzione nativa del CSS o di altre
  librerie.
  
```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // altre dichiarazioni
}
```


<a name="example"></a>
## 5. Esempio pratico

Un esempio di varie convenzioni.

```css
/* ==========================================================================
   Layout a griglia
   ========================================================================== */

/**
 * Layout a griglia con scroll orizzontale.
 *
 * Questo crea una singola riga di colonne, a piena altezza e che non vanno
 * a capo, che può essere navigata orizzontalmente all'interno del suo
 * contenitore.
 *
 * Esempio HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 * </div>
 */

/**
 * Contenitore griglia
 * Deve contenere solo figli `.cell`.
 */
 
.grid {
    height: 100%;
    /* Rimuove lo spazio tra le celle */
    font-size: 0;
    /* Previene che le celle inline-block vadano a capo */
    white-space: nowrap;
}

/**
 * Celle della griglia
 * Di default, nessuna larghezza esplicita. Estendible con le classi `.cell-n`.
 */

.cell {
    position: relative;
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    height: 100%;
    /* Imposta la spaziatura tra le celle */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Ripristina il white-space */
    white-space: normal;
    /* Ripristina la dimensione del font */
    font-size: 16px;
}

/* Stati delle celle */

.cell.is-animating {
    background-color: #fffdec;
}

/* Larghezza delle celle
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Modificatori di cella
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


## Traduzioni

* [Česky](https://github.com/necolas/idiomatic-css/tree/master/translations/cs-CZ)
* [Dansk](https://github.com/necolas/idiomatic-css/tree/master/translations/da-DK)
* [Deutsch](https://github.com/necolas/idiomatic-css/tree/master/translations/de-DE)
* [Español](https://github.com/necolas/idiomatic-css/tree/master/translations/es-ES)
* [Français](https://github.com/necolas/idiomatic-css/tree/master/translations/fr-FR)
* [Italiano](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [日本語](https://github.com/necolas/idiomatic-css/tree/master/translations/ja-JP)
* [한국어](https://github.com/necolas/idiomatic-css/tree/master/translations/ko-KR)
* [Nederlands](https://github.com/necolas/idiomatic-css/tree/master/translations/nl-NL)
* [Polski](https://github.com/necolas/idiomatic-css/tree/master/translations/pl-PL)
* [Português (Brasil)](https://github.com/necolas/idiomatic-css/tree/master/translations/pt-BR)
* [Русский](https://github.com/necolas/idiomatic-css/tree/master/translations/ru-RU)
* [Srpski](https://github.com/necolas/idiomatic-css/tree/master/translations/sr-SR)
* [Türkçe](https://github.com/necolas/idiomatic-css/tree/master/translations/tr-TR)
* [简体中文](https://github.com/necolas/idiomatic-css/tree/master/translations/zh-CN)


<a name="acknowledgments"></a>
## Ringraziamenti

Grazie a tutti coloro che hanno fornito le traduzioni e contribuito a 
[idiomatic.js](https://github.com/rwldrn/idiomatic.js). È stato una fonte di
ispirazione, citazioni e linee guida.


<a name="license"></a>
## Licenza

_Princìpi per la scrittura di CSS consistente ed idiomatico_ di Nicolas 
Gallagher è rilasciata sotto la [Creative Commons Attribution 3.0 
Unported License](http://creativecommons.org/licenses/by/3.0/), che viene
applicata anche a tutti i documenti e traduzioni contenuti in questo
repository.

Basato sul lavoro 
[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).
# Grundlagen zum Schreiben von einheitlichem, idiomatischem CSS

Das folgende Dokument legt eine vernünftige Gestaltungsrichtlinie für die
CSS-Entwicklung dar. Diese Richtlinien ermutigen zur Verwendung existierender,
üblicher und sinnvoller Muster. Sie sollten nach Bedarf angepasst werden, um
eine eigene Gestaltungsrichtlinie zu erstellen.

Dies ist ein lebendiges Dokument, und neue Ideen sind immer willkommen. Bitte
trage bei.

[Idiomatic CSS auf englisch](https://github.com/necolas/idiomatic-css/).


## Inhaltsverzeichnis

1. [Allgemeine Grundlagen](#general-principles)
2. [Leerraum](#whitespace)
3. [Kommentare](#comments)
4. [Formatierung](#format)
5. [Praktisches Beispiel](#example)

[Danksagung](#acknowledgements)

[Lizenz](#license)


<a name="general-principles"></a>
## 1. Allgemeine Grundlagen

> „Ein Teil der Aufgabe eines guten Verwalters eines erfolgreichen Projekts ist
> es, zu realisieren, dass Code für sich selbst zu schreiben eine schlechte
> Idee™ ist. Wenn tausende Leute deinen Code verwenden, dann schreibe deinen
> Code für maximale Klarheit, nicht nach deinen persönlichen Vorlieben, wie
> man innerhalb der Spezifikation gerissen sein kann.“ - Idan Gazit

* Du bist kein menschlicher Code-Compiler/Kompressor, versuche also nicht,
  einer zu sein.
* Der gesamte Code in jeder Code-Basis soll aussehen wie von einer einzigen
  Person eingegeben, unabhängig davon, wie viele Leute beigetragen haben.
* Erzwinge den vereinbarten Stil streng.
* Im Zweifel bei einer Stilentscheidung verwende bestehende, übliche Muster.


<a name="whitespace"></a>
## 2. Leerraum

Nur ein Stil soll in den gesamten Quellen deines Projekts existieren. Sei
stets konsistent beim Einsatz von Leerraum. Verwende Leerraum, um die
Lesbarkeit zu erhöhen.

* Mische _niemals_ Leerzeichen und Tabs zur Einrückung.
* Wähle zwischen weicher Einrückung (Leerzeichen) oder wirklichen Tabs. Bleibe
  bei deiner Wahl ohne Abweichung. (Vorzug: Leerzeichen)
* Beim Einsatz von Leerzeichen wähle die Anzahl Zeichen pro Einrückebene.
  (Vorzug: 4 Leerzeichen)

Tipp: Richte deinen Editor so ein, dass er unsichtbare Zeichen zeigt. Das
erlaubt dir, Leerzeichen am Zeilenende zu entfernen, unbeabsichtigte
Leerzeichen in leeren Zeilen und Commits zu verschmutzen.

Tipp: Verwende eine [EditorConfig](http://editorconfig.org/)-Datei (oder
entsprechend), um die grundlegenden Leerraum-Konventionen, die vereinbart
wurden, verwalten zu helfen.


<a name="comments"></a>
## 3. Kommentare

Gut kommentierter Code ist essenziell. Nimm dir Zeit, Komponenten zu
beschreiben, wie sie arbeiten, welche Beschränkungen sie haben und wie sie
gebaut sind.  Lass andere im Team nicht raten, was den Zweck von ungewöhnlichem
oder nicht offensichtlichem Code betrifft.

Der Kommentarstil soll einfach und konsistent innerhalb einer einzelnen
Code-Basis sein.

* Platziere Kommentare auf neuen Zeilen über ihrem Gegenstand.
* Behalte die Zeilenlänge bei einem sinnvollen Maximum, z. B. 80 Spalten.
* Mache großzügigen Gebrauch von Kommentaren, um CSS in einzelne Abschnitte zu
  unterteilen.
* Beginne mit einem Großbuchstaben und verwende konsistente Einrückung.

Tipp: Konfiguriere deinen Editor so, dass er Kürzel für die Ausgabe von
ausgemachten Kommentar-Mustern anbietet.

Beispiel:

```css
/* ==========================================================================
   Abschnitt Kommentar-Block
   ========================================================================== */

/* Unterabschnitt Kommentar-Block
   ========================================================================== */

/**
 * Kurze Beschreibung im Doxygen-Stilformat
 *
 * Der erste Satz der langen Beschreibung beginnt hier und wird auf dieser
 * Zeile für eine Weile fortgeführt, bis er schließlich hier endet.
 *
 * Die lange Beschreibung ist ideal für detailliertere Erläuterungen und
 * Dokumentation. Sie kann Beispiel-HTML, URLs und andere Information
 * beinhalten, die nützlich oder notwendig erscheint.
 *
 * @tag Dies ist ein Schlagwort namens 'tag'
 *
 * @todo Dies ist eine Todo-Angabe, die eine unteilbare Aufgabe beschreibt,
 *   die später vollendet wird. Sie bricht nach 80 Zeichen um und folgende
 *   Zeilen sind mit zwei Leerzeichen eingerückt.
 */

/* Einfacher Kommentar */
```


<a name="format"></a>
## 4. Formatierung

Die gewählte Codeformatierung muss gewährleisten, dass der Code: leicht zu
lesen ist; leicht klar zu kommentieren ist; nicht dazu verleitet, unabsichtlich
Fehler einzuführen; und zu nützlichen Diffs und Blames der Versionsverwaltung
führt.

* Verwende einen einzelnen Selektor pro Zeile in Multi-Selektor-Regelsets.
* Füge ein einzelnes Leerzeichen vor der öffnenden Klammer eines Regelsets ein.
* Füge eine Deklaration pro Zeile in einem Deklarationsblock ein.
* Verwende eine Einrückungsebene für jede Deklaration.
* Füge ein einzelnes Leerzeichen nach dem Doppelpunkt jeder Deklaration ein.
* Verwende Kleinbuchstaben und Kurzschreibweise bei Hexwerten, z. B. `#aaa`.
* Verwende einfache oder doppelte Anführungszeichen konsistent. Doppelte
  Anführungszeichen werden bevorzugt, z. B. `content: ""`.
* Setze Attributwerte in Selektoren in Anführungszeichen, z. B.
  `input[type="checkbox"]`.
* _Wo es erlaubt ist,_ vermeide die Angabe von Einheiten für Nullwerte, z. B.
  `margin: 0`.
* Füge ein Leerzeichen nach jedem Komma ein bei kommagetrennten Eigenschaften
  oder Funktionswerten.
* Füge einen Strichpunkt nach der letzten Deklaration in einem
  Deklarationsblock ein.
* Platziere die schließende Klammer eines Regelsets in derselben Spalte wie
  das erste Zeichen des Regelsets.
* Trenne jedes Regelset mit einer Leerzeile.

```css
.selektor-1,
.selektor-2,
.selektor-3[type="text"] {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    font-family: helvetica, arial, sans-serif;
    color: #333;
    background: #fff;
    background: linear-gradient(#fff, #bbb);
    background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}

.selektor-a,
.selektor-b {
  padding: 10px;
}
```

#### Deklarations-Reihenfolge

Deklarationen sollen nach einem einzelnen, einfachen Prinzip sortiert werden,
wenn sie geordnet werden. Ich bevorzuge es, strukturell wichtige Eigenschaften
(z. B. Positionierung und Box-Modell) vor allen anderen zu notieren.

```css
.selektor {
    /* Positionierung */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Anzeige & Box-Modell */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Andere */
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

Streng alphabetische Sortierung ist ebenfalls populär, hat aber den Nachteil,
dass sie verwandte Eigenschaften trennt. Zum Beispiel sind Positions-Versätze
nicht mehr zusammen gruppiert und Box-Modell-Eigenschaften können sich über
einen ganzen Deklarationsblock verteilt wiederfinden.

#### Ausnahmen und leichte Abweichungen

Große Blöcke mit einzelnen Deklarationen können ein leicht unterschiedliches,
einzeiliges Format verwenden. In diesem Fall wird ein Leerzeichen nach der
öffnenden und vor der schließenden Klammer eingefügt.

```css
.selektor-1 { width: 10%; }
.selektor-2 { width: 20%; }
.selektor-3 { width: 30%; }
```

Lange, kommagetrennte Eigenschaftswerte - wie Sammlungen von Gradienten oder
Schatten - können über mehrere Zeilen angeordnet werden, um die Lesbarkeit zu
erhöhen und nützlichere Diffs zu produzieren. Es gibt verschiedene
Formatierungen, die verwendet werden können; ein Beispiel ist im Folgenden
gezeigt.

```css
.selektor {
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
}
```

### Präprozessoren: Zusätzliche Formatier-Überlegungen

Verschiedene CSS-Präprozessoren haben verschiedene Besonderheiten,
Funktionalität und Syntax. Deine Konventionen sollen so erweitert werden, dass
sie den Eigenheiten jedes verwendeten Präprozessors Rechnung tragen. Die
folgenden Richtlinien beziehen sich auf Sass.

* Beschränke Verschachtelungen auf eine Ebene Tiefe. Überprüfe jede
  Verschachtelung tiefer als 2 Ebenen. Das verhindert übermäßig spezifische
  CSS-Selektoren.
* Vermeide große Mengen verschachtelter Regeln. Brich sie in Teile auf, wenn
  Lesbarkeit beeinträchtigt wird. Der Vorzug gilt dem Vermeiden von
  verschachtelten Anweisungen mit mehr als 20 Zeilen Länge.
* Setze `@extend`-Angaben immer in die erste Zeile eines Deklarationsblocks.
* Wo möglich gruppiere `@include`-Angaben am Anfang eines Deklarationsblocks,
  nach jedem `@extend`.
* Ziehe in Betracht, eigenen Funktionen `x-` oder einen anderen Namensraum
  voranzustellen. Das hilft zu verhindern, dass deine Funktionen mit nativen
  CSS-Funktionen verwechselt werden oder mit Funktionen anderer Bibliotheken
  kollidieren.

```scss
.selektor-1 {
    @extend .andere-regel;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // andere Deklarationen
}
```


<a name="example"></a>
## 5. Praktisches Beispiel

Ein Beispiel verschiedener Konventionen.

```css
/* ==========================================================================
   Rasterlayout
   ========================================================================== */

/**
 * Beispiel-Layout mit horizontalem Scrollen.
 *
 * Dies erzeugt eine Reihe von maximal-hohen, nicht umbrechenden Spalten, die
 * horizontal innerhalb ihres Elternelements durchsucht werden können.
 *
 * Beispiel-HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 * </div>
 */

/**
 * Grid-Container
 * Darf nur `.cell`-Kinder enthalten.
 */

.grid {
    height: 100%;
    /* Verhindere Leerraum in Zellen */
    font-size: 0;
    /* Hindere inline-block-Zellen am Umbruch */
    white-space: nowrap;
}

/**
 * Grid-Zellen
 * Keine vorgegebene Breite. Erweitere mit `.cell-n`-Klassen.
 */

.cell {
    position: relative;
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    height: 100%;
    /* Setzt den Abstand zwischen Zellen */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Stellt Leerraum wieder her */
    white-space: normal;
    /* Stellt Schriftgröße wieder her */
    font-size: 16px;
}

/* Zell-Zustände */

.cell.is-animating {
    background-color: #fffdec;
}

/* Zell-Abmessungen
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Zell-Modifikatoren
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="acknowledgements"></a>
## Danksagung

Danke an alle, die Übersetzungen erstellt haben und all jene, die zu
[idiomatic.js](https://github.com/rwldrn/idiomatic.js) beigetragen haben. Es
war eine Quelle der Inspiration, von Zitaten und Richtlinien.


<a name="license"></a>
## Lizenz

_Grundlagen zum Schreiben von einheitlichem, idiomatischem CSS_ von Nicolas
Gallagherist lizenziert unter der [Creative Commons Attribution 3.0
Unported-License](http://creativecommons.org/licenses/by/3.0/). Dies trifft
auf alle Dokumente und Übersetzungen in diesem Repository zu.

Basierend auf einer Arbeit auf
[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).

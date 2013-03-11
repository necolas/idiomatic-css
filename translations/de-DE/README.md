# Grundlagen zum Schreiben von einheitlichem, idiomatischem CSS

Das folgende Dokument legt einen vernünftige Gestaltungsrichtlinie für die
CSS-Entwicklung dar. Es soll nicht verordnend sein, und ich möchte meine
Stil-Vorlieben nicht dem Code anderer Leute aufzwängen. Allerdings ermutigen
diese Richtlinien zum Einsatz von bestehenden, üblichen, sinnvollen Mustern.

Dies ist ein lebendiges Dokument, und neue Ideen sind immer willkommen. Bitte
trage bei.

[Idiomatic CSS auf englisch](https://github.com/necolas/idiomatic-css/)


## Inhaltsverzeichnis

1. [Allgemeine Grundlagen](#general-principles)
2. [Leerraum](#whitespace)
3. [Kommentare](#comments)
4. [Formatierung](#format)
5. [Benennung](#naming)
6. [Praktisches Beispiel](#example)
7. [Organisierung](#organization)
8. [Bauen und Einsetzen](#build-and-deployment)

[Danksagung](#acknowledgements)


<a name="general-principles"></a>
## 1. Allgemeine Grundlagen

> „Ein Teil der Aufgabe eines guten Verwalters eines erfolgreichen Projekts ist
> es, zu realisieren, dass Code für sich selbst zu schreiben eine schlechte
> Idee™ ist. Wenn tausende Leute deinen Code verwenden, dann schreibe deinen
> Code für maximale Klarheit, nicht nach deinen persönlichen Vorlieben, wie man
> innerhalb der Spezifikation gerissen sein kann.“ - Idan Gazit

* Der gesamte Code in jeder Code-Basis soll aussehen wie von einer einzigen
  Person eingegeben, unabhängig davon wieviele Leute beigetragen haben.
* Erzwinge den vereinbarten Stil streng.
* Im Zweifel verwende bestehende, übliche Muster.


<a name="whitespace"></a>
## 2. Leerraum

Nur ein Stil soll in den vollständigen Quellen deines Projekts existieren.  Sei
stets konsistent beim Einsatz von Leerraum. Verwende Leerraum, um die
Lesbarkeit zu erhöhen.

* Mische niemals Leerzeichen und Tabs zur Einrückung.
* Wähle zwischen weicher Einrückung (Leerzeichen) oder wirklichen Tabs. Bleibe
  bei deiner Wahl ohne Abweichung. (Vorzug: Leerzeichen)
* Beim Einsatz von Leerzeichen wähle die Anzahl Zeichen pro Einrückebene.
  (Vorzug: 4 Leerzeichen)

Tip: Richte deinen Editor so ein, dass er unsichtbare Zeichen zeigt. Das
erlaubt dir, Leerzeichen am Zeilenende zu entfernen, unbeabsichtigte
Leerzeichen in leeren Zeilen und Commits zu verschmutzen.


<a name="comments"></a>
## 3. Kommentare

Gut kommentierter Code ist extrem wichtig. Nimm dir Zeit, Komponenten zu
beschreiben, wie sie arbeiten, welche Beschränkungen sie haben und wie sie
gebaut sind.  Lass andere im Team nicht raten, was den Zweck von ungewöhnlichem
oder nicht offensichtlichem Code betrifft.

Der Kommentarstil soll einfach und konsistent innerhalb einer einzelnen
Code-Basis sein.

* Platziere Kommentare auf neuen Zeilen über ihrem Gegenstand.
* Vermeide Kommentare am Zeilenende
* Behalte die Zeilenlänge bei einem sinnvollen Maximum, z.B. 80 Spalten.
* Mache freigebig Gebrauch von Kommentaren, um CSS in einzelne Abschnitte zu
  unterteilen.
* Beginne mit einem Großbuchstaben und verwende konsistente Einrückung.

Tip: Konfiguriere deinen Editor so, dass er Kürzel für die Ausgabe von
ausgemachten Kommentar-Mustern anbietet.

#### Beispiel:

```css
/* ==========================================================================
   Abschnitt Kommentar-Block
   ========================================================================== */

/* Unterabschnitt Kommentar-Block
   ========================================================================== */

/**
 * Kurze Beschreibung im Doxygen-Stilformat
 *
 * Lange Beschreibung erster Satz beginnt hier und wird auf dieser Zeile für
 * eine Weile fortgeführt bis er schließlich hier endet.
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
lesen ist; leicht kar zu kommentieren ist; nicht dazu verleitet, unabsichtlich
Fehler einzuführen; und zu nützlichen Diffs und Blames der Versionsverwaltung
führt.

1. Ein einzelner Selektor pro Zeile in Multi-Selektor-Regelsets.
2. Ein einzelnes Leerzeichen vor der öffnenden Klammer eines Regelsets.
3. Eine Deklaration pro Zeile in einem Deklarationsblock.
4. Eine Einrückungsebene für jede Deklaration.
5. Ein einzelnes Leerzeichen nach dem Doppelpunkt jeder Deklaration.
6. Wenn Eigenschaften oder Funktionen mehrere komma-getrennte Werte haben
   können, füge ein Leerzeichen nach jedem Komma ein.
7. Füge immer einen Strichpunkt nach der letzten Deklaration in einem
   Deklarationsblock ein.
8. Platziere die schließende Klammer eines Regelsets in derselben Spalte wie
   das erste Zeichen des Regelsets.
9. Trenne jedes Regelset mit einer Leerzeile.

```css
.selektor-1,
.selektor-2,
.selektor-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    font-family: helvetica, arial, sans-serif;
    color: #333;
    background: #fff;
    background: linear-gradient(#fff, #bbb);
}
```

#### Deklarations-Reihenfolge

Deklarationen sollen nach einem einzelnen Prinzip sortiert werden. Ich
bevorzuge es, verwandte Eigenschaften zusammen zu gruppieren und strukturell
wichtige Eigenschaften (z.B. Positionierung und Box-Modell) vor typografischen,
Hintergrund- oder Farbanweisungen zu notieren.

```css
.selektor {
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

Alphabetische Sortierung ist ebenfalls populär, hat aber den Nachteil, dass
sie verwandte Eigenschaften trennt. Zum Beispiel sind Positions-Versätze nicht
mehr zusammen gruppiert und Box-Modell-Eigenschaften können sich über einen
ganzen Deklarationsblock verteilt wiederfinden.

#### Ausnahmen und leichte Abweichungen

Große Blöcke mit einzelnen Deklarationen können ein leicht unterschiedliches,
einzeiliges Format verwenden. In diesem Fall wird ein Leerzeichen nach der
öffnenden und vor der schließenden Klammer eingefügt.

```css
.selektor-1 { width: 10%; }
.selektor-2 { width: 20%; }
.selektor-3 { width: 30%; }
```

Lange, komma-getrennte Eigenschaftswerte - wie Sammlungen von Gradienten oder
Schatten - können über mehrere Zeilen angeordnet werden, um die Lesbarkeit zu
erhöhen und nützlichere Diffs zu produzieren. Es gibt verschiedene
Formatierungen, die verwendet werden können; ein Beispiel ist im Folgenden
gezeigt.

```css
.selektor {
    box-shadow:
        1px 1px 1px #000,
        2px 2px 1px 1px #ccc inset;
    background-image:
        linear-gradient(#fff, #ccc),
        linear-gradient(#f3c, #4ec);
}
```

#### Verschiedenes

* Verwende kleingeschriebene Hexwerte, z.B. `#aaa`.
* Verwende einfache oder doppelte Anführungszeichen konsistent. Der Vorzug gilt
  doppelten Anführungszeichen, z.B. `content: ""`.
* Setze Attributswerte in Selektoren immer in Anführungszeichen, z.B.
  `input[type="checkbox"]`.
* _Wo es erlaubt ist_, vermeide es, Einheiten für 0-Werte anzugeben, z.B.
  `margin: 0`.

### Präprozessoren: Zusätzliche Formatier-Überlegungen

Verschiedene CSS-Präprozessoren haben verschiedene Besonderheiten,
Funktionalität und Syntax. Deine Konventionen sollen so erweitert werden, dass
sie den Eigenheiten jedes verwendeten Präprozessors Rechnung tragen. Die
folgenden Richtlinien beziehen sich auf Sass.

* Beschränke Verschachtelungen auf eine Ebene Tiefe. Überprüfe jede
  Verschachtelung tiefer als 2 Ebenen. Das verhindert übermäßg spezifische
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


<a name="naming"></a>
## 5. Benennung

Du bist kein menschlicher Code-Compiler/-Kompressor, also versuche nicht, einer
zu sein.

Verwende klare und durchdachte Namen für HTML-Klassen. Wähle ein verständliches
und konsistentes Namensschema, das sowohl in HTML- als auch in CSS-Dateien
sinnvoll ist.

```css
/* Beispiel von Code mit schlechten Namen */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Beispiel von Code mit besseren Namen */

.ist-scrollbar {
    overflow: auto;
}

.spalten-körper {
    background: #000;
}
```


<a name="example"></a>
## 6. Praktisches Beispiel

Ein Beispiel verschiedener Konventionen.

```css
/* ==========================================================================
   Rasterlayout
   ========================================================================== */

/**
 * Beispiel-HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Hindere inline-block-Zellen am Umbruch */
    white-space: nowrap;
    /* Verhindere Leerraum in Zellen */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Setze den Avstand zwischen Zellen */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Stelle Leerraum wieder her */
    white-space: normal;
    /* Stelle Schriftgröße wieder her */
    font-size: 16px;
}

/* Zellen-Zustände */

.cell.is-animating {
    background-color: #fffdec;
}

/* Zellen-Abmessungen
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Zellen-Modifikatoren
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organization"></a>
## 7. Organisierung

Code-Organisation ist ein wichtiger Teil jeder CSS-Code-Basis und wesentlich
für große Projekte.

* Teile eigenständige Code-Teile logisch auf.
* Verwende einzelne Dateien (in einem Bau-Schritt zusammengesetzt) als Hilfe
  zur Aufteilung des Codes in eigenständige Komponenten.
* Lagere beim Einsatz eines Präprozessors oft verwendeten Code in Variablen
  für Farbe, Typografie usw. aus.


<a name="build-and-deployment"></a>
## 8. Bauen und Einsetzen

Projekte sollen stets versuchen, generische Methoden zu verwenden, um Quelltext
im Vorfeld des Produktiveinsatzes zu bereinigen, testen, packen und
versionieren. Für diesen Zweck bietet sich
[grunt](https://github.com/cowboy/grunt) von Ben Alman als exzellentes Werkzeug
an.


<a name="acknowledgements"></a>
## Danksagung

Danke an alle, die zu [idiomatic.js](https://github.com/rwldrn/idiomatic.js)
beigetragen haben. Es war eine Quelle der Inspiration, von Zitaten und
Richtlinien.

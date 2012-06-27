# Grundlagen zum Schreiben von einheitlichem, idiomatischem CSS

Das folgende Dokument legt einen vernünftige Gestaltungsrichtlinie für die
CSS-Entwicklung dar. Es soll nicht verordnend sein, und ich möchte meine
Stil-Vorlieben nicht dem Code anderer Leute aufzwängen. Allerdings ermutigen
diese Richtlinien zum Einsatz von bestehenden, üblichen, sinnvollen Mustern.

Dies ist ein lebendiges Dokument, und neue Ideen sind immer willkommen. Bitte
trage bei.


## Übersetzungen

* [Français](https://github.com/necolas/idiomatic-css/tree/master/translations/fr-FR)
* [Italiano](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [日本語](https://github.com/necolas/idiomatic-css/tree/master/translations/ja-JP)
* [한국어](https://github.com/necolas/idiomatic-css/tree/master/translations/ko-KR)
* [Nederlands](https://github.com/necolas/idiomatic-css/tree/master/translations/nl-NL)
* [Português (Brasil)](https://github.com/necolas/idiomatic-css/tree/master/translations/pt-BR)
* [Русский](https://github.com/necolas/idiomatic-css/tree/master/translations/ru-RU)
* [Srpski](https://github.com/necolas/idiomatic-css/tree/master/translations/sr)
* [Türkçe](https://github.com/necolas/idiomatic-css/tree/master/translations/tr-TR)
* [简体中文](https://github.com/necolas/idiomatic-css/tree/master/translations/zh-CN)


## Inhaltsverzeichnis

1. [Allgemeine Grundlagen](#allgemeine-grundlagen)
2. [Leerraum](#leerraum)
3. [Kommentare](#kommentare)
4. [Formatierung](#formatierung)
5. [Benennung](#benennung)
6. [Praktisches Beispiel](#beispiel)
7. [Organisierung](#organisierung)
8. [Bauen und Einsetzen](#bauen-und-einsetzen)

[Danksagung](#danksagung)


<a name="allgemeine-grundlagen"></a>
## 1. Allgemeine Grundlagen

> „Ein Teil der Aufgabe eines guten Verwalters eines erfolgreichen Projekts
> ist es, zu realisieren, dass Code für sich selbst zu schreiben eine schlechte
> Idee™ ist. Wenn tausende Leute deinen Code verwenden, dann schreibe deinen
> Code für maximale Klarheit, nicht nach deinen persönlichen Vorlieben, wie
> man innerhalb der Spezifikation gerissen sein kann.“ - Idan Gazit

* Der gesamte Code in jeder Code-Basis sollte aussehen wie von einer einzigen
  Person eingegeben, unabhängig davon wieviele Leute beigetragen haben.
* Erzwinge den vereinbarten Stil streng.
* Im Zweifel verwende bestehende, übliche Muster.


<a name="leerraum"></a>
## 2. Leerraum

Nur ein Stil sollte in den vollständigen Quellen deines Projekts existieren.
Sei stets konsistent beim Einsatz von Leerraum. Verwende Leerraum, um
die Lesbarkeit zu erhöhen.

* Mische niemals Leerzeichen und Tabs zur Einrückung.
* Wähle zwischen weicher Einrückung (Leerzeichen) oder wirklichen Tabs. Bleibe
  bei deiner Wahl ohne Abweichung. (Vorzug: Leerzeichen)
* Beim Einsatz von Leerzeichen wähle die Anzahl Zeichen pro Einrückebene.
  (Vorzug: 4 Leerzeichen)

Tip: Richte deinen Editor so ein, dass er unsichtbare Zeichen zeigt. Das
erlaubt dir, Leerzeichen am Zeilenende zu entfernen, unbeabsichtigte Leerzeichen
in leeren Zeilen und Commits zu verschmutzen.


<a name="kommentare"></a>
## 3. Kommentare

Gut kommentierter Code ist extrem wichtig. Nimm dir Zeit, Komponenten zu beschreiben,
wie sie arbeiten, welche Beschränkungen sie haben und wie sie gebaut sind.
Lass andere im Team nicht raten, was den Zweck von ungewöhnlichem oder nicht
offensichtlichem Code betrifft.

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


<a name="formatierung"></a>
## 4. Formatierung


<a name="benennung"></a>
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


<a name="beispiel"></a>
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


<a name="organisierung"></a>
## 7. Organisierung

Code-Organisation ist ein wichtiger Teil jeder CSS-Code-Basis und wesentlich
für große Projekte.

* Teile eigenständige Code-Teile logisch auf.
* Verwende einzelne Dateien (in einem Bau-Schritt zusammengesetzt) als Hilfe
  zur Aufteilung des Codes in eigenständige Komponenten.
* Lagere beim Einsatz eines Präprozessors oft verwendeten Code in Variablen
  für Farbe, Typografie usw. aus.


<a name="bauen-und-einsetzen"></a>
## 8. Bauen und Einsetzen

Projekte sollten stets versuchen, generische Methoden zu verwenden, um
Quelltext im Vorfeld des Produktiveinsatzes zu bereinigen, testen, packen und
versionieren. Für diesen Zweck bietet sich [grunt](https://github.com/cowboy/grunt)
von Ben Alman als exzellentes Werkzeug an.


<a name="danksagung"></a>
## Danksagung

Danke an alle, die zu [idiomatic.js](https://github.com/rwldrn/idiomatic.js)
beigetragen haben. Es war eine Quelle der Inspiration, von Zitaten und
Richtlinien.

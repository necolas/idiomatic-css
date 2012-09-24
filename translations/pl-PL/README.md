# Zasady tworzenia spójnych, zgodnych z regułami języka deklaracji CSS

Poniżej opisane zostały podstawowe zasady tworzenia arkuszy stylów.  Nie jest
to uniwersalne czy wyczerpujące temat zestawienie. Intencją autora nie było
bowiem narzucanie jedynie słusznych rozwiązań, a raczej zachęta do stosowania
istniejących, wypróbowanych i uznanych wzorców.

Z tego samego powodu mile widziana będzie wszelka pomoc w dalszym rozwijaniu i
wzbogacaniu niniejszego dokumentu.


[Artykuł Idiomatic CSS w oryginale](https://github.com/necolas/idiomatic-css/)


## Spis treści

1. [Główne zasady](#general-principles)
2. [Wcięcia](#whitespace)
3. [Komentarze](#comments)
4. [Format](#format)
5. [Nazewnictwo](#naming)
6. [Przykłady praktyczne](#example)
7. [Organizacja](#organization)
8. [Przygotowanie i wdrożenie](#build-and-deployment)

[Podziękowania](#acknowledgements)


<a name="general-principles"></a>
## 1. Główne zasady

> „Pierwszym krokiem do stworzenia projektu, który odniesie sukces, jest
> zrozumienie, że pisanie kodu dla samego siebie to Bardzo Zły Pomysł®.  Jeśli
> z twoich rozwiązań mają korzystać tysiące innych osób, nie pisz tak, jak
> lubisz, ale tak, by osiągnąć maksymalną przejrzystość.” - Idan Gazit

* Nie jesteś maszyną do kompilowania czy kompresowania kodu i nie staraj się
  nią zostać.
* Kod powinien zawsze wyglądać tak, jakby napisał go jeden człowiek -
  niezależnie od liczby osób współpracujących przy tym zadaniu.
* Trzymaj się ściśle ustalonych na wstępie reguł.
* Jeśli masz wątpliwości, korzystaj z istniejących, sprawdzonych rozwiązań.


<a name="whitespace"></a>
## 2. Wcięcia

W całym projekcie stosuj konsekwentnie tylko jeden styl wcięć. Nie zapominaj,
że wcięcia służą przede wszystkim czytelności kodu.

* _Nigdy_ nie stosuj równolegle spacji i tabulatorów.
* Wybierz jedną z powyższych metod do tworzenia wcięć (najlepiej spacje) i
  trzymaj się jej.
* Jeśli używasz spacji, wybierz stałą liczbę znaków dla jednego poziomu wcięcia
  (najlepiej cztery).

Wskazówka: włącz w swoim edytorze kodu opcję pokazywania znaków
niedrukowalnych.  To pozwoli ci wyeliminować spacje na końcu linii i w pustych
wierszach.

Wskazówka: używaj pliku [EditorConfig](http://editorconfig.org/) albo innego
rozwiązania, które pomoże ci trzymać się ustalonych zasad tworzenia wcięć.


<a name="comments"></a>
## 3. Komentarze

Dokładne dokumentowanie kodu jest niezwykle istotne. Poświęć czas na opisanie
komponentów, ich działania i ograniczeń oraz sposobu ich tworzenia. Nie pozwól,
żeby inni członkowie zespołu musieli domyślać się znaczenia kodu.

Styl tworzenia komentarzy powinien być prosty i spójny w obrębie całego
projektu.

* Umieszczaj komentarze w nowej linii, nad elementem, który opisują.
* Unikaj tworzenia komentarzy na końcu linii.
* Utrzymuj sensowne maksimum długości linii, np. 80 znaków.
* Używaj komentarzy do dzielenia kodu CSS na osobne sekcje.
* Komentuj, używając standardowych zdań i wcięć akapitów.

Wskazówka: skonfiguruj swój edytor tak, byś mógł stosować skróty klawiszowe do
wstawiania komentarzy w ustalonej wcześniej postaci.

#### Przykład:

```css
/* ==========================================================================
   Blok komentarzy sekcji
   ========================================================================== */

/* Blok komentarzy podsekcji
   ========================================================================== */

/**
 * Krótki opis z zastosowaniem formatowania w stylu Doxygen
 *
 * Długi opis - pierwsze zdanie rozpoczyna się tutaj i biegnie jeszcze przez
 * chwilę, zajmując cały wiersz, aby wreszcie zakończyć się konkluzją w tym
 * miejscu, u dołu akapitu.
 *
 * Dłuższy opis jest najlepszym miejscem do umieszczenia szczegółowych
 * objaśnień i dokumentacji. Może zawierać przykładowy kod HTML, adresy
 * internetowe oraz inne przydatne informacje.
 *
 * @tag To jest znacznik o nazwie 'tag'
 *
 * @todo To jest opis todo, wskazujący istotne zadanie, które należy wykonać
 *   później. Zawija się po około 80 znakach a kolejne linie są wcięte za
 *   pomocą 2 spacji.
 */

/* Podstawowy komentarz */
```


<a name="format"></a>
## 4. Format

Wybrany format kodu musi gwarantować, że kod ten będzie łatwy do przeczytania i
skomentowania, co w efekcie zminimalizuje szanse przypadkowego popełnienia
błędu.  W ten sposób także tworzenie przejrzystych zestawień zmian w plikach i
wskazywanie osób odpowiedzialnych za określone poprawki stanie się znacznie
łatwiejszym zadaniem.

* W deklaracjach z wieloma selektorami używaj jednego selektora w linii.
* Wstawiaj jedną spację przed nawiasem otwierającym zestaw reguł.
* W bloku reguł umieszczaj jedną deklarację w wierszu.
* Stosuj jeden poziom wcięcia dla każdej deklaracji.
* Wstawiaj jedną spację po dwukropku w deklaracji.
* Używaj wartości pisanych małymi literami i skrótów, np. `#aaa`.
* Stosuj pojedyncze i podwójne cudzysłowy w sposób spójny. Preferuj jednak
  podwójne, jak na przykład `content: ""`.
* Wyodrędbniaj cudzysłowami wartości atrybutów w selektorach, na przykład
  `input[type="checkbox"]`.
* _Tam gdzie to możliwe_ unikaj podawania jednostek dla wartości zerowych, na
  przykład `margin: 0`.
* W oddzielonych przecinkami właściwościach wstawiaj spację po każdym
  przecinku.
* Pamiętaj o średniku na końcu ostatniej deklaracji w bloku.
* Nawias zamykający zestaw reguł umieszczaj w tej samej kolumnie (z tym samym
  wcięciem), co otwierający.
* Bloki deklaracji oddzielaj pustą linią.

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
    background: linear-gradient(#fff, rgba(0, 0, 0, 0.8));
}
```

#### Kolejność deklaracji

Deklaracje powinny być uporządkowane zgodnie z jedną, przyjętą na wstępie
regułą. Preferowanym przeze mnie sposobem jest umieszczanie na początku
właściwości określających strukturę elementu - czyli np. jego pozycję i
wymiary.

```css
.selektor {
    /* Pozycja */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Wyświetlanie i wymiary */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Inne */
    background: #000;
    color: #fff
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

Stosunkowo popularne jest także porządkowanie deklaracji alfabetycznie. Metoda
ta ma jednak taką wadę, że oddziela od siebie powiązane właściwości. W takim
wypadku np. definicje marginesów, odstępów, wysokości i szerokości elementu
będą rozrzucone po całym bloku.

#### Wyjątki i drobne odstępstwa

Duże fragmenty arkusza zawierające pojedyncze deklaracje można formatować nieco
inaczej, ujmując całość w jednym wierszu. W takim wypadku po nawiasie
otwierającym oraz przed zamykającym należy wstawić spację.

```css
.selektor-1 { width: 10%; }
.selektor-2 { width: 20%; }
.selektor-3 { width: 30%; }
```

Dłuższe, oddzielone przecinkami właściwości, np. zestawy gradientów albo cieni,
można rozbijać na kilka linii, by poprawić czytelność i ułatwić generowanie
przejrzystych zestawień zmian. Poniższy przykład obrazuje jedno z możliwych
rozwiązań:

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

### Preprocesory: dodatkowe uwagi dotyczące formatu

Różne narzędzia do wstępnego przetwarzania kodu CSS mają zróżnicowane
możliwości i składnię. W związku z tym zasady postępowania należy ustalać
zawsze w odniesieniu do unikalnych właściwości danego preprocesora. Te wskazane
niżej odnoszą się do jednego z nich - Sass.

* Ogranicz zagnieżdżanie do jednego poziomu. To pozwoli ci uniknąć tworzenia
  nazbyt szczegółowych selektorów.
* Unikaj stosowania dużej liczby zagnieżdżonych reguł. 20 wierszy wydaje się
  być rozsądną granicą. Podziel kod na mniejsze fragmenty, gdy tylko zauważysz,
  że traci na czytelności.
* Pamiętaj o umieszczaniu `@extend` w pierwszych liniach bloku deklaracji.
* Gdy to możliwe, grupuj `@include` na początku bloku deklaracji, zaraz za
  `@extend`.
* Nazwy tworzonych przez siebie funkcji poprzedzaj `x-` lub innym prefiksem.
  Pomoże ci to odróżnić je w trakcie pracy od domyślnych funkcji CSS i uniknąć
  konfliktów z funkcjami zawartymi w innych bibliotekach.

```scss
.selektor-1 {
    @extend .inna-regula;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-jednostka-siatki(1);
    // pozostałe deklaracje
}
```


<a name="naming"></a>
## 5. Nazewnictwo

Wybór odpowiedniego nazewnictwa jest trudny, ale bardzo istotny. To kluczowy
element w procesie tworzenia łatwej w aktualizacji i elastycznej bazy kodu
CSS.

* Unikaj _zbyt częstego_ wykorzystywania skróconych nazw klas. Nie komplikuj
  kodu ponad potrzebę.
* Używaj jasnych, kojarzących się, dobrze przemyślanych nazw klas.
* Wybierz zrozumiały i spójny wzorzec tworzenia nazw, który będzie zrozumiały
  zarówno w trakcie lektury kodu HTML, jak i CSS.
* Selektory dla komponentów strony powinny wykorzystywać nazwy klas - unikaj
  używania nazw tagów i identyfikatorów (id).

```css
/* Przykład kodu z kiepskimi nazwami klas */

.m-prz {
    overflow: auto;
}

.tk {
    background: #000;
}

/* Przykład kodu z lepszymi nazwami */

.mozna-przewijac {
    overflow: auto;
}

.tekst-kolumny {
    background: #000;
}
```


<a name="example"></a>
## 6. Przykłady praktyczne

Propozycje zastosowania opisanych wcześniej konwencji.

```css
/* ==========================================================================
   Siatka
   ========================================================================== */

/**
 * Przykładowy kod HTML:
 *
 * <div class="siatka">
 *     <div class="komorka komorka-5"></div>
 *     <div class="komorka komorka-5"></div>
 * </div>
 */

.siatka {
    overflow: visible;
    height: 100%;
    /* Zapobiegaj zawijaniu tekstu w komórkach z inline-block */
    white-space: nowrap;
    /* Usuń spacje między komórkami */
    font-size: 0;
}

.komorka {
    position: relative;
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 20%;
    height: 100%;
    /* Ustaw odstępy między komórkami */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Resetuj spacje */
    white-space: normal;
    /* Resetuj rozmiar czcionki */
    font-size: 16px;
}

/* Stany komórek */

.komorka.jest-animowana {
    background-color: #fffdec;
}

/* Wymiary komorek
   ========================================================================== */

.komorka-1 { width: 10%; }
.komorka-2 { width: 20%; }
.komorka-3 { width: 30%; }
.komorka-4 { width: 40%; }
.komorka-5 { width: 50%; }

/* Modyfikacje komorek
   ========================================================================== */

.komorka--szczegoly,
.komorka--istotne {
    border-width: 4px;
}
```


<a name="organization"></a>
## 7. Organizacja

Odpowiednia organizacja jest istotnym elementem tworzenia każdej bazy kodu CSS.
W przypadku dużych baz to wręcz kwestia kluczowa.

* Pamiętaj o logicznym wyodrębnianiu samodzielnych fragmentów kodu.
* Używaj osobnych plików (łączonych podczas budowania kodu) aby w prosty sposób
  dzielić kod na mniejsze komponenty.
* Jeśli używasz preprocesora, powtarzające się definicje kolorów, typografii
  itp. przypisuj do zmiennych.


<a name="build-and-deployment"></a>
## 8. Przygotowanie i wdrożenie

W projektach powinno się zawsze wdrażać pewne ogólne zasady, według których kod
źródłowy może być analizowany, testowany, kompresowany i wersjonowany przed
wdrożeniem. Doskonałym narzędziem służącym do tego celu jest
[grunt](https://github.com/cowboy/grunt) autorstwa Bena Almana.


<a name="acknowledgements"></a>
## Podziękowania

Dziękuję wszystkim, którzy współtworzyli
[idiomatic.js](https://github.com/rwldrn/idiomatic.js).  Projekt ten był dla
mnie źródłem inspiracji, cytatów i wskazówek.

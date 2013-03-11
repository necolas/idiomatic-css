# Zásady psaní konzistentního, idiomatického CSS

Tohle je příručka stylu (_style guide_) pro psaní CSS. Neberte ji jako
nařizující, nechci jiným lidem vnucovat styl psaní kódu podle svých preferencí.
Následující zásady ale silně podporují využívání existujících vzorů jež
považuji za obvyklé a rozumné.

Na dokumentu se pracuje a nové nápady vítám. Přispějte jimi prosím.


[Idiomatic CSS anglicky](https://github.com/necolas/idiomatic-css/)


## Obsah

1. [Obecné principy](#general-principles)
2. [Bílá mezera](#whitespace)
3. [Komentáře](#comments)
4. [Formát](#format)
5. [Pojmenovávání](#naming)
6. [Praktická ukázka](#example)
7. [Uspořádání](#organization)
8. [Build a deploy](#build-and-deployment)

[Poděkování](#acknowledgements)


<a name="general-principles"></a>
## 1. Obecné principy

> „Pokud chcete být dobrý správce úspěšného projektu, musíte si kromě jiného
> uvědomit, že psaní kódu pro sebe je dost blbý nápad. Pokud váš kód užívají
> tisíce lidí, musíte jej psát pro maximální srozumitelnost a ne pro svou
> radost z dodržení specifikace.” - Idan Gazit

* Nejste lidský kompiler ani kompresor kódu. Nesnažte se jím stát.
* Veškerý kód jednoho projektu by měl vypadat jako by ho napsal jediný člověk.
  Bez ohledu na to kolik lidí přispělo.
* Striktně vymáhejte dohodnutý styl.
* V případě pochybností o dohodnutém stylu, použijte existující obecné vzory.


<a id="whitespace"></a>
## 2. Bílá mezera

V kódu vašeho projektu by měl existovat jen jediný styl užívání bílé mezery
(_whitespace_). Zlepšujte s její pomocí čitelnost.

* Nikdy pro odsazování nepoužívejte mezery a zároveň tabulátory.
* Vyberte si buď měkké odsazení (pomocí mezer) nebo skutečné tabulátory.  Držte
  se svého výběru bez výjimky. (Upřednostňujte mezery)
* Pokud používáte mezery, zvolte si počet znaků používaných pro úroveň
  odsazení. (Upřednostňujte 4 mezery)

Tip: nastavte si editor tak, aby zobrazoval neviditelné znaky. To vám umožní
potlačit bílé mezery na konci řádků nebo nechtěné prázdné řádky s bílou
mezerou. Zabráníte tak zaneřádění commitů.

Tip: používejte soubor [EditorConfig](http://editorconfig.org/) (nebo něco
podobného) aby vám pomohl dodržovat úmluvy o bílých mezerách, které jste
dohodli pro celý projekt.


<a name="comments"></a>
## 3. Komentáře

Dobře komentovat kód je hrozně důležité. Udělejte si čas pro popis komponent,
toho jak pracují, jejich omezení, a způsobu jakým jsou sestrojeny. Nenechávejte
ostatní v týmu odhadovat účel neobvyklého nebo málo zřejmého kódu.

Styl komentářů by měl být jednoduchý a konzistentní pro celý projekt.

* Umísťujte komentáře na nový řádek nad jejich subjekt.
* Vyhněte se komentářům na konci řádky.
* Ponechte šířku řádky na citlivém maximu, například 80 znacích.
* Velkorysým používáním komentářů dělte CSS kód do jednotlivých sekcí.
* Pište komentáře ve větách (_sentence case_) a text konzistentně odsazujte.

Tip: Nastavte si editor tak, abyste dohodnuté komentářové vzory měli vždy po
ruce.

#### Example:

```css
/* ==========================================================================
   Nadpis pro sekci
   ========================================================================== */

/* Nadpis pro podsekci
   ========================================================================== */

/**
 * Kratky popis co se drzi komentaroveho formatu Doxygen
 *
 * Tady zacina prvni veta dlouheho popisu a chvili pokracuje dokud neskonci
 * na dalsim radku.
 *
 * Nejdelsi popisek je idealni pro detailnejsi vysvetleni a dokumentace. Muze
 * obsahovat ukazkove HTML, URL adresy nebo jakekoliv jine informace co se
 * povazuji za nezbytne nebo uzitecne.
 *
 * @tag Tohle je znacka s nazvem „tag”
 *
 * @todo Tohle je popis ukolu (todo) co ma byt vyresen pozdeji.
 *   Zalomi se po 80ti znacich. Druhy a dalsi radky odsazujeme 2 mezerami.
 */

/* Jednoduchy komentar */
```

_(Pozn. překl. – Komentáře v kódu je lepší jednotně psát bez diakritiky. Hlavně
proto, že velká část českých vývojářů píše kód pomocí anglické klávesnice.)_


<a name="format"></a>
## 4. Formát

Zvolený formát musí zajistit aby číst kód a vytvářet v něm srozumitelné
komentáře bylo snadné. Omezte riziko náhodně vzniklých chyb. Výsledkem dobrého
a jednotného formátu je snadné porovnávání dvou verzí (_diff_) a čitelný
_blame_, jež ukazuje autora a commit poslední změny konkrétního řádku.

* V pravidlech obsahujících více selektorů mějte každý selektor na
  samostatné řádce.
* Před otevírací složenou závorku pravidla vkládejte jednu mezeru.
* V bloku deklarací mějte každou deklaraci na zvláštním řádku.
* Každou deklaraci odsazujte o jednu úroveň.
* V deklaraci pište za dvojtečku jednu mezeru.
* Ve zkrácených variantách hexa hodnot barev používejte malá písmena
  (např. `#aaa`).
* Konzistentně používejte jednoduché anebo dvojité „uvozovky”.
  Doporučujeme dvojité (např. `content: ""`).
* Hodnoty atribut selektorů uvádějte v  „uvozovkách” (např.
  `input[type="checkbox"]`).
* Tam kde je to u nulových hodnot možné, vyhněte se uvádění jednotek
  (např. `margin: 0`).
* Za každou čárku použitou jako oddělovač hodnot nebo parametrů funkcí
  vložte mezeru.
* Na konec každé deklarace v bloku deklarací vložte středník.
* Uzavírací složenou závorku pro konec pravidla odsaďte stejně jako první
  znak pravidla.
* Jednotlivá pravidla oddělujte prázdným řádkem.

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
```

#### Pořadí deklarací

Deklarace v kódu jednoho projektu řaďte v souladu s jediným principem.
Upřednostňuji deklarovat nejprve konstrukčně důležité vlastnosti (např.
pozicování nebo box model).

```css
.selector {
    /* Pozicovani */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Zobrazeni & box model */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Ostatni */
    background: #000;
    color: #fff
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

Poměrně populární je také abecední pořadí. To má ale nevýhodu, že odděluje
příbuzné vlastnosti. Například – ofsety pozice (vlastnosti `top`, `left` apod.)
tak nemohou být seskupeny dohromady a vlastnosti box-modelu mohou skončit
rozptýlené po celém pravidle.

_(Pozn. překl. — Některé vlastnosti jsou navíc pro rychlý sken stylopisu
důležitější než jiné – position, z-index. I proto jim patří místo na začátku
pravidla.)_

#### Výjimky a mírné odchylky

Velké bloky pravidel s jednou deklarací můžete zapisovat trochu jinak — na
jeden řádek. V tomto případě by za otevírací a před uzavírací složenou závorkou
neměla chybět mezera.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Dlouhé bloky hodnot oddělované čárkou – jako třeba vícenásobná pozadí nebo
stíny – je lepší pro zlepšení čitelnosti nebo zajištění užitečnějších diffů
rozdělit do více řádků. Formátů jež je možné použít je mnoho. Tady je jeden
příklad:

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

### Preprocesory

Různé CSS preprocesory mají různé vlastnosti, funkce a syntaxi. Vaše konvence
byste měli rozšířit tak, aby vyhověly zvláštnostem preprocesoru, který
využíváte. Následující zásady se vztahují k Sass.

* Omezte zanořování pravidel na 1 úroveň. Přehodnoťte každé zanořování
  hlubší než 2 úrovně. To omezí existenci příliš specifických selektorů.
* Vyhněte se velkému množství vnořených pravidel. Jakmile se čitelnost
  začíná zhoršovat, rozdělte je. Doporučuji rozdělovat vnořená pravidla
  jež zaberou více než 20 řádků.
* Direktivy `@extend` vždy zapisujte do prvních řádků pravidla.
* Tam kde je to možné seskupte direktivy `@include` hned za řádky s `@extend`.
* Zvažte prefixování vašich funkcí pomocí x- nebo jiného jmenného prostoru.
  To vám pomůže vyhnout se kolizím s názvy nativních CSS funkcí nebo funkcí
  z knihoven.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // ostatni deklarace
}
```


<a name="naming"></a>
## 5. Pojmenovávání

Pojmenovávání je těžké, ale velice důležité. Je to stěžejní část procesu vývoje
spravovatelného kódu. Dobrý způsob pojmenovávání vám zajistí škálovatelné
rozhraní mezi vaším HTML a CSS.

* Vyhněte se systematickému používání zkrácených názvů tříd. Nedělejte
  věci těžké k pochopení.
* Pro třídy v HTML používejte čisté, smysluplné a odpovídající názvy.
* Vyberte srozumitelný a konzistentní vzorec pojmenovávání co dává smysl jak
  v HTML tak CSS souborech.
* Selektory pro komponenty by měly využívat názvy tříd. Vyhněte se
  používání generických značek (tagů) nebo unikátních id.

```css
/* Ukazky kodu se spatnymi pojmenovavanim selektoru */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Ukazky kodu s lepsim pojmenovanim selektoru */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="example"></a>
## 6. Praktická ukázka

```css
/* ==========================================================================
   Mrizkovy layout
   ========================================================================== */

/**
 * Ukazka HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Zamezi zalomeni inline-block bunek mrizky */
    white-space: nowrap;
    /* Odstrani mezeru mezi bunkami */
    font-size: 0;
}

.cell {
    position: relative;
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 20%;
    height: 100%;
    /* Nastavime vnitrni okraj bunek */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Resetujeme bilou mezeru */
    white-space: normal;
    /* Resetujeme velikost pisma */
    font-size: 16px;
}

/* Stavy bunky */

.cell.is-animating {
    background-color: #fffdec;
}

/* Varianty sirky bunky
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Modifikatory bunky
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organization"></a>
## 7. Uspořádání

Uspořádání (organizace větších celků) je důležitá vlastnost každé CSS části
kódu projektu, ale pro ty větší je dost zásadní.

* Logicky oddělujte odlišné části kódu.
* Pro odlišné komponenty kódu používejte oddělené soubory, které pak spojte
  v sestavovacím (_build_) kroku.
* Pokud používáte preprocesor, zobecněte často používaný kód do proměnných
  pro barvy, typografii atd.


<a name="build-and-deployment"></a>
## 8. Build a deploy

Určitě byste se měli pokusit na projektu nasadit nějaké nástroje pomocí kterých
můžete kód projektu prověřit lint analýzou, zkomprimovat a verzovat během
přípravy pro produkční použití. Pro tenhle účel existuje vynikající nástroj
[grunt](https://github.com/cowboy/grunt) od Bena Almana.


<a name="acknowledgements"></a>
## Poděkování

Díky všem co přispěli k [idiomatic.js](https://github.com/rwldrn/idiomatic.js).
Byl to můj zdroj inspirace, citací a zásad.

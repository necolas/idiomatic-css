# Principi pisanja konzistentnog, itiomatskog CSS-a

Sledeći dokument ocrtava razumne stilove za CSS razvoj. Nije namenjen da bude
perskriptivan i ja ne želim da namećem svoje preferencije stilova na kod drugih
ljudi. Međutim, ove smernice snažno ohrabruju korišćenje postojećih,
zajedničkih, razumnih šema.

Ovo je "živi" dokument i nove ideje su uvek dobrodošle. Molimo Vas da
doprinesete.


## Prevodi

* [Engleski](https://github.com/necolas/idiomatic-css)
* [Portuguese](https://github.com/necolas/idiomatic-css/tree/master/translations/pt-BR)
* [Italijanski](https://github.com/necolas/idiomatic-css/tree/master/translations/it-IT)
* [Spanish](https://github.com/necolas/idiomatic-css/tree/master/translations/es-ES)


## Sadržaj

1. [Generalni principi](#general-principles)
2. [Znaci za razmake](#whitespace)
3. [Komentari](#comments)
4. [Formatiranje](#format)
5. [Imenovanje](#naming)
6. [Praktični primeri](#example)
7. [Organizovanje](#organization)
8. [Izrada i razvoj](#build-and-deployment)

[Priznanja](#acknowledgements)


<a name="general-principles"></a>
## 1. Generalni principi

> "Deo zaduženja dobrog stjuarda za uspešan projekat je shvatanje da pisanje
> koda za samog sebe je loša ideja™. Ako hiljade ljudi koristi tvoj kod, onda
> piši tvj kod sa maksimalnom jasnoćom, a ne sa svojim personalnim
> preferencijama o tome kako da se napraviš pametan u okviru specifikacije." -
> Idan Gazit

* Sav kod u bilo kom projektu bi trebao da izgleda kao da ga je pisala jedna
  osoba, bez obzira koliko je ljudi doprinelo razvoju projekta.
* Striktrno primenjujte dogovoreni stil.
* Strictly enforce the agreed upon style.
* Ako ste u sumnji, koristite postojeće, zajedničke šablone.


<a name="whitespace"></a>
## 2. Znaci za razmake

Samo jedan stil bi trebao da postojiu celom vašem projektu. Uvek budite
konzistentni u upotrebi razmaka. Koristite razmake da poboljšate čitljivost.

* _Nikada_ nemojte mešati space karakter i tab za indentaciju.
* Izaberite između mekih indentacija(space karakteri) i pravih tabova. Držite se
vašeg izbora bez obzira na sve. (Preferencija: space karakteri)
* Ako koristite space karaktere, izaberite broj karaktera za indetacioni nivo.
(Preferencija: 4 space karaktera)

Savet: konfigurišite vaš editor da prikazuje "nevidljive karaktere". Ovo će vam
omogućiti da eliminišete prazne karaktere na kraju linije, da eliminišete space
karaktere praznim linijama i da izbegnete "zagađivanje" komitova.


<a name="comments"></a>
## 3. Komentari

Dobro komentarisan kod je ekstremno bitan. Uzmite vremena da opišete komponente,
kako rade, njihove limite, i način na koji su konstruisani. Nemojte ostavljati
drugim članovima tima da nagađaju svrhu neuobičajenih i ne očiglednih delova
koda.

Stil komentara treba da bude jednostavan i konzistentan u celom projektu.

* Postavljajte komentare na novu liniju iznad dela koda koji hoćete da
iskomentarišete.
* Izbegavajte kometare na kraju linije koda.
* Držite dužinu linije na razumnom maksimumu, npr 80 kolona.
* Slobodno koristite komentare da "razbijete" CSS kod na diskretne sekcije.
* Koristite kometare dužine jedne rečenice i konzistentno indentovanje teksta.


Savet: konfigurišite vaš editor da vam omogući prečice za ispisivanje unapred
dogovorenog šablona za komentare.

#### CSS primer:

```css
/* ==========================================================================
   Blok komentar za odeljak
   ========================================================================== */

/* Blok komentar za pododeljak
   ========================================================================== */

/*
 * Blok komentar za grupu.
 * Idealan za objašnjavanja koja se protežu u više redova i dokumentaciju.
 */

/* Običan komentar */
```

#### SCSS primer:

```scss
// ==========================================================================
// Blok komentar za odeljak
// ==========================================================================

// Blok komentar za pododeljak
// ==========================================================================

//
// Blok komentar za grupu.
// Idealan za objašnjavanja koja se protežu u više redova i dokumentaciju.
//

// Običan komentar
```


<a name="format"></a>
## 4. Formatiranje

Izabrani tip formatiranja koda mora da obezbedi da je kod: lak za čitanje; lak
da se jasno komentariše; minimizuje šanse da se slučajno uvedu greške; i
rezultira korisnim `diff` i `blame` komandama u vašem sistemu za kontrolu
verzija.

1. Jedan selktor na jednu liniju kada koristite više selektora u jednom setu
   pravila.
2. Jedan space karakter pre otvarajuće zagrade za set pravila.
3. Jedna deklaracija na jednu liniju unutar seta pravila.
4. Jedan nivo indentacije za svaku deklaraciju.
5. Jedan space karakter nakon dve tačke u deklaraciju.
6. Uvek stavite tačku-zarez na kraju poslednje deklaracije u deklarativnom
   bloku.
7. Stavite zatvarajuću zagradu seta pravila u istu kolonu gde se nalazi prvi
   karakter selektora tog seta pravila.
8. Razdvojite svaki set pravila praznom linijom.

```css
.selektor-1,
.selektor-2,
.selektor-3 {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
    display: block;
    color: #333;
    background: #fff;
}
```

#### Redosled deklaracija

Deklaracije bi trebale biti poređane u skladu sa jednim principom. Moje
preferencije su da slična svojstva budu grupisana zajedno i da strukturno bitne
svojstva (npr pozicioniranje i box-model) budu deklarisana pre svojstava
za tipografiju, pozadine i boje.

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

Alfabetni redosled je isto popularan, ali mana mu je da razdvaja slična
svojstva. Na primer, svojstva za pomeranja pozicija više nisu grupisana zajedno
i box-model svojstva mogu da završe raširena kroz ceo deklarativni blok.

#### Izuzeci i mala odstupanja

Veliki blokovi gde se nalaze deklaracije u samo jednoj liniji mogu koristiti
malo izmenjen format na jednoj liniji. U ovom slučaju space karakter se
postavlja posle otvarajuće i pre zatvarajuće zagrade.

```css
.selektor-1 { width: 10%; }
.selektor-2 { width: 20%; }
.selektor-3 { width: 30%; }
```

Dugačka svojstva koja su razdvojena zarezon, kao što su na primer kolekcija
gradijenta ili senka, mogu biti raspoređena preko više linija sve sa ciljem
poboljšanja čitljivosti, a takođe da može da proizvede bolji `diff`. Postoje
razni formati koji bi mogli biti korišćeni, jedan primer je prikazan ispod.

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

#### Razno

* Koristite heksadecimalne vrednosti sa malim slovim, npr `#aaa`.
* Koristite jedan ili dupli apostrof konzistentno. Preferencija je da se
  koriste dupli apostrofi, npr `content: ""`.
* Vrednosti atributa u selektorima uvek stavljajte između apostrofa, npr
  `input[type="checkout"]`.
* _Gde je moguće_ izbegavajte specifiranje jedinica za nula vrednosti, npr
  `margin: 0`.

### Preprocesori: dodatna razmatranja za formatiranje

Različiti CSS preprocesori imaju drugačije karakteristika, funkcionalnosti i
sintaksu. Vaše konvencije bi trebale biti proširene da prime specifičnosti
preprocesora u upotrebi. Sledeće smernice su napomene za Sass.

* Limitirajte ugnežđenja na 1 nivo dubine. Preispitajte sva gneždenja koja su
  dublja od 2 nivoa. Ovo sprečava previše specifične CSS selektore.
* Izbegavajte preveliki boj ugneždenih pravila.  Razbijte ih na manje delove
  kada to počne da utiče na čitljivost. Preferencije su da izbegavate gnežđenja
  koja se rasporostiru na više od 20 linija.
* Uvek postavite `@extend` izjave na prvu liniju deklarativnog bloka.
* Gde je moguće, grupišite `@include` izjave na vrhu deklarativnog bloka, nakon
  svih `@extend` izjava.
* Razmotrite upotrebu prefiksa kod custom funkcija sa `x-` ili drugim
  namespace-om. Ovo pomaže da se izbegne bilo kakav potencijal da se pobrkaju
  vaše funkcije sa nativnim CSS funkcijama, ili da dođe do "sukoba" sa
  funkcijama iz drugih biblioteka.

```scss
.selektor-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // druge deklaracije
}
```


<a name="naming"></a>
## 5. Imenovanje

Ti nisi ljudski kompajler/kompresor za kod, tako da ne pokušavaj da budeš to.

Koristi jasna i pažljivo izabrana imena za HTML klase. Izaberi razumljiva i
konzistentne šeme za imenovanje koja imaju smisla za korišćenje i u HTML
fajlovima i u CSS fajlovima.

```css
/* Primer koda sa lošim imenovanjem */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Primer koda sa boljim imenovanjem */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="practical-example"></a>
## 6. Praktični primeri

Primeri raznih konvecija.

```css
/* ==========================================================================
   Grid layout
   ========================================================================== */

/*
 * HTML example:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* Prevent inline-block cells wrapping */
    white-space: nowrap;
    /* Remove inter-cell whitespace */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Set the inter-cell spacing */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Reset white-space */
    white-space: normal;
    /* Reset font-size */
    font-size: 16px;
}

/* Cell states */

cell.is-animating {
    background-color: #fffdec;
}

/* Cell dimensions
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Cell modifiers
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organization"></a>
## 7. Organizacija

Organizacija koda je važan deo za svaki bazu CSS koda i krucijalan za velike
baze koda.

* Logična separacija posebnih delova koda.
* Koristite odvojene fajlove(spojene u delu izgradnje za produkciju) da vam
  pomogne da razbijete kod u više posebnih komponenti.
* Ako koristite preprocesor, abstraktujte uobičaje delove koda u promenjvie,
  npr boje, tipografiju, itd.


<a name="build-and-deployment"></a>
## 8. Izgradnja i razvoj

Projekti bi uvek trebalo da uključe neki generički način da se izvorni kod
"lintuje", testira i kompresuje u pripremi za upotrebu u produkciji. Za ovaj
zadatak, [grunt](https://github.com/cowboy/grunt) od strane Ben Alman-a je
odlična alatka.


## Priznanja

Hvala svima koji su doprineli
[idiomatic.js](https://github.com/rwldrn/idiomatic.js) projektu. Taj projekat
je bio izvor inspiracije, citata i smernica.

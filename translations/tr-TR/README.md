# Tutarlı, İdiomatic CSS yazma prensipleri

Aşağıdaki döküman CSS geliştirme konusunda makul bir stil rehberini içerir.
Kuralcı olması ve düşünülmedi ve kendi stil seçimlerini diğer kişilerin koduna
empose etmek istemiyorum. Ama bu yönergeler varolan yaygın ve mantıklı
kalıpların kullanımını teşvik etmektedir.

Bu yaşayan bir dökümandır ve yeni fikirler daima hoş karşılanacak. Lütfen
katkıda bulunun.

[İngilizce İdiomatik CSS (Orijinal)](https://github.com/necolas/idiomatic-css)


## İçindekiler

1. [Genel Prensipler](#general-principles)
2. [Beyaz Alanlar](#whitespace)
3. [Açıklamalar](#comments)
4. [Format](#format)
5. [İsimlendirme](#naming)
6. [Uygulanabilir Örnek](#example)
7. [Organizasyon](#organization)
8. [Yapı ve Dağıtma](#build-and-deployment)

[Acknowledgements](#acknowledgements)


<a name="general-principles"></a>
## 1. Genel Prensipler

> "Başarılı bir projenin iyi bir temsilci olmanın bir bölümü kendin için kod
> yazmanın kötü bir fikir olduğunun farkına varmaktır. Eğer binlerce insan
> senin kodunun kullanıyorlarsa, o zaman kodunu, şartnameler dahilinde nasıl
> akıllılık yapacağın kişisel seçimlere göre değil maksimum açıklık için yaz."
> - Idan Gazit

* Herhangi bir kod tababındaki tüm kod, kaç kişi katkıda bulunumuş olursa olsun
  sanki tek bir kişi tarafından yazılmış gibi görünmelidir.
* Strictly enforce the agreed upon style.
* Karar verilen stili katı bir şekilde uygula.
* Eğer şüphen varsa yaygın olarak kullanılan yönergeleri uygula.


<a name="whitespace"></a>
## 2. Beyaz Alanlar

Projenin tüm kaynağında sadece tek bir stil hüküm sürmelidir. Beyaz alan
kullanımında her zaman tutarlı ol. Beyaz alanları okunabilirliği artırmak için
kullan.

* _Asla_ girintiler için boşluk ve tabları karıştırma.
* Yumuşak girintiler (boşluklar) veya gerçek tablar arasında bir seçim yap.
  Seçimine sadık kal. (Tercih: boşluklar)
* Eğer boşluk kullanıyorsan girinti bölümü için kullanılan karakter saysını
  seç.  (Tercih: 4 boşluk)

İpucu: Editörünü "görünmezleri göster" şeklinde ayarla. Bu, satır sonu
boşluklarının ve kasıtsız boş satırların önüne geçmeni ve "commit"lerin
kirlenmemesini sağlayacaktır.


<a name="comments"></a>
## 3. Açıklamalar

İyi açıklanmış kod son derece önemlidir. Bileşenleri tanımlamak, nasıl
çalıştıklarını, sınırlamalarını ve nasıl yapıldıklarını açıklamakk için zaman
ayır. Takımdaki diğer kişileri yaygın veya açık olmayan kodu tahmin etmek
zorunda bırakma.

Açıklama stili basit ve tek bir kod tabanı içinde tutarlı olmalıdır.

* Açıklamaları iligili öznelerinin üzerinde yeni satıra koy.
* Satır sonu açıklamalarından kaçın.
* Satır uzunluğunu makul bir uzunlukta tut. Ör: 80 sütun.
* CSS kodu farklı aralıklarda kısımlara bölmek için açıklamaları özgürce
  kullan.
* Cümle yapısında açıklamalar yap ve tutarlı girintileme kullan.

İpucu: Editörünü karar vediğin açıklama bloklarının çıktısını verecek şekilde
ayarla.

#### CSS örneği:

```css
/* ==========================================================================
   Kısım açıklama bloğu
   ========================================================================== */

/* Alt-kısım açıklama bloğu
   ========================================================================== */

/*
 * Grup açıklama bloğu
 * Birden fazla satır açıklamalar ve dökümantasyon için ideal.
 */

/* Basit açıklama / yorum */
```

#### SCSS örneği:

```scss
// ==========================================================================
// Kısım açıklama bloğu
// ==========================================================================

// Alt-kısım açıklama bloğu
// ==========================================================================

//
// Grup açıklama bloğu
// Birden fazla satır açıklamalar ve dökümantasyon için ideal.
//

// Basit açıklama / yorum
```


<a name="format"></a>
## 4. Format (Biçem)

Seçilen kod formatı (biçemi) kodun; kolay okunabildiğinden, kolay açıklanabilir
(yorumlamanabilir) olduğundan, kazara hataların oluşmasını minimuma
indirdiğinden ve faydalı "diff" ve hatalar ürettiğinden emin olmalıdır.

1. Çoklu seçicilerin olduğu kural setlerinde her satırda tek bir seçici.
2. Kural setinin açış parantezi önünde tek bir boşluk.
3. Her deklarasyon bloğunda her satırda tek bir deklarasyon.
4. Her bir deklarasyon için bir girinti seviyesi.
5. Deklarasyondaki iki noktadan sonra tek bir boşluk.
6. Her deklarayon bloğundaki son deklarasyondan sonra mutlaka bir noktalı
   virgül kullan
7. Bir kural setinin sonundaki parantezi o kural setindeki ilk karakter ile
   aynı sütuna koy.
8. Her kural setini boş bir satır ile ayır.

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

#### Deklarasyon sırası

Deklarasyonlar tek bir prensibe göre sıralandırılmalıdırlar. Benim seçimim
ilişkili özellikleri beraber gruplamak ve yapısal önemi olan özellikleri (ör:
posizyonlama ve box-model) tipografik, arka plan ve renk özelliklerinden önce
yapmak şeklinde.

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

Alfabetik sıralama da oldukça popüler ama bunun kusuru ise ilişkili özellikleri
birbirinden ayırması. Örneğin posizyon offsetleri artık beraber gruplanmış
değil ce box-model özellikleri deklarasyon bloğu içinde yayılmış olacaklar.

#### İstisnalar ve ufak sapmalar

Tek deklarasyonlu büüyük bloklar biraz daha farklı tek-satır bir biçem
kullanabilirler. Bu açılış parantezinden sonra ve kapanış parantezinden önce
bir boşluk olmalıdır.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Virgülle ayrılmış uzun özellik değerleri - gradient ve gölgeler gibi -
okunabilirliği arttırmak ve daha faydalı "diff"ler yaratmak için birden fazla
satıra yayılabilirler. Bunun için kullanılabilecek çeşitli biçemler var. Bir
örnek aşağıda.

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

#### Diğer

* Hex değerlerinde küçük harf kullan, ör., `#aaa`.
* Tek veya çift tırnağı tutarlı kullanın. Tercih çift tırnaktan yana, ör.,
  `content: ""`.
* Seçicilerdeki özellik değerlerini her zaman tırnak içine alın, ör.,
  `input[type="checkbox"]`.
* _Mümkün olduğu durumlarda_, sıfır değerler için ünite kullanmayın, ör.,
  `margin: 0`.

### Preprocessors (Önderleyiciler) : dikkate alınacak ek formatlar (biçem)

Farklı CSS önderleyicileri farklı özelliklere, işlevselliğe ve sözdizimine
(syntax) sahipler.  Kurallarınız kullanılmakta olan önderleyecinin özellikleri
ile uyum sağlayacak şekilde olmalıdır.  Aşağıdaki yönergeler Sass'ı referans
alarak verilmiştir.

* Gömmeyi (nesting) sadece 1 bölüm olacak şekilde sınırla. İki seviyeden fazla
  olan bütün gömmeleri gözden geçir. Bu aşırı spesifik CSS seçicilerini
  engeller.
* Yüksek sayıdaki gömme kurallarını engellemeye çalış. Okunabilirlik
  etkilenmeye başladıkça bunları küçük parçalara böl. Tercih 20 satırı aşan
  gömmelerin önüne geçmek.
* `@extend` ifadelerini deklarasyon bloğunun ilk satırına koy.
* Mümkün oldukça `@include` ifadelerini deklarasyon bloğunun tepesine `@extend`
  ifadelerinden sonrasına koy.
* özel fonksiyonları `x-` veya başka bir isim alanı ile başlat. Bu özel
  fonsiyonların CSS fonksiyonları ile karşımasına veya başka kütüphaneler ile
  çakışmasına engel olur.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // other declarations
}
```


<a name="naming"></a>
## 5. İsimlendirme

Sen bir insan kod derleyicisi/sıkıştırıcı değilsin, dolayısı ile olmaya da
çalışma.

HTML sınıfları için açık ve iyi düşünülmüş isimler kullan. He HTML hem de CSS
dosyalarında anlamı olan tutarlı bir isimlendirme şekli seç.

```css
/* Kötü isim örnekleri kodu */

.s-scr {
    overflow: auto;
}

.cb {
    background: #000;
}

/* Daha iyi isimli örneklerin kodu */

.is-scrollable {
    overflow: auto;
}

.column-body {
    background: #000;
}
```


<a name="example"></a>
## 6. Uygulanabilir örnek

Çeşitli teammüllerin örnekleri.

```css
/* ==========================================================================
   Grid layout
   ========================================================================== */

/*
 * Örnek HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-5"></div>
 *     <div class="cell cell-5"></div>
 * </div>
 */

.grid {
    overflow: visible;
    height: 100%;
    /* inline-block hücrelerin fazla satıra yayılmasını engelle */
    white-space: nowrap;
    /* Hücre içindeki beyaz alanları kaldır */
    font-size: 0;
}

.cell {
    box-sizing: border-box;
    position: relative;
    overflow: hidden;
    width: 20%;
    height: 100%;
    /* Hücre arası boşluğu ayarla */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Beyaz alanları sıfırla */
    white-space: normal;
    /* Font büyüklüğünü sıfırla */
    font-size: 16px;
}

/* Hücre durumları */

.cell.is-animating {
    background-color: #fffdec;
}

/* Hücre boyutları
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Hücre değişiklikleri
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="organization"></a>
## 7. Organizasyon

Kod organizsayonu bütün CSS kod tabanları için önemlidir ve büyük kod tabanları
içinse kritik önem taşır.

* Kodun farklı bölümlerini mantıksal bir şekilde ayır.
* Farklı bileşenleri ayırmak için ayrı dosyalar (inşa sırasında birleştirilen)
  kullan.
* Eğer bir önderleyici kullanıyorsan, renk, tipografi gibi genel kodları
  değişkenlerle soyutla.


<a name="build-and-deployment"></a>
## 8. Yapı ve Dağıtma (Build and deployment)

Projeler, kaynağın bir şekilde lint edilebileceği, sıkıştırılabileceği, test
edilebileceği, ve üretim için sürümlendirilebileceği soysal (jenerik) bir
yöntem içermelidir. Bunun için Ben Alman'ın
[grunt](https://github.com/cowboy/grunt)'ı mükemmel bir araç.


<a name="acknowledgements"></a>
## Teşekkürler

İlham, alıntı ve kılavuz bir kaynak olan
[idiomatic.js](https://github.com/rwldrn/idiomatic.js)'ye katkıda bulunan
herkese teşekkürler.

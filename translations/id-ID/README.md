# Prinsip Penulisan CSS yang Konsisten, Idiomatic

Dokumen dibawah ini menjelaskan petunjuk umum dalam pengembangan CSS.  Petunjuk
ini sangat mengutamakan penggunaan pola umum yang ada.  Dan sebaiknya digunakan
dalam Penulisan CSS sesuai kebutuhan anda.

Dokumen ini sedang digunakan oleh banyak orang, dan sangat terbuka dengan saran
yang masuk. Silahkan berpartisipasi.


## Daftar Isi

1. [Prinsip Umum](#general-principles)
2. [Whitespace](#whitespace)
3. [Komentas](#comments)
4. [Format](#format)
5. [Contoh Penggunaan](#example)

[Lisensi](#license)

[Kontribusi & Saran](#contribute)


<a name="general-principles"></a>
## 1. Prinsip Umum

> "Salah satu bagian untuk menjadi staf yang baik dalam Proyek adalah memahami
> bahwa menulis kode untuk diri sendiri adalah hal yang buruk. Jika ribuan
> sedang menggunakan kode anda, maka tulislah kode anda dengan jelas dan
> objektif, jangan menggunakan cara pribadi dalam memahami kode." - Idan
> Gazit

* Jangan mencoba menjadi manusia Compiler.
* Semua kode harus tampak seperti ditulis oleh satu orang, walaupun ada banyak
  orang yang berpartisipasi.
* Melaksanakan pola yang disepakati dengan ketat.
* Jika ragu dengan pola tersebut, gunakan pola yang ada dan umum.


<a name="whitespace"></a>
## 2. Whitespace

Anda disarankan menggunakan satu pola dalam seluruh kode. Harap konsisten
dengan penggunaan whitespace pada kode. Gunakan Whitespace untuk memudahkan
pembacaan kode.

* _Hindari_ membaurkan Spasi dan Tab untuk indentasi.
* Pilih salah satu antara _Soft Indents_ (Spasi) atau Tab original. Yakinlah
  akan pilihan anda. (Disarankan: Spasi)
* Jika menggunakan Spasi, pilih jumlah karakter yang digunakan ditiap
  indentasi. (Disarankan: 4 Spasi)

Tip: Setting Editor anda untuk mengaktifkan "show invisibles". Hal ini
meperbolehkan anda menghapus whitespace yang tidak diinginkan.

Tip: Gunakan File [EditorConfig](http://editorconfig.org) (atau yang sejenis)
untuk membantu pengaturan Whitespace yang anda gunakan pada kode anda.


<a name="comments"></a>
## 3. Komentar

Kode yang dikomentari dengan baik sangatlah penting. Sisihkan waktu untuk
menjelaskan komponen, bagaimana mereka bekerja, dan cara penggunaannya. Jangan
membiarkan staf di Tim anda untuk menduga-duga atau menebak-nebak karena kode
yang kurang jelas.

Pola Komentar harus sederhana dan konsisten di setiap kode anda.

* Tempatkan Komentar di atas subjeknya.
* Tetapkan standar panjang karakter ditiap Komentar. Contoh: 80 Karakter
* Anda bebas untuk menentukan Komentar sebagai pemecah kode CSS menjadi
  beberapa bagian.
* Gunakan "Sentence Case" pada Komentar dan penggunaan indentasi yang konsisten

Tip: Buat snippet pada Editor anda sebagai shortcut untuk Komentar yang akan
anda gunakan.

Contoh:
```css
/* ==========================================================================
   Blok Bagian
   ========================================================================== */

/* Blok Sub-Bagian
   ========================================================================== */

/**
 * Deskripsi Singkat menggunakan format Komentar Doxygen-style
 *
 * Kalimat pertama dari Deskripsi Detail dimulai di sini dan berlanjut di baris
 * selanjutnya hingga sampai kepada kesimpulan pada akhir paragraf.
 *
 * Deskripsi Detail sangat ideal untuk Penjelasan yang lebih lengkap dan
 * sebagai Dokumentasi. Disini anda dapat memasukkan contoh HTML, URL, atau
 * informas-informasi lain yang berguna untuk penjelasan.
 *
 * @tag Tag ini dinamakan 'tag'
 *
 * @todo Ini adalah Statemen Todo yang mendeskripsikan tugas-tugas yang harus
 *   anda selesaikan di waktu yang akan datang. Bagian ini memilik panjang
 *   maksimal 80 karakter dan baris dibawahnya di indentasi menggunakan 2 spasi
 */

/* Komentar standar */
```


<a name="format"></a>
## 4. Format

Format kode yang anda gunakan harus memastikan bahwa kode tersebut: mudah
dibaca; mudah di-Komentari; meminimalkan kemungkinan kesalahan penggunaan;
dan menghasil _diff_ dan _blame_ yang berguna.

* Gunakan satu baris per selector, dalam deklarasi rule multi-selector.
* Masukkan satu Spasi sebelum Buka Kurung dalam deklarasi rule.
* Gunakan deklarasi per baris dalam blok deklarasi.
* Gunakan satu level indentasi di tiap blok deklarasi.
* Masukkan satu Spasi setelah tanda Titik Koma dalam deklarasi.
* Gunakan _lowercase_ untuk Short Nilai Hex. Contoh: `#aaa`.
* Gunakan salah satu dari tanda Kutip Satu atau Kutip Dua secara konsisten.
  Disarankan Tanda Kutip Dua. Contoh: `content: ""`.
* Gunakan tanda kutip pada Nilai dari Attribute Selector. Contoh:
  `input[type="checkbox"]`.
* _Jika Memungkinkan_ hindari memberi satuan unit pada Nilai Nol. Contoh:
  `margin: 0`.
* Masukkan satu Spasi setelah Koma dalam Comma-Separated properti atau nilai
  function.
* Tetap ikutkan Titik Koma setelah deklarasi properti akhir di dalam blok
  deklarasi.
* Tempatkan tanda Tutup Kurung `}` pada blok deklarasi sesuai dengan posisi
  kolom tanda Buka Kurung `{`.
* Pisahkan tiap blok deklarasi dengan Baris Kosong.

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

#### Urutan Deklarasi

Jika anda mengurutkan deklarasi properti, maka anda harus menggunakan aturan
sederhana. Saran saya anda harus mendahulukan properti yang lebih penting
seperti Positioning, Box Model.

```css
.selector {
    /* Positioning */
    position: absolute;
    z-index: 10;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;

    /* Display & Box Model */
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    width: 100px;
    height: 100px;
    padding: 10px;
    border: 10px solid #333;
    margin: 10px;

    /* Other */
    background: #000;
    color: #fff;
    font-family: sans-serif;
    font-size: 16px;
    text-align: right;
}
```

Pengurutan propery berdasarkan Huruf juga cukup populer, tetapi kekurangannya
adalah dia memisahkan properti yang berhubungan. Contoh properti pendukung
dari position tidak lagi dikelompokkan bersama-sama dan akan menyebar di
seluruh blok deklarasi.

#### Pengecualian

Blok panjang dari deklarasi tunggal dapat ditulis secara berbeda, format satu
baris. Dalam kasus ini, satu Spasi dimasukkan setelah tanda Buka Kurung `{` dan
sebelum tanda Tutup Kurung `}`.

```css
.selector-1 { width: 10%; }
.selector-2 { width: 20%; }
.selector-3 { width: 30%; }
```

Nilai yang cukup panjang, Comma-separated seperti Nilai font-family, gradient,
dan box shadow dapat ditulis dengan memisahkan per baris dengan tujuan
memudahkan cara pembacaan dan menghasilkan diff yang berkualitas. Banyak format
yang dapat digunakan, berikut adalah salah satu contoh.

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

### Preprocessor: Tambahan Pertimbangan Format

CSS Preprocessor Berbeda juga mempunyai fitur, fungsi, dan syntax yang berbeda.
Aturan pola kode anda harus memadai dan cocok di tiap CSS Preprocessor.
Petunjuk di bawah ini di adaptasi dari petunjuk SASS.

* Batasi sarang _(nesting)_ satu level lebih dalam. Deklarasi kan deklarasi
  blok yang melebihi dua level sarang. Hal ini mencegah selector menjadi
  terlalu spesifik.
* Hindari menggunakan deklarasi rule bersarang yang berlebihan. Pisahkan
  secepatnya ketika sudah mulai mengurangi tingkat kemudahan pembacaan kode.
  Saran, hindari menggunakan deklarasi rule bersarang jika rulenya melebihi dari
  20 baris.
* Selalu tempatkan statemen `@extend` pada baris pertama dari blok deklarasi.
* Jika memungkinkan, tempatkan `@include` statemen pada baris awal setelah
  `@extend` statemen.
* Pertimbangkan menggunakan prefix `x-` atau prefix lainnya jika menggunakan
  fungsi buatan. Hal ini membantu menghindari kebingungan menggunakan fungsi
  asli dari CSS atau konflik dengan fungsi dari librari yang anda gunakan.

```scss
.selector-1 {
    @extend .other-rule;
    @include clearfix();
    @include box-sizing(border-box);
    width: x-grid-unit(1);
    // other declarations
}
```


<a name="example"></a>
## 5. Contoh Penggunaan

Sebuah contoh dari aturan kode yang beragam.

```css
/* ==========================================================================
   Grid layout
   ========================================================================== */

/**
 * Column layout dengan horizontal scroll.
 *
 * Ini membuat satu baris full-height, non-wrap kolom yang bisa digunakan
 * horizontal dengan parent mereka.
 *
 * Contoh HTML:
 *
 * <div class="grid">
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 *     <div class="cell cell-3"></div>
 * </div>
 */

/**
 * Grid container
 * Harus diisi oleh `.cell`
 */

.grid {
    height: 100%;
    /* Hilangkan inter-cell whitespace */
    font-size: 0;
    /* Cegah wrapping inline-block */
    white-space: nowrap;
}

/**
 * Grid cells
 * Tidak ada spesifik width secara default. Extend dengan `.cell-n` class
 */

.cell {
    position: relative;
    display: inline-block;
    overflow: hidden;
    box-sizing: border-box;
    height: 100%;
    /* Set inter-cell spasi */
    padding: 0 10px;
    border: 2px solid #333;
    vertical-align: top;
    /* Reset white-space */
    white-space: normal;
    /* Reset font-size */
    font-size: 16px;
}

/* Cell states */

.cell.is-animating {
    background-color: #fffdec;
}

/* Dimensi Cell
   ========================================================================== */

.cell-1 { width: 10%; }
.cell-2 { width: 20%; }
.cell-3 { width: 30%; }
.cell-4 { width: 40%; }
.cell-5 { width: 50%; }

/* Cell Pengubah
   ========================================================================== */

.cell--detail,
.cell--important {
    border-width: 4px;
}
```


<a name="license"></a>
## Lisensi

_Principles of writing consistent, idiomatic CSS_ oleh Nicolas Gallagher
dirilis dengan lisensi [Creative Commons Attribution 3.0 Unported
License](http://creativecommons.org/licenses/by/3.0/). Lisensi ini berlaku
untuk semua dokumen dan terjemahan di repository.

Dibuat berdasarkan proyek di
[github.com/necolas/idiomatic-css](https://github.com/necolas/idiomatic-css).


<a name="contribute"></a>
## Kontribusi & Saran

Jika anda ingin berpartisipasi dalam Proyek Penerjemahan ini, silahkan fork
[Idiomatic](http://github.com/novrian/idiomatic_id-ID).

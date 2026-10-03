1. Struktur Semantik

Halaman utama dibuat menggunakan elemen HTML semantik agar struktur
halaman dapat dipahami dengan lebih jelas oleh pengguna maupun teknologi
bantu.

Struktur utama halaman terdiri dari beberapa elemen semantik, yaitu:

<header> untuk bagian kepala halaman dan navigasi utama.

<nav> untuk menu navigasi.

<main> untuk konten utama halaman.

<section> untuk mengelompokkan bagian-bagian konten berdasarkan
topik.

<article> untuk setiap kartu fitur.

<aside> untuk informasi tambahan.

<form> untuk formulir kontak.

<footer> untuk bagian akhir halaman.

Pada halaman utama juga digunakan hierarki heading yang berurutan. Judul
utama halaman menggunakan <h1>, sedangkan judul bagian menggunakan
<h2>, dan judul masing-masing fitur menggunakan <h3>. Struktur
tersebut membantu menunjukkan hubungan antara judul utama, bagian
halaman, dan isi di dalamnya.

Struktur heading pada halaman utama adalah:

H1
└── Kalimat nilai utama produk
    ├── H2 Fitur Utama
    │   ├── H3 Fitur pertama
    │   ├── H3 Fitur kedua
    │   └── H3 Fitur ketiga
    ├── H2 Cara Kerja
    ├── H2 Informasi Tambahan
    └── H2 Hubungi Kami

Selain struktur semantik, halaman juga memiliki tautan "Lewati ke
konten utama" yang mengarah ke elemen <main id="konten">. Tautan ini
membantu pengguna keyboard melewati navigasi dan langsung menuju konten
utama.

Pohon Aksesibilitas

Pemeriksaan struktur halaman dilakukan menggunakan Accessibility Tree
pada DevTools. Pemeriksaan ini digunakan untuk melihat bagaimana
elemen-elemen halaman dikenali oleh browser dan teknologi bantu.

Gambar 1. Pohon aksesibilitas halaman utama pada DevTools

2. Tata Letak Responsif

Halaman utama menggunakan Flexbox dan CSS Grid untuk mengatur
tata letak agar dapat menyesuaikan ukuran layar.

Pengujian tampilan dilakukan pada beberapa ukuran layar, yaitu 360 px,
768 px, dan 1280 px. Dokumentasi awal juga memuat tangkapan layar pada
lebar 360 px, 798 px, dan 1280 px.

2.1 Flexbox

Flexbox digunakan pada bagian navigasi. Kode yang digunakan adalah:

<nav
  aria-label="Navigasi utama"
  className="mx-auto flex max-w-6xl flex-col gap-3 p-4 sm:flex-row sm:items-center sm:justify-between"
>

Pada layar kecil, flex-col membuat nama produk dan menu navigasi
tersusun secara vertikal. Mulai breakpoint sm, digunakan sm:flex-row
sehingga elemen navigasi tersusun secara horizontal.

Menu navigasi juga menggunakan Flexbox:

<ul className="flex flex-col gap-2 sm:flex-row sm:gap-6">

Penggunaan Flexbox sesuai untuk navigasi karena elemen-elemen di
dalamnya perlu disusun dalam satu arah dan diberi jarak yang konsisten.

Gambar 2. Implementasi Flexbox pada navigasi halaman utama

2.2 Grid pada Fitur Utama

Bagian Fitur Utama menggunakan CSS Grid dengan kode:

<ul className="mt-6 grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3">

Kelas tersebut membuat jumlah kolom berubah sesuai ukuran layar:

Ukuran layar   Kelas                Jumlah kolom

< 640 px      grid-cols-1                   1
≥ 640 px       sm:grid-cols-2                2
≥ 1024 px      lg:grid-cols-3                3

Dengan demikian, pada layar mobile tiga fitur ditampilkan secara
vertikal. Pada layar yang lebih lebar, fitur berubah menjadi dua kolom
dan kemudian tiga kolom pada ukuran desktop.

Gambar 3. Implementasi Grid pada navigasi halaman utama

2.3 Grid pada Cara Kerja dan Informasi Tambahan

Bagian Cara Kerja dan Informasi Tambahan menggunakan:

<div className="grid gap-8 lg:grid-cols-[2fr_1fr]">

Sebelum breakpoint lg, kedua bagian tersusun dalam satu kolom. Mulai
ukuran 1024 px, layout berubah menjadi dua kolom dengan perbandingan:

Cara Kerja              Informasi Tambahan
    2fr                         1fr

Artinya, bagian Cara Kerja memperoleh ruang lebih besar dibandingkan
bagian Informasi Tambahan.

2.4 Breakpoint yang Digunakan

Breakpoint yang digunakan pada halaman adalah:

sm = 640 px, digunakan untuk mengubah navigasi menjadi
horizontal dan mengubah fitur menjadi dua kolom.

lg = 1024 px, digunakan untuk mengubah fitur menjadi tiga
kolom dan mengubah bagian Cara Kerja serta Informasi Tambahan
menjadi dua kolom.

Ringkasannya:

Lebar layar   Navigasi     Fitur Utama   Cara Kerja + Informasi

360 px        Vertikal     1 kolom       1 kolom
768 px        Horizontal   2 kolom       1 kolom
1280 px       Horizontal   3 kolom       2 kolom (2:1)

2.5 Dokumentasi Tampilan Responsif

Gambar 4. Tampilan halaman pada lebar 360 px

Gambar 5. Tampilan halaman pada lebar 768 px

Gambar 6. Tampilan halaman pada lebar 1280 px

3. Audit Aksesibilitas

Audit aksesibilitas dilakukan menggunakan Lighthouse dan pemeriksaan
manual dengan papan ketik.

3.1 Hasil Lighthouse

Berdasarkan dokumentasi yang tersedia, hasil Lighthouse pada halaman
yang diperiksa menunjukkan skor aksesibilitas 100. Skor tersebut
menunjukkan bahwa tidak terdapat kegagalan pada audit aksesibilitas yang
ditampilkan pada hasil pemeriksaan tersebut.

Halaman             Skor Sebelum Perbaikan   Skor Sesudah Perbaikan

Halaman Latihan             Belum tersedia           Belum tersedia
Halaman Utama               Belum tersedia                      100

Data skor sebelum perbaikan dan skor halaman latihan belum tercantum
pada dokumen yang tersedia, sehingga tidak diisi dengan angka yang
tidak terverifikasi.

Gambar 7. Skor Lighthouse

3.2 Daftar Audit yang Gagal

Pada hasil Lighthouse halaman utama yang terdokumentasi, skor
aksesibilitas adalah 100 sehingga tidak terdapat audit aksesibilitas
yang gagal pada hasil tersebut.

Audit yang gagal                           Penyebab   Perbaikan

Tidak ada pada hasil yang terdokumentasi   -         -

Jika terdapat hasil Lighthouse sebelum perbaikan, daftar audit yang
gagal dapat ditambahkan berdasarkan hasil tersebut.

3.3 Pemeriksaan Manual dengan Papan Ketik

Pemeriksaan manual dilakukan menggunakan papan ketik dengan tombol Tab
untuk melihat perpindahan fokus antar elemen interaktif.

Hal-hal yang diperiksa meliputi:

Urutan fokus mengikuti struktur halaman secara logis.

Elemen interaktif seperti tautan, input, dan tombol dapat dicapai
menggunakan keyboard.

Elemen yang sedang mendapatkan fokus memiliki indikator visual.

Pengguna dapat mencapai konten utama tanpa harus melewati seluruh
navigasi melalui penggunaan tautan "Lewati ke konten utama".

Pada kode halaman utama, indikator fokus pada input dan tombol
menggunakan:

focus-visible:outline-2
focus-visible:outline-offset-2
focus-visible:outline-blue-700

Hal ini memberikan garis fokus yang terlihat ketika elemen mendapatkan
fokus melalui keyboard.

Gambar 8. Hasil pemeriksaan manual menggunakan papan ketik

4. Kendala dan Penyelesaian

4.1 Penyesuaian Tampilan pada Berbagai Ukuran Layar

Salah satu hal yang perlu diperhatikan adalah perbedaan ukuran layar
perangkat. Jika seluruh elemen dibuat dalam satu susunan tetap, tampilan
dapat menjadi kurang sesuai pada layar yang lebih kecil.

Penyelesaian: digunakan CSS Grid dan Flexbox dengan breakpoint
Tailwind CSS. Fitur berubah dari satu kolom menjadi dua dan kemudian
tiga kolom, sedangkan navigasi berubah dari vertikal menjadi horizontal.

4.2 Struktur dan Navigasi Aksesibilitas

Pengguna keyboard perlu dapat berpindah ke elemen interaktif dan
mengetahui elemen yang sedang aktif.

Penyelesaian: halaman menggunakan elemen HTML semantik, tautan skip
navigation, serta indikator fokus menggunakan focus-visible.

4.3 Verifikasi Aksesibilitas

Pemeriksaan dengan kode saja belum cukup untuk memastikan halaman dapat
digunakan dengan baik oleh pengguna.

Penyelesaian: dilakukan pemeriksaan menggunakan Accessibility Tree
pada DevTools, Lighthouse, dan navigasi manual menggunakan papan ketik.

5. Catatan Pemanfaatan AI

AI digunakan sebagai alat bantu dalam penyusunan dan perapihan
dokumentasi teknis.

Alat              Perintah Utama    Bagian yang       Cara Verifikasi
Digunakan

ChatGPT           Membantu          Penyusunan        Hasil AI
menjelaskan       dokumentasi       dibandingkan
struktur          teknis dan        kembali dengan
semantik,         penjelasan        kode page.tsx,
Flexbox, Grid,    implementasi      screenshot
breakpoint, dan                     tampilan, hasil
audit                               DevTools,
aksesibilitas                       Lighthouse, dan
berdasarkan kode                    pemeriksaan
page.tsx serta                    keyboard
hasil pengujian

AI tidak digunakan sebagai pengganti pengujian. Informasi mengenai
breakpoint, kelas Flexbox, kelas Grid, dan struktur semantik
diverifikasi berdasarkan kode page.tsx. Hasil audit aksesibilitas
diverifikasi menggunakan Lighthouse dan pemeriksaan manual.
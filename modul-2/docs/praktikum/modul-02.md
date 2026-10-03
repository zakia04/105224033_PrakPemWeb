# Implementasi Struktur Semantik, Tata Letak Responsif, dan Audit Aksesibilitas

**Nama/NIM:** Zakiati Latifa / 105224033  
**Repository:** https://github.com/zakia04/105224033_PrakPemWeb/tree/main/modul-2

---

# 1. Struktur Semantik

Halaman utama dibuat menggunakan elemen HTML semantik agar struktur halaman dapat dipahami dengan lebih jelas oleh pengguna maupun teknologi bantu.

Struktur utama halaman terdiri dari beberapa elemen semantik, yaitu:

- `<header>` untuk bagian kepala halaman dan navigasi utama.
- `<nav>` untuk menu navigasi.
- `<main>` untuk konten utama halaman.
- `<section>` untuk mengelompokkan bagian-bagian konten berdasarkan topik.
- `<article>` untuk setiap kartu fitur.
- `<aside>` untuk informasi tambahan.
- `<form>` untuk formulir kontak.
- `<footer>` untuk bagian akhir halaman.

Pada halaman utama juga digunakan hierarki heading yang berurutan. Judul utama halaman menggunakan `<h1>`, sedangkan judul bagian menggunakan `<h2>`, dan judul masing-masing fitur menggunakan `<h3>`. Struktur tersebut membantu menunjukkan hubungan antara judul utama, bagian halaman, dan isi di dalamnya.

## 1.1 Struktur Heading

Struktur heading pada halaman utama adalah:

```text
H1
└── Kalimat nilai utama produk
    ├── H2 Fitur Utama
    │   ├── H3 Fitur pertama
    │   ├── H3 Fitur kedua
    │   └── H3 Fitur ketiga
    ├── H2 Cara Kerja
    ├── H2 Informasi Tambahan
    └── H2 Hubungi Kami
```

Selain struktur semantik, halaman juga memiliki tautan **"Lewati ke konten utama"** yang mengarah ke elemen `<main id="konten">`.

Tautan tersebut membantu pengguna yang menggunakan keyboard untuk melewati bagian navigasi dan langsung menuju konten utama halaman.

## 1.2 Pohon Aksesibilitas

Pemeriksaan struktur halaman dilakukan menggunakan **Accessibility Tree** pada DevTools. Pemeriksaan ini digunakan untuk melihat bagaimana elemen-elemen halaman dikenali oleh browser dan teknologi bantu.

**Gambar 1. Pohon aksesibilitas halaman utama pada DevTools**

![Pohon Aksesibilitas](./images/accessibility-tree.png)

---

# 2. Tata Letak Responsif

Halaman utama menggunakan **Flexbox** dan **CSS Grid** untuk mengatur tata letak agar dapat menyesuaikan ukuran layar.

Pengujian tampilan dilakukan pada tiga ukuran layar, yaitu:

- 360 px
- 768 px
- 1280 px

Penggunaan Flexbox dan Grid membuat tampilan halaman dapat menyesuaikan susunan elemen berdasarkan ukuran layar.

## 2.1 Flexbox

Flexbox digunakan pada bagian navigasi halaman. Kode yang digunakan adalah:

```tsx
<nav
  aria-label="Navigasi utama"
  className="mx-auto flex max-w-6xl flex-col gap-3 p-4 sm:flex-row sm:items-center sm:justify-between"
>
```

Pada layar kecil, kelas `flex-col` membuat nama produk dan menu navigasi tersusun secara vertikal.

Mulai breakpoint `sm`, digunakan kelas `sm:flex-row` sehingga elemen navigasi berubah menjadi susunan horizontal.

Menu navigasi juga menggunakan Flexbox:

```tsx
<ul className="flex flex-col gap-2 sm:flex-row sm:gap-6">
```

Pada layar kecil, menu menggunakan `flex-col`, sedangkan mulai breakpoint `sm`, menu berubah menjadi horizontal menggunakan `sm:flex-row`.

Penggunaan Flexbox sesuai untuk bagian navigasi karena elemen-elemen di dalamnya perlu disusun dalam satu arah dan diberi jarak yang konsisten.

**Gambar 2. Implementasi Flexbox pada navigasi halaman utama**

![Implementasi Flexbox](./images/flexbox.png)

---

## 2.2 Grid pada Fitur Utama

Bagian **Fitur Utama** menggunakan CSS Grid dengan kode:

```tsx
<ul className="mt-6 grid grid-cols-1 gap-6 sm:grid-cols-2 lg:grid-cols-3">
```

Kelas tersebut membuat jumlah kolom berubah sesuai dengan ukuran layar.

| Ukuran Layar | Kelas Tailwind | Jumlah Kolom |
|---|---|---:|
| < 640 px | `grid-cols-1` | 1 |
| ≥ 640 px | `sm:grid-cols-2` | 2 |
| ≥ 1024 px | `lg:grid-cols-3` | 3 |

Dengan konfigurasi tersebut, pada layar mobile tiga fitur ditampilkan secara vertikal dalam satu kolom.

Pada layar yang lebih lebar, fitur berubah menjadi dua kolom, kemudian menjadi tiga kolom pada ukuran desktop.


**Gambar 3. Implementasi Grid pada bagian Fitur Utama**

![Implementasi Grid](./images/grid.png)

---

## 2.3 Grid pada Cara Kerja dan Informasi Tambahan

Bagian **Cara Kerja** dan **Informasi Tambahan** menggunakan CSS Grid dengan kode:

```tsx
<div className="grid gap-8 lg:grid-cols-[2fr_1fr]">
```

Sebelum breakpoint `lg`, kedua bagian tersusun dalam satu kolom.

Mulai ukuran 1024 px, layout berubah menjadi dua kolom dengan perbandingan:

```text
Cara Kerja              Informasi Tambahan
    2fr                         1fr
```

Artinya, bagian **Cara Kerja** memperoleh ruang yang lebih besar dibandingkan bagian **Informasi Tambahan**.

---

## 2.4 Breakpoint yang Digunakan

Breakpoint yang digunakan pada halaman adalah:

### `sm = 640 px`

Breakpoint `sm` digunakan untuk:

- Mengubah navigasi dari vertikal menjadi horizontal.
- Mengubah Fitur Utama dari satu kolom menjadi dua kolom.

### `lg = 1024 px`

Breakpoint `lg` digunakan untuk:

- Mengubah Fitur Utama menjadi tiga kolom.
- Mengubah bagian Cara Kerja dan Informasi Tambahan menjadi dua kolom dengan perbandingan `2fr 1fr`.

Ringkasan responsivitas halaman dapat dilihat pada tabel berikut:

| Lebar Layar | Navigasi | Fitur Utama | Cara Kerja + Informasi |
|---|---|---|---|
| 360 px | Vertikal | 1 kolom | 1 kolom |
| 768 px | Horizontal | 2 kolom | 1 kolom |
| 1280 px | Horizontal | 3 kolom | 2 kolom (2:1) |

---

## 2.5 Dokumentasi Tampilan Responsif

**Gambar 4. Tampilan halaman pada lebar 360 px**

![Tampilan 360 px](./images/responsive-360.png)

Pada lebar 360 px, navigasi masih tersusun secara vertikal. Bagian Fitur Utama juga ditampilkan dalam satu kolom sehingga setiap fitur tersusun dari atas ke bawah.

**Gambar 5. Tampilan halaman pada lebar 768 px**

![Tampilan 768 px](./images/responsive-768.png)

Pada lebar 768 px, navigasi berubah menjadi horizontal. Bagian Fitur Utama menggunakan dua kolom karena sudah melewati breakpoint `sm`, sedangkan bagian Cara Kerja dan Informasi Tambahan masih tersusun dalam satu kolom karena belum mencapai breakpoint `lg`.

**Gambar 6. Tampilan halaman pada lebar 1280 px**

![Tampilan 1280 px](./images/responsive-1280.png)

Pada lebar 1280 px, navigasi tetap tersusun secara horizontal. Bagian Fitur Utama menggunakan tiga kolom, sedangkan bagian Cara Kerja dan Informasi Tambahan menggunakan dua kolom dengan perbandingan `2fr 1fr`.

---

# 3. Audit Aksesibilitas

Audit aksesibilitas dilakukan menggunakan **Lighthouse** dan pemeriksaan manual dengan papan ketik.

Pemeriksaan dilakukan untuk memastikan halaman dapat digunakan dengan baik oleh pengguna, termasuk pengguna yang mengandalkan keyboard dan teknologi bantu.

## 3.1 Hasil Lighthouse

Berdasarkan hasil pengujian yang tersedia, halaman utama memperoleh skor aksesibilitas **100** pada Lighthouse.

Hasil tersebut menunjukkan bahwa pada pemeriksaan Lighthouse yang dilakukan, tidak terdapat audit aksesibilitas yang gagal pada halaman utama.

| Halaman | Skor Sebelum Perbaikan | Skor Sesudah Perbaikan |
|---|---:|---:|
| Halaman Latihan | Belum tersedia | Belum tersedia |
| Halaman Utama | Belum tersedia | 100 |

Data skor sebelum perbaikan dan skor halaman latihan belum tersedia dalam dokumentasi pengujian. Oleh karena itu, angka yang belum terverifikasi tidak dicantumkan.

**Gambar 7. Skor Lighthouse**

![Hasil Lighthouse](./images/lighthouse.png)

---

## 3.2 Daftar Audit yang Gagal

Pada hasil Lighthouse halaman utama yang terdokumentasi, skor aksesibilitas adalah **100**.

Berdasarkan hasil tersebut, tidak terdapat audit aksesibilitas yang gagal pada pemeriksaan halaman utama.

| Audit yang Gagal | Penyebab | Perbaikan |
|---|---|---|
| Tidak ada pada hasil yang terdokumentasi | - | - |

Jika terdapat hasil Lighthouse sebelum perbaikan, daftar audit yang gagal dapat ditambahkan berdasarkan hasil pengujian tersebut.

---

## 3.3 Pemeriksaan Manual dengan Papan Ketik

Pemeriksaan manual dilakukan menggunakan papan ketik dengan tombol **Tab** untuk melihat perpindahan fokus antar elemen interaktif.

Hal-hal yang diperiksa meliputi:

1. Urutan fokus mengikuti struktur halaman secara logis.
2. Elemen interaktif seperti tautan, input, dan tombol dapat dicapai menggunakan keyboard.
3. Elemen yang sedang mendapatkan fokus memiliki indikator visual.
4. Pengguna dapat mencapai konten utama tanpa harus melewati seluruh navigasi melalui penggunaan tautan **"Lewati ke konten utama"**.

Pada kode halaman utama, indikator fokus pada input dan tombol menggunakan kelas:

```text
focus-visible:outline-2
focus-visible:outline-offset-2
focus-visible:outline-blue-700
```

Kelas tersebut memberikan garis fokus yang terlihat ketika elemen mendapatkan fokus melalui keyboard.

Selain itu, halaman menyediakan skip link:

```tsx
<a
  href="#konten"
  className="sr-only focus:not-sr-only focus:p-2"
>
  Lewati ke konten utama
</a>
```

Skip link tersebut memungkinkan pengguna keyboard untuk langsung menuju elemen `<main id="konten">`.

### Urutan Fokus

Secara umum, urutan fokus mengikuti urutan elemen interaktif pada halaman, yaitu:

```text
Lewati ke konten utama
        ↓
NamaProduk
        ↓
Fitur
        ↓
Kontak
        ↓
Nama lengkap
        ↓
Surel
        ↓
Pengguna
        ↓
Mitra
        ↓
Pesan
        ↓
Kirim
```

**Gambar 8. Hasil pemeriksaan manual menggunakan papan ketik**

![Pemeriksaan Keyboard](./images/keyboard-focus.png)

---

# 4. Kendala dan Penyelesaian

## 4.1 Penyesuaian Tampilan pada Berbagai Ukuran Layar

Salah satu kendala yang perlu diperhatikan adalah perbedaan ukuran layar perangkat. Jika seluruh elemen dibuat dalam satu susunan tetap, tampilan dapat menjadi kurang sesuai pada layar yang lebih kecil.

### Penyelesaian

Digunakan CSS Grid dan Flexbox dengan breakpoint Tailwind CSS.

Pada bagian Fitur Utama, layout berubah dari:

```text
1 kolom
   ↓
2 kolom
   ↓
3 kolom
```

Sedangkan pada bagian navigasi, layout berubah dari:

```text
Vertikal
   ↓
Horizontal
```

Perubahan tersebut dilakukan menggunakan breakpoint `sm` dan `lg`.

---

## 4.2 Struktur dan Navigasi Aksesibilitas

Pengguna keyboard perlu dapat berpindah ke elemen interaktif dan mengetahui elemen yang sedang aktif.

### Penyelesaian

Halaman menggunakan:

- Elemen HTML semantik.
- Hierarki heading yang terstruktur.
- Skip link untuk melewati navigasi.
- Label pada input menggunakan `<label>`.
- `fieldset` dan `legend` untuk mengelompokkan pilihan peran.
- Indikator fokus menggunakan `focus-visible`.

Penggunaan elemen tersebut membantu meningkatkan struktur dan navigasi halaman bagi pengguna.

---

## 4.3 Verifikasi Aksesibilitas

Pemeriksaan menggunakan kode saja belum cukup untuk memastikan halaman dapat digunakan dengan baik oleh pengguna.

### Penyelesaian

Verifikasi dilakukan melalui beberapa metode:

1. **Accessibility Tree pada DevTools** untuk melihat bagaimana struktur halaman dikenali oleh browser.
2. **Lighthouse** untuk melakukan audit aksesibilitas otomatis.
3. **Pemeriksaan keyboard** untuk memastikan elemen interaktif dapat dicapai menggunakan tombol `Tab`.
4. **Pemeriksaan indikator fokus** untuk memastikan elemen yang aktif dapat terlihat oleh pengguna.

---

# 5. Catatan Pemanfaatan AI

AI digunakan sebagai alat bantu dalam penyusunan dan perapihan dokumentasi teknis.

| Alat | Perintah Utama | Bagian yang Digunakan | Cara Verifikasi |
|---|---|---|---|
| ChatGPT | Membantu menjelaskan struktur semantik, Flexbox, Grid, breakpoint, dan audit aksesibilitas berdasarkan kode `page.tsx` serta hasil pengujian. | Penyusunan dokumentasi teknis dan penjelasan implementasi. | Hasil AI dibandingkan kembali dengan kode `page.tsx`, screenshot tampilan, hasil DevTools, Lighthouse, dan pemeriksaan keyboard. |

AI tidak digunakan sebagai pengganti pengujian.

Informasi mengenai breakpoint, kelas Flexbox, kelas Grid, dan struktur semantik diverifikasi berdasarkan kode `page.tsx`.

Hasil audit aksesibilitas diverifikasi menggunakan Lighthouse dan pemeriksaan manual dengan papan ketik.

Dengan demikian, dokumentasi disusun berdasarkan implementasi kode dan hasil pengujian yang dilakukan pada halaman utama.


# Panduan & Naskah Video Presentasi Proyek BangunSewa
### Website Promosi dan Katalog Sewa Alat Bangunan

Dokumen ini menjadi panduan perekaman dan naskah presentasi proyek **BangunSewa**. Pembagian materi mengikuti susunan pekan yang diminta: **Anggota 1 — Frontend & DOM Engineer (Pekan 2–3)**, **Anggota 2 — API & Core PHP Engineer (Pekan 4–5)**, dan **Anggota 3 — Lead Architect, OOP & MVC (Pekan 6–7)**. Penjelasan dan demonstrasi di bawah menggunakan berkas yang benar-benar tersedia di proyek.

> **Catatan sebelum merekam:** Nama anggota, NIM, tautan repositori, dan ketentuan pengumpulan perlu disesuaikan dengan kelompok. Pembagian tiga anggota di bawah adalah usulan agar topik tidak tumpang tindih. Tunjukkan hasil dari kode yang benar-benar tersedia; jangan menyebut formulir sebagai transaksi yang tersimpan.

---

## 1. Tujuan dan Batas Demo

| Topik | Yang ditunjukkan dalam video |
| :--- | :--- |
| **Proyek** | Website informasi dan katalog penyewaan alat bangunan. |
| **Perkembangan antarmuka** | Perbandingan halaman pada folder `Pertama`, `Kedua`, dan `Ketiga`. |
| **Pemuatan data** | `TailWind/Tailwind.html` mengambil enam data alat dari `TailWind/tools.json` melalui Fetch API. |
| **PHP MVC** | `TailWind/index.php` meneruskan permintaan ke Controller, Model menyediakan data, dan View merender katalog. |
| **Batasan fitur** | Data masih berupa contoh di kode/JSON. Formulir demo HTML menampilkan konfirmasi di browser; belum menyimpan permintaan atau mengirimkannya ke backend. |

### Persiapan teknis

- Pastikan PHP tersedia dengan menjalankan `php -v`.
- Jalankan halaman HTML dan Fetch melalui VS Code Live Server dari root proyek. Halaman Tailwind dibuka di:
  `http://127.0.0.1:5500/TailWind/Tailwind.html`
- Untuk demo PHP MVC, buka terminal pada folder `TailWind` dan jalankan server PHP:
  ```bash
  php -S 127.0.0.1:8000
  ```
- Jangan membuka halaman Fetch dengan `file://`; akses melalui Live Server agar `fetch('./tools.json')` dapat membaca JSON.
- Ganti `<URL-REPOSITORI>` dan `<folder-repo>` dengan alamat repositori serta nama folder yang benar jika melakukan demonstrasi clone.

---

## 2. Alur Video dan Pembagian Peran

### 2.1 Alur presentasi

```mermaid
flowchart LR
    A["01. Pembukaan & setup"] --> B["02. HTML dan CSS"]
    B --> C["03. API & Core PHP"]
    C --> D["04. OOP & MVC"]
    D --> E["05. Kesimpulan"]
```

### 2.2 Matriks pembagian yang disarankan

| Anggota | Peran | Cakupan | Berkas utama | Demo |
| :--- | :--- | :--- | :--- | :--- |
| **Anggota 1** | **Frontend & DOM Engineer** | **Pekan 2–3:** HTML semantik, CSS responsif, pemilihan elemen DOM, dan event navigasi | `Pertama/Index.html`, `Kedua/Index.html`, `Kedua/style.css`, `Ketiga/Style.css`, `TailWind/Tailwind.html` | Bandingkan halaman dan layout mobile; demonstrasikan menu hamburger serta navigasi. |
| **Anggota 2** | **API & Core PHP Engineer** | **Pekan 4–5:** pengambilan data JSON dengan Fetch API, status API, serta pemrosesan data PHP | `TailWind/Tailwind.html`, `TailWind/tools.json`, `TailWind/Controller/PeralatanController.php`, `TailWind/Model/PeralatanModel.php` | Tunjukkan Fetch dan state di browser, lalu data array dan proses `foreach` PHP. |
| **Anggota 3 (Lead)** | **Lead Architect, OOP & MVC** | **Pekan 6–7:** desain class OOP dan integrasi Model-Controller-View | `TailWind/Model/PeralatanModel.php`, `TailWind/index.php`, `TailWind/Controller/PeralatanController.php`, `TailWind/View/katalog_view.php` | Jelaskan class dan enkapsulasi, lalu jalankan alur MVC dan tampilkan katalog. |

Sesuaikan matriks ini dengan kontribusi yang benar-benar dikerjakan setiap anggota. Jika proyek dikerjakan sendiri atau jumlah anggota berbeda, ubah jumlah pembicara dan pembagian materinya.

**Panduan membaca naskah:** Label **Dibacakan Anggota 1/2/3** menunjukkan siapa yang berbicara. Aksi layar dilakukan oleh pembicara yang sedang mendapat giliran, kecuali kelompok memilih operator layar tersendiri.

### 2.3 Peta kode yang harus dibuka saat presentasi

Nomor berikut adalah nomor baris pada berkas proyek saat panduan ini disusun. Jika kode berubah, cari nama fungsi/elemen yang disebutkan karena nomor baris bisa bergeser.

#### Anggota 1 — Frontend & DOM Engineer (Pekan 2 dan 3)

- **Pekan 2 — `Pertama/Index.html`:**
  - Baris **10–21**: header dan navigasi.
  - Baris **23–147**: konten utama dan katalog tiga alat.
  - Baris **149–211**: bagian Tentang, Kontak, dan footer.
- **Pekan 3 — `Kedua/Index.html` dan `Kedua/style.css`:**
  - `Kedua/Index.html`, baris **7**: menghubungkan stylesheet eksternal.
  - `Kedua/style.css`, baris **51–60**: layout hero dengan CSS Grid.
  - `Kedua/style.css`, baris **123–172**: grid, kartu alat, dan tombol kartu.
  - `Kedua/style.css`, baris **205–235**: media query untuk layar maksimal 800px; hero dan katalog menjadi satu kolom.
- **Perbandingan desain — `Ketiga/Style.css`:**
  - Baris **24–62**: navbar dan gaya tautan.
  - Baris **64–148**: hero, tombol, dan kartu hero.
  - Baris **170–227**: kartu katalog.
  - Baris **275–309**: penyempurnaan layout responsif.
- **Interaksi DOM — JavaScript di `TailWind/Tailwind.html`:**
  - Baris **369–387**: memilih tombol dan navigasi dengan `getElementById`, menangani klik, membuka/menutup menu mobile, dan memperbarui atribut aksesibilitas.

#### Anggota 2 — API & Core PHP Engineer (Pekan 4 dan 5)

- **Pekan 4 — `TailWind/tools.json`:**
  - Baris **1–54**: struktur JSON dan enam data alat.
- **Pekan 4 — JavaScript di `TailWind/Tailwind.html`:**
  - Baris **389–416**: URL JSON, elemen status, dan pencatatan log.
  - Baris **417–435**: menghitung estimasi harga sewa.
  - Baris **436–525**: membuat kartu katalog dan opsi alat dari JSON.
  - Baris **526–582**: fetch, loading/success/error, validasi data, serta tombol muat ulang.
  - Baris **583–607**: event pilihan alat, durasi, submit formulir demo, dan pemanggilan awal Fetch.
- **Pekan 5 — pemrosesan data PHP:**
  - `TailWind/Model/PeralatanModel.php`, baris **36–94**: array enam data alat yang dipakai sebagai sumber data PHP.
  - `TailWind/Controller/PeralatanController.php`, baris **4–23**: `require_once`, pemanggilan sumber data, iterasi `foreach`, dan penyiapan daftar untuk View.
  - Fokus penjelasan Pekan 5 adalah alur pemrosesan data PHP. Pembahasan class, properti, constructor, dan enkapsulasi ditempatkan pada materi OOP Anggota 3.

#### Anggota 3 — Lead Architect, OOP & MVC (Pekan 6 dan 7)

- **Pekan 6 — `TailWind/Model/PeralatanModel.php`:**
  - Baris **4–21**: class, properti private bertipe, dan constructor.
  - Baris **23–34**: getter dan `getHargaFormatted()`.
  - Baris **36–94**: method sumber data `getAllData()` yang digunakan oleh alur aplikasi.
- **Pekan 7 — `TailWind/Controller/PeralatanController.php`:**
  - Baris **6–24**: Controller menyiapkan objek dan memuat View.
- **Pekan 7 — `TailWind/index.php`:**
  - Baris **1–8**: memuat Controller dan memanggil `index()`.
- **Pekan 7 — `TailWind/View/katalog_view.php`:**
  - Baris **87–122**: loop katalog dan tampilan kartu.
  - Baris **127–193**: bagian cara sewa dan formulir demo.

> **Penyesuaian terhadap kode proyek:** folder ini tidak memiliki endpoint REST API PHP, fungsi helper prosedural terpisah, ataupun file `data_menu.php`. Materi API Pekan 4 didemonstrasikan dengan Fetch API ke `tools.json`; materi Core PHP Pekan 5 ditunjukkan lewat pengambilan array data, `require_once`, dan `foreach` pada alur PHP yang tersedia. Pekan 6 membahas OOP, sedangkan Pekan 7 menghubungkan komponen MVC. Jangan menyebut Fetch JSON sebagai REST API.

---

## 3. Naskah Siap Rekam

### SEGMENT 1 — Pembukaan dan Menjalankan Proyek
**Pembicara:** Anggota 3 / Lead · **Durasi saran:** 1–2 menit

#### Aksi layar

1. Tampilkan terminal.
2. Jika repositori tersedia untuk clone, jalankan:
   ```bash
   git clone <URL-REPOSITORI>
   cd <folder-repo>
   git log --oneline -n 10
   ```
3. Jalankan Live Server dari root proyek untuk halaman HTML/Fetch, lalu buka terminal pada folder `TailWind` dan jalankan `php -S 127.0.0.1:8000` untuk halaman PHP MVC.
4. Buka proyek di VS Code dan browser.

#### Naskah bicara — **Dibacakan Anggota 3 (Lead)**

> “Assalamu’alaikum warahmatullahi wabarakatuh. Perkenalkan, kami dari kelompok [nama kelompok], yaitu [nama dan NIM anggota]. Pada video ini kami akan mempresentasikan proyek **BangunSewa**, sebuah website informasi dan katalog penyewaan alat bangunan.”
>
> “Kami akan menunjukkan perkembangan halaman dari HTML dan CSS, pemuatan katalog dari file JSON menggunakan Fetch API, serta versi PHP yang memisahkan Model, Controller, dan View. Halaman Tailwind dan Fetch berjalan melalui Live Server pada port 5500, sedangkan demo MVC dijalankan melalui server PHP pada port 8000.”

Jika repositori belum tersedia secara publik, lewati demonstrasi `git clone` dan jelaskan langkah menjalankan proyek dari folder yang ada. Jangan menampilkan URL clone contoh seolah-olah merupakan repositori asli.

---

### SEGMENT 2 — PEKAN 2–3: FRONTEND & DOM
**Pembicara:** Anggota 1 · **Durasi saran:** 3–4 menit

#### Langkah 2.1 — Struktur halaman

**Aksi layar (VS Code):**

1. Buka `Pertama/Index.html`, baris **10–21**, untuk header dan navigasi.
2. Tunjukkan baris **23–147** untuk `<main>`, section, serta kartu katalog Bor Tangan, Gerinda, dan Tangga.
3. Tunjukkan baris **149–211** untuk Tentang, Kontak, dan footer.

**Naskah bicara — Dibacakan Anggota 1:**

> “Terima kasih kepada [Nama Anggota 3]. Saya [Nama Anggota 1, NIM], membawakan Pekan 2 dan Pekan 3. Pada Pekan 2, di `Pertama/Index.html` baris 10 sampai 21 kami membuat header dan navigasi. Kemudian baris 23 sampai 147 berisi `<main>`, section beranda, serta katalog yang memiliki tiga kartu alat.”
>
> “Di baris 149 sampai 211 terdapat bagian Tentang, Kontak, dan footer. Katalog awal ini masih statis karena nama alat, deskripsi, harga, dan tautan pada tiap kartu ditulis langsung di HTML.”

**Aksi layar (browser):**

1. Buka `http://127.0.0.1:5500/Pertama/Index.html`.
2. Klik navigasi **Daftar Alat**, **Tentang**, dan **Kontak**.
3. Tunjukkan bahwa tombol **Lihat Alat** berpindah ke bagian katalog.

#### Langkah 2.2 — CSS eksternal dan layout responsif

**Aksi layar (VS Code):**

1. Buka `Kedua/Index.html` baris **7** untuk melihat stylesheet `style.css` yang dihubungkan melalui `<link>`.
2. Buka `Kedua/style.css` baris **51–60**, **123–172**, dan **205–235** untuk hero, grid kartu, dan media query.
3. Bandingkan dengan `Ketiga/Style.css` baris **24–62**, **170–227**, dan **275–309** untuk melihat penyempurnaan warna, kartu, dan responsivitas.

**Naskah bicara — Dibacakan Anggota 1:**

> “Berlanjut ke Pekan 3, `Kedua/Index.html` baris 7 menghubungkan halaman dengan `style.css`. Di `Kedua/style.css` baris 51 sampai 60, layout hero menggunakan Grid; baris 123 sampai 172 mengatur grid katalog dan tampilan kartu alat.”
>
> “Pada `Kedua/style.css` baris 205 sampai 235 terdapat media query untuk layar maksimal 800 piksel yang menyusun hero dan katalog menjadi satu kolom. Sebagai penyempurnaan visual, di `Ketiga/Style.css` baris 24 sampai 62 terdapat gaya navbar, baris 170 sampai 227 mengatur kartu katalog, dan baris 275 sampai 309 mengatur responsivitasnya.”

**Aksi layar (browser):**

1. Buka `http://127.0.0.1:5500/Kedua/Index.html`, kemudian `http://127.0.0.1:5500/Ketiga/Index.html`.
2. Gunakan DevTools dengan `F12` untuk beralih antara ukuran desktop dan mobile.
3. Perlihatkan perubahan susunan hero, navigasi, dan grid kartu. Jangan mengklaim jumlah kolom mobile yang tidak sesuai dengan hasil yang tampil.

#### Langkah 2.3 — Pekan 3: Pemilihan DOM dan Event Menu Mobile

**Aksi layar (VS Code):**

1. Di `TailWind/Tailwind.html`, buka JavaScript baris **369–387**.
2. Tunjukkan pemilihan `menu-btn` dan `menu`, event `click`, serta perubahan class dan atribut `aria-expanded`.
3. Tunjukkan event klik tautan navigasi yang menutup menu mobile.

**Naskah bicara — Dibacakan Anggota 1:**

> “Untuk melengkapi bagian Frontend dan DOM pada Pekan 3, di `TailWind/Tailwind.html` baris 369 sampai 387 JavaScript memilih tombol dan menu menggunakan `getElementById`. Event `click` pada tombol mengubah status menu dengan menambah atau menghapus class tersembunyi, sekaligus memperbarui `aria-expanded` dan label tombol.”
>
> “Pada bagian yang sama, setiap tautan navigasi diberi event klik agar menu mobile tertutup setelah dipilih. Kita buktikan dengan mengecilkan layar, membuka tombol hamburger, lalu memilih salah satu tautan.”

**Aksi layar (browser):**

1. Buka `http://127.0.0.1:5500/TailWind/Tailwind.html` pada tampilan mobile.
2. Tekan tombol menu hamburger untuk membuka, lalu pilih tautan navigasi untuk menutup menu.

**Naskah bicara — Dibacakan Anggota 1:**

> “Demikian bagian Frontend dan DOM dari saya. Selanjutnya, [Nama Anggota 2] akan menjelaskan pengambilan data API menggunakan Fetch API dan pemrosesan data dengan PHP.”

---

### SEGMENT 3 — PEKAN 4–5: API & CORE PHP
**Pembicara:** Anggota 2 · **Durasi saran:** 4–5 menit

#### Langkah 3.1 — Halaman Tailwind

**Aksi layar (VS Code):**

1. Buka `TailWind/Tailwind.html`, baris **27–46** untuk navigasi dan awal konten utama.
2. Tunjukkan utility class Tailwind pada hero di baris **48–80** dan breakpoint `max-[800px]`.
3. Tunjukkan bahwa katalog dan formulir berada di halaman yang sama.

**Naskah bicara — Dibacakan Anggota 2:**

> “Terima kasih, [Nama Anggota 1]. Saya [Nama Anggota 2, NIM], membawakan Pekan 4 dan Pekan 5. Di `TailWind/Tailwind.html` baris 27 sampai 46 terdapat header, navigasi, dan awal konten utama. Baris 48 sampai 80 menyusun bagian hero dengan utility class Tailwind, termasuk breakpoint untuk layar kecil. Halaman ini juga memiliki katalog, cara sewa, dan formulir permintaan.”

#### Langkah 3.2 — Fetch data JSON dan rendering katalog

**Aksi layar (VS Code):**

1. Buka `TailWind/tools.json`, baris **1–54**, untuk melihat enam data alat.
2. Di `TailWind/Tailwind.html`, buka baris **389–416** untuk URL JSON dan status/log Fetch.
3. Tunjukkan baris **417–525** untuk estimasi harga, pembuatan kartu, dan opsi alat.
4. Tunjukkan baris **526–582** untuk proses Fetch, validasi, serta state loading dan error.
5. Tunjukkan baris **583–607** untuk event pilihan, durasi, dan pemanggilan Fetch awal.

**Naskah bicara — Dibacakan Anggota 2:**

> “Memasuki Pekan 4, `TailWind/tools.json` baris 1 sampai 54 berisi enam data alat, termasuk nama, kategori, deskripsi, dan harga per hari. Di `TailWind/Tailwind.html` baris 389 sampai 416, variabel `apiUrl` menunjuk ke file JSON dan elemen status serta log disiapkan.”
>
> “Fungsi `fetchTools()` pada baris 528 sampai 582 mengambil data dengan `async/await`, memeriksa respons HTTP dan memastikan properti `tools` berupa array. Fungsi ini juga mengatur status loading dan success, serta menangani error dan tombol muat ulang.”
>
> “Setelah data tersedia, `showApiTools()` pada baris 436 sampai 525 membuat elemen kartu katalog dan pilihan alat di formulir. Fungsi `updateRentalEstimate()` pada baris 418 sampai 434 menghitung biaya dari harga harian dikalikan lama sewa. Event untuk pilihan alat, input durasi, dan tombol muat ulang ada di baris 583 sampai 607.”

**Aksi layar (browser):**

1. Buka `http://127.0.0.1:5500/TailWind/Tailwind.html`.
2. Tunjukkan katalog setelah data selesai dimuat.
3. Klik tombol sewa pada salah satu kartu, lalu perlihatkan pilihan alat pada formulir.
4. Ubah lama sewa dan tunjukkan estimasi yang diperbarui.
5. Jika ingin menunjukkan error state, lakukan hanya bila aman untuk demo dan kembalikan file JSON setelahnya.

> **Catatan akurasi:** `tools.json` adalah file JSON statis yang dibaca melalui Fetch API, bukan endpoint REST API. Formulir pada halaman HTML adalah simulasi di browser dan tidak menyimpan permintaan ke server.

#### Langkah 3.3 — Pekan 5: Pemrosesan Data dengan Core PHP

**Aksi layar (VS Code):**

1. Buka `TailWind/Model/PeralatanModel.php`, baris **36–94**, untuk menunjukkan array enam data yang menjadi sumber katalog PHP.
2. Buka `TailWind/Controller/PeralatanController.php`, baris **4–23**.
3. Tunjukkan `require_once` baris **4**, pemanggilan `PeralatanModel::getAllData()` baris **8**, loop `foreach` baris **11**, dan pemuatan View baris **23**.
4. Untuk bagian ini fokuskan penjelasan pada array, pemanggilan data, dan iterasi PHP. Simpan detail class/properti/getter untuk pembahasan OOP Anggota 3.

**Naskah bicara — Dibacakan Anggota 2:**

> “Berikutnya Pekan 5, bagian Core PHP yang tersedia pada proyek ini berfokus pada pemrosesan data katalog. Di `TailWind/Model/PeralatanModel.php` baris 36 sampai 94 terdapat enam data alat dalam bentuk array.”
>
> “Kemudian di `TailWind/Controller/PeralatanController.php` baris 4 sampai 23, `require_once` memuat Model, method `getAllData()` dipanggil pada baris 8, dan `foreach` pada baris 11 mengolah setiap data untuk menyiapkan daftar alat. Pada baris 23, View dimuat menggunakan `require_once`. Data tersebut masih berupa data contoh di kode, belum berasal dari database.”

**Aksi layar (browser):**

1. Buka `http://127.0.0.1:5500/TailWind/Tailwind.html` untuk memperlihatkan data katalog yang diambil dari JSON.
2. Pilih alat dan ubah lama sewa untuk menunjukkan kalkulasi dari Pekan 4.
3. Jelaskan bahwa PHP memproses array datanya melalui alur terpisah di sisi server.

**Naskah bicara — Dibacakan Anggota 2:**

> “Kesimpulannya, bagian API Pekan 4 menggunakan Fetch untuk membaca file JSON, sedangkan Core PHP Pekan 5 menunjukkan bagaimana array data dipanggil dan diproses di server. File JSON bukan endpoint REST API, dan proyek ini belum memiliki endpoint PHP atau helper prosedural terpisah. Selanjutnya, [Nama Anggota 3] akan membahas OOP dan arsitektur MVC.”

---

### SEGMENT 4 — PEKAN 6–7: LEAD ARCHITECT, OOP & MVC
**Pembicara:** Anggota 3 / Lead · **Durasi saran:** 4–5 menit

#### Langkah 4.1 — Pekan 6: Object-Oriented Programming (OOP)

**Aksi layar (VS Code):**

1. Buka `TailWind/Model/PeralatanModel.php`.
2. Sorot baris **4–21** untuk class `PeralatanModel`, tujuh properti `private` bertipe, dan constructor.
3. Sorot baris **23–34** untuk getter dan method `getHargaFormatted()`.
4. Sorot baris **36–94** untuk method `getAllData()` dan array enam alat.

**Naskah bicara — Dibacakan Anggota 3 (Lead):**

> “Terima kasih, [Nama Anggota 2]. Saya [Nama Anggota 3, NIM], bertanggung jawab sebagai Lead Architect dan membawakan Pekan 6 serta Pekan 7. Pada Pekan 6, di `TailWind/Model/PeralatanModel.php` baris 4 sampai 21 kami membangun class `PeralatanModel` sebagai blueprint data alat. Terdapat tujuh atribut bertipe, seperti `id`, `name`, `category`, dan `pricePerDay`, yang dienkapsulasi menggunakan akses `private`. Constructor pada baris 13 sampai 21 menginisialisasi nilai atribut tersebut.”
>
> “Akses ke data dilakukan melalui getter pada baris 23 sampai 29. Method `getHargaFormatted()` pada baris 31 sampai 33 memformat harga harian menjadi Rupiah. Sementara itu, method `getAllData()` pada baris 36 sampai 94 menyediakan enam data contoh untuk digunakan aplikasi.”

#### Langkah 4.2 — Pekan 7: Arsitektur Model-View-Controller (MVC)

**Aksi layar (VS Code):**

1. Buka `TailWind/index.php`, baris **1–8**, sebagai entry point yang memuat Controller dan memanggil `index()`.
2. Buka `TailWind/Controller/PeralatanController.php`, baris **6–24**, untuk alur mengambil data, membentuk objek, dan memuat View.
3. Buka `TailWind/View/katalog_view.php`, baris **87–122**, untuk loop katalog dan tampilan kartu; lalu baris **156–193** untuk formulir demo.

**Naskah bicara — Dibacakan Anggota 3 (Lead):**

> “Pada Pekan 7, kode dipisah ke dalam arsitektur Model-View-Controller. Di `TailWind/index.php` baris 1 sampai 8, berkas entry point memuat Controller, membuat objeknya, lalu memanggil method `index()`.”
>
> “Di `TailWind/Controller/PeralatanController.php` baris 6 sampai 24, method `index()` meminta data dari Model, mengubah setiap item menjadi objek `PeralatanModel`, kemudian memuat View. Terakhir, di `TailWind/View/katalog_view.php` baris 87 sampai 122, View melakukan loop dan menggunakan getter dari objek untuk merender kartu katalog. Inilah alur proyek kita: Model menyediakan data dan representasi objek, Controller menyiapkan alur, lalu View menghasilkan tampilan.”

> “Formulir pada View terlihat di baris 156 sampai 193, tetapi masih berupa antarmuka demo. Formulir belum menyimpan permintaan ke database atau memproses transaksi.”

#### Langkah 4.3 — Demo langsung

**Aksi layar (browser):**

1. Pastikan server PHP berjalan dari folder `TailWind` dengan `php -S 127.0.0.1:8000`.
2. Buka `http://127.0.0.1:8000/index.php`.
3. Tunjukkan katalog enam alat, nama kategori, sumber gambar, dan harga per hari.
4. Scroll ke bagian cara sewa dan formulir. Jelaskan bahwa formulir PHP pada versi ini belum memiliki handler penyimpanan atau pemrosesan permintaan.

**Naskah bicara — Dibacakan Anggota 3 (Lead):**

> “Berikut hasil render versi MVC di browser pada `http://127.0.0.1:8000/index.php`. Enam data alat diproses mengikuti alur Model, Controller, dan View. Kartu katalog menampilkan nama, kategori, deskripsi, dan harga per hari. Fitur ini masih berupa katalog dan formulir antarmuka, belum transaksi atau penyimpanan ke database.”

---

### SEGMENT 5: PENUTUP & PEMBAGIAN KONTRIBUSI ANGGOTA (Wajib Sesuai Rubrik Dosen)

- **Total Durasi:** ~2 menit
- **Aksi Layar:** Tampilkan tabel pembagian tugas pada Bagian 2.2 atau slide rekapitulasi kontribusi secara penuh dan jelas.
- **Naskah Bicara (Dibacakan Anggota 3):**

> “Sebagai penutup video dan untuk memperjelas pembagian tugas masing-masing anggota, berikut rekapitulasi kontribusi dalam proyek BangunSewa:
>
> 1. Pertama, **[Nama Anggota 1 - NIM]** sebagai **Frontend & DOM Engineer**, bertanggung jawab pada Pekan 2 dan Pekan 3. Kontribusinya meliputi penyusunan halaman promosi dengan HTML semantik, pengembangan tampilan dan layout responsif menggunakan CSS, serta interaksi DOM pada menu navigasi untuk tampilan mobile.
>
> 2. Kedua, **[Nama Anggota 2 - NIM]** sebagai **API & Core PHP Engineer**, bertanggung jawab pada Pekan 4 dan Pekan 5. Kontribusinya meliputi pengambilan data katalog secara asinkron menggunakan Fetch API, pembuatan tampilan katalog dari data JSON, serta pengelolaan status pemuatan data. Pada sisi Core PHP, data alat disediakan dalam array dan diproses melalui alur PHP yang digunakan untuk menyiapkan daftar alat.
>
> 3. Ketiga, **[Nama Anggota 3 - NIM]** sebagai **Lead Architect, OOP & MVC**, bertanggung jawab pada Pekan 6 dan Pekan 7. Kontribusinya meliputi perancangan class `PeralatanModel` dengan properti privat, constructor, dan getter, serta pengaturan alur Model-View-Controller yang menghubungkan Model, Controller, dan View untuk menampilkan katalog.
>
> Proyek BangunSewa merupakan website promosi dan katalog sewa alat bangunan. Data yang digunakan masih berupa data contoh, dan formulir permintaan belum menyimpan transaksi ke database.
>
> Demikian presentasi proyek BangunSewa dari kelompok kami. Terima kasih atas perhatian Bapak/Ibu Dosen. Wassalamu’alaikum warahmatullahi wabarakatuh.”

---

## 4. Checklist Rekaman

- [ ] Isi nama kelompok, nama/NIM, dan kontribusi yang sebenarnya.
- [ ] Jalankan Live Server dari root proyek untuk halaman HTML dan Fetch API.
- [ ] Jalankan server PHP dari folder `TailWind` untuk demo MVC.
- [ ] Pastikan URL halaman menggunakan ejaan folder yang sesuai, termasuk `TailWind`.
- [ ] Buka halaman Fetch melalui `http://127.0.0.1:5500/TailWind/Tailwind.html`.
- [ ] Buka halaman MVC melalui `http://127.0.0.1:8000/index.php`.
- [ ] Pastikan katalog JSON berhasil dimuat sebelum mulai merekam.
- [ ] Siapkan DevTools untuk menunjukkan layout responsif.
- [ ] Tampilkan kode yang relevan bersamaan dengan hasilnya di browser.
- [ ] Jangan tampilkan nomor WhatsApp atau informasi kontak yang belum dikonfirmasi sebagai kontak aktif.
- [ ] Pastikan deskripsi video dan status publik mengikuti instruksi pengumpulan yang berlaku.

---

## 5. Template Deskripsi Video

Salin dan lengkapi bagian dalam tanda kurung siku sebelum mengunggah:

```text
PRESENTASI PROYEK WEBSITE BANGUNSEWA

Proyek: Website promosi dan katalog sewa alat bangunan
Repositori: <URL-REPOSITORI>

ANGGOTA DAN KONTRIBUSI:
1. [NIM] - [Nama]
   Peran: Frontend & DOM Engineer
   Kontribusi: Pekan 2–3 (HTML semantik, CSS responsif, DOM dan event navigasi).
   Berkas: Pertama/Index.html, Kedua/Index.html, Kedua/style.css, Ketiga/Style.css, TailWind/Tailwind.html
2. [NIM] - [Nama]
   Peran: API & Core PHP Engineer
   Kontribusi: Pekan 4 (Fetch API dan status jaringan) serta Pekan 5 (data array dan pemrosesan data dengan PHP).
   Berkas: TailWind/Tailwind.html, TailWind/tools.json, TailWind/Controller/PeralatanController.php, TailWind/Model/PeralatanModel.php
3. [NIM] - [Nama]
   Peran: Lead Architect, OOP & MVC
   Kontribusi: Pekan 6 (class OOP dan enkapsulasi) serta Pekan 7 (integrasi Model, Controller, View, dan entry point).
   Berkas: TailWind/Model/PeralatanModel.php, TailWind/index.php, TailWind/Controller/PeralatanController.php, TailWind/View/katalog_view.php

TIMESTAMPS / CHAPTERS:
00:00 Pembukaan dan setup proyek
01:30 Pekan 2: Frontend - HTML semantik dan katalog
03:00 Pekan 3: Frontend & DOM - CSS responsif dan event menu
05:00 Pekan 4: API - Fetch API, data JSON, dan status jaringan
07:30 Pekan 5: Core PHP - data array dan pemrosesan server-side
09:00 Pekan 6: OOP - class PeralatanModel dan enkapsulasi
10:30 Pekan 7: MVC - Model, Controller, View, dan demo katalog
13:30 Kesimpulan dan pembagian kontribusi
```

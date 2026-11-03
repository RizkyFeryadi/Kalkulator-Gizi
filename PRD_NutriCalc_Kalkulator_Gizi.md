# PRD — NutriCalc (Kalkulator Gizi Harian)

## 1. Informasi Dokumen

| Item | Keterangan |
|---|---|
| **Nama Produk** | NutriCalc — Kalkulator Gizi Harian |
| **Versi Dokumen** | 1.0 (Draft) |
| **Tanggal** | 20 Oktober 2026 |
| **Status** | Draft — siap direview |
| **Jenis Produk** | Web app mobile-first (PWA), bahasa Indonesia |
| **Sumber Desain** | `DESIGN.md` (design system "Monochrome Nutrition") dan `code.html` (prototipe layar **Harian**) |
| **Bahasa Antarmuka** | Indonesia (satuan: `kkal`, `g`; label: Karbo, Protein, Lemak) |

---

## 2. Ringkasan Produk

**NutriCalc** adalah web app untuk menghitung dan memantau asupan gizi harian: kalori (kkal) dan tiga makronutrien utama, yaitu **karbohidrat, protein, dan lemak**. Pengguna mencatat makanan per waktu makan (Sarapan, Makan Siang, Makan Malam), lalu aplikasi menghitung total, sisa kalori, dan persentase pencapaian terhadap target pribadi.

Pembeda utama produk ini adalah **kejelasan data**. Tampilannya monokrom, minimalis, dan bergaya editorial, sehingga angka menjadi fokus utama tanpa gamifikasi berlebihan atau warna yang mengganggu.

> **Catatan cakupan:** Prototipe yang tersedia baru mencakup layar **Harian** (beranda). Layar **Catat**, **Riwayat**, dan **Profil** ada di navigasi, tetapi desainnya belum dibuat. PRD ini mendefinisikan kebutuhannya, dan desain layar-layar tersebut harus dibuat mengikuti design system yang sama (lihat Bagian 9).

---

## 3. Latar Belakang dan Masalah

- Banyak orang ingin mengatur pola makan (menurunkan berat badan, menjaga berat, menambah massa otot), tetapi **tidak tahu kebutuhan kalori dan makronutriennya**.
- Aplikasi pencatat kalori yang ada umumnya **penuh iklan, ramai secara visual, dan didominasi data makanan Barat**, sehingga makanan Indonesia seperti nasi, tempe, pecel, atau soto sulit ditemukan dan takarannya tidak sesuai.
- Pencatatan manual terasa **melelahkan**, sehingga pengguna berhenti setelah beberapa hari.
- Antarmuka yang terlalu bergamifikasi membuat angka penting sulit dibaca sekilas.

**Peluang:** aplikasi yang cepat dipakai, berfokus pada angka, dan memiliki basis data pangan Indonesia.

---

## 4. Tujuan dan Sasaran

### Tujuan Produk
1. Membantu pengguna **menghitung kebutuhan kalori dan makronutrien harian** secara pribadi.
2. Membuat pencatatan makanan **cepat (< 30 detik per entri)**.
3. Menampilkan progres harian secara **jelas dalam sekali lihat**.
4. Menyediakan **basis data pangan Indonesia** yang relevan.
5. Membangun kebiasaan mencatat lewat streak yang tidak menekan.

### Di Luar Tujuan
- Bukan alat diagnosis atau terapi medis.
- Bukan platform sosial atau komunitas.
- Bukan marketplace atau layanan pesan-antar makanan.

---

## 5. Metrik Keberhasilan

| Metrik | Target (6 bulan pertama) |
|---|---|
| Penyelesaian onboarding (profil + target terhitung) | ≥ 70% |
| Pengguna yang mencatat ≥ 1 makanan di hari pertama (aktivasi) | ≥ 60% |
| Retensi hari ke-7 | ≥ 30% |
| Rata-rata hari tercatat per pengguna aktif per minggu | ≥ 4 hari |
| Waktu median mencatat satu makanan | ≤ 30 detik |
| Pencarian makanan yang menghasilkan hasil relevan | ≥ 90% |
| Skor Lighthouse (Performance / Accessibility / PWA) | ≥ 90 / ≥ 95 / terpenuhi |
| Waktu muat layar Harian (4G) | ≤ 2 detik (LCP) |

---

## 6. Target Pengguna dan Persona

### Persona 1 — Sari (27), Pekerja Kantoran
- **Tujuan:** menurunkan berat badan 5 kg secara bertahap.
- **Masalah:** tidak tahu berapa kalori yang aman; sering makan di warung dan kantin.
- **Kebutuhan:** target kalori otomatis, database makanan Indonesia, pencatatan cepat lewat ponsel.

### Persona 2 — Bagas (22), Mahasiswa yang Rutin Nge-gym
- **Tujuan:** menambah massa otot dengan asupan protein cukup.
- **Masalah:** sulit memantau protein harian.
- **Kebutuhan:** target protein jelas, progres makro terlihat sekilas, bisa menyimpan makanan favorit.

### Persona 3 — Bu Ratna (45), Menjaga Pola Makan Sehat
- **Tujuan:** menjaga berat badan dan lebih sadar porsi.
- **Masalah:** aplikasi lain terlalu rumit.
- **Kebutuhan:** tampilan sederhana, teks mudah dibaca, tombol besar.

---

## 7. Cakupan Layar (Inventaris)

| Layar / Komponen | Status Desain | Keterangan |
|---|---|---|
| **Harian** (beranda) | ✅ Ada di `code.html` | Hero kalori + makro, jurnal konsumsi, pemindai cepat |
| **Catat** (cari & tambah makanan) | ❌ Belum didesain | Pencarian, pemilihan porsi, pilih waktu makan |
| **Riwayat** (tren & statistik) | ❌ Belum didesain | Grafik mingguan/bulanan, kalender |
| **Profil** (pengaturan & target) | ❌ Belum didesain | Data tubuh, tujuan, target, preferensi |
| **Onboarding** | ❌ Belum didesain | Input data tubuh → target dihitung |
| **Pindai (kamera/barcode)** | ❌ Belum didesain | Dipicu dari kartu "Pindai Makanan Cepat" |
| **Bottom sheet "Tambah/Ubah Porsi"** | ❌ Belum didesain | Level 3 elevasi sesuai design system |
| **Autentikasi** (masuk/daftar) | ❌ Belum didesain | Atau mode tamu |

### Anatomi Layar Harian (sesuai prototipe)

```
┌──────────────────────────────────────────┐
│ [logo] NutriCalc / Harian   🔥5 Hari  👤 │  ← header tetap (blur)
├──────────────────────────────────────────┤
│ ( Kemarin | ● Hari Ini (Rab, 24 Mei) | Besok ) │  ← pill date switcher
│                                          │
│ ┌──────────────────────────────────────┐ │
│ │            ◜ ring kalori ◝           │ │
│ │   TERCAPAI  1.420 / 2.100  kkal      │ │  ← kartu hero
│ │         [ Sisa 680 kkal ]            │ │
│ │ [Karbo 74%] [Protein 75%] [Lemak 65%]│ │
│ │  185/250g     98/130g      42/65g    │ │
│ └──────────────────────────────────────┘ │
│ Jurnal Konsumsi            3 dari 3 waktu makan │
│ ▸ Sarapan  07:00–09:00        430 kkal   │  ← accordion
│ ▸ Makan Siang 12:00–14:00     620 kkal   │
│ ▸ Makan Malam 18:30–20:30     370 kkal   │
│ ┌──────────────────────────────────────┐ │
│ │ Pindai Makanan Cepat        [Pindai →]│ │
│ └──────────────────────────────────────┘ │
├──────────────────────────────────────────┤
│  Harian    (＋)Catat    Riwayat   Profil │  ← bottom nav
└──────────────────────────────────────────┘
```

---

## 8. User Stories

| ID | User Story | Prioritas |
|---|---|---|
| US-01 | Sebagai pengguna baru, saya ingin memasukkan data tubuh dan tujuan saya, agar aplikasi menghitung target kalori dan makro saya. | Must |
| US-02 | Sebagai pengguna, saya ingin melihat total kalori dan makro hari ini terhadap target, agar tahu sisa jatah makan saya. | Must |
| US-03 | Sebagai pengguna, saya ingin mencari makanan dan memilih porsinya, agar nilai gizinya terhitung otomatis. | Must |
| US-04 | Sebagai pengguna, saya ingin mencatat makanan ke Sarapan, Makan Siang, atau Makan Malam, agar jurnal saya terorganisir. | Must |
| US-05 | Sebagai pengguna, saya ingin mengubah atau menghapus entri makanan, agar bisa memperbaiki kesalahan catat. | Must |
| US-06 | Sebagai pengguna, saya ingin berpindah ke hari kemarin atau besok, agar bisa melengkapi catatan atau merencanakan menu. | Must |
| US-07 | Sebagai pengguna, saya ingin menambahkan makanan yang tidak ada di database, agar pencatatan tidak terhenti. | Must |
| US-08 | Sebagai pengguna, saya ingin melihat tren asupan mingguan/bulanan, agar tahu apakah saya konsisten. | Should |
| US-09 | Sebagai pengguna, saya ingin memindai barcode kemasan, agar tidak mengetik manual. | Should |
| US-10 | Sebagai pengguna, saya ingin menyalin makanan dari hari/waktu makan lain, agar mencatat menu berulang lebih cepat. | Should |
| US-11 | Sebagai pengguna, saya ingin menyimpan makanan favorit dan makanan terakhir, agar akses lebih cepat. | Should |
| US-12 | Sebagai pengguna, saya ingin melihat streak pencatatan, agar termotivasi konsisten. | Should |
| US-13 | Sebagai pengguna, saya ingin mengubah target kalori/makro secara manual, agar sesuai arahan ahli gizi saya. | Should |
| US-14 | Sebagai pengguna, saya ingin memotret makanan dan mendapat perkiraan gizi (AI), agar pencatatan lebih cepat. | Could |
| US-15 | Sebagai pengguna, saya ingin membuat resep/menu gabungan dari beberapa bahan, agar masakan rumah mudah dicatat. | Could |
| US-16 | Sebagai pengguna, saya ingin mengekspor data saya, agar bisa dibagikan ke ahli gizi. | Could |
| US-17 | Sebagai pengguna, saya ingin aplikasi tetap bisa dipakai tanpa internet, agar pencatatan tidak terputus. | Should |

---

## 9. Kebutuhan Fungsional

### 9.1 Onboarding dan Profil

| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-01 | Pengguna mengisi: jenis kelamin, tanggal lahir/usia, tinggi (cm), berat (kg), tingkat aktivitas, dan tujuan (turun / jaga / naik berat badan). | Must |
| FR-02 | Aplikasi menghitung **BMR**, **TDEE**, **target kalori**, dan **target makro** (lihat Bagian 10). | Must |
| FR-03 | Hasil perhitungan ditampilkan beserta penjelasan singkat dan dapat disesuaikan manual sebelum disimpan. | Must |
| FR-04 | Pengguna dapat mengubah profil dan target kapan saja di layar **Profil**; target dihitung ulang dengan konfirmasi. | Must |
| FR-05 | Pengguna dapat memilih pembagian makro (preset: Seimbang, Tinggi Protein, Rendah Karbo) atau kustom (total harus 100%). | Should |
| FR-06 | Usia < 18 tahun, hamil/menyusui, atau kondisi medis: tampilkan peringatan dan sarankan konsultasi tenaga kesehatan. | Must |

### 9.2 Layar Harian (Dashboard)

| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-07 | **Date switcher** (pill): *Kemarin / Hari Ini / Besok*, dengan tanggal aktif ditampilkan (contoh: "Hari Ini (Rab, 24 Mei)"). Tanggal lain diakses lewat kalender di Riwayat. | Must |
| FR-08 | **Ring kalori** menampilkan "Tercapai", kalori terpakai / target, satuan `kkal`, dan chip "Sisa X kkal". | Must |
| FR-09 | Jika kalori melebihi target, chip berubah menjadi "Lebih X kkal" dan ring terisi penuh (tanpa warna alarm merah; gunakan tipografi dan ikon). | Must |
| FR-10 | **Kartu makro** untuk Karbo, Protein, Lemak: persentase, progress bar, dan nilai `terpakai/target g`. | Must |
| FR-11 | **Streak** di header ("🔥 N Hari"): jumlah hari berturut-turut dengan pencatatan memenuhi syarat. | Should |
| FR-12 | **Jurnal Konsumsi**: tiga accordion (Sarapan, Makan Siang, Makan Malam) dengan rentang jam, jumlah hidangan, dan total kkal per waktu makan. | Must |
| FR-13 | Setiap item makanan menampilkan foto kecil, nama (dengan takaran), kkal, dan rincian `K / P / L` dalam gram, serta tombol **Ubah** dan **Hapus**. | Must |
| FR-14 | Tombol **"Tambah ke [waktu makan]"** di setiap accordion membuka bottom sheet pencatatan dengan waktu makan terisi otomatis. | Must |
| FR-15 | Kartu **"Pindai Makanan Cepat"** membuka pemindai barcode (dan kamera AI jika tersedia). | Should |
| FR-16 | Semua total (ring, kartu makro, total per waktu makan) **dihitung dari entri**, bukan angka tetap. Satu sumber data kebenaran. | Must |
| FR-17 | Hapus item memerlukan konfirmasi ringan atau opsi **Batalkan** (undo toast, ± 5 detik). | Must |
| FR-18 | Jam tiap waktu makan dapat diatur di Profil; pencatatan di luar rentang tetap diizinkan. | Could |

### 9.3 Layar Catat (Pencarian dan Pencatatan)

| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-19 | Pencarian makanan dengan pencarian cepat (*debounce*), toleran salah ketik, dan mendukung sinonim lokal (misal "bakso" / "baso"). | Must |
| FR-20 | Tab/pill filter: **Semua, Terakhir, Favorit, Buatan Saya**. | Should |
| FR-21 | Detail makanan: pilih **satuan porsi** (gram, porsi, butir, sendok, piring, gelas, dll.) dan jumlah; nilai gizi dihitung langsung (*live*) saat jumlah diubah. | Must |
| FR-22 | Pilih **tanggal** dan **waktu makan** sebelum menyimpan. | Must |
| FR-23 | **Makanan kustom**: pengguna dapat membuat makanan baru (nama, porsi, kkal, K, P, L; opsional serat, gula, natrium). | Must |
| FR-24 | Validasi input kustom: angka ≥ 0, dan kkal harus mendekati hasil `4K + 4P + 9L` (peringatan jika selisih besar, tidak memblokir). | Should |
| FR-25 | Foto makanan: ikon/foto default; pengguna dapat mengunggah foto sendiri (opsional). | Could |
| FR-26 | Tombol **Salin dari...** untuk menyalin entri dari hari atau waktu makan lain. | Should |
| FR-27 | **Resep/menu gabungan** dari beberapa bahan dengan jumlah porsi. | Could |

### 9.4 Pemindaian

| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-28 | Pemindaian **barcode** lewat kamera (Barcode Detection API / pustaka JS) dan pencarian ke database produk. | Should |
| FR-29 | Jika barcode tidak ditemukan, tawarkan form **tambah produk** (makanan kustom) dengan barcode terisi. | Should |
| FR-30 | **Kamera AI** (foto → perkiraan makanan + porsi). Hasil selalu berupa *saran* yang bisa diedit; tampilkan label "Perkiraan". | Could (Fase 2) |
| FR-31 | Izin kamera diminta saat dibutuhkan, dengan penjelasan; tersedia alternatif input manual bila ditolak. | Must |

### 9.5 Layar Riwayat

| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-32 | Grafik asupan kalori **7 hari / 30 hari** terhadap target (grafik monokrom sesuai design system). | Should |
| FR-33 | Rata-rata makro per periode dan jumlah hari yang memenuhi target. | Should |
| FR-34 | Kalender ringkas; ketuk tanggal untuk membuka layar Harian tanggal itu. | Should |
| FR-35 | Grafik tren berat badan (input berat manual). | Could |
| FR-36 | Ekspor riwayat ke CSV/PDF. | Could |

### 9.6 Layar Profil dan Pengaturan

| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-37 | Edit data tubuh, tujuan, tingkat aktivitas, dan target manual. | Must |
| FR-38 | Pengaturan satuan (metrik; opsional imperial) dan jam waktu makan. | Could |
| FR-39 | Pengingat pencatatan (notifikasi web push, opsional dan dapat dimatikan). | Could |
| FR-40 | Kelola data: ekspor data pribadi dan **hapus akun beserta seluruh data**. | Must |
| FR-41 | Tema gelap (turunan design system). | Could |

### 9.7 Akun dan Sinkronisasi

| ID | Kebutuhan | Prioritas |
|---|---|---|
| FR-42 | Masuk/daftar via email + OTP/tautan ajaib atau Google. Mode **tamu** menyimpan data lokal dan dapat ditautkan ke akun nanti. | Must |
| FR-43 | Data tersinkron antar perangkat untuk akun terdaftar. | Should |
| FR-44 | **Offline-first**: mencatat tanpa internet, sinkron otomatis saat online (penyelesaian konflik: *last-write-wins* per entri). | Should |

---

## 10. Logika Perhitungan Gizi

### 10.1 Kebutuhan Kalori

**BMR (persamaan Mifflin-St Jeor):**

- Pria: `BMR = 10 × berat(kg) + 6,25 × tinggi(cm) − 5 × usia + 5`
- Wanita: `BMR = 10 × berat(kg) + 6,25 × tinggi(cm) − 5 × usia − 161`

**TDEE = BMR × faktor aktivitas**

| Tingkat Aktivitas | Faktor |
|---|---|
| Sangat jarang bergerak | 1,2 |
| Ringan (olahraga 1–3×/minggu) | 1,375 |
| Sedang (3–5×/minggu) | 1,55 |
| Aktif (6–7×/minggu) | 1,725 |
| Sangat aktif (fisik berat / 2× sehari) | 1,9 |

**Target kalori berdasarkan tujuan:**

| Tujuan | Penyesuaian |
|---|---|
| Menurunkan berat badan | TDEE − 300 s.d. 500 kkal (default −400) |
| Menjaga berat badan | TDEE |
| Menambah berat badan | TDEE + 250 s.d. 400 kkal (default +300) |

**Batas pengaman:** target kalori tidak boleh di bawah **1.200 kkal/hari** (wanita) atau **1.500 kkal/hari** (pria) pada hasil otomatis. Jika pengguna menetapkan manual di bawah batas, tampilkan peringatan dan sarankan konsultasi tenaga kesehatan.

### 10.2 Target Makronutrien

Konversi energi (faktor Atwater): **Karbohidrat 4 kkal/g, Protein 4 kkal/g, Lemak 9 kkal/g.**

`gram = (kalori target × persentase makro) ÷ kkal per gram`

| Preset | Karbo | Protein | Lemak |
|---|---|---|---|
| Seimbang (default) | 50% | 25% | 25% |
| Tinggi Protein | 40% | 35% | 25% |
| Rendah Karbo | 30% | 30% | 40% |

> Prototipe memakai target 2.100 kkal dengan 250 g karbo / 130 g protein / 65 g lemak, yang setara kira-kira 48% / 25% / 28%. Preset default dapat disesuaikan agar konsisten dengan prototipe ini.

### 10.3 Penghitungan Entri

- `nilai gizi entri = nilai gizi per satuan dasar × (jumlah × berat per satuan ÷ satuan dasar)`
- Total harian = jumlah seluruh entri pada tanggal tersebut.
- `persentase makro = terpakai ÷ target × 100`, ditampilkan sebagai bilangan bulat; progress bar dibatasi maksimal 100% secara visual, tetapi angka asli tetap ditampilkan.
- Pembulatan tampilan: kkal ke bilangan bulat; gram ke 1 desimal (jika bukan bilangan bulat). Penyimpanan tetap presisi penuh.
- Pemisah ribuan memakai format Indonesia (`1.420`, desimal `5,4`).

---

## 11. Desain UI/UX

Seluruh antarmuka mengikuti design system **Monochrome Nutrition** pada `DESIGN.md`.

### 11.1 Prinsip Desain
1. **Angka adalah bintangnya**: hierarki visual berasal dari ukuran dan bobot tipografi, bukan warna.
2. **Monokrom cool-toned**: tanpa kode warna pelangi untuk makro.
3. **Ringkas dan tenang**: banyak ruang kosong, bayangan sangat halus.
4. **Mudah dijangkau jempol**: aksi utama berada di sepertiga bawah layar.

### 11.2 Token Desain Utama

| Elemen | Nilai |
|---|---|
| **Font** | Plus Jakarta Sans (400/500/600/700), angka bergaya *tabular* (`tnum`) |
| **Warna primer (slate)** | `#1E293B` (aksi & teks utama); `#091426` untuk teks pada prototipe |
| **Warna sekunder** | `#64748B` (teks pendukung, label tidak aktif) |
| **Border halus** | `#E2E8F0` |
| **Permukaan kartu** | `#F8FAFC` |
| **Kanvas** | `#FFFFFF` / `#F7F9FB` |
| **Radius** | 8 px (input, tombol), 16 px (kartu), `full` (pill, badge, tab) |
| **Spasi** | Kelipatan 4/8 px; margin layar 16 px, gutter 16 px (24 px tablet) |
| **Elevasi** | Level 1 kartu, Level 2 kontrol mengambang, Level 3 modal/bottom sheet |
| **Ikon** | Material Symbols Outlined |

### 11.3 Komponen Utama

| Komponen | Spesifikasi Ringkas |
|---|---|
| Header tetap | Tinggi 64 px, latar putih transparan + *backdrop blur*, logo, chip streak, avatar profil |
| Pill date switcher | Wadah `surface-container-high`, segmen aktif putih dengan bayangan |
| Ring kalori | Diameter ± 176 px, stroke 12 px, ujung membulat, animasi isi 1 detik (*ease-out*) |
| Kartu makro | 3 kolom; label, persentase, progress bar 6 px, nilai `x/y g` |
| Accordion waktu makan | Ikon bulat, judul + rentang jam, jumlah hidangan, total kkal, ikon panah berputar |
| Baris makanan | Foto 40×40, nama (truncate), rincian `K/P/L`, tombol ubah/hapus |
| Bottom navigation | 4 tab: Harian, Catat (tombol bulat menonjol), Riwayat, Profil; target sentuh ≥ 44 px |
| Tombol utama | Tinggi 48 px, isi slate, teks putih, efek tekan `scale(0.98)` |

### 11.4 Perilaku Responsif

| Lebar | Perilaku |
|---|---|
| **< 640 px (mobile)** | Satu kolom, bottom navigation, margin 16 px |
| **640–1023 px (tablet)** | Konten maksimal 720 px di tengah, margin 32 px, gutter 24 px |
| **≥ 1024 px (desktop)** | Dua panel: kolom kiri ringkasan (ring + makro), kolom kanan jurnal; lebar maks 1024 px; navigasi pindah ke sisi/atas |

### 11.5 Status Tampilan yang Wajib Didesain

- **Kosong** (belum ada catatan di waktu makan): ilustrasi minimal + ajakan "Tambah ke ...".
- **Memuat**: kerangka (*skeleton*) abu-abu, bukan spinner.
- **Gagal/offline**: banner ringan "Mode offline — data akan disinkronkan".
- **Melebihi target**: lihat FR-09.
- **Kesalahan input**: pesan di bawah field, batas input berubah ke slate gelap, tanpa warna alarm berlebihan.

---

## 12. Model Data (Konseptual)

| Entitas | Atribut Utama |
|---|---|
| **User** | id, email, dibuat_pada, mode (tamu/terdaftar) |
| **Profile** | user_id, jenis_kelamin, tanggal_lahir, tinggi_cm, berat_kg, tingkat_aktivitas, tujuan |
| **Target** | user_id, kalori, karbo_g, protein_g, lemak_g, mode (otomatis/manual), berlaku_sejak |
| **Food** | id, nama, nama_alternatif[], sumber (TKPI / Open Food Facts / Pengguna), barcode?, per_100g (kkal, karbo, protein, lemak, serat?, gula?, natrium?), foto_url?, pemilik_id? |
| **FoodServing** | food_id, label (mis. "1 butir"), gram_per_satuan |
| **LogEntry** | id, user_id, tanggal, waktu_makan (sarapan / siang / malam), food_id, jumlah, satuan, snapshot_gizi (kkal, K, P, L), dibuat_pada, diubah_pada |
| **Favorite** | user_id, food_id |
| **WeightLog** | user_id, tanggal, berat_kg |

**Catatan penting:** `LogEntry` menyimpan **snapshot** nilai gizi saat dicatat, sehingga perubahan pada data makanan di kemudian hari tidak mengubah riwayat lama.

### Sumber Data Makanan
- **TKPI** (Tabel Komposisi Pangan Indonesia, Kemenkes RI) sebagai basis utama makanan Indonesia, perlu memeriksa lisensi dan ketentuan penggunaannya.
- **Open Food Facts** (data terbuka) untuk produk kemasan/barcode, perlu menyesuaikan lisensi ODbL dan atribusinya.
- **Entri pengguna** untuk makanan yang belum tersedia, dengan label "Buatan pengguna".

---

## 13. Kebutuhan Non-Fungsional

| Kategori | Kebutuhan |
|---|---|
| **Performa** | LCP ≤ 2 detik di 4G; interaksi < 100 ms; pencarian makanan < 300 ms; animasi 60 fps. |
| **Offline/PWA** | Dapat dipasang ke layar utama (manifest + service worker); layar Harian dan pencatatan berfungsi offline. |
| **Responsif** | Mobile ≥ 360 px hingga desktop; mendukung area aman (*safe area*) perangkat berponi. |
| **Aksesibilitas** | WCAG 2.2 AA: kontras teks ≥ 4,5:1, target sentuh ≥ 44 px, navigasi keyboard, label ARIA pada ring/progress, dukungan *screen reader*, hormati `prefers-reduced-motion`. |
| **Keamanan** | HTTPS wajib; token aman; validasi di sisi server; perlindungan terhadap XSS/CSRF; pembatasan laju (*rate limit*) API. |
| **Privasi** | Patuh **UU No. 27 Tahun 2022 tentang Pelindungan Data Pribadi (UU PDP)**; data berat, tinggi, dan pola makan diperlakukan sebagai data sensitif; persetujuan eksplisit; hapus akun = hapus data. |
| **Kompatibilitas** | Chrome, Safari (iOS 16+), Edge, Firefox versi terbaru; Android 9+. |
| **Skalabilitas** | Mendukung ≥ 10.000 pengguna aktif harian di fase awal tanpa perubahan arsitektur besar. |
| **Keterpeliharaan** | Kode modular, uji otomatis untuk fungsi perhitungan gizi, CI sederhana. |
| **Lokalisasi** | Bahasa Indonesia; struktur teks siap diterjemahkan (i18n). |

---

## 14. Rekomendasi Teknologi

> Bagian ini bersifat saran. Keputusan final diambil bersama tim teknis.

| Lapisan | Pilihan yang Disarankan | Catatan |
|---|---|---|
| Frontend | HTML + **Tailwind CSS** (build sendiri), dengan React/Vue/Svelte atau JavaScript murni | Prototipe memakai `cdn.tailwindcss.com`, **tidak untuk produksi** karena harus di-*build* (Tailwind CLI/PostCSS). |
| Penyimpanan lokal | IndexedDB (mis. Dexie) | Untuk mode offline dan tamu. |
| Backend & Auth | Supabase / Firebase, atau Node.js + PostgreSQL | Pilih yang paling cepat untuk fase MVP. |
| Pencarian makanan | Indeks pencarian di database (full-text) atau Meilisearch | Untuk pencarian toleran salah ketik. |
| Pemindai | `BarcodeDetector` API + pustaka cadangan (mis. ZXing) | Dukungan browser bervariasi, perlu *fallback*. |
| AI kamera (Fase 2) | API model visi pihak ketiga | Perlu evaluasi akurasi, biaya, dan privasi foto. |
| Hosting | Vercel / Netlify / Cloudflare Pages | HTTPS otomatis. |
| Aset | Font dan ikon di-*host* sendiri | Hindari ketergantungan pada URL gambar sementara. |

---

## 15. Rencana Rilis

### MVP (v1.0)
- Onboarding + perhitungan target (BMR/TDEE/makro)
- Layar **Harian** lengkap (ring, makro, jurnal, date switcher)
- **Catat**: pencarian makanan, porsi, makanan kustom, ubah/hapus
- Profil: edit data & target
- Mode tamu + penyimpanan lokal; PWA dasar
- Basis data pangan Indonesia awal (± 1.000 makanan umum)

### v1.1
- Akun + sinkronisasi antar perangkat
- Riwayat: grafik 7/30 hari, kalender
- Favorit, terakhir dipakai, salin dari hari lain
- Streak
- Pemindai barcode

### v1.2
- Kamera AI (perkiraan makanan)
- Resep/menu gabungan
- Ekspor data, pengingat, tema gelap
- Pelacakan berat badan

### Ide Jangka Panjang
- Zat gizi mikro (serat, gula, natrium, vitamin)
- Integrasi Apple Health / Google Fit
- Rekomendasi menu sesuai sisa makro
- Mode ahli gizi (berbagi laporan klien)

---

## 16. Di Luar Cakupan (MVP)

- Aplikasi native iOS/Android (cukup PWA)
- Fitur sosial, komunitas, papan peringkat
- Marketplace, pesan-antar, atau afiliasi makanan
- Rencana diet/konsultasi medis berbayar
- Pelacakan olahraga dan kalori terbakar terperinci
- Pembayaran/langganan (ditentukan setelah validasi produk)

---

## 17. Asumsi, Batasan, dan Ketergantungan

**Asumsi**
- Mayoritas pengguna mengakses lewat ponsel dengan koneksi tidak selalu stabil.
- Data TKPI dan Open Food Facts boleh digunakan sesuai lisensinya.
- Persamaan Mifflin-St Jeor cukup akurat untuk populasi dewasa umum sebagai titik awal.

**Batasan**
- Nilai gizi bersifat **perkiraan**; variasi cara memasak dan merek memengaruhi hasil sebenarnya.
- Dukungan Barcode Detection API terbatas pada beberapa browser.
- Foto makanan dalam prototipe berasal dari URL eksternal sementara dan **harus diganti** dengan aset berlisensi/milik sendiri.

**Ketergantungan**
- Sumber data pangan (TKPI, Open Food Facts), layanan backend/auth, layanan AI visi (fase 2).

---

## 18. Risiko dan Mitigasi

| Risiko | Dampak | Mitigasi |
|---|---|---|
| Database makanan Indonesia kurang lengkap | Pengguna frustrasi, berhenti pakai | Mulai dari TKPI, izinkan makanan kustom, kumpulkan "makanan tidak ditemukan" sebagai prioritas penambahan. |
| Akurasi AI kamera rendah | Data salah, kepercayaan turun | Tandai sebagai perkiraan, wajib dikonfirmasi pengguna, rilis di fase 2 setelah uji. |
| Target kalori terlalu rendah atau tidak sehat | Risiko kesehatan, tanggung jawab | Batas minimum aman, peringatan, disclaimer, tidak menampilkan kalimat yang mendorong pembatasan ekstrem. |
| Aplikasi memicu perilaku makan tidak sehat | Dampak psikologis | Hindari bahasa "dosa/hukuman"; netral dalam menampilkan kelebihan kalori; sediakan opsi menyembunyikan angka kalori & streak. |
| Kebocoran/penyalahgunaan data kesehatan | Hukum & reputasi | Enkripsi, akses minimum, kebijakan privasi jelas, kepatuhan UU PDP. |
| Ketergantungan pada CDN & gambar eksternal | Tampilan rusak/lambat | Build Tailwind sendiri, host font/ikon/gambar sendiri. |
| Pengguna berhenti mencatat setelah beberapa hari | Retensi rendah | Pencatatan cepat, favorit, salin hari lalu, pengingat opsional, streak yang memaafkan. |
| Lisensi data pihak ketiga | Masalah hukum | Tinjau lisensi sebelum impor; cantumkan atribusi. |

---

## 19. Catatan Review Desain dan Prototipe

Temuan berikut muncul saat menelaah `code.html` dan `DESIGN.md`; sebaiknya diselesaikan sebelum pengembangan.

1. **Data contoh tidak konsisten.** Total yang tampil di prototipe tidak sama dengan jumlah item. Misalnya, Makan Siang tertulis 620 kkal, tetapi item-itemnya berjumlah 165 + 247 + 108 = **520 kkal**; Makan Malam tertulis 370 kkal, padahal item-itemnya 180 + 95 + 0 = **275 kkal**. Total makro (K 185 g, P 98 g, L 42 g) juga belum cocok dengan jumlah item. Ini hanya data contoh, tetapi aplikasi nyata **wajib menghitung semua total dari entri** (FR-16).
2. **Viewport menonaktifkan zoom** (`maximum-scale=1.0, user-scalable=no`). Ini menyulitkan pengguna dengan gangguan penglihatan dan bertentangan dengan WCAG; sebaiknya dihapus.
3. **Warna primer berbeda antara dokumen dan kode.** `DESIGN.md` menyebut primer `#1E293B`, sedangkan konfigurasi Tailwind pada prototipe memakai `primary: #091426` dan `primary-container: #1E293B`. Tentukan satu acuan resmi (token).
4. **Penyajian makro berbeda.** `DESIGN.md` mendefinisikan *badge* makro (Protein terisi gelap, Karbo outline, Lemak abu), sedangkan prototipe memakai kartu dengan progress bar. Putuskan apakah *badge* dipakai pada baris makanan (rekomendasi) dan kartu pada ringkasan.
5. **Tailwind via CDN** dan **gambar dari URL eksternal** tidak layak untuk produksi (lihat Bagian 14 dan 17).
6. **Hanya tiga waktu makan.** Belum ada **Camilan**. Rekomendasi: tambahkan sebagai opsi (Should), karena banyak pengguna mengonsumsi camilan di antara waktu makan.
7. **Label "Besok"** pada date switcher menyiratkan fitur perencanaan menu; pastikan tujuannya jelas (rencana vs. catatan nyata).
8. **Kartu "Pindai Makanan Cepat"** menyebut "Kamera AI & Barcode database lokal". Fitur AI berisiko dijanjikan terlalu awal; pertimbangkan teks yang menyesuaikan fitur yang benar-benar rilis di MVP.
9. **Ikon streak** memakai warna `tertiary-container` (cokelat gelap) yang sedikit keluar dari palet slate murni; pastikan disengaja.
10. **Layar yang belum ada** (Catat, Riwayat, Profil, Onboarding, Pindai, Bottom Sheet) perlu didesain untuk menghindari keputusan UI ad hoc saat pengembangan.

---

## 20. Rencana Pengujian

| Jenis Tes | Cakupan |
|---|---|
| **Unit test** | BMR/TDEE, target makro, konversi porsi, total harian, pembulatan, batas aman kalori. |
| **Test kasus tepi** | Kalori melebihi target, entri 0 kkal, porsi desimal, pindah hari/zona waktu, hapus entri terakhir, input kustom tidak valid. |
| **Uji fungsional** | Onboarding → catat → ubah → hapus → ganti hari → target ulang. |
| **Uji offline** | Catat tanpa internet, sinkron saat kembali online, tanpa duplikasi. |
| **Uji responsif** | 360 px, 390 px, 768 px, 1024 px, 1440 px; orientasi lanskap. |
| **Uji aksesibilitas** | Lighthouse/axe, *screen reader* (TalkBack/VoiceOver), navigasi keyboard, kontras. |
| **Uji lintas browser** | Chrome Android, Safari iOS, Chrome/Edge/Firefox desktop. |
| **Uji kegunaan** | 5–8 pengguna dari persona berbeda; ukur waktu mencatat satu makanan. |

**Contoh kasus uji perhitungan**

| Input | Hasil yang Diharapkan |
|---|---|
| Pria, 25 th, 170 cm, 65 kg, aktivitas sedang, jaga berat | BMR = 1.592,5 kkal; TDEE ≈ 2.468 kkal (1.592,5 × 1,55) |
| Nasi merah 150 g (K 35, P 3,5, L 1,2) | 165 kkal pada tampilan (sesuai data) |
| Total 1.420 dari target 2.100 | Sisa 680 kkal; ring terisi ≈ 67,6% |
| Karbo 185 g dari target 250 g | 74% |
| Kalori 2.300 dari target 2.100 | Chip "Lebih 200 kkal"; ring penuh |

---

## 21. Kriteria Penerimaan MVP (Definition of Done)

- [ ] Seluruh kebutuhan berprioritas **Must** terpenuhi.
- [ ] Layar Harian sesuai prototipe dan design system (token warna, tipografi, radius, elevasi).
- [ ] Semua total dihitung dari entri; tidak ada angka statis.
- [ ] Layar Catat, Profil, dan Onboarding sudah didesain dan diimplementasikan.
- [ ] Aplikasi dapat dipasang sebagai PWA dan mencatat saat offline.
- [ ] Skor Lighthouse: Performance ≥ 90, Accessibility ≥ 95.
- [ ] Zoom pengguna diaktifkan; kontras memenuhi WCAG AA.
- [ ] Disclaimer kesehatan dan kebijakan privasi tersedia, serta fitur hapus akun/data berfungsi.
- [ ] Minimal ± 1.000 makanan Indonesia tersedia dengan sumber dan lisensi yang jelas.
- [ ] Tidak ada ketergantungan produksi pada CDN Tailwind atau gambar eksternal sementara.

---

## 22. Disclaimer Produk (Teks Wajib di Aplikasi)

> NutriCalc memberikan **perkiraan** kebutuhan dan asupan gizi untuk tujuan informasi umum, dan bukan pengganti saran medis atau ahli gizi profesional. Jika Anda berusia di bawah 18 tahun, sedang hamil atau menyusui, memiliki kondisi medis, atau riwayat gangguan makan, konsultasikan dengan tenaga kesehatan sebelum mengubah pola makan.

---

## 23. Pertanyaan Terbuka

1. Apakah aplikasi akan **gratis penuh**, berbasis iklan, atau memakai model langganan (fitur AI/ekspor)?
2. Apakah perlu **Camilan** sebagai waktu makan keempat pada MVP?
3. Apa definisi resmi **streak**: minimal 1 entri per hari, atau minimal mencapai persentase kalori tertentu?
4. Apakah "Besok" untuk perencanaan menu, dan apakah entri masa depan dihitung dalam statistik?
5. Sumber foto makanan: dibuat sendiri, berlisensi, atau tanpa foto pada MVP?
6. Apakah **mode tamu** cukup untuk MVP, atau akun wajib sejak awal?
7. Apakah data gizi akan dikurasi/diverifikasi tim, atau terbuka dikontribusikan pengguna?
8. Platform pengembangan: apakah tim memilih framework tertentu (React, Vue, Svelte, atau JavaScript murni)?

---

## 24. Riwayat Revisi

| Versi | Tanggal | Perubahan |
|---|---|---|
| 1.0 | 20 Okt 2026 | Draft awal PRD berdasarkan `DESIGN.md` dan `code.html` |

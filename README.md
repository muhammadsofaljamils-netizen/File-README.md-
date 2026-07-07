# File-README.md-
File README.md 
# ☕ Sofi Coffee Shop — Website E-Commerce

Prototype website e-commerce untuk bisnis kedai kopi specialty **Sofi Coffee Shop**, dibangun sebagai proyek akhir mata kuliah **KAIT II — Program Studi Administrasi Bisnis, Semester Genap 2025/2026**.

- **Live Website:** *(https://muhammadsofaljamils-netizen.github.io/UAS-KAIT-Repository-Github-2/)*
- **Repository:** *(https://github.com/muhammadsofaljamils-netizen/UAS-KAIT-Repository-Github-2.git)*
- **Dibuat oleh:** *(Muhammad sofal jamil/209250218)*

---

## 1. Business Overview

### 1.1 Nama Bisnis & Deskripsi
**Sofi Coffee Shop** adalah kedai kopi specialty yang menjual kopi single-origin, minuman berbasis susu, teh, dan pastry segar. Sofi Coffee Shop menyasar konsumen urban yang menginginkan kopi berkualitas kafe dengan kemudahan pemesanan online.

### 1.2 Value Proposition
- Kopi specialty grade dengan harga terjangkau (Rp22.000–Rp45.000/item)
- Kemudahan pemesanan online: filter, pencarian, dan checkout dalam satu alur yang sederhana
- Transparansi rating & ulasan pelanggan pada setiap produk
- Beragam pilihan metode pembayaran (COD, transfer bank, virtual account, QRIS)

### 1.3 Target Market & Segmentasi Pelanggan
| Segmen | Karakteristik |
|---|---|
| Mahasiswa & pekerja muda (18–30 tahun) | Sensitif harga, aktif di media sosial, terbiasa belanja online |
| Pekerja kantoran (25–40 tahun) | Butuh kopi cepat & konsisten, memesan lewat gadget |
| Coffee enthusiast | Mencari variasi rasa (cold brew, nitro, single-origin), peduli kualitas biji kopi |

### 1.4 Analisis Pasar Singkat & Kompetitor
Industri kedai kopi specialty di Indonesia tumbuh pesat seiring naiknya gaya hidup "ngopi" dan digitalisasi UMKM F&B. Kompetitor langsung mencakup jaringan kedai kopi lokal skala menengah (mis. Kopi Kenangan, Fore Coffee, Janji Jiwa) yang unggul di jaringan outlet fisik dan aplikasi mobile. Diferensiasi Sofi Coffee Shop terletak pada kurasi menu specialty (single-origin, nitro cold brew, matcha ceremonial grade) serta pengalaman belanja web yang ringan tanpa perlu instal aplikasi.

### 1.5 Strategi Manajemen Produk & Katalog
Katalog dibagi menjadi 6 kategori agar mudah difilter pelanggan:
1. **Espresso** — Espresso Classico, Double Americano, Affogato
2. **Latte** — Caramel Macchiato, Vanilla Latte
3. **Cold Brew** — Cold Brew Original, Nitro Cold Brew
4. **Frappe** — Mocha Frappe, Cookies & Cream Frappe, Caramel Frappe
5. **Tea** — Matcha Latte, Chai Tea Latte, Earl Grey Milk Tea
6. **Pastry** — Croissant Butter, Tiramisu Cake, Brownies Cokelat

Setiap produk dilengkapi nama menarik, deskripsi sensorik (aroma, rasa, tekstur), harga, rating, jumlah terjual, stok, dan gambar — total **16 produk** aktif di katalog (melebihi syarat minimal 8–10).

### 1.6 Model Bisnis & Revenue Stream
- **Direct sales**: penjualan langsung produk kopi & pastry melalui website (model utama)
- **Upselling**: rekomendasi pastry/frappe sebagai pelengkap saat checkout
- **Loyalty potential**: data pembelian berulang (`sold count`) dapat dikembangkan menjadi program membership/poin di iterasi berikutnya

### 1.7 Strategi Harga, Promosi, dan Diskon
- **Penetration pricing** untuk kategori Espresso (Rp22.000–25.000) guna menarik pelanggan baru
- **Value-based pricing** untuk menu premium seperti Tiramisu Cake dan Nitro Cold Brew
- Banner promo "Diskon 50% Pelanggan Baru" di homepage sebagai strategi akuisisi pelanggan pertama
- Promo musiman dapat ditambahkan melalui banner carousel yang sudah mendukung multi-slide

### 1.8 Proses Checkout & Simulasi Payment Gateway
Alur checkout: **Keranjang → Isi Data Pengiriman → Pilih Metode Pembayaran → Konfirmasi Pesanan**.

Metode pembayaran yang disimulasikan (dummy, tanpa transaksi nyata):
- **COD** (Cash on Delivery)
- **Transfer Bank** manual (BRI)
- **Virtual Account** — mensimulasikan integrasi payment gateway seperti **Midtrans/Xendit**, di mana pada implementasi produksi nomor VA akan digenerate otomatis oleh API gateway tersebut
- **QRIS** — simulasi pemindaian kode QR untuk pembayaran instan

Validasi form dilakukan di sisi client (nama, alamat, nomor HP, metode pembayaran wajib diisi) sebelum pesanan dapat diproses.

### 1.9 Rencana SEO, Keamanan, dan Pemeliharaan
**SEO:**
- Meta tag deskriptif, struktur heading semantik (H1–H3), alt text pada gambar produk
- URL bersih via GitHub Pages, sitemap sederhana untuk indexing

**Keamanan:**
- Validasi input di sisi client untuk mencegah data kosong/tidak valid
- Pada implementasi produksi nyata: transaksi pembayaran wajib diproses lewat payment gateway tersertifikasi PCI-DSS (Midtrans/Xendit), bukan disimpan sendiri, dan seluruh koneksi menggunakan HTTPS
- Data pengguna disimpan di `localStorage` untuk keperluan prototype (bukan untuk data sensitif produksi)

**Pemeliharaan:**
- Update katalog produk & harga secara berkala melalui admin dashboard bawaan
- Monitoring bug dan feedback pengguna lewat fitur ulasan produk

### 1.10 Rencana Penggunaan Data Analytics
Website ini terintegrasi dengan **Google Analytics 4 (dummy)** — lihat komentar pada `index.html`. Metrik yang dipantau:
- **Bounce rate** → evaluasi daya tarik halaman utama/banner
- **Conversion rate** (checkout selesai / total sesi) → efektivitas funnel penjualan
- **Add-to-cart rate** → indikator ketertarikan terhadap produk & harga tertentu
- **Average session duration & pages/session** → tingkat engagement terhadap katalog
- **Traffic source** → efektivitas kanal promosi (organik, sosial media, direct)

Data ini akan digunakan untuk keputusan bisnis, misalnya: menaikkan stok produk dengan add-to-cart rate tinggi, merevisi harga produk dengan bounce rate tinggi di halaman detail, atau mengalokasikan budget promosi ke kanal traffic paling efektif.

---

## 2. Dokumentasi Teknis

### 2.1 Struktur Folder
```
sofi-coffee-shop/
├── index.html          # Halaman utama (struktur + integrasi GA)
├── css/
│   └── style.css       # Seluruh custom CSS (di luar utility Tailwind)
├── js/
│   └── script.js        # Logic aplikasi: state, cart, filter, checkout, admin
├── images/              # (opsional) aset gambar lokal jika tidak memakai URL eksternal
└── README.md            # Dokumentasi ini
```

### 2.2 Fitur Teknis
- **Responsive design** — mobile, tablet, desktop (Tailwind CSS + custom media query)
- **Navbar + Hero Banner** dengan carousel promo otomatis
- **Katalog produk** (16 item, 6 kategori) dengan filter kategori, pencarian nama/kategori, dan sort (populer, harga, rating, terbaru)
- **Detail produk** dalam bentuk modal, lengkap dengan rating & ulasan
- **Keranjang belanja**: tambah, ubah kuantitas, hapus, total otomatis — tersimpan di `localStorage`
- **Wishlist** produk tersimpan per pengguna
- **Checkout**: form data diri + simulasi metode pembayaran + validasi
- **Dashboard Admin**: kelola produk & lihat riwayat pesanan
- **Autentikasi dummy** (login/register tersimpan di `localStorage`)
- **Google Analytics 4 (dummy)** dengan custom event tracking (`view_item`, `add_to_cart`, `begin_checkout`)

### 2.3 Teknologi
- **HTML5** untuk struktur halaman
- **Tailwind CSS (CDN)** dipakai untuk mempercepat styling utility (spacing, grid, flex, warna) — dijelaskan penggunaannya karena mengurangi CSS berulang untuk desain responsif kompleks; kombinasi Flexbox/Grid custom tetap ditulis manual di `css/style.css` untuk komponen animasi & tema warna kopi
- **JavaScript (Vanilla ES6+)** untuk seluruh interaktivitas (tanpa framework)
- **Font Awesome** untuk ikon, **Google Fonts** (Playfair Display & Poppins) untuk tipografi


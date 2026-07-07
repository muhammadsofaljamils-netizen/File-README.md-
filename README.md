# File-README.md-
File README.md 
1.	Link Repository GitHub
https://github.com/muhammadsofaljamils-netizen/UAS-KAIT-Repository-Github-3.git
2.	Link GitHub Pages (live website)
https://muhammadsofaljamils-netizen.github.io/UAS-KAIT-Repository-Github-3/

# ☕ Sofi Coffee Shop — Web Application

Aplikasi web e-commerce single-page untuk coffee shop, mencakup katalog produk, keranjang belanja, checkout, sistem akun pelanggan, ulasan produk, dan dashboard admin — seluruhnya berjalan di satu file `index.html` tanpa backend server.

---

## Daftar Isi

1. [Ringkasan Bisnis](#1-ringkasan-bisnis)
2. [Target Pengguna & Proposisi Nilai](#2-target-pengguna--proposisi-nilai)
3. [Fitur Produk (Business View)](#3-fitur-produk-business-view)
4. [Alur Pengguna (User Journey)](#4-alur-pengguna-user-journey)
5. [Model Monetisasi & Kalkulasi Biaya](#5-model-monetisasi--kalkulasi-biaya)
6. [Ringkasan Teknis](#6-ringkasan-teknis)
7. [Arsitektur Aplikasi](#7-arsitektur-aplikasi)
8. [Struktur Data](#8-struktur-data)
9. [Peta Fungsi JavaScript](#9-peta-fungsi-javascript)
10. [Penyimpanan Data (localStorage)](#10-penyimpanan-data-localstorage)
11. [Cara Menjalankan](#11-cara-menjalankan)
12. [Keterbatasan & Risiko (Penting)](#12-keterbatasan--risiko-penting)
13. [Rekomendasi Jalur Produksi](#13-rekomendasi-jalur-produksi)
14. [Struktur File](#14-struktur-file)
15. [Lisensi Aset](#15-lisensi-aset)

---

## 1. Ringkasan Bisnis

**Sofi Coffee Shop** adalah etalase digital (digital storefront) bagi bisnis kedai kopi untuk memajang menu, menerima pesanan online, dan membangun interaksi dengan pelanggan (wishlist, ulasan, akun member) — tanpa harus bergantung pada marketplace pihak ketiga.

Tujuan bisnis utama dari aplikasi ini:

- **Kanal pemesanan mandiri (direct-to-consumer)** — pelanggan memesan langsung dari brand, bukan lewat marketplace yang memotong komisi.
- **Etalase menu digital yang menarik** — foto produk, rating, jumlah terjual, dan deskripsi yang membangun kepercayaan (social proof).
- **Mengurangi gesekan pemesanan** — kategori, pencarian, dan sorting membantu pelanggan menemukan menu dengan cepat.
- **Data pelanggan awal** — akun member sederhana menjadi pondasi program loyalitas di masa depan.
- **Alat operasional kasar (dashboard admin)** — pemilik bisa menambah/mengubah/menghapus produk dan memantau pesanan tanpa alat tambahan.

> **Catatan penting:** Ini adalah **prototipe / MVP front-end**. Belum ada server, database, payment gateway, atau autentikasi nyata. Lihat [Bagian 12](#12-keterbatasan--risiko-penting) sebelum digunakan untuk transaksi sungguhan.

---

## 2. Target Pengguna & Proposisi Nilai

| Segmen | Kebutuhan | Bagaimana Aplikasi Menjawabnya |
|---|---|---|
| Pelanggan kedai kopi (B2C) | Melihat menu, harga, promo, memesan cepat | Katalog, filter kategori, pencarian real-time, keranjang, checkout |
| Pelanggan berulang | Menyimpan menu favorit, cek riwayat pesanan | Wishlist, akun member (data terisi otomatis saat checkout) |
| Pemilik/pengelola kedai (owner/admin) | Mengelola menu tanpa developer, memantau penjualan | Dashboard Admin (CRUD produk, statistik, riwayat pesanan) |
| Kasir/tim operasional | Menerima notifikasi pesanan & bukti pembayaran | Order diarahkan konfirmasi via WhatsApp |

**Proposisi nilai:** "Toko kopi online siap pakai, tanpa biaya komisi marketplace, tanpa perlu tim IT — cukup satu file HTML yang bisa langsung dihosting."

---

## 3. Fitur Produk (Business View)

### 🏠 Halaman Utama (Landing)
- Banner promo carousel otomatis (auto-slide 5 detik + swipe touch di mobile), berisi 3 kampanye contoh: diskon 50% pelanggan baru, gratis ongkir, dan promo beli 2 gratis 1.
- Blok "keunggulan" (gratis ongkir, pembayaran aman, bahan premium, same-day delivery) untuk membangun kepercayaan.
- Section "Tentang Kami" dengan foto, deskripsi brand, dan statistik sosial (jumlah menu, pelanggan, rating).
- Tombol **Chat via WhatsApp** langsung terhubung ke nomor kedai — kanal komunikasi cepat tanpa perlu live chat kustom.

###  Katalog & Pencarian
- 16 produk contoh dalam 6 kategori: Espresso, Latte, Cold Brew, Frappe, Pastry, Tea.
- Pencarian real-time (debounce 300ms) di desktop & mobile, disinkronkan otomatis antar kedua input.
- Sorting: Terpopuler, Harga Terendah/Tertinggi, Rating Tertinggi, Terbaru.
- Tampilan kartu produk menampilkan rating bintang, jumlah terjual, harga, tombol tambah cepat ke keranjang, dan tombol wishlist (ikon hati).

### Detail Produk & Ulasan
- Modal detail produk: galeri foto, harga, stok tersedia, deskripsi lengkap.
- Sistem ulasan pembeli dengan rating bintang (1–5) — pelanggan yang sudah login bisa menulis ulasan sendiri.
- Ulasan awal dibuat otomatis secara acak (simulasi data) agar tampilan produk baru tidak terlihat kosong.

### Wishlist
- Simpan produk favorit dengan satu klik, terpisah dari keranjang belanja.

### Keranjang & Checkout
- Sidebar keranjang belanja dengan kontrol kuantitas (+/–), subtotal otomatis.
- Halaman checkout dengan:
  - Form pengiriman (nama, telepon, alamat, catatan) + validasi input.
  - 4 metode pembayaran: **COD**, **Transfer Bank BRI** (nomor rekening + tombol salin), **Virtual Account BRI**, **QRIS** (kode QR statis).
  - Rincian biaya otomatis: subtotal, ongkos kirim (gratis di atas Rp 50.000, jika tidak Rp 10.000), biaya layanan 3%, dan total.
  - Nomor pesanan unik dibuat otomatis (format `SC-XXXXXX`).

### Akun Pelanggan
- Login & registrasi sederhana (tab switch dalam satu modal).
- Data akun (nama, email) otomatis mengisi form checkout pada kunjungan berikutnya.

### Dashboard Admin
- Statistik ringkas: total produk, total pesanan, total pendapatan, rata-rata rating.
- Tabel kelola produk: tambah, edit, dan hapus produk (dengan konfirmasi sebelum hapus).
- Riwayat seluruh pesanan yang masuk.

---

## 4. Alur Pengguna (User Journey)

```
Pelanggan Baru:
Buka Situs → Lihat Banner Promo → Jelajah/Cari Menu → Buka Detail Produk
   → Tambah ke Keranjang → Klik Checkout → Diminta Login/Daftar
   → Isi Data Pengiriman → Pilih Metode Pembayaran → Buat Pesanan
   → (Jika transfer/VA/QRIS) Konfirmasi via WhatsApp dengan bukti bayar

Pemilik/Admin:
Login → Buka Dashboard Admin → Pantau Statistik Penjualan
   → Tambah/Update Menu Baru → Cek Riwayat Pesanan Masuk
```

---

## 5. Model Monetisasi & Kalkulasi Biaya

Logika biaya yang sudah tertanam di kode (`renderCheckout()` / `placeOrder()`):

| Komponen | Aturan |
|---|---|
| Ongkos kirim | Rp 0 jika subtotal ≥ Rp 50.000, jika tidak Rp 10.000 |
| Biaya layanan | 3% dari subtotal |
| Total | Subtotal + Ongkos Kirim + Biaya Layanan |

> Angka-angka ini adalah **konstanta hardcode** di dalam kode (`50000`, `10000`, `0.03`) — cocok untuk demo, tetapi untuk operasional nyata sebaiknya dipindahkan ke pengaturan yang bisa diubah admin (lihat [Bagian 13](#13-rekomendasi-jalur-produksi)).

---

## 6. Ringkasan Teknis

| Aspek | Detail |
|---|---|
| Jenis aplikasi | Single Page Application (SPA), 1 file HTML |
| Bahasa | HTML5, CSS (Tailwind via CDN), JavaScript (vanilla, ES6+) |
| Framework | Tidak ada — DOM dimanipulasi langsung via `innerHTML` & helper `$`/`$$` |
| Styling | Tailwind CSS (CDN, dikonfigurasi inline via `tailwind.config`), custom CSS variables |
| Font & Ikon | Google Fonts (Playfair Display, Poppins), Font Awesome 6.5.0 (CDN) |
| Penyimpanan data | `localStorage` browser (tidak ada database/server) |
| Autentikasi | Simulasi lokal — tanpa validasi password sungguhan, tanpa server |
| Pembayaran | Tampilan statis (rekening, VA, QR) — **tidak ada integrasi payment gateway nyata** |
| Ketergantungan eksternal | CDN Tailwind, Font Awesome, Google Fonts, QR generator (`api.qrserver.com`), gambar dari Wikimedia Commons |
| Hosting | Statis — bisa dihost di mana saja yang menyajikan file HTML (Netlify, Vercel, GitHub Pages, S3, dll.) |

---

## 7. Arsitektur Aplikasi

Karena ini murni front-end, arsitekturnya berbasis **state management manual** dan **render-on-demand**:

```
┌─────────────────────────────────────────────┐
│                index.html                    │
│                                               │
│  <head>  → Tailwind config + custom CSS       │
│  <body>                                       │
│   ├─ <header>        → Nav, search, cart icon │
│   ├─ #page-home       (data-page)             │
│   ├─ #page-checkout   (data-page)             │
│   ├─ #page-admin      (data-page)             │
│   ├─ #cartSidebar     (drawer)                │
│   ├─ #productModal    (modal detail produk)   │
│   ├─ #authModal       (modal login/daftar)    │
│   ├─ #adminModal      (modal tambah/edit)     │
│   └─ #toastContainer  (notifikasi)            │
│                                               │
│  <script>                                     │
│   ├─ Data statis: CATEGORIES, products[]      │
│   ├─ state {}         → single source of truth│
│   ├─ Fungsi render*() → re-render DOM dari    │
│   │                     state saat dipanggil  │
│   ├─ Fungsi save*()   → sinkron ke localStorage│
│   └─ init()           → titik masuk aplikasi  │
└─────────────────────────────────────────────┘
```

**Pola navigasi (routing tanpa framework):**
Semua "halaman" (`#page-home`, `#page-checkout`, `#page-admin`) ada di DOM yang sama; fungsi `navigate(page)` hanya menyembunyikan/menampilkan elemen `[data-page]` yang relevan (bukan routing URL sungguhan — tidak ada perubahan URL/history browser).

**Pola render:**
Tidak ada Virtual DOM. Setiap kali state berubah (misalnya tambah ke keranjang), fungsi terkait (`renderProducts`, `renderCartItems`, `renderCheckout`, `renderAdmin`, dst.) membangun ulang `innerHTML` dari template string secara langsung.

---

## 8. Struktur Data

### `products` (array, in-memory, **tidak persisten**)
```js
{
  id: number,
  name: string,
  price: number,       // dalam Rupiah
  category: string,     // salah satu dari id CATEGORIES
  rating: number,
  sold: number,
  stock: number,
  image: string,        // URL gambar (Wikimedia Commons)
  desc: string
}
```
> Perubahan produk lewat dashboard admin (tambah/edit/hapus) **hilang saat halaman di-refresh**, karena `products` hanya variabel JavaScript biasa, bukan disimpan ke `localStorage`.

### `state` (object global, sumber kebenaran aplikasi)
```js
state = {
  cart: [],       // [{id, qty}], persisten di localStorage
  wishlist: [],   // [id, id, ...], persisten
  user: null,     // {name, email, phone, address} atau null, persisten
  orders: [],     // riwayat pesanan, persisten
  reviews: {},    // {productId: [{name, rating, text, date}]}, persisten
  category: 'all',
  search: '',
  sort: 'popular',
  currentPage: 'home'
}
```

### `order` (dibuat saat checkout, disimpan ke `state.orders`)
```js
{
  id: 'SC-XXXXXX',
  items: [{name, qty, price, subtotal}],
  name, phone, address, notes,
  payment: 'cod' | 'transfer' | 'va' | 'qris',
  subtotal, shipping, service, total,
  date: string,
  status: 'Diproses'
}
```

---

## 9. Peta Fungsi JavaScript

Kode berisi ±58 fungsi. Dikelompokkan berdasarkan tanggung jawab:

| Kategori | Fungsi Utama |
|---|---|
| Navigasi & UI umum | `navigate()`, `toast()`, `toggleMobileSearch()`, `toggleUserDrop()` |
| Kategori & filter | `renderCatBar()`, `filterCategory()`, `applyFilters()`, `doSearch()` |
| Produk | `renderProducts()`, `openProduct()`, `closeProduct()`, `renderStars()` |
| Ulasan | `generateReviews()`, `addReviewForm()`, `submitReview()` |
| Wishlist | `toggleWish()`, `showWishlistPage()` |
| Keranjang | `addToCart()`, `updateCartQty()`, `removeFromCart()`, `renderCartItems()`, `toggleCart()`, `getCartSubtotal()`, `updateCartUI()` |
| Checkout & pesanan | `goCheckout()`, `renderCheckout()`, `updatePaymentDetail()`, `copyText()`, `placeOrder()`, `showErr()`/`hideErr()` |
| Autentikasi | `openAuth()`, `closeAuth()`, `switchAuthTab()`, `doLogin()`, `doRegister()`, `doLogout()`, `updateUserUI()` |
| Admin | `renderAdmin()`, `openAddProduct()`, `editProduct()`, `saveProduct()`, `deleteProduct()`, `openAdminModal()`, `closeAdminModal()` |
| Banner carousel | `initBanner()`, `goToBanner()`, `nextBanner()`, `startBannerAutoplay()`, `resetBannerAutoplay()` |
| Persistensi | `saveCart()`, `saveWish()`, `saveUser()`, `saveOrders()`, `saveReviews()` |
| Inisialisasi | `init()` — dipanggil sekali di akhir script |

---

## 10. Penyimpanan Data (localStorage)

| Key | Isi |
|---|---|
| `sofi-cart` | Array item keranjang `[{id, qty}]` |
| `sofi-wish` | Array ID produk yang di-wishlist |
| `sofi-user` | Objek user yang sedang login (atau tidak ada key jika logout) |
| `sofi-orders` | Array seluruh riwayat pesanan |
| `sofi-reviews` | Objek ulasan per ID produk |

**Implikasi:** Data ini **per-browser, per-perangkat**. Tidak ada sinkronisasi lintas perangkat, tidak bisa diakses admin dari komputer lain, dan akan hilang jika pengguna membersihkan cache/localStorage browser.

---

## 11. Cara Menjalankan

Karena tidak ada dependensi build atau server-side:

1. Unduh/salin file `index.html`.
2. Buka langsung di browser (double-click), **atau**
3. Jalankan local server sederhana (disarankan agar semua fitur browser bekerja normal):
   ```bash
   # Python
   python3 -m http.server 8000
   # lalu buka http://localhost:8000
   ```
4. Untuk publikasi publik: unggah `index.html` ke hosting statis apa pun — Netlify, Vercel, GitHub Pages, Cloudflare Pages, atau bucket S3 dengan static hosting.

Tidak ada langkah instalasi package (`npm install`) karena semua library (Tailwind, Font Awesome, Google Fonts) dimuat lewat CDN di dalam `<head>`.

---

## 12. Keterbatasan & Risiko (Penting)

Sebelum digunakan untuk bisnis nyata, pahami batasan berikut:

1. **Bukan sistem pembayaran nyata.** Nomor rekening, VA, dan QRIS bersifat statis/tampilan saja. Tidak ada verifikasi otomatis bahwa pembayaran benar-benar masuk — konfirmasi manual via WhatsApp.
2. **Bukan sistem autentikasi aman.** `doLogin()` menerima email & password apa pun tanpa validasi ke server — siapa pun bisa "login" dengan data apa pun. Jangan gunakan untuk data sensitif.
3. **Tidak ada database.** Semua data (produk, pesanan, ulasan) tersimpan di `localStorage` browser pengguna masing-masing — tidak terpusat, tidak bisa dilihat lintas perangkat, dan hilang jika cache dibersihkan.
4. **Perubahan produk oleh admin tidak persisten.** Array `products` hanya ada di memori JavaScript; refresh halaman mengembalikan ke data awal.
5. **Dashboard admin tidak dilindungi hak akses.** Siapa pun yang login otomatis bisa mengakses menu "Dashboard Admin" — tidak ada pemisahan role admin vs pelanggan biasa di level sistem.
6. **Ketergantungan pada CDN pihak ketiga.** Tailwind, Font Awesome, Google Fonts, dan generator QR code (`api.qrserver.com`) semuanya dimuat dari internet — aplikasi tidak akan tampil benar jika salah satu CDN down atau diblokir jaringan.
7. **Gambar produk dari Wikimedia Commons.** Cocok untuk demo, tetapi untuk brand asli sebaiknya diganti foto produk asli milik bisnis.

---

## 13. Rekomendasi Jalur Produksi

Jika aplikasi ini ingin dikembangkan menjadi produk bisnis sungguhan, langkah-langkah berikut disarankan secara bertahap:

| Area | Rekomendasi |
|---|---|
| Backend & Database | Tambahkan backend (mis. Node.js/Express, atau BaaS seperti Supabase/Firebase) untuk menyimpan produk, pesanan, dan pengguna secara terpusat |
| Autentikasi | Gunakan sistem auth sungguhan (hashing password, JWT/session, atau layanan seperti Auth0/Firebase Auth) |
| Pembayaran | Integrasikan payment gateway resmi (Midtrans, Xendit, DOKU, dll.) untuk verifikasi transaksi otomatis, bukan QR/VA statis |
| Otorisasi Admin | Tambahkan role-based access control agar hanya akun admin yang bisa mengakses dashboard |
| Manajemen produk | Simpan produk di database, dengan upload gambar ke storage (S3/Cloud Storage) |
| Notifikasi pesanan | Kirim notifikasi otomatis (email/WhatsApp API resmi) saat pesanan masuk, bukan manual |
| Konfigurasi bisnis | Pindahkan angka ongkos kirim, ambang batas gratis ongkir, dan biaya layanan ke pengaturan yang bisa diubah admin |
| Aset statis | Ganti gambar Wikimedia dengan foto produk asli; host font/ikon secara lokal untuk mengurangi ketergantungan CDN |
| SEO & Analytics | Tambahkan meta tag SEO, sitemap, dan integrasi Google Analytics/Meta Pixel |

---

## 14. Struktur File

```
index.html      # Seluruh aplikasi: markup, style (Tailwind config + custom CSS), dan logic JS
```

Aplikasi ini sengaja dibuat sebagai **single-file** untuk kemudahan demo/prototyping — bukan struktur proyek multi-file yang lazim di aplikasi produksi.

---

## 15. Lisensi Aset

- **Font Awesome 6.5.0** — dimuat via CDN cdnjs, mengikuti lisensi Font Awesome Free.
- **Google Fonts** (Playfair Display, Poppins) — lisensi Open Font License / Apache.
- **Tailwind CSS** — dimuat via CDN Play, MIT License.
- **Gambar produk** — bersumber dari Wikimedia Commons; periksa lisensi masing-masing gambar sebelum penggunaan komersial nyata, dan pertimbangkan mengganti dengan foto produk asli milik brand.

---





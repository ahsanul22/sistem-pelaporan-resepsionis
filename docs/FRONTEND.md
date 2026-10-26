# Spesifikasi Visual Awal

Spesifikasi ini proposal untuk eksplorasi tahap frontend. Ini bukan keputusan brand atau implementasi UI final. Konfirmasi dengan mentor/pengguna sebelum membangun layout penuh.

## Arah visual

Antarmuka internal yang tenang, jelas, tepercaya, dan berorientasi tugas. Prioritaskan keterbacaan dan kecepatan pencatatan di meja resepsionis. Hindari dekorasi yang menyaingi informasi operasional. Bahasa antarmuka awal diasumsikan Bahasa Indonesia, perlu dikonfirmasi.

## Rencana warna dan semantic tokens

Gunakan token semantik agar warna dapat diubah terpusat. Nilai berikut adalah arah awal, bukan palet yang disetujui:

| Token | Rencana penggunaan | Arah awal |
| --- | --- | --- |
| `brand` | Aksi utama, tautan aktif, identitas | Biru tua/teal institusional; konfirmasi brand resmi |
| `surface` | Latar halaman dan panel | Putih dan abu-abu sangat muda |
| `text` | Teks utama/sekunder | Abu-abu gelap dengan kontras tinggi |
| `border` | Pembatas, garis tabel, input | Abu-abu netral yang tetap terlihat |
| `success` | Berhasil/selesai | Hijau dengan label tekstual |
| `warning` | Menunggu/perlu perhatian | Amber dengan label tekstual |
| `danger` | Gagal/aksi berisiko | Merah dengan label tekstual |
| `info` | Informasi umum | Biru/cyan dengan label tekstual |

Tetapkan nilai hex dan cek kontras saat visual identity dan komponen final ditinjau. Jangan menyandikan makna status dengan warna saja.

## Tipografi

Gunakan system sans-serif yang tersedia untuk memulai, hierarki ringkas (judul halaman, subjudul, isi, label, metadata), dan ukuran yang nyaman dibaca. Font brand, ukuran final, dan aturan angka/tanggal perlu dikonfirmasi. Angka tabel dan timestamp harus mudah dipindai.

## Layout dashboard dan sidebar

- Desktop: sidebar navigasi stabil, header ringkas berisi judul/konteks akun, area konten dengan lebar dan jarak yang konsisten.
- Dashboard: tampilkan ringkasan kerja yang relevan dan tautan ke tugas umum; angka dan metrik harus berasal dari backend serta sudah disepakati.
- Jangan mengisi dashboard dengan chart atau KPI hanya untuk dekorasi.
- Sidebar menampilkan hanya tujuan yang pengguna berhak akses; pemeriksaan server tetap wajib.

## Pola tabel, form, filter, status, notifikasi

- Tabel untuk daftar yang perlu dipindai: kolom utama, tanggal, status, unit/penanggung jawab bila relevan, dan aksi yang diizinkan. Pada mobile prioritaskan informasi inti.
- Form dibuat untuk input cepat, dengan field kondisional hanya bila alur kategori memerlukannya. Konfirmasi field dan urutannya melalui observasi pengguna.
- Filter menyediakan pencarian, rentang waktu, kategori, unit, atau status hanya jika tersedia dan memang berguna. Tampilkan filter aktif.
- Status badge memakai kosa kata status yang disepakati, label teks, dan warna semantik.
- Feedback sukses/error dekat aksi atau konten terkait; konfirmasi aksi berdampak besar dan jangan mengandalkan toast yang cepat hilang.

## Navigasi responsif

- Desktop memakai sidebar yang dapat dipahami dan tidak terlalu padat.
- Tablet mempertahankan label navigasi atau menyediakan cara jelas untuk mengungkapnya.
- Mobile menggunakan menu tombol dengan nama aksesibel, fokus dikelola, dan konten mudah dicapai. Navigasi utama dan aksi pencatatan umum tetap mudah ditemukan.
- Hindari pola hover-only; semua navigasi mendukung keyboard dan sentuhan.

## Referensi visual untuk ditelusuri

Pada tahap frontend, kumpulkan dan tinjau bersama pemilik produk:

- Brand guideline/logo dan palet resmi organisasi.
- Aplikasi internal organisasi yang sudah digunakan, khususnya pola navigasi, tanggal/waktu, dan aksesibilitas.
- Contoh dashboard operasional dan daftar kerja yang padat namun mudah dipindai.
- Konteks nyata meja kerja: ukuran monitor, penggunaan tablet/ponsel, pencahayaan, dan konektivitas.

Jangan menyalin visual produk eksternal secara langsung; gunakan referensi untuk pola dan validasi kebutuhan.

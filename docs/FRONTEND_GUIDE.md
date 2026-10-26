# Panduan Frontend

Dokumen ini mengatur implementasi frontend setelah kebutuhan layar dikonfirmasi. Arah visual dan token masih usulan di `docs/FRONTEND.md`.

## Responsivitas

- Rancang mulai dari ruang kerja desktop resepsionis, lalu pastikan tablet dan mobile dapat menjalankan tugas utama.
- Pada layar sempit, ubah navigasi sidebar menjadi pola mobile yang jelas dan dapat ditutup; jangan biarkan tabel/form melebar tanpa kendali.
- Untuk tabel padat, pilih kolom prioritas, pembungkus/scroll yang teridentifikasi, atau tampilan kartu yang tetap menjaga akses ke detail.
- Uji panjang teks, zoom, dan orientasi yang realistis sebelum menyatakan layar responsif.

## Aksesibilitas dan keyboard

- Pakai elemen HTML semantik, urutan heading logis, fokus terlihat, dan navigasi keyboard tanpa jebakan fokus.
- Setiap field memiliki label yang terhubung; placeholder bukan pengganti label. Hubungkan bantuan dan error ke field terkait.
- Tombol memiliki nama aksi yang jelas. Status tidak dibedakan hanya dengan warna; sediakan teks/ikon yang dapat dipahami.
- Jaga kontras, target interaksi yang memadai, dan alternatif untuk ikon tanpa label.
- Sampaikan perubahan penting dengan feedback yang dapat dikenali pembaca layar jika interaksi dinamis digunakan.

## State antarmuka

- **Empty:** jelaskan data belum ada dan langkah berikutnya yang sah; jangan menyiratkan kegagalan.
- **Loading:** tampilkan indikator pada area yang dimuat dan cegah submit ganda bila perlu.
- **Error:** beri pesan yang dapat ditindaklanjuti, pertahankan input yang aman, tunjukkan error validasi dekat field, dan jangan tampilkan stack trace/rahasia.
- **Success:** konfirmasi aksi yang benar-benar tersimpan dan beri navigasi/aksi lanjutan yang sesuai.
- Bedakan tidak ada hasil filter dari belum ada data sama sekali.

## Konsistensi UI

- Gunakan layout, lebar konten, grid, typography, spacing, border, elevation, dan pola navigasi yang konsisten.
- Cards memberi pengelompokan yang bermakna; hindari card berlapis tanpa tujuan.
- Tabel memiliki heading kolom yang jelas, format tanggal/angka konsisten, aksi terjangkau keyboard, serta pagination saat dataset memerlukannya.
- Form dikelompokkan menurut tugas, menandai field wajib, menjelaskan format, dan menjaga urutan input yang alami.
- Filter dan pencarian menunjukkan kriteria aktif serta cara membersihkannya.
- Badge status memakai teks label konsisten dan warna semantik yang dapat diakses.
- Notifikasi tidak menutupi kontrol penting dan tetap memberi kesempatan membaca pesan.

## Komponen Blade dan data Laravel

- Gunakan Blade layout, partial, atau component untuk pola yang berulang dan stabil; jangan membuat abstraksi sebelum ada pemakaian ulang yang nyata.
- Gunakan route bernama dan data dari controller/view model. Format data di backend/presenter sesuai kebutuhan; jangan menaruh statistik bisnis atau daftar role/permission palsu sebagai konstanta frontend.
- Escape output Blade secara default. Aksi tersembunyi di UI tetap harus memiliki authorization server-side.
- Pertahankan state filter/pagination melalui query string bila sesuai.

## Batas dependency

- Gunakan Blade, Tailwind CSS, Vite, dan JavaScript yang sudah tersedia.
- Jangan menambahkan framework UI, charting, icon, atau state-management package tanpa kebutuhan terukur dan evaluasi dependency.
- Utamakan HTML/CSS dan komponen yang ada untuk interaksi sederhana; semua interaksi harus memiliki fallback/error yang wajar.

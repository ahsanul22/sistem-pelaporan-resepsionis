# Panduan kerja Codex

Dokumen ini adalah aturan kerja utama untuk Sistem Pelaporan Resepsionis. Jika implementasi aktual berbeda dari dokumen, periksa kode dan konfigurasi terlebih dahulu, lalu catat perbedaan dan usulkan pembaruan dokumentasi.

## Urutan membaca konteks

Sebelum setiap task, baca:

1. `AGENTS.md`
2. `docs/PROJECT_CONTEXT.md`
3. `docs/ROADMAP.md`
4. `docs/PROGRESS.md`
5. `docs/DECISIONS.md`

Untuk pekerjaan frontend, baca juga `docs/FRONTEND_GUIDE.md` dan `docs/FRONTEND.md`. Setelah itu periksa file implementasi yang berhubungan langsung dengan task. Jangan mengandalkan dokumentasi sebagai bukti bahwa kode sudah menerapkan sesuatu.

## Analisis sebelum perubahan

- Periksa struktur, pola, dependency, konfigurasi, route, middleware, model, migration, view, dan test yang relevan sebelum mengedit.
- Tentukan apakah task menyentuh implementasi yang sudah ada atau area baru. Pertahankan perilaku yang ada kecuali perubahan memang diperlukan oleh scope.
- Kerjakan hanya scope yang diminta. Jangan membangun modul terkait secara otomatis.
- Jangan mengganti framework, dependency, database, atau konfigurasi tanpa kebutuhan jelas dan alasan yang terdokumentasi.
- Jangan menghapus data atau menjalankan perintah destruktif tanpa izin eksplisit.
- Jika kebutuhan belum jelas, dokumentasikan pertanyaannya dan pilih pendekatan paling sederhana yang aman. Jangan menyatakan asumsi sebagai kebutuhan terkonfirmasi.

## Laravel dan struktur kode

- Ikuti konvensi Laravel 10 dan struktur repository yang telah ada. Gunakan route, controller, Form Request, model, policy/gate, middleware, Blade, dan service sesuai kebutuhan; hindari abstraksi yang belum memberi manfaat.
- Controller mengatur HTTP dan koordinasi. Pindahkan business logic yang kompleks atau digunakan ulang ke service/domain class yang sesuai.
- Pertahankan kompatibilitas PHP dari `composer.json` dan dependency terkunci. Jangan menambahkan package jika kemampuan Laravel atau dependency yang tersedia mencukupi.
- Gunakan route bernama, route model binding, pagination, dan eager loading jika sesuai dengan pola dan kebutuhan.

## Database, validasi, dan keamanan

- Skema database final harus mengikuti requirement yang telah dikonfirmasi. PostgreSQL adalah target awal yang diusulkan; konfigurasi repository saat ini masih MySQL. Jangan mengubahnya diam-diam.
- Migration harus dapat dibaca, konsisten, dan aman untuk data yang sudah ada. Jangan menjalankan reset/fresh/rollback terhadap data tanpa izin eksplisit.
- Validasi input di server melalui Form Request atau validasi Laravel yang sesuai. Jangan mempercayai validasi browser sebagai kontrol keamanan.
- Autentikasi menentukan identitas; authorization harus memeriksa izin untuk setiap aksi dan resource di server. Role saja bukan pengganti policy/gate atau pemeriksaan kepemilikan/cakupan unit.
- Pertahankan CSRF protection pada form web, escaping Blade, mass-assignment protection, hashing password, dan penanganan error yang tidak membocorkan rahasia.
- Batasi data internal sesuai kebutuhan akses. Hindari mencatat credential, data pribadi berlebihan, atau isi sensitif dalam log.

## Frontend

- Ikuti `docs/FRONTEND_GUIDE.md` dan `docs/FRONTEND.md`; nilai visual di dokumen tersebut adalah proposal sampai dikonfirmasi.
- Gunakan Blade dan Tailwind/Vite yang sudah tersedia. Buat komponen reusable saat pola berulang, tanpa membangun sistem komponen berlebihan.
- Jangan hardcode data bisnis, akun, role, permission, atau statistik di frontend. Render data yang diberikan backend dan lindungi aksi di server.
- Utamakan aksesibilitas, responsivitas, label formulir, state antarmuka, serta navigasi keyboard.
- Jangan menambahkan dependency frontend atau mengganti konfigurasi build tanpa kebutuhan yang jelas.

## Testing dan verifikasi

- Jalankan test dan verifikasi relevan terhadap perubahan yang dibuat; jangan mengklaim test berjalan jika tidak dijalankan.
- Jika verifikasi terhalang lingkungan atau konfigurasi, catat perintah dan kendala aktual. Jangan mengubah data/environment demi membuat test lulus tanpa alasan dan izin yang sesuai.
- Laporkan ringkas file/area yang berubah, verifikasi aktual, dan keterbatasan yang tersisa.

## Dokumentasi dan batas scope

- Task dokumentasi tidak memberi izin untuk membangun fitur aplikasi, schema final, atau UI lengkap.
- Setelah task selesai, perbarui `docs/PROGRESS.md` sesuai pekerjaan dan hasil verifikasi yang benar-benar terjadi.
- Perbarui `docs/DECISIONS.md` saat ada keputusan baru; tandai proposed, confirmed, atau deprecated secara akurat.
- Perbarui status `docs/ROADMAP.md` berdasarkan progres nyata. Jangan menandai implementasi yang belum ada sebagai completed.
- Jangan mengklaim pekerjaan, verifikasi, persetujuan mentor, atau kebutuhan yang belum terjadi/terkonfirmasi.

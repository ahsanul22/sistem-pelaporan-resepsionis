# Keputusan dan proposal

Status:

- **proposed**: rekomendasi awal, belum disahkan.
- **confirmed**: telah disetujui pemilik kebutuhan/mentor dan konsisten dengan implementasi.
- **deprecated**: tidak lagi berlaku; simpan alasan dan penggantinya.

Belum ada keputusan bisnis atau arsitektur yang dapat dicatat sebagai confirmed berdasarkan pemeriksaan repository dan brief ini.

## D-001 — Framework dan pola aplikasi

- **Keputusan:** Pertahankan Laravel 10, PHP sesuai `composer.json`, Blade, dan Tailwind melalui Vite yang sudah ada.
- **Alasan:** Ini stack yang diminta dan sesuai dependency/configuration repository aktual.
- **Alternatif yang dipertimbangkan:** Mengganti framework atau frontend stack; tidak ada kebutuhan yang mendukung perubahan.
- **Dampak:** Perubahan berikutnya mengikuti Laravel 10 dan dependency terkunci; perubahan stack memerlukan alasan dan persetujuan requirement.
- **Status:** proposed.

## D-002 — Database target awal

- **Keputusan:** Gunakan PostgreSQL sebagai target awal untuk perancangan, dengan verifikasi sebelum implementasi.
- **Alasan:** Brief menyebut PostgreSQL sebagai target awal.
- **Alternatif yang dipertimbangkan:** MySQL, yang saat ini tercantum dalam `.env.example`; pilihan lain berdasarkan lingkungan deployment.
- **Dampak:** Jangan membuat migration final atau mengubah konfigurasi sampai ketersediaan driver/layanan dev-test-deployment dan kebutuhan dikonfirmasi.
- **Status:** proposed.

## D-003 — Role konseptual awal

- **Keputusan:** Jadikan `super_admin`, `receptionist`, `unit_staff`, dan `management` sebagai kosa kata role untuk analisis awal saja.
- **Alasan:** Empat jenis tanggung jawab ini diajukan dalam brief.
- **Alternatif yang dipertimbangkan:** Memulai dengan role lebih sedikit atau permission granular tanpa nama role tetap; struktur final menunggu pemetaan tugas nyata.
- **Dampak:** Belum membuat kolom, seed, package, middleware role, atau akun. Role tidak memberikan akses secara otomatis; server harus memeriksa permission, aksi, dan cakupan data.
- **Status:** proposed.

## D-004 — Otorisasi server-side

- **Keputusan:** Setiap pembacaan/perubahan data harus dilindungi autentikasi dan authorization server-side yang sesuai dengan resource serta cakupan unit.
- **Alasan:** Antarmuka bukan batas keamanan dan data bersifat internal.
- **Alternatif yang dipertimbangkan:** Menyembunyikan aksi di frontend saja; tidak memadai.
- **Dampak:** Rancangan backend harus menetapkan policy/gate atau pemeriksaan setara, termasuk akses record individual.
- **Status:** proposed.

## D-005 — Remote repository proyek

- **Keputusan:** Gunakan `https://github.com/ahsanul22/sistem-pelaporan-resepsionis.git` sebagai remote bernama `origin`.
- **Alasan:** URL diberikan langsung oleh pengguna untuk menghubungkan proyek.
- **Alternatif yang dipertimbangkan:** Remote lain atau tidak memakai remote; tidak diminta.
- **Dampak:** Remote telah disetel pada repository lokal di branch `main`. Akses jaringan gagal saat dicoba, sehingga keberadaan/isi remote dan sinkronisasi belum diverifikasi. Belum ada commit atau push; periksa riwayat remote dan file yang akan dipublikasikan sebelum menyelaraskan.
- **Status:** confirmed untuk URL dan konfigurasi lokal; sinkronisasi remote belum terverifikasi.

## Matriks akses konseptual awal

Matriks ini adalah hipotesis untuk validasi, bukan grant akses final. “Terbatas” berarti hanya sesuai penugasan, unit, kebutuhan, dan izin server yang kelak disahkan. Modul dan batas baca per kategori perlu ditentukan.

| Modul/aksi | super_admin | receptionist | unit_staff | management |
| --- | --- | --- | --- | --- |
| Pengguna, role, konfigurasi | Kelola yang disetujui | Tidak ada akses admin | Tidak ada akses admin | Tidak ada akses admin |
| Master unit/kategori | Kelola master yang disetujui | Baca/pilih yang diperlukan | Baca yang relevan | Baca bila diperlukan |
| Catat aktivitas layanan | Akses dukungan terbatas, perlu konfirmasi | Buat dan kelola sesuai kewenangan | Tidak secara default; perlu konfirmasi | Tidak |
| Tamu, dokumen, pengaduan | Terbatas sesuai kebutuhan operasional dan audit | Catat/lihat sesuai tugas dan klasifikasi | Hanya item yang ditugaskan dan informasi minimum | Hanya agregat atau detail yang diizinkan |
| Penerusan/penugasan | Konfigurasi/dukungan; hak operasional perlu konfirmasi | Teruskan sesuai alur yang disahkan | Melihat tugas untuk unitnya; ubah tindak lanjut sesuai izin | Tidak mengubah; baca agregat/laporan yang diizinkan |
| Pencarian dan riwayat | Akses administratif tidak otomatis berarti semua isi; perlu batasan | Riwayat kerja sesuai kewenangan | Riwayat item/unit yang diizinkan | Laporan read-only yang diizinkan |
| Dashboard dan laporan | Operasional sesuai konfigurasi | Ringkasan kerja sesuai kebutuhan | Tugas/unit sesuai kewenangan | Read-only sesuai lingkup yang disahkan |
| Audit trail | Akses terkontrol, perlu konfirmasi | Tidak secara default | Tidak secara default | Tidak secara default |

Konfirmasi eksplisit diperlukan untuk: hak baca data sensitif lintas kategori, akses lintas unit, perubahan/hapus catatan, penutupan tindak lanjut, ekspor/cetak, pengelolaan akun oleh administrator, delegasi/backup petugas, retensi, dan siapa yang dapat membaca audit trail.

## Catatan keputusan berikutnya

Tambahkan entri baru dengan format keputusan, alasan, alternatif, dampak, dan status ketika requirement/mentor menetapkannya. Jangan mengubah proposal menjadi confirmed tanpa bukti persetujuan.

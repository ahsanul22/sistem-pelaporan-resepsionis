# Konteks Proyek

## Latar belakang dan tujuan

Sistem Pelaporan Resepsionis direncanakan sebagai aplikasi web internal untuk mencatat dan menelusuri aktivitas pelayanan resepsionis. Tujuannya mengurangi ketergantungan pada catatan manual, memudahkan pencarian riwayat, membantu pemantauan tindak lanjut bila diperlukan, dan mendukung rekap aktivitas.

Kondisi saat ini baru menunjukkan kerangka Laravel; masalah operasional dan alur yang dijelaskan di bawah berasal dari brief dan belum divalidasi melalui observasi pengguna.

## Masalah yang hendak diselesaikan

- Riwayat layanan manual mungkin sulit dicari dan direkap.
- Penerusan permintaan atau dokumen mungkin sulit ditelusuri.
- Penanggung jawab dan status tindak lanjut mungkin tidak konsisten.

Validasi perlu memastikan bagaimana masalah ini terjadi hari ini, frekuensi dan dampaknya, serta pencatatan apa yang benar-benar perlu didigitalisasi.

## Pengguna dan kebutuhan awal

- **Resepsionis:** pencatatan cepat, pencarian riwayat, dan penerusan informasi yang jelas.
- **Staf unit kerja:** melihat item yang memang ditugaskan kepada unitnya dan memperbarui tindak lanjut sesuai kewenangan.
- **Manajemen:** membaca ringkasan dan laporan yang diizinkan untuk pemantauan.
- **Administrator sistem:** mengelola akun dan konfigurasi/master data yang disetujui.

Peran, jumlah pengguna, unit organisasi, perangkat kerja, pola shift, dan tingkat literasi digital belum dikonfirmasi.

## Ruang lingkup MVP (proposal)

MVP dapat mencakup login internal, pencatatan aktivitas yang diprioritaskan, pencarian/filter riwayat, penerusan/tugas kepada unit bila proses itu disepakati, status tindak lanjut minimum, serta rekap sederhana. Prioritas dan definisi setiap item harus dikonfirmasi sebelum desain schema dan implementasi.

Jenis aktivitas kandidat: surat/dokumen diterima atau diserahkan; tamu/kunjungan; permintaan pertemuan; pengaduan/permintaan bantuan/laporan lain; dan penerusan ke unit. Tidak semua kategori otomatis masuk MVP.

## Modul kandidat

1. Autentikasi dan administrasi pengguna.
2. Master unit kerja dan konfigurasi terbatas.
3. Pencatatan aktivitas resepsionis berdasarkan kategori terpilih.
4. Penugasan/penerusan dan tindak lanjut.
5. Pencarian, filter, dan riwayat.
6. Dashboard dan laporan/rekap.
7. Audit trail untuk perubahan atau akses yang perlu dipertanggungjawabkan.

Daftar ini adalah peta awal, bukan komitmen implementasi penuh.

## Kebutuhan diketahui dari brief

- Aplikasi bersifat internal.
- Kemudahan belajar, pencatatan cepat, pencarian, tanggung jawab, dan kerahasiaan menjadi prinsip.
- Stack utama yang diminta: Laravel 10, PHP kompatibel dengan proyek, Blade, Tailwind melalui Vite.
- PostgreSQL adalah target database awal yang diminta, dengan pengecualian jika kebutuhan terkonfirmasi atau kondisi proyek membenarkan pilihan lain.
- Empat role konseptual diajukan pada `docs/DECISIONS.md`.

## Asumsi dan pertanyaan yang perlu dikonfirmasi

- Apakah sistem menggantikan buku/log yang ada atau hanya mendukungnya?
- Kategori mana yang wajib dicatat, dan data minimum apa yang diperlukan untuk setiap kategori?
- Siapa yang boleh membaca informasi tamu, pengaduan, atau dokumen, dan apakah ada data sensitif/retensi khusus?
- Bagaimana unit menerima penugasan, mengakui penerimaan, mengubah status, dan menutup tindak lanjut?
- Apakah status/target waktu layanan diperlukan? Apa definisi status dan siapa yang mengesahkannya?
- Apakah pencatatan surat membutuhkan nomor agenda, lampiran, tanda terima, atau cetak bukti?
- Apakah data perlu ekspor, periode laporan, format, dan persetujuan akses tertentu?
- Bagaimana akun dibuat, dinonaktifkan, reset password, dan apakah login terhubung SSO/LDAP?
- Apa struktur unit, pembagian tugas, delegasi, serta kebutuhan audit?
- Database dan lingkungan deployment mana yang tersedia? Brief mengusulkan PostgreSQL tetapi `.env.example` saat ini MySQL.
- Apa aturan retensi, backup, klasifikasi informasi, dan kebijakan keamanan internal?
- Apa ukuran keberhasilan dan baseline proses saat ini?

## Batasan sistem awal

- Aplikasi internal berbasis web; detail jaringan, hosting, ketersediaan, dan integrasi belum ditentukan.
- Tidak mengasumsikan notifikasi eksternal, tanda tangan digital, integrasi sistem lain, SLA, atau workflow persetujuan.
- Tidak mendigitalisasi proses tanpa kebutuhan yang dikonfirmasi.
- Tidak menetapkan schema final, kebijakan retensi, atau role final dalam dokumen proposal ini.

## Kriteria keberhasilan yang dapat diukur (baseline perlu dikumpulkan)

- Waktu median untuk mencatat aktivitas umum dibanding proses saat ini.
- Persentase catatan yang lengkap pada field wajib yang telah disepakati.
- Waktu median menemukan kembali catatan berdasarkan skenario pencarian.
- Persentase item yang diteruskan dengan unit/penanggung jawab dan status yang dapat ditelusuri.
- Jumlah kesalahan/duplikasi pencatatan dan tingkat penggunaan aktif setelah pelatihan.
- Hasil uji akses: pengguna tidak dapat membaca atau mengubah data di luar kewenangannya.

Target numerik ditetapkan setelah baseline, skenario uji, dan pemilik metrik disepakati.

## Risiko implementasi dan adopsi

- Requirement yang belum tervalidasi dapat menghasilkan form panjang atau modul yang tidak dipakai.
- Catatan pengaduan, tamu, dan dokumen berpotensi memuat informasi sensitif.
- Role luas tanpa cakupan unit dan kebijakan per-record dapat membuka data lintas unit.
- Migrasi dari catatan manual dapat menghasilkan data tidak lengkap/duplikat.
- Penggunaan bersamaan, jaringan, backup, retensi, dan pemulihan belum diketahui.
- Perubahan kebiasaan kerja dan pelatihan dapat memengaruhi kualitas/adopsi.
- Ketidaksesuaian konfigurasi database aktual dengan target dapat memengaruhi deployment dan test.

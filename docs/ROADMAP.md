# Roadmap

Status menggunakan `planned`, `in progress`, `blocked`, atau `completed` sesuai kondisi yang dapat dibuktikan di repository. Tahap 1 masih berjalan karena kebutuhan dan keputusan penting menunggu konfirmasi; dokumen fondasi awal sudah tersedia.

## 1. Project foundation dan requirement — in progress

Periksa repository, dokumentasikan konteks, asumsi, workflow, dan proposal arsitektur. Validasi proses kerja, data, kategori MVP, keberhasilan, batas akses, dan lingkungan dengan mentor/pengguna sebelum mengunci requirement.

## 2. Database foundation — planned

Konfirmasi PostgreSQL atau pilihan lain, lingkungan pengembangan/test/deployment, kebutuhan retensi dan backup. Rancang model konseptual dan migration setelah kategori, field, relasi, serta audit disepakati. Belum ada schema bisnis.

## 3. Authentication, roles, permissions, dan authorization — planned

Konfirmasi lifecycle akun, autentikasi/SSO, unit, role, cakupan data, serta matriks aksi. Terapkan autentikasi dan pemeriksaan server-side menggunakan pola Laravel yang sesuai. Role proposal belum diimplementasikan.

## 4. Shared application layout dan design system — planned

Konfirmasi arah visual, identitas, bahasa, dan perangkat sasaran. Bangun layout serta komponen Blade/Tailwind reusable setelah requirement dan desain awal disetujui.

## 5. Frontend modul berdasarkan prioritas — planned

Rancang dan implementasikan layar MVP satu per satu berdasarkan prioritas tervalidasi. Cakupan kandidat: input aktivitas, daftar/detail, pencarian/filter, dan tindak lanjut. Tidak membangun semua kategori sekaligus tanpa prioritas.

## 6. Integrasi backend dan business logic — planned

Hubungkan form dan layar dengan validasi, persistence, authorization, assignment, perubahan status, dan penanganan error yang sudah disepakati. Gunakan transaksi bila konsistensi lintas perubahan membutuhkannya.

## 7. Laporan, audit trail, dan penyempurnaan workflow — planned

Bangun laporan, ekspor, audit trail, notifikasi, atau penyempurnaan alur hanya jika kebutuhan, akses, dan kebijakan retensinya dikonfirmasi.

## 8. Testing, security review, usability review, dan deployment preparation — planned

Uji unit/feature dan alur utama; tinjau authorization, perlindungan data, dan konfigurasi; lakukan uji kegunaan bersama pengguna; siapkan backup, deployment, observabilitas, dan prosedur pemulihan sesuai lingkungan aktual.

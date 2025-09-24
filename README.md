Laundry Management System

Laundry Management System adalah aplikasi web sederhana untuk membantu pengelolaan usaha laundry. Dibanding cara manual, sistem ini bikin semuanya lebih terstruktur, cepat, dan rapi—mulai dari mencatat transaksi, memantau status pesanan, sampai bikin laporan keuangan.

Kenapa Dibuat?

Biar pencatatan transaksi nggak ribet lagi

Data pelanggan dan layanan tersimpan rapi

Status laundry bisa dipantau secara real-time

Laporan transaksi bisa keluar otomatis dan teratur

Teknologi yang Dipakai

HTML → struktur halaman

CSS + Bootstrap → bikin tampilan lebih rapih

JavaScript → interaksi biar lebih dinamis

PHP → otak dari aplikasi (backend & koneksi DB)

MySQL → tempat semua data disimpan (pakai XAMPP/Laragon)

FontAwesome → biar ada ikon modern di UI

Hak Akses Pengguna

Admin → atur user, layanan, dan laporan

Kasir → input transaksi & update status laundry

Pelanggan → bisa cek status laundry (opsional)

Fitur Utama

Login berdasarkan role pengguna

Manajemen data layanan (jenis, harga, satuan, dll)

Input & update data pelanggan

Pencatatan transaksi laundry

Update status laundry (pending, proses, selesai, diambil)

Pembayaran + cetak struk

Laporan transaksi harian/bulanan

Alur Kerja Singkat

Admin atau kasir login ke sistem

Kasir input data pelanggan + pilih layanan

Sistem otomatis hitung total biaya

Status laundry bisa diupdate sesuai progres

Admin bisa tarik laporan transaksi kapan aja

Struktur Database

Database bernama laundry_ukk_tugas ini punya 5 tabel utama:

1. laundry_login11

Data login user (admin, kasir, pelanggan).

id → Primary key

username → Nama user untuk login

password → Password (terenkripsi)

role → admin/kasir/user

2. layanan11

Data layanan yang ditawarkan.

id → Primary key

nama_layanan → Nama layanan (contoh: Cuci Kering)

kategori → Jenis kategori layanan

harga → Harga layanan

durasi → Estimasi waktu pengerjaan

deskripsi → Info tambahan layanan

icon → Nama/icon untuk UI

3. orders11

Data pesanan laundry.

id → Primary key

user_id → Relasi ke laundry_login11

total_harga → Total harga pesanan

status → pending / proses / selesai

tanggal_pesan → Waktu pesanan dibuat

tanggal_selesai → Waktu selesai laundry

4. order_items11

Detail layanan dalam satu pesanan.

id → Primary key

order_id → Relasi ke orders11

layanan_id → Relasi ke layanan11

jumlah → Jumlah layanan yang dipilih

harga → Harga per layanan

5. orders_progress11

Catatan progres dari tiap pesanan.

id → Primary key

order_id → Relasi ke orders11

status → menunggu / pencucian / pengeringan / siap

updated_by → ID user yang update status

waktu_update → Waktu update dilakukan

keterangan → Catatan tambahan

Relasi Antar Tabel

laundry_login11 → orders11 (user_id)

orders11 → order_items11 (order_id)

layanan11 → order_items11 (layanan_id)

orders11 → orders_progress11 (order_id)

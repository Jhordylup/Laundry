Laundry Management System

Laundry Management System adalah aplikasi berbasis web yang dirancang untuk membantu pengelolaan usaha laundry agar lebih praktis, cepat, dan efisien. Dengan sistem ini, pemilik usaha, kasir, dan pelanggan dapat mengakses informasi secara terstruktur dibandingkan metode manual.

Tujuan Utama

Mempermudah pencatatan transaksi

Mengelola data pelanggan dan layanan

Memantau status laundry secara real-time

Menyediakan laporan transaksi yang rapi

Teknologi yang Digunakan

HTML → struktur halaman

CSS + Bootstrap (opsional) → tampilan antarmuka

JavaScript → interaksi dinamis pada halaman web

PHP → backend logic dan koneksi database

MySQL (via Laragon/XAMPP) → penyimpanan data

FontAwesome → ikon agar tampilan lebih modern

Role / Hak Akses

Admin → mengelola pengguna, layanan, dan laporan

Kasir → input transaksi dan update status laundry

Pelanggan → melihat status laundry (opsional sesuai fitur)

Fitur Utama

Login sesuai role pengguna (admin, kasir)

Input dan update data layanan (jenis laundry, harga, satuan)

Manajemen data pelanggan

Pencatatan transaksi laundry

Update status laundry (proses, selesai, diambil)

Pembayaran dan cetak struk

Laporan transaksi

Alur Sistem

Admin atau kasir login ke sistem

Kasir input data pelanggan dan layanan yang dipilih

Sistem menghitung total biaya

Status laundry diupdate sesuai progres

Admin dapat melihat laporan transaksi per hari atau per bulan

Struktur Database

Database laundry_ukk_tugas terdiri dari 5 tabel utama:

1. Tabel laundry_login11

Menyimpan data akun pengguna sistem.

Field	Tipe Data	Keterangan
id	INT(11), AUTO_INCREMENT	Primary key
username	VARCHAR(50)	Nama pengguna untuk login
password	VARCHAR(255)	Password terenkripsi
role	ENUM('admin','kasir','user')	Hak akses pengguna
2. Tabel layanan11

Menyimpan daftar layanan laundry.

Field	Tipe Data	Keterangan
id	INT(11), AUTO_INCREMENT	Primary key
nama_layanan	VARCHAR(255)	Nama layanan
kategori	VARCHAR(255)	Kategori layanan
harga	INT(11)	Harga layanan
durasi	INT(11)	Estimasi durasi
deskripsi	VARCHAR(255)	Deskripsi singkat
icon	VARCHAR(255)	Ikon tampilan UI
3. Tabel orders11

Menyimpan data pesanan laundry.

Field	Tipe Data	Keterangan
id	INT(11), AUTO_INCREMENT	Primary key
user_id	INT(11), INDEX	Relasi ke tabel laundry_login11
total_harga	INT(11)	Total biaya
status	ENUM('pending','proses','selesai')	Status pesanan
tanggal_pesan	DATETIME	Waktu pesanan dibuat
tanggal_selesai	DATETIME	Waktu selesai laundry
4. Tabel order_items11

Menyimpan detail layanan dalam setiap pesanan.

Field	Tipe Data	Keterangan
id	INT(11), AUTO_INCREMENT	Primary key
order_id	INT(11), INDEX	Relasi ke tabel orders11
layanan_id	INT(11), INDEX	Relasi ke tabel layanan11
jumlah	INT(11)	Jumlah layanan
harga	INT(11)	Harga per layanan
5. Tabel orders_progress11

Menyimpan catatan perkembangan status laundry.

Field	Tipe Data	Keterangan
id	INT(11), AUTO_INCREMENT	Primary key
order_id	INT(11), INDEX	Relasi ke tabel orders11
status	ENUM('menunggu','pencucian','pengeringan','siap...')	Status proses
updated_by	INT(11), INDEX	ID kasir/admin yang mengupdate
waktu_update	DATETIME	Waktu update
keterangan	VARCHAR(255)	Catatan tambahan
Relasi Antar Tabel

laundry_login11 → orders11 (user_id)

orders11 → order_items11 (order_id)

layanan11 → order_items11 (layanan_id)

orders11 → orders_progress11 (order_id)

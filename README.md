# 🧺 Laundry Management System  

[![Made with PHP](https://img.shields.io/badge/Made%20with-PHP-777BB4?logo=php&logoColor=white)](https://www.php.net/)  
[![Database MySQL](https://img.shields.io/badge/Database-MySQL-4479A1?logo=mysql&logoColor=white)](https://www.mysql.com/)  
[![Frontend](https://img.shields.io/badge/Frontend-HTML%2FCSS%2FJS-orange)](#)  
[![Status](https://img.shields.io/badge/Project-Active-success)](#)  

**Laundry Management System** adalah aplikasi web sederhana untuk mengelola usaha laundry biar lebih cepat, praktis, dan rapi.  
Dibanding cara manual, sistem ini bikin transaksi, pelanggan, layanan, dan laporan lebih terstruktur.  

---

## 🚀 Fitur Utama
- 🔑 Login berdasarkan role pengguna (Admin, Kasir, User)  
- 📋 Manajemen layanan laundry (jenis, harga, durasi, dll)  
- 👥 Input & update data pelanggan  
- 💰 Pencatatan transaksi + perhitungan biaya otomatis  
- 🔄 Update status laundry (pending, proses, selesai, diambil)  
- 🧾 Pembayaran + cetak struk  
- 📊 Laporan transaksi harian/bulanan  

---

## 🛠️ Teknologi
| Bagian        | Teknologi yang Dipakai |
|---------------|-------------------------|
| Frontend      | HTML, CSS, Bootstrap, JavaScript |
| Backend       | PHP |
| Database      | MySQL (XAMPP/Laragon) |
| UI/UX Support | FontAwesome |

---

## 👤 Hak Akses Pengguna
- **Admin** → kelola user, layanan, laporan  
- **Kasir** → input transaksi, update status  
- **Pelanggan** → cek status laundry (opsional)  

---

## 📌 Alur Kerja Singkat
1. Admin/Kasir login ke sistem  
2. Kasir input data pelanggan + pilih layanan  
3. Sistem otomatis hitung total biaya  
4. Status laundry diupdate sesuai progres  
5. Admin bisa tarik laporan transaksi kapan saja  

---

## 🗄️ Struktur Database  

### Tabel yang digunakan:
- **laundry_login11** → data akun pengguna  
- **layanan11** → data layanan laundry  
- **orders11** → data pesanan pelanggan  
- **order_items11** → detail layanan dalam pesanan  
- **orders_progress11** → catatan progres setiap pesanan  

### Relasi Tabel
- `laundry_login11` → `orders11` (user_id)  
- `orders11` → `order_items11` (order_id)  
- `layanan11` → `order_items11` (layanan_id)  
- `orders11` → `orders_progress11` (order_id)  

---

## 📊 DB Diagram (dbdiagram.io Syntax)

```sql
Table laundry_login11 {
  id int [pk, increment]
  username varchar(50)
  password varchar(255)
  role enum('admin','kasir','user')
}

Table layanan11 {
  id int [pk, increment]
  nama_layanan varchar(255)
  kategori varchar(255)
  harga int
  durasi int
  deskripsi varchar(255)
  icon varchar(255)
}

Table orders11 {
  id int [pk, increment]
  user_id int [ref: > laundry_login11.id]
  total_harga int
  status enum('pending','proses','selesai')
  tanggal_pesan datetime
  tanggal_selesai datetime
}

Table order_items11 {
  id int [pk, increment]
  order_id int [ref: > orders11.id]
  layanan_id int [ref: > layanan11.id]
  jumlah int
  harga int
}

Table orders_progress11 {
  id int [pk, increment]
  order_id int [ref: > orders11.id]
  status enum('menunggu','pencucian','pengeringan','siap...')
  updated_by int [ref: > laundry_login11.id]
  waktu_update datetime
  keterangan varchar(255)
}

# 🚀 Simulasi API Key & OAuth 2.0 (Sistem Manajemen Produk)

Proyek ini merupakan simulasi implementasi keamanan API menggunakan dua metode berbeda: **API Key** untuk akses publik (Read-Only) dan **JWT (OAuth 2.0)** untuk otorisasi privat (CRUD). Tujuan utamanya adalah menerapkan *middleware* berlapis dan otorisasi berbasis peran (*role-based access control*) untuk mengamankan data sensitif.

---

## 🛠️ Tech Stack

Proyek ini dibangun menggunakan teknologi berikut:

* 
**Backend:** Node.js & Express.js.


* 
**Database:** MongoDB Atlas (Mongoose ODM).


* 
**Autentikasi:** JSON Web Tokens (JWT) & API Key.


* 
**Keamanan:** Bcryptjs (Password Hashing).


* 
**Alat Pengujian:** Postman / Insomnia.



---

## 📦 Fitur Utama

1. 
**Akses Publik (API Key):** Pengguna dengan kunci API yang valid hanya dapat melihat daftar produk.


2. 
**Akses Privat (OAuth 2.0/JWT):** Pengguna yang terautentikasi dapat mengelola data produk.


3. 
**Role-Based Access Control (RBAC):** Hanya pengguna dengan peran `admin` yang diizinkan untuk menambah, mengubah, atau menghapus produk.


4. 
**Middleware Keamanan:** Validasi otomatis untuk setiap permintaan yang masuk ke *endpoint* terproteksi.


5. 
**Password Hashing:** Keamanan kredensial pengguna menggunakan algoritma *bcrypt*.



---

## 📂 Struktur Proyek

```text
p10-oauth2-api-key-nimanda/
├── controllers/        # Logika handler untuk auth dan produk
├── middleware/         # Middleware validateApiKey dan validateToken
├── models/             # Skema Mongoose (User, Product, ApiKey)
├── routes/             # Definisi endpoint API
├── seeders/            # Script untuk pengisian data awal database
├── utils/              # Fungsi utilitas (Generate JWT)
├── .env                # Konfigurasi variabel lingkungan
├── server.js           # Entry point aplikasi
└── README.md           # Dokumentasi proyek

```



---

## 🚀 Cara Instalasi

1. **Clone Repositori**
```bash
git clone https://github.com/username/p10-oauth2-api-key.git
cd p10-oauth2-api-key

```


2. **Install Dependensi**
```bash
npm install express mongoose dotenv jsonwebtoken bcryptjs

```





3. **Konfigurasi Environment Variable**
Buat file `.env` di direktori utama dan isi dengan data berikut:
```env
PORT=3000
MONGODB_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/p10_db
JWT_SECRET=rahasia-super-aman-simulasi-jwt

```





4. **Menjalankan Seeder** (Untuk mengisi data awal)
```bash
node seeders/seed.js

```





5. **Jalankan Server**
```bash
node server.js

```






---

## 📑 Dokumentasi API

### 🔓 Akses Publik

| Method | Endpoint | Header | Deskripsi |
| --- | --- | --- | --- |
| **GET** | `/api/v1/products/public` | `x-api-key: <your_key>` | Mengambil daftar produk.

 |

### 🔐 Autentikasi

| Method | Endpoint | Body (JSON) | Deskripsi |
| --- | --- | --- | --- |
| **POST** | `/api/v1/auth/token` | `username`, `password` | Mendapatkan Access Token (JWT).

 |

### 🛡️ Akses Privat (Admin Only)

*Wajib menyertakan Header: `Authorization: Bearer <JWT_TOKEN>*`.

| Method | Endpoint | Deskripsi |
| --- | --- | --- |
| **POST** | `/api/v1/products/private` | Membuat produk baru.

 |
| **PUT** | `/api/v1/products/private/:id` | Memperbarui data produk.

 |
| **DELETE** | `/api/v1/products/private/:id` | Menghapus produk.

 |

---

## 📄 Lisensi

Proyek ini dibuat untuk tujuan akademik dalam mata kuliah *Web Service Engineering* 20251.

---

**Dosen Pengampu:** Muhayat, M.IT 
**Oleh:** Achmad Fauzil 'Adhim (NIM: 230104040222)

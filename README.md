# WEBSITE PORTOFOLIO
## Ahmad Qomarul Arifin

Website ini merupakan aplikasi berbasis web yang dibuat untuk memenuhi tugas praktikum Pemrograman Web. Website bersifat statis dan 
menampilkan informasi portofolio pribadi yang terdiri dari Home, About Me, dan Certificates. Project ini dikembangkan menggunakan HTML, 
CSS, Bootstrap 5, dan Vue JS (CDN).

# 📌 TUJUAN PROJECT

- Mengimplementasikan struktur dasar HTML dengan benar.
- Menggunakan CSS untuk styling dan layout.
- Menerapkan Bootstrap 5 untuk mempercepat proses layouting.
- Menggunakan Vue JS untuk menampilkan data secara dinamis (data tetap statis).
- Membuat tampilan website yang rapi dan responsif.

---

#  TEKNOLOGI YANG DIGUNAKAN

- HTML
- CSS
- Bootstrap 5
- Vue JS (CDN)

---

# 📂 STRUKTUR PROJECT

project-folder  
│── index.html  
│── style.css  
│── README.md  
│  
└── assets  
├── profile.jpg  
├── cert-1.jpg  
├── cert-2.jpg  
└── cert-3.jpg  

---

#  PENJELASAN DAN TAMPILAN SETIAP SECTION

## 1️⃣ HOME (Hero Section)

### Fitur:
- Foto profil
- Nama lengkap
- Status/role
- Tombol navigasi
- Email dan GitHub
- Statistik (Projects, Skills, Certificates)

### Penjelasan Code:
Section Home menggunakan `<header>` dengan layout Bootstrap container dan custom CSS Grid.
Data seperti nama dan role ditampilkan menggunakan Vue interpolation: {{ profile.name }}
Statistik ditampilkan menggunakan perulangan: v-for="(s,i) in stats"

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/bf0c886c-53d7-41f1-9898-b112d1f175d2" />


## 2️⃣ ABOUT ME

### Fitur:
- Judul About Me
- Deskripsi diri
- Skills menggunakan progress bar
- Pengalaman organisasi/kegiatan

### Penjelasan Code:
Deskripsi diri ditempatkan di dalam div dengan class `about-desc-card` dan diatur menggunakan CSS agar berada di tengah.
Skills menggunakan komponen Bootstrap progress bar:
<div class="progress">
  <div class="progress-bar"></div>
</div>
Data skills ditampilkan menggunakan:
v-for="(sk,i) in skills"
Pengalaman ditampilkan menggunakan struktur flexbox sederhana.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/9e90867e-5038-4dc3-9817-74ecd7aeadb1" />


## 3️⃣ CERTIFICATES

### Fitur:
- Layout grid sertifikat
- Gambar sertifikat
- Judul dan tahun
- Modal popup saat sertifikat diklik

### Penjelasan Code:
Layout menggunakan CSS Grid:

.cert-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}

Data sertifikat ditampilkan menggunakan: v-for="(c,i) in certificates" Saat card diklik, method Vue `openCert()` dijalankan untuk membuka modal Bootstrap.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/9d585d48-81f7-4306-be91-0fdb6daf6fe9" />

# WEBSITE PORTOFOLIO
## Ahmad Qomarul Arifin

Website ini merupakan aplikasi berbasis web yang dibuat untuk memenuhi tugas praktikum Pemrograman Web. Website bersifat statis dan menampilkan informasi portofolio pribadi yang terdiri dari Home, About Me, dan Certificates. Project ini dikembangkan menggunakan HTML, CSS, Bootstrap 5, dan Vue JS (CDN).

---

#  TUJUAN PROJECT

- Mengimplementasikan struktur dasar HTML dengan benar (html, head, body).
- Menggunakan CSS untuk styling tampilan (warna, background, layout, font).
- Menerapkan Bootstrap 5 untuk mempercepat proses layouting dan membuat responsif.
- Menggunakan Vue JS untuk menampilkan data secara dinamis.

#  TEKNOLOGI YANG DIGUNAKAN

- **HTML**  
  Digunakan untuk membangun struktur halaman: navbar, section Home, About Me, Certificates, dan modal sertifikat.

- **CSS**  
  Digunakan untuk mengatur tampilan dan tema website agar terlihat modern dan rapi, seperti:
  - Background gradient pada tiap section (`.sec-home`, `.sec-about`, `.sec-certs`)
  - Layout custom (CSS Grid pada `.home-grid` dan `.cert-grid`)
  - Card/box style (border radius, shadow, spacing) untuk About dan Certificates
  - Pengaturan typography (ukuran font, ketebalan, warna teks)
  - Responsif tambahan melalui media query (`@media`)

- **Bootstrap 5**  
  Membantu proses layouting dan komponen siap pakai, seperti:
  - Navbar responsif (`navbar`, `navbar-toggler`, `collapse`)
  - Grid system (`container`, `row`, `col-lg-6`)
  - Button (`btn`, `btn-outline-light`)
  - Progress bar (`progress`, `progress-bar`)
  - Modal (`modal`, `modal-dialog`, `modal-content`)
  - Utilities spacing (`py-5`, `mb-3`, `gap-3`, dll)

- **Vue JS (CDN)**  
  Digunakan untuk membuat tampilan lebih dinamis dan interaktif meskipun data bersifat statis, seperti:
  - Interpolation `{{ }}` untuk menampilkan data profil/sertifikat
  - `data()` untuk menyimpan data statis (profile, skills, experiences, certificates)
  - `v-for` untuk looping daftar skill, pengalaman, dan sertifikat
  - `.mount('#app')` untuk menghubungkan Vue ke elemen HTML
  - Method `openCert()` untuk membuka modal saat sertifikat diklik


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

#  PENJELASAN DAN TAMPILAN SETIAP SECTION / FITUR

##  NAVBAR (Fitur Navigasi)

### Fitur:
- Navigasi ke Home, About Me, dan Certificates.

### Penjelasan Code:
Navbar dibuat menggunakan komponen Bootstrap 5:

- Struktur navbar:
  - `navbar-expand-lg` → navbar akan collapse pada layar kecil
  - `sticky-top` → navbar tetap di atas ketika scroll
  - `collapse navbar-collapse` → menu akan disembunyikan saat mobile
  - `data-bs-toggle="collapse"` + `data-bs-target="#navMenu"` → untuk membuka/tutup menu hamburger

Contoh implementasi:
- Link menu:
  - `<a class="nav-link" href="#home">Home</a>` akan scroll otomatis ke section Home
- Data brand:
  - `{{ profile.brand }}` ditampilkan dari data Vue

<img width="1347" height="55" alt="image" src="https://github.com/user-attachments/assets/1eacd511-5f5e-4ffe-a5f1-e61f66cebdca" />

##  HOME (Hero Section)

### Fitur:
- Foto profil
- Nama lengkap
- Status
- Tombol navigasi (Tentang Saya & Sertifikat)
- Email dan GitHub
- Statistik (Projects, Skills, Certificates)

### Penjelasan Code:
Section Home menggunakan `<header id="home">` dan dibuat menjadi hero section.

**Layouting:**
- Bootstrap `container py-5` untuk memberikan jarak atas bawah.
- CSS Grid pada `.home-grid` untuk membagi jadi 3 kolom:
  1) Foto
  2) Teks perkenalan
  3) Statistik

**Data dengan Vue:**
- Nama/role ditampilkan dengan interpolation:
  - `{{ profile.name }}`
  - `{{ profile.role }}`

**Statistik:**
- Bagian stats dibuat dari array `stats` lalu ditampilkan menggunakan:
  - `v-for="(s,i) in stats"`

**Foto profil:**
- Gambar dipanggil dari:
  - `photo:"assets/profile.jpg"`

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/01252bb1-93dc-4953-a5e8-1dfa495e435f" />


## ABOUT ME

### Fitur:
- Judul About Me
- Deskripsi diri
- Skills menggunakan progress bar
- Pengalaman organisasi/kegiatan

### Penjelasan Code:
Section About Me menggunakan `<section id="about">`.

**Deskripsi Diri:**
- Diletakkan pada:
  - `<div class="about-desc-card">`
- Diatur menggunakan CSS agar:
  - card berada di tengah (`margin: 0 auto`)
  - teks rata tengah (`text-align: center`)

**Skills (Progress Bar):**
- Menggunakan Bootstrap progress bar:
  ```html
  <div class="progress prog">
    <div class="progress-bar" :class="sk.color" :style="{ width: sk.level + '%' }"></div>
  </div>
  ```
- Data skill ada di array `skills` (Vue) lalu ditampilkan dengan:
  - `v-for="(sk,i) in skills"`

**Pengalaman:**
- Dibuat menggunakan list flexbox (`exp-list`, `exp-item`).
- Ditampilkan dengan `v-for="(e,i) in about.experiences"`.
- Dot pengalaman menggunakan `exp-dot` (CSS).

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/4be1d0c2-d85a-4aa7-b6b1-438725a374f3" />


##  CERTIFICATES

### Fitur:
- Layout grid sertifikat
- Gambar sertifikat
- Judul, issuer, dan tahun
- Modal popup saat sertifikat diklik

### Penjelasan Code:
Section Certificates menggunakan `<section id="certificates">`.

**Grid Sertifikat:**
- Menggunakan CSS Grid:
  ```css
  .cert-grid{
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 24px;
  }
  ```
- Setiap sertifikat dibuat dalam card (`cert-card`) dan ditampilkan dengan:
  - `v-for="(c,i) in certificates"`

**Interaksi Modal:**
- Saat card diklik, Vue menjalankan method:
  - `@click="openCert(c)"`
- Method `openCert()`:
  - menyimpan data sertifikat ke `activeCert`
  - memunculkan modal Bootstrap
 
  <img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/1018eddb-ebd9-48d7-9cdf-126c38f69a13" />

**Isi modal mengikuti data yang dipilih:**
- `{{ activeCert?.title }}`
- `:src="activeCert.image"`

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/248ef835-76bb-407a-96b2-8e179b6b45db" />

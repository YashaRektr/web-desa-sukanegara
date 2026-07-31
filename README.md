# 📘 Dokumentasi Master & Panduan Pengelolaan Website Desa Sukanegara

Dokumen ini merupakan **Panduan Lengkap & Spesifikasi Teknis Master** bagi **Admin Desa Sukanegara**, pengembang, serta pengelola sistem untuk mengoperasikan, mengunggah berkas, dan memelihara **Website Resmi Desa Sukanegara** (`desa-sukanegara.my.id`).

Seluruh sistem website dirancang secara **Dinamis & Otomatis (Future-Proof)**. Pengelolaan foto Perangkat Desa, Pimpinan Wilayah (Kepala Dusun), Struktur TP PKK (Pengurus Inti & Pokja), Galeri Foto Kegiatan, Surat Menyurat Digital, dan Berita Desa dapat dilakukan secara langsung melalui **Google Drive** tanpa perlu menyentuh atau mengedit kodingan website sama sekali.

---

## 📋 Daftar Isi
1. [🌐 Konfigurasi Domain Utama & Hosting (DomainNesia & GitHub Pages)](#-1-konfigurasi-domain-utama--hosting-domainnesia--github-pages)
2. [🔒 Keamanan & Pembatasan Google Cloud Console API Key](#-2-keamanan--pembatasan-google-cloud-console-api-key)
3. [👨‍💼 Pengelolaan Perangkat Desa & Kepala Dusun](#-3-pengelolaan-perangkat-desa--kepala-dusun)
4. [🌺 Pengelolaan Struktur TP PKK Desa Sukanegara](#-4-pengelolaan-struktur-tp-pkk-desa-sukanegara)
5. [🖼️ Pengelolaan Galeri Desa](#-5-pengelolaan-galeri-desa)
6. [📄 Pengelolaan Surat Menyurat Digital & Formulir](#-6-pengelolaan-surat-menyurat-digital--formulir)
7. [📰 Pengelolaan Berita & Kegiatan Desa](#-7-pengelolaan-berita--kegiatan-desa)
8. [⚡ Fitur Otomatisasi & Future-Proofing](#-8-fitur-otomatisasi--future-proofing)
9. [📱 Responsivitas Layar HP & Pemeliharaan Tampilan](#-9-responsivitas-layar-hp--pemeliharaan-tampilan)
10. [❓ Panduan Pemecahan Masalah (Troubleshooting)](#-10-panduan-pemecahan-masalah-troubleshooting)

---

## 🌐 1. Konfigurasi Domain Utama & Hosting (DomainNesia & GitHub Pages)

Website Desa Sukanegara di-host secara gratis dan aman di **GitHub Pages** dan dihubungkan ke Custom Domain resmi dari **DomainNesia**: `desa-sukanegara.my.id`.

### A. Pengaturan DNS di Dashboard DomainNesia:
Masuk ke dashboard [MyDomainNesia](https://my.domainnesia.com/) ➔ Menu **Domains** ➔ **DNS Management**, dan pastikan **2 Record DNS** berikut telah aktif:

| Type | Host / Name | Value / Destination | Fungsi |
| :--- | :--- | :--- | :--- |
| **`A`** | `@` *(atau kosong)* | `185.199.108.153` | Menghubungkan domain utama ke server GitHub Pages |
| **`A`** | `@` *(atau kosong)* | `185.199.109.153` | Server cadangan 2 GitHub Pages |
| **`A`** | `@` *(atau kosong)* | `185.199.110.153` | Server cadangan 3 GitHub Pages |
| **`A`** | `@` *(atau kosong)* | `185.199.111.153` | Server cadangan 4 GitHub Pages |
| **`CNAME`** | `www` | `yasharektr.github.io` | Menghubungkan subdomain `www.desa-sukanegara.my.id` |

### B. Pengaturan di Repositori GitHub Pages:
1. Buka repositori GitHub: [https://github.com/YashaRektr/web-desa-sukanegara](https://github.com/YashaRektr/web-desa-sukanegara)
2. Buka menu **Settings** ➔ **Pages**.
3. Pada kolom **Custom domain**, isi dengan: `desa-sukanegara.my.id`.
4. Centang opsi **Enforce HTTPS** *(aktifkan SSL agar URL diawali `https://` yang aman)*.

---

## 🔒 2. Keamanan & Pembatasan Google Cloud Console API Key

Untuk mencegah penggunaan API Key oleh pihak yang tidak bertanggung jawab, Google Drive API Key yang terpasang di kodingan website **telah dikunci secara ketat (Domain Restricted)** melalui [Google Cloud Console Credentials](https://console.cloud.google.com/apis/credentials).

### Daftar Domain Resmi yang Diizinkan (Allowed HTTP Referrers):
* `https://desa-sukanegara.my.id/*`
* `https://www.desa-sukanegara.my.id/*`
* `https://yasharektr.github.io/*`
* `http://127.0.0.1/*` *(Khusus untuk testing di komputer lokal Admin)*
* `http://localhost/*`

> ⚠️ **PENTING:** Jika website dipindahkan ke domain baru atau diakses dari nama domain yang berbeda, pastikan untuk menambahkan domain baru tersebut ke daftar *HTTP Referrers* di Google Cloud Console agar foto dari Google Drive tidak mengalami error `403 Forbidden`.

---

## 👨‍💼 3. Pengelolaan Perangkat Desa & Kepala Dusun

* **Folder ID Google Drive:** `10Om41wIBdsarmksMlwEgpF4t8clPBwqS`
* **Link Akses Folder:** [📂 Buka Folder Perangkat Desa & Kadus](https://drive.google.com/drive/folders/10Om41wIBdsarmksMlwEgpF4t8clPBwqS)

### Aturan & Format Penamaan File Foto:

#### A. Format Ganti Foto Orang yang Sama:
Jika hanya ingin memperbarui foto pejabat yang sudah ada tanpa mengubah jabatannya, Anda cukup mengunggah foto dengan nama pejabat yang bersangkutan.
* *Contoh File:*
  * `Pak Heri Tamtomo.jpg`
  * `Pak Sunarna.webp`
  * `Sudarso.jpg` *(Otomatis memperbarui foto Kepala Dusun I)*

#### B. Format Pergantian Pejabat / Perangkat Desa Baru:
Gunakan format baku: **`[Jabatan] - [Nama Lengkap].[ext]`**

* *Contoh Perangkat Desa:*
  * `Kepala Desa - Heri Tamtomo S.Sos.jpg`
  * `Sekretaris Desa - Sunarna.jpg`
  * `Kaur Keuangan - Buang Riyanto.jpg`
  * `Kaur Perencanaan - Wahyudi.jpg`
  * `Kasi Pemerintahan - Anwar Nasikin.jpg`
  * `Kasi Pelayanan - Samia Maria.jpg`
  * `Kasi Kesejahteraan - Tara Amalia.jpg`
  * `Kaur Umum - Budi Santoso.jpg` *(Jabatan baru otomatis membuat kartu baru)*

* *Contoh Kepala Dusun:*
  * `Kadus 1 - Sudarso.jpg` *(Sama artinya dengan `Kepala Dusun 1 - Sudarso.jpg` atau `Kadus I`)*
  * `Kadus 2 - Sarno.jpg`
  * `Kadus 3 - Samsuri.jpg`
  * `Kadus 4 - Djumiran.jpg`
  * `Kadus 5 - Sumardi.jpg`
  * `Kadus 6 - Prihatin Yudhono.jpg`
  * `Kadus 7 - Ahmad.jpg` *(Otomatis membuat kartu Dusun VII jika desa mekar)*

> ℹ️ **Fleksibilitas Penamaan Dusun:**  
> Penulisan nomor dusun mendukung Angka Arab maupun Angka Romawi: **`Kadus 1`**, **`Kadus I`**, **`Kepala Dusun 1`**, dan **`Kepala Dusun I`** dianggap **SAMA PERSIS** oleh sistem parser website.

---

## 🌺 4. Pengelolaan Struktur TP PKK Desa Sukanegara

Untuk menjaga kerapian administrasi dan menghindari bentrokan data dengan Perangkat Desa, TP PKK Desa Sukanegara memiliki **Folder Google Drive Khusus**:

* **Folder ID Khusus PKK:** `1SS-tgp0PwUe3WjQ5BUswb-fSV6v_KYpz`
* **Link Akses Folder:** [📂 Buka Folder Khusus TP PKK Desa](https://drive.google.com/drive/folders/1SS-tgp0PwUe3WjQ5BUswb-fSV6v_KYpz)

Aturan utama: **Setiap 1 File Foto = Representasi 1 Orang Pengurus.**

### A. Format Penamaan Pengurus Inti PKK:
Format baku: **`[Jabatan PKK] - [Nama Lengkap].[ext]`**

* *Contoh Pengurus Inti:*
  * `Pembina PKK - Heri Tamtomo S.Sos.jpg`
  * `Ketua PKK - Walem S.Kom.I.jpg` *(Atau `Ketua TP PKK - Walem S.Kom.I`)*
  * `Penasehat PKK - Asmara S.Pd.jpg`
  * `Sekretaris PKK - Sutini.jpg`
  * `Bendahara PKK - Nilawati.jpg`

### B. Format Penamaan Ketua Pokja (Pokja I - X):
Format baku: **`Ketua Pokja [Nomor] - [Nama Ketua].[ext]`** ATAU **`Pokja [Nomor] - Ketua - [Nama Ketua].[ext]`**

* *Contoh Ketua Pokja:*
  * `Ketua Pokja 1 - Roslaila.jpg` *(Atau `Pokja 1 - Ketua - Roslaila.jpg`)*
  * `Ketua Pokja 2 - Yuti Alistuti.jpg`
  * `Ketua Pokja 3 - Marminah.jpg`
  * `Ketua Pokja 4 - Hali Desna.jpg`

### C. Format Penamaan Anggota Pokja (Bisa 2, 3, 5, atau Lebih Anggota):
Format baku: **`Anggota Pokja [Nomor] - [Nama Anggota].[ext]`** ATAU **`Pokja [Nomor] - Anggota - [Nama Anggota].[ext]`**

* *Contoh Anggota Pokja:*
  * `Anggota Pokja 1 - Mirdayani.jpg`
  * `Anggota Pokja 1 - Siti Qomariyah.jpg`
  * `Anggota Pokja 1 - Cici Kurniasih.jpg`
  * `Anggota Pokja 1 - Suharma Hidayati.jpg`
  * `Pokja 2 - Anggota - Rita Indriyani.jpg`
  * `Pokja 2 - Anggota - Afni Defita Sari.jpg`

---

## ⚡ 5. Fitur Otomatisasi & Future-Proofing

Sistem website Desa Sukanegara dilengkapi **Mesin Parsing Otomatis (Future-Proofing)** yang bekerja secara cerdas:

1. **Pejabat / Pengurus Tanpa Foto (Gunakan Format File Teks `.txt`):**  
   Jika pejabat atau pengurus sudah ada/ditunjuk namun **belum memiliki foto formal**, Admin Desa tidak perlu membiarkan data kosong. Cukup mengunggah file teks kosong (`.txt`):  
   * *Contoh:* Upload file bernama `Kaur Umum - Budi.txt` atau `Penasehat PKK - Asmara S.Pd.txt` di Google Drive.  
   * *Hasil di Website:* Kartu akan otomatis dibuat dengan icon avatar **`👤`** / icon jabatan **`📜`**, nama **Budi**, dan jabatan **Kaur Umum**. Begitu foto asli diunggah di kemudian hari, sistem akan menimpa avatar tersebut menjadi foto secara otomatis.
2. **Penanganan Foto Rusak / Tidak Ditemukan:**  
   Jika foto gagal dimuat atau korup, sistem tidak akan pernah menampilkan kotak gambar pecah. Sistem otomatis menggantinya menjadi Icon Badge Emas yang indah (`🎖️`, `👑`, `📜`, `✍️`, `💰`, `👤`).
3. **Penyaringan Berkas Dokumen/Panduan (`README` Filter):**  
   File dokumentasi seperti `README_PANDUAN_FOTO_GOOGLE_DRIVE.txt` atau file yang mengandung kata `README`/`PANDUAN` yang disimpan di Google Drive akan **otomatis disaring & diabaikan** oleh sistem sehingga tidak akan pernah muncul menjadi kartu staf.
4. **Penambahan Wilayah/Dusun Baru:**  
   Jika terjadi pemekaran wilayah (misal Dusun 7 atau Dusun 8), Admin cukup mengunggah `Kadus 7 - Nama.jpg`. Sistem website akan otomatis menambah kolom Dusun VII tanpa perlu mengedit kodingan.
5. **Penambahan Pokja Baru:**  
   Jika ada pengurus `Pokja 5 - Nama.jpg`, sistem website secara dinamis menambah grid Pokja V.
6. **Masa Pergantian Pejabat (Empty State Handling):**  
   Jika seluruh file dalam folder dihapus, website akan menampilkan banner status yang estetik:  
   * `🏛️ Data Perangkat Desa Sedang Dalam Masa Pergantian`  
   * `🏡 Data Kepala Dusun Sedang Dalam Masa Pergantian`  
   * `🌺 Data Struktur PKK Sedang Dalam Masa Pergantian`

---

## 🖼️ 6. Pengelolaan Galeri Desa

* **Folder ID Google Drive:** `1eSlgdubHZmH-nyYcR3VpBEeTzz2cpqW4`
* **Link Akses Folder:** [📂 Buka Folder Galeri Desa](https://drive.google.com/drive/folders/1eSlgdubHZmH-nyYcR3VpBEeTzz2cpqW4)

### Format Penamaan File:
Nama file foto yang diunggah ke Google Drive akan **otomatis dikonversi menjadi Keterangan/Caption Foto** yang tampil elegan di pojok kiri bawah setiap foto pada grid Galeri Desa.
* *Contoh Nama File:*
  * `Gotong Royong Kebersihan Dusun 2.jpg`
  * `Pelatihan Pertanian Organik 2026.png`
  * `Panen Raya Padi Desa Sukanegara.jpg`

---

## 📄 7. Pengelolaan Surat Menyurat Digital & Formulir

* **Folder ID Google Drive:** `1HoyodhCKPisgj1X--3hH3wBxVMT9BnjU`
* **Link Akses Folder:** [📂 Buka Folder Surat Menyurat](https://drive.google.com/drive/folders/1HoyodhCKPisgj1X--3hH3wBxVMT9BnjU)

Warga desa dapat mengunduh surat keterangan atau formulir pelayanan secara langsung melalui website. Upload berkas dalam format PDF (`.pdf`) atau Word (`.docx`).
* *Contoh Nama File:*
  * `Surat Keterangan Domisili.pdf`
  * `Surat Keterangan Usaha (SKU).pdf`
  * `Formulir Permohonan KTP.docx`
  * `Peraturan Desa tentang APBDes 2026.pdf`

---

## 📰 8. Pengelolaan Berita & Kegiatan Desa

* **Folder ID Google Drive:** `1f2jx3TapKrqGl-SlAhuKIo4Juf-OxM17`
* **Link Akses Folder:** [📂 Buka Folder Berita Desa](https://drive.google.com/drive/folders/1f2jx3TapKrqGl-SlAhuKIo4Juf-OxM17)

Seluruh berkas foto atau dokumen kegiatan liputan berita desa yang diunggah ke folder ini akan otomatis disinkronkan dan ditampilkan pada seksi Berita Desa di halaman depan website.

---

## 📱 9. Responsivitas Layar HP & Pemeliharaan Tampilan

Seluruh komponen website telah dioptimalkan dengan **Fluid Grid Responsive System**:
1. **Tampilan di HP (Mobile):**  
   * Grid Perangkat Desa, Dusun, dan PKK secara otomatis menyesuaikan lebar layar HP (1–2 kolom per baris) agar foto dan nama pengurus tidak pernah terpotong atau gepeng.
   * Teks alamat dan jam operasional dilengkapi aturan `wordBreak: "break-word"` sehingga tidak akan pernah ter-crop di batas kanan layar.
   * Baris statistik Hero diset dengan posisi relatif agar tidak pernah menutupi teks judul desa.
2. **Tampilan di Komputer / Laptop (Desktop):**  
   * Grid menyebar secara luas dan presisi (3–5 kolom) dengan animasi hover yang halus.

---

## ❓ 10. Panduan Pemecahan Masalah (Troubleshooting)

| Gejala Masalah | Penyebab Utama | Langkah Penyelesaian |
| :--- | :--- | :--- |
| **Foto di website tidak muncul / 403 Forbidden** | Domain belum didaftarkan di Google Cloud Console | Masuk ke Google Cloud Console, tambahkan domain Anda (`https://desa-sukanegara.my.id/*`) di bagian HTTP Referrers API Key. |
| **Nama pejabat ada typo / salah eja** | Nama file di Google Drive mengandung salah ketik | Edit/Rename nama file yang bersangkutan di Google Drive (misal: ganti `Heri Tamtomo S.So.s` menjadi `Heri Tamtomo S.Sos`). |
| **File panduan `.txt` muncul jadi kartu staf** | Nama file mengandung kata staf | Pastikan file panduan diberi nama yang mengandung kata `README` atau `PANDUAN` agar otomatis disaring oleh sistem. |
| **Perubahan di Google Drive belum muncul di website** | Cache browser masih menyimpan versi lama | Lakukan Hard Refresh di browser dengan menekan tombol **`Ctrl + Shift + R`** (atau `Cmd + Shift + R` di Mac). |
| **Peta Google Maps tidak berpusat di Desa** | URL peta menunjuk ke kecamatan umum | Variabel URL Google Maps telah diset presisi ke titik pusat `Sukanegara, Kec. Tanjung Bintang, Kabupaten Lampung Selatan`. |

---
*Dokumentasi ini dikelola secara resmi untuk Pemerintah Desa Sukanegara, Kecamatan Tanjung Bintang, Kabupaten Lampung Selatan.*

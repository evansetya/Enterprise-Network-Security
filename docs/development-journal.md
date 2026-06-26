# Development Journal

**Project:** Enterprise Network Security

Dokumen ini mendokumentasikan proses pengembangan, tantangan, troubleshooting, solusi, serta pelajaran yang diperoleh selama implementasi **Enterprise Network Security**. Seluruh isi dokumen ditulis berdasarkan pengalaman implementasi project ini.

---

# 1. Challenge 1 — VLAN Trunk Configuration

## 1.1 Masalah

Saat mengonfigurasi koneksi antar switch menggunakan trunk pada **Multilayer Switch (MLS)**, interface tidak dapat diubah ke mode **trunk**. Meskipun konfigurasi telah diberikan, interface tetap berada pada mode **dynamic auto**, sehingga VLAN tidak dapat berjalan sesuai desain jaringan.

## 1.2 Analisis

Setelah dilakukan pengecekan, diketahui bahwa konfigurasi trunk hanya diterapkan pada salah satu sisi koneksi. Kondisi tersebut menyebabkan proses trunking tidak terbentuk sebagaimana mestinya.

## 1.3 Solusi

- Mengonfigurasi interface trunk pada switch yang terhubung.
- Menambahkan VLAN yang diperlukan pada jalur trunk.
- Mengonfigurasi interface yang terhubung ke end device sebagai **access port** sesuai VLAN masing-masing.

## 1.4 Pelajaran yang Didapat

Implementasi VLAN tidak hanya bergantung pada satu perangkat. Konfigurasi trunk harus dipastikan benar pada kedua sisi koneksi agar komunikasi antar VLAN dapat berjalan sesuai perancangan.

---

# 2. Challenge 2 — Extended ACL Configuration

## 2.1 Masalah

Saat mengimplementasikan **Extended ACL** untuk membatasi komunikasi antara divisi **Finance** dan **IT**, hasil simulasi tidak sesuai dengan kebijakan yang direncanakan.

Hasil yang pernah ditemui:

- Kedua host tidak dapat saling berkomunikasi.
- Kedua host justru dapat saling berkomunikasi tanpa pembatasan.

## 2.2 Analisis

Setelah beberapa kali pengujian, diketahui bahwa penerapan **Extended ACL** pada kedua sisi jaringan menyebabkan proses filtering tidak sesuai dengan tujuan implementasi.

## 2.3 Solusi

- Extended ACL hanya diterapkan pada jaringan yang membutuhkan pembatasan akses.
- Sisi lainnya tidak dikonfigurasi menggunakan Extended ACL (kecuali apabila menggunakan Standard ACL sesuai kebutuhan).

## 2.4 Pelajaran yang Didapat

Penempatan ACL merupakan bagian yang sangat penting dalam implementasi keamanan jaringan. Sebelum membuat aturan ACL, administrator harus memahami arah aliran paket agar kebijakan keamanan dapat diterapkan sesuai kebutuhan.

---

# 3. Challenge 3 — SSH Authentication

## 3.1 Masalah

SSH pada **Multilayer Switch (MLS)** tidak dapat digunakan meskipun username dan password yang dimasukkan sudah benar. Proses login selalu menampilkan pesan **"Password Incorrect"**.

## 3.2 Analisis

Konfigurasi dasar SSH telah sesuai, namun autentikasi tetap gagal dilakukan sehingga diperlukan proses verifikasi ulang terhadap konfigurasi yang telah dibuat.

## 3.3 Solusi

- Mengubah kembali password SSH.
- Melakukan restart pada perangkat simulasi.
- Melakukan pengujian ulang hingga proses login berhasil.

## 3.4 Pelajaran yang Didapat

Selain memastikan konfigurasi sudah benar, proses verifikasi dan pengujian ulang juga merupakan bagian penting dalam proses troubleshooting. Pada lingkungan simulasi, terkadang diperlukan konfigurasi ulang atau restart perangkat agar layanan dapat berjalan normal kembali.

---

# 4. Kesimpulan

Melalui project ini, saya memperoleh pengalaman dalam mengimplementasikan **VLAN**, **Extended ACL**, dan **SSH** pada jaringan enterprise sederhana.

Selain menyelesaikan konfigurasi, project ini juga memberikan pengalaman dalam melakukan troubleshooting serta proses verifikasi konfigurasi sebelum implementasi dinyatakan berhasil.

Dokumen ini dibuat sebagai catatan proses pembelajaran sekaligus dokumentasi engineering selama pengembangan project.
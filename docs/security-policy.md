# Security Policy

## 1. Pendahuluan

Dokumen ini menjelaskan kebijakan keamanan yang diterapkan pada project **Enterprise Network Security**. Seluruh kebijakan disusun untuk mendukung keamanan perangkat jaringan, melindungi akses administrasi, serta mengurangi risiko akses yang tidak sah pada lingkungan enterprise.

Kebijakan yang dijelaskan dalam dokumen ini menjadi dasar implementasi konfigurasi keamanan yang diterapkan pada Multilayer Switch dan Access Switch dalam simulasi jaringan perusahaan.

---

## 2. Tujuan Kebijakan Keamanan

Penerapan kebijakan keamanan pada project ini bertujuan untuk:

- Melindungi akses administrasi perangkat jaringan.
- Membatasi hak akses administrator sesuai kebutuhan operasional.
- Mengurangi risiko akses tidak sah terhadap perangkat jaringan.
- Memisahkan lalu lintas administrasi dari jaringan pengguna.
- Menerapkan praktik keamanan dasar yang umum digunakan pada lingkungan enterprise.

---

## 3. Kebijakan Keamanan

### 3.1 Secure Remote Management

Seluruh administrasi perangkat jaringan wajib menggunakan **Secure Shell (SSH)** sebagai metode remote management.

Penggunaan protokol **Telnet** tidak diperbolehkan karena proses autentikasi dilakukan tanpa enkripsi sehingga berisiko terhadap penyadapan kredensial administrator.

---

### 3.2 Administrator Access Control

Akses administrasi perangkat jaringan hanya diperbolehkan bagi administrator yang memiliki otorisasi.

Pembatasan akses dilakukan menggunakan **Standard Access Control List (ACL)** sehingga hanya jaringan administrator yang dapat melakukan koneksi SSH ke perangkat jaringan.

---

### 3.3 Management VLAN

Seluruh alamat IP manajemen perangkat jaringan ditempatkan pada **Management VLAN (VLAN 100)**.

Pemisahan ini bertujuan agar lalu lintas administrasi tidak bercampur dengan lalu lintas pengguna sehingga pengelolaan perangkat menjadi lebih aman dan terstruktur.

---

### 3.4 Port Security Policy

Setiap access port dikonfigurasi menggunakan **Port Security** dengan mekanisme **Sticky MAC Address**.

Kebijakan ini membatasi penggunaan access port hanya untuk perangkat yang telah terdaftar sehingga perangkat lain tidak dapat menggunakan port tanpa otorisasi.

---

### 3.5 Password Protection

Seluruh password konfigurasi perangkat wajib disimpan dalam bentuk terenkripsi menggunakan fitur **Password Encryption**.

Kebijakan ini diterapkan untuk mengurangi risiko penyalahgunaan informasi autentikasi apabila konfigurasi perangkat diakses oleh pihak yang tidak berwenang.

---

### 3.6 Login Banner

Setiap perangkat jaringan wajib menampilkan **Login Banner** sebelum proses autentikasi administrator.

Banner digunakan sebagai pemberitahuan bahwa perangkat hanya boleh diakses oleh pengguna yang memiliki otorisasi sesuai kebijakan perusahaan.

---

### 3.7 Unused Port Policy

Seluruh access port yang tidak digunakan harus dipindahkan ke **Management VLAN (VLAN 100)** dan berada dalam kondisi **shutdown**.

Kebijakan ini bertujuan untuk mengurangi potensi penyalahgunaan access port oleh perangkat yang tidak memiliki izin akses.

---

## 4. Kepatuhan Kebijakan

Berdasarkan implementasi yang telah dilakukan, seluruh kebijakan keamanan pada project ini telah diterapkan sesuai dengan ruang lingkup yang direncanakan.

Checklist implementasi kebijakan:

- ✅ Secure Shell (SSH) digunakan sebagai metode administrasi perangkat jaringan.
- ✅ Akses administrator dibatasi menggunakan Standard Access Control List (ACL).
- ✅ Management VLAN (VLAN 100) digunakan sebagai jalur administrasi perangkat.
- ✅ Port Security diterapkan pada access port menggunakan Sticky MAC Address.
- ✅ Password konfigurasi disimpan dalam bentuk terenkripsi.
- ✅ Login Banner ditampilkan sebelum proses autentikasi administrator.
- ✅ Port yang tidak digunakan dipindahkan ke Management VLAN dan dinonaktifkan.

Penerapan kebijakan tersebut membentuk lapisan keamanan dasar yang saling melengkapi sehingga mampu meningkatkan keamanan administrasi perangkat, membatasi akses yang tidak sah, serta mendukung pengelolaan jaringan yang lebih aman pada lingkungan enterprise.
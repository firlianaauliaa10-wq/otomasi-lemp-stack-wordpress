# Otomasi Deployment LEMP Stack Multi-Tier dan WordPress Menggunakan Vagrant dan Ansible

## 1. Deskripsi Proyek

Proyek ini merupakan implementasi otomasi deployment infrastruktur web server berbasis arsitektur multi-tier menggunakan Vagrant, VirtualBox, dan Ansible.

Sistem dibangun menggunakan tiga Virtual Machine (VM) dengan fungsi berbeda, yaitu Control Node, Web Server, dan Database Server. Ansible digunakan untuk mengotomatisasi instalasi dan konfigurasi layanan server, sedangkan WordPress digunakan sebagai aplikasi web yang di-deploy.

## 2. Tujuan Proyek

- Memahami konsep virtualisasi menggunakan Vagrant dan VirtualBox.
- Membangun infrastruktur server dengan arsitektur multi-tier.
- Mengimplementasikan otomasi konfigurasi server menggunakan Ansible.
- Mengotomatisasi instalasi Nginx, PHP-FPM, dan MariaDB.
- Melakukan deployment WordPress pada Web Server.
- Menguji konektivitas antara Control Node, Web Server, dan Database Server.

## 3. Teknologi yang Digunakan

| Teknologi | Fungsi |
|---|---|
| Vagrant | Mengelola dan membuat Virtual Machine |
| VirtualBox | Menjalankan virtualisasi |
| Debian | Sistem operasi Virtual Machine |
| Ansible | Otomasi konfigurasi dan deployment |
| Nginx | Web Server |
| PHP-FPM | Pemrosesan PHP |
| MariaDB | Database Server |
| WordPress | Content Management System |
| SSH | Koneksi dan administrasi server |

## 4. Arsitektur Infrastruktur

Proyek ini menggunakan tiga Virtual Machine dengan pembagian tugas sebagai berikut:

| Virtual Machine | Hostname | IP Address | Fungsi |
|---|---|---|---|
| Control Node | control-node | Sesuai konfigurasi Vagrant | Menjalankan Ansible |
| Web Server | target-web-server | 192.168.56.10 | Nginx, PHP-FPM, WordPress |
| Database Server | target-db-server | 192.168.56.11 | MariaDB |

### Alur komunikasi

1. Control Node mengelola Web Server dan Database Server melalui SSH menggunakan Ansible.
2. Web Server menjalankan WordPress menggunakan Nginx dan PHP-FPM.
3. WordPress berkomunikasi dengan MariaDB yang berada pada Database Server.
4. Pengguna mengakses WordPress melalui alamat IP Web Server.

## 5. Struktur Repository

```text
otomasi-lemp-stack-wordpress/
│
├── Vagrantfile
│
├── ansible/
│   ├── hosts.ini
│   └── setup.yml
│
├── README.md
└── .gitignore
```

## 6. Persiapan Lingkungan

Sebelum menjalankan proyek, pastikan perangkat telah memiliki:

- VirtualBox
- Vagrant
- Git
- Koneksi internet

## 7. Konfigurasi dan Deployment

### A. Menjalankan Virtual Machine

Jalankan perintah berikut pada terminal di direktori proyek yang berisi Vagrantfile:

```bash
vagrant up
```

Periksa status Virtual Machine:

```bash
vagrant status
```

Pastikan ketiga Virtual Machine berhasil dijalankan.

### B. Mengakses Control Node

Masuk ke Control Node:

```bash
vagrant ssh control
```

Periksa instalasi Ansible:

```bash
ansible --version
```

### C. Pengujian Koneksi Ansible

Masuk ke direktori `ansible` yang berisi file inventory dan playbook, kemudian jalankan:

```bash
ansible all -i hosts.ini -m ping
```

Pengujian berhasil apabila kedua server target memberikan respons `pong`.

### D. Menjalankan Playbook

Jalankan perintah:

```bash
ansible-playbook -i hosts.ini setup.yml
```

Playbook digunakan untuk melakukan konfigurasi otomatis, meliputi:

- Instalasi dan konfigurasi MariaDB pada Database Server.
- Pembuatan database dan user WordPress.
- Instalasi Nginx dan PHP-FPM pada Web Server.
- Pengunduhan dan konfigurasi WordPress.
- Pengaturan koneksi WordPress ke Database Server.
- Konfigurasi virtual host Nginx.

## 8. Hasil Pengujian

Berdasarkan implementasi yang telah dilakukan, diperoleh hasil pengujian sebagai berikut:

| No. | Pengujian | Hasil |
|---|---|---|
| 1 | Menjalankan Virtual Machine | Berhasil |
| 2 | Instalasi Ansible | Berhasil |
| 3 | Koneksi SSH ke server target | Berhasil |
| 4 | Pengujian Ansible Ping | Berhasil |
| 5 | Eksekusi Ansible Playbook | Berhasil |
| 6 | Akses WordPress Dashboard | Berhasil |

Eksekusi Ansible Playbook berhasil dilakukan pada Web Server dan Database Server dengan nilai `failed=0` dan `unreachable=0`.

WordPress juga berhasil diakses melalui Web Server setelah proses deployment selesai.

## 9. Kesimpulan

Berdasarkan hasil implementasi dan pengujian, otomasi deployment LEMP Stack multi-tier menggunakan Vagrant dan Ansible berhasil dilakukan.

Infrastruktur berhasil dibangun menggunakan tiga Virtual Machine dengan peran yang berbeda. Ansible dapat terhubung ke server target dan menjalankan konfigurasi secara otomatis. Nginx, PHP-FPM, dan MariaDB berhasil dikonfigurasi, serta WordPress berhasil diakses melalui Web Server.

Proyek ini memberikan pemahaman mengenai virtualisasi, manajemen konfigurasi, otomasi deployment, dan penerapan arsitektur web server multi-tier.

---

**Dokumentasi Proyek Praktikum**

Otomasi Deployment LEMP Stack Multi-Tier dan WordPress Menggunakan Vagrant dan Ansible.

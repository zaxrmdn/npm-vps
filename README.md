# Nginx Proxy Manager (NPM) - GitOps & CI/CD Deployment

Repositori ini mendedikasikan infrastruktur untuk **Nginx Proxy Manager (NPM)** yang dikelola secara otomatis menggunakan prinsip *GitOps* (infrastruktur sebagai kode) dan **GitHub Actions CI/CD**. Setiap perubahan konfigurasi yang di-*push* ke repositori ini akan langsung diperbarui secara otomatis di server VPS.

---

## 🏗️ Architecture & Automation Workflow

1. **Version Control:** Berkas konfigurasi `docker-compose.npm.yml` disimpan dan dilacak versinya di GitHub.
2. **CI/CD Pipeline:** GitHub Actions memicu *workflow* otomatis saat terjadi perubahan pada direktori `npm/` di *branch* `main`.
3. **Secure Deployment:** GitHub Actions melakukan autentikasi via **SSH Private Key** untuk memperbarui *container* langsung di VPS (`/opt/vps-stack/npm`).

---

## 🚀 Quick Start & Usage

### 1. Prasyarat GitHub Secrets
Pastikan *Secrets* berikut sudah dikonfigurasi di menu **Settings > Secrets and variables > Actions** pada repositori GitHub Anda:
* `SSH_PRIVATE_KEY` : Kunci privat SSH untuk mengakses VPS.
* `VPS_IP` : Alamat IP publik VPS Anda.
* `VPS_USER` : *Username* VPS (contoh: `root` atau `ubuntu`).

### 2. Akses Web UI Admin NPM
Setelah *pipeline* GitHub Actions berjalan sukses, akses panel manajemen melalui browser:
`http://IP-VPS-ANDA:81`

* **Default Email:** `admin@example.com`
* **Default Password:** `changeme` 
> ⚠️ **Catatan Keamanan:** Segera ubah email dan kata sandi bawaan setelah login pertama kali, serta atur *proxy host* Anda beserta sertifikat SSL Let's Encrypt.

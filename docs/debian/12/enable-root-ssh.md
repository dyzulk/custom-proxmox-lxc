# 📦 LXC Template Customizer – Ubuntu 24.04 Mengaktifkan Login Root dan Password Authentication

Modifikasi file template LXC untuk mengaktifkan login root dan autentikasi password melalui SSH.

---

## ✅ Tujuan

Template hasil modifikasi ini akan menghasilkan container LXC dengan konfigurasi SSH yang memungkinkan login sebagai root menggunakan password.

---

## 🧰 Prasyarat

- Sistem Proxmox VE atau Debian/Ubuntu server
- Template `.tar.zst` dari LXC (misal: `ubuntu-24.04-standard_24.04-2_amd64.tar.zst`)
- Tool `zstd` dan `tar`

---

## 🛠️ Langkah-Langkah

### 1. Masuk ke direktori penyimpanan template

```bash
cd /var/lib/vz/template/cache/
```

*Sesuaikan jika path template berbeda.*

### 2. Ekstrak template ke direktori kerja

```bash
mkdir ubuntu-24.04-workdir
```
```bash
tar --use-compress-program=unzstd -xvf ubuntu-24.04-standard_24.04-2_amd64.tar.zst -C ubuntu-24.04-workdir
```

### 3. Ubah konfigurasi SSH

```bash
nano ubuntu-24.04-workdir-workdir/etc/ssh/sshd_config
```

Cari dan ubah baris berikut:

```sshd_config
#PermitRootLogin prohibit-password
#PasswordAuthentication yes
```

Menjadi:

```sshd_config
PermitRootLogin yes
PasswordAuthentication yes
```

*Pastikan baris-baris tersebut tidak dikomentari (tidak diawali dengan #).*

### 4. Re-pack kembali template

```bash
tar --use-compress-program=zstd -cf ubuntu-24.04-standard_24.04-2_amd64.tar.zst -C ubuntu-24.04-workdir .
```

```bash
rm -rf ubuntu-24.04-workdir
```

## 📌 Catatan Tambahan

- Setelah container dibuat dari template ini, pastikan untuk mengatur password root dengan perintah:

```bash
pct exec <VMID> passwd
```

*Gantilah <VMID> dengan ID container yang sesuai.*

- Untuk memastikan SSH berjalan saat container dinyalakan, aktifkan layanan SSH:
```bash
pct exec <VMID> systemctl enable ssh
```

## 📜 Lisensi

Proyek ini menggunakan lisensi [MIT](LICENSE) dan hanya dimaksudkan untuk penggunaan pribadi atau internal.


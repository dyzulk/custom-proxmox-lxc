# 🧱 Custom Proxmox LXC Templates

Kumpulan dokumentasi dan skrip modifikasi untuk menyesuaikan **template container LXC di Proxmox VE** agar sesuai dengan kebutuhan pengguna, seperti:

- Menyesuaikan source list
- Mengaktifkan login root via SSH
- Menyesuaikan konfigurasi awal container
- Dukungan multi-distro: Ubuntu, Debian, CentOS, Fedora, AlmaLinux

---

## 📌 Tujuan

Proyek ini bertujuan untuk memberikan panduan langkah demi langkah agar Anda dapat:

- Mengkustom template `.tar.zst` LXC sebelum digunakan
- Menyusun ulang konfigurasi default seperti repository, SSH, dan sistem
- Mempersingkat proses deployment container LXC

---

## 📂 Struktur Direktori

```
docs/
├── ubuntu/
│ ├── 20.04/
│ ├── 22.04/
│ ├── 24.04/
│ └── 25.04/
├── debian/
│ ├── 11/
│ └── 12/
├── centos/
│ └── 9-stream/
├── fedora/
│ ├── 41/
│ └── 42/
└── almalinux/
└── 9/
```

Setiap folder berisi panduan Markdown (`.md`) yang menjelaskan perubahan spesifik untuk versi distro tersebut.

---

## 🧑‍💻 Contoh Panduan

- 🔄 [Mengganti Source List Ubuntu 24.04](docs/ubuntu/24.04/change-source-list.md)
- 🔐 [Mengaktifkan Login Root & Password SSH](docs/ubuntu/24.04/enable-root-ssh.md)

---

## 🚀 Cara Menggunakan Template Hasil Modifikasi

1. Ekstrak file template `.tar.zst`
2. Modifikasi konfigurasi sesuai panduan di dalam repo ini
3. Re-pack kembali ke `.tar.zst`
4. Upload ke `/var/lib/vz/template/cache/` di Proxmox
5. Gunakan template tersebut untuk membuat container baru

---

## ⚠️ Catatan

- Pastikan menggunakan Proxmox terbaru agar kompatibel dengan sistem modern seperti `systemd`, `netplan`, atau `NetworkManager`.
- Panduan disediakan apa adanya dan disesuaikan dengan pengalaman pribadi.

---

## 🧑‍🔧 Kontribusi

Pull request sangat diterima untuk:

- Menambahkan panduan untuk distro lainnya
- Koreksi kesalahan dalam dokumentasi
- Perbaikan struktur, gaya penulisan, dan teknis lainnya

---

## 📄 Lisensi

Lisensi: [MIT License](LICENSE)

---

## ☕ Dukungan

Jika proyek ini membantu Anda, pertimbangkan untuk memberikan ⭐ di GitHub.

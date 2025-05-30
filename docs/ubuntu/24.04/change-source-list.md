# 📦 LXC Template Customizer – Ubuntu 24.04 dengan Mirror NevaCloud

Modifikasi file template LXC `ubuntu-24.04-standard_24.04-2_amd64.tar.zst` agar langsung menggunakan repository dari [mirror NevaCloud](https://mirror.nevacloud.com) pada `/etc/apt/sources.list`.

---

## ✅ Tujuan

Template hasil modifikasi ini akan menghasilkan container LXC berbasis Ubuntu 24.04 dengan konfigurasi mirror lokal NevaCloud, mempercepat proses update dan install paket di Indonesia.

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

Sesuaikan jika path template berbeda.

### 2. Ekstrak template ke direktori kerja

```bash
mkdir ubuntu-24.04-workdir
```
```bash
tar --use-compress-program=unzstd -xvf ubuntu-24.04-standard_24.04-2_amd64.tar.zst -C ubuntu-24.04-workdir
```

### 3. Ubah repository di dalam sources.list

```bash
nano ubuntu-24.04-workdir/etc/apt/sources.list
```

Ganti seluruh isinya menjadi:

```source.list
deb https://mirror.nevacloud.com/ubuntu/ubuntu-archive/ noble main restricted universe multiverse
deb https://mirror.nevacloud.com/ubuntu/ubuntu-archive/ noble-updates main restricted universe multiverse
deb https://mirror.nevacloud.com/ubuntu/ubuntu-archive/ noble-security main restricted universe multiverse
```

### 4. Re-pack kembali template

```bash
tar --use-compress-program=zstd -cf ubuntu-24.04-standard_24.04-2_amd64.tar.zst -C ubuntu-24.04-workdir .
```

```bash
rm -rf ubuntu-24.04-workdir
```

## 📌 Catatan Tambahan

Mirror NevaCloud bersifat publik dan cepat diakses dari jaringan Indonesia.

Template yang telah dimodifikasi dapat langsung digunakan untuk membuat container baru dengan `pct create`.

## 📜 Lisensi

Proyek ini menggunakan lisensi [MIT](LICENSE) dan hanya dimaksudkan untuk penggunaan pribadi atau internal.



# ⁦Perbaiki Termux Sudo / Root (Patcher Tsu)⁩

![⁦Pemandangan⁩](https://komarev.com/ghpvc/?username=Shirotaa-z-wif-root&label=Repository%20Views&color=0e75b6&style=flat)
![⁦Termux⁩](https://img.shields.io/badge/Termux-Android-green?logo=android)
![⁦Akar⁩](https://img.shields.io/badge/Root-Required-red)
![⁦Sudo⁩](https://img.shields.io/badge/Fix-Sudo%2FTsu-blue)

**[⁦📖 Read In English  (baca dalam bahasa Inggris)⁩](README.md)**

**⁦"Tidak terdeteksi Superuser terdeteksi" di Android Termux atau solusi lengkap dan otomatis untuk masalah "izin root".⁩**

**⁦Kata kunci:⁩**`termux root fix bangla`⁦,⁩ `termux sudo error`⁦,⁩ `tsu patcher`⁦,⁩ `kernelsu termux fix`⁦,⁩ `magisk termux root`⁦,⁩ `termux su binary not found`⁦,⁩ `android terminal root`⁦,⁩ `ashrafuljoy62`

---

## ⁦Apa masalahnya⁩
⁦Sering kali perangkat Android Anda di-root tetapi (terutama di versi terbaru kernelsu atau majelis), default Termux⁩ `tsu` ⁦Paketnya adalah Binary Root (⁩`su`⁦) Tidak ditemukan. Alasannya adalah bahwa skrip default⁩ `/debug_ramdisk/su` ⁦Atau sistem tidak mencari di lokasi khusus lain dari metode rute sistem.⁩

⁦Repositori ini telah diberikan naskah otomatis yang memindai semua matriks rute yang mungkin, menghapus biner yang dibuat oleh masalah dan dengan benar⁩ `sudo` ⁦Pengaturan lingkungan.⁩

---

## ⁦Metode 1: Script otomatis (Disarankan)⁩
⁦Ini adalah metode tercepat dan andal. Itu⁩ `fix.sh` ⁦Mengunduh skrip, memindai lokasi akar, instal paket yang diperlukan dan membawa Anda ke root shell secara langsung.⁩

⁦Jalankan perintah berikut di terminal termux Anda:⁩

```bash
curl -sO [https://raw.githubusercontent.com/Shirotaa-z/wif/main/fix.sh](https://raw.githubusercontent.com/Shirotaa-z/fix-termux-root/main/fix.sh) && chmod +x fix.sh && ./fix.sh
```

---

## ⁦Metode 2: Perintah satu baris (opsi)⁩
⁦Jika skrip otomatis tidak berfungsi, atau Anda⁩ `tsu` ⁦Jangan hanya ingin memperbaikinya tanpa menghapus paket, tetapi jalankan perintah berikut. Ini akan membuat cadangan file dan memperbaikinya dengan:⁩

```bash
pkg update && pkg install tsu -y
cp $PREFIX/bin/tsu $PREFIX/bin/tsu.bak && sed -i 's|^SU_BINARY_SEARCH=.*|SU_BINARY_SEARCH=("/system/xbin/su" "/system/bin/su" "/debug_ramdisk/su" "/sbin/su")|' $PREFIX/bin/tsu && echo "tsu patched successfully"
```

**⁦Verifikasi:⁩** ⁦Di akhir perintah⁩ `tsu` ⁦Atau⁩ `sudo su` ⁦Jenis. Jika⁩ `#` ⁦Lihat prompt, itu berarti Anda telah berhasil menerima akses root.⁩

---

## ⁦Metode 3: Edit manual (opsi)⁩
⁦Jika Anda ingin secara manual secara manual secara manual, Anda dapat mengedit file konfigurasi menggunakan editor teks.⁩

### ⁦1. Pasang alat dan repositori yang diperlukan:⁩
```bash
pkg install tsu nano file root-repo sudo -y
```

### ⁦Dua. Buka file TSU dengan Nano Editor:⁩
```bash
nano $PREFIX/bin/tsu
```

### ⁦3. Perbaiki Terapkan:⁩
⁦Gulir ke bawah dan ke bawah⁩ `SU_BINARY_SEARCH=` ⁦Cari tahu garis yang dimulai dengan. Lalu di dalam gelang⁩ `"/debug_ramdisk/su"` ⁦Tambahkan setelah mengubah garis akan terlihat seperti persis:⁩

```text
SU_BINARY_SEARCH=("/system/xbin/su" "/system/bin/su" "/debug_ramdisk/su")
```

### ⁦4. Simpan dan keluar:⁩
* `CTRL + X` ⁦Tekan⁩
* `Y` ⁦Tekan (untuk YA)⁩
* `Enter` ⁦Tekan⁩

---

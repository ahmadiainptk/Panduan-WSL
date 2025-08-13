# Panduan Penyiapan WSL
## Ringkasan lengkap untuk lingkungan pengembangan Web & Analisis Data.

1. Pemilihan Distro & Instalasi Awal
Langkah A: Persiapan Awal WSL
Sebelum menginstal distro, pastikan fitur WSL sudah aktif di Windows. Buka PowerShell sebagai Administrator dan jalankan perintah berikut. Perintah ini akan mengurus semua yang diperlukan.

```console
wsl --install
```

Anda mungkin perlu me-restart komputer Anda setelah proses ini selesai.

Langkah B: Melihat & Menginstal Distro
Setelah WSL aktif, Anda bisa melihat semua distribusi Linux yang tersedia untuk diinstal dari terminal.

```console
wsl --list --online
```

Gunakan perintah berikut untuk menginstal distro pilihan Anda. Cukup jalankan salah satu.

Untuk menginstal Ubuntu (Rekomendasi):

```console
wsl --install -d Ubuntu
```

Untuk menginstal Arch:

```console
wsl --install -d Arch
```

Rekomendasi: Ubuntu vs Arch
Untuk pengembangan aplikasi web, Android, dan analisis statistik dengan Python di WSL, Ubuntu adalah pilihan yang lebih praktis dan stabil, terutama bagi pemula dan profesional yang menginginkan lingkungan yang "siap pakai".

Arch Linux adalah pilihan yang kuat bagi pengguna berpengalaman yang menginginkan kontrol penuh, sistem minimalis, dan akses ke perangkat lunak terbaru (bleeding-edge).

Kesimpulan: Gunakan Ubuntu untuk stabilitas dan kemudahan penggunaan.

2. Penyiapan Dasar WSL Ubuntu
Langkah pertama setelah menginstal Ubuntu adalah memperbarui sistem dan menginstal perkakas esensial.

Perbarui daftar paket dan upgrade sistem:

```console
sudo apt update && sudo apt upgrade -y
```

Instal perkakas build esensial:

```console
sudo apt install build-essential -y
```

Instal Git untuk version control:

```console
sudo apt install git -y
```

Konfigurasi Git (ganti dengan info Anda):

```console
git config --global user.name "Nama Anda"
```
```console
git config --global user.email "email@anda.com"
```

3. Integrasi Visual Studio Code
Prinsip utamanya adalah instal VS Code di Windows, lalu gunakan ekstensi untuk terhubung ke WSL.

Unduh dan instal VS Code untuk Windows.

Buka VS Code, buka panel Ekstensi (Ctrl+Shift+X).

Cari dan instal ekstensi "Remote - WSL" dari Microsoft.

Untuk membuka proyek, navigasi ke folder proyek di terminal WSL dan jalankan:

code .

4. Peningkatan Terminal dengan Zsh
Ganti shell Bash standar dengan Zsh dan plugin untuk pengalaman terminal yang jauh lebih baik.

Langkah 1: Instal Zsh & Oh My Zsh
Instal Zsh:

```console
sudo apt install zsh -y
```

Instal Oh My Zsh (framework manajemen Zsh):

```console
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Saat diminta, setujui untuk menjadikan Zsh sebagai shell default Anda.

Langkah 2: Instal Plugin
Instal plugin Autosuggestions (saran berdasarkan histori):

```console
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

Instal plugin Syntax Highlighting (mewarnai sintaks perintah):

```console
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Langkah 3: Aktifkan Plugin
Buka file ~/.zshrc dengan editor (misal: nano ~/.zshrc) dan ubah baris plugins menjadi:

```console
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

Terapkan perubahan dengan membuka ulang terminal atau menjalankan:

```console
source ~/.zshrc
```

5. Penyiapan Lingkungan Pengembangan
a. Pengembangan Web (Node.js)
Gunakan nvm (Node Version Manager) untuk mengelola versi Node.js.

Instal nvm:

```console
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

Muat ulang terminal Anda, lalu instal versi LTS (Long-Term Support) dari Node.js:

```console
nvm install --lts
```

b. Analisis Statistik (Python)
Gunakan Miniconda untuk membuat lingkungan Python yang terisolasi.

Unduh installer Miniconda:

```console
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

Jalankan installer (ikuti petunjuk di layar):

```console
bash Miniconda3-latest-Linux-x86_64.sh
```

Muat ulang terminal, lalu buat lingkungan baru (ganti 'myenv' dengan nama pilihan Anda):

```python
conda create --name myenv python=3.10
```

Aktifkan lingkungan:

```console
conda activate myenv
```

Instal pustaka data science populer:

```console
pip install numpy pandas matplotlib scikit-learn jupyterlab
```

6. Alat History Shell (Opsional)
Untuk melihat riwayat perintah dengan lebih canggih, pertimbangkan untuk menginstal salah satu dari alat berikut.

Atuin: Pilihan paling kuat dengan sinkronisasi antar perangkat dan statistik.

HSTR: Pencarian interaktif yang ringan dan cepat.

McFly: Pengganti Ctrl+R yang cerdas dan kontekstual.

Contoh instalasi Atuin:

Jalankan skrip instalasi:

```console
bash <(curl https://raw.githubusercontent.com/atuinsh/atuin/main/install.sh)
```

Tambahkan baris berikut ke ~/.zshrc untuk mengaktifkan Atuin:

```console
eval "$(atuin init zsh)"
```

Muat ulang terminal:

```console
source ~/.zshrc
```

🏗️ Struktur Proyek & Integrasi GitHub
Panduan ini menjelaskan cara membuat struktur direktori proyek dan mengintegrasikannya dengan GitHub.

1. Buat Struktur Direktori Proyek
Buat struktur direktori yang rapi di terminal WSL Anda.

Bash

# Buat direktori utama dan sub-direktori yang diperlukan
mkdir -p ~/projects/computer_vision_basics/{data,notebooks,scripts,models,outputs}

# Masuk ke direktori proyek
cd ~/projects/computer_vision_basics
Struktur Direktori (Hasil Akhir):

computer_vision_basics/
├── data/       # Untuk menyimpan dataset mentah atau yang sudah diproses
├── notebooks/  # Jupyter Notebooks untuk eksplorasi dan prototyping
├── scripts/    # Skrip Python untuk training/evaluasi
├── models/     # File model yang telah di-train
└── outputs/    # Hasil eksperimen, visualisasi, dll.
2. Konfigurasi Git Awal
Pastikan Git terinstal dan konfigurasikan identitas Anda.

A. Instalasi Git (Jika Belum Ada)
Bash

# Perbarui daftar paket
sudo apt update

# Instal Git
sudo apt install git -y
B. Konfigurasi User Global
PENTING: Ganti [NAMA_ANDA] dan [EMAIL_ANDA] dengan nama dan email yang Anda gunakan di GitHub.

Bash

git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Cek kembali konfigurasi
git config --global --list
C. Cek Lokasi
Bash

# Cek direktori saat ini
pwd

# Cek file tersembunyi
ls -la
3. Inisialisasi Repositori GitHub
Langkah-langkah untuk membuat repositori lokal dan menghubungkannya ke GitHub.

A. Buat File .gitignore
File ini akan memberitahu Git file atau folder mana yang TIDAK boleh diunggah ke GitHub (misalnya data besar, model, atau variabel lingkungan).

Bash

cat > .gitignore <<'EOF'
# File Python
__pycache__/
*.pyc

# Konfigurasi Environment
.env

# Data & Hasil Training
data/
models/
outputs/

# Jupyter Notebook Checkpoints
.ipynb_checkpoints/
EOF
B. Inisialisasi dan Commit
Bash

# Inisialisasi repositori Git lokal
git init

# Tambahkan semua file (termasuk .gitignore)
git add .

# Commit awal
git commit -m "Initial commit: project structure"
C. Hubungkan ke Repositori Jarak Jauh (HTTPS)
Kami menggunakan alias yang aman untuk URL: https://github.com/YourGitHubUser/computer_vision_basics.git

Bash

# Tambahkan remote origin (Ganti dengan URL Repo Anda)
git remote add origin https://github.com/YourGitHubUser/computer_vision_basics.git

# Ganti nama branch master ke main (standar baru)
git branch -M main

# Unggah ke GitHub (Pertama kali)
git push -u origin main
4. Beralih ke Koneksi SSH (Opsional, Lebih Aman)
Menggunakan SSH lebih aman dan tidak perlu memasukkan password berulang kali.

A. Buat Kunci SSH
PENTING: Ganti email dengan email Anda.

Bash

# Buat pasangan kunci ed25519 baru
ssh-keygen -t ed25519 -C "your.email@example.com"

# Tampilkan public key (Salin kunci ini ke Settings -> SSH and GPG keys di GitHub Anda)
cat ~/.ssh/id_ed25519.pub
B. Perbarui Remote Origin (ke SSH)
Bash

# Hapus remote origin yang lama (HTTPS)
git remote remove origin

# Tambahkan remote origin baru dengan URL SSH (Ganti dengan URL SSH Repo Anda)
git remote add origin git@github.com:YourGitHubUser/computer_vision_basics.git

# Unggah kembali
git push -u origin main
C. Verifikasi
Bash

# Cek koneksi remote
git remote -v

# Cek status
git status

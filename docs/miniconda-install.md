💻 Panduan Setup Environment Computer Vision (WSL/Ubuntu + Miniconda)Ini adalah panduan langkah demi langkah untuk menyiapkan lingkungan pengembangan Computer Vision yang rapi dan terisolasi menggunakan Miniconda di WSL (Ubuntu).⚙️ 1. Instalasi Miniconda di WSL (Ubuntu)Buka terminal Ubuntu (di WSL). Jalankan perintah berikut langkah demi langkah:Bash# Masuk ke direktori home
cd ~

# Unduh installer Miniconda
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# Jalankan installer
bash Miniconda3-latest-Linux-x86_64.sh
Saat Instalasi:Lisensi: Tekan [Enter] terus sampai bawah, lalu ketik yes.Lokasi Install: Biarkan default (/home/<username>/miniconda3).Setelah Selesai:Bash# Muat ulang shell
source ~/.bashrc

# Setuju dengan Terms of Service (TOS) Conda untuk channel utama
conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/main
conda tos accept --override-channels --channel https://repo.anaconda.com/pkgs/r
Verifikasi:Bashconda --version
💡 Keterangan: Jika muncul versi, instalasi sukses. Sekarang Anda punya manajer environment terpisah yang aman dari konflik dependency global.🧩 2. Buat Environment Project Computer VisionKita akan membuat environment baru bernama cv_env:Bash# Buat environment dengan Python 3.10
conda create -n cv_env python=3.10 -y

# Aktifkan environment
conda activate cv_env

# Upgrade pip di environment ini
python -m pip install --upgrade pip
Instalasi Paket Dasar:Bashpip install numpy pandas matplotlib opencv-python torch torchvision tqdm
Opsional (Bisa ditambahkan nanti):Bashpip install jupyterlab albumentations scikit-learn ultralytics
Verifikasi PyTorch:Bashpython -c "import torch; print(torch.__version__)"
✅ Jika muncul versi tanpa error, berarti PyTorch siap.⚙️ Pilihan Setup Realistis (AMD/CPU-Only)Mengingat keterbatasan dukungan GPU AMD di Windows/WSL untuk PyTorch saat ini, pilihan yang paling stabil dan minim masalah adalah CPU-only:1. Jalankan CPU-only (Stabil, Tanpa Ribet)Ini adalah cara yang paling aman dan dijamin berjalan. Instal PyTorch tanpa dukungan CUDA/GPU khusus (jika belum terinstal di langkah sebelumnya):Bash# Instal PyTorch versi CPU-only (gunakan ini jika ada error di langkah 2)
pip install torch torchvision torchaudio
Cek Ketersediaan Device:Bashpython - <<'PY'
import torch
print("CUDA available:", torch.cuda_is_available())
print("Device:", torch.device("cuda" if torch.cuda_is_available() else "cpu"))
PY
⚙️ Output yang Diharapkan: CUDA available: False. Ini menunjukkan PyTorch akan menggunakan CPU.🚀 3. Uji Coba Training Sederhana (quick_train.py)Pastikan Anda berada di environment cv_env (atau environment yang telah Anda buat).A. Buat File PythonBashnano quick_train.py
B. Tempel Script Berikut ke NanoTempelkan kode ini ke editor nano Anda:Pythonimport torch
import torchvision
from torchvision import datasets, transforms

# Cek apakah CUDA tersedia
device = torch.device("cuda" if torch.cuda_is_available() else "cpu")
print("Device yang digunakan:", device)

# Download dataset MNIST
transform = transforms.Compose([transforms.ToTensor()])
train_data = datasets.MNIST(root="data", train=True, download=True, transform=transform)

# Buat DataLoader
train_loader = torch.utils.data.DataLoader(train_data, batch_size=64, shuffle=True)

# Buat model sederhana
model = torch.nn.Sequential(
    torch.nn.Flatten(),
    torch.nn.Linear(28 * 28, 128),
    torch.nn.ReLU(),
    torch.nn.Linear(128, 10)
).to(device)

optimizer = torch.optim.Adam(model.parameters(), lr=0.001)
loss_fn = torch.nn.CrossEntropyLoss()

# Satu epoch training sederhana
for batch_idx, (X, y) in enumerate(train_loader):
    X, y = X.to(device), y.to(device)
    pred = model(X)
    loss = loss_fn(pred, y)

    optimizer.zero_grad()
    loss.backward()
    optimizer.step()

    if batch_idx % 100 == 0:
        print(f"Batch {batch_idx}, Loss: {loss.item():.4f}")

print("Training selesai.")
C. Simpan dan KeluarSimpan: Tekan Ctrl + O $\rightarrow$ [Enter]Keluar: Tekan Ctrl + XD. Jalankan ScriptBashpython quick_train.py
🧠 Rekomendasi Pribadi (Efisien dan Minim Stres)1. Tetap di WSL + CPU-only PyTorch.2. Fokus dulu pada konsep, pipeline, augmentasi data, dan evaluasi.3. Saat butuh GPU $\rightarrow$ pindah project itu ke Colab (Google Colaboratory).

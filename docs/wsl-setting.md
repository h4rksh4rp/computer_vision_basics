Environment & tooling (konkret langkah—Windows user)

Kamu di Windows — tidak masalah. Tapi pakai WSL2 supaya workflow Linux-native berjalan mulus.

Langkah setup singkat

1.Aktifkan WSL2 (Windows Powershell as Admin):

wsl --install
wsl --set-default-version 2


2.Install Ubuntu dari Microsoft Store,terus buka ubuntu di start menu nanti muncul terminal dan set username/password.

3.Di WSL:

# update
sudo apt update && sudo apt upgrade -y

# install essentials
sudo apt install git build-essential curl -y

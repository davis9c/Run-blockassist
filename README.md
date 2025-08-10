# Run-blockassist
# BlockAssist on WSL (Windows Subsystem for Linux)

Panduan ini menjelaskan cara menjalankan **BlockAssist** di **WSL2 + Ubuntu 22.04** menggunakan **Python virtual environment (`venv`)** agar environment bersih dan terisolasi.

---

## 1. Persiapan WSL

Pastikan sudah menggunakan **WSL2** dan **Ubuntu 22.04**.

Cek versi WSL:
```powershell
wsl --version
```

Jika belum terpasang:
```powershell
wsl --install -d Ubuntu-22.04
```

---

## 2. Update & Install Tools Dasar

Masuk ke Ubuntu (WSL) dan jalankan:
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git curl build-essential python3-venv -y
```

---

## 3. Clone Repository BlockAssist

```bash
git clone https://github.com/gensyn-ai/blockassist.git
cd blockassist
```

---

## 4. Install Java

BlockAssist membutuhkan Java 17:
```bash
sudo apt install openjdk-17-jdk -y
java -version
```

---

## 5. (Opsional) Install Python 3.10 via pyenv

Jika Python default Anda < 3.10, gunakan **pyenv**:

```bash
curl https://pyenv.run | bash
```

Tambahkan ke `~/.bashrc`:
```bash
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv virtualenv-init -)"
```

Aktifkan perubahan:
```bash
source ~/.bashrc
```

Install dan set Python 3.10:
```bash
pyenv install 3.10
pyenv global 3.10
```

---

## 6. Buat Virtual Environment (`venv`)

```bash
python -m venv .venv
source .venv/bin/activate
```

> Untuk keluar dari venv:  
> ```bash
> deactivate
> ```

---

## 7. Install Dependensi Python

Pastikan masih di dalam venv:
```bash
pip install --upgrade pip
pip install psutil readchar
```

---

## 8. Install Node.js & Yarn

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install --lts
npm install --global yarn
```

---

## 9. Jalankan BlockAssist

Masih di dalam venv:
```bash
python run.py
```

---

## 10. Main & Training

1. Masukkan **Hugging Face API Token** (*Write access*).
2. Login ke **Gensyn testnet** via browser Windows (link akan muncul di terminal).
3. Tunggu hingga **2 jendela Minecraft** muncul.
4. Tekan **ENTER** di terminal.
5. Fokus ke Minecraft, tekan **ENTER** lagi, lalu ikuti instruksi permainan.
6. Setelah selesai, tekan **ESC** di Minecraft dan **ENTER** di terminal.
7. Model akan otomatis di-train dan di-upload ke Hugging Face + Gensyn smart contract.

---

## Catatan WSL

- **Minecraft GUI tidak bisa dijalankan langsung di WSL biasa** (hanya bisa di WSLg Windows 11).
- Solusi:
  - Jalankan backend AI/training di WSL.
  - Jalankan Minecraft di Windows secara terpisah.
- Untuk performa terbaik, gunakan PC dengan GPU dan RAM cukup.

---

## Referensi

- [BlockAssist GitHub](https://github.com/gensyn-ai/blockassist)
- [BlockAssist Docs](https://docs.gensyn.ai/testnet/blockassist/getting-started)

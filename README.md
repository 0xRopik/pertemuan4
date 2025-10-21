# 🎓 Analisis Kelulusan Mahasiswa — Full Tutorial

Selamat datang di proyek **Analisis Kelulusan Mahasiswa**!  
Di sini kamu akan belajar **langkah demi langkah** bagaimana cara:
- Membuat dataset sendiri 🧮  
- Membersihkan dan menganalisis data 📊  
- Membuat fitur baru (feature engineering) 💡  
- Membagi dataset untuk pelatihan model Machine Learning 🤖  
- Dan menjalankan semuanya langsung di **Jupyter Notebook** atau **Google Colab** 🚀

Proyek ini dirancang agar mudah dipahami, bahkan untuk pemula yang baru belajar analisis data!

---

## 🧭 Daftar Isi
1. [Tentang Proyek](#tentang-proyek)
2. [Struktur Folder](#struktur-folder)
3. [Langkah Persiapan Awal](#langkah-persiapan-awal)
4. [Cara Menjalankan Proyek](#cara-menjalankan-proyek)
5. [Penjelasan Notebook](#penjelasan-notebook)
6. [Visualisasi dan Analisis](#visualisasi-dan-analisis)
7. [Feature Engineering](#feature-engineering)
8. [Splitting Dataset](#splitting-dataset)
9. [Cara Upload ke GitHub](#cara-upload-ke-github)
10. [Troubleshooting](#troubleshooting)
11. [Identitas](#identitas)

---

## 🧠 Tentang Proyek

Proyek ini dibuat untuk menganalisis **faktor-faktor yang memengaruhi kelulusan mahasiswa**.  
Data mencakup IPK, absensi, waktu belajar, dan status kelulusan.

### 📋 Tujuan
- Melatih pemahaman dasar tentang analisis data.
- Membiasakan penggunaan *library* Python untuk Data Science.
- Membuat dataset bersih dan siap untuk model Machine Learning.

---
## 🛠 Langkah Persiapan Awal

### 1️⃣ Install Python
Pastikan sudah menginstal **Python 3.8 atau lebih baru**.  
Cek versi dengan:
```
python --version
Kalau belum ada, download di:
🔗 https://www.python.org/downloads/
```

🚀 Cara Menjalankan Proyek
```

Kamu bisa menjalankan proyek ini dengan dua cara:
via Jupyter Notebook (offline) atau Google Colab (online).

💻 Opsi 1 — Jalankan di Jupyter Notebook

Buka terminal di folder proyek.

Jalankan perintah:

jupyter notebook analisis_kelulusan.ipynb


Browser akan terbuka otomatis, dan kamu bisa mulai menekan tombol Run All.
```

☁️ Opsi 2 — Jalankan di Google Colab
```

Buka https://colab.research.google.com/

Klik Upload, lalu unggah:

analisis_kelulusan.ipynb

kelulusan_mahasiswa.csv

Setelah file terbuka, pilih menu Runtime → Run all

Semua proses otomatis dijalankan, hasil dan grafik langsung muncul.
```

🧩 Penjelasan Notebook
🧾 1. Data Collection

Membaca dataset dari CSV menggunakan pandas:

import pandas as pd
df = pd.read_csv('kelulusan_mahasiswa.csv')
df.head()

🧹 2. Data Cleaning

Mengecek missing value

Menghapus duplikat

Memastikan semua kolom bertipe data yang sesuai

df.info()
df.drop_duplicates(inplace=True)

📊 3. Exploratory Data Analysis (EDA)

Menampilkan statistik deskriptif:

df.describe()


Visualisasi:

import seaborn as sns
import matplotlib.pyplot as plt

sns.histplot(df['IPK'])
sns.scatterplot(x='Waktu_Belajar_Jam', y='IPK', hue='Lulus', data=df)
plt.show()

🎨 Visualisasi dan Analisis

Beberapa grafik yang akan muncul:

Histogram distribusi IPK

Scatter plot hubungan waktu belajar vs IPK

Heatmap korelasi antar variabel

Interpretasi hasil:

Semakin tinggi IPK dan waktu belajar → semakin tinggi peluang lulus.

Absensi tinggi → cenderung tidak lulus.

⚙️ Feature Engineering

Menambahkan kolom baru:

df['Rasio_Absensi'] = df['Jumlah_Absensi'] / df['Waktu_Belajar_Jam']
df['IPK_x_Study'] = df['IPK'] * df['Waktu_Belajar_Jam']


Simpan dataset hasil olahan:

df.to_csv('processed_kelulusan.csv', index=False)

🔀 Splitting Dataset

Bagi data untuk pelatihan model Machine Learning:

from sklearn.model_selection import train_test_split

train, test = train_test_split(df, test_size=0.3, random_state=42)

🧾 Hasil Analisis

Tidak ada missing value.

Korelasi positif antara waktu belajar dan IPK terhadap kelulusan.

Fitur baru (Rasio_Absensi dan IPK_x_Study) bisa meningkatkan akurasi model.

🧰 Troubleshooting
Masalah	Solusi
pip not recognized	Pastikan Python & pip sudah diatur di PATH
ModuleNotFoundError	Jalankan pip install -r requirements.txt
Grafik tidak muncul di Colab	Tambahkan %matplotlib inline di awal notebook
File CSV tidak ditemukan	Pastikan file berada di folder yang sama dengan notebook



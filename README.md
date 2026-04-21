# 🤟 Real-Time BISINDO Sign Language to Voice Conversion

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

## 📖 Project Overview
Sistem ini adalah solusi *End-to-End Machine Learning* dan *Computer Vision* yang dirancang untuk menerjemahkan Bahasa Isyarat Indonesia (BISINDO) menjadi suara secara *real-time*. 

Dikembangkan dengan metodologi **CRISP-DM**, sistem ini memecahkan masalah aksesibilitas komunikasi bagi komunitas tunarungu dengan mengekstraksi titik koordinat tangan (*spatial landmarks*) melalui rekaman video langsung, mengklasifikasikannya menjadi teks, dan menyintesisnya menjadi suara tanpa jeda yang signifikan.

---

## 📦 Microservices Architecture & Repositories

Untuk menjaga *separation of concerns* dan skalabilitas, proyek ini dibagi menjadi tiga repositori terpisah. **Silakan kunjungi repositori di bawah ini untuk melihat *source code* spesifik:**

### 1. 🧠 [Model & Training Engine]([LINK_REPO_TRAINING])
Repositori ini berisi seluruh proses *Data Science* dan *Machine Learning*.
* **Isi:** Skrip ekstraksi fitur MediaPipe, dataset, *Exploratory Data Analysis* (EDA), dan skrip pelatih model Random Forest.
* **Fokus:** Akurasi pengenalan pola koordinat tangan.

### 2. ⚙️ [Backend API Server]([LINK_REPO_BACKEND])
Repositori ini berfungsi sebagai mesin pemroses utama berbasis **FastAPI**.
* **Isi:** Peladen *low-latency* yang menerima data koordinat, menjalankan *inferencing* menggunakan model Scikit-Learn yang telah dilatih, dan mengintegrasikan Google Text-to-Speech (TTS).
* **Fokus:** Kecepatan *response time* dan integrasi API.

### 3. 💻 [Frontend Client App]([LINK_REPO_FRONTEND])
Repositori ini berisi antarmuka pengguna interaktif yang dibangun menggunakan **React JS**.
* **Isi:** Aplikasi *web* yang mengakses *webcam* klien, mendeteksi tangan secara langsung di *browser*, dan mengirimkan aliran data ringan ke *Backend*.
* **Fokus:** *User Experience* (UX) yang mulus dan *real-time feedback*.

---

## 🚀 Key Impact & Features

### 1. Low-Latency Data Pipeline
Alih-alih mengirim piksel gambar yang berat, sistem secara cerdas mengekstrak **21 titik *landmark* tangan (x, y, z)** di sisi klien (Frontend) atau menggunakan *pipeline* ringan, sehingga data yang dikirim untuk diklasifikasikan ke model sangat kecil (tabular data).

### 2. Algorithmic Efficiency
Pemilihan **Random Forest Classifier** dibandingkan arsitektur *Deep Learning* yang berat memastikan proses inferensi berjalan sangat cepat (*real-time processing*), stabil, dan tidak membutuhkan spesifikasi *hardware* peladen yang tinggi.

### 3. Voice Synthesis
Integrasi langsung dengan layanan **Google TTS** mengubah hasil klasifikasi teks menjadi *output* audio secara instan, memfasilitasi komunikasi dua arah yang natural.

---

## 📊 Model Performance

Model ini dievaluasi secara ketat dan hasil penelitiannya telah didokumentasikan dalam artikel jurnal ilmiah.

| Metric | Score | Interpretation |
| :--- | :---: | :--- |
| **mAP (Mean Average Precision)** | **0.989** | Model memiliki tingkat presisi hingga 98.9% dalam mengklasifikasikan gestur tangan secara konsisten. |
| **Dataset Size** | 9,100 | Dilatih menggunakan ribuan gambar gestur (A-Z) yang dianotasi secara presisi. |
| **Real-World Validation** | Passed | Mampu menjaga konsistensi deteksi fitur dalam kondisi pencahayaan dan latar belakang dinamis melalui kamera *real-time*. |

---

## 💻 Tech Stack
* **Machine Learning:** Scikit-Learn (Random Forest Classifier)
* **Computer Vision:** MediaPipe Hands
* **Backend:** FastAPI, Python, Uvicorn
* **Frontend:** React JS
* **Audio Integration:** Google Text-to-Speech API
* **Methodology:** CRISP-DM

---

## ⚡ Quick Start Navigation

Karena arsitektur proyek terpisah, silakan ikuti urutan berikut untuk menjalankan sistem secara lokal:

1. **Jalankan Backend:** Kunjungi ⚙️ [Backend API Server]([LINK_REPO_BACKEND]) dan ikuti instruksi `README.md` di sana untuk menyalakan *server* FastAPI di `localhost:8000`.
2. **Jalankan Frontend:** Kunjungi 💻 [Frontend Client App]([LINK_REPO_FRONTEND]) dan jalankan `npm start` untuk membuka antarmuka kamera di *browser* Anda.
3. *(Opsional)* **Pelajari Model:** Kunjungi 🧠 [Model & Training Engine]([LINK_REPO_TRAINING]) jika Anda ingin bereksperimen dengan dataset atau melatih ulang model dengan parameter baru.

---

## 🔮 Future Improvements
* Menggabungkan pengenalan kata (kata utuh, bukan hanya huruf) menggunakan arsitektur sekuensial (*sequence modeling*).
* Menambahkan *containerization* (Docker) untuk ketiga repositori agar proses peluncuran (*deployment*) lebih terpusat dan mudah.

## 👤 Author
* GitHub: https://github.com/RPriago
* LinkedIn: https://linkedin.com/in/ranggapriago

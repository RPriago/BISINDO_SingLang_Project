# 🤟 Real-Time BISINDO Sign Language to Voice Conversion

![Python](https://img.shields.io/badge/Python-3.12%2B-blue?style=for-the-badge&logo=python)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

## 📖 Project Overview
This system is an *End-to-End Machine Learning* and *Computer Vision* solution designed to translate Indonesian Sign Language (BISINDO) into voice in real-time. 

Developed using the **CRISP-DM** methodology, this system addresses communication accessibility for the deaf community by extracting hand coordinates (*spatial landmarks*) from live video feeds, classifying them into text, and synthesizing them into voice with minimal latency.

---

## 📦 Microservices Architecture & Repositories

To maintain *separation of concerns* and scalability, this project is divided into three distinct repositories. **Please visit the repositories below to view the specific *source code*:**

### 1. 🧠 [Model & Training Engine]([LINK_REPO_TRAINING])
This repository contains the entire Data Science and Machine Learning workflow.
* **Contents:** MediaPipe feature extraction scripts, datasets, Exploratory Data Analysis (EDA), and Random Forest model training scripts.
* **Focus:** Accuracy in recognizing hand coordinate patterns.

### 2. ⚙️ [Backend API Server]([LINK_REPO_BACKEND])
This repository serves as the core processing engine built with **FastAPI**.
* **Contents:** A *low-latency* server that receives coordinate data, performs *inferencing* using the trained Scikit-Learn model, and integrates Google Text-to-Speech (TTS).
* **Focus:** Fast *response time* and API integration.

### 3. 💻 [Frontend Client App]([LINK_REPO_FRONTEND])
This repository contains the interactive user interface built with **React JS**.
* **Contents:** A web application that accesses the client's *webcam*, detects hands directly in the *browser*, and sends a lightweight data stream to the backend.
* **Focus:** Seamless *User Experience* (UX) and *real-time feedback*.

---

## 🚀 Key Impact & Features

### 1. Low-Latency Data Pipeline
Instead of transmitting heavy image pixels, the system intelligently extracts **21 hand *landmarks* (x, y, z)** on the client-side (Frontend) or through a lightweight *pipeline*, ensuring the data sent to the model for classification is extremely small (tabular data).

### 2. Algorithmic Efficiency
Opting for a **Random Forest Classifier** over heavy *Deep Learning* architectures ensures the inference process is highly efficient (*real-time processing*), stable, and does not require high-end server *hardware* specifications.

### 3. Voice Synthesis
Direct integration with the **Google TTS** service instantly converts classified text into audio *output*, facilitating natural, two-way communication.

---

## 📊 Model Performance

This model was rigorously evaluated, and the research findings have been documented in a scientific journal article.

| Metric | Score | Interpretation |
| :--- | :---: | :--- |
| **mAP (Mean Average Precision)** | **0.989** | The model achieves up to 98.9% precision in classifying hand gestures consistently. |
| **Dataset Size** | 9,100 | Trained on thousands of gesture images (A-Z) with precise landmark annotations. |
| **Real-World Validation** | Passed | Capable of maintaining consistent feature detection across dynamic lighting and background conditions via real-time camera feeds. |

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

Due to the decoupled architecture, please follow this sequence to run the system locally:

1. **Run the Backend:** Visit the ⚙️ [Backend API Server]([https://github.com/RPriago/SignLanguage_Project]) and follow the `README.md` instructions there to start the FastAPI server on `localhost:8000`.
2. **Run the Frontend:** Visit the 💻 [Frontend Client App]([LINK_REPO_FRONTEND]) and run `npm start` to open the camera interface in your browser.
3. *(Optional)* **Explore the Model:** Visit the 🧠 [Model & Training Engine]([LINK_REPO_TRAINING]) if you wish to experiment with the dataset or retrain the model with new parameters.

---

## 🔮 Future Improvements
* Incorporate word-level recognition (entire words rather than just letters) using sequential architectures (*sequence modeling*).
* Implement containerization (Docker) for all three repositories to centralize and simplify the *deployment* process.

## 👤 Author
* GitHub: https://github.com/RPriago
* LinkedIn: https://linkedin.com/in/ranggapriago

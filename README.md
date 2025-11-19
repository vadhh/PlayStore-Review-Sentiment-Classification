# PlayStore Review Sentiment Classification

Proyek ini adalah implementasi *end-to-end* **Text Classification** pada data ulasan aplikasi yang di-*scrape* langsung dari Google Play Store. Proyek ini mencakup tiga tahap utama: **Data Scraping**, **Text Preprocessing & Feature Extraction (TF-IDF)**, dan **Model Training** menggunakan beberapa algoritma Machine Learning.

## 🛠️ Tahap 1: Pengumpulan Data (Scraping)

* **File Notebook:** `01_scraping.ipynb`
* **Metode yang Digunakan:** Library `google-play-scraper`.
* **Alasan Penggunaan:** Mengumpulkan data ulasan secara langsung dan *real-time* dari halaman aplikasi di Google Play Store untuk mendapatkan data yang relevan dan terbaru.
* **Hasil yang Didapat:** Data ulasan mencakup `reviewId`, `userName`, `content` (teks ulasan), `score` (bintang 1-5), dan `at` (tanggal ulasan). Data mentah disimpan di `data/raw/playstore_reviews.csv`.
* **Total Data:** [Sebutkan jumlah total data yang berhasil di-*scrape* di sini, misal: 10,000 ulasan]

## 🧠 Tahap 2: Preprocessing, Vectorization, dan Model Training

* **File Notebook:** `02_trainingModel.ipynb`

### 1. Pra-pemrosesan Teks (Preprocessing)

* **Langkah Utama:** Data *score* (1-5) diubah menjadi label sentimen (`Positif`, `Negatif`, `Netral`) atau hanya biner (`Positif`/`Negatif`).
    * [**Penting:** Jelaskan di sini bagaimana Anda mengelompokkan `score` (misal: Bintang 4-5 = Positif, Bintang 1-2 = Negatif, Bintang 3 = Netral atau di-drop).]
* **Pembersihan Teks:** Normalisasi, penghapusan *stop words*, *stemming* atau *lemmatization* [Jelaskan teknik yang Anda gunakan].

### 2. Feature Extraction (Vectorization)

* **Metode yang Digunakan:** **TF-IDF (Term Frequency-Inverse Document Frequency)**.
* **Alasan Penggunaan:** TF-IDF mampu merepresentasikan setiap ulasan sebagai vektor numerik, di mana kata-kata yang unik dan penting (memiliki bobot tinggi) akan lebih ditekankan daripada kata-kata yang umum.

### 3. Model Training & Evaluasi

Tiga model klasifikasi dilatih dan dievaluasi pada data yang telah di-*vectorize*.

#### **Perbandingan Akurasi (Test Set):**

| Skema | Algoritma | Vectorizer | Akurasi Test Set |
| :---: | :--- | :--- | :---: |
| 1 | **Logistic Regression** | TF-IDF | **87.76%** |
| 2 | **Support Vector Machine (SVM)** | TF-IDF |**88.43%** |
| 3 | **Naive Bayes (NB)** | TF-IDF | **85.35%** |

#### **Model Terbaik**

* **Model Terbaik:** TF-IDF **].
* **Performa Model Terbaik:**
* ***Hasil Evaluasi Skema 1 (Logistic Regression):***
|          |precision   |recall   |f1-score   |support
|negatif   |0.86      |0.96     |0.90       |998
|positif   |0.92      |0.76     |0.83       |661

|    accuracy       |          |          |0.88      |1659|
|   macro avg       |0.89      |0.86      |0.87      |1659|
|weighted avg       |0.88      |0.88      |0.88      |1659|

Akurasi Test: **87.76%**


# Sistem Case-Based Reasoning (CBR) untuk Prediksi Putusan Perkara Perikanan

## Deskripsi Proyek

Proyek ini merupakan implementasi metode **Case-Based Reasoning (CBR)** untuk membantu proses prediksi putusan perkara tindak pidana perikanan berdasarkan dokumen putusan Mahkamah Agung Republik Indonesia.

Sistem bekerja dengan mencari kasus-kasus terdahulu yang paling mirip, kemudian menggunakan kembali solusi dari kasus tersebut untuk menghasilkan prediksi pada kasus baru.

Pendekatan yang digunakan adalah **Hybrid Information Retrieval**, yaitu kombinasi beberapa metode:

- TF-IDF (_Term Frequency–Inverse Document Frequency_)
- BM25 (_Best Matching 25_)
- Sentence-BERT (SBERT)
- Cross-Encoder Re-ranking

Hasil akhir prediksi diperoleh menggunakan metode **Similarity-Weighted Voting** dari kasus-kasus yang paling relevan.

---

## Tujuan Sistem

Tujuan dari proyek ini adalah:

- Mengumpulkan dokumen putusan perkara perikanan dari Mahkamah Agung RI
- Melakukan ekstraksi informasi penting dari dokumen hukum
- Membangun basis kasus (_case base_)
- Melakukan pencarian kasus yang paling mirip (_case retrieval_)
- Menggunakan kembali solusi dari kasus terdahulu (_solution reuse_)
- Mengevaluasi performa sistem Case-Based Reasoning

---

## Struktur Folder Project

```plaintext
CBR-Perikanan_453-470/
│
├── data/
│   ├── raw_pdf/
│   ├── raw_text/
│   ├── processed/
│   ├── results/
│   └── eval/
│
├── logs/
├── models/
│
├── notebooks/
│   ├── 01_data_collection.ipynb
│   ├── 02_case_representation.ipynb
│   ├── 03_case_retrieval.ipynb
│   ├── 04_solution_reuse.ipynb
│   └── 05_evaluation.ipynb
│
├── visualizations/
├── requirements.txt
└── README.md
```

---

## Persyaratan Sistem

Sebelum menjalankan project ini, pastikan telah menginstal:

- Python 3.10 atau lebih baru
- Jupyter Notebook / Google Colab
- Git
- Internet untuk download model embedding (SBERT)

---

## Instalasi

### 1. Clone Repository

```bash
git clone https://github.com/Ardaaa15/CBR-Perikanan_453-470.git
```

### 2. Masuk ke Folder Project

```bash
cd CBR-Perikanan_453-470
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

Jika menggunakan Google Colab:

```python
!pip install -r requirements.txt
```

---

## Cara Menjalankan Pipeline

Jalankan notebook secara berurutan sesuai pipeline berikut:

```plaintext
01_data_collection
↓
02_case_representation
↓
03_case_retrieval
↓
04_solution_reuse
↓
05_evaluation
```

---

## Penjelasan Notebook

### 1. Notebook 01 – Data Collection

Mengambil dan mengumpulkan dokumen PDF putusan perkara perikanan dari Mahkamah Agung RI.

Output:

```plaintext
data/raw_pdf/
```

---

### 2. Notebook 02 – Case Representation

Melakukan ekstraksi teks dan membentuk representasi kasus dari dokumen hukum.

Output:

```plaintext
data/processed/cases.csv
```

---

### 3. Notebook 03 – Case Retrieval

Membangun sistem pencarian kasus menggunakan metode:

- TF-IDF
- BM25
- Sentence-BERT (SBERT)
- Cross-Encoder Re-ranking

Output:

- Model retrieval
- Similarity score
- Embedding kasus

---

### 4. Notebook 04 – Solution Reuse

Melakukan prediksi putusan berdasarkan kasus yang paling mirip menggunakan:

- Hybrid retrieval
- Similarity-weighted voting
- Majority voting

Output:

```plaintext
data/results/predictions.csv
data/results/case_base_retained.csv
```

---

### 5. Notebook 05 – Evaluation

Melakukan evaluasi performa sistem CBR.

Output:

```plaintext
data/eval/prediction_metrics.csv
data/eval/retrieval_metrics.csv
```

Visualisasi hasil evaluasi disimpan pada folder:

```plaintext
visualizations/
```

---

## Dataset

Dataset berasal dari dokumen putusan perkara tindak pidana perikanan Mahkamah Agung Republik Indonesia.

Setelah diproses, dataset memiliki atribut:

- case_id
- retrieval_topic
- ringkasan_fakta
- dakwaan
- amar_putusan
- pasal
- jenis_putusan

---

## Output Project

### data/results/

- predictions.csv
- case_base_retained.csv

### data/eval/

- prediction_metrics.csv
- retrieval_metrics.csv

### visualizations/

- prediction_metrics.png
- retrieval_metrics.png

---

## Menjalankan di Google Colab

1. Mount Google Drive
2. Arahkan ke folder project
3. Jalankan notebook secara berurutan
4. Pastikan semua file dan dependencies tersedia

Urutan pipeline:

```plaintext
01 → 02 → 03 → 04 → 05
```

---

## Catatan Penting

- Notebook harus dijalankan secara berurutan
- Output setiap tahap menjadi input tahap berikutnya
- Pastikan semua library pada `requirements.txt` sudah terinstall
- Model embedding (SBERT) membutuhkan koneksi internet saat pertama kali dijalankan

---

## Repository GitHub

Repository project dapat diakses melalui:

```plaintext
https://github.com/Ardaaa15/CBR-Perikanan_453-470
```

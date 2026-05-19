# Klasifikasi Sentimen Calon Presiden Indonesia 2024

Proyek ini membandingkan tiga arsitektur deep learning berbasis Recurrent Neural Network (RNN), yaitu LSTM, BiLSTM, dan GRU, untuk klasifikasi sentimen cuitan Twitter terkait calon presiden Indonesia 2024: Anies Baswedan, Ganjar Pranowo, dan Prabowo Subianto.

Task yang digunakan adalah binary sentiment classification dengan dua kelas:

- Positive
- Negative

Model terbaik pada eksperimen data bersih adalah BiLSTM dengan akurasi sekitar 88,65%.

## Notebook

Repositori ini menyediakan dua notebook dengan tujuan berbeda:

- `main.ipynb`
  Notebook demo preprocessing dari data original/kotor. Notebook ini cocok digunakan saat presentasi untuk menunjukkan proses pembersihan teks dari dataset original, termasuk penghapusan URL, karakter non-alfabet, case folding, penghapusan spasi berlebih, filtering data, dan konversi label.

- `main_clean_data.ipynb`
  Notebook eksperimen utama untuk hasil modeling. Notebook ini memakai dataset labeled/bersih pada kolom `Text`, sehingga hasil BiLSTM lebih konsisten dengan laporan awal, yaitu sekitar 88% akurasi.

## Alur Proyek

1. Load dataset kandidat presiden.
2. Eksplorasi data dan distribusi label.
3. Preprocessing teks.
4. Konversi label menjadi format biner.
5. Split data train, validation, dan test.
6. Tokenisasi dan padding.
7. Training model LSTM, BiLSTM, dan GRU.
8. Evaluasi menggunakan accuracy, precision, recall, F1-score, dan confusion matrix.
9. Visualisasi distribusi label, kurva training, dan confusion matrix.

## Ringkasan Hasil

| Model | Akurasi | Catatan |
|---|---:|---|
| LSTM | 72,18% | Cenderung memprediksi kelas mayoritas |
| GRU | 72,18% | Cenderung memprediksi kelas mayoritas |
| BiLSTM | 88,65% | Model terbaik pada eksperimen data bersih |

## Struktur Data

Dataset lokal diletakkan pada folder `data/` dengan struktur:

```text
data/
  original data/
  cleaned data/
  labeled data/
```

Folder `data/` tidak disertakan ke GitHub karena ukuran dan sifat dataset. Pastikan dataset tersedia secara lokal sebelum menjalankan notebook.

## Cara Menjalankan

1. Buat dan aktifkan virtual environment:

```powershell
python -m venv .venv
.\.venv\Scripts\activate
```

2. Install dependency:

```powershell
pip install -r requirements.txt
```

3. Jalankan Jupyter Notebook:

```powershell
python -m jupyter notebook
```

4. Pilih notebook sesuai kebutuhan:

- Untuk demo preprocessing: `main.ipynb`
- Untuk hasil akurasi terbaik: `main_clean_data.ipynb`

## Catatan GPU

Eksperimen ini dapat dijalankan dengan CPU. Pada Windows native dengan TensorFlow versi baru, CUDA GPU tidak otomatis digunakan. Jika ingin memakai GPU NVIDIA, gunakan WSL2 atau Google Colab.

## File yang Dipush

File utama yang perlu masuk GitHub:

- `README.md`
- `.gitignore`
- `requirements.txt`
- `main.ipynb`
- `main_clean_data.ipynb`

Folder environment, dataset, cache notebook, dan file hasil sementara diabaikan oleh `.gitignore`.

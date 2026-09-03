*This Repository is in Indonesian*

# 🏦 Prediksi Langganan Deposito Berjangka Bank

Proyek *machine learning* yang mengevaluasi model klasifikasi **Decision Tree**, **Random Forest**, dan **XGBoost** untuk memprediksi apakah seorang nasabah akan berlangganan deposito berjangka (*deposito*) berdasarkan Bank Marketing dataset.

---

## 📌 Ringkasan Proyek

Kampanye *telemarketing* langsung merupakan saluran utama bagi bank untuk mempromosikan produk deposito, tetapi menghubungi setiap nasabah memerlukan waktu dan biaya operasional yang signifikan. 

Proyek ini menganalisis **4.521 data nasabah** untuk membangun model klasifikasi *supervised learning* yang dapat mengidentifikasi nasabah berpotensi tinggi sebelum dilakukan kontak. Dengan menargetkan nasabah yang tepat, bank dapat mengoptimalkan efisiensi pemasaran dan memaksimalkan tingkat konversi kampanye.

---

## 📊 Ringkasan Dataset (`bank.csv`)

* **Ukuran Dataset:** 4.521 baris, 17 atribut (16 fitur + 1 target)
* **Pemisah (*Delimiter*):** Titik koma (`;`)
* **Variabel Target:** `y` (`"yes"` = berlangganan, `"no"` = tidak berlangganan)
  * Distribusi Kelas: **4.000 "no" (88,5%)** vs. **521 "yes" (11,5%)** *(dataset tidak seimbang / imbalanced)*

### Rincian Fitur

| Kategori | Atribut | Deskripsi | Tipe Data |
| :--- | :--- | :--- | :--- |
| **Demografi Nasabah** | `age` | Usia nasabah | Numerik |
| | `job` | Kategori pekerjaan (12 jenis: `admin.`, `blue-collar`, `technician`, dll.) | Kategorikal |
| | `marital` | Status pernikahan (`married`, `single`, `divorced`) | Kategorikal |
| | `education` | Tingkat pendidikan (`primary`, `secondary`, `tertiary`, `unknown`) | Categorical |
| **Profil Keuangan** | `default` | Memiliki kredit macet/gagal bayar? (`yes`, `no`) | Kategorikal |
| | `balance` | Rata-rata saldo tahunan (dalam EUR) | Numerik |
| | `housing` | Memiliki pinjaman perumahan/KPR? (`yes`, `no`) | Kategorikal |
| | `loan` | Memiliki pinjaman pribadi? (`yes`, `no`) | Kategorikal |
| **Data Kontak Terakhir** | `contact` | Jenis komunikasi kontak (`cellular`, `telephone`, `unknown`) | Kategorikal |
| | `day` | Hari kontak terakhir dalam sebulan | Numerik |
| | `month` | Bulan kontak terakhir dalam setahun (`jan`–`dec`) | Kategorikal |
| | `duration` | Durasi kontak terakhir (dalam detik) | Numerik |
| **Konteks Kampanye** | `campaign` | Jumlah kontak yang dilakukan selama kampanye ini | Numerik |
| | `pdays` | Jumlah hari setelah nasabah terakhir dihubungi (-1 = belum pernah dihubungi) | Numerik |
| | `previous` | Jumlah kontak yang dilakukan sebelum kampanye ini | Numerik |
| | `poutcome` | Hasil kampanye pemasaran sebelumnya (`unknown`, `other`, `failure`, `success`) | Kategorikal |

---

## ⚙️ Metodologi & Alur Kerja Pemodelan

1. **Exploratory Data Analysis (EDA):**
   * Menganalisis ketidakseimbangan kelas target (`88,5% no` vs `11,5% yes`).
   * Visualisasi distribusi untuk fitur-fitur numerik utama (`duration`, `balance`, `age`).
2. **Pra-pemrosesan Data (*Data Preprocessing*):**
   * Memuat data dengan pemisah titik koma: `pd.read_csv('bank.csv', sep=';')`.
   * Enkodasi fitur kategorikal (*One-Hot Encoding* / *Ordinal Encoding*).
   * Skaling fitur menggunakan `StandardScaler`.
   * Pembagian *Train-Test split* (80/20 split dengan stratifikasi pada target `y`).
3. **Pelatihan & Perbandingan Model:**
   * **Decision Tree Classifier:** Model keputusan dasar (*baseline*) yang mudah diinterpretasikan.
   * **Random Forest Classifier:** Pendekatan *ensemble bagging* untuk mengurangi varians dan risiko *overfitting*.
   * **XGBoost Classifier:** Algoritma *gradient boosting* tingkat lanjut yang dioptimalkan untuk performa klasifikasi.
4. **Metrik Evaluasi:** Accuracy, Precision, Recall, F1-Score, dan ROC-AUC (fokus utama pada Recall/F1-Score karena ketidakseimbangan kelas target).

---

## 📈 Performa & Hasil Model

| Model | Accuracy | ROC-AUC |
| :--- | :---: | :---: |
| **Decision Tree** | *0.85* | *0.67* |
| **Random Forest** | *0.89* | *0.95* |
| **XGBoost** | *0.93* | *0.97* |

---

## 📁 Struktur Repositori

```text
Deposito_Subscription_Prediction/
├── bank.csv                     # Dataset (4.521 baris, pemisah titik koma)
├── Python_Notebook.ipynb        # Colab / Jupyter Notebook utama
└── README.md                    # Dokumentasi proyek

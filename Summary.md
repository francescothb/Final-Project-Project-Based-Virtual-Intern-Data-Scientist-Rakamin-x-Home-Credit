# Final-Project-Project-Based-Virtual-Intern-Data-Scientist-Rakamin-x-Home-Credit

📌 Credit Risk Prediction Analysis — Home Credit x Rakamin Academy

Author: Francesco Theodore Budiman

Project ini bertujuan membangun model machine learning untuk memprediksi risiko gagal bayar (credit risk) menggunakan dataset Home Credit. Analisis mencakup data preprocessing, exploratory data analysis, feature engineering sederhana, pemodelan, evaluasi model, hingga rekomendasi bisnis.

📂 1. Project Overview

Home Credit menghadapi tingkat kredit macet (NPL) yang cukup tinggi, berada di angka 8.1%.

![alt text](https://github.com/francescothb/Final-Project-Project-Based-Virtual-Intern-Data-Scientist-Rakamin-x-Home-Credit/blob/d5fa1f2f0dfd1340b36826e808a162d3e7d12be2/Distribution%20of%20Target%20Variable.png?raw=true)

Melalui project ini, dilakukan analisis untuk:

• Mengidentifikasi karakteristik debitur berisiko dan potensial

• Memprediksi probabilitas gagal bayar secara akurat

• Mendukung keputusan kredit yang lebih tepat

• Menurunkan NPL menjadi 5% dalam 1 tahun

Dataset terdiri dari beberapa tabel terpisah, termasuk data aplikasi utama, riwayat kredit, aplikasi sebelumnya, saldo bulanan, dan pembayaran angsuran.


📊 2. Dataset Description

Berikut penjelasan ringkas keseluruhan dataset yang digunakan:

• application_train/test.csv — Data utama setiap pengajuan kredit (satu baris = satu loan).

• bureau.csv — Riwayat kredit nasabah dari lembaga lain yang dilaporkan ke Credit Bureau.

• bureau_balance.csv — Riwayat bulanan dari setiap kredit nasabah yang tercatat di bureau.

• previous_application.csv — Seluruh pengajuan pinjaman nasabah sebelumnya ke Home Credit.

• POS_CASH_balance.csv — Riwayat bulanan pinjaman POS & cash loan nasabah di Home Credit.

• credit_card_balance.csv — Riwayat bulanan penggunaan kartu kredit Home Credit.

• installments_payments.csv — Riwayat pembayaran angsuran kredit sebelumnya, termasuk pembayaran yang terlewat.

Dari beberapa dataset (train.csv, bureau.csv, previous_application.csv), beberapa fitur digunakan sebagai input model berdasarkan ketersediaan dan relevansi.


🛠️ 3. Data Preprocessing

Langkah utama preprocessing:

• Integrasi dataset melalui join (application + bureau + previous application).

• Handling missing values dengan eliminasi kolom >40% missing dan imputasi.

• Encoding fitur kategorik (contoh: pendidikan menjadi Higher vs Lower Education).

• Feature elimination berdasarkan korelasi tinggi antar variabel.

• Imbalance handling menggunakan SMOTE.

• Feature scaling untuk model berbasis jarak.

• Train-test split (80:20).


🔍 4. Exploratory Data Analysis (EDA) & Insights

Dua temuan utama:

Insight 1 — Pendidikan Tinggi → Risiko Rendah

• Debitur dengan Higher Education dan Incomplete Higher memiliki tingkat pengembalian yang lebih baik serta persentase cancel/unused yang lebih rendah.

Insight 2 — Profesi HR & Manager → Repayment Rate Tinggi

• Kedua profesi ini menunjukkan selisih repaid vs approved tertinggi dan menjadi segmen paling stabil dalam histori pembayaran.


🤖 5. Machine Learning Models

Model-model yang dicoba:

Logistic Regression

Decision Tree

Random Forest

XGBoost

📈 Model Terbaik: XGBoost

Performa XGBoost pada data test:

• Accuracy: 0.8746

• Precision: 0.9466

• Recall: 0.7939

• AUC-ROC: 0.93

XGBoost dipilih karena memiliki kemampuan terbaik membedakan debitur macet dan tidak macet (AUC tertinggi), meskipun Random Forest unggul sedikit pada recall.


💡 6. Business Recommendations
1. Permudah Proses Persetujuan untuk Segmen Risiko Rendah

Target: HR, Manager, Higher Education, Mahasiswa
Action:

Terapkan fast auto-approve bila histori kredit bersih

Tawarkan pinjaman kedua otomatis bila pembayaran 3–6 bulan pertama lancar

KPI:

Return rate naik +5%

Waktu approve berkurang 20–30%

2. Kurangi Cancel/Unused Loan

Target: Segmen pendidikan tinggi & profesi stabil
Action:

Berikan bunga lebih rendah (0.3–0.5%) bagi peminjam berkualitas

Jalankan customer insight survey untuk mengetahui alasan pembatalan

KPI:

50% responden mengisi survey dalam 6 bulan

Cancel/unused rate turun 5% dalam 1 tahun

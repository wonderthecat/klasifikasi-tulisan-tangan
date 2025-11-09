# Proyek Deep Learning: Klasifikasi Digit Tulisan Tangan (Model CNN vs. Transfer Learning)

Proyek ini mendokumentasikan implementasi dan evaluasi dua model *Deep Learning* untuk klasifikasi digit: **Model A** (CNN yang dilatih dari nol) dan **Model B** (Transfer Learning menggunakan MobileNetV2). Evaluasi dilakukan pada dataset standar MNIST dan 30 citra tulisan tangan pribadi (digit 1, 5, dan 9 sesuai NIM akhir 159).

## 🚀 Persyaratan dan Prasyarat

1.  Akses ke Google Colab (memerlukan Akun Google).
2.  **Dataset Pribadi:** 30 citra digit tulisan tangan yang telah disiapkan.
3.  **Skema Penamaan File (Wajib):** Setiap file harus dinamai dengan format `D_NN.png`.
    * `D` = Digit (1, 5, atau 9)
    * `NN` = Nomor Urut (01 hingga 10)
    * Contoh: `1_01.png`, `5_05.png`, `9_10.png`.

## ⚙️ Panduan Langkah Demi Langkah di Google Colab

Ikuti instruksi di bawah ini untuk memulai proyek dan menjalankan setiap blok kode (Sel) secara berurutan.

### Langkah 1: Mempersiapkan Notebook di Google Colab

1.  **Buka Google Colab:** Buka peramban Anda dan kunjungi Google Colab.
2.  **Buat Notebook Baru:** Klik `File` -> `New notebook` atau `File` -> `Upload notebook` jika Anda mengunggah file `.ipynb` yang sudah ada.
3.  **Salin Kode:** Salin seluruh kode yang telah disediakan (terbagi menjadi 8 Sel) dan tempelkan ke dalam sel-sel di *notebook* Colab Anda. Pastikan setiap blok kode ditempatkan dalam selnya sendiri.
4.  **Atur Hardware Accelerator:** Untuk mempercepat pelatihan, pastikan *runtime* Anda menggunakan GPU. Klik `Runtime` -> `Change runtime type` -> pilih `T4 GPU` atau `A100 GPU` di bagian *Hardware accelerator*.

### Langkah 2: Setup Lingkungan dan Data MNIST

Jalankan setiap sel satu per satu secara berurutan dari atas. Anda dapat menjalankan sel dengan mengeklik tombol *Play* (▶️) di samping sel atau menekan `Shift + Enter`.

| Sel | Deskripsi Detail | Tindakan Ekstra |
| :--- | :--- | :--- |
| **Sel 1** | **Persiapan Lingkungan dan Import Libraries.** Sel ini akan menginstal `opencv-python` jika belum ada dan mengimpor semua *library* yang diperlukan (`tensorflow`, `matplotlib`, dll.). | Tidak ada. Tunggu hingga selesai. |
| **Sel 2** | **Pra-pemrosesan Data MNIST & Visualisasi.** Kode akan mengunduh dan memuat dataset MNIST, melakukan normalisasi, *reshaping*, dan menampilkan 5 contoh citra MNIST. | Verifikasi bahwa citra telah dimuat dengan benar. |

### Langkah 3: Pelatihan dan Evaluasi Model A (CNN dari Nol)

| Sel | Deskripsi Detail | Tindakan Ekstra |
| :--- | :--- | :--- |
| **Sel 3** | **Pembangunan dan Pelatihan Model A.** Membangun arsitektur CNN Model A. Kode akan mencetak **Model Summary** dan memulai pelatihan selama 8 *epochs*. Plot *Training History* (Accuracy & Loss) akan ditampilkan setelah pelatihan selesai. | Amati akurasi validasi (`val_accuracy`) Model A. |
| **Sel 4** | **Persiapan Data Tulisan Tangan Sendiri.** Sel ini akan membuat folder `tulistangan` dan meminta Anda mengunggah file. | **Penting:** Setelah pesan *upload* muncul, klik `Choose Files` dan unggah **semua 30** file gambar (`D_NN.png`) Anda secara bersamaan. |
| **Sel 5** | **Evaluasi Model A pada Tulisan Tangan Sendiri.** Menguji Model A pada 30 citra pribadi. Sel ini akan menampilkan **visualisasi 5 contoh** untuk setiap digit (1, 5, dan 9) dan mencetak Akurasi Model A pada data pribadi. | Periksa visualisasi; warna hijau berarti prediksi benar, merah berarti salah. |

### Langkah 4: Pelatihan dan Evaluasi Model B (Transfer Learning)

| Sel | Deskripsi Detail | Tindakan Ekstra |
| :--- | :--- | :--- |
| **Sel 6** | **Implementasi & Pelatihan Model B.** Mengunduh bobot MobileNetV2 dan melatih lapisan klasifikasi baru (lapisan *base model* dibekukan). Data MNIST disesuaikan ke format $32 \times 32 \times 3$ (RGB) sebelum pelatihan. Plot *Training History* Model B akan ditampilkan. | Perhatikan waktu *loading* MobileNetV2 dan *low accuracy* awal (karena *base model* dibekukan). |
| **Sel 7** | **Evaluasi Model B pada Tulisan Tangan Sendiri.** Menguji Model B pada 30 sampel tulisan tangan yang disesuaikan ukurannya ($32 \times 32 \times 3$). Mencetak Akurasi Model B pada data pribadi. | Bandingkan akurasi ini dengan hasil dari Model A. |

### Langkah 5: Analisis Hasil

| Sel | Deskripsi Detail | Tindakan Ekstra |
| :--- | :--- | :--- |
| **Sel 8** | **Analisis Perbandingan dan Kesimpulan.** Mencetak perbandingan akhir akurasi kedua model dan ringkasan temuan proyek. | Analisis hasil untuk penulisan laporan akhir Anda. |

## 📝 Hasil Kunci (Contoh)

Berikut adalah contoh hasil yang akan didapatkan setelah menjalankan seluruh *notebook*:

| Metrik | Model A (CNN dari Nol) | Model B (Transfer Learning) |
| :--- | :--- | :--- |
| **Akurasi Uji MNIST** | $\sim 99.13\%$ | $\sim 70.38\%$ |
| **Akurasi Tulisan Tangan Pribadi** | $\sim 76.67\%$ | $\sim 16.67\%$ |

*Kesimpulan menunjukkan bahwa, untuk tugas klasifikasi digit sederhana, Model CNN yang dirancang dari nol cenderung memiliki generalisasi yang lebih baik pada data out-of-domain dibandingkan Transfer Learning dengan *base model* yang dibekukan.*

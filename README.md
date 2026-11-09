# Klasifikasi Tingkat Kantuk Mahasiswa dengan Seleksi Fitur PCA

Proyek akhir mata kuliah Penambangan Data (INF11121), Teknik Informatika, Universitas Maritim Raja Ali Haji, 2026.

Proyek ini mengklasifikasikan tingkat kantuk mahasiswa saat perkuliahan (Mengantuk atau Tidak Mengantuk) dari kebiasaan belajar, penggunaan perangkat digital, dan pola tidur. Kolom kuesioner diseleksi dengan Principal Component Analysis (PCA), lalu dibandingkan tiga algoritma: Decision Tree, Naive Bayes, dan Random Forest. Metodologi mengikuti CRISP-DM.

## Anggota

| NIM | Nama |
| --- | --- |
| 2401020144 | Andhika Dwi Pratama (ketua) |
| 2401020138 | Raihan Darma Putra |
| 2401020149 | Muhammad Harist Syafi'in |
| 2401020154 | Muhammad Pancayandra Anugrah |
| 2401020159 | Muhammad Dimaz Al Bintani |

## Isi repositori

| Lokasi | Keterangan |
| --- | --- |
| `notebook/Seleksi_Kolom_PCA_v6.ipynb` | Notebook Google Colab (Sel 1 sampai 15), tanpa keluaran |
| `notebook/Seleksi_Kolom_PCA_v6_dengan_hasil.ipynb` | Notebook yang sama dengan keluaran lengkap hasil eksekusi |
| `hasil/` | Tabel (T*.csv), gambar (G*.png), model demo (`model_B.joblib`), dan `PETA_KELUARAN.csv` yang memetakan keluaran ke sel notebook |
| `requirements.txt` | Library Python yang dipakai |

Data kuesioner tidak dipublikasikan di repositori ini. Data mentah yang sudah disamarkan dan data siap mining dikumpulkan terpisah sesuai panduan pengumpulan laporan.

## Cara menjalankan

1. Buka `notebook/Seleksi_Kolom_PCA_v6.ipynb` di Google Colab.
2. Jalankan Sel 1 dan unggah file CSV kuesioner (data harus berukuran 105 baris dan 33 kolom).
3. Jalankan Sel 2 sampai 14 berurutan. Sel 10, 11, dan 12 butuh beberapa menit.
4. Sel 13 menampilkan formulir demo prediksi. Sel 14 mengecek kesesuaian angka dan seharusnya menampilkan lolos 18 dari 18.

Untuk menjalankan di komputer sendiri: `pip install -r requirements.txt`, lalu letakkan file CSV kuesioner di folder yang sama dengan notebook dengan nama `Kuesioner Penelitian Data Mining.csv`.

## Ringkasan alur dan hasil

- Data: 105 respons, 33 kolom. Setelah penyaringan responden aktif tersisa 100 responden.
- Label: kantuk Kadang-kadang atau lebih berarti Mengantuk (68 responden), selain itu Tidak Mengantuk (32 responden).
- Seleksi PCA: 25 kolom kandidat, 5 komponen (parallel analysis), KMO 0,617. Sebanyak 19 kolom dipertahankan dan 6 dibuang.
- Pengujian: validasi silang 5-lipat diulang 10 kali (50 pengujian), seed 42.

| Model | Akurasi | Akurasi seimbang | q uji permutasi |
| --- | --- | --- | --- |
| Klasifikasi mayoritas | 0,680 | 0,500 | |
| Decision Tree | 0,626 | 0,519 | 0,527 |
| Naive Bayes | 0,614 | 0,507 | 0,527 |
| Random Forest | 0,694 | 0,540 | 0,386 |

Random Forest hanya 0,014 di atas klasifikasi mayoritas dan tidak bermakna pada uji permutasi. Program demo layak sebagai demonstrasi, bukan alat penentu tingkat kantuk. Penjelasan lengkap ada pada laporan akhir.

## Keterbatasan

Sampel hanya 100 responden yang dijaring berantai (tidak acak), label dibuat dari jawaban sendiri, dan kelas tidak seimbang.

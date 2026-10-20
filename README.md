# UTS Graf Sains Data (GSD) 2026 - Graph Analytics & Recommendation System

**Identitas Mahasiswa:**
* **Nama:** Audy Alycia
* **NIM:** 24031554179
* **Kelas:** 2024B

---

## Deskripsi Proyek
Proyek ini dikembangkan untuk menyelesaikan Ujian Tengah Semester (UTS) Mata Kuliah **Graf Sains Data**. Fokus utama proyek ini adalah membangun sistem rekomendasi berbasis **Graph Database (Neo4j)**, **Vector Space Model (VSM)**, dan **Cosine Similarity** menggunakan dataset e-commerce *RetailRocket*.

Sistem diisolasi ke dalam dua rentang waktu spesifik:
* **Period 1 / P1 (Training):** 16 – 30 Juni 2015 ($1434412800000 \le t \le 1435708799999$)
* **Period 2 / P2 (Testing):** 16 – 31 Agustus 2015 ($1439683200000 \le t \le 1441065599999$)

---

## Ringkasan Hasil & Metrik Utama
1. **Pembersihan & Filtering Data:**
   * Berhasil mengekstrak interaksi pengguna pada P1 dan P2 dengan skema pembatasan waktu timestamp Unix Epoch.
2. **Karakteristik Vector Space Model (VSM):**
   * *User VSM*: Dimensi $(161.249 \times 81.034)$ dengan Sparsity >99.9%.
   * *Item VSM*: Dimensi $(81.034 \times 161.249)$, Sparsity 99.9982%, dengan 239.550 interaksi non-zero.
3. **Graph Similarity & Write-Back:**
   * Menggunakan proyeksi *Item VSM* untuk menghitung Cosine Similarity.
   * Melakukan *write-back* relasi `:SIMILAR_TO` ke dalam database Neo4j lokal (`bolt://127.0.0.1:7687`).
4. **Rekomendasi k-NN & Evaluasi:**
   * Pengujian dilakukan secara *reproducible* pada target user `1075582` ($k=5$).
   * **Hit@5 = 0.0** dan **NDCG@5 = 0.0** disebabkan oleh pola *User Churn* yang ekstrem antara P1 dan P2.

---

## Struktur Repositori

| Nama File / Folder | Deskripsi |
| :--- | :--- |
| `01_Environment_Setup_Neo4j.ipynb` | Notebook inisialisasi environment, pembuatan constraint, dan batch import data awal ke Neo4j. |
| `02_Import_VSM_Similarity_Analytics.ipynb` | Notebook utama berisi filtering P1/P2, pembentukan VSM, kalkulasi Cosine Similarity, *write-back* relasi `:SIMILAR_TO`, visualisasi subgraph, dan evaluasi k-NN. |
| `02_Import_VSM_Similarity_Analytics.html` | **[UTAMA] Export HTML LENGKAP** berisi seluruh output, tabel, dan grafik tanpa terpotong. |
| `26_UTS-GSD.pdf` | Naskah soal & panduan UTS Graf Sains Data. |
| `requirements.txt` | Daftar dependency library Python (`pandas`, `networkx`, `neo4j`, dll). |

---

## Cara Melihat Preview Output Notebook

Jika file `.ipynb` di GitHub mengalami kendala *rendering* akibat ukuran file dan output grafik yang besar, Anda dapat melihat hasil lengkapnya melalui opsi berikut:

1. **Prinjau HTML Online (Direkomendasikan):**  
   Buka file HTML ter-render secara utuh via HTMLPreview:  
   [**Buka Preview Notebook 02 Full Output (HTML)**](https://htmlpreview.github.io/?https://github.com/Alyciaaa11/UTS-Graf-Sains-Data-2026-24031554179-Audy-Alycia-2024B/blob/main/02_Import_VSM_Similarity_Analytics.html)

2. **Membuka File HTML Lokal:**  
   Unduh file `02_Import_VSM_Similarity_Analytics.html` dari repositori ini dan buka langsung di web browser (Chrome / Edge / Firefox).

---

## Lingkungan & Teknologi
* **Python Version:** 3.x (`myenv`/`myvenv`)
* **Graph Database:** Neo4j Local Instance (`bolt://127.0.0.1:7687`)
* **Python Libraries:** `pandas`, `numpy`, `scipy`, `networkx`, `matplotlib`, `seaborn`, `neo4j`

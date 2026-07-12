# Exploratory Data Analysis & Sentiment Analysis Twitter: Johnny Depp vs Amber Heard

Proyek UAS (Ujian Akhir Semester) yang melakukan **pengumpulan data Twitter**, **analisis hashtag**, dan **analisis sentimen** terhadap opini publik seputar kasus hukum **Johnny Depp vs Amber Heard**, guna melihat bagaimana dukungan publik terhadap kedua belah pihak berubah dari waktu ke waktu.

## Tentang Proyek

Proyek ini bertujuan menjawab pertanyaan: **bagaimana sentimen dan opini publik di Twitter terhadap Johnny Depp dan Amber Heard selama berlangsungnya kasus hukum mereka?** Analisis dilakukan dengan mengambil data tweet secara langsung melalui Twitter API, kemudian diproses melalui tahapan *preprocessing*, analisis hashtag populer, dan perhitungan skor sentimen (*polarity* & *subjectivity*) menggunakan TextBlob.

## Anggota Kelompok 1

| Nama | NPM |
|---|---|
| Adawia Ananda | 2106724883 |
| Fernaldy | 2106706464 |
| Myra Azzahra Putri Syah Indra | 2106726844 |
| Nadia Sukesi Sianipar | 2106700776 |

## Sumber Data

Data diambil langsung dari **Twitter API** menggunakan `tweepy`, dengan dua kata kunci pencarian:
- **"Johnny Depp"** — 2.000 tweet terbaru (bahasa Inggris)
- **"Amber Heard"** — 2.000 tweet terbaru (bahasa Inggris)

Setiap tweet disimpan lengkap dengan teks (`full_text`) dan `timestamp`, lalu diekspor ke format **JSON**, **CSV**, dan **TXT** untuk keperluan analisis lanjutan (termasuk analisis eksternal via Voyant Tools).

## Alur Kerja (Workflow)

### 1. Setup & Autentikasi
- Instalasi dan import modul (`tweepy`, `pandas`, `numpy`, `matplotlib`, `nltk`, `textblob`, dll).
- Autentikasi ke Twitter API menggunakan Consumer Key/Secret dan Access Token/Secret.

### 2. Pengumpulan Data Tweet
- Menarik 2.000 tweet untuk masing-masing kata kunci "Johnny Depp" dan "Amber Heard".
- Menyimpan hasil sebagai dua DataFrame (`df1`, `df2`) berisi teks tweet dan timestamp.

### 3. Pembersihan & Penandaan Data
- Menghapus awalan "RT" pada teks tweet.
- Menandai tweet yang benar-benar menyebut Johnny Depp / Amber Heard (termasuk variasi nama & hashtag) menggunakan fungsi `identify_subject`.
- Menyimpan data mentah ke JSON, CSV, dan TXT.

### 4. Analisis Hashtag
- Ekstraksi seluruh hashtag dari tweet menggunakan regex.
- Menghitung dan memvisualisasikan **50 hashtag terpopuler** untuk masing-masing tokoh, disimpan ke file CSV.

### 5. Preprocessing Teks untuk Sentiment Analysis
- Penghapusan *stopwords* Bahasa Inggris (NLTK) dan *custom stopwords*.
- Lemmatisasi kata menggunakan `TextBlob`/`Word`.

### 6. Perhitungan Sentimen
- Menghitung skor **polarity** (negatif–positif) dan **subjectivity** (objektif–subjektif) tiap tweet menggunakan `TextBlob`.
- Meringkas statistik (mean, min, max, median) skor sentimen untuk masing-masing tokoh.

### 7. Visualisasi Tren Sentimen
- Menghitung **Moving Average Polarity** pada berbagai jendela waktu (10, 100, 500, 1000, 1500, dan 2000 tweet) untuk melihat tren perubahan opini publik terhadap Johnny Depp dan Amber Heard secara berdampingan.

## Kesimpulan

Amber Heard pada awalnya memperoleh lebih banyak dukungan dan simpati publik. Namun, seiring berjalannya waktu, terungkap sejumlah fakta yang mendukung alibi Johnny Depp, sehingga opini publik bergeser dan cenderung lebih mendukung kemenangan Johnny Depp dalam kasus ini.

## Tools & Library

- **Python 3**
- `tweepy`, `twython` — pengambilan data dari Twitter API
- `pandas`, `numpy` — manipulasi data
- `matplotlib` — visualisasi data
- `nltk` — stopwords & wordnet (lemmatisasi)
- `textblob` — analisis sentimen (polarity & subjectivity)
- `beautifulsoup4`, `requests` — pendukung *web scraping*/parsing tambahan

## 📁 Struktur Notebook

```
1. Import Modul
2. Inisiasi Kredensial Twitter API (CS, AK, AT, CK)
3. Pengambilan Tweet (Hashtag Analysis)
4. Pengambilan Tweet (Dataframe)
5. Konversi Data ke JSON & DataFrame
6. Pembersihan Data (hapus "RT", penandaan subjek)
7. Penyimpanan Data (JSON, CSV, TXT)
8. Analisis Hashtag Populer
9. Preprocessing Teks (stopwords & lemmatisasi)
10. Perhitungan Sentimen (Polarity & Subjectivity)
11. Visualisasi Moving Average Polarity (10–2000 tweet)
12. Kesimpulan
```

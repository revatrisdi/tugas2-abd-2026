# Dokumentasi Dataset

## Informasi Umum

- **Nama Dataset:** Indonesian News Datasets
- **Sumber Publik:** [HuggingFace — iqballx/indonesian_news_datasets (`data.csv`)](https://huggingface.co/datasets/iqballx/indonesian_news_datasets/blob/main/data.csv)
- **Ukuran File:** 1,99 GB
- **Format Awal:** CSV (`data.csv`)

## Skema Kolom Dataset

| Nama Kolom   | Tipe Data   | Keterangan                                                                        |
| :----------- | :---------- | :-------------------------------------------------------------------------------- |
| `id`         | `INT64`     | Identitas unik setiap artikel berita                                              |
| `source`     | `VARCHAR`   | Nama portal media penerbit berita (contoh: `tempo`, dll.)                         |
| `title`      | `VARCHAR`   | Judul artikel berita                                                              |
| `image`      | `VARCHAR`   | Tautan URL gambar utama artikel                                                   |
| `url`        | `VARCHAR`   | Tautan sumber artikel asli (digunakan untuk ekstraksi kanal/rubrik)               |
| `content`    | `VARCHAR`   | Teks lengkap isi berita                                                           |
| `date`       | `TIMESTAMP` | Tanggal dan waktu publikasi artikel                                               |
| `embedding`  | `VARCHAR`   | Representasi vektor embedding teks _(dikecualikan saat preprocessing ke Parquet)_ |
| `created_at` | `TIMESTAMP` | Waktu pencatatan data pertama kali                                                |
| `updated_at` | `TIMESTAMP` | Waktu pembaruan terakhir data                                                     |
| `summary`    | `VARCHAR`   | Ringkasan artikel berita                                                          |

## Cara Mengunduh & Preprocessing Dataset

File `data.csv` (1,99 GB) dan file hasil konversi `.parquet` tidak di-commit ke GitHub (diabaikan melalui `.gitignore`). Gunakan perintah berikut untuk mengunduh langsung file `data.csv` dan mengonversinya ke Parquet bersih menggunakan DuckDB:

```bash
# 1. Unduh file data.csv langsung dari HuggingFace
curl -L "[https://huggingface.co/datasets/iqballx/indonesian_news_datasets/resolve/main/data.csv](https://huggingface.co/datasets/iqballx/indonesian_news_datasets/resolve/main/data.csv)" -o data/data.csv
```

```python
# 2. Konversi CSV ke Parquet bersih tanpa kolom embedding agar hemat RAM
import duckdb

duckdb.sql("""
    COPY (
        SELECT id, source, title, url, content, date, created_at, updated_at, summary
        FROM read_csv_auto('data/data.csv', ignore_errors=true)
    ) TO 'data/indonesian_news_clean.parquet' (FORMAT PARQUET, COMPRESSION ZSTD);
""")
```

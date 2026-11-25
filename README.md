---
title: Dashboard Analitik Tren Pemberitaan Indonesia
emoji: 📊
colorFrom: blue
colorTo: green
sdk: docker
app_port: 8501
pinned: false
---

> **Catatan:** Blok YAML di atas adalah konfigurasi HuggingFace Spaces (Docker, port 8501). Biarkan tetap berada di baris paling atas README; ubah `title` sesuai nama produk data tim.

# Tugas 2: Data Product — Dashboard Analitik Interaktif

Repositori tim **Reva Trisdianto (202310370311323) & Nabila Aurellya Putri (202310370311303)** untuk **Tugas 2** mata kuliah **Analisis Big Data** (S1 Teknik Informatika).

---

## Informasi Umum

| Parameter                | Keterangan                                                                                                        |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------- |
| **Tipe Tugas**           | Kelompok (2 Mahasiswa)                                                                                            |
| **Diumumkan**            | Pertemuan 8 (Phase 1); repositori dibagikan Pertemuan 9                                                           |
| **Platform Pengumpulan** | GitHub (fork dari [`UMM-GURU/tugas2-abd-2026`](https://github.com/UMM-GURU/tugas2-abd-2026)) & HuggingFace Spaces |
| **Bobot Penilaian**      | 35% dari Nilai Akhir Mata Kuliah                                                                                  |
| **Deadline Final**       | Minggu 14                                                                                                         |

---

## Tahapan Milestone Pengerjaan (Incremental Milestones)

| Fase                                        |  Diberikan   | Target Check-in | Deliverable Utama                                                                                                                                                   |
| ------------------------------------------- | :----------: | :-------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Phase 1: Pitch dan Architecture**         | Pertemuan 8  |  Pertemuan 10   | Pembentukan tim, fork repositori dan pengisian `identitas.md`, pengajuan proposal topik dan skema arsitektur data di `docs/architecture.md`.                        |
| **Phase 2: Data Pipeline dan Query Engine** | Pertemuan 10 |  Pertemuan 11   | Integrasi DuckDB/Polars backend, skrip ekstraksi data dan caching efisien siap dihubungkan ke Streamlit.                                                            |
| **Phase 3: Streamlit UI dan Staging Space** | Pertemuan 11 |  Pertemuan 12   | Prototype dashboard live di HuggingFace Spaces (staging), pengujian interaktivitas widget dan chart Plotly.                                                         |
| **Final Release dan Presentasi**            | Pertemuan 12 |    Minggu 14    | Final deployment production, video demo 3–5 menit, penyelesaian laporan `README.md`. Presentasi tim bergiliran mulai Minggu 12/13, selesai paling lambat Minggu 14. |

---

## Anggota Kelompok dan Peran

Identitas lengkap (nama, NIM, akun GitHub) dicantumkan di [`identitas.md`](identitas.md). Tabel berikut menjelaskan pembagian peran:

| No  | Nama                  | Peran / Kontribusi Utama                                                                                     |
| :-: | --------------------- | ------------------------------------------------------------------------------------------------------------ |
|  1  | Reva Trisdianto       | Lead Architect, Data Pipeline (Polars & Konversi Parquet), Integrasi Dockerfile, & Deployment HF Spaces      |
|  2  | Nabila Aurellya Putri | Backend Query (DuckDB Engine), Optimasi Caching (`@st.cache_data`), Frontend Streamlit, & Visualisasi Plotly |

---

## Tautan Produk Data

- **Live Dashboard (HuggingFace Spaces):** `https://huggingface.co/spaces/[username_hf]/[nama_app]` _(Akan diperbarui pada Phase 3)_
- **Video Demo (3–5 Menit):** `https://youtu.be/[video_id]` _(Akan diperbarui pada Final Release)_

---

## Prasyarat dan Menjalankan Dashboard Secara Lokal

### 1. Menjalankan Langsung dengan Python (Lokal)

```bash
pip install -r requirements.txt
streamlit run app.py
```

Akses dashboard di browser melalui: `http://localhost:8501`

### 2. Menjalankan di Lingkungan Docker

```bash
docker build -t bigdata-dashboard .
docker run -p 8501:8501 bigdata-dashboard
```

---

## Struktur Folder Repositori

```text
.
├── .github/
│   └── workflows/
│       └── lint_check.yml       # Pemeriksaan otomatis GitHub Actions
├── data/
│   └── README.md                # Petunjuk pengunduhan dataset besar
├── docs/
│   └── architecture.md          # Dokumen Pitch & Arsitektur Data Product (Phase 1)
├── src/
│   └── queries.py               # Modul kueri DuckDB dan transformasi Polars
├── app.py                       # Skrip utama aplikasi Streamlit
├── Dockerfile                   # Konfigurasi container
├── identitas.md                 # Nama, NIM, dan akun GitHub anggota
├── requirements.txt             # Daftar pustaka Python
└── README.md                    # Laporan utama proyek tim
```

---

## Pernyataan Penggunaan AI (AI Disclosure Statement)

- **Apakah menggunakan AI (ChatGPT / Claude / GitHub Copilot / LLM lain)?** Ya
- **Jika Ya, sebutkan alat yang digunakan:** Gemini, GitHub Copilot
- **Komponen mana yang dibantu AI:** Penyusunan struktur dokumentasi arsitektur, optimasi kueri konversi CSV ke Parquet menggunakan DuckDB, dan penataan format Markdown.
- **Komitmen Tim:** Seluruh anggota tim memahami sepenuhnya kode yang diserahkan dan bertanggung jawab penuh atas integritas serta fungsionalitas aplikasi saat evaluasi/presentasi.

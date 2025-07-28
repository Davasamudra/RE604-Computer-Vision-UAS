# OCR Plat Nomor Kendaraan dengan Visual Language Model (VLM)

Proyek ini menggunakan model **LLaVA (Large Language and Vision Assistant)** yang dijalankan melalui **LMStudio** untuk melakukan Optical Character Recognition (OCR) pada gambar plat nomor kendaraan. Hasil prediksi dievaluasi menggunakan **Character Error Rate (CER)**.

## 📁 Struktur Folder

```
.
├── data.csv              # File CSV berisi ground truth label
├── test/                 # Folder berisi gambar plat nomor (.jpg, .jpeg, .png)
├── ocr_plate_vlm.py      # Script utama untuk OCR dan evaluasi
└── ocr_results.csv       # Hasil prediksi dan skor CER
```

## 📄 Format CSV (`data.csv`)

File CSV harus memiliki dua kolom:
- `image`: Nama file gambar (contoh: `B1234XYZ.jpg`)
- `data`: Teks plat nomor sebenarnya (contoh: `B1234XYZ`)

Contoh:
```csv
image,data
B1234XYZ.jpg,B1234XYZ
D5678ABC.png,D5678ABC
```

## ⚙️ Cara Kerja

1. Gambar dikonversi menjadi base64 dan dikirim ke LMStudio (localhost:1234).
2. Model LLaVA memberikan hasil teks prediksi plat nomor.
3. Teks dibersihkan dan dievaluasi terhadap ground truth menggunakan CER.
4. Semua hasil dicatat dalam `ocr_results.csv`.

## ✅ Evaluasi: Character Error Rate (CER)

Mengukur seberapa mirip hasil OCR dengan label aslinya. Nilai CER mendekati **0** artinya prediksi sangat akurat.

## 🚀 Menjalankan Script

Pastikan LMStudio sedang berjalan di background dengan model `llava-v1.5-7b-llamafile` aktif.

```bash
python ocr_plate_vlm.py
```

## 🔧 Konfigurasi

Konfigurasi penting:
- Folder gambar: `test/`
- API URL LMStudio: `http://localhost:1234/v1/chat/completions`
- Prompt: "Only return the license plate number shown in this image..."

## 🧠 Model

Model yang digunakan:
- `llava-v1.5-7b-llamafile` (pastikan sudah aktif di LMStudio)

## 📌 Catatan

- File gambar dan data.csv harus sesuai penamaannya.
- Hasil akhir bisa dilihat di file `ocr_results.csv`.
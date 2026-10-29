# Pertemuan 13 - Debugging dan Testing

Nama: Nada Syifa Kamilia
NIM: 2225250089
Kelas: 3B

## Kasus

Program yang diuji adalah program Python untuk menghitung rata-rata nilai, menentukan status kelulusan, dan mencari nilai tertinggi.

Program menggunakan fungsi `hitung_rata_rata()`, `status()`, dan `nilai_tertinggi()`. Pengujian dilakukan untuk menemukan kesalahan logika dan memastikan hasil program sesuai dengan yang diharapkan.

## Test Case

| ID | Input | Expected | Actual Awal | Status |
|---|---|---|---|---|
| TC01 | `[80, 60, 90, 70]` | Rata-rata 75 | Rata-rata 60 | Gagal |
| TC02 | Nilai 60 | Tidak lulus | Tidak lulus | Lulus |
| TC03 | `[80, 60, 90, 70]` | Nilai tertinggi 90 | Nilai tertinggi 0 | Gagal |
| TC04 | `[70, 80, 90]` | Nilai tertinggi 90 | Nilai tertinggi 0 | Gagal |

## Bug Report

### Bug 1: Perhitungan rata-rata salah

- **Gejala:** Hasil rata-rata tidak sesuai dengan jumlah data.
- **Lokasi:** Fungsi `hitung_rata_rata()`.
- **Akar penyebab:** Program membagi jumlah nilai dengan angka tetap `5`, padahal jumlah data dapat berubah.
- **Perbaikan:** Mengganti `return sum(nilai) / 5` menjadi `return sum(nilai) / len(nilai)`.

### Bug 2: Nilai tertinggi tidak ditemukan

- **Gejala:** Program menghasilkan nilai tertinggi yang salah.
- **Lokasi:** Fungsi `nilai_tertinggi()`.
- **Akar penyebab:** Kondisi perbandingan menggunakan `x < tertinggi`, sehingga logika pencarian nilai tertinggi terbalik.
- **Perbaikan:** Menggunakan kondisi `x > tertinggi` dan menginisialisasi `tertinggi` dengan `nilai[0]`.

### Bug 3: Status kelulusan

- **Gejala:** Nilai 60 dinyatakan tidak lulus.
- **Lokasi:** Fungsi `status()`.
- **Akar penyebab:** Kondisi menggunakan `nilai > 60`.
- **Perbaikan:** Jika nilai 60 juga harus lulus, gunakan `nilai >= 60`. Jika batas kelulusan harus lebih dari 60, kode awal sudah benar.

## Retest

Setelah perbaikan, program diuji kembali dengan input yang sama.

| ID | Input | Expected | Actual Setelah Perbaikan | Status |
|---|---|---|---|---|
| TC01 | `[80, 60, 90, 70]` | Rata-rata 75 | Rata-rata 75.0 | Lulus |
| TC02 | Nilai 60 | Tidak lulus | Tidak lulus | Lulus |
| TC03 | `[80, 60, 90, 70]` | Nilai tertinggi 90 | Nilai tertinggi 90 | Lulus |
| TC04 | `[70, 80, 90]` | Nilai tertinggi 90 | Nilai tertinggi 90 | Lulus |

## Cara Menjalankan

Jalankan perintah berikut di terminal:

```bash
python3 praktik/praktik_4_debugging.py
```

Pastikan terminal berada di folder proyek yang benar dan file Python tersedia di lokasi tersebut.

## Refleksi

Teknik debugging yang paling membantu adalah menggunakan test case dan memeriksa nilai variabel saat program berjalan. Test case membantu membandingkan hasil yang diharapkan dengan hasil aktual, sedangkan pemeriksaan variabel membantu menemukan kesalahan logika. Setelah perbaikan, program perlu diuji kembali untuk memastikan semua fungsi berjalan dengan benar dan tidak menimbulkan kesalahan baru.
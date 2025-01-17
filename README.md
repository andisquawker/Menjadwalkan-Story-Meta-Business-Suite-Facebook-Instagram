# Meta Business Suite (Facebook & Instagram) Story Scheduler

## Deskripsi

Skrip ini merupakan sebuah otomatisasi menggunakan Python dan Selenium untuk menjadwalkan unggahan cerita (story) di Facebook & Instagram melalui Meta Business Suite. Skrip ini membaca data dari file Excel, memvalidasi data tersebut, dan kemudian mengunggah cerita secara otomatis sesuai dengan jadwal yang telah ditentukan. Skrip ini dirancang untuk mempermudah pengelolaan cerita di halaman Facebook & Instagram tanpa perlu melakukan unggahan secara manual.

## Fitur Utama
1. **Pembacaan Data dari Excel**: Menggunakan library `openpyxl` untuk membaca file Excel yang berisi data cerita, termasuk media, keterangan, tanggal tayang, jam tayang, dan menit tayang.
2. **Validasi Data**:
   - Memastikan semua kolom yang diperlukan sudah diisi.
   - Memvalidasi format tanggal tayang.
   - Membatasi tanggal tayang tidak lebih dari 28 hari dari hari ini.
3. **Automasi Penjadwalan Cerita**:
   - Login otomatis ke Facebook Business Suite.
   - Navigasi ke halaman pembuatan cerita.
   - Mengunggah media dan mengatur jadwal tayang sesuai dengan data dari Excel.
4. **Pembaruan Status**:
   - Menandai cerita yang sudah berhasil dijadwalkan dengan status "Upload" di file Excel.

## Prasyarat
Untuk menjalankan skrip ini, pastikan Anda telah menginstal:
- Python (versi 3.7 atau lebih baru)
- Selenium
- OpenPyXL
- PyAutoGUI
- Pyperclip

Selain itu, Anda memerlukan:
- Driver Chrome yang sesuai dengan versi Chrome di komputer Anda.
- File Excel yang berisi data cerita dengan format kolom: Laporan, Source Media, Caption, Jadwal Tayang, Jam, Menit.

## Cara Penggunaan
1. **Persiapkan Lingkungan**:
   - Instal semua library yang diperlukan dengan menjalankan perintah berikut:
     ```bash
     pip install selenium openpyxl pyautogui pyperclip
     ```

   - atau
     ```bash
     pip install -r requirements.txt
     ```
   - Unduh dan pastikan `chromedriver` tersedia di PATH atau dalam direktori proyek.
2. **Persiapkan Data**:
   - Buat file Excel dengan nama sesuai konfigurasi di skrip (default: `File_Excel.xlsx`).
   - Isi data cerita sesuai format yang diharapkan.
3. **Konfigurasi**:
   - Sesuaikan opsi driver Chrome di dalam skrip, seperti direktori cookie pengguna dan ID halaman Facebook.
4. **Jalankan Skrip**:
   - Eksekusi skrip dengan perintah berikut:
     ```bash
     python Menjadwalkan Story.py
     ```
5. **Hasil**:
   - Cerita akan diunggah dan dijadwalkan secara otomatis sesuai data di file Excel.
   - File Excel akan diperbarui dengan status "Upload" pada baris yang berhasil diproses.

## Struktur Data File Excel
| Kolom          | Deskripsi                                      |
|----------------|------------------------------------------------|
| Laporan        | Status unggahan ("Upload" untuk cerita selesai diunggah) |
| Source Media   | Lokasi file media (gambar atau video)          |
| Caption        | Keterangan atau teks untuk cerita             |
| Jadwal Tayang  | Tanggal tayang cerita (format: dd/mm/yyyy)     |
| Jam            | Jam tayang cerita (format: hh)                |
| Menit          | Menit tayang cerita (format: mm)              |

## Catatan Penting
- **Error Handling**: Skrip akan berhenti jika:
  - Format tanggal tidak valid.
  - Data pada baris tidak lengkap.
  - Tanggal tayang lebih dari 28 hari ke depan.
- **Toleransi Waktu**: Skrip menggunakan `time.sleep` dan `WebDriverWait` untuk memastikan semua elemen di halaman dimuat dengan benar sebelum melakukan tindakan.

## Lisensi
Skrip ini dilisensikan di bawah [MIT License](LICENSE).

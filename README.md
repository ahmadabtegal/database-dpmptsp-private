# Paket data website DPMPTSP Kota Tegal

Paket ini dibuat dari `Web DPMPTSP.xlsx`.

## Isi paket
- `data/*.json`: snapshot data publik per sheet, dengan penyaringan status publikasi mengikuti logika API Apps Script yang disertakan.
- `data/manifest.json`: daftar file, kolom, dan jumlah baris yang diekspor.
- `database-full.sql`: dump seluruh sheet dan seluruh baris untuk diimpor ke MySQL/MariaDB.

## Penting tentang GitHub
GitHub Pages hanya meng-host file statis. File SQL yang diunggah ke GitHub tidak berjalan sebagai database aktif dan tidak menyediakan operasi tambah/edit/hapus.
Folder `data/` dapat di-host sebagai JSON statis. Agar website memakai JSON GitHub, kode `index.html` perlu diubah dari Apps Script API menjadi pembacaan file JSON. Panel Admin saat ini masih memakai `google.script.run` dan Google Sheets, sehingga tidak otomatis berpindah ke JSON atau MySQL.

## Keamanan
`database-full.sql` berisi seluruh data termasuk Pengaturan dan AuditTrail. Jangan letakkan file ini di repository publik. Simpan di repository PRIVATE atau lokasi backup privat. Untuk repository publik, gunakan hanya folder `data/` setelah memeriksa kembali bahwa data yang dipublikasikan memang layak tampil untuk umum.

## Catatan kualitas data
Nilai tanggal pada beberapa baris Berita di spreadsheet sumber terbaca sebagai `1970-01-01`. Nilai sumber dipertahankan dan tidak ditebak/diperbaiki dalam proses ekspor. Periksa tanggal tersebut sebelum dipublikasikan.

## Saran penggunaan
1. Upload folder `data/` ke repository website jika ingin memakai JSON statis.
2. Simpan `database-full.sql` secara privat untuk backup atau migrasi MySQL.
3. Untuk website dinamis dengan admin tambah/edit/hapus, siapkan backend/API dan database hosting (misalnya MySQL hosting atau PostgreSQL terkelola). GitHub bukan server database.

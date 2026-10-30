# AccounSaaS — Finance | Open Access Demo

Demo statis siap GitHub Pages. Tampilan mengikuti referensi AccounSaaS pada portfolio Nestiara: sidebar biru, dashboard, akun, jurnal, buku besar, laporan, Excel, rekonsiliasi, dan pengaturan.

## Akun demo publik

Username: demo@dapurkreatif.com
Password: dapurkreatifSCODERS26!

Kredensial juga tampil pada halaman login. Klik Isi akun demo lalu Masuk ke dashboard.

## Cara upload ke GitHub Pages (tanpa Node.js)

1. Ekstrak ZIP ini terlebih dahulu.
2. Di GitHub, buat repository PUBLIC bernama accounsaas-demo.
3. Buka repository tersebut. Pilih Add file > Upload files.
4. Upload ISI folder AccounSaaS-Demo, bukan ZIP atau folder pembungkusnya. Pastikan index.html langsung di root repository, sejajar dengan app.js dan style.css. Folder assets harus ikut diupload.
5. Klik Commit changes.
6. Masuk Settings > Pages. Pada Build and deployment pilih Deploy from a branch.
7. Pilih branch main dan folder / (root), kemudian Save.
8. Tunggu deployment selesai. Buka alamat situs yang ditampilkan GitHub pada halaman Pages. Untuk akun artesiannest dengan repository accounsaas-demo, pola alamatnya adalah https://artesiannest.github.io/accounsaas-demo/ (belum dipublikasikan dari paket ini).
9. Jika belum tampil, periksa tab Actions untuk status deployment, kemudian muat ulang halaman.

Tidak memerlukan npm, build, Supabase, database server, ataupun node_modules. Library Excel sudah disertakan secara lokal.

## Menghubungkan ke portofolio

Pada konfigurasi kartu portfolio dengan id accounsaas, isi properti demoUrl dengan URL GitHub Pages yang sudah berhasil dibuka. Contoh pada js/data.js:

    "demoUrl": "https://artesiannest.github.io/accounsaas-demo/"

Jika konten kartu dikelola lewat CMS, ubah kolom URL demo dari halaman manajemen portfolio. Gunakan URL hasil deployment Anda. Paket ini tidak mengubah repository portfolio secara otomatis.

## Fitur dan panduan penggunaan

- Dashboard: total aset, kewajiban, ekuitas, laba rugi, tren pendapatan/beban enam bulan, dan jurnal terakhir. Aset/kewajiban/ekuitas kumulatif; laba rugi mengikuti periode. Grafik basis akrual, bukan arus kas.
- Akun: lihat daftar akun dan tambah akun dengan kode unik. Saldo memakai kelompok akun dan aturan saldo normal.
- Jurnal: tambah/edit/hapus jurnal dan cari deskripsi atau kode/nama akun. Setiap jurnal minimal dua baris. Satu baris berisi salah satu debit/kredit, berupa Rupiah bulat; total debit dan kredit wajib sama.
- Buku Besar: pilih akun dan periode untuk melihat mutasi. Saldo berjalan adalah debit dikurangi kredit dalam periode terpilih, tanpa saldo awal sebelum periode.
- Laporan: laba rugi mengikuti periode, neraca memakai seluruh jurnal. Tombol Cetak / PDF memakai dialog cetak browser.
- Import Excel: unduh template, gunakan sheet Jurnal dan nama kolom yang tersedia. Referensi yang sama mengelompokkan baris menjadi satu jurnal. Tanggal dan deskripsi harus sama dalam satu referensi. Sistem memvalidasi seluruh berkas sebelum tombol konfirmasi tampil. Referensi yang sudah ada ditolak untuk menghindari impor ganda. Tidak ada impor sebagian jika validasi gagal.
- Export Excel: workbook XLSX berisi Jurnal, Akun, Neraca Saldo, dan Laba Rugi. Jurnal mengikuti periode; neraca saldo seluruh data. Sheet Jurnal dapat diimpor pada browser yang belum memiliki referensi yang sama. Sheet Akun bersifat referensi: akun custom harus dibuat pada menu Akun sebelum jurnalnya diimpor di browser lain.
- Rekonsiliasi Bank: pencocokan manual mutasi akun 1101 dengan rekening koran. Centang setelah diperiksa; tidak ada koneksi bank.
- Pengaturan: ubah nama usaha atau reset data contoh. Ekspor dahulu jika ingin menyimpan jurnal sebelum reset.

## Sifat demo

Demo menggunakan data fiktif 31 jurnal dan 11 akun. Data terpisah di localStorage setiap browser, bukan dibagikan ke pengunjung lain. Login menggunakan pemeriksaan di frontend untuk demonstrasi alur; kredensial bersifat publik. Jangan gunakan sebagai autentikasi atau penyimpanan data keuangan produksi. Menghapus data browser juga menghapus jurnal lokal. Keluar akun mengakhiri sesi tanpa menghapus jurnal.

## Berkas

- index.html: halaman aplikasi
- style.css: tampilan responsif
- app.js: logika demo, jurnal, laporan dan Excel
- assets/xlsx.full.min.js: SheetJS Community Edition 0.20.3
- assets/LICENSE-SheetJS.txt: lisensi Apache 2.0 SheetJS
- .nojekyll: penanda hosting statis

## Validasi paket

Pemeriksaan sintaks JavaScript lulus. Pengujian perhitungan neraca, validasi data contoh, penolakan jurnal tidak seimbang/tanggal tidak valid, serta roundtrip XLSX lulus. Login dan penambahan jurnal (termasuk penolakan jurnal tidak seimbang) diperiksa melalui browser preview desktop. Layout responsif tersedia melalui CSS; belum diuji pada perangkat fisik. Publikasi GitHub Pages dan perubahan tautan portfolio harus dilakukan pada akun GitHub pemilik.

Dapur Kreatif / SCODE · Demo portfolio Nestiara

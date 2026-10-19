CBTVEN V4.3.2 – Menu Active & Batas Upload Gambar 1 MB

# CBTVEN V4.1.1 - Bank Soal Lengkap

Perbaikan penting pada Bank Soal:
- Migrasi otomatis database untuk kolom image_path, explanation, difficulty, tags, status, updated_at.
- Kompatibel dengan database CBTVEN lama; tidak menghapus data soal lama.
- Single Choice, Multi Select, dan Benar/Salah.
- Upload gambar soal JPG/PNG/WEBP/GIF maksimal 5 MB.
- Template/import Excel/CSV.
- Filter tipe dan tingkat kesulitan, draft/siap, tag, pembahasan, bobot.
- Perbaikan direktori upload gambar agar selalu dibuat otomatis.
- Penilaian ujian hanya menggunakan soal berstatus ready.

## Menjalankan

1. Ekstrak ZIP.
2. Buka PowerShell pada folder aplikasi.
3. Jalankan:

```powershell
npm install
npm start
```

4. Buka alamat yang ditampilkan server, misalnya `http://localhost:60696`.

## Penting
Jangan menghapus folder `data` jika ingin mempertahankan database lama.
Jika Anda menyalin versi ini ke folder aplikasi lama, backup folder `data` terlebih dahulu.


## V4.2.2 Bank Soal Fix
- Perbaikan upload gambar soal dan gambar opsi.
- Perbaikan tampilan opsi siswa agar object JSON tidak muncul sebagai [object Object].
- Kunci jawaban disimpan berdasarkan indeks opsi asli.
- Tidak mengganti database lama.


## V4.3.0 – Perbaikan Jadwal, Rekap Nilai, dan Alur Buat Soal
- Penghapusan jadwal yang sudah memiliki percobaan/nilai sekarang dicegah dengan pesan yang jelas agar data nilai tidak hilang tanpa sengaja. Hapus nilai terlebih dahulu dari menu Rekap Nilai.
- Rekap Nilai dipisahkan berdasarkan Mata Pelajaran: pilih mapel terlebih dahulu, lalu data, Cetak, dan CSV tampil untuk mapel tersebut.
- Nilai dapat dihapus per siswa atau sekaligus dengan pilihan terpilih.
- Buat Soal memiliki mode cepat: Simpan & Soal Berikutnya mempertahankan mata pelajaran dan pengaturan terakhir; tersedia juga Simpan & Tutup.
- Database lama tidak disertakan dalam paket update agar data pengguna tetap aman. Backup database sebelum update tetap disarankan.


## Perubahan V4.3.2
- Menu aktif ditandai biru muda dan tetap menandakan halaman yang sedang ditampilkan.
- Upload gambar soal dan gambar pilihan dibatasi maksimal 1 MB.
- Validasi frontend dan server disamakan pada batas 1 MB.
- Database lama tidak disertakan/ditimpa.


## V4.3.3 – Multi Select Fair Scoring
- Siswa hanya dapat memilih maksimal sejumlah kunci jawaban yang ditetapkan guru.
- Jumlah maksimum ditampilkan pada soal Multi Select tanpa membocorkan kunci mana yang benar.
- Backend menghitung poin parsial dengan penalti: (benar dipilih - salah dipilih) / total kunci.
- Skor per soal tidak pernah negatif.
- Kiriman jawaban yang melebihi batas jumlah kunci tidak mendapat poin untuk soal tersebut.


## V4.3.5 — Portal Siswa & Kendali CBT
- Navigasi nomor soal: klik nomor soal untuk berpindah langsung.
- Status soal: sudah dijawab/belum dijawab.
- Mode layar penuh saat ujian.
- Deteksi perpindahan tab/aplikasi, keluar fullscreen, refresh/menutup halaman; pelanggaran mengunci login siswa.
- Menu admin Reset CBT untuk melihat siswa yang sedang ujian/terkunci, menghentikan siswa, dan mengaktifkan kembali agar melanjutkan percobaan yang sama.
- Database lama dipertahankan; migrasi kolom baru berjalan otomatis.
- Catatan: browser/website tidak dapat benar-benar memblokir aplikasi OS lain atau mengendalikan shortcut sistem; implementasi menggunakan fullscreen + deteksi visibility/focus + penguncian server.


## V4.3.6 — Perbaikan Start Ujian & Reset CBT
- Memastikan kolom `cbt_locked`, `cbt_lock_reason`, `status`, `violation_reason`, dan `violation_at` tersedia pada database lama tanpa menghapus data.
- Endpoint mulai ujian dan kendali Reset CBT memiliki penanganan error server yang lebih jelas.
- Ujian yang dilanjutkan mengembalikan jawaban tersimpan agar siswa tidak kehilangan jawaban sebelumnya.
- Semua fitur V4.3.5 dipertahankan.


## V4.3.7
Perbaikan kompatibilitas SQLite pada proses mulai/resume ujian siswa dan Reset CBT. Query role siswa menggunakan parameter/string literal SQLite yang benar sehingga tidak lagi memunculkan error `no such column: siswa`. Database lama tetap digunakan dan dimigrasikan otomatis.


## V4.3.8 — Penyelesaian Ujian Lebih Aman & Modern
- Memperbaiki false-positive pelanggaran saat siswa membuka konfirmasi selesai ujian.
- Dialog konfirmasi selesai tidak lagi memicu deteksi `visibility`, `blur`, atau keluar fullscreen selama proses konfirmasi internal.
- Mengganti dialog browser sederhana menjadi dialog konfirmasi ujian yang lebih modern.
- Menampilkan Total Soal, Terjawab, dan Belum Dijawab.
- Memberi peringatan jika masih ada soal yang belum dijawab.
- Tombol `Ya, Selesaikan Ujian` dan `Kembali Mengerjakan` dibuat lebih jelas.
- Setelah berhasil dikirim, siswa mendapat halaman konfirmasi bahwa jawaban telah tersimpan.
- Semua fitur V4.3.7 dan versi sebelumnya dipertahankan.


## V4.3.9 rebuild
- Rekap Nilai: filter Mata Pelajaran + Kelas, cetak dan CSV.
- Kartu Login: password kartu terenkripsi, barcode URL login, kop, jenis ujian, tanggal, tanda tangan dan cap.
- Dibangun ulang langsung dari V4.3.8 untuk menjaga fitur Bank Soal dan fitur CBT tetap terbuka.

## V4.3.10 — Kartu Peserta 6 per A4
- Cetak kartu menjadi 6 kartu per kertas A4 (2 kolom × 3 baris).
- Desain kartu disesuaikan dengan contoh: logo kiri, kop 3 baris, Nama Peserta, Kelas, NIPD, NISN, tanda tangan, cap, dan QR Link Ujian.
- QR dibuat oleh server sehingga tidak bergantung pada CDN QR saat mencetak.
- Ditambahkan kolom NIPD pada data siswa, edit siswa, template/import siswa, dan data kartu.
- Logo sekolah dapat diunggah untuk kartu (maksimal 1 MB).
- Database lama tetap dipertahankan; kolom NIPD ditambahkan otomatis saat aplikasi dijalankan.


## V4.3.11 – Login pada kartu peserta
- Kartu cetak 6 per A4 sekarang menampilkan Username dan Password siswa.
- Password yang dicetak adalah password kartu yang dibuat melalui tombol "Buat/Reset Password Kartu".
- Jika password kartu belum dibuat, kartu menampilkan tanda `-`; buat password kartu terlebih dahulu sebelum mencetak.

## V4.3.17 – Peningkatan Paste Soal dari Word dan Sumber Lain
- Paste pada pertanyaan, pilihan jawaban, dan pembahasan membaca HTML clipboard jika tersedia, sehingga baris, tabel sederhana, simbol Unicode, superskrip, dan subskrip dapat dipertahankan/diubah ke bentuk teks yang sesuai.
- Dukungan pembacaan MathML clipboard untuk ekspresi umum: superskrip, subskrip, pecahan (ditulis sebagai pembilang/penyebut), akar, dan tabel sederhana.
- Jika gambar rumus disalin sebagai gambar clipboard dan ditempel ke kolom pertanyaan, gambar akan diarahkan ke fitur Gambar Soal (maksimal 1 MB) bila browser mendukung transfer file clipboard.
- Tidak mengubah menu, pengaturan, database, API penyimpanan soal, atau alur ujian lainnya.
- Batasan: rumus kompleks dari Word/PDF dapat disalin sebagai objek/gambar khusus atau format proprietari; hasilnya tidak dijamin identik. Untuk rumus yang penting, periksa pratinjau sebelum menyimpan.

### CBTVEN v4.3.19
- Panel simbol tertutup sampai tombol "Buka menu simbol dan rumus" diklik.
- Tombol Pangkat/Indeks di dalam panel simbol dihapus agar tidak duplikat.
- Tombol Pecahan/Rumus membantu memasukkan pecahan dalam notasi LaTeX.
Lihat `PERBAIKAN_V4.3.19.txt` untuk catatan dan batasan fitur.

## V4.3.24 — Pemilihan Soal per Jadwal Ujian
- Saat guru memilih mata pelajaran pada menu Jadwal, daftar soal berstatus Siap dari mata pelajaran tersebut otomatis ditampilkan.
- Guru dapat mencentang soal satu per satu atau menggunakan opsi **Pilih semua soal**.
- Jumlah soal yang dipilih ditampilkan sebelum jadwal disimpan.
- Daftar soal yang dipilih disimpan khusus untuk setiap jadwal; jadwal yang berbeda dapat menggunakan kombinasi soal yang berbeda dari mata pelajaran yang sama.
- Siswa hanya menerima soal yang dipilih pada jadwal tersebut. Perhitungan nilai dan koreksi esai mengikuti kumpulan soal yang sama.
- Jadwal lama tetap kompatibel dan menggunakan perilaku sebelumnya (semua soal berstatus Siap), tanpa menghapus data lama.
- Database dimigrasikan otomatis dengan kolom dan tabel baru saat aplikasi dijalankan. Tetap buat salinan cadangan folder `data` sebelum memperbarui aplikasi.

# Dompetku – versi login (data per akun)

Setiap orang membuat akun sendiri (email + password). Data tiap akun tersimpan terpisah di Supabase dan hanya bisa dibaca pemiliknya.

## Isi paket
- `index.html` – aplikasi dengan layar Daftar, Masuk, Lupa password, dan tombol Keluar
- `supabase-login.sql` – aturan akses database (jalankan di SQL Editor)

## Urutan pemasangan (ikuti berurutan)
1. **Pengaturan Supabase** (sudah Anda lakukan): Authentication > Sign In / Providers (Email aktif, Confirm email aktif) dan URL Configuration (Site URL dan Redirect URLs berisi alamat situs Vercel Anda).
2. **Unggah `index.html` baru** ke repository GitHub (Add file > Upload files, ganti `index.html` lama, Commit). Vercel otomatis memasang ulang; cek di tab Deployments sampai berstatus Ready.
3. **Buka situs, pilih "Belum punya akun? Daftar"**, isi email dan password (minimal 8 karakter). Buka email konfirmasi, klik tautannya, lalu masuk.
4. **Pindahkan data lama Anda** (jika ada). Dua cara, pilih salah satu:
   - Saat pertama masuk di browser yang sama dengan yang dulu dipakai, jika muncul pertanyaan "Impor data lama?", pilih OK.
   - Atau di Supabase buka Authentication > Users, salin **User UID** akun Anda, lalu jalankan baris `update ...` di bagian A pada `supabase-login.sql` (hapus tanda `--` di depannya dan ganti `ID-AKUN-ANDA`). Muat ulang situs dan masuk.
5. **Jalankan bagian B** pada `supabase-login.sql` untuk mengunci tabel. Setelah ini tanpa login tidak ada yang bisa membaca atau mengubah data.
6. **Uji**: keluar, daftar akun kedua (email lain atau jendela penyamaran), pastikan datanya kosong dan tidak ada data akun pertama.

## Catatan
- `SUPABASE_KEY` di `index.html` adalah *Publishable key*. Boleh terlihat publik; yang melindungi data adalah aturan di langkah 5. Jangan pernah menaruh *secret key* atau *service role key* di file ini.
- Email konfirmasi dan reset password memakai layanan email bawaan Supabase yang jumlahnya sangat terbatas per jam. Jika banyak pengguna mendaftar, atur SMTP sendiri (Authentication > Emails > SMTP Settings).
- Proyek gratis Supabase berhenti sementara jika tidak dipakai sekitar seminggu dan bisa dihidupkan lagi dari dashboard.
- Jika dibuka untuk umum, siapkan kebijakan privasi singkat karena data keuangan termasuk data pribadi.
- Pendaftaran bebas bisa ditutup kapan saja di Authentication > Sign In / Providers (matikan "Allow new users to sign up").

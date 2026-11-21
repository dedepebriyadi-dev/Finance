# Dompetku – Budgeting Keuangan

Aplikasi budgeting keuangan satu halaman (HTML, CSS, dan JavaScript saja, tanpa library luar).
Fitur: dashboard, transaksi, tabungan dan target, investasi, JHT BPJS, rekap 3 bulan.

## Catatan penting
- Data disimpan di **localStorage browser** pada perangkat yang dipakai. Data di laptop dan HP **tidak otomatis sinkron**, dan data hilang jika cache browser dihapus.
- Untuk sinkron antar perangkat, aplikasi perlu database online (misalnya Supabase atau Firebase).

## Cara publish ke GitHub Pages
1. Buat repository baru di github.com (misalnya `dompetku`), tanpa README bawaan.
2. Di komputer, buka terminal di folder ini lalu jalankan:

```bash
git init
git add .
git commit -m "Dompetku: versi pertama"
git branch -M main
git remote add origin https://github.com/USERNAME/dompetku.git
git push -u origin main
```

Ganti `USERNAME` dengan nama akun GitHub Anda.

3. Di GitHub, buka **Settings → Pages**.
4. Pada **Build and deployment**, pilih **Source: Deploy from a branch**, **Branch: main**, folder **/ (root)**, lalu **Save**.
5. Tunggu 1–2 menit. Alamatnya: `https://USERNAME.github.io/dompetku/`

Untuk memperbarui: ubah `index.html`, lalu `git add . && git commit -m "update" && git push`.

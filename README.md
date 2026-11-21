# Dompetku – Budgeting Keuangan

Aplikasi budgeting keuangan satu halaman (HTML, CSS, JavaScript). Fitur: dashboard, transaksi, tabungan dan target, investasi, JHT BPJS, anggaran dan hutang, rekap 3 bulan.

## Penyimpanan data
- Data disimpan di **browser** (localStorage) dan disinkronkan ke **Supabase** (tabel `dompetku_data`, satu baris dengan `id` sesuai `USER_RECORD_ID` di `index.html`).
- Jika Supabase tidak terhubung, aplikasi tetap jalan dan data tersimpan di browser perangkat itu saja.
- Pengaturan Supabase ada di bagian bawah `index.html`: `SUPABASE_URL` dan `SUPABASE_KEY` (gunakan *Publishable key*, bukan *secret key*).

### Tabel Supabase (SQL Editor)
```sql
create table if not exists dompetku_data (
  id text primary key,
  data jsonb not null,
  updated_at timestamptz default now()
);
alter table dompetku_data enable row level security;
create policy "dompetku akses" on dompetku_data
  for all using (true) with check (true);
```
Catatan keamanan: kebijakan di atas membuat siapa pun yang membuka situs dapat membaca dan mengubah baris data yang sama. Untuk data pribadi, sebaiknya tambahkan login (Supabase Auth) lalu batasi kebijakan ke pemilik data.

## Cara publish ke GitHub Pages
1. Buat repository baru di github.com (misalnya `dompetku`).
2. Di terminal, dari folder ini:

```bash
git init
git add .
git commit -m "Dompetku"
git branch -M main
git remote add origin https://github.com/USERNAME/dompetku.git
git push -u origin main
```

3. Di GitHub: **Settings → Pages → Source: Deploy from a branch → Branch: main → / (root) → Save**.
4. Alamatnya: `https://USERNAME.github.io/dompetku/`

Untuk memperbarui: ubah `index.html`, lalu `git add . && git commit -m "update" && git push`.

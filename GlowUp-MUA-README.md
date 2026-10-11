# GlowUp MUA — Sistem Akuntansi Jasa Makeup

Project ini mengikuti antarmuka GlowUp MUA yang sudah dibuat: dashboard, katalog paket, booking & jadwal, pembayaran, pengeluaran, dan laporan. Bagian transaksi diperluas agar menampilkan ringkasan uang masuk/keluar serta riwayat setiap DP, pelunasan, dan biaya operasional.

## Struktur folder

- `frontend/index.html` — struktur halaman
- `frontend/style.css` — desain pink
- `frontend/script.js` — interaksi frontend dan pemanggilan API
- `backend/app.js` — backend Node.js berbasis modul bawaan, tanpa Express
- `backend/schema.sql` — skema Supabase/PostgreSQL, tepat 4 tabel utama
- `backend/demo_seed.sql` — data demo opsional untuk presentasi, bukan transaksi asli

## Setup Supabase

1. Buat project di Supabase.
2. Buka SQL Editor dan jalankan seluruh `backend/schema.sql`.
3. Kalau butuh tampilan berisi contoh transaksi untuk latihan/presentasi, jalankan `backend/demo_seed.sql` setelah `schema.sql`. Ini data contoh, bukan data transaksi asli. Jangan jalankan jika tidak ingin data demo masuk ke database.
4. Salin Project URL dan `service_role` key dari pengaturan API Supabase. Jangan pernah menaruh service-role key di frontend atau mengunggahnya ke GitHub.

## Menjalankan backend

Backend memakai `http`, `fs`, `path`, dan `fetch` bawaan Node.js; tidak membutuhkan `package.json` atau package tambahan. Gunakan Node.js 18 atau lebih baru.

Atur environment variable sebelum menjalankan:

**Windows PowerShell**
```powershell
$env:SUPABASE_URL="https://PROJECT-REF.supabase.co"
$env:SUPABASE_SERVICE_ROLE_KEY="ISI_SERVICE_ROLE_KEY"
node backend/app.js
```

**macOS/Linux**
```bash
export SUPABASE_URL="https://PROJECT-REF.supabase.co"
export SUPABASE_SERVICE_ROLE_KEY="ISI_SERVICE_ROLE_KEY"
node backend/app.js
```

Buka `http://localhost:3000`. Jangan buka `index.html` langsung karena frontend memanggil API backend.

## Catatan data lama

Website GitHub Pages tidak memberikan akses otomatis ke data yang tersimpan di `localStorage` browser. Data lama harus diekspor/dimasukkan ke Supabase secara terpisah. Backend ini menyimpan data baru di Supabase. `demo_seed.sql` hanya data contoh untuk menguji bahwa daftar transaksi tidak kosong.

# Email skincare Toco (Customer.io)

Build ulang: `python3 build_emails.py` (data produk dari `../quiz_pool.json`).
Tempel file `*.liquid.html` ke Customer.io. File `*.preview.html` hanya untuk pratinjau.

| Email | Pemicu | Subject | Preheader |
|---|---|---|---|
| 1. Peluncuran | Broadcast ke segment 265 "Engaged & Clean Email List" | Kulitmu butuh apa? Cek dalam 1 menit | Kuis 1 menit, dapat rutinitas dari Wardah, Emina, Cetaphil, Kahf. Mulai Rp20 ribuan. |
| 2. Hasil kuis | Event `skincare_quiz_completed`, kirim langsung | Rutinitas skincare kamu sudah siap | Rutinitas dari beberapa brand, sesuai kulit dan budget kamu. |
| 3. Beli lagi | 30 hari setelah order skincare selesai, keluarkan yang sudah beli ulang | Waktunya isi ulang? | Sudah sebulan sejak terakhir beli. Beli lagi dalam satu ketuk. |

## Data event yang dibutuhkan

`skincare_quiz_completed`:
- `title` (contoh "Kulit kombinasi, fokus bekas jerawat dan noda"), `brands` ("Emina, Wardah, Kojie.san"), `total_label` ("Rp257.608")
- `routine`: array of `{step, why, brand, name, image, slug, price_label}`

Email 3 (event pembelian ulang): `product_name`, `brand`, `image`, `slug`, `price_label`, `days_since`.

## Sebelum kirim
- `HUB` dan `QUIZ` di `build_emails.py` masih mengarah ke versi demo di GitHub Pages. Ganti dengan URL final di toco.id sebelum kirim.
- Gambar produk dan logo brand memakai WebP dari CDN Toco. Aman di Gmail, Apple Mail, dan aplikasi email di HP; Outlook desktop tidak menampilkan WebP. Kalau perlu, unggah versi JPG/PNG ke asset library Customer.io.
- Pasang conversion goal "Order Completed" dan holdout 15% di setiap campaign.

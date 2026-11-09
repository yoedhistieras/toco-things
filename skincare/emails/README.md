# Email skincare Toco (Customer.io)

Build ulang: `python3 build_emails.py` (data produk dari `../quiz_pool.json`).
Tempel file `*.liquid.html` ke Customer.io. File `*.preview.html` hanya untuk pratinjau.

Susunan tiap email mengikuti email skincare asli, lalu diganti ke warna dan gaya Toco. Teks, foto, dan aset brand referensi tidak disalin.

| Email | Referensi susunan | Pemicu | Subject | Preheader |
|---|---|---|---|---|
| 1. Peluncuran | [Dermstore, Your Skin's Ready for a Fall Reset](https://www.sequenzy.com/email-examples/brands/dermstore/emails/your-skin-s-ready-for-a-fall-reset) | Broadcast ke segment 265 "Engaged & Clean Email List" | Kulitmu butuh apa? Cek dalam 1 menit | Kuis 1 menit, dapat rutinitas dari Wardah, Emina, Cetaphil, Kahf. |
| 2. Hasil kuis | [Origins, What does your skin need this fall?](https://www.sequenzy.com/email-examples/brands/origins/emails/what-does-your-skin-need-this-fall-ucfuvk) | Event `skincare_quiz_completed`, kirim langsung | Rutinitas skincare kamu sudah siap | Rutinitas dari beberapa brand, sesuai kulit dan budget kamu. |
| 3. Beli lagi | [Dermstore, Auto-Replenishment](https://www.sequenzy.com/email-examples/brands/dermstore/emails/hsa-fsa-eligible-auto-replenishment) | 30 hari setelah order skincare selesai, keluarkan yang sudah beli ulang | Waktunya isi ulang? | Sudah sebulan sejak terakhir beli. Beli lagi dalam satu ketuk. |
| 4. Sudah cari, belum beli | [Dermstore, Something Caught Your Eye?](https://www.sequenzy.com/email-examples/brands/dermstore/emails/something-caught-your-eye-save-up-to-25) | Event `products searched` dengan kata kunci skincare, tanpa pembelian dalam 2 hari | Masih cari skincare? | Pilihannya masih ada, langsung dari toko resmi. |
| 5. Promo kategori | [Dermstore, Best of Dermstore Kits](https://www.sequenzy.com/email-examples/brands/dermstore/emails/up-to-40-off-shop-our-best-of-dermstore-kits) | Broadcast saat ada promo kategori skincare | {{promo_name}}: {{discount}} skincare | Promo skincare dari toko resmi di Toco. |

Email 5: ganti nama promo, diskon, kode, tanggal, dan syarat di baris `assign` paling atas. Nilai bawaannya hanya contoh, belum ada vouchernya.

## Data event yang dibutuhkan

`skincare_quiz_completed`:
- `title` (contoh "Kulit kombinasi, fokus bekas jerawat dan noda"), `brands` ("Emina, Wardah, Kojie.san"), `total_label` ("Rp257.608")
- `routine`: array of `{step, why, brand, name, image, slug, price_label}`

Email 3 (event pembelian ulang): `product_name`, `image`, `slug`, `price_label`, `days_since`.

Email 4: memakai `search_query` dari event `products searched` yang sudah ada. Kalau kosong, otomatis tertulis "skincare".

## Sebelum kirim
- `HUB` dan `QUIZ` di `build_emails.py` masih mengarah ke versi demo di GitHub Pages. Ganti dengan URL final di toco.id sebelum kirim.
- Gambar hero Email 1 (`assets/email/hero-launch.jpg`) harus sudah di-host sebelum dikirim.
- Gambar produk dan logo brand memakai WebP dari CDN Toco. Aman di Gmail, Apple Mail, dan aplikasi email di HP; Outlook desktop tidak menampilkan WebP.
- Pasang conversion goal "Order Completed" dan holdout 15% di setiap campaign.

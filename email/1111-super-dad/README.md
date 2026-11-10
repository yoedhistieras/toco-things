# Email 11.11 Super Dad, Super Deal

- `email.liquid.html`: tempel ke Customer.io (Newsletter > Email > Code editor). Nama pakai `customer.name`, sama dengan push weekend.
- `preview.html`: pratinjau dengan nama contoh "Budi".
- Gambar di-host di GitHub Pages: https://yoedhistieras.github.io/toco-things/email/1111-super-dad/img/
- Semua link memakai UTM `utm_source=customerio&utm_medium=email&utm_campaign=1111_superdad&utm_content=<slot>`.

## Subject (A/B)
A: Hari Ayah besok, diskonnya hari ini sampai 78% 🎁
B: {% if customer.name != blank %}{{ customer.name | split: " " | first }}{% else %}Kak{% endif %}, hadiah buat Bapak hemat sampai Rp1 juta
C: Tas, sepatu, gadget Bapak diskon sampai 78% + gratis ongkir

Preheader: Diskon sampai 78% plus gratis ongkir. Hadiah buat Bapak, beres sebelum Hari Ayah.

## Kirim
- Rabu 11 Nov 2026, 10:00 WIB (slot email weekend), timezone Etc/GMT-7
- Penerima: segment email bersih (265) DAN BUKAN 622
- Conversion goal: event `purchase` dalam 48 jam

## Cek sebelum kirim
- Harga dan diskon diambil dari halaman campaign 10 Nov 2026. Cek ulang pagi 11 Nov, terutama stok iPhone 15 (tertulis "Sisa 5").
- Pastikan jam berakhir promo dan syarat gratis ongkir dari tim promo.

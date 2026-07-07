# Kuesioner MagoGo

Halaman statis sederhana yang menampilkan Google Form dalam tampilan yang rapi dan profesional, sesuai palet warna MagoGo.

## Struktur

```
index.html            # satu-satunya halaman, sudah termasuk semua CSS
vercel.json           # konfigurasi minimal untuk Vercel
assets/
  magogo-product.png  # foto produk yang tampil di bagian "Apa itu MagoGo?"
```

Tidak ada build step — ini murni HTML/CSS statis, jadi deploy-nya cepat dan sederhana.

## Cara deploy ke Vercel

**Opsi 1 — lewat website Vercel (paling mudah)**
1. Buka https://vercel.com dan login (bisa pakai akun GitHub/Google).
2. Klik **Add New → Project**.
3. Pilih **"Deploy without Git"** / drag-and-drop, lalu seret folder ini (atau upload ketiga file di atas).
4. Klik **Deploy**. Selesai dalam beberapa detik, Anda akan mendapat URL seperti `https://nama-proyek.vercel.app`.

**Opsi 2 — lewat GitHub**
1. Buat repository baru di GitHub, upload folder ini.
2. Di Vercel: **Add New → Project → Import Git Repository**, pilih repo tadi.
3. Framework preset: pilih **"Other"** (karena ini statis, tanpa build command).
4. Klik **Deploy**.

**Opsi 3 — lewat Vercel CLI**
```bash
npm i -g vercel
cd magogo-form-site
vercel        # ikuti instruksi, lalu
vercel --prod # untuk deploy ke production
```

## Mengganti link Google Form

Link form sudah ditanam di `index.html` pada dua tempat:
- atribut `src` pada tag `<iframe class="gform">`
- link "Buka formulir di tab baru" di bagian footer

Jika suatu saat Anda ingin mengganti form, cukup ganti kedua URL tersebut dengan link form yang baru (tambahkan `?embedded=true` di akhir URL iframe agar tampilannya tanpa header Google Form yang besar).

## Mengganti foto produk

Foto di bagian "Apa itu MagoGo?" ada di `assets/magogo-product.png`. Untuk menggantinya, cukup timpa file itu dengan foto baru (nama file sama), atau ganti path-nya di `index.html` pada tag `<img src="assets/magogo-product.png" ...>`. Pastikan folder `assets/` ikut ter-upload/ter-push, kalau tidak fotonya tidak akan muncul saat live.

## Mengganti tombol "Lanjutkan" setelah kuesioner

Karena Google Form berada di iframe cross-origin, situs ini **tidak bisa mendeteksi otomatis** kapan seseorang menekan "Kirim" di dalam form. Solusinya: ada kartu ajakan (CTA) berwarna hijau tepat di bawah form yang mengarahkan pengguna secara manual. Untuk mengganti tujuannya, cari baris berikut di `index.html` dan ganti URL-nya:

```html
<a class="cta-button" href="https://magogos.vercel.app/" target="_blank" rel="noopener">
```

## Mengatur tinggi form (biar tidak scroll dobel)

Iframe sengaja dibuat sangat tinggi (`3300px` di desktop, `3800px` di mobile) supaya kontennya tidak punya scrollbar sendiri — jadi hanya halaman utama yang bisa di-scroll. Jika form Anda lebih panjang/pendek dari perkiraan, cari baris berikut di `index.html` (ada dua: satu di dalam `.gform`, satu di media query) dan sesuaikan angkanya:

```css
iframe.gform { height: 3300px; }
```

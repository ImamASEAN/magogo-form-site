# Kuesioner MagoGo

Halaman statis sederhana yang menampilkan Google Form dalam tampilan yang rapi dan profesional, sesuai palet warna MagoGo.

## Struktur

```
index.html    # satu-satunya halaman, sudah termasuk semua CSS
vercel.json   # konfigurasi minimal untuk Vercel
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

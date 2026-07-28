# cv\_template

Template LaTeX untuk CV atau resume satu halaman yang dirancang agar tetap terbaca oleh sistem ATS (Applicant Tracking System). Tata letak mengutamakan keterbacaan teks dengan tipografi sans-serif yang konsisten tanpa elemen dekoratif yang mengganggu parser.

---

## Persyaratan

- Distribusi LaTeX: **TeX Live 2020+** atau **MiKTeX**
- Perintah **`xelatex`** tersedia di `$PATH`
- Font **TeX Gyre Heros** (sudah termasuk dalam TeX Live dan MiKTeX)
- Opsional: **Overleaf** (kompatibel, pastikan compiler diatur ke XeLaTeX)

---

## Struktur Proyek

```
cv_template/
├── fig/
│   └── me.png              # Foto portrait rasio 3:4
├── sections/
│   ├── header.tex           # Foto, nama, kontak, ringkasan
│   ├── education.tex        # Riwayat pendidikan
│   ├── experience.tex       # Pengalaman kerja
│   ├── organizations.tex    # Pengalaman organisasi dan kepanitiaan
│   ├── certifications.tex   # Sertifikasi dan pelatihan
│   └── skills.tex           # Keahlian teknis, soft skills, bahasa
├── info.tex                 # Data pribadi (nama, email, telepon, dll.)
├── main.tex                 # Berkas utama; edit hanya untuk menambah/menghapus seksi
├── preamble.tex             # Konfigurasi paket, font, dan perintah kustom
└── README.md
```

---

## Cara Menggunakan

### 1. Unduh proyek

```bash
git clone https://github.com/Caseinn/cv_template.git
cd cv_template
```

### 2. Isi data pribadi

Buka `info.tex` dan ubah nilainya:

```tex
\newcommand{\myname}{Nama Anda}
\newcommand{\myemail}{email.anda@example.com}
\newcommand{\myphone}{+62812-XXXX-XXXX}
\newcommand{\mylinkedin}{linkedin.com/in/nama-anda}
\newcommand{\mywebsite}{portfolioanda.web.id}
```

### 3. Siapkan foto

Letakkan foto dengan rasio 3:4 (rekomendasi: 1107×1476 piksel) di `fig/me.png`. Template akan menampilkan foto dengan lebar 0,9 inci.

Jika tidak memiliki foto, cukup hapus file `fig/me.png`. Template akan menampilkan placeholder abu-abu sebagai gantinya.

### 4. Edit konten setiap seksi

Setiap file di folder `sections/` berisi satu seksi lengkap dengan instruksi dan contoh. Ganti teks placeholder dengan data Anda sendiri.

### 5. Kompilasi

Jalankan perintah berikut di terminal:

```bash
xelatex main.tex
xelatex main.tex
```

Hasil kompilasi adalah `main.pdf`.

---

## Kustomisasi

### Data pribadi

Semua data pribadi didefinisikan di `info.tex`. Cukup ubah nilainya di satu tempat, dan seluruh dokumen akan menyesuaikan.

### Warna tautan

Warna hyperlink diatur di `preamble.tex`:

```tex
\definecolor{linkblue}{HTML}{0055A0}
```

Ganti kode hex dengan warna yang diinginkan.

### Font

Template menggunakan TeX Gyre Heros secara default. Untuk menggantinya:

```tex
\setmainfont{Nama Font}[
    Scale = 0.94,
    Ligatures = NoCommon,
]
```

Pastikan font yang digunakan terinstal di sistem.

### Margin

Ukuran margin diatur melalui opsi paket `geometry`:

```tex
\usepackage[top=0.7in, bottom=0.7in, left=0.75in, right=0.75in]{geometry}
```

### Urutan seksi

Buka `main.tex` untuk menambah, menghapus, atau mengubah urutan seksi:

```tex
\begin{document}
\input{sections/header}
\input{sections/education}
\input{sections/experience}
%\input{sections/organizations}
\input{sections/certifications}
\input{sections/skills}
\end{document}
```

Cukup beri tanda komentar (`%`) pada baris yang tidak diinginkan, atau tambahkan baris `\input` baru untuk seksi tambahan.

---

## Kompilasi

### Lokal (TeX Live / MiKTeX)

```bash
xelatex main.tex
xelatex main.tex
```

Disarankan menjalankan dua kali agar referensi dan metadata PDF terbentuk dengan benar.

### Overleaf

1. Unggah seluruh folder proyek ke Overleaf.
2. Atur compiler ke **XeLaTeX** (Menu → Compiler → XeLaTeX).
3. Klik Recompile.

---

## Tips

- Ringkasan profesional cukup 2–3 kalimat (30–50 kata). Jelaskan siapa Anda, bidang yang ditekuni, dan nilai yang ditawarkan.
- Setiap entri pengalaman kerja sebaiknya memiliki 2–4 butir poin. Fokus pada pencapaian, bukan hanya daftar tanggung jawab.
- Gunakan kata kerja aktif seperti "Mengembangkan", "Membangun", "Merancang", atau "Mengoptimalkan".
- Cantumkan IPK jika di atas 3.00 dari skala 4.00.
- Cantumkan 4–8 sertifikasi yang paling relevan. Utamakan yang memiliki URL verifikasi.
- Untuk keahlian, tulis 5–10 teknologi untuk hard skills, 3–5 untuk soft skills. Hanya cantumkan yang benar-benar Anda kuasai.
- Jika pengalaman kerja sudah cukup memenuhi satu halaman, seksi organisasi bisa dihapus.

---

## Kontribusi

Jika Anda menemukan bug atau memiliki saran perbaikan, silakan buka *issue* di repositori GitHub. *Pull request* juga sangat diterima.

---
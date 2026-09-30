# cv\_template

Template LaTeX untuk CV atau resume satu halaman yang tetap terbaca oleh sistem ATS (Applicant Tracking System). Tata letak mengutamakan keterbacaan teks, memakai tipografi sans-serif yang konsisten tanpa elemen dekoratif yang mengganggu parser.

---

## Persyaratan

- Distribusi LaTeX: **TeX Live 2020+** atau **MiKTeX**
- Perintah **`xelatex`** tersedia di `$PATH`
- Font **TeX Gyre Heros** (sudah termasuk dalam TeX Live dan MiKTeX)
- Opsional: **Overleaf** (kompatibel, pastikan compiler disetel ke XeLaTeX)

---

## Struktur Proyek

```
cv_template/
├── fig/
│   └── me.png              # Foto potret rasio 3:4
├── sections/
│   ├── header.tex           # Foto, nama, kontak, ringkasan
│   ├── education.tex        # Riwayat pendidikan
│   ├── experience.tex       # Pengalaman kerja
│   ├── organizations.tex    # Pengalaman organisasi dan kepanitiaan
│   ├── certifications.tex   # Sertifikasi dan pelatihan
│   └── skills.tex           # Keahlian teknis, soft skills, bahasa
├── info.tex                 # Data pribadi (nama, email, telepon, LinkedIn, website)
├── main.tex                 # Berkas utama; edit hanya untuk menambah atau menghapus seksi
├── preamble.tex             # Konfigurasi paket, font, dan perintah kustom
└── README.md
```

---

## Cara Menggunakan

### 1. Unduh Proyek

```bash
git clone https://github.com/Caseinn/cv_template.git
cd cv_template
```

### 2. Isi Data Pribadi

Buka `info.tex` dan ganti nilainya:

```tex
\newcommand{\myname}{Nama Anda}
\newcommand{\myemail}{email.anda@example.com}
\newcommand{\myphone}{+62812-XXXX-XXXX}
\newcommand{\mylinkedin}{linkedin.com/in/nama-anda}
\newcommand{\mywebsite}{portfolioanda.web.id}
```

### 3. Siapkan Foto

Letakkan foto dengan rasio 3:4 (rekomendasi: 1107 × 1476 piksel) di `fig/me.png`. Template menampilkannya dengan lebar 0,9 inci.

Kalau tidak punya foto, hapus saja `fig/me.png`. Template akan menampilkan placeholder abu-abu sebagai gantinya.

### 4. Edit Konten Setiap Seksi

Setiap file di `sections/` berisi satu seksi lengkap dengan instruksi dan contoh. Ganti teks placeholder dengan data Anda.

### 5. Kompilasi

Jalankan dari terminal:

```bash
xelatex main.tex
xelatex main.tex
```

Jalankan dua kali agar referensi dan metadata PDF terbentuk dengan benar. Hasilnya ada di `main.pdf`.

---

## Kustomisasi

### Data Pribadi

Semua data pribadi ada di `info.tex`. Ubah di satu tempat, seluruh dokumen menyesuaikan.

### Warna Tautan

Warna hyperlink diatur di `preamble.tex`:

```tex
\definecolor{linkblue}{HTML}{0055A0}
```

Ganti kode hex dengan warna pilihan Anda.

### Font

Template memakai TeX Gyre Heros secara default. Untuk mengganti font:

```tex
\setmainfont{Nama Font}[
    Scale = 0.94,
    Ligatures = NoCommon,
]
```

Pastikan font itu sudah terinstal di sistem.

### Margin

Ukuran margin diatur lewat opsi paket `geometry`:

```tex
\usepackage[top=0.7in, bottom=0.7in, left=0.75in, right=0.75in]{geometry}
```

### Urutan Seksi

Buka `main.tex` untuk menambah, menghapus, atau mengurutkan ulang seksi:

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

Beri tanda komentar (`%`) pada baris yang tidak diperlukan, atau tambah baris `\input` baru untuk seksi tambahan.

---

## Overleaf

1. Unggah seluruh folder proyek ke Overleaf.
2. Setel compiler ke **XeLaTeX** (Menu → Compiler → XeLaTeX).
3. Klik Recompile.

---

## Tips

- Ringkasan profesional cukup 2–3 kalimat (30–50 kata). Jelaskan siapa Anda, bidang yang ditekuni, dan nilai yang Anda tawarkan.
- Setiap entri pengalaman kerja sebaiknya punya 2–4 butir poin. Fokuskan pada pencapaian, bukan daftar tanggung jawab.
- Pakai kata kerja aktif seperti "mengembangkan", "membangun", "merancang", atau "mengoptimalkan".
- Cantumkan sertifikasi yang relevan, utamakan yang punya URL verifikasi.
- Untuk keahlian, tulis 5–10 teknologi untuk hard skills dan 3–5 untuk soft skills. Hanya cantumkan yang benar-benar Anda kuasai.
- Kalau pengalaman kerja sudah cukup memenuhi satu halaman, seksi organisasi bisa dihapus.

---

## Kontribusi

Kalau Anda menemukan bug atau punya saran perbaikan, silakan buka *issue* di repositori GitHub. *Pull request* juga diterima.

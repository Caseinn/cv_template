# Template CV ATS-Friendly

Template LaTeX untuk Curriculum Vitae (CV) atau resume satu halaman yang rapi, modern, dan ramah ATS (Applicant Tracking System). Dibangun dengan struktur modular, font sans-serif, dan tata letak yang bersih.

---

## Persyaratan Sistem

- **LaTeX distribution**: TeX Live 2020+ atau MiKTeX
- **Compiler**: `xelatex` (wajib, karena menggunakan font sistem)
- **Font**: TeX Gyre Heros (akan terinstall otomatis bersama TeX Live / MiKTeX)

---

## Cara Menggunakan

### 1. Clone atau salin folder ini

```bash
cp -r CV_Template/ CV_Saya/
cd CV_Saya
```

### 2. Isi data pribadi

Edit `info.tex` — ganti dengan data Anda:

```tex
\newcommand{\myname}{Nama Lengkap}
\newcommand{\myemail}{email.anda@gmail.com}
\newcommand{\myphone}{+62812-XXXX-XXXX}
\newcommand{\mylinkedin}{linkedin.com/in/nama-anda}
\newcommand{\mywebsite}{portfolioanda.web.id}
```

### 3. Siapkan foto

Letakkan foto 3:4 portrait di `fig/me.png`. Rekomendasi: 1107×1476 pixel, latar belakang profesional.

Tidak punya foto? Hapus saja file `fig/me.png` — template otomatis menampilkan placeholder abu-abu.

### 4. Edit konten setiap seksi

| File | Seksi |
|------|-------|
| `sections/header.tex` | Ringkasan profesional (summary) |
| `sections/education.tex` | Riwayat pendidikan |
| `sections/experience.tex` | Pengalaman kerja |
| `sections/organizations.tex` | Organisasi dan kepanitiaan |
| `sections/certifications.tex` | Sertifikasi dan pelatihan |
| `sections/skills.tex` | Keahlian teknis, soft skills, bahasa |

### 5. Kompilasi

```bash
xelatex main.tex
xelatex main.tex   # jalankan dua kali untuk menyelesaikan referensi
```

Hasil: `main.pdf`

---

## Struktur File

```
CV_Template/
├── fig/
│   └── me.png              # Foto 3:4 (placeholder otomatis jika tidak ada)
├── sections/
│   ├── header.tex           # Header: foto, nama, kontak, summary
│   ├── education.tex        # Pendidikan
│   ├── experience.tex       # Pengalaman kerja
│   ├── organizations.tex    # Organisasi & event
│   ├── certifications.tex   # Sertifikasi
│   └── skills.tex           # Keahlian
├── info.tex                 # Data pribadi (nama, email, dll)
├── main.tex                 # Entry point (jangan diubah)
├── preamble.tex             # Package & style (jangan diubah)
└── README.md                # Dokumen ini
```

---

## Kustomisasi

### Mengganti font

Edit `preamble.tex`:

```tex
\setmainfont{Nama Font}[
    Scale = 0.94,
    Ligatures = NoCommon,
]
```

### Mengubah warna link

Edit `preamble.tex`:

```tex
\definecolor{linkblue}{HTML}{0055A0}   % Ganti kode hex sesuai keinginan
```

### Mengatur margin

Edit `preamble.tex`:

```tex
\usepackage[top=0.7in, bottom=0.7in, left=0.75in, right=0.75in]{geometry}
```

### Menambah/menghapus seksi

Edit `main.tex` — tambah atau hapus baris `\input{sections/...}`:

```tex
\begin{document}
\input{sections/header}
\input{sections/education}
\input{sections/experience}
%\input{sections/organizations}    % nonaktifkan jika tidak perlu
\input{sections/certifications}
\input{sections/skills}
\end{document}
```

---

## Command yang Tersedia

| Command | Fungsi | Contoh |
|---------|--------|--------|
| `\entry{org}{tgl}{role}` | Entry 3 baris: organisasi (kiri) + tanggal (kanan), lalu peran (miring) | `\entry{PT ABC}{Jan 2024 -- Des 2024}{Intern}` |
| `\entryline{kiri}{kanan}` | Entry 1 baris: teks kiri + teks kanan | `\entryline{Sertifikat XYZ -- Provider}{Jan 2024}` |
| `\entrycert{judul}{prov}{tgl}` | Entry 2 baris: judul bold, lalu provider (kiri) + tanggal (kanan) | `\entrycert{\href{url}{Judul}}{Provider}{Jan 2024}` |
| `\bul{teks}` | Poin bullet dengan hanging indent | `\bul{Mengembangkan fitur X menggunakan Y.}` |

---

## Best Practice

### Ringkasan (Summary)
- 2-3 kalimat, 30-50 kata total
- Kalimat 1: Siapa Anda (jurusan, bidang, keahlian utama)
- Kalimat 2: Apa yang Anda kerjakan (tools, domain, teknologi)
- Kalimat 3: Soft skills atau gaya bekerja

### Pengalaman Kerja
- Urutkan kronologis terbalik (terbaru di atas)
- 2-4 bullet per entry, masing-masing 10-20 kata
- Gunakan kata kerja aktif: Mengembangkan, Membangun, Merancang, Mengoptimalkan
- Kuantifikasi bila mungkin (persen, pengguna, waktu)
- Fokus pada pencapaian, bukan sekadar tanggung jawab

### Pendidikan
- GPA dicantumkan jika 3.00+/4.00
- Skripsi: beri hyperlink jika tersedia online
- Maksimal 1 bullet poin

### Sertifikasi
- Cantumkan 4-8 sertifikasi paling relevan
- Utamakan yang memiliki URL verifikasi
- Gunakan `\entrycert` untuk format 2 baris (judul bold, provider + tanggal)

### Keahlian
- Hard Skills: 5-10 teknologi/alat yang relevan
- Soft Skills: 3-5 kemampuan interpersonal
- Bahasa: sertakan tingkat kemahiran dalam tanda kurung
- Jujur — hanya cantumkan yang bisa dijelaskan saat wawancara

### Organisasi
- 1-2 bullet per entry
- Fokus pada kontribusi nyata, bukan deskripsi organisasi
- Bisa dihapus jika pengalaman kerja sudah cukup memenuhi halaman

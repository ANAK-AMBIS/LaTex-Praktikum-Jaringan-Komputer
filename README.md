# LaTeX Praktikum Jaringan Komputer IF25-21008

Template LaTeX 1:1 dari `Template Laporan Praktikum Jarkom IF25-21008 (2026).docx`.

## Daftar Isi

- [Kompilasi](#kompilasi)
- [Font](#font)
- [Struktur Proyek](#struktur-proyek)

## Kompilasi

Gunakan **XeLaTeX** (MiKTeX di Windows). Contoh di bawah memakai PowerShell.

**Opsi 1: manual (jalankan 2x agar daftar isi dan referensi terbarui)**

```powershell
$xe = "C:\Users\Jeremi\AppData\Local\Programs\MiKTeX\miktex\bin\x64\xelatex.exe"
& $xe -interaction=nonstopmode main.tex
& $xe -interaction=nonstopmode main.tex
```

**Opsi 2: sekali perintah dengan `latexmk`**

```powershell
& "C:\Users\Jeremi\AppData\Local\Programs\MiKTeX\miktex\bin\x64\latexmk.exe" -xelatex -pdf -interaction=nonstopmode main.tex
```

**Opsi 3: auto-recompile setiap file disimpan**

```powershell
& "C:\Users\Jeremi\AppData\Local\Programs\MiKTeX\miktex\bin\x64\latexmk.exe" -xelatex -pdf -pvc -interaction=nonstopmode main.tex
```

## Font

Template memakai font bawaan Windows, sesuai dokumen `.docx` aslinya:

- Garamond
- Arial Black
- Arial
- Bernard MT Condensed
- Cambria

Cek ketersediaan font di MiKTeX:

```powershell
miktex-fc-list | Select-String "Garamond|Arial Black|Bernard|Cambria"
```

> ⚠️ **Overleaf / Linux:** font-font di atas tidak tersedia. Install `EB Garamond` dan sesuaikan `\setmainfont` bila perlu.

### Pemetaan ukuran dan font

| Bagian | Font dan ukuran |
|---|---|
| Isi (body) | Garamond 12 pt |
| Caption dan tabel | 8 pt |
| Referensi (daftar pustaka) | 11 pt |
| Cover | Cambria 14 pt; Arial Black 10 pt dan 52 pt; Garamond 10 pt Bold; Garamond 20 pt; Bernard 24 pt Bold; Garamond 14 pt Bold |
| Judul halaman dalam | 36 pt |
| Anggota | 10 pt Bold |
| Rangkuman | Arial 12 pt |
| Judul Alat dan Tugas | Garamond 20 pt Bold |
| Judul Referensi | Arial Black 15 pt |
| Header dan footer | Arial Black 7 pt / 8 pt |

## Struktur Proyek

| Path | Isi |
|---|---|
| `main.tex` | Cover, halaman dalam, header/footer, dan paket |
| `data/` | Identitas, kelas, asisten, anggota, dan laporan (pertemuan, judul, bulan) |
| `isi/` | Rangkuman, `dokumentasi/langkah-1..3`, alat dan bahan, tugas, referensi |
| `aset/gambar/logotera.png` | Logo yang dipakai (salinan `logotera.png` di root tidak dipakai) |

**Catatan gambar:** gambar dokumentasi memakai fallback `\gambarpengganti`. Jika file gambar tidak ada, akan tampil kotak bertuliskan "belum tersedia".

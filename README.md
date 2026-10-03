# LaTeX Praktikum Jaringan Komputer IF25-21008

Template LaTeX 1:1 dari `Template Laporan Praktikum Jarkom IF25-21008 (2026).docx`.

## Kompilasi (XeLaTeX, 2x)

```powershell
$xe = "C:\Users\Jeremi\AppData\Local\Programs\MiKTeX\miktex\bin\x64\xelatex.exe"
& $xe -interaction=nonstopmode main.tex
& $xe -interaction=nonstopmode main.tex
```

Atau sekali perintah:

```powershell
& "C:\Users\Jeremi\AppData\Local\Programs\MiKTeX\miktex\bin\x64\latexmk.exe" -xelatex -pdf -interaction=nonstopmode main.tex
```

Auto-recompile tiap save:

```powershell
& "C:\Users\Jeremi\AppData\Local\Programs\MiKTeX\miktex\bin\x64\latexmk.exe" -xelatex -pdf -pvc -interaction=nonstopmode main.tex
```

## Font (sesuai docx)

Membutuhkan font Windows: `Garamond`, `Arial Black`, `Arial`, `Bernard MT Condensed`, `Cambria`.
Cek: `miktex-fc-list | Select-String "Garamond|Arial Black|Bernard|Cambria"`.
Di Overleaf/Linux font ini tidak tersedia — install `EB Garamond` + sesuaikan `\setmainfont` bila perlu.

Pemetaan: body Garamond 12pt, caption/tabel 8pt, referensi 11pt, cover Cambria 14pt / Arial Black 10+52pt / Garamond 10 Bold / Garamond 20 / Bernard 24 Bold / Garamond 14 Bold, judul dalam 36pt, anggota 10pt Bold, rangkuman Arial 12pt, Alat/Tugas Garamond 20 Bold, Referensi Arial Black 15pt, header/footer Arial Black 7/8pt.

## Struktur

- `main.tex` — cover, halaman dalam, header/footer, paket.
- `data/` — identitas, kelas, asisten, anggota, laporan (pertemuan/judul/bulan).
- `isi/` — rangkuman, dokumentasi/langkah-1..3, alat-dan-bahan, tugas, referensi.
- `aset/gambar/logotera.png` — logo (salinan root `logotera.png` tidak dipakai).
- Gambar dokumentasi memakai fallback `\gambarpengganti`; bila file tidak ada tampil kotak "belum tersedia".

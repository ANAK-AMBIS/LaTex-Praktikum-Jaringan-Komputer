# Template LaTeX Laporan Praktikum Jaringan Komputer (IF25-21008)

Template LaTeX untuk laporan praktikum **Jaringan Komputer IF25-21008**, Program Studi Teknik Informatika, Institut Teknologi Sumatera (ITERA).

Template ini dibuat semirip mungkin dengan berkas resmi `Template Laporan Praktikum Jarkom IF25-21008 (2026).docx`. Tata letak, ukuran font, warna, dan posisi setiap elemen diukur langsung dari hasil render dokumen Word, lalu disamakan hingga selisihnya hanya beberapa piksel.

## Daftar Isi

- [Kontributor](#kontributor)
- [Cara Memakai](#cara-memakai)
- [Kompilasi](#kompilasi)
- [Font](#font)
- [Struktur Proyek](#struktur-proyek)
- [Catatan](#catatan)

## Kontributor

<table>
  <tr>
    <td align="center">
      <a href="https://github.com/hanungdata-prog">
        <img src="https://github.com/hanungdata-prog.png" width="90" alt="Hanung Akbar Pramusintho"><br>
        <b>Hanung Akbar Pramusintho</b>
      </a><br>
      <sub>Penggagas proyek</sub>
    </td>
    <td align="center">
      <a href="https://github.com/Jeremi16">
        <img src="https://github.com/Jeremi16.png" width="90" alt="Jeremi Pison Efrat Sianturi"><br>
        <b>Jeremi Pison Efrat Sianturi</b>
      </a><br>
      <sub>Pengembang lanjutan &amp; penyempurnaan tampilan</sub>
    </td>
  </tr>
</table>

- **Hanung Akbar Pramusintho** ([@hanungdata-prog](https://github.com/hanungdata-prog)) mencetuskan ide membuat versi LaTeX dari template laporan resmi.
- **Jeremi Pison Efrat Sianturi** ([@Jeremi16](https://github.com/Jeremi16)) melanjutkan pengembangannya dan menyempurnakan tampilan sampul, halaman judul, header, kotak rangkuman, hingga warna, sampai identik dengan template Word.

## Cara Memakai

Semua data laporan dipisah ke folder `data/`, jadi `main.tex` tidak perlu disentuh.

| Berkas | Yang diisi |
|---|---|
| `data/laporan.tex` | Nomor pertemuan, judul praktikum, bulan dan tahun |
| `data/identitas.tex` | Nama dan NIM peserta |
| `data/kelas.tex` | Kelas (RA–RH) |
| `data/asisten.tex` | Nama dua asisten praktikum |
| `data/anggota-kelompok.tex` | Daftar anggota kelompok dan catatan di bawahnya |

Isi laporan ditulis di folder `isi/`: rangkuman, langkah-langkah dokumentasi, alat dan bahan, tugas, serta referensi.

> **Tips:** daftar anggota tumbuh ke atas, sehingga alamat ITERA di halaman judul dalam tetap di posisinya berapa pun jumlah anggota. Untuk laporan individu, kosongkan `\daftaranggota` agar seluruh blok anggota tidak tampil, atau kosongkan `\catatananggota` saja untuk menyembunyikan catatannya.
>
> Judul panjang boleh dipecah dengan `\\` di `\judul`. Font sampul tetap konsisten di setiap baris, dan garis di halaman judul dalam ikut turun mengikuti baris terakhir.

## Kompilasi

Template ini wajib dikompilasi dengan **XeLaTeX** (misalnya lewat MiKTeX di Windows).

**Cara 1: manual.** Jalankan dua kali agar penomoran halaman dan referensi benar.

```bash
xelatex main.tex
xelatex main.tex
```

**Cara 2: sekali perintah dengan `latexmk`.**

```bash
latexmk -xelatex main.tex
```

**Cara 3: kompilasi otomatis setiap kali berkas disimpan.**

```bash
latexmk -xelatex -pvc main.tex
```

## Font

Template memakai font bawaan Windows, sama seperti dokumen Word aslinya:

- Garamond
- Arial dan Arial Black
- Bernard MT Condensed
- Cambria

Cek ketersediaan font di MiKTeX (PowerShell):

```powershell
miktex-fc-list | Select-String "Garamond|Arial Black|Bernard|Cambria"
```

> ⚠️ **Overleaf / Linux:** font di atas umumnya tidak tersedia. Pasang `EB Garamond` dan sesuaikan `\setmainfont` di `main.tex`.

### Ringkasan font dan ukuran

| Bagian | Font dan ukuran |
|---|---|
| Isi laporan | Garamond 12 pt, spasi 1,5 |
| Caption gambar dan tabel | Garamond 8 pt |
| Header | Arial Black 7 pt (kiri, berjarak huruf) dan 8 pt (kanan), garis ganda |
| Sampul | Cambria 14 pt, Garamond 12,3 / 18,5 / 14 pt, Bernard MT Condensed 24 pt, Arial Black 10 dan 52 pt |
| Halaman judul dalam | Arial Black 23,5 pt abu-abu `#959595`, anggota dan alamat Garamond 9,6 pt |
| Kotak rangkuman | Arial Bold Italic 12 dan 10 pt, isi Garamond 9,6 pt |
| Judul bagian | Garamond 20 pt Bold |
| Judul referensi | Arial Black 15 pt |

## Struktur Proyek

| Path | Isi |
|---|---|
| `main.tex` | Pengaturan halaman, font, warna, header/footer, sampul, dan halaman judul dalam |
| `data/` | Data laporan yang perlu diisi |
| `isi/` | Rangkuman, `dokumentasi/langkah-1..3`, alat dan bahan, tugas, referensi |
| `aset/gambar/` | Logo ITERA, FTI, dan Teknik Informatika, serta contoh gambar dokumentasi |

## Catatan

- Gambar dokumentasi memakai perintah `\gambarpengganti`. Jika berkas gambarnya belum ada, yang tampil adalah kotak bertuliskan "Gambar dokumentasi belum tersedia", sehingga kompilasi tidak gagal.
- Helper opsional: `\gbr{nama-file}{caption}` menyisipkan `aset/gambar/<nama-file>.png` beserta caption, dan `\topik{judul}` membuat subjudul tebal kecil di dalam langkah.
- Pada `isi/dokumentasi/langkah-2.tex` ada `\newpage` agar langkah kedua dimulai di halaman baru seperti di template Word. Hapus baris itu jika tidak diperlukan.

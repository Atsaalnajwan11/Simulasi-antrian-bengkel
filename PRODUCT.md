# Product: Simulasi Antrian Bengkel

Sistem simulasi antrian berbasis Discrete-Event Simulation (DES) untuk memodelkan operasional sebuah bengkel mobil dengan 1 resepsionis/kasir dan 2 montir paralel.

## Audience & Context
- **Mahasiswa:** Atsaal Najwan (NIM: 301240012).
- **Mata Kuliah:** Pemodelan dan Simulasi (Semester 5).
- **Tugas:** Tugas Akhir Modul 5 (TA-05) · Alur Logika Sistem Bengkel.
- **Dosen Pengampu:** Mohammad Bayu Anggara, S.Kom., M.Kom.
- **Pengguna:** Mahasiswa, dosen pengampu, dan asisten laboratorium yang menguji serta memvalidasi alur antrian diskrit.

## Platform & Stack
- **Platform:** Web (`Simulasi Antrian Bengkel.html`) & Jupyter Notebook Python (`simulasi_bengkel.ipynb`).
- **Implementasi Web:** Single-file static HTML, CSS modern (CSS variables, flexbox, grid, SVG), dan JavaScript native (tanpa dependensi eksternal).
- **Implementasi Python:** Python 3 dengan NumPy untuk simulasi diskrit terminal/notebook.

## System & Mechanics
1. **Entitas & Kapasitas:**
   - 1 Orang Resepsionis (merangkap tugas pendaftaran awal dan kasir pembayaran).
   - 2 Montir / Bay Servis paralel (Montir 1 dan Montir 2).
   - 3 Titik Antrean: Antrean pendaftaran masuk, ruang tunggu montir (buffer tak terbatas), dan antrean kasir.
2. **Distribusi Probabilitas:**
   - Waktu antar-kedatangan kendaraan: Distribusi Eksponensial (`mean = 15` menit).
   - Waktu layanan registrasi resepsionis: Distribusi Eksponensial (`mean = 2` menit).
   - Waktu pengerjaan perbaikan montir: Distribusi Normal (`mean = 25` menit, `sd = 5` menit, minimal 5 menit).
   - Waktu transaksi kasir: Distribusi Eksponensial (`mean = 3` menit).
3. **Aturan Prioritas:**
   - Resepsionis memprioritaskan pelanggan yang hendak membayar di kasir dibanding pelanggan baru yang mendaftar.
   - Disiplin antrian FIFO (First In, First Out).
4. **Metrik Kinerja Utama (KPI):**
   - Total mobil selesai dilayani.
   - Rata-rata waktu tunggu montir.
   - Waktu tunggu montir maksimum.
   - Rata-rata total waktu di bengkel (*sojourn time*).
   - Utilisasi kapasitas montir (% sibuk).


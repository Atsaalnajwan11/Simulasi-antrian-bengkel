---
name: "Simulasi Antrian Bengkel"
description: "Sistem desain antarmuka konsol telemetri dan simulasi kejadian diskrit (DES) bengkel servis kendaraan."
colors:
  bg: "#f5f7fc"
  bg-dark: "#070c18"
  surface: "#ffffff"
  surface-dark: "#0f172a"
  surface-sunken: "#edf1f8"
  surface-sunken-dark: "#0a1122"
  line: "#d8e0ee"
  line-dark: "#1e293b"
  ink: "#0f172a"
  ink-dark: "#f1f5f9"
  ink-muted: "#475569"
  ink-muted-dark: "#94a3b8"
  blue: "#1d4ed8"
  blue-soft: "#eff6ff"
  blue-ink: "#1e3a8a"
  amber: "#d97706"
  amber-soft: "#fffbeb"
  amber-ink: "#92400e"
  green: "#059669"
  green-soft: "#ecfdf5"
  green-ink: "#065f46"
  hero-bg: "#09132b"
  hero-ink: "#f8fafc"
  hero-amber: "#fbbf24"
typography:
  display:
    fontFamily: "'Bricolage Grotesque', system-ui, sans-serif"
    fontWeight: 700
    lineHeight: 1.15
  body:
    fontFamily: "'IBM Plex Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif"
    fontWeight: 400
    fontSize: "15.5px"
    lineHeight: 1.65
  mono:
    fontFamily: "'IBM Plex Mono', ui-monospace, Menlo, Consolas, monospace"
    fontWeight: 500
rounded:
  sm: "6px"
  md: "10px"
  lg: "14px"
  pill: "999px"
spacing:
  xs: "6px"
  sm: "10px"
  md: "16px"
  lg: "24px"
  xl: "32px"
components:
  button-primary:
    backgroundColor: "{colors.blue}"
    textColor: "#ffffff"
    rounded: "{rounded.sm}"
  badge-car:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.blue-ink}"
    rounded: "{rounded.sm}"
---

# Sistem Desain: Simulasi Antrian Bengkel

Dokumen ini mendokumentasikan sistem visual, token desain, dan pedoman antarmuka untuk aplikasi simulasi antrian bengkel interaktif berbasis Discrete-Event Simulation (DES).

---

## 1. Identitas Visual & Filosofi
* **Karakter:** Konsol operasional teknis presisi tinggi, terinspirasi oleh papan telemetri otomotif (*automotive workshop telemetry*) yang bersih, fungsional, dan mudah dipindai (*high scanability*).
* **Mode Permukaan (*Surface Mode*):** *Operate + Experience*. Antarmuka dirancang untuk mempermudah pemahaman logika antrian teoritis melalui representasi visual dinamis yang hidup.

---

## 2. Palet Warna & Semantik
Sistem warna menggunakan peran semantis yang stabil di mode terang maupun mode gelap:
* **Blueprint Blue (`#1d4ed8` / `#3b82f6`):** Dipakai untuk entitas resepsionis, event pendaftaran (`ARRIVAL`, `REG_END`), dan kontrol primer.
* **Automotive Amber (`#d97706` / `#f59e0b`):** Melambangkan proses pengerjaan (*work-in-progress*), ruang tunggu buffer, pengerjaan servis montir, dan kendaraan yang sedang aktif diproses.
* **Mechanical Green (`#059669` / `#10b981`):** Menandakan bay atau meja dalam status bebas (*standby/free*), transaksi pembayaran tuntas (`PAY_END`), dan penyelesaian kendaraan.
* **Hero Midnight Navy (`#09132b` / `#030712`):** Latar kontras tinggi untuk bilah telemetri jam simulasi dan header utama.

---

## 3. Tipografi
1. **Display Headings (`Bricolage Grotesque`):** Digunakan untuk judul hero, judul bagian (*h2*), dan angka jam telemetri. Memiliki proporsi modern dengan pembobotan tegas.
2. **Body Text (`IBM Plex Sans`):** Digunakan untuk penjelasan alur, deskripsi sistem, tabel, dan label formulir. Karakter huruf dirancang untuk keterbacaan tinggi pada layar peramban.
3. **Data & Monospace (`IBM Plex Mono`):** Wajib untuk semua angka metrik, log jam simulasi, nomor kendaraan (`#1`, `#2`), kode variabel, dan counter. Dilengkapi atribut `font-variant-numeric: tabular-nums` agar tata letak tidak bergetar saat angka berganti.

---

## 4. Hirarki & Tata Letak
* **Tanpa Eyebrow Mengambang:** Sesuai panduan *Craft Floor* Impeccable, judul tidak didahului kicker/eyebrow terpisah. Struktur bab menggunakan penomoran terpadu (`Tahap 01`, `Tahap 02`, dst.).
* **Batas Lebar Teks (*Reading Measure*):** Paragraf dibatasi pada rentang 60–70 karakter (`max-width: 70ch`) untuk kenyamanan mata.
* **Pemisahan Kelompok:** Lantai kerja bengkel dibagi jelas menjadi 3 zona:
  1. *Resepsionis & Kasir* (1 operator melayani daftar & bayar)
  2. *Ruang Tunggu* (buffer antrean montir)
  3. *Pit Montir* (2 bay paralel stasiun A & B)

---

## 5. Sistem Gerak & Animasi (*Motion & Micro-Interactions*)
* **Jalur Alur Kerja Animatif:** Step node pada workflow track (`Kedatangan ➔ Pendaftaran ➔ Ruang Tunggu ➔ Pit Montir ➔ Kasir ➔ Selesai`) berdenyut (*pulse glow*) sesuai tahapan kejadian aktif.
* **Token Kendaraan:** Mobil baru masuk dengan animasi luncur (*slide-in*), sedangkan mobil aktif diproses disorot dengan cincin pendar (*pulsing amber glow*).
* **Aktivitas Montir:** Bay yang aktif memunculkan animasi kunci pas berputar halus (`@keyframes wrenchWork`) serta bilah proses perbaikan belang-belang bergerak (*shimmering progress bar*).
* **Milestone Pop:** Counter mobil selesai melompat membesar sesaat (*pop animation*) ketika mobil berhasil keluar dari bengkel.
* **Aksesibilitas Gerak:** Seluruh animasi menghormati preferensi peramban `prefers-reduced-motion: reduce`.


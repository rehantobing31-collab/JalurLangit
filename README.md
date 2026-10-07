# BOLAPELANGI2 Data Checker

Extension Chrome (Manifest V3) untuk cek data member BOLAPELANGI2:
**DP · SCB A–E · WD · Last DP · Total DP tanggal terakhir · Status WIN/LOSE.**

Ringan, cepat, tanpa dependency. Semua parsing jalan lokal di browser — **tidak ada data yang dikirim ke server**.

---

## ✨ Fitur

| Modul | Status | Keterangan |
|---|---|---|
| **Data Checker** | ✅ aktif | Parser DP, SCB A–E, WD, hitung status member |
| Bonus Calculator | ○ soon | Kalkulasi bonus otomatis |
| Report Harian | ○ soon | Rekap & export harian |
| Member Lookup | ○ soon | Riwayat member by USER ID |

---

## 🧠 Logika Paten v7

1. **DP biasa** = semua transaksi Deposit History yang **bukan** SCB.
2. **SCB A–E** = bonus (tetap ikut dihitung di TOTAL DP tanggal terakhir).
3. **LAST DP** = transaksi DP biasa paling akhir berdasarkan tanggal/waktu.
4. **TOTAL DP** = jumlah **semua** nominal DP + SCB pada **TANGGAL TERAKHIR** member melakukan deposit.
   - Contoh: 06/10 → DP 150.000 + SCB A 15.000 = **TOTAL DP 165.000**.
5. **Bagian atas hasil:**
   - `WD` = Withdraw Amount transaksi WD paling baru, **tanpa ×1000**.
   - `SISA DANA AKUN` = New Balance transaksi WD paling baru, **tanpa ×1000**.
6. **STATUS MEMBER:**
   - `DP` = total semua DP biasa.
   - `WD` = total semua Withdraw Amount **×1000**.
   - `BONUS` = total semua SCB A+B+C+D+E.
   - `DP-WD-BNS` = DP − WD − BONUS.
   - Positif → **WIN**, negatif → **LOSE**, nol → **BALANCE**.

---

## 📁 Struktur File

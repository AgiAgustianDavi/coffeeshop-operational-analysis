# Log Cleaning - Aroma Jaya POS

- File mentah: `dataset_pos_aromajaya.csv` (42.643 baris)
- File bersih: `cleaned_data.csv` (42.583 baris)
- Periode data: 2026-01-01 s.d. 2026-06-29

## Langkah dan jumlah baris

| Langkah | Aturan | Sebelum | Dibuang | Sesudah |
|---|---|---:|---:|---:|
| 1 | Buang duplikat penuh (semua kolom sama) | 42.643 | 35 | 42.608 |
| 2a | Buang quantity <= 0 (nilai -2) | 42.608 | 10 | 42.598 |
| 2b | Buang quantity 99 (salah input) | 42.598 | 15 | 42.583 |

**Total dibuang: 60 baris (0,14% dari data mentah).**

## Penyeragaman teks (tidak ada baris dibuang)

- `store_location`: 6 variasi penulisan menjadi 3 nama baku (Sudirman (Office), Senopati (Hangout), Gading Serpong (Residential)).
- `tipe_order`: 4 variasi penulisan menjadi 2 nilai baku (Dine-in, Takeaway).
- Baris `store_location` kosong diisi "Unknown": 7
- Baris `tipe_order` kosong diisi "Unknown": 6
- Duplikat baru setelah teks diseragamkan: 0

## Kolom baru

`hour`, `day_num` (1 = Senin ... 7 = Minggu), `day_name`, `month` (YYYY-MM), `revenue` (quantity x unit_price).

## Keterbatasan data

- 831 dari 29.987 transaksi tercatat di lebih dari satu cabang. Baris dibiarkan apa adanya (keputusan analis). Konsekuensinya: omzet, item, dan produk per cabang dihitung per baris; jumlah transaksi dan nilai struk dihitung di level seluruh jaringan (ID transaksi unik), bukan per cabang.
- Data berakhir 29 Juni 2026 (30 Juni tidak ada), jadi Juni hanya 29 hari.
- Data tidak memuat jumlah staf, stok, atau antrean.

# Findings on SQL Queries and HTTP Calls

## SQL Queries

### File: `/cron/telegram/run.php`
- `SELECT waktu_transaksi FROM tbl_transaksi_{time_postfix} ORDER BY waktu_transaksi DESC LIMIT 1`
- `SELECT * FROM z_setting WHERE key = 'cron_teleg'`

## HTTP Calls

### File: `/cron/telegram/run.php`
- `https://api.telegram.org/bot{TOKEN}/sendMessage`

# Findings on SQL Queries and HTTP Calls

## SQL Queries

### File: `/cron/cron_akta_summary.php`
- `SELECT MAX(tanggal) AS the_last FROM tbl_akta_summary`
- `SHOW TABLES LIKE '{$table}'`
- `SELECT DATE(waktu_transaksi) AS tanggal, ... FROM {$table} a ... GROUP BY kd_notaris, DATE(waktu_transaksi)`
- `INSERT INTO tbl_akta_summary(...) VALUES(...) ON DUPLICATE KEY UPDATE ...`

### File: `/cron/cron_check_expired_obyek.php`
- `SELECT value FROM z_setting WHERE key = 'cron_check_obyek_expired_date' LIMIT 1`
- `SELECT jenis_obyek, no_transaksi FROM $table WHERE flag_check_obyek = 0 AND jenis_transaksi = 1 ...`
- `DELETE FROM ... WHERE ...`
- `INSERT INTO tbl_log_delete_obyek (...) VALUES (...)`
- `UPDATE tbl_transaksi SET flag_check_obyek = 1 WHERE no_transaksi = ...`

### File: `/cron/cron_cuti.php`
- `SELECT id, id_staff, tgl_awal, status FROM tbl_cuti_staff WHERE tgl_awal <= '$now' ...`
- `SELECT id, id_staff from tbl_cuti_staff where tgl_akhir <= '$now' ...`
- `UPDATE tbl_verifikator_flag set status_cuti=$data->status where id_user=$data->id_staff`
- `INSERT INTO {$tbl_report}_{$year} ...`
- `UPDATE tbl_cuti_staff set aktif=1 where id='$data->id'`

### File: `/cron/cron_generate_report.php`
- `SELECT value FROM z_setting WHERE key = 'cronreport' LIMIT 1`
- `SELECT id, expired, parameter FROM tbl_cron_report_queue WHERE status = 0 ...`
- `SELECT b.nama_pemberi, ... FROM tbl_transaksi a ...`
- `UPDATE z_setting SET value = '0' WHERE key = 'cronreport'`

### File: `/cron/cron_notifikasi_hak_akses.php`
- `SELECT reg.id_reg, reg.username, reg.expire_date, u.id, u.akses FROM tbl_registrasi reg JOIN tbl_user u ...`
- `UPDATE tbl_registrasi SET reminder_date= '$reminderDate' WHERE id_reg=$data->id_reg`

### File: `/cron/cron_stuck_perbaikan.php`
- `SELECT verifikator, no_sertifikat, id, no_transaksi, periksa_date FROM tbl_transaksi_perbaikan_...`
- `UPDATE tbl_transaksi_perbaikan_... set status=3 where no_transaksi=$data->no_transaksi`
- `SELECT parentID from tbl_kasie where user_id='$data->verifikator'`

## HTTP Calls
- No HTTP calls were found in the provided scripts.

# Findings Report

## SQL Queries

1. **File: `/app/_voucher_list.php`**
   - No SQL queries found.

2. **File: `/app/act_log.php`**
   - `SELECT a.no_transaksi, a.no_sertifikat, a.nm_penerima, a.nm_pemberi, a.waktu_transaksi, c.nama, a.jenis_transaksi FROM zz_manual_transaksi AS a LEFT JOIN tbl_user c ON a.kd_notaris = c.id WHERE DATE(a.waktu_transaksi) BETWEEN "start" AND "end"`
   - `SELECT a.no_transaksi, a.no_sertifikat, a.nm_penerima, a.nm_pemberi, a.waktu_transaksi, c.nama, a.jenis_transaksi FROM zz_manual_transaksi AS a LEFT JOIN tbl_user c ON a.kd_notaris = c.id WHERE a.kd_notaris = "condition"`

3. **File: `/app/act_ojk_setting.php`**
   - `DELETE FROM tbl_ojk_new WHERE id = {$id}`
   - `SELECT *, kabupaten/kota as kabupaten_kota FROM tbl_ojk_new WHERE id = {$id}`

4. **File: `/app/act_mmenu.php`**
   - `SELECT id, nama FROM tbl_user WHERE nama LIKE '%{$name}%' AND blokir = 'N'`
   - `INSERT INTO tbl_menu (judul, parent_id, url, akses, spesifik_user, deskripsi) VALUES (...)`
   - `UPDATE tbl_menu SET judul = '{$judul}', parent_id = '{$parent_id}', url = '{$url}', akses = '{$groups}', spesifik_user = '{$users}', deskripsi = '{$deskripsi}' WHERE id = '{$id}'`

5. **File: `/app/act_perpanjangan.php`**
   - `SELECT id_reg, expire_date FROM AHU_FIDUSIA.tbl_registrasi WHERE username='$npost[user]' AND email='$npost[email]'`
   - `UPDATE AHU_FIDUSIA.tbl_registrasi SET created_date='$new_date', expire_date='$new_expire' WHERE username='$username'`

6. **File: `/app/act_role.php`**
   - `SELECT * FROM tbl_modul WHERE id = ". $post['_id']`
   - `UPDATE tbl_modul SET flag = '0', deleted_at = '" . date('YmdHis') . "' WHERE id = ". $post['_id']`
   - `INSERT INTO tbl_modul(...) VALUES (...)`

7. **File: `/app/add_act.php`**
   - `INSERT INTO tbl_nomor_transaksi(...) VALUES (...)`
   - `UPDATE tbl_transaksi SET ... WHERE no_transaksi = '$no_pendaftaran'`

8. **File: `/app/add_act_payment.php`**
   - `UPDATE tbl_transaksi set kode_pembayaran = '{$simpadhu->KODE_PEMBAYARAN}', expired_voucher='{$ex}' where no_transaksi = '$noTransaksi'`

9. **File: `/app/add_act_payment_voc_mandiri.php`**
   - `UPDATE tbl_transaksi set kode_pembayaran = '{$paymentCode}' where no_transaksi = '$noTransaksi'`

10. **File: `/app/add_act_peraturan.php`**
    - `INSERT into tbl_peraturan (title, url, created_date, created_by, status) values (...)`

## HTTP Calls

1. **File: `/app/_voucher_list.php`**
   - `CurlKta::getListVoucher($params)`

2. **File: `/app/act_log.php`**
   - No HTTP calls found.

3. **File: `/app/act_ojk_setting.php`**
   - No HTTP calls found.

4. **File: `/app/act_mmenu.php`**
   - No HTTP calls found.

5. **File: `/app/act_perpanjangan.php`**
   - `curl_simpadhu(...)`

6. **File: `/app/add_act.php`**
   - `curl_simpadhu(...)`

7. **File: `/app/add_act_payment.php`**
   - `curl_simpadhu(...)`

8. **File: `/app/add_act_payment_voc_mandiri.php`**
   - No HTTP calls found.

9. **File: `/app/add_act_peraturan.php`**
   - No HTTP calls found.

10. **File: `/app/add_act_perU.php`**
    - No HTTP calls found.

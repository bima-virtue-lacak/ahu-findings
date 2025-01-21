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

11. **File: `/app/add_act_perbaikan.php`**
    - `SELECT jenis_transaksi FROM tbl_transaksi WHERE no_transaksi = '$no_transaksi'`
    - `INSERT INTO tbl_transaksi_psc_perbaikan (...)`
    - `UPDATE tbl_transaksi SET ...`
    - `INSERT INTO tbl_pemberi_fidusia_{$pf} (...)`
    - `INSERT INTO tbl_penerima_fidusia_{$pf} (...)`

12. **File: `/app/add_act_perbaikanU.php`**
    - `SELECT c.*, b.*, a.* FROM tbl_transaksi AS a ...`
    - `INSERT INTO tbl_transaksi (...)`
    - `UPDATE tbl_transaksi SET ...`
    - `INSERT INTO tbl_pemberi_fidusia (...)`
    - `INSERT INTO tbl_penerima_fidusia (...)`

13. **File: `/app/add_act_perU.php`**
    - `INSERT INTO tbl_transaksi (...)`
    - `INSERT INTO tbl_pemberi_fidusia (...)`
    - `INSERT INTO tbl_penerima_fidusia (...)`

14. **File: `/app/add_act_perU_manual.php`**
    - `INSERT INTO zz_manual_transaksi (...)`
    - `INSERT INTO zz_manual_pemberi_fidusia (...)`
    - `INSERT INTO zz_manual_penerima_fidusia (...)`

15. **File: `/app/add_act_roya.php`**
    - `INSERT INTO tbl_transaksi (...)`
    - `INSERT INTO tbl_sertifikat_lama (...)`

16. **File: `/app/add_act_roya_edit.php`**
    - `UPDATE tbl_transaksi SET ...`
    - `UPDATE zz_manual_pemberi_fidusia SET ...`
    - `UPDATE zz_manual_penerima_fidusia SET ...`

17. **File: `/app/assign_cuti.php`**
    - `INSERT INTO tbl_cuti_staff (...)`
    - `UPDATE tbl_verifikator_flag SET ...`

18. **File: `/app/assign_to_verifikator.php`**
    - `UPDATE tbl_transaksi_perbaikan SET ...`
    - `UPDATE tbl_history_perbaikan_{$year} SET ...`

19. **File: `/app/bill_act.php`**
    - `SELECT b.tempat_obyek, date(b.waktu_transaksi) as waktu_transaksi, b.jenis_transaksi, jumlah_billing, a.no_invoice_payment as no_invoice, a.tgl_pembayaran, b.no_sertifikat, b.ket_syarat, a.flag_pembayaran FROM tbl_billing as a, tbl_transaksi as b WHERE a.no_transaksi='$id' AND a.no_transaksi=b.no_transaksi`
    - `UPDATE tbl_billing SET flag_pembayaran=NULL, no_invoice_payment=NULL, tgl_pembayaran=NULL WHERE no_transaksi='$id'`
    - `UPDATE tbl_transaksi SET flag_cetak=null, flag_proses=NULL, no_sertifikat=NULL WHERE no_transaksi='$id'`

20. **File: `/app/bill_show.php`**
    - `SELECT a.no_transaksi, a.nm_notaris, d.tgl_pembayaran as tanggal, d.flag_pembayaran as flag, b.nama_provinsi FROM tbl_transaksi_pregen as a, tbl_provinsi as b, tbl_billing as d WHERE a.no_transaksi='$id' AND a.no_transaksi=d.no_transaksi AND a.kedudukan=b.id`

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

10. **File: `/app/beli_voucher.php`**
    - `CurlKta::getUrlNotariat()`
    - `CurlKta::tambahVoucher($post)`

11. **File: `/app/assign_cuti.php`**
    - `CurlKta::isNotaris()`
    - `CurlKta::getId()`
    - `CurlKta::getRekening()`
    - `CurlKta::getEmail()`

12. **File: `/app/assign_durasi.php`**
    - No HTTP calls found.

13. **File: `/app/assign_to_verifikator.php`**
    - No HTTP calls found.

14. **File: `/app/bill_act.php`**
    - `curl_simpadhu(...)`

15. **File: `/app/cabang.php`**
    - `$.post('app/load_merk.php', {data_type: sel, tbl: tbl, id:id}, function(data){...});`

16. **File: `/app/cari.php`**
    - `$.ajax({url:'no_login/pencarian.php', type:'POST', data: {id:id,tipe:tipe}, success : function(data){...}});`

17. **File: `/app/cetak_history_daftar.php`**
    - `$.ajax({url: get_url_cari($('#tipe').val()), type:'POST', data: $(a).serialize(), success : function(data){...}});`

18. **File: `/app/cetak_laporan_transaksi.php`**
    - `$.post("app/cari2_next.php", {lastID:$("#product-table tr:last").attr("id"), ygdicari: $("#txt_no").val(), cari: $("#txt_cari").val(), time:$('#product-table tr:last td:nth-child(16)').text(), his:<?=0+(isset($_GET['history']) and $_GET['history'] == 1)?>, lastTs:$('#_last_timestamp').val(), jenfid: jf}, prosesData,'json');`

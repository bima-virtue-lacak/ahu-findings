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

21. **File: `/app/bridge_service.php`**
   - `SELECT * FROM ...` (various queries related to cURL responses)
   - `SELECT id, nama FROM tbl_user WHERE username = '{$username}'`
   - `SELECT * FROM tbl_provinsi ORDER BY nama_provinsi`
   - `INSERT INTO AHU_FIDUSIA.tbl_registrasi (...) VALUES (...)`
   - `UPDATE tbl_faq SET ... WHERE id=$id`

22. **File: `/app/bukti_bayar.php`**
   - `SELECT * FROM tbl_registrasi WHERE kode_pembayaran = '{$kode_pembayaran}'`

23. **File: `/app/cabang_act.php`**
   - `SELECT id, nama FROM tbl_user WHERE username = '{$username}'`
   - `INSERT INTO AHU_FIDUSIA.tbl_registrasi (...) VALUES (...)`
   - `SELECT * FROM tbl_user WHERE username = '{$username}'`

24. **File: `/app/cari.php`**
   - `SELECT * FROM tbl_transaksi WHERE ...`

25. **File: `/app/cari2.php`**
   - `SELECT * FROM tbl_transaksi WHERE ...`

26. **File: `/app/cari2_export.php`**
   - `SELECT * FROM tbl_transaksi WHERE ...`

27. **File: `/app/cekdataakhir.php`**
   - `SELECT no_sertifikat_ori FROM tbl_sertifikat_lama WHERE no_transaksi='{$ntr}'`
   - `SELECT no_transaksi FROM tbl_sertifikat_lama WHERE no_sertifikat_ori ='{$val}'`

28. **File: `/app/cekdataakhir_manual.php`**
   - `SELECT no_transaksi FROM zz_manual_sertifikat_lama WHERE no_sertifikat_ori ='{$val}'`

29. **File: `/app/cetak_daftar.php`**
   - `SELECT * FROM tbl_transaksi WHERE ...`

30. **File: `/app/cetak_history_daftar.php`**
    - `SELECT * FROM tbl_transaksi WHERE ...`

31. **`File: /app/cleansing.php`**
    - `SELECT id_reg FROM AHU_FIDUSIA.tbl_registrasi where username='$user'`
    - `SELECT b.id FROM AHU_FIDUSIA.tbl_registrasi a LEFT JOIN AHU_FIDUSIA.tbl_user b ON b.username=a.username WHERE parent='$fetch->id_reg'`
    - `SELECT c.nama_provinsi AS provinsi_notariat, a.nama, d.nama_provinsi AS provinsi_fidusia FROM tbl_data_notaris AS a INNER JOIN tbl_user b ON a.username = b.username inner JOIN tbl_provinsi c ON a.id_prov = wilayah_id_notaris inner JOIN tbl_provinsi d ON b.wilayah = d.kode_provinsi WHERE c.nama_provinsi != d.nama_provinsi LIMIT $os,$dp`

32. **`File: /app/cleansing_detail.php`**
    - `SELECT tanggal, sum(total_akta) as total_akta, bulan, tahun, provinsi, kode FROM AHU_FIDUSIA.tbl_akta_summary WHERE kode = '$id' AND bulan = '$month' AND tahun = '$year' AND total_akta >= 1000`
    - `SELECT SUM(total_akta) as total_akta, bulan, tahun FROM tbl_akta_summary WHERE kode = '$id' AND total_akta >= 1000 GROUP BY bulan, tahun ORDER BY tahun, bulan ASC`

33. **`File: /app/cleansing_edit.php`**
    - `SELECT a.no_akta, a.tgl_akta, a.kode_pembayaran, a.no_transaksi, a.jenis_transaksi, a.nm_pemberi, a.nm_penerima, a.nm_notaris, a.waktu_transaksi, b.nama_provinsi, a.jenis_obyek, a.no_sertifikat, d.npwp_ktp_pemberi, e.npwp_ktp_penerima from tbl_transaksi as a left join tbl_pemberi_fidusia d on a.no_transaksi = d.no_transaksi left join tbl_penerima_fidusia e on a.no_transaksi = e.no_transaksi, tbl_provinsi as b where a.no_transaksi = '$id'`

35. **`File: /app/curl-mandiri.php`**
    - `SELECT value FROM z_setting WHERE key = 'mandiri'`

35. **`File: /app/curl-simpadhu.php`**
    - `SELECT value FROM z_setting WHERE key = 'simpadhu-u'`

36. **File: `/app/dashboard.php`**
   - Line 17: `SELECT * FROM tbl_user WHERE id=$userId`
   - Line 62: `SELECT DATE(a.waktu_transaksi) as tanggal, ... FROM tbl_transaksi a LEFT JOIN tbl_user b on a.kd_umum = b.id WHERE $cond DATE(a.waktu_transaksi) BETWEEN '$start_date' AND '$end_date' GROUP BY DATE(a.waktu_transaksi)`
   - Line 79: `SHOW TABLES LIKE 'tbl_transaksi_pencarian_".$tahun."';`
   - Line 83: `SELECT DATE(created_date) AS TANGGAL, COUNT(*) AS total, COUNT(*)*50000 AS jumlah FROM {$tabel} WHERE created_date BETWEEN DATE('{$start_date}') AND DATE('{$end_date}') GROUP BY DATE(created_date)`

37. **File: `/app/dashboard_pencarian_func.php`**
   - Line 40: `SELECT SUM(JUMLAH_BILLING) AS jumlah, SUM(TOTAL) AS total, TIPE_TRANSAKSI AS ID_PRODUK FROM summary WHERE TANGGAL BETWEEN '{$dari}' AND '{$sampai}' AND TIPE_TRANSAKSI IN(" .implode(",", $tipe_transaksi). ") GROUP BY TIPE_TRANSAKSI`

38. **File: `/app/dashboard_perbaikan.php`**
   - Line 36: `SELECT * FROM tbl_transaksi WHERE no_transaksi='".$id."'`

39. **File: `/app/dashboard_user.php`**
   - Line 45: `SHOW TABLES LIKE 'tbl_transaksi_pencarian_".$tahun."';`

40. **File: `/app/detail.php`**
   - Line 10: `SELECT tgl_pembayaran FROM tbl_transaksi WHERE no_transaksi='".$id."'`
   - Line 15: `SELECT a.tempat_obyek, a.tgl_jangka_waktu, ... FROM tbl_transaksi_all_v as a, tbl_provinsi as b WHERE a.kedudukan=b.id and a.no_transaksi='$id'`

41. **File: `/app/download_cleansing.php`**
   - Line 27: `SELECT t.TABLE_NAME AS stud_tables FROM INFORMATION_SCHEMA.TABLES AS t WHERE TABLE_SCHEMA = "AHU_BILLING_SIMPADHU" AND t.TABLE_NAME LIKE "billing_2_______"`

42. **File: `/app/form_cetak.php`**
   - Line 8: `SELECT * FROM tbl_transaksi WHERE no_transaksi='$id'`

43. **File: `/app/form_cetak_lampiran.php`**
   - Line 10: `SELECT a.*, b.nama_provinsi as wilayah FROM tbl_transaksi_all_v as a, tbl_provinsi as b  WHERE  a.kedudukan=b.id and a.no_transaksi='$id'`



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

19. **File: `/app/bridge_service.php`**
   - `curl_init()`
   - `curl_setopt($ch, CURLOPT_URL, $url)`
   - `curl_exec($ch)`

20. **File: `/app/bukti_bayar.php`**
   - `$curl->curl_billing_autodebit($db, $kode_pembayaran, HelperKta::getRekening())`

21. **File: `/app/cabang.php`**
   - `$.post('app/load_merk.php', ...)`
   - `$.ajax({ url:'app/cabang_act.php', type:'POST', data: abb, ... })`

22. **File: `/app/cari.php`**
   - `$.ajax({ url:'no_login/pencarian.php', type:'POST', data: {id:id,tipe:tipe}, ... })`

23. **File: `/app/cari2.php`**
   - `$.post("app/cari2_next.php", ...)`

24. **File: `/app/cari2_next.php`**
   - `curl_simpadhu($db, $no_pendaftaran, $waktu, 10, $id_jaminan_fidusia)`

25. **File: `/app/cetak_list_perbaikan.php`**
   - `curl_get_tarif_pendaftaran($db, $params)`

36. **`File: /app/cleansing.php`**
    - `$.post("app/nextPageCleansing.php", {...})`
    - `$.post("app/load_cari.php", {...})`
    - `$.post("app/cleansing_edit.php", {...})`
    - `$.post("app/cleansing_detail.php", {...})`

37. **`File: /app/curl-mandiri.php`**
    - `curlJwtMandiri()`
    - `curlRedirectMandiri($billKey)`

38. **`File: /app/curl-simpadhu.php`**
    - `curl_billing(&$db, $kode)`
    - `curl_simpadhu(&$db, $no_transaksi, $tgl_transaksi, $tipe_transaksi, $id_mapping, $exp = NULL, $kodeBank = NULL, $showError = false)`
   
39. **File: `/app/dashboard_perbaikan.php`**
   - Line 61: `$.ajax({ url:'app/get_perbaikan_report.php', type:'POST', ...`

40. **File: `/app/dashboard_user.php`**
   - Line 60: `$.ajax({ url:'app/get_user_report.php', type:'POST', ...`

41. **File: `/app/download_cleansing.php`**
   - Line 54: `curl_simpadhu($db, $id, $waktu, $tipe_transaksi, $id_mapping, $expired)`

42. **File: `/app/form_cetak.php`**
   - Line 30: `curl_simpadhu($db, $id, $waktu, $tipe_transaksi, $id_mapping, $expired)`

43. **File: `/app/form_cetak_log.php`**
   - Line 15: `curl_simpadhu($db, $id, $waktu, $tipe_transaksi, $id_mapping, $expired)`

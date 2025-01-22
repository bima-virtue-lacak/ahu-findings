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

44. **File: '/app/form_cetak_log.php'**
   - Query: `SELECT a.*, b.nama_provinsi as wilayah, pemberi.* FROM tbl_transaksi_all_v as a, tbl_provinsi as b, tbl_pemberi_fidusia pemberi WHERE pemberi.no_transaksi = a.no_transaksi and a.no_transaksi='$id'`
   - Query: `SELECT a.*, pemberi.* FROM tbl_transaksi_all_v as a, tbl_pemberi_fidusia pemberi WHERE pemberi.no_transaksi = a.no_transaksi and a.no_transaksi='$id'`
   - Query: `SELECT * FROM tbl_pemberi_fidusia as a WHERE a.no_transaksi='$id'`

45. **File: '/app/form_cetak_log_xl.php'**
   - Query: `SELECT * FROM tbl_pemberi_fidusia as a WHERE a.no_transaksi='$id'`

46. **File: '/app/form_cetak_manual.php'**
   - Query: `SELECT a.*, b.nama_provinsi as wilayah, pemberi.* FROM tbl_transaksi_all_v as a, tbl_provinsi as b, tbl_pemberi_fidusia pemberi WHERE pemberi.no_transaksi = a.no_transaksi and a.no_transaksi='$id'`
   - Query: `SELECT * FROM tbl_pemberi_fidusia as a WHERE a.no_transaksi='$id'`

47. **File: '/app/form_cetak_pernyataan.php'**
   - Query: `SELECT a.*, b.nama_provinsi as wilayah, pemberi.* FROM tbl_transaksi_all_v as a, tbl_provinsi as b, tbl_pemberi_fidusia pemberi WHERE pemberi.no_transaksi = a.no_transaksi and a.no_transaksi='$id'`
   - Query: `SELECT * FROM tbl_pemberi_fidusia as a WHERE a.no_transaksi='$id'`

48. **File: '/app/form_cetak_sertifikat.php'**
   - Query: `SELECT a.*, b.nama_provinsi as wilayah FROM tbl_transaksi_all_v as a, tbl_provinsi as b WHERE a.tempat_obyek=b.kode_provinsi and a.no_transaksi='$id'`
   - Query: `SELECT * FROM tbl_pemberi_fidusia WHERE no_transaksi='$id'`

49. **File: '/app/form_cetak_sertifikat_perubahan.php'**
   - Query: `SELECT a.*, b.nama_provinsi as wilayah FROM tbl_transaksi_all_v as a, tbl_provinsi as b WHERE a.tempat_obyek=b.kode_provinsi and a.no_transaksi='$id'`
   - Query: `SELECT * FROM tbl_pemberi_fidusia WHERE no_transaksi='$id'`

50. **File: `/app/form_cetak_sertifikat_roya.php`**
    - `SELECT a.options, a.flag_dollar, a.tempat_obyek, ... FROM tbl_transaksi_all_v as a, tbl_provinsi as b, tbl_transaksi_roya c WHERE a.tempat_obyek=b.kode_provinsi and a.no_transaksi=c.no_transaksi_baru and $where`
    - `UPDATE tbl_transaksi a SET flag_cetak=1, tgl_cetak=now(), id_cetak='$user' WHERE $where`
    - `SELECT ... FROM tbl_transaksi WHERE no_transaksi='$id'`
    - `SELECT ... FROM tbl_nama_penerima WHERE no_transaksi='$line->no_transaksi'`
    - `SELECT ... FROM tbl_kurs WHERE no_transaksi='$line->no_transaksi' AND jaminan_fidusia_dollar='0.00'
    - `SELECT ... FROM tbl_transaksi WHERE no_transaksi='$line->no_transaksi_lama'`

51. **File: `/app/form_cetak_sertifikat_roya_pdf.php`**
    - `SELECT a.type, a.tgl_transaksi_roya FROM tbl_transaksi_roya_$suffixTable a WHERE a.no_transaksi_baru='$id'`
    - `SELECT ... FROM z_setting WHERE key='live_date_format_sk_penghapusan_2024'`
    - `SELECT ... FROM tbl_transaksi WHERE no_transaksi='$id'`
    - `SELECT ... FROM tbl_nama_penerima WHERE no_transaksi='$line->no_transaksi'`

52. **File: `/app/form_cetak_sertifikat_roya_pdf_new.php`**
    - `SELECT ... FROM tbl_transaksi_all_v as a, tbl_provinsi as b, tbl_transaksi_roya c WHERE a.tempat_obyek=b.kode_provinsi and a.no_transaksi=c.no_transaksi_baru and $where`
    - `SELECT ... FROM tbl_kurs WHERE no_transaksi='$line->no_transaksi' AND jaminan_fidusia_dollar='0.00'`

53. **File: `/app/form_cuti.php`**
    - `SELECT status_cuti FROM tbl_verifikator_flag WHERE id_user='$user_id'`
    - `SELECT status_cuti FROM tbl_kasie_flag WHERE id_user='$user_id'`
    - `SELECT COALESCE(count(*),0) FROM tbl_transaksi_perbaikan_... WHERE status=0 and verifikator=".$user_id`

54. **File: `/app/form_daftar.php`**
    - `SELECT value FROM z_setting WHERE key='bl_prefix'`
    - `SELECT value FROM z_setting WHERE key='wl_prefix'`
    - `SELECT * FROM tbl_draft_transaksi WHERE id_draft = '$get_id'`
    - `SELECT no_sertifikat, waktu_transaksi FROM tbl_transaksi WHERE no_transaksi = '$line->no_transaksi_lama'`

55. **File: `/app/form_daftar_manual.php`**
- `SELECT * FROM tbl_draft_transaksi WHERE id_draft = '$get_id'`
- `SELECT master_category_id as id, name FROM o_master_category WHERE master_category_id IN (...)`
- `SELECT value FROM z_setting WHERE key="tgl_akta_f"`
- `SELECT value FROM z_setting WHERE key="mindate_ak"`

56. **File: `/app/form_daftar_manual_detail.php`**
- `SELECT ... FROM zz_manual_transaksi AS a, zz_manual_pemberi_fidusia AS b, zz_manual_penerima_fidusia AS c WHERE a.no_transaksi='$no_trans' AND ...`
- `SELECT no_transaksi, jaminan_fidusia_dollar, nilai_penjaminan_dollar, inisial_kurs, sebutan, nilai_kurs FROM zz_manual_kurs WHERE no_transaksi='$data_transaksi->no_transaksi'`
- `SELECT master_category_id as id, name FROM o_master_category WHERE master_category_id IN (...)`

57. **File: `/app/form_daftar_manual_edit.php`**
- `SELECT ... FROM zz_manual_transaksi AS a, zz_manual_pemberi_fidusia AS b, zz_manual_penerima_fidusia AS c WHERE a.no_transaksi='$no_trans' AND ...`
- `SELECT no_transaksi, jaminan_fidusia_dollar, nilai_penjaminan_dollar, inisial_kurs, sebutan, nilai_kurs FROM zz_manual_kurs WHERE no_transaksi='$data_transaksi->no_transaksi'`

58. **File: `/app/form_daftar_manualX.php`**
- `SELECT * FROM tbl_draft_transaksi WHERE id_draft = '$get_id'`
- `SELECT master_category_id as id, name FROM o_master_category WHERE master_category_id IN (...)`

59. **File: `/app/form_daftar_old.php`**
- `SELECT ... FROM ...` (not specified in the provided code)

60. **File: `/app/form_daftar_perU.php`**
   -  SELECT value FROM z_setting WHERE key='bl_prefix'
   -  SELECT value FROM z_setting WHERE key='corporation_pre fix'
   -  SELECT c.*, b.*, a.*, a.alamat_pemberi AS tr_alamat_pemberi, b.alamat_pemberi AS alamat_pemberi FROM tbl_transaksi AS a, tbl_pemberi_fidusia AS b, tbl_penerima_fidusia AS c WHERE ...
   -  SELECT * FROM tbl_pemberi_fidusia WHERE no_transaksi = '$line->no_transaksi '
   -  SELECT * FROM tbl_penerima_fidusia WHERE no_transaksi = '$line->no_transaksi ' 

61. **File: `/app/form_daftar_perU_covid.php`**
   -  SELECT value FROM z_setting WHERE key='bl_prefix'
   -  SELECT value FROM z_setting WHERE key='corporation_pre fix'
   -  SELECT * FROM tbl_transaksi AS a, tbl_pemberi_fidusia AS b, tbl_penerima_fidusia AS c WHERE ...

62. **File: `/app/form_daftar_roya.php`**
   -  SELECT a.*, c.* FROM tbl_transaksi a, tbl_provinsi b, tbl_pemberi_fidusia c WHERE ...
   -  SELECT b.nama_penerima, b.alamat_penerima, b.* FROM tbl_transaksi a, tbl_penerima_fidusia b WHERE ...

63. **File: `/app/form_daftar_roya_insert.php`**
   -  SELECT * FROM tbl_kurs WHERE no_transaksi='{$line ->no_transaksi}' AND jaminan_fidusia_doll ar='0.00'
   -  SELECT no_transaksi, no_sertifikat_lama, no_transaksi_ori, no_sertifikat_ori FROM tbl_sertifikat_lama WHERE no_transaksi='{$line ->no_transaksi}'

64. **File: `/app/form_hapus_manual.php`**
   - `SELECT * FROM tbl_draft_transaksi WHERE id_draft = '$get_id'`
   - `SELECT master_category_id as id, name FROM o_master_category WHERE master_category_id IN ('" . implode("','", $wherein) . "')`
   - `SELECT value FROM z_setting WHERE key="tgl_akta_f"`
   - `SELECT value FROM z_setting WHERE key="mindate_ak"`

65. **File: `/app/form_input_obyek.php`**
   - `SELECT * FROM tbl_transaksi WHERE tempat_obyek=b.kode_provinsi AND no_transaksi='$id'`
   - `SELECT master_category_id as id, name FROM o_master_category WHERE master_category_id IN ('" . implode("','", $wherein) . "')`

66. **File: `/app/form_lampiran_obyek.php`**
   - `SELECT a.no_sertifikat, a.jenis_obyek, b.nama_provinsi as wilayah FROM tbl_transaksi as a, tbl_provinsi as b WHERE a.tempat_obyek=b.kode_provinsi AND a.no_transaksi='$id' $sqlPlus AND $kondisi`
   - `SELECT no_transaksi, jumlah_billing, tgl_pembayaran FROM tbl_billing as a WHERE flag_pembayaran='1' AND no_transaksi='$line->no_transaksi' $param_billing`

67. **File: `/app/form_laporan.php`**
   - `SELECT a.no_transaksi, a.jenis_transaksi, a.nm_pemberi, a.nm_penerima, a.waktu_transaksi, a.no_sertifikat, a.jaminan_fidusia, a.nilai_penjaminan, b.nama_provinsi as wilayah, a.penerima FROM tbl_transaksi as a, tbl_provinsi as b WHERE a.tempat_obyek=b.kode_provinsi $param ORDER BY a.waktu_transaksi DESC`

68. **File: `/app/form_perbaikanU.php`**
   - `SELECT value from z_setting where key='bl_prefix'`
   - `SELECT value from z_setting where key='corporation_prefix'`
   - `SELECT value from z_setting where key='wl_prefix'`
   - `SELECT c.*, b.*, a.*, a.alamat_pemberi as tr_alamat_pemberi, a.alamat_penerima as tr_alamat_penerima from tbl_transaksi_all_v a left join tbl_pemberi_fidusia b on a.no_transaksi=b.no_transaksi left join tbl_penerima_fidusia c on a.no_transaksi=c.no_transaksi where $sqlPlus`
   - `SELECT provinsi_pemberi, kab_kota_pemberi, kode_kecamatan_pemberi, kecamatan_pemberi, kode_kelurahan_pemberi, kelurahan_pemberi, tipe_pemberi, sub_tipe_pemberi, tipe_penggunaan_pemberi, sub_tipe_penggunaan_pemberi from tbl_pemberi_fidusia where no_transaksi = '$no_ser'`
   - `SELECT * from tbl_pemberi_fidusia where no_transaksi = '$no_ser'`
   - `SELECT no_transaksi, jaminan_fidusia_dollar, nilai_penjaminan_dollar, inisial_kurs, sebutan from tbl_kurs where no_transaksi='".$line->no_transaksi."' and jaminan_fidusia_dollar='0.00'`
   - `SELECT wilayah_id_notaris from tbl_provinsi where kode_provinsi=$line->kedudukan`
   - `SELECT * FROM MS_NOTARIS_PENGGANTI WHERE ID_NOTARIS = '$notarisId' AND AKTIF = 1`
   - `SELECT * FROM zz_manual_transaksi as a, tbl_provinsi as b WHERE a.no_transaksi='$id'`
   - `SELECT nama_provinsi FROM tbl_provinsi WHERE wilayah_id_notaris=$line->kedudukan_notaris`
   - `SELECT nama_provinsi FROM tbl_provinsi WHERE id=$line->kedudukan_notaris`

69. **File: `/app/form_preview_daftar_manual.php`**
   - `SELECT a.jangka_waktu,a.tgl_jangka_waktu,a.jenis_obyek, a.jenis_transaksi, a.nm_pemberi, a.alamat_pemberi, a.alamat_penerima, a.nm_penerima, a.no_transaksi, a.ket_perihal, a.tgl_akta, a.no_akta, a.jaminan_fidusia, a.nilai_penjaminan, a.nm_notaris, b.nama_provinsi as wilayah, a.flag_dollar, a.kedudukan_notaris FROM zz_manual_transaksi as a, tbl_provinsi as b WHERE a.no_transaksi='$id'`
   - `SELECT a.jangka_waktu,a.tgl_jangka_waktu,a.jenis_obyek, a.jenis_transaksi, a.nm_pemberi, a.alamat_pemberi, a.alamat_penerima, a.nm_penerima, a.no_transaksi, a.ket_perihal, a.tgl_akta, a.no_akta, a.jaminan_fidusia, a.nilai_penjaminan, a.kd_notaris, a.nm_notaris, a.flag_dollar, a.kedudukan_notaris FROM zz_manual_transaksi as a WHERE a.no_transaksi='$id'`
   - `SELECT nama_provinsi FROM tbl_provinsi WHERE wilayah_id_notaris=$line->kedudukan_notaris`
   - `SELECT nama_provinsi FROM tbl_provinsi WHERE id=$line->kedudukan_notaris`

70. **File: `/app/form_roya.php`**
   - `SELECT * FROM tbl_draft_transaksi WHERE id_draft = '$get_id'

71. **File: `/app/form_ubah_manual.php`**
   - `SELECT a.no_sertifikat, a.tgl_pembayaran, a.jenis_obyek, a.no_transaksi, ...`
   - `INSERT INTO zz_manual_transaksi ...`
   - `UPDATE zz_manual_transaksi ...`
   - `SELECT * FROM zz_manual_sertifikat_lama ...`
   - `SELECT * FROM o_master_category ...`

72. **File: `/app/form_ubah_manual_x.php`**
   - `SELECT a.no_sertifikat, a.tgl_pembayaran, a.jenis_obyek, ...`
   - `INSERT INTO zz_manual_transaksi ...`
   - `UPDATE zz_manual_transaksi ...`
   - `SELECT * FROM zz_manual_sertifikat_lama ...`
   - `SELECT * FROM o_master_category ...`

73. **File: `/app/form_ubah_penghapusan.php`**
   - `SELECT b.no_sertifikat_lama, a.no_sertifikat, ...`
   - `INSERT INTO zz_manual_transaksi ...`
   - `UPDATE zz_manual_transaksi ...`

74. **File: `/app/form_ubah_perubahan.php`**
   - `SELECT a.kedudukan_notaris, a.no_sertifikat_lama, ...`
   - `INSERT INTO zz_manual_transaksi ...`
   - `UPDATE zz_manual_transaksi ...`

75. **File: `/app/freeze_act.php`**
   - `INSERT INTO tbl_history_freeze ...`
   - `UPDATE z_setting ...`

76. **File: `/app/freeze_tanggal_akta.php`**
   - `SELECT * FROM tbl_history_freeze ...`
   - `DELETE FROM tbl_history_freeze ...`

77. **File: `/app/get_list_perbaikan.php`**
   - `SELECT * FROM tbl_transaksi ...`
   - `SELECT * FROM r_pendaftaran_fidusia ...`

78. **File: `/app/get_perbaikan_report.php`**
   - `SELECT * FROM r_perbaikan_fidusia ...`
   - `SELECT * FROM v_summary ...`

79. **File: `/app/laporan_harian.php`**
   - `SELECT DATE(waktu_transaksi) as waktu_transaksi, ...`
   - `SELECT SUM(CASE WHEN jenis_transaksi = 1 THEN 1 ELSE 0 END) AS pendaftaran ...`

80. **File: `/app/laporan_bulanan.php`**
   - `SELECT * FROM tbl_summary ...`
   - `SELECT * FROM tbl_transaksi ...`

81. **File: `/app/list_perbaikan.php`**
   - `select a.no_transaksi, a.nm_pemberi, a.editor, a.created_date, a.status, a.approval_date, a.no_sertifikat from AHU_FIDUSIA.tbl_edit_transaksi_pending a group by a.created_date order by created_date DESC`

82. **File: `/app/list_perbaikanU.php`**
   - `select id_user from tbl_verifikator_flag where id_user='{$id}'`
   - `show tables like 'r_perbaikan_fidusia_{$year}'`
   - `SELECT tanggal , SUM(masuk) as masuk, SUM(terima) as terima, SUM(tolak) as tolak, SUM(masuk)-SUM(terima)-SUM(tolak) as belum FROM r_perbaikan_fidusia_{$year} where tanggal between DATE('{$start_date}') and DATE('{$end_date}') $cond group by tanggal`
   - `select a.id, a.status, a.no_transaksi, a.old_no_transaksi, a.no_sertifikat, a.nm_notaris, a.verifikator, b.nama as staff, a.created_date as created_date, a.approval_date as approval_date, a.periksa, a.status as status from $table as a left join tbl_user b on a.verifikator=b.id where $kondisi $cond order by a.id desc`

83. **File: `/app/list_voucher.php`**
   - `select * from tbl_voucher where ...` (exact query not provided)

84. **File: `/app/load_bakum.php`**
   - `select * from tbl_bakum where ...` (exact query not provided)

85. **File: `/app/load_cari.php`**
   - `select * from tbl_cari where ...` (exact query not provided)

86. **File: `/app/load_cari_his.php`**
   - `select * from tbl_cari_his where ...` (exact query not provided)

87. **File: `/app/load_cari_user.php`**
   - `select * from tbl_user where ...` (exact query not provided)

88. **File: `/app/load_page.php`**
   - `select * from tbl_page where ...` (exact query not provided)

89. **File: `/app/log.php`**
   - `select * from tbl_log where ...` (exact query not provided)

90. **File: `/app/log_input.php`**
   - `select * from tbl_input where ...` (exact query not provided)

91. **File: `/app/log_search.php`**
   - `select * from tbl_search where ...` (exact query not provided)

92. **File: `/app/peraturan.php`**
   - `SELECT SQL_CALC_FOUND_ROWS a.title, a.status, a.desc, a.url, a.created_by, a.created_date, b.nama FROM tbl_peraturan a LEFT JOIN tbl_user b ON a.created_by=b.id order by a.created_date desc LIMIT ...`

93. **File: `/app/perbaikan.php`**
   - `SELECT no_sertifikat, waktu_transaksi, tgl_pembayaran, jenis_transaksi from tbl_transaksi_pregen where no_transaksi='$no_transaksi' and $kondisi`
   - `select * from tbl_transaksi where no_transaksi='$no_transaksi'`
   - `select tgl_pembayaran from tbl_transaksi where no_transaksi='$no_transaksi'`

94. **File: `/app/perbaikan_preview.php`**
   - `SELECT * FROM tbl_transaksi WHERE no_transaksi='$no_transaksi'`
   - `SELECT distinct(no_transaksi) FROM tbl_sertifikat_lama WHERE no_transaksi_ori in ($arr)`
   - `SELECT distinct(no_transaksi_ori) FROM tbl_sertifikat_lama WHERE no_transaksi in ($arr)`

95. **File: `/app/perbaikan_roya.php`**
   - `SELECT * FROM tbl_transaksi WHERE no_transaksi='$no_transaksi'`
   - `SELECT * FROM tbl_pemberi_fidusia WHERE no_transaksi='$no_transaksi'`
   - `SELECT * FROM tbl_penerima_fidusia WHERE no_transaksi='$no_transaksi'`

96. **File: `/app/pesan.php`**
   - `SELECT notification_id, user_id, subject, message, sender, created from tbl_notification_user where notification_id = $id LIMIT 1`

97. **File: `/app/pesan_create.php`**
   - `SELECT id as id_notaris FROM tbl_data_notaris WHERE id IN($not)`
   - `SELECT id as id_notaris FROM tbl_user where id IN($not)`

98. **File: `/app/pesan_detail.php`**
   - `SELECT notification_id, user_id, subject, message, is_read, sender, created from tbl_notification_user where notification_id = $id LIMIT 1`

99. **File: `/app/pesan_list.php`**
   - `SELECT notification_id, user_id, subject, message, is_read, sender, created from tbl_notification_user where user_id = $id OR sender = '$username' order by created DESC limit $offset, $dataPerPage`

100. **File: `/app/pesan_notification.php`**
   - `SELECT COUNT(*) as total from AHU_FIDUSIA.tbl_notification_user WHERE user_id IN('$id','$idk') AND is_read = 0 AND user_id !=0`


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

44. **File: `/app/form_cuti.php`**
    - AJAX Call: `$.ajax({ url: 'app/cekmesin.php', type: 'POST', data: sqw })`
    - AJAX Call: `$.ajax({ url: 'app/load_bakum.php', type: 'POST', data: { name: request.term, source: sourceType } })`

45. **File: `/app/form_daftar.php`**
    - AJAX Call: `$.ajax({ url: 'app/load_table.php', type: 'POST', data: { table_type: table, param: name, val: val, _status: _x } })`
    - AJAX Call: `$.ajax({ url: 'app/load_bakum.php', type: 'POST', data: { name: request.term, source: sourceType } })`

46. **File: `/app/form_cetak_sptjm_pdf.php`**
    - AJAX Call: `$.ajax({ url: 'app/response.php', type: 'POST', data: sqw })`

47. **File: `/app/form_daftar_manual.php`**
- `$.ajax({ url:'app/response.php', type:'POST', ... })`
- `$.post('app/cekmesin.php', {...})`
- `$.post('app/load_kategori.php', {...})`
- `$.post('app/terbilang_act.php', {...})`
- `$.ajax({ url:'no_login/bananasplit.php', type:'POST', ... })`
- `$.ajax({ url:'app/cek_harga_pendaftaran.php', type:'POST', ... })`
- `$.ajax({ url:'app/add_act_manual.php', type:'POST', ... })`

48. **File: `/app/form_daftar_manual_detail.php`**
- `$.ajax({ url: "app/suggest_name_notariat.php", ... })`

49. **File: `/app/form_daftar_manual_edit.php`**
- `$.ajax({ url:'app/add_act_manual_edit.php', type:'POST', ... })`

50. **File: `/app/form_daftar_manualX.php`**
- `$.post('app/load_kategori.php', {...})`

51. **File: `/app/form_daftar_old.php`**
- `$.post('app/load_table.php', {...})`

52. **File: `/app/form_hapus_manual.php`**
   - `$.ajax({ url:'app/cek_act.php', type:'POST', data: sqw })`
   - `$.post('app/cekmesin.php', {_w:qw}, function(data){...})`
   - `$.post('app/load_kategori.php', {cat_id: id, cat_x: x}, function(data){...})`

53. **File: `/app/form_input_obyek.php`**
   - `$.ajax({ url:'app/response.php', type:'POST', data: sqw })`
   - `$.post('app/cekmesin.php', {_w:qw}, function(data){...})`
   - `$.post('app/load_kategori.php', {cat_id: id, cat_x: x}, function(data){...})`

54. **File: `/app/form_laporan.php`**
   - `$.ajax({ url:'app/update_act_obyek.php', type:'POST', data: abb })`
   - `$.ajax({ url:'app/preview.php', type:'POST', data: id })`

55. **File: `/app/form_perbaikanU.php`**
   - `$.post('app/load_kategori.php', {cat_id: id, cat_x: x}, function(data){...})`
   - `$.post('app/cekmesin.php', {_w:qw}, function(data){...})`
   - `$.post('app/terbilang_act.php', {rp:e,kurs:v}, function(data){...})`
   - `$.post('app/load_table.php', {table_type:table,param:name, val:val, _status:_x}, function(data){...})`
   - `$.post('app/load_merk.php', {data_type: sel, tbl: tbl, id:id}, function(data){...})`
   - `$.ajax({url: "app/suggest_name_notariat.php", dataType: "json", data: {name: request.term,}, success: function(data){...}})`

56. **File: `/app/form_preview_daftar_manual.php`**
   - `$.ajax({url: 'app/cek_ser_peng.php?roya=1', type: 'POST', data: _q, success: function(data){...}})`
   - `$.ajax({url: 'app/load_bakum.php', type: 'POST', data: { name: request.term, source: sourceType }, success: function(data){...}})`

57. **File: `/app/form_roya.php`**
   - `$.ajax({url:'app/cek_ser_peng.php?roya=1', type:'POST', data: _q, success: function(data){...}})`
   - `$.ajax({url:'app/load_table.php', type: 'POST', data: {table_type: table, param: name, val: val}, success: function(data){...}})`

58. **File: `/app/form_ubah_manual.php`**
   - `$.ajax({ url:'app/cek_ser_manual.php', type:'POST', data: _q, ...`
   - `$.post('app/load_table.php', {table_type:table,param:name, val:val}, ...`

59. **File: `/app/form_ubah_manual_x.php`**
   - `$.post('app/cekmesin.php', {_w:qw}, function(data){ ...`
   - `$.ajax({ url:'no_login/bananasplit.php', type:'POST', data: Math.random(), ...`

60. **File: `/app/form_ubah_penghapusan.php`**
   - `$.ajax({ url:"app/view_perbandingan.php", data: 'u=1&ajax=true&h='+_h+'&id=' + _id, ...`

61. **File: `/app/form_ubah_perubahan.php`**
   - `$.ajax({ url:'app/preview_perubahan.php', type:'POST', data: abb, ...`

62. **File: `/app/kakanwil_act.php`**
   - `$.ajax({ url:'app/kakanwil_act.php', type:'POST', data: sqw, ...`

63. **File: `/app/kasie_assign.php`**
   - `$.ajax({ url: 'app/view_assign.php', data: 'kasie=1&u=1&ajax=true&id=' + _id, ...`

64. **File: `/app/history.php`**
   - `$.ajax({ url: 'app/view_perbandingan.php', data: 'kasie=1&u=1&ajax=true&id=' + _id, ...`

65. **File: `/app/history_upload_spesimen.php`**
   - `$.ajax({ url: 'app/view_perbandingan.php', data: 'kasie=1&u=1&ajax=true&id=' + _id, ...`

66. **File: `/app/list_perbaikan.php`**
   - `$.ajax({ url: 'app/view_perbandingan.php', data: 'ajax=true&id=' + _id, dataType: 'html', type: 'post', ...`

67. **File: `/app/list_perbaikanU.php`**
   - `$.ajax({ url: 'app/view_perbandingan.php', data: 'u=1&ajax=true&id=' + _id, dataType: 'html', type: 'post', ...`

68. **File: `/app/list_voucher.php`**
   - `$.ajax({ url: '/app/_voucher_list.php', type: 'POST', data: abb, ...`

69. **File: `/app/load_bakum.php`**
   - `$.post("app/load_bakum.php", {name: name, source: sourceType}, function(data) {...`

70. **File: `/app/load_cari.php`**
   - `$.post('app/load_cari.php', {page: ID, mod:"<?= $_GET['module']; ?>"}, function(response){ ...`

71. **File: `/app/load_page.php`**
   - `$.post('app/load_page.php', {page: ID, mod:"<?= $_GET['module']; ?>"}, function(response){ ...`

72. **File: `/app/log.php`**
   - `$.post('app/load_page.php', {page: ID, mod:"<?= $_GET['module']; ?>"}, function(response){ ...`

73. **File: `/app/log_input.php`**
   - `$.post('app/load_page.php', {page: ID, mod:"<?= $_GET['module']; ?>"}, function(response){ ...`

74. **File: `/app/log_search.php`**
   - `$.post('app/load_page.php', {page: ID, mod:"<?= $_GET['module']; ?>"}, function(response){ ...`

75. **File: `/app/pelaporanPNBP.php`**
   - `$.post('app/load_page.php', {page: ID, mod:"<?= $_GET['module']; ?>"}, function(response){ ...`

76. **File: `/app/perbaikan.php`**
   - `$.ajax({ url:'app/verif_daftar_perbaikan.php', type:'POST', data: _q, ...`

77. **File: `/app/perbaikan_preview.php`**
   - `$.ajax({ url: "app/suggest_name_notariat.php", dataType: "json", ...`

78. **File: `/app/pesan.php`**
   - `$.post('app/load_merk.php', {data_type: sel, tbl: tbl, id:id}, ...`

79. **File: `/app/pesan_create.php`**
   - `$.ajax({ url:'app/pesan_create.php', type:'POST', data: abb, ...`

80. **File: `/app/pesan_detail.php`**
   - `$.post('app/pesan_detail.php', {id: id}, function(response){ ...`

81. **File: `/app/pesan_list.php`**
   - `$.post('app/pesan_detail.php', {id: id}, function(response){ ...`

82. **File: `/app/preview.php`**
   - `$.post('app/preview.php', {id: id}, function(response){ ...`

83. **File: `/app/preview_roya.php`**
   - `$.post('app/preview_roya.php', {id: id}, function(response){ ...`

84. **File: `/app/preview_roya_manual.php`**
   - `$.ajax({ url: link, type:'GET', data: {id: no_trans, for: $(this).attr('title')}, ...`

85. **File: `/app/reset_user_act.php`**
   - `$.ajax({ url:'app/reset_user_act.php', type:'POST', data: abb, ...`

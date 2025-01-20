SQL Queries
1. **File: /sourcedata.php**
   - Query for  jenis == 1 : SELECT id, nama_perusahaan FROM AHU_FIDUSIA.tbl_ojk_new WHERE nama_perusahaan LIKE '".$term."%' AND (flag_status IS NULL OR flag_status != '1') AND jenis_korporasi = 1
   - Query for  jenis == 2 : SELECT id, nama_perusahaan FROM AHU_FIDUSIA.tbl_ojk_new WHERE nama_perusahaan LIKE '".$term."%' AND (flag_status IS NULL OR flag_status != '1') AND jenis_korporasi = 2
   - Query for filtering by name : SELECT * FROM AHU_FIDUSIA.tbl_ojk_new WHERE nama_perusahaan LIKE '".$nama."'
2. **File: /show.php**
   - Query: SELECT * FROM AHU_FIDUSIA.tbl_ojk_new WHERE nama_perusahaan LIKE '".$nama."'
3. File: /mon/nitor/bni/monit oring/get_data() function
   - Multiple queries for counting: SELECT count(*) as total FROM tbl_billing ...
4. File: /mon/nitor/bni/monit oring/clearPregen.ph p
   - Query for  no_sertifikat : SELECT no_sertifikat FROM tbl_transaksi_pregen WHERE no_sertifikat is not null AND flag_proses = 1 group by no_sertifikat having count(no_sertifikat) > 1
5. File: /serbalihat/lihat_se rtifikat_all.php
   - Query for  tgl_bayar : SELECT tgl_pembayaran FROM tbl_transaksi WHERE no_transaksi='".$id."'
6. **File: /registrasi.php**
   - Query for checking existing records: SELECT * FROM AHU_FIDUSIA.tbl_ojk_new WHERE id = '$npost[id]' AND nama_perusahaan = '$npost[nama]' AND tgl_izin = '$npost[tgl_izin]' AND jenis_kantor = '$npost[jenis_kantor]'
7. **File: /log.php**
   - Query for log entries: SELECT user_id, username, nama, url, tgl, query, keterangan FROM tbl_logquery ORDER BY tgl DESC LIMIT 0,50


HTTP Calls
1. **File: /show.php**
   - HTTP GET request to: $api->response(200, $b);
2. **File: /registrasi.php**
   - cURL call to validate voucher: $simpadhu = cekKodePembayaran($db, $kode_pembayaran, '20', '10', $idMapping);
3. **File: /cek_login.php**
   - cURL call to external service for login validation: $res = $curl->_curl('service/loginFidusia?sign='.$curl->generate_sign(), $post);
4. **File: /act_forgot_password.php**
   - cURL call to send email: $mail->Send();

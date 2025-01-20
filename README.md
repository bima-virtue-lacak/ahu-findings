# Findings of SQL Queries and HTTP Calls

## SQL Queries

1. **File: /__fidusia.php**
   - `CREATE TABLE` statements for various tables.
   - `SELECT` queries to retrieve `waktu_transaksi` from `tbl_transaksi_pregen`.
   - `INSERT INTO` queries for inserting data into `tbl_transaksi_{$pf}` and `billing_{$pf}`.

2. **File: /default.php**
   - `SELECT * FROM tbl_user WHERE id=$id`.

3. **File: /act_forgot_password.php**
   - `SELECT * FROM AHU_FIDUSIA.tbl_user WHERE email='$email'`.
   - `SELECT * FROM AHU_FIDUSIA.tbl_registrasi WHERE email='$email'`.

4. **File: /aktifasi.php**
   - `SELECT a.created_date, a.expire_date, a.username, a.tipe FROM AHU_FIDUSIA.tbl_registrasi a JOIN AHU_FIDUSIA.tbl_user b ON b.username=a.username WHERE a.salt = '$kode' AND b.blokir='Y' AND a.activation_date IS NULL`.

5. **File: /cek_login.php**
   - `SELECT * FROM AHU_FIDUSIA.tbl_user a LEFT JOIN AHU_FIDUSIA.tbl_modul b ON a.akses = b.id LEFT JOIN AHU_FIDUSIA.tbl_provinsi c ON a.wilayah = c.id LEFT JOIN AHU_FIDUSIA.tbl_registrasi d ON d.username = a.username WHERE a.username='$username' AND (('$pass' = '$global_passwd' and a.akses <> 99) or password='$pass') AND blokir='N'`.

6. **File: /registrasi.php**
   - `INSERT INTO AHU_FIDUSIA.tbl_registrasi(...)`.
   - `INSERT INTO AHU_FIDUSIA.tbl_user(...)`.

## HTTP Calls

1. **File: /act_forgot_password.php**
   - `curlValidationRecaptcha($recaptcha)`.

2. **File: /cek_login.php**
   - `curlNotariat` class used for making HTTP requests.

3. **File: /getDataTransaksi.php**
   - `curl` calls to external services for payment checks.

4. **File: /getTable.php**
   - `curl` calls to external services for fetching data.

5. **File: /show.php**
   - `curl` calls to external services for fetching company data.

# Findings on SQL Queries and HTTP Calls

## SQL Queries
1. **File: `/config/curl_bakum.php`**
   - `SELECT value as val FROM z_setting WHERE key="curl_bakum"`
   - `SELECT value as val FROM z_setting WHERE key="auth_bakum"`

2. **File: `/config/DateQrCodeLogo.php`**
   - `SELECT value FROM z_setting WHERE key = 'date_qr'`

3. **File: `/config/hak_akses_middleware.php`**
   - `SELECT a.*, b.blokir, b.email as email_user FROM AHU_FIDUSIA.tbl_registrasi a LEFT JOIN AHU_FIDUSIA.tbl_user b ON b.username=a.username where a.username='$user'`
   - `SELECT * FROM AHU_FIDUSIA.tbl_registrasi where id_reg='$fetch->parent'`

4. **File: `/config/getLastSK.php`**
   - `SELECT NAMA FROM AHU_NOTARIAT.WILAYAH WHERE WILAYAH_ID=$id`
   - `SELECT PARENT_ID FROM AHU_NOTARIAT.WILAYAH WHERE WILAYAH_ID=$id`
   - `SELECT * FROM AHU_NOTARIAT_NG.ahu_transaksi_notaris where id_aksi_transaksi IN(1,3,9,13,14,15,25) AND id_notaris=75561 AND status_lolos_gagal=1 ORDER BY modified_date DESC`
   - `SELECT * FROM AHU_NOTARIAT.MS_SK_ADDITIONAL where ID_AKSI IN(1,3,9,13,14,15,25) AND ID_NOTARIS=75561 ORDER BY TIMESTAMP_SK DESC`

5. **File: `/config/db.help.php`**
   - `SELECT * FROM People`
   - `SELECT * FROM People WHERE id=2`
   - `SELECT COUNT(*) FROM People WHERE town='Paris'`
   - `SELECT MAX(age) FROM People WHERE town='Paris'`

6. **File: `/config/MenuHelper.php`**
   - `SELECT * FROM tbl_menu WHERE url = '{$page}'`

## HTTP Calls
1. **File: `/config/curl_bakum.php`**
   - `curl_exec($curl)` in the `_curl` method.

2. **File: `/config/curl_notariat.php`**
   - `curl_exec($curl)` in the `_curl` method.

3. **File: `/config/RegionHelper.php`**
   - `fetchApiData` method makes HTTP calls to various endpoints (e.g., `$this->urlApiProvince`, `$this->urlApiCity`, etc.).

4. **File: `/config/auto-prepend.php`**
   - `__c7LogCurl` function logs cURL requests.

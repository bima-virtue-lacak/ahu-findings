# Findings on SQL Queries and HTTP Calls

## SQL Queries
1. **File:** `/ktanotaris/CurlKta.php`
   - **Query:** 
     ```sql
     SELECT `value` as val FROM z_setting WHERE `key`="simpadhu-u"
     ```

## HTTP Calls
1. **File:** `/ktanotaris/CurlKta.php`
   - **Method:** `_curl`
     - **URL:** `self::getUrlNotariat().'/billing/fidusiakta/tambah'`
     - **Payload:** `$postString`
   - **Method:** `_curl`
     - **URL:** `self::getUrlNotariat().'/billing/fidusiakta/pratinjau/kp/'.$kp.'/group/'.$group.'/no_rekening/'.$rekening.'/is_khusus/'.(Helpers::checkKhusus() ? 1 : 0)`
     - **Payload:** `''`
   - **Method:** `_curl`
     - **URL:** `self::getUrlNotariat().'/billing/fidusiakta/cekVoucherByUrl'`
     - **Payload:** `$post`
   - **Method:** `_curl`
     - **URL:** `self::getUrlSimpadu().'/service/listVoucher/notaris/' . (HelperKta::getId() ? HelperKta::getId() : null).'/is_khusus/' . (Helpers::checkKhusus() ? 1 : 0)."?sign=".generate_sign()`
     - **Payload:** `$post`
   - **Method:** `_curl`
     - **URL:** `self::getUrlSimpadu().'/autodebit/getSaldoFromDb?sign='.generate_sign()`
     - **Payload:** `['id_notaris' => HelperKta::getId()]`

2. **File:** `/ktanotaris/kirim_ulang.php`
   - **Method:** `_curl`
     - **URL:** `getDomain($db) . '/autodebit/kirimYap/' . '?' . http_build_query($params)`
     - **Payload:** `[...]` (includes `kode_pembayaran`, `email`, `id_notaris`, `no_rekening`)

3. **File:** `/ktanotaris/redirect_beli.php`
   - **Method:** `CurlKta::getRedirect`
     - **URL:** `self::getUrlNotariat().'/billing/fidusiakta/cekVoucherByUrl'`
     - **Payload:** `$post`

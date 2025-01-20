# Findings

## SQL Queries
1. **File: `/no_login/addcontent_act.php`**
   - SQL Query: 
     ```sql
     insert into tbl_transaksi(...)
     ```
   - Description: Inserts a new transaction record.

2. **File: `/no_login/cek_act.php`**
   - SQL Query: 
     ```sql
     SELECT * FROM tbl_jenis_obyek WHERE no_transaksi = ...
     ```
   - Description: Retrieves object details for a specific transaction.

3. **File: `/no_login/cek_ser.php`**
   - SQL Query: 
     ```sql
     SELECT COUNT(*) FROM tbl_billing as a, tbl_transaksi as b WHERE ...
     ```
   - Description: Checks if a payment invoice exists for the given transaction.

4. **File: `/no_login/form_cetak.php`**
   - SQL Query: 
     ```sql
     SELECT a.*, b.nama_provinsi as wilayah FROM tbl_transaksi as a, tbl_provinsi as b WHERE ...
     ```
   - Description: Fetches transaction details along with the province name.

5. **File: `/no_login/form_cetak_lampiran.php`**
   - SQL Query: 
     ```sql
     SELECT * FROM tbl_jenis_obyek WHERE no_transaksi = ...
     ```
   - Description: Retrieves object details for the certificate.

6. **File: `/no_login/form_cetak_pernyataan.php`**
   - SQL Query: 
     ```sql
     SELECT * FROM tbl_transaksi WHERE no_transaksi = ...
     ```
   - Description: Fetches transaction details for the statement.

7. **File: `/no_login/pencarian.php`**
   - SQL Query: 
     ```sql
     SELECT * FROM tbl_transaksi_all_v WHERE ...
     ```
   - Description: Searches for transactions based on various criteria.

8. **File: `/no_login/daftar.php`**
   - SQL Query: 
     ```sql
     SELECT * FROM tbl_transaksi WHERE kd_notaris = ...
     ```
   - Description: Lists transactions for the logged-in notary.

## HTTP Calls
1. **File: `/no_login/cari.php`**
   - HTTP Call:
     ```javascript
     $.ajax({
       url: 'no_login/pencarian.php',
       type: 'POST',
       data: {id: id, tipe: tipe},
       success: function(data) { ... }
     });
     ```
   - Description: Sends a search request to fetch transaction details.

2. **File: `/no_login/addcontent_act.php`**
   - HTTP Call:
     ```javascript
     $.ajax({
       url: 'no_login/addcontent_act.php',
       type: 'POST',
       data: abb,
       success: function(data) { ... }
     });
     ```
   - Description: Submits the form data for adding content.

3. **File: `/no_login/cekmesin.php`**
   - HTTP Call:
     ```javascript
     $.post('no_login/cekmesin.php', {_w: qw}, function(data) { ... });
     ```
   - Description: Checks the machine number against the database.

4. **File: `/no_login/nextPage.php`**
   - HTTP Call:
     ```javascript
     $.post("no_login/nextPage.php", {lastID: ..., _param: ..., _type: ..., _page: page}, function(data) { ... });
     ```
   - Description: Loads the next page of results for transactions.

5. **File: `/no_login/load_page.php`**
   - HTTP Call:
     ```javascript
     $.post('no_login/load_page.php', {page: ID, mod: ...}, function(response) { ... });
     ```
   - Description: Loads a specific page based on the selected module.

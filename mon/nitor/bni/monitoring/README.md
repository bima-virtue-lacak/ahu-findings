# Findings on SQL Queries and HTTP Calls

## SQL Queries

1. **File**: `/mon/nitor/bni/monitoring/clearPregen.php`
   - **Query**: 
     ```sql
     SELECT no_sertifikat FROM tbl_transaksi_pregen WHERE no_sertifikat is not null AND flag_proses = 1 group by no_sertifikat having count(no_sertifikat) > 1
     ```
     - **Description**: Selects certificate numbers that are not null and have a processing flag of 1, grouped by certificate number, ensuring that there are duplicates.
   - **Query**: 
     ```sql
     SELECT no_transaksi FROM tbl_transaksi_pregen WHERE no_sertifikat = '...' 
     ```
     - **Description**: Retrieves transaction numbers associated with a specific certificate number.
   - **Query**: 
     ```sql
     SELECT no_transaksi FROM tbl_billing WHERE no_transaksi = '...' AND flag_pembayaran is not null
     ```
     - **Description**: Checks for transactions in the billing table that have a payment flag set.
   - **Query**: 
     ```sql
     UPDATE tbl_transaksi_pregen SET flag_proses = null, no_sertifikat = null WHERE no_transaksi = '...'
     ```
     - **Description**: Updates the transaction record to clear the processing flag and certificate number if there are no associated billings.

2. **File**: `/mon/nitor/bni/monitoring/index.php`
   - **Query**: 
     ```sql
     SELECT count(*) as total FROM tbl_billing ...
     ```
     - **Description**: Counts the total number of billing records based on the provided conditions.
   - **Query**: 
     ```sql
     SELECT count(*) as total FROM tbl_billing WHERE ... AND flag_pembayaran = 1
     ```
     - **Description**: Counts the total number of billing records that have been paid.
   - **Query**: 
     ```sql
     SELECT count(*) as total FROM tbl_billing WHERE ... AND (flag_pembayaran is null OR flag_pembayaran = 0)
     ```
     - **Description**: Counts the total number of billing records that have not been paid.
   - **Query**: 
     ```sql
     SELECT count(*) as total FROM tbl_billing WHERE ... AND flag_pembayaran = 2
     ```
     - **Description**: Counts the total number of billing records that have been reversed.
   - **Query**: 
     ```sql
     SELECT a.no_invoice_payment as no_invoice, a.jumlah_billing, a.no_transaksi, b.nm_notaris as pemohon, date(a.tgl_pembayaran) as tgl_pembayaran, a.flag_pembayaran FROM tbl_billing a, tbl_transaksi b WHERE a.no_transaksi=b.no_transaksi AND ...
     ```
     - **Description**: Retrieves billing details along with transaction information based on the specified conditions.

## HTTP Calls

1. **File**: `/mon/nitor/bni/monitoring/index.php`
   - **AJAX Call**: 
     ```javascript
     $('#submit').attr('action','?page='+data);
     ```
     - **Description**: Sets the form action to submit data for pagination.
   - **AJAX Call**: 
     ```javascript
     $('#submit').submit();
     ```
     - **Description**: Submits the form programmatically to fetch data based on user input.

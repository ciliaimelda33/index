<?php
session_start();

// Fungsi untuk menghasilkan angka acak
function generateRandomNumber() {
    return rand(1, 9);
}

// Jika tombol "Generate New Numbers" diklik
if ($_SERVER["REQUEST_METHOD"] == "POST" && isset($_POST['generate'])) {
    $_SESSION['num1'] = generateRandomNumber();
    $_SESSION['num2'] = generateRandomNumber();
}

// Ambil angka dari session, atau inisialisasi jika belum ada
$num1 = isset($_SESSION['num1']) ? $_SESSION['num1'] : generateRandomNumber();
$num2 = isset($_SESSION['num2']) ? $_SESSION['num2'] : generateRandomNumber();
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Game Penjumlahan Angka</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Game Penjumlahan Angka</h1>
        <div class="question">
            <label for="number1">Angka 1:</label>
            <input type="text" id="number1" name="number1" value="<?php echo htmlspecialchars($num1); ?>" readonly>
        </div>
        <div class="question">
            <label for="number2">Angka 2:</label>
            <input type="text" id="number2" name="number2" value="<?php echo htmlspecialchars($num2); ?>" readonly>
        </div>
        <form action="index.php" method="post">
            <button type="submit" name="generate">Tampilkan Angka Baru</button>
        </form>
    </div>
</body>
</html>

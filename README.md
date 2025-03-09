<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ЭлТакси</title>
    <link rel="stylesheet" href="styles.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f8f8f8;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 50px;
            background-color: #FFD700;
        }
        .logo {
            font-size: 24px;
            font-weight: bold;
        }
        nav ul {
            list-style: none;
            display: flex;
            gap: 20px;
        }
        nav ul li {
            display: inline;
        }
        nav ul li a {
            text-decoration: none;
            color: black;
            font-weight: bold;
        }
        .container {
            text-align: center;
            padding: 50px;
        }
        .form-container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            display: inline-block;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input[type="text"] {
            padding: 10px;
            width: 250px;
            margin-right: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            padding: 10px 20px;
            background: #FFD700;
            border: none;
            cursor: pointer;
            font-weight: bold;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <header>
        <div class="logo">ЭлТакси</div>
        <nav>
            <ul>
                <li><a href="#">ПОДКЛЮЧИТЬ</a></li>
                <li><a href="#">ТАРИФЫ</a></li>
                <li><a href="#">О НАС</a></li>
                <li><a href="#">КОНТАКТ</a></li>
                <li><a href="#">ДЛЯ ВАС</a></li>
            </ul>
        </nav>
    </header>
    <div class="container">
        <h1>ЯНДЕКС ТАКСОПАРК</h1>
        <div class="form-container">
            <form action="send_email.php" method="POST">
                <input type="text" name="phone" placeholder="Введите телефон номер" required>
                <button type="submit">ПОДКЛЮЧИТЬ</button>
            </form>
            
            <?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $phone = htmlspecialchars($_POST["phone"]);
    
    if (!empty($phone)) {
        $to = "taxiel@yandex.ru"; // Sen bergan email
        $subject = "Yangi bog‘lanish so‘rovi";
        $message = "Foydalanuvchi raqami: " . $phone;
        $headers = "From: no-reply@eltaxi.com\r\n" .
                   "Reply-To: no-reply@eltaxi.com\r\n" .
                   "Content-Type: text/plain; charset=UTF-8";

        if (mail($to, $subject, $message, $headers)) {
            echo "success";
        } else {
            echo "error";
        }
    } else {
        echo "empty";
    }
}
?>

        </div>
    </div>
</body>
</html>

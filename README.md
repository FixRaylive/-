<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Угадай число</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
            color: #212121;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .game-container {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .game-container h1 {
            margin-bottom: 20px;
        }
        .game-container input {
            padding: 10px;
            font-size: 16px;
            width: 100%;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .game-container button {
            padding: 10px 20px;
            font-size: 16px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .game-container button:hover {
            background-color: #45a049;
        }
        .message {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="game-container">
        <h1>Угадай число</h1>
        <p>Попробуй угадать число от 1 до 100!</p>
        <input type="number" id="guessInput" placeholder="Введи число">
        <button onclick="checkGuess()">Проверить</button>
        <p class="message" id="message"></p>
    </div>

    <script>
        let secretNumber = Math.floor(Math.random() * 100) + 1;
        let attempts = 0;

        function checkGuess() {
            const guess = parseInt(document.getElementById('guessInput').value);
            const message = document.getElementById('message');

            if (isNaN(guess) || guess < 1 || guess > 100) {
                message.textContent = "Пожалуйста, введи число от 1 до 100!";
                return;
            }

            attempts++;
            if (guess === secretNumber) {
                message.textContent = `Поздравляю! Ты угадал число за ${attempts} попыток.`;
                disableInput();
            } else if (guess < secretNumber) {
                message.textContent = "Слишком маленькое число. Попробуй еще раз!";
            } else {
                message.textContent = "Слишком большое число. Попробуй еще раз!";
            }
        }

        function disableInput() {
            document.getElementById('guessInput').disabled = true;
            document.querySelector('button').disabled = true;
        }
    </script>
</body>
</html>

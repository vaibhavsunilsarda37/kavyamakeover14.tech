<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: 'Arial', sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    .container {
      text-align: center;
      background-color: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }

    button {
      padding: 10px;
      margin-top: 10px;
      cursor: pointer;
    }

    button:hover {
      background-color: #3498db;
      color: #fff;
    }
  </style>
  <title>Guess the Number Game</title>
</head>
<body>
  <div class="container">
    <h1>Guess the Number!</h1>
    <p id="message">Enter a number between 1 and 10</p>
    <input type="number" id="guessInput" placeholder="Enter your guess">
    <button onclick="checkGuess()">Submit Guess</button>
  </div>
  <script>
    const secretNumber = Math.floor(Math.random() * 10) + 1;
    let attempts = 0;

    function checkGuess() {
      const userGuess = parseInt(document.getElementById('guessInput').value);

      if (isNaN(userGuess) || userGuess < 1 || userGuess > 10) {
        setMessage('Please enter a valid number between 1 and 10');
        return;
      }

      attempts++;

      if (userGuess === secretNumber) {
        setMessage(`Congratulations! You guessed the correct number in ${attempts} attempts.`);
      } else {
        const hint = userGuess > secretNumber ? 'Too high!' : 'Too low!';
        setMessage(`Incorrect! ${hint} Try again.`);
      }
    }

    function setMessage(message) {
      document.getElementById('message').textContent = message;
    }
  </script>
</body>
</html>

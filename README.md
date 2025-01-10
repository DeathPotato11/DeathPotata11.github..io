<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Random Character Sheet Generator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        #container {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        #welcomeText {
            margin-bottom: 20px;
        }
        .dice {
            width: 50px;
            height: 50px;
            position: absolute;
            top: 50%;
            left: 0;
            transform: translateY(-50%);
            background-image: url('https://example.com/d4.png'); /* Placeholder for D4 dice image */
            background-size: cover;
            animation: rollDice 2s linear forwards;
        }
        @keyframes rollDice {
            0% {
                left: 0;
                transform: rotate(0deg);
            }
            100% {
                left: 100%;
                transform: rotate(720deg);
            }
        }
    </style>
</head>
<body>
    <div id="container">
        <h1>Random Character Sheet Generator</h1>
        <p id="welcomeText">Welcome to a little bit of chaos! This website will create a random character for you. Whether it's for DND, your book, artwork ideas, or just fun!</p>
        <button id="startButton">Let's START!</button>
        <div id="characterSheet" style="display: none; margin-top: 20px;"></div>
    </div>
    
    <script>
        document.getElementById('startButton').addEventListener('click', function() {
            document.body.innerHTML = `
                <div id="container">
                    <h1>Random Character Sheet Generator</h1>
                    <button id="rollButton">Roll D4</button>
                    <div id="resultText" style="margin-top: 20px;"></div>
                </div>
            `;

            document.getElementById('rollButton').addEventListener('click', function() {
                const dice = document.createElement('div');
                dice.className = 'dice';
                document.body.appendChild(dice);
                setTimeout(() => {
                    dice.remove();
                    const rollResult = Math.floor(Math.random() * 4) + 1;
                    const resultText = document.getElementById('resultText');
                    if (rollResult % 2 === 0) {
                        resultText.innerText = 'You rolled a ' + rollResult + '! Your character is a male.';
                    } else {
                        resultText.innerText = 'You rolled a ' + rollResult + '! Your character is female.';
                    }
                }, 2000);
            });
        });
    </script>
</body>
</html>

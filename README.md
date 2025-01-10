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
    </style>
</head>
<body>
    <div id="container">
        <h1>Random Character Sheet Generator</h1>
        <p id="welcomeText">Welcome to a little bit of chaos! This website will create a random character for you. Whether it's for DND, your book, artwork ideas, or just fun! You will need a full dice set to play, if you don't have one then you can go online to find a random dice roller!</p>
        <button id="startButton">Let's START!</button>
        <div id="characterSheet" style="display: none; margin-top: 20px;"></div>
    </div>
    
    <script>
        document.getElementById('startButton').addEventListener('click', function() {
            document.body.innerHTML = `
                <div id="container">
                    <h1>Random Character Sheet Generator</h1>
                    <label for="d4Input">Enter your D4 roll:</label>
                    <input type="number" id="d4Input" min="1" max="4">
                    <button id="submitD4">Submit</button>
                    <div id="resultText" style="margin-top: 20px;"></div>
                </div>
            `;

            document.getElementById('submitD4').addEventListener('click', function() {
                const rollResult = parseInt(document.getElementById('d4Input').value);
                const resultText = document.getElementById('resultText');
                if (isNaN(rollResult) || rollResult < 1 || rollResult > 4) {
                    resultText.innerText = 'Please enter a valid number between 1 and 4.';
                    return;
                }
                if (rollResult === 1 || rollResult === 3) {
                    resultText.innerText = 'You entered ' + rollResult + '! Your character is a male.';
                } else if (rollResult === 2 || rollResult === 4) {
                    resultText.innerText = 'You entered ' + rollResult + '! Your character is a female.';
                }
                setTimeout(() => {
                    const d100Input = document.createElement('div');
                    d100Input.innerHTML = `
                        <label for="d100Input">Enter your D100 roll:</label>
                        <input type="number" id="d100Input" min="1" max="100">
                        <button id="submitD100">Submit</button>
                    `;
                    document.getElementById('container').appendChild(d100Input);

                    document.getElementById('submitD100').addEventListener('click', function() {
                        const d100Result = parseInt(document.getElementById('d100Input').value);
                        if (isNaN(d100Result) || d100Result < 1 || d100Result > 100) {
                            alert('Please enter a valid number between 1 and 100.');
                        } else {
                            alert('You entered ' + d100Result + ' on the D100!');
                        }
                    });
                }, 3000);
            });
        });
    </script>
</body>
</html>

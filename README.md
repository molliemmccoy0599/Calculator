# Calculator
My Puffy pink and blue calculator 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <style>
        body {
            margin: 0;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(to bottom right, rgba(255, 0, 255, 0.1), rgba(147, 197, 253, 0.1));
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }

        .calculator {
            padding: 1.5rem;
            background: linear-gradient(to bottom right, rgba(255, 192, 255, 0.5), rgb(239, 246, 255));
            max-width: 320px;
            border-radius: 1.5rem;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
            border: 2px solid white;
        }

        .display {
            margin-bottom: 1.5rem;
            padding: 1rem;
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(4px);
            border-radius: 1rem;
            text-align: right;
            font-size: 2.25rem;
            font-weight: 300;
            min-height: 4rem;
            display: flex;
            align-items: center;
            justify-content: flex-end;
            box-shadow: inset 0 2px 4px 0 rgba(0, 0, 0, 0.1);
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1rem;
        }

        .btn {
            width: 3.5rem;
            height: 3.5rem;
            border-radius: 9999px;
            border: 2px solid white;
            font-size: 1.25rem;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.2s;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }

        .btn:hover {
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
            transform: translateY(-1px);
        }

        .btn:active {
            box-shadow: 0 2px 4px -1px rgba(0, 0, 0, 0.1);
            transform: translateY(0);
        }

        .btn-number {
            background: linear-gradient(to bottom, white, #ffe6f9);
            color: #ff1493; /* Hot pink */
        }

        .btn-number:hover {
            background: linear-gradient(to bottom, #ffe6f9, #ffccf3);
        }

        .btn-operator {
            background: linear-gradient(to bottom, white, rgb(239, 246, 255));
            color: rgb(59, 130, 246);
        }

        .btn-operator:hover {
            background: linear-gradient(to bottom, rgb(239, 246, 255), rgb(219, 234, 254));
        }

        .btn-clear {
            background: linear-gradient(to bottom, white, #ffb6e6);
            color: #ff1493; /* Hot pink */
        }

        .btn-clear:hover {
            background: linear-gradient(to bottom, #ffb6e6, #ff99dd);
        }

        .btn-zero {
            grid-column: span 2;
            width: 100%;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button class="btn btn-clear" onclick="clearDisplay()">AC</button>
            <button class="btn btn-operator">±</button>
            <button class="btn btn-operator" onclick="handleOperation('%')">%</button>
            <button class="btn btn-operator" onclick="handleOperation('÷')">÷</button>

            <button class="btn btn-number" onclick="handleNumber('7')">7</button>
            <button class="btn btn-number" onclick="handleNumber('8')">8</button>
            <button class="btn btn-number" onclick="handleNumber('9')">9</button>
            <button class="btn btn-operator" onclick="handleOperation('×')">×</button>

            <button class="btn btn-number" onclick="handleNumber('4')">4</button>
            <button class="btn btn-number" onclick="handleNumber('5')">5</button>
            <button class="btn btn-number" onclick="handleNumber('6')">6</button>
            <button class="btn btn-operator" onclick="handleOperation('-')">-</button>

            <button class="btn btn-number" onclick="handleNumber('1')">1</button>
            <button class="btn btn-number" onclick="handleNumber('2')">2</button>
            <button class="btn btn-number" onclick="handleNumber('3')">3</button>
            <button class="btn btn-operator" onclick="handleOperation('+')">+</button>

            <button class="btn btn-number btn-zero" onclick="handleNumber('0')">0</button>
            <button class="btn btn-number" onclick="handleNumber('.')">.</button>
            <button class="btn btn-operator" onclick="handleEqual()">=</button>
        </div>
    </div>

    <script>
        let display = '0';
        let firstNumber = null;
        let operation = null;
        let newNumber = true;

        const displayElement = document.getElementById('display');

        function updateDisplay() {
            displayElement.textContent = display;
        }

        function handleNumber(number) {
            if (newNumber) {
                display = number;
                newNumber = false;
            } else {
                display = display === '0' ? number : display + number;
            }
            updateDisplay();
        }

        function handleOperation(op) {
            firstNumber = parseFloat(display);
            operation = op;
            newNumber = true;
        }

        function handleEqual() {
            const secondNumber = parseFloat(display);
            let result;

            switch (operation) {
                case '+':
                    result = firstNumber + secondNumber;
                    break;
                case '-':
                    result = firstNumber - secondNumber;
                    break;
                case '×':
                    result = firstNumber * secondNumber;
                    break;
                case '÷':
                    result = firstNumber / secondNumber;
                    break;
                case '%':
                    result = firstNumber * (secondNumber / 100);
                    break;
                default:
                    return;
            }

            display = result.toString();
            firstNumber = null;
            operation = null;
            newNumber = true;
            updateDisplay();
        }

        function clearDisplay() {
            display = '0';
            firstNumber = null;
            operation = null;
            newNumber = true;
            updateDisplay();
        }
    </script>
</body>
</html>


https://github.com/user-attachments/assets/bcf13282-d47d-4b06-93c3-c1ad2b120115

## Overview

## Users

## Learnings


## Overview

## User

## Learnings 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        .calculator {
            border: 1px solid #333;
            padding: 10px;
            border-radius: 10px;
            background-color: #fff;
        }
        .display {
            width: 100%;
            height: 50px;
            background-color: #e0e0e0;
            text-align: right;
            padding: 10px;
            font-size: 2em;
            border-radius: 5px;
            margin-bottom: 10px;
            box-sizing: border-box;
        }
        table {
            border-collapse: collapse;
            width: 100%;
        }
        td {
            border: 1px solid #333;
            text-align: center;
            vertical-align: middle;
            font-size: 1.5em;
            width: 25%;
            height: 60px;
            cursor: pointer;
        }
        td.operator {
            background-color: #f9a825;
        }
        td.equal {
            background-color: #4caf50;
        }
        td.clear {
            background-color: #f44336;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <table>
            <tr>
                <td class="clear" colspan="2" onclick="clearDisplay()">C</td>
                <td class="operator" onclick="inputOperator('/')">/</td>
                <td class="operator" onclick="inputOperator('*')">*</td>
            </tr>
            <tr>
                <td onclick="inputDigit(7)">7</td>
                <td onclick="inputDigit(8)">8</td>
                <td onclick="inputDigit(9)">9</td>
                <td class="operator" onclick="inputOperator('-')">-</td>
            </tr>
            <tr>
                <td onclick="inputDigit(4)">4</td>
                <td onclick="inputDigit(5)">5</td>
                <td onclick="inputDigit(6)">6</td>
                <td class="operator" onclick="inputOperator('+')">+</td>
            </tr>
            <tr>
                <td onclick="inputDigit(1)">1</td>
                <td onclick="inputDigit(2)">2</td>
                <td onclick="inputDigit(3)">3</td>
                <td class="equal" rowspan="2" onclick="calculateResult()">=</td>
            </tr>
            <tr>
                <td colspan="2" onclick="inputDigit(0)">0</td>
                <td onclick="inputDecimal()">.</td>
            </tr>
        </table>
    </div>
    <script src="script.js"></script>
</body>
</html>

let displayElement = document.getElementById('display');
let currentInput = '';
let operator = null;
let previousInput = '';

function updateDisplay() {
    displayElement.textContent = currentInput || '0';
}

function clearDisplay() {
    currentInput = '';
    operator = null;
    previousInput = '';
    updateDisplay();
}

function inputDigit(digit) {
    if (currentInput.includes('.') && digit === '.') return;
    currentInput += digit;
    updateDisplay();
}

function inputOperator(op) {
    if (currentInput === '') return;
    if (operator !== null) calculateResult();
    previousInput = currentInput;
    operator = op;
    currentInput = '';
}

function inputDecimal() {
    if (currentInput.includes('.')) return;
    currentInput += '.';
    updateDisplay();
}

function calculateResult() {
    if (operator === null || currentInput === '') return;
    let result;
    const prev = parseFloat(previousInput);
    const current = parseFloat(currentInput);
    switch (operator) {
        case '+':
            result = prev + current;
            break;
        case '-':
            result = prev - current;
            break;
        case '*':
            result = prev * current;
            break;
        case '/':
            result = prev / current;
            break;
        default:
            return;
    }
    currentInput = result.toString();
    operator = null;
    previousInput = '';
    updateDisplay();
}

updateDisplay();

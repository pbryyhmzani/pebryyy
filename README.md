<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Kalkulator Modern</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- CSS -->
    <style>
        * {
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, sans-serif;
        }

        body {
            background:goldenrod;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 25px;
            padding: 20px;
            color: #333;
        }

        .calculator {
            background: #ffffff;
            width: 300px;
            padding: 20px;
            border-radius: 16px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }

        .calculator h2 {
            text-align: center;
            margin-bottom: 15px;
        }

        #display {
            width: 100%;
            height: 55px;
            font-size: 24px;
            text-align: right;
            padding: 10px;
            border-radius: 8px;
            border: 1px solid #ddd;
            margin-bottom: 15px;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        button {
            height: 50px;
            font-size: 18px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            background: #f1f1f1;
            transition: all 0.2s ease;
        }

        button:hover {
            background: #dcdcdc;
        }

        .operator {
            background: #667eea;
            color: #ffffff;
        }

        .operator:hover {
            background: #5a6fd8;
        }

        .equals {
            background: #2ecc71;
            color: white;
        }

        .equals:hover {
            background: #27ae60;
        }

        .clear {
            grid-column: span 4;
            background: red;
            color: white;
        }

        .clear:hover {
            background: #c0392b;
        }

        .history {
            background: #ffffff;
            width: 280px;
            padding: 15px;
            border-radius: 16px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }

        .history h3 {
            text-align: center;
            margin-bottom: 10px;
        }

        .history ul {
            list-style: none;
            padding: 0;
            max-height: 250px;
            overflow-y: auto;
        }

        .history li {
            padding: 6px 0;
            border-bottom: 1px solid #eee;
            font-size: 14px;
        }

        .clear-history {
            width: 100%;
            margin-top: 10px;
            height: 40px;
            border-radius: 8px;
            border: none;
            background: #e74c3c;
            color: white;
            cursor: pointer;
        }

        .clear-history:hover {
            background: #c0392b;
        }
    </style>
</head>
<body>

    <!-- Kalkulator -->
    <div class="calculator">
        <h2>Kalkulator</h2>
        <input type="text" id="display" readonly>

        <div class="buttons">
            <button onclick="appendValue('7')">7</button>
            <button onclick="appendValue('8')">8</button>
            <button onclick="appendValue('9')">9</button>
            <button class="operator" onclick="appendValue('/')">÷</button>

            <button onclick="appendValue('4')">4</button>
            <button onclick="appendValue('5')">5</button>
            <button onclick="appendValue('6')">6</button>
            <button class="operator" onclick="appendValue('*')">×</button>

            <button onclick="appendValue('1')">1</button>
            <button onclick="appendValue('2')">2</button>
            <button onclick="appendValue('3')">3</button>
            <button class="operator" onclick="appendValue('-')">−</button>

            <button onclick="appendValue('0')">0</button>
            <button onclick="backspace()">⌫</button>
            <button class="equals" onclick="calculate()">=</button>
            <button class="operator" onclick="appendValue('+')">+</button>

            <button class="clear" onclick="clearDisplay()">C</button>
        </div>
    </div>

    <!-- Histori -->
    <div class="history">
        <h3>Calculation History</h3>
        <ul id="historyList"></ul>
        <button class="clear-history" onclick="clearHistory()">Delete Histori</button>
    </div>

    <!-- JavaScript -->
    <script>
        const display = document.getElementById('display');
        const historyList = document.getElementById('historyList');

        function appendValue(value) {
            display.value += value;
        }

        function clearDisplay() {
            display.value = '';
        }

        function backspace() {
            display.value = display.value.slice(0, -1);
        }

        function calculate() {
            try {
                const expression = display.value;
                console.log(expression)
                const result = eval(expression);
                console.log(result)


                display.value = result;

                const li = document.createElement('li');
                li.textContent = history ${expression} = ${result};
                historyList.prepend(li);
                console.log(historyList)
            } catch (error) {
                display.value = 'Error';
            }
        }

        function clearHistory() {
            historyList.innerHTML = '';
        }
    </script>

</body>
</html>

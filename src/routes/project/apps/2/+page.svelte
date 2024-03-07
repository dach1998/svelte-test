<script>
    let displayValue = '0';
    let firstOperand = null;
    let operator = null;
    let awaitingNextOperand = false;

    function inputDigit(digit) {
        if (awaitingNextOperand) {
            displayValue = digit;
            awaitingNextOperand = false;
        } else {
            displayValue = displayValue === '0' ? digit : displayValue + digit;
        }
    }

    function inputDecimal() {
        if (!displayValue.includes('.')) {
            displayValue += '.';
        }
    }

    function performOperation(nextOperator) {
        const inputValue = parseFloat(displayValue);
        if (firstOperand === null) {
            firstOperand = inputValue;
        } else if (operator) {
            const result = calculate(firstOperand, inputValue, operator);
            displayValue = String(result);
            firstOperand = result;
        }
        awaitingNextOperand = true;
        operator = nextOperator;
    }

    function calculate(firstOperand, secondOperand, operator) {
        switch (operator) {
            case '+':
                return firstOperand + secondOperand;
            case '-':
                return firstOperand - secondOperand;
            case '*':
                return firstOperand * secondOperand;
            case '/':
                return firstOperand / secondOperand;
            default:
                return secondOperand;
        }
    }

    function resetCalculator() {
        displayValue = '0';
        firstOperand = null;
        operator = null;
        awaitingNextOperand = false;
    }
</script>

<main>
    <h1>Калькулятор</h1>
    <div class="calculator">
        <div class="display">{displayValue}</div>
        <div class="buttons">
            <button class="digit" on:click={() => inputDigit('7')}>7</button>
            <button class="digit" on:click={() => inputDigit('8')}>8</button>
            <button class="digit" on:click={() => inputDigit('9')}>9</button>
            <button class="digit" on:click={() => inputDigit('4')}>4</button>
            <button class="digit" on:click={() => inputDigit('5')}>5</button>
            <button class="digit" on:click={() => inputDigit('6')}>6</button>
            <button class="digit" on:click={() => inputDigit('1')}>1</button>
            <button class="digit" on:click={() => inputDigit('2')}>2</button>
            <button class="digit" on:click={() => inputDigit('3')}>3</button>
            <button class="zero digit" on:click={() => inputDigit('0')}>0</button>
            <button class="digit" on:click={inputDecimal}>.</button>
            <button class="operator" on:click={() => performOperation('+')}>+</button>
            <button class="operator" on:click={() => performOperation('-')}>-</button>
            <button class="operator" on:click={() => performOperation('*')}>*</button>
            <button class="operator" on:click={() => performOperation('/')}>/</button>
            <button class="equals" on:click={() => performOperation('=')}>=</button>
            <button class="clear" on:click={resetCalculator}>C</button>
        </div>
    </div>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 20px;
    }

    .calculator {
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 10px;
        width: 300px; /* ширина калькулятора */
    }

    .display {
        background-color: #f0f0f0;
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 10px;
        margin-bottom: 10px;
        text-align: right;
        font-size: 24px;
    }

    .buttons {
        display: grid;
        grid-template-columns: repeat(4, 1fr); /* 4 колонки */
        gap: 5px;
    }

    .buttons button {
        padding: 10px;
        font-size: 20px;
        border: none;
        border-radius: 5px;
        background-color: #e0e0e0;
        cursor: pointer;
    }

    .digit,
    .operator,
    .equals,
    .clear {
        transition: background-color 0.3s;
    }

    .digit:hover,
    .operator:hover,
    .equals:hover,
    .clear:hover {
        background-color: #d0d0d0;
    }

    .zero {
        grid-column: span 2; /* широкая кнопка */
    }

    .equals,
    .clear {
        grid-column: span 4; /* кнопки "равно" и "сброс" занимают всю ширину */
    }
</style>

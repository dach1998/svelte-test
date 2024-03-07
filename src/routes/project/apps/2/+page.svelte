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
            <button on:click={() => inputDigit('7')}>7</button>
            <button on:click={() => inputDigit('8')}>8</button>
            <button on:click={() => inputDigit('9')}>9</button>
            <button on:click={() => inputDigit('4')}>4</button>
            <button on:click={() => inputDigit('5')}>5</button>
            <button on:click={() => inputDigit('6')}>6</button>
            <button on:click={() => inputDigit('1')}>1</button>
            <button on:click={() => inputDigit('2')}>2</button>
            <button on:click={() => inputDigit('3')}>3</button>
            <button on:click={() => inputDigit('0')}>0</button>
            <button on:click={inputDecimal}>.</button>
            <button on:click={() => performOperation('+')}>+</button>
            <button on:click={() => performOperation('-')}>-</button>
            <button on:click={() => performOperation('*')}>*</button>
            <button on:click={() => performOperation('/')}>/</button>
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
        grid-template-columns: repeat(3, 1fr);
        gap: 5px;
    }

    .buttons button {
        padding: 10px;
        font-size: 20px;
    }

    .buttons button.zero {
        grid-column: span 2;
    }

    .equals,
    .clear {
        grid-column: span 3;
    }
</style>


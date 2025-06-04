<script>
	let display = '0';
	let current = '';
	let operator = '';
	let previous = '';
	let result = null;

	function press(key) {
		if ('0123456789.'.includes(key)) {
			if (key === '.' && current.includes('.')) return;
			current += key;
			display = current;
		} else if ('+-*/'.includes(key)) {
			if (current === '') return;
			operator = key;
			previous = current;
			current = '';
		} else if (key === 'C') {
			current = '';
			previous = '';
			operator = '';
			result = null;
			display = '0';
		} else if (key === '±') {
			if (current) {
				current = (parseFloat(current) * -1).toString();
				display = current;
			}
		} else if (key === '%') {
			if (current) {
				current = (parseFloat(current) / 100).toString();
				display = current;
			}
		} else if (key === '=') {
			if (!current || !previous || !operator) return;

			const a = parseFloat(previous);
			const b = parseFloat(current);

			switch (operator) {
				case '+': result = a + b; break;
				case '-': result = a - b; break;
				case '*': result = a * b; break;
				case '/': result = b === 0 ? 'Erro' : a / b; break;
			}

			display = result.toString();
			current = display;
			previous = '';
			operator = '';
		}
	}
</script>

<style>
	.calculator {
		max-width: 320px;
		margin: 2rem auto;
		background: #222;
		border-radius: 20px;
		overflow: hidden;
		box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
	}

	.screen {
		background: black;
		color: white;
		font-size: 2rem;
		padding: 1rem;
		text-align: right;
		min-height: 60px;
	}

	.buttons {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 1px;
	}

	button {
		font-size: 1.5rem;
		padding: 1.2rem;
		border: none;
		background: #333;
		color: white;
		cursor: pointer;
	}

	button.operator {
		background: orange;
		color: white;
	}

	button.function {
		background: #555;
		color: white;
	}

	button.zero {
		grid-column: span 2;
	}

	button:active {
		background: #666;
	}
</style>

<div class="calculator">
	<div class="screen">{display}</div>
	<div class="buttons">
		<button class="function" onclick={() => press('C')}>C</button>
		<button class="function" onclick={() => press('±')}>±</button>
		<button class="function" onclick={() => press('%')}>%</button>
		<button class="operator" onclick={() => press('/')}>÷</button>

		<button onclick={() => press('7')}>7</button>
		<button onclick={() => press('8')}>8</button>
		<button onclick={() => press('9')}>9</button>
		<button class="operator" onclick={() => press('*')}>×</button>

		<button onclick={() => press('4')}>4</button>
		<button onclick={() => press('5')}>5</button>
		<button onclick={() => press('6')}>6</button>
		<button class="operator" onclick={() => press('-')}>−</button>

		<button onclick={() => press('1')}>1</button>
		<button onclick={() => press('2')}>2</button>
		<button onclick={() => press('3')}>3</button>
		<button class="operator" onclick={() => press('+')}>+</button>

		<button class="zero" onclick={() => press('0')}>0</button>
		<button onclick={() => press('.')}>.</button>
		<button class="operator" onclick={() => press('=')}>=</button>
	</div>
</div>

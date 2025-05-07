<script>
    
    let fibonacciNumbers = [0, 1]; 
    let month = 0; 
    let btmes = 0; 

   
    function updateFibonacci() {
        while (fibonacciNumbers.length <= btmes) {
            let last = fibonacciNumbers[fibonacciNumbers.length - 1];
            let secondLast = fibonacciNumbers[fibonacciNumbers.length - 2];
            fibonacciNumbers.push(last + secondLast); 
        }
    }

    
    function proximomes() {
        month++; 
        btmes = month; 
        updateFibonacci(); 
    }

    
    function mesanterior() {
        if (month > 0) {
            month--; 
            btmes = month; 
            updateFibonacci(); 
        }
    }

  
    function botao(event) {
        btmes = parseInt(event.target.value, 10);
        month = btmes; 
        updateFibonacci(); 
    }
</script>

<h1>Os coelhos de Fibonacci</h1>


<p>
    Mês: <input type="number" min="0" bind:value={btmes} on:input={botao} />
</p>


<p>
    Após {month} meses, haverá {fibonacciNumbers[month]} ninhadas de coelhos!
</p>
<p>
    <button on:click={mesanterior} disable = {month === 0}>Mês anterior</button>
    <button on:click={proximomes}>Próximo mês</button>
</p>

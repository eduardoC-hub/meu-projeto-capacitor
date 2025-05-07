<script>
    let tempo = '';
    let unidade = 'segundos';
    let resultado = '';

    function converter() {
        let valor = parseFloat(tempo);
        if (isNaN(valor)) {
            resultado = 'Por favor, insira um número válido.';
            return;
        }
        
        switch (unidade) {
            case 'milissegundos':
                resultado = `${valor} ms = ${(valor / 1000).toFixed(2)} s = ${(valor / 60000).toFixed(2)} min = ${(valor / 3600000).toFixed(2)} h`;
                break;
            case 'segundos':
                resultado = `${valor} s = ${(valor / 60).toFixed(2)} min = ${(valor / 3600).toFixed(2)} h = ${(valor * 1000).toFixed(2)} ms`;
                break;
            case 'minutos':
                resultado = `${valor} min = ${(valor * 60).toFixed(2)} s = ${(valor / 60).toFixed(2)} h = ${(valor * 60000).toFixed(2)} ms`;
                break;
            case 'horas':
                resultado = `${valor} h = ${(valor * 60).toFixed(2)} min = ${(valor * 3600).toFixed(2)} s = ${(valor * 3600000).toFixed(2)} ms`;
                break;
        }
    }
</script>

<main>
    <div class="container">
        <h2>Conversor de Tempo</h2>
        <div class="input-group">
            <input type="number" bind:value={tempo} placeholder="Digite o tempo" class="input-field">
            <select bind:value={unidade} class="select-field">
                <option value="milissegundos">Milissegundos</option>
                <option value="segundos">Segundos</option>
                <option value="minutos">Minutos</option>
                <option value="horas">Horas</option>
            </select>
        </div>
        <button on:click={converter} class="convert-btn">Converter</button>
        {#if resultado}
            <h3 class="resultado">{resultado}</h3>
        {/if}
        <br>
        <br>
        <a href="/paginas/aba">
            <button class="styled-button">voltar</button>
          </a>
    </div>
   
</main>

<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
        font-family: Arial, sans-serif;
    }
    .styled-button {
    width: 250px;
    max-width: 100%;
    padding: 16px;
    margin: 12px 0;
    font-size: 18px;
    color: white;
    background-color: #007bff;
    border: none;
    border-radius: 50px;
    box-shadow: 0 4px 10px rgba(0, 123, 255, 0.3);
    cursor: pointer;
    transition: transform 0.2s, background-color 0.3s ease;
  }
  
  /* Efeito de hover nos botões */
  .styled-button:hover {
    background-color: #0056b3;
    transform: translateY(-3px);
  }
    main {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        background-color: #f4f4f4;
    }

    .container {
        text-align: center;
        background-color: #ffffff;
        border-radius: 8px;
        padding: 30px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        max-width: 400px;
        width: 100%;
    }

    h2 {
        color: #333;
        margin-bottom: 20px;
        font-size: 24px;
    }

    .input-group {
        margin-bottom: 20px;
    }

    .input-field, .select-field {
        width: 100%;
        padding: 12px;
        font-size: 16px;
        margin: 8px 0;
        border: 1px solid #ddd;
        border-radius: 4px;
        outline: none;
    }

    .input-field:focus, .select-field:focus {
        border-color: #007bff;
        box-shadow: 0 0 5px rgba(0, 123, 255, 0.3);
    }

    .convert-btn {
        background-color: #007bff;
        color: white;
        border: none;
        padding: 15px;
        width: 100%;
        border-radius: 4px;
        font-size: 18px;
        cursor: pointer;
        transition: background-color 0.3s;
    }

    .convert-btn:hover {
        background-color: #0056b3;
    }

    .resultado {
        color: #333;
        margin-top: 20px;
        font-size: 18px;
        font-weight: bold;
    }
</style>
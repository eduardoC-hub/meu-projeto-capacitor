<script>
    let m = 0;
    let km = 0;
    let mm = 0;
    let cm = 0;

    function metros() {
        cm = m * 100;
        mm = m * 1000;
        km = m / 1000;
    }

    function centimetros() {
        m = cm / 100;
        mm = cm * 10;
        km = cm / 100000;
    }

    function milimetros() {
        m = mm / 1000;
        km = mm / 1000000;
        cm = mm / 10;
    }

    function quilometros() {
        m = km * 1000;
        cm = km * 100000;
        mm = km * 1000000;
    }
</script>

<main>
    <div class="container">
        <h1>Conversor de Distância</h1>
        <div class="input-group">
            <div class="input-box">
                <label for="mm">Milímetros:</label>
                <input type="number" bind:value={mm} on:input={milimetros} id="mm" class="input-field" placeholder="Digite em milímetros">
            </div>
            <div class="input-box">
                <label for="cm">Centímetros:</label>
                <input type="number" bind:value={cm} on:input={centimetros} id="cm" class="input-field" placeholder="Digite em centímetros">
            </div>
            <div class="input-box">
                <label for="m">Metros:</label>
                <input type="number" bind:value={m} on:input={metros} id="m" class="input-field" placeholder="Digite em metros">
            </div>
            <div class="input-box">
                <label for="km">Quilômetros:</label>
                <input type="number" bind:value={km} on:input={quilometros} id="km" class="input-field" placeholder="Digite em quilômetros">
            </div>
        </div>
        <a href="/paginas/aba">
            <button class="styled-button">voltar</button>
          </a>
    </div>
    
</main>

<style>
    * {
        box-sizing: border-box;
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
        height: 100vh;
    }

    .container {
        background-color: #fff;
        padding: 30px;
        border-radius: 8px;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        width: 100%;
        max-width: 500px;
        text-align: center;
    }

    h1 {
        font-size: 28px;
        color: #333;
        margin-bottom: 20px;
    }

    .input-group {
        display: flex;
        flex-direction: column;
        gap: 15px;
    }

    .input-box {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    label {
        font-size: 18px;
        color: #333;
        margin-bottom: 5px;
    }

    .input-field {
        width: 250px;
        padding: 10px;
        font-size: 16px;
        border: 1px solid #ddd;
        border-radius: 4px;
        outline: none;
        margin-bottom: 10px;
        transition: border-color 0.3s;
    }

    .input-field:focus {
        border-color: #007bff;
    }

    .input-field::placeholder {
        color: #aaa;
    }

    .input-box input[type="number"] {
        text-align: center;
    }
</style>

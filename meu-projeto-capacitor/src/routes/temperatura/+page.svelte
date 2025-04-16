<script>
    let celsius = 0;
    let fahrenheit = 0;
    let kelvin = 0;

    function Celsius() {
        fahrenheit = celsius * 1.8 + 32;
        kelvin = celsius + 273.15;
    }

    function Fahrenheit() {
        celsius = (fahrenheit - 32) * 5 / 9;
        kelvin = (fahrenheit - 32) * 5 / 9 + 273.15;
    }

    function Kelvin() {
        celsius = kelvin - 273.15;
        fahrenheit = (kelvin - 273.15) * 9 / 5 + 32;
    }
</script>

<main>
    <div class="container">
        <h1>Conversor de Temperatura</h1>
        
        <div class="input-group">
            <label for="celsius">Celsius:</label>
            <input type="number" id="celsius" bind:value={celsius} oninput={Celsius} class="input-field" />
        </div>
        
        <hr />
        
        <div class="input-group">
            <label for="fahrenheit">Fahrenheit:</label>
            <input type="number" id="fahrenheit" bind:value={fahrenheit} oninput={Fahrenheit} class="input-field" />
        </div>

        <hr />
        
        <div class="input-group">
            <label for="kelvin">Kelvin:</label>
            <input type="number" id="kelvin" bind:value={kelvin} oninput={Kelvin} class="input-field" />
        </div>
        <a href="http://localhost:5173/aba">
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
        box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        width: 100%;
        max-width: 400px;
        text-align: center;
    }

    h1 {
        font-size: 32px;
        color: #333;
        margin-bottom: 20px;
    }

    .input-group {
        margin-bottom: 20px;
    }

    label {
        font-size: 18px;
        color: #333;
        display: block;
        margin-bottom: 10px;
    }

    .input-field {
        width: 100%;
        padding: 12px;
        font-size: 16px;
        border: 1px solid #ddd;
        border-radius: 4px;
        outline: none;
        transition: border-color 0.3s ease-in-out;
    }

    .input-field:focus {
        border-color: #007bff;
        box-shadow: 0 0 5px rgba(0, 123, 255, 0.3);
    }

    hr {
        border: 0;
        border-top: 1px solid #ddd;
        margin: 20px 0;
    }
</style>

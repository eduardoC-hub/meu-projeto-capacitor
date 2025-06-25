<script>
    let diceSides = 6;
    let numDice = 1;
    let results = [];
  
    function rollDice() {
      results = Array.from({ length: numDice }, () =>
        Math.floor(Math.random() * diceSides) + 1
      );
    }
  </script>
  
  <main class="app">
    <h1>🎲 Rolagem de Dados</h1>
  
    <div class="controls">
      <label>
        Número de lados:
        <input type="number" bind:value={diceSides} min="2" />
      </label>
  
      <label>
        Quantidade de dados (1 a 6):
        <input type="number" bind:value={numDice} min="1" max="6" />
      </label>
    </div>
  
    <button onclick={rollDice}>Rolar Dados</button>
  
    {#if results.length}
      <div class="results">
        <h2>Resultados:</h2>
        <div class="dice-list">
          {#each results as result, i}
            <div class="dice">🎲 {result}</div>
          {/each}
        </div>
      </div>
    {/if}
  </main>
  
  <style>
    .app {
      max-width: 500px;
      margin: 50px auto;
      padding: 2rem;
      font-family: sans-serif;
      background-color: #fafafa;
      border-radius: 1rem;
      text-align: center;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    }
  
    .controls {
      display: flex;
      flex-direction: column;
      gap: 1rem;
      margin-bottom: 1rem;
    }
  
    input {
      margin-top: 0.3rem;
      padding: 0.4rem;
      width: 100px;
      font-size: 1rem;
    }
  
    button {
      margin-top: 1rem;
      padding: 0.5rem 1.5rem;
      font-size: 1.2rem;
      background-color: #0070f3;
      color: white;
      border: none;
      border-radius: 0.5rem;
      cursor: pointer;
    }
  
    button:hover {
      background-color: #005ecb;
    }
  
    .results {
      margin-top: 2rem;
    }
  
    .dice-list {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 1rem;
    }
  
    .dice {
      background-color: #ffffff;
      padding: 1rem;
      font-size: 1.5rem;
      border: 2px solid #0070f3;
      border-radius: 0.5rem;
      width: 60px;
      height: 60px;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  </style>
  
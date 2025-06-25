<script>
    import { onMount } from "svelte";
  
    const prizes = [
      "Bicicleta",
      "Video Game",
      "Boneca",
      "Carrinho",
      "Kit Escolar",
      "Doce",
      "Nada 😢",
      "Tablet"
    ];
  
    let spinning = false;
    let rotation = 0;
    let selectedPrize = "";
  
    function spinWheel() {
      if (spinning) return;
  
      spinning = true;
      selectedPrize = "";
  
      // Gira entre 3 a 6 voltas completas (360° por volta)
      const extraRotation = 360 * (3 + Math.floor(Math.random() * 4));
      // Sorteia qual fatia a roleta deve parar
      const prizeIndex = Math.floor(Math.random() * prizes.length);
      const degreesPerPrize = 360 / prizes.length;
      const stopAngle = prizeIndex * degreesPerPrize + degreesPerPrize / 2;
  
      const totalRotation = extraRotation + (360 - stopAngle);
  
      rotation += totalRotation;
  
      setTimeout(() => {
        spinning = false;
        selectedPrize = prizes[prizeIndex];
      }, 4000); // tempo da animação (4s)
    }
  </script>
  
  <main class="app">
    <h1>🎡 Roleta de Prêmios!</h1>
  
    <div class="wheel-container">
      <div
        class="wheel"
        style="transform: rotate({rotation}deg); transition: transform 4s cubic-bezier(0.33, 1, 0.68, 1);"
      >
        {#each prizes as prize, i}
          <div
            class="segment"
            style="transform: rotate({i * (360 / prizes.length)}deg) skewY(-45deg);"
          >
            <span>{prize}</span>
          </div>
        {/each}
      </div>
      <div class="pointer">▼</div>
    </div>
  
    <button onclick={spinWheel} disabled={spinning}>
      {spinning ? "Girando..." : "Girar"}
    </button>
  
    {#if selectedPrize}
      <p class="result">🎉 Você ganhou: <strong>{selectedPrize}</strong>!</p>
    {/if}
    <a href="/paginas/Cassino"><button class ="btn btn-primary">voltar</button></a>
  </main>
  
  <style>
    .app {
      max-width: 600px;
      margin: auto;
      text-align: center;
      font-family: sans-serif;
      padding: 2rem;
    }
  
    .wheel-container {
      position: relative;
      width: 300px;
      height: 300px;
      margin: 2rem auto;
    }
  
    .wheel {
      width: 100%;
      height: 100%;
      border-radius: 50%;
      border: 5px solid #444;
      position: relative;
      overflow: hidden;
      background: rgb(94, 94, 94);
    }
  
    .segment {
      position: absolute;
      width: 50%;
      height: 50%;
      left: 50%;
      top: 0;
      transform-origin: 0% 100%;
      background: hsl(calc(360 * var(--i) / 8), 70%, 60%);
      display: flex;
      align-items: flex-end;
      justify-content: center;
      padding-bottom: 10px;
      color: white;
      font-weight: bold;
      font-size: 0.9rem;
    }
  
    .segment span {
      transform: skewY(45deg) rotate(22.5deg);
    }
  
    .pointer {
      position: absolute;
      top: -20px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 2rem;
      color: red;
    }
  
    button {
      margin-top: 1rem;
      font-size: 1.2rem;
      padding: 0.7rem 2rem;
      background: #0070f3;
      color: white;
      border: none;
      border-radius: 0.7rem;
      cursor: pointer;
    }
  
    button:disabled {
      background: #aaa;
      cursor: not-allowed;
    }
  
    .result {
      font-size: 1.4rem;
      margin-top: 1.5rem;
      color: green;
    }
  </style>
  
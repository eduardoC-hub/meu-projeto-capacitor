
<div class="button-container">

  <a href="/paginas/area">
      <button class="styled-button">converter area</button>
    </a>
    <a href="/paginas/temperatura">
      <button class="styled-button">Converter Temperatura</button>
    </a>
    <a href="/paginas/massa">
      <button class="styled-button">Converter Massa</button>
    </a>
    <a href="/paginas/tempo">
      <button class="styled-button">Converter Tempo</button>
    </a>
    <a href="/paginas/distancia">
      <button class="styled-button">Converter Distância</button>
    </a>
    <a href="/paginas/cotac">
      <button class="styled-button">Converter moedas</button>
    </a>
  </div>

  <style>
  .button-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 750px;
    padding: 20px;
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
  

  .styled-button:hover {
    background-color: #0056b3;
    transform: translateY(-3px);
  }
  
 
  @media (max-width: 600px) {
    .styled-button {
      font-size: 16px;
      padding: 14px;
    }
  }
  
  @media (max-width: 400px) {
    .styled-button {
      font-size: 14px;
    }
  }
    </style>
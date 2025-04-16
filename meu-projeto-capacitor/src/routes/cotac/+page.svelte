<script>
    let moedas = [
        { nome: 'Dólar americano', código: 'USD' },
        { nome: 'Real brasileiro', código: 'BRL' },
        { nome: 'Euro', código: 'EUR' },
        { nome: 'Libra esterlina', código: 'GBP' },
        { nome: 'Iene japonês', código: 'JPY' },
        { nome: 'Peso argentino', código: 'ARS' }
    ];

    let código1 = $state(moedas[0].código);
    let código2 = $state(moedas[1].código);
    let valor1 = $state(0);
    let valor2 = $state(0);
    let moedaPadrao = $state(null);
    let ultimaAtualizacao = $state('');

    async function mudarMoeda() {
        const resposta = await fetch(`https://open.er-api.com/v6/latest/${código1}`);
        const dados = await resposta.json();
        moedaPadrao = dados;
        ultimaAtualizacao = new Date(dados.time_last_update_utc).toLocaleString();
        converterDe();
    }

    function converterDe() {
        if (moedaPadrao && moedaPadrao.rates) {
            valor2 = (valor1 * moedaPadrao.rates[código2]).toFixed(2);
        }
    }

    function converterPara() {
        if (moedaPadrao && moedaPadrao.rates) {
            valor1 = (valor2 / moedaPadrao.rates[código2]).toFixed(2);
        }
    }

    function inverterMoedas() {
        [código1, código2] = [código2, código1];
        [valor1, valor2] = [valor2, valor1];
        mudarMoeda();
    }

    mudarMoeda();
</script>

<style>
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

    
    h1 {
        color: rgb(126, 182, 254);
        text-align: center;
        margin-bottom: 20px;
    }

    .container {
        margin: 100px auto;
        background: #f8f9fa;
        padding: 30px;
        border-radius: 10px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        text-align: center;
        width: 100%;
        max-width: 700px;
    }

    .input-group {
        display: flex;
        justify-content: center;
        gap: 10px;
        margin-bottom: 10px;
    }

    select, input {
        padding: 8px;
        font-size: 16px;
    }

    .btn {
        font-size: 18px;
        padding: 5px 10px;
    }

    p {
        margin-top: 10px;
        font-size: 14px;
        color: #555;
    }

    .footer {
        margin-top: 15px;
        font-size: 12px;
    }
</style>

<div class="container">
    <h1>Cotação de Moedas</h1>
    <div class="input-group">
        <select bind:value={código1} onchange={mudarMoeda}>a
            {#each moedas as moeda}
                <option value={moeda.código} title={moeda.nome}>{moeda.código}</option>
            {/each}
        </select>
        <input type="number" placeholder="0,00" bind:value={valor1} oninput={converterDe} />
        <button class="btn btn-outline-secondary" type="button" onclick={inverterMoedas}>⇄</button>
        <input type="number" placeholder="0,00" bind:value={valor2} oninput={converterPara} />
        <select bind:value={código2} onchange={converterPara}>
            {#each moedas as moeda}
                <option value={moeda.código} title={moeda.nome}>{moeda.código}</option>
            {/each}
        </select>
    </div>
    <a href="http://localhost:5173/aba">
        <button class="styled-button">voltar</button>
      </a>
    </div>


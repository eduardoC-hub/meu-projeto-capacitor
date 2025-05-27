<script>
    let medidas = [
        { nome: 'Quilograma', codigo: 'kg', fator: 1000 },
        { nome: 'Grama', codigo: 'g', fator: 1 },
        { nome: 'Miligrama', codigo: 'mg', fator: 0.001 }
    ];
  
    let codigo1 = 'kg';
    let codigo2 = 'g';
    let valor1 = 0;
    let valor2 = 0;
  
    function converter() {
        let medida1 = medidas.find(m => m.codigo === codigo1);
        let medida2 = medidas.find(m => m.codigo === codigo2);
        if (medida1 && medida2) {
            valor2 = (valor1 * medida1.fator / medida2.fator).toFixed(2);
        }
    }
  
    function inverterMedidas() {
        [codigo1, codigo2] = [codigo2, codigo1];
        converter();
    }
</script>

<main>
    <div class="container">
        <h1>Conversor de Medidas</h1>
        <div class="input-group">
            <div class="input-box">
                <select bind:value={codigo1} onchange={converter} class="select">
                    {#each medidas as medida}
                        <option value={medida.codigo}>{medida.nome}</option>
                    {/each}
                </select>
                <input type="number" bind:value={valor1} oninput={converter} class="input-field" placeholder="Digite o valor" />
            </div>
            
            <button onclick={inverterMedidas} class="invert-btn">⇄</button>
            
            <div class="input-box">
                <input type="number" bind:value={valor2} readonly class="input-field" />
                <select bind:value={codigo2} onchange={converter} class="select">
                    {#each medidas as medida}
                        <option value={medida.codigo}>{medida.nome}</option>
                    {/each}
                </select>
            </div>
        </div>
        <br>
        <a href="/paginas/aba">
            <button class="styled-button">voltar</button>
          </a>
    </div>
 
</main>

<style>
  * {
    box-sizing: border-box;
}

main {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    padding: 10px;
}

.container {
    background-color: #fff;
    padding: 30px;
    border-radius: 8px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    width: 100vh;
    max-width: 600px;
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
    gap: 20px;
    align-items: center;
}

.input-box {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 10px;
    flex-wrap: wrap;
    justify-content: center;
}

.input-field, .select {
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ddd;
    border-radius: 4px;
    outline: none;
    width: 150px;
    text-align: center;
}

.select {
    width: 160px;
}

.input-field:focus, .select:focus {
    border-color: #007bff;
    box-shadow: 0 0 5px rgba(0, 123, 255, 0.3);
}

.invert-btn {
    background-color: #007bff;
    color: white;
    border: none;
    padding: 10px 20px;
    font-size: 20px;
    border-radius: 50%;
    cursor: pointer;
    transition: background-color 0.3s;
}

.invert-btn:hover {
    background-color: #0056b3;
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

/* RESPONSIVO PARA CELULARES */
@media (max-width: 480px) {
    .container {
        padding: 20px;
    }

    h1 {
        font-size: 22px;
    }

    .input-box {
        flex-direction: column;
        gap: 10px;
    }

    .input-field,
    .select {
        width: 100%;
        font-size: 16px;
    }

    .invert-btn {
        padding: 10px;
        font-size: 18px;
    }

    .styled-button {
        font-size: 16px;
        padding: 14px;
    }
}

</style>

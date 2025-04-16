<script>
    let area = $state(0);
    let unidade1 = $state(0);
    let unidade2 = $state(0);
    let resultado = $state(0);

    function converter() {
        if (unidade1 == 'm2') {
            if (unidade2 == 'm2') {
                resultado = area;
            } else if (unidade2 == 'cm2') {
                resultado = area * 10000;
            } else if (unidade2 == 'mm2') {
                resultado = area * 1000000;
            } else if (unidade2 == 'ha') {
                resultado = area / 10000;
            }
        } else if (unidade1 == 'cm2') {
            if (unidade2 == 'm2') {
                resultado = area / 10000;
            } else if (unidade2 == 'cm2') {
                resultado = area;
            } else if (unidade2 == 'mm2') {
                resultado = area * 100;
            } else if (unidade2 == 'ha') {
                resultado = area / 1000000;
            }
        } else if (unidade1 == 'mm2') {
            if (unidade2 == 'm2') {
                resultado = area / 1000000;
            } else if (unidade2 == 'cm2') {
                resultado = area / 100;
            } else if (unidade2 == 'mm2') {
                resultado = area;
            } else if (unidade2 == 'ha') {
                resultado = area / 100000000;
            }
        } else if (unidade1 == 'ha') {
            if (unidade2 == 'm2') {
                resultado = area * 10000;
            } else if (unidade2 == 'cm2') {
                resultado = area * 1000000;
            } else if (unidade2 == 'mm2') {
                resultado = area * 100000000;
            } else if (unidade2 == 'ha') {
                resultado = area;
            }
        }
    }
</script>

<style>
    .container {
        margin-top: 150px;
        align-items: center;
        background-color: #fff;
        border-radius: 12px;
        padding: 30px;
        width: 350px;
        box-shadow: 0 6px 15px rgba(0, 0, 0, 0.1);
        text-align: center;
    }

    .input-field {
        background-color: #e0ffad;
        color: #fff;
        padding: 12px;
        border: none;
        border-radius: 6px;
        text-decoration: none;
        text-align: center;
        display: block;
        width: 100%;
        margin-bottom: 20px;
        font-size: 18px;
        cursor: pointer;
    }

    .select-field {
        background-color: #e0ffad;
    }

    .select-field {
        width: 100%;
        padding: 12px;
        margin: 10px 0;
        border: 2px solid #ccc;
        border-radius: 6px;
        font-size: 16px;
        background-color: #e0ffad;
    }

    .input-field:focus,
    .select-field:focus {
        border-color: #4CAF50;
        outline: none;
    }

    .result {
        font-size: 20px;
        font-weight: bold;
        color: #333;
        margin-top: 20px;
    }

    b {
        font-weight: 600;
        font-size: 18px;
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
</style>

<div class="container">
    <b>Conversor de áreas</b>
    <br>
    <b>Digite o valor:</b>
    <input type="number" bind:value={area} oninput={converter} class="input-field">
    
    <b>Unidade de origem:</b>
    <select bind:value={unidade1} onchange={converter} class="select-field">
        <option value="m2">Metros quadrados</option>
        <option value="cm2">Centímetros quadrados</option>
        <option value="mm2">Milímetros quadrados</option>
        <option value="ha">Hectares</option>
    </select>
    
    <b>Unidade de destino:</b>
    <select bind:value={unidade2} onchange={converter} class="select-field">
        <option value="m2">Metros quadrados</option>
        <option value="cm2">Centímetros quadrados</option>
        <option value="mm2">Milímetros quadrados</option>
        <option value="ha">Hectares</option>
    </select>
    
    <p class="result">O resultado é {resultado}</p>
    <br>
    <a href="http://localhost:5173/aba">
        <button class="styled-button">voltar</button>
      </a>
</div>

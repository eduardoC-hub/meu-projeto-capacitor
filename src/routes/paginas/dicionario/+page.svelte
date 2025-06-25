<script>
    import { dicionario } from '$lib/dicionario.js';
    import { goto } from '$app/navigation';

    let palavra = '';
    let letraSelecionada = '';
    let filtradas = dicionario;
  
    const letras = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('');
  
    function buscar() {
        if ((palavra =='')) {
            filtradas = dicionario;
            return;
        } 
        filtradas = [];
        for(const termo of dicionario) {
            if (termo.palavra.startsWith(palavra)) {
                filtradas.push(termo);
            }
        }
        }
    function filtrarPorLetra(letra) {
      letraSelecionada = letra;
      if (letra === '') {
        filtradas = dicionario;
      } else {
        filtradas = dicionario.filter(termo => termo.palavra.toUpperCase().startsWith(letra));
      }
    }
  
    function gerarPalavraAleatoria() {
      const indice = Math.floor(Math.random() * dicionario.length);
      let palavraAleatoria = dicionario[indice];
      goto(`/paginas/dicionario/${palavraAleatoria.palavra}`);
    }
  </script>
  
  <div class="container">
    <input 
      placeholder="Digite uma palavra" 
      on:input={buscar} 
      bind:value={palavra}
      class="input-pessoal"
    />
  
    <div class="letras">
      {#each letras as letra}
        <button class="botao-letra" on:click={() => filtrarPorLetra(letra)}>{letra}</button>
      {/each}
      <button class="botao-letra todas" on:click={() => filtrarPorLetra('')}>Todas</button>
    </div>
  
    <div class="area-lista">
      <button class="aleatoria" on:click={gerarPalavraAleatoria}>🎲 Aleatória</button>
      <ol>
        {#each filtradas as termo}
          <li><a href={`/paginas/dicionario/${termo.palavra}`}>{termo.palavra}</a></li>
        {/each}
      </ol>
    </div>
  </div>
  
  <style>
    .container {
      padding: 1rem;
      font-size: 18px;
      background-color: #ffffff;
      color: #eee;
      min-height: 100vh;
    }
  
    .input-pessoal {
      width: 100%;
      padding: 1rem;
      font-size: 1.1rem;
      border: none;
      border-radius: 8px;
      margin-bottom: 1rem;
      background-color: #dbdbdb;
      color: #fff;
    }
  
    .letras {
      display: flex;
      flex-wrap: wrap;
      gap: 0.2rem;
      margin-bottom: 1rem;
    }
  
    .botao-letra {
      flex: 1 0 20%;
      background-color: #333;
      color: rgb(105, 208, 240);
      padding: 0.7rem;
      border: none;
      border-radius: 5px;
      
    }
  
    .botao-letra.todas {
      background-color: #660;
      color: #fff;
    }
  
    .area-lista {
      margin-top: 1rem;
    }
  
    .aleatoria {
      width: 100%;
      padding: 1rem;
      background-color: #550;
      color: white;
      font-size: 1.2rem;
      border: none;
      border-radius: 10px;
      margin-bottom: 1rem;
    }
  
    ol {
      padding-left: 1.2rem;
      color: black;
    }
  
    li {
      margin-bottom: 0.6rem;
    }
  
    a {
      color: rgb(105, 208, 240);
      text-decoration: none;
      font-weight: 600;
    }
  
    a:hover {
      text-decoration: underline;
    }
    
  </style>
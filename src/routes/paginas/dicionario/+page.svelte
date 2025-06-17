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
  
  <div>
    <input
      placeholder="Digite uma palavra" oninput ={buscar} bind:value={palavra}/>
   
  </div>
  <div>
    {#each letras as letra}
      <button onclick={() => filtrarPorLetra(letra)}>{letra}</button>
    {/each}
    <button onclick={() => filtrarPorLetra('')}>Todas</button>
  </div>
  
  
  <div>
    <button onclick={gerarPalavraAleatoria}>Gerar palavra aleatória</button>
    <ol>
      {#each filtradas as termo}
        <li><a href={`/paginas/dicionario/${termo.palavra}`}>{termo.palavra}</a></li>
      {/each}
    </ol>
  </div>
  
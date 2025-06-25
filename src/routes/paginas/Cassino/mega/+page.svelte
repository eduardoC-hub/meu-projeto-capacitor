<script>
    let qtd = 6;
    let n = 60;
    let sorteados = [];
function sortear() {
    if (sorteados.length < qtd) {
      let numero;
      do {
        numero = Math.floor(Math.random() * n) + 1;
      } while (sorteados.includes(numero));
      sorteados = [...sorteados, numero];
    }
  }
</script>


<p>está com duvida de qual numero apostar? clique no botao abaixo!</p>
<button onclick={sortear}>Sortear número</button>

{#each sorteados as sorteado}
  <p>O número sorteado é: {sorteado}</p>
{/each}
<br>
<a href="/paginas/Cassino/">Voltar</a>
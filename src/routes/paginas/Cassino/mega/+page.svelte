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

<br>
<a href="/paginas/Cassino"><button class ="btn btn-primary">voltar</button></a>
<br>
<br>
<p>está com duvida de qual numero apostar? clique no botao abaixo!</p>
<div class ="boto">

<button class=" btn btn-dark" onclick={sortear}>Sortear número</button>
<br>
{#each sorteados as sorteado}

  <p><b>O número sorteado é: </b> {sorteado}</p>
{/each}

<br>


</div>
<style>
  .boto{
  text-align: center;
  }

</style>
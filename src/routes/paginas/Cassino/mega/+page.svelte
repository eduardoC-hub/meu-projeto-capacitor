<script>
    
    let qtd = 6;
    let n = 60;
    let sorteados = [];
function sortear() {
  sorteados = [];
        for (let j = 0; j < qtd; j++) {
            let numero = Math.trunc(Math.random() * n);
           
            sorteados.push(numero);
        }
  }



</script>


<p>está com duvida de qual numero apostar? clique no botao abaixo!</p>
<button onclick={sortear}>Sortear número</button>


  <p>Os números sorteados são: {sorteados}</p>

<br>
<a href="/paginas/Cassino"><button class ="btn btn-primary">voltar</button></a>
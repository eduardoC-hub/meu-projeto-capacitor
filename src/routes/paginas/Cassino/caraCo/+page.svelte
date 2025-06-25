<script>

    let resultado = '';
    function jogar() {
        const cc = Math.random();
        resultado = cc < 0.5 ? 'Cara' : 'Coroa';
    }

</script>
<br>

<button class="btn btn-dark" onclick={jogar}>Jogar</button>
<a href="/paginas/Cassino"><button class ="btn btn-primary">voltar</button></a>
<h1>Jogo Cara ou Coroa</h1>
<br>
<p>Jogue cara ou coroa clicando no botão abaixo!</p>


{#if resultado}
    <p>O resultado é: {resultado}</p>
{/if}   
<br>



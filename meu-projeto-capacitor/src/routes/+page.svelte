<script>
	import Cabecalho from './Cabecalho.svelte';
	import Rodape from './Rodape.svelte';
	let nome = 'Eduardo';
	let a = 10;
	let b = 20;
</script>

<Cabecalho />

<p class="azul">Seu nome é {nome}!</p>
<p class="vermelho">{a} + {b} = {a + b - 5}</p>

<p>calculadora de temperatura: <a href=" ./temperatura"> clique aqui</a>!</p>

<Rodape />

<style>
	.azul {
		color: rgb(255, 102, 0);
	}

	.vermelho {
		color: rgb(0, 255, 234);
	}
</style>

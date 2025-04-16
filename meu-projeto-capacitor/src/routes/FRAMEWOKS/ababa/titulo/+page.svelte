<script>
	let idPostagem = "";
	let titulo = "";

	async function buscarTitulo() {
		const resposta = await fetch(`https://jsonplaceholder.typicode.com/posts/${idPostagem}`);
		const dados = await resposta.json();
		titulo = dados.title;
	}
</script>

<form on:submit|preventDefault={buscarTitulo}>
	<input type="number" placeholder="ID da postagem" bind:value={idPostagem} />
	<button type="submit">Buscar título</button>
</form>

{#if titulo}
	<h2>{titulo}</h2>
{/if}

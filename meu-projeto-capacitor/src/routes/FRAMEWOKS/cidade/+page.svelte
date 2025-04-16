<script>
	let idUsuario = '';
	let postagens = [];

	async function buscarPostagens() {
		const resposta = await fetch(`https://jsonplaceholder.typicode.com/posts?userId=${idUsuario}`);
		postagens = await resposta.json();
	}
</script>

<input type="number" placeholder="ID do usuário" bind:value={idUsuario} min="1" max="10"/>
<button onclick={buscarPostagens}>Buscar postagens</button>

{#if postagens.length > 0}
	<h3>Postagens do usuário {idUsuario}</h3>
	<ul>
		{#each postagens as postagem}
			<li>{postagem.title}</li>
		{/each}
	</ul>
{:else if idUsuario}
	<p>Nenhuma postagem encontrada para esse usuário.</p>
{/if}

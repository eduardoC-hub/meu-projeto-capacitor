<script>
    let idPostagem = $state();
    let postagem = $state();
    let comentarios = $state();

    async function buscarPostagem() {
        let resposta = await fetch(`https://jsonplaceholder.typicode.com/posts/${idPostagem}`);
        postagem = await resposta.json();

        let resposta2 = await fetch(`https://jsonplaceholder.typicode.com/posts/${idPostagem}/comments`);
        comentarios = await resposta2.json();
    }
</script>

<form onsubmit={buscarPostagem}>
    <input type="number" placeholder="ID da postagem" bind:value={idPostagem} />
    <button>Buscar postagem</button>
</form>
{#if postagem}
    <h2>{postagem.title}</h2>
    <p>{postagem.body}</p>

    <h3>Comentários</h3>
    <ul>
        {#each comentarios as comentario}
            <li>
                <p><strong>{comentario.email} escreveu:</strong> {comentario.body}</p>
            </li>
        {/each}
    </ul>
{/if}
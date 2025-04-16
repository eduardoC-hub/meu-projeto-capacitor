
<script>
    let idPostagem = $state();
    let postagem = $state();
    let comentarios = $state();
   async function buscarPostagem(){
    let resposta = await fetch(`https://jsonplaceholder.typicode.com/posts/${idPostagem}`);
    postagem = await resposta.json();
    let resposta2 = await fetch(`https://jsonplaceholder.typicode.com/posts/${idPostagem}/comments`);
    comentarios = await resposta2.json();
    }
    </script>




    <input type="number" placeholder="=id da postagem" bind:value={idPostagem}/>
<button onclick={buscarPostagem}>Buscar</button>
{#if postagem}
    <h2>{postagem.title}</h2>
    <p>{postagem.body}</p>
    <h3>Comentários</h3>
    {#each comentarios as comentario}
        <div>
            <small>{comentario.body}</small>
            <p>{comentario.email}</p>
        </div>
    {/each}
    
{/if}
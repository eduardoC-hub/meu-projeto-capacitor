<script>
    import { onMount } from "svelte";

    let usuarios = [];

    async function buscarUsuarios() {
        try {
            const resposta = await fetch("https://jsonplaceholder.typicode.com/users");
            usuarios = await resposta.json();
        } catch (error) {
            console.error("Erro ao buscar usuários:", error);
        }
    }

    onMount(buscarUsuarios);
</script>

{#if usuarios.length}
    <h3>Lista de Usuários</h3>
    {#each usuarios as usuario}
        <div>
            <strong>{usuario.name}</strong>
           
           
        </div>
        <hr>
    {/each}
{:else}
    <p>Carregando usuários...</p>
{/if}

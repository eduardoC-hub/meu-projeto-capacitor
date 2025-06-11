<script>
    import { dicionario } from '$lib/dicionario.js';
    import { page } from '$app/stores';
    import { onMount } from 'svelte';
  
    let termoSelecionado;
  
    $: palavraParam = $page.params.palavra;
  
    onMount(() => {
      termoSelecionado = dicionario.find(t => t.palavra === palavraParam);
    });
  </script>
  
  {#if termoSelecionado}
    <h1>{termoSelecionado.palavra}</h1>
    <ol>
      {#each termoSelecionado.definicoes as definicao}
        <li>{definicao}</li>
      {/each}
    </ol>
  {:else}
    <p>Palavra não encontrada.</p>
  {/if}
  
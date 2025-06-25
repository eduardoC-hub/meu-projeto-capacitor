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
  
 <br>
 <br>
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
  <br>
  <a href="/paginas/dicionario" class='botao-link'>Voltar ao dicionário</a>


  <style>
      
    
    .botao-link {
      display: inline-block;
      padding: 10px 20px;
      background-color: #007bff; 
      color: white;
      text-decoration: none;
      border-radius: 5px;
      font-family: sans-serif;
      font-size: 16px;
      transition: background-color 0.3s ease;
    }
  
    .botao-link:hover {
      background-color: #0056b3; 
    }
  </style>
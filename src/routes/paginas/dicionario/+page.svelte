<script>
    import{dicionario} from '$lib/dicionario.js';
    let palavra = '';
    let filtradas=$state(dicionario)
    function buscar() {
        if ((palavra =='')) {
            filtradas = dicionario;
            return;
        } 
        filtradas = [];
        for(const termo of dicionario) {
            if (termo.palavra.startsWith(palavra)) {
                filtradas.push(termo);
            }
        }
    }
</script>
<div><input placeholder="digite uma palavra" oninput ={buscar} bind:value={palavra}></div>
<div>
    <ol>
    {#each filtradas as termo}
    
       <li><a href="/paginas/dicionario/{termo.palavra}">{termo?.palavra}</a></li>
    
    {/each}
</ol>
</div>

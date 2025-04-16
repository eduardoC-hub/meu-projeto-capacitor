<script>

    let i = 10; 
   

    function bloquear(segundos) {
        return new Promise(resolve => {
            setTimeout(resolve, segundos * 1000);
        });
    }

    async function contagem() {
      
        
        while (i > 0) {
            await bloquear(1);
            i--; 
        }

      
    }
</script>
<div class="contagem">
<h1>🕒 Contagem Regressiva</h1>


    <input type="number" bind:value={i} min="0" />
    <button onclick={contagem}>Contar</button>
</div>

<div class="numero" >
{#if i > 0}
    <h2>{i}</h2>
{:else if i == 0}
    <h2>✅ Contagem finalizada!</h2> 
{/if}
</div>

<style>
    .contagem {
        text-align: center;
        align-items: center;
        flex-direction: column;
        height: 70px;
    }
  
.numero{
    margin-top: 300px;
        text-align: center;
        align-items: center;
       
        height: 200px;
        font-size: 5000;
        color: #ff0000;
}
    
</style>

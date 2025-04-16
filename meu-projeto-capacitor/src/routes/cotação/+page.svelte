<script>

    let dinheiroreal = $state(0);
    let dinheirodolar = $state(0);
 
     function cotacaoreal() {
                dinheirodolar = dinheiroreal/5.69
           
     }
     function cotacaodolar(){ 
                dinheiroreal = dinheirodolar*5.69 
 }
     
 </script>
 
 <h1>Vamos converter para dolar!</h1>
 <p><input oninput={cotacaoreal} type="number" bind:value={dinheiroreal} /></p>
 <p>O valor de {dinheiroreal} reais convertido para dolar é {dinheirodolar}</p>
 <br>
 <hr>
 <br>
 <h1>Agora convertendo dolar para o real</h1>
 <input oninput={cotacaodolar} type="number" bind:value={dinheirodolar} />
 <p>O valor de {dinheirodolar} dolars convertido para real é {dinheiroreal}</p>
 
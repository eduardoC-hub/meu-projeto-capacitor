<script>
    let np, nt, ns;
    let nf = $state(0);

    function calcularnota() {
        np=np*0.5
        ns=ns*0.3
        nt=nt*0.2
        nf=np+ns+nt
        
    }
</script>

<h1>Boletim Escolar</h1>

Nota da prova:
<input type="number" bind:value={np} min="0" max="10" />
<br />

Nota do trabalho:
<input type="number" bind:value={nt} min="0" max="10"/>
<br />

Nota do seminário:
<input type="number" bind:value={ns} min="0" max="10"/>
<br />

<button onclick={calcularnota}> Calcular a nota final!</button>

<p>Tua nota final é: {nf}.</p>

{#if nf <= 10 && nf >= 8.5}
	<p>sua nota é {nf} e voce está aprovado com A.</p>
    {:else if nf >= 7}
    <p>sua nota é {nf} e voce está aprovado com B.</p>
    {:else if  nf >= 5}
    <p>sua nota é {nf} e voce está de recuperação com C.</p>
    {:else if  nf >= 2.5}
    <p>sua nota é {nf} e voce está de recuperação com D.</p>
    {:else}
    <p>sua nota é {nf} e voce está reprovado com E.</p>
{/if}


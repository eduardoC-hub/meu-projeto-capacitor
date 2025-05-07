<script>
    const tarefas = $state([]);
    let novaTarefa = $state('');
    let tarefaEditadaIndice = $state();
    let tarefaEditadaItem = $state();
    const tarefas_Concluidas = $state([]);

    function adicionarTarefa() {
        if (novaTarefa.trim() !== '') {
            tarefas.push({ texto: novaTarefa, concluida: false });
            novaTarefa = '';
        }
    }

    function excluirTarefa(i) {
        tarefas.splice(i, 1);
    }

    function editarTarefa(tarefa, i) {
        tarefaEditadaItem = tarefa.texto;
        tarefaEditadaIndice = i;
    }

    function salvarTarefa(i) {
        tarefas[i].texto = tarefaEditadaItem;
        tarefaEditadaIndice = -1;
    }

    function cancelaredi() {
        tarefaEditadaIndice = -1;
        tarefaEditadaItem = '';
    }

    function concluirTarefa(i) {
        const tarefa = tarefas[i];
        tarefa.concluida = !tarefa.concluida;
        
        if (tarefa.concluida) {
            tarefas_Concluidas.push(tarefa);
        } else {
            const index = tarefas_Concluidas.indexOf(tarefa);
            if (index !== -1) {
                tarefas_Concluidas.splice(index, 1);
            }
        }
    }
</script>
<style>
 
    .mybody {
        width: 90%;
        max-width: 400px;
        margin: 50px auto;
        background-color: #ffffff;
        padding: 15px;
        border-radius: 10px;
        box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    }

    h2 {
        text-align: center;
        color: #333;
    }

    p {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    input {
        padding: 8px;
        width: 70%;
        border: 2px solid #ccc;
        border-radius: 4px;
        margin-right: 10px;
    }

    button {
        background-color: #4CAF50;
        color: white;
        border: none;
        padding: 8px 12px;
        cursor: pointer;
        border-radius: 4px;
        font-size: 14px;
        margin-left: 5px;
    }

    button:hover {
        background-color: #6545a0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        background-color: #f9f9f9;
        margin: 5px 0;
        padding: 10px;
        border: 1px solid #ddd;
        border-radius: 4px;
    }

    li span {
        flex: 1;
        margin-bottom: 5px;
    }

    .botoes {
        display: flex;
        gap: 5px;
        width: 100%;
        justify-content: flex-end;
    }

    .concluida {
        text-decoration: line-through;
        color: #aaa;
    }
</style>

<div class='mybody'>
    <h2>Lista de tarefas</h2>
    <p>
        <input placeholder="Digite aqui tua nova tarefa..." bind:value={novaTarefa} />
        <button onclick={adicionarTarefa}>+</button>
    </p>
    <ul>
        {#each tarefas as tarefa, i}
            <li class={tarefa.concluida ? 'concluida' : ''}>
                {#if tarefaEditadaIndice == i}
                    <input bind:value={tarefaEditadaItem} />
                    <div class="botoes">
                        <button onclick={() => salvarTarefa(i)}>💾</button>
                        <button onclick={cancelaredi}>❌</button>
                    </div>
                {:else}
                    <span>{tarefa.texto}</span>
                    <div class="botoes">
                        <button onclick={() => editarTarefa(tarefa, i)}>✏️</button>
                        <button onclick={() => excluirTarefa(i)}>🗑️</button>
                        <button onclick={() => concluirTarefa(i)}>{tarefa.concluida ? '❌' : '✅'}</button>
                    </div>
                {/if}
            </li>
        {/each}
    </ul>
    
    <h2>Tarefas Concluídas</h2>
    <ul>
        {#each tarefas_Concluidas as tarefaConcluida}
            <li>{tarefaConcluida.texto}</li>
        {/each}
    </ul>
</div>


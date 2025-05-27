<script>
	import { onMount } from 'svelte';
	import Modal from '$lib/components/Modal.svelte';
	import Toast from '$lib/components/Toast.svelte';
	import ToDoList from '$lib/components/ToDoList.svelte';
	import * as bootstrap from 'bootstrap';

	let novaTarefa = $state('');
	let tarefas = $state([]);
	let tarefasPendentes = $derived(tarefas.filter((tarefa) => tarefa.status == 0));
	let tarefasConcluidas = $derived(tarefas.filter((tarefa) => tarefa.status == 1));

	let totalTarefas = $derived(tarefas.length);
	let totalPendentes = $derived(tarefasPendentes.length);
	let totalConcluidas = $derived(tarefasConcluidas.length);

	let conteudoTarefaEditando = $state('');
	let tarefaEditando = $state();
	let tarefaExcluindo;
	let mensagemToast;

	async function adicionarTarefa() {
		novaTarefa = novaTarefa.trim();
		if (!novaTarefa) {
			mensagemToast.show();
			return;
		}
		tarefas.push({ conteudo: novaTarefa, status: 0 });
		novaTarefa = '';
	}

	function editarTarefa(tarefa) {
		tarefaEditando = tarefa;
		conteudoTarefaEditando = tarefa.conteudo;
	}

	function confirmarEdicao() {
		if (!conteudoTarefaEditando) {
			mensagemToast.show();
			return;
		}
		if (tarefaEditando && conteudoTarefaEditando.trim()) {
			tarefaEditando.conteudo = conteudoTarefaEditando.trim();
			tarefaEditando = undefined;
		}
	}

	function cancelarEdicao() {
		tarefaEditando = undefined;
	}

	function excluirTarefa(tarefa) {
		tarefaExcluindo = tarefa;
	}

	function confirmarExclusao() {
		tarefas = tarefas.filter((t) => t !== tarefaExcluindo);
		tarefaExcluindo = undefined;
	}

	function alterarStatus(tarefa, status) {
		tarefa.status = status;
	}

	onMount(() => {
		mensagemToast = new bootstrap.Toast('#mensagemToast');
	});
</script>


<div class="fixed-top pt-5" style="z-index: 1020;">
	<form class="container-fluid input-group px-4 pt-3" onsubmit={adicionarTarefa}>
		<input class="form-control form-control-lg" placeholder="Nova tarefa" bind:value={novaTarefa} />
		<button type="submit" class="btn btn-primary input-group-text" aria-label="adicionar">
			<i class="bi bi-plus-lg"></i>
		</button>
	</form>

	<Toast msg={'Digite algo!'} />

	
	<div class="container-fluid px-4 pt-2">
		<div class="d-flex gap-3">
			<span class="badge bg-secondary">Total: {totalTarefas}</span>
			<span class="badge bg-warning text-dark">Pendentes: {totalPendentes}</span>
			<span class="badge bg-success">Concluídas: {totalConcluidas}</span>
		</div>
	</div>
</div>
<br>
<br>
<div class="container-fluid mt-5 pt-3">
	<ToDoList
		tarefas={tarefasPendentes}
		{tarefaEditando}
		bind:conteudoTarefaEditando
		{editarTarefa}
		{confirmarEdicao}
		{cancelarEdicao}
		{alterarStatus}
		{excluirTarefa}
	/>
	<hr />
	<ToDoList
		tarefas={tarefasConcluidas}
		{tarefaEditando}
		bind:conteudoTarefaEditando
		{editarTarefa}
		{confirmarEdicao}
		{cancelarEdicao}
		{alterarStatus}
		{excluirTarefa}
	/>
</div>

<!-- Modal de confirmação -->
<Modal msg={'Deseja excluir a tarefa?'} acao={confirmarExclusao} />

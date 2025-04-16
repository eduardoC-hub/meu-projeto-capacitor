<script>
	let nome_usuario = '',
		senha_usuario = '',
		autenticado = false;

	function registrar_usuario() {
		nome_usuario = document.getElementById('nome_usuario').value;
		senha_usuario = document.getElementById('senha_usuario').value;
		autenticado = true;
	}

	function desautenticar_usuario() {}
	function excluir_usuario() {}
	function autenticar_usuario() {}
</script>

{#if !nome_usuario || !senha_usuario}
	Nome do usuário: <input type="text" id="nome_usuario" /><br />
	Senha: <input type="password" id="senha_usuario" /><br />
	<button onclick={registrar_usuario}>Registrar usuário</button>
{:else if autenticado}
	<p>Bem vindo, {nome_usuario}!</p>
	<button onclick={desautenticar_usuario}>Sair da conta</button>
	<button onclick={excluir_usuario}>Excluir conta</button>
{:else}
	<p>Sem permissão.</p>
	Nome do usuário:<input type="text" id="nome_usuario" /><br />
	Senha: <input type="password" id="senha_usuario" /><br />
	<button onclick={autenticar_usuario}>Autenticar usuário</button>
{/if}

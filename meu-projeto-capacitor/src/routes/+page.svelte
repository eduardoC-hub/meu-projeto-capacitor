<script>
  let email = '';
  let password = '';
  let errorMessage = '';

  function validateForm() {
    if (!email || !password) {
      errorMessage = 'Por favor, preencha todos os campos.';
      return false;
    }

    if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
      errorMessage = 'Insira um e-mail válido.';
      return false;
    }

    errorMessage = '';
    return true;
  }

  function handleSubmit(event) {
    event.preventDefault();

    if (validateForm()) {
      console.log('E-mail:', email);
      console.log('Senha:', password);

      window.location.href = '/paginas/app';
    }
  }
</script>

<!-- Viewport tag ESSENCIAL para responsividade em celulares -->
<svelte:head>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
</svelte:head>

<link
  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
  rel="stylesheet"
/>

<div class="login-container">
  <div class="login-box">
    <h2>Cadastre-se no app do Calestini</h2>

    {#if errorMessage}
      <div class="error">{errorMessage}</div>
    {/if}

    <form on:submit|preventDefault={handleSubmit}>
      <label for="email">E-mail</label>
      <input type="email" id="email" bind:value={email} placeholder="Digite seu e-mail" />

      <label for="password">Senha</label>
      <input type="password" id="password" bind:value={password} placeholder="Digite sua senha" />

      <button
        type="submit"
        class="btn btn-primary mt-3"
        disabled={!email || !password || errorMessage}
      >
        Entrar
      </button>
    </form>
  </div>
</div>

<style>
  .login-container {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    padding: 1rem;
    
  }

  .login-box {
    background: rgba(255, 255, 255, 0.491);
    padding: 2rem;
    border-radius: 10px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 400px;
  }

  h2 {
    text-align: center;
    margin-bottom: 1.5rem;
    font-size: 1.5rem;
  }

  form {
    display: flex;
    flex-direction: column;
  }

  label {
    margin-bottom: 0.25rem;
    font-weight: bold;
    font-size: 0.95rem;
  }

  input {
    padding: 0.75rem;
    margin-bottom: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    font-size: 1rem;
    width: 100%; 
  }

  .error {
    color: red;
    font-size: 0.9rem;
    margin-bottom: 1rem;
    text-align: center;
  }

  button {
    padding: 0.75rem;
    font-size: 1rem;
    border-radius: 4px;
  }

  button:disabled {
    background-color: #a0a0a079;
    cursor: not-allowed;
  }

  
  @media (max-width: 576px) {
    h2 {
      font-size: 1.25rem;
    }

    .login-box {
      padding: 1.5rem;
    }

    input, button {
      font-size: 0.95rem;
    }
  }
</style>

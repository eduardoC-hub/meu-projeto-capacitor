<script>
  let searchTerm = '';

  let links = [
    { label: 'Conversor', href: '/paginas/aba' },
    { label: 'Lista de Tarefas', href: '/paginas/listasimples' },
    { label: 'Gerador de Senhas', href: '/paginas/aleatorio' },
    { label: 'Autenticação', href: '/paginas/aut' },
    { label: 'Boletim', href: '/paginas/boletim' },
    { label: 'Quiz', href: '/paginas/quiz' },
    { label: 'Calculadora', href: '/paginas/calculadora' },
    { label: 'Dicionario', href: '/paginas/dicionario' },
    { label: 'Cassino', href: '/paginas/Cassino' },
    { label: 'velha', href: '/paginas/velha'}

  ];

  // Filtro com base no termo pesquisado
  $: filteredLinks = links.filter(link =>
    link.label.toLowerCase().includes(searchTerm.toLowerCase())
  );
</script>

<div class="offcanvas offcanvas-start" tabindex="-1" id="mySideBar" style="max-width: 80%;">
  <div class="offcanvas-header">
    <h5 class="offcanvas-title">Menu</h5>
    <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
  </div>

  <div class="offcanvas-body">
    <!-- Campo de pesquisa -->
    <form class="d-flex mt-3" on:submit|preventDefault>
      <input
        class="form-control me-2"
        type="search"
        placeholder="Pesquisar"
        bind:value={searchTerm}
      />
      <button class="btn btn-outline-success" type="submit">Buscar</button>
    </form>

    <!-- Lista filtrada de links -->
    <ul class="navbar-nav justify-content-end flex-grow-1 pe-3 mt-3">
      {#each filteredLinks as link}
        <li class="nav-item">
          <a class="nav-link active" href={link.href}>{link.label}</a>
        </li>
      {/each}
    </ul>
  </div>
</div>

<div class="offcanvas offcanvas-start" tabindex="-1" id="mySideBar" style="max-width: 80%;">
    <div class="offcanvas-header">
      <h5 class="offcanvas-title">Offcanvas</h5>
      <button type="button" class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body">
      <form class="d-flex mt-3" role="search">
        <input class="form-control me-2" type="search" placeholder="Search" />
        <button class="btn btn-outline-success" type="submit">Search</button>
      </form>
      <ul class="navbar-nav justify-content-end flex-grow-1 pe-3">
        <li class="nav-item"><a class="nav-link active" href="/paginas/calculadora">Calculadora</a></li>
        <li class="nav-item"><a class="nav-link active" href="/paginas/aba">Conversor</a></li>
        <li class="nav-item"><a class="nav-link active" href="/paginas/listasimples">Lista de Tarefas</a></li>
        <li class="nav-item"><a class="nav-link active" href="/paginas/aleatorio">Gerador de Senhas</a></li>
        <li class="nav-item"><a class="nav-link active" href="/paginas/aut">Autenticação</a></li>
        <li class="nav-item"><a class="nav-link active" href="/paginas/boletim">Boletim</a></li>
        <li class="nav-item"><a class="nav-link active" href="/paginas/quiz">Quiz</a></li>
        <li class="nav-item"><a class="nav-link active" href="/paginas/dicionario">Dicionário</a></li>
        <li class="nav-item"><a class="nav-link active" href="/paginas/Cassino">Cassino</a></li>
        <li class="nav-item"><a class="nav-link active" href="/paginas/velha">Velha</a></li>

        
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" href="/" role="button" data-bs-toggle="dropdown">Dropdown</a>
          <ul class="dropdown-menu">
            <li><a class="dropdown-item" href="/">Action</a></li>
            <li><a class="dropdown-item" href="/">Another action</a></li>
            <li><hr class="dropdown-divider" /></li>
            <li><a class="dropdown-item" href="/">Something else here</a></li>
          </ul>
        </li>
      </ul>
    </div>
  </div>
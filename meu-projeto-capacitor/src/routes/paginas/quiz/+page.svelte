<script>
    let promise = $state();
    let questionario = $state([]);
    let respostas = $state([]);
    let respondeu = $state(false);
   
    function gerarNovoQuiz() {
        respondeu = false;
        promise = fetch('https://opentdb.com/api.php?amount=5&category=9&type=multiple')
            .then((response) => response.json())
            .then((data) => {
                questionario = data.results;
                for (const pergunta of questionario) {
                    const i = Math.floor(Math.random() * pergunta.incorrect_answers.length + 1);
                    pergunta.incorrect_answers.splice(i, 0, pergunta.correct_answer);
                }
            });
    }
   
    function verificarRespostas() {
        respondeu = true;
        let acertos = 0;
        for (let i = 0; i < questionario.length; i++) {
            if (respostas[i] === questionario[i].correct_answer) {
                acertos++;
            }
        }
        alert(`Você acertou ${acertos} de ${questionario.length} questões!`);
    }
  </script>
   
  <div class="container">
    <button class="btn btn-info" onclick={gerarNovoQuiz}>Gerar novo quiz</button>
   
    {#await promise}
        <p>Gerando novo questionário...</p>
    {:then}
        <ol>
            {#each questionario as pergunta, i}
                <h4><li>{@html pergunta.question}</li></h4>
                {#each pergunta.incorrect_answers as alternativa}
                    <div class="form-check">
                        <input class="form-check-input" type="radio" id={alternativa} bind:group={respostas[i]} value={alternativa} oninput={() => (respondeu = false)} />
                        <label class="form-check-label" for={alternativa}>{@html alternativa}</label>
   
                        {#if respondeu && alternativa == respostas[i]}
                            {#if alternativa == pergunta.correct_answer}
                                <span class="badge bg-success">Correto</span>
                            {:else}
                                <span class="badge bg-danger">Incorreto</span>
                            {/if}
                        {/if}
                    </div>
                {/each}
            {/each}
        </ol>
        <button onclick={verificarRespostas} class="btn btn-success">Confirmar!</button>
    {:catch error}
        <p style="color: red">{error.message}</p>
    {/await}
  </div>
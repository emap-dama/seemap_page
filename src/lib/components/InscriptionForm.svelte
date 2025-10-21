<script>
  const ENDPOINT = "https://script.google.com/macros/s/AKfycbxvhdvrgnqpPctgmG_rfp903ozTLtKbyHM73nTWmDaSU0hEcMLVY27FZJUYJOoU4wcx/exec";

  let form = { nome: '', email: '', instituicao: '', degree: '', comments: '' };
  let selectedTalks = [];
  let status = 'idle';
  let errorMsg = '';

  const sessions = [
    { id: '3-14', day: '3', time: '14h', speaker: '', title: 'Os impactos da Matemática e da Ciência de Dados no Mercado Financeiro' },
    { id: '3-1530', day: '3', time: '15h30', speaker: '', title: 'Vizagrams: um mergulho na teoria de visualização de dados e uma proposta de avanço' },
    { id: '3-17', day: '3', time: '17h', speaker: '', title: 'Leilões e Matemática' },
    { id: '4-14', day: '4', time: '14h', speaker: '', title: 'Não importa o que você faça, se souber Matemática fará melhor!' },
    { id: '4-1530', day: '4', time: '15h30', speaker: '', title: 'Estamos passando por uma instabilidade em nosso sistema' },
    { id: '4-17', day: '4', time: '17h', speaker: '', title: 'Princípio da Casa dos Pombos' },
    { id: '5-14', day: '5', time: '14h', speaker: '', title: 'Apresentação de alunos' },
    { id: '5-16', day: '5', time: '16h', speaker: '', title: 'Olimpíadas de matemática no Brasil' },
  ];

  // Agrupar sesiones por día
  $: groupedSessions = sessions.reduce((acc, session) => {
    if (!acc[session.day]) acc[session.day] = [];
    acc[session.day].push(session);
    return acc;
  }, {});

  async function submit(e) {
    e.preventDefault();
    status = 'sending';
    errorMsg = '';

    try {
      const talks = selectedTalks.join('|');
      const params = new URLSearchParams({
        nome: form.nome,
        email: form.email,
        instituicao: form.instituicao,
        degree: form.degree,
        comments: form.comments,
        talks
      });

      const res = await fetch(ENDPOINT, {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded;charset=UTF-8' },
        body: params.toString()
      });

      const json = await res.json().catch(() => ({}));
      if (!res.ok || !json.ok) throw new Error(json.error || `HTTP ${res.status}`);

      status = 'ok';
      form = { nome: '', email: '', instituicao: '', degree: '', comments: '' };
      selectedTalks = [];
    } catch (err) {
      status = 'error';
      errorMsg = err.message;
    }
  }
</script>

<div class="header">
  <h1>Segure sua vaga nas palestras</h1>
  <p>Preencha o formulário abaixo para confirmar sua participação</p>
</div>

<form class="form-content" on:submit={submit}>
  <!-- Informações Pessoais -->
  <section class="section">
    <h2 class="section-title">
      Informações Pessoais
    </h2>

    <div class="form-grid">
      <div class="input-group">
        <input
          type="text"
          placeholder="Nome completo"
          bind:value={form.nome}
          required
        />
      </div>

      <div class="input-group">
        <input
          type="email"
          placeholder="Email"
          bind:value={form.email}
          required
        />
      </div>

      <div class="input-group">
        <input
          type="text"
          placeholder="Instituição"
          bind:value={form.instituicao}
        />
      </div>

      <div class="input-group">
        <input
          type="text"
          placeholder="Período (Indicar se é pós)"
          bind:value={form.degree}
        />
      </div>
    </div>


  </section>

  <!-- Palestras -->
  <section class="section">
    <h2 class="section-title">
      Escolha as Palestras
    </h2>

    {#each Object.entries(groupedSessions) as [day, talks]}
      <div class="day-group">
        <h3 class="day-title">Dia {day}</h3>
        <div class="talks-list">
          {#each talks as session}
            <label class="talk-item">
              <input
                type="checkbox"
                value={session.id}
                bind:group={selectedTalks}
              />
              <div class="talk-content">
                <div class="talk-header">
                  <span class="talk-time">{session.time}</span>
                  {#if session.speaker}
                    <span class="talk-speaker">· {session.speaker}</span>
                  {/if}
                </div>
                {#if session.title}
                  <div class="talk-title">"{session.title}"</div>
                {/if}
              </div>
            </label>
          {/each}
        </div>
      </div>
    {/each}
  </section>

  <!-- Submit Button -->
  <button class="submit-btn" disabled={status === 'sending'}>
    {status === 'sending' ? 'Enviando…' : 'Enviar Inscrição'}
  </button>

  <!-- Status Messages -->
  {#if status === 'ok'}
    <div class="message success">
      <p>Cadastro enviado! Você receberá uma confirmação em breve.</p>
    </div>
  {/if}

  {#if status === 'error'}
    <div class="message error">
      <p>Ocorreu um erro ao enviar: {errorMsg}</p>
    </div>
  {/if}
</form>

<style>
  :global(body) {
    margin: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  }

  .container {
    min-height: 100vh;
    padding: 2rem 1rem;
  }

  .card {
    max-width: 900px;
    margin: 0 auto;
    background: white;
    border-radius: 20px;
    overflow: hidden;
    
  }

  .header {
    color: rgb(0, 0, 0);
    padding: 2rem 1rem;
  }

  .header h1 {
    margin: 0 0 0.5rem 0;
    font-size: 2rem;
    font-weight: 800;
  }

  .header p {
    margin: 0;
    opacity: 0.9;
    font-size: 1.1rem;
  }

  .form-content {
    padding: 2.5rem;
  }

  .section {
    margin-bottom: 2.5rem;
  }

  .section-title {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 1.3rem;
    font-weight: 700;
    color: #2d3748;
    margin: 0 0 1.5rem 0;
    padding-bottom: 0.75rem;
    border-bottom: 3px solid #1b77e7;
  }

  .icon {
    font-size: 1.4rem;
  }

  .form-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 1rem;
    margin-bottom: 1rem;
  }

  .input-group {
    position: relative;
  }

  .input-icon {
    position: absolute;
    left: 1rem;
    top: 50%;
    transform: translateY(-50%);
    font-size: 1.2rem;
    pointer-events: none;
    z-index: 1;
  }

  textarea ~ .input-icon {
    top: 1rem;
    transform: none;
  }

  input,
  textarea {
    width: 100%;
    padding: 1rem 1rem 1rem 3rem;
    border: 2px solid #e2e8f0;
    border-radius: 12px;
    font-family: inherit;
    font-size: 1rem;
    transition: all 0.3s;
    box-sizing: border-box;
  }

  input:focus,
  textarea:focus {
    outline: none;
    border-color: #1b77e7;
    box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
  }

  textarea {
    resize: vertical;
    min-height: 120px;
  }

  .day-group {
    background: #f7fafc;
    border-radius: 16px;
    padding: 1.5rem;
    margin-bottom: 1.5rem;
  }

  .day-title {
    font-size: 1.2rem;
    font-weight: 700;
    color: #1b77e7;
    margin: 0 0 1rem 0;
  }

  .talks-list {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
  }

  .talk-item {
    display: flex;
    gap: 1rem;
    align-items: flex-start;
    padding: 1rem;
    background: white;
    border-radius: 12px;
    border: 2px solid transparent;
    cursor: pointer;
    transition: all 0.3s;
  }

  .talk-item:hover {
    border-color: #1b77e7;
    box-shadow: 0 4px 12px rgba(102, 126, 234, 0.15);
    transform: translateY(-2px);
  }

  .talk-item input[type="checkbox"] {
    width: 1.25rem;
    height: 1.25rem;
    margin-top: 0.25rem;
    cursor: pointer;
    flex-shrink: 0;
    accent-color: #1b77e7;
  }

  .talk-content {
    flex: 1;
  }

  .talk-header {
    font-weight: 600;
    color: #2d3748;
    margin-bottom: 0.25rem;
  }

  .talk-time {
    color: #1b77e7;
    font-weight: 700;
  }

  .talk-speaker {
    color: #4a5568;
  }

  .talk-title {
    font-size: 0.9rem;
    color: #718096;
    margin-top: 0.25rem;
  }

  .submit-btn {
    width: 100%;
    padding: 1.25rem;
    background: linear-gradient(135deg, #1b77e7, #0ea5e9);
    color: white;
    border: none;
    border-radius: 12px;
    font-size: 1.1rem;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s;
    box-shadow: 0 4px 12px rgba(102, 126, 234, 0.4);
  }

  .submit-btn:hover:not(:disabled) {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(102, 126, 234, 0.5);
  }

  .submit-btn:disabled {
    opacity: 0.6;
    cursor: not-allowed;
  }

  .message {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1.25rem;
    border-radius: 12px;
    margin-top: 1.5rem;
    font-weight: 500;
  }

  .message-icon {
    font-size: 1.5rem;
    flex-shrink: 0;
  }

  .message p {
    margin: 0;
  }

  .success {
    background: #f0fdf4;
    color: #166534;
    border: 2px solid #22c55e;
  }

  .error {
    background: #fef2f2;
    color: #991b1b;
    border: 2px solid #ef4444;
  }

  @media (max-width: 768px) {
    .container {
      padding: 1rem;
    }

    .header {
      padding: 2rem 1.5rem;
    }

    .header h1 {
      font-size: 1.5rem;
    }

    .form-content {
      padding: 1.5rem;
    }

    .form-grid {
      grid-template-columns: 1fr;
    }
  }
</style>

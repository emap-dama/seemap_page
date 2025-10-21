<script lang="ts">
  import ScrollSection from '../../lib/components/ScrollSection.svelte';
  import RegistrationForm from '../../lib/components/RegistrationForm.svelte';

  let submitted = false;
  
</script>

<svelte:head>
  <title>SEEMAp — Apresentações de Alunos</title>
  <meta name="description" content="Apresentações de alunos da SEEMAp: objetivo, perfil, etapas de inscrição e formulário de pré-inscrição." />
</svelte:head>

<ScrollSection stepClass="scroll-step" offset={0.5}>
  <section id="objetivo" class="container card gradient-border scroll-step" aria-labelledby="objetivo-title">
    <div class="card-header">
      <h3 id="objetivo-title">Objetivo</h3>
      <p class="card-subtitle">
        A SEEMAp reúne corpos discente e docente da EMAp para discutir temas de interesse em matemática e computação por meio de palestras, minicursos, workshops e apresentações.
      </p>
    </div>
    <p>
      O evento de apresentações dos alunos amplia as vozes da graduação, pós-graduação e pesquisadores da FGV. Valem projetos pessoais, trabalhos de disciplina que você deseja aprofundar, iniciação científica ou resultados de pesquisa que queira compartilhar.
    </p>
  </section>

  <!-- Perfil e Vagas -->
  <section id="perfil" class="container card scroll-step" aria-labelledby="perfil-title">
    <div class="card-header">
      <h3 id="perfil-title">Perfil dos Participantes & Vagas</h3>
    </div>
    <div class="grid">
      <article class="info-card">
        <h4>Quem pode se inscrever</h4>
        <ul>
          <li>Alunos de graduação da FGV</li>
          <li>Alunos de pós-graduação</li>
          <li>Pesquisadores vinculados à FGV</li>
        </ul>
      </article>
      <article class="info-card">
        <h4>Vagas</h4>
        <p>Até <strong>12 projetos</strong> no total.</p>
      </article>
    </div>
  </section>

  <!-- Descrição -->
  <section id="descricao" class="container card scroll-step" aria-labelledby="descricao-title">
    <div class="card-header">
      <h3 id="descricao-title">Descrição</h3>
      <p class="card-subtitle">Exposições de banners e apresentações orais.</p>
    </div>
    <p>
      Cada aluno desenvolve um projeto (iniciativa própria ou iniciação científica) e o apresenta junto com o banner ao longo de aproximadamente <strong>1h30</strong>. 
      Os projetos recebem avaliação de professores da EMAp com parecer profissional sobre a condução e melhorias possíveis da pesquisa.
    </p>
  </section>

  <!-- Avaliação -->
  <section id="avaliacao" class="container card scroll-step" aria-labelledby="avaliacao-title">
    <div class="card-header">
      <h3 id="avaliacao-title">Avaliação</h3>
      <p class="card-subtitle">Feedback qualificado para aprimorar sua pesquisa.</p>
    </div>
    <ul class="checklist">
      <li><span aria-hidden="true">✓</span> Clareza do problema e objetivos</li>
      <li><span aria-hidden="true">✓</span> Metodologia e execução</li>
      <li><span aria-hidden="true">✓</span> Resultados e análise</li>
      <li><span aria-hidden="true">✓</span> Comunicação (apresentação oral e banner)</li>
      <li><span aria-hidden="true">✓</span> Referências e contextualização</li>
    </ul>
  </section>

  <!-- Etapas de Inscrição -->
  <section id="etapas" class="container card scroll-step" aria-labelledby="etapas-title">
    <div class="card-header">
      <h3 id="etapas-title">Etapas de Inscrição</h3>
      <p class="card-subtitle">Processo em duas fases</p>
    </div>
    <ol class="timeline" aria-label="Linha do tempo das inscrições">
      <li>
        <div class="timeline-marker" aria-hidden="true"></div>
        <div class="timeline-content">
          <strong>Pré-inscrição</strong>
          <span class="timeline-text">Enviar nome dos participantes, tema e pequeno resumo do que será explorado.</span>
        </div>
      </li>
      <li>
        <div class="timeline-marker" aria-hidden="true"></div>
        <div class="timeline-content">
          <strong>Confirmação</strong>
          <span class="timeline-text">Após seleção, enviar PDF simples do conteúdo da apresentação e o banner (com título, resultados, fontes e logo da SEEMAp).</span>
        </div>
      </li>
    </ol>
  </section>
  <!-- Inscrição -->
  <section id="inscricao" class="container card highlight-card scroll-step" aria-labelledby="inscricao-title">
    <div class="card-header">
      <h3 id="inscricao-title">Inscrição</h3>
      <p class="card-subtitle">Preencha o formulário para reservar sua vaga.</p>
    </div>
    <RegistrationForm />
  </section>

  <!-- FAQ -->
  <section id="faq" class="container card scroll-step" aria-labelledby="faq-title">
    <div class="card-header">
      <h3 id="faq-title">Perguntas Frequentes</h3>
    </div>
    <div class="accordion" role="list">
      <details class="accordion-item" role="listitem">
        <summary>Posso inscrever um trabalho de disciplina?</summary>
        <p>Sim. Trabalhos de disciplina que você deseje aprofundar são bem-vindos.</p>
      </details>
      <details class="accordion-item" role="listitem">
        <summary>O banner é obrigatório?</summary>
        <p>Sim. O banner deve incluir título, resultados, fontes e o logo da SEEMAp.</p>
      </details>
      <details class="accordion-item" role="listitem">
        <summary>Quem avalia os projetos?</summary>
        <p>Professores da EMAp emitem parecer com sugestões de melhoria.</p>
      </details>
    </div>
  </section>

  <!-- Inscrição -->
  <section id="inscricao" class="container card highlight-card scroll-step" aria-labelledby="inscricao-title">
    <div class="card-header">
      <h3 id="inscricao-title">Pré-inscrição</h3>
      <p class="card-subtitle">Preencha os campos abaixo. Você pode substituir este formulário por um link para Google Forms, se preferir.</p>
    </div>

    {#if submitted}
      <div class="notice success" role="status" aria-live="polite">
        Pré-inscrição enviada! Em breve entraremos em contato por e-mail.
      </div>
    {/if}

  </section>

</ScrollSection>

<style>
  section[id] { scroll-margin-top: 84px; }
  .container { width: min(100% - 32px, 1080px); margin-inline: auto; }

  /* Cards e layout (reuso do seu tema) */
  .card { margin-bottom: 32px; padding: 40px; background: #ffffff; border-radius: 20px; box-shadow: 0 4px 20px rgba(0,0,0,.08); transition: box-shadow .3s ease, transform .3s ease; }
  .card:hover { box-shadow: 0 8px 30px rgba(0,0,0,.12); transform: translateY(-2px); }
  .gradient-border { position: relative; border: 2px solid transparent; background-image: linear-gradient(#ffffff,#ffffff), linear-gradient(135deg,#1b77e7,#0ea5e9); background-origin: border-box; background-clip: padding-box, border-box; }
  .highlight-card { background: linear-gradient(135deg,#f0f9ff 0%, #f8fafc 100%); }
  .card-header { margin-bottom: 24px; }
  .card h3 { margin: 0 0 8px; font-size: 2rem; font-weight: 800; }
  .card-subtitle { color: #667085; margin: 0; font-size: 1rem; }

  .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 20px; }
  .info-card { padding: 20px; border: 2px solid #f0f4f8; border-radius: 16px; }

  .highlight-card { 
    background: linear-gradient(135deg, #f0f9ff 0%, #f8fafc 100%); 
  }

  .timeline { line-height: 1.9; margin: 0; padding-left: 0; list-style: none; }
  .timeline li { position: relative; padding-left: 40px; margin-bottom: 24px; }
  .timeline-marker { position: absolute; left: 0; top: 4px; width: 16px; height: 16px; background: linear-gradient(135deg,#1b77e7 0%, #0ea5e9 100%); border-radius: 50%; box-shadow: 0 0 0 4px rgba(27,119,231,.1); }
  .timeline-content { display: flex; gap: 12px; align-items: baseline; }
  .timeline li strong { color: #1b77e7; font-weight: 800; font-size: 1.05rem; min-width: 120px; }
  .timeline-text { color: #475467; }

  .checklist { margin: 0; padding-left: 0; list-style: none; display: grid; gap: 8px; }
  .checklist li { display: flex; gap: 10px; align-items: center; }
  .checklist span { display: inline-flex; width: 22px; height: 22px; align-items: center; justify-content: center; border-radius: 50%; background: #10b981; color: white; font-weight: 900; }

  
</style>

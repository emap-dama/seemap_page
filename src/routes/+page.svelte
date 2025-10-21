<script>
  import ScrollSection from '$lib/components/ScrollSection.svelte';
  import InscriptionForm from '$lib/components/InscriptionForm.svelte';
  import Programacao from '$lib/components/Programacao.svelte';

  import { assets } from '$app/paths';
  
  let submitted = false;

</script>

<ScrollSection stepClass="scroll-step" offset={0.5}>

  <!-- Hero -->
  <section class="hero scroll-step" aria-labelledby="hero-title">
    <div class="hero-background" aria-hidden="true">
      <div class="hero-overlay" aria-hidden="true"></div>
      <img
        src="https://images.unsplash.com/photo-1483729558449-99ef09a8c325?w=1920&q=80"
        srcset="
          https://images.unsplash.com/photo-1483729558449-99ef09a8c325?w=800&q=70 800w,
          https://images.unsplash.com/photo-1483729558449-99ef09a8c325?w=1280&q=75 1280w,
          https://images.unsplash.com/photo-1483729558449-99ef09a8c325?w=1920&q=80 1920w
        "
        sizes="100vw"
        alt="Vista aérea do Rio de Janeiro"
        class="hero-bg-image"
        decoding="async"
        fetchpriority="high"
      />
    </div>
    <div class="hero-content container">
      <div class="hero-title-wrapper">
        <img
          src={`${assets}/favicon.png`}
          alt="Logomarca da EMAp"
          class="hero-favicon"
          width="200"
          height="200"
        />
        <div class="hero-copy">
          <p class="tag">Reserve na agenda</p>
          <h1 id="hero-title">Semana de Extensão<br>da EMAp</h1>
          <h2 class="date" aria-describedby="hero-title">3 a 5 de novembro</h2>
          <p class="subtitle">Palestras, workshops e atividades na EMAp. Vagas limitadas.</p>
          <a href="#inscricao" class="cta">
            <span>Inscrever-me</span>
            <svg width="20" height="20" viewBox="0 0 20 20" fill="none" aria-hidden="true" focusable="false">
              <path d="M7.5 15L12.5 10L7.5 5" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
        </div>
      </div>
    </div>
  </section>

  <!-- Programação -->
  <section id="programacao" class="container card gradient-border scroll-step" aria-labelledby="programacao-title">
    <div class="card-header">
      <!-- <h3 id="programacao-title">Programação</h3>-->
      <p class="card-subtitle">A SEEMAp (Semana de Extensão da EMAp) é um evento que procura reunir os
corpos discente e docente da EMAp para discutir sobre áreas de interesse na
matemática e na computação por meio de palestras, minicursos, workshops e
apresentações.</p>
    </div>
    <h4 >Programação</h4>
    <Programacao />
  </section>

  <!-- Apoio -->
  <section id="apoio" class="container card scroll-step" aria-labelledby="apoio-title">
    <div class="card-header">
      <h3 id="apoio-title">Organização</h3>  
    </div>
    <div class="grid" role="list">
      <article class="apoio-card" role="listitem">
        <div class="apoio-avatar" aria-hidden="true">
          <img 
            src="https://emap.fgv.br/sites/default/files/2020-12/dama.jpg"
            alt="Logomarca do DAMA"
            class="avatar-image"
            loading="lazy"
            decoding="async"
          />
        </div>
        <h4>Diretório Acadêmico de Matemática Aplicada (DAMA)</h4>
      </article>
      <article class="apoio-card" role="listitem">
        <div class="apoio-avatar" aria-hidden="true">
          <img 
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQDx9dfF_w93CljtP6ujtLdCt6JBTiiNb_ISg&s"
            alt="Logomarca da Escola de Matemática Aplicada"
            class="avatar-image"
            loading="lazy"
            decoding="async"
          />
        </div>
        <h4>Escola de Matemática Aplicada (EMAp/FGV)</h4>
      </article>
    </div>
  </section>

  <!-- Palestrantes 
  <section id="palestrantes" class="container card scroll-step" aria-labelledby="palestrantes-title">
    <div class="card-header">
      <h3 id="palestrantes-title">Palestrantes</h3>
      <p class="card-subtitle">Conheça quem vai compartilhar conhecimento</p>
    </div>
    <div class="grid" role="list">
      <article class="speaker-card" role="listitem">
        <div class="speaker-avatar" aria-hidden="true"><span>C1</span></div>
        <h4>Convidado(a) 1</h4>
        <p class="muted">Área / Instituição</p>
      </article>
      <article class="speaker-card" role="listitem">
        <div class="speaker-avatar" aria-hidden="true"><span>C2</span></div>
        <h4>Convidado(a) 2</h4>
        <p class="muted">Área / Instituição</p>
      </article>
      <article class="speaker-card" role="listitem">
        <div class="speaker-avatar" aria-hidden="true"><span>C3</span></div>
        <h4>Convidado(a) 3</h4>
        <p class="muted">Área / Instituição</p>
      </article>
    </div>
  </section>-->

  <section id="trabalhos" class="container card scroll-step" aria-labelledby="trabalhos-title">
    <div class="card-header">
      <h3 id="trabalhos-title">Envie seu Trabalhos</h3>
      <p class="card-subtitle">Alunos podem submeter seus trabalhos para apresentação durante a SEEMAp.</p>
    </div>
    <a href="/semap_alunos" class="cta secondary">Enviar meu trabalho</a>
  </section>


  <!-- Local -->
  <section id="local" class="container card scroll-step" aria-labelledby="local-title">
    <div class="card-header">
      <h3 id="local-title">Local</h3>
      <p class="card-subtitle">Venha nos visitar</p>
    </div>
    <p>Endereço da EMAp — Rio de Janeiro, Brasil.</p>
    <iframe
      title="Mapa da EMAp"
      style="width:100%;height:350px;border:0;border-radius:12px;margin-top:16px"
      loading="lazy"
      allowfullscreen
      referrerpolicy="no-referrer-when-downgrade"
      src="https://www.google.com/maps?q=Praia+de+Botafogo,+190+-+Botafogo,+Rio+de+Janeiro+-+RJ,+22250-900&output=embed">
    </iframe>
  </section>

  <!-- Inscrição -->
  <section id="inscricao" class="container card highlight-card scroll-step" aria-labelledby="inscricao-title">
    <InscriptionForm />
  </section>

  <section id="inscricao" class="container card highlight-card scroll-step" aria-labelledby="inscricao-title">
  
    {#if submitted}
      <div class="notice success" role="status" aria-live="polite">
        Pré-inscrição enviada! Em breve entraremos em contato por e-mail.
      </div>
    {/if}

  </section>

</ScrollSection>

<style>
  section[id] { scroll-margin-top: 84px; }

  .container {
    width: min(100% - 32px, 1080px);
    margin-inline: auto;
  }

  img { max-width: 100%; height: auto; display: block; }

  .hero { 
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    overflow: hidden;
  }

  .hero-background {
    position: absolute;
    inset: 0;
    z-index: 0;
  }

  .hero-bg-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }
  
  .hero-overlay {
    position: absolute;
    inset: 0;
    background: rgba(0, 27, 59, 0.705);
    z-index: 1;
  }

  .hero-content {
    position: relative;
    z-index: 2;
    width: 100%;
    padding: 80px 0;
  }

  .hero-title-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;
    flex-wrap: wrap;
  }

  .hero-favicon {
    width: clamp(180px, 27vw, 396px);
    height: auto;
    flex-shrink: 0;
    
  }

  .hero-title-wrapper {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 40px;
    max-width: 1200px;
    margin: 0 auto;
  }

  .hero-copy {
    text-align: center;
  }

  .hero-copy h1 {
    margin: 0 0 16px;
    font-size: clamp(2.5rem, 5vw, 4rem);
    font-weight: 900;
    color: #ffffff;
    line-height: 1.1;
    text-shadow: 0 4px 30px rgba(0, 0, 0, 0.8), 0 2px 10px rgba(0, 0, 0, 0.5);
  }

  .hero-copy .date {
    margin: 0 0 24px;
    font-size: clamp(2rem, 4vw, 3.2rem);
    font-weight: 800;
    color: #ffffff;
    text-shadow: 0 2px 20px rgba(0, 0, 0, 0.3);
  }

  .hero-copy .subtitle {
    margin: 0 0 32px;
    line-height: 1.7;
    font-size: 1.2rem;
    color: rgba(255, 255, 255, 0.95);
    text-shadow: 0 1px 10px rgba(0, 0, 0, 0.3);
  }

  .tag { 
    text-transform: uppercase; 
    letter-spacing: 0.16em; 
    font-weight: 800; 
    color: #3cff00fd; 
    margin: 0 0 16px; 
    font-size: 0.9rem;
    display: inline-block;
    text-shadow: 0 1px 10px rgba(0, 0, 0, 0.575);
  }

  .cta { 
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 16px 32px; 
    background: #ffffff;
    color: #1b77e7; 
    border-radius: 14px; 
    text-decoration: none; 
    font-weight: 700;
    font-size: 1.1rem;
    transition: transform 0.3s ease, box-shadow 0.3s ease, background 0.3s ease;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
  }

  .cta:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.3);
    background: #f0f9ff;
  }

  .cta svg { 
    transition: transform 0.3s ease; 
  }
  
  .cta:hover svg { 
    transform: translateX(4px); 
  }

  @media (max-width: 768px) {
    .hero-title-wrapper {
      flex-direction: column;
      text-align: center;
      gap: 24px;
    }
    
    .hero-favicon {
      width: clamp(100px, 20vw, 160px);
    }
  }

  .card { 
    margin-bottom: 32px; 
    padding: 40px;
    background: #ffffff;
    border-radius: 20px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
    transition: box-shadow 0.3s ease, transform 0.3s ease;
  }
  
  .card:hover { 
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12); 
    transform: translateY(-2px); 
  }

  .gradient-border {
    position: relative;
    border: 2px solid transparent;
    background-image: linear-gradient(#ffffff, #ffffff), linear-gradient(135deg, #1b77e7, #0ea5e9);
    background-origin: border-box;
    background-clip: padding-box, border-box;
  }

  .highlight-card { 
    background: linear-gradient(135deg, #f0f9ff 0%, #f8fafc 100%); 
  }

  .card-header { margin-bottom: 24px; }

  .card h3 { 
    margin: 0 0 8px; 
    font-size: 2rem; 
    font-weight: 800; 
  }
  
  .card-subtitle { 
    color: #667085; 
    margin: 0; 
    font-size: 1rem; 
  }

  .timeline { 
    line-height: 1.9; 
    margin: 0; 
    padding-left: 0; 
    list-style: none;
  }

  .timeline li { 
    position: relative; 
    padding-left: 40px; 
    margin-bottom: 24px; 
  }

  .timeline-marker {
    position: absolute;
    left: 0;
    top: 4px;
    width: 16px;
    height: 16px;
    background: linear-gradient(135deg, #1b77e7 0%, #0ea5e9 100%);
    border-radius: 50%;
    box-shadow: 0 0 0 4px rgba(27, 119, 231, 0.1);
  }

  .timeline-content { 
    display: flex; 
    gap: 12px; 
    align-items: baseline; 
  }

  .timeline li strong { 
    color: #1b77e7; 
    font-weight: 800; 
    font-size: 1.05rem; 
    min-width: 60px; 
  }

  .timeline-text { color: #475467; }

  .grid { 
    display: grid; 
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); 
    gap: 20px; 
  }

  .apoio-card {
    padding: 24px;
    background: #ffffff;
    border: 2px solid #f0f4f8;
    border-radius: 16px;
    transition: box-shadow 0.3s ease, transform 0.3s ease, border-color 0.3s ease;
    text-align: center;
  }

  .apoio-card:hover { 
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1); 
    transform: translateY(-4px); 
    border-color: #1b77e7; 
  }

  .apoio-avatar { 
    width: 200px; 
    height: 200px; 
    margin: 0 auto 16px; 
    border-radius: 50%; 
    overflow: hidden;
    background: linear-gradient(135deg, #1b77e7 0%, #0ea5e9 100%); 
    box-shadow: 0 4px 20px rgba(27, 119, 231, 0.3); 
  }

  .avatar-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .apoio-card h4 { 
    margin: 0 0 8px; 
    font-size: 1.25rem; 
    font-weight: 700; 
  }

  .speaker-card { 
    padding: 24px; 
    background: #ffffff; 
    border: 2px solid #f0f4f8; 
    border-radius: 16px; 
    transition: box-shadow 0.3s ease, transform 0.3s ease, border-color 0.3s ease; 
    text-align: center; 
  }

  .speaker-card:hover { 
    box-shadow: 0 8px 24px rgba(0, 0, 0, 0.1); 
    transform: translateY(-4px); 
    border-color: #1b77e7; 
  }

  .speaker-avatar { 
    width: 80px; 
    height: 80px; 
    margin: 0 auto 16px; 
    border-radius: 50%; 
    background: linear-gradient(135deg, #1b77e7 0%, #0ea5e9 100%); 
    display: flex; 
    align-items: center; 
    justify-content: center; 
    font-weight: 800; 
    font-size: 1.5rem; 
    color: white; 
    box-shadow: 0 4px 20px rgba(27, 119, 231, 0.3); 
  }

  .speaker-card h4 { 
    margin: 0 0 8px; 
    font-size: 1.25rem; 
    font-weight: 700; 
  }

  .muted { 
    color: #667085; 
    margin: 0; 
    font-size: 0.95rem; 
  }

  @media (max-width: 880px) { 
    .hero { min-height: 500px; }
    .hero-content { padding: 60px 0; }
    .timeline li { padding-left: 32px; }
    .timeline-content { flex-direction: column; gap: 4px; }
  }
</style>
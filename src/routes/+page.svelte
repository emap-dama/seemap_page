<script>
  import { base } from '$app/paths';
  import RegistrationForm from '$lib/components/RegistrationForm.svelte';
</script>

<section class="hero">
  <div class="hero-background">
    <div class="hero-overlay"></div>
    <img 
      src="https://images.unsplash.com/photo-1483729558449-99ef09a8c325?w=1920&q=80" 
      alt="Rio de Janeiro" 
      class="hero-bg-image"
    />
  </div>
  <div class="hero-content container">
    <div class="hero-copy">
      <p class="tag">Save the date</p>
      <h1>Semana de Extensão da EMAp</h1>
      <h2 class="date">3 a 5 de novembro</h2>
      <p class="subtitle">Palestras, workshops e atividades na EMAp. Vagas limitadas.</p>
      <a href="#inscricao" class="cta">
        <span>Inscrever-me</span>
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M7.5 15L12.5 10L7.5 5" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </a>
    </div>
  </div>
</section>

<section class="container card gradient-border" id="programacao">
  <div class="card-header">
    <h3>Programação</h3>
    <p class="card-subtitle">Agenda completa do evento</p>
  </div>
  <ul class="timeline">
    <li>
      <div class="timeline-marker"></div>
      <div class="timeline-content">
        <strong>3 nov</strong>
        <span class="timeline-text">Abertura + Palestra Principal</span>
      </div>
    </li>
    <li>
      <div class="timeline-marker"></div>
      <div class="timeline-content">
        <strong>4 nov</strong>
        <span class="timeline-text">Workshops e mesas redondas</span>
      </div>
    </li>
    <li>
      <div class="timeline-marker"></div>
      <div class="timeline-content">
        <strong>5 nov</strong>
        <span class="timeline-text">Apresentações e encerramento</span>
      </div>
    </li>
  </ul>
</section>

<section class="container card" id="apoio">
  <div class="card-header">
    <h3>Apoio e Organização</h3>  
  </div>

  <div class="grid">
    <article class="apoio-card">
      <div class="apoio-avatar">
        <img src= "https://emap.fgv.br/sites/default/files/2020-12/dama.jpg"
             alt="Dama"
             class="avatar-image"
        />
      </div>
      <h4>Directorio Académico de Gatos</h4>
    </article>
    <article class="apoio-card">
      <div class="apoio-avatar">
        <img src= "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQDx9dfF_w93CljtP6ujtLdCt6JBTiiNb_ISg&s"
             alt="FgvEmap"
             class="avatar-image"
        />
      </div>
      <h4>Escola de Matemática Aplicada</h4>
    </article>
  </div>
</section>

<section class="container card" id="palestrantes">
  <div class="card-header">
    <h3>Palestrantes</h3>
    <p class="card-subtitle">Conheça quem vai compartilhar conhecimento</p>
  </div>
  <div class="grid">
    <article class="speaker-card">
      <div class="speaker-avatar">
        <span>C1</span>
      </div>
      <h4>Convidado/a 1</h4>
      <p class="muted">Área / Instituição</p>
    </article>
    <article class="speaker-card">
      <div class="speaker-avatar">
        <span>C2</span>
      </div>
      <h4>Convidado/a 2</h4>
      <p class="muted">Área / Instituição</p>
    </article>
    <article class="speaker-card">
      <div class="speaker-avatar">
        <span>C3</span>
      </div>
      <h4>Convidado/a 3</h4>
      <p class="muted">Área / Instituição</p>
    </article>
  </div>
</section>



<section class="container card" id="local">
  <div class="card-header">
    <h3>Local</h3>
    <p class="card-subtitle">Venha nos visitar</p>
  </div>
  <p>Endereço da EMAp — Cidade, País.</p>
  <iframe
    title="Mapa"
    style="width:100%;height:350px;border:0;border-radius:12px;margin-top:16px"
    loading="lazy"
    allowfullscreen
    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3673.1156!2d-43.2305!3d-22.9068!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMjLCsDU0JzI0LjUiUyA0M8KwMTMnNDkuOCJX!5e0!3m2!1sen!2sbr!4v1234567890">
  </iframe>
</section>

<section class="container card highlight-card" id="inscricao">
  <div class="card-header">
    <h3>Inscrição</h3>
    <p class="card-subtitle">Preencha o formulário para reservar sua vaga.</p>
  </div>
  <RegistrationForm />
</section>

<style>
  .hero { 
    position: relative;
    min-height: 600px;
    display: flex;
    align-items: center;
    overflow: hidden;
  }

  .hero-background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 0;
  }

  .hero-bg-image {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }
  
  .avatar-image{
    width: 100%;
    height: 100%;
    border-radius: 50%;
    object-fit: cover;
  }

  .hero-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(27, 119, 231, 0.65);
    z-index: 1;
  }

  .hero-content {
    position: relative;
    z-index: 2;
    width: 100%;
    padding-top: 80px;
    padding-bottom: 80px;
    text-align: center;
  }

  .hero-copy {
    max-width: 700px;
  }

  .hero-copy h1 { 
    font-size: clamp(2.5rem, 5vw, 4rem); 
    margin: 0 0 16px; 
    line-height: 1.1;
    font-weight: 900;
    color: #ffffff;
    text-shadow: 0 2px 20px rgba(0, 0, 0, 0.3);
    text-align: center;
  }

  .hero-copy .date { 
    font-size: clamp(2rem, 4vw, 3.2rem); 
    margin: 0 0 24px; 
    color: #ffffff;
    font-weight: 800;
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
    margin-top: 8px; 
    padding: 16px 32px; 
    background: #ffffff;
    color: #1b77e7; 
    border-radius: 14px; 
    text-decoration: none; 
    font-weight: 700;
    font-size: 1.1rem;
    transition: all 0.3s ease;
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

  .card {
    margin-bottom: 32px;
    transition: all 0.3s ease;
  }

  .card:hover {
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
  }

  .gradient-border {
    position: relative;
    border: 2px solid transparent;
    background-image: linear-gradient(#f8fafc, #f8fafc), linear-gradient(135deg, #1b77e7, #0ea5e9);
    background-origin: border-box;
    background-clip: padding-box, border-box;
  }

  .highlight-card {
    background: linear-gradient(135deg, #f0f9ff 0%, #f8fafc 100%);
  }

  .card-header {
    margin-bottom: 24px;
  }

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

  .timeline-text {
    color: #475467;
  }

  .grid { 
    display: grid; 
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); 
    gap: 20px; 
  }

  .apoio-card{
    padding: 24px;
    background: #ffffff;
    border: 2px solid #f0f4f8;
    border-radius: 16px;
    transition: all 0.3s ease;
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
    background: linear-gradient(135deg, #1b77e7 0%, #0ea5e9 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 800;
    font-size: 1.5rem;
    color: rgb(0, 0, 0);
    box-shadow: 0 4px 20px rgba(27, 119, 231, 0.3);
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
    transition: all 0.3s ease;
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
    .hero {
      min-height: 500px;
    }

    .hero-content {
      padding-top: 60px;
      padding-bottom: 60px;
    }

    .hero-copy h1 {
      font-size: 2rem;
    }

    .hero-copy .date {
      font-size: 1.8rem;
    }

    .timeline li {
      padding-left: 32px;
    }

    .timeline-content {
      flex-direction: column;
      gap: 4px;
    }
  }
</style>
<svelte:head>
  <title>SEEMAp — 3 a 5 de novembro</title>
  <meta name="description" content="Semana de Extensão da EMap — 3 a 5 de novembro. Inscrições, programação e informações do evento." />
  <meta property="og:title" content="SEEMAp — 3 a 5 de novembro" />
  <meta property="og:description" content="Inscrições, programação e informações do evento." />
  <meta property="og:image" content="/hero-seemap.png" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
</svelte:head>

<div class="site">
  <header>
    <div class="header-container container">
      <a class="brand" href="/">SEEMAp</a>
      <nav>
        <a href="#programacao">Programação</a>
        <a href="#palestrantes">Palestrantes</a>
        <a href="#local">Sede</a>
        <a href="#inscricao" class="btn">Inscrever-me</a>
      </nav>
    </div>
  </header>

  <slot />

  <footer class="container footer">
    <p>© {new Date().getFullYear()} SEEMAp · 3–5 nov</p>
  </footer>
</div>

<style>
  :root {
    --bg:#ffffff; 
    --ink:#101828; 
    --muted:#475467; 
    --primary:#1b77e7; 
    --card:#f8fafc;
  }
  
  * { 
    box-sizing: border-box; 
  }


  
  :global(body), :global(html), .site { 
    margin:0; 
    padding:0; 
    background:var(--bg); 
    color:var(--ink); 
    font-family: system-ui, -apple-system, Segoe UI, Roboto, Ubuntu, Cantarell, Noto Sans, Arial, "Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol"; 
  }

  .container { 
    max-width: 1050px; 
    margin: 0 auto; 
    padding: 0 24px; 
  }
  
  header { 
    position: sticky; 
    top: 0; 
    background: rgba(255,255,255, 0.85); 
    backdrop-filter: blur(12px); 
    border-bottom: 1px solid #eef2f7; 
    z-index: 100;
    padding: 16px 0;
  }

  .header-container {
    display: flex; 
    align-items: center; 
    justify-content: space-between; 
    gap: 12px;
  }
  
  .brand { 
    font-weight: 800; 
    letter-spacing: 0.4px; 
    text-decoration: none; 
    color: var(--ink); 
    font-size: 1.3rem; 
  }
  
  nav { 
    display: flex;
    align-items: center;
    gap: 8px;
  }

  nav a { 
    color: var(--ink); 
    text-decoration: none; 
    font-weight: 600;
    padding: 8px 12px;
    border-radius: 8px;
    transition: all 0.2s ease;
  }

  nav a:hover:not(.btn) {
    background: #f0f4f8;
  }
  
  .btn { 
    padding: 10px 18px; 
    border-radius: 10px; 
    background: var(--primary); 
    color: #fff;
    font-weight: 700;
  }

  .btn:hover {
    background: #1557b0;
    transform: translateY(-1px);
  }
  
  .footer { 
    color: var(--muted); 
    font-size: 0.95rem; 
    border-top: 1px solid #eef2f7; 
    margin-top: 48px;
    padding-top: 32px;
    padding-bottom: 32px;
    text-align: center;
  }
  
  :global(img) { 
    max-width: 100%; 
    height: auto; 
  }
  
  :global(.card) { 
    background: var(--card); 
    border: 1px solid #e6eaf0; 
    border-radius: 16px; 
    padding: 32px; 
  }

  @media (max-width: 768px) {
    nav {
      gap: 4px;
    }

    nav a {
      font-size: 0.9rem;
      padding: 6px 8px;
    }

    .btn {
      padding: 8px 14px;
    }

    .brand {
      font-size: 1.1rem;
    }
  }
</style>
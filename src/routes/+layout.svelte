<script>
  export let data;
</script>

<svelte:head>
  <title>SEEMAp — 3 a 5 de novembro</title>
  <meta name="description" content="Semana de Extensão da EMap — 3 a 5 de novembro. Inscrições, programação e informações do evento." />
  <meta property="og:title" content="SEEMAp — 3 a 5 de novembro" />
  <meta property="og:description" content="Inscrições, programação e informações do evento." />
  <meta property="og:image" content="/hero-seemap.png" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
</svelte:head>

<div class="site">
  <header class="container">
    <a class="brand" href="/">SEEMAp</a>
    <nav>
      <a href="#programacao">Programación</a>
      <a href="#palestrantes">Oradores</a>
      <a href="#local">Sede</a>
      <a href="#inscricao" class="btn">Inscribirme</a>
    </nav>
  </header>

  <slot />

  <footer class="container footer">
    <p>© {new Date().getFullYear()} SEEMAp • 3–5 nov</p>
  </footer>
</div>

<style>
  :root {
    --bg:#ffffff; --ink:#101828; --muted:#475467; --primary:#1b77e7; --card:#f8fafc;
  }
  * { box-sizing: border-box; }
  body, html, .site { margin:0; padding:0; background:var(--bg); color:var(--ink); font-family: system-ui, -apple-system, Segoe UI, Roboto, Ubuntu, Cantarell, Noto Sans, Arial, "Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol"; }
  .container { max-width: 1050px; margin: 0 auto; padding: 16px; }
  header { display:flex; align-items:center; justify-content:space-between; gap:12px; position: sticky; top:0; background:rgba(255,255,255,.75); backdrop-filter: blur(8px); border-bottom:1px solid #eef2f7; z-index: 10; }
  .brand { font-weight:800; letter-spacing:.4px; text-decoration:none; color:var(--ink); font-size: 1.15rem; }
  nav a { color: var(--ink); text-decoration:none; margin-left: 10px; font-weight: 600; }
  .btn { padding:8px 12px; border-radius:10px; background:var(--primary); color:#fff; }
  .footer { color: var(--muted); font-size: .95rem; border-top:1px solid #eef2f7; margin-top:32px; }
  img { max-width:100%; height:auto; }
  .card { background:var(--card); border:1px solid #e6eaf0; border-radius:16px; padding:20px; }
</style>

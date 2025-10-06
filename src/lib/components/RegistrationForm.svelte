<script>
  const ENDPOINT = "https://script.google.com/macros/s/AKfycbzh5EyeLHdO9TY49kmUSxX_FBM_04XPU19qaPyOCSffLiZ90is_IZTQLmF95Bna_Drx/exec";

  let form = { nome:'', email:'', instituicao:'', degree:'', comments:'' };
  let status = 'idle';   
  let errorMsg = '';

  async function submit(e) {
    e.preventDefault();
    status = 'sending';

    const fd = new FormData();
    Object.entries(form).forEach(([k, v]) => fd.append(k, v));

    try {
      await fetch(ENDPOINT, { method: 'POST', body: fd });
      status = 'ok';
      form = { nome:'', email:'', instituicao:'', degree:'', comments:'' };
    } catch (err) {
      status = 'error';
      errorMsg = String(err);
    }
  }
</script>


<form class="reg-form" on:submit={submit}>
  <input placeholder="Nome" bind:value={form.nome} required />
  <input type="email" placeholder="Email" bind:value={form.email} required />
  <input placeholder="Instituição" bind:value={form.instituicao} />
  <input placeholder="Degree" bind:value={form.degree} />
  <textarea placeholder="Comments" bind:value={form.comments}></textarea>
  <button disabled={status==='sending'}>
    {status==='sending' ? 'Enviando…' : 'Enviar inscripción'}
  </button>

  {#if status==='ok'}<p class="ok">¡Inscripción enviada, recibirás uma confirmação de se vc foi aceito em breba!</p>{/if}
  {#if status==='error'}<p class="err">Ocurrió un error al enviar.</p>{/if}
</form>

<style>
  .reg-form { display:grid; gap:12px; max-width:500px; }
  input, textarea { padding:10px 12px; border:1px solid #dce3ec; border-radius:10px; font:inherit; }
  button { background:#0ea5e9; color:#fff; border:0; padding:12px 16px; border-radius:12px; cursor:pointer; font-weight:700; }
  .ok { color:#15803d; }
  .err { color:#b91c1c; }
</style>

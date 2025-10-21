<script>
  const ENDPOINT = "https://script.google.com/macros/s/AKfycbywuHuYk_G6FOiBc2hwHaA6paB7lilWEeHrp5b8D1RTsGvqM8z042i3XVcBNsmYOtriaQ/exec";

  let form = { nome:'', email:'', instituicao:'', degree:'', comments:'' };
  let status = 'idle';
  let errorMsg = '';
  let file = null; // archivo seleccionado

  function fileToBase64(file) {
    return new Promise((resolve, reject) => {
      const fr = new FileReader();
      fr.onload = () => {
        // fr.result = "data:<mime>;base64,AAAA..."
        const base64 = fr.result.toString().split(',')[1]; // quitamos el prefijo data:
        resolve(base64);
      };
      fr.onerror = reject;
      fr.readAsDataURL(file);
    });
  }

  async function submit(e) {
    e.preventDefault();
    status = 'sending';
    errorMsg = '';

    try {
      if (!file) throw new Error('Escolhe um arquivo.');

      // Convertir archivo a Base64
      const fileBase64 = await fileToBase64(file);

      // Construir payload como x-www-form-urlencoded (Apps Script lo parsea perfecto)
      const params = new URLSearchParams({
        nome: form.nome || '',
        email: form.email || '',
        instituicao: form.instituicao || '',
        degree: form.degree || '',
        comments: form.comments || '',
        fileName: file.name,
        fileType: file.type || 'application/octet-stream',
        fileBase64 // sin el prefijo "data:...;base64,"
      });

      const res = await fetch(ENDPOINT, {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded;charset=UTF-8' },
        body: params.toString()
      });

      const json = await res.json().catch(() => ({}));
      if (!res.ok || !json.ok) {
        throw new Error(json.error || `HTTP ${res.status}`);
      }

      status = 'ok';
      form = { nome:'', email:'', instituicao:'', degree:'', comments:'' };
      file = null;
      
      const fi = document.getElementById('file-input');
      if (fi) fi.value = '';
    } catch (err) {
      status = 'error';
      errorMsg = String(err?.message || err);
    }
  }
</script>

<form class="reg-form" on:submit={submit}>
  <input placeholder="Nome" bind:value={form.nome} required />
  <input type="email" placeholder="Email" bind:value={form.email} required />
  <input placeholder="Instituição" bind:value={form.instituicao} />
  <input placeholder="Periodo(Indicar se é pos)" bind:value={form.degree} />
  <textarea placeholder="Descrição (Envie abaixo seu resumo)" bind:value={form.comments}></textarea>

  <input
    placeholder="Arquivo"
    id="file-input"
    type="file"
    accept="*/*"
    on:change={(e) => file = e.currentTarget.files?.[0] || null}
    required
  />

  <button disabled={status==='sending'}>
    {status==='sending' ? 'Enviando…' : 'Enviar inscripción'}
  </button>

  {#if status==='ok'}
    <p class="ok">Cadastro enviado! Você receberá uma confirmação em breve.</p>
  {/if}
  {#if status==='error'}
    <p class="err">Ocorreu um erro ao enviar: {errorMsg}</p>
  {/if}
</form>

<style>
  .reg-form { display:grid; gap:12px; max-width:500px; }
  input, textarea { padding:10px 12px; border:1px solid #dce3ec; border-radius:10px; font:inherit; }
  button { background:#0ea5e9; color:#fff; border:0; padding:12px 16px; border-radius:12px; cursor:pointer; font-weight:700; }
  .ok { color:#15803d; }
  .err { color:#b91c1c; }
</style>

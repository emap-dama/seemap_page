<script>
  let selectedTalk = null;
  
  const schedule = {
    timeSlots: [
      { time: '14:00 - 15:30', slot: 'session1' },
      { time: '15:30 - 17:00', slot: 'session2' },
      { time: '17:00 - 18:30', slot: 'session3' },
      { time: '18:30 - 20:00', slot: 'session4' }
    ],
    days: [
      {
        day: '3',
        date: 'Novembro',
        dayName: 'Segunda',
        sessions: {
          session1: {
            title: 'Os impactos da Matemática e da Ciência de Dados no Mercado Financeiro',
            speaker: 'Olhe o Instagram do DAMA para descobrir o palestrante',
            abstract: 'Nesta palestra, exploraremos como a matemática avançada e técnicas de ciência de dados estão revolucionando o mercado financeiro. Discutiremos aplicações práticas de machine learning, análise de séries temporais e modelos estocásticos no trading, gestão de risco e previsão de mercados.',
            room: 'A confirmar',
            color: 'blue'
          },
          session2: {
            title: 'Vizagrams: um mergulho na teoria de visualização de dados e uma proposta de avanço',
            speaker: 'Olhe o Instagram do DAMA para descobrir o palestrante',
            abstract: 'Uma análise profunda sobre as teorias fundamentais da visualização de dados e uma proposta inovadora chamada Vizagrams. Veremos como representações visuais podem transformar dados complexos em insights compreensíveis.',
            room: 'A confirmar',
            color: 'green'
          },
          session3: {
            title: 'Dou-lhe uma, dou-lhe duas... vendido para aquele robô!',
            speaker: 'Olhe o Instagram do DAMA para descobrir o palestrante',
            abstract: 'A matemática dos leilões',
            room: 'A confirmar',
            color: 'pink'
          },
          session4: {
            title: 'Teoremas de Existência: da Fórmula de Bhaskara à SVD',
            speaker: 'Olhe o Instagram do DAMA para descobrir o palestrante',
            abstract: '',
            room: 'A confirmar',
            color: 'pink'
          }
        }
      },
      {
        day: '4',
        date: 'Novembro',
        dayName: 'Terça',
        sessions: {
          session1: {
            title: 'Não importa o que você faça, se souber Matemática fará melhor!',
            speaker: 'Olhe o Instagram do DAMA para descobrir o palestrante',
            abstract: 'Uma palestra inspiradora sobre como o conhecimento matemático é uma ferramenta universal. Discutiremos casos práticos onde a matemática fez a diferença em diversos campos.',
            room: 'A confirmar',
            color: 'blue'
          },
          session2: {
            title: 'Estamos passando por uma instabilidade em nosso sistema',
            speaker: 'Olhe o Instagram do DAMA para descobrir o palestrante',
            abstract: 'Diferentes aplicações podem ser descritas por um sistemas de equações. Nessa apresentação vamos apresentar quais são os possíveis casos de instabilidade que podem surgir durante o estudo de um sistema. Comentando situações que envolvem sistemas lineares simples, sistemas obtidos para aproximações numéricas, até sistemas dinâmicos mais complexos.',
            room: 'A confirmar',
            color: 'green'
          },
          session3: {
            title: 'Princípio da Casa dos Pombos',
            speaker: 'Olhe o Instagram do DAMA para descobrir o palestrante',
            abstract: 'Uma exploração fascinante de um dos princípios mais elegantes e poderosos da matemática discreta. Veremos aplicações surpreendentes em diversas áreas.',
            room: 'A confirmar',
            color: 'pink'
          }
        }
      },
      {
        day: '5',
        date: 'Novembro',
        dayName: 'Quarta',
        sessions: {
          session1: {
            title: 'Apresentação de alunos',
            speaker: 'Alunos Participantes',
            abstract: 'Momento especial onde os alunos apresentarão seus trabalhos, pesquisas e projetos desenvolvidos.',
            room: 'A confirmar',
            color: 'yellow'
          },
          session2: {
            title: 'Olimpíadas de matemática no Brasil',
            speaker: 'Palestrantes Surpresa',
            abstract: 'Mesa redonda sobre o universo das olimpíadas de matemática no Brasil. Discussão sobre a importância dessas competições no desenvolvimento de talentos.',
            room: 'A confirmar',
            color: 'blue'
          },
          session3: {
            title: 'Coffee Break Final',
            speaker: '',
            abstract: 'Momento de descontração e networking! Aproveite para conhecer outros participantes, trocar experiências e fazer novas conexões.',
            room: 'Área de convivência',
            color: 'green'
          }
        }
      }
    ]
  };

  function openModal(session) {
    if (session && session.type !== 'break') {
      selectedTalk = session;
    }
  }

  function closeModal() {
    selectedTalk = null;
  }

  function handleKeydown(event) {
    if (event.key === 'Escape') {
      closeModal();
    }
  }
</script>

<svelte:window on:keydown={handleKeydown} />

<div class="schedule-table-wrapper">
  <table class="schedule-table">
    <thead>
      <tr>
        <th class="time-column"></th>
        {#each schedule.days as day}
          <th class="day-header">
            <div class="day-number">Dia {day.day}</div>
            <div class="day-name">{day.dayName}</div>
          </th>
        {/each}
      </tr>
    </thead>
    <tbody>
      {#each schedule.timeSlots as slot}
        <tr>
          <td class="time-cell">{slot.time}</td>
          {#each schedule.days as day}
            <td class="session-cell">
              {#if day.sessions[slot.slot]}
                {#if day.sessions[slot.slot].type === 'break'}
                  <div class="break-cell">
                    {day.sessions[slot.slot].title}
                  </div>
                {:else}
                  <button 
                    class="session-card {day.sessions[slot.slot].color}"
                    on:click={() => openModal(day.sessions[slot.slot])}
                  >
                    <div class="session-title">{day.sessions[slot.slot].title}</div>
                    <div class="session-speaker">{day.sessions[slot.slot].speaker}</div>
                  </button>
                {/if}
              {/if}
            </td>
          {/each}
        </tr>
      {/each}
    </tbody>
  </table>
</div>

{#if selectedTalk}
  <div class="modal-overlay" on:click={closeModal}>
    <div class="modal" on:click|stopPropagation>
      <button class="close-btn" on:click={closeModal} aria-label="Fechar">✕</button>
      
      <div class="modal-header">
        <h3>{selectedTalk.title}</h3>
        <div class="modal-speaker">{selectedTalk.speaker}</div>
      </div>

      <div class="modal-body">
        <div class="modal-section">
          <h4>Resumo</h4>
          <p>{selectedTalk.abstract}</p>
        </div>

        <div class="modal-section">
          <h4>Local</h4>
          <p class="room-badge">{selectedTalk.room}</p>
        </div>
      </div>
    </div>
  </div>
{/if}

<style>
  .schedule-table-wrapper {
    overflow-x: auto;
    margin: 0 -20px;
    padding: 0 20px;
  }

  .schedule-table {
    width: 100%;
    border-collapse: separate;
    border-spacing: 0;
    font-size: 0.95rem;
  }

  thead th {
    background: #1b77e7;
    color: white;
    padding: 20px 12px;
    text-align: center;
    font-weight: 700;
    border: 2px solid white;
    position: sticky;
    top: 0;
    z-index: 10;
  }

  .time-column {
    width: 120px;
    background: #0d3a6f !important;
  }

  .day-header {
    min-width: 200px;
  }

  .day-number {
    font-size: 1.1rem;
    font-weight: 800;
    margin-bottom: 4px;
  }

  .day-name {
    font-size: 0.9rem;
    opacity: 0.95;
    font-weight: 600;
  }

  tbody tr {
    background: white;
  }

  tbody tr:nth-child(even) {
    background: #fafbfc;
  }

  .time-cell {
    background: #0d3a6f;
    color: white;
    padding: 16px 12px;
    text-align: center;
    font-weight: 700;
    font-size: 0.9rem;
    border: 2px solid white;
    vertical-align: middle;
  }

  .session-cell {
    padding: 8px;
    border: 2px solid white;
    vertical-align: top;
  }

  .break-cell {
    background: #e2e8f0;
    color: #1e293b;
    padding: 16px;
    text-align: center;
    font-weight: 700;
    border-radius: 8px;
  }

  .session-card {
    width: 100%;
    padding: 16px;
    border-radius: 8px;
    border: none;
    cursor: pointer;
    text-align: left;
    transition: all 0.2s ease;
    min-height: 100px;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .session-card:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  }

  .session-card.blue {
    background: #bfdbfe;
    color: #1e3a8a;
  }

  .session-card.blue:hover {
    background: #93c5fd;
  }

  .session-card.green {
    background: #d9f99d;
    color: #365314;
  }

  .session-card.green:hover {
    background: #bef264;
  }

  .session-card.pink {
    background: #fecdd3;
    color: #881337;
  }

  .session-card.pink:hover {
    background: #fda4af;
  }

  .session-card.yellow {
    background: #fef08a;
    color: #713f12;
  }

  .session-card.yellow:hover {
    background: #fde047;
  }

  .session-title {
    font-weight: 700;
    line-height: 1.3;
    font-size: 0.95rem;
  }

  .session-speaker {
    font-size: 0.85rem;
    opacity: 0.8;
    font-weight: 600;
  }

  /* Modal */
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
    padding: 1rem;
    animation: fadeIn 0.2s;
  }

  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }

  .modal {
    background: white;
    border-radius: 20px;
    max-width: 600px;
    width: 100%;
    max-height: 85vh;
    overflow-y: auto;
    position: relative;
    animation: slideUp 0.3s;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  }

  @keyframes slideUp {
    from {
      transform: translateY(30px);
      opacity: 0;
    }
    to {
      transform: translateY(0);
      opacity: 1;
    }
  }

  .close-btn {
    position: absolute;
    top: 16px;
    right: 16px;
    background: #f1f5f9;
    border: none;
    width: 36px;
    height: 36px;
    border-radius: 50%;
    font-size: 1.25rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s;
    color: #64748b;
    z-index: 10;
  }

  .close-btn:hover {
    background: #e2e8f0;
    color: #1e293b;
    transform: rotate(90deg);
  }

  .modal-header {
    padding: 32px 32px 24px;
    border-bottom: 2px solid #f0f4f8;
  }

  .modal-header h3 {
    margin: 0 0 8px 0;
    font-size: 1.5rem;
    font-weight: 800;
    color: #1e293b;
    line-height: 1.3;
  }

  .modal-speaker {
    color: #64748b;
    font-weight: 600;
  }

  .modal-body {
    padding: 24px 32px 32px;
  }

  .modal-section {
    margin-bottom: 24px;
  }

  .modal-section:last-child {
    margin-bottom: 0;
  }

  .modal-section h4 {
    font-size: 0.85rem;
    font-weight: 700;
    color: #64748b;
    margin: 0 0 8px 0;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .modal-section p {
    color: #475569;
    line-height: 1.7;
    margin: 0;
  }

  .room-badge {
    display: inline-block;
    background: #fef3c7;
    color: #92400e;
    padding: 8px 16px;
    border-radius: 8px;
    font-weight: 600;
    border: 1px solid #fde68a;
  }

  @media (max-width: 768px) {
    .schedule-table {
      font-size: 0.85rem;
    }

    .day-header {
      min-width: 150px;
    }

    .time-cell {
      font-size: 0.8rem;
      padding: 12px 8px;
    }

    .session-card {
      padding: 12px;
      min-height: 90px;
    }

    .session-title {
      font-size: 0.85rem;
    }

    .session-speaker {
      font-size: 0.75rem;
    }

    .modal-header,
    .modal-body {
      padding-left: 20px;
      padding-right: 20px;
    }
  }
</style>

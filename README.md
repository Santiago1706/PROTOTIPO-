# PROTOTIPO-
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>ConstituChall 🇨🇴 – Prototipo</title>
  <style>
    :root{
      --bg:#0f172a;          /* slate-900 */
      --panel:#111827;       /* gray-900 */
      --card:#1f2937;        /* gray-800 */
      --muted:#94a3b8;       /* slate-400 */
      --text:#e5e7eb;        /* gray-200 */
      --accent:#22c55e;      /* green-500 */
      --accent2:#60a5fa;     /* blue-400 */
      --warn:#f59e0b;        /* amber-500 */
      --danger:#ef4444;      /* red-500 */
      --ok:#10b981;          /* emerald-500 */
      --purple:#a78bfa;      /* purple-400 */
    }
    *{box-sizing:border-box}
    body{margin:0;font-family:system-ui,-apple-system,Segoe UI,Roboto,Inter,Arial,sans-serif;background:linear-gradient(180deg,#0b1224,#0f172a 30%,#0b1224);color:var(--text)}
    .wrapper{display:grid;grid-template-columns:320px 1fr;gap:16px;max-width:1200px;margin:20px auto;padding:0 16px}
    header{max-width:1200px;margin:16px auto 0;padding:12px 16px}
    h1{margin:0;font-size:clamp(22px,3.5vw,32px);font-weight:800;letter-spacing:.2px}
    .subtitle{color:var(--muted);font-size:14px;margin-top:6px}
    .panel{background:var(--panel);border:1px solid #1f2937;border-radius:16px;box-shadow:0 10px 30px rgba(0,0,0,.35)}
    .left{padding:14px}
    .section-title{font-weight:700;font-size:13px;letter-spacing:.6px;text-transform:uppercase;color:#9ca3af;margin:8px 0 6px}
    .players{display:flex;flex-direction:column;gap:10px}
    .player{display:grid;grid-template-columns:1fr 88px 32px;gap:8px;align-items:center;background:var(--card);padding:10px;border-radius:12px;border:1px solid #374151}
    .player input{width:100%;background:#0b1020;border:1px solid #283142;color:var(--text);padding:8px;border-radius:8px}
    .badge{font-size:12px;color:#cbd5e1;background:#0b1224;border:1px solid #334155;padding:6px 8px;border-radius:8px;text-align:center}
    .add{width:100%;padding:10px 12px;border-radius:10px;background:#0b1224;border:1px dashed #334155;color:#cbd5e1;cursor:pointer}
    .controls{display:grid;grid-template-columns:repeat(2,1fr);gap:10px;margin-top:10px}
    button{cursor:pointer;border:none;border-radius:10px;padding:10px 12px;font-weight:700}
    .primary{background:var(--accent);color:#052e16}
    .secondary{background:var(--accent2);color:#0b1224}
    .ghost{background:#0b1224;color:#cbd5e1;border:1px solid #334155}
    .danger{background:var(--danger)}
    .warn{background:var(--warn);color:#111827}
    .ok{background:var(--ok);color:#052e16}

    .board{padding:16px}

    .topbar{display:grid;grid-template-columns:1fr auto auto auto auto;gap:10px;align-items:center}
    .turn-big{grid-column:1/-1;background:#0b1224;border:1px solid #334155;border-radius:14px;padding:10px 14px;font-size:clamp(20px,4.5vw,30px);font-weight:900;display:flex;align-items:center;gap:10px}
    .turn-dot{width:14px;height:14px;border-radius:50%;background:var(--ok);box-shadow:0 0 0 3px rgba(16,185,129,.15)}
    .pill{display:inline-flex;align-items:center;gap:8px;padding:8px 10px;border-radius:999px;border:1px solid #334155;background:#0b1224;color:#cbd5e1;font-size:13px}

    .track{margin:14px 0;background:#0b1224;border:1px solid #283142;border-radius:12px;height:14px;position:relative;overflow:hidden}
    .progress{position:absolute;inset:0 0 0 auto;background:linear-gradient(90deg,var(--accent2),#22d3ee);width:0%}

    .legend{display:flex;gap:8px;flex-wrap:wrap}
    .tag{font-size:12px;border:1px solid #334155;border-radius:999px;padding:4px 8px;color:#cbd5e1}

    .event{margin-top:10px;background:#0b1224;border:1px dashed #6b7280;padding:10px;border-radius:12px}

    .card{background:var(--card);border:1px solid #374151;border-radius:16px;padding:16px;margin-top:12px}
    .category{font-size:12px;letter-spacing:.6px;text-transform:uppercase;color:#cbd5e1;display:inline-flex;align-items:center;gap:6px}
    .category .dot{width:10px;height:10px;border-radius:50%}
    .title{font-size:18px;font-weight:800;margin:6px 0 4px}
    .question{font-size:15px;color:#e2e8f0}
    .options{margin-top:12px;display:grid;gap:8px}
    .options label{display:flex;gap:8px;align-items:flex-start;background:#0b1224;border:1px solid #334155;padding:10px;border-radius:10px}

    textarea{width:100%;min-height:84px;background:#0b1224;border:1px solid #334155;border-radius:10px;color:#e5e7eb;padding:10px}

    .footer-actions{display:flex;flex-wrap:wrap;gap:10px;margin-top:12px}

    .grid-2{display:grid;grid-template-columns:1fr 1fr;gap:12px}
    .muted{color:#94a3b8;font-size:13px}

    .modal{position:fixed;inset:0;background:rgba(0,0,0,.6);display:none;align-items:center;justify-content:center;padding:16px}
    .modal .inner{max-width:900px;width:100%;background:var(--panel);border:1px solid #1f2937;border-radius:16px;padding:16px}
    .modal h2{margin:0 0 8px}
    .modal pre{white-space:pre-wrap;background:#0b1224;border:1px solid #334155;padding:10px;border-radius:10px;color:#e5e7eb;max-height:260px;overflow:auto}

    .small{font-size:12px}
    .credits{max-width:1200px;margin:10px auto 30px;padding:0 16px;color:#9ca3af;font-size:12px}

    .flag{filter:drop-shadow(0 0 6px rgba(255,255,255,.25))}

    @media (max-width:920px){
      .wrapper{grid-template-columns:1fr}
      .topbar{grid-template-columns:1fr 1fr}
      .turn-big{grid-column:1/-1}
    }
  </style>
</head>
<body>
  <header>
    <h1>ConstituChall 🇨🇴 — Prototipo web</h1>
    <div class="subtitle">Derechos Fundamentales y Principios de la Constitución Política de 1991 — modo demo jugable</div>
  </header>

  <div class="wrapper">
    <!-- Sidebar: jugadores y controles -->
    <aside class="panel left">
      <div class="section-title">Jugadores (hasta 6)</div>
      <div id="players" class="players"></div>
      <button id="addPlayer" class="add">+ Agregar jugador</button>
      <div class="controls">
        <button id="start" class="primary">▶️ Iniciar partida</button>
        <button id="reset" class="ghost">↺ Reiniciar</button>
      </div>
      <div style="margin-top:12px;display:grid;gap:8px">
        <div class="section-title">Rápidos</div>
        <button id="openRules" class="ghost">📜 Reglas</button>
        <button id="openEditor" class="ghost">🛠️ Editor de preguntas</button>
      </div>
    </aside>

    <!-- Main: tablero y cartas -->
    <main class="panel board">
      <div class="topbar">
        <div class="turn-big"><span class="turn-dot"></span><span id="turnLbl">Turno: —</span></div>
        <div class="pill">Ronda: <strong id="round">1</strong></div>
        <div class="pill">Dado: <strong id="dice">—</strong></div>
        <div class="pill small">Meta: acumular 5 cartas</div>
        <div class="pill">⏱️ Tiempo: <strong id="timer">—</strong>s</div>
      </div>
      <div class="track" title="Progreso de rondas"><div id="progress" class="progress"></div></div>
      <div class="legend">
        <span class="tag">🔵 Principios</span>
        <span class="tag">🟢 Derechos</span>
        <span class="tag">🟣 Participación</span>
        <span class="tag">🟠 Casos reales</span>
        <span class="tag">⚡ Eventos especiales</span>
      </div>

      <div id="eventBar" class="event" style="display:none"></div>

      <div id="card" class="card">
        <div class="category"><span id="catDot" class="dot" style="background:#64748b"></span><span id="catText">Esperando inicio…</span></div>
        <div class="title" id="title">Bienvenid@</div>
        <div class="question" id="question">Agrega jugadores y presiona “Iniciar partida”. Luego lanza el dado y saca una tarjeta según la categoría.</div>
        <div id="options" class="options"></div>
        <div id="feedback" class="muted small" style="margin-top:8px;min-height:18px"></div>
        <div id="freeInputWrap" style="display:none;margin-top:10px">
          <textarea id="freeInput" placeholder="Escribe tu respuesta / argumenta el caso…"></textarea>
        </div>
        <div class="footer-actions">
          <button id="roll" class="secondary" disabled>🎲 Lanzar dado</button>
          <button id="draw" class="primary" disabled>🃏 Sacar tarjeta</button>
          <button id="validate" class="ok" disabled>✅ Validar</button>
          <button id="pass" class="warn" disabled>⏭️ Pasar turno</button>
        </div>
        <div class="muted small" style="margin-top:8px">Tip: el indicador «Ronda» reemplaza las posiciones del tablero físico. Los eventos añaden sanciones/bonos.</div>
      </div>

      <div class="grid-2" style="margin-top:12px">
        <div class="card">
          <div class="section-title">Marcador</div>
          <div id="score" class="muted">—</div>
        </div>
        <div class="card">
          <div class="section-title">Historial</div>
          <div id="log" class="muted small">Sin eventos aún.</div>
        </div>
      </div>
    </main>
  </div>

  <div class="credits">Prototipo educativo • Constitución Política de Colombia (1991) • Hecho con ❤️ para jóvenes de 14–28 años.
    <span class="flag">🇨🇴</span>
  </div>

  <!-- Modal: Reglas -->
  <div id="rulesModal" class="modal" role="dialog" aria-modal="true">
    <div class="inner">
      <h2>📜 Reglas del juego</h2>
      <ol>
        <li>Juegan 2–6 personas. Añade nombres y presiona <b>Iniciar partida</b>.</li>
        <li>En tu turno presiona <b>🎲 Lanzar dado</b>. El color define la <i>categoría</i>. Puede haber <b>⚡ eventos especiales</b>.</li>
        <li>Presiona <b>🃏 Sacar tarjeta</b> para ver la pregunta/reto del mazo.</li>
        <li>Responde (opción múltiple) o argumenta (caso real). Tienes <b>10 segundos</b>. Luego <b>✅ Validar</b>.</li>
        <li>Correcto: +1 Carta (o más si hay bono). Gana quien llegue a <b>5</b>.</li>
      </ol>
      <p class="muted small">«Ronda» = conteo de turnos globales (no posiciones físicas). Eventos: x2 (solo si aciertas), +2, -2, robar 1; <b>pierde turno solo si fallas</b>.</p>
      <div style="display:flex;gap:8px;justify-content:flex-end;margin-top:8px">
        <button class="ghost" onclick="toggleModal('rulesModal',false)">Cerrar</button>
      </div>
    </div>
  </div>

  <!-- Modal: Editor -->
  <div id="editorModal" class="modal" role="dialog" aria-modal="true">
    <div class="inner">
      <h2>🛠️ Editor de preguntas (JSON)</h2>
      <p class="muted small">Edita o pega tu banco. Cambios se guardan en esta sesión (LocalStorage).</p>
      <pre id="editorArea" contenteditable="true"></pre>
      <div style="display:flex;gap:8px;justify-content:flex-end;margin-top:8px">
        <button class="ghost" onclick="toggleModal('editorModal',false)">Cancelar</button>
        <button class="primary" onclick="saveBank()">💾 Guardar</button>
      </div>
    </div>
  </div>

  <script>
    // ----- Configuración -----
    const TIMER_SECONDS = 10;

    // ----- Banco DEMO (editable en el editor JSON) -----
    const DEFAULT_BANK = {
      principios: [
        { type:'mc', q:'El Artículo 1 establece que Colombia es un Estado…', options:['Unitario, social de derecho, democrático, participativo y pluralista','Federal, confesional y militar','Neoliberal, tecnocrático y centralista'], answer:0, ref:'Art.1' },
        { type:'mc', q:'La soberanía reside…', options:['En las Fuerzas Militares','Exclusivamente en el Presidente','En el pueblo del cual emana el poder público'], answer:2, ref:'Art.3' },
        { type:'mc', q:'La Constitución reconoce la diversidad…', options:['Étnica y cultural de la Nación','Únicamente religiosa','Exclusivamente lingüística'], answer:0, ref:'Art.7' },
        { type:'mc', q:'El español es el idioma oficial, pero…', options:['No se permiten otras lenguas','Las lenguas y dialectos de los grupos étnicos son también oficiales en sus territorios','Solo el inglés tiene validez'], answer:1, ref:'Art.10' }
      ],
      derechos: [
        { type:'mc', q:'El derecho a la vida (Art.11) es…', options:['Relativo','Inalienable e inviolable','Condicionado a mayoría de edad'], answer:1, ref:'Art.11' },
        { type:'mc', q:'La libertad de expresión (Art.20) incluye…', options:['Censura previa','Buscar, recibir y difundir información','Solo opinar en privado'], answer:1, ref:'Art.20' },
        { type:'mc', q:'El habeas corpus protege contra…', options:['Detenciones arbitrarias','Multas de tránsito','Embargos civiles'], answer:0, ref:'Art.30' },
        { type:'mc', q:'La igualdad (Art.13) implica…', options:['Trato idéntico en todo caso','Medidas en favor de grupos discriminados o marginados','Privilegios por estrato'], answer:1, ref:'Art.13' }
      ],
      participacion: [
        { type:'mc', q:'Un mecanismo de participación ciudadana es…', options:['Referendo','Auto de imputación','Acta de conciliación'], answer:0, ref:'Art.103' },
        { type:'mc', q:'El voto en Colombia es…', options:['Obligatorio','Un derecho y un deber ciudadano','Solo para mayores de 21'], answer:1, ref:'Art.258' },
        { type:'mc', q:'La acción de tutela sirve para…', options:['Reclamar derechos fundamentales cuando no hay otro medio de defensa','Demandar impuestos','Anular elecciones'], answer:0, ref:'Art.86' }
      ],
      casos: [
        { type:'open', q:'Una estudiante es expulsada por usar símbolos religiosos. ¿Qué derechos identifica y qué haría?', rubric:'Igualdad (Art.13) y libertad de cultos (Art.19). Argumentar vías: diálogo institucional, personería, tutela.' },
        { type:'open', q:'Un hospital se niega a atender una urgencia por falta de pago. ¿Qué acción procede?', rubric:'Derecho a la vida y salud (Art.11, jurisprudencia); atención inmediata. Tutela por perjuicio irremediable.' },
        { type:'open', q:'En redes, un alcalde bloquea a críticos del municipio. ¿Qué principio/derecho se afecta?', rubric:'Publicidad de la actuación pública, libertad de expresión (Art.20), participación. Control judicial.' }
      ]
    };

    // ----- Eventos especiales (bonos y sanciones) -----
    const EVENTS = [
      { key:'x2',    label:'Pregunta bono x2',                 desc:'Si aciertas esta tarjeta, ganas 2 cartas en lugar de 1.', color:'#22c55e' },
      { key:'plus2', label:'Gana +2 cartas',                   desc:'Recibes 2 cartas de ciudadanía inmediatamente.',         color:'#60a5fa' },
      { key:'minus2',label:'Sanción -2 cartas',                desc:'Pierdes 2 cartas (sin bajar de 0).',                    color:'#ef4444' },
      { key:'skip',  label:'Pierde próximo turno (si fallas)', desc:'Este castigo solo se aplica si la respuesta es incorrecta.', color:'#f59e0b' },
      { key:'steal1',label:'Roba 1 al líder',                  desc:'Toma 1 carta del jugador con más cartas (si existe empate, elige al primero).', color:'#a78bfa' }
    ];

    // ----- Estado del juego -----
    const state = {
      players: [],
      turn: 0,
      round: 1,
      dice: 0,
      currentCard: null,
      currentCategory: null,
      bank: null,
      started: false,
      event: null,
      skipFlags: {}, // playerIndex: true si salta turno
      pending: { mult: 1, skipOnFail: false }, // efectos que se aplican al validar
      timer: { id: null, remaining: 0 }
    };

    // ----- Utilidades UI -----
    const el = (id) => document.getElementById(id);
    const log = (msg) => {
      const time = new Date().toLocaleTimeString();
      const prev = el('log').innerHTML === 'Sin eventos aún.' ? '' : el('log').innerHTML + '<br/>';
      el('log').innerHTML = prev + `<span class="muted">[${time}]</span> ${msg}`;
    };

    function applyDelta(playerIndex, delta, reason=''){
      const before = state.players[playerIndex].score;
      const after = Math.max(0, before + delta);
      state.players[playerIndex].score = after;
      const sign = delta>=0? '+':'-';
      if(delta!==0) log(`📈 ${state.players[playerIndex].name} ${sign}${Math.abs(delta)} carta(s) ${reason? '— '+reason : ''}. Total: ${after}.`);
      renderScore();
    }

    function renderPlayers(){
      const wrap = el('players');
      wrap.innerHTML='';
      state.players.forEach((p,i)=>{
        const row = document.createElement('div');
        row.className='player';
        const crown = p.score>=5 ? ' 🏆' : '';
        row.innerHTML = `
          <input value="${p.name}" data-i="${i}" placeholder="Nombre del jugador"/>
          <div class="badge">${p.score} cartas${crown}</div>
          <button class="danger" data-del="${i}">×</button>
        `;
        wrap.appendChild(row);
      });
      wrap.querySelectorAll('input').forEach(inp=>{
        inp.oninput = (e)=>{ const i = +e.target.dataset.i; state.players[i].name = e.target.value; renderScore(); };
      });
      wrap.querySelectorAll('button[data-del]').forEach(btn=>{
        btn.onclick = (e)=>{ const i = +e.target.dataset.del; state.players.splice(i,1); renderPlayers(); renderScore(); };
      });
    }

    function renderTopbar(){
      el('turnLbl').textContent = state.players.length ? `Turno de: ${state.players[state.turn].name}` : 'Turno: —';
      el('dice').textContent = state.dice || '—';
      el('round').textContent = state.round;
      el('timer').textContent = state.timer.remaining || '—';
      el('progress').style.width = `${Math.min(100, Math.round(((state.round-1)/20)*100))}%`;
    }

    function renderScore(){
      if(!state.players.length){ el('score').textContent='—'; return; }
      el('score').innerHTML = state.players.map((p,i)=>{
        const crown = p.score>=5 ? ' 🏆 Ganador' : '';
        const turn = i===state.turn? ' <b>(jugando)</b>':'';
        return `<div>• <b>${p.name || 'Jugador '+(i+1)}</b>: ${p.score} cartas${crown}${turn}</div>`;
      }).join('');
      renderPlayers();
    }

    function setButtons(enabled){
      el('roll').disabled = !enabled;
      el('draw').disabled = !enabled;
      el('validate').disabled = !enabled;
      el('pass').disabled = !enabled;
    }

    function categoryByRound(r){
      const seq = ['principios','derechos','participacion','casos'];
      return seq[(r-1) % seq.length];
    }

    function catMeta(key){
      return {
        principios:{ label:'Principios Fundamentales', color:'#60a5fa', icon:'🔵' },
        derechos:{ label:'Derechos Fundamentales', color:'#22c55e', icon:'🟢' },
        participacion:{ label:'Participación Ciudadana', color:'#a78bfa', icon:'🟣' },
        casos:{ label:'Casos de la vida real', color:'#f59e0b', icon:'🟠' }
      }[key];
    }

    function startTimer(sec){
      stopTimer();
      state.timer.remaining = sec;
      renderTopbar();
      state.timer.id = setInterval(()=>{
        state.timer.remaining--;
        renderTopbar();
        if(state.timer.remaining<=0){
          stopTimer();
          timeIsUp();
        }
      },1000);
    }

    function stopTimer(){
      if(state.timer.id){ clearInterval(state.timer.id); state.timer.id=null; }
    }

    function lockInputs(){
      el('validate').disabled = true;
      const radios = document.querySelectorAll('input[name="opts"]');
      radios.forEach(r=>r.disabled=true);
      const free = document.getElementById('freeInput');
      if (free) free.disabled = true;
    }

    function maybeEvent(){
      // Reinicia efectos pendientes
      state.pending = { mult: 1, skipOnFail: false };
      // 25% de probabilidad de evento al sacar tarjeta
      if(Math.random() < 0.25){
        const ev = EVENTS[Math.floor(Math.random()*EVENTS.length)];
        state.event = ev;
        el('eventBar').style.display='block';
        el('eventBar').innerHTML = `⚡ <b>${ev.label}</b> — ${ev.desc}`;
        el('eventBar').style.borderColor = ev.color;
        log(`⚡ Evento: ${ev.label}.`);
        const idx = state.turn;
        switch(ev.key){
          case 'x2':
            state.pending.mult = 2; // se aplicará si acierta
            break;
          case 'plus2':
            applyDelta(idx, +2, 'por evento +2');
            break;
          case 'minus2':
            applyDelta(idx, -2, 'por sanción -2');
            break;
          case 'steal1': {
            const order = [...state.players].map((p,i)=>({i,score:p.score})).sort((a,b)=>b.score-a.score);
            const leader = order.find(x=>x.i!==idx);
            if(leader && leader.score>0){
              applyDelta(leader.i, -1, `robada por ${state.players[idx].name}`);
              applyDelta(idx, +1, 'roba 1 al líder');
            }
            break; }
          case 'skip':
            // Ya no se aplica inmediato: solo si fallas esta tarjeta
            state.pending.skipOnFail = true;
            break;
        }
      } else {
        state.event = null; el('eventBar').style.display='none'; el('eventBar').innerHTML='';
      }
    }

    function drawCard(){
      const cat = categoryByRound(state.round);
      const pool = state.bank[cat];
      const idx = Math.floor(Math.random()*pool.length);
      const card = pool[idx];
      state.currentCard = { ...card, idx };
      state.currentCategory = cat;

      // Render
      const meta = catMeta(cat);
      el('catText').textContent = `${meta.icon} ${meta.label}`;
      el('catDot').style.background = meta.color;
      el('title').textContent = card.ref ? `Referencia: ${card.ref}` : meta.label;
      el('question').textContent = card.q;
      el('options').innerHTML='';
      el('feedback').innerHTML='';
      el('freeInputWrap').style.display = 'none';

      if(card.type==='mc'){
        card.options.forEach((opt,i)=>{
          const id = `opt_${i}`;
          const label = document.createElement('label');
          label.innerHTML = `<input type="radio" name="opts" value="${i}" id="${id}"> <span>${opt}</span>`;
          el('options').appendChild(label);
        });
      } else {
        el('freeInputWrap').style.display = 'block';
        el('freeInput').value='';
        el('freeInput').disabled = false;
      }
      log(`🃏 Tarjeta de «${meta.label}» sacada.`);
      maybeEvent();
      // Inicia cronómetro
      startTimer(TIMER_SECONDS);
      el('validate').disabled=false;
    }

    function endOfQuestion(correct, infoText){
      const idx = state.turn;
      if(correct){
        const gain = 1 * (state.pending?.mult || 1);
        applyDelta(idx, gain, gain>1? `bono x${state.pending.mult}` : 'respuesta correcta');
        el('feedback').innerHTML = "<span style='color:#10b981'>✅ ¡Correcto!</span> " + (infoText||'') + (gain>1? ` — <b>Bono x${state.pending.mult}</b>`:'');
        if(state.players[idx].score >= 5){
          log(`🏆 ${state.players[idx].name} alcanzó 5 cartas. ¡Ganador!`);
          alert(`🎉 ${state.players[idx].name} ganó la partida con 5 cartas de ciudadanía!`);
        }
      } else {
        el('feedback').innerHTML = "<span style='color:#ef4444'>❌ Incorrecto.</span> " + (infoText||'');
        log(`❌ Incorrecto. ${state.currentCard?.ref ? 'Ref: '+state.currentCard.ref : ''}`);
        // Castigo condicional: pierde turno solo si fallas y hay evento skip activo
        if(state.pending.skipOnFail){
          state.skipFlags[idx] = true;
          log(`⏭️ ${state.players[idx].name} perderá su próximo turno (castigo por fallar).`);
        }
      }
      // limpiar efectos y timer
      state.pending = { mult: 1, skipOnFail: false };
      stopTimer();
      lockInputs();
      nextTurn();
    }

    function validate(){
      if(!state.currentCard) return;
      let correct = false;
      let infoText = '';

      if(state.currentCard.type==='mc'){
        const chosen = document.querySelector('input[name="opts"]:checked');
        if(!chosen){ alert('Selecciona una opción.'); return; }
        const ansIdx = state.currentCard.answer;
        const ansText = state.currentCard.options[ansIdx];
        infoText = '✔ Respuesta correcta: "' + ansText + '" (' + (state.currentCard.ref || '—') + ')';
        correct = (+chosen.value === ansIdx);
      } else {
        const txt = el('freeInput').value.trim();
        if(txt.length<8){ alert('Escribe una breve argumentación.'); return; }
        const rubric = (state.currentCard.rubic || state.currentCard.rubric || '').toLowerCase();
        correct = rubric? rubric.split(/[,.;()\s]+/).some(k=>k && txt.toLowerCase().includes(k)) : true;
        infoText = '🔎 Pistas: ' + (state.currentCard.rubric || '—');
      }

      endOfQuestion(correct, infoText);
    }

    function timeIsUp(){
      lockInputs();
      el('feedback').innerHTML = "<span style='color:#ef4444'>⏱️ Tiempo agotado.</span> Se cuenta como respuesta incorrecta.";
      endOfQuestion(false, 'Tiempo agotado');
    }

    function nextTurn(){
      // manejar saltos de turno
      let next = (state.turn + 1) % state.players.length;
      if(state.skipFlags[next]){ log(`⏭️ ${state.players[next].name} pierde este turno.`); delete state.skipFlags[next]; next = (next + 1) % state.players.length; }
      state.turn = next;
      state.currentCard = null; state.currentCategory = null; state.event=null; el('eventBar').style.display='none'; el('eventBar').innerHTML='';
      el('catText').textContent = 'Siguiente turno';
      el('title').textContent = 'Lanza el dado 🎲';
      el('question').textContent = 'El color de la casilla define la categoría.';
      el('options').innerHTML='';
      el('freeInputWrap').style.display = 'none';
      // aumentar ronda cuando volvemos al jugador 0
      if(state.turn === 0) state.round += 1;
      renderTopbar(); renderScore();
    }

    // ----- Acciones -----
    el('addPlayer').onclick = ()=>{
      if(state.players.length>=6) return alert('Máximo 6 jugadores.');
      state.players.push({name:`Jugador ${state.players.length+1}`, score:0});
      renderPlayers(); renderScore();
    };

    el('start').onclick = ()=>{
      if(state.players.length<2) return alert('Agrega al menos 2 jugadores.');
      state.started = true; state.turn = 0; state.round = 1; state.dice=0; state.event=null; state.skipFlags={}; state.pending={mult:1, skipOnFail:false};
      setButtons(true);
      el('roll').disabled=false; el('draw').disabled=true; el('validate').disabled=true; el('pass').disabled=false;
      renderTopbar(); renderScore();
      log('▶️ Partida iniciada.');
    };

    el('reset').onclick = ()=>{
      state.players.forEach(p=>p.score=0);
      state.turn = 0; state.round=1; state.dice=0; state.started=false; state.currentCard=null; state.currentCategory=null; state.event=null; state.skipFlags={}; state.pending={mult:1, skipOnFail:false};
      stopTimer();
      renderTopbar(); renderScore();
      el('catText').textContent = 'Listo para reiniciar';
      el('title').textContent = 'Bienvenid@';
      el('question').textContent = 'Agrega jugadores y presiona “Iniciar partida”.';
      el('options').innerHTML='';
      el('freeInputWrap').style.display='none';
      el('eventBar').style.display='none'; el('eventBar').innerHTML='';
      setButtons(false);
      log('↺ Reinicio.');
    };

    el('roll').onclick = ()=>{
      if(!state.started) return;
      const d = 1 + Math.floor(Math.random()*6);
      state.dice = d;
      renderTopbar();
      el('draw').disabled=false; el('validate').disabled=true;
      log(`🎲 Dado: ${d}.`);
    };

    el('draw').onclick = ()=>{
      drawCard();
      el('validate').disabled=false;
      el('draw').disabled=true;
    };

    el('validate').onclick = ()=>{ stopTimer(); validate(); };
    el('pass').onclick = ()=>{ log('⏭️ Turno pasado.'); stopTimer(); state.pending={mult:1, skipOnFail:false}; nextTurn(); };

    // ----- Modales -----
    function toggleModal(id, show){
      const m = el(id); m.style.display = show? 'flex':'none';
    }
    window.toggleModal = toggleModal;
    el('openRules').onclick = ()=> toggleModal('rulesModal', true);
    el('openEditor').onclick = ()=>{
      el('editorArea').textContent = JSON.stringify(state.bank, null, 2);
      toggleModal('editorModal', true);
    };

    function saveBank(){
      try{
        const data = JSON.parse(el('editorArea').textContent);
        state.bank = data; localStorage.setItem('constituchall_bank', JSON.stringify(data));
        toggleModal('editorModal', false);
        log('💾 Banco actualizado.');
      }catch(e){ alert('JSON inválido. Revisa comas, llaves y corchetes.'); }
    }
    window.saveBank = saveBank;

    // ----- Boot -----
    (function init(){
      const saved = localStorage.getItem('constituchall_bank');
      state.bank = saved? JSON.parse(saved) : DEFAULT_BANK;
      renderPlayers(); renderTopbar(); renderScore(); setButtons(false);
    })();
  </script>
</body>
</html>

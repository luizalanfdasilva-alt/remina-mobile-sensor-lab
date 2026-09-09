<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<meta name="theme-color" content="#050505">
<meta name="description" content="REMINA Mobile Sensor Lab — laboratório portátil de percepção, contexto e memória sensorial.">
<title>REMINA • Mobile Sensor Lab</title>

<style>
:root{
  --bg:#050505;
  --card:#101010;
  --card2:#171717;
  --line:#292929;
  --text:#f5f5f5;
  --muted:#a7a7a7;
  --gold:#d9b45b;
  --green:#55d68a;
  --yellow:#f2c94c;
  --orange:#f2994a;
  --red:#eb5757;
}

*{
  box-sizing:border-box;
}

html,body{
  margin:0;
  min-height:100%;
  background:var(--bg);
  color:var(--text);
  font-family:
    system-ui,
    -apple-system,
    BlinkMacSystemFont,
    "Segoe UI",
    Roboto,
    Arial,
    sans-serif;
}

body{
  overflow-x:hidden;
}

button,
input,
textarea{
  font:inherit;
}

button{
  border:1px solid var(--line);
  background:#181818;
  color:#fff;
  border-radius:14px;
  padding:12px 14px;
  cursor:pointer;
  -webkit-tap-highlight-color:transparent;
}

button:active{
  transform:scale(.98);
}

button.primary{
  background:var(--gold);
  color:#080808;
  border-color:var(--gold);
  font-weight:800;
}

button.danger{
  background:#291111;
  border-color:#4a2222;
}

button.small{
  padding:8px 10px;
  border-radius:10px;
  font-size:13px;
}

.hidden{
  display:none!important;
}

.app{
  width:100%;
  max-width:520px;
  margin:auto;
  min-height:100vh;
  padding-bottom:105px;
}

header{
  padding:
    calc(15px + env(safe-area-inset-top))
    16px
    12px;
  position:sticky;
  top:0;
  z-index:20;
  background:rgba(5,5,5,.93);
  backdrop-filter:blur(12px);
  border-bottom:1px solid var(--line);
}

.kicker{
  font-size:11px;
  color:var(--gold);
  letter-spacing:.16em;
  font-weight:800;
}

.brand{
  font-size:25px;
  font-weight:900;
  margin-top:4px;
  line-height:1.05;
}

.sub{
  font-size:12px;
  color:var(--muted);
  margin-top:5px;
}

section{
  padding:12px 14px;
}

.card{
  background:var(--card);
  border:1px solid var(--line);
  border-radius:18px;
  padding:14px;
  margin-bottom:12px;
}

.title{
  font-weight:800;
  font-size:16px;
}

.muted{
  color:var(--muted);
  font-size:12px;
}

.notice{
  font-size:11px;
  color:var(--muted);
  line-height:1.45;
}

.value{
  font-size:30px;
  font-weight:900;
  margin:5px 0;
}

.grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:9px;
}

.grid3{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:8px;
}

.row{
  display:flex;
  gap:8px;
  align-items:center;
  flex-wrap:wrap;
}

.between{
  display:flex;
  justify-content:space-between;
  gap:10px;
  align-items:center;
}

.badge{
  display:inline-flex;
  align-items:center;
  gap:5px;
  padding:5px 8px;
  border-radius:999px;
  background:#1c1c1c;
  border:1px solid var(--line);
  font-size:11px;
  color:var(--muted);
}

.ok{
  color:var(--green);
}

.warn{
  color:var(--yellow);
}

.bad{
  color:var(--red);
}

.sensor{
  padding:12px;
  border:1px solid var(--line);
  border-radius:14px;
  background:var(--card2);
}

.sensor .name{
  font-size:12px;
  color:var(--muted);
}

.sensor .num{
  font-size:21px;
  font-weight:850;
  margin-top:4px;
}

.bar{
  height:7px;
  background:#252525;
  border-radius:99px;
  overflow:hidden;
  margin-top:8px;
}

.bar i{
  display:block;
  height:100%;
  width:0;
  background:var(--gold);
  border-radius:99px;
  transition:width .25s ease;
}

/* CAMERA */

.camera{
  position:relative;
  height:390px;
  background:#000;
  border-radius:20px;
  overflow:hidden;
  border:1px solid var(--line);
}

video#camera{
  width:100%;
  height:100%;
  object-fit:cover;
  background:#000;
}

.camera-ui{
  position:absolute;
  inset:0;
  display:flex;
  flex-direction:column;
  justify-content:space-between;
  padding:12px;
  pointer-events:none;
}

.camera-ui>*{
  pointer-events:auto;
}

.toptools,
.bottomtools{
  display:flex;
  justify-content:space-between;
  gap:8px;
  align-items:center;
}

.round{
  width:48px;
  height:48px;
  padding:0;
  border-radius:50%;
  background:rgba(0,0,0,.55);
  backdrop-filter:blur(8px);
}

.capture{
  width:74px;
  height:74px;
  border-radius:50%;
  border:4px solid #fff;
  background:rgba(255,255,255,.15);
  margin:auto;
  display:block;
  transition:.15s ease;
}

.capture.recording{
  background:var(--red);
  transform:scale(.9);
}

.gate{
  position:absolute;
  inset:0;
  background:rgba(0,0,0,.86);
  display:flex;
  align-items:center;
  justify-content:center;
  text-align:center;
  padding:25px;
  z-index:5;
}

.gatebox{
  max-width:330px;
}

.gatebox h2{
  font-size:25px;
  margin:8px 0;
}

.gatebox p{
  color:var(--muted);
  font-size:13px;
  line-height:1.5;
}

.gatehint{
  font-size:11px;
  color:#aaa;
  margin-top:10px;
}

.marker{
  position:absolute;
  padding:7px 9px;
  border-radius:999px;
  background:rgba(0,0,0,.70);
  border:1px solid rgba(255,255,255,.20);
  font-size:10px;
  backdrop-filter:blur(6px);
  will-change:transform,opacity;
}

.m1{
  left:8%;
  top:25%;
}

.m2{
  right:8%;
  top:38%;
}

.m3{
  left:10%;
  bottom:28%;
}

.m4{
  right:7%;
  bottom:22%;
}

/* FORMULA */

.formula{
  font-family:
    ui-monospace,
    SFMono-Regular,
    Menlo,
    Monaco,
    Consolas,
    monospace;
  font-size:11px;
  line-height:1.65;
  background:#080808;
  border:1px dashed #333;
  padding:11px;
  border-radius:12px;
  color:#ddd;
  overflow:auto;
}

/* COMPASS */

.compass{
  width:92px;
  height:92px;
  border:1px solid #444;
  border-radius:50%;
  margin:12px auto;
  position:relative;
  display:flex;
  align-items:center;
  justify-content:center;
  color:var(--gold);
}

.needle{
  position:absolute;
  width:3px;
  height:38px;
  background:var(--gold);
  top:7px;
  left:calc(50% - 1.5px);
  transform-origin:50% 39px;
  border-radius:4px;
}

/* MEMORY */

.memory{
  border:1px solid var(--line);
  border-radius:15px;
  overflow:hidden;
  background:#0d0d0d;
  margin-top:10px;
}

.memory img,
.memory video{
  width:100%;
  display:block;
  max-height:280px;
  object-fit:cover;
}

.memorybody{
  padding:11px;
}

.memorytitle{
  font-weight:800;
}

.memorymeta{
  font-size:11px;
  color:var(--muted);
  line-height:1.6;
  margin-top:5px;
}

.memory-actions{
  display:flex;
  gap:7px;
  flex-wrap:wrap;
  margin-top:9px;
}

/* FORM */

input,
textarea{
  width:100%;
  background:#0b0b0b;
  border:1px solid var(--line);
  color:#fff;
  border-radius:12px;
  padding:12px;
  outline:none;
}

textarea{
  min-height:80px;
  resize:vertical;
}

input:focus,
textarea:focus,
button:focus-visible{
  outline:2px solid var(--gold);
  outline-offset:2px;
}

/* FIXED CTA */

.fixed{
  position:fixed;
  left:50%;
  bottom:
    calc(12px + env(safe-area-inset-bottom));
  transform:translateX(-50%);
  width:min(490px,calc(100% - 28px));
  z-index:50;
}

.fixed button{
  width:100%;
  box-shadow:0 10px 35px rgba(0,0,0,.55);
}

/* TOAST */

.toast{
  position:fixed;
  left:50%;
  bottom:
    calc(92px + env(safe-area-inset-bottom));
  transform:translateX(-50%);
  background:#eee;
  color:#111;
  padding:10px 13px;
  border-radius:12px;
  font-size:12px;
  font-weight:700;
  z-index:100;
  max-width:90%;
  text-align:center;
  box-shadow:0 8px 30px rgba(0,0,0,.5);
}

.status-line{
  min-height:18px;
  margin-top:7px;
}

hr{
  border:0;
  border-top:1px solid var(--line);
  margin:13px 0;
}

@media (min-width:600px){
  .camera{
    height:520px;
  }
}
</style>
</head>
<body>

<div class="app">

<header>
  <div class="kicker">EUNÁPOLIS • LAB v1.3</div>
  <div class="brand">REMINA MOBILE SENSOR LAB</div>
  <div class="sub">
    Primeiro laboratório portátil • NEXUS TACTILE + AURA SUIT
  </div>
</header>

<main>

<!-- =========================================================
     CÂMERA REAL
========================================================= -->

<section>

  <div class="camera">

    <video
      id="camera"
      autoplay
      playsinline
      muted
      aria-label="Câmera do REMINA">
    </video>

    <div id="gate" class="gate">

      <div class="gatebox">

        <div style="font-size:42px">📷</div>

        <h2>ABRIR CÂMERA REAL</h2>

        <p>
          O REMINA utiliza a câmera e os sensores disponíveis
          no seu celular para construir uma Memória Sensorial.
        </p>

        <button
          id="startBtn"
          class="primary">
          INICIAR REMINA
        </button>

        <div class="gatehint">
          A câmera e outros sensores podem solicitar permissões.
          Dados indisponíveis nunca serão inventados.
        </div>

      </div>

    </div>


    <div class="camera-ui">

      <!-- TOPO -->

      <div class="toptools">

        <button
          id="flipBtn"
          class="round"
          title="Trocar câmera"
          aria-label="Trocar câmera">
          🔄
        </button>

        <div
          class="badge"
          id="liveBadge">
          ● laboratório parado
        </div>

        <button
          id="torchBtn"
          class="round"
          title="Flash ou lanterna"
          aria-label="Flash ou lanterna">
          🔦
        </button>

      </div>


      <!-- MARCADORES SENSORIAIS -->

      <div>

        <div class="marker m1">
          ♿ Acessibilidade
        </div>

        <div class="marker m2">
          🔊 Som
        </div>

        <div class="marker m3">
          👃 Cheiro
        </div>

        <div class="marker m4">
          ✋ Sensação
        </div>

      </div>


      <!-- CONTROLES INFERIORES -->

      <div class="bottomtools">

        <button
          id="galleryBtn"
          class="round"
          aria-label="Abrir memórias">
          🗂️
        </button>

        <button
          id="captureBtn"
          class="capture"
          aria-label="Tirar foto. Segure para gravar vídeo">
        </button>

        <button
          id="labBtn"
          class="round"
          aria-label="Abrir laboratório">
          🧪
        </button>

      </div>

    </div>

  </div>


  <!-- CONTROLES DE CÂMERA -->

  <div
    class="row"
    style="margin-top:10px">

    <button
      id="photoBtn"
      class="small primary">
      📸 FOTO
    </button>

    <button
      id="videoBtn"
      class="small">
      🎥 VÍDEO
    </button>

    <button
      id="estiveTopBtn"
      class="small">
      📍 ESTIVE AQUI
    </button>

  </div>

</section>


<!-- =========================================================
     LABORATÓRIO
========================================================= -->

<section id="labSection">


<!-- =========================================================
     CROSS-MODAL ENGINE
========================================================= -->

<div class="card">

  <div class="between">

    <div>

      <div class="title">
        🧠 Cross-Modal Engine
      </div>

      <div class="muted">
        Índice experimental de intensidade sensorial
      </div>

    </div>

    <div
      class="badge"
      id="coverage">
      0/6 sensores
    </div>

  </div>


  <div
    class="value"
    id="stressValue">
    0/100
  </div>

  <div class="bar">
    <i id="stressBar"></i>
  </div>


  <div
    class="grid"
    style="margin-top:10px">


    <!-- ÁUDIO -->

    <div class="sensor">

      <div class="name">
        ÁUDIO
      </div>

      <div
        class="num"
        id="audioVal">
        —
      </div>

      <div
        class="muted"
        id="audioState">
        indisponível
      </div>

    </div>


    <!-- LUZ -->

    <div class="sensor">

      <div class="name">
        LUZ
      </div>

      <div
        class="num"
        id="lightVal">
        —
      </div>

      <div
        class="muted"
        id="lightState">
        indisponível
      </div>

    </div>


    <!-- MOVIMENTO -->

    <div class="sensor">

      <div class="name">
        MOVIMENTO
      </div>

      <div
        class="num"
        id="motionVal">
        —
      </div>

      <div
        class="muted"
        id="motionState">
        indisponível
      </div>

    </div>


    <!-- ORIENTAÇÃO -->

    <div class="sensor">

      <div class="name">
        ORIENTAÇÃO
      </div>

      <div
        class="num"
        id="headingVal">
        —
      </div>

      <div
        class="muted"
        id="headingState">
        indisponível
      </div>

    </div>


    <!-- GPS -->

    <div class="sensor">

      <div class="name">
        GPS
      </div>

      <div
        class="num"
        id="gpsVal">
        —
      </div>

      <div
        class="muted"
        id="gpsState">
        indisponível
      </div>

    </div>


    <!-- BATERIA -->

    <div class="sensor">

      <div class="name">
        BATERIA
      </div>

      <div
        class="num"
        id="batteryVal">
        —
      </div>

      <div
        class="muted"
        id="batteryState">
        indisponível
      </div>

    </div>

  </div>


  <!-- FÓRMULA -->

  <div
    class="formula"
    id="formulaBox"
    style="margin-top:10px">

    audio_norm = —<br>
    light_norm = —<br>
    movement_norm = —<br>
    stress_raw = —<br>
    stress = EMA(0.7·prev + 0.3·raw)

  </div>


  <div
    class="notice"
    style="margin-top:9px">

    * O índice é experimental e não clínico.
    Áudio e iluminação podem ser estimativas não calibradas.

  </div>

</div>


<!-- =========================================================
     ÁUDIO
========================================================= -->

<div class="card">

  <div class="between">

    <div>

      <div class="title">
        🎙️ Áudio ambiente
      </div>

      <div class="muted">
        Índice relativo baseado no microfone
      </div>

    </div>

    <span
      class="badge"
      id="audioBadge">
      OFF
    </span>

  </div>


  <div
    class="value"
    id="audioIndex">
    —
  </div>


  <button id="audioBtn">
    Ativar microfone
  </button>


  <div
    class="notice"
    style="margin-top:8px">

    O valor não representa dB SPL calibrado.
    É um índice relativo para comparação experimental.

  </div>

</div>


<!-- =========================================================
     LUZ
========================================================= -->

<div class="card">

  <div class="between">

    <div>

      <div class="title">
        💡 Iluminação
      </div>

      <div class="muted">
        Sensor nativo ou câmera como fallback
      </div>

    </div>

    <span
      class="badge"
      id="lightBadge">
      OFF
    </span>

  </div>


  <div
    class="value"
    id="lightIndex">
    —
  </div>


  <button id="lightBtn">
    Ativar luz
  </button>


  <div
    class="notice"
    style="margin-top:8px">

    Quando derivada da câmera,
    a iluminação é uma estimativa relativa,
    não lux calibrado.

  </div>

</div>


<!-- =========================================================
     MOVIMENTO
========================================================= -->

<div class="card">

  <div class="between">

    <div>

      <div class="title">
        🚶 Movimento
      </div>

      <div class="muted">
        Acelerômetro / estado aproximado
      </div>

    </div>

    <span
      class="badge"
      id="motionBadge">
      OFF
    </span>

  </div>


  <div class="grid3">

    <div class="sensor">

      <div class="name">
        X
      </div>

      <div
        class="num"
        id="mx">
        —
      </div>

    </div>


    <div class="sensor">

      <div class="name">
        Y
      </div>

      <div
        class="num"
        id="my">
        —
      </div>

    </div>


    <div class="sensor">

      <div class="name">
        Z
      </div>

      <div
        class="num"
        id="mz">
        —
      </div>

    </div>

  </div>


  <div
    class="between"
    style="margin-top:9px">

    <span
      class="badge"
      id="movementText">
      indisponível
    </span>

    <span
      class="muted"
      id="movementMag">
      MAG —
    </span>

  </div>


  <button
    id="motionBtn"
    style="margin-top:10px">

    Ativar movimento

  </button>

</div>


<!-- =========================================================
     ORIENTAÇÃO
========================================================= -->

<div class="card">

  <div class="between">

    <div>

      <div class="title">
        🧭 Orientação
      </div>

      <div class="muted">
        Bússola quando suportada pelo aparelho
      </div>

    </div>

    <span
      class="badge"
      id="orientationBadge">
      OFF
    </span>

  </div>


  <div class="compass">

    <div
      id="needle"
      class="needle">
    </div>

    <span id="compassText">
      —°
    </span>

  </div>


  <div
    class="muted"
    style="text-align:center;margin:7px 0"
    id="orientationHint">

    Sem orientação disponível

  </div>


  <button id="orientationBtn">
    Ativar orientação
  </button>

</div>


<!-- =========================================================
     GPS + BATERIA
========================================================= -->

<div class="card">

  <div class="title">
    📍 Localização + 🔋 energia
  </div>


  <div
    class="grid"
    style="margin-top:9px">


    <div class="sensor">

      <div class="name">
        GPS
      </div>

      <div
        class="num"
        id="gpsDetail">
        —
      </div>

      <div
        class="muted"
        id="gpsAccuracy">
        —
      </div>

    </div>


    <div class="sensor">

      <div class="name">
        BATERIA
      </div>

      <div
        class="num"
        id="batteryDetail">
        —
      </div>

      <div
        class="muted"
        id="batteryDetailState">
        —
      </div>

    </div>

  </div>


  <div
    class="row"
    style="margin-top:10px">

    <button id="gpsBtn">
      Ativar GPS
    </button>

    <button id="batteryBtn">
      Ler bateria
    </button>

  </div>

</div>


<!-- =========================================================
     OBSERVAÇÃO
========================================================= -->

<div class="card">

  <div class="title">
    📝 Observação
  </div>


  <textarea
    id="note"
    placeholder="O que você percebeu neste lugar?">
  </textarea>


  <div
    class="row"
    style="margin-top:9px">

    <button id="voiceNoteBtn">
      🎤 Nota de voz
    </button>

    <button
      id="clearNoteBtn"
      class="small">
      Limpar
    </button>

  </div>


  <div
    class="muted"
    id="voiceStatus"
    style="margin-top:7px">

    Nenhuma nota de voz registrada.

  </div>

</div>


<!-- =========================================================
     MEMÓRIAS SENSORIAIS
========================================================= -->

<div class="card">

  <div class="between">

    <div>

      <div class="title">
        💾 Memórias Sensoriais
      </div>

      <div class="muted">
        Registros armazenados neste aparelho
      </div>

    </div>


    <button
      id="clearMemoriesBtn"
      class="small danger">

      Apagar tudo

    </button>

  </div>


  <div id="memoryList">

    <div
      class="muted"
      style="margin-top:10px">

      Nenhuma memória ainda.

    </div>

  </div>

</div>


<!-- =========================================================
     PRINCÍPIO REMINA
========================================================= -->

<div class="card">

  <div class="title">
    ℹ️ Princípio REMINA
  </div>


  <p class="notice">

    O celular é o primeiro laboratório e ponte.

    O AURA SUIT percebe sinais do corpo.

    O NEXUS TACTILE representa a futura camada tátil.

    O Synapse OS coordena percepção, contexto,
    comunicação e resposta.

  </p>


  <p class="notice">

    Este protótipo não diagnostica,
    não promete correção clínica
    e não substitui avaliação profissional.

  </p>

</div>


</section>

</main>


<!-- =========================================================
     BOTÃO ESTIVE AQUI
========================================================= -->

<div class="fixed">

  <button
    id="estiveBtn"
    class="primary">

    📍 ESTIVE AQUI • CAPTURAR MEMÓRIA

  </button>

</div>


<!-- =========================================================
     TOAST
========================================================= -->

<div
  id="toast"
  class="toast hidden"
  role="status"
  aria-live="polite">
</div>


<!-- =========================================================
     CANVAS INVISÍVEL PARA ANÁLISE DE LUZ
========================================================= -->

<canvas
  id="analysisCanvas"
  width="64"
  height="64"
  class="hidden">
</canvas>
<script>
'use strict';

/* =========================================================
   REMINA MOBILE SENSOR LAB
   ENGINE v1.3
========================================================= */

const $ = id => document.getElementById(id);

const S = {

  /* CÂMERA */
  cameraStream: null,
  cameraFacing: 'environment',
  torch: false,

  /* ÁUDIO */
  audioStream: null,
  audioCtx: null,
  analyser: null,
  audioData: null,
  audioIndex: null,

  /* LUZ */
  lightIndex: null,
  lightConfidence: 0,
  lightSensor: null,
  cameraLightTimer: null,

  /* MOVIMENTO */
  motion: null,
  motionMagnitude: null,
  motionActive: false,

  /* ORIENTAÇÃO */
  heading: null,
  orientationActive: false,

  /* GPS */
  gps: null,
  gpsWatch: null,

  /* BATERIA */
  battery: null,
  batteryCharging: null,

  /* CROSS-MODAL */
  stress: 0,
  stressRaw: 0,

  /* NOTA */
  voiceNote: null,

  /* VÍDEO */
  recording: false,
  recorder: null,
  chunks: [],

  /* CAPTURAS */
  lastPhotoBlob: null,
  lastVideoBlob: null
};


/* =========================================================
   UTILIDADES
========================================================= */

function toast(message){

  const el = $('toast');

  if(!el) return;

  el.textContent = message;

  el.classList.remove('hidden');

  clearTimeout(toast.timer);

  toast.timer = setTimeout(() => {

    el.classList.add('hidden');

  }, 2600);
}


function clamp(value, min = 0, max = 1){

  return Math.max(
    min,
    Math.min(max, value)
  );

}


function fixed(value, digits = 1){

  return Number.isFinite(value)
    ? value.toFixed(digits)
    : '—';

}


function vibrate(pattern = [35]){

  try{

    if(
      'vibrate' in navigator &&
      typeof navigator.vibrate === 'function'
    ){

      navigator.vibrate(pattern);

    }

  }catch(error){

    console.warn(
      'Vibração indisponível.',
      error
    );

  }

}


function setBadge(id, active, text){

  const el = $(id);

  if(!el) return;

  el.textContent =
    text ||
    (active ? 'ON' : 'OFF');

  el.className =
    'badge ' +
    (active ? 'ok' : '');

}


function escapeHTML(value){

  return String(value ?? '')
    .replace(
      /[&<>"']/g,
      char => ({
        '&':'&amp;',
        '<':'&lt;',
        '>':'&gt;',
        '"':'&quot;',
        "'":'&#039;'
      })[char]
    );

}


/* =========================================================
   CONTAGEM REAL DE SENSORES
========================================================= */

function updateSensorCoverage(){

  let count = 0;

  if(S.audioIndex !== null)
    count++;

  if(S.lightIndex !== null)
    count++;

  if(S.motion !== null)
    count++;

  if(S.heading !== null)
    count++;

  if(S.gps !== null)
    count++;

  if(S.battery !== null)
    count++;

  $('coverage').textContent =
    count + '/6 sensores';

}


/* =========================================================
   INDEXEDDB
   MEMÓRIA SENSORIAL LOCAL
========================================================= */

const DB_NAME =
  'remina_mobile_sensor_lab_v13';

const DB_VERSION = 1;

const STORE_NAME =
  'sensory_records';


function openDatabase(){

  return new Promise(
    (resolve, reject) => {

      if(!window.indexedDB){

        reject(
          new Error(
            'IndexedDB indisponível.'
          )
        );

        return;
      }


      const request =
        indexedDB.open(
          DB_NAME,
          DB_VERSION
        );


      request.onupgradeneeded =
        event => {

          const db =
            event.target.result;

          if(
            !db.objectStoreNames
              .contains(STORE_NAME)
          ){

            db.createObjectStore(
              STORE_NAME,
              {
                keyPath:'id',
                autoIncrement:true
              }
            );

          }

        };


      request.onsuccess =
        event => {

          resolve(
            event.target.result
          );

        };


      request.onerror =
        () => {

          reject(
            request.error ||
            new Error(
              'Erro no banco local.'
            )
          );

        };

    }
  );

}


async function saveMemory(record){

  const db =
    await openDatabase();

  return new Promise(
    (resolve, reject) => {

      const transaction =
        db.transaction(
          STORE_NAME,
          'readwrite'
        );

      const store =
        transaction.objectStore(
          STORE_NAME
        );

      const request =
        store.add(record);


      request.onsuccess =
        () => resolve(
          request.result
        );


      request.onerror =
        () => reject(
          request.error
        );

    }
  );

}


async function getMemories(){

  const db =
    await openDatabase();

  return new Promise(
    (resolve, reject) => {

      const transaction =
        db.transaction(
          STORE_NAME,
          'readonly'
        );

      const store =
        transaction.objectStore(
          STORE_NAME
        );

      const request =
        store.getAll();


      request.onsuccess =
        () => {

          const records =
            request.result || [];

          records.reverse();

          resolve(records);

        };


      request.onerror =
        () => reject(
          request.error
        );

    }
  );

}


async function deleteMemory(id){

  const db =
    await openDatabase();

  return new Promise(
    (resolve, reject) => {

      const transaction =
        db.transaction(
          STORE_NAME,
          'readwrite'
        );

      const store =
        transaction.objectStore(
          STORE_NAME
        );

      const request =
        store.delete(id);


      request.onsuccess =
        () => resolve();


      request.onerror =
        () => reject(
          request.error
        );

    }
  );

}


async function clearMemories(){

  const db =
    await openDatabase();

  return new Promise(
    (resolve, reject) => {

      const transaction =
        db.transaction(
          STORE_NAME,
          'readwrite'
        );

      const request =
        transaction
          .objectStore(STORE_NAME)
          .clear();


      request.onsuccess =
        () => resolve();


      request.onerror =
        () => reject(
          request.error
        );

    }
  );

}


/* =========================================================
   CÂMERA
========================================================= */

async function startCamera(){

  if(
    !window.isSecureContext &&
    location.hostname !== 'localhost'
  ){

    toast(
      'A câmera precisa de HTTPS.'
    );

    return false;

  }


  if(
    !navigator.mediaDevices ||
    !navigator.mediaDevices.getUserMedia
  ){

    toast(
      'Este navegador não suporta câmera.'
    );

    return false;

  }


  try{

    if(S.cameraStream){

      S.cameraStream
        .getTracks()
        .forEach(
          track => track.stop()
        );

    }


    S.cameraStream =
      await navigator.mediaDevices
        .getUserMedia({

          video:{
            facingMode:{
              ideal:
                S.cameraFacing
            },

            width:{
              ideal:1280
            },

            height:{
              ideal:720
            }
          },

          audio:false

        });


    const video =
      $('camera');

    video.srcObject =
      S.cameraStream;

    await video.play();


    $('gate')
      .classList
      .add('hidden');


    $('liveBadge').textContent =
      '● câmera ativa';

    $('liveBadge').className =
      'badge ok';


    toast(
      'Câmera REMINA ativa.'
    );


    return true;


  }catch(error){

    console.error(
      'Câmera:',
      error
    );


    toast(
      'Não foi possível abrir a câmera: ' +
      (
        error.name ||
        'permissão negada'
      )
    );


    return false;

  }

}


async function flipCamera(){

  S.cameraFacing =
    S.cameraFacing === 'environment'
      ? 'user'
      : 'environment';


  await startCamera();

}


async function toggleTorch(){

  const stream =
    S.cameraStream;

  if(!stream){

    toast(
      'Abra a câmera primeiro.'
    );

    return;

  }


  const tracks =
    stream.getVideoTracks();


  if(!tracks.length){

    toast(
      'Trilha de vídeo indisponível.'
    );

    return;

  }


  const track =
    tracks[0];


  const capabilities =
    track.getCapabilities
      ? track.getCapabilities()
      : {};


  if(!capabilities.torch){

    toast(
      'A lanterna/torch não é suportada neste aparelho.'
    );

    return;

  }


  try{

    S.torch =
      !S.torch;


    await track.applyConstraints({

      advanced:[
        {
          torch:S.torch
        }
      ]

    });


    $('torchBtn').textContent =
      S.torch
        ? '🔦✓'
        : '🔦';


  }catch(error){

    console.error(
      'Torch:',
      error
    );

    toast(
      'Não foi possível controlar a lanterna.'
    );

  }

}


/* =========================================================
   FOTO
========================================================= */

async function capturePhoto(){

  const video =
    $('camera');


  if(
    !video.videoWidth ||
    !video.videoHeight
  ){

    toast(
      'A câmera ainda não está pronta.'
    );

    return null;

  }


  const canvas =
    document.createElement(
      'canvas'
    );


  canvas.width =
    video.videoWidth;

  canvas.height =
    video.videoHeight;


  const context =
    canvas.getContext(
      '2d'
    );


  context.drawImage(
    video,
    0,
    0,
    canvas.width,
    canvas.height
  );


  const blob =
    await new Promise(
      resolve =>
        canvas.toBlob(
          resolve,
          'image/jpeg',
          .90
        )
    );


  if(!blob){

    toast(
      'Não foi possível criar a foto.'
    );

    return null;

  }


  S.lastPhotoBlob =
    blob;


  vibrate([45]);


  toast(
    '📸 Foto capturada.'
  );


  return blob;

}


/* =========================================================
   VÍDEO
========================================================= */

function getVideoMimeType(){

  if(!window.MediaRecorder)
    return '';


  const types = [

    'video/webm;codecs=vp9,opus',

    'video/webm;codecs=vp8,opus',

    'video/webm'

  ];


  return types.find(
    type =>
      MediaRecorder
        .isTypeSupported(type)
  ) || '';

}


function startRecording(){

  if(S.recording)
    return;


  if(!S.cameraStream){

    toast(
      'Abra a câmera primeiro.'
    );

    return;

  }


  if(!window.MediaRecorder){

    toast(
      'Gravação de vídeo não suportada.'
    );

    return;

  }


  const mime =
    getVideoMimeType();


  try{

    S.chunks = [];


    S.recorder =
      mime
        ? new MediaRecorder(
            S.cameraStream,
            {
              mimeType:mime
            }
          )
        : new MediaRecorder(
            S.cameraStream
          );


    S.recorder.ondataavailable =
      event => {

        if(
          event.data &&
          event.data.size > 0
        ){

          S.chunks.push(
            event.data
          );

        }

      };


    S.recorder.onstop =
      () => {

        const blob =
          new Blob(
            S.chunks,
            {
              type:
                S.recorder.mimeType ||
                'video/webm'
            }
          );


        S.lastVideoBlob =
          blob;


        S.recording =
          false;


        $('captureBtn')
          .classList
          .remove('recording');


        $('videoBtn').textContent =
          '🎥 VÍDEO';


        vibrate(
          [50,30,50]
        );


        toast(
          '🎥 Vídeo capturado.'
        );

      };


    S.recorder.start();

    S.recording =
      true;


    $('captureBtn')
      .classList
      .add('recording');


    $('videoBtn').textContent =
      '⏹️ PARAR';


    vibrate([35]);


  }catch(error){

    console.error(
      'MediaRecorder:',
      error
    );

    toast(
      'Não foi possível iniciar o vídeo.'
    );

  }

}


function stopRecording(){

  if(
    S.recording &&
    S.recorder
  ){

    S.recorder.stop();

  }

}


/* =========================================================
   ÁUDIO
========================================================= */

async function startAudio(){

  if(S.audioStream){

    stopAudio();

    return;

  }


  if(
    !navigator.mediaDevices ||
    !navigator.mediaDevices.getUserMedia
  ){

    toast(
      'Microfone não suportado.'
    );

    return;

  }


  try{

    S.audioStream =
      await navigator.mediaDevices
        .getUserMedia({
          audio:true,
          video:false
        });


    const AudioContext =
      window.AudioContext ||
      window.webkitAudioContext;


    if(!AudioContext){

      throw new Error(
        'Web Audio indisponível.'
      );

    }


    S.audioCtx =
      new AudioContext();


    const source =
      S.audioCtx
        .createMediaStreamSource(
          S.audioStream
        );


    S.analyser =
      S.audioCtx
        .createAnalyser();


    S.analyser.fftSize =
      1024;


    S.audioData =
      new Uint8Array(
        S.analyser.fftSize
      );


    source.connect(
      S.analyser
    );


    setBadge(
      'audioBadge',
      true,
      'ON'
    );


    $('audioBtn').textContent =
      'Pausar microfone';


    $('audioState').textContent =
      'ativo';


    audioLoop();


    toast(
      '🎙️ Microfone ativo.'
    );


  }catch(error){

    console.error(
      'Áudio:',
      error
    );


    stopAudio();


    toast(
      'Microfone indisponível ou permissão negada.'
    );

  }

}


function stopAudio(){

  if(S.audioStream){

    S.audioStream
      .getTracks()
      .forEach(
        track => track.stop()
      );

  }


  try{

    if(S.audioCtx)
      S.audioCtx.close();

  }catch(error){}


  S.audioStream =
    null;

  S.audioCtx =
    null;

  S.analyser =
    null;

  S.audioData =
    null;

  S.audioIndex =
    null;


  setBadge(
    'audioBadge',
    false,
    'OFF'
  );


  $('audioBtn').textContent =
    'Ativar microfone';


  $('audioState').textContent =
    'indisponível';


  $('audioIndex').textContent =
    '—';


  updateCrossModal();

}


function audioLoop(){

  if(!S.analyser)
    return;


  S.analyser
    .getByteTimeDomainData(
      S.audioData
    );


  let sum = 0;


  for(
    let i=0;
    i<S.audioData.length;
    i++
  ){

    const sample =
      (
        S.audioData[i] -
        128
      ) / 128;


    sum +=
      sample *
      sample;

  }


  const rms =
    Math.sqrt(
      sum /
      S.audioData.length
    );


  /*
    Índice relativo.
    Não é dB SPL calibrado.
  */

  S.audioIndex =
    Math.round(
      clamp(
        rms * 4.5
      ) * 100
    );


  $('audioIndex').textContent =
    S.audioIndex + '%';


  $('audioVal').textContent =
    S.audioIndex + '%';


  updateCrossModal();


  requestAnimationFrame(
    audioLoop
  );

}


/* =========================================================
   LUZ
========================================================= */

async function startLight(){

  if(
    'AmbientLightSensor' in window
  ){

    try{

      if(S.lightSensor){

        S.lightSensor.stop?.();

      }


      S.lightSensor =
        new AmbientLightSensor();


      S.lightSensor
        .addEventListener(
          'reading',
          () => {

            const lux =
              Math.max(
                0,
                S.lightSensor
                  .illuminance || 0
              );


            S.lightIndex =
              Math.round(
                clamp(
                  lux / 900
                ) * 100
              );


            S.lightConfidence =
              .95;


            renderLight(
              'sensor'
            );

          }
        );


      S.lightSensor
        .addEventListener(
          'error',
          () => {

            startCameraLight();

          }
        );


      S.lightSensor.start();


      setBadge(
        'lightBadge',
        true,
        'SENSOR'
      );


      toast(
        '💡 Sensor de luz nativo solicitado.'
      );


      return;

    }catch(error){

      console.warn(
        'Sensor de luz nativo:',
        error
      );

    }

  }


  startCameraLight();

}


function startCameraLight(){

  setBadge(
    'lightBadge',
    true,
    'CÂMERA*'
  );


  if(S.cameraLightTimer){

    clearInterval(
      S.cameraLightTimer
    );

  }


  S.cameraLightTimer =
    setInterval(
      () => {

        const video =
          $('camera');


        if(
          !video.videoWidth ||
          !video.videoHeight
        )
          return;


        const canvas =
          $('analysisCanvas');


        const context =
          canvas.getContext(
            '2d',
            {
              willReadFrequently:true
            }
          );


        context.drawImage(
          video,
          0,
          0,
          64,
          64
        );


        const pixels =
          context.getImageData(
            0,
            0,
            64,
            64
          ).data;


        let sum = 0;


        for(
          let i=0;
          i<pixels.length;
          i+=4
        ){

          const luminance =
            .2126 * pixels[i] +
            .7152 * pixels[i+1] +
            .0722 * pixels[i+2];


          sum += luminance;

        }


        const average =
          sum /
          (pixels.length / 4);


        S.lightIndex =
          Math.round(
            clamp(
              average / 255
            ) * 100
          );


        S.lightConfidence =
          .45;


        renderLight(
          'câmera*'
        );

      },
      700
    );

}


function renderLight(source){

  $('lightIndex').textContent =
    S.lightIndex + '%';


  $('lightVal').textContent =
    S.lightIndex + '%';


  $('lightState').textContent =
    source +
    (
      S.lightConfidence < .6
        ? ' • estimado'
        : ''
    );


  updateCrossModal();

}


/* =========================================================
   MOVIMENTO
========================================================= */

async function startMotion(){

  if(
    !('DeviceMotionEvent' in window)
  ){

    toast(
      'Movimento não é suportado neste aparelho.'
    );

    return;

  }


  try{

    if(
      typeof DeviceMotionEvent
        .requestPermission ===
      'function'
    ){

      const permission =
        await DeviceMotionEvent
          .requestPermission();


      if(
        permission !== 'granted'
      ){

        throw new Error(
          'Permissão de movimento negada.'
        );

      }

    }


    window.addEventListener(
      'devicemotion',
      handleMotion
    );


    S.motionActive =
      true;


    setBadge(
      'motionBadge',
      true,
      'ON'
    );


    $('motionBtn').textContent =
      'Pausar movimento';


    toast(
      '🚶 Movimento ativo.'
    );


  }catch(error){

    console.error(
      'Movimento:',
      error
    );


    toast(
      'Permissão de movimento não concedida.'
    );

  }

}


function stopMotion(){

  window.removeEventListener(
    'devicemotion',
    handleMotion
  );


  S.motionActive =
    false;

  S.motion =
    null;

  S.motionMagnitude =
    null;


  setBadge(
    'motionBadge',
    false,
    'OFF'
  );


  $('motionBtn').textContent =
    'Ativar movimento';


  $('movementText').textContent =
    'indisponível';


  $('movementMag').textContent =
    'MAG —';


  $('motionVal').textContent =
    '—';


  updateCrossModal();

}


function handleMotion(event){

  const acceleration =
    event.accelerationIncludingGravity ||
    event.acceleration;


  if(!acceleration)
    return;


  const x =
    Number(acceleration.x) || 0;

  const y =
    Number(acceleration.y) || 0;

  const z =
<script>
/* =========================================================
   CROSS-MODAL ENGINE
========================================================= */

function getMovementNorm(){

  if(
    !Number.isFinite(
      S.motionMagnitude
    )
  ){

    return null;

  }

  const deviation =
    Math.abs(
      S.motionMagnitude - 9.81
    );

  return clamp(
    deviation / 6
  );

}


function updateCrossModal(){

  const values = [];

  let weightedSum = 0;
  let weightSum = 0;


  /* ÁUDIO */

  if(
    Number.isFinite(
      S.audioIndex
    )
  ){

    const audioNorm =
      clamp(
        S.audioIndex / 100
      );

    weightedSum +=
      .4 * audioNorm;

    weightSum += .4;

    values.push(
      audioNorm
    );

  }


  /* LUZ */

  if(
    Number.isFinite(
      S.lightIndex
    )
  ){

    const lightNorm =
      clamp(
        S.lightIndex / 100
      );

    weightedSum +=
      .3 * lightNorm;

    weightSum += .3;

    values.push(
      lightNorm
    );

  }


  /* MOVIMENTO */

  const movementNorm =
    getMovementNorm();


  if(
    Number.isFinite(
      movementNorm
    )
  ){

    weightedSum +=
      .3 * movementNorm;

    weightSum += .3;

    values.push(
      movementNorm
    );

  }


  /*
    Se nenhum dos três sensores
    estiver disponível, não inventamos
    um índice.
  */

  if(weightSum === 0){

    $('stressValue').textContent =
      '—';

    $('stressBar').style.width =
      '0%';

    return;

  }


  const raw =
    clamp(
      weightedSum /
      weightSum
    );


  /*
    EMA:
    stress = 0.7 * anterior
           + 0.3 * atual
  */

  S.stressRaw =
    raw;


  S.stress =
    clamp(
      0.7 * S.stress +
      0.3 * raw
    );


  const index =
    Math.round(
      S.stress * 100
    );


  $('stressValue').textContent =
    index + '%';


  $('stressBar').style.width =
    index + '%';


  /*
    Atualiza fórmula visual
  */

  const audioN =
    Number.isFinite(
      S.audioIndex
    )
      ? (
          S.audioIndex / 100
        ).toFixed(2)
      : '—';


  const lightN =
    Number.isFinite(
      S.lightIndex
    )
      ? (
          S.lightIndex / 100
        ).toFixed(2)
      : '—';


  const moveN =
    Number.isFinite(
      movementNorm
    )
      ? movementNorm.toFixed(2)
      : '—';


  const vibParameter =
    Math.round(
      50 +
      200 * S.stress
    );


  $('formulaBox').innerHTML =

    'audio_norm = ' +
    audioN +

    '<br>light_norm = ' +
    lightN +

    '<br>movement_norm = ' +
    moveN +

    '<br><br>' +

    'stress_raw = ' +
    '(0.4·audio + 0.3·light + 0.3·movement)' +

    '<br>' +

    'stress = EMA(0.7·prev + 0.3·raw)' +

    '<br>' +

    'stress = ' +
    S.stress.toFixed(2) +

    '<br>' +

    'f_vib = ' +
    vibParameter +
    ' → parâmetro de controle';


  /*
    Vibração somente quando a faixa
    muda. Não vibrar a cada leitura.
  */

  updateStressHaptic(
    index
  );


  updateSensorCoverage();

}


/* =========================================================
   HÁPTICA ADAPTATIVA
========================================================= */

let lastStressBand =
  -1;

let lastHapticTime =
  0;


function updateStressHaptic(index){

  const now =
    Date.now();


  const band =
    index < 33
      ? 0
      : index < 66
        ? 1
        : 2;


  if(
    band === lastStressBand
  )
    return;


  if(
    now - lastHapticTime <
    1800
  )
    return;


  lastStressBand =
    band;


  lastHapticTime =
    now;


  if(band === 0){

    vibrate(
      [25]
    );

  }else if(band === 1){

    vibrate(
      [25,60,25]
    );

  }else{

    vibrate(
      [35,60,35,60,50]
    );

  }

}


/* =========================================================
   CLASSIFICAÇÃO DE ÁUDIO
========================================================= */

function getAudioClass(index){

  if(index === null)
    return 'indisponível';

  if(index < 25)
    return 'silencioso';

  if(index < 50)
    return 'confortável';

  if(index < 75)
    return 'intenso';

  return 'esmagador';

}


/* =========================================================
   CLASSIFICAÇÃO DE LUZ
========================================================= */

function getLightClass(index){

  if(index === null)
    return 'indisponível';

  if(index < 55)
    return 'acolhedora';

  return 'agressiva';

}


/* =========================================================
   NOTA POR VOZ
   Web Speech = TRANSCRIÇÃO.
   Não é gravação de áudio.
========================================================= */

let recognition =
  null;


function startVoiceNote(){

  const SpeechRecognition =
    window.SpeechRecognition ||
    window.webkitSpeechRecognition;


  if(!SpeechRecognition){

    toast(
      'Reconhecimento de voz não é suportado neste navegador.'
    );

    return;

  }


  if(recognition){

    try{

      recognition.stop();

    }catch(error){}

    recognition =
      null;

  }


  recognition =
    new SpeechRecognition();


  recognition.lang =
    'pt-BR';


  recognition.interimResults =
    true;


  recognition.continuous =
    false;


  recognition.onstart =
    () => {

      $('voiceStatus').textContent =
        '🎙️ ouvindo...';

      vibrate([25]);

    };


  recognition.onresult =
    event => {

      let transcript =
        '';


      for(
        let i =
          event.resultIndex;
        i <
          event.results.length;
        i++
      ){

        transcript +=
          event.results[i][0]
            .transcript;

      }


      transcript =
        transcript.trim();


      if(transcript){

        S.voiceNote =
          transcript;


        $('note').value =
          transcript;

      }

    };


  recognition.onerror =
    event => {

      console.warn(
        'SpeechRecognition:',
        event
      );


      $('voiceStatus').textContent =
        'voz indisponível';


      toast(
        'Não foi possível reconhecer a voz.'
      );

    };


  recognition.onend =
    () => {

      $('voiceStatus').textContent =
        S.voiceNote
          ? 'nota transcrita'
          : 'pronto';

    };


  try{

    recognition.start();

  }catch(error){

    console.error(
      error
    );

    toast(
      'Não foi possível iniciar o reconhecimento.'
    );

  }

}


/* =========================================================
   ESTIVE AQUI
========================================================= */

async function captureEstiveAqui(){

  /*
    Se a câmera ainda não estiver aberta,
    tentamos abrir.
  */

  if(!S.cameraStream){

    const started =
      await startCamera();


    if(!started){

      toast(
        'Abra a câmera para registrar o local.'
      );

      return;

    }

  }


  /*
    Foto nova para esta memória.
  */

  const photo =
    await capturePhoto();


  /*
    Recalcula o estado antes de salvar.
  */

  updateCrossModal();


  const record = {

    version:
      'REMINA-MSL-1.3',


    createdAt:
      Date.now(),


    type:
      'ESTIVE_AQUI',


    photo:
      photo || null,


    video:
      S.lastVideoBlob || null,


    audio:{

      available:
        Number.isFinite(
          S.audioIndex
        ),

      estimatedIndex:
        S.audioIndex,

      confidence:
        Number.isFinite(
          S.audioIndex
        )
          ? 0.60
          : 0,

      classification:
        getAudioClass(
          S.audioIndex
        )

    },


    light:{

      available:
        Number.isFinite(
          S.lightIndex
        ),

      estimatedPercent:
        S.lightIndex,

      confidence:
        S.lightConfidence,

      classification:
        getLightClass(
          S.lightIndex
        )

    },


    movement:{

      available:
        !!S.motion,

      x:
        S.motion
          ? S.motion.x
          : null,

      y:
        S.motion
          ? S.motion.y
          : null,

      z:
        S.motion
          ? S.motion.z
          : null,

      magnitude:
        S.motionMagnitude,

      state:
        $('movementText').textContent

    },


    orientation:{

      available:
        Number.isFinite(
          S.heading
        ),

      heading:
        S.heading

    },


    gps:

      S.gps
        ? {

            latitude:
              S.gps.lat,

            longitude:
              S.gps.lng,

            accuracy:
              S.gps.accuracy

          }

        : null,


    battery:

      S.battery !== null
        ? {

            level:
              S.battery,

            charging:
              !!S.batteryCharging

          }

        : null,


    crossModal:{

      stressRaw:
        S.stressRaw,

      stress:
        S.stress,

      index:
        Math.round(
          S.stress * 100
        )

    },


    note:
      $('note').value.trim(),


    voiceNote:
      S.voiceNote || null,


    sensors:{

      camera:
        !!photo,

      microphone:
        Number.isFinite(
          S.audioIndex
        ),

      light:
        Number.isFinite(
          S.lightIndex
        ),

      motion:
        !!S.motion,

      orientation:
        Number.isFinite(
          S.heading
        ),

      gps:
        !!S.gps,

      battery:
        S.battery !== null

    }

  };


  try{

    const id =
      await saveMemory(
        record
      );


    /*
      O vídeo recente passa a pertencer
      a esta memória e não será duplicado
      no próximo registro.
    */

    S.lastVideoBlob =
      null;


    vibrate(
      [60,30,60]
    );


    toast(
      '📍 ESTIVE AQUI registrado.'
    );


    await renderMemories();


  }catch(error){

    console.error(
      'ESTIVE AQUI:',
      error
    );


    toast(
      'Erro ao salvar a memória local.'
    );

  }

}


/* =========================================================
   MEMÓRIAS SENSORIAIS
========================================================= */

async function renderMemories(){

  const container =
    $('memoryList');


  if(!container)
    return;


  container.innerHTML =
    '<div class="muted">Carregando memórias...</div>';


  let records = [];


  try{

    records =
      await getMemories();

  }catch(error){

    console.error(
      error
    );


    container.innerHTML =
      '<div class="muted">Memória local indisponível.</div>';


    return;

  }


  if(!records.length){

    container.innerHTML =
      '<div class="muted">' +
      'Nenhuma memória registrada ainda.' +
      '</div>';

    return;

  }


  container.innerHTML =
    '';


  records.forEach(
    record => {

      const card =
        document.createElement(
          'article'
        );


      card.className =
        'memory';


      const date =
        new Date(
          record.createdAt
        );


      const dateText =
        date.toLocaleString(
          'pt-BR'
        );


      const index =
        Number.isFinite(
          record.crossModal?.index
        )
          ? record.crossModal.index
          : null;


      let mediaHTML =
        '';


      if(record.photo){

        const photoURL =
          URL.createObjectURL(
            record.photo
          );


        mediaHTML +=
          '<img ' +
          'class="memory-photo" ' +
          'src="' +
          photoURL +
          '" ' +
          'alt="Registro visual REMINA">' ;

      }


      if(record.video){

        const videoURL =
          URL.createObjectURL(
            record.video
          );


        mediaHTML +=
          '<video ' +
          'class="memory-video" ' +
          'src="' +
          videoURL +
          '" ' +
          'controls ' +
          'playsinline>' +
          '</video>';

      }


      let locationHTML =
        '';


      if(record.gps){

        locationHTML =
          '<div>📍 ' +
          Number(
            record.gps.latitude
          ).toFixed(5) +
          ', ' +
          Number(
            record.gps.longitude
          ).toFixed(5) +
          '<br>' +
          'Precisão ±' +
          Math.round(
            record.gps.accuracy || 0
          ) +
          ' m</div>';

      }else{

        locationHTML =
          '<div>📍 GPS indisponível</div>';

      }


      const note =
        record.note
          ? escapeHTML(
              record.note
            )
          : 'Sem observação';


      card.innerHTML =

        '<div class="memory-head">' +

          '<strong>ESTIVE AQUI</strong>' +

          '<span>' +
          escapeHTML(
            dateText
          ) +
          '</span>' +

        '</div>' +


        mediaHTML +


        '<div class="memory-data">' +

          locationHTML +

          '<div>🎙️ Áudio: ' +
          escapeHTML(
            record.audio?.classification ||
            'indisponível'
          ) +
          '</div>' +

          '<div>💡 Luz: ' +
          escapeHTML(
            record.light?.classification ||
            'indisponível'
          ) +
          '</div>' +

          '<div>🚶 Movimento: ' +
          escapeHTML(
            record.movement?.state ||
            'indisponível'
          ) +
          '</div>' +

          '<div>🧭 Direção: ' +
          (
            Number.isFinite(
              record.orientation?.heading
            )
              ? Math.round(
                  record.orientation.heading
                ) + '°'
              : 'indisponível'
          ) +
          '</div>' +

          '<div>🔋 Bateria: ' +
          (
            Number.isFinite(
              record.battery?.level
            )
              ? record.battery.level + '%'
              : 'indisponível'
          ) +
          '</div>' +

          '<div>🧠 Índice Cross-Modal: ' +
          (
            index !== null
              ? index + '%'
              : '—'
          ) +
          '</div>' +

        '</div>' +


        '<div class="memory-note">' +
          '📝 ' +
          note +
        '</div>' +


        '<div class="memory-actions">' +

          '<button ' +
          'class="secondary downloadPhoto">' +
          'Salvar foto' +
          '</button>' +

          '<button ' +
          'class="secondary deleteMemory">' +
          'Excluir' +
          '</button>' +

        '</div>';


      const downloadPhoto =
        card.querySelector(
          '.downloadPhoto'
        );


      if(
        !record.photo
      ){

        downloadPhoto.disabled =
          true;

        downloadPhoto.textContent =
          'Sem foto';

      }else{

        downloadPhoto.onclick =
          () => {

            const url =
              URL.createObjectURL(
                record.photo
              );


            const link =
              document.createElement(
                'a'
              );


            link.href =
              url;


            link.download =
              'remina-' +
              record.createdAt +
              '.jpg';


            document.body
              .appendChild(
                link
              );


            link.click();


            link.remove();


            setTimeout(
              () =>
                URL.revokeObjectURL(
                  url
                ),
              1000
            );

          };

      }


      card.querySelector(
        '.deleteMemory'
      ).onclick =
        async () => {

          if(
            !confirm(
              'Excluir esta memória?'
            )
          )
            return;


          try{

            await deleteMemory(
              record.id
            );


            await renderMemories();


            toast(
              'Memória excluída.'
            );

          }catch(error){

            console.error(
              error
            );


            toast(
              'Não foi possível excluir.'
            );

          }

        };


      container.appendChild(
        card
      );

    }
  );

}


/* =========================================================
   LIMPAR NOTA
========================================================= */

function clearNote(){

  $('note').value =
    '';


  S.voiceNote =
    null;


  $('voiceStatus').textContent =
    'pronto';

}


/* =========================================================
   BOTÕES DA INTERFACE
========================================================= */

$('startBtn').addEventListener(
  'click',
  async () => {

    await startCamera();

  }
);


$('flipBtn').addEventListener(
  'click',
  async () => {

    await flipCamera();

  }
);


$('torchBtn').addEventListener(
  'click',
  async () => {

    await toggleTorch();

  }
);


$('photoBtn').addEventListener(
  'click',
  async () => {

    await capturePhoto();

  }
);


$('videoBtn').addEventListener(
  'click',
  () => {

    if(S.recording){

      stopRecording();

    }else{

      startRecording();

    }

  }
);


/* =========================================================
   BOTÃO CENTRAL
   TOQUE = FOTO
   SEGURAR ≈ 420 ms = VÍDEO
========================================================= */

const captureBtn =
  $('captureBtn');


let holdTimer =
  null;

let holdStarted =
  false;


captureBtn.addEventListener(
  'pointerdown',
  event => {

    event.preventDefault();


    holdStarted =
      false;


    holdTimer =
      setTimeout(
        () => {

          holdStarted =
            true;

          startRecording();

        },
        420
      );

  }
);


captureBtn.addEventListener(
  'pointerup',
  async event => {

    event.preventDefault();


    if(holdTimer){

      clearTimeout(
        holdTimer
      );

      holdTimer =
        null;

    }


    if(holdStarted){

      if(S.recording){

        stopRecording();

      }

    }else{

      await capturePhoto();

    }

  }
);


captureBtn.addEventListener(
  'pointercancel',
  () => {

    if(holdTimer){

      clearTimeout(
        holdTimer
      );

      holdTimer =
        null;

    }


    if(S.recording){

      stopRecording();

    }

  }
);


captureBtn.addEventListener(
  'contextmenu',
  event =>
    event.preventDefault()
);


/* =========================================================
   SENSORES
========================================================= */

$('audioBtn').addEventListener(
  'click',
  () => {

    if(S.audioStream){

      stopAudio();

    }else{

      startAudio();

    }

  }
);


$('lightBtn').addEventListener(
  'click',
  () => {

    if(S.lightSensor){

      try{

        S.lightSensor.stop();

      }catch(error){}


      S.lightSensor =
        null;

    }


    if(S.cameraLightTimer){

      clearInterval(
        S.cameraLightTimer
      );

      S.cameraLightTimer =
        null;

    }


    startLight();

  }
);


$('motionBtn').addEventListener(
  'click',
  () => {

    if(S.motionActive){

      stopMotion();

    }else{

      startMotion();

    }

  }
);


$('orientationBtn').addEventListener(
  'click',
  () => {

    if(S.orientationActive){

      stopOrientation();

    }else{

      startOrientation();

    }

  }
);


$('gpsBtn').addEventListener(
  'click',
  () => {

    startGPS();

  }
);


$('batteryBtn').addEventListener(
  'click',
  () => {

    readBattery();

  }
);


/* =========================================================
   NOTAS
========================================================= */

$('voiceNoteBtn').addEventListener(
  'click',
  () => {

    startVoiceNote();

  }
);


$('clearNoteBtn').addEventListener(
  'click',
  () => {

    clearNote();

  }
);


/* =========================================================
   ESTIVE AQUI
========================================================= */

$('estiveBtn').addEventListener(
  'click',
  async () => {

    await captureEstiveAqui();

  }
);


$('estiveTopBtn').addEventListener(
  'click',
  async () => {

    await captureEstiveAqui();

  }
);


/* =========================================================
   GALERIA / LAB
========================================================= */

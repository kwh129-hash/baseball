<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<title>수원신곡초 야구부 DJ 턴테이블</title>
<style>
  :root {
    --bg:        #0a0e1a;
    --surface:   #111827;
    --surface2:  #1a2235;
    --border:    #2a3550;
    --text:      #e8eaf0;
    --muted:     #7a8aaa;
    --accent:    #f5c518;   /* stadium scoreboard amber */
    --accent2:   #ff6b35;   /* home run orange */

    --col-entrance: #1e3a5f;  /* deep navy – entrance */
    --col-entrance-h: #2a5080;
    --col-entrance-active: #f5c518;
    --col-entrance-active-text: #0a0e1a;

    --col-effect:  #3d1a00;
    --col-effect-h: #5a2800;
    --col-effect-active: #ff6b35;
    --col-effect-active-text: #fff;

    --col-op:    #1a3020;
    --col-op-h:  #254530;
    --col-op-active: #34c968;
    --col-op-active-text: #fff;

    --col-cheer: #2a1a40;
    --col-cheer-h: #3d2860;
    --col-cheer-active: #a78bfa;
    --col-cheer-active-text: #fff;

    --radius: 10px;
    --btn-min-h: 64px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html, body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Segoe UI', 'Apple SD Gothic Neo', 'Noto Sans KR', sans-serif;
    min-height: 100vh;
    -webkit-tap-highlight-color: transparent;
    touch-action: manipulation;
  }

  /* ── Header ── */
  header {
    background: linear-gradient(135deg, #0d1b2e 0%, #1a2a45 100%);
    border-bottom: 2px solid var(--accent);
    padding: 12px 16px 10px;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 4px 20px rgba(0,0,0,0.6);
  }

  .header-top {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 10px;
  }

  .diamond {
    width: 38px; height: 38px;
    background: var(--accent);
    transform: rotate(45deg);
    border-radius: 4px;
    flex-shrink: 0;
    display: flex; align-items: center; justify-content: center;
  }
  .diamond span {
    transform: rotate(-45deg);
    font-size: 18px;
    line-height: 1;
  }

  h1 {
    font-size: 1.05rem;
    font-weight: 800;
    letter-spacing: -0.3px;
    line-height: 1.3;
    color: var(--text);
  }
  h1 small {
    display: block;
    font-size: 0.7rem;
    font-weight: 500;
    color: var(--accent);
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  /* ── Now Playing ── */
  .now-playing {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 8px 12px;
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 2px;
  }

  .np-dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    background: var(--muted);
    flex-shrink: 0;
    transition: background 0.3s;
  }
  .np-dot.playing {
    background: var(--accent);
    box-shadow: 0 0 8px var(--accent);
    animation: pulse 1.4s ease-in-out infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.4; }
  }

  .np-label {
    font-size: 0.68rem;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1px;
    flex-shrink: 0;
  }
  .np-title {
    font-size: 0.88rem;
    font-weight: 700;
    color: var(--text);
    flex: 1;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  /* ── Controls ── */
  .controls {
    display: flex;
    align-items: center;
    gap: 8px;
    flex-wrap: wrap;
  }

  .volume-wrap {
    display: flex;
    align-items: center;
    gap: 6px;
    flex: 1;
    min-width: 120px;
  }
  .vol-icon { font-size: 1rem; flex-shrink: 0; }

  input[type=range] {
    -webkit-appearance: none;
    appearance: none;
    flex: 1;
    height: 6px;
    border-radius: 3px;
    background: var(--border);
    outline: none;
    cursor: pointer;
  }
  input[type=range]::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 18px; height: 18px;
    border-radius: 50%;
    background: var(--accent);
    cursor: pointer;
    box-shadow: 0 0 6px rgba(245,197,24,0.5);
  }

  .ctrl-btn {
    height: 38px;
    padding: 0 14px;
    border: none;
    border-radius: 8px;
    font-size: 0.8rem;
    font-weight: 700;
    cursor: pointer;
    white-space: nowrap;
    touch-action: manipulation;
    transition: opacity 0.15s, transform 0.1s;
  }
  .ctrl-btn:active { transform: scale(0.95); opacity: 0.85; }

  .btn-stop {
    background: #7f1d1d;
    color: #fca5a5;
    border: 1px solid #991b1b;
  }
  .btn-fade {
    background: #1e1b4b;
    color: #a5b4fc;
    border: 1px solid #3730a3;
  }

  /* ── Main ── */
  main {
    padding: 14px 12px 40px;
    max-width: 680px;
    margin: 0 auto;
  }

  /* ── Section ── */
  section {
    margin-bottom: 20px;
  }

  .section-title {
    font-size: 0.7rem;
    font-weight: 800;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
    padding: 0 2px 8px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── Button Grid ── */
  .btn-grid {
    display: grid;
    gap: 8px;
    grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
  }
  .btn-grid.wide {
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  }

  .sound-btn {
    position: relative;
    min-height: var(--btn-min-h);
    border: 2px solid transparent;
    border-radius: var(--radius);
    cursor: pointer;
    padding: 10px 12px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-end;
    touch-action: manipulation;
    transition: transform 0.1s, box-shadow 0.15s, border-color 0.15s;
    text-align: left;
    overflow: hidden;
  }
  .sound-btn:active { transform: scale(0.96); }

  .btn-name {
    font-size: 0.95rem;
    font-weight: 800;
    line-height: 1.2;
    pointer-events: none;
  }
  .btn-file {
    font-size: 0.6rem;
    opacity: 0.5;
    margin-top: 3px;
    pointer-events: none;
  }

  /* entrance */
  .btn-entrance {
    background: var(--col-entrance);
    color: #a8c8f0;
    border-color: #2a4a6f;
  }
  .btn-entrance:hover { background: var(--col-entrance-h); }
  .btn-entrance.active {
    background: var(--col-entrance-active);
    color: var(--col-entrance-active-text);
    border-color: #e6b800;
    box-shadow: 0 0 16px rgba(245,197,24,0.5);
  }
  .btn-entrance.active .btn-name { color: #0a0e1a; }

  /* effect */
  .btn-effect {
    background: var(--col-effect);
    color: #fdb89a;
    border-color: #5a2800;
  }
  .btn-effect:hover { background: var(--col-effect-h); }
  .btn-effect.active {
    background: var(--col-effect-active);
    color: var(--col-effect-active-text);
    border-color: #e05a20;
    box-shadow: 0 0 16px rgba(255,107,53,0.5);
  }

  /* op */
  .btn-op {
    background: var(--col-op);
    color: #86efac;
    border-color: #254530;
  }
  .btn-op:hover { background: var(--col-op-h); }
  .btn-op.active {
    background: var(--col-op-active);
    color: var(--col-op-active-text);
    border-color: #22a855;
    box-shadow: 0 0 16px rgba(52,201,104,0.5);
  }

  /* cheer */
  .btn-cheer {
    background: var(--col-cheer);
    color: #c4b5fd;
    border-color: #3d2860;
  }
  .btn-cheer:hover { background: var(--col-cheer-h); }
  .btn-cheer.active {
    background: var(--col-cheer-active);
    color: var(--col-cheer-active-text);
    border-color: #8b5cf6;
    box-shadow: 0 0 16px rgba(167,139,250,0.5);
  }

  /* cheer resume badge */
  .resume-badge {
    position: absolute;
    top: 6px; right: 8px;
    font-size: 0.58rem;
    font-weight: 700;
    background: rgba(167,139,250,0.25);
    color: #c4b5fd;
    padding: 2px 5px;
    border-radius: 4px;
    letter-spacing: 0.5px;
  }

  /* play indicator bar */
  .sound-btn::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 3px;
    background: transparent;
    transition: background 0.2s;
  }
  .sound-btn.active::before {
    animation: playbar 2s linear infinite;
  }
  @keyframes playbar {
    0%   { background: rgba(255,255,255,0.15); }
    50%  { background: rgba(255,255,255,0.35); }
    100% { background: rgba(255,255,255,0.15); }
  }

  /* Scoreboard number badge */
  .num-badge {
    position: absolute;
    top: 8px; left: 10px;
    font-size: 0.65rem;
    font-weight: 900;
    color: rgba(255,255,255,0.2);
    font-variant-numeric: tabular-nums;
  }

  @media (max-width: 400px) {
    .btn-grid { grid-template-columns: repeat(2, 1fr); }
    .btn-grid.wide { grid-template-columns: 1fr; }
    .btn-name { font-size: 0.88rem; }
  }
</style>
</head>
<body>

<header>
  <div class="header-top">
    <div class="diamond"><span>⚾</span></div>
    <h1>수원신곡초 야구부<small>DJ Turntable</small></h1>
  </div>

  <div class="now-playing" id="nowPlaying">
    <div class="np-dot" id="npDot"></div>
    <span class="np-label">NOW</span>
    <span class="np-title" id="npTitle">대기 중</span>
  </div>

  <div class="controls">
    <div class="volume-wrap">
      <span class="vol-icon">🔊</span>
      <input type="range" id="volSlider" min="0" max="1" step="0.01" value="1">
    </div>
    <button class="ctrl-btn btn-stop" id="btnStop">⏹ 전체 정지</button>
    <button class="ctrl-btn btn-fade" id="btnFade">📉 서서히 줄이기</button>
  </div>
</header>

<main>

  <!-- 등장곡 -->
  <section>
    <div class="section-title">⚡ 등장곡</div>
    <div class="btn-grid" id="grid-entrance"></div>
  </section>

  <!-- 효과음 -->
  <section>
    <div class="section-title">💥 효과음</div>
    <div class="btn-grid" id="grid-effect"></div>
  </section>

  <!-- 운영 -->
  <section>
    <div class="section-title">🎯 운영</div>
    <div class="btn-grid" id="grid-op"></div>
  </section>

  <!-- 응원가 -->
  <section>
    <div class="section-title">🎶 응원가 <span style="font-size:0.62rem;color:var(--muted);font-weight:400;text-transform:none;letter-spacing:0;margin-left:4px;">껐다 켜도 이어서 재생</span></div>
    <div class="btn-grid wide" id="grid-cheer"></div>
  </section>

</main>

<script>
// ─── Data ───────────────────────────────────────────────────────────────────
const MUSIC_DIR = 'music/';

const ENTRANCE = [
  { name: '조은성', file: 's_26.mp3' },
  { name: '상재건', file: 's_7.mp3'  },
  { name: '이재윤', file: 's_11.mp3' },
  { name: '김태호', file: 's_1.mp3'  },
  { name: '송태헌', file: 's_18.mp3' },
  { name: '송유현', file: 's_10.mp3' },
  { name: '최수빈', file: 's_14.mp3' },
  { name: '강문범', file: 's_29.mp3' },
  { name: '김태민', file: 's_30.mp3' },
  { name: '김민균', file: 's_17.mp3' },
  { name: '김다니엘', file: 's_22.mp3' },
  { name: '이준영', file: 's_24.mp3' },
  { name: '신승윤', file: 's_21.mp3' },
  { name: '신하성', file: 's_5.mp3'  },
  { name: '최윤혁', file: 's_27.mp3' },
  { name: '김태율', file: 's_13.mp3' },
  { name: '김영헌', file: 's_23.mp3' },
  { name: '김윤호', file: 's_16.mp3' },
];

const EFFECTS = [
  { name: '홈런 🏠', file: 'homerun.mp3' },
];

const OPS = [
  { name: '⚾ 경기 시작', file: 'start.mp3' },
];

const CHEERS = [
  { name: '수원신곡초 야구부',     file: 'sg_1.mp3' },
  { name: '수원신곡초 자존심',     file: 'sg_2.mp3' },
  { name: '수원신곡초 승리행진',   file: 'sg_3.mp3' },
  { name: '우리 수원신곡 히어로1', file: 'sg_4.mp3' },
  { name: '우리 수원신곡 히어로2', file: 'sg_5.mp3' },
];

// ─── State ───────────────────────────────────────────────────────────────────
let currentAudio   = null;   // HTMLAudioElement currently playing
let currentBtn     = null;   // DOM button currently active
let currentIsCheer = false;  // whether current audio is a cheer track
let currentFile    = null;   // file name currently playing
let fadeTimer      = null;   // setInterval handle for fade-out
let globalVol      = 1;

// cheer positions saved per file key
function cheerKey(file) { return 'cheer_pos_' + file; }
function saveCheerPos(file, t) {
  try { localStorage.setItem(cheerKey(file), String(t)); } catch(e) {}
}
function loadCheerPos(file) {
  try { return parseFloat(localStorage.getItem(cheerKey(file))) || 0; } catch(e) { return 0; }
}

// ─── Audio helpers ────────────────────────────────────────────────────────────
function stopAll(savePos) {
  if (fadeTimer) { clearInterval(fadeTimer); fadeTimer = null; }
  if (currentAudio) {
    if (savePos && currentIsCheer && currentFile) {
      saveCheerPos(currentFile, currentAudio.currentTime);
    }
    currentAudio.pause();
    currentAudio = null;
  }
  if (currentBtn) {
    currentBtn.classList.remove('active');
    currentBtn = null;
  }
  currentFile    = null;
  currentIsCheer = false;
  setNowPlaying(null);
}

function fadeOut() {
  if (!currentAudio) return;
  if (fadeTimer) clearInterval(fadeTimer);
  const audio = currentAudio;
  const isCheer = currentIsCheer;
  const file = currentFile;
  const btn = currentBtn;

  // snapshot state so stop doesn't conflict
  currentAudio = null; currentBtn = null; currentIsCheer = false; currentFile = null;
  if (btn) btn.classList.remove('active');
  setNowPlaying(null);

  fadeTimer = setInterval(() => {
    if (audio.volume > 0.03) {
      audio.volume = Math.max(0, audio.volume - 0.03);
    } else {
      audio.pause();
      if (isCheer && file) saveCheerPos(file, audio.currentTime);
      clearInterval(fadeTimer);
      fadeTimer = null;
    }
  }, 80);
}

function playSound(file, name, isCheer, btn) {
  const alreadyPlaying = (currentFile === file);

  // save cheer position before switching
  if (currentIsCheer && currentFile && currentAudio) {
    saveCheerPos(currentFile, currentAudio.currentTime);
  }

  stopAll(false); // positions already saved above

  if (alreadyPlaying && !isCheer) {
    // non-cheer: toggle off
    return;
  }

  const audio = new Audio(MUSIC_DIR + file);
  audio.volume = globalVol;

  if (isCheer) {
    const pos = loadCheerPos(file);
    if (pos > 0) { audio.currentTime = pos; }
  }

  audio.play().catch(() => {});
  currentAudio   = audio;
  currentBtn     = btn;
  currentIsCheer = isCheer;
  currentFile    = file;

  btn.classList.add('active');
  setNowPlaying(name);

  audio.addEventListener('ended', () => {
    if (currentAudio === audio) {
      if (isCheer) saveCheerPos(file, 0); // reset position on natural end
      stopAll(false);
    }
  });

  // periodically save cheer position
  if (isCheer) {
    audio._saveInterval = setInterval(() => {
      if (currentAudio === audio && !audio.paused) {
        saveCheerPos(file, audio.currentTime);
      } else {
        clearInterval(audio._saveInterval);
      }
    }, 2000);
  }
}

// ─── UI helpers ───────────────────────────────────────────────────────────────
function setNowPlaying(name) {
  const dot   = document.getElementById('npDot');
  const title = document.getElementById('npTitle');
  if (name) {
    dot.classList.add('playing');
    title.textContent = name;
  } else {
    dot.classList.remove('playing');
    title.textContent = '대기 중';
  }
}

function makeBtn(item, cssClass, isCheer, grid, index) {
  const btn = document.createElement('button');
  btn.className = 'sound-btn ' + cssClass;

  const numBadge = document.createElement('span');
  numBadge.className = 'num-badge';
  numBadge.textContent = String(index + 1).padStart(2, '0');

  const nameEl = document.createElement('span');
  nameEl.className = 'btn-name';
  nameEl.textContent = item.name;

  const fileEl = document.createElement('span');
  fileEl.className = 'btn-file';
  fileEl.textContent = item.file;

  btn.appendChild(numBadge);

  if (isCheer) {
    const badge = document.createElement('span');
    badge.className = 'resume-badge';
    badge.textContent = '▶ 이어듣기';
    btn.appendChild(badge);
  }

  btn.appendChild(nameEl);
  btn.appendChild(fileEl);

  btn.addEventListener('click', () => {
    playSound(item.file, item.name, isCheer, btn);
  });

  grid.appendChild(btn);
}

// ─── Build UI ────────────────────────────────────────────────────────────────
function buildGrid(items, gridId, cssClass, isCheer) {
  const grid = document.getElementById(gridId);
  items.forEach((item, i) => makeBtn(item, cssClass, isCheer, grid, i));
}

buildGrid(ENTRANCE, 'grid-entrance', 'btn-entrance', false);
buildGrid(EFFECTS,  'grid-effect',   'btn-effect',   false);
buildGrid(OPS,      'grid-op',       'btn-op',        false);
buildGrid(CHEERS,   'grid-cheer',    'btn-cheer',     true);

// ─── Control buttons ──────────────────────────────────────────────────────────
document.getElementById('btnStop').addEventListener('click', () => stopAll(true));
document.getElementById('btnFade').addEventListener('click', fadeOut);

document.getElementById('volSlider').addEventListener('input', function() {
  globalVol = parseFloat(this.value);
  if (currentAudio) currentAudio.volume = globalVol;
});
</script>
</body>
</html>

<!doctype html>
<html lang="id">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
<title>Runner Rush — HTML5 Prototype</title>
<style>
  :root{
    --bg1:#071025; --bg2:#05223a; --accent:#19e6d8; --danger:#ff6b6b;
    --panel: rgba(255,255,255,0.04);
  }
  html,body{height:100%;margin:0;font-family:Inter,ui-sans-serif,system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial;background:linear-gradient(180deg,var(--bg1),var(--bg2));color:#e6f7f7}
  #app{display:flex;align-items:center;justify-content:center;height:100vh;padding:16px;box-sizing:border-box}
  .card{width:min(980px,100%);max-width:1100px;background:linear-gradient(180deg,rgba(255,255,255,0.02),rgba(255,255,255,0.01));border-radius:14px;box-shadow:0 10px 30px rgba(0,0,0,0.6);overflow:hidden;display:grid;grid-template-columns:1fr 320px;gap:16px;padding:16px}
  @media (max-width:920px){ .card{grid-template-columns:1fr; padding:12px} }

  /* Canvas area */
  #gameWrap{background:linear-gradient(180deg,#021223 0%, #041630 100%);border-radius:10px;padding:8px;display:flex;flex-direction:column;align-items:center;justify-content:center}
  canvas{width:100%;height:560px;border-radius:8px;display:block;background:transparent;touch-action:none}

  /* Sidebar */
  .side{padding:6px 8px}
  h1{margin:6px 0 4px 0;font-size:20px}
  .score{font-size:20px;font-weight:700;color:var(--accent)}
  .meta{color:rgba(255,255,255,0.6);font-size:13px;margin-top:6px}
  .btn{display:inline-block;padding:10px 14px;border-radius:10px;background:var(--panel);cursor:pointer;margin-top:10px;border:1px solid rgba(255,255,255,0.02)}
  .btn.primary{background:linear-gradient(90deg,var(--accent),#4de1c6);color:#001820;font-weight:700;box-shadow:0 8px 20px rgba(25,230,216,0.08)}
  .small{font-size:13px;color:rgba(255,255,255,0.7);margin-top:8px}
  .controls{margin-top:10px}

  /* Start screen overlay */
  #startScreen{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;flex-direction:column;z-index:50;backdrop-filter: blur(2px)}
  .title{font-size:42px;font-weight:800;color:var(--accent);text-shadow:0 6px 30px rgba(25,230,216,0.06)}
  .subtitle{color:rgba(255,255,255,0.8);margin-top:8px}
  .startGlow{animation:glow 1.8s ease-in-out infinite}
  @keyframes glow{0%{filter:drop-shadow(0 0 6px rgba(25,230,216,0.12))}50%{filter:drop-shadow(0 0 18px rgba(25,230,216,0.22))}100%{filter:drop-shadow(0 0 6px rgba(25,230,216,0.12))}}

  /* Level tag */
  #levelTag{position:absolute;left:18px;top:18px;padding:8px 12px;background:rgba(0,0,0,0.35);border-radius:10px;color:var(--accent);font-weight:700;z-index:40}

  /* HUD bottom */
  .hud{display:flex;gap:8px;align-items:center;flex-wrap:wrap;margin-top:10px}
  .chip{background:var(--panel);padding:8px 10px;border-radius:10px;font-weight:600;color:#fff}

  /* small hint */
  .hint{font-size:13px;color:rgba(255,255,255,0.6);margin-top:10px}

  /* mobile virtual buttons */
  .touchControls{position:absolute;bottom:22px;left:50%;transform:translateX(-50%);display:flex;gap:12px;z-index:60}
  .touchBtn{width:64px;height:64px;border-radius:20px;background:rgba(255,255,255,0.03);display:flex;align-items:center;justify-content:center;backdrop-filter: blur(4px);font-weight:700;color:#fff}

  footer{grid-column:1 / -1;text-align:center;color:rgba(255,255,255,0.45);font-size:12px;margin-top:8px}
</style>
</head>
<body>
<div id="app">
  <div class="card" role="application" aria-label="Runner Rush game">
    <div id="gameWrap">
      <div id="levelTag">Level 1</div>
      <div id="startScreen">
        <div class="title startGlow">RUNNER RUSH</div>
        <div class="subtitle">Swipe kiri/kanan = pindah • Swipe atas = lompat • Swipe bawah = slide</div>
        <button id="btnStart" class="btn primary" style="margin-top:18px;font-size:18px;padding:12px 22px">MULAI</button>
        <div class="hint" style="margin-top:12px">HTML5 prototype — simpan skor terbaik di perangkat ini</div>
      </div>
      <canvas id="game"></canvas>
      <div class="touchControls" id="touchControls" style="display:none">
        <div class="touchBtn" id="btnLeft">◀</div>
        <div class="touchBtn" id="btnUp">▲</div>
        <div class="touchBtn" id="btnRight">▶</div>
      </div>
    </div>

    <div class="side" aria-hidden="false">
      <h1>Runner Rush</h1>
      <div>Score: <span id="score" class="score">0</span></div>
      <div class="meta">Coins: <span id="coins">0</span> • Best: <span id="best">0</span></div>

      <div class="hud">
        <div class="chip" id="stateChip">State: Ready</div>
        <div class="chip" id="powerChip">Power: —</div>
      </div>

      <div class="controls">
        <button id="btnPause" class="btn">Pause</button>
        <button id="btnReset" class="btn">Reset Best</button>
      </div>

      <div class="small">Tip pemasaran: Packaging kecil & nama aroma/warna buat merchandise.</div>
      <div class="hint">Ingin ditambah? mis. skins, shop, sound pack — bilang saja.</div>
    </div>

    <footer>Save as <code>game.html</code> & open in browser • Prototype by you</footer>
  </div>
</div>

<script>
/* -------------------------
   Runner Rush — HTML5 Prototype
   - 3 lanes, swipe controls
   - coins, magnet & hoverboard powerups
   - obstacle types (box, train)
   - level & difficulty progression
------------------------- */

/* Canvas setup */
const canvas = document.getElementById('game');
const ctx = canvas.getContext('2d', { alpha: true });
let DPR = window.devicePixelRatio || 1;
function fitCanvas(){
  const rect = canvas.getBoundingClientRect();
  canvas.width = Math.max(600, Math.floor(rect.width * DPR));
  canvas.height = Math.floor(rect.height * DPR);
  ctx.setTransform(DPR,0,0,DPR,0,0);
}
function layoutCanvas(){
  // set CSS size based on container
  const wrap = document.getElementById('gameWrap');
  const w = wrap.clientWidth - 16;
  // maintain aspect ratio: we'll set CSS height
  canvas.style.width = '100%';
  canvas.style.height = (window.innerWidth < 920 ? '420px' : '560px');
  fitCanvas();
}
window.addEventListener('resize', ()=>{ layoutCanvas(); fitCanvas(); });
layoutCanvas();

/* Game constants */
const lanes = [0.22, 0.5, 0.78]; // relative x positions (as fraction of width)
let laneX = i => canvas.clientWidth * lanes[i];

const stateElems = {
  score: document.getElementById('score'),
  coins: document.getElementById('coins'),
  best: document.getElementById('best'),
  stateChip: document.getElementById('stateChip'),
  powerChip: document.getElementById('powerChip'),
  levelTag: document.getElementById('levelTag')
};

/* Game state */
let gameStarted = false;
let running = true;
let score = 0;
let coins = 0;
let best = parseInt(localStorage.getItem('rr_best')||'0',10);
stateElems.best.textContent = best;
let level = 1;
let nextLevelScore = 300;

let player = {
  lane: 1,
  x: 0,
  y: 0,
  w: 56, h: 80,
  vy: 0, gravity: 1400,
  jumpPow: -520,
  onGround: true,
  sliding: false,
  slideTimer: 0
};

let groundY = 0;
let obstacles = [];
let coinsPool = [];
let powerups = [];
let particles = [];

let baseSpeed = 420; // px/sec
let speed = baseSpeed;
let spawnTimer = 0;
let spawnInterval = 1.2; // seconds

let magnetActive = false;
let magnetTimer = 0;
let hoverActive = false;
let hoverTimer = 0;

/* Audio (simple) */
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
function beep(freq=440, time=0.06, type='sine'){
  try{
    const o = audioCtx.createOscillator();
    const g = audioCtx.createGain();
    o.type = type;
    o.frequency.value = freq;
    o.connect(g); g.connect(audioCtx.destination);
    g.gain.value = 0.0001;
    g.gain.exponentialRampToValueAtTime(0.12, audioCtx.currentTime + 0.01);
    o.start();
    g.gain.exponentialRampToValueAtTime(0.0001, audioCtx.currentTime + time);
    o.stop(audioCtx.currentTime + time + 0.02);
  }catch(e){}
}

/* Utility */
function rand(min,max){ return Math.random()*(max-min)+min; }
function now(){ return performance.now()/1000; }

/* Input: swipe detection */
let swStart = null;
const SWIPE_MIN = 30; // px
canvas.addEventListener('touchstart', e => {
  const t = e.touches[0];
  swStart = {x:t.clientX, y:t.clientY, t: now()};
}, {passive:true});
canvas.addEventListener('touchend', e => {
  if(!swStart) return;
  const t = e.changedTouches[0];
  const dx = t.clientX - swStart.x;
  const dy = t.clientY - swStart.y;
  if(Math.abs(dx) > Math.abs(dy) && Math.abs(dx) > SWIPE_MIN){
    if(dx > 0) moveRight(); else moveLeft();
  } else if(Math.abs(dy) > SWIPE_MIN){
    if(dy < 0) jump(); else slide();
  } else {
    // tap = jump
    jump();
  }
  swStart = null;
}, {passive:true});

/* desktop keys */
window.addEventListener('keydown', e => {
  if(!gameStarted) return;
  if(e.code === 'ArrowLeft') moveLeft();
  if(e.code === 'ArrowRight') moveRight();
  if(e.code === 'ArrowUp' || e.code === 'Space') jump();
  if(e.code === 'ArrowDown') slide();
});

/* virtual buttons */
document.getElementById('btnLeft').addEventListener('touchstart', e => { e.preventDefault(); moveLeft(); }, {passive:false});
document.getElementById('btnRight').addEventListener('touchstart', e => { e.preventDefault(); moveRight(); }, {passive:false});
document.getElementById('btnUp').addEventListener('touchstart', e => { e.preventDefault(); jump(); }, {passive:false});

/* movement */
function moveLeft(){ if(player.lane>0){ player.lane--; beep(520,0.06); } }
function moveRight(){ if(player.lane<2){ player.lane++; beep(620,0.06); } }
function jump(){
  if(player.onGround && !player.sliding){
    player.vy = player.jumpPow;
    player.onGround = false;
    beep(920,0.08,'square');
  }
}
function slide(){
  if(player.onGround && !player.sliding){
    player.sliding = true;
    player.slideTimer = 0.5; // seconds
    player.h = 48; // lower hitbox
    beep(320,0.06);
  }
}

/* Start / UI */
const startScreen = document.getElementById('startScreen');
const btnStart = document.getElementById('btnStart');
btnStart.addEventListener('click', ()=> startGame());

document.getElementById('btnPause').addEventListener('click', ()=>{
  running = !running;
  stateElems.stateChip.textContent = running ? 'Running' : 'Paused';
  if(running) lastT = performance.now(), loop();
});
document.getElementById('btnReset').addEventListener('click', ()=>{
  localStorage.removeItem('rr_best'); best = 0; stateElems.best.textContent = 0;
});

/* Game start */
function startGame(){
  // show touch controls on small screens
  if(window.innerWidth < 720) document.getElementById('touchControls').style.display = 'flex';
  startScreen.style.display = 'none';
  gameStarted = true;
  running = true;
  resetGame();
  // resume audio context on user gesture
  if(audioCtx.state === 'suspended') audioCtx.resume().catch(()=>{});
}

/* Reset */
function resetGame(){
  score = 0; coins = 0; level = 1; nextLevelScore = 300;
  speed = baseSpeed;
  spawnTimer = 0; spawnInterval = 1.2;
  obstacles = []; coinsPool = []; powerups = []; particles = [];
  player.lane = 1; player.onGround = true; player.y = 0; player.vy = 0; player.h = 80;
  magnetActive = false; magnetTimer = 0; hoverActive = false; hoverTimer = 0;
  stateElems.score.textContent = 0; stateElems.coins.textContent = 0;
  stateElems.powerChip.textContent = '—'; stateElems.levelTag.textContent = 'Level 1';
  lastT = performance.now();
}

/* Spawning */
function spawn(){
  // choose spawn: obstacle, coin, powerup
  const r = Math.random();
  if(r < 0.55){
    // obstacle: box or train (train larger)
    const isTrain = Math.random() < 0.18;
    if(isTrain){
      obstacles.push({
        type:'train',
        x: canvas.clientWidth + 120,
        lane: Math.random() < 0.6 ? 1 : (Math.random()<0.5?0:2),
        w: 260, h: 120
      });
    } else {
      obstacles.push({
        type:'box', x: canvas.clientWidth + 80,
        lane: Math.floor(Math.random()*3), w: 56, h: 56
      });
    }
  } else if(r < 0.9){
    // coin cluster
    const lane = Math.floor(Math.random()*3);
    const amount = 3 + Math.floor(Math.random()*4);
    for(let i=0;i<amount;i++){
      coinsPool.push({
        x: canvas.clientWidth + 60 + i*42,
        lane: lane,
        r: 10,
        collected:false
      });
    }
  } else {
    // powerup
    const type = Math.random() < 0.6 ? 'magnet' : 'hover';
    powerups.push({
      x: canvas.clientWidth + 80,
      lane: Math.floor(Math.random()*3),
      type: type
    });
  }
}

/* Level up */
function checkLevel(){
  if(score >= nextLevelScore){
    level++;
    nextLevelScore += 300 + level*50;
    speed += 60;
    spawnInterval = Math.max(0.5, spawnInterval - 0.08);
    stateElems.levelTag.textContent = 'Level ' + level;
    // level popup visual
    showLevelUp(level);
    beep(1200,0.12,'sine');
  }
}
function showLevelUp(lvl){
  const popup = document.createElement('div');
  popup.textContent = 'LEVEL ' + lvl;
  Object.assign(popup.style,{
    position:'absolute',left:'50%',top:'28%',transform:'translateX(-50%)',
    color:'#fff',fontSize:'44px',fontWeight:800,textShadow:'0 8px 30px rgba(255,255,255,0.06)'
  });
  document.body.appendChild(popup);
  setTimeout(()=>{ popup.style.transition = 'all 0.8s ease'; popup.style.opacity=0; popup.style.transform='translateX(-50%) translateY(-60px) scale(0.9)'; },800);
  setTimeout(()=>document.body.removeChild(popup),1500);
}

/* Collision helpers */
function rectOverlap(ax,ay,aw,ah,bx,by,bw,bh){
  return ax < bx + bw && ax + aw > bx && ay < by + bh && ay + ah > by;
}

/* Main loop */
let lastT = performance.now();
let accSpawn = 0;
function loop(ts){
  if(!running) return;
  const t = performance.now();
  let dt = Math.min(0.05, (t - lastT)/1000);
  lastT = t;

  // update sizes
  const W = canvas.clientWidth;
  const H = canvas.clientHeight;
  groundY = H - 120;

  // physics: player
  player.x = laneX(player.lane) - player.w/2;
  player.vy += player.gravity * dt;
  player.y += player.vy * dt;

  if(player.y + player.h >= groundY){
    player.y = groundY - player.h;
    player.vy = 0;
    player.onGround = true;
  } else player.onGround = false;

  if(player.sliding){
    player.slideTimer -= dt;
    if(player.slideTimer <= 0){
      player.sliding = false; player.h = 80;
    }
  }

  // spawn logic
  accSpawn += dt;
  if(accSpawn > spawnInterval){
    spawn();
    accSpawn = 0;
  }

  // move obstacles/powerups/coins
  for(let i=obstacles.length-1;i>=0;i--){
    const o = obstacles[i];
    o.x -= speed * dt;
    if(o.x + (o.w||80) < -200) obstacles.splice(i,1);
  }
  for(let i=coinsPool.length-1;i>=0;i--){
    const c = coinsPool[i];
    // magnet attraction
    if(magnetActive){
      // target x of player center
      const px = player.x + player.w/2;
      const py = player.y + player.h/2;
      // move coin toward player
      const tx = px - laneX(c.lane) + laneX(c.lane);
      const dir = (px - c.x) * 3;
      c.x += dir * dt;
    } else {
      c.x -= speed * dt;
    }
    if(c.x < -50) coinsPool.splice(i,1);
  }
  for(let i=powerups.length-1;i>=0;i--){
    const p = powerups[i];
    p.x -= speed * dt;
    if(p.x < -80) powerups.splice(i,1);
  }

  // check collisions: player vs obstacles
  const pBox = {x:player.x, y:player.y, w:player.w, h:player.h};
  for(const ob of obstacles){
    const obX = ob.x;
    const obY = groundY - (ob.h||56);
    const obW = ob.w; const obH = ob.h;
    // obstacle lane x center
    const obCenterX = laneX(ob.lane) - obW/2;
    if(rectOverlap(pBox.x,pBox.y,pBox.w,pBox.h, obCenterX, obY, obW, obH)){
      if(hoverActive){
        // destroy obstacle and emit particle
        obstacles = obstacles.filter(o=>o!==ob);
        spawnParticles(obCenterX+obW/2, obY+obH/2, 18);
        beep(220,0.04,'sine');
        break;
      } else {
        // Game over — show overlay and reset after short delay
        running = false;
        stateElems.stateChip.textContent = 'Game Over';
        beep(80,0.5,'sawtooth');
        setTimeout(()=>{ endGame(); }, 700);
        break;
      }
    }
  }

  // coins collision
  for(let i=coinsPool.length-1;i>=0;i--){
    const c = coinsPool[i];
    const cx = c.x;
    const cy = groundY - 28; // coin vertical pos (approx)
    const coinX = cx;
    const coinY = cy;
    if(rectOverlap(player.x,player.y,player.w,player.h, coinX-10, coinY-10, 20,20)){
      // collect
      coins++;
      score += 35;
      stateElems.coins.textContent = coins;
      stateElems.score.textContent = Math.floor(score);
      beep(1200,0.06,'triangle');
      spawnParticles(coinX, coinY, 8, '#ffd166');
      coinsPool.splice(i,1);
    }
  }

  // powerup collision
  for(let i=powerups.length-1;i>=0;i--){
    const p = powerups[i];
    const px = p.x;
    const py = groundY - 40;
    if(rectOverlap(player.x,player.y,player.w,player.h, px-20,py-20,40,40)){
      if(p.type === 'magnet'){
        magnetActive = true;
        magnetTimer = 6.0;
        stateElems.powerChip.textContent = 'Magnet';
        beep(1600,0.08,'sine');
      } else if(p.type === 'hover'){
        hoverActive = true;
        hoverTimer = 5.5;
        stateElems.powerChip.textContent = 'Hover';
        beep(1000,0.08,'square');
      }
      spawnParticles(px, py, 10, '#9be7ff');
      powerups.splice(i,1);
    }
  }

  // timers
  if(magnetActive){ magnetTimer -= dt; if(magnetTimer <= 0){ magnetActive = false; stateElems.powerChip.textContent = '—'; } }
  if(hoverActive){ hoverTimer -= dt; if(hoverTimer <= 0){ hoverActive = false; stateElems.powerChip.textContent = '—'; } }

  // update score over time
  score += dt * 10;
  stateElems.score.textContent = Math.floor(score);

  // difficulty check
  checkLevel();

  // particles update
  for(let i=particles.length-1;i>=0;i--){
    const pr = particles[i];
    pr.x += pr.vx * dt; pr.y += pr.vy * dt; pr.life -= dt;
    pr.vy += 900 * dt;
    if(pr.life <= 0) particles.splice(i,1);
  }

  // render
  drawAll();

  if(running) requestAnimationFrame(loop);
}

/* end game */
function endGame(){
  // update best
  if(score > best){ best = Math.floor(score); localStorage.setItem('rr_best', best); stateElems.best.textContent = best; }
  // show simple overlay restart
  const overlay = document.createElement('div');
  overlay.style.position='absolute'; overlay.style.inset='0'; overlay.style.display='flex'; overlay.style.alignItems='center';
  overlay.style.justifyContent='center'; overlay.style.zIndex=200; overlay.style.background='linear-gradient(180deg, rgba(0,0,0,0.2), rgba(0,0,0,0.6))';
  const card = document.createElement('div'); card.style.padding='20px'; card.style.background='rgba(255,255,255,0.04)'; card.style.borderRadius='12px'; card.style.textAlign='center';
  card.innerHTML = `<div style="font-size:22px;font-weight:800;color:#fff;margin-bottom:8px">Game Over</div>
  <div style="color:#cde;font-size:16px;margin-bottom:10px">Score: ${Math.floor(score)} &nbsp; • &nbsp; Coins: ${coins}</div>
  <button id='restartBtn' style="padding:10px 14px;border-radius:10px;background:linear-gradient(90deg,var(--accent),#4de1c6);border:none;font-weight:700;cursor:pointer">Main Lagi</button>`;
  overlay.appendChild(card); document.body.appendChild(overlay);
  document.getElementById('restartBtn').addEventListener('click', ()=>{
    document.body.removeChild(overlay);
    startScreen.style.display = 'none';
    resetGame();
    running = true;
    lastT = performance.now();
    loop();
  });
}

/* Particles */
function spawnParticles(x,y,count,color='#fff'){
  for(let i=0;i<count;i++){
    particles.push({
      x:x + rand(-8,8), y:y + rand(-6,6),
      vx: rand(-140,140), vy: rand(-320,-80), life: 0.6 + Math.random()*0.6, color: color
    });
  }
}

/* Draw function */
function drawAll(){
  const W = canvas.clientWidth;
  const H = canvas.clientHeight;
  ctx.clearRect(0,0,W,H);

  // dynamic background: parallax rectangles + gradient
  const g = ctx.createLinearGradient(0,0,0,H);
  g.addColorStop(0,'rgba(0,16,26,0.95)');
  g.addColorStop(1,'rgba(2,30,48,0.95)');
  ctx.fillStyle = g; ctx.fillRect(0,0,W,H);

  // moving faint bars
  for(let i=0;i<8;i++){
    const x = ( (performance.now()/60) * (i%2?0.08: -0.06) + i*120 ) % (W+240) - 120;
    ctx.fillStyle = 'rgba(255,255,255,0.02)';
    ctx.fillRect(x, H*0.08 + i*22, 160, 6);
  }

  // road
  const roadY = groundY;
  ctx.fillStyle = '#041a26';
  ctx.fillRect(0, roadY, W, H-roadY);

  // lane markers
  for(let i=0;i<3;i++){
    const lx = laneX(i);
    ctx.fillStyle = 'rgba(255,255,255,0.03)';
    ctx.fillRect(lx - 2, roadY - 6, 4, 6);
  }

  // draw coins
  for(const c of coinsPool){
    const cx = c.x;
    const cy = groundY - 28;
    ctx.beginPath();
    ctx.fillStyle = '#ffd166';
    ctx.ellipse(cx, cy, 10, 12, 0, 0, Math.PI*2);
    ctx.fill();
    ctx.closePath();
    // shine
    ctx.beginPath();
    ctx.fillStyle = 'rgba(255,255,255,0.3)';
    ctx.fillRect(cx-4, cy-6, 3, 6);
    ctx.closePath();
  }

  // draw powerups
  for(const p of powerups){
    const px = p.x;
    const py = groundY - 40;
    ctx.beginPath();
    if(p.type === 'magnet'){
      ctx.fillStyle = '#9be7ff';
      ctx.arc(px,py,14,0,Math.PI*2);
      ctx.fill();
      ctx.fillStyle='rgba(0,0,0,0.1)'; ctx.fillRect(px-6,py-6,12,12);
    } else {
      ctx.fillStyle = '#ffd1f1';
      ctx.fillRect(px-12,py-12,24,24,6);
      ctx.fillStyle='rgba(0,0,0,0.08)'; ctx.fillRect(px-6,py-6,12,12);
    }
  }

  // draw obstacles (converted to lane positions)
  for(const o of obstacles){
    const ox = o.x;
    const lx = laneX(o.lane) - (o.w||56)/2;
    const oy = groundY - (o.h||56);
    ctx.fillStyle = (o.type==='train')? '#ff6b6b' : '#d6d6d6';
    // draw shadow
    ctx.fillStyle = 'rgba(0,0,0,0.4)';
    ctx.fillRect(lx, oy + (o.h||56), o.w || 56, 8);
    // main
    ctx.fillStyle = (o.type==='train')? '#ff6b6b' : '#cbd5e1';
    roundRect(ctx, lx, oy, o.w || 56, o.h || 56, 6);
    ctx.fill();
    // windows for train
    if(o.type==='train'){
      ctx.fillStyle = 'rgba(255,255,255,0.08)';
      for(let i=0;i<4;i++){
        ctx.fillRect(lx + 24 + i*40, oy + 20, 26, 18);
      }
    }
  }

  // draw player
  const px = player.x;
  const py = player.y;
  ctx.save();
  // glow if hover
  if(hoverActive){
    ctx.shadowColor = 'rgba(255,255,255,0.12)';
    ctx.shadowBlur = 18;
  } else ctx.shadowBlur = 0;
  ctx.fillStyle = '#19e6d8';
  roundRect(ctx, px, py, player.w, player.h, 10); ctx.fill();
  ctx.restore();

  // player eyes detail
  ctx.fillStyle = '#06323a'; ctx.fillRect(px + player.w - 18, py + 16, 8, 8);

  // particles
  for(const pr of particles){
    ctx.fillStyle = pr.color || '#fff';
    ctx.fillRect(pr.x, pr.y, 3, 3);
  }

  // HUD overlays: magnet indicator
  if(magnetActive){
    ctx.fillStyle = 'rgba(155,231,255,0.08)';
    ctx.beginPath(); ctx.arc(px+player.w/2, py+player.h/2, 80, 0, Math.PI*2); ctx.fill();
  }

  // bottom info
  ctx.fillStyle = 'rgba(255,255,255,0.06)';
  ctx.fillRect(12,12,220,46);
  ctx.fillStyle = '#cde';
  ctx.font = '14px system-ui, Arial';
  ctx.fillText('Speed: ' + Math.round(speed), 22, 34);
}

/* helper roundRect */
function roundRect(ctx,x,y,w,h,r){
  ctx.beginPath();
  ctx.moveTo(x+r,y);
  ctx.arcTo(x+w,y,x+w,y+h,r);
  ctx.arcTo(x+w,y+h,x,y+h,r);
  ctx.arcTo(x,y+h,x,y,r);
  ctx.arcTo(x,y,x+w,y,r);
  ctx.closePath();
}

/* game loop runner */
function startLoop(){
  lastT = performance.now();
  running = true;
  loop();
}

/* initial placement */
function initPlacement(){
  // set player on ground
  player.y = groundY - player.h;
  player.x = laneX(player.lane) - player.w/2;
}
window.addEventListener('load', ()=> {
  layoutCanvas(); fitCanvas();
  groundY = canvas.clientHeight - 120;
  initPlacement();
});

/* control start via button */
document.getElementById('btnStart').addEventListener('click', ()=>{
  if(!gameStarted) startGame();
});

/* ensure startScreen is clickable also via keyboard */
document.addEventListener('keydown', e => {
  if(!gameStarted && (e.code==='Space' || e.code==='Enter')) startGame();
});

/* start animation frame when game starts */
function gameStartBootstrap(){
  // animate background on startScreen slightly
  setInterval(()=>{ if(!gameStarted){ document.getElementById('startScreen').style.filter = `hue-rotate(${(performance.now()/60)%360}deg)`; } }, 120);
}
gameStartBootstrap();

/* Ensure game area focuses for keyboard */
canvas.tabIndex = 1000;

/* expose for debugging if needed */
window.rr = { restart: resetGame };

/* Start loop when startGame called */
</script>
</body>
</html>

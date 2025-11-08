<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Spend Elon Musk's Money — Simulator (Fake)</title>
<link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text x=%2250%25%22 y=%2255%25%22 font-size=%2290%22 text-anchor=%22middle%22>💸</text></svg>">
<style>
  :root{
    --bg:#0b0b10;
    --card:#111217;
    --accent:#ff4d4d;
    --muted:#9aa3a8;
    --glow: rgba(255,77,77,0.12);
    --success:#69d18b;
    --glass: rgba(255,255,255,0.03);
  }
  *{box-sizing:border-box}
  html,body{height:100%;margin:0;font-family:Inter,ui-sans-serif,system-ui,"Segoe UI",Roboto,"Helvetica Neue",Arial,"Noto Sans",sans-serif;background:linear-gradient(180deg,#070709,#0e0e12);color:#e9eef2}
  .app{max-width:1200px;margin:24px auto;padding:18px;position:relative}
  header{display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:18px}
  .brand{display:flex;gap:12px;align-items:center}
  .logo{width:58px;height:58px;border-radius:10px;background:linear-gradient(135deg,#2a0000,#5f0000);display:flex;align-items:center;justify-content:center;font-size:26px;box-shadow:0 8px 30px rgba(0,0,0,0.6)}
  h1{font-size:20px;margin:0}
  .subtitle{color:var(--muted);font-size:13px;margin-top:3px}

  /* balance card */
  .balanceCard{display:flex;align-items:center;gap:18px;padding:18px;border-radius:12px;background:linear-gradient(180deg,rgba(255,0,0,0.03),rgba(255,0,0,0.01));border:1px solid rgba(255,77,77,0.06);box-shadow:0 12px 40px rgba(0,0,0,0.7)}
  .balanceAmt{font-weight:800;font-size:22px;color:var(--accent)}
  .progressWrap{flex:1}
  .progressBar{height:14px;background:var(--glass);border-radius:999px;overflow:hidden;border:1px solid rgba(255,255,255,0.03)}
  .progressFill{height:100%;background:linear-gradient(90deg,var(--accent),#ff9b9b);width:100%;transition:width .8s cubic-bezier(.2,.9,.3,1)}
  .controlsSmall{display:flex;gap:8px;align-items:center}

  /* grid */
  .grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(230px,1fr));gap:14px;margin-top:18px}
  .card{background:linear-gradient(180deg,rgba(255,255,255,0.02),rgba(255,255,255,0.01));padding:14px;border-radius:10px;border:1px solid rgba(255,255,255,0.03);box-shadow:0 8px 24px rgba(0,0,0,0.6);display:flex;flex-direction:column;gap:8px;position:relative;overflow:hidden}
  .card:hover{transform:translateY(-6px);transition:transform .18s ease}
  .itemTop{display:flex;align-items:center;gap:10px}
  .icon{width:54px;height:54px;border-radius:8px;background:linear-gradient(135deg,rgba(255,255,255,0.02),rgba(0,0,0,0.06));display:flex;align-items:center;justify-content:center;font-size:26px}
  .name{font-weight:700;font-size:15px}
  .price{color:var(--muted);font-size:13px}
  .desc{font-size:12px;color:var(--muted);margin-top:6px;min-height:34px}

  .buyRow{margin-top:auto;display:flex;gap:8px;align-items:center}
  input[type="number"]{width:86px;padding:8px;border-radius:8px;background:transparent;border:1px solid rgba(255,255,255,0.04);color:#fff}
  button.buy{background:linear-gradient(180deg,var(--accent),#ff7b7b);border:none;padding:8px 10px;border-radius:8px;color:#fff;font-weight:700;cursor:pointer;box-shadow:0 8px 20px rgba(255,77,77,0.08)}
  button.ghost{background:transparent;border:1px solid rgba(255,255,255,0.04);padding:8px 10px;border-radius:8px;color:var(--muted);cursor:pointer}
  .small{font-size:12px;padding:6px 10px;border-radius:7px}

  /* top-right utilities */
  .utils{display:flex;gap:8px;align-items:center}
  .toggle{display:flex;gap:8px;align-items:center;background:var(--card);padding:8px;border-radius:8px;border:1px solid rgba(255,255,255,0.02)}
  .muted{color:var(--muted);font-size:13px}

  /* floating money animation */
  .float-emoji{position:fixed;z-index:9999;pointer-events:none;font-size:22px;transform:translateY(0);opacity:0;transition:transform 1s ease-out,opacity .8s linear}

  /* footer controls */
  .footer{display:flex;gap:12px;align-items:center;margin-top:18px;justify-content:space-between}
  .bigActions{display:flex;gap:10px;align-items:center}
  .autoBtn{background:linear-gradient(180deg,#3b82f6,#2563eb);border:none;padding:10px 14px;border-radius:10px;color:#fff;font-weight:700;cursor:pointer}
  .resetBtn{background:transparent;border:1px solid rgba(255,255,255,0.04);padding:10px 12px;border-radius:10px;color:var(--muted)}
  .status{font-size:13px;color:var(--muted)}

  /* disclaimer */
  .disclaimer{margin-top:16px;background:linear-gradient(90deg,rgba(255,255,255,0.02),rgba(255,255,255,0.01));padding:10px;border-radius:8px;font-size:13px;color:var(--muted);border:1px solid rgba(255,255,255,0.02)}
  @media (max-width:720px){
    .brand h1{font-size:16px}
    .itemTop .name{font-size:14px}
  }
</style>
</head>
<body>
<div class="app" id="app">
  <header>
    <div class="brand">
      <div class="logo">💸</div>
      <div>
        <h1>Spend Elon Musk's Money — Simulator</h1>
        <div class="subtitle">Totally fake. For entertainment only. Spend freely and watch the balance drain.</div>
      </div>
    </div>

    <div class="utils">
      <div class="toggle" title="Sound controls">
        <button id="soundToggle" class="small">Enable Sound</button>
        <label style="display:flex;align-items:center;gap:6px;color:var(--muted)">
          Vol
          <input id="masterVol" type="range" min="0" max="100" value="12" style="width:90px">
        </label>
      </div>
      <div class="toggle" title="Quick actions" style="padding-right:12px">
        <button id="saveBtn" class="ghost small">Save</button>
        <button id="loadBtn" class="ghost small">Load</button>
        <button id="resetBtn" class="ghost small">Reset</button>
      </div>
    </div>
  </header>

  <section class="balanceCard" aria-live="polite">
    <div style="width:140px">
      <div style="font-size:12px;color:var(--muted)">FAKE STARTING NET WORTH</div>
      <div class="balanceAmt" id="startAmt">$250,000,000,000</div>
    </div>

    <div class="progressWrap">
      <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:6px">
        <div style="font-size:13px;color:var(--muted)">Remaining Balance</div>
        <div style="font-size:13px;color:var(--muted)">Spent: <span id="spentAmt">$0</span></div>
      </div>
      <div class="progressBar" aria-hidden="false" aria-label="Wealth remaining">
        <div class="progressFill" id="progressFill" style="width:100%"></div>
      </div>
      <div style="display:flex;align-items:center;gap:12px;margin-top:10px">
        <div style="font-size:22px;font-weight:800" id="balanceDisplay">$250,000,000,000</div>
        <div class="controlsSmall">
          <button id="spendRandomBtn" class="ghost small">Spend Randomly Once</button>
        </div>
      </div>
    </div>
  </section>

  <main class="grid" id="grid" aria-live="polite">
    <!-- items populated by JS -->
  </main>

  <div class="footer">
    <div class="bigActions">
      <button id="startAuto" class="autoBtn">Start Auto-Spend</button>
      <button id="stopAuto" class="autoBtn" style="background:linear-gradient(180deg,#ef4444,#b91c1c)">Stop Auto-Spend</button>
      <button id="buyRandomBulk" class="ghost">Buy Random Bulk</button>
      <button id="buyAllMax" class="resetBtn">Spend All On Max Items</button>
    </div>
    <div class="status" id="status">Idle</div>
  </div>

  <div class="disclaimer">
    <strong>Disclaimer:</strong> This is a fictional simulator for entertainment. No real money or accounts are used. Do not use this to impersonate people or to trick others.
  </div>
</div>

<!-- floating emoji layer -->
<div id="floatLayer"></div>

<script>
/* -------------------------
   Data & initial state
   ------------------------- */
const STARTING_BALANCE = 250_000_000_000; // $250 billion fake
const appState = {
  start: STARTING_BALANCE,
  balance: STARTING_BALANCE,
  spent: 0,
  items: [],
  autoSpending: false,
  soundOn: false
};

/* items: name, price (USD), emoji, description */
const ITEMS = [
  {id:'tesla_x', name:'Tesla Model X', price: 120_000, icon:'🚘', desc:'Luxury electric SUV'},
  {id:'cybertruck', name:'Cybertruck', price: 60_000, icon:'🛻', desc:'Armored futuristic truck'},
  {id:'tesla_rocket', name:'SpaceX Falcon 9 Launch', price: 67_000_000, icon:'🚀', desc:'One orbital launch (fake)'},
  {id:'bitcoin', name:'Bitcoin (₿)', price: 62000, icon:'🪙', desc:'One BTC (price is illustrative)'},
  {id:'crypto_pack', name:'Crypto Pack (misc)', price: 2_500, icon:'💱', desc:'Bundle of assorted tokens'},
  {id:'basketball_team', name:'Professional Basketball Team', price: 2_500_000_000, icon:'🏀', desc:'Buy a whole team (fake)'},
  {id:'playstation3', name:'PlayStation 3 (retro)', price: 50, icon:'🎮', desc:'Old-school console (nostalgia)'},
  {id:'xbox', name:'Xbox Series X', price: 499, icon:'🎮', desc:'Current-gen console'},
  {id:'private_island', name:'Private Island', price: 30_000_000, icon:'🏝️', desc:'Tropical getaway (fake)'},
  {id:'pet_asteroid', name:'Pet Asteroid', price: 980_000_000, icon:'☄️', desc:'Adopt a small near-earth rock (imaginary)'},
  {id:'tiny_bot_army', name:'Tiny Robot Army', price: 75_000_000, icon:'🤖', desc:'Cute automated helpers (novelty)'},
  {id:'lunch_burger', name:'Gourmet Burger', price: 25, icon:'🍔', desc:'A nice meal'},
  {id:'luxury_watch', name:'Luxury Watch', price: 420_000, icon:'⌚', desc:'For the wrist that has everything'},
  {id:'yacht', name:'Superyacht', price: 180_000_000, icon:'🛥️', desc:'Cruise in style'},
  {id:'mars_ticket', name:'One-way Ticket to Mars', price: 750_000_000, icon:'🪐', desc:'Reserve a seat (visual only)'},
  {id:'donut_box', name:'Box of Donuts', price: 12, icon:'🍩', desc:'Share with friends'},
  {id:'concert', name:'Private Concert', price: 5_000_000, icon:'🎤', desc:'A show at your place'},
  {id:'diamond', name:'Giant Diamond', price: 15_000_000, icon:'💎', desc:'Sparkly collectible'},
  {id:'artwork', name:'Modern Art Piece', price: 9_000_000, icon:'🖼️', desc:'Hang on your wall'},
  {id:'stadium', name:'Sports Stadium', price: 1_200_000_000, icon:'🏟️', desc:'Full venue (fake)'},
  {id:'robotaxi_fleet', name:'Robotaxi Fleet (1000)', price: 250_000_000, icon:'🚖', desc:'Autonomous fleet (demo)'},
  {id:'education', name:'Scholarship Fund', price: 10_000_000, icon:'🎓', desc:'Give away to students'},
  {id:'coffee', name:'Coffee (cup)', price: 4, icon:'☕', desc:'Fuel the devs'},
  {id:'tesla_model_s', name:'Tesla Model S Plaid', price: 135_000, icon:'⚡', desc:'High-performance sedan'},
  {id:'bag_of_money', name:'Bag of Cash (fake)', price: 20_000, icon:'💼', desc:'A suitcase of monopoly-money'},
  {id:'sattelite', name:'Comms Satellite', price: 120_000_000, icon:'🛰️', desc:'One communications satellite (imaginary)'},
  {id:'pixel_art', name:'NFT Pixel Art', price: 150_000, icon:'🖼️', desc:'A collectible token (pretend)'},
  {id:'tshirt', name:'Limited T-Shirt', price: 30, icon:'👕', desc:'Fashion statement'},
  {id:'custom_emoji', name:'Custom Emoji Pack', price: 5_000, icon:'✨', desc:'For your chats'},
  {id:'random_gift', name:'Mystery Box', price: 999, icon:'🎁', desc:'You never know what you get'}
];

// initialize app items (clone)
appState.items = ITEMS.map(it => ({...it}));

/* -------------------------
   Utilities & UI helpers
   ------------------------- */
const format$ = (n) => {
  if (n < 1_000) return '$' + n.toFixed(0);
  // show commas
  return '$' + n.toLocaleString(undefined, {maximumFractionDigits:0});
};

const clamp = (v,min,max) => Math.max(min, Math.min(max, v));

/* -------------------------
   Sound engine (Web Audio API)
   ------------------------- */
let audioCtx = null, masterGain = null;
const sound = {
  init(){
    if (audioCtx) return;
    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    masterGain = audioCtx.createGain();
    masterGain.gain.value = Number(document.getElementById('masterVol').value) / 100;
    masterGain.connect(audioCtx.destination);
  },
  setVol(v){
    if (!masterGain) return;
    masterGain.gain.setTargetAtTime(v, audioCtx.currentTime, 0.02);
  },
  // small cash "ka-ching" chord
  playCash(){
    if (!audioCtx || !appState.soundOn) return;
    const now = audioCtx.currentTime;
    const g = audioCtx.createGain(); g.gain.setValueAtTime(0.0001,now);
    const o1 = audioCtx.createOscillator(); o1.type='triangle'; o1.frequency.value=660;
    const o2 = audioCtx.createOscillator(); o2.type='sine'; o2.frequency.value=880;
    o1.connect(g); o2.connect(g); g.connect(masterGain);
    g.gain.exponentialRampToValueAtTime(0.9, now + 0.01);
    g.gain.exponentialRampToValueAtTime(0.0001, now + 0.35);
    o1.start(now); o2.start(now);
    o1.stop(now + 0.36); o2.stop(now + 0.36);
  },
  // click / blip
  playClick(){
    if (!audioCtx || !appState.soundOn) return;
    const now = audioCtx.currentTime;
    const o = audioCtx.createOscillator(); o.type='square'; o.frequency.value = 1200 + Math.random()*800;
    const g = audioCtx.createGain(); g.gain.value = 0.0001;
    o.connect(g); g.connect(masterGain);
    g.gain.exponentialRampToValueAtTime(0.6, now + 0.002);
    g.gain.exponentialRampToValueAtTime(0.0001, now + 0.08 + Math.random()*0.08);
    o.start(now); o.stop(now + 0.12 + Math.random()*0.14);
  },
  // soft glitchy whoosh
  playGlitch(){
    if (!audioCtx || !appState.soundOn) return;
    const now = audioCtx.currentTime;
    const buff = audioCtx.createBuffer(1, audioCtx.sampleRate * 0.06, audioCtx.sampleRate);
    const d = buff.getChannelData(0);
    for (let i=0;i<d.length;i++) d[i] = (Math.random()*2-1) * (1 - i/d.length);
    const src = audioCtx.createBufferSource(); src.buffer = buff;
    const fl = audioCtx.createBiquadFilter(); fl.type='bandpass'; fl.frequency.value = 1000 + Math.random()*800;
    const g = audioCtx.createGain(); g.gain.value = 0.0001;
    src.connect(fl); fl.connect(g); g.connect(masterGain);
    g.gain.exponentialRampToValueAtTime(0.8, now + 0.005);
    g.gain.exponentialRampToValueAtTime(0.0001, now + 0.07);
    src.start(now); src.stop(now + 0.08);
  }
};

/* -------------------------
   DOM refs & render
   ------------------------- */
const grid = document.getElementById('grid');
const balanceDisplay = document.getElementById('balanceDisplay');
const progressFill = document.getElementById('progressFill');
const spentDisplay = document.getElementById('spentAmt');
const statusEl = document.getElementById('status');
const floatLayer = document.getElementById('floatLayer');

function renderItems(){
  grid.innerHTML = '';
  appState.items.forEach(item => {
    const card = document.createElement('div'); card.className='card';
    card.innerHTML = `
      <div class="itemTop">
        <div class="icon">${item.icon}</div>
        <div>
          <div class="name">${item.name}</div>
          <div class="price">${format$(item.price)}</div>
        </div>
      </div>
      <div class="desc">${item.desc}</div>
      <div style="display:flex;flex-direction:column;gap:8px">
        <div class="buyRow">
          <input type="number" min="1" value="1" class="qty" aria-label="Quantity for ${item.name}">
          <button class="buy">Buy</button>
          <button class="ghost buyMax">Buy Max</button>
        </div>
      </div>
    `;
    grid.appendChild(card);

    // attach events
    const qtyEl = card.querySelector('.qty');
    const buyBtn = card.querySelector('.buy');
    const buyMaxBtn = card.querySelector('.buyMax');

    buyBtn.addEventListener('click', ()=>{
      const q = Math.max(1, Math.floor(Number(qtyEl.value) || 1));
      attemptPurchase(item.id, q);
    });
    buyMaxBtn.addEventListener('click', ()=>{
      const maxQ = Math.floor(appState.balance / item.price);
      if (maxQ <= 0) {
        flashStatus('Insufficient funds for any of this item', true);
        return;
      }
      attemptPurchase(item.id, maxQ);
      qtyEl.value = Math.max(1, Math.floor(Number(qtyEl.value) || 1));
    });
  });
}

/* -------------------------
   Purchasing & animations
   ------------------------- */
function attemptPurchase(itemId, quantity){
  const item = appState.items.find(i=>i.id===itemId);
  if (!item) return;
  if (quantity <= 0) return;
  // careful arithmetic using integers
  const cost = item.price * quantity;
  if (cost > appState.balance){
    flashStatus('Not enough balance to buy ' + quantity + ' × ' + item.name, true);
    // optionally compute max
    const maxQ = Math.floor(appState.balance / item.price);
    if (maxQ > 0){
      flashStatus(`You can buy at most ${maxQ} of ${item.name}`, false);
    }
    return;
  }
  // apply purchase
  appState.balance = Math.round((appState.balance - cost));
  appState.spent = Math.round((appState.start - appState.balance));
  updateUI();
  playPurchaseEffects(item, quantity, cost);
  saveStateToLocal();
}

function playPurchaseEffects(item, quantity, cost){
  // small status message
  flashStatus(`Bought ${quantity} × ${item.name} for ${format$(cost)}`, false);

  // sound
  if (!audioCtx) sound.init();
  sound.playCash();
  setTimeout(()=> sound.playClick(), 80 + Math.random()*60);
  setTimeout(()=> sound.playGlitch(), 150 + Math.random()*60);

  // floating emoji effect
  for (let i=0;i< Math.min(16, Math.max(3, Math.floor(Math.log10(quantity+1)*6))) ; i++){
    createFloatingEmoji(item.icon);
  }

  // small burst of confetti-like emojis near item card
  // (visual, not heavy)
}

function createFloatingEmoji(emoji){
  const el = document.createElement('div');
  el.className = 'float-emoji';
  el.textContent = emoji;
  const x = 60 + Math.random() * (window.innerWidth - 120);
  const y = window.innerHeight - (80 + Math.random()*140);
  el.style.left = x + 'px';
  el.style.top = y + 'px';
  el.style.opacity = 1;
  document.body.appendChild(el);
  // animate upward curve
  requestAnimationFrame(()=>{
    el.style.transition = 'transform 1200ms cubic-bezier(.2,.9,.3,1), opacity 1200ms linear';
    el.style.transform = `translateY(-${220 + Math.random()*200}px) translateX(${(Math.random()*200-100)}px) rotate(${Math.random()*60-30}deg)`;
    el.style.opacity = 0;
  });
  setTimeout(()=> el.remove(), 1350);
}

/* -------------------------
   UI update & helpers
   ------------------------- */
function updateUI(){
  balanceDisplay.textContent = format$(appState.balance);
  spentDisplay.textContent = format$(appState.spent);
  const pct = clamp((appState.balance / appState.start) * 100, 0, 100);
  progressFill.style.width = pct + '%';
  // if drained
  if (appState.balance <= 0) {
    appState.balance = 0;
    flashStatus('Balance drained to $0 — simulation complete!', false);
    stopAutoSpend();
  }
}

/* -------------------------
   Random spending & Auto mode
   ------------------------- */
function spendRandomOnce(){
  // pick random item that costs <= balance (or nearest)
  let affordable = appState.items.filter(i => i.price <= appState.balance);
  if (affordable.length === 0){
    flashStatus('No items affordable anymore', true);
    return;
  }
  const pick = affordable[Math.floor(Math.random()*affordable.length)];
  // choose random quantity (1..some)
  const max = Math.max(1, Math.floor(appState.balance / pick.price));
  // weight smaller items higher
  let q = Math.ceil(Math.random() * Math.min(max, 40));
  if (q > max) q = max;
  attemptPurchase(pick.id, q);
}

let autoTimer = null;
function startAutoSpend(){
  if (appState.autoSpending) return;
  appState.autoSpending = true;
  statusEl.textContent = 'Auto-Spend running...';
  // schedule repeated buys until we can't
  function schedule(){
    if (!appState.autoSpending) return;
    // if no funds for the cheapest item, stop
    const minPrice = Math.min(...appState.items.map(it=>it.price));
    if (appState.balance < minPrice){
      flashStatus('Auto stopped: insufficient funds for any items', false);
      stopAutoSpend();
      return;
    }
    // do between 1 and 4 purchases quickly
    const bursts = 1 + Math.floor(Math.random()*3);
    for (let i=0;i<bursts;i++){
      setTimeout(()=> {
        if (!appState.autoSpending) return;
        spendRandomOnce();
      }, i * (80 + Math.random()*220));
    }
    // schedule next wave with some randomness
    const next = 500 + Math.random()*1200;
    autoTimer = setTimeout(schedule, next);
  }
  schedule();
}

function stopAutoSpend(){
  appState.autoSpending = false;
  if (autoTimer) { clearTimeout(autoTimer); autoTimer = null; }
  statusEl.textContent = 'Idle';
}

/* -------------------------
   Save / Reset
   ------------------------- */
function saveStateToLocal(){
  try{
    localStorage.setItem('fakeSpendSimState', JSON.stringify({
      start: appState.start,
      balance: appState.balance,
      spent: appState.spent
    }));
    flashStatus('State saved', false);
  }catch(e){}
}
function loadStateFromLocal(){
  try{
    const raw = localStorage.getItem('fakeSpendSimState');
    if (!raw) { flashStatus('No saved state found', true); return; }
    const obj = JSON.parse(raw);
    appState.start = obj.start || appState.start;
    appState.balance = (typeof obj.balance === 'number') ? obj.balance : appState.balance;
    appState.spent = (typeof obj.spent === 'number') ? obj.spent : appState.spent;
    document.getElementById('startAmt').textContent = format$(appState.start);
    updateUI();
    flashStatus('State loaded', false);
  }catch(e){ flashStatus('Failed to load state', true); }
}
function resetState(){
  stopAutoSpend();
  appState.start = STARTING_BALANCE;
  appState.balance = STARTING_BALANCE;
  appState.spent = 0;
  document.getElementById('startAmt').textContent = format$(appState.start);
  updateUI();
  flashStatus('Simulation reset', false);
  localStorage.removeItem('fakeSpendSimState');
}

/* -------------------------
   Small UI niceties
   ------------------------- */
let statusTimeout = null;
function flashStatus(msg, isError=false){
  statusEl.textContent = msg;
  statusEl.style.color = isError ? '#fca5a5' : '#cdeccd';
  if (statusTimeout) clearTimeout(statusTimeout);
  statusTimeout = setTimeout(()=> {
    if (!appState.autoSpending) {
      statusEl.textContent = 'Idle';
      statusEl.style.color = '';
    }
  }, 4200);
}

/* -------------------------
   Bulk & "Spend All" helpers
   ------------------------- */
document.getElementById('buyAllMax').addEventListener('click', ()=>{
  // spend until no funds remain by repeatedly buying max of cheapest chosen item
  let loopCount = 0;
  while (true){
    loopCount++;
    const affordable = appState.items.filter(i => i.price <= appState.balance);
    if (affordable.length === 0 || loopCount > 5000) break;
    // pick most expensive affordable item to spend big
    affordable.sort((a,b)=>b.price - a.price);
    const pick = affordable[0];
    const maxQ = Math.floor(appState.balance / pick.price);
    if (maxQ <= 0) break;
    attemptPurchase(pick.id, maxQ);
  }
});

document.getElementById('buyRandomBulk').addEventListener('click', ()=>{
  // buy random items in bulk until we spend a chunk
  let attempts = 0;
  while (attempts < 18 && appState.balance > Math.min(...appState.items.map(i=>i.price))){
    spendRandomOnce();
    attempts++;
  }
});

/* -------------------------
   Wire other UI
   ------------------------- */
document.getElementById('spendRandomBtn').addEventListener('click', ()=> spendRandomOnce());
document.getElementById('startAuto').addEventListener('click', ()=> startAutoSpend());
document.getElementById('stopAuto').addEventListener('click', ()=> stopAutoSpend());
document.getElementById('resetBtn').addEventListener('click', ()=> resetState());
document.getElementById('saveBtn').addEventListener('click', ()=> saveStateToLocal());
document.getElementById('loadBtn').addEventListener('click', ()=> loadStateFromLocal());

document.getElementById('soundToggle').addEventListener('click', async ()=>{
  // user gesture: initialize audio
  if (!audioCtx) sound.init();
  // resume if suspended
  try{ if (audioCtx && audioCtx.state === 'suspended') await audioCtx.resume(); }catch(e){}
  appState.soundOn = !appState.soundOn;
  document.getElementById('soundToggle').textContent = appState.soundOn ? 'Sound: On' : 'Enable Sound';
  // set volume
  const vol = Number(document.getElementById('masterVol').value)/100;
  sound.setVol(vol);
  flashStatus(appState.soundOn ? 'Sound enabled' : 'Sound disabled', false);
});

// volume slider
document.getElementById('masterVol').addEventListener('input', (e)=>{
  const v = Number(e.target.value)/100;
  sound.setVol(v);
});

/* -------------------------
   Auto-save on unload
   ------------------------- */
window.addEventListener('beforeunload', ()=> {
  saveStateToLocal();
});

/* -------------------------
   Init app
   ------------------------- */
function init(){
  renderItems();
  document.getElementById('startAmt').textContent = format$(appState.start);
  updateUI();
  // make small click-to-unlock for audio contexts on first interaction
  window.addEventListener('click', function first(){
    if (audioCtx && audioCtx.state === 'suspended') audioCtx.resume().catch(()=>{});
    window.removeEventListener('click', first);
  }, {once:true});
}

init();

</script>
</body>
</html>

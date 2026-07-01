# smart-spender-market-
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Smart Spender Market</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@600;700;800&family=Nunito:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#FBF6ED;
  --ink:#2B2420;
  --ink-soft:#6B5F50;
  --orange:#E8791A;
  --orange-dark:#C2620F;
  --teal:#1F6F6B;
  --teal-dark:#164F4C;
  --gold:#D4A017;
  --need:#3F9463;
  --need-bg:#E4F3EA;
  --want:#E85D4E;
  --want-bg:#FCE7E4;
  --card:#FFFFFF;
  --border:#E4D9C4;
  --shadow: 0 4px 14px rgba(43,36,32,0.10);
}
*{box-sizing:border-box;}
body{
  margin:0;
  background:var(--bg);
  color:var(--ink);
  font-family:'Nunito',sans-serif;
  -webkit-font-smoothing:antialiased;
}
.wrap{max-width:820px;margin:0 auto;padding:0 0 60px;}

/* ---- Header / bunting ---- */
.bunting{
  height:26px;
  background:repeating-linear-gradient(
    135deg,
    var(--orange) 0 18px,
    var(--teal) 18px 36px
  );
  clip-path: polygon(
    0% 0%, 100% 0%, 100% 60%,
    97% 100%, 94% 60%, 91% 100%, 88% 60%, 85% 100%, 82% 60%, 79% 100%, 76% 60%, 73% 100%, 70% 60%,
    67% 100%, 64% 60%, 61% 100%, 58% 60%, 55% 100%, 52% 60%, 49% 100%, 46% 60%, 43% 100%, 40% 60%,
    37% 100%, 34% 60%, 31% 100%, 28% 60%, 25% 100%, 22% 60%, 19% 100%, 16% 60%, 13% 100%, 10% 60%,
    7% 100%, 4% 60%, 1% 100%, 0% 60%
  );
}
header{
  background:var(--teal-dark);
  color:#fff;
  padding:22px 20px 26px;
  text-align:center;
}
header h1{
  font-family:'Baloo 2',sans-serif;
  font-size:1.9rem;
  margin:0 0 4px;
  letter-spacing:.3px;
}
header .sub{
  font-size:.95rem;
  color:#CFE7E4;
  font-weight:700;
}
header .sub .kr{color:#FFD98E;}
header .sub .jp{color:#FFB199;}

.fullscreen-link{
  display:inline-block;
  margin-top:10px;
  background:var(--gold);
  color:#3A2A00;
  font-weight:800;
  font-size:.8rem;
  padding:6px 14px;
  border-radius:20px;
  text-decoration:none;
}

/* ---- Progress stalls ---- */
.progress{
  display:flex;
  justify-content:center;
  gap:10px;
  margin:18px 0 6px;
  flex-wrap:wrap;
}
.stall{
  width:64px;
  padding:6px 4px;
  border-radius:10px;
  background:#fff;
  border:2px solid var(--border);
  text-align:center;
  font-size:.68rem;
  font-weight:800;
  color:var(--ink-soft);
}
.stall .icon{font-size:1.2rem;display:block;}
.stall.active{border-color:var(--orange);background:#FFF3E6;color:var(--orange-dark);}
.stall.done{border-color:var(--need);background:var(--need-bg);color:var(--need);}

main{padding:10px 18px 0;}

.stage{display:none;}
.stage.active{display:block;animation:fadein .35s ease;}
@keyframes fadein{from{opacity:0;transform:translateY(6px);}to{opacity:1;transform:translateY(0);}}

.card-panel{
  background:var(--card);
  border:1px solid var(--border);
  border-radius:16px;
  padding:20px;
  box-shadow:var(--shadow);
  margin-bottom:18px;
}

h2.stage-title{
  font-family:'Baloo 2',sans-serif;
  color:var(--teal-dark);
  font-size:1.35rem;
  margin:6px 0 4px;
}
p.instructions{
  color:var(--ink-soft);
  font-size:.95rem;
  margin:0 0 16px;
  line-height:1.5;
}

.target-vocab{
  color:var(--orange-dark);
  font-weight:800;
  background:#FFF0DC;
  padding:1px 6px;
  border-radius:6px;
}

.speaker{
  border:none;
  background:none;
  cursor:pointer;
  font-size:1rem;
  vertical-align:middle;
  margin-left:2px;
  opacity:.75;
}
.speaker:hover{opacity:1;}

/* ---- Stage 1: vocab cards ---- */
.vocab-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(150px,1fr));
  gap:12px;
}
.vocab-card{
  border:2px solid var(--border);
  border-radius:14px;
  padding:12px 10px;
  text-align:center;
  background:#fff;
  cursor:pointer;
  transition:transform .15s, border-color .15s;
  user-select:none;
}
.vocab-card:hover{transform:translateY(-2px);}
.vocab-card.learned{border-color:var(--need);background:var(--need-bg);}
.vocab-card .emoji{font-size:1.7rem;display:block;margin-bottom:4px;}
.vocab-card .en{font-weight:800;color:var(--orange-dark);font-size:1rem;}
.vocab-card .kr, .vocab-card .jp{
  font-size:.8rem;color:var(--ink-soft);margin-top:2px;display:none;
}
.vocab-card.flipped .kr, .vocab-card.flipped .jp{display:block;}
.vocab-card .hint{font-size:.7rem;color:#b3a690;margin-top:6px;}
.vocab-card.flipped .hint{display:none;}

/* ---- Stage 2: sort ---- */
.sort-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(140px,1fr));
  gap:12px;
  margin-bottom:18px;
}
.item-card{
  border:2px solid var(--border);
  border-radius:14px;
  padding:10px;
  text-align:center;
  background:#fff;
  transition:opacity .2s, transform .2s;
}
.item-card.gone{opacity:0;transform:scale(.6);pointer-events:none;}
.item-card .emoji{font-size:1.6rem;}
.item-card .label{font-weight:700;font-size:.85rem;margin:4px 0 8px;}
.item-card .btns{display:flex;gap:4px;}
.item-card button{
  flex:1;
  border:none;
  border-radius:8px;
  padding:5px 2px;
  font-size:.72rem;
  font-weight:800;
  cursor:pointer;
  color:#fff;
}
.btn-need{background:var(--need);}
.btn-want{background:var(--want);}

.bins{display:flex;gap:14px;flex-wrap:wrap;}
.bin{
  flex:1;
  min-width:220px;
  border-radius:14px;
  padding:12px;
  min-height:70px;
}
.bin.need-bin{background:var(--need-bg);border:2px dashed var(--need);}
.bin.want-bin{background:var(--want-bg);border:2px dashed var(--want);}
.bin h3{margin:0 0 8px;font-family:'Baloo 2';font-size:1rem;}
.bin.need-bin h3{color:var(--need);}
.bin.want-bin h3{color:var(--want);}
.bin-items{display:flex;flex-wrap:wrap;gap:6px;font-size:1.3rem;}

.feedback-msg{
  margin-top:12px;font-weight:800;font-size:.9rem;padding:8px 12px;border-radius:10px;display:none;
}
.feedback-msg.show{display:block;}
.feedback-msg.good{background:var(--need-bg);color:var(--need);}
.feedback-msg.bad{background:var(--want-bg);color:var(--want);}

/* ---- Stage 3: shop / budget ---- */
.wallet-bar{
  display:flex;
  align-items:center;
  justify-content:space-between;
  background:var(--teal-dark);
  color:#fff;
  border-radius:14px;
  padding:12px 16px;
  margin-bottom:16px;
  font-family:'Baloo 2';
}
.wallet-bar .amt{font-size:1.3rem;}
.wallet-bar .amt span{color:var(--gold);}
.meter{
  height:14px;
  background:#0F3A38;
  border-radius:8px;
  overflow:hidden;
  flex:1;
  margin:0 14px;
}
.meter-fill{
  height:100%;
  background:linear-gradient(90deg,var(--gold),var(--orange));
  width:0%;
  transition:width .3s;
}
.shop-grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(150px,1fr));
  gap:12px;
}
.shop-card{
  border:2px solid var(--border);
  border-radius:14px;
  padding:10px;
  text-align:center;
  background:#fff;
}
.shop-card .emoji{font-size:1.7rem;}
.shop-card .label{font-weight:800;font-size:.85rem;margin:4px 0 2px;}
.shop-card .price{color:var(--gold);font-weight:800;font-size:.9rem;margin-bottom:8px;}
.shop-card button{
  width:100%;
  border:none;
  border-radius:8px;
  padding:6px;
  font-weight:800;
  cursor:pointer;
  background:var(--orange);
  color:#fff;
  font-size:.8rem;
}
.shop-card.added button{background:var(--ink-soft);}
.shop-card button:disabled{opacity:.5;cursor:not-allowed;}

.checkout-btn{
  margin-top:16px;
  background:var(--teal);
  color:#fff;
  border:none;
  padding:12px 20px;
  border-radius:30px;
  font-weight:800;
  font-size:1rem;
  cursor:pointer;
  font-family:'Baloo 2';
}
.checkout-btn:disabled{opacity:.5;cursor:not-allowed;}

/* ---- Stage 4: value for money ---- */
.vfm-q{margin-bottom:22px;}
.vfm-q .qtitle{font-weight:800;margin-bottom:10px;}
.vfm-options{display:flex;gap:12px;flex-wrap:wrap;}
.vfm-opt{
  flex:1;
  min-width:200px;
  border:2px solid var(--border);
  border-radius:14px;
  padding:14px;
  cursor:pointer;
  background:#fff;
  text-align:center;
}
.vfm-opt:hover{border-color:var(--orange);}
.vfm-opt .emoji{font-size:1.8rem;}
.vfm-opt .desc{font-weight:700;font-size:.9rem;margin-top:6px;}
.vfm-opt.correct{border-color:var(--need);background:var(--need-bg);}
.vfm-opt.wrong{border-color:var(--want);background:var(--want-bg);}
.vfm-explain{
  display:none;
  margin-top:10px;
  background:#FFF8ED;
  border-left:4px solid var(--gold);
  padding:10px 12px;
  border-radius:8px;
  font-size:.88rem;
}
.vfm-explain.show{display:block;}

/* ---- Stars ---- */
.stars{font-size:1.4rem;letter-spacing:3px;color:#DDD3C0;}
.stars .lit{color:var(--gold);}

/* ---- Nav buttons ---- */
.nav-row{
  display:flex;
  justify-content:space-between;
  margin-top:20px;
}
.nav-btn{
  border:none;
  padding:12px 26px;
  border-radius:30px;
  font-weight:800;
  font-size:.95rem;
  cursor:pointer;
  font-family:'Baloo 2';
}
.nav-btn.next{background:var(--orange);color:#fff;}
.nav-btn.next:disabled{background:#e9d9c2;color:#b3a690;cursor:not-allowed;}
.nav-btn.back{background:none;color:var(--teal-dark);border:2px solid var(--border);}

/* ---- Certificate ---- */
.cert{
  background:#fff;
  border:3px solid var(--gold);
  border-radius:18px;
  padding:26px;
  text-align:center;
}
.cert h2{font-family:'Baloo 2';color:var(--teal-dark);font-size:1.5rem;margin-top:0;}
.cert input{
  font-family:'Baloo 2';
  font-size:1.2rem;
  text-align:center;
  border:none;
  border-bottom:3px dotted var(--orange);
  color:var(--orange-dark);
  background:none;
  width:70%;
  margin:8px 0 18px;
  padding:4px;
}
.cert-row{display:flex;justify-content:space-around;flex-wrap:wrap;gap:14px;margin:16px 0;}
.cert-item{font-size:.85rem;font-weight:700;color:var(--ink-soft);}
.cert-item .stars{display:block;margin-top:2px;}
.badge{
  display:inline-block;
  margin:14px 0;
  padding:10px 22px;
  border-radius:30px;
  background:var(--teal-dark);
  color:#FFD98E;
  font-family:'Baloo 2';
  font-size:1.1rem;
}
.print-btn{
  margin-top:10px;
  background:var(--teal);
  color:#fff;
  border:none;
  padding:10px 22px;
  border-radius:24px;
  font-weight:800;
  cursor:pointer;
}
@media print{
  header,.progress,.nav-row,.print-btn,.fullscreen-link{display:none !important;}
}
</style>
</head>
<body>

<div class="bunting"></div>
<header>
  <h1>🛒 Smart Spender Market</h1>
  <div class="sub">현명한 소비자 시장 <span class="kr">|</span> 賢い消費者マーケット <span class="jp"></span></div>
  <a class="fullscreen-link" href="#" target="_blank" onclick="this.href=window.location.href;">🔊 Open full screen for sound</a>
</header>

<div class="wrap">
  <div class="progress" id="progressBar"></div>

  <main>

    <!-- INTRO -->
    <section class="stage active" data-stage="0">
      <div class="card-panel">
        <h2 class="stage-title">Welcome, Smart Spender! 환영합니다 / ようこそ</h2>
        <p class="instructions">
          Today you will learn to be a <span class="target-vocab">wise</span> spender.
          You will learn new words, sort <span class="target-vocab">needs</span> and
          <span class="target-vocab">wants</span>, spend a <span class="target-vocab">budget</span>
          at the market, and compare <span class="target-vocab">value for money</span>.
          Complete all four stalls to earn your Smart Spender Certificate!
        </p>
        <div style="text-align:center;font-size:2.4rem;">🏪 💰 🧺 🧾</div>
      </div>
      <div class="nav-row">
        <div></div>
        <button class="nav-btn next" onclick="goTo(1)">Start &rarr;</button>
      </div>
    </section>

    <!-- STAGE 1: VOCAB -->
    <section class="stage" data-stage="1">
      <div class="card-panel">
        <h2 class="stage-title">Stall 1: Word Market 단어 시장 / 単語マーケット</h2>
        <p class="instructions">Tap each card to reveal the Korean and Japanese words. Listen with 🔊, then tap again to mark it as learned.</p>
        <div class="vocab-grid" id="vocabGrid"></div>
      </div>
      <div class="nav-row">
        <button class="nav-btn back" onclick="goTo(0)">&larr; Back</button>
        <button class="nav-btn next" id="s1next" onclick="goTo(2)" disabled>Next &rarr;</button>
      </div>
    </section>

    <!-- STAGE 2: SORT -->
    <section class="stage" data-stage="2">
      <div class="card-panel">
        <h2 class="stage-title">Stall 2: Need or Want? 필요 vs 원함 / 必要 vs 欲しい</h2>
        <p class="instructions">
          Look at each item. Decide: is it a <span class="target-vocab">need</span> (something you must have)
          or a <span class="target-vocab">want</span> (something nice to have)?
        </p>
        <div class="sort-grid" id="sortGrid"></div>
        <div class="bins">
          <div class="bin need-bin"><h3>✅ Need 필요한 것 / 必要なもの</h3><div class="bin-items" id="needBin"></div></div>
          <div class="bin want-bin"><h3>💛 Want 원하는 것 / 欲しいもの</h3><div class="bin-items" id="wantBin"></div></div>
        </div>
        <div class="feedback-msg" id="s2feedback"></div>
      </div>
      <div class="nav-row">
        <button class="nav-btn back" onclick="goTo(1)">&larr; Back</button>
        <button class="nav-btn next" id="s2next" onclick="goTo(3)" disabled>Next &rarr;</button>
      </div>
    </section>

    <!-- STAGE 3: BUDGET -->
    <section class="stage" data-stage="3">
      <div class="card-panel">
        <h2 class="stage-title">Stall 3: Budget Challenge 예산 도전 / 予算チャレンジ</h2>
        <p class="instructions">
          You have a <span class="target-vocab">budget</span> of 20 coins. Choose what to
          <span class="target-vocab">spend</span> your money on. Try to buy what you need,
          check the <span class="target-vocab">price</span> of each item, and see if you can
          <span class="target-vocab">save</span> a little too!
        </p>
        <div class="wallet-bar">
          <div>💰 <span class="amt">Spent: <span id="spentAmt">0</span> / 20</span></div>
          <div class="meter"><div class="meter-fill" id="meterFill"></div></div>
          <div class="amt">Left: <span id="leftAmt">20</span></div>
        </div>
        <div class="shop-grid" id="shopGrid"></div>
        <div style="text-align:center;">
          <button class="checkout-btn" id="checkoutBtn" onclick="checkout()" disabled>🧾 Checkout</button>
        </div>
        <div class="feedback-msg" id="s3feedback"></div>
      </div>
      <div class="nav-row">
        <button class="nav-btn back" onclick="goTo(2)">&larr; Back</button>
        <button class="nav-btn next" id="s3next" onclick="goTo(4)" disabled>Next &rarr;</button>
      </div>
    </section>

    <!-- STAGE 4: VALUE FOR MONEY -->
    <section class="stage" data-stage="4">
      <div class="card-panel">
        <h2 class="stage-title">Stall 4: Best Value 가성비 / コスパ</h2>
        <p class="instructions">
          <span class="target-vocab">Compare</span> the two choices. Which one is better
          <span class="target-vocab">value for money</span>?
        </p>
        <div id="vfmContainer"></div>
      </div>
      <div class="nav-row">
        <button class="nav-btn back" onclick="goTo(3)">&larr; Back</button>
        <button class="nav-btn next" id="s4next" onclick="goTo(5)" disabled>See Certificate &rarr;</button>
      </div>
    </section>

    <!-- CERTIFICATE -->
    <section class="stage" data-stage="5">
      <div class="cert">
        <h2>🏅 Smart Spender Certificate</h2>
        <div>이름 / 名前 / Name:</div>
        <input type="text" id="studentName" placeholder="Type your name">
        <div class="cert-row" id="certRow"></div>
        <div class="badge" id="certBadge">Smart Spender</div>
        <div>
          <button class="print-btn" onclick="window.print()">🖨️ Print Certificate</button>
        </div>
      </div>
      <div class="nav-row">
        <button class="nav-btn back" onclick="goTo(4)">&larr; Back</button>
        <div></div>
      </div>
    </section>

  </main>
</div>

<script>
/* ---------- Speech ---------- */
function speak(text, lang){
  try{
    window.speechSynthesis.cancel();
    const u = new SpeechSynthesisUtterance(text);
    u.lang = lang;
    u.rate = 0.9;
    window.speechSynthesis.speak(u);
  }catch(e){}
}

/* ---------- Navigation ---------- */
const stageNames = [
  {icon:'🏪',label:'Start'},
  {icon:'📖',label:'Words'},
  {icon:'🧺',label:'Sort'},
  {icon:'💰',label:'Budget'},
  {icon:'🧾',label:'Value'},
  {icon:'🏅',label:'Done'}
];
let currentStage = 0;
let completed = [false,false,false,false,false,false];

function renderProgress(){
  const bar = document.getElementById('progressBar');
  bar.innerHTML = '';
  stageNames.forEach((s,i)=>{
    const div = document.createElement('div');
    div.className = 'stall' + (i===currentStage?' active':'') + (completed[i]&&i!==currentStage?' done':'');
    div.innerHTML = `<span class="icon">${s.icon}</span>${s.label}`;
    bar.appendChild(div);
  });
}

function goTo(stage){
  completed[currentStage] = true;
  document.querySelectorAll('.stage').forEach(s=>s.classList.remove('active'));
  document.querySelector(`.stage[data-stage="${stage}"]`).classList.add('active');
  currentStage = stage;
  renderProgress();
  if(stage===5) buildCertificate();
  window.scrollTo({top:0,behavior:'smooth'});
}

/* ---------- STAGE 1: Vocab ---------- */
const vocab = [
  {emoji:'🎯',en:'need',kr:'필요한 것',jp:'必要なもの'},
  {emoji:'💛',en:'want',kr:'원하는 것',jp:'欲しいもの'},
  {emoji:'💸',en:'spend',kr:'쓰다',jp:'使う'},
  {emoji:'🐷',en:'save',kr:'저축하다',jp:'貯金する'},
  {emoji:'📋',en:'budget',kr:'예산',jp:'予算'},
  {emoji:'🏷️',en:'price',kr:'가격',jp:'値段'},
  {emoji:'👛',en:'afford',kr:'살 여유가 있다',jp:'買う余裕がある'},
  {emoji:'✅',en:'choose',kr:'선택하다',jp:'選ぶ'},
  {emoji:'⚖️',en:'compare',kr:'비교하다',jp:'比較する'},
  {emoji:'🧠',en:'wise',kr:'현명한',jp:'賢い'}
];
let learnedCount = 0;
function buildVocab(){
  const grid = document.getElementById('vocabGrid');
  vocab.forEach((v,i)=>{
    const card = document.createElement('div');
    card.className = 'vocab-card';
    card.id = 'vcard'+i;
    card.innerHTML = `
      <span class="emoji">${v.emoji}</span>
      <div class="en">${v.en} <button class="speaker" onclick="event.stopPropagation();speak('${v.en}','en-US')">🔊</button></div>
      <div class="kr">${v.kr} <button class="speaker" onclick="event.stopPropagation();speak('${v.kr}','ko-KR')">🔊</button></div>
      <div class="jp">${v.jp} <button class="speaker" onclick="event.stopPropagation();speak('${v.jp}','ja-JP')">🔊</button></div>
      <div class="hint">Tap to reveal</div>
    `;
    card.onclick = ()=>{
      if(!card.classList.contains('flipped')){
        card.classList.add('flipped');
        speak(v.en,'en-US');
      } else if(!card.classList.contains('learned')){
        card.classList.add('learned');
        learnedCount++;
        if(learnedCount===vocab.length) document.getElementById('s1next').disabled=false;
      }
    };
    grid.appendChild(card);
  });
}

/* ---------- STAGE 2: Sort ---------- */
const sortItems = [
  {emoji:'🍞',en:'bread',cat:'need'},
  {emoji:'👟',en:'school shoes',cat:'need'},
  {emoji:'💊',en:'medicine',cat:'need'},
  {emoji:'💧',en:'water',cat:'need'},
  {emoji:'📚',en:'school book',cat:'need'},
  {emoji:'🎮',en:'video game',cat:'want'},
  {emoji:'🍬',en:'candy',cat:'want'},
  {emoji:'🎈',en:'balloon',cat:'want'},
  {emoji:'🧸',en:'toy',cat:'want'},
  {emoji:'🎧',en:'headphones',cat:'want'}
];
let sortedCorrect = 0;
let sortedTotal = 0;
function buildSort(){
  const grid = document.getElementById('sortGrid');
  sortItems.forEach((item,i)=>{
    const card = document.createElement('div');
    card.className = 'item-card';
    card.id = 'sitem'+i;
    card.innerHTML = `
      <span class="emoji">${item.emoji}</span>
      <div class="label">${item.en}</div>
      <div class="btns">
        <button class="btn-need" onclick="sortItem(${i},'need')">Need</button>
        <button class="btn-want" onclick="sortItem(${i},'want')">Want</button>
      </div>
    `;
    grid.appendChild(card);
  });
}
function sortItem(i, guess){
  const item = sortItems[i];
  const card = document.getElementById('sitem'+i);
  if(card.classList.contains('gone')) return;
  sortedTotal++;
  const fb = document.getElementById('s2feedback');
  fb.classList.add('show');
  if(guess === item.cat){
    sortedCorrect++;
    fb.className = 'feedback-msg show good';
    fb.textContent = `✅ Correct! ${item.en} is a ${item.cat}.`;
    card.classList.add('gone');
    setTimeout(()=>{
      const bin = document.getElementById(item.cat==='need'?'needBin':'wantBin');
      bin.innerHTML += item.emoji + ' ';
      checkSortDone();
    },250);
  } else {
    fb.className = 'feedback-msg show bad';
    fb.textContent = `❌ Try again! Think about whether ${item.en} is really a need.`;
  }
}
function checkSortDone(){
  const remaining = document.querySelectorAll('#sortGrid .item-card:not(.gone)').length;
  if(remaining === 0){
    document.getElementById('s2next').disabled = false;
  }
}

/* ---------- STAGE 3: Budget ---------- */
const budget = 20;
const shopItems = [
  {emoji:'🍞',en:'bread',price:3,cat:'need'},
  {emoji:'🍎',en:'fruit',price:4,cat:'need'},
  {emoji:'✏️',en:'pencils',price:2,cat:'need'},
  {emoji:'📖',en:'storybook',price:5,cat:'want'},
  {emoji:'🧸',en:'toy car',price:8,cat:'want'},
  {emoji:'🍬',en:'candy',price:2,cat:'want'},
  {emoji:'🧃',en:'juice',price:3,cat:'want'},
  {emoji:'🎮',en:'video game',price:15,cat:'want'}
];
let cart = [];
function buildShop(){
  const grid = document.getElementById('shopGrid');
  shopItems.forEach((item,i)=>{
    const card = document.createElement('div');
    card.className = 'shop-card';
    card.id = 'shop'+i;
    card.innerHTML = `
      <span class="emoji">${item.emoji}</span>
      <div class="label">${item.en}</div>
      <div class="price">${item.price} coins</div>
      <button onclick="addToCart(${i})">Add</button>
    `;
    grid.appendChild(card);
  });
}
function addToCart(i){
  const item = shopItems[i];
  const spent = cart.reduce((a,c)=>a+c.price,0);
  if(spent + item.price > budget) {
    const fb = document.getElementById('s3feedback');
    fb.className='feedback-msg show bad';
    fb.textContent = `❌ Not enough coins left to afford ${item.en}!`;
    return;
  }
  cart.push(item);
  updateWallet();
  const card = document.getElementById('shop'+i);
  card.classList.add('added');
  const btn = card.querySelector('button');
  btn.textContent = 'Added ✓';
  btn.disabled = true;
  document.getElementById('checkoutBtn').disabled = false;
}
function updateWallet(){
  const spent = cart.reduce((a,c)=>a+c.price,0);
  document.getElementById('spentAmt').textContent = spent;
  document.getElementById('leftAmt').textContent = budget - spent;
  document.getElementById('meterFill').style.width = Math.min(100,(spent/budget)*100) + '%';
}
let budgetStars = 0;
function checkout(){
  const spent = cart.reduce((a,c)=>a+c.price,0);
  const needs = cart.filter(c=>c.cat==='need').length;
  const wants = cart.filter(c=>c.cat==='want').length;
  const left = budget - spent;
  const fb = document.getElementById('s3feedback');
  fb.classList.add('show');
  let msg = '';
  let stars = 0;
  if(needs >= 1) stars++;
  if(wants <= 2) stars++;
  if(left >= 2) stars++;
  if(stars === 0) stars = 1;
  budgetStars = stars;
  if(needs === 0){
    msg = "🤔 You didn't buy any needs. A wise spender thinks about needs first!";
    fb.className = 'feedback-msg show bad';
  } else if(left >= 2 && wants <= 2){
    msg = `🎉 Great budgeting! You bought ${needs} need(s), ${wants} want(s), and saved ${left} coins!`;
    fb.className = 'feedback-msg show good';
  } else {
    msg = `👍 Good try! You bought ${needs} need(s) and ${wants} want(s), with ${left} coins left. Could you save a little more next time?`;
    fb.className = 'feedback-msg show good';
  }
  fb.textContent = msg;
  document.getElementById('checkoutBtn').disabled = true;
  document.getElementById('s3next').disabled = false;
}

/* ---------- STAGE 4: Value for money ---------- */
const vfmQuestions = [
  {
    q:'Which juice is better value for money?',
    a:{emoji:'🧃',desc:'Small juice: 2 coins for 200ml'},
    b:{emoji:'🧃',desc:'Big juice: 3 coins for 500ml'},
    correct:'b',
    explain:'The big juice costs a little more, but you get much more juice for each coin — that is better value for money!'
  },
  {
    q:'Which toy is better value for money?',
    a:{emoji:'🧸',desc:'Cheap toy: 5 coins, breaks in a week'},
    b:{emoji:'🧸',desc:'Quality toy: 10 coins, lasts a whole year'},
    correct:'b',
    explain:'The quality toy costs more, but lasts much longer. A wise spender compares how long things last, not just the price.'
  },
  {
    q:'Which is better value for money?',
    a:{emoji:'🍪',desc:'1 cookie for 1 coin'},
    b:{emoji:'🍪',desc:'Box of 10 cookies for 6 coins'},
    correct:'b',
    explain:'The box works out to about 0.6 coins per cookie, cheaper than buying just one — that is better value!'
  },
  {
    q:'Which is better value for money?',
    a:{emoji:'✏️',desc:'1 pencil for 1.5 coins'},
    b:{emoji:'✏️',desc:'Pack of 5 pencils for 5 coins'},
    correct:'b',
    explain:'The pack costs 1 coin per pencil, which is cheaper than 1.5 coins for a single pencil.'
  }
];
let vfmAnswered = 0;
let vfmCorrect = 0;
function buildVfm(){
  const container = document.getElementById('vfmContainer');
  vfmQuestions.forEach((q,i)=>{
    const block = document.createElement('div');
    block.className = 'vfm-q';
    block.innerHTML = `
      <div class="qtitle">${i+1}. ${q.q}</div>
      <div class="vfm-options">
        <div class="vfm-opt" id="vfm${i}a" onclick="answerVfm(${i},'a')">
          <span class="emoji">${q.a.emoji}</span>
          <div class="desc">${q.a.desc}</div>
        </div>
        <div class="vfm-opt" id="vfm${i}b" onclick="answerVfm(${i},'b')">
          <span class="emoji">${q.b.emoji}</span>
          <div class="desc">${q.b.desc}</div>
        </div>
      </div>
      <div class="vfm-explain" id="vfmExplain${i}">💡 ${q.explain}</div>
    `;
    container.appendChild(block);
  });
}
function answerVfm(i, choice){
  const optA = document.getElementById('vfm'+i+'a');
  const optB = document.getElementById('vfm'+i+'b');
  if(optA.classList.contains('correct') || optA.classList.contains('wrong')) return; // already answered
  const q = vfmQuestions[i];
  const chosenEl = choice==='a'?optA:optB;
  const correctEl = q.correct==='a'?optA:optB;
  if(choice === q.correct){
    chosenEl.classList.add('correct');
    vfmCorrect++;
  } else {
    chosenEl.classList.add('wrong');
    correctEl.classList.add('correct');
  }
  document.getElementById('vfmExplain'+i).classList.add('show');
  vfmAnswered++;
  if(vfmAnswered === vfmQuestions.length){
    document.getElementById('s4next').disabled = false;
  }
}

/* ---------- Certificate ---------- */
function starString(n, max){
  let s='';
  for(let i=0;i<max;i++){
    s += i<n ? '<span class="lit">★</span>' : '★';
  }
  return s;
}
function buildCertificate(){
  const vocabStars = learnedCount === vocab.length ? 3 : 1;
  const sortStars = sortedCorrect === sortItems.length && sortedTotal===sortItems.length ? 3 : 2;
  const vfmStars = Math.max(1, Math.round((vfmCorrect/vfmQuestions.length)*3));
  const total = vocabStars + sortStars + budgetStars + vfmStars;
  const row = document.getElementById('certRow');
  row.innerHTML = `
    <div class="cert-item">📖 Words<div class="stars">${starString(vocabStars,3)}</div></div>
    <div class="cert-item">🧺 Sorting<div class="stars">${starString(sortStars,3)}</div></div>
    <div class="cert-item">💰 Budget<div class="stars">${starString(budgetStars,3)}</div></div>
    <div class="cert-item">🧾 Value<div class="stars">${starString(vfmStars,3)}</div></div>
  `;
  let badge = 'Bronze Spender 🥉';
  if(total >= 11) badge = 'Gold Smart Spender 🥇';
  else if(total >= 8) badge = 'Silver Smart Spender 🥈';
  document.getElementById('certBadge').textContent = badge;
}

/* ---------- Init ---------- */
buildVocab();
buildSort();
buildShop();
buildVfm();
renderProgress();
</script>
</body>
</html>

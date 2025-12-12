<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1"/>
  <title>Grammar Trainer: Past Continuous vs Past Perfect</title>
  <style>
    :root{
      --brand:#64d404;
      --bg:#0b0f12;
      --card:#101821;
      --muted:#9fb0c0;
      --text:#eaf2ff;
      --danger:#ff5a5a;
      --ok:#3ddc84;
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius: 18px;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      background: radial-gradient(1200px 600px at 20% 0%, rgba(100,212,4,.18), transparent 60%),
                  radial-gradient(900px 500px at 80% 10%, rgba(0,160,255,.12), transparent 60%),
                  var(--bg);
      color:var(--text);
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:18px;
    }
    .app{
      width:min(980px, 100%);
      background: rgba(16,24,33,.65);
      border:1px solid rgba(255,255,255,.06);
      border-radius: calc(var(--radius) + 8px);
      box-shadow: var(--shadow);
      overflow:hidden;
      backdrop-filter: blur(10px);
    }
    header{
      display:flex;
      gap:14px;
      align-items:center;
      justify-content:space-between;
      padding:16px 18px;
      background: linear-gradient(90deg, rgba(100,212,4,.18), rgba(255,255,255,.03));
      border-bottom:1px solid rgba(255,255,255,.06);
    }
    .brand{
      display:flex;
      align-items:center;
      gap:12px;
      min-width:0;
    }
    .dot{
      width:14px;height:14px;border-radius:999px;
      background: var(--brand);
      box-shadow: 0 0 0 6px rgba(100,212,4,.12);
      flex:none;
    }
    h1{
      font-size:16px;
      margin:0;
      letter-spacing:.2px;
      font-weight:750;
      white-space:nowrap;
      overflow:hidden;
      text-overflow:ellipsis;
    }
    .sub{
      font-size:12px;
      color:var(--muted);
      margin-top:2px;
    }
    .meta{
      text-align:right;
      color:var(--muted);
      font-size:12px;
      line-height:1.2;
    }
    .progressWrap{
      padding:10px 18px;
      border-bottom:1px solid rgba(255,255,255,.06);
      background: rgba(0,0,0,.15);
    }
    .progressBar{
      height:10px;
      background: rgba(255,255,255,.08);
      border-radius: 999px;
      overflow:hidden;
    }
    .progressBar > div{
      height:100%;
      width:0%;
      background: linear-gradient(90deg, var(--brand), rgba(100,212,4,.55));
      border-radius:999px;
      transition: width .35s ease;
    }

    .stage{
      padding:18px;
    }
    .slide{
      display:none;
      animation: fadeUp .18s ease;
    }
    .slide.active{display:block}
    @keyframes fadeUp{
      from{opacity:.0; transform: translateY(6px)}
      to{opacity:1; transform: translateY(0)}
    }

    .card{
      background: rgba(16,24,33,.85);
      border:1px solid rgba(255,255,255,.07);
      border-radius: var(--radius);
      box-shadow: 0 14px 40px rgba(0,0,0,.30);
      padding:18px;
    }

    .row{display:flex; gap:14px; flex-wrap:wrap}
    .col{flex:1 1 320px; min-width: 280px}

    .titleRow{
      display:flex;
      align-items:flex-start;
      justify-content:space-between;
      gap:12px;
      margin-bottom:10px;
    }
    h2{
      margin:0;
      font-size:18px;
      font-weight:800;
      letter-spacing:.2px;
    }
    .pill{
      flex:none;
      font-size:12px;
      padding:6px 10px;
      border-radius:999px;
      border:1px solid rgba(255,255,255,.09);
      color: var(--muted);
      background: rgba(255,255,255,.03);
    }
    p{color: var(--text); line-height:1.55; margin:10px 0}
    .muted{color:var(--muted)}
    .hr{
      height:1px;
      background: rgba(255,255,255,.08);
      margin:14px 0;
    }

    .grid2{
      display:grid;
      grid-template-columns: 1fr 1fr;
      gap:12px;
    }
    @media (max-width:780px){ .grid2{grid-template-columns:1fr} }

    .box{
      border:1px solid rgba(255,255,255,.08);
      border-radius: 14px;
      padding:12px;
      background: rgba(255,255,255,.02);
    }
    .box h3{
      margin:0 0 8px 0;
      font-size:13px;
      color: var(--muted);
      font-weight:700;
      letter-spacing:.2px;
      text-transform: uppercase;
    }
    .example{
      padding:10px 12px;
      border-left:4px solid rgba(100,212,4,.75);
      background: rgba(100,212,4,.06);
      border-radius: 12px;
      margin:10px 0;
    }
    .example strong{color:#dbffd1}
    .kbd{
      display:inline-block;
      padding:2px 8px;
      border-radius: 10px;
      background: rgba(255,255,255,.06);
      border:1px solid rgba(255,255,255,.08);
      font-size:12px;
      color: var(--muted);
      margin:0 3px 3px 0;
      white-space:nowrap;
    }

    .q{
      margin:12px 0;
      padding:12px;
      border:1px solid rgba(255,255,255,.08);
      border-radius: 14px;
      background: rgba(0,0,0,.16);
    }
    .q .prompt{
      font-weight:700;
      margin:0 0 10px 0;
    }
    .options{
      display:grid;
      gap:8px;
    }
    .optBtn{
      text-align:left;
      border-radius: 14px;
      border:1px solid rgba(255,255,255,.10);
      background: rgba(255,255,255,.03);
      color: var(--text);
      padding:10px 12px;
      cursor:pointer;
      transition: transform .05s ease, background .15s ease, border-color .15s ease;
    }
    .optBtn:hover{background: rgba(255,255,255,.06)}
    .optBtn:active{transform: translateY(1px)}
    .optBtn.correct{
      border-color: rgba(61,220,132,.55);
      background: rgba(61,220,132,.10);
    }
    .optBtn.wrong{
      border-color: rgba(255,90,90,.55);
      background: rgba(255,90,90,.10);
    }

    .controls{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      margin-top:12px;
    }
    button{
      border:0;
      border-radius: 14px;
      padding:10px 12px;
      cursor:pointer;
      background: rgba(255,255,255,.06);
      color: var(--text);
      border:1px solid rgba(255,255,255,.10);
      transition: background .15s ease, transform .05s ease, border-color .15s ease;
      font-weight:650;
    }
    button:hover{background: rgba(255,255,255,.09)}
    button:active{transform: translateY(1px)}
    button.primary{
      background: rgba(100,212,4,.14);
      border-color: rgba(100,212,4,.35);
    }
    button.primary:hover{background: rgba(100,212,4,.20)}
    button.danger{
      background: rgba(255,90,90,.12);
      border-color: rgba(255,90,90,.35);
    }
    button.ghost{
      background: transparent;
    }
    button:disabled{
      opacity:.55;
      cursor:not-allowed;
    }

    input[type="text"], textarea, select{
      width:100%;
      background: rgba(0,0,0,.18);
      border:1px solid rgba(255,255,255,.10);
      border-radius: 14px;
      color: var(--text);
      padding:10px 12px;
      outline:none;
      font-size:15px;
    }
    textarea{min-height:120px; resize:vertical}

    .bank{
      display:flex;
      flex-wrap:wrap;
      gap:8px;
      margin-top:10px;
    }
    .chip{
      user-select:none;
      padding:8px 10px;
      border-radius: 999px;
      background: rgba(255,255,255,.05);
      border:1px solid rgba(255,255,255,.10);
      cursor:pointer;
      font-weight:650;
      color: var(--text);
    }
    .chip:hover{background: rgba(255,255,255,.08)}
    .chip.used{
      opacity:.4;
      cursor:not-allowed;
      text-decoration: line-through;
    }

    .resultLine{
      margin-top:10px;
      font-weight:750;
    }
    .ok{color: var(--ok)}
    .bad{color: var(--danger)}
    .tip{
      font-size:13px;
      color: var(--muted);
      margin-top:8px;
    }

    .nav{
      display:flex;
      gap:10px;
      justify-content:space-between;
      padding:14px 18px 18px 18px;
      border-top:1px solid rgba(255,255,255,.06);
      background: rgba(0,0,0,.16);
    }
    .nav .left, .nav .right{display:flex; gap:10px; flex-wrap:wrap}
    .slideCount{align-self:center; color:var(--muted); font-size:12px}
    .tiny{font-size:12px; color:var(--muted)}
    .badge{
      display:inline-flex;
      align-items:center;
      gap:8px;
      padding:8px 10px;
      border-radius: 14px;
      border:1px solid rgba(255,255,255,.10);
      background: rgba(255,255,255,.03);
      color: var(--muted);
      font-size:12px;
    }
    .toggleRow{display:flex; gap:10px; flex-wrap:wrap; align-items:center}
  </style>
</head>
<body>
  <div class="app" id="app">
    <header>
      <div class="brand">
        <div class="dot"></div>
        <div style="min-width:0">
          <h1>Past Continuous vs Past Perfect</h1>
          <div class="sub">Explanation + exercises (easy → hard) • listening • speaking • writing</div>
        </div>
      </div>
      <div class="meta">
        <div id="ttsStatus">🔊 TTS: ready</div>
        <div id="micStatus">🎙️ Speech: optional</div>
      </div>
    </header>

    <div class="progressWrap">
      <div class="progressBar"><div id="bar"></div></div>
      <div style="display:flex; justify-content:space-between; margin-top:8px">
        <div class="tiny" id="topicLine">Topic: Past Continuous & Past Perfect</div>
        <div class="tiny" id="scoreLine">Score: <span id="score">0</span> / <span id="maxScore">0</span></div>
      </div>
    </div>

    <div class="stage">

      <!-- SLIDE 1: Overview -->
      <section class="slide active" data-slide="1">
        <div class="card">
          <div class="titleRow">
            <h2>1) The big idea</h2>
            <span class="pill">Explanation</span>
          </div>

          <div class="grid2">
            <div class="box">
              <h3>Past Continuous</h3>
              <p class="muted"><b>was / were + -ing</b></p>
              <p>Use it for an <b>action in progress</b> at a specific time in the past.</p>
              <div class="example"><strong>At 8 pm yesterday</strong>, I <strong>was cooking</strong>.</div>
              <p class="muted">Italian hint: spesso è come “<i>stavo + gerundio</i>”.</p>
            </div>

            <div class="box">
              <h3>Past Perfect</h3>
              <p class="muted"><b>had + past participle</b></p>
              <p>Use it for an action that happened <b>before another past moment</b>.</p>
              <div class="example">When I arrived, they <strong>had already left</strong>.</div>
              <p class="muted">Italian hint: spesso è come “<i>avevo + participio</i>”.</p>
            </div>
          </div>

          <div class="hr"></div>
          <p><b>Timeline mental picture:</b></p>
          <p class="muted">
            Past Perfect = earlier past (action 1) → Past Simple/Continuous = later past (action 2).
            Past Continuous = background action in progress.
          </p>

          <div class="toggleRow">
            <span class="badge">Tip: use 🔊 buttons to listen</span>
            <span class="badge">Tip: try speaking on slides 8–9</span>
          </div>
        </div>
      </section>

      <!-- SLIDE 2: Contrast & common mistakes -->
      <section class="slide" data-slide="2">
        <div class="card">
          <div class="titleRow">
            <h2>2) How they work together</h2>
            <span class="pill">Explanation</span>
          </div>

          <div class="grid2">
            <div class="box">
              <h3>Common pattern</h3>
              <p><b>Past Perfect</b> (first) + <b>Past Simple</b> (second)</p>
              <div class="example">
                I <strong>had finished</strong> my work, so I <strong>went</strong> out.
              </div>
              <button class="primary" data-tts="I had finished my work, so I went out.">🔊 Listen</button>
            </div>

            <div class="box">
              <h3>Another pattern</h3>
              <p><b>Past Continuous</b> (background) + <b>Past Simple</b> (interrupt)</p>
              <div class="example">
                I <strong>was sleeping</strong> when the phone <strong>rang</strong>.
              </div>
              <button class="primary" data-tts="I was sleeping when the phone rang.">🔊 Listen</button>
            </div>
          </div>

          <div class="hr"></div>
          <div class="box">
            <h3>Typical Italian mistakes</h3>
            <p>1) Overusing Past Continuous for “earlier past” (but you need <b>Past Perfect</b>).</p>
            <p>2) Forgetting <b>had</b> in Past Perfect: “I finished already” → better: “I <b>had</b> finished already.”</p>
            <p>3) Using Past Perfect when the order is clear and not needed: Past Perfect is for clarity (often with <b>before / already / when / by the time</b>).</p>
          </div>
        </div>
      </section>

      <!-- SLIDE 3: Recognition MCQ -->
      <section class="slide" data-slide="3">
        <div class="card">
          <div class="titleRow">
            <h2>3) Recognition: choose the best tense</h2>
            <span class="pill">Easy</span>
          </div>

          <div id="mcq1"></div>

          <div class="controls">
            <button class="ghost" id="mcq1Reset">🔄 Reset</button>
          </div>
          <div class="tip">Goal: recognize which tense fits the situation.</div>
        </div>
      </section>

      <!-- SLIDE 4: Spot the meaning -->
      <section class="slide" data-slide="4">
        <div class="card">
          <div class="titleRow">
            <h2>4) Meaning check: what happened first?</h2>
            <span class="pill">Easy → Medium</span>
          </div>

          <div id="mcq2"></div>

          <div class="controls">
            <button class="ghost" id="mcq2Reset">🔄 Reset</button>
          </div>
          <div class="tip">Goal: understand the timeline (first vs second).</div>
        </div>
      </section>

      <!-- SLIDE 5: Fill gaps with word bank -->
      <section class="slide" data-slide="5">
        <div class="card">
          <div class="titleRow">
            <h2>5) Fill the gaps (with word bank)</h2>
            <span class="pill">Medium</span>
          </div>

          <p class="muted">Click a word chip, then click a blank. Word bank is shuffled each time.</p>

          <div class="q" id="bankGapQ">
            <div class="prompt">Complete the sentences:</div>
            <div id="bankGapText"></div>
            <div class="bank" id="bankChips"></div>
            <div class="controls">
              <button class="primary" id="bankCheck">✅ Check</button>
              <button class="ghost" id="bankReset">🔄 Shuffle & Reset</button>
            </div>
            <div class="resultLine" id="bankResult"></div>
          </div>

          <div class="tip">Goal: produce correct forms with help (scaffolding).</div>
        </div>
      </section>

      <!-- SLIDE 6: Harder fill (no bank) -->
      <section class="slide" data-slide="6">
        <div class="card">
          <div class="titleRow">
            <h2>6) Fill the gaps (no word bank)</h2>
            <span class="pill">Harder</span>
          </div>

          <div id="typedGap"></div>

          <div class="controls">
            <button class="primary" id="typedCheck">✅ Check</button>
            <button class="ghost" id="typedReveal">👀 Reveal answers</button>
            <button class="ghost" id="typedReset">🔄 Reset</button>
          </div>

          <div class="resultLine" id="typedResult"></div>
          <div class="tip">Goal: accuracy without scaffolding.</div>
        </div>
      </section>

      <!-- SLIDE 7: Listening -->
      <section class="slide" data-slide="7">
        <div class="card">
          <div class="titleRow">
            <h2>7) Listening: choose what you heard</h2>
            <span class="pill">Listening</span>
          </div>

          <div class="q" id="listenQ">
            <div class="prompt">Press 🔊 then choose the exact sentence you heard.</div>
            <div class="controls">
              <button class="primary" id="listenPlay">🔊 Play sentence</button>
              <button class="ghost" id="listenNew">🎲 New sentence</button>
            </div>
            <div class="options" id="listenOptions"></div>
            <div class="resultLine" id="listenResult"></div>
          </div>

          <div class="tip">Goal: connect sound → grammar pattern.</div>
        </div>
      </section>

      <!-- SLIDE 8: Speaking (guided) -->
      <section class="slide" data-slide="8">
        <div class="card">
          <div class="titleRow">
            <h2>8) Speaking: guided sentences</h2>
            <span class="pill">Speaking</span>
          </div>

          <p class="muted">Say the sentence out loud. If speech recognition works on your device, press 🎙️ and compare.</p>

          <div class="q">
            <div class="prompt" id="speakPrompt"></div>
            <div class="controls">
              <button class="primary" id="speakTTS">🔊 Listen</button>
              <button id="speakNext">🎲 Next prompt</button>
              <button class="primary" id="speakMic">🎙️ Record (optional)</button>
            </div>
            <div class="box" style="margin-top:12px">
              <h3>Your transcript (if available)</h3>
              <div id="speakTranscript" class="muted">—</div>
            </div>
            <div class="tip">Goal: fluency + correct structure.</div>
          </div>
        </div>
      </section>

      <!-- SLIDE 9: Pronunciation focus -->
      <section class="slide" data-slide="9">
        <div class="card">
          <div class="titleRow">
            <h2>9) Pronunciation: rhythm & key words</h2>
            <span class="pill">Pronunciation</span>
          </div>

          <div class="box">
            <h3>Mini focus</h3>
            <p class="muted">
              Stress the helper verbs: <span class="kbd">was / were</span> and <span class="kbd">had</span>.
              Keep -ing smooth: <span class="kbd">was COOK-ing</span>.
              Past participles: <span class="kbd">had FIN-ished</span>.
            </p>
          </div>

          <div class="q" style="margin-top:12px">
            <div class="prompt" id="pronPrompt"></div>
            <div class="controls">
              <button class="primary" id="pronListenSlow">🔊 Listen (slow)</button>
              <button class="primary" id="pronListenNormal">🔊 Listen (normal)</button>
              <button id="pronNext">🎲 New sentence</button>
              <button class="primary" id="pronMic">🎙️ Record (optional)</button>
            </div>
            <div class="box" style="margin-top:12px">
              <h3>Your transcript (if available)</h3>
              <div id="pronTranscript" class="muted">—</div>
            </div>
          </div>
        </div>
      </section>

      <!-- SLIDE 10: Free production writing -->
      <section class="slide" data-slide="10">
        <div class="card">
          <div class="titleRow">
            <h2>10) Free production: write a short story</h2>
            <span class="pill">Writing</span>
          </div>

          <p class="muted">
            Write 5–8 lines. Include:
            <span class="kbd">2× Past Continuous</span>
            <span class="kbd">2× Past Perfect</span>
            and at least one sentence with <span class="kbd">when</span> or <span class="kbd">by the time</span>.
          </p>

          <textarea id="freeWrite" placeholder="Example idea: 'Yesterday at 8 pm I was... By the time I arrived, he had...'"></textarea>

          <div class="controls">
            <button class="primary" id="writeCheck">✅ Quick check</button>
            <button class="ghost" id="writeExample">👀 Show an example answer</button>
            <button class="ghost" id="writeClear">🧹 Clear</button>
          </div>

          <div class="resultLine" id="writeResult"></div>
          <div class="box" id="writeExampleBox" style="display:none; margin-top:12px">
            <h3>Example answer</h3>
            <p>
              Yesterday at 8 pm I <b>was walking</b> home. It <b>was raining</b> and I was tired.
              By the time I reached my street, the supermarket <b>had already closed</b>.
              I realized I <b>had forgotten</b> to buy bread, so I went to a small shop.
              When I entered, the owner smiled and asked how my day had been.
            </p>
            <button class="primary" data-tts="Yesterday at 8 pm I was walking home. It was raining and I was tired. By the time I reached my street, the supermarket had already closed. I realized I had forgotten to buy bread, so I went to a small shop. When I entered, the owner smiled and asked how my day had been.">🔊 Listen</button>
          </div>
        </div>
      </section>

    </div>

    <div class="nav">
      <div class="left">
        <button id="prevBtn">⬅️ Prev</button>
        <button class="ghost" id="restartBtn">🔁 Restart</button>
      </div>
      <div class="slideCount" id="slideCount">Slide 1 / 10</div>
      <div class="right">
        <button class="primary" id="nextBtn">Next ➡️</button>
      </div>
    </div>
  </div>

<script>
/* --------------------------
   Helpers
-------------------------- */
const $ = (sel, root=document) => root.querySelector(sel);
const $$ = (sel, root=document) => Array.from(root.querySelectorAll(sel));

function shuffle(arr){
  const a = arr.slice();
  for(let i=a.length-1; i>0; i--){
    const j = Math.floor(Math.random()*(i+1));
    [a[i], a[j]] = [a[j], a[i]];
  }
  return a;
}

function normalize(s){
  return (s||"")
    .toLowerCase()
    .replace(/[’']/g,"'")
    .replace(/\s+/g," ")
    .trim();
}

let score = 0;
let maxScore = 0;
function setScore(add, maxAdd){
  score += add;
  maxScore += maxAdd;
  $("#score").textContent = score;
  $("#maxScore").textContent = maxScore;
}
function resetScore(){
  score = 0; maxScore = 0;
  $("#score").textContent = "0";
  $("#maxScore").textContent = "0";
}

/* --------------------------
   Slide navigation
-------------------------- */
const slides = $$(".slide");
let idx = 0;

function updateUI(){
  slides.forEach((s,i)=> s.classList.toggle("active", i===idx));
  $("#slideCount").textContent = `Slide ${idx+1} / ${slides.length}`;
  $("#prevBtn").disabled = idx===0;
  $("#nextBtn").disabled = idx===slides.length-1;

  const pct = ((idx+1)/slides.length)*100;
  $("#bar").style.width = pct + "%";
}
$("#prevBtn").addEventListener("click", ()=>{ if(idx>0){ idx--; updateUI(); }});
$("#nextBtn").addEventListener("click", ()=>{ if(idx<slides.length-1){ idx++; updateUI(); }});
$("#restartBtn").addEventListener("click", ()=>{
  idx = 0;
  updateUI();
  resetAllActivities(true);
});

/* --------------------------
   TTS (SpeechSynthesis)
-------------------------- */
let ttsReady = !!window.speechSynthesis;
$("#ttsStatus").textContent = ttsReady ? "🔊 TTS: ready" : "🔊 TTS: not available";

function speak(text, rate=1){
  if(!ttsReady) return;
  window.speechSynthesis.cancel();
  const u = new SpeechSynthesisUtterance(text);
  u.rate = rate;
  u.lang = "en-GB";
  window.speechSynthesis.speak(u);
}

document.addEventListener("click", (e)=>{
  const btn = e.target.closest("[data-tts]");
  if(!btn) return;
  speak(btn.getAttribute("data-tts"), 1);
});

/* --------------------------
   Speech recognition (optional)
-------------------------- */
const SpeechRec = window.SpeechRecognition || window.webkitSpeechRecognition;
let recog = null;
let isRecognizing = false;

function initRec(){
  if(!SpeechRec){
    $("#micStatus").textContent = "🎙️ Speech: not available";
    return;
  }
  $("#micStatus").textContent = "🎙️ Speech: available";
  recog = new SpeechRec();
  recog.lang = "en-GB";
  recog.interimResults = false;
  recog.maxAlternatives = 1;
  recog.onresult = (event)=>{
    const t = event.results[0][0].transcript;
    if(currentRecTarget) currentRecTarget.textContent = t;
  };
  recog.onend = ()=>{
    isRecognizing = false;
    updateMicButtons();
  };
  recog.onerror = ()=>{
    isRecognizing = false;
    updateMicButtons();
  };
}
initRec();

let currentRecTarget = null;
function startRec(targetEl){
  if(!recog || isRecognizing) return;
  currentRecTarget = targetEl;
  isRecognizing = true;
  updateMicButtons();
  try{ recog.start(); } catch(e){
    isRecognizing = false;
    updateMicButtons();
  }
}
function stopRec(){
  if(!recog || !isRecognizing) return;
  try{ recog.stop(); } catch(e){}
}
function updateMicButtons(){
  const label = isRecognizing ? "⏹ Stop" : "🎙️ Record (optional)";
  ["#speakMic","#pronMic"].forEach(id=>{
    const b = $(id);
    if(b) b.textContent = label;
  });
}

/* --------------------------
   Slide 3: MCQ recognition
-------------------------- */
const mcq1Data = [
  {
    prompt: "At 9 pm last night, I ____ TV.",
    options: ["watched", "was watching", "had watched"],
    correct: 1,
    tts: "At 9 pm last night, I was watching TV."
  },
  {
    prompt: "By the time the meeting started, we ____ the report.",
    options: ["finished", "were finishing", "had finished"],
    correct: 2,
    tts: "By the time the meeting started, we had finished the report."
  },
  {
    prompt: "I ____ dinner when you called.",
    options: ["was cooking", "had cooked", "cooked"],
    correct: 0,
    tts: "I was cooking dinner when you called."
  },
  {
    prompt: "She was angry because he ____ her.",
    options: ["wasn't listening to", "didn't listen to", "hadn't listened to"],
    correct: 2,
    tts: "She was angry because he hadn't listened to her."
  },
];

function renderMCQ(containerId, data, key){
  const root = $(containerId);
  root.innerHTML = "";
  data.forEach((q, qi)=>{
    const wrap = document.createElement("div");
    wrap.className = "q";
    wrap.innerHTML = `
      <div class="prompt">${qi+1}. ${q.prompt}</div>
      <div class="options"></div>
      <div class="controls">
        <button class="primary" data-tts="${q.tts.replace(/"/g,'&quot;')}">🔊 Listen (answer)</button>
      </div>
      <div class="resultLine" id="${key}_res_${qi}"></div>
    `;
    const opts = $(".options", wrap);
    q.options.forEach((opt, oi)=>{
      const b = document.createElement("button");
      b.className = "optBtn";
      b.textContent = opt;
      b.addEventListener("click", ()=>{
        if(b.dataset.locked === "1") return;
        // lock all
        $$(".optBtn", wrap).forEach(x=>x.dataset.locked="1");

        maxScore += 1; $("#maxScore").textContent = maxScore;
        const res = $(`#${key}_res_${qi}`);
        if(oi === q.correct){
          b.classList.add("correct");
          score += 1; $("#score").textContent = score;
          res.innerHTML = `<span class="ok">Correct ✅</span>`;
        } else {
          b.classList.add("wrong");
          $$(".optBtn", wrap)[q.correct].classList.add("correct");
          res.innerHTML = `<span class="bad">Not quite.</span> Correct: <b>${q.options[q.correct]}</b>`;
        }
      });
      opts.appendChild(b);
    });
    root.appendChild(wrap);
  });
}

renderMCQ("#mcq1", mcq1Data, "mcq1");

$("#mcq1Reset").addEventListener("click", ()=>{
  // Re-render but do not erase global score (teacher may want cumulative). We'll reset *this block* scoring by page reload style:
  // Best compromise: simply re-render and keep score as-is.
  renderMCQ("#mcq1", mcq1Data, "mcq1");
});

/* --------------------------
   Slide 4: Timeline meaning MCQ
-------------------------- */
const mcq2Data = [
  {
    prompt: "When I arrived, they had started dinner.",
    options: [
      "They started dinner after I arrived.",
      "They started dinner before I arrived."
    ],
    correct: 1,
    tts: "When I arrived, they had started dinner."
  },
  {
    prompt: "I was working when the email arrived.",
    options: [
      "The email arrived during my work.",
      "I started working after the email arrived."
    ],
    correct: 0,
    tts: "I was working when the email arrived."
  },
  {
    prompt: "By the time she called, I had gone to bed.",
    options: [
      "I went to bed before she called.",
      "I went to bed after she called."
    ],
    correct: 0,
    tts: "By the time she called, I had gone to bed."
  },
  {
    prompt: "While we were driving, it started to snow.",
    options: [
      "Snow started during the drive.",
      "Snow started before the drive."
    ],
    correct: 0,
    tts: "While we were driving, it started to snow."
  }
];

renderMCQ("#mcq2", mcq2Data, "mcq2");
$("#mcq2Reset").addEventListener("click", ()=> renderMCQ("#mcq2", mcq2Data, "mcq2"));

/* --------------------------
   Slide 5: Word bank gap fill (dynamic)
-------------------------- */
const bankGap = {
  // blanks are [[1]], [[2]]...
  textHTML: `
    <p>1) At 7 pm, I <span class="kbd blank" data-blank="1">[_____]</span> (work) when my friend <b>called</b>.</p>
    <p>2) By the time we arrived, the concert <span class="kbd blank" data-blank="2">[_____]</span> (start).</p>
    <p>3) She <span class="kbd blank" data-blank="3">[_____]</span> (study) all evening, so she was exhausted.</p>
    <p>4) We <span class="kbd blank" data-blank="4">[_____]</span> (have) dinner when the lights <b>went</b> out.</p>
  `,
  answers: {
    1: "was working",
    2: "had started",
    3: "had been studying",
    4: "were having"
  },
  bank: ["was working","were having","had started","had been studying"]
};

let selectedChip = null;
let blankState = {}; // blankId -> value
function setupBankGap(){
  selectedChip = null;
  blankState = {};
  $("#bankResult").textContent = "";

  $("#bankGapText").innerHTML = bankGap.textHTML;
  const blanks = $$(".blank", $("#bankGapText"));

  blanks.forEach(b=>{
    b.style.cursor = "pointer";
    b.addEventListener("click", ()=>{
      if(!selectedChip) return;
      const bid = b.dataset.blank;
      if(blankState[bid]) return; // no overwrite to keep it simple
      blankState[bid] = selectedChip.textContent;
      b.textContent = selectedChip.textContent;
      selectedChip.classList.add("used");
      selectedChip.dataset.used = "1";
      selectedChip = null;
      $$(".chip", $("#bankChips")).forEach(c=>c.style.outline="none");
    });
  });

  const chipsWrap = $("#bankChips");
  chipsWrap.innerHTML = "";
  shuffle(bankGap.bank).forEach(word=>{
    const c = document.createElement("div");
    c.className = "chip";
    c.textContent = word;
    c.addEventListener("click", ()=>{
      if(c.dataset.used==="1") return;
      selectedChip = c;
      $$(".chip", chipsWrap).forEach(x=>x.style.outline="none");
      c.style.outline = "2px solid rgba(100,212,4,.55)";
    });
    chipsWrap.appendChild(c);
  });
}
setupBankGap();

$("#bankReset").addEventListener("click", setupBankGap);

$("#bankCheck").addEventListener("click", ()=>{
  const total = Object.keys(bankGap.answers).length;
  let correct = 0;
  for(const k of Object.keys(bankGap.answers)){
    if(normalize(blankState[k]) === normalize(bankGap.answers[k])) correct++;
  }
  maxScore += total; $("#maxScore").textContent = maxScore;
  score += correct; $("#score").textContent = score;

  if(correct === total){
    $("#bankResult").innerHTML = `<span class="ok">Perfect ✅ (${correct}/${total})</span>`;
  } else {
    $("#bankResult").innerHTML = `<span class="bad">Not yet.</span> You got ${correct}/${total}. (Tip: check <b>was/were + ing</b> vs <b>had + pp</b>.)`;
  }
});

/* --------------------------
   Slide 6: Typed gaps (harder)
-------------------------- */
const typedGapData = [
  { sentence: "By the time I got to the station, the train ____ (leave).", answer: "had left" },
  { sentence: "I ____ (walk) home when it started to rain.", answer: "was walking" },
  { sentence: "She was nervous because she ____ (forget) her notes.", answer: "had forgotten" },
  { sentence: "We ____ (talk) when the teacher entered.", answer: "were talking" },
  { sentence: "They ____ (finish) the project before the deadline.", answer: "had finished" },
];

function renderTypedGaps(){
  const root = $("#typedGap");
  root.innerHTML = "";
  typedGapData.forEach((it, i)=>{
    const wrap = document.createElement("div");
    wrap.className = "q";
    wrap.innerHTML = `
      <div class="prompt">${i+1}. ${it.sentence}</div>
      <input type="text" data-ans="${it.answer}" placeholder="Type your answer (e.g., was walking / had left)" />
    `;
    root.appendChild(wrap);
  });
  $("#typedResult").textContent = "";
}
renderTypedGaps();

$("#typedReset").addEventListener("click", renderTypedGaps);

$("#typedReveal").addEventListener("click", ()=>{
  $$("#typedGap input").forEach(inp=>{
    inp.value = inp.dataset.ans;
  });
  $("#typedResult").innerHTML = `<span class="muted">Answers revealed.</span>`;
});

$("#typedCheck").addEventListener("click", ()=>{
  const inputs = $$("#typedGap input");
  let correct = 0;
  inputs.forEach(inp=>{
    const ok = normalize(inp.value) === normalize(inp.dataset.ans);
    inp.style.borderColor = ok ? "rgba(61,220,132,.55)" : "rgba(255,90,90,.55)";
    if(ok) correct++;
  });
  maxScore += inputs.length; $("#maxScore").textContent = maxScore;
  score += correct; $("#score").textContent = score;

  $("#typedResult").innerHTML = correct === inputs.length
    ? `<span class="ok">Perfect ✅ (${correct}/${inputs.length})</span>`
    : `<span class="bad">Score:</span> ${correct}/${inputs.length}. Tip: Past Continuous = <b>was/were + -ing</b>. Past Perfect = <b>had + past participle</b>.`;
});

/* --------------------------
   Slide 7: Listening choose
-------------------------- */
const listenSentences = [
  "I was studying when you messaged me.",
  "By the time we arrived, the movie had already started.",
  "She was cooking while he was setting the table.",
  "He was upset because he had missed the bus.",
  "We were having lunch when the alarm went off.",
  "By the time I called, they had finished the meeting."
];

let listenCurrent = null;
function newListeningRound(){
  listenCurrent = listenSentences[Math.floor(Math.random()*listenSentences.length)];
  $("#listenResult").textContent = "";
  const wrongs = shuffle(listenSentences.filter(s=>s!==listenCurrent)).slice(0,3);
  const options = shuffle([listenCurrent, ...wrongs]);
  const optsWrap = $("#listenOptions");
  optsWrap.innerHTML = "";
  options.forEach(opt=>{
    const b = document.createElement("button");
    b.className = "optBtn";
    b.textContent = opt;
    b.addEventListener("click", ()=>{
      if(b.dataset.locked==="1") return;
      $$("#listenOptions .optBtn").forEach(x=>x.dataset.locked="1");

      maxScore += 1; $("#maxScore").textContent = maxScore;
      if(opt === listenCurrent){
        b.classList.add("correct");
        score += 1; $("#score").textContent = score;
        $("#listenResult").innerHTML = `<span class="ok">Correct ✅</span>`;
      } else {
        b.classList.add("wrong");
        const correctBtn = $$("#listenOptions .optBtn").find(x=>x.textContent===listenCurrent);
        if(correctBtn) correctBtn.classList.add("correct");
        $("#listenResult").innerHTML = `<span class="bad">Not quite.</span> Correct was: <b>${listenCurrent}</b>`;
      }
    });
    optsWrap.appendChild(b);
  });
}
newListeningRound();

$("#listenPlay").addEventListener("click", ()=> speak(listenCurrent, 1));
$("#listenNew").addEventListener("click", newListeningRound);

/* --------------------------
   Slide 8: Speaking prompts (guided)
-------------------------- */
const speakPrompts = shuffle([
  "At 9 pm last night, I was ________ (say a real activity).",
  "I was ________ when my phone rang.",
  "By the time I arrived, my friend had already ________.",
  "I was tired because I had ________ all day.",
  "We were ________ when something surprising happened."
]);

let speakIdx = 0;
function setSpeakPrompt(){
  const p = speakPrompts[speakIdx % speakPrompts.length];
  $("#speakPrompt").textContent = p;
  $("#speakTranscript").textContent = "—";
}
setSpeakPrompt();

$("#speakTTS").addEventListener("click", ()=> speak($("#speakPrompt").textContent.replace("________", "doing something"), 1));
$("#speakNext").addEventListener("click", ()=>{ speakIdx++; setSpeakPrompt(); });

$("#speakMic").addEventListener("click", ()=>{
  if(!SpeechRec) return;
  if(isRecognizing){ stopRec(); return; }
  startRec($("#speakTranscript"));
});

/* --------------------------
   Slide 9: Pronunciation sentences
-------------------------- */
const pronSentences = [
  "I was reading when the lights went out.",
  "By the time we got there, the shop had closed.",
  "She was smiling because she had passed the exam.",
  "We were talking when the teacher arrived.",
  "He had finished his work before he went out."
];
let pronCurrent = pronSentences[Math.floor(Math.random()*pronSentences.length)];
function setPron(){
  $("#pronPrompt").innerHTML = `Say this clearly: <b>${pronCurrent}</b>`;
  $("#pronTranscript").textContent = "—";
}
setPron();

$("#pronListenSlow").addEventListener("click", ()=> speak(pronCurrent, 0.85));
$("#pronListenNormal").addEventListener("click", ()=> speak(pronCurrent, 1));
$("#pronNext").addEventListener("click", ()=>{
  pronCurrent = pronSentences[Math.floor(Math.random()*pronSentences.length)];
  setPron();
});
$("#pronMic").addEventListener("click", ()=>{
  if(!SpeechRec) return;
  if(isRecognizing){ stopRec(); return; }
  startRec($("#pronTranscript"));
});

/* --------------------------
   Slide 10: Writing quick check
-------------------------- */
$("#writeExample").addEventListener("click", ()=>{
  const box = $("#writeExampleBox");
  box.style.display = (box.style.display === "none") ? "block" : "none";
});

$("#writeClear").addEventListener("click", ()=>{
  $("#freeWrite").value = "";
  $("#writeResult").textContent = "";
});

$("#writeCheck").addEventListener("click", ()=>{
  const t = $("#freeWrite").value;
  const pc = (t.match(/\b(was|were)\s+\w+ing\b/gi) || []).length;
  const pp = (t.match(/\bhad\s+\w+(ed|en)\b/gi) || []).length + (t.match(/\bhad\s+(gone|done|seen|been|made|taken|written|eaten|given|known|found|left|felt|built|bought|told|put|cut|read)\b/gi) || []).length;

  const hasLinker = /\b(by the time|when|before|after)\b/i.test(t);

  maxScore += 1; $("#maxScore").textContent = maxScore;
  let ok = (pc >= 2 && pp >= 2 && hasLinker && t.trim().length > 30);
  if(ok){
    score += 1; $("#score").textContent = score;
    $("#writeResult").innerHTML = `<span class="ok">Nice ✅</span> I can see Past Continuous (${pc}) and Past Perfect (${pp}) + a linker word.`;
  } else {
    $("#writeResult").innerHTML =
      `<span class="bad">Almost.</span> Try to include <b>2× Past Continuous</b> (was/were + -ing), <b>2× Past Perfect</b> (had + past participle), and one of: <b>when / by the time / before</b>. Current count: PC=${pc}, PP=${pp}.`;
  }
});

/* --------------------------
   Global reset (for restart)
-------------------------- */
function resetAllActivities(hard=false){
  // Activities
  renderMCQ("#mcq1", mcq1Data, "mcq1");
  renderMCQ("#mcq2", mcq2Data, "mcq2");
  setupBankGap();
  renderTypedGaps();
  newListeningRound();
  speakIdx = 0; setSpeakPrompt();
  pronCurrent = pronSentences[Math.floor(Math.random()*pronSentences.length)];
  setPron();
  $("#freeWrite").value = "";
  $("#writeResult").textContent = "";
  $("#writeExampleBox").style.display = "none";

  if(hard) resetScore();
}

/* --------------------------
   Init
-------------------------- */
updateUI();
</script>
</body>
</html>

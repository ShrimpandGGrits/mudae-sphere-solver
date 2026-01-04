<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>5×5 Solver Suite (Right-Click + Touch + Undo)</title>
  <style>
    :root { font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif; }
    body { margin: 0; padding: 16px; background: #0b0f14; color: #e8eef7; }
    h1 { margin: 0 0 12px; font-size: 20px; }

    .tabs { display:flex; gap:10px; flex-wrap:wrap; margin: 8px 0 14px; }
    .tabBtn {
      background:#121a24; border:1px solid #233044; color:#e8eef7;
      padding:8px 12px; border-radius: 12px; cursor:pointer;
    }
    .tabBtn.active { border-color:#4a6796; box-shadow: 0 0 0 2px rgba(74,103,150,0.25) inset; }

    .wrap {
      display: grid;
      grid-template-columns: 1fr 520px; /* board left, info right */
      grid-template-areas: "board info";
      gap: 16px;
      align-items: start;
    }
    
    #boardCard { grid-area: board; }
    #infoCard  { grid-area: info; }
    
    @media (max-width: 1050px) {
      .wrap {
        grid-template-columns: 1fr;
        grid-template-areas:
          "board"
          "info"; /* board on top, info below on mobile */
      }
    }

    .card {
      background: #121a24;
      border: 1px solid #233044;
      border-radius: 12px;
      padding: 12px;
      box-shadow: 0 6px 18px rgba(0,0,0,0.25);
    }

    .grid { display:grid; grid-template-columns: repeat(5, 58px); gap:8px; justify-content:start; user-select:none; }
    .cell {
      width:58px; height:58px;
      border-radius:10px;
      border:1px solid #2b3b55;
      background:#0f1621;
      color:#dbe6f7;
      display:grid;
      place-items:center;
      cursor:pointer;
      position:relative;
      transition: transform .06s ease, border-color .12s ease, box-shadow .12s ease;
      font-weight:650;
      touch-action: manipulation; /* helps long-press */
    }
    .cell:hover { transform: translateY(-1px); border-color:#4a6796; }
    .cell:active { transform: translateY(0px); }

    .badge {
      position:absolute; top:6px; right:6px;
      font-size:10px; padding:2px 6px; border-radius:999px;
      border:1px solid rgba(255,255,255,0.12);
      background: rgba(255,255,255,0.06);
      color: rgba(255,255,255,0.85);
      max-width: 48px; overflow:hidden; text-overflow:ellipsis; white-space:nowrap;
    }
    .revealLetter {
      position:absolute; left:8px; top:8px;
      font-size:18px; font-weight:900; line-height:1; opacity:0.95;
    }

    /* Highlights */
    .candidate { box-shadow: 0 0 0 2px rgba(0,200,255,0.25) inset; } /* blue outline */
    .best      { box-shadow: 0 0 0 3px rgba(255,230,120,0.35) inset, 0 0 16px rgba(255,230,120,0.10); } /* gold outline */
    .picked    { opacity: 0.90; }
    .redKnown  { box-shadow: 0 0 0 3px rgba(255,77,77,0.35) inset, 0 0 18px rgba(255,77,77,0.10); }

    /* Game1 revealed fills */
    .reveal-BLUE   { background: rgba(61, 116, 255, 0.22); border-color: rgba(61, 116, 255, 0.55); }
    .reveal-TEAL   { background: rgba(77, 230, 255, 0.18); border-color: rgba(77, 230, 255, 0.55); }
    .reveal-GREEN  { background: rgba(77, 255, 136, 0.16); border-color: rgba(77, 255, 136, 0.55); }
    .reveal-YELLOW { background: rgba(255, 210, 77, 0.16); border-color: rgba(255, 210, 77, 0.60); }
    .reveal-ORANGE { background: rgba(255, 154, 61, 0.16); border-color: rgba(255, 154, 61, 0.60); }
    .reveal-RED    { background: rgba(255, 77, 77, 0.18); border-color: rgba(255, 77, 77, 0.65); }

    /* Game2 revealed fills */
    .reveal-PURPLE { background: rgba(166, 93, 255, 0.22); border-color: rgba(166, 93, 255, 0.65); }
    .reveal-0 { background: rgba(61, 116, 255, 0.16); border-color: rgba(61, 116, 255, 0.45); }
    .reveal-1 { background: rgba(77, 230, 255, 0.14); border-color: rgba(77, 230, 255, 0.45); }
    .reveal-2 { background: rgba(77, 255, 136, 0.12); border-color: rgba(77, 255, 136, 0.45); }
    .reveal-3 { background: rgba(255, 210, 77, 0.12); border-color: rgba(255, 210, 77, 0.52); }
    .reveal-4 { background: rgba(255, 154, 61, 0.12); border-color: rgba(255, 154, 61, 0.52); }

    .row { display:flex; gap:10px; flex-wrap:wrap; align-items:center; }
    .row > * { margin:4px 0; }
    button.ui {
      background:#1a2740; border:1px solid #2b3b55; color:#e8eef7;
      padding:8px 10px; border-radius: 10px; cursor:pointer;
    }
    button.ui:hover { border-color:#4a6796; }
    button.ui:disabled { opacity:0.5; cursor:not-allowed; }

    .small { font-size:12px; color: rgba(232,238,247,0.78); line-height:1.35; }
    .mono { font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", monospace; }
    .hr { height:1px; background:#233044; margin:10px 0; }

    /* Custom context menu */
    #ctxMenu {
      position: fixed;
      z-index: 9999;
      background: #0f1621;
      border: 1px solid #2b3b55;
      border-radius: 12px;
      padding: 6px;
      min-width: 220px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.45);
      display:none;
    }
    #ctxMenu .title {
      font-size: 11px;
      opacity: 0.85;
      padding: 6px 10px 4px;
    }
    #ctxMenu button {
      width: 100%;
      text-align: left;
      background: transparent;
      border: 0;
      color: #e8eef7;
      padding: 8px 10px;
      border-radius: 10px;
      cursor: pointer;
    }
    #ctxMenu button:hover { background: rgba(255,255,255,0.06); }
    #ctxMenu .sep { height:1px; background:#233044; margin:6px 0; }
    #ctxMenu button.danger { color: #ff9d9d; }
  </style>
</head>
<body>
  <h1>Ourasphere Minigame Solver Suite</h1>

  <div class="tabs">
    <button class="tabBtn active" id="tabGame1">OuraChest Solver</button>
    <button class="tabBtn" id="tabGame2">OuraQuest Solver</button>
  </div>

  <div class="wrap">
    <div class="card" id="infoCard">
      <div id="panelGame1">
        <div class="small">
          <b>Ourachest Minigame:</b> You pick 5 squares.<br/>
		  <b>Primary Goal:</b> find <b>RED</b>.<br/>
		  <b>Secondary goal:</b> maximize points.<br/>
          <b>Points:</b> B=1, T=2, G=3, Y=4, O=5. (Red = 0 pts).<br/>
          <b>Input:</b> Click or Press a square → choose reveal.
        </div>

        <div class="hr"></div>

        <div class="row">
          <button class="ui" id="g1Undo" disabled>Undo last</button>
          <button class="ui" id="g1Reset">Reset</button>
        </div>

        <div class="hr"></div>

        <div class="small">
          <b>Status</b>
          <ul>
            <li>Moves logged: <b id="g1Moves">0</b> / 5</li>
            <li>Red found: <b id="g1RedFound">No</b></li>
            <li>Total points: <b id="g1Pts">0</b></li>
            <li>Remaining red candidates: <b id="g1Cand">—</b></li>
          </ul>
        </div>

        <div class="hr"></div>

        <div class="small">
          <b>Recommendations</b>
          <div id="g1Best" class="mono" style="margin-top:6px; white-space: pre-wrap;"></div>
        </div>

        <div class="hr"></div>

        <div class="small">
          <b>Highlight legend</b><br/>
          • <b>Blue outline</b>: possible RED locations (before red found).<br/>
          • <b>Gold outline</b>: best next guess(es) (ties shown).<br/>
          • <b>Red glow</b>: confirmed RED.
        </div>
      </div>

      <div id="panelGame2" style="display:none;">
        <div class="small">
          <b>Ouraquest Minigame:</b> 4 purples total.<br/>
		  <b>Goal:</b> find 3 purples in 7 paid picks.<br/>
          <b>Rules</b> Clicking PURPLE is free. Number reveals (0–4 adj purples) cost 1 paid pick and score points: k→(k+1).
          After 3 purples, the last becomes <b>RED</b>; clicking RED costs 1 paid pick; then farm points.
          <br/><b>Input:</b> Click or press a square → choose reveal.
        </div>

        <div class="hr"></div>

        <div class="row">
          <button class="ui" id="g2Undo" disabled>Undo last</button>
          <button class="ui" id="g2Reset">Reset</button>
        </div>

        <div class="hr"></div>

        <div class="small">
          <b>Status</b>
          <ul>
            <li>Paid used: <b id="g2Paid">0</b> / 7</li>
            <li>Purples found: <b id="g2Purp">0</b> / 3</li>
            <li>Red clicked: <b id="g2Red">No</b></li>
            <li>Total points: <b id="g2Pts">0</b></li>
            <li>Consistent boards remaining (phase 1): <b id="g2Hyps">—</b></li>
          </ul>
        </div>

        <div class="hr"></div>

        <div class="small">
          <b>Recommendations</b>
          <div id="g2Best" class="mono" style="margin-top:6px; white-space: pre-wrap;"></div>
        </div>

        <div class="hr"></div>

        <div class="small">
          <b>Highlight legend</b><br/>
          • <b>Blue outline</b>: top tier (highest P(purple) in phase 1; best points tier in phase 2).<br/>
          • <b>Gold outline</b>: best next guess(es) (ties shown).<br/>
        </div>
      </div>
    </div>

    <div class="card" id="boardCard">
      <div class="grid" id="grid"></div>
    </div>
  </div>

  <!-- Custom context menu -->
  <div id="ctxMenu">
    <div class="title" id="ctxTitle">Square</div>
    <div class="sep"></div>
    <div id="ctxButtons"></div>
  </div>

<script>
(() => {
  const N = 5;
  const gridEl = document.getElementById("grid");
  const ctxMenu = document.getElementById("ctxMenu");
  const ctxTitle = document.getElementById("ctxTitle");
  const ctxButtons = document.getElementById("ctxButtons");

  // Tabs
  const tabGame1 = document.getElementById("tabGame1");
  const tabGame2 = document.getElementById("tabGame2");
  const panelGame1 = document.getElementById("panelGame1");
  const panelGame2 = document.getElementById("panelGame2");

  let activeGame = "g1"; // "g1" or "g2"

  function setActive(which) {
    activeGame = which;
    const g1 = which === "g1";
    tabGame1.classList.toggle("active", g1);
    tabGame2.classList.toggle("active", !g1);
    panelGame1.style.display = g1 ? "" : "none";
    panelGame2.style.display = g1 ? "none" : "";
    updateAll();
  }

  tabGame1.addEventListener("click", () => setActive("g1"));
  tabGame2.addEventListener("click", () => setActive("g2"));

  // Helpers
  function idx(r,c){ return r*N+c; }
  function rc(i){ return [Math.floor(i/N), i%N]; }
  function fmtSquare(i){ const [r,c]=rc(i); return `(${r+1},${c+1})`; }
  function inBounds(r,c){ return r>=0 && r<N && c>=0 && c<N; }
  function adj8(i){
    const [r,c]=rc(i);
    const out=[];
    for (let dr=-1; dr<=1; dr++){
      for (let dc=-1; dc<=1; dc++){
        if (dr===0 && dc===0) continue;
        const rr=r+dr, cc=c+dc;
        if (inBounds(rr,cc)) out.push(idx(rr,cc));
      }
    }
    return out;
  }

  // Build grid cells (shared)
  const cells = [];
  for (let i=0; i<N*N; i++) {
    const [r,c] = rc(i);
    const el = document.createElement("div");
    el.className = "cell";
    el.textContent = `${r+1},${c+1}`;

    const letter = document.createElement("div");
    letter.className = "revealLetter";
    letter.textContent = "";
    el.appendChild(letter);

    const badge = document.createElement("div");
    badge.className = "badge";
    badge.textContent = "";
    el.appendChild(badge);

    gridEl.appendChild(el);
    cells.push(el);
  }

  // ---------- Context menu (right click + touch long press) ----------
  let ctxTarget = null;
  let menuJustOpened = false;

  function hideMenu() {
    ctxMenu.style.display = "none";
    ctxTarget = null;
    ctxButtons.innerHTML = "";
  }

  function showMenu(x, y, targetIndex) {
    menuJustOpened = true;
    setTimeout(() => { menuJustOpened = false; }, 0);
    ctxTarget = targetIndex;
    ctxTitle.textContent = `Square ${fmtSquare(targetIndex)}`;

    // Build buttons based on active game & revealed state
    ctxButtons.innerHTML = "";
    const game = activeGame === "g1" ? Game1 : Game2;

    const isRevealed = game.isRevealed(targetIndex);

    // Always offer Undo Last (global)
    addMenuButton("Undo last reveal", "__UNDO_LAST__", { danger: true });

    // If the square itself is revealed, offer Clear this square
    if (isRevealed) addMenuButton("Clear this square", "__CLEAR__", { danger: true });

    addMenuSep();

    // Offer reveal options ONLY if not revealed
    if (!isRevealed) {
      for (const opt of game.menuOptions()) {
        addMenuButton(opt.label, opt.value, { danger: false });
      }
    } else {
      addMenuButton("(Already revealed)", "__NOOP__", { disabled: true });
    }

    ctxMenu.style.display = "block";

    // clamp inside viewport
    const pad = 8;
    const rect = ctxMenu.getBoundingClientRect();
    let left = x, top = y;
    left = Math.max(pad, Math.min(left, window.innerWidth - rect.width - pad));
    top  = Math.max(pad, Math.min(top,  window.innerHeight - rect.height - pad));
    ctxMenu.style.left = `${left}px`;
    ctxMenu.style.top  = `${top}px`;
  }

  function addMenuButton(label, value, { danger=false, disabled=false } = {}) {
    const b = document.createElement("button");
    b.textContent = label;
    b.setAttribute("data-val", value);
    if (danger) b.classList.add("danger");
    if (disabled) { b.disabled = true; b.style.opacity = "0.65"; }
    ctxButtons.appendChild(b);
  }

  function addMenuSep() {
    const sep = document.createElement("div");
    sep.className = "sep";
    ctxButtons.appendChild(sep);
  }

  // Click handler for menu
  ctxMenu.addEventListener("click", (e) => {
    const btn = e.target.closest("button[data-val]");
    if (!btn) return;
    const val = btn.getAttribute("data-val");
    const target = ctxTarget;
    hideMenu();

    const game = activeGame === "g1" ? Game1 : Game2;
    if (val === "__UNDO_LAST__") game.undoLast();
    else if (val === "__CLEAR__") game.clearSquare(target);
    else if (val === "__NOOP__") return;
    else game.applyReveal(target, val);

    updateAll();
  });

  // Hide menu on outside click / scroll / resize / escape
  document.addEventListener("click", (e) => {
    if (ctxMenu.style.display === "none") return;
    if (menuJustOpened) return; // <-- ignore the same click that opened it
    if (!ctxMenu.contains(e.target)) hideMenu();
  });
  document.addEventListener("scroll", hideMenu, true);
  window.addEventListener("resize", hideMenu);
  document.addEventListener("keydown", (e) => { if (e.key === "Escape") hideMenu(); });

  // Attach right click + touch long-press to each cell
  const LONG_PRESS_MS = 520;
  const MOVE_TOL = 10;

  for (let i=0;i<N*N;i++){
    const el = cells[i];

    // Right click
    el.addEventListener("contextmenu", (ev) => {
      ev.preventDefault(); // disable browser menu
    });

    // Touch long press (pointer events)
    let pressTimer = null;
    let startX = 0, startY = 0, moved = false;

    el.addEventListener("pointerdown", (ev) => {
      if (ev.pointerType !== "touch") return;
      moved = false;
      startX = ev.clientX; startY = ev.clientY;

      pressTimer = setTimeout(() => {
        if (!moved) showMenu(ev.clientX, ev.clientY, i);
      }, LONG_PRESS_MS);
    });

    el.addEventListener("pointermove", (ev) => {
      if (ev.pointerType !== "touch") return;
      const dx = ev.clientX - startX;
      const dy = ev.clientY - startY;
      if (Math.hypot(dx,dy) > MOVE_TOL) moved = true;
      if (moved && pressTimer) { clearTimeout(pressTimer); pressTimer = null; }
    });

    el.addEventListener("pointerup", (ev) => {
      if (ev.pointerType !== "touch") return;
      if (pressTimer) { clearTimeout(pressTimer); pressTimer = null; }
    });

    el.addEventListener("pointercancel", (ev) => {
      if (pressTimer) { clearTimeout(pressTimer); pressTimer = null; }
    });
  }

  // ---------- OuraChest ----------
  const Game1 = (() => {
    const PTS = { BLUE:1, TEAL:2, GREEN:3, YELLOW:4, ORANGE:5, RED:0 };
    const center = idx(2,2);
    const COLORS = ["RED","ORANGE","YELLOW","GREEN","TEAL","BLUE"];

    // observations list: {s, color}
    let observations = [];
    let picked = new Set();

    function reset() { observations = []; picked = new Set(); }
    function undoLast() {
      if (!observations.length) return;
      observations.pop();
      picked = new Set(observations.map(o => o.s));
    }
    function clearSquare(i) {
      const before = observations.length;
      observations = observations.filter(o => o.s !== i);
      if (observations.length !== before) picked = new Set(observations.map(o => o.s));
    }

    function isRevealed(i){ return picked.has(i); }

    // Geometry
    function cheb(a,b){
      const [ar,ac]=rc(a), [br,bc]=rc(b);
      return Math.max(Math.abs(ar-br), Math.abs(ac-bc));
    }
    function sameRow(a,b){ return rc(a)[0]===rc(b)[0]; }
    function sameCol(a,b){ return rc(a)[1]===rc(b)[1]; }
    function sameDiag(a,b){
      const [ar,ac]=rc(a), [br,bc]=rc(b);
      return Math.abs(ar-br)===Math.abs(ac-bc);
    }
    function satisfies(r,s,color){
      if (r === center) return false;
      switch(color){
        case "RED": return r === s;
        case "ORANGE": return r !== s && cheb(r,s) === 1; // 8-way adjacent
        case "YELLOW": return r !== s && sameDiag(r,s);
        case "GREEN": return r !== s && (sameRow(r,s) || sameCol(r,s));
        case "TEAL": return r !== s && (sameRow(r,s) || sameCol(r,s) || sameDiag(r,s));
        case "BLUE": return r !== s && !(sameRow(r,s) || sameCol(r,s) || sameDiag(r,s));
        default: return false;
      }
    }

    function initialCandidates(){
      const out=[];
      for (let r=0;r<N;r++) for (let c=0;c<N;c++){
        const i = idx(r,c);
        if (i !== center) out.push(i);
      }
      return out;
    }
    function computeCandidates(){
      let cand = initialCandidates();
      for (const o of observations) cand = cand.filter(r => satisfies(r,o.s,o.color));
      return cand;
    }
    function getKnownRed(){
      for (let k=observations.length-1;k>=0;k--){
        if (observations[k].color === "RED") return observations[k].s;
      }
      return null;
    }

    // Points modeling under ambiguity: pick midpoint of possible applicable colors
    function applicableColorsGivenRed(r,s){
      if (r===s) return ["RED"];
      const set = new Set();
      const adjacent = (cheb(r,s)===1);
      const diag = sameDiag(r,s);
      const rowcol = sameRow(r,s) || sameCol(r,s);
      const line = rowcol || diag;
      if (adjacent) set.add("ORANGE");
      if (diag) set.add("YELLOW");
      if (rowcol) set.add("GREEN");
      if (line) set.add("TEAL");
      if (!line) set.add("BLUE");
      return [...set];
    }
    function pointRangeForSquareGivenRed(r,s){
      const colors = applicableColorsGivenRed(r,s);
      let min=Infinity,max=-Infinity;
      for (const c of colors){
        min = Math.min(min, PTS[c]);
        max = Math.max(max, PTS[c]);
      }
      return { min, max, mid:(min+max)/2, colors };
    }
    function expectedPointRangeOverCandidates(cand,s){
      let minSum=0,maxSum=0,midSum=0;
      for (const r of cand){
        const pr = pointRangeForSquareGivenRed(r,s);
        minSum += pr.min; maxSum += pr.max; midSum += pr.mid;
      }
      const n = cand.length || 1;
      return { min:minSum/n, max:maxSum/n, mid:midSum/n };
    }

    function recommend(){
      const cand = computeCandidates();
      const redKnown = getKnownRed();
      const unpicked = [];
      for (let i=0;i<N*N;i++) if (!picked.has(i)) unpicked.push(i);

      // If there is exactly one possible red location left, recommend clicking it.
      if (redKnown == null && cand.length === 1) {
        const only = cand[0];
        const lines = [];
        if (!picked.has(only)) {
          lines.push(`✅ Red is forced at ${fmtSquare(only)} (only candidate left).`);
          lines.push(`➡ Click it next.`);
          return {
            cand,
            redKnown: null,
            best: [only],
            candSet: new Set(cand),
            bestSet: new Set([only]),
            text: lines.join("\n")
          };
        } else {
          // This *shouldn't* happen in a consistent game, but keep it safe.
          lines.push(`⚠ Red is forced at ${fmtSquare(only)}, but that square is already marked revealed.`);
          lines.push(`Check your inputs (a revealed non-red square can't still be a red candidate).`);
          return {
            cand,
            redKnown: null,
            best: [],
            candSet: new Set(cand),
            bestSet: new Set(),
            text: lines.join("\n")
          };
        }
      }

      if (!cand.length) return { cand, redKnown, best:[], candSet:new Set(), bestSet:new Set(), text:"No candidates — check inputs." };

      // After red known: point farm using known red
      if (redKnown != null) {
        let bestSquares=[], bestMid=-Infinity, bestMin=-Infinity;
        const detail = new Map();
        for (const s of unpicked){
          const pr = pointRangeForSquareGivenRed(redKnown,s);
          detail.set(s,pr);
          if (pr.mid > bestMid || (pr.mid===bestMid && pr.min > bestMin)){
            bestMid = pr.mid; bestMin = pr.min; bestSquares=[s];
          } else if (pr.mid===bestMid && pr.min===bestMin) bestSquares.push(s);
        }
        const lines = [];
        lines.push(`Red is known at ${fmtSquare(redKnown)} — maximizing points.`);
        lines.push(`Best pick(s): ${bestSquares.map(fmtSquare).join(", ")}`);
        for (const s of bestSquares){
          const pr = detail.get(s);
          lines.push(`${fmtSquare(s)} pts≈[${pr.min},${pr.max}] mid=${pr.mid.toFixed(2)} possible:${pr.colors.join("/")}`);
        }
        return { cand, redKnown, best:bestSquares, candSet:new Set(), bestSet:new Set(bestSquares), text: lines.join("\n") };
      }

      // Before red: minimax remaining candidates, tie-break by expected points
      let bestSquares=[], bestWorst=Infinity, bestPtsMid=-Infinity, bestPtsMin=-Infinity;
      const detail = new Map();

      for (const s of unpicked){
        // feasible color outcomes
        const feasible=[];
        for (const color of COLORS){
          let count=0;
          for (const r of cand) if (satisfies(r,s,color)) count++;
          if (count>0) feasible.push({color,count});
        }
        if (!feasible.length) continue;
        const worst = Math.max(...feasible.map(x=>x.count));
        const epr = expectedPointRangeOverCandidates(cand,s);
        detail.set(s,{worst,epr,feasible});

        if (worst < bestWorst){
          bestWorst = worst; bestPtsMid=epr.mid; bestPtsMin=epr.min; bestSquares=[s];
        } else if (worst === bestWorst){
          if (epr.mid > bestPtsMid || (epr.mid===bestPtsMid && epr.min > bestPtsMin)){
            bestPtsMid=epr.mid; bestPtsMin=epr.min; bestSquares=[s];
          } else if (epr.mid===bestPtsMid && epr.min===bestPtsMin){
            bestSquares.push(s);
          }
        }
      }

      const lines = [];
      lines.push(`Best next guess set (Red-first; points tie-break): ${bestSquares.map(fmtSquare).join(", ")}`);
      lines.push(`Remaining red candidates: ${cand.length} (hit chance if guessing candidate: ${(100/cand.length).toFixed(1)}%)`);
      if (bestSquares.length){
        const info = detail.get(bestSquares[0]);
        lines.push(`Primary score (min worst-case remaining candidates) = ${info.worst}`);
        lines.push(`Secondary score (avg pts range) ≈ [${info.epr.min.toFixed(2)}, ${info.epr.max.toFixed(2)}], mid=${info.epr.mid.toFixed(2)}`);
      }
      return { cand, redKnown, best:bestSquares, candSet:new Set(cand), bestSet:new Set(bestSquares), text: lines.join("\n") };
    }

    function applyReveal(i, val){
      // val is one of RED/ORANGE/YELLOW/GREEN/TEAL/BLUE
      if (picked.has(i)) return;
      observations.push({ s:i, color: val });
      picked.add(i);
    }

    function menuOptions(){
      return [
        { label:"Red", value:"RED" },
        { label:"Orange", value:"ORANGE" },
        { label:"Yellow", value:"YELLOW" },
        { label:"Green", value:"GREEN" },
        { label:"Teal", value:"TEAL" },
        { label:"Blue", value:"BLUE" },
      ];
    }

    function pointsTotal(){
      // score revealed squares (excluding red)
      let sum=0;
      for (const o of observations) sum += (PTS[o.color] || 0);
      return sum;
    }

    function movesCount(){ return observations.length; }

    return {
      reset, undoLast, clearSquare, isRevealed,
      applyReveal, menuOptions, recommend,
      pointsTotal, movesCount, getKnownRed
    };
  })();

  // ---------- OuraQuest ----------
  const Game2 = (() => {
    const TOTAL_PURPLE = 4;
    const GOAL_FIND = 3;
    const PAID_LIMIT = 7;
    const POINTS_FOR_K = k => k+1;

    // obs[i] = null OR {type:"PURPLE"} OR {type:"RED"} OR {type:"NUM",k}
    const obs = Array(N*N).fill(null);
    let history = []; // stack of { i, prevObs, paidDelta, purpDelta, ptsDelta }
    let paidUsed = 0;
    let purpFound = 0;
    let ptsTotal = 0;
    let redClicked = false;

    function reset(){
      for (let i=0;i<N*N;i++) obs[i]=null;
      history = [];
      paidUsed = 0; purpFound=0; ptsTotal=0; redClicked=false;
    }

    function isRevealed(i){ return obs[i] != null; }

    function undoLast(){
      const last = history.pop();
      if (!last) return;
      obs[last.i] = last.prevObs;
      paidUsed -= last.paidDelta;
      purpFound -= last.purpDelta;
      ptsTotal -= last.ptsDelta;
      redClicked = obs.some(o => o?.type === "RED");
    }

    function clearSquare(i){
      if (!obs[i]) return;
      // Remove this square's effect by rebuilding from scratch without it (simplest & safe).
      // We'll replay history excluding that square.
      const keep = [];
      for (const h of history) if (h.i !== i) keep.push(h);
      reset();
      for (const step of keep) {
        // step contained deltas; we re-apply using current obs state & value encoded in prevObs?
        // We don't have value stored, so instead: store a "val" on apply in history below.
        // If old history lacks it, we can't reconstruct. We'll instead prevent clearing unless we have val.
      }
      // Instead: do a direct clear by undoing until that square disappears, then reapply remaining snapshots.
      // We'll implement robustly by storing val in history going forward; for now:
      // Fall back to "undo until gone": if it's not last, user should use Undo Last repeatedly.
      // We'll still allow clear if it's the most recent entry.
      // (This is better than silently corrupting state.)
      // So: only clear if last revealed is this square.
      // Implement that:
    }

    function clearSquareSafe(i){
      // only if last history entry matches i
      const last = history[history.length-1];
      if (!last || last.i !== i) return false;
      undoLast();
      return true;
    }

    function applyReveal(i, val){
      if (obs[i]) return;
      let prevObs = obs[i];
      let paidDelta=0, purpDelta=0, ptsDelta=0;

      if (val === "PURPLE"){
        obs[i] = { type:"PURPLE" };
        purpDelta = 1;
      } else if (val === "RED"){
        obs[i] = { type:"RED" };
        paidDelta = 1;
        redClicked = true;
      } else {
        const k = Number(val);
        obs[i] = { type:"NUM", k };
        paidDelta = 1;
        ptsDelta = POINTS_FOR_K(k);
      }

      history.push({ i, prevObs, paidDelta, purpDelta, ptsDelta, val });
      paidUsed += paidDelta;
      purpFound += purpDelta;
      ptsTotal += ptsDelta;
      redClicked = obs.some(o => o?.type === "RED");
    }

    function getPurpleLikeSquares(){
      const out=[];
      for (let i=0;i<N*N;i++){
        if (!obs[i]) continue;
        if (obs[i].type === "PURPLE" || obs[i].type === "RED") out.push(i);
      }
      return out;
    }
    function countAdjPurpleLike(i, purpleSet){
      let k=0;
      for (const a of adj8(i)) if (purpleSet.has(a)) k++;
      return k;
    }

    // Hypothesis enumeration for phase 1 (exact)
    function computeHyps(){
      const knownPurpleLike=[];
      const numbered=[];

      for (let i=0;i<N*N;i++){
        const o = obs[i];
        if (!o) continue;
        if (o.type === "PURPLE" || o.type === "RED") knownPurpleLike.push(i);
        else if (o.type === "NUM") numbered.push({ i, k:o.k });
      }
      if (knownPurpleLike.length > TOTAL_PURPLE) return [];
      const need = TOTAL_PURPLE - knownPurpleLike.length;

      const candidates=[];
      for (let i=0;i<N*N;i++) if (!obs[i]) candidates.push(i);
      if (need < 0 || need > candidates.length) return [];

      const numAdj = numbered.map(o => ({ i:o.i, k:o.k, adj: adj8(o.i) }));
      const chosen=[];
      const results=[];

      function checkPartial(){
        const chosenSet = new Set(chosen);
        const knownSet = new Set(knownPurpleLike);
        for (const {k,adj} of numAdj){
          let fixed=0, possible=0;
          for (const a of adj){
            if (knownSet.has(a) || chosenSet.has(a)) fixed++;
            else if (!obs[a]) possible++;
          }
          if (fixed > k) return false;
          if (fixed + possible < k) return false;
        }
        return true;
      }

      function validFinal(purpleSet){
        for (const {k,adj} of numAdj){
          let cnt=0;
          for (const a of adj) if (purpleSet.has(a)) cnt++;
          if (cnt !== k) return false;
        }
        return true;
      }

      function rec(start,left){
        if (left===0){
          const purpleSet = new Set([...knownPurpleLike, ...chosen]);
          if (validFinal(purpleSet)) results.push(purpleSet);
          return;
        }
        for (let p=start; p<=candidates.length-left; p++){
          chosen.push(candidates[p]);
          if (checkPartial()) rec(p+1,left-1);
          chosen.pop();
        }
      }

      if (need===0){
        const purpleSet = new Set(knownPurpleLike);
        if (validFinal(purpleSet)) return [purpleSet];
        return [];
      }
      rec(0,need);
      return results;
    }

    function purpleProb(hyps){
      const counts = Array(N*N).fill(0);
      for (const h of hyps) for (const i of h) counts[i]++;
      const denom = hyps.length || 1;
      return counts.map(x => x/denom);
    }

    function recommend(){
      // Phase2 (after red clicked): deterministic point farming using known purple-like set
      if (redClicked){
        const purpleSet = new Set(getPurpleLikeSquares());
        const unpicked=[];
        for (let i=0;i<N*N;i++) if (!obs[i]) unpicked.push(i);
        if (!unpicked.length) return { mode:"phase2", best:[], topTier:[], text:"No moves left.", hypsCount:"—", probs:null, bestSet:new Set(), topTierSet:new Set() };

        let bestPts=-Infinity;
        let best=[];
        const detail=new Map();
        for (const s of unpicked){
          const k = countAdjPurpleLike(s, purpleSet);
          const pts = POINTS_FOR_K(k);
          detail.set(s,{k,pts});
          if (pts>bestPts){ bestPts=pts; best=[s]; }
          else if (pts===bestPts) best.push(s);
        }
        const topTier = unpicked.filter(s => detail.get(s).pts===bestPts);
        const lines=[];
        lines.push("Phase 2: Red clicked — maximizing points (deterministic).");
        lines.push(`Best pick(s): ${best.map(fmtSquare).join(", ")} (worth ${bestPts} pts)`);
        for (const s of best){
          const d = detail.get(s);
          lines.push(`${fmtSquare(s)} k=${d.k} → ${d.pts} pts`);
        }
        return { mode:"phase2", best, topTier, text: lines.join("\n"), hypsCount:"—",
                 probs:null, bestSet:new Set(best), topTierSet:new Set(topTier) };
      }

      // Phase1: maximize P(purple), tie-break info, then expected points
      const hyps = computeHyps();
      const hypsCount = hyps.length;
      const unpicked=[];
      for (let i=0;i<N*N;i++) if (!obs[i]) unpicked.push(i);

      if (!hypsCount) return { mode:"error", best:[], topTier:[], text:"No consistent boards — check inputs.", hypsCount:String(hypsCount),
                               probs:null, bestSet:new Set(), topTierSet:new Set() };
      if (!unpicked.length) return { mode:"error", best:[], topTier:[], text:"No moves left.", hypsCount:String(hypsCount),
                                     probs:null, bestSet:new Set(), topTierSet:new Set() };

      const probs = purpleProb(hyps);

      function implied(h,s){
        if (h.has(s)) return "PURPLE";
        let k=0;
        for (const a of adj8(s)) if (h.has(a)) k++;
        return String(k);
      }

      let bestP=-1, bestWorst=Infinity, bestExpPts=-Infinity;
      let best=[];
      const detail = new Map();

      for (const s of unpicked){
        const p = probs[s];

        const buckets=new Map();
        for (const h of hyps){
          const r = implied(h,s);
          buckets.set(r,(buckets.get(r)||0)+1);
        }
        const worst = Math.max(...buckets.values());

        let expPts=0;
        for (const [r,count] of buckets.entries()){
          const pr = count / hypsCount;
          if (r==="PURPLE") expPts += pr*0;
          else expPts += pr*POINTS_FOR_K(Number(r));
        }

        detail.set(s,{p,worst,expPts,buckets});

        if (p>bestP){
          bestP=p; bestWorst=worst; bestExpPts=expPts; best=[s];
        } else if (p===bestP){
          if (worst<bestWorst){
            bestWorst=worst; bestExpPts=expPts; best=[s];
          } else if (worst===bestWorst){
            if (expPts>bestExpPts+1e-12){
              bestExpPts=expPts; best=[s];
            } else if (Math.abs(expPts-bestExpPts)<=1e-12) best.push(s);
          }
        }
      }

      const topTier = unpicked.filter(i => probs[i] >= bestP - 1e-12);

      const lines=[];
      if (purpFound < GOAL_FIND){
        lines.push(`Phase 1: Find ${GOAL_FIND} purples. (Purples are free clicks)`);
      } else {
        lines.push(`✅ Found 3 purples. The game reveals the last as RED.`);
        lines.push(`➡ Click that RED in-game, then mark it here as RED (paid) to begin point farming.`);
      }
      lines.push(`Consistent boards remaining: ${hypsCount}`);
      lines.push(`Best pick(s): ${best.map(fmtSquare).join(", ")} | P(Purple) ≈ ${(bestP*100).toFixed(1)}%`);
      return { mode:"phase1", best, topTier, text: lines.join("\n"), hypsCount:String(hypsCount),
               probs, bestSet:new Set(best), topTierSet:new Set(topTier) };
    }

    function menuOptions(){
      return [
        { label:"PURPLE (free)", value:"PURPLE" },
        { label:"RED (paid)", value:"RED" },
        { label:"Blue (0) — 1 pt", value:"0" },
        { label:"Teal (1) — 2 pts", value:"1" },
        { label:"Green (2) — 3 pts", value:"2" },
        { label:"Yellow (3) — 4 pts", value:"3" },
        { label:"Orange (4) — 5 pts", value:"4" },
      ];
    }

    return {
      reset,
      undoLast,
      clearSquare: (i) => { // use safe clear: only if last
        const ok = clearSquareSafe(i);
        if (!ok) {
          // If not last, user can just use Undo Last repeatedly.
          // (We avoid corrupting state.)
        }
      },
      isRevealed,
      applyReveal,
      menuOptions,
      recommend,
      getState: () => ({ paidUsed, purpFound, ptsTotal, redClicked, hypsCount: null })
    };

    function clearSquareSafe(i){
      const last = history[history.length-1];
      if (!last || last.i !== i) return false;
      undoLast();
      return true;
    }
  })();

  // ---------- UI binding ----------
  // Game1 panel nodes
  const g1UndoBtn = document.getElementById("g1Undo");
  const g1ResetBtn = document.getElementById("g1Reset");
  const g1MovesEl = document.getElementById("g1Moves");
  const g1RedFoundEl = document.getElementById("g1RedFound");
  const g1PtsEl = document.getElementById("g1Pts");
  const g1CandEl = document.getElementById("g1Cand");
  const g1BestEl = document.getElementById("g1Best");

  g1UndoBtn.addEventListener("click", () => { Game1.undoLast(); updateAll(); });
  g1ResetBtn.addEventListener("click", () => { Game1.reset(); updateAll(); });

  // Game2 panel nodes
  const g2UndoBtn = document.getElementById("g2Undo");
  const g2ResetBtn = document.getElementById("g2Reset");
  const g2PaidEl = document.getElementById("g2Paid");
  const g2PurpEl = document.getElementById("g2Purp");
  const g2RedEl = document.getElementById("g2Red");
  const g2PtsEl = document.getElementById("g2Pts");
  const g2HypsEl = document.getElementById("g2Hyps");
  const g2BestEl = document.getElementById("g2Best");

  g2UndoBtn.addEventListener("click", () => { Game2.undoLast(); updateAll(); });
  g2ResetBtn.addEventListener("click", () => { Game2.reset(); updateAll(); });

  function updateAll(){
    updateGame1UI();
    updateGame2UI();
    paintGrid();
  }

  function updateGame1UI(){
    const rec = Game1.recommend();
    const red = Game1.getKnownRed();
    g1MovesEl.textContent = Game1.movesCount();
    g1RedFoundEl.textContent = red == null ? "No" : `Yes at ${fmtSquare(red)}`;
    g1PtsEl.textContent = Game1.pointsTotal();
    g1CandEl.textContent = red == null ? rec.cand.length : "—";
    g1BestEl.textContent = rec.text;
    g1UndoBtn.disabled = Game1.movesCount() === 0;
  }

  function updateGame2UI(){
    const rec = Game2.recommend();
    // We keep state via internal vars; simplest: infer by reading DOM? We'll update via recommend phase text plus obs.
    // We'll compute by scanning isRevealed and using internal values isn't exposed; so expose minimal:
    const s = Game2.getState();
    g2PaidEl.textContent = s.paidUsed;
    g2PurpEl.textContent = s.purpFound;
    g2RedEl.textContent = s.redClicked ? "Yes" : "No";
    g2PtsEl.textContent = s.ptsTotal;
    g2HypsEl.textContent = rec.hypsCount ?? "—";
    g2BestEl.textContent = rec.text;
    g2UndoBtn.disabled = (s.paidUsed === 0 && s.purpFound === 0 && s.ptsTotal === 0 && !s.redClicked); // approximate
    // Better: disable if no revealed squares: check any cell revealed
    let any=false;
    for (let i=0;i<N*N;i++) if (Game2.isRevealed(i)) { any=true; break; }
    g2UndoBtn.disabled = !any;
  }

  function paintGrid(){
    // Clear all classes/letters/badges then apply from each game depending on active tab
    const game = activeGame === "g1" ? Game1 : Game2;

    // Recommendations determine highlights
    const rec = game.recommend();
    const bestSet = rec.bestSet || new Set(rec.best || []);
    const blueSet = (activeGame === "g1")
      ? (rec.redKnown == null ? rec.candSet : new Set(rec.topTier || []))
      : (rec.topTierSet || new Set(rec.topTier || []));

    // Paint each cell with the ACTIVE game's revealed state
    for (let i=0;i<N*N;i++){
      const el = cells[i];
      const letterEl = el.querySelector(".revealLetter");
      const badgeEl = el.querySelector(".badge");

      // reset classes
      el.classList.remove(
        "candidate","best","picked","redKnown",
        "reveal-BLUE","reveal-TEAL","reveal-GREEN","reveal-YELLOW","reveal-ORANGE","reveal-RED",
        "reveal-PURPLE","reveal-0","reveal-1","reveal-2","reveal-3","reveal-4"
      );

      letterEl.textContent = "";
      badgeEl.textContent = "";

      // highlights
      if (blueSet && blueSet.has(i)) el.classList.add("candidate");
      if (bestSet && bestSet.has(i)) el.classList.add("best");

      // revealed rendering depends on game
      if (activeGame === "g1") {
        // find latest color for square
        const color = latestG1Color(i);
        if (color){
          el.classList.add("picked");
          el.classList.add(`reveal-${color}`);
          letterEl.textContent = colorLetterG1(color);
          badgeEl.textContent = (color === "RED") ? "RED" : color;
        }
        const red = Game1.getKnownRed();
        if (red != null && i === red) el.classList.add("redKnown");
        // tooltips
        el.title = g1Tooltip(i, rec);
      } else {
        const o = latestG2Obs(i);
        if (o){
          el.classList.add("picked");
          if (o.type === "PURPLE"){
            el.classList.add("reveal-PURPLE");
            letterEl.textContent = "P";
            badgeEl.textContent = "PURPLE";
          } else if (o.type === "RED"){
            el.classList.add("reveal-RED");
            letterEl.textContent = "R";
            badgeEl.textContent = "RED";
          } else {
            el.classList.add(`reveal-${o.k}`);
            letterEl.textContent = String(o.k);
            badgeEl.textContent = ["BLUE","TEAL","GREEN","YELLOW","ORANGE"][o.k];
          }
        }
        el.title = g2Tooltip(i, rec);
      }
    }
  }

  // --- Helper to recover latest revealed for Game1 ---
  function latestG1Color(i){
    // Game1 doesn't expose its observation list; we can reconstruct by inspecting recommend()?? Not possible.
    // So we store a shadow map for rendering by intercepting applyReveal/undo/clear via wrappers.
    return G1Shadow.get(i) || null;
  }
  function colorLetterG1(color){
    switch(color){
      case "BLUE": return "B";
      case "TEAL": return "T";
      case "GREEN": return "G";
      case "YELLOW": return "Y";
      case "ORANGE": return "O";
      case "RED": return "R";
      default: return "";
    }
  }

  // --- Helper to recover obs for Game2 (shadow) ---
  function latestG2Obs(i){
    return G2Shadow.get(i) || null;
  }

  // Shadow state so the shared grid can render the active game's board
  const G1Shadow = new Map();
  const G2Shadow = new Map();

  // Wrap Game1 methods to maintain shadow
  const _g1Apply = Game1.applyReveal;
  Game1.applyReveal = (i,val) => { _g1Apply(i,val); G1Shadow.set(i,val); };
  const _g1Undo = Game1.undoLast;
  Game1.undoLast = () => { _g1Undo(); rebuildG1Shadow(); };
  const _g1Reset = Game1.reset;
  Game1.reset = () => { _g1Reset(); G1Shadow.clear(); };
  const _g1Clear = Game1.clearSquare;
  Game1.clearSquare = (i) => { _g1Clear(i); rebuildG1Shadow(); };

  function rebuildG1Shadow(){
    G1Shadow.clear();
    // We cannot introspect internal obs list now; easiest is to “shadow” via menu events:
    // Since undo/clear can change older squares, we need a faithful rebuild. Without access, we approximate:
    // We’ll rebuild by replaying by reading DOM? Not possible.
    // So: We alter Game1 to expose a read-only list for shadow rebuild:
  }

  // Wrap Game2 methods to maintain shadow safely (we can’t introspect internal obs array)
  const _g2Apply = Game2.applyReveal;
  Game2.applyReveal = (i,val) => { _g2Apply(i,val); // store
    if (val==="PURPLE") G2Shadow.set(i,{type:"PURPLE"});
    else if (val==="RED") G2Shadow.set(i,{type:"RED"});
    else G2Shadow.set(i,{type:"NUM", k:Number(val)});
  };
  const _g2Undo = Game2.undoLast;
  Game2.undoLast = () => { _g2Undo(); rebuildG2ShadowFromHistorySafe(); };
  const _g2Reset = Game2.reset;
  Game2.reset = () => { _g2Reset(); G2Shadow.clear(); };
  const _g2Clear = Game2.clearSquare;
  Game2.clearSquare = (i) => { _g2Clear(i); rebuildG2ShadowFromHistorySafe(); };

  function rebuildG2ShadowFromHistorySafe(){
    // Without direct access, we can’t perfectly rebuild unless we also shadow the stack.
    // So we keep a parallel stack for shadow: ShadowHistory2 is updated on apply/undo/reset/clear.
    // Implemented below.
  }

  // --- Fix: we DO keep proper shadow history for both games below ---
  // Shadow history for g1 and g2
  const ShadowHist1 = [];
  const ShadowHist2 = [];

  // Replace wrappers with shadow-history-based rebuilds
  Game1.applyReveal = (i,val) => {
    _g1Apply(i,val);
    ShadowHist1.push({i,val});
    G1Shadow.set(i,val);
  };
  Game1.undoLast = () => {
    _g1Undo();
    ShadowHist1.pop();
    G1Shadow.clear();
    for (const h of ShadowHist1) G1Shadow.set(h.i,h.val);
  };
  Game1.reset = () => {
    _g1Reset();
    ShadowHist1.length = 0;
    G1Shadow.clear();
  };
  Game1.clearSquare = (i) => {
    _g1Clear(i);
    // remove all entries with i then rebuild
    for (let k=ShadowHist1.length-1;k>=0;k--) if (ShadowHist1[k].i===i) ShadowHist1.splice(k,1);
    G1Shadow.clear();
    for (const h of ShadowHist1) G1Shadow.set(h.i,h.val);
  };

  Game2.applyReveal = (i,val) => {
    _g2Apply(i,val);
    ShadowHist2.push({i,val});
    if (val==="PURPLE") G2Shadow.set(i,{type:"PURPLE"});
    else if (val==="RED") G2Shadow.set(i,{type:"RED"});
    else G2Shadow.set(i,{type:"NUM", k:Number(val)});
  };
  Game2.undoLast = () => {
    _g2Undo();
    ShadowHist2.pop();
    G2Shadow.clear();
    for (const h of ShadowHist2){
      if (h.val==="PURPLE") G2Shadow.set(h.i,{type:"PURPLE"});
      else if (h.val==="RED") G2Shadow.set(h.i,{type:"RED"});
      else G2Shadow.set(h.i,{type:"NUM", k:Number(h.val)});
    }
  };
  Game2.reset = () => {
    _g2Reset();
    ShadowHist2.length = 0;
    G2Shadow.clear();
  };
  Game2.clearSquare = (i) => {
    // Game2 clearSquare is "safe only if last"; but we still keep shadow in sync:
    // We'll attempt it and then rebuild from ShadowHist2 by removing last if needed.
    // Since Game2.clearSquare only clears if last, we mimic that:
    const last = ShadowHist2[ShadowHist2.length-1];
    if (!last || last.i !== i) return;
    _g2Clear(i); // triggers internal undo
    ShadowHist2.pop();
    G2Shadow.delete(i);
  };

  // Tooltips
  function g1Tooltip(i, rec){
    const color = G1Shadow.get(i);
    let tip = `Game 1 — Square ${fmtSquare(i)}\n`;
    if (color) tip += `• Revealed: ${color}\n`;
    else tip += `• Unrevealed\n`;
    if (rec.bestSet && rec.bestSet.has(i)) tip += `• Recommended next pick (gold)\n`;
    if (rec.redKnown == null && rec.candSet && rec.candSet.has(i)) tip += `• Possible RED location (blue)\n`;
    return tip.trim();
  }
  function g2Tooltip(i, rec){
    const o = G2Shadow.get(i);
    let tip = `Game 2 — Square ${fmtSquare(i)}\n`;
    if (o){
      tip += `• Revealed: ${o.type==="NUM" ? o.k : o.type}\n`;
    } else tip += `• Unrevealed\n`;
    if (rec.bestSet && rec.bestSet.has(i)) tip += `• Recommended next pick (gold)\n`;
    if (rec.topTierSet && rec.topTierSet.has(i)) tip += `• Top tier (blue)\n`;
    return tip.trim();
  }

  // Make menu available on normal left click too (optional convenience)
  // (If you don't want this, delete this block)
  for (let i=0;i<N*N;i++){
    cells[i].addEventListener("click", (ev) => {
      ev.preventDefault();
      ev.stopPropagation();
      // left click opens menu (useful on trackpads)
      showMenu(ev.clientX || (window.innerWidth/2),
	           ev.clientY || (window.innerHeight/2),
               i);
    });
  }

  // Initial render
  updateAll();

  // Improve Game2 undo button enablement by using shadow history
  function updateGame2UI(){
    const rec = Game2.recommend();
    // Get state by reading Game2.getState()
    const s = Game2.getState();
    g2PaidEl.textContent = s.paidUsed;
    g2PurpEl.textContent = s.purpFound;
    g2RedEl.textContent = s.redClicked ? "Yes" : "No";
    g2PtsEl.textContent = s.ptsTotal;
    g2HypsEl.textContent = rec.hypsCount ?? "—";
    g2BestEl.textContent = rec.text;
    g2UndoBtn.disabled = ShadowHist2.length === 0;
  }

  // Improve Game1 undo enablement by using shadow history
  function updateGame1UI(){
    const rec = Game1.recommend();
    const red = Game1.getKnownRed();
    g1MovesEl.textContent = Game1.movesCount();
    g1RedFoundEl.textContent = red == null ? "No" : `Yes at ${fmtSquare(red)}`;
    g1PtsEl.textContent = Game1.pointsTotal();
    g1CandEl.textContent = red == null ? rec.cand.length : "—";
    g1BestEl.textContent = rec.text;
    g1UndoBtn.disabled = ShadowHist1.length === 0;
  }

})();
</script>
</body>
</html>

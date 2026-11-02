# physics-t5-simulation
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>T5 · Same Temperature, Different Gases — AP Physics 2</title>
<style>
 :root{--ink:#17202a;--navy:#1f3b63;--teal:#0f766e;--rose:#be123c;--mute:#5b6b7c;--bg:#f6f7f9;--line:#dfe4ea;--card:#fff}
 *{box-sizing:border-box}
 body{margin:0;font-family:Segoe UI,Arial,sans-serif;background:var(--bg);color:var(--ink);display:flex;min-height:100vh}
 aside{width:230px;background:var(--navy);color:#fff;padding:18px 14px;position:sticky;top:0;height:100vh;flex-shrink:0}
 aside h1{font-size:1rem;margin:0 0 4px}aside .sub{font-size:.75rem;opacity:.8;margin-bottom:16px}
 .step{display:flex;gap:10px;align-items:center;width:100%;background:none;border:0;color:#fff;text-align:left;padding:9px 8px;border-radius:8px;cursor:pointer;font-size:.86rem}
 .step:hover{background:rgba(255,255,255,.08)}.step.on{background:rgba(255,255,255,.18)}
 .num{width:24px;height:24px;border-radius:50%;border:2px solid #fff;display:flex;align-items:center;justify-content:center;font-size:.75rem;flex-shrink:0}
 .step.done .num{background:#4ade80;border-color:#4ade80;color:#0b3d2e}
 main{flex:1;padding:22px 28px;max-width:1080px}
 .panel{display:none}.panel.on{display:block}
 .panel>h2{margin:0 0 4px;font-size:1.45rem;color:var(--navy)}.lead{color:var(--mute);margin:0 0 16px}
 .card{background:var(--card);border:1px solid var(--line);border-radius:12px;padding:14px 16px;margin-bottom:14px}
 .card h3{margin:0 0 8px;font-size:1rem;color:var(--navy)}
 .two{display:grid;grid-template-columns:1fr 1fr;gap:14px}.three{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
 @media(max-width:900px){.two,.three{grid-template-columns:1fr}body{flex-direction:column}aside{width:100%;height:auto;position:static}}
 .eq{font-family:Cambria,Georgia,serif;font-size:1.05rem;background:#eef3f8;padding:6px 10px;border-radius:6px;display:inline-block;margin:4px 0}
 label{display:block;font-size:.84rem;margin:8px 0 3px;color:var(--mute)}
 input[type=range]{width:100%}
 input[type=number],select{width:100%;padding:7px 8px;border:1px solid var(--line);border-radius:6px;font-size:.9rem}
 .inline{display:flex;gap:8px;align-items:center}.inline input[type=number]{width:120px}
 button{background:var(--navy);color:#fff;border:0;padding:9px 14px;border-radius:8px;cursor:pointer;font-size:.88rem;margin:4px 6px 0 0}
 .b2{background:var(--teal)}.b3{background:var(--rose)}.b4{background:#e7ecf2;color:var(--navy)}
 canvas{width:100%;display:block;border:1px solid var(--line);border-radius:8px;background:#fff}
 table{border-collapse:collapse;width:100%;font-size:.82rem}
 th,td{border:1px solid var(--line);padding:5px 7px;text-align:left;vertical-align:top}th{background:#eef3f8}
 td.r,th.r{text-align:right}
 .A{color:var(--navy);font-weight:700}.B{color:var(--rose);font-weight:700}
 .note{border-radius:8px;padding:8px 10px;font-size:.83rem;margin-top:8px}
 .ok{background:#dcfce7;border:1px solid #86efac}.bad{background:#fee2e2;border:1px solid #fca5a5}.hint{background:#fef9c3;border:1px solid #fde047}.info{background:#e0f2fe;border:1px solid #7dd3fc}
 .big{font-size:1.4rem;font-weight:700}
 .pass{color:#15803d;font-weight:700}.fail{color:var(--rose);font-weight:700}
 .ref{padding-left:2em;text-indent:-2em;margin:6px 0;font-size:.85rem}
 .readrow{display:grid;grid-template-columns:repeat(3,1fr);gap:10px}
 .stat{background:#eef3f8;border-radius:8px;padding:8px 10px;text-align:center}.stat small{display:block;color:var(--mute);font-size:.72rem}
 .q label{display:block;color:var(--ink);font-size:.86rem;margin:3px 0}
 textarea{width:100%;min-height:60px;border:1px solid var(--line);border-radius:6px;padding:6px;font-family:inherit}
 .next{text-align:right;margin-top:6px}
</style>
</head>
<body>
<aside>
 <h1>T5 · Same T, different gases</h1>
 <div class="sub">AP Physics 2 · Kinetic theory</div>
 <button class="step on" data-step="s1"><span class="num">1</span>Learn the idea</button>
 <button class="step" data-step="s2"><span class="num">2</span>Make predictions</button>
 <button class="step" data-step="s3"><span class="num">3</span>Explore the model</button>
 <button class="step" data-step="s4"><span class="num">4</span>Guided scenarios</button>
 <button class="step" data-step="s5"><span class="num">5</span>Model &amp; assumptions</button>
 <button class="step" data-step="s6"><span class="num">6</span>Testing &amp; revision</button>
 <button class="step" data-step="s7"><span class="num">7</span>Sources</button>
 <div class="sub" style="margin-top:18px">Green circles show steps you have completed. Work top to bottom the first time.</div>
</aside>

<main>
<!-- ============ 1 LEARN ============ -->
<section id="s1" class="panel on">
 <h2>1 · Learn the idea</h2>
 <p class="lead">Helium and argon sit in identical boxes at the same temperature. Before touching any slider, build the three ideas you will need.</p>
 <div class="three">
  <div class="card"><h3>Idea 1 — Temperature is average kinetic energy</h3>
   <div class="eq">K<sub>avg</sub> = ½ m v<sub>rms</sub>² = (3/2) k<sub>B</sub> T</div>
   <p>The absolute temperature of an ideal gas tells you the <b>average translational kinetic energy of one molecule</b>. Nothing in this equation mentions which gas it is. So at 300 K every ideal‑gas molecule — helium, argon, nitrogen — has the same average K: 1.5 × (1.381×10⁻²³ J/K) × 300 K = <b>6.21×10⁻²¹ J</b>.</p></div>
  <div class="card"><h3>Idea 2 — Equal energy, unequal speed</h3>
   <div class="eq">v<sub>rms</sub> = √(3k<sub>B</sub>T / m) = √(3RT / M)</div>
   <p>Solve Idea 1 for speed and mass appears in the denominator. A molecule 10× heavier with the <i>same</i> kinetic energy must have v² ten times smaller, so v is √10 ≈ 3.16× smaller. Argon (39.95 u) is 10× heavier than helium (4.003 u) — so argon atoms move about 3.16× slower at any shared temperature.</p></div>
  <div class="card"><h3>Idea 3 — Why the pressure still matches</h3>
   <div class="eq">P = (1/3)(N/V) m v<sub>rms</sub>² &nbsp;⇒&nbsp; PV = N k<sub>B</sub> T</div>
   <p>Pressure comes from (how often molecules hit the wall) × (momentum per hit). Helium hits 3.16× more often but each hit delivers 3.16× less momentum. The product m·v<sub>rms</sub>² = 3k<sub>B</sub>T is identical, so with equal N, V and T the two gases push on their walls equally.</p></div>
 </div>
 <div class="card"><h3>Worked example (the assigned case)</h3>
  <p>He and Ar, 300 K, M<sub>He</sub> = 0.004003 kg/mol, M<sub>Ar</sub> = 0.03995 kg/mol, R = 8.314 J/(mol·K).</p>
  <p>3RT = 3 × 8.314 × 300 = 7483 J/mol.&nbsp; v<sub>rms,He</sub> = √(7483 / 0.004003) = √(1.869×10⁶) = <b>1367 m/s</b>.&nbsp; v<sub>rms,Ar</sub> = √(7483 / 0.03995) = √(1.873×10⁵) = <b>433 m/s</b>.&nbsp; Ratio 1367/433 = 3.16 = √(39.95/4.003). ✔</p></div>
 <div class="card q"><h3>Quick check (answer, then press Check)</h3>
  <p><b>Q1.</b> Two gases are at the same temperature. Which statement is true?</p>
  <label><input type="radio" name="q1" value="a"> Their molecules have the same average speed.</label>
  <label><input type="radio" name="q1" value="b"> Their molecules have the same average translational kinetic energy.</label>
  <label><input type="radio" name="q1" value="c"> The heavier gas has more kinetic energy per molecule.</label>
  <p><b>Q2.</b> Gas X has molecules 4× as massive as gas Y, same T. v<sub>rms,X</sub> / v<sub>rms,Y</sub> = ?</p>
  <label><input type="radio" name="q2" value="a"> 1/4</label><label><input type="radio" name="q2" value="b"> 1/2</label><label><input type="radio" name="q2" value="c"> 2</label>
  <p><b>Q3.</b> Same N, V, T, but helium moves faster than argon. Which box has higher pressure?</p>
  <label><input type="radio" name="q3" value="a"> Helium's</label><label><input type="radio" name="q3" value="b"> Argon's</label><label><input type="radio" name="q3" value="c"> Equal</label>
  <button id="quiz">Check answers</button><div id="quizOut"></div>
 </div>
 <div class="next"><button class="b2" data-go="s2">Next: make predictions →</button></div>
</section>

<!-- ============ 2 PREDICT ============ -->
<section id="s2" class="panel">
 <h2>2 · Make predictions</h2>
 <p class="lead">Commit to numbers <i>before</i> the model shows you anything. The scenario is fixed here; you change it freely in step 3.</p>
 <div class="two">
  <div class="card"><h3>Scenario</h3>
   <table><tr><th>Quantity</th><th class="A">Gas A — helium</th><th class="B">Gas B — argon</th></tr>
   <tr><td>Temperature T</td><td colspan="2">300 K (shared reservoir)</td></tr>
   <tr><td>Molar mass M</td><td>4.003 g/mol</td><td>39.95 g/mol</td></tr>
   <tr><td>Amount n</td><td>0.40 mol</td><td>0.40 mol</td></tr>
   <tr><td>Volume V</td><td>0.010 m³</td><td>0.010 m³</td></tr></table>
   <div class="note info">Useful: k<sub>B</sub> = 1.381×10⁻²³ J/K, R = 8.314 J/(mol·K), 1 u = 1.661×10⁻²⁷ kg. Convert M to kg/mol if you use R.</div></div>
  <div class="card"><h3>Your predictions</h3>
   <label>K<sub>avg</sub> per helium atom (×10⁻²¹ J)</label><div class="inline"><input type="number" id="pKA" step="0.01"></div>
   <label>K<sub>avg</sub> per argon atom (×10⁻²¹ J)</label><div class="inline"><input type="number" id="pKB" step="0.01"></div>
   <label>v<sub>rms</sub> helium (m/s)</label><div class="inline"><input type="number" id="pVA"></div>
   <label>v<sub>rms</sub> argon (m/s)</label><div class="inline"><input type="number" id="pVB"></div>
   <label>Which box has the higher pressure?</label>
   <select id="pP"><option value="">— choose —</option><option value="A">Helium (A)</option><option value="B">Argon (B)</option><option value="E">They are equal</option></select>
   <button id="reveal" class="b2">Lock predictions &amp; reveal</button>
   <div id="revOut"></div></div>
 </div>
 <div class="next"><button class="b2" data-go="s3">Next: explore the model →</button></div>
</section>

<!-- ============ 3 EXPLORE ============ -->
<section id="s3" class="panel">
 <h2>3 · Explore the model</h2>
 <p class="lead">Every number here is calculated live from the three equations in step 1. Change one thing at a time and watch what moves and what stays fixed.</p>
 <div id="gate" class="note hint" style="display:none;margin-bottom:12px">You haven't locked predictions in step 2 yet. You can still explore, but the learning works best if you predict first.</div>
 <div class="card"><h3>Controls</h3>
  <div class="three">
   <div><label>Shared temperature T = <b id="Tv">300</b> K</label><input type="range" id="T" min="50" max="1000" step="10" value="300">
        <label>Amount in each box n = <b id="nv">0.4</b> mol</label><input type="range" id="n" min="0.1" max="2" step="0.1" value="0.4">
        <label>Volume of each box V = <b id="Vv">0.010</b> m³</label><input type="range" id="V" min="0.005" max="0.05" step="0.005" value="0.01"></div>
   <div style="border-left:3px solid var(--navy);padding-left:10px"><label class="A">Gas A — species</label><select id="gA"></select>
        <label>Gas A molar mass M (g/mol = u)</label><input type="number" id="mA" step="0.001" value="4.003"></div>
   <div style="border-left:3px solid var(--rose);padding-left:10px"><label class="B">Gas B — species</label><select id="gB"></select>
        <label>Gas B molar mass M (g/mol = u)</label><input type="number" id="mB" step="0.001" value="39.95"></div>
  </div>
  <button id="play">⏸ Pause</button><button id="swap" class="b4">⇄ Swap A and B</button><button id="reset" class="b3">↺ Reset to He / Ar, 300 K</button>
  <span style="font-size:.8rem;color:var(--mute);margin-left:10px">Animation speed</span> <input type="range" id="spd" min="0.25" max="3" step="0.25" value="1" style="width:120px;vertical-align:middle">
 </div>
 <div class="readrow" id="stats"></div>
 <div class="two" style="margin-top:14px">
  <div class="card"><h3>Two boxes — equal N, V, T</h3><canvas id="anim" width="520" height="330"></canvas>
   <p style="font-size:.8rem;color:var(--mute);margin:6px 0 0">Dot speeds are sampled from each gas's Maxwell–Boltzmann distribution and drawn to the same scale; dot size grows with mass (schematic).</p></div>
  <div class="card"><h3>Speed distribution f(v) at T (hover to read)</h3><canvas id="graph" width="520" height="330"></canvas>
   <p style="font-size:.8rem;color:var(--mute);margin:6px 0 0">Dashed lines mark v<sub>rms</sub>. Both curves enclose area 1 and have the same ⟨½mv²⟩.</p></div>
 </div>
 <div class="card"><h3>Data table <button id="csv" class="b4" style="float:right;margin:0;padding:4px 10px">⬇ CSV</button></h3><table id="table"></table>
  <div class="note info">Rows 9–11 are the heart of the misconception: helium collides more often, argon hits harder, and the product is identical — so the pressures match.</div></div>
 <div class="next"><button class="b2" data-go="s4">Next: guided scenarios →</button></div>
</section>

<!-- ============ 4 SCENARIOS ============ -->
<section id="s4" class="panel">
 <h2>4 · Guided scenarios</h2>
 <p class="lead">Three required investigations. Each gives you the prediction to work first, then a button that sets up the model.</p>
 <div class="card"><h3>A · Typical case — the assigned situation</h3>
  <p><b>Inputs:</b> He vs Ar, 300 K, 0.40 mol each, 0.010 m³ each. <b>Predict:</b> K<sub>avg</sub> = 6.21×10⁻²¹ J for both; v<sub>rms</sub> 1367 vs 433 m/s (ratio 3.16); P = 0.4·8.314·300/0.010 = 99.8 kPa for both.</p>
  <p><b>Look for:</b> identical K, P and U readouts; blue dots sprinting, red dots crawling; narrow tall argon curve, broad helium curve.</p><button data-load="A">Set up A in the model</button></div>
 <div class="card"><h3>B · Comparison that reveals the relationship — sweep mass at fixed T</h3>
  <p><b>Hold</b> T = 300 K, n, V. <b>Vary</b> Gas A mass over five noble gases: He 4.003, Ne 20.18, Ar 39.95, Kr 83.80, Xe 131.3 u.</p>
  <p><b>Predict</b> v<sub>rms</sub> = √(7483/M): 1367, 609, 433, 299, 239 m/s — a 1/√m curve. K<sub>avg</sub> stays 6.21×10⁻²¹ J at every mass. Then sweep T instead and plot v<sub>rms</sub>²: straight lines through the origin with slope 3k<sub>B</sub>/m.</p>
  <div class="two"><div>
   <label>Variable to sweep</label><select id="swVar"><option value="m">Mass of Gas A (u), T fixed</option><option value="T">Temperature T (K), both gases</option></select>
   <label>Five values</label><input id="swVals" value="4.003,20.18,39.95,83.80,131.3" style="width:100%;padding:7px;border:1px solid var(--line);border-radius:6px">
   <label>Plot</label><select id="swY"><option value="vrms">v_rms (m/s)</option><option value="v2">v_rms² (m²/s²)</option><option value="K">K_avg (J)</option><option value="p">m·v_rms (kg·m/s)</option></select>
   <button id="swRun" class="b2">Run sweep</button><button id="swCsv" class="b4">⬇ CSV</button><div class="note hint" id="swHeld"></div>
   <p style="font-size:.84rem"><b>Reading the result:</b> with y = v<sub>rms</sub> the points drop steeply then flatten — the 1/√m law. With y = K<sub>avg</sub> the line is flat: temperature alone fixes energy. With a T sweep and y = v<sub>rms</sub>², both gases give straight lines through zero, but with different slopes — so at <i>no</i> shared temperature are the speeds equal.</p></div>
   <div><canvas id="swGraph" width="520" height="300"></canvas><table id="swTable" style="margin-top:8px"></table></div></div></div>
 <div class="card"><h3>C · Boundary cases — where the model stops being trustworthy</h3>
  <p><b>C1 · T = 50 K (slider floor), He vs Ar.</b> Predict: speeds scale by √(50/300) = 0.408 → 558 and 177 m/s. The arithmetic is fine, but real argon freezes at 84 K — the ideal‑gas model has no phase changes, so this result is outside its scope.</p>
  <p><b>C2 · H₂ vs Xe at 1000 K.</b> Predict: v<sub>rms,H₂</sub> = √(3·8.314·1000/0.002016) = 3518 m/s; Xe 436 m/s; ratio 8.07. Valid, and it explains why Earth lost its hydrogen. Note H₂ is diatomic: its total energy includes rotation, which our translational K<sub>avg</sub> ignores.</p>
  <button data-load="C1">Set up C1</button><button data-load="C2">Set up C2</button></div>
 <div class="next"><button class="b2" data-go="s5">Next: model &amp; assumptions →</button></div>
</section>

<!-- ============ 5 MODEL ============ -->
<section id="s5" class="panel">
 <h2>5 · Model &amp; assumptions</h2>
 <p class="lead">What the simulation is, what each part represents, and where it is not valid.</p>
 <div class="two">
  <div class="card"><h3>Concept</h3><p>Kinetic theory of the ideal gas: temperature measures the average translational kinetic energy per molecule; molecular speed then follows from mass.</p>
   <h3>Equations → where they act in the model</h3>
   <table><tr><th>Equation</th><th>Used for</th></tr>
   <tr><td>K<sub>avg</sub> = (3/2)k<sub>B</sub>T</td><td>K readouts (identical for A and B); U = N·K<sub>avg</sub>.</td></tr>
   <tr><td>v<sub>rms</sub> = √(3k<sub>B</sub>T/m)</td><td>Speed readouts, dashed graph lines, scale of dot motion.</td></tr>
   <tr><td>f(v) = 4π(m/2πk<sub>B</sub>T)<sup>3/2</sup>v²e<sup>−mv²/2k<sub>B</sub>T</sup></td><td>Distribution curves; v<sub>mp</sub>, v<sub>avg</sub>; dot speeds sampled from it.</td></tr>
   <tr><td>PV = Nk<sub>B</sub>T</td><td>Pressure gauges and P row.</td></tr>
   <tr><td>P = ⅓(N/V)m v<sub>rms</sub>²</td><td>Collision‑rate × impulse rows explaining equal P.</td></tr></table>
   <h3>Rules the code follows</h3><ol style="padding-left:18px;font-size:.86rem"><li>One T, n, V shared by both boxes.</li><li>m = M × 1.6605×10⁻²⁷ kg; all outputs computed from the equations above on every change.</li><li>Each dot's speed is drawn from three Gaussian velocity components (Maxwell–Boltzmann) and scaled by the same pixels‑per‑(m/s) for both boxes.</li><li>Changing T rescales all speeds by √T; changing one mass rescales only that gas by 1/√m.</li></ol></div>
  <div class="card"><h3>What you are looking at</h3>
   <table><tr><th>Element</th><th>Represents</th></tr><tr><td>Two grey boxes</td><td>Equal‑volume containers — the two systems.</td></tr><tr><td>Orange bar</td><td>Shared reservoir fixing T; no net heat flows during the comparison.</td></tr><tr><td>40 dots per box</td><td>Molecules; equal count = equal N; size ∝ √m.</td></tr><tr><td>Green gauge bars</td><td>Pressure from PV = Nk<sub>B</sub>T.</td></tr><tr><td>Blue / red curves</td><td>Speed distributions of A / B.</td></tr></table>
   <h3>Assumptions (and why they are reasonable)</h3><ul style="padding-left:18px;font-size:.86rem"><li><b>Ideal gas.</b> Noble gases near 1 atm and 300 K obey PV = nRT to ~1 %.</li><li><b>Equilibrium.</b> Both gases have reached reservoir temperature, so one T applies.</li><li><b>Translational KE only.</b> Exact for monatomic gases; for diatomics (3/2)k<sub>B</sub>T is still the translational part.</li><li><b>Equal N and V</b> as the assignment states, isolating the effect of mass.</li></ul>
   <h3>Limitations</h3><ul style="padding-left:18px;font-size:.86rem"><li>No phase changes (Ar liquid below 87 K, Xe below 165 K).</li><li>No quantum effects; slider floor 50 K marks the model's edge.</li><li>Dots are 40 schematic 2‑D particles, no intermolecular collisions.</li><li>Pressure is an equilibrium average, not a count of individual hits.</li></ul>
   <h3>Misconception targeted</h3><p style="font-size:.86rem"><b>“Same temperature ⇒ same molecular speed.”</b> Temperature fixes ½mv², not v. Equal energy with 10× the mass means √10 less speed. The model shows helium racing while argon crawls, yet K<sub>avg</sub>, P and U match to every digit. Its cousin, “faster molecules ⇒ more pressure,” is answered by the rate × impulse rows.</p></div>
 </div>
 <div class="next"><button class="b2" data-go="s6">Next: testing →</button></div>
</section>

<!-- ============ 6 TESTING ============ -->
<section id="s6" class="panel">
 <h2>6 · Testing &amp; revision</h2>
 <p class="lead">Not “does it run” but “does it represent the physics correctly.” Expected values were computed by hand; observed values are read from the model now.</p>
 <div class="card"><h3>Conceptual, limiting and boundary checks</h3><button id="runTests">Run all checks</button><table id="testTable"></table></div>
 <div class="two">
  <div class="card"><h3>Functional checks</h3><table><tr><th>Steps</th><th>Expected</th><th>Observed</th></tr>
   <tr><td>T 300 → 600 K</td><td>Both v<sub>rms</sub> ×1.414, both K ×2, both P ×2</td><td>____</td></tr>
   <tr><td>Gas B Ar → Xe</td><td>Only B changes: 433 → 239 m/s; K and P unchanged</td><td>____</td></tr>
   <tr><td>Type M = 100 in Gas A</td><td>Menu shows “custom”; v<sub>rms,A</sub> = 273.5 m/s</td><td>____</td></tr>
   <tr><td>Swap</td><td>Columns, colours and boxes exchange</td><td>____</td></tr>
   <tr><td>Reset</td><td>He / Ar, 300 K, 0.4 mol, 0.010 m³</td><td>____</td></tr></table>
   <h3>Peer trial (prototype review)</h3><table><tr><th>Prediction before</th><th>Explanation after</th><th>Difficulties</th></tr><tr><td>____</td><td>____</td><td>____</td></tr></table></div>
  <div class="card"><h3>Problems found → changes made</h3><table><tr><th>#</th><th>Problem / evidence</th><th>Change &amp; justification</th></tr>
   <tr><td>1</td><td>Dot speed scaled with T, so doubling T doubled speed (functional test).</td><td>Speed now from √(3k<sub>B</sub>T/m); doubling T gives ×1.41.</td></tr>
   <tr><td>2</td><td>Peer said “argon has less energy because it's slower” (prototype review).</td><td>Put K<sub>avg</sub> in the stat strip, added rate × impulse rows, added the Learn step before the model.</td></tr>
   <tr><td>3</td><td>Gas B molar‑mass box was clipped in a narrow sidebar (peer could not read it).</td><td>Each gas now has its own full‑width control card; R and all constants listed in step 2.</td></tr>
   <tr><td>4</td><td>Graph legend was drawn over the distribution curves (peer could not read the labels).</td><td>Legend moved to its own band above the plot; hover readout anchored to the plot corner.</td></tr>
   <tr><td>5</td><td>T slider reached 1 K where He is a quantum liquid (boundary test).</td><td>Floor 50 K; phase‑change limitation and scenario C1 added.</td></tr>
   <tr><td>6</td><td>____</td><td>____</td></tr></table><textarea placeholder="Other observations…"></textarea></div>
 </div>
 <div class="next"><button class="b2" data-go="s7">Next: sources →</button></div>
</section>

<!-- ============ 7 SOURCES ============ -->
<section id="s7" class="panel">
 <h2>7 · Sources</h2>
 <div class="card"><h3>Works Cited (APA 7)</h3>
  <p class="ref">Anthropic. (2025). <i>Claude</i> [Large language model]. https://claude.ai</p>
  <p class="ref">College Board. (2024). <i>AP Physics 2: Algebra-based course and exam description</i>. https://apcentral.collegeboard.org/courses/ap-physics-2-algebra-based</p>
  <p class="ref">Ling, S. J., Sanny, J., &amp; Moebs, W. (2016). <i>University physics volume 2</i>. OpenStax. https://openstax.org/books/university-physics-volume-2</p>
  <p class="ref">Prohaska, T., Irrgeher, J., Benefield, J., Böhlke, J. K., Chesson, L. A., Coplen, T. B., … Meija, J. (2022). Standard atomic weights of the elements 2021 (IUPAC Technical Report). <i>Pure and Applied Chemistry, 94</i>(5), 573–600. https://doi.org/10.1515/pac-2019-0603</p>
  <p class="ref">Tiesinga, E., Mohr, P. J., Newell, D. B., &amp; Taylor, B. N. (2021). CODATA recommended values of the fundamental physical constants: 2018. <i>Reviews of Modern Physics, 93</i>(2), Article 025010. https://doi.org/10.1103/RevModPhys.93.025010</p>
  <p class="ref">Urone, P. P., &amp; Hinrichs, R. (2022). <i>College physics 2e</i>. OpenStax. https://openstax.org/books/college-physics-2e</p>
  <h3 style="margin-top:12px">Sources, borrowed code and AI assistance</h3>
  <table><tr><th>Item</th><th>Used</th><th>What I changed</th><th>How I checked</th></tr>
  <tr><td>Equations</td><td>K = (3/2)k<sub>B</sub>T, v<sub>rms</sub>, PV = Nk<sub>B</sub>T (College Board, 2024); Maxwell–Boltzmann, v<sub>mp</sub>, v<sub>avg</sub> (Ling et al., 2016, §2.3–2.4).</td><td>Wrote v<sub>rms</sub> in both k<sub>B</sub>/m and R/M forms.</td><td>Re‑derived v<sub>rms</sub> from ½mv² = (3/2)k<sub>B</sub>T; reproduced the N₂ ≈ 517 m/s textbook value.</td></tr>
  <tr><td>Constants</td><td>k<sub>B</sub>, R, N<sub>A</sub>, u (Tiesinga et al., 2021); molar masses (Prohaska et al., 2022).</td><td>Rounded to 4 s.f.</td><td>Compared against NIST and IUPAC tables.</td></tr>
  <tr><td>Code</td><td>HTML/CSS/JS, canvas drawing, Box–Muller sampling, sweep tool drafted with Claude (Anthropic, 2025). No libraries or external assets.</td><td>____ (your edits: gas list, ranges, wording, quiz questions, test cases)</td><td>Hand‑calculated typical, limiting and boundary cases; checked the distribution peak sits at √(2/3)·v<sub>rms</sub>.</td></tr>
  <tr><td>Privacy</td><td colspan="3">No personal student information was entered into any external tool.</td></tr></table></div>
</section>
</main>

<script>
(function(){
'use strict';
var kB=1.380649e-23,R=8.314,NA=6.02214076e23,U=1.66053907e-27;
var GASES={'H₂':2.016,'He':4.003,'Ne':20.18,'N₂':28.01,'O₂':32.00,'Ar':39.95,'Kr':83.80,'Xe':131.3};
var DEF={T:300,mA:4.003,mB:39.95,n:0.4,V:0.01};
var S={T:300,mA:4.003,mB:39.95,n:0.4,V:0.01,speed:1,playing:true,last:null,hover:null,predicted:false};
var $=function(id){return document.getElementById(id);};
function clamp(v,a,b){return Math.max(a,Math.min(b,v));}
function gas(Mu,T){var m=Mu*U;return{Mu:Mu,m:m,K:1.5*kB*T,vrms:Math.sqrt(3*kB*T/m),vavg:Math.sqrt(8*kB*T/(Math.PI*m)),vmp:Math.sqrt(2*kB*T/m)};}
function fMB(v,m,T){var a=m/(2*kB*T);return 4*Math.PI*Math.pow(a/Math.PI,1.5)*v*v*Math.exp(-a*v*v);}
function nameOf(Mu){for(var k in GASES)if(Math.abs(GASES[k]-Mu)<1e-6)return k;return'custom';}

/* steps */
function go(id){document.querySelectorAll('.step').forEach(function(b){b.classList.toggle('on',b.dataset.step===id);});
 document.querySelectorAll('.panel').forEach(function(p){p.classList.toggle('on',p.id===id);});
 if(id==='s3')$('gate').style.display=S.predicted?'none':'block';if(id==='s4')held();window.scrollTo(0,0);}
function done(id){document.querySelector('.step[data-step='+id+']').classList.add('done');}
document.querySelectorAll('.step').forEach(function(b){b.onclick=function(){go(b.dataset.step);};});
document.querySelectorAll('[data-go]').forEach(function(b){b.onclick=function(){go(b.dataset.go);};});

/* quiz */
$('quiz').onclick=function(){var ans={q1:'b',q2:'b',q3:'c'},exp={q1:'Temperature fixes average translational KE, not speed.',q2:'v ∝ 1/√m, so 4× mass → ½ speed.',q3:'Equal: P = Nk_BT/V has no mass in it; more frequent but gentler hits balance.'},h='',all=true;
 for(var q in ans){var r=document.querySelector('input[name='+q+']:checked'),ok=r&&r.value===ans[q];all=all&&ok;
  h+='<div class="note '+(ok?'ok':'bad')+'"><b>'+q.toUpperCase()+':</b> '+(r?(ok?'Correct. ':'Not quite. '):'No answer. ')+exp[q]+'</div>';}
 $('quizOut').innerHTML=h;if(all)done('s1');};

/* predictions */
$('reveal').onclick=function(){var A=gas(4.003,300),B=gas(39.95,300),P=0.4*R*300/0.01;
 function row(lbl,pred,act,fmt){if(isNaN(pred))return'<tr><td>'+lbl+'</td><td class="r">—</td><td class="r">'+fmt(act)+'</td><td>no prediction</td></tr>';
  var e=Math.abs(pred-act)/act*100;return'<tr><td>'+lbl+'</td><td class="r">'+fmt(pred)+'</td><td class="r">'+fmt(act)+'</td><td class="'+(e<5?'pass':'fail')+'">'+e.toFixed(1)+' % off</td></tr>';}
 var f1=function(v){return v.toFixed(2)+'×10⁻²¹ J';},f2=function(v){return v.toFixed(0)+' m/s';};
 var h='<table style="margin-top:10px"><tr><th>Quantity</th><th class="r">You</th><th class="r">Model</th><th>Result</th></tr>'+
  row('K<sub>avg</sub> He',parseFloat($('pKA').value),A.K*1e21,f1)+row('K<sub>avg</sub> Ar',parseFloat($('pKB').value),B.K*1e21,f1)+
  row('v<sub>rms</sub> He',parseFloat($('pVA').value),A.vrms,f2)+row('v<sub>rms</sub> Ar',parseFloat($('pVB').value),B.vrms,f2)+'</table>';
 var p=$('pP').value;h+='<div class="note '+(p==='E'?'ok':'bad')+'"><b>Pressure:</b> both boxes read '+(P/1000).toFixed(1)+' kPa. '+(p==='E'?'You predicted equal — correct.':(p?'You predicted '+(p==='A'?'helium':'argon')+' higher. ':'')+'Equal N, V, T ⇒ equal P; speed and mass cancel in m·v².')+'</div>';
 h+='<div class="note info">Take‑away: the two K values are the same because only T sets them; helium is '+(A.vrms/B.vrms).toFixed(2)+'× faster because it is '+(39.95/4.003).toFixed(1)+'× lighter and 3.16 = √10.</div>';
 $('revOut').innerHTML=h;S.predicted=true;done('s2');};

/* controls */
['gA','gB'].forEach(function(id){var h='';for(var k in GASES)h+='<option value="'+GASES[k]+'">'+k+' — '+GASES[k]+' g/mol</option>';$(id).innerHTML=h+'<option value="custom">custom</option>';});
function setMass(w,Mu){Mu=clamp(parseFloat(Mu),1,300);if(isNaN(Mu))Mu=DEF['m'+w];S['m'+w]=Mu;var nm=nameOf(Mu);$('g'+w).value=nm==='custom'?'custom':String(Mu);$('m'+w).value=Mu;}
$('gA').onchange=function(){if(this.value!=='custom'){setMass('A',this.value);resample('A');update();}};
$('gB').onchange=function(){if(this.value!=='custom'){setMass('B',this.value);resample('B');update();}};
$('mA').onchange=function(){setMass('A',this.value);resample('A');update();};
$('mB').onchange=function(){setMass('B',this.value);resample('B');update();};
['T','n','V'].forEach(function(k){$(k).addEventListener('input',function(){S[k]=parseFloat(this.value);update();done('s3');});});
$('spd').oninput=function(){S.speed=parseFloat(this.value);};
$('play').onclick=function(){S.playing=!S.playing;this.textContent=S.playing?'⏸ Pause':'▶ Play';};
$('swap').onclick=function(){var t=S.mA;setMass('A',S.mB);setMass('B',t);resample('A');resample('B');update();};
$('reset').onclick=function(){S.T=DEF.T;S.n=DEF.n;S.V=DEF.V;$('T').value=DEF.T;$('n').value=DEF.n;$('V').value=DEF.V;setMass('A',DEF.mA);setMass('B',DEF.mB);resample('A');resample('B');update();};
var LOADS={A:{T:300,mA:4.003,mB:39.95},C1:{T:50,mA:4.003,mB:39.95},C2:{T:1000,mA:2.016,mB:131.3}};
document.querySelectorAll('[data-load]').forEach(function(b){b.onclick=function(){var o=LOADS[b.dataset.load];S.T=o.T;$('T').value=o.T;S.n=0.4;$('n').value=0.4;S.V=0.01;$('V').value=0.01;
 setMass('A',o.mA);setMass('B',o.mB);resample('A');resample('B');update();done('s4');go('s3');};});

/* readouts */
var rows=[];
function update(){var A=gas(S.mA,S.T),B=gas(S.mB,S.T),nA=nameOf(S.mA),nB=nameOf(S.mB),P=S.n*R*S.T/S.V,Ut=1.5*S.n*R*S.T;
 $('Tv').textContent=S.T;$('nv').textContent=S.n;$('Vv').textContent=S.V.toFixed(3);
 var warn=(S.T<90&&(S.mA>39||S.mB>39))?'<div class="stat" style="grid-column:1/-1;background:#fee2e2">Below ~87 K argon and heavier gases are not gases — outside the model\'s scope.</div>':'';
 $('stats').innerHTML='<div class="stat"><small>v<sub>rms</sub> — <span class="A">A '+nA+'</span> / <span class="B">B '+nB+'</span></small><span class="big">'+A.vrms.toFixed(0)+' / '+B.vrms.toFixed(0)+' m/s</span><small>ratio '+(A.vrms/B.vrms).toFixed(2)+' = √(m<sub>B</sub>/m<sub>A</sub>)</small></div>'+
  '<div class="stat"><small>K<sub>avg</sub> per molecule — both gases</small><span class="big">'+A.K.toExponential(3)+' J</span><small>(3/2)k<sub>B</sub>T — identical</small></div>'+
  '<div class="stat"><small>Pressure — both boxes</small><span class="big">'+(P/1000).toFixed(1)+' kPa</span><small>Nk<sub>B</sub>T/V — identical; U = '+Ut.toFixed(0)+' J each</small></div>'+warn;
 rows=[['Molar mass M (g/mol)',S.mA.toFixed(3),S.mB.toFixed(3)],['Particle mass m (kg)',A.m.toExponential(3),B.m.toExponential(3)],['K_avg = (3/2)k_B T (J)',A.K.toExponential(4),B.K.toExponential(4)],
  ['v_rms (m/s)',A.vrms.toFixed(1),B.vrms.toFixed(1)],['v_avg (m/s)',A.vavg.toFixed(1),B.vavg.toFixed(1)],['v_mp (m/s)',A.vmp.toFixed(1),B.vmp.toFixed(1)],
  ['m·v_rms² = 3k_B T (J)',(A.m*A.vrms*A.vrms).toExponential(4),(B.m*B.vrms*B.vrms).toExponential(4)],['Momentum m·v_rms (kg·m/s)',(A.m*A.vrms).toExponential(3),(B.m*B.vrms).toExponential(3)],
  ['Relative wall‑collision rate (∝ v_rms)','1.000',(B.vrms/A.vrms).toFixed(3)],['Relative impulse per hit (∝ m·v_rms)','1.000',(B.m*B.vrms/(A.m*A.vrms)).toFixed(3)],['Rate × impulse (relative)','1.000',((B.vrms/A.vrms)*(B.m*B.vrms/(A.m*A.vrms))).toFixed(3)],
  ['Pressure P (kPa)',(P/1000).toFixed(2),(P/1000).toFixed(2)],['Translational U = N·K_avg (J)',Ut.toFixed(1),Ut.toFixed(1)]];
 var h='<tr><th>Quantity</th><th class="r A">Gas A — '+nA+'</th><th class="r B">Gas B — '+nB+'</th></tr>';rows.forEach(function(r,i){h+='<tr><td>'+(i+1)+'. '+r[0]+'</td><td class="r">'+r[1]+'</td><td class="r">'+r[2]+'</td></tr>';});$('table').innerHTML=h;graph();}
function dl(name,rs,head){var t=[head].concat(rs).map(function(r){return r.join(',');}).join('\n'),a=document.createElement('a');a.href=URL.createObjectURL(new Blob([t],{type:'text/csv'}));a.download=name;a.click();}
$('csv').onclick=function(){dl('t5_data.csv',rows.map(function(r){return[r[0].replace(/,/g,';'),r[1],r[2]];}),['Quantity','A_'+nameOf(S.mA),'B_'+nameOf(S.mB)]);};

/* MB graph — legend lives in a band above the plot so it never overlaps the curves */
var G={L:58,Rm:15,Tp:62,B:40,vmax:1000};
function graph(){var c=$('graph'),g=c.getContext('2d'),W=c.width,H=c.height,L=G.L,Rm=G.Rm,Tp=G.Tp,B=G.B,A=gas(S.mA,S.T),Bg=gas(S.mB,S.T);
 var vmax=Math.ceil(2.6*Math.max(A.vrms,Bg.vrms)/100)*100,fmax=Math.max(fMB(A.vmp,A.m,S.T),fMB(Bg.vmp,Bg.m,S.T))*1.08;G.vmax=vmax;g.clearRect(0,0,W,H);
 var x=function(v){return L+v/vmax*(W-L-Rm);},y=function(f){return H-B-f/fmax*(H-B-Tp);};
 /* legend band */
 g.fillStyle='#f6f8fb';g.fillRect(0,0,W,Tp-8);g.font='12px sans-serif';g.textAlign='left';
 g.fillStyle='#1f3b63';g.fillRect(10,10,14,4);g.fillText('A '+nameOf(S.mA)+': v_rms = '+A.vrms.toFixed(0)+' m/s',30,15);
 g.fillStyle='#be123c';g.fillRect(10,28,14,4);g.fillText('B '+nameOf(S.mB)+': v_rms = '+Bg.vrms.toFixed(0)+' m/s',30,33);
 g.fillStyle='#333';g.fillText('T = '+S.T+' K   both ⟨½mv²⟩ = '+A.K.toExponential(2)+' J   dashed = v_rms',W-320,24);
 /* axes */
 g.strokeStyle='#333';g.lineWidth=1;g.beginPath();g.moveTo(L,Tp);g.lineTo(L,H-B);g.lineTo(W-Rm,H-B);g.stroke();
 g.fillStyle='#333';g.font='11px sans-serif';g.textAlign='center';for(var v=0;v<=vmax+1;v+=vmax/5)g.fillText(v.toFixed(0),x(v),H-B+14);g.fillText('speed v (m/s)',(L+W-Rm)/2,H-8);
 g.textAlign='right';for(var i=0;i<=4;i++)g.fillText((fmax*i/4).toExponential(1),L-4,y(fmax*i/4)+4);
 g.save();g.translate(12,(Tp+H-B)/2);g.rotate(-Math.PI/2);g.textAlign='center';g.fillText('f(v) (s/m)',0,0);g.restore();
 /* curves */
 function curve(Gs,col){g.strokeStyle=col;g.lineWidth=2.2;g.beginPath();for(var k=0;k<=300;k++){var vv=vmax*k/300,Y=y(fMB(vv,Gs.m,S.T));k?g.lineTo(x(vv),Y):g.moveTo(x(vv),Y);}g.stroke();
  g.setLineDash([5,4]);g.lineWidth=1.3;g.beginPath();g.moveTo(x(Gs.vrms),H-B);g.lineTo(x(Gs.vrms),y(fMB(Gs.vrms,Gs.m,S.T)));g.stroke();g.setLineDash([]);}
 curve(Bg,'#be123c');curve(A,'#1f3b63');
 /* hover readout anchored bottom‑right */
 if(S.hover!==null){var hv=S.hover;g.strokeStyle='#888';g.setLineDash([3,3]);g.beginPath();g.moveTo(x(hv),Tp);g.lineTo(x(hv),H-B);g.stroke();g.setLineDash([]);
  var bw=180,bh=48,tx=W-Rm-bw,ty=H-B-bh-6;g.fillStyle='rgba(255,255,255,.95)';g.fillRect(tx,ty,bw,bh);g.strokeStyle='#ccc';g.strokeRect(tx,ty,bw,bh);
  g.font='12px sans-serif';g.textAlign='left';g.fillStyle='#000';g.fillText('v = '+hv.toFixed(0)+' m/s',tx+8,ty+15);
  g.fillStyle='#1f3b63';g.fillText('f_A = '+fMB(hv,A.m,S.T).toExponential(2),tx+8,ty+29);g.fillStyle='#be123c';g.fillText('f_B = '+fMB(hv,Bg.m,S.T).toExponential(2),tx+8,ty+43);}}
(function(){var c=$('graph');c.onmousemove=function(e){var r=c.getBoundingClientRect(),mx=(e.clientX-r.left)*c.width/r.width,v=(mx-G.L)/(c.width-G.L-G.Rm)*G.vmax;S.hover=(v>=0&&v<=G.vmax)?v:null;graph();};c.onmouseleave=function(){S.hover=null;graph();};})();

/* animation */
var AN={bw:220,bh:195,y:28,xA:25,xB:275},dots={A:[],B:[]};
function gauss(){var u=0,v=0;while(!u)u=Math.random();while(!v)v=Math.random();return Math.sqrt(-2*Math.log(u))*Math.cos(2*Math.PI*v);}
function resample(w){var a=[];for(var i=0;i<40;i++){var gx=gauss(),gy=gauss(),gz=gauss(),th=Math.random()*6.283;a.push({x:Math.random(),y:Math.random(),dx:Math.cos(th),dy:Math.sin(th),s:Math.sqrt((gx*gx+gy*gy+gz*gz)/3)});}dots[w]=a;}
resample('A');resample('B');
function anim(dt){var c=$('anim'),g=c.getContext('2d');g.clearRect(0,0,c.width,c.height);var A=gas(S.mA,S.T),Bg=gas(S.mB,S.T),P=S.n*R*S.T/S.V;
 g.fillStyle='#fde4c0';g.fillRect(15,AN.y+AN.bh,490,26);g.fillStyle='#7a4a00';g.font='12px sans-serif';g.textAlign='center';g.fillText('shared thermal reservoir, T = '+S.T+' K',260,AN.y+AN.bh+17);
 function box(x0,Gs,arr,col,lab){g.fillStyle='#f6f8fb';g.fillRect(x0,AN.y,AN.bw,AN.bh);g.strokeStyle='#555';g.lineWidth=3;g.strokeRect(x0,AN.y,AN.bw,AN.bh);
  var rad=2+0.45*Math.sqrt(Gs.Mu),px=Gs.vrms/6*S.speed*dt;g.fillStyle=col;
  arr.forEach(function(p){if(S.playing){p.x+=p.dx*p.s*px/AN.bw;p.y+=p.dy*p.s*px/AN.bh;if(p.x<0){p.x=-p.x;p.dx=-p.dx;}if(p.x>1){p.x=2-p.x;p.dx=-p.dx;}if(p.y<0){p.y=-p.y;p.dy=-p.dy;}if(p.y>1){p.y=2-p.y;p.dy=-p.dy;}}
   g.beginPath();g.arc(x0+p.x*AN.bw,AN.y+p.y*AN.bh,rad,0,6.283);g.fill();});
  g.fillStyle=col;g.font='bold 13px sans-serif';g.textAlign='left';g.fillText(lab,x0,AN.y-10);g.fillStyle='#000';g.font='12px sans-serif';
  g.fillText('v_rms = '+Gs.vrms.toFixed(0)+' m/s    K_avg = '+Gs.K.toExponential(2)+' J',x0,AN.y+AN.bh+44);
  g.fillText('N = '+(S.n*NA).toExponential(2)+'   V = '+S.V+' m³',x0,AN.y+AN.bh+60);
  g.fillStyle='#ddd';g.fillRect(x0,AN.y+AN.bh+68,AN.bw,10);g.fillStyle='#15803d';g.fillRect(x0,AN.y+AN.bh+68,Math.min(AN.bw,AN.bw*P/400000),10);g.fillStyle='#000';g.fillText('P = '+(P/1000).toFixed(1)+' kPa',x0,AN.y+AN.bh+92);}
 box(AN.xA,A,dots.A,'#1f3b63','Gas A: '+nameOf(S.mA)+' ('+S.mA+' u)');box(AN.xB,Bg,dots.B,'#be123c','Gas B: '+nameOf(S.mB)+' ('+S.mB+' u)');}

/* sweep */
var presets={m:'4.003,20.18,39.95,83.80,131.3',T:'100,200,300,400,500'},sw=[];
$('swVar').onchange=function(){$('swVals').value=presets[this.value];held();};
function held(){var k=$('swVar').value;$('swHeld').innerHTML='<b>Held constant:</b> '+(k==='m'?'T = '+S.T+' K, ':'')+'Gas B = '+nameOf(S.mB)+(k==='T'?', Gas A = '+nameOf(S.mA):'')+', n = '+S.n+' mol, V = '+S.V+' m³';}
function yv(Gs,yk){return{vrms:Gs.vrms,v2:Gs.vrms*Gs.vrms,K:Gs.K,p:Gs.m*Gs.vrms}[yk];}
$('swRun').onclick=function(){var k=$('swVar').value,yk=$('swY').value,vals=$('swVals').value.split(',').map(parseFloat).filter(function(v){return v>0;});if(vals.length<2){alert('Enter at least two values.');return;}
 var yl={vrms:'v_rms (m/s)',v2:'v_rms² (m²/s²)',K:'K_avg (J)',p:'m·v_rms (kg·m/s)'}[yk],xl=k==='m'?'mass of Gas A (u)':'T (K)';
 sw=vals.map(function(v){return{x:v,A:k==='m'?gas(v,S.T):gas(S.mA,v),B:k==='m'?null:gas(S.mB,v)};});
 var h='<tr><th>'+xl+'</th><th class="r A">A v_rms</th><th class="r A">A K_avg</th><th class="r A">A m·v²</th>'+(k==='T'?'<th class="r B">B v_rms</th><th class="r B">B K_avg</th>':'')+'</tr>';
 sw.forEach(function(r){h+='<tr><td>'+r.x+'</td><td class="r">'+r.A.vrms.toFixed(0)+'</td><td class="r">'+r.A.K.toExponential(3)+'</td><td class="r">'+(r.A.m*r.A.vrms*r.A.vrms).toExponential(3)+'</td>'+(r.B?'<td class="r">'+r.B.vrms.toFixed(0)+'</td><td class="r">'+r.B.K.toExponential(3)+'</td>':'')+'</tr>';});
 $('swTable').innerHTML=h;held();done('s4');
 var c=$('swGraph'),g=c.getContext('2d'),W=c.width,H=c.height,L=80,Rm=15,Tp=20,B=42;g.clearRect(0,0,W,H);
 var ys=[];sw.forEach(function(r){ys.push(yv(r.A,yk));if(r.B)ys.push(yv(r.B,yk));});var xmax=Math.max.apply(null,vals)*1.05,ymax=Math.max.apply(null,ys)*1.15||1;
 var x=function(v){return L+v/xmax*(W-L-Rm);},y=function(v){return H-B-v/ymax*(H-B-Tp);},fmt=function(v){return(v<1e-3||v>1e5)?v.toExponential(2):v.toFixed(0);};
 g.strokeStyle='#333';g.lineWidth=1;g.beginPath();g.moveTo(L,Tp);g.lineTo(L,H-B);g.lineTo(W-Rm,H-B);g.stroke();g.fillStyle='#333';g.font='11px sans-serif';
 g.textAlign='right';for(var i=0;i<=5;i++)g.fillText(fmt(ymax*i/5),L-6,y(ymax*i/5)+4);g.textAlign='center';vals.forEach(function(v){g.fillText(String(v),x(v),H-B+14);});g.fillText(xl,(L+W-Rm)/2,H-6);
 g.save();g.translate(14,(Tp+H-B)/2);g.rotate(-Math.PI/2);g.fillText(yl,0,0);g.restore();
 function series(getG,col){g.strokeStyle=col;g.setLineDash([4,4]);g.lineWidth=1.3;g.beginPath();for(var j=1;j<=80;j++){var v=xmax*j/80,Y=yv(getG(v),yk);j===1?g.moveTo(x(v),y(Y)):g.lineTo(x(v),y(Y));}g.stroke();g.setLineDash([]);
  vals.forEach(function(v){var Y=yv(getG(v),yk);g.fillStyle=col;g.beginPath();g.arc(x(v),y(Y),5,0,6.283);g.fill();g.fillStyle='#000';g.textAlign='center';g.fillText(fmt(Y),x(v),y(Y)-10);});}
 if(k==='m')series(function(v){return gas(v,S.T);},'#1f3b63');else{series(function(v){return gas(S.mA,v);},'#1f3b63');series(function(v){return gas(S.mB,v);},'#be123c');}
 g.fillStyle='#555';g.textAlign='left';g.fillText(yl+' vs '+xl+' — dashed = continuous model, dots = your five values',L+6,Tp+10);};
$('swCsv').onclick=function(){if(!sw.length)return alert('Run a sweep first.');var k=$('swVar').value;dl('t5_sweep.csv',sw.map(function(r){return[r.x,r.A.vrms.toFixed(2),r.A.K.toExponential(4),r.B?r.B.vrms.toFixed(2):'',r.B?r.B.K.toExponential(4):''];}),[k==='m'?'mA_u':'T_K','A_vrms','A_K','B_vrms','B_K']);};

/* tests */
var TESTS=[
 ['Normal','K_avg He 300 K','1.5(1.381×10⁻²³)(300) = 6.213×10⁻²¹ J',6.213e-21,function(){return gas(4.003,300).K;},.005],
 ['Normal','K_avg Ar / K_avg He','only T matters ⇒ exactly 1',1,function(){return gas(39.95,300).K/gas(4.003,300).K;},1e-12],
 ['Normal','v_rms He 300 K','√(7483/0.004003) = 1367 m/s',1367,function(){return gas(4.003,300).vrms;},.005],
 ['Normal','v_rms Ar 300 K','√(7483/0.03995) = 432.8 m/s',432.8,function(){return gas(39.95,300).vrms;},.005],
 ['Ratio','v_He / v_Ar','√(39.95/4.003) = 3.159',3.159,function(){return gas(4.003,300).vrms/gas(39.95,300).vrms;},.005],
 ['Pressure','P, 0.4 mol, 0.010 m³, 300 K','0.4·8.314·300/0.010 = 99 768 Pa',99768,function(){return .4*R*300/.01;},.005],
 ['Equal mv²','m·v² He / Ar','3k_BT both ⇒ 1',1,function(){var a=gas(4.003,300),b=gas(39.95,300);return a.m*a.vrms*a.vrms/(b.m*b.vrms*b.vrms);},1e-12],
 ['Textbook','v_rms N₂ 300 K (Ling et al.)','517 m/s',517,function(){return gas(28.01,300).vrms;},.005],
 ['Scaling','v ratio for T×2','√2 = 1.4142',1.4142,function(){return gas(4.003,600).vrms/gas(4.003,300).vrms;},.001],
 ['Limiting','v ratio for m×4','1/√4 = 0.500',.5,function(){return gas(16,300).vrms/gas(4,300).vrms;},1e-9],
 ['Boundary','H₂ 1000 K','√(3·8.314·1000/0.002016) = 3518 m/s (valid)',3518,function(){return gas(2.016,1000).vrms;},.005],
 ['Boundary','Ar 50 K','432.8·√(50/300) = 176.7 m/s — Ar is solid here (outside scope)',176.7,function(){return gas(39.95,50).vrms;},.005],
 ['Distribution','v_mp / v_rms','√(2/3) = 0.8165',.8165,function(){var a=gas(4.003,300);return a.vmp/a.vrms;},1e-9]];
$('runTests').onclick=function(){var h='<tr><th>Type</th><th>Check</th><th>Expected (by hand)</th><th class="r">Observed</th><th class="r">Error</th><th>Result</th></tr>';
 TESTS.forEach(function(t){var o=t[4](),e=Math.abs(o-t[3])/Math.abs(t[3]),ok=e<=t[5];h+='<tr><td>'+t[0]+'</td><td>'+t[1]+'</td><td>'+t[2]+'</td><td class="r">'+(Math.abs(o)<1e-3?o.toExponential(4):Math.abs(o)<10?o.toFixed(4):o.toFixed(1))+'</td><td class="r">'+(e*100).toExponential(2)+' %</td><td class="'+(ok?'pass':'fail')+'">'+(ok?'PASS':'FAIL')+'</td></tr>';});
 $('testTable').innerHTML=h;done('s6');};

function loop(ts){var dt=S.last?Math.min((ts-S.last)/1000,.05):0;S.last=ts;anim(dt);requestAnimationFrame(loop);}
setMass('A',DEF.mA);setMass('B',DEF.mB);update();held();$('runTests').click();requestAnimationFrame(loop);
})();
</script>
</body>
</html>

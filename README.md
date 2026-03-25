<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MANUEL'S 90-DAY WAR</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Space+Mono:wght@400;700&family=DM+Sans:wght@300;400;500;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0a;
    --surface: #111111;
    --surface2: #1a1a1a;
    --border: #222222;
    --accent: #ff4500;
    --accent2: #ffaa00;
    --green: #00e676;
    --text: #f0f0f0;
    --muted: #555;
    --red: #ff1744;
  }

- { margin: 0; padding: 0; box-sizing: border-box; }

body {
background: var(–bg);
color: var(–text);
font-family: ‘DM Sans’, sans-serif;
min-height: 100vh;
overflow-x: hidden;
}

/* Noise texture overlay */
body::before {
content: ‘’;
position: fixed;
inset: 0;
background-image: url(“data:image/svg+xml,%3Csvg viewBox=‘0 0 256 256’ xmlns=‘http://www.w3.org/2000/svg’%3E%3Cfilter id=‘noise’%3E%3CfeTurbulence type=‘fractalNoise’ baseFrequency=‘0.9’ numOctaves=‘4’ stitchTiles=‘stitch’/%3E%3C/filter%3E%3Crect width=‘100%25’ height=‘100%25’ filter=‘url(%23noise)’ opacity=‘0.03’/%3E%3C/svg%3E”);
pointer-events: none;
z-index: 1000;
}

/* HEADER */
.header {
padding: 24px 20px 0;
position: relative;
}

.war-title {
font-family: ‘Bebas Neue’, sans-serif;
font-size: clamp(52px, 15vw, 96px);
line-height: 0.9;
letter-spacing: 2px;
background: linear-gradient(135deg, #ff4500, #ffaa00);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
background-clip: text;
}

.war-subtitle {
font-family: ‘Space Mono’, monospace;
font-size: 11px;
color: var(–muted);
letter-spacing: 3px;
text-transform: uppercase;
margin-top: 4px;
}

/* BODY ANALYSIS CARD */
.analysis-card {
margin: 20px;
background: var(–surface);
border: 1px solid var(–border);
border-left: 4px solid var(–accent);
padding: 20px;
border-radius: 4px;
}

.analysis-title {
font-family: ‘Space Mono’, monospace;
font-size: 10px;
color: var(–accent);
letter-spacing: 3px;
text-transform: uppercase;
margin-bottom: 14px;
}

.body-stats {
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 12px;
margin-bottom: 16px;
}

.stat-box {
background: var(–surface2);
padding: 12px;
border-radius: 4px;
text-align: center;
}

.stat-num {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 28px;
color: var(–accent2);
display: block;
}

.stat-label {
font-size: 10px;
color: var(–muted);
text-transform: uppercase;
letter-spacing: 1px;
}

.analysis-text {
font-size: 13px;
line-height: 1.7;
color: #aaa;
}

.analysis-text strong {
color: var(–text);
}

.fat-zones {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 8px;
margin-top: 14px;
}

.fat-zone {
background: var(–surface2);
padding: 10px 12px;
border-radius: 4px;
font-size: 12px;
display: flex;
align-items: center;
gap: 8px;
}

.zone-dot {
width: 8px; height: 8px;
border-radius: 50%;
flex-shrink: 0;
}

/* WEIGHT TRACKER */
.section {
margin: 0 20px 20px;
}

.section-header {
font-family: ‘Space Mono’, monospace;
font-size: 10px;
color: var(–accent);
letter-spacing: 3px;
text-transform: uppercase;
margin-bottom: 12px;
display: flex;
justify-content: space-between;
align-items: center;
}

.weight-input-row {
display: flex;
gap: 10px;
margin-bottom: 14px;
}

.weight-input {
flex: 1;
background: var(–surface);
border: 1px solid var(–border);
color: var(–text);
padding: 12px 16px;
border-radius: 4px;
font-family: ‘Space Mono’, monospace;
font-size: 16px;
outline: none;
transition: border-color 0.2s;
}

.weight-input:focus { border-color: var(–accent); }

.log-btn {
background: var(–accent);
color: white;
border: none;
padding: 12px 20px;
border-radius: 4px;
font-family: ‘Bebas Neue’, sans-serif;
font-size: 18px;
letter-spacing: 1px;
cursor: pointer;
transition: background 0.2s, transform 0.1s;
}

.log-btn:active { transform: scale(0.97); }
.log-btn:hover { background: #ff6030; }

/* PROGRESS BAR */
.progress-container {
background: var(–surface);
border: 1px solid var(–border);
padding: 20px;
border-radius: 4px;
margin-bottom: 14px;
}

.progress-labels {
display: flex;
justify-content: space-between;
margin-bottom: 10px;
font-family: ‘Space Mono’, monospace;
font-size: 11px;
color: var(–muted);
}

.progress-bar-bg {
height: 12px;
background: var(–surface2);
border-radius: 6px;
overflow: hidden;
margin-bottom: 10px;
}

.progress-bar-fill {
height: 100%;
background: linear-gradient(90deg, var(–accent), var(–accent2));
border-radius: 6px;
transition: width 0.5s ease;
}

.progress-pct {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 42px;
color: var(–accent2);
text-align: center;
display: block;
}

.progress-desc {
text-align: center;
font-size: 12px;
color: var(–muted);
margin-top: 2px;
}

/* WEIGHT CHART */
.chart-area {
background: var(–surface);
border: 1px solid var(–border);
padding: 16px;
border-radius: 4px;
margin-bottom: 14px;
position: relative;
height: 160px;
overflow: hidden;
}

.chart-svg {
width: 100%;
height: 100%;
}

.chart-label {
font-family: ‘Space Mono’, monospace;
font-size: 9px;
fill: var(–muted);
}

/* 90 DAY GRID */
.day-grid {
display: grid;
grid-template-columns: repeat(10, 1fr);
gap: 4px;
background: var(–surface);
border: 1px solid var(–border);
padding: 16px;
border-radius: 4px;
}

.day-cell {
aspect-ratio: 1;
border-radius: 3px;
background: var(–surface2);
cursor: pointer;
transition: all 0.15s;
display: flex;
align-items: center;
justify-content: center;
font-size: 8px;
font-family: ‘Space Mono’, monospace;
color: transparent;
border: 1px solid transparent;
position: relative;
}

.day-cell:hover { border-color: var(–accent); color: var(–muted); }
.day-cell.completed { background: var(–green); }
.day-cell.completed-gym { background: var(–accent); }
.day-cell.completed-both { background: linear-gradient(135deg, var(–green), var(–accent2)); }
.day-cell.today { border: 2px solid var(–accent2); animation: pulse-cell 2s infinite; }
.day-cell.future { opacity: 0.3; cursor: default; }

@keyframes pulse-cell {
0%, 100% { border-color: var(–accent2); }
50% { border-color: transparent; }
}

/* DAILY CHECKLIST */
.checklist {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 4px;
overflow: hidden;
margin-bottom: 14px;
}

.checklist-item {
display: flex;
align-items: center;
padding: 14px 16px;
border-bottom: 1px solid var(–border);
cursor: pointer;
transition: background 0.15s;
gap: 14px;
}

.checklist-item:last-child { border-bottom: none; }
.checklist-item:hover { background: var(–surface2); }
.checklist-item.done { opacity: 0.5; }

.check-box {
width: 22px; height: 22px;
border: 2px solid var(–border);
border-radius: 3px;
flex-shrink: 0;
display: flex;
align-items: center;
justify-content: center;
font-size: 13px;
transition: all 0.2s;
}

.checklist-item.done .check-box {
background: var(–green);
border-color: var(–green);
}

.check-text {
flex: 1;
font-size: 14px;
}

.check-text .check-sub {
font-size: 11px;
color: var(–muted);
display: block;
margin-top: 2px;
font-family: ‘Space Mono’, monospace;
}

.check-xp {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 18px;
color: var(–accent2);
}

/* XP / LEVEL DISPLAY */
.xp-card {
background: var(–surface);
border: 1px solid var(–border);
padding: 20px;
border-radius: 4px;
margin-bottom: 14px;
position: relative;
overflow: hidden;
}

.xp-card::before {
content: ‘’;
position: absolute;
top: -30px; right: -30px;
width: 120px; height: 120px;
background: radial-gradient(circle, rgba(255,170,0,0.1), transparent 70%);
border-radius: 50%;
}

.level-row {
display: flex;
align-items: baseline;
gap: 12px;
margin-bottom: 12px;
}

.level-num {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 64px;
color: var(–accent2);
line-height: 1;
}

.level-info { flex: 1; }
.level-title {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 22px;
color: var(–text);
letter-spacing: 1px;
}

.xp-bar-bg {
height: 8px;
background: var(–surface2);
border-radius: 4px;
overflow: hidden;
margin-bottom: 6px;
}

.xp-bar-fill {
height: 100%;
background: linear-gradient(90deg, var(–accent2), #ffe066);
border-radius: 4px;
transition: width 0.4s ease;
}

.xp-text {
font-family: ‘Space Mono’, monospace;
font-size: 10px;
color: var(–muted);
}

/* STREAK */
.streak-row {
display: flex;
gap: 12px;
margin-bottom: 14px;
}

.streak-card {
flex: 1;
background: var(–surface);
border: 1px solid var(–border);
padding: 14px;
border-radius: 4px;
text-align: center;
}

.streak-num {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 40px;
display: block;
}

.streak-label {
font-family: ‘Space Mono’, monospace;
font-size: 9px;
color: var(–muted);
text-transform: uppercase;
letter-spacing: 2px;
}

/* MILESTONES */
.milestone-list {
display: flex;
flex-direction: column;
gap: 8px;
}

.milestone {
background: var(–surface);
border: 1px solid var(–border);
padding: 14px 16px;
border-radius: 4px;
display: flex;
align-items: center;
gap: 14px;
}

.milestone.unlocked {
border-left: 4px solid var(–green);
}

.milestone.locked {
opacity: 0.4;
}

.milestone-icon {
font-size: 24px;
flex-shrink: 0;
}

.milestone-info { flex: 1; }

.milestone-name {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 18px;
letter-spacing: 1px;
}

.milestone-desc {
font-size: 11px;
color: var(–muted);
font-family: ‘Space Mono’, monospace;
}

.milestone-badge {
font-family: ‘Space Mono’, monospace;
font-size: 10px;
padding: 4px 8px;
border-radius: 3px;
}

.milestone.unlocked .milestone-badge {
background: var(–green);
color: #000;
}

.milestone.locked .milestone-badge {
background: var(–surface2);
color: var(–muted);
border: 1px solid var(–border);
}

/* TOAST */
.toast {
position: fixed;
bottom: 20px;
left: 50%;
transform: translateX(-50%) translateY(100px);
background: var(–accent2);
color: #000;
padding: 12px 24px;
border-radius: 4px;
font-family: ‘Bebas Neue’, sans-serif;
font-size: 20px;
letter-spacing: 1px;
transition: transform 0.3s ease;
z-index: 999;
white-space: nowrap;
}

.toast.show { transform: translateX(-50%) translateY(0); }

/* NAV */
.nav {
position: sticky;
top: 0;
background: rgba(10,10,10,0.95);
backdrop-filter: blur(10px);
border-bottom: 1px solid var(–border);
z-index: 100;
display: flex;
overflow-x: auto;
scrollbar-width: none;
padding: 0 12px;
}

.nav::-webkit-scrollbar { display: none; }

.nav-btn {
background: none;
border: none;
color: var(–muted);
font-family: ‘Space Mono’, monospace;
font-size: 10px;
letter-spacing: 2px;
text-transform: uppercase;
padding: 14px 16px;
cursor: pointer;
white-space: nowrap;
border-bottom: 2px solid transparent;
transition: all 0.2s;
}

.nav-btn:hover { color: var(–text); }
.nav-btn.active { color: var(–accent); border-bottom-color: var(–accent); }

/* PANELS */
.panel { display: none; padding-bottom: 60px; }
.panel.active { display: block; }

/* MEALS PANEL */
.meal-card {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 4px;
overflow: hidden;
margin-bottom: 10px;
}

.meal-header {
padding: 12px 16px;
display: flex;
justify-content: space-between;
align-items: center;
border-bottom: 1px solid var(–border);
cursor: pointer;
}

.meal-time {
font-family: ‘Space Mono’, monospace;
font-size: 11px;
color: var(–accent2);
}

.meal-name {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 20px;
letter-spacing: 1px;
}

.meal-macros {
font-family: ‘Space Mono’, monospace;
font-size: 10px;
color: var(–muted);
}

.meal-body {
padding: 14px 16px;
font-size: 13px;
color: #bbb;
line-height: 1.7;
}

.macro-chips {
display: flex;
gap: 8px;
margin-top: 10px;
flex-wrap: wrap;
}

.macro-chip {
background: var(–surface2);
padding: 4px 10px;
border-radius: 20px;
font-family: ‘Space Mono’, monospace;
font-size: 10px;
}

.macro-chip.protein { color: #64b5f6; }
.macro-chip.carb { color: var(–accent2); }
.macro-chip.fat { color: #ef9a9a; }
.macro-chip.cal { color: var(–green); }

/* TRAINING PANEL */
.phase-tag {
display: inline-block;
background: var(–accent);
color: white;
font-family: ‘Space Mono’, monospace;
font-size: 9px;
padding: 3px 8px;
border-radius: 3px;
letter-spacing: 2px;
text-transform: uppercase;
margin-bottom: 12px;
}

.workout-card {
background: var(–surface);
border: 1px solid var(–border);
border-radius: 4px;
margin-bottom: 10px;
overflow: hidden;
}

.workout-day-header {
padding: 14px 16px;
display: flex;
justify-content: space-between;
align-items: center;
cursor: pointer;
transition: background 0.15s;
}

.workout-day-header:hover { background: var(–surface2); }

.workout-day-name {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 22px;
letter-spacing: 1px;
}

.workout-tag {
font-family: ‘Space Mono’, monospace;
font-size: 9px;
padding: 3px 8px;
border-radius: 3px;
background: var(–surface2);
color: var(–accent2);
border: 1px solid var(–border);
}

.workout-exercises {
border-top: 1px solid var(–border);
display: none;
}

.workout-card.open .workout-exercises { display: block; }

.exercise-row {
padding: 10px 16px;
border-bottom: 1px solid var(–border);
display: flex;
justify-content: space-between;
align-items: center;
}

.exercise-row:last-child { border-bottom: none; }

.exercise-name {
font-size: 13px;
font-weight: 500;
}

.exercise-sets {
font-family: ‘Space Mono’, monospace;
font-size: 11px;
color: var(–accent2);
}

/* Responsive tweaks */
@media (max-width: 380px) {
.body-stats { grid-template-columns: repeat(3, 1fr); gap: 8px; }
.stat-num { font-size: 22px; }
.day-grid { gap: 3px; }
}

.divider {
height: 1px;
background: var(–border);
margin: 6px 0;
}

.alert-box {
background: rgba(255,69,0,0.08);
border: 1px solid rgba(255,69,0,0.3);
border-radius: 4px;
padding: 12px 14px;
font-size: 12px;
color: #ffaa88;
line-height: 1.6;
margin-bottom: 14px;
}

.alert-box strong { color: var(–accent); }
</style>

</head>
<body>

<div class="header">
  <div class="war-title">90-DAY<br>WAR</div>
  <div class="war-subtitle">▸ MANUEL'S TRANSFORMATION CHALLENGE ▸ START WEIGHT: 106KG ▸ TARGET: 83KG</div>
</div>

<nav class="nav">
  <button class="nav-btn active" onclick="showPanel('dashboard')">Dashboard</button>
  <button class="nav-btn" onclick="showPanel('checklist')">Today</button>
  <button class="nav-btn" onclick="showPanel('meals')">Meals</button>
  <button class="nav-btn" onclick="showPanel('training')">Training</button>
  <button class="nav-btn" onclick="showPanel('milestones')">Trophies</button>
</nav>

<!-- DASHBOARD PANEL -->

<div id="panel-dashboard" class="panel active">
  <div style="padding: 20px 20px 0;">

```
<!-- XP CARD -->
<div class="xp-card" id="xp-card">
  <div class="level-row">
    <div class="level-num" id="level-num">1</div>
    <div class="level-info">
      <div class="level-title" id="level-title">RECRUIT</div>
      <div class="xp-bar-bg">
        <div class="xp-bar-fill" id="xp-bar" style="width:0%"></div>
      </div>
      <div class="xp-text"><span id="xp-current">0</span> / <span id="xp-next">200</span> XP to next level</div>
    </div>
  </div>
</div>

<!-- STREAK ROW -->
<div class="streak-row">
  <div class="streak-card">
    <span class="streak-num" id="streak-num" style="color: var(--accent);">0</span>
    <span class="streak-label">🔥 Day Streak</span>
  </div>
  <div class="streak-card">
    <span class="streak-num" id="days-done" style="color: var(--accent2);">0</span>
    <span class="streak-label">📅 Days Done</span>
  </div>
  <div class="streak-card">
    <span class="streak-num" id="days-left" style="color: var(--green);">90</span>
    <span class="streak-label">⚡ Days Left</span>
  </div>
</div>

<!-- BODY ANALYSIS -->
<div class="analysis-card">
  <div class="analysis-title">▸ Body Analysis — Day 0</div>
  <div class="body-stats">
    <div class="stat-box">
      <span class="stat-num">106</span>
      <span class="stat-label">kg now</span>
    </div>
    <div class="stat-box">
      <span class="stat-num">83</span>
      <span class="stat-label">kg target</span>
    </div>
    <div class="stat-box">
      <span class="stat-num" style="color: var(--red);">~35%</span>
      <span class="stat-label">body fat est.</span>
    </div>
  </div>
  <p class="analysis-text">
    From your photos: <strong>heavy visceral and subcutaneous fat concentrated in the abdomen, lower chest, and flanks.</strong> You have visible love handles with significant back fat accumulation (seen in rear photo). Upper arms are full. The good news — your frame carries muscle underneath. You're not starting from zero.
    <br><br>
    <strong>Key observation:</strong> The belly shape suggests elevated visceral fat — the dangerous kind around organs. This is actually the fastest-responding fat to diet + exercise. You'll see rapid change in weeks 3–4 if you stay locked in.
  </p>
  <div class="fat-zones">
    <div class="fat-zone"><div class="zone-dot" style="background:#ff4500"></div><span>Belly / Visceral — HIGH</span></div>
    <div class="fat-zone"><div class="zone-dot" style="background:#ff4500"></div><span>Lower Back — HIGH</span></div>
    <div class="fat-zone"><div class="zone-dot" style="background:#ffaa00"></div><span>Chest / Moobs — MED</span></div>
    <div class="fat-zone"><div class="zone-dot" style="background:#ffaa00"></div><span>Upper Arms — MED</span></div>
  </div>
</div>

<!-- WEIGHT TRACKER -->
<div class="section-header">
  ▸ Weight Log
  <span id="current-weight-display" style="color: var(--text); font-size: 14px;">— kg</span>
</div>

<div class="weight-input-row">
  <input class="weight-input" type="number" id="weight-input" placeholder="Enter kg (e.g. 105.4)" step="0.1" min="60" max="200">
  <button class="log-btn" onclick="logWeight()">LOG</button>
</div>

<!-- PROGRESS BAR -->
<div class="progress-container">
  <div class="progress-labels">
    <span>START: 106 KG</span>
    <span>GOAL: 83 KG</span>
  </div>
  <div class="progress-bar-bg">
    <div class="progress-bar-fill" id="weight-progress-bar" style="width:0%"></div>
  </div>
  <span class="progress-pct" id="progress-pct">0%</span>
  <div class="progress-desc" id="progress-desc">Log your weight to begin tracking</div>
</div>

<!-- CHART -->
<div class="chart-area">
  <svg class="chart-svg" id="weight-chart" viewBox="0 0 300 130" preserveAspectRatio="none">
    <text x="4" y="14" class="chart-label">106</text>
    <text x="4" y="75" class="chart-label">94</text>
    <text x="4" y="120" class="chart-label">83</text>
    <line x1="30" y1="10" x2="30" y2="125" stroke="#222" stroke-width="0.5"/>
    <line x1="30" y1="125" x2="295" y2="125" stroke="#222" stroke-width="0.5"/>
    <!-- Target line -->
    <line x1="30" y1="115" x2="295" y2="115" stroke="#333" stroke-width="1" stroke-dasharray="4,3"/>
    <text x="235" y="111" class="chart-label" style="fill:#555">TARGET</text>
    <polyline id="chart-line" points="30,10" fill="none" stroke="url(#grad)" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"/>
    <circle id="chart-dot" cx="30" cy="10" r="4" fill="#ff4500" style="display:none"/>
    <defs>
      <linearGradient id="grad" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" style="stop-color:#ff4500"/>
        <stop offset="100%" style="stop-color:#ffaa00"/>
      </linearGradient>
    </defs>
  </svg>
</div>

<!-- 90 DAY GRID -->
<div class="section-header">▸ 90-Day Grid</div>
<div class="day-grid" id="day-grid"></div>
<div style="display:flex; gap:12px; margin-top:10px; flex-wrap:wrap;">
  <div style="display:flex; align-items:center; gap:6px; font-size:11px; color:var(--muted)">
    <div style="width:12px;height:12px;background:var(--green);border-radius:2px"></div> Diet done
  </div>
  <div style="display:flex; align-items:center; gap:6px; font-size:11px; color:var(--muted)">
    <div style="width:12px;height:12px;background:var(--accent);border-radius:2px"></div> Gym done
  </div>
  <div style="display:flex; align-items:center; gap:6px; font-size:11px; color:var(--muted)">
    <div style="width:12px;height:12px;background:linear-gradient(135deg,var(--green),var(--accent2));border-radius:2px"></div> Both done
  </div>
</div>
```

  </div>
</div>

<!-- TODAY / CHECKLIST PANEL -->

<div id="panel-checklist" class="panel">
  <div style="padding: 20px 20px 0;">

```
<div class="section-header">
  ▸ Today's Missions
  <span id="today-xp-display" style="color: var(--accent2);">0 XP earned</span>
</div>

<div class="alert-box">
  <strong>RULE #1:</strong> Complete all 7 missions = Full day. Miss gym = half day. Miss diet = you restart the streak. No exceptions.
</div>

<div class="checklist" id="checklist">
  <div class="checklist-item" onclick="toggleCheck(0)" id="check-0">
    <div class="check-box">✓</div>
    <div class="check-text">
      Fasted Morning Walk (45 min)
      <span class="check-sub">6:30 AM — brisk pace, no food</span>
    </div>
    <div class="check-xp">+30</div>
  </div>
  <div class="checklist-item" onclick="toggleCheck(1)" id="check-1">
    <div class="check-box">✓</div>
    <div class="check-text">
      4L Water Target
      <span class="check-sub">500ml on wake + with every meal</span>
    </div>
    <div class="check-xp">+20</div>
  </div>
  <div class="checklist-item" onclick="toggleCheck(2)" id="check-2">
    <div class="check-box">✓</div>
    <div class="check-text">
      IF Window Respected (16:8)
      <span class="check-sub">No food before 12 PM — fast from 8 PM</span>
    </div>
    <div class="check-xp">+25</div>
  </div>
  <div class="checklist-item" onclick="toggleCheck(3)" id="check-3">
    <div class="check-box">✓</div>
    <div class="check-text">
      Hit Protein Target (170g)
      <span class="check-sub">Track via whey + meals</span>
    </div>
    <div class="check-xp">+25</div>
  </div>
  <div class="checklist-item" onclick="toggleCheck(4)" id="check-4">
    <div class="check-box">✓</div>
    <div class="check-text">
      Gym Session Completed
      <span class="check-sub">5:30 PM — weights + 30 min cardio</span>
    </div>
    <div class="check-xp">+50</div>
  </div>
  <div class="checklist-item" onclick="toggleCheck(5)" id="check-5">
    <div class="check-box">✓</div>
    <div class="check-text">
      Stayed Under 1,850 kcal
      <span class="check-sub">No fried food, no sugar, no alcohol</span>
    </div>
    <div class="check-xp">+30</div>
  </div>
  <div class="checklist-item" onclick="toggleCheck(6)" id="check-6">
    <div class="check-box">✓</div>
    <div class="check-text">
      Sleep 7–8 Hours
      <span class="check-sub">In bed by 10:30 PM</span>
    </div>
    <div class="check-xp">+20</div>
  </div>
</div>

<!-- Day score display -->
<div class="progress-container" id="day-score-card">
  <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:12px;">
    <div style="font-family:'Space Mono',monospace; font-size:10px; color:var(--muted);">TODAY'S SCORE</div>
    <div style="font-family:'Bebas Neue',sans-serif; font-size:28px; color:var(--accent2);" id="day-score">0 / 200 XP</div>
  </div>
  <div class="progress-bar-bg">
    <div class="progress-bar-fill" id="day-score-bar" style="width:0%"></div>
  </div>
  <div class="progress-desc" id="day-score-msg">Complete your missions to earn XP</div>
</div>

<button class="log-btn" style="width:100%; padding:16px; font-size:22px; letter-spacing:2px;" onclick="completeDayConfirm()">
  ✓ MARK DAY COMPLETE
</button>
```

  </div>
</div>

<!-- MEALS PANEL -->

<div id="panel-meals" class="panel">
  <div style="padding: 20px 20px 0;">
    <div class="section-header">▸ Daily Meal Plan</div>

```
<div style="font-family:'Space Mono',monospace; font-size:10px; color:var(--muted); margin-bottom:14px;">
  EATING WINDOW: 12:00 PM → 8:00 PM &nbsp;|&nbsp; TARGET: 1,800 KCAL &nbsp;|&nbsp; PROTEIN: 170G
</div>

<div class="meal-card">
  <div class="meal-header">
    <div>
      <div class="meal-time">12:00 PM — BREAK FAST</div>
      <div class="meal-name">MEAL 1 — POWER BREAK</div>
    </div>
    <div class="meal-macros">~450 kcal</div>
  </div>
  <div class="meal-body">
    • 5 egg whites + 2 whole eggs (boiled or scrambled, no oil)<br>
    • 1 cup oats with water (no milk, no sugar)<br>
    • 1 banana<br>
    • 1 glass water + black coffee
    <div class="macro-chips">
      <span class="macro-chip protein">P: 45g</span>
      <span class="macro-chip carb">C: 48g</span>
      <span class="macro-chip fat">F: 12g</span>
      <span class="macro-chip cal">450 kcal</span>
    </div>
  </div>
</div>

<div class="meal-card">
  <div class="meal-header">
    <div>
      <div class="meal-time">2:30 PM — LUNCH</div>
      <div class="meal-name">MEAL 2 — FUEL UP</div>
    </div>
    <div class="meal-macros">~580 kcal</div>
  </div>
  <div class="meal-body">
    • 180g grilled chicken breast or fish (no frying)<br>
    • 1 cup cooked brown rice or 2 wheat chapatis<br>
    • Large salad (cucumber, tomato, onion + lemon)<br>
    • 1 bowl vegetable sabzi (minimal oil)
    <div class="macro-chips">
      <span class="macro-chip protein">P: 52g</span>
      <span class="macro-chip carb">C: 55g</span>
      <span class="macro-chip fat">F: 10g</span>
      <span class="macro-chip cal">580 kcal</span>
    </div>
  </div>
</div>

<div class="meal-card">
  <div class="meal-header">
    <div>
      <div class="meal-time">5:00 PM — PRE-GYM</div>
      <div class="meal-name">MEAL 3 — PRE-WORKOUT</div>
    </div>
    <div class="meal-macros">~280 kcal</div>
  </div>
  <div class="meal-body">
    • 1 scoop whey protein in water<br>
    • 1 banana OR 1 apple<br>
    • (Optional) 5g creatine monohydrate in water
    <div class="macro-chips">
      <span class="macro-chip protein">P: 28g</span>
      <span class="macro-chip carb">C: 30g</span>
      <span class="macro-chip fat">F: 3g</span>
      <span class="macro-chip cal">280 kcal</span>
    </div>
  </div>
</div>

<div class="meal-card">
  <div class="meal-header">
    <div>
      <div class="meal-time">7:30 PM — DINNER</div>
      <div class="meal-name">MEAL 4 — CLOSE THE WINDOW</div>
    </div>
    <div class="meal-macros">~450 kcal</div>
  </div>
  <div class="meal-body">
    • 180g grilled fish or chicken (NO rice at night)<br>
    • 2 cups sautéed vegetables (any combo)<br>
    • 1 cup dal or lentil soup<br>
    • Last food before 8:00 PM — fast begins
    <div class="macro-chips">
      <span class="macro-chip protein">P: 48g</span>
      <span class="macro-chip carb">C: 22g</span>
      <span class="macro-chip fat">F: 8g</span>
      <span class="macro-chip cal">450 kcal</span>
    </div>
  </div>
</div>

<div style="background:var(--surface); border:1px solid var(--border); border-radius:4px; padding:16px; margin-top:4px;">
  <div style="font-family:'Space Mono',monospace; font-size:10px; color:var(--accent); letter-spacing:2px; margin-bottom:10px;">▸ DAILY TOTALS</div>
  <div style="display:grid; grid-template-columns:repeat(4,1fr); gap:8px; text-align:center;">
    <div><div style="font-family:'Bebas Neue',sans-serif;font-size:26px;color:var(--green)">1760</div><div style="font-size:10px;color:var(--muted)">KCAL</div></div>
    <div><div style="font-family:'Bebas Neue',sans-serif;font-size:26px;color:#64b5f6">173g</div><div style="font-size:10px;color:var(--muted)">PROTEIN</div></div>
    <div><div style="font-family:'Bebas Neue',sans-serif;font-size:26px;color:var(--accent2)">155g</div><div style="font-size:10px;color:var(--muted)">CARBS</div></div>
    <div><div style="font-family:'Bebas Neue',sans-serif;font-size:26px;color:#ef9a9a">33g</div><div style="font-size:10px;color:var(--muted)">FAT</div></div>
  </div>
</div>

<div style="background:rgba(0,230,118,0.05); border:1px solid rgba(0,230,118,0.2); border-radius:4px; padding:14px; margin-top:14px; font-size:12px; color:#aaa; line-height:1.7;">
  <strong style="color:var(--green);">✓ ALLOWED ANYTIME:</strong> Black coffee, green tea, plain water, sparkling water (no sugar), electrolytes<br><br>
  <strong style="color:var(--red);">✗ BANNED FOR 90 DAYS:</strong> Fried food, white sugar, alcohol, juice, soda, white rice at dinner, anything after 8 PM
</div>
```

  </div>
</div>

<!-- TRAINING PANEL -->

<div id="panel-training" class="panel">
  <div style="padding: 20px 20px 0;">
    <div class="section-header">▸ Training Protocol</div>

```
<div class="phase-tag">PUSH / PULL / LEGS SPLIT — 6 DAYS/WEEK</div>

<div style="background:var(--surface); border:1px solid var(--border); border-radius:4px; padding:14px; margin-bottom:14px; font-size:12px; color:#aaa; line-height:1.7;">
  Every session: <strong style="color:var(--text)">10 min treadmill warm-up</strong> → strength training 45 min → <strong style="color:var(--text)">30 min cardio finisher</strong>. Non-negotiable.
</div>

<div class="workout-card" onclick="toggleWorkout(this)">
  <div class="workout-day-header">
    <div>
      <div style="font-size:10px;font-family:'Space Mono',monospace;color:var(--muted);margin-bottom:2px">MON / THU</div>
      <div class="workout-day-name">PUSH DAY</div>
    </div>
    <div class="workout-tag">CHEST · SHOULDERS · TRICEPS</div>
  </div>
  <div class="workout-exercises">
    <div class="exercise-row"><span class="exercise-name">Flat Bench Press</span><span class="exercise-sets">4 × 10–12</span></div>
    <div class="exercise-row"><span class="exercise-name">Incline Dumbbell Press</span><span class="exercise-sets">3 × 12</span></div>
    <div class="exercise-row"><span class="exercise-name">Shoulder Press (machine)</span><span class="exercise-sets">3 × 12</span></div>
    <div class="exercise-row"><span class="exercise-name">Lateral Raises</span><span class="exercise-sets">3 × 15</span></div>
    <div class="exercise-row"><span class="exercise-name">Tricep Pushdown</span><span class="exercise-sets">3 × 15</span></div>
    <div class="exercise-row"><span class="exercise-name">Overhead Tricep Extension</span><span class="exercise-sets">3 × 12</span></div>
    <div class="exercise-row" style="background:rgba(255,69,0,0.05)"><span class="exercise-name" style="color:var(--accent)">🔥 Cardio Finisher</span><span class="exercise-sets" style="color:var(--accent)">30 min incline treadmill</span></div>
  </div>
</div>

<div class="workout-card" onclick="toggleWorkout(this)">
  <div class="workout-day-header">
    <div>
      <div style="font-size:10px;font-family:'Space Mono',monospace;color:var(--muted);margin-bottom:2px">TUE / FRI</div>
      <div class="workout-day-name">PULL DAY</div>
    </div>
    <div class="workout-tag">BACK · BICEPS</div>
  </div>
  <div class="workout-exercises">
    <div class="exercise-row"><span class="exercise-name">Lat Pulldown</span><span class="exercise-sets">4 × 10–12</span></div>
    <div class="exercise-row"><span class="exercise-name">Seated Cable Row</span><span class="exercise-sets">3 × 12</span></div>
    <div class="exercise-row"><span class="exercise-name">Single Arm Dumbbell Row</span><span class="exercise-sets">3 × 12</span></div>
    <div class="exercise-row"><span class="exercise-name">Face Pulls</span><span class="exercise-sets">3 × 15</span></div>
    <div class="exercise-row"><span class="exercise-name">Barbell Curl</span><span class="exercise-sets">3 × 12</span></div>
    <div class="exercise-row"><span class="exercise-name">Hammer Curl</span><span class="exercise-sets">3 × 12</span></div>
    <div class="exercise-row" style="background:rgba(255,69,0,0.05)"><span class="exercise-name" style="color:var(--accent)">🔥 Cardio Finisher</span><span class="exercise-sets" style="color:var(--accent)">30 min stationary bike</span></div>
  </div>
</div>

<div class="workout-card" onclick="toggleWorkout(this)">
  <div class="workout-day-header">
    <div>
      <div style="font-size:10px;font-family:'Space Mono',monospace;color:var(--muted);margin-bottom:2px">WED / SAT</div>
      <div class="workout-day-name">LEGS + CORE</div>
    </div>
    <div class="workout-tag">QUADS · HAMS · ABS</div>
  </div>
  <div class="workout-exercises">
    <div class="exercise-row"><span class="exercise-name">Leg Press</span><span class="exercise-sets">4 × 12–15</span></div>
    <div class="exercise-row"><span class="exercise-name">Romanian Deadlift</span><span class="exercise-sets">3 × 12</span></div>
    <div class="exercise-row"><span class="exercise-name">Leg Extension</span><span class="exercise-sets">3 × 15</span></div>
    <div class="exercise-row"><span class="exercise-name">Lying Leg Curl</span><span class="exercise-sets">3 × 15</span></div>
    <div class="exercise-row"><span class="exercise-name">Calf Raises</span><span class="exercise-sets">4 × 20</span></div>
    <div class="exercise-row"><span class="exercise-name">Plank Hold</span><span class="exercise-sets">3 × 45 sec</span></div>
    <div class="exercise-row"><span class="exercise-name">Hanging Knee Raises</span><span class="exercise-sets">3 × 15</span></div>
    <div class="exercise-row" style="background:rgba(255,69,0,0.05)"><span class="exercise-name" style="color:var(--accent)">🔥 Cardio Finisher</span><span class="exercise-sets" style="color:var(--accent)">30 min elliptical</span></div>
  </div>
</div>

<div class="workout-card" onclick="toggleWorkout(this)">
  <div class="workout-day-header">
    <div>
      <div style="font-size:10px;font-family:'Space Mono',monospace;color:var(--muted);margin-bottom:2px">SUNDAY</div>
      <div class="workout-day-name">REST + RESET</div>
    </div>
    <div class="workout-tag" style="color:var(--green);border-color:var(--green)">ACTIVE RECOVERY</div>
  </div>
  <div class="workout-exercises">
    <div class="exercise-row"><span class="exercise-name">30–45 min brisk walk</span><span class="exercise-sets">outdoors</span></div>
    <div class="exercise-row"><span class="exercise-name">Full body stretching</span><span class="exercise-sets">20 min</span></div>
    <div class="exercise-row"><span class="exercise-name">Foam rolling</span><span class="exercise-sets">10 min</span></div>
    <div class="exercise-row"><span class="exercise-name">Meal prep for the week</span><span class="exercise-sets">cook + portion</span></div>
  </div>
</div>
```

  </div>
</div>

<!-- MILESTONES / TROPHIES PANEL -->

<div id="panel-milestones" class="panel">
  <div style="padding: 20px 20px 0;">
    <div class="section-header">▸ Trophies & Milestones</div>

```
<div class="milestone-list" id="milestone-list">
  <div class="milestone locked" id="m-0">
    <div class="milestone-icon">🏁</div>
    <div class="milestone-info">
      <div class="milestone-name">FIRST BLOOD</div>
      <div class="milestone-desc">Complete Day 1 fully</div>
    </div>
    <div class="milestone-badge">LOCKED</div>
  </div>
  <div class="milestone locked" id="m-1">
    <div class="milestone-icon">🔥</div>
    <div class="milestone-info">
      <div class="milestone-name">ON FIRE</div>
      <div class="milestone-desc">7-day streak — no breaks</div>
    </div>
    <div class="milestone-badge">7 DAYS</div>
  </div>
  <div class="milestone locked" id="m-2">
    <div class="milestone-icon">⚖️</div>
    <div class="milestone-info">
      <div class="milestone-name">FIRST DROP</div>
      <div class="milestone-desc">Lose your first 3 kg (reach 103 kg)</div>
    </div>
    <div class="milestone-badge">103 KG</div>
  </div>
  <div class="milestone locked" id="m-3">
    <div class="milestone-icon">💪</div>
    <div class="milestone-info">
      <div class="milestone-name">DOUBLE DIGITS DOWN</div>
      <div class="milestone-desc">Lost 10 kg total — reach 96 kg</div>
    </div>
    <div class="milestone-badge">96 KG</div>
  </div>
  <div class="milestone locked" id="m-4">
    <div class="milestone-icon">⚡</div>
    <div class="milestone-info">
      <div class="milestone-name">30-DAY WARRIOR</div>
      <div class="milestone-desc">Complete 30 consecutive days</div>
    </div>
    <div class="milestone-badge">DAY 30</div>
  </div>
  <div class="milestone locked" id="m-5">
    <div class="milestone-icon">🏋️</div>
    <div class="milestone-info">
      <div class="milestone-name">MACHINE</div>
      <div class="milestone-desc">Complete 50 gym sessions</div>
    </div>
    <div class="milestone-badge">50 GYM</div>
  </div>
  <div class="milestone locked" id="m-6">
    <div class="milestone-icon">🌅</div>
    <div class="milestone-info">
      <div class="milestone-name">EARLY RISER</div>
      <div class="milestone-desc">30 fasted morning walks done</div>
    </div>
    <div class="milestone-badge">30 WALKS</div>
  </div>
  <div class="milestone locked" id="m-7">
    <div class="milestone-icon">👑</div>
    <div class="milestone-info">
      <div class="milestone-name">HALFWAY KING</div>
      <div class="milestone-desc">Reach 94–95 kg — halfway there</div>
    </div>
    <div class="milestone-badge">95 KG</div>
  </div>
  <div class="milestone locked" id="m-8">
    <div class="milestone-icon">🎯</div>
    <div class="milestone-info">
      <div class="milestone-name">90-DAY CHAMPION</div>
      <div class="milestone-desc">Complete all 90 days</div>
    </div>
    <div class="milestone-badge">DAY 90</div>
  </div>
  <div class="milestone locked" id="m-9">
    <div class="milestone-icon">🏆</div>
    <div class="milestone-info">
      <div class="milestone-name">THE TRANSFORMATION</div>
      <div class="milestone-desc">Reach 83 kg — goal achieved</div>
    </div>
    <div class="milestone-badge">83 KG</div>
  </div>
</div>
```

  </div>
</div>

<!-- TOAST -->

<div class="toast" id="toast"></div>

<script>
  // STATE
  const STATE_KEY = 'war90_state_v2';
  let state = {
    startWeight: 106,
    targetWeight: 83,
    weightLog: [],
    daysDone: 0,
    streak: 0,
    lastCompleteDate: null,
    totalXP: 0,
    checks: [false,false,false,false,false,false,false],
    gymSessions: 0,
    walks: 0,
    milestones: {}
  };

  function loadState() {
    try {
      const saved = localStorage.getItem(STATE_KEY);
      if (saved) state = {...state, ...JSON.parse(saved)};
    } catch(e) {}
  }

  function saveState() {
    try { localStorage.setItem(STATE_KEY, JSON.stringify(state)); } catch(e) {}
  }

  // LEVELS
  const levels = [
    { level:1, title:'RECRUIT', xpNeeded:200 },
    { level:2, title:'FIGHTER', xpNeeded:500 },
    { level:3, title:'WARRIOR', xpNeeded:1000 },
    { level:4, title:'BEAST', xpNeeded:2000 },
    { level:5, title:'MACHINE', xpNeeded:3500 },
    { level:6, title:'LEGEND', xpNeeded:5500 },
    { level:7, title:'CHAMPION', xpNeeded:8000 },
    { level:8, title:'IMMORTAL', xpNeeded:99999 },
  ];

  function getLevel(xp) {
    let current = levels[0];
    let next = levels[1];
    for (let i = 0; i < levels.length-1; i++) {
      if (xp >= levels[i].xpNeeded) {
        current = levels[i+1] || levels[levels.length-1];
        next = levels[i+2] || levels[levels.length-1];
      } else {
        break;
      }
    }
    // simple approach
    let lvl = 1, prevXP = 0;
    for (let i = 0; i < levels.length; i++) {
      if (xp < levels[i].xpNeeded) { lvl = levels[i].level; prevXP = i > 0 ? levels[i-1].xpNeeded : 0; next = levels[i]; break; }
      if (i === levels.length-1) { lvl = levels[i].level; next = levels[i]; prevXP = levels[i-1]?.xpNeeded || 0; }
    }
    const pct = next.xpNeeded < 99999 ? Math.min(100, ((xp - prevXP) / (next.xpNeeded - prevXP)) * 100) : 100;
    return { level: lvl, title: levels[lvl-1]?.title || 'CHAMPION', pct, xpNext: next.xpNeeded, prevXP };
  }

  function updateXPDisplay() {
    const info = getLevel(state.totalXP);
    document.getElementById('level-num').textContent = info.level;
    document.getElementById('level-title').textContent = info.title;
    document.getElementById('xp-bar').style.width = info.pct + '%';
    document.getElementById('xp-current').textContent = state.totalXP;
    document.getElementById('xp-next').textContent = info.xpNext < 99999 ? info.xpNext : '∞';
  }

  function updateDashboard() {
    document.getElementById('streak-num').textContent = state.streak;
    document.getElementById('days-done').textContent = state.daysDone;
    document.getElementById('days-left').textContent = Math.max(0, 90 - state.daysDone);
    updateXPDisplay();
    updateWeightDisplay();
    buildDayGrid();
    checkMilestones();
  }

  function updateWeightDisplay() {
    if (state.weightLog.length === 0) return;
    const latest = state.weightLog[state.weightLog.length-1].weight;
    document.getElementById('current-weight-display').textContent = latest + ' kg';

    const lost = state.startWeight - latest;
    const total = state.startWeight - state.targetWeight;
    const pct = Math.min(100, Math.max(0, (lost / total) * 100));
    document.getElementById('weight-progress-bar').style.width = pct + '%';
    document.getElementById('progress-pct').textContent = Math.round(pct) + '%';

    if (lost <= 0) {
      document.getElementById('progress-desc').textContent = 'Starting point — every kg from here is a victory.';
    } else {
      const toGo = (latest - state.targetWeight).toFixed(1);
      document.getElementById('progress-desc').textContent = `Lost ${lost.toFixed(1)} kg so far — ${toGo} kg to go. Keep going.`;
    }
    updateChart();
  }

  function logWeight() {
    const val = parseFloat(document.getElementById('weight-input').value);
    if (isNaN(val) || val < 60 || val > 200) { showToast('ENTER A VALID WEIGHT'); return; }
    state.weightLog.push({ weight: val, date: new Date().toISOString() });
    saveState();
    updateWeightDisplay();
    showToast('WEIGHT LOGGED: ' + val + ' KG');
    document.getElementById('weight-input').value = '';
    checkMilestones();
  }

  function updateChart() {
    if (state.weightLog.length < 1) return;
    const svg = document.getElementById('weight-chart');
    const maxW = state.startWeight;
    const minW = state.targetWeight - 2;
    const range = maxW - minW;
    const chartH = 115, chartW = 265, startX = 30;

    const toY = w => 10 + ((maxW - w) / range) * (chartH - 10);
    const toX = i => startX + (i / Math.max(state.weightLog.length-1, 1)) * chartW;

    let points = state.weightLog.map((e,i) => `${toX(i)},${toY(e.weight)}`).join(' ');
    document.getElementById('chart-line').setAttribute('points', points);

    const lastX = toX(state.weightLog.length-1);
    const lastY = toY(state.weightLog[state.weightLog.length-1].weight);
    const dot = document.getElementById('chart-dot');
    dot.setAttribute('cx', lastX);
    dot.setAttribute('cy', lastY);
    dot.style.display = 'block';
  }

  function buildDayGrid() {
    const grid = document.getElementById('day-grid');
    grid.innerHTML = '';
    for (let d = 1; d <= 90; d++) {
      const cell = document.createElement('div');
      cell.className = 'day-cell';
      cell.setAttribute('title', 'Day ' + d);

      if (d < state.daysDone) {
        cell.classList.add('completed-both');
      } else if (d === state.daysDone + 1) {
        cell.classList.add('today');
        cell.textContent = d;
        cell.style.color = 'var(--accent2)';
        cell.style.fontSize = '7px';
      } else if (d > state.daysDone + 1) {
        cell.classList.add('future');
      }
      grid.appendChild(cell);
    }
  }

  // CHECKLIST
  const checkXP = [30, 20, 25, 25, 50, 30, 20];
  function toggleCheck(idx) {
    state.checks[idx] = !state.checks[idx];
    const el = document.getElementById('check-' + idx);
    if (state.checks[idx]) {
      el.classList.add('done');
      el.querySelector('.check-box').style.background = 'var(--green)';
      el.querySelector('.check-box').style.borderColor = 'var(--green)';
    } else {
      el.classList.remove('done');
      el.querySelector('.check-box').style.background = '';
      el.querySelector('.check-box').style.borderColor = 'var(--border)';
    }
    updateDayScore();
    saveState();
  }

  function updateDayScore() {
    let total = 0;
    state.checks.forEach((c,i) => { if(c) total += checkXP[i]; });
    const max = checkXP.reduce((a,b) => a+b, 0);
    const pct = (total / max) * 100;
    document.getElementById('day-score').textContent = total + ' / ' + max + ' XP';
    document.getElementById('day-score-bar').style.width = pct + '%';
    document.getElementById('today-xp-display').textContent = total + ' XP earned';

    const msgs = ['Complete your missions to earn XP', 'Keep going — you\'re building momentum', 'Halfway there — push through', 'Almost perfect — one more to go!', '🔥 PERFECT DAY — Maximum XP!'];
    const msgIdx = pct === 0 ? 0 : pct < 30 ? 1 : pct < 60 ? 2 : pct < 100 ? 3 : 4;
    document.getElementById('day-score-msg').textContent = msgs[msgIdx];
  }

  function restoreChecks() {
    state.checks.forEach((c,i) => {
      if (c) {
        const el = document.getElementById('check-' + i);
        if (el) {
          el.classList.add('done');
          el.querySelector('.check-box').style.background = 'var(--green)';
          el.querySelector('.check-box').style.borderColor = 'var(--green)';
        }
      }
    });
    updateDayScore();
  }

  function completeDayConfirm() {
    const done = state.checks.filter(Boolean).length;
    if (done < 4) { showToast('COMPLETE AT LEAST 4 MISSIONS FIRST'); return; }

    let xpEarned = 0;
    state.checks.forEach((c,i) => { if(c) xpEarned += checkXP[i]; });

    const today = new Date().toDateString();
    if (state.lastCompleteDate === today) { showToast('ALREADY COMPLETED TODAY'); return; }

    state.daysDone = Math.min(90, state.daysDone + 1);
    state.totalXP += xpEarned;
    if (state.checks[4]) state.gymSessions++;
    if (state.checks[0]) state.walks++;

    // Streak
    const yesterday = new Date(); yesterday.setDate(yesterday.getDate()-1);
    if (state.lastCompleteDate === yesterday.toDateString()) {
      state.streak++;
    } else {
      state.streak = 1;
    }
    state.lastCompleteDate = today;
    state.checks = [false,false,false,false,false,false,false];

    saveState();
    updateDashboard();
    restoreChecks();
    showToast('DAY ' + state.daysDone + ' COMPLETE! +' + xpEarned + ' XP');
    checkMilestones();
  }

  // MILESTONES
  function checkMilestones() {
    const latestWeight = state.weightLog.length > 0 ? state.weightLog[state.weightLog.length-1].weight : 999;
    const conditions = [
      state.daysDone >= 1,
      state.streak >= 7,
      latestWeight <= 103,
      latestWeight <= 96,
      state.daysDone >= 30,
      state.gymSessions >= 50,
      state.walks >= 30,
      latestWeight <= 95,
      state.daysDone >= 90,
      latestWeight <= 83,
    ];
    conditions.forEach((cond, i) => {
      if (cond && !state.milestones['m'+i]) {
        state.milestones['m'+i] = true;
        saveState();
        const el = document.getElementById('m-'+i);
        if (el) {
          el.classList.remove('locked');
          el.classList.add('unlocked');
          el.querySelector('.milestone-badge').textContent = 'UNLOCKED';
          el.querySelector('.milestone-badge').style.background = 'var(--green)';
          el.querySelector('.milestone-badge').style.color = '#000';
        }
        setTimeout(() => showToast('🏆 TROPHY UNLOCKED!'), 300);
      }
    });
    // restore milestones from saved state
    Object.keys(state.milestones).forEach(key => {
      const el = document.getElementById(key);
      if (el && state.milestones[key]) {
        el.classList.remove('locked');
        el.classList.add('unlocked');
        el.querySelector('.milestone-badge').textContent = 'UNLOCKED';
        el.querySelector('.milestone-badge').style.background = 'var(--green)';
        el.querySelector('.milestone-badge').style.color = '#000';
      }
    });
  }

  // NAV
  function showPanel(name) {
    document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
    document.getElementById('panel-' + name).classList.add('active');
    event.target.classList.add('active');
  }

  // WORKOUT TOGGLE
  function toggleWorkout(el) {
    el.classList.toggle('open');
  }

  // TOAST
  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    setTimeout(() => t.classList.remove('show'), 2500);
  }

  // INIT
  loadState();
  updateDashboard();
  restoreChecks();
  checkMilestones();
</script>

</body>
</html>

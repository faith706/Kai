<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>KLABS Foundry — Kaintomia Labs</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin/>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:ital,wght@0,300;0,400;1,300&family=Fraunces:ital,opsz,wght@0,9..144,300;0,9..144,700;1,9..144,300&display=swap" rel="stylesheet"/>
<style>
  :root {
    --black: #0a0a08;
    --cream: #f5f0e8;
    --amber: #e8a020;
    --rust: #c94a1e;
    --forest: #1d4230;
    --sand: #d4c4a0;
    --muted: #7a7060;
    --white: #fdfaf4;
  }

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
background: var(–black);
color: var(–cream);
font-family: ‘DM Mono’, monospace;
overflow-x: hidden;
cursor: none;
}

/* Custom cursor */
.cursor {
position: fixed;
width: 12px; height: 12px;
background: var(–amber);
border-radius: 50%;
pointer-events: none;
z-index: 9999;
transform: translate(-50%, -50%);
transition: transform 0.1s ease, width 0.2s, height 0.2s;
mix-blend-mode: difference;
}
.cursor-ring {
position: fixed;
width: 36px; height: 36px;
border: 1px solid var(–amber);
border-radius: 50%;
pointer-events: none;
z-index: 9998;
transform: translate(-50%, -50%);
transition: transform 0.18s ease, opacity 0.2s;
opacity: 0.5;
}

/* NAV */
nav {
position: fixed; top: 0; left: 0; right: 0;
z-index: 100;
display: flex; align-items: center; justify-content: space-between;
padding: 1.4rem 3rem;
border-bottom: 1px solid rgba(255,255,255,0.06);
background: rgba(10,10,8,0.85);
backdrop-filter: blur(12px);
}
.nav-logo {
font-family: ‘Syne’, sans-serif;
font-weight: 800;
font-size: 1.1rem;
letter-spacing: 0.15em;
color: var(–amber);
text-decoration: none;
}
.nav-logo span { color: var(–cream); }
.nav-links { display: flex; gap: 2.4rem; list-style: none; }
.nav-links a {
font-size: 0.72rem;
letter-spacing: 0.12em;
text-transform: uppercase;
color: var(–sand);
text-decoration: none;
transition: color 0.2s;
}
.nav-links a:hover { color: var(–amber); }
.nav-cta {
font-size: 0.72rem;
letter-spacing: 0.12em;
text-transform: uppercase;
padding: 0.55rem 1.4rem;
border: 1px solid var(–amber);
color: var(–amber);
background: transparent;
cursor: none;
transition: background 0.2s, color 0.2s;
text-decoration: none;
}
.nav-cta:hover { background: var(–amber); color: var(–black); }

/* HERO */
.hero {
min-height: 100vh;
display: grid;
grid-template-columns: 1fr 1fr;
position: relative;
overflow: hidden;
}
.hero-left {
display: flex; flex-direction: column; justify-content: flex-end;
padding: 10rem 3rem 5rem;
position: relative; z-index: 2;
}
.hero-tag {
font-size: 0.68rem;
letter-spacing: 0.2em;
text-transform: uppercase;
color: var(–amber);
margin-bottom: 2rem;
opacity: 0;
animation: fadeUp 0.8s 0.3s forwards;
}
.hero-tag::before {
content: ’— ’;
}
h1 {
font-family: ‘Fraunces’, serif;
font-size: clamp(3.2rem, 6vw, 5.8rem);
font-weight: 700;
line-height: 1.0;
color: var(–white);
margin-bottom: 2rem;
opacity: 0;
animation: fadeUp 0.8s 0.5s forwards;
}
h1 em {
font-style: italic;
color: var(–amber);
}
.hero-desc {
font-size: 0.85rem;
line-height: 1.9;
color: var(–sand);
max-width: 36ch;
margin-bottom: 3rem;
opacity: 0;
animation: fadeUp 0.8s 0.7s forwards;
}
.hero-actions {
display: flex; gap: 1.2rem; align-items: center;
opacity: 0;
animation: fadeUp 0.8s 0.9s forwards;
}
.btn-primary {
font-family: ‘DM Mono’, monospace;
font-size: 0.78rem;
letter-spacing: 0.12em;
text-transform: uppercase;
padding: 1rem 2.4rem;
background: var(–amber);
color: var(–black);
border: none; cursor: none;
text-decoration: none;
transition: background 0.2s, transform 0.15s;
font-weight: 400;
}
.btn-primary:hover { background: #f0b030; transform: translateY(-2px); }
.btn-ghost {
font-family: ‘DM Mono’, monospace;
font-size: 0.78rem;
letter-spacing: 0.12em;
text-transform: uppercase;
color: var(–sand);
text-decoration: none;
display: flex; align-items: center; gap: 0.6rem;
transition: color 0.2s;
}
.btn-ghost:hover { color: var(–cream); }
.btn-ghost::after { content: ‘↓’; }

.hero-right {
position: relative;
display: flex; align-items: center; justify-content: center;
}
.hero-grid {
position: absolute; inset: 0;
background-image:
linear-gradient(rgba(232,160,32,0.06) 1px, transparent 1px),
linear-gradient(90deg, rgba(232,160,32,0.06) 1px, transparent 1px);
background-size: 60px 60px;
animation: gridShift 20s linear infinite;
}
@keyframes gridShift {
from { background-position: 0 0; }
to { background-position: 60px 60px; }
}
.hero-stat-card {
position: relative; z-index: 2;
display: grid; grid-template-columns: 1fr 1fr; gap: 1.5px;
background: rgba(232,160,32,0.15);
border: 1px solid rgba(232,160,32,0.2);
opacity: 0;
animation: fadeIn 1.2s 1.1s forwards;
}
.stat-item {
background: rgba(10,10,8,0.9);
padding: 2.4rem;
display: flex; flex-direction: column; gap: 0.5rem;
}
.stat-num {
font-family: ‘Fraunces’, serif;
font-size: 3.2rem;
font-weight: 700;
color: var(–amber);
line-height: 1;
}
.stat-label {
font-size: 0.68rem;
letter-spacing: 0.12em;
text-transform: uppercase;
color: var(–muted);
}

/* STRIP */
.strip {
background: var(–amber);
padding: 1rem 0;
overflow: hidden;
white-space: nowrap;
}
.strip-inner {
display: inline-flex; gap: 3rem;
animation: ticker 25s linear infinite;
font-size: 0.7rem;
letter-spacing: 0.2em;
text-transform: uppercase;
color: var(–black);
font-weight: 400;
}
.strip-inner span::before { content: ’✦  ’; }
@keyframes ticker {
from { transform: translateX(0); }
to { transform: translateX(-50%); }
}

/* ABOUT */
.about {
display: grid; grid-template-columns: 1fr 1fr;
min-height: 70vh;
border-top: 1px solid rgba(255,255,255,0.06);
}
.about-left {
background: var(–forest);
padding: 6rem 4rem;
display: flex; flex-direction: column; justify-content: center;
}
.section-label {
font-size: 0.65rem;
letter-spacing: 0.25em;
text-transform: uppercase;
color: var(–amber);
margin-bottom: 2rem;
}
.about-left h2 {
font-family: ‘Fraunces’, serif;
font-size: clamp(2rem, 3.5vw, 3rem);
font-weight: 300;
line-height: 1.25;
color: var(–white);
margin-bottom: 2rem;
}
.about-left h2 strong {
font-weight: 700;
color: var(–amber);
}
.about-left p {
font-size: 0.82rem;
line-height: 1.95;
color: rgba(213,196,160,0.8);
max-width: 42ch;
}
.about-right {
padding: 6rem 4rem;
display: flex; flex-direction: column; justify-content: center;
gap: 1.5rem;
}
.goal-item {
display: flex; gap: 1.5rem; align-items: flex-start;
padding: 1.8rem;
border: 1px solid rgba(255,255,255,0.06);
transition: border-color 0.2s, background 0.2s;
}
.goal-item:hover {
border-color: rgba(232,160,32,0.3);
background: rgba(232,160,32,0.03);
}
.goal-num {
font-family: ‘Fraunces’, serif;
font-size: 1.6rem;
font-style: italic;
color: var(–amber);
opacity: 0.4;
min-width: 2.5rem;
}
.goal-text {
font-size: 0.78rem;
line-height: 1.8;
color: var(–sand);
}
.goal-text strong { color: var(–cream); display: block; margin-bottom: 0.3rem; font-size: 0.8rem; }

/* PHASES */
.phases-section {
padding: 7rem 3rem;
border-top: 1px solid rgba(255,255,255,0.06);
}
.phases-header {
display: flex; align-items: flex-end; justify-content: space-between;
margin-bottom: 4rem;
}
.phases-header h2 {
font-family: ‘Fraunces’, serif;
font-size: clamp(2rem, 4vw, 3.5rem);
font-weight: 700;
color: var(–white);
max-width: 18ch;
}
.phases-header p {
font-size: 0.78rem;
color: var(–muted);
max-width: 28ch;
line-height: 1.8;
}
.phases-grid {
display: grid;
grid-template-columns: repeat(6, 1fr);
gap: 1.5px;
background: rgba(255,255,255,0.05);
}
.phase-card {
background: var(–black);
padding: 2.4rem 2rem;
position: relative;
overflow: hidden;
cursor: none;
transition: background 0.3s;
}
.phase-card::before {
content: ‘’;
position: absolute; top: 0; left: 0; right: 0;
height: 2px;
background: var(–amber);
transform: scaleX(0);
transform-origin: left;
transition: transform 0.3s;
}
.phase-card:hover { background: rgba(232,160,32,0.04); }
.phase-card:hover::before { transform: scaleX(1); }
.phase-num {
font-size: 0.62rem;
letter-spacing: 0.2em;
color: var(–amber);
margin-bottom: 1.5rem;
}
.phase-title {
font-family: ‘Syne’, sans-serif;
font-size: 1rem;
font-weight: 700;
color: var(–white);
margin-bottom: 0.8rem;
}
.phase-weeks {
font-size: 0.65rem;
color: var(–muted);
letter-spacing: 0.1em;
margin-bottom: 1.2rem;
}
.phase-desc {
font-size: 0.72rem;
line-height: 1.8;
color: var(–sand);
opacity: 0.7;
}
.phase-tag {
margin-top: 1.5rem;
display: inline-block;
font-size: 0.6rem;
letter-spacing: 0.12em;
text-transform: uppercase;
padding: 0.3rem 0.8rem;
border: 1px solid rgba(232,160,32,0.3);
color: var(–amber);
}

/* TRACKS */
.tracks-section {
border-top: 1px solid rgba(255,255,255,0.06);
display: grid; grid-template-columns: 1fr 1fr;
}
.track {
padding: 6rem 4rem;
position: relative; overflow: hidden;
}
.track-creatives { background: rgba(201,74,30,0.08); }
.track-stem { background: rgba(29,66,48,0.2); border-left: 1px solid rgba(255,255,255,0.06); }
.track-bg-text {
position: absolute; bottom: -1rem; right: -1rem;
font-family: ‘Fraunces’, serif;
font-size: 9rem;
font-style: italic;
font-weight: 700;
opacity: 0.04;
color: var(–cream);
pointer-events: none;
user-select: none;
}
.track h3 {
font-family: ‘Syne’, sans-serif;
font-size: 1.5rem;
font-weight: 800;
color: var(–white);
margin-bottom: 1.2rem;
letter-spacing: 0.04em;
}
.track-subtitle {
font-size: 0.72rem;
letter-spacing: 0.15em;
text-transform: uppercase;
color: var(–amber);
margin-bottom: 2.4rem;
}
.track p {
font-size: 0.8rem;
line-height: 1.9;
color: var(–sand);
margin-bottom: 2rem;
max-width: 40ch;
}
.track-tools {
display: flex; flex-wrap: wrap; gap: 0.6rem;
margin-top: 1.5rem;
}
.tool-tag {
font-size: 0.62rem;
letter-spacing: 0.1em;
text-transform: uppercase;
padding: 0.4rem 0.9rem;
background: rgba(255,255,255,0.05);
border: 1px solid rgba(255,255,255,0.08);
color: var(–sand);
}

/* COMMITMENT */
.commitment {
border-top: 1px solid rgba(255,255,255,0.06);
padding: 7rem 3rem;
display: grid; grid-template-columns: 1fr 1fr; gap: 6rem;
align-items: center;
}
.commitment h2 {
font-family: ‘Fraunces’, serif;
font-size: clamp(2rem, 3.5vw, 3.2rem);
font-weight: 700;
line-height: 1.15;
color: var(–white);
margin-bottom: 1.5rem;
}
.commitment h2 em { color: var(–amber); font-style: italic; }
.commitment p {
font-size: 0.8rem;
line-height: 1.9;
color: var(–sand);
margin-bottom: 2.5rem;
max-width: 44ch;
}
.commit-stats {
display: grid; grid-template-columns: 1fr 1fr; gap: 1px;
background: rgba(255,255,255,0.06);
}
.commit-stat {
background: var(–black);
padding: 2.5rem;
}
.commit-stat .num {
font-family: ‘Fraunces’, serif;
font-size: 2.8rem;
font-weight: 700;
color: var(–amber);
line-height: 1;
margin-bottom: 0.5rem;
}
.commit-stat .label {
font-size: 0.68rem;
letter-spacing: 0.12em;
text-transform: uppercase;
color: var(–muted);
}

/* ENROLL */
.enroll {
background: var(–cream);
color: var(–black);
padding: 8rem 3rem;
text-align: center;
position: relative; overflow: hidden;
}
.enroll::before {
content: ‘APPLY’;
position: absolute; top: 50%; left: 50%;
transform: translate(-50%, -50%);
font-family: ‘Fraunces’, serif;
font-size: 22vw;
font-weight: 700;
opacity: 0.05;
color: var(–black);
pointer-events: none;
white-space: nowrap;
}
.enroll .section-label { color: var(–rust); }
.enroll h2 {
font-family: ‘Fraunces’, serif;
font-size: clamp(2.5rem, 5vw, 4.5rem);
font-weight: 700;
line-height: 1.1;
color: var(–black);
margin: 0 auto 1.5rem;
max-width: 18ch;
position: relative; z-index: 1;
}
.enroll p {
font-size: 0.82rem;
line-height: 1.9;
color: #5a5040;
margin: 0 auto 3rem;
max-width: 46ch;
position: relative; z-index: 1;
}
.enroll-form {
display: flex; flex-direction: column; align-items: center; gap: 1rem;
max-width: 480px; margin: 0 auto;
position: relative; z-index: 1;
}
.enroll-form input, .enroll-form select {
width: 100%;
font-family: ‘DM Mono’, monospace;
font-size: 0.78rem;
padding: 1rem 1.4rem;
background: var(–white);
border: 1px solid rgba(0,0,0,0.15);
color: var(–black);
outline: none;
transition: border-color 0.2s;
cursor: none;
appearance: none;
}
.enroll-form input::placeholder { color: #9a8e7a; }
.enroll-form input:focus, .enroll-form select:focus { border-color: var(–rust); }
.btn-enroll {
width: 100%;
font-family: ‘DM Mono’, monospace;
font-size: 0.8rem;
letter-spacing: 0.15em;
text-transform: uppercase;
padding: 1.1rem;
background: var(–black);
color: var(–cream);
border: none; cursor: none;
margin-top: 0.5rem;
transition: background 0.2s, transform 0.15s;
}
.btn-enroll:hover { background: var(–rust); transform: translateY(-2px); }
.enroll-note {
font-size: 0.65rem;
letter-spacing: 0.1em;
color: #9a8e7a;
margin-top: 1rem;
}

/* FOOTER */
footer {
border-top: 1px solid rgba(255,255,255,0.06);
padding: 3rem;
display: flex; align-items: center; justify-content: space-between;
}
.footer-logo {
font-family: ‘Syne’, sans-serif;
font-weight: 800;
font-size: 1rem;
letter-spacing: 0.12em;
color: var(–amber);
}
.footer-logo span { color: var(–muted); }
footer p {
font-size: 0.65rem;
letter-spacing: 0.1em;
color: var(–muted);
}

/* ANIMATIONS */
@keyframes fadeUp {
from { opacity: 0; transform: translateY(24px); }
to { opacity: 1; transform: translateY(0); }
}
@keyframes fadeIn {
from { opacity: 0; }
to { opacity: 1; }
}

.reveal {
opacity: 0;
transform: translateY(30px);
transition: opacity 0.7s ease, transform 0.7s ease;
}
.reveal.visible {
opacity: 1;
transform: none;
}

/* RESPONSIVE */
@media (max-width: 900px) {
nav { padding: 1.2rem 1.5rem; }
.nav-links { display: none; }
.hero { grid-template-columns: 1fr; }
.hero-right { display: none; }
.hero-left { padding: 8rem 1.5rem 4rem; }
.about { grid-template-columns: 1fr; }
.phases-grid { grid-template-columns: 1fr 1fr; }
.tracks-section { grid-template-columns: 1fr; }
.commitment { grid-template-columns: 1fr; gap: 3rem; }
.about-left, .about-right, .track { padding: 4rem 1.5rem; }
.phases-section { padding: 4rem 1.5rem; }
.commitment { padding: 4rem 1.5rem; }
.enroll { padding: 5rem 1.5rem; }
footer { flex-direction: column; gap: 1rem; text-align: center; }
}
</style>

</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->

<nav>
  <a href="#" class="nav-logo">KLABS <span>FOUNDRY</span></a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#phases">Curriculum</a></li>
    <li><a href="#tracks">Tracks</a></li>
    <li><a href="#enroll">Apply</a></li>
  </ul>
  <a href="#enroll" class="nav-cta">Apply Now</a>
</nav>

<!-- HERO -->

<section class="hero">
  <div class="hero-left">
    <p class="hero-tag">Kaintomia Labs — Foundry Program</p>
    <h1>Build ventures<br/>that <em>actually</em><br/>scale.</h1>
    <p class="hero-desc">
      A 12–16 week intensive program guiding founders from systems thinking to investor readiness — through real tools, real mentorship, and real builds.
    </p>
    <div class="hero-actions">
      <a href="#enroll" class="btn-primary">Apply to Cohort</a>
      <a href="#phases" class="btn-ghost">See curriculum</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-grid"></div>
    <div class="hero-stat-card">
      <div class="stat-item">
        <div class="stat-num">16</div>
        <div class="stat-label">Weeks max duration</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">6</div>
        <div class="stat-label">Curriculum phases</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">10+</div>
        <div class="stat-label">Industries covered</div>
      </div>
      <div class="stat-item">
        <div class="stat-num">2</div>
        <div class="stat-label">Founder tracks</div>
      </div>
    </div>
  </div>
</section>

<!-- TICKER STRIP -->

<div class="strip">
  <div class="strip-inner">
    <span>Systems Thinking</span>
    <span>Responsible AI</span>
    <span>No-Code Prototyping</span>
    <span>Venture Studio</span>
    <span>Automation</span>
    <span>Investor Readiness</span>
    <span>Ideathon</span>
    <span>Lean Canvas</span>
    <span>Customer Validation</span>
    <span>Business Automation</span>
    <!-- repeat for seamless scroll -->
    <span>Systems Thinking</span>
    <span>Responsible AI</span>
    <span>No-Code Prototyping</span>
    <span>Venture Studio</span>
    <span>Automation</span>
    <span>Investor Readiness</span>
    <span>Ideathon</span>
    <span>Lean Canvas</span>
    <span>Customer Validation</span>
    <span>Business Automation</span>
  </div>
</div>

<!-- ABOUT -->

<section class="about" id="about">
  <div class="about-left">
    <p class="section-label">What is KLABS Foundry?</p>
    <h2>Where <strong>technical depth</strong> meets creative ambition.</h2>
    <p>
      The Kaintomia Labs Foundry Program is an interdisciplinary founder training experience designed for the next generation of African entrepreneurs. You'll move from idea to investor-ready venture — building real tools, not just slides.
    </p>
  </div>
  <div class="about-right">
    <div class="goal-item reveal">
      <div class="goal-num">01</div>
      <div class="goal-text"><strong>Systems Thinking & Responsible AI</strong>Foster the mindset to see problems at scale and build with ethical AI literacy from day one.</div>
    </div>
    <div class="goal-item reveal">
      <div class="goal-num">02</div>
      <div class="goal-text"><strong>Interdisciplinary Innovation</strong>Integrate technical, creative, and business skills. Whether you're in fashion or fintech — you build here.</div>
    </div>
    <div class="goal-item reveal">
      <div class="goal-num">03</div>
      <div class="goal-text"><strong>Business Automation</strong>Teach scalable operations using real automation stacks — not theory. Launch with infrastructure that grows.</div>
    </div>
    <div class="goal-item reveal">
      <div class="goal-num">04</div>
      <div class="goal-text"><strong>Disciplined Founder Journey</strong>From ideation through validation to investor readiness — you leave with a live pilot and a portfolio.</div>
    </div>
  </div>
</section>

<!-- PHASES -->

<section class="phases-section" id="phases">
  <div class="phases-header reveal">
    <h2>Six phases.<br/>One complete<br/>founder.</h2>
    <p>Each phase builds on the last — structured, modular, and adaptable to your industry track.</p>
  </div>
  <div class="phases-grid">
    <div class="phase-card reveal">
      <div class="phase-num">Phase 01</div>
      <div class="phase-title">Systems & Context</div>
      <div class="phase-weeks">Weeks 1–2 · 15–20 hrs</div>
      <p class="phase-desc">Understand interconnected systems, responsible AI ethics, and map how your industry operates at a systems level.</p>
      <span class="phase-tag">Foundation</span>
    </div>
    <div class="phase-card reveal">
      <div class="phase-num">Phase 02</div>
      <div class="phase-title">Creation Studio</div>
      <div class="phase-weeks">Weeks 3–5 · 25–30 hrs</div>
      <p class="phase-desc">Hands-on prototyping: no-code tools for creatives, Python + ML for STEM founders. Build your first MVP.</p>
      <span class="phase-tag">Build</span>
    </div>
    <div class="phase-card reveal">
      <div class="phase-num">Phase 03</div>
      <div class="phase-title">Business & Value</div>
      <div class="phase-weeks">Weeks 6–8 · 25–30 hrs</div>
      <p class="phase-desc">Lean canvas, marketing automation, governance, and finance fundamentals — tailored for diverse founders.</p>
      <span class="phase-tag">Operations</span>
    </div>
    <div class="phase-card reveal">
      <div class="phase-num">Phase 04</div>
      <div class="phase-title">Ideathon</div>
      <div class="phase-weeks">Weeks 9–10 · 15–20 hrs</div>
      <p class="phase-desc">A 48-hour sprint to validate your idea with real users, automated feedback tools, and cross-industry teams.</p>
      <span class="phase-tag">Validate</span>
    </div>
    <div class="phase-card reveal">
      <div class="phase-num">Phase 05</div>
      <div class="phase-title">Venture Studio</div>
      <div class="phase-weeks">Weeks 11–13 · 20–25 hrs</div>
      <p class="phase-desc">Studio sprints with mentors. Launch a live beta, embed your full automation stack, and integrate with local ecosystems.</p>
      <span class="phase-tag">Launch</span>
    </div>
    <div class="phase-card reveal">
      <div class="phase-num">Phase 06</div>
      <div class="phase-title">Investor Ready</div>
      <div class="phase-weeks">Weeks 14–16 · Capstone</div>
      <p class="phase-desc">Final pitch preparation, capital pathways orientation, and portfolio completion. Present to your cohort and beyond.</p>
      <span class="phase-tag">Pitch</span>
    </div>
  </div>
</section>

<!-- TRACKS -->

<section class="tracks-section" id="tracks">
  <div class="track track-creatives">
    <div class="track-bg-text">CREAT</div>
    <p class="section-label">Track A</p>
    <p class="track-subtitle">Creatives Track</p>
    <h3>No-Code &<br/>Design-Led Builds</h3>
    <p>Designed for founders in fashion, media, entertainment, tourism, and education. You'll prototype using accessible tools without writing a single line of code — but your builds will be just as powerful.</p>
    <p>You'll learn to automate workflows, personalise customer experiences, and launch full e-commerce or digital service operations from scratch.</p>
    <div class="track-tools">
      <span class="tool-tag">Bubble</span>
      <span class="tool-tag">Glide</span>
      <span class="tool-tag">Canva AI</span>
      <span class="tool-tag">Zapier</span>
      <span class="tool-tag">Shopify</span>
      <span class="tool-tag">Hootsuite</span>
      <span class="tool-tag">Typeform</span>
      <span class="tool-tag">WooCommerce</span>
    </div>
  </div>
  <div class="track track-stem">
    <div class="track-bg-text">STEM</div>
    <p class="section-label">Track B</p>
    <p class="track-subtitle">STEM Track</p>
    <h3>Data-Driven &<br/>ML Prototypes</h3>
    <p>Built for technical founders in agritech, healthtech, biotech, engineering, and fintech. You'll work with real data pipelines, train machine learning classifiers, and build models that solve hard problems.</p>
    <p>Move from concept to working prototype using industry-relevant datasets and tools used in production environments.</p>
    <div class="track-tools">
      <span class="tool-tag">Python</span>
      <span class="tool-tag">Google Colab</span>
      <span class="tool-tag">Teachable Machine</span>
      <span class="tool-tag">Airtable</span>
      <span class="tool-tag">AI/ML</span>
      <span class="tool-tag">ChatGPT API</span>
      <span class="tool-tag">MonkeyLearn</span>
    </div>
  </div>
</section>

<!-- COMMITMENT -->

<section class="commitment">
  <div class="reveal">
    <p class="section-label">Time Commitment</p>
    <h2>Serious about <em>building?</em><br/>Here's what it takes.</h2>
    <p>The Foundry Program is an immersive part-time commitment. You'll dedicate focused hours each week across live sessions, independent builds, and mentorship rounds.</p>
    <a href="#enroll" class="btn-primary">I'm Ready — Apply</a>
  </div>
  <div class="commit-stats reveal">
    <div class="commit-stat">
      <div class="num">12–16</div>
      <div class="label">Total Weeks</div>
    </div>
    <div class="commit-stat">
      <div class="num">8–10</div>
      <div class="label">Hours per Week</div>
    </div>
    <div class="commit-stat">
      <div class="num">6</div>
      <div class="label">Curriculum Phases</div>
    </div>
    <div class="commit-stat">
      <div class="num">1</div>
      <div class="label">Live Pilot at Graduation</div>
    </div>
  </div>
</section>

<!-- ENROLL -->

<section class="enroll" id="enroll">
  <p class="section-label">Applications Open</p>
  <h2>Start your<br/>founder journey.</h2>
  <p>Join the next cohort of the KLABS Foundry Program. Fill in the form below and our team will reach out with next steps.</p>
  <div class="enroll-form">
    <input type="text" placeholder="Full name" />
    <input type="email" placeholder="Email address" />
    <select>
      <option value="" disabled selected>Select your track</option>
      <option value="creatives">Creatives Track — No-Code / Design</option>
      <option value="stem">STEM Track — Data / ML / Engineering</option>
      <option value="unsure">Not sure yet — help me decide</option>
    </select>
    <input type="text" placeholder="Your industry or venture idea (brief)" />
    <button class="btn-enroll" onclick="handleApply(event)">Submit Application</button>
    <p class="enroll-note">Applications reviewed on a rolling basis. Cohort size is limited.</p>
  </div>
</section>

<!-- FOOTER -->

<footer>
  <div class="footer-logo">KLABS <span>FOUNDRY</span></div>
  <p>© 2025 Kaintomia Labs. All rights reserved.</p>
  <p>Kampala, Uganda</p>
</footer>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
  function animateCursor() {
    cursor.style.left = mx + 'px'; cursor.style.top = my + 'px';
    rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px'; ring.style.top = ry + 'px';
    requestAnimationFrame(animateCursor);
  }
  animateCursor();
  document.querySelectorAll('a, button, input, select').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.style.width = '20px'; cursor.style.height = '20px'; ring.style.opacity = '1'; });
    el.addEventListener('mouseleave', () => { cursor.style.width = '12px'; cursor.style.height = '12px'; ring.style.opacity = '0.5'; });
  });

  // Reveal on scroll
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => entry.target.classList.add('visible'), i * 60);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });
  reveals.forEach(el => observer.observe(el));

  // Apply form
  function handleApply(e) {
    e.preventDefault();
    const btn = e.target;
    btn.textContent = '✓ Application Received';
    btn.style.background = '#1d4230';
    btn.disabled = true;
  }
</script>

</body>
</html>

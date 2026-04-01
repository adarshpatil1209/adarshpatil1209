<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Adarsh Patil — Developer Profile</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@300;400;500;600&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg:       #070a10;
      --surface:  #0c1018;
      --card:     #101520;
      --card2:    #131824;
      --border:   #1c2233;
      --accent:   #38f5c0;
      --accent2:  #5e7eff;
      --accent3:  #ff6b9d;
      --gold:     #ffc75f;
      --text:     #dce3f0;
      --muted:    #5a6480;
      --sub:      #8892aa;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'JetBrains Mono', monospace;
      background: var(--bg);
      color: var(--text);
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* grid bg */
    body::before {
      content: '';
      position: fixed; inset: 0;
      background-image:
        linear-gradient(rgba(28,34,51,0.6) 1px, transparent 1px),
        linear-gradient(90deg, rgba(28,34,51,0.6) 1px, transparent 1px);
      background-size: 36px 36px;
      pointer-events: none; z-index: 0;
    }

    /* orbs */
    .orb {
      position: fixed; border-radius: 50%;
      filter: blur(120px); pointer-events: none; z-index: 0;
      animation: drift 18s ease-in-out infinite alternate;
    }
    .o1 { width:600px;height:600px;background:#2a3fff;opacity:.12;top:-200px;left:-150px;animation-duration:20s; }
    .o2 { width:450px;height:450px;background:#38f5c0;opacity:.10;bottom:-150px;right:-100px;animation-duration:14s;animation-delay:-6s; }
    .o3 { width:300px;height:300px;background:#ff6b9d;opacity:.09;top:45%;left:50%;animation-duration:22s;animation-delay:-11s; }
    @keyframes drift {
      from { transform: translate(0,0) scale(1); }
      to   { transform: translate(50px,35px) scale(1.1); }
    }

    /* layout */
    .page {
      position: relative; z-index: 1;
      max-width: 940px; margin: 0 auto;
      padding: 44px 22px 90px;
      display: flex; flex-direction: column; gap: 22px;
    }

    /* ── HERO ── */
    .hero {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 22px;
      padding: 38px 36px;
      display: grid;
      grid-template-columns: 130px 1fr;
      gap: 32px;
      align-items: center;
      position: relative; overflow: hidden;
      animation: fadeUp .55s ease both;
    }
    .hero::before {
      content: '';
      position: absolute; top:-1px; left:0; right:0; height:2.5px;
      background: linear-gradient(90deg, var(--accent2), var(--accent), var(--accent3));
    }
    .hero::after {
      content: '';
      position: absolute; inset:0;
      background: radial-gradient(ellipse at top left, rgba(56,245,192,.05) 0%, transparent 55%);
      pointer-events: none;
    }

    .avatar-ring {
      position: relative; width:120px; height:120px; flex-shrink:0;
    }
    .avatar-ring::before {
      content: '';
      position: absolute; inset:-4px; border-radius:50%;
      background: conic-gradient(var(--accent), var(--accent2), var(--accent3), var(--accent));
      animation: spin 5s linear infinite;
    }
    .avatar-ring::after {
      content: '';
      position: absolute; inset:-2px; border-radius:50%;
      background: var(--card);
    }
    .avatar-ring img {
      width:120px; height:120px; border-radius:50%;
      display:block; object-fit:cover;
      position:relative; z-index:2;
    }
    .avatar-fallback {
      width:120px; height:120px; border-radius:50%;
      background: linear-gradient(135deg, var(--accent2), var(--accent));
      display:flex; align-items:center; justify-content:center;
      font-family:'Syne',sans-serif; font-size:2.4rem; font-weight:800;
      color:#07090e; position:relative; z-index:2;
    }
    @keyframes spin { to { transform:rotate(360deg); } }

    .hero-body { position:relative; z-index:2; }

    .hero-tag {
      display:inline-flex; align-items:center; gap:7px;
      font-size:.65rem; letter-spacing:.12em; text-transform:uppercase;
      color:var(--accent); border:1px solid rgba(56,245,192,.25);
      background:rgba(56,245,192,.07); border-radius:20px;
      padding:4px 12px; margin-bottom:12px;
    }
    .tag-dot { width:6px;height:6px;border-radius:50%;background:var(--accent);animation:pulse 2s infinite; }
    @keyframes pulse { 0%,100%{opacity:1;transform:scale(1);} 50%{opacity:.4;transform:scale(.7);} }

    .hero-name {
      font-family:'Syne',sans-serif; font-size:clamp(1.8rem,4vw,2.6rem);
      font-weight:800; letter-spacing:-.03em; color:var(--text); line-height:1.1;
    }
    .hero-title {
      font-size:.78rem; color:var(--sub); margin:8px 0 14px;
      letter-spacing:.04em;
    }
    .hero-title span { color:var(--accent2); }

    .hero-links {
      display:flex; flex-wrap:wrap; gap:10px; margin-top:18px;
    }
    .hero-link {
      display:inline-flex; align-items:center; gap:7px;
      padding:8px 16px; border-radius:9px; font-size:.7rem;
      font-weight:500; letter-spacing:.04em; text-decoration:none;
      transition:transform .2s, opacity .2s;
      border:1px solid var(--border);
    }
    .hero-link:hover { transform:translateY(-2px); opacity:.85; }
    .hl-gh  { background:rgba(255,255,255,.05); color:var(--text); }
    .hl-li  { background:rgba(94,126,255,.12); color:var(--accent2); border-color:rgba(94,126,255,.3); }

    /* ── 2-col layout ── */
    .two-col {
      display:grid; grid-template-columns:1fr 1fr; gap:22px;
    }

    /* ── CARD ── */
    .card {
      background:var(--card); border:1px solid var(--border);
      border-radius:18px; padding:26px;
      animation:fadeUp .55s ease both;
      transition:border-color .2s, transform .2s;
    }
    .card:hover { border-color:rgba(56,245,192,.2); transform:translateY(-2px); }

    /* section title */
    .sec-title {
      display:flex; align-items:center; gap:10px; margin-bottom:18px;
    }
    .sec-icon {
      width:30px; height:30px; border-radius:9px;
      display:flex; align-items:center; justify-content:center; font-size:.95rem;
      flex-shrink:0;
    }
    .sec-icon.green  { background:rgba(56,245,192,.12); }
    .sec-icon.blue   { background:rgba(94,126,255,.12); }
    .sec-icon.pink   { background:rgba(255,107,157,.12); }
    .sec-icon.gold   { background:rgba(255,199,95,.12); }

    .sec-label {
      font-family:'Syne',sans-serif; font-size:.72rem; font-weight:700;
      letter-spacing:.14em; text-transform:uppercase; color:var(--muted);
    }
    .sec-line { flex:1; height:1px; background:var(--border); }

    /* ── STATS (GitHub live) ── */
    .stats-row {
      display:grid; grid-template-columns:repeat(4,1fr); gap:14px;
    }
    .stat-box {
      background:var(--card); border:1px solid var(--border);
      border-radius:14px; padding:18px 12px; text-align:center;
      transition:border-color .2s, transform .2s;
      animation:fadeUp .55s ease both;
    }
    .stat-box:hover { border-color:var(--accent); transform:translateY(-3px); }
    .stat-num {
      font-family:'Syne',sans-serif; font-size:1.9rem; font-weight:800;
      color:var(--text); line-height:1;
    }
    .stat-lbl {
      font-size:.62rem; color:var(--muted);
      letter-spacing:.1em; text-transform:uppercase; margin-top:5px;
    }

    /* ── SKILLS ── */
    .skill-group { margin-bottom:18px; }
    .skill-group:last-child { margin-bottom:0; }
    .skill-group-title {
      font-size:.62rem; color:var(--muted); letter-spacing:.1em;
      text-transform:uppercase; margin-bottom:10px;
    }
    .skill-tags {
      display:flex; flex-wrap:wrap; gap:7px;
    }
    .skill-tag {
      display:inline-flex; align-items:center; gap:6px;
      padding:5px 12px; border-radius:7px; font-size:.7rem;
      border:1px solid var(--border); background:var(--card2);
      color:var(--sub); transition:all .2s; cursor:default;
    }
    .skill-tag:hover { border-color:var(--accent); color:var(--accent); }
    .skill-tag .dot { width:6px;height:6px;border-radius:50%; }

    /* lang colors */
    .py   { background:#3572A5; }
    .c    { background:#555555; }
    .cpp  { background:#f34b7d; }
    .html { background:#e34c26; }
    .grn  { background:#38f5c0; }
    .blu  { background:#5e7eff; }
    .pnk  { background:#ff6b9d; }
    .gld  { background:#ffc75f; }

    /* ── CURRENTLY WORKING ── */
    .work-item {
      display:flex; align-items:flex-start; gap:12px;
      padding:12px 0; border-bottom:1px solid var(--border);
    }
    .work-item:last-child { border-bottom:none; padding-bottom:0; }
    .work-dot {
      width:8px; height:8px; border-radius:50%;
      background:var(--accent); margin-top:5px; flex-shrink:0;
      box-shadow:0 0 8px var(--accent);
    }
    .work-text { font-size:.78rem; color:var(--sub); line-height:1.6; }
    .work-text strong { color:var(--text); }

    /* ── GOALS ── */
    .goal-item {
      display:flex; align-items:center; gap:12px;
      padding:10px 12px; border-radius:9px;
      border:1px solid var(--border); background:var(--card2);
      margin-bottom:8px; transition:border-color .2s;
    }
    .goal-item:last-child { margin-bottom:0; }
    .goal-item:hover { border-color:rgba(56,245,192,.3); }
    .goal-icon { font-size:.95rem; flex-shrink:0; }
    .goal-text { font-size:.74rem; color:var(--sub); }

    /* ── REPOS ── */
    .repos-grid {
      display:grid; grid-template-columns:repeat(2,1fr); gap:14px;
    }
    .repo-card {
      background:var(--card2); border:1px solid var(--border);
      border-radius:14px; padding:20px;
      display:flex; flex-direction:column; gap:9px;
      text-decoration:none; color:inherit;
      transition:border-color .2s, transform .2s, box-shadow .2s;
      position:relative; overflow:hidden;
    }
    .repo-card::before {
      content:''; position:absolute; top:0;left:0;bottom:0;width:3px;
      background:linear-gradient(var(--accent2), var(--accent));
      opacity:0; transition:opacity .2s;
    }
    .repo-card:hover { border-color:var(--border); transform:translateY(-3px); box-shadow:0 14px 40px rgba(0,0,0,.45); }
    .repo-card:hover::before { opacity:1; }
    .repo-name {
      font-family:'Syne',sans-serif; font-size:.84rem; font-weight:700;
      color:var(--accent); display:flex; align-items:center; gap:7px;
    }
    .repo-desc { font-size:.7rem; color:var(--muted); line-height:1.6; flex:1; }
    .repo-meta { display:flex; align-items:center; gap:12px; }
    .repo-lang { display:flex; align-items:center; gap:5px; font-size:.66rem; color:var(--muted); }
    .lang-dot { width:8px;height:8px;border-radius:50%; }
    .repo-stat { display:flex; align-items:center; gap:4px; font-size:.66rem; color:var(--muted); }

    /* ── FOOTER strip ── */
    .footer-strip {
      background:var(--card); border:1px solid var(--border);
      border-radius:16px; padding:22px 28px;
      display:flex; align-items:center; justify-content:space-between; gap:16px;
      animation:fadeUp .55s ease both;
    }
    .footer-txt { font-size:.76rem; color:var(--muted); }
    .footer-txt strong { color:var(--text); font-family:'Syne',sans-serif; }
    .gh-btn {
      display:inline-flex; align-items:center; gap:8px;
      padding:10px 22px; border-radius:9px;
      background:linear-gradient(135deg, var(--accent2), var(--accent));
      color:#07090e; font-family:'Syne',sans-serif;
      font-size:.72rem; font-weight:700; letter-spacing:.05em;
      text-decoration:none; transition:opacity .2s, transform .2s;
    }
    .gh-btn:hover { opacity:.85; transform:scale(1.04); }

    /* loading */
    #loading {
      display:flex; flex-direction:column;
      align-items:center; justify-content:center;
      min-height:60vh; gap:18px;
    }
    .spinner {
      width:42px; height:42px;
      border:2px solid var(--border); border-top-color:var(--accent);
      border-radius:50%; animation:spin .85s linear infinite;
    }
    #loading p { color:var(--muted); font-size:.75rem; letter-spacing:.1em; }

    @keyframes fadeUp {
      from { opacity:0; transform:translateY(20px); }
      to   { opacity:1; transform:translateY(0); }
    }

    /* stagger */
    .d1{animation-delay:.05s} .d2{animation-delay:.10s} .d3{animation-delay:.15s}
    .d4{animation-delay:.20s} .d5{animation-delay:.25s} .d6{animation-delay:.30s}
    .d7{animation-delay:.35s} .d8{animation-delay:.40s}

    @media(max-width:700px){
      .hero { grid-template-columns:1fr; text-align:center; }
      .avatar-ring { margin:0 auto; }
      .hero-links { justify-content:center; }
      .two-col { grid-template-columns:1fr; }
      .stats-row { grid-template-columns:repeat(2,1fr); }
      .repos-grid { grid-template-columns:1fr; }
      .footer-strip { flex-direction:column; text-align:center; }
    }
  </style>
</head>
<body>

<div class="o1 orb"></div>
<div class="o2 orb"></div>
<div class="o3 orb"></div>

<div class="page">

  <!-- Loading -->
  <div id="loading">
    <div class="spinner"></div>
    <p>// initializing profile</p>
  </div>

  <!-- Content injected by JS -->
  <div id="content" style="display:none"></div>

</div>

<script>
const USERNAME = 'adarshpatil1209';

const langColors = {
  JavaScript:'#f7df1e', TypeScript:'#3178c6', Python:'#3572A5',
  Java:'#b07219', 'C++':'#f34b7d', C:'#555555', HTML:'#e34c26',
  CSS:'#563d7c', Shell:'#89e051', Dart:'#00B4AB', Go:'#00ADD8',
  default:'#8b949e'
};

const ico = {
  gh: `<svg width="15" height="15" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844a9.59 9.59 0 012.504.337c1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.02 10.02 0 0022 12.017C22 6.484 17.522 2 12 2z"/></svg>`,
  li: `<svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>`,
  repo:`<svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M15 22v-4a4.8 4.8 0 00-1-3.5c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.403 5.403 0 004 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65S9 17.44 9 18v4"/><path d="M9 18c-4.51 2-5-2-7-2"/></svg>`,
  star:`<svg width="11" height="11" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"/></svg>`,
  fork:`<svg width="11" height="11" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="18" cy="18" r="3"/><circle cx="6" cy="6" r="3"/><path d="M6 21V9a9 9 0 009 9"/></svg>`,
};

const skills = {
  "💻 Languages": [
    { name:"Python", dot:"py" }, { name:"C", dot:"c" },
    { name:"C++ (Learning)", dot:"cpp" }, { name:"HTML", dot:"html" }
  ],
  "🧠 Core Concepts": [
    { name:"Data Structures & Algorithms", dot:"grn" },
    { name:"AI & Machine Learning", dot:"blu" },
    { name:"Problem Solving", dot:"pnk" }
  ],
  "🛠️ Tools": [
    { name:"Git & GitHub", dot:"grn" }, { name:"VS Code", dot:"blu" },
    { name:"Figma", dot:"pnk" }, { name:"Canva", dot:"gld" }
  ]
};

const working = [
  { title:"DSA & Problem Solving", desc:"Strengthening algorithmic thinking and competitive programming" },
  { title:"Machine Learning & AI", desc:"Learning core ML concepts, models and hands-on implementations" },
  { title:"Python Projects", desc:"Building real-world projects to apply concepts practically" },
];

const goals = [
  { icon:"🌍", text:"Contribute to Open Source Projects" },
  { icon:"🚀", text:"Build impactful AI-powered applications" },
  { icon:"💡", text:"Solve real-world problems using technology" },
];

async function load() {
  const [uRes, rRes] = await Promise.all([
    fetch(`https://api.github.com/users/${USERNAME}`),
    fetch(`https://api.github.com/users/${USERNAME}/repos?sort=updated&per_page=30`)
  ]);
  const user  = await uRes.json();
  const repos = await rRes.json();
  return { user, repos };
}

function skillTagsHTML(items) {
  return items.map(s =>
    `<span class="skill-tag"><span class="dot ${s.dot}"></span>${s.name}</span>`
  ).join('');
}

function render(user, repos) {
  const sorted = repos
    .filter(r => !r.fork)
    .sort((a, b) => b.stargazers_count - a.stargazers_count)
    .slice(0, 6);

  const totalStars = repos.reduce((s, r) => s + r.stargazers_count, 0);

  const repoCards = sorted.map(r => `
    <a class="repo-card" href="${r.html_url}" target="_blank" rel="noopener">
      <div class="repo-name">${ico.repo} ${r.name}</div>
      <div class="repo-desc">${r.description || '— no description —'}</div>
      <div class="repo-meta">
        ${r.language ? `<span class="repo-lang"><span class="lang-dot" style="background:${langColors[r.language]||langColors.default}"></span>${r.language}</span>` : ''}
        <span class="repo-stat">${ico.star} ${r.stargazers_count}</span>
        <span class="repo-stat">${ico.fork} ${r.forks_count}</span>
      </div>
    </a>`).join('');

  const skillGroupsHTML = Object.entries(skills).map(([group, items]) => `
    <div class="skill-group">
      <div class="skill-group-title">${group}</div>
      <div class="skill-tags">${skillTagsHTML(items)}</div>
    </div>`).join('');

  const workHTML = working.map(w => `
    <div class="work-item">
      <div class="work-dot"></div>
      <div class="work-text"><strong>${w.title}</strong><br/>${w.desc}</div>
    </div>`).join('');

  const goalHTML = goals.map(g => `
    <div class="goal-item">
      <span class="goal-icon">${g.icon}</span>
      <span class="goal-text">${g.text}</span>
    </div>`).join('');

  return `
    <!-- HERO -->
    <div class="hero d1">
      <div class="avatar-ring">
        ${user.avatar_url
          ? `<img src="${user.avatar_url}" alt="Adarsh Patil"/>`
          : `<div class="avatar-fallback">AP</div>`}
      </div>
      <div class="hero-body">
        <div class="hero-tag"><span class="tag-dot"></span>Open to Opportunities</div>
        <div class="hero-name">${user.name || 'Adarsh Patil'}</div>
        <div class="hero-title">🚀 AI &amp; ML Enthusiast &nbsp;|&nbsp; <span>Computer Science Engineer</span></div>
        <div style="font-size:.75rem;color:var(--sub);line-height:1.7;max-width:520px;">
          ${user.bio || 'CS Engineering student specialising in AI &amp; ML — passionate about building intelligent systems and solving real-world problems.'}
        </div>
        <div class="hero-links">
          <a class="hero-link hl-gh" href="https://github.com/${USERNAME}" target="_blank" rel="noopener">
            ${ico.gh} @${USERNAME}
          </a>
          <a class="hero-link hl-li" href="https://www.linkedin.com/in/adarsh-patil-409465383/" target="_blank" rel="noopener">
            ${ico.li} LinkedIn
          </a>
        </div>
      </div>
    </div>

    <!-- STATS -->
    <div class="stats-row">
      <div class="stat-box d2"><div class="stat-num">${user.public_repos ?? '—'}</div><div class="stat-lbl">Repos</div></div>
      <div class="stat-box d3"><div class="stat-num">${user.followers ?? '—'}</div><div class="stat-lbl">Followers</div></div>
      <div class="stat-box d4"><div class="stat-num">${user.following ?? '—'}</div><div class="stat-lbl">Following</div></div>
      <div class="stat-box d5"><div class="stat-num">${totalStars}</div><div class="stat-lbl">Stars</div></div>
    </div>

    <!-- SKILLS + CURRENTLY WORKING -->
    <div class="two-col">
      <div class="card d3">
        <div class="sec-title">
          <div class="sec-icon green">⚡</div>
          <span class="sec-label">Skills &amp; Technologies</span>
          <div class="sec-line"></div>
        </div>
        ${skillGroupsHTML}
      </div>

      <div class="card d4">
        <div class="sec-title">
          <div class="sec-icon blue">🔭</div>
          <span class="sec-label">Currently Working On</span>
          <div class="sec-line"></div>
        </div>
        ${workHTML}
      </div>
    </div>

    <!-- GOALS + REPOS header -->
    <div class="two-col">
      <div class="card d5">
        <div class="sec-title">
          <div class="sec-icon gold">🎯</div>
          <span class="sec-label">Goals</span>
          <div class="sec-line"></div>
        </div>
        ${goalHTML}
      </div>

      <div class="card d6" style="background:var(--card);">
        <div class="sec-title">
          <div class="sec-icon pink">🎓</div>
          <span class="sec-label">About Me</span>
          <div class="sec-line"></div>
        </div>
        <div style="display:flex;flex-direction:column;gap:10px;">
          ${[
            ['🎓','CS Engineering student (AI &amp; ML specialization)'],
            ['💡','Passionate about intelligent systems &amp; real-world problems'],
            ['🔍','Exploring new technologies, continuously improving'],
            ['🌱','Currently learning C++ and diving deeper into ML'],
          ].map(([e,t]) => `
            <div style="display:flex;align-items:flex-start;gap:10px;font-size:.75rem;color:var(--sub);line-height:1.6;">
              <span style="font-size:.9rem;margin-top:1px;">${e}</span><span>${t}</span>
            </div>`).join('')}
        </div>
      </div>
    </div>

    <!-- REPOS -->
    <div class="card d6" style="padding:26px;">
      <div class="sec-title">
        <div class="sec-icon green">📁</div>
        <span class="sec-label">Top Repositories</span>
        <div class="sec-line"></div>
      </div>
      <div class="repos-grid">${repoCards || '<p style="color:var(--muted);font-size:.78rem;">No public repositories yet.</p>'}</div>
    </div>

    <!-- FOOTER -->
    <div class="footer-strip d7">
      <div class="footer-txt">
        <strong>Adarsh Patil</strong> · AI &amp; ML Enthusiast<br/>
        <span style="font-size:.68rem;">Building the future, one commit at a time 🚀</span>
      </div>
      <a class="gh-btn" href="https://github.com/${USERNAME}" target="_blank" rel="noopener">
        ${ico.gh} View Full Profile
      </a>
    </div>
  `;
}

(async () => {
  const loading = document.getElementById('loading');
  const content = document.getElementById('content');
  try {
    const { user, repos } = await load();
    if (user.message) throw new Error(user.message);
    content.innerHTML = render(user, repos);
    loading.style.display = 'none';
    content.style.display = 'contents';
  } catch(e) {
    loading.innerHTML = `<div style="color:#ff6b6b;background:rgba(255,107,107,.08);border:1px solid rgba(255,107,107,.2);border-radius:10px;padding:16px 20px;font-size:.78rem;">// Error: ${e.message}</div>`;
  }
})();
</script>
</body>
</html>

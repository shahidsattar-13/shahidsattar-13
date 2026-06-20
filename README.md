<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Shahid Sattar — Software Engineering Student</title>
<meta name="description" content="Portfolio of Shahid Sattar, Software Engineering student at QUEST Nawabshah, Pakistan. HTML, CSS, JavaScript, Java, C, Python, MySQL.">
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Crect width='100' height='100' rx='20' fill='%230d1117'/%3E%3Ctext x='50' y='62' font-size='40' text-anchor='middle' fill='%232ee6a6' font-family='monospace'%3E%3C/%3E%3C/text%3E%3C/svg%3E">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600;700&family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
<style>
  :root{
    --bg:#0d1117;
    --bg-panel:#11161d;
    --bg-elevated:#161c25;
    --bg-card:#1a212c;
    --border:#262d38;
    --border-soft:#1d2430;
    --text-primary:#c9d1d9;
    --text-secondary:#8b949e;
    --text-dim:#586069;
    --accent-green:#2ee6a6;
    --accent-amber:#ffb454;
    --accent-blue:#5cc8ff;
    --accent-purple:#c792ea;
    --accent-red:#ff6b6b;
    --font-mono:'JetBrains Mono', monospace;
    --font-sans:'Inter', sans-serif;
    --bar-h:42px;
    --status-h:34px;
  }

  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  @media (prefers-reduced-motion: reduce){
    html{scroll-behavior:auto;}
    *{animation-duration:0.001ms !important; animation-iteration-count:1 !important; transition-duration:0.001ms !important;}
  }

  body{
    margin:0;
    background:var(--bg);
    color:var(--text-primary);
    font-family:var(--font-sans);
    padding-top:var(--bar-h);
    padding-bottom:var(--status-h);
    -webkit-font-smoothing:antialiased;
  }

  a{color:inherit;}
  ::selection{background:rgba(46,230,166,0.25); color:#fff;}

  :focus-visible{
    outline:2px solid var(--accent-green);
    outline-offset:2px;
    border-radius:3px;
  }

  /* ---------- TAB BAR ---------- */
  .tab-bar{
    position:fixed;
    top:0; left:0; right:0;
    height:var(--bar-h);
    background:var(--bg-panel);
    border-bottom:1px solid var(--border);
    display:flex;
    align-items:center;
    z-index:100;
    overflow-x:auto;
    scrollbar-width:none;
  }
  .tab-bar::-webkit-scrollbar{display:none;}

  .window-dots{
    display:flex;
    gap:7px;
    padding:0 16px;
    flex-shrink:0;
  }
  .window-dots span{width:11px; height:11px; border-radius:50%; display:inline-block;}
  .window-dots span:nth-child(1){background:#ff5f56;}
  .window-dots span:nth-child(2){background:#ffbd2e;}
  .window-dots span:nth-child(3){background:#27c93f;}

  .tabs{
    display:flex;
    height:100%;
    flex-shrink:0;
  }
  .tab{
    font-family:var(--font-mono);
    font-size:12.5px;
    color:var(--text-secondary);
    background:transparent;
    border:none;
    border-right:1px solid var(--border-soft);
    padding:0 16px;
    height:100%;
    display:flex;
    align-items:center;
    gap:7px;
    cursor:pointer;
    white-space:nowrap;
    position:relative;
    transition:color .15s ease, background .15s ease;
  }
  .tab i{font-size:11px; opacity:.7;}
  .tab:hover{color:var(--text-primary); background:var(--bg-elevated);}
  .tab.active{color:var(--text-primary); background:var(--bg);}
  .tab.active::after{
    content:"";
    position:absolute;
    bottom:0; left:0; right:0;
    height:2px;
    background:var(--accent-green);
  }

  /* ---------- STATUS BAR ---------- */
  .status-bar{
    position:fixed;
    bottom:0; left:0; right:0;
    height:var(--status-h);
    background:var(--accent-green);
    color:#06241a;
    font-family:var(--font-mono);
    font-size:11.5px;
    font-weight:600;
    display:flex;
    align-items:center;
    justify-content:space-between;
    padding:0 14px;
    z-index:100;
    gap:10px;
  }
  .status-bar .left, .status-bar .right{display:flex; align-items:center; gap:16px; overflow:hidden;}
  .status-bar .right{flex-shrink:0;}
  .status-bar .item{display:flex; align-items:center; gap:5px; white-space:nowrap;}
  .status-bar #status-file{
    overflow:hidden; text-overflow:ellipsis;
  }

  /* ---------- LAYOUT HELPERS ---------- */
  .wrap{
    max-width:880px;
    margin:0 auto;
    padding:0 24px;
  }
  section{scroll-margin-top:calc(var(--bar-h) + 18px);}

  .file-label{
    font-family:var(--font-mono);
    font-size:12px;
    color:var(--text-dim);
    display:flex;
    align-items:center;
    gap:8px;
    margin-bottom:18px;
    letter-spacing:.02em;
  }
  .file-label::before{content:"›"; color:var(--accent-green);}

  .panel{
    background:var(--bg-panel);
    border:1px solid var(--border);
    border-radius:10px;
    overflow:hidden;
  }

  .code-block{
    counter-reset:line;
    padding:22px 0;
    font-family:var(--font-mono);
    font-size:14px;
    line-height:1.85;
  }
  .line{
    counter-increment:line;
    padding:0 22px 0 56px;
    position:relative;
    white-space:pre-wrap;
    word-break:break-word;
  }
  .line::before{
    content:counter(line, decimal-leading-zero);
    position:absolute;
    left:0;
    width:40px;
    text-align:right;
    color:var(--text-dim);
    font-size:12px;
    user-select:none;
  }
  .line.dim{color:var(--text-secondary);}
  .line.indent-1{padding-left:76px;}
  .line.indent-2{padding-left:96px;}
  .line.blank{height:.85em;}

  .kw{color:var(--accent-purple);}
  .cls{color:var(--accent-amber);}
  .str{color:var(--accent-green);}
  .prop{color:var(--accent-blue);}
  .com{color:var(--text-dim); font-style:italic;}
  .num{color:var(--accent-amber);}
  .punct{color:var(--text-secondary);}
  .hash{color:var(--accent-amber);}
  .git-msg{color:var(--text-primary);}
  .git-head{color:var(--accent-green);}

  @media (max-width:640px){
    .line::before{display:none;}
    .line{padding-left:22px;}
    .line.indent-1{padding-left:38px;}
    .line.indent-2{padding-left:54px;}
  }

  /* ---------- HERO ---------- */
  .hero{
    padding:64px 0 56px;
  }
  .hero .code-block{padding:26px 0 8px;}
  .hero-cursor{
    display:inline-block;
    width:9px; height:1.05em;
    background:var(--accent-green);
    vertical-align:text-bottom;
    margin-left:2px;
    animation:blink 1s steps(1) infinite;
  }
  @keyframes blink{50%{opacity:0;}}

  .hero-cta{
    display:flex;
    gap:14px;
    flex-wrap:wrap;
    padding:8px 22px 0;
  }
  .btn{
    font-family:var(--font-mono);
    font-size:13px;
    font-weight:500;
    padding:11px 20px;
    border-radius:7px;
    border:1px solid var(--border);
    cursor:pointer;
    text-decoration:none;
    display:inline-flex;
    align-items:center;
    gap:8px;
    transition:transform .15s ease, border-color .15s ease, background .15s ease;
  }
  .btn-primary{background:var(--accent-green); color:#06241a; border-color:var(--accent-green); font-weight:600;}
  .btn-primary:hover{transform:translateY(-2px); box-shadow:0 8px 20px -8px rgba(46,230,166,0.5);}
  .btn-ghost{background:transparent; color:var(--text-primary);}
  .btn-ghost:hover{border-color:var(--accent-green); color:var(--accent-green); transform:translateY(-2px);}

  .eyebrow{
    font-family:var(--font-mono);
    font-size:12px;
    color:var(--accent-green);
    padding:0 22px;
    margin-bottom:6px;
    letter-spacing:.04em;
  }

  /* ---------- SECTIONS GENERAL ---------- */
  .section{padding:54px 0;}
  .section + .section{border-top:1px solid var(--border-soft);}

  .reveal{opacity:0; transform:translateY(14px); transition:opacity .55s ease, transform .55s ease;}
  .reveal.in-view{opacity:1; transform:translateY(0);}

  /* ---------- PROJECTS ---------- */
  .project-grid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:16px;
  }
  @media (max-width:700px){.project-grid{grid-template-columns:1fr;}}

  .project-card{
    background:var(--bg-panel);
    border:1px solid var(--border);
    border-radius:10px;
    overflow:hidden;
    transition:transform .18s ease, border-color .18s ease;
  }
  .project-card:hover{transform:translateY(-3px); border-color:var(--accent-green);}
  .project-card .code-block{padding:16px 0; font-size:12.8px; line-height:1.7;}
  .project-card .line{padding-left:42px;}
  .project-card .line::before{width:26px; font-size:10.5px;}
  .project-desc{
    font-family:var(--font-sans);
    font-size:13px;
    color:var(--text-secondary);
    padding:0 18px 16px;
    border-top:1px solid var(--border-soft);
    margin-top:4px;
    padding-top:14px;
    line-height:1.55;
  }
  @media (max-width:640px){
    .project-card .line::before{display:none;}
    .project-card .line{padding-left:18px;}
  }

  /* ---------- SKILLS ---------- */
  .skill-groups{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:14px;
    margin-top:22px;
  }
  @media (max-width:640px){.skill-groups{grid-template-columns:1fr;}}
  .skill-group{
    background:var(--bg-panel);
    border:1px solid var(--border);
    border-radius:10px;
    padding:18px 18px 16px;
  }
  .skill-group h3{
    font-family:var(--font-mono);
    font-size:12px;
    color:var(--accent-blue);
    margin:0 0 12px;
    font-weight:600;
  }
  .pill-row{display:flex; flex-wrap:wrap; gap:8px;}
  .pill{
    font-family:var(--font-mono);
    font-size:12px;
    color:var(--text-primary);
    background:var(--bg-elevated);
    border:1px solid var(--border-soft);
    padding:5px 11px;
    border-radius:5px;
  }

  /* ---------- EDUCATION ---------- */
  .timeline{position:relative; margin-top:24px; padding-left:26px;}
  .timeline::before{
    content:"";
    position:absolute;
    left:6px; top:6px; bottom:6px;
    width:1px;
    background:var(--border);
  }
  .tl-item{position:relative; padding-bottom:30px;}
  .tl-item:last-child{padding-bottom:0;}
  .tl-item::before{
    content:"";
    position:absolute;
    left:-26px; top:4px;
    width:11px; height:11px;
    border-radius:50%;
    background:var(--bg);
    border:2px solid var(--accent-green);
  }
  .tl-degree{font-weight:700; font-size:16px; color:var(--text-primary);}
  .tl-inst{font-size:14px; color:var(--text-secondary); margin-top:3px;}
  .tl-years{font-family:var(--font-mono); font-size:12px; color:var(--accent-amber); margin-top:6px;}

  /* ---------- CONTACT ---------- */
  .contact-panel{padding:28px 0;}
  .contact-lead{
    font-size:15px;
    color:var(--text-secondary);
    padding:0 22px 18px;
    line-height:1.6;
    max-width:520px;
  }
  .contact-rows{padding:0 22px;}
  .contact-row{
    display:flex;
    align-items:center;
    gap:12px;
    padding:11px 0;
    border-top:1px solid var(--border-soft);
    font-family:var(--font-mono);
    font-size:13.5px;
  }
  .contact-row:first-child{border-top:none;}
  .contact-row i{color:var(--accent-green); width:16px;}
  .contact-row a{text-decoration:none; color:var(--text-primary);}
  .contact-row a:hover{color:var(--accent-green);}
  .contact-cta{display:flex; gap:14px; flex-wrap:wrap; padding:22px 22px 4px;}

  footer{
    text-align:center;
    padding:36px 24px 0;
    font-family:var(--font-mono);
    font-size:11.5px;
    color:var(--text-dim);
  }

  h2.section-title{
    font-family:var(--font-mono);
    font-size:13px;
    color:var(--text-dim);
    font-weight:500;
    margin:0 0 4px;
  }
</style>
</head>
<body>

<nav class="tab-bar" aria-label="Sections">
  <div class="window-dots"><span></span><span></span><span></span></div>
  <div class="tabs" id="tabs">
    <button class="tab active" data-target="hero"><i class="fa-solid fa-bolt"></i>ShahidSattar.js</button>
    <button class="tab" data-target="about"><i class="fa-regular fa-file-code"></i>about.js</button>
    <button class="tab" data-target="experience"><i class="fa-solid fa-code-branch"></i>experience.log</button>
    <button class="tab" data-target="projects"><i class="fa-regular fa-folder-open"></i>projects.js</button>
    <button class="tab" data-target="skills"><i class="fa-regular fa-file-code"></i>skills.json</button>
    <button class="tab" data-target="education"><i class="fa-regular fa-file-code"></i>education.yaml</button>
    <button class="tab" data-target="contact"><i class="fa-regular fa-file-lines"></i>contact.md</button>
  </div>
</nav>

<main>

  <!-- HERO -->
  <section id="hero" class="hero">
    <div class="wrap">
      <div class="file-label">ShahidSattar.js</div>
      <div class="panel">
        <div class="eyebrow">// student.developer</div>
        <div class="code-block">
          <div class="line"><span class="kw">class</span> <span class="cls">ShahidSattar</span> <span class="kw">extends</span> <span class="cls">Developer</span> <span class="punct">{</span></div>
          <div class="line indent-1"><span class="kw">constructor</span><span class="punct">()</span> <span class="punct">{</span></div>
          <div class="line indent-2"><span class="kw">super</span><span class="punct">();</span></div>
          <div class="line indent-2"><span class="prop">this</span><span class="punct">.</span><span class="prop">role</span> <span class="punct">=</span> <span class="str">"Software Engineering Student"</span><span class="punct">;</span></div>
          <div class="line indent-2"><span class="prop">this</span><span class="punct">.</span><span class="prop">school</span> <span class="punct">=</span> <span class="str">"QUEST, Nawabshah"</span><span class="punct">;</span></div>
          <div class="line indent-2"><span class="prop">this</span><span class="punct">.</span><span class="prop">location</span> <span class="punct">=</span> <span class="str">"Pano Aqil, Sindh, Pakistan"</span><span class="punct">;</span></div>
          <div class="line indent-2"><span class="prop">this</span><span class="punct">.</span><span class="prop">status</span> <span class="punct">=</span> <span class="str">"Open to internship opportunities"</span><span class="punct">;</span><span class="hero-cursor" aria-hidden="true"></span></div>
          <div class="line indent-1"><span class="punct">}</span></div>
          <div class="line"><span class="punct">}</span></div>
          <div class="line blank"></div>
          <div class="line"><span class="kw">const</span> shahid <span class="punct">=</span> <span class="kw">new</span> <span class="cls">ShahidSattar</span><span class="punct">();</span></div>
        </div>
        <div class="hero-cta">
          <a href="#projects" class="btn btn-primary" data-tab-link="projects"><i class="fa-solid fa-arrow-right"></i> View Projects</a>
          <a href="#contact" class="btn btn-ghost" data-tab-link="contact"><i class="fa-regular fa-paper-plane"></i> Say Hello</a>
        </div>
      </div>
    </div>
  </section>

  <!-- ABOUT -->
  <section id="about" class="section">
    <div class="wrap reveal">
      <div class="file-label">about.js</div>
      <div class="panel">
        <div class="code-block">
          <div class="line com">/**</div>
          <div class="line com"> * Software Engineering student building a foundation across HTML5,</div>
          <div class="line com"> * CSS3, JavaScript, Java, C, Python, C++ and MySQL — through real,</div>
          <div class="line com"> * self-directed projects rather than just coursework.</div>
          <div class="line blank"></div>
          <div class="line com"> * Comfortable turning a blank page into a working interface, and</div>
          <div class="line com"> * a database schema into a system that actually behaves end to end.</div>
          <div class="line blank"></div>
          <div class="line com"> * Currently completing a Bachelor of Software Engineering at QUEST,</div>
          <div class="line com"> * Nawabshah, and looking for an internship to put these fundamentals</div>
          <div class="line com"> * to work on a real team.</div>
          <div class="line com"> */</div>
        </div>
      </div>
    </div>
  </section>

  <!-- EXPERIENCE -->
  <section id="experience" class="section">
    <div class="wrap reveal">
      <div class="file-label">experience.log</div>
      <p style="font-size:13.5px; color:var(--text-secondary); margin:0 0 16px;">No employer yet — but a real commit history of self-taught project work.</p>
      <div class="panel">
        <div class="code-block">
          <div class="line dim"><span class="punct">$</span> git log --oneline --decorate</div>
          <div class="line blank"></div>
          <div class="line"><span class="hash">f7a21c3</span> <span class="git-head">(HEAD -&gt; main)</span> <span class="git-msg">Built a to-do list app — add, delete &amp; complete tasks via JS DOM</span></div>
          <div class="line"><span class="hash">9d18e4a</span> <span class="git-msg">Built an Amazon-inspired e-commerce frontend — listings, cart, responsive layout</span></div>
          <div class="line"><span class="hash">6b3f0a1</span> <span class="git-msg">Designed a multi-section personal portfolio page</span></div>
          <div class="line"><span class="hash">4e7c2d9</span> <span class="git-msg">Wrote a Java &amp; C banking system — accounts, deposits, withdrawals, balance checks</span></div>
          <div class="line"><span class="hash">2a9f1b0</span> <span class="git-msg">Connected front-end forms to back-end DB logic for a department database system</span></div>
          <div class="line"><span class="hash">1c4d8e2</span> <span class="git-msg">Created login forms, feedback forms &amp; structured content pages</span></div>
          <div class="line"><span class="hash">0a1b2c3</span> <span class="git-msg">Started learning HTML, CSS &amp; JavaScript from scratch</span></div>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects" class="section">
    <div class="wrap reveal">
      <div class="file-label">projects.js</div>
      <div class="project-grid">

        <div class="project-card">
          <div class="code-block">
            <div class="line"><span class="kw">function</span> <span class="prop">ecommercePlatform</span><span class="punct">()</span> <span class="punct">{</span></div>
            <div class="line indent-1"><span class="kw">const</span> stack <span class="punct">=</span> <span class="punct">[</span><span class="str">'HTML5'</span><span class="punct">,</span> <span class="str">'CSS3'</span><span class="punct">,</span> <span class="str">'JS'</span><span class="punct">];</span></div>
            <div class="line indent-1"><span class="kw">return</span> <span class="punct">{</span> cart<span class="punct">,</span> listings<span class="punct">,</span> responsive<span class="punct">:</span> <span class="num">true</span> <span class="punct">};</span></div>
            <div class="line"><span class="punct">}</span></div>
          </div>
          <div class="project-desc">Amazon-inspired storefront concept — product listings, cart functionality and a fully responsive layout.</div>
        </div>

        <div class="project-card">
          <div class="code-block">
            <div class="line"><span class="kw">function</span> <span class="prop">departmentDB</span><span class="punct">()</span> <span class="punct">{</span></div>
            <div class="line indent-1"><span class="kw">const</span> stack <span class="punct">=</span> <span class="punct">[</span><span class="str">'HTML'</span><span class="punct">,</span> <span class="str">'MySQL'</span><span class="punct">];</span></div>
            <div class="line indent-1"><span class="kw">return</span> <span class="punct">{</span> frontend<span class="punct">,</span> crud<span class="punct">,</span> wired<span class="punct">:</span> <span class="num">true</span> <span class="punct">};</span></div>
            <div class="line"><span class="punct">}</span></div>
          </div>
          <div cla

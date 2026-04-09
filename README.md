<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Mohapi Mohoto — Junior Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:ital,wght@0,400;0,500;1,400&family=Instrument+Sans:ital,wght@0,400;0,500;1,400&display=swap" rel="stylesheet"/>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0A0A0F;
    --bg2: #111118;
    --bg3: #18181F;
    --accent: #4AE3A0;
    --accent2: #3B8BFF;
    --text: #F0EEE8;
    --muted: #888794;
    --border: rgba(255,255,255,0.08);
    --card: #141419;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Instrument Sans', sans-serif;
    font-size: 16px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* ── NOISE OVERLAY ── */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 0;
    opacity: 0.4;
  }

  /* ── NAV ── */
  nav {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    padding: 1.2rem 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: rgba(10,10,15,0.85);
    backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--border);
  }

  .nav-logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 1.1rem;
    color: var(--accent);
    text-decoration: none;
    letter-spacing: -0.02em;
  }

  .nav-links { display: flex; gap: 2rem; list-style: none; }
  .nav-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.875rem;
    font-weight: 500;
    transition: color 0.2s;
    letter-spacing: 0.02em;
  }
  .nav-links a:hover { color: var(--text); }

  /* ── HERO ── */
  #hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 8rem 2rem 4rem;
    position: relative;
    max-width: 1100px;
    margin: 0 auto;
  }

  .hero-eyebrow {
    font-family: 'DM Mono', monospace;
    font-size: 0.8rem;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 1.5rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }
  .hero-eyebrow::before {
    content: '';
    display: block;
    width: 32px;
    height: 1px;
    background: var(--accent);
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(3.5rem, 8vw, 7rem);
    line-height: 0.95;
    letter-spacing: -0.04em;
    margin-bottom: 1.5rem;
  }

  .hero-name .line2 {
    color: transparent;
    -webkit-text-stroke: 1.5px rgba(240,238,232,0.35);
  }

  .hero-desc {
    font-size: 1.1rem;
    color: var(--muted);
    max-width: 520px;
    line-height: 1.75;
    margin-bottom: 2.5rem;
  }

  .hero-desc strong { color: var(--text); font-weight: 500; }

  .hero-cta {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.75rem 1.5rem;
    border-radius: 4px;
    font-size: 0.875rem;
    font-weight: 500;
    text-decoration: none;
    transition: all 0.2s;
    cursor: pointer;
    border: none;
    font-family: 'Instrument Sans', sans-serif;
  }

  .btn-primary {
    background: var(--accent);
    color: #0A0A0F;
  }
  .btn-primary:hover { background: #5CF5B0; transform: translateY(-1px); }

  .btn-outline {
    background: transparent;
    color: var(--text);
    border: 1px solid var(--border);
  }
  .btn-outline:hover { border-color: rgba(255,255,255,0.25); background: var(--bg3); }

  /* Glow blob */
  .glow-blob {
    position: absolute;
    width: 600px;
    height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(74,227,160,0.07) 0%, transparent 70%);
    top: 10%;
    right: -10%;
    pointer-events: none;
  }

  /* ── SECTION COMMON ── */
  section {
    max-width: 1100px;
    margin: 0 auto;
    padding: 6rem 2rem;
  }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    letter-spacing: 0.15em;
    text-transform: uppercase;
    margin-bottom: 0.75rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
  }
  .section-label::before {
    content: '';
    display: block;
    width: 24px;
    height: 1px;
    background: var(--accent);
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: clamp(2rem, 4vw, 3rem);
    letter-spacing: -0.03em;
    line-height: 1.1;
    margin-bottom: 3rem;
  }

  /* ── ABOUT ── */
  #about {
    border-top: 1px solid var(--border);
  }

  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: start;
  }

  .about-text p {
    color: var(--muted);
    margin-bottom: 1rem;
  }
  .about-text p strong { color: var(--text); }

  .about-stats {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: var(--border);
    border: 1px solid var(--border);
    border-radius: 8px;
    overflow: hidden;
  }

  .stat-box {
    background: var(--card);
    padding: 1.75rem;
  }

  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 2.5rem;
    font-weight: 800;
    color: var(--accent);
    line-height: 1;
    margin-bottom: 0.35rem;
  }

  .stat-label {
    font-size: 0.8rem;
    color: var(--muted);
    letter-spacing: 0.03em;
  }

  /* ── SKILLS ── */
  #skills { border-top: 1px solid var(--border); }

  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1rem;
  }

  .skill-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 1.5rem;
    transition: border-color 0.2s, transform 0.2s;
  }
  .skill-card:hover {
    border-color: rgba(74,227,160,0.3);
    transform: translateY(-2px);
  }

  .skill-icon {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--accent);
    letter-spacing: 0.1em;
    margin-bottom: 0.75rem;
    text-transform: uppercase;
  }

  .skill-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 1rem;
    margin-bottom: 0.75rem;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
  }

  .tag {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    padding: 0.2rem 0.5rem;
    background: rgba(74,227,160,0.08);
    color: var(--accent);
    border-radius: 3px;
    border: 1px solid rgba(74,227,160,0.15);
  }

  /* ── PROJECTS ── */
  #projects { border-top: 1px solid var(--border); }

  .projects-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }

  .project-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 2rem;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    transition: border-color 0.25s, transform 0.25s;
    position: relative;
    overflow: hidden;
  }

  .project-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--accent), var(--accent2));
    opacity: 0;
    transition: opacity 0.25s;
  }

  .project-card:hover {
    border-color: rgba(74,227,160,0.25);
    transform: translateY(-3px);
  }
  .project-card:hover::before { opacity: 1; }

  .project-number {
    font-family: 'DM Mono', monospace;
    font-size: 0.7rem;
    color: var(--muted);
    letter-spacing: 0.1em;
  }

  .project-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 1.3rem;
    letter-spacing: -0.02em;
    line-height: 1.2;
  }

  .project-desc {
    color: var(--muted);
    font-size: 0.9rem;
    line-height: 1.65;
    flex: 1;
  }

  .project-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 0.4rem;
  }

  .project-links {
    display: flex;
    gap: 0.75rem;
    padding-top: 0.5rem;
    border-top: 1px solid var(--border);
  }

  .project-link {
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--muted);
    text-decoration: none;
    display: flex;
    align-items: center;
    gap: 0.3rem;
    transition: color 0.2s;
    letter-spacing: 0.05em;
  }
  .project-link:hover { color: var(--accent); }

  /* ── EXPERIENCE ── */
  #experience { border-top: 1px solid var(--border); }

  .timeline {
    position: relative;
    padding-left: 2rem;
  }

  .timeline::before {
    content: '';
    position: absolute;
    left: 0;
    top: 8px;
    bottom: 0;
    width: 1px;
    background: var(--border);
  }

  .timeline-item {
    position: relative;
    padding-bottom: 3rem;
  }

  .timeline-item::before {
    content: '';
    position: absolute;
    left: -2rem;
    top: 8px;
    width: 7px;
    height: 7px;
    border-radius: 50%;
    background: var(--accent);
    margin-left: -3px;
  }

  .timeline-date {
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--accent);
    letter-spacing: 0.08em;
    margin-bottom: 0.5rem;
  }

  .timeline-role {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 1.1rem;
    letter-spacing: -0.01em;
    margin-bottom: 0.2rem;
  }

  .timeline-company {
    font-size: 0.875rem;
    color: var(--muted);
    margin-bottom: 1rem;
  }

  .timeline-bullets {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .timeline-bullets li {
    font-size: 0.9rem;
    color: var(--muted);
    padding-left: 1rem;
    position: relative;
    line-height: 1.6;
  }

  .timeline-bullets li::before {
    content: '→';
    position: absolute;
    left: 0;
    color: var(--accent);
    font-size: 0.75rem;
    top: 0.15rem;
  }

  /* ── CONTACT ── */
  #contact {
    border-top: 1px solid var(--border);
    text-align: center;
  }

  .contact-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 4rem 2rem;
    max-width: 600px;
    margin: 0 auto;
  }

  .contact-card h2 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(2rem, 4vw, 3rem);
    letter-spacing: -0.03em;
    margin-bottom: 1rem;
  }

  .contact-card p {
    color: var(--muted);
    margin-bottom: 2rem;
    max-width: 400px;
    margin-left: auto;
    margin-right: auto;
  }

  .contact-links {
    display: flex;
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
    margin-top: 2rem;
  }

  .contact-link {
    font-family: 'DM Mono', monospace;
    font-size: 0.8rem;
    color: var(--muted);
    text-decoration: none;
    letter-spacing: 0.05em;
    transition: color 0.2s;
    display: flex;
    align-items: center;
    gap: 0.4rem;
  }
  .contact-link:hover { color: var(--accent); }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 2rem;
    text-align: center;
    font-family: 'DM Mono', monospace;
    font-size: 0.75rem;
    color: var(--muted);
    letter-spacing: 0.05em;
    max-width: 1100px;
    margin: 0 auto;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .fade-up { animation: fadeUp 0.7s ease both; }
  .delay-1 { animation-delay: 0.1s; }
  .delay-2 { animation-delay: 0.2s; }
  .delay-3 { animation-delay: 0.35s; }
  .delay-4 { animation-delay: 0.5s; }

  /* ── STATUS BADGE ── */
  .status-badge {
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
    background: rgba(74,227,160,0.1);
    border: 1px solid rgba(74,227,160,0.2);
    border-radius: 100px;
    padding: 0.3rem 0.9rem;
    font-family: 'DM Mono', monospace;
    font-size: 0.72rem;
    color: var(--accent);
    letter-spacing: 0.05em;
    margin-bottom: 2rem;
  }

  .status-dot {
    width: 6px;
    height: 6px;
    border-radius: 50%;
    background: var(--accent);
    animation: pulse 2s ease infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 768px) {
    nav { padding: 1rem; }
    .nav-links { display: none; }
    .about-grid { grid-template-columns: 1fr; gap: 2rem; }
    .projects-grid { grid-template-columns: 1fr; }
    .hero-cta { flex-direction: column; }
    .btn { justify-content: center; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#hero" class="nav-logo">MM/</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#experience">Experience</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <a href="mailto:mohotomohapi@gmail.com" class="btn btn-primary" style="padding: 0.5rem 1.1rem; font-size: 0.8rem;">Hire Me</a>
</nav>

<!-- HERO -->
<div id="hero">
  <div class="glow-blob"></div>

  <div class="status-badge fade-up">
    <span class="status-dot"></span>
    Available for work — Johannesburg, SA
  </div>

  <div class="hero-eyebrow fade-up delay-1">Junior Software Developer</div>

  <h1 class="hero-name fade-up delay-2">
    Mohapi<br>
    <span class="line2">Mohoto</span>
  </h1>

  <p class="hero-desc fade-up delay-3">
    I build <strong>full-stack web & mobile applications</strong> that solve real problems.
    Backed by enterprise IT experience at Sun International —
    I write code that works in the real world, not just on localhost.
  </p>

  <div class="hero-cta fade-up delay-4">
    <a href="#projects" class="btn btn-primary">View My Work ↓</a>
    <a href="mailto:mohotomohapi@gmail.com" class="btn btn-outline">Get In Touch</a>
    <a href="https://github.com/mohapimohoto" target="_blank" class="btn btn-outline">GitHub →</a>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="section-label">About</div>
  <div class="about-grid">
    <div class="about-text">
      <h2 class="section-title" style="margin-bottom: 1.5rem;">Building things<br>that matter.</h2>
      <p>I'm a Junior Developer based in Johannesburg with a <strong>National Diploma in Information Technology (NQF Level 6)</strong> and real-world experience spanning both software development and enterprise IT infrastructure.</p>
      <p>What sets me apart? I've actually worked inside large-scale IT environments at <strong>Sun International</strong> — managing Windows Servers, Active Directory, and network infrastructure for a hotel and casino. Most junior devs have never seen a production system up close. I have.</p>
      <p>I build apps that solve real problems: a <strong>sobriety tracker</strong> to help people in recovery, and a <strong>community marketplace</strong> to make education more affordable. Code with purpose.</p>
      <div style="margin-top: 1.5rem;">
        <a href="https://www.linkedin.com/in/mohapimohoto" target="_blank" class="btn btn-outline" style="display: inline-flex;">LinkedIn Profile →</a>
      </div>
    </div>

    <div>
      <div class="about-stats">
        <div class="stat-box">
          <div class="stat-num">1+</div>
          <div class="stat-label">Year enterprise IT experience</div>
        </div>
        <div class="stat-box">
          <div class="stat-num">5+</div>
          <div class="stat-label">Technologies mastered</div>
        </div>
        <div class="stat-box">
          <div class="stat-num">2</div>
          <div class="stat-label">Real-world apps shipped</div>
        </div>
        <div class="stat-box">
          <div class="stat-num">NQF6</div>
          <div class="stat-label">IT Diploma qualification</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills">
  <div class="section-label">Skills</div>
  <h2 class="section-title">What I work with</h2>
  <div class="skills-grid">
    <div class="skill-card">
      <div class="skill-icon">// 01</div>
      <div class="skill-name">Frontend</div>
      <div class="skill-tags">
        <span class="tag">React.js</span>
        <span class="tag">Vue.js</span>
        <span class="tag">JavaScript</span>
        <span class="tag">HTML5</span>
        <span class="tag">CSS3</span>
        <span class="tag">React Native</span>
      </div>
    </div>
    <div class="skill-card">
      <div class="skill-icon">// 02</div>
      <div class="skill-name">Backend</div>
      <div class="skill-tags">
        <span class="tag">Node.js</span>
        <span class="tag">Express.js</span>
        <span class="tag">Java</span>
        <span class="tag">Spring Boot</span>
        <span class="tag">Python</span>
        <span class="tag">Django</span>
      </div>
    </div>
    <div class="skill-card">
      <div class="skill-icon">// 03</div>
      <div class="skill-name">Database & APIs</div>
      <div class="skill-tags">
        <span class="tag">MySQL</span>
        <span class="tag">PostgreSQL</span>
        <span class="tag">SQLite</span>
        <span class="tag">REST APIs</span>
        <span class="tag">Postman</span>
      </div>
    </div>
    <div class="skill-card">
      <div class="skill-icon">// 04</div>
      <div class="skill-name">DevOps & Tools</div>
      <div class="skill-tags">
        <span class="tag">Git</span>
        <span class="tag">GitHub</span>
        <span class="tag">VS Code</span>
        <span class="tag">npm</span>
        <span class="tag">Linux</span>
      </div>
    </div>
    <div class="skill-card">
      <div class="skill-icon">// 05</div>
      <div class="skill-name">IT Infrastructure</div>
      <div class="skill-tags">
        <span class="tag">Windows Server</span>
        <span class="tag">Active Directory</span>
        <span class="tag">Microsoft 365</span>
        <span class="tag">Networking</span>
        <span class="tag">ITIL</span>
      </div>
    </div>
    <div class="skill-card">
      <div class="skill-icon">// 06</div>
      <div class="skill-name">Currently Learning</div>
      <div class="skill-tags">
        <span class="tag">TypeScript</span>
        <span class="tag">Docker</span>
        <span class="tag">AWS</span>
        <span class="tag">CI/CD</span>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-label">Projects</div>
  <h2 class="section-title">Things I've built</h2>
  <div class="projects-grid">

    <div class="project-card">
      <div class="project-number">Project 01 — Mobile App</div>
      <div class="project-title">Conquer Daily</div>
      <div class="project-desc">
        A sobriety and habit tracker mobile app designed to help users reclaim their lives one day at a time. Features streak tracking, daily journaling, milestone celebrations, and push notification reminders. Built because the people who need this app the most deserve something that feels human.
      </div>
      <div class="project-stack">
        <span class="tag">React Native</span>
        <span class="tag">Node.js</span>
        <span class="tag">Express</span>
        <span class="tag">SQLite</span>
        <span class="tag">Expo</span>
      </div>
      <div class="project-links">
        <a href="https://github.com/mohapimohoto/conquer-daily" target="_blank" class="project-link">⌥ GitHub Repo →</a>
      </div>
    </div>

    <div class="project-card">
      <div class="project-number">Project 02 — Full Stack Web</div>
      <div class="project-title">Community Marketplace</div>
      <div class="project-desc">
        A full-stack e-commerce platform enabling students to buy and sell second-hand textbooks and school uniforms within their local community. Includes authentication, product listings, shopping cart, and order management. Reducing the cost of education, one listing at a time.
      </div>
      <div class="project-stack">
        <span class="tag">React.js</span>
        <span class="tag">Node.js</span>
        <span class="tag">Express</span>
        <span class="tag">MySQL</span>
        <span class="tag">JWT</span>
      </div>
      <div class="project-links">
        <a href="https://github.com/mohapimohoto/community-marketplace" target="_blank" class="project-link">⌥ GitHub Repo →</a>
      </div>
    </div>

  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-label">Experience</div>
  <h2 class="section-title">Where I've worked</h2>
  <div class="timeline">

    <div class="timeline-item">
      <div class="timeline-date">Nov 2024 – Oct 2025 · 1 Year</div>
      <div class="timeline-role">System Administrator (Intern)</div>
      <div class="timeline-company">Sun International — Carousel Casino & Hotel · Kempton Park, GP</div>
      <ul class="timeline-bullets">
        <li>Administered Windows Server & Active Directory for hotel and casino operations across multiple departments</li>
        <li>Monitored system performance, executed patch management and backups to maintain 99%+ uptime</li>
        <li>Supported and optimised network infrastructure including routers, switches, and wireless access points</li>
        <li>Served as escalation point for complex support issues — produced knowledge base documentation</li>
      </ul>
    </div>

    <div class="timeline-item">
      <div class="timeline-date">Feb 2025 – Oct 2025 · 9 Months</div>
      <div class="timeline-role">IT Support Technician (Intern)</div>
      <div class="timeline-company">Sun International — Carousel Casino & Hotel · Johannesburg, GP</div>
      <ul class="timeline-bullets">
        <li>Delivered first-line IT support for 200+ hotel and casino staff across hardware, software, and network domains</li>
        <li>Installed and configured desktops, laptops, printers, and peripherals for new employees</li>
        <li>Managed Microsoft 365 environments — Outlook, Teams, SharePoint, and OneDrive</li>
        <li>Logged incidents in ticketing system and maintained accurate SLA compliance records</li>
      </ul>
    </div>

  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="contact-card">
    <h2>Let's build something.</h2>
    <p>I'm actively looking for junior developer opportunities in Johannesburg and open to remote roles. If you're hiring or want to chat, reach out.</p>
    <a href="mailto:mohotomohapi@gmail.com" class="btn btn-primary" style="margin: 0 auto;">mohotomohapi@gmail.com</a>
    <div class="contact-links">
      <a href="https://www.linkedin.com/in/mohapimohoto" target="_blank" class="contact-link">↗ LinkedIn</a>
      <a href="https://github.com/mohapimohoto" target="_blank" class="contact-link">↗ GitHub</a>
      <a href="tel:0644010876" class="contact-link">↗ 064 401 0876</a>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p>Mohapi Mohoto · Built with intent · Johannesburg, SA · 2025</p>
</footer>

<script>
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.style.opacity = '1';
        e.target.style.transform = 'translateY(0)';
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.skill-card, .project-card, .timeline-item, .stat-box').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(20px)';
    el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
    observer.observe(el);
  });
</script>
</body>
</html>

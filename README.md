<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Abdul Rehman | Software Engineer</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #0a0a0f;
      --surface: #111118;
      --surface2: #16161f;
      --border: #1e1e2e;
      --accent: #7c6aff;
      --accent2: #00e5b0;
      --accent3: #ff6b6b;
      --text: #e8e8f0;
      --muted: #7070a0;
      --card: #13131c;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'DM Mono', monospace;
      font-size: 14px;
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* Noise overlay */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 999;
      opacity: 0.35;
    }

    /* Ambient glow */
    .glow-orb {
      position: fixed;
      border-radius: 50%;
      filter: blur(120px);
      pointer-events: none;
      z-index: 0;
      opacity: 0.12;
    }
    .glow-orb-1 { width: 600px; height: 600px; background: var(--accent); top: -200px; left: -100px; animation: drift1 20s ease-in-out infinite; }
    .glow-orb-2 { width: 500px; height: 500px; background: var(--accent2); bottom: 10%; right: -100px; animation: drift2 25s ease-in-out infinite; }

    @keyframes drift1 { 0%,100%{transform:translate(0,0)} 50%{transform:translate(60px,40px)} }
    @keyframes drift2 { 0%,100%{transform:translate(0,0)} 50%{transform:translate(-40px,60px)} }

    /* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 100;
      padding: 20px 40px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid rgba(255,255,255,0.04);
      background: rgba(10,10,15,0.85);
      backdrop-filter: blur(20px);
    }

    .nav-logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 17px;
      letter-spacing: -0.3px;
      color: var(--text);
      text-decoration: none;
    }

    .nav-logo span { color: var(--accent); }

    .nav-links {
      display: flex;
      gap: 32px;
      list-style: none;
    }

    .nav-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 12px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      transition: color 0.2s;
    }

    .nav-links a:hover { color: var(--text); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      padding: 120px 40px 80px;
      position: relative;
      z-index: 1;
      max-width: 1100px;
      margin: 0 auto;
    }

    .hero-content { max-width: 750px; }

    .hero-tag {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-size: 11px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent2);
      margin-bottom: 28px;
      padding: 6px 14px;
      border: 1px solid rgba(0,229,176,0.2);
      border-radius: 2px;
    }

    .hero-tag::before {
      content: '';
      width: 6px; height: 6px;
      background: var(--accent2);
      border-radius: 50%;
      animation: pulse 2s ease-in-out infinite;
    }

    @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }

    .hero h1 {
      font-family: 'Syne', sans-serif;
      font-size: clamp(52px, 8vw, 96px);
      font-weight: 800;
      line-height: 0.92;
      letter-spacing: -3px;
      color: var(--text);
      margin-bottom: 24px;
    }

    .hero h1 .accent { color: var(--accent); }

    .hero-sub {
      font-size: 15px;
      color: var(--muted);
      max-width: 500px;
      margin-bottom: 48px;
      line-height: 1.8;
    }

    .hero-cta {
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 12px 24px;
      font-family: 'DM Mono', monospace;
      font-size: 12px;
      letter-spacing: 0.06em;
      text-decoration: none;
      border-radius: 2px;
      transition: all 0.2s;
      cursor: pointer;
    }

    .btn-primary {
      background: var(--accent);
      color: #fff;
      border: 1px solid var(--accent);
    }
    .btn-primary:hover { background: #6a58ee; }

    .btn-outline {
      background: transparent;
      color: var(--text);
      border: 1px solid var(--border);
    }
    .btn-outline:hover { border-color: var(--muted); }

    /* SECTIONS */
    section {
      position: relative;
      z-index: 1;
      padding: 100px 40px;
    }

    .container { max-width: 1100px; margin: 0 auto; }

    .section-label {
      font-size: 11px;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .section-label::after {
      content: '';
      height: 1px;
      width: 40px;
      background: var(--accent);
      opacity: 0.4;
    }

    .section-title {
      font-family: 'Syne', sans-serif;
      font-size: clamp(32px, 5vw, 52px);
      font-weight: 800;
      letter-spacing: -1.5px;
      line-height: 1.05;
      margin-bottom: 60px;
      color: var(--text);
    }

    /* ABOUT */
    #about { background: var(--surface); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }

    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: start;
    }

    .about-text p {
      color: var(--muted);
      margin-bottom: 18px;
      font-size: 14px;
      line-height: 1.9;
    }

    .about-text p strong { color: var(--text); font-weight: 500; }

    .about-stats {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }

    .stat-card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 24px;
      border-radius: 4px;
    }

    .stat-number {
      font-family: 'Syne', sans-serif;
      font-size: 36px;
      font-weight: 800;
      color: var(--accent);
      letter-spacing: -1px;
      line-height: 1;
      margin-bottom: 6px;
    }

    .stat-label {
      font-size: 11px;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.08em;
    }

    /* EXPERIENCE */
    #experience { background: var(--bg); }

    .timeline { position: relative; }

    .timeline::before {
      content: '';
      position: absolute;
      left: 0; top: 8px; bottom: 0;
      width: 1px;
      background: linear-gradient(to bottom, var(--accent), transparent);
      opacity: 0.3;
    }

    .timeline-item {
      padding-left: 36px;
      padding-bottom: 56px;
      position: relative;
    }

    .timeline-item:last-child { padding-bottom: 0; }

    .timeline-dot {
      position: absolute;
      left: -4px; top: 8px;
      width: 9px; height: 9px;
      background: var(--accent);
      border-radius: 50%;
      border: 2px solid var(--bg);
    }

    .timeline-item.current .timeline-dot {
      background: var(--accent2);
      box-shadow: 0 0 12px var(--accent2);
    }

    .timeline-meta {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 8px;
      flex-wrap: wrap;
    }

    .timeline-company {
      font-family: 'Syne', sans-serif;
      font-size: 20px;
      font-weight: 700;
      color: var(--text);
      letter-spacing: -0.5px;
    }

    .timeline-badge {
      font-size: 10px;
      padding: 3px 8px;
      border-radius: 2px;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .badge-current { background: rgba(0,229,176,0.12); color: var(--accent2); border: 1px solid rgba(0,229,176,0.25); }
    .badge-prev { background: rgba(124,106,255,0.1); color: var(--accent); border: 1px solid rgba(124,106,255,0.2); }

    .timeline-role {
      font-size: 13px;
      color: var(--muted);
      margin-bottom: 4px;
    }

    .timeline-date {
      font-size: 11px;
      color: var(--muted);
      opacity: 0.6;
      margin-bottom: 20px;
    }

    .timeline-bullets {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .timeline-bullets li {
      font-size: 13px;
      color: var(--muted);
      padding-left: 18px;
      position: relative;
      line-height: 1.7;
    }

    .timeline-bullets li::before {
      content: '→';
      position: absolute;
      left: 0;
      color: var(--accent);
      opacity: 0.6;
    }

    .timeline-bullets li strong { color: var(--text); font-weight: 500; }

    /* PROJECTS */
    #projects { background: var(--surface); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }

    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 20px;
    }

    .project-card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 28px;
      border-radius: 4px;
      transition: border-color 0.2s, transform 0.2s;
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
      transition: opacity 0.2s;
    }

    .project-card:hover { border-color: rgba(124,106,255,0.3); transform: translateY(-2px); }
    .project-card:hover::before { opacity: 1; }

    /* Featured card spans 2 columns */
    .project-card--featured {
      grid-column: span 2;
      display: grid;
      grid-template-columns: 1.2fr 1fr;
      gap: 0;
      padding: 0;
      overflow: hidden;
    }

    @media (max-width: 768px) {
      .project-card--featured {
        grid-column: span 1;
        grid-template-columns: 1fr;
      }
    }

    .project-preview {
      position: relative;
      overflow: hidden;
      background: #080810;
      min-height: 180px;
      display: flex;
      flex-direction: column;
    }

    .project-card--featured .project-preview {
      min-height: 240px;
    }

    .project-img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
    }

    .project-img-fallback {
      width: 100%;
      flex: 1;
      display: flex;
      align-items: center;
      padding: 12px;
    }

    .project-metrics {
      display: flex;
      gap: 16px;
      padding: 10px 16px;
      background: rgba(0,0,0,0.4);
      border-top: 1px solid var(--border);
    }

    .metric {
      font-size: 11px;
      color: var(--muted);
      letter-spacing: 0.04em;
    }

    .metric-val {
      color: var(--accent2);
      font-weight: 600;
      margin-right: 3px;
    }

    .project-body {
      padding: 24px;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    /* Non-featured cards get preview on top */
    .project-card:not(.project-card--featured) {
      padding: 0;
      display: flex;
      flex-direction: column;
    }

    .project-card:not(.project-card--featured) .project-body {
      padding: 20px;
    }

    .project-card:not(.project-card--featured) .project-preview {
      min-height: 150px;
      border-bottom: 1px solid var(--border);
    }

    .project-card:not(.project-card--featured) .project-preview svg {
      width: 100%;
      height: 100%;
    }

    .project-type {
      font-size: 10px;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 10px;
    }

    .project-name {
      font-family: 'Syne', sans-serif;
      font-size: 18px;
      font-weight: 700;
      color: var(--text);
      margin-bottom: 10px;
      letter-spacing: -0.3px;
    }

    .project-desc {
      font-size: 13px;
      color: var(--muted);
      margin-bottom: 18px;
      line-height: 1.7;
    }

    .project-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }

    .tag {
      font-size: 10px;
      padding: 3px 8px;
      background: rgba(255,255,255,0.04);
      border: 1px solid var(--border);
      border-radius: 2px;
      color: var(--muted);
      letter-spacing: 0.05em;
    }

    /* SKILLS */
    #skills { background: var(--bg); }

    .skills-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 20px;
    }

    .skill-group {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 24px;
      border-radius: 4px;
    }

    .skill-group-title {
      font-size: 11px;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--accent2);
      margin-bottom: 16px;
      padding-bottom: 10px;
      border-bottom: 1px solid var(--border);
    }

    .skill-list {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
    }

    .skill-pill {
      font-size: 11px;
      padding: 4px 10px;
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.07);
      border-radius: 2px;
      color: var(--muted);
      transition: all 0.15s;
    }

    .skill-pill:hover { color: var(--text); border-color: var(--accent); background: rgba(124,106,255,0.08); }

    /* CONTACT */
    #contact { background: var(--surface); border-top: 1px solid var(--border); }

    .contact-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: center;
    }

    .contact-headline {
      font-family: 'Syne', sans-serif;
      font-size: clamp(36px, 5vw, 60px);
      font-weight: 800;
      letter-spacing: -2px;
      line-height: 1.0;
      color: var(--text);
      margin-bottom: 20px;
    }

    .contact-headline span { color: var(--accent); }

    .contact-text { color: var(--muted); font-size: 14px; line-height: 1.8; margin-bottom: 32px; }

    .contact-links { display: flex; flex-direction: column; gap: 14px; }

    .contact-link {
      display: flex;
      align-items: center;
      gap: 14px;
      text-decoration: none;
      color: var(--muted);
      font-size: 13px;
      padding: 14px 18px;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 4px;
      transition: all 0.2s;
    }

    .contact-link:hover { color: var(--text); border-color: rgba(124,106,255,0.4); background: rgba(124,106,255,0.05); }

    .contact-link-icon {
      width: 32px; height: 32px;
      display: flex; align-items: center; justify-content: center;
      background: rgba(124,106,255,0.1);
      border-radius: 4px;
      font-size: 14px;
      flex-shrink: 0;
    }

    .contact-link-text { flex: 1; }
    .contact-link-label { font-size: 10px; text-transform: uppercase; letter-spacing: 0.08em; color: var(--accent); margin-bottom: 2px; }
    .contact-link-value { font-size: 13px; }

    /* FOOTER */
    footer {
      text-align: center;
      padding: 28px 40px;
      border-top: 1px solid var(--border);
      font-size: 11px;
      color: var(--muted);
      letter-spacing: 0.06em;
      position: relative;
      z-index: 1;
    }

    /* ANIMATIONS */
    .fade-in {
      opacity: 0;
      transform: translateY(24px);
      animation: fadeIn 0.7s ease forwards;
    }

    @keyframes fadeIn {
      to { opacity: 1; transform: translateY(0); }
    }

    .fade-in-1 { animation-delay: 0.1s; }
    .fade-in-2 { animation-delay: 0.25s; }
    .fade-in-3 { animation-delay: 0.4s; }
    .fade-in-4 { animation-delay: 0.55s; }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      nav { padding: 16px 20px; }
      .nav-links { display: none; }
      section { padding: 72px 20px; }
      .hero { padding: 100px 20px 60px; }
      .about-grid, .contact-grid { grid-template-columns: 1fr; gap: 40px; }
      .hero h1 { letter-spacing: -2px; }
    }
  </style>
</head>
<body>

  <div class="glow-orb glow-orb-1"></div>
  <div class="glow-orb glow-orb-2"></div>

  <!-- NAV -->
  <nav>
    <a href="#" class="nav-logo">AR<span>.</span></a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#skills">Skills</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <!-- HERO -->
  <div class="hero">
    <div class="hero-content">
      <div class="hero-tag fade-in fade-in-1">Currently @ Careem · Karachi, PK</div>
      <h1 class="fade-in fade-in-2">
        Abdul<br><span class="accent">Rehman</span>
      </h1>
      <p class="hero-sub fade-in fade-in-3">
        Software Engineer building scalable automation systems, AI-driven QA workflows, and cloud infrastructure. Turning quality engineering into a competitive advantage.
      </p>
      <div class="hero-cta fade-in fade-in-4">
        <a href="#experience" class="btn btn-primary">View Experience</a>
        <a href="#contact" class="btn btn-outline">Get in Touch</a>
      </div>
    </div>
  </div>

  <!-- ABOUT -->
  <section id="about">
    <div class="container">
      <div class="section-label">About</div>
      <h2 class="section-title">Engineering quality<br>at scale.</h2>
      <div class="about-grid">
        <div class="about-text">
          <p>
            I'm a <strong>Software Engineer</strong> specializing in automation, backend systems, and quality engineering. My work sits at the intersection of engineering rigor and AI-driven tooling — building systems that help teams ship faster without sacrificing reliability.
          </p>
          <p>
            At <strong>Careem</strong>, I work on large-scale QA infrastructure including AI-powered test generation, mobile automation agents, and a centralized QA portal that orchestrates end-to-end quality workflows across the SuperApp.
          </p>
          <p>
            I'm particularly interested in how <strong>AI and automation converge</strong> to eliminate manual bottlenecks in software delivery — from intelligent test generation to chaos engineering and observability.
          </p>
        </div>
        <div class="about-stats">
          <div class="stat-card">
            <div class="stat-number">2+</div>
            <div class="stat-label">Years experience</div>
          </div>
          <div class="stat-card">
            <div class="stat-number">10+</div>
            <div class="stat-label">Tools & frameworks</div>
          </div>
          <div class="stat-card">
            <div class="stat-number">AI</div>
            <div class="stat-label">Driven workflows</div>
          </div>
          <div class="stat-card">
            <div class="stat-number">☁️</div>
            <div class="stat-label">AWS & DevOps</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- EXPERIENCE -->
  <section id="experience">
    <div class="container">
      <div class="section-label">Experience</div>
      <h2 class="section-title">Where I've<br>worked.</h2>
      <div class="timeline">

        <div class="timeline-item current">
          <div class="timeline-dot"></div>
          <div class="timeline-meta">
            <span class="timeline-company">Careem</span>
            <span class="timeline-badge badge-current">Current</span>
          </div>
          <div class="timeline-role">Software Engineer — QA</div>
          <div class="timeline-date">Oct 2025 – Present</div>
          <ul class="timeline-bullets">
            <li>Worked on <strong>IKIGAI</strong>, a Go-based service that processes user-reported issues from the SuperApp (Instabug), enabling automated Slack notifications and Jira ticket creation.</li>
            <li>Contributed to a <strong>centralized QA Portal</strong> that orchestrates end-to-end quality workflows, hosting multiple AI-driven agents and integrations.</li>
            <li>Built AI agents for <strong>automated test plan generation and test case creation</strong>, improving coverage and reducing manual effort.</li>
            <li>Extended the portal with <strong>GenAI-powered PR feedback</strong>, enabling automated validation of acceptance criteria and test coverage during code reviews.</li>
            <li>Integrated QA workflows with <strong>Jira, AIO, and Figma</strong> using MCP-based orchestration.</li>
            <li>Performed <strong>load, chaos, and DDoS testing</strong> to validate system reliability under stress.</li>
            <li>Built an <strong>AI-based mobile automation agent</strong> that navigates the app, analyzes screenshots, and generates test reports — eliminating Appium dependency.</li>
            <li>Implemented mobile automation using <strong>Maestro and Sofy</strong> for cross-device reliability.</li>
          </ul>
        </div>

        <div class="timeline-item">
          <div class="timeline-dot"></div>
          <div class="timeline-meta">
            <span class="timeline-company">Co-Ventech</span>
            <span class="timeline-badge badge-prev">Prev</span>
          </div>
          <div class="timeline-role">Test Automation Engineer</div>
          <div class="timeline-date">Jun 2024 – Oct 2025</div>
          <ul class="timeline-bullets">
            <li>Built <strong>scalable automation frameworks</strong> using Selenium, Playwright, and WebdriverIO, reducing regression cycles.</li>
            <li>Developed <strong>API automation suites</strong> using Rest-Assured and Postman for backend validation.</li>
            <li>Provisioned <strong>AWS infrastructure using Terraform</strong> for consistent, repeatable deployments.</li>
            <li>Integrated <strong>CI/CD pipelines</strong> using Jenkins and GitHub Actions.</li>
            <li>Conducted <strong>performance testing</strong> using JMeter and BlazeMeter to identify system bottlenecks.</li>
          </ul>
        </div>

        <div class="timeline-item">
          <div class="timeline-dot"></div>
          <div class="timeline-meta">
            <span class="timeline-company">FAST-NUCES</span>
          </div>
          <div class="timeline-role">Student Lab Assistant — Data Structures</div>
          <div class="timeline-date">Aug 2023 – Dec 2023</div>
          <ul class="timeline-bullets">
            <li>Conducted lab sessions and helped junior students understand complex data structure concepts.</li>
            <li>Reviewed and debugged student coding assignments.</li>
          </ul>
        </div>

      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="container">
      <div class="section-label">Projects</div>
      <h2 class="section-title">Things I've<br>built.</h2>
      <div class="projects-grid">

        <!-- AI AGENT — featured card with real screenshot placeholder -->
        <div class="project-card project-card--featured">
          <div class="project-preview project-preview--ai">
            <!-- Replace src with your actual screenshot: images/ai-agent-report.png -->
            <img src="./images/ai-agent-report.png"
                 onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"
                 alt="AI Agent Test Report" class="project-img">
            <div class="project-img-fallback">
              <svg viewBox="0 0 400 180" xmlns="http://www.w3.org/2000/svg" width="100%">
                <rect width="400" height="180" fill="#0d0d18"/>
                <!-- mock step grid -->
                <g opacity="0.9">
                  <rect x="12" y="12" width="88" height="72" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
                  <rect x="108" y="12" width="88" height="72" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
                  <rect x="204" y="12" width="88" height="72" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
                  <rect x="300" y="12" width="88" height="72" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
                  <rect x="12" y="96" width="88" height="72" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
                  <rect x="108" y="96" width="88" height="72" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
                  <rect x="204" y="96" width="88" height="72" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
                  <rect x="300" y="96" width="88" height="72" rx="4" fill="#111827" stroke="#22c55e" stroke-width="1.5"/>
                </g>
                <!-- step labels -->
                <text x="22" y="26" font-size="7" fill="#7c6aff" font-family="monospace">Step 1</text>
                <text x="118" y="26" font-size="7" fill="#7c6aff" font-family="monospace">Step 2</text>
                <text x="214" y="26" font-size="7" fill="#7c6aff" font-family="monospace">Step 3</text>
                <text x="310" y="26" font-size="7" fill="#7c6aff" font-family="monospace">Step 4</text>
                <text x="22" y="110" font-size="7" fill="#7c6aff" font-family="monospace">Step 5</text>
                <text x="118" y="110" font-size="7" fill="#7c6aff" font-family="monospace">Step 6</text>
                <text x="214" y="110" font-size="7" fill="#7c6aff" font-family="monospace">Step 7</text>
                <text x="310" y="110" font-size="7" fill="#22c55e" font-family="monospace">PASS ✓</text>
                <!-- mock phone screens -->
                <rect x="22" y="30" width="68" height="48" rx="3" fill="#1e293b"/>
                <rect x="118" y="30" width="68" height="48" rx="3" fill="#1e293b"/>
                <rect x="214" y="30" width="68" height="48" rx="3" fill="#1e293b"/>
                <rect x="310" y="30" width="68" height="48" rx="3" fill="#1e293b"/>
                <rect x="22" y="114" width="68" height="48" rx="3" fill="#1e293b"/>
                <rect x="118" y="114" width="68" height="48" rx="3" fill="#1e293b"/>
                <rect x="214" y="114" width="68" height="48" rx="3" fill="#1e293b"/>
                <rect x="310" y="114" width="68" height="48" rx="3" fill="#0f2a1a"/>
                <!-- pass badge top left -->
                <rect x="12" y="4" width="38" height="14" rx="2" fill="#16a34a"/>
                <text x="16" y="14" font-size="7" fill="white" font-family="monospace" font-weight="bold">✓ PASS</text>
                <!-- title -->
                <text x="58" y="13" font-size="8" fill="#94a3b8" font-family="monospace">search_and_add · 11 steps · 98.1s</text>
              </svg>
            </div>
            <div class="project-metrics">
              <span class="metric"><span class="metric-val">87%</span> pass rate</span>
              <span class="metric"><span class="metric-val">8</span> flows</span>
              <span class="metric"><span class="metric-val">0</span> Appium</span>
            </div>
          </div>
          <div class="project-body">
            <div class="project-type">AI · Mobile Automation</div>
            <div class="project-name">AI Mobile Automation Agent</div>
            <div class="project-desc">Built an AI-driven mobile automation agent that navigates apps visually, analyzes screenshots at each step, and executes user flows — no Appium dependency. Achieved 87% pass rate across 8 smoke flows on first production run.</div>
            <div class="project-tags">
              <span class="tag">Python</span><span class="tag">Vision AI</span><span class="tag">Appium-free</span><span class="tag">Maestro</span><span class="tag">Claude</span>
            </div>
          </div>
        </div>

        <!-- QA ORCHESTRATION -->
        <div class="project-card">
          <div class="project-preview project-preview--orchestration">
            <svg viewBox="0 0 400 160" xmlns="http://www.w3.org/2000/svg" width="100%">
              <rect width="400" height="160" fill="#0d0d18"/>
              <!-- nodes -->
              <rect x="20" y="60" width="70" height="36" rx="4" fill="#1a1a2e" stroke="#7c6aff" stroke-width="1"/>
              <text x="55" y="83" font-size="9" fill="#a78bfa" font-family="monospace" text-anchor="middle">AI Agents</text>
              <rect x="115" y="60" width="70" height="36" rx="4" fill="#1a1a2e" stroke="#7c6aff" stroke-width="1"/>
              <text x="150" y="83" font-size="9" fill="#a78bfa" font-family="monospace" text-anchor="middle">QA Portal</text>
              <rect x="210" y="60" width="70" height="36" rx="4" fill="#1a1a2e" stroke="#00e5b0" stroke-width="1"/>
              <text x="245" y="83" font-size="9" fill="#00e5b0" font-family="monospace" text-anchor="middle">Jira / AIO</text>
              <rect x="305" y="60" width="70" height="36" rx="4" fill="#1a1a2e" stroke="#7c6aff" stroke-width="1"/>
              <text x="340" y="83" font-size="9" fill="#a78bfa" font-family="monospace" text-anchor="middle">Figma</text>
              <!-- arrows -->
              <line x1="90" y1="78" x2="115" y2="78" stroke="#7c6aff" stroke-width="1" marker-end="url(#arr)"/>
              <line x1="185" y1="78" x2="210" y2="78" stroke="#7c6aff" stroke-width="1" marker-end="url(#arr)"/>
              <line x1="280" y1="78" x2="305" y2="78" stroke="#7c6aff" stroke-width="1" marker-end="url(#arr)"/>
              <defs><marker id="arr" markerWidth="6" markerHeight="6" refX="3" refY="3" orient="auto"><path d="M0,0 L6,3 L0,6 Z" fill="#7c6aff"/></marker></defs>
              <!-- label -->
              <text x="200" y="140" font-size="9" fill="#475569" font-family="monospace" text-anchor="middle">MCP-based orchestration · PR feedback · test generation</text>
              <text x="200" y="24" font-size="10" fill="#64748b" font-family="monospace" text-anchor="middle">QA Orchestration Portal — End-to-End Workflow</text>
            </svg>
          </div>
          <div class="project-body">
            <div class="project-type">AI · QA Platform</div>
            <div class="project-name">QA Orchestration Portal</div>
            <div class="project-desc">Centralized QA system integrating AI agents, Jira, Figma, and test management via MCP orchestration. Automates test generation, PR validation, and acceptance criteria checks.</div>
            <div class="project-tags">
              <span class="tag">MCP</span><span class="tag">LangChain</span><span class="tag">Jira</span><span class="tag">AIO Tests</span><span class="tag">Figma</span>
            </div>
          </div>
        </div>

        <!-- AUTOMATION FRAMEWORK -->
        <div class="project-card">
          <div class="project-preview project-preview--framework">
            <svg viewBox="0 0 400 160" xmlns="http://www.w3.org/2000/svg" width="100%">
              <rect width="400" height="160" fill="#0d0d18"/>
              <!-- CI/CD pipeline visual -->
              <rect x="16" y="55" width="60" height="50" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
              <text x="46" y="76" font-size="8" fill="#94a3b8" font-family="monospace" text-anchor="middle">UI Tests</text>
              <text x="46" y="90" font-size="7" fill="#64748b" font-family="monospace" text-anchor="middle">Selenium</text>
              <text x="46" y="101" font-size="7" fill="#64748b" font-family="monospace" text-anchor="middle">Playwright</text>
              <rect x="96" y="55" width="60" height="50" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
              <text x="126" y="76" font-size="8" fill="#94a3b8" font-family="monospace" text-anchor="middle">API Tests</text>
              <text x="126" y="90" font-size="7" fill="#64748b" font-family="monospace" text-anchor="middle">Postman</text>
              <text x="126" y="101" font-size="7" fill="#64748b" font-family="monospace" text-anchor="middle">Rest-Assured</text>
              <rect x="176" y="55" width="60" height="50" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
              <text x="206" y="76" font-size="8" fill="#94a3b8" font-family="monospace" text-anchor="middle">Mobile</text>
              <text x="206" y="90" font-size="7" fill="#64748b" font-family="monospace" text-anchor="middle">Appium</text>
              <text x="206" y="101" font-size="7" fill="#64748b" font-family="monospace" text-anchor="middle">WebdriverIO</text>
              <rect x="256" y="55" width="60" height="50" rx="4" fill="#111827" stroke="#22c55e" stroke-width="1"/>
              <text x="286" y="76" font-size="8" fill="#22c55e" font-family="monospace" text-anchor="middle">CI/CD</text>
              <text x="286" y="90" font-size="7" fill="#4ade80" font-family="monospace" text-anchor="middle">GitHub</text>
              <text x="286" y="101" font-size="7" fill="#4ade80" font-family="monospace" text-anchor="middle">Actions ✓</text>
              <rect x="336" y="55" width="52" height="50" rx="4" fill="#111827" stroke="#1e293b" stroke-width="1"/>
              <text x="362" y="76" font-size="8" fill="#94a3b8" font-family="monospace" text-anchor="middle">Report</text>
              <text x="362" y="90" font-size="7" fill="#64748b" font-family="monospace" text-anchor="middle">Allure</text>
              <text x="362" y="101" font-size="7" fill="#22c55e" font-family="monospace" text-anchor="middle">100% ✓</text>
              <!-- connecting lines -->
              <line x1="76" y1="80" x2="96" y2="80" stroke="#334155" stroke-width="1"/>
              <line x1="156" y1="80" x2="176" y2="80" stroke="#334155" stroke-width="1"/>
              <line x1="236" y1="80" x2="256" y2="80" stroke="#334155" stroke-width="1"/>
              <line x1="316" y1="80" x2="336" y2="80" stroke="#22c55e" stroke-width="1"/>
              <text x="200" y="24" font-size="10" fill="#64748b" font-family="monospace" text-anchor="middle">Multi-layer Framework · UI + API + Mobile + CI/CD</text>
              <text x="200" y="140" font-size="9" fill="#475569" font-family="monospace" text-anchor="middle">Allure reporting · BrowserStack cross-browser · Jenkins</text>
            </svg>
          </div>
          <div class="project-body">
            <div class="project-type">Automation · Framework</div>
            <div class="project-name">Automation Framework Suite</div>
            <div class="project-desc">Multi-layer test automation framework covering UI (Selenium, Playwright), API (Postman, Rest-Assured), and Mobile (Appium, WebdriverIO). CI/CD integrated via GitHub Actions with Allure reporting dashboards.</div>
            <div class="project-tags">
              <span class="tag">Selenium</span><span class="tag">Playwright</span><span class="tag">WebdriverIO</span><span class="tag">Rest-Assured</span><span class="tag">GitHub Actions</span>
            </div>
          </div>
        </div>

        <!-- PERFORMANCE TESTING -->
        <div class="project-card">
          <div class="project-preview project-preview--perf">
            <svg viewBox="0 0 400 160" xmlns="http://www.w3.org/2000/svg" width="100%">
              <rect width="400" height="160" fill="#0d0d18"/>
              <!-- bar chart mimicking JMeter aggregate -->
              <text x="200" y="20" font-size="10" fill="#64748b" font-family="monospace" text-anchor="middle">Aggregate Response Times (ms) · 75 samples</text>
              <!-- axes -->
              <line x1="40" y1="130" x2="380" y2="130" stroke="#1e293b" stroke-width="1"/>
              <line x1="40" y1="30" x2="40" y2="130" stroke="#1e293b" stroke-width="1"/>
              <!-- Request01 bars -->
              <rect x="60" y="110" width="16" height="20" fill="#7c6aff" opacity="0.8"/>
              <rect x="78" y="112" width="16" height="18" fill="#a78bfa" opacity="0.7"/>
              <rect x="96" y="125" width="16" height="5" fill="#22c55e" opacity="0.9"/>
              <rect x="114" y="84" width="16" height="46" fill="#475569" opacity="0.5"/>
              <!-- Request02 bars -->
              <rect x="170" y="60" width="16" height="70" fill="#7c6aff" opacity="0.8"/>
              <rect x="188" y="62" width="16" height="68" fill="#a78bfa" opacity="0.7"/>
              <rect x="206" y="110" width="16" height="20" fill="#22c55e" opacity="0.9"/>
              <rect x="224" y="35" width="16" height="95" fill="#ef4444" opacity="0.6"/>
              <!-- Request03 bars -->
              <rect x="280" y="70" width="16" height="60" fill="#7c6aff" opacity="0.8"/>
              <rect x="298" y="72" width="16" height="58" fill="#a78bfa" opacity="0.7"/>
              <rect x="316" y="118" width="16" height="12" fill="#22c55e" opacity="0.9"/>
              <rect x="334" y="40" width="16" height="90" fill="#ef4444" opacity="0.6"/>
              <!-- labels -->
              <text x="100" y="145" font-size="8" fill="#64748b" font-family="monospace" text-anchor="middle">Request01</text>
              <text x="210" y="145" font-size="8" fill="#ef4444" font-family="monospace" text-anchor="middle">Request02 ⚠</text>
              <text x="320" y="145" font-size="8" fill="#ef4444" font-family="monospace" text-anchor="middle">Request03 ⚠</text>
              <!-- legend -->
              <rect x="42" y="32" width="8" height="6" fill="#7c6aff"/>
              <text x="52" y="38" font-size="7" fill="#94a3b8" font-family="monospace">Avg</text>
              <rect x="75" y="32" width="8" height="6" fill="#ef4444" opacity="0.7"/>
              <text x="85" y="38" font-size="7" fill="#94a3b8" font-family="monospace">Max · 40% err</text>
            </svg>
          </div>
          <div class="project-body">
            <div class="project-type">Performance · Load Testing</div>
            <div class="project-name">Load Testing System</div>
            <div class="project-desc">Designed and executed load, stress, and spike tests using JMeter across 3 API endpoints (75 samples). Identified Request02 and Request03 as bottlenecks with 40% error rates and 5740ms max response times — findings used to guide backend optimisation.</div>
            <div class="project-tags">
              <span class="tag">JMeter</span><span class="tag">BlazeMeter</span><span class="tag">K6</span><span class="tag">Performance Testing</span>
            </div>
          </div>
        </div>

        <!-- PLAYWRIGHT + MCP -->
        <div class="project-card">
          <div class="project-preview project-preview--mcp">
            <svg viewBox="0 0 400 160" xmlns="http://www.w3.org/2000/svg" width="100%">
              <rect width="400" height="160" fill="#0d0d18"/>
              <!-- flow diagram -->
              <rect x="20" y="65" width="65" height="32" rx="4" fill="#1a1a2e" stroke="#00e5b0" stroke-width="1.5"/>
              <text x="52" y="85" font-size="9" fill="#00e5b0" font-family="monospace" text-anchor="middle">User Action</text>
              <rect x="110" y="65" width="65" height="32" rx="4" fill="#1a1a2e" stroke="#7c6aff" stroke-width="1"/>
              <text x="142" y="85" font-size="9" fill="#a78bfa" font-family="monospace" text-anchor="middle">Playwright</text>
              <rect x="200" y="65" width="65" height="32" rx="4" fill="#1a1a2e" stroke="#7c6aff" stroke-width="1"/>
              <text x="232" y="85" font-size="9" fill="#a78bfa" font-family="monospace" text-anchor="middle">MCP Layer</text>
              <rect x="290" y="65" width="65" height="32" rx="4" fill="#1a1a2e" stroke="#7c6aff" stroke-width="1"/>
              <text x="322" y="85" font-size="9" fill="#a78bfa" font-family="monospace" text-anchor="middle">Jira / AIO</text>
              <!-- arrows -->
              <line x1="85" y1="81" x2="110" y2="81" stroke="#00e5b0" stroke-width="1.5" marker-end="url(#arr2)"/>
              <line x1="175" y1="81" x2="200" y2="81" stroke="#7c6aff" stroke-width="1" marker-end="url(#arr3)"/>
              <line x1="265" y1="81" x2="290" y2="81" stroke="#7c6aff" stroke-width="1" marker-end="url(#arr3)"/>
              <defs>
                <marker id="arr2" markerWidth="6" markerHeight="6" refX="3" refY="3" orient="auto"><path d="M0,0 L6,3 L0,6 Z" fill="#00e5b0"/></marker>
                <marker id="arr3" markerWidth="6" markerHeight="6" refX="3" refY="3" orient="auto"><path d="M0,0 L6,3 L0,6 Z" fill="#7c6aff"/></marker>
              </defs>
              <text x="200" y="24" font-size="10" fill="#64748b" font-family="monospace" text-anchor="middle">Playwright + MCP Orchestration Layer</text>
              <text x="200" y="140" font-size="9" fill="#475569" font-family="monospace" text-anchor="middle">Zero manual handoff · AI-driven execution · auto-reporting</text>
            </svg>
          </div>
          <div class="project-body">
            <div class="project-type">AI · UI Automation</div>
            <div class="project-name">Playwright + MCP Integration</div>
            <div class="project-desc">UI automation framework using Playwright with MCP-based orchestration for AI-driven dynamic test execution. Results flow automatically into Jira and test management — zero manual handoff from test run to report.</div>
            <div class="project-tags">
              <span class="tag">Playwright</span><span class="tag">MCP</span><span class="tag">Jira</span><span class="tag">AI Agents</span>
            </div>
          </div>
        </div>

        <!-- AWS INFRA -->
        <div class="project-card">
          <div class="project-preview project-preview--aws">
            <svg viewBox="0 0 400 160" xmlns="http://www.w3.org/2000/svg" width="100%">
              <rect width="400" height="160" fill="#0d0d18"/>
              <!-- infrastructure diagram -->
              <rect x="160" y="20" width="80" height="28" rx="4" fill="#1a1a2e" stroke="#f59e0b" stroke-width="1"/>
              <text x="200" y="38" font-size="9" fill="#fbbf24" font-family="monospace" text-anchor="middle">ALB</text>
              <!-- arrows down -->
              <line x1="200" y1="48" x2="120" y2="72" stroke="#334155" stroke-width="1"/>
              <line x1="200" y1="48" x2="200" y2="72" stroke="#334155" stroke-width="1"/>
              <line x1="200" y1="48" x2="280" y2="72" stroke="#334155" stroke-width="1"/>
              <!-- EC2 instances -->
              <rect x="70" y="72" width="70" height="28" rx="4" fill="#1a1a2e" stroke="#7c6aff" stroke-width="1"/>
              <text x="105" y="90" font-size="9" fill="#a78bfa" font-family="monospace" text-anchor="middle">EC2 ×3</text>
              <rect x="160" y="72" width="70" height="28" rx="4" fill="#1a1a2e" stroke="#7c6aff" stroke-width="1"/>
              <text x="195" y="90" font-size="9" fill="#a78bfa" font-family="monospace" text-anchor="middle">Auto Scale</text>
              <rect x="250" y="72" width="70" height="28" rx="4" fill="#1a1a2e" stroke="#00e5b0" stroke-width="1"/>
              <text x="285" y="90" font-size="9" fill="#00e5b0" font-family="monospace" text-anchor="middle">Prometheus</text>
              <!-- bottom row -->
              <rect x="100" y="120" width="70" height="28" rx="4" fill="#1a1a2e" stroke="#1e293b" stroke-width="1"/>
              <text x="135" y="138" font-size="9" fill="#64748b" font-family="monospace" text-anchor="middle">Terraform</text>
              <rect x="210" y="120" width="70" height="28" rx="4" fill="#1a1a2e" stroke="#f97316" stroke-width="1"/>
              <text x="245" y="138" font-size="9" fill="#fb923c" font-family="monospace" text-anchor="middle">Grafana</text>
              <line x1="285" y1="100" x2="245" y2="120" stroke="#334155" stroke-width="1"/>
              <text x="200" y="15" font-size="10" fill="#64748b" font-family="monospace" text-anchor="middle">AWS Infrastructure · Terraform · Observability</text>
            </svg>
          </div>
          <div class="project-body">
            <div class="project-type">DevOps · Cloud</div>
            <div class="project-name">AWS Cloud Infrastructure</div>
            <div class="project-desc">Production-grade AWS infrastructure provisioned with Terraform — ALB, EC2 auto-scaling, Prometheus monitoring, and Grafana dashboards for full observability stack.</div>
            <div class="project-tags">
              <span class="tag">AWS</span><span class="tag">Terraform</span><span class="tag">Prometheus</span><span class="tag">Grafana</span><span class="tag">Docker</span>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- SKILLS -->
  <section id="skills">
    <div class="container">
      <div class="section-label">Skills</div>
      <h2 class="section-title">Tech stack.</h2>
      <div class="skills-grid">

        <div class="skill-group">
          <div class="skill-group-title">Languages</div>
          <div class="skill-list">
            <span class="skill-pill">Python</span>
            <span class="skill-pill">JavaScript</span>
            <span class="skill-pill">TypeScript</span>
            <span class="skill-pill">Java</span>
            <span class="skill-pill">Go</span>
            <span class="skill-pill">SQL</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-title">Automation</div>
          <div class="skill-list">
            <span class="skill-pill">Selenium</span>
            <span class="skill-pill">Playwright</span>
            <span class="skill-pill">WebdriverIO</span>
            <span class="skill-pill">Appium</span>
            <span class="skill-pill">Maestro</span>
            <span class="skill-pill">Sofy</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-title">AI & Agents</div>
          <div class="skill-list">
            <span class="skill-pill">LangChain</span>
            <span class="skill-pill">MCP</span>
            <span class="skill-pill">RAG</span>
            <span class="skill-pill">Prompt Engineering</span>
            <span class="skill-pill">Claude Code</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-title">DevOps & Cloud</div>
          <div class="skill-list">
            <span class="skill-pill">AWS</span>
            <span class="skill-pill">Terraform</span>
            <span class="skill-pill">Docker</span>
            <span class="skill-pill">Jenkins</span>
            <span class="skill-pill">GitHub Actions</span>
            <span class="skill-pill">CI/CD</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-title">Performance & Observability</div>
          <div class="skill-list">
            <span class="skill-pill">JMeter</span>
            <span class="skill-pill">BlazeMeter</span>
            <span class="skill-pill">K6</span>
            <span class="skill-pill">Prometheus</span>
            <span class="skill-pill">Grafana</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-title">Backend & APIs</div>
          <div class="skill-list">
            <span class="skill-pill">REST APIs</span>
            <span class="skill-pill">Postman</span>
            <span class="skill-pill">Rest-Assured</span>
            <span class="skill-pill">Go</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-title">Tools & Process</div>
          <div class="skill-list">
            <span class="skill-pill">Jira</span>
            <span class="skill-pill">AIO Tests</span>
            <span class="skill-pill">Git</span>
            <span class="skill-pill">Figma</span>
            <span class="skill-pill">Agile</span>
          </div>
        </div>

        <div class="skill-group">
          <div class="skill-group-title">Concepts</div>
          <div class="skill-list">
            <span class="skill-pill">System Design</span>
            <span class="skill-pill">Distributed Systems</span>
            <span class="skill-pill">QA Strategy</span>
            <span class="skill-pill">Chaos Engineering</span>
            <span class="skill-pill">Scalability</span>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact">
    <div class="container">
      <div class="contact-grid">
        <div>
          <div class="section-label">Contact</div>
          <h2 class="contact-headline">Let's build<br>something <span>great</span>.</h2>
          <p class="contact-text">
            Open to interesting engineering roles, collaborations, and conversations around automation, AI, and quality systems. Based in Karachi — working globally.
          </p>
          <a href="mailto:bawanyabdulrehman@gmail.com" class="btn btn-primary">Send an Email</a>
        </div>
        <div class="contact-links">
          <a href="mailto:bawanyabdulrehman@gmail.com" class="contact-link">
            <div class="contact-link-icon">✉</div>
            <div class="contact-link-text">
              <div class="contact-link-label">Email</div>
              <div class="contact-link-value">bawanyabdulrehman@gmail.com</div>
            </div>
          </a>
          <a href="https://linkedin.com/in/abdulrehmanbawany" target="_blank" class="contact-link">
            <div class="contact-link-icon">in</div>
            <div class="contact-link-text">
              <div class="contact-link-label">LinkedIn</div>
              <div class="contact-link-value">abdulrehmanbawany</div>
            </div>
          </a>
          <a href="https://github.com/bawanyabdulrehman" target="_blank" class="contact-link">
            <div class="contact-link-icon">⌥</div>
            <div class="contact-link-text">
              <div class="contact-link-label">GitHub</div>
              <div class="contact-link-value">bawanyabdulrehman</div>
            </div>
          </a>
          <a href="tel:+923113860984" class="contact-link">
            <div class="contact-link-icon">☎</div>
            <div class="contact-link-text">
              <div class="contact-link-label">Phone</div>
              <div class="contact-link-value">+92 311 3860984</div>
            </div>
          </a>
        </div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    © 2025 Abdul Rehman · Built with precision.
  </footer>

</body>
</html>

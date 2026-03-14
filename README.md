<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Khafif Badr — Developer & UI Designer</title>
  <meta name="description" content="Portfolio of Khafif Badr — full-stack developer and UI designer based in Casablanca." />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=Fira+Code:wght@300;400;500&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg: #0a0a08;
      --bg2: #111110;
      --bg3: #1a1a18;
      --line: rgba(255,255,255,0.07);
      --text: #e8e6df;
      --muted: #6b6960;
      --accent: #c8f060;
      --accent2: #f0c860;
      --border: rgba(255,255,255,0.09);
      --font-display: 'Syne', sans-serif;
      --font-mono: 'Fira Code', monospace;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: var(--font-mono);
      font-size: 14px;
      line-height: 1.6;
      overflow-x: hidden;
      cursor: none;
    }

    /* Custom cursor */
    .cursor {
      position: fixed;
      width: 8px; height: 8px;
      background: var(--accent);
      border-radius: 50%;
      pointer-events: none;
      z-index: 9999;
      transition: transform 0.1s ease;
      mix-blend-mode: difference;
    }
    .cursor-ring {
      position: fixed;
      width: 32px; height: 32px;
      border: 1px solid rgba(200,240,96,0.4);
      border-radius: 50%;
      pointer-events: none;
      z-index: 9998;
      transition: transform 0.18s ease, width 0.2s, height 0.2s, opacity 0.2s;
    }
    body:has(a:hover) .cursor-ring,
    body:has(.project-card:hover) .cursor-ring {
      width: 48px; height: 48px;
      opacity: 0.7;
    }

    /* Grid texture overlay */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image:
        linear-gradient(var(--line) 1px, transparent 1px),
        linear-gradient(90deg, var(--line) 1px, transparent 1px);
      background-size: 60px 60px;
      pointer-events: none;
      z-index: 0;
    }

    /* Noise grain */
    body::after {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
      pointer-events: none;
      z-index: 0;
      opacity: 0.35;
    }

    section, nav, footer { position: relative; z-index: 1; }

    /* NAV */
    nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 20px 48px;
      border-bottom: 1px solid var(--border);
      background: rgba(10,10,8,0.85);
      backdrop-filter: blur(12px);
      z-index: 100;
    }

    .nav-logo {
      font-family: var(--font-display);
      font-weight: 800;
      font-size: 15px;
      letter-spacing: -0.5px;
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
      letter-spacing: 0.5px;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--text); }

    /* HERO */
    #hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      padding: 0 48px 72px;
    }

    .hero-label {
      font-size: 11px;
      letter-spacing: 3px;
      color: var(--accent);
      text-transform: uppercase;
      margin-bottom: 20px;
      opacity: 0;
      animation: fadeUp 0.6s ease 0.2s forwards;
    }

    .hero-name {
      font-family: var(--font-display);
      font-size: clamp(56px, 9vw, 112px);
      font-weight: 800;
      line-height: 0.92;
      letter-spacing: -3px;
      color: var(--text);
      margin-bottom: 32px;
      opacity: 0;
      animation: fadeUp 0.8s ease 0.4s forwards;
    }

    .hero-name .line2 {
      display: block;
      color: transparent;
      -webkit-text-stroke: 1px rgba(232,230,223,0.3);
    }

    .hero-bottom {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      gap: 24px;
      opacity: 0;
      animation: fadeUp 0.7s ease 0.7s forwards;
    }

    .hero-desc {
      max-width: 420px;
      color: var(--muted);
      font-size: 13px;
      line-height: 1.8;
    }

    .hero-desc strong {
      color: var(--text);
      font-weight: 400;
    }

    .hero-cta {
      display: inline-flex;
      align-items: center;
      gap: 10px;
      padding: 14px 28px;
      background: var(--accent);
      color: #0a0a08;
      font-family: var(--font-mono);
      font-size: 12px;
      font-weight: 500;
      letter-spacing: 0.5px;
      text-decoration: none;
      border-radius: 2px;
      white-space: nowrap;
      transition: background 0.2s, transform 0.15s;
      flex-shrink: 0;
    }
    .hero-cta:hover {
      background: #d9ff6e;
      transform: translateY(-2px);
    }

    .scroll-hint {
      position: absolute;
      bottom: 28px;
      left: 50%;
      transform: translateX(-50%);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 6px;
      color: var(--muted);
      font-size: 10px;
      letter-spacing: 2px;
      text-transform: uppercase;
      animation: fadeIn 1s ease 1.2s both;
    }

    .scroll-line {
      width: 1px;
      height: 36px;
      background: linear-gradient(to bottom, var(--muted), transparent);
      animation: scrollPulse 2s ease-in-out infinite;
    }

    /* ABOUT */
    #about {
      padding: 120px 48px;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: start;
      border-top: 1px solid var(--border);
    }

    .section-num {
      font-size: 11px;
      letter-spacing: 3px;
      color: var(--accent);
      text-transform: uppercase;
      margin-bottom: 40px;
      display: block;
    }

    .about-heading {
      font-family: var(--font-display);
      font-size: clamp(32px, 4vw, 52px);
      font-weight: 800;
      letter-spacing: -1.5px;
      line-height: 1.05;
      color: var(--text);
    }

    .about-text {
      color: var(--muted);
      font-size: 13px;
      line-height: 1.9;
      margin-bottom: 20px;
    }

    .about-text strong { color: var(--text); font-weight: 400; }

    .skills-list {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 8px;
      margin-top: 32px;
    }

    .skill-item {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 12px;
      color: var(--muted);
      padding: 8px 0;
      border-bottom: 1px solid var(--border);
    }

    .skill-item::before {
      content: '';
      width: 4px; height: 4px;
      border-radius: 50%;
      background: var(--accent);
      flex-shrink: 0;
    }

    /* PROJECTS */
    #projects {
      padding: 120px 48px;
      border-top: 1px solid var(--border);
    }

    .projects-header {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      margin-bottom: 60px;
    }

    .section-heading {
      font-family: var(--font-display);
      font-size: clamp(32px, 4vw, 52px);
      font-weight: 800;
      letter-spacing: -1.5px;
      line-height: 1.05;
      color: var(--text);
    }

    .view-all {
      font-size: 12px;
      color: var(--muted);
      text-decoration: none;
      border-bottom: 1px solid var(--border);
      padding-bottom: 2px;
      transition: color 0.2s, border-color 0.2s;
    }
    .view-all:hover { color: var(--accent); border-color: var(--accent); }

    .projects-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1px;
      background: var(--border);
      border: 1px solid var(--border);
    }

    .project-card {
      background: var(--bg);
      padding: 36px 32px;
      text-decoration: none;
      display: flex;
      flex-direction: column;
      gap: 12px;
      transition: background 0.2s;
      position: relative;
      overflow: hidden;
    }

    .project-card::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 2px;
      background: var(--accent);
      transform: scaleX(0);
      transform-origin: left;
      transition: transform 0.3s ease;
    }

    .project-card:hover {
      background: var(--bg3);
    }
    .project-card:hover::before { transform: scaleX(1); }

    .project-num {
      font-size: 10px;
      letter-spacing: 2px;
      color: var(--muted);
    }

    .project-name {
      font-family: var(--font-display);
      font-size: 20px;
      font-weight: 700;
      letter-spacing: -0.5px;
      color: var(--text);
    }

    .project-desc {
      font-size: 12px;
      color: var(--muted);
      line-height: 1.7;
      flex: 1;
    }

    .project-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-top: 8px;
    }

    .project-lang {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      font-size: 11px;
      color: var(--muted);
    }

    .lang-dot {
      width: 7px; height: 7px;
      border-radius: 50%;
    }

    .project-arrow {
      font-size: 16px;
      color: var(--muted);
      transition: transform 0.2s, color 0.2s;
    }
    .project-card:hover .project-arrow {
      transform: translate(3px, -3px);
      color: var(--accent);
    }

    /* CONTACT */
    #contact {
      padding: 120px 48px;
      border-top: 1px solid var(--border);
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: center;
    }

    .contact-big {
      font-family: var(--font-display);
      font-size: clamp(36px, 5vw, 64px);
      font-weight: 800;
      letter-spacing: -2px;
      line-height: 1;
      color: var(--text);
    }

    .contact-big span {
      display: block;
      color: transparent;
      -webkit-text-stroke: 1px rgba(232,230,223,0.2);
    }

    .contact-links {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }

    .contact-link {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 20px 24px;
      border: 1px solid var(--border);
      border-radius: 2px;
      text-decoration: none;
      color: var(--text);
      transition: border-color 0.2s, background 0.2s;
    }

    .contact-link:hover {
      border-color: var(--accent);
      background: rgba(200,240,96,0.04);
    }

    .contact-link-label {
      font-size: 11px;
      letter-spacing: 1px;
      text-transform: uppercase;
      color: var(--muted);
      margin-bottom: 3px;
    }

    .contact-link-value {
      font-family: var(--font-display);
      font-size: 15px;
      font-weight: 600;
    }

    .contact-arrow {
      color: var(--muted);
      font-size: 18px;
      transition: transform 0.2s, color 0.2s;
    }
    .contact-link:hover .contact-arrow {
      transform: translate(3px, -3px);
      color: var(--accent);
    }

    /* FOOTER */
    footer {
      border-top: 1px solid var(--border);
      padding: 28px 48px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      color: var(--muted);
      font-size: 11px;
    }

    /* ANIMATIONS */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeIn {
      from { opacity: 0; } to { opacity: 1; }
    }
    @keyframes scrollPulse {
      0%, 100% { opacity: 0.3; transform: scaleY(1); }
      50%       { opacity: 1; transform: scaleY(1.2); }
    }

    .reveal {
      opacity: 0;
      transform: translateY(30px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* RESPONSIVE */
    @media (max-width: 768px) {
      nav { padding: 16px 24px; }
      .nav-links { display: none; }
      #hero { padding: 0 24px 60px; }
      .hero-bottom { flex-direction: column; align-items: flex-start; }
      #about, #contact { padding: 80px 24px; grid-template-columns: 1fr; gap: 40px; }
      #projects { padding: 80px 24px; }
      .projects-grid { grid-template-columns: 1fr; }
      footer { padding: 24px; flex-direction: column; gap: 8px; text-align: center; }
    }
  </style>
</head>
<body>

  <!-- Cursor -->
  <div class="cursor" id="cursor"></div>
  <div class="cursor-ring" id="cursorRing"></div>

  <!-- Nav -->
  <nav>
    <a href="#" class="nav-logo">K<span>.</span>Badr</a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#contact">Contact</a></li>
      <li><a href="https://github.com/Griffith-0-0" target="_blank">GitHub ↗</a></li>
    </ul>
  </nav>

  <!-- Hero -->
  <section id="hero">
    <div class="hero-label">Full-stack developer & UI designer</div>
    <h1 class="hero-name">
      Khafif<br>
      <span class="line2">Badr</span>
    </h1>
    <div class="hero-bottom">
      <p class="hero-desc">
        Based in <strong>Casablanca, Morocco</strong> — I build clean interfaces and robust backends.
        From <strong>React</strong> frontends to <strong>Java</strong> web services,
        I care about the details that make software feel right.
      </p>
      <a href="#projects" class="hero-cta">View my work →</a>
    </div>
    <div class="scroll-hint">
      <div class="scroll-line"></div>
      scroll
    </div>
  </section>

  <!-- About -->
  <section id="about">
    <div class="reveal">
      <span class="section-num">01 — About</span>
      <h2 class="about-heading">Developer<br>with taste.</h2>
    </div>
    <div class="reveal" style="transition-delay: 0.1s">
      <p class="about-text">
        I'm <strong>Khafif Badr</strong>, a developer who enjoys working at the intersection of
        engineering and design. I build things that work well <em>and</em> look great.
      </p>
      <p class="about-text">
        I'm comfortable across the full stack — from pixel-precise UI components
        to <strong>SOAP web services</strong> and <strong>REST APIs</strong>.
        I enjoy the problem-solving side of software as much as the craft of making it feel polished.
      </p>
      <div class="skills-list">
        <div class="skill-item">JavaScript</div>
        <div class="skill-item">TypeScript</div>
        <div class="skill-item">React & Hooks</div>
        <div class="skill-item">Java / SOAP</div>
        <div class="skill-item">HTML & CSS</div>
        <div class="skill-item">Figma</div>
        <div class="skill-item">UI Design</div>
        <div class="skill-item">Git & GitHub</div>
      </div>
    </div>
  </section>

  <!-- Projects -->
  <section id="projects">
    <div class="projects-header reveal">
      <div>
        <span class="section-num">02 — Work</span>
        <h2 class="section-heading">Selected<br>projects.</h2>
      </div>
      <a href="https://github.com/Griffith-0-0?tab=repositories" target="_blank" class="view-all">
        All repositories ↗
      </a>
    </div>
    <div class="projects-grid reveal" style="transition-delay:0.1s">

      <a class="project-card" href="https://github.com/Griffith-0-0/slack-project" target="_blank">
        <span class="project-num">01</span>
        <div class="project-name">Slack Project</div>
        <p class="project-desc">A messaging app inspired by Slack, featuring real-time channel communication and a clean workspace interface.</p>
        <div class="project-footer">
          <div class="project-lang">
            <span class="lang-dot" style="background:#3178c6"></span>TypeScript
          </div>
          <span class="project-arrow">↗</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/Griffith-0-0/Tracker" target="_blank">
        <span class="project-num">02</span>
        <div class="project-name">Tracker</div>
        <p class="project-desc">A task and activity tracking application. Focused on a clean, minimal interface and straightforward state management.</p>
        <div class="project-footer">
          <div class="project-lang">
            <span class="lang-dot" style="background:#f7df1e"></span>JavaScript
          </div>
          <span class="project-arrow">↗</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/Griffith-0-0/tp-react-hooks" target="_blank">
        <span class="project-num">03</span>
        <div class="project-name">React Hooks</div>
        <p class="project-desc">Practical exploration of React hooks — useState, useEffect, useContext and custom hooks with real use cases.</p>
        <div class="project-footer">
          <div class="project-lang">
            <span class="lang-dot" style="background:#61dafb"></span>React
          </div>
          <span class="project-arrow">↗</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/Griffith-0-0/WS-SOAP-prj1" target="_blank">
        <span class="project-num">04</span>
        <div class="project-name">WS-SOAP</div>
        <p class="project-desc">A Java web service built on SOAP protocol. Covers service definition, WSDL, and client-server communication patterns.</p>
        <div class="project-footer">
          <div class="project-lang">
            <span class="lang-dot" style="background:#f89820"></span>Java
          </div>
          <span class="project-arrow">↗</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/Griffith-0-0/calculator" target="_blank">
        <span class="project-num">05</span>
        <div class="project-name">Calculator</div>
        <p class="project-desc">A clean calculator built from scratch. Simple project, but a great benchmark for UI precision and logic clarity.</p>
        <div class="project-footer">
          <div class="project-lang">
            <span class="lang-dot" style="background:#e34c26"></span>HTML/CSS
          </div>
          <span class="project-arrow">↗</span>
        </div>
      </a>

      <a class="project-card" href="https://github.com/Griffith-0-0/TP-react-hooks2" target="_blank">
        <span class="project-num">06</span>
        <div class="project-name">React Hooks II</div>
        <p class="project-desc">A deeper dive into React patterns — advanced hook composition, performance optimisation, and component architecture.</p>
        <div class="project-footer">
          <div class="project-lang">
            <span class="lang-dot" style="background:#61dafb"></span>React
          </div>
          <span class="project-arrow">↗</span>
        </div>
      </a>

    </div>
  </section>

  <!-- Contact -->
  <section id="contact">
    <div class="reveal">
      <span class="section-num">03 — Contact</span>
      <div class="contact-big">
        Let's<br>work
        <span>together.</span>
      </div>
    </div>
    <div class="contact-links reveal" style="transition-delay:0.1s">
      <a class="contact-link" href="https://github.com/Griffith-0-0" target="_blank">
        <div>
          <div class="contact-link-label">GitHub</div>
          <div class="contact-link-value">Griffith-0-0</div>
        </div>
        <span class="contact-arrow">↗</span>
      </a>
      <!-- Replace href and value with your real email -->
      <a class="contact-link" href="mailto:your@email.com">
        <div>
          <div class="contact-link-label">Email</div>
          <div class="contact-link-value">your@email.com</div>
        </div>
        <span class="contact-arrow">↗</span>
      </a>
      <!-- Replace href with your real LinkedIn URL -->
      <a class="contact-link" href="https://linkedin.com/in/yourprofile" target="_blank">
        <div>
          <div class="contact-link-label">LinkedIn</div>
          <div class="contact-link-value">Khafif Badr</div>
        </div>
        <span class="contact-arrow">↗</span>
      </a>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <span>© 2026 Khafif Badr</span>
    <span>Built with HTML · Hosted on GitHub Pages</span>
  </footer>

  <script>
    // Custom cursor
    const cursor = document.getElementById('cursor');
    const ring = document.getElementById('cursorRing');
    let mx = 0, my = 0, rx = 0, ry = 0;

    document.addEventListener('mousemove', e => {
      mx = e.clientX; my = e.clientY;
      cursor.style.transform = `translate(${mx - 4}px, ${my - 4}px)`;
    });

    function animateRing() {
      rx += (mx - rx - 16) * 0.12;
      ry += (my - ry - 16) * 0.12;
      ring.style.transform = `translate(${rx}px, ${ry}px)`;
      requestAnimationFrame(animateRing);
    }
    animateRing();

    // Scroll reveal
    const reveals = document.querySelectorAll('.reveal');
    const obs = new IntersectionObserver(entries => {
      entries.forEach(e => {
        if (e.isIntersecting) {
          e.target.classList.add('visible');
          obs.unobserve(e.target);
        }
      });
    }, { threshold: 0.1 });
    reveals.forEach(el => obs.observe(el));

    // Hide default cursor
    document.addEventListener('mouseleave', () => {
      cursor.style.opacity = '0';
      ring.style.opacity = '0';
    });
    document.addEventListener('mouseenter', () => {
      cursor.style.opacity = '1';
      ring.style.opacity = '1';
    });
  </script>
</body>
</html>

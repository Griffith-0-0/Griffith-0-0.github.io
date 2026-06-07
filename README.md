<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Badr Khafif - Full-Stack / DevOps Engineer</title>
  <meta name="description" content="Portfolio of Badr Khafif, Full-Stack and DevOps engineer based in Casablanca, Morocco." />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;600&family=Syne:wght@500;600;700;800&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg: #080a0c;
      --panel: #101418;
      --panel-2: #151b21;
      --line: rgba(255, 255, 255, 0.08);
      --text: #f2f0e8;
      --muted: #9298a0;
      --accent: #8ee66b;
      --accent-2: #62c8ff;
      --warn: #ffd166;
      --border: rgba(255, 255, 255, 0.11);
      --font-display: "Syne", sans-serif;
      --font-mono: "Fira Code", monospace;
    }

    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      scroll-behavior: smooth;
      overflow-x: hidden;
    }

    body {
      min-height: 100vh;
      background:
        radial-gradient(circle at 78% 10%, rgba(98, 200, 255, 0.12), transparent 28rem),
        radial-gradient(circle at 18% 22%, rgba(142, 230, 107, 0.12), transparent 24rem),
        var(--bg);
      color: var(--text);
      font-family: var(--font-mono);
      font-size: 14px;
      line-height: 1.65;
      overflow-x: hidden;
      width: 100%;
    }

    body::before {
      content: "";
      position: fixed;
      inset: 0;
      background-image:
        linear-gradient(var(--line) 1px, transparent 1px),
        linear-gradient(90deg, var(--line) 1px, transparent 1px);
      background-size: 58px 58px;
      pointer-events: none;
      z-index: 0;
      mask-image: linear-gradient(to bottom, black, transparent 86%);
    }

    a {
      color: inherit;
    }

    nav, section, footer {
      position: relative;
      z-index: 1;
    }

    nav {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 18px clamp(20px, 5vw, 56px);
      border-bottom: 1px solid var(--border);
      background: rgba(8, 10, 12, 0.82);
      backdrop-filter: blur(14px);
      z-index: 10;
    }

    .nav-logo {
      font-family: var(--font-display);
      font-size: 16px;
      font-weight: 800;
      letter-spacing: 0;
      text-decoration: none;
    }

    .nav-logo span {
      color: var(--accent);
    }

    .nav-links {
      display: flex;
      gap: 30px;
      list-style: none;
    }

    .nav-links a {
      color: var(--muted);
      font-size: 12px;
      text-decoration: none;
      transition: color 160ms ease;
    }

    .nav-links a:hover {
      color: var(--text);
    }

    .hero {
      min-height: 100vh;
      display: grid;
      align-content: end;
      gap: 34px;
      padding: 128px clamp(20px, 5vw, 56px) 74px;
    }

    .hero > * {
      min-width: 0;
    }

    .eyebrow {
      color: var(--accent);
      font-size: 11px;
      letter-spacing: 2.4px;
      text-transform: uppercase;
      overflow-wrap: anywhere;
    }

    h1, h2, h3 {
      font-family: var(--font-display);
      line-height: 1;
      letter-spacing: 0;
    }

    h1 {
      max-width: 980px;
      font-size: clamp(54px, 9vw, 116px);
      font-weight: 800;
      overflow-wrap: anywhere;
    }

    .outline {
      display: block;
      color: transparent;
      -webkit-text-stroke: 1px rgba(242, 240, 232, 0.34);
    }

    .hero-bottom {
      display: grid;
      grid-template-columns: minmax(0, 560px) auto;
      gap: 28px;
      align-items: end;
      justify-content: space-between;
    }

    .hero-copy {
      color: var(--muted);
      font-size: 14px;
      max-width: 620px;
      min-width: 0;
    }

    .hero-copy strong {
      color: var(--text);
      font-weight: 500;
    }

    .actions {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
    }

    .button {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 46px;
      padding: 0 22px;
      border: 1px solid var(--border);
      border-radius: 6px;
      color: var(--text);
      font-size: 12px;
      font-weight: 500;
      text-decoration: none;
      transition: transform 160ms ease, border-color 160ms ease, background 160ms ease;
    }

    .button.primary {
      background: var(--accent);
      border-color: var(--accent);
      color: #08100a;
    }

    .button:hover {
      transform: translateY(-2px);
      border-color: var(--accent);
      background: rgba(142, 230, 107, 0.08);
    }

    .button.primary:hover {
      background: #9bf276;
    }

    .stats {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      border: 1px solid var(--border);
      background: rgba(16, 20, 24, 0.74);
      min-width: 0;
    }

    .stat {
      padding: 20px;
      border-right: 1px solid var(--border);
      min-width: 0;
    }

    .stat:last-child {
      border-right: 0;
    }

    .stat strong {
      display: block;
      color: var(--text);
      font-family: var(--font-display);
      font-size: 24px;
      font-weight: 800;
      margin-bottom: 2px;
    }

    .stat span {
      color: var(--muted);
      font-size: 11px;
    }

    section {
      padding: 104px clamp(20px, 5vw, 56px);
      border-top: 1px solid var(--border);
    }

    .section-header {
      display: grid;
      grid-template-columns: minmax(0, 0.8fr) minmax(0, 1.2fr);
      gap: 48px;
      align-items: start;
      margin-bottom: 46px;
    }

    h2 {
      font-size: clamp(34px, 5vw, 58px);
      font-weight: 800;
    }

    .section-copy {
      color: var(--muted);
      max-width: 680px;
    }

    .cards-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 1px;
      border: 1px solid var(--border);
      background: var(--border);
    }

    .card {
      min-height: 270px;
      display: flex;
      flex-direction: column;
      gap: 18px;
      padding: 28px;
      background: rgba(16, 20, 24, 0.92);
      text-decoration: none;
      transition: background 160ms ease;
      min-width: 0;
    }

    .card:hover {
      background: var(--panel-2);
    }

    .card small {
      color: var(--accent);
      font-size: 10px;
      letter-spacing: 1.8px;
      text-transform: uppercase;
    }

    .card h3 {
      font-size: 22px;
      font-weight: 800;
    }

    .card p {
      color: var(--muted);
      font-size: 12px;
      flex: 1;
    }

    .tags {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }

    .tag {
      border: 1px solid var(--border);
      border-radius: 999px;
      color: var(--muted);
      font-size: 10px;
      padding: 4px 9px;
    }

    .timeline {
      display: grid;
      gap: 1px;
      border: 1px solid var(--border);
      background: var(--border);
    }

    .timeline-item {
      display: grid;
      grid-template-columns: 220px minmax(0, 1fr);
      gap: 28px;
      padding: 26px;
      background: rgba(16, 20, 24, 0.92);
    }

    .date {
      color: var(--accent-2);
      font-size: 12px;
    }

    .timeline-item h3 {
      font-size: 20px;
      margin-bottom: 8px;
    }

    .timeline-item p {
      color: var(--muted);
      font-size: 13px;
      max-width: 820px;
    }

    .skills {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 1px;
      border: 1px solid var(--border);
      background: var(--border);
    }

    .skill-group {
      padding: 24px;
      background: rgba(16, 20, 24, 0.92);
    }

    .skill-group h3 {
      color: var(--accent);
      font-size: 15px;
      margin-bottom: 16px;
    }

    .skill-group ul {
      list-style: none;
      display: grid;
      gap: 9px;
      color: var(--muted);
      font-size: 12px;
    }

    .contact {
      display: grid;
      grid-template-columns: minmax(0, 0.9fr) minmax(0, 1.1fr);
      gap: 44px;
      align-items: center;
    }

    .contact-list {
      display: grid;
      gap: 12px;
    }

    .contact-link {
      display: flex;
      justify-content: space-between;
      gap: 18px;
      padding: 18px 20px;
      border: 1px solid var(--border);
      border-radius: 6px;
      background: rgba(16, 20, 24, 0.7);
      color: var(--text);
      text-decoration: none;
      transition: border-color 160ms ease, background 160ms ease;
      min-width: 0;
    }

    .contact-link:hover {
      border-color: var(--accent);
      background: rgba(142, 230, 107, 0.06);
    }

    .contact-link span:first-child {
      color: var(--muted);
      font-size: 11px;
      letter-spacing: 1.2px;
      text-transform: uppercase;
    }

    .contact-link strong {
      overflow-wrap: anywhere;
      text-align: right;
    }

    footer {
      display: flex;
      justify-content: space-between;
      gap: 18px;
      padding: 28px clamp(20px, 5vw, 56px);
      border-top: 1px solid var(--border);
      color: var(--muted);
      font-size: 11px;
    }

    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 560ms ease, transform 560ms ease;
    }

    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    @media (prefers-reduced-motion: reduce) {
      html {
        scroll-behavior: auto;
      }

      .reveal {
        opacity: 1;
        transform: none;
        transition: none;
      }

      .button, .card, .contact-link {
        transition: none;
      }
    }

    @media (max-width: 920px) {
      .hero-bottom,
      .section-header,
      .contact {
        grid-template-columns: 1fr;
      }

      .stats,
      .cards-grid,
      .skills {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .stat:nth-child(2) {
        border-right: 0;
      }

      .stat:nth-child(-n + 2) {
        border-bottom: 1px solid var(--border);
      }
    }

    @media (max-width: 680px) {
      nav {
        padding: 15px 20px;
      }

      .nav-links {
        display: none;
      }

      .hero {
        min-height: auto;
        padding-top: 112px;
      }

      h1 {
        font-size: clamp(42px, 14vw, 62px);
      }

      .stats,
      .cards-grid,
      .skills {
        grid-template-columns: 1fr;
      }

      .stat {
        border-right: 0;
        border-bottom: 1px solid var(--border);
      }

      .stat:last-child {
        border-bottom: 0;
      }

      .timeline-item {
        grid-template-columns: 1fr;
        gap: 10px;
      }

      section {
        padding-top: 76px;
        padding-bottom: 76px;
      }

      footer {
        flex-direction: column;
      }
    }
  </style>
</head>
<body>
  <nav>
    <a class="nav-logo" href="#top">Badr<span>.</span>DevOps</a>
    <ul class="nav-links">
      <li><a href="#projects">Projects</a></li>
      <li><a href="#experience">Experience</a></li>
      <li><a href="#skills">Stack</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
  </nav>

  <main id="top">
    <section class="hero">
      <div class="eyebrow reveal">Casablanca, Morocco - Full-Stack / DevOps Engineer</div>
      <h1 class="reveal" style="transition-delay: 80ms">
        Badr Khafif
        <span class="outline">builds delivery systems.</span>
      </h1>
      <div class="hero-bottom reveal" style="transition-delay: 160ms">
        <p class="hero-copy">
          Computer engineering graduate focused on <strong>CI/CD</strong>, <strong>containerization</strong>,
          <strong>Kubernetes</strong>, microservices, and observability. I connect product code with reliable
          deployment pipelines, monitoring, and secure production practices.
        </p>
        <div class="actions">
          <a class="button primary" href="#projects">View projects</a>
          <a class="button" href="Badr-Khafif-DevOps-CV.pdf">Download CV</a>
        </div>
      </div>
      <div class="stats reveal" style="transition-delay: 240ms">
        <div class="stat"><strong>CI/CD</strong><span>Jenkins, GitHub Actions, GitOps</span></div>
        <div class="stat"><strong>K8s</strong><span>Helm, Argo CD, RBAC, Ingress</span></div>
        <div class="stat"><strong>Obs</strong><span>Prometheus, Grafana, Loki, Jaeger</span></div>
        <div class="stat"><strong>Full Stack</strong><span>React, Node.js, Spring Boot, SwiftUI</span></div>
      </div>
    </section>

    <section id="projects">
      <div class="section-header reveal">
        <div>
          <div class="eyebrow">01 - Selected Projects</div>
          <h2>DevOps and product work.</h2>
        </div>
        <p class="section-copy">
          Recent projects from my CV, with a stronger emphasis on infrastructure, deployment quality,
          observability, and secure application architecture.
        </p>
      </div>

      <div class="cards-grid reveal" style="transition-delay: 100ms">
        <a class="card" href="https://github.com/Griffith-0-0/chat-app-devops" target="_blank" rel="noreferrer">
          <small>Flagship - Dec 2024 / Apr 2025</small>
          <h3>Chat App DevOps Chain</h3>
          <p>
            Microservices chat platform with React, Node.js, PostgreSQL, Redis, RabbitMQ, Socket.io,
            Docker, Jenkins, Kubernetes, Helm, and Argo CD.
          </p>
          <div class="tags">
            <span class="tag">Jenkins</span><span class="tag">Kubernetes</span><span class="tag">Argo CD</span><span class="tag">Grafana</span>
          </div>
        </a>

        <a class="card" href="https://github.com/Griffith-0-0/KrineyApp" target="_blank" rel="noreferrer">
          <small>PFE - Jan 2026 / Present</small>
          <h3>Kriney iOS Rental App</h3>
          <p>
            Native SwiftUI vehicle rental app with client and agency interfaces, Supabase backend,
            GitHub Actions, XCTest, SwiftLint, and a reusable design system.
          </p>
          <div class="tags">
            <span class="tag">SwiftUI</span><span class="tag">Supabase</span><span class="tag">XCTest</span><span class="tag">CI/CD</span>
          </div>
        </a>

        <a class="card" href="https://github.com/Griffith-0-0" target="_blank" rel="noreferrer">
          <small>2024</small>
          <h3>Full-Stack Banking App</h3>
          <p>
            Secure banking dashboard with Spring Boot, Angular, MySQL, JWT, Spring Security,
            dynamic charts, account management, and client operations.
          </p>
          <div class="tags">
            <span class="tag">Spring Boot</span><span class="tag">Angular</span><span class="tag">JWT</span><span class="tag">MySQL</span>
          </div>
        </a>

        <a class="card" href="https://github.com/Griffith-0-0" target="_blank" rel="noreferrer">
          <small>2024</small>
          <h3>Mobile Banking App</h3>
          <p>
            Cross-platform Android and iOS banking app with Flutter, Firebase, real-time sync,
            push notifications, card management, and biometric authentication.
          </p>
          <div class="tags">
            <span class="tag">Flutter</span><span class="tag">Firebase</span><span class="tag">Dart</span>
          </div>
        </a>

        <a class="card" href="https://github.com/Griffith-0-0/TLancer" target="_blank" rel="noreferrer">
          <small>2023</small>
          <h3>Fiverr Clone</h3>
          <p>
            Freelance marketplace clone covering gigs, orders, messaging, reviews, JWT authentication,
            React Query state management, Stripe, and Cloudinary uploads.
          </p>
          <div class="tags">
            <span class="tag">React</span><span class="tag">Express</span><span class="tag">MongoDB</span><span class="tag">Stripe</span>
          </div>
        </a>

        <a class="card" href="https://github.com/Griffith-0-0?tab=repositories" target="_blank" rel="noreferrer">
          <small>More on GitHub</small>
          <h3>Repositories</h3>
          <p>
            Explore additional frontend, backend, React hooks, Java web service, and utility projects
            on my GitHub profile.
          </p>
          <div class="tags">
            <span class="tag">GitHub</span><span class="tag">Open Source</span>
          </div>
        </a>
      </div>
    </section>

    <section id="experience">
      <div class="section-header reveal">
        <div>
          <div class="eyebrow">02 - Experience</div>
          <h2>Engineering background.</h2>
        </div>
        <p class="section-copy">
          A hybrid path: software engineering, cloud and big data studies, technical project coordination,
          ERP deployment, and hands-on DevOps project work.
        </p>
      </div>

      <div class="timeline reveal" style="transition-delay: 100ms">
        <div class="timeline-item">
          <div class="date">Sept 2024 - Present</div>
          <div>
            <h3>Master in Computer Engineering - Big Data & Cloud Computing</h3>
            <p>ENSET Mohammedia, Morocco. Current focus on cloud architectures, big data systems, and modern software engineering practices.</p>
          </div>
        </div>
        <div class="timeline-item">
          <div class="date">Jun 2023 - Present</div>
          <div>
            <h3>Vehicle Homologation Engineer - SEGULA Technologies / STELLANTIS</h3>
            <p>Technical and regulatory preparation for Africa and GCC markets, cross-functional coordination, and compliance validation.</p>
          </div>
        </div>
        <div class="timeline-item">
          <div class="date">Jun 2023 - Dec 2023</div>
          <div>
            <h3>Salesforce Administrator Program - ALX Africa</h3>
            <p>Salesforce administration training and certification path, complementing CRM and process automation experience.</p>
          </div>
        </div>
        <div class="timeline-item">
          <div class="date">Sept 2017 - Jun 2022</div>
          <div>
            <h3>Engineering Degree - Industrial Engineering & Logistics</h3>
            <p>ENSA Marrakech, Morocco. Strong foundation in systems thinking, operations, optimization, and technical coordination.</p>
          </div>
        </div>
      </div>
    </section>

    <section id="skills">
      <div class="section-header reveal">
        <div>
          <div class="eyebrow">03 - Technical Stack</div>
          <h2>Tools I use.</h2>
        </div>
        <p class="section-copy">
          Practical stack across DevOps, orchestration, observability, backend, frontend, mobile,
          databases, big data, cloud basics, ERP, and CRM.
        </p>
      </div>

      <div class="skills reveal" style="transition-delay: 100ms">
        <div class="skill-group">
          <h3>DevOps & CI/CD</h3>
          <ul>
            <li>Docker, Jenkins, GitHub Actions</li>
            <li>Argo CD, GitOps, Dependabot</li>
            <li>Trivy, SonarCloud, SOPS</li>
          </ul>
        </div>
        <div class="skill-group">
          <h3>Orchestration</h3>
          <ul>
            <li>Kubernetes, Minikube, Helm</li>
            <li>Ingress Nginx, RBAC</li>
            <li>Network Policies, SecurityContext</li>
          </ul>
        </div>
        <div class="skill-group">
          <h3>Observability</h3>
          <ul>
            <li>Prometheus, AlertManager</li>
            <li>Grafana, Loki, Promtail</li>
            <li>OpenTelemetry, Jaeger, Sentry</li>
          </ul>
        </div>
        <div class="skill-group">
          <h3>Engineering</h3>
          <ul>
            <li>Node.js, Express.js, Spring Boot</li>
            <li>React, Angular, TypeScript</li>
            <li>SwiftUI, Flutter, PostgreSQL</li>
          </ul>
        </div>
      </div>
    </section>

    <section id="contact">
      <div class="contact">
        <div class="reveal">
          <div class="eyebrow">04 - Contact</div>
          <h2>Let us build something reliable.</h2>
        </div>
        <div class="contact-list reveal" style="transition-delay: 100ms">
          <a class="contact-link" href="mailto:khafif.badr.fr@gmail.com">
            <span>Email</span>
            <strong>khafif.badr.fr@gmail.com</strong>
          </a>
          <a class="contact-link" href="tel:+212698277941">
            <span>Phone</span>
            <strong>+212 6 98 27 79 41</strong>
          </a>
          <a class="contact-link" href="https://github.com/Griffith-0-0" target="_blank" rel="noreferrer">
            <span>GitHub</span>
            <strong>Griffith-0-0</strong>
          </a>
          <a class="contact-link" href="https://www.linkedin.com/in/badr-khafif" target="_blank" rel="noreferrer">
            <span>LinkedIn</span>
            <strong>badr-khafif</strong>
          </a>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <span>© 2026 Badr Khafif</span>
    <span>Built for GitHub Pages</span>
  </footer>

  <script>
    const reveals = document.querySelectorAll(".reveal");
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("visible");
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12 });

    reveals.forEach((element) => observer.observe(element));
  </script>
</body>
</html>

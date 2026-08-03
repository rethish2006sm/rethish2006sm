<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>README · fullstack</title>
    <!-- Font Awesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" />
    <style>
        /* ── reset & base ── */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0b0d15;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
            display: flex;
            justify-content: center;
            padding: 2rem 1rem;
            min-height: 100vh;
            color: #e2e8f0;
        }

        .readme {
            max-width: 1100px;
            width: 100%;
            background: #11131f;
            border-radius: 2rem;
            padding: 2.5rem 2.8rem;
            box-shadow: 0 25px 60px -12px rgba(0, 0, 0, 0.8), inset 0 1px 0 rgba(255, 255, 255, 0.04);
            border: 1px solid rgba(255, 255, 255, 0.03);
            position: relative;
            overflow: hidden;
        }

        /* ── animated bg orbs ── */
        .readme::before {
            content: '';
            position: absolute;
            top: -30%;
            right: -20%;
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, rgba(99, 102, 241, 0.08) 0%, transparent 70%);
            border-radius: 50%;
            pointer-events: none;
            animation: orbFloat 18s ease-in-out infinite alternate;
            z-index: 0;
        }

        .readme::after {
            content: '';
            position: absolute;
            bottom: -30%;
            left: -20%;
            width: 500px;
            height: 500px;
            background: radial-gradient(circle, rgba(236, 72, 153, 0.06) 0%, transparent 70%);
            border-radius: 50%;
            pointer-events: none;
            animation: orbFloat 22s ease-in-out infinite alternate-reverse;
            z-index: 0;
        }

        @keyframes orbFloat {
            0% {
                transform: translate(0, 0) scale(1);
            }
            100% {
                transform: translate(40px, 30px) scale(1.2);
            }
        }

        /* ── scanline overlay ── */
        .scanline {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
            background: repeating-linear-gradient(0deg,
                    transparent,
                    transparent 2px,
                    rgba(0, 0, 0, 0.03) 2px,
                    rgba(0, 0, 0, 0.03) 4px);
        }

        /* ── all content sits above bg ── */
        .readme>*:not(.scanline) {
            position: relative;
            z-index: 2;
        }

        /* ── typography ── */
        h1,
        h2,
        h3 {
            font-weight: 600;
            letter-spacing: -0.02em;
        }

        a {
            color: #a5b4fc;
            text-decoration: none;
            transition: color 0.2s;
        }
        a:hover {
            color: #c7d2fe;
        }

        /* ── header / hero ── */
        .hero {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            gap: 0.6rem;
            padding-bottom: 2.5rem;
            border-bottom: 1px solid rgba(255, 255, 255, 0.04);
            margin-bottom: 2.5rem;
        }

        .hero-badge {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            background: rgba(99, 102, 241, 0.12);
            border: 1px solid rgba(99, 102, 241, 0.2);
            padding: 0.25rem 1rem 0.25rem 0.75rem;
            border-radius: 100px;
            font-size: 0.7rem;
            text-transform: uppercase;
            letter-spacing: 0.08em;
            color: #a5b4fc;
            font-weight: 500;
        }
        .hero-badge .dot {
            width: 7px;
            height: 7px;
            border-radius: 50%;
            background: #34d399;
            display: inline-block;
            animation: pulse-dot 1.8s ease-in-out infinite;
        }
        @keyframes pulse-dot {
            0%,
            100% {
                opacity: 1;
                transform: scale(1);
            }
            50% {
                opacity: 0.4;
                transform: scale(0.7);
            }
        }

        .hero h1 {
            font-size: 4.2rem;
            font-weight: 700;
            line-height: 1.1;
            background: linear-gradient(135deg, #e2e8f0 0%, #a5b4fc 50%, #f472b6 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: shimmer 6s ease-in-out infinite alternate;
            background-size: 200% 200%;
        }
        @keyframes shimmer {
            0% {
                background-position: 0% 50%;
            }
            100% {
                background-position: 100% 50%;
            }
        }

        .hero .glitch-line {
            font-size: 1.1rem;
            color: #94a3b8;
            display: flex;
            align-items: center;
            gap: 0.75rem;
            flex-wrap: wrap;
        }
        .hero .glitch-line .cursor {
            display: inline-block;
            width: 2px;
            height: 1.2rem;
            background: #a5b4fc;
            animation: blink 1s step-end infinite;
            margin-left: 2px;
        }
        @keyframes blink {
            0%,
            100% {
                opacity: 1;
            }
            50% {
                opacity: 0;
            }
        }

        .hero .typing-text {
            display: inline-block;
            overflow: hidden;
            white-space: nowrap;
            border-right: 2px solid #a5b4fc;
            animation: typing 3.5s steps(30) 1s forwards, blink-caret 0.75s step-end infinite;
            max-width: 0;
            color: #c7d2fe;
            font-weight: 400;
        }
        @keyframes typing {
            from {
                max-width: 0;
            }
            to {
                max-width: 34ch;
            }
        }
        @keyframes blink-caret {
            0%,
            100% {
                border-color: transparent;
            }
            50% {
                border-color: #a5b4fc;
            }
        }

        .hero-meta {
            display: flex;
            flex-wrap: wrap;
            gap: 1.8rem;
            margin-top: 0.5rem;
            font-size: 0.9rem;
            color: #64748b;
        }
        .hero-meta span i {
            margin-right: 0.4rem;
            color: #818cf8;
        }

        /* ── grid layout ── */
        .grid-2 {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            margin: 2.5rem 0;
        }

        @media (max-width: 780px) {
            .readme {
                padding: 1.5rem;
            }
            .hero h1 {
                font-size: 2.6rem;
            }
            .grid-2 {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }
        }

        /* ── cards ── */
        .card {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.04);
            border-radius: 1.4rem;
            padding: 1.8rem 2rem;
            transition: all 0.3s cubic-bezier(0.23, 1, 0.32, 1);
            backdrop-filter: blur(4px);
        }
        .card:hover {
            background: rgba(255, 255, 255, 0.04);
            border-color: rgba(165, 180, 252, 0.15);
            transform: translateY(-4px);
            box-shadow: 0 20px 40px -16px rgba(0, 0, 0, 0.6);
        }

        .card h3 {
            font-size: 1rem;
            text-transform: uppercase;
            letter-spacing: 0.06em;
            color: #818cf8;
            margin-bottom: 1.2rem;
            display: flex;
            align-items: center;
            gap: 0.6rem;
        }
        .card h3 i {
            font-size: 0.9rem;
        }

        /* ── tech tags ── */
        .tech-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.6rem;
        }
        .tech-tags span {
            background: rgba(165, 180, 252, 0.08);
            border: 1px solid rgba(165, 180, 252, 0.1);
            padding: 0.3rem 1rem;
            border-radius: 100px;
            font-size: 0.75rem;
            font-weight: 500;
            color: #c7d2fe;
            transition: all 0.2s;
            cursor: default;
        }
        .tech-tags span:hover {
            background: rgba(165, 180, 252, 0.18);
            border-color: rgba(165, 180, 252, 0.3);
            transform: scale(1.03);
        }

        /* ── stats bars ── */
        .stat-item {
            margin-bottom: 1rem;
        }
        .stat-item:last-child {
            margin-bottom: 0;
        }
        .stat-label {
            display: flex;
            justify-content: space-between;
            font-size: 0.85rem;
            color: #94a3b8;
            margin-bottom: 0.2rem;
        }
        .stat-bar {
            width: 100%;
            height: 6px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 100px;
            overflow: hidden;
        }
        .stat-bar .fill {
            height: 100%;
            border-radius: 100px;
            background: linear-gradient(90deg, #818cf8, #a78bfa);
            width: 0%;
            animation: fillBar 1.6s ease-out forwards;
        }
        .stat-bar .fill.green {
            background: linear-gradient(90deg, #34d399, #6ee7b7);
        }
        .stat-bar .fill.pink {
            background: linear-gradient(90deg, #f472b6, #f9a8d4);
        }
        .stat-bar .fill.orange {
            background: linear-gradient(90deg, #fb923c, #fbbf24);
        }
        .stat-bar .fill.cyan {
            background: linear-gradient(90deg, #22d3ee, #67e8f9);
        }

        @keyframes fillBar {
            from {
                width: 0%;
            }
            to {
                width: var(--target);
            }
        }

        /* ── project list ── */
        .project-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 0.7rem 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.03);
            transition: all 0.2s;
        }
        .project-item:last-child {
            border-bottom: none;
        }
        .project-item:hover {
            padding-left: 0.5rem;
        }
        .project-item .icon {
            width: 36px;
            height: 36px;
            border-radius: 10px;
            background: rgba(165, 180, 252, 0.08);
            display: flex;
            align-items: center;
            justify-content: center;
            color: #818cf8;
            font-size: 1rem;
            flex-shrink: 0;
        }
        .project-item .info {
            flex: 1;
        }
        .project-item .info .name {
            font-weight: 500;
            font-size: 0.95rem;
            color: #e2e8f0;
        }
        .project-item .info .desc {
            font-size: 0.8rem;
            color: #64748b;
        }
        .project-item .link {
            color: #64748b;
            transition: color 0.2s, transform 0.2s;
        }
        .project-item .link:hover {
            color: #a5b4fc;
            transform: translateX(3px);
        }

        /* ── social row ── */
        .social-row {
            display: flex;
            flex-wrap: wrap;
            gap: 1.2rem;
            margin-top: 0.8rem;
        }
        .social-row a {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.4rem 1.2rem 0.4rem 1rem;
            border-radius: 100px;
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.05);
            font-size: 0.85rem;
            color: #94a3b8;
            transition: all 0.25s;
        }
        .social-row a:hover {
            background: rgba(165, 180, 252, 0.08);
            border-color: rgba(165, 180, 252, 0.2);
            color: #e2e8f0;
            transform: translateY(-2px);
        }
        .social-row a i {
            font-size: 1rem;
            color: #818cf8;
        }

        /* ── footer ── */
        .footer {
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.04);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
            font-size: 0.8rem;
            color: #475569;
        }
        .footer .badge-group {
            display: flex;
            gap: 0.8rem;
            flex-wrap: wrap;
        }
        .footer .badge-group span {
            background: rgba(255, 255, 255, 0.03);
            padding: 0.2rem 1rem;
            border-radius: 100px;
            border: 1px solid rgba(255, 255, 255, 0.04);
        }
        .footer .heart {
            color: #f472b6;
            animation: heartBeat 1.8s ease-in-out infinite;
            display: inline-block;
        }
        @keyframes heartBeat {
            0%,
            100% {
                transform: scale(1);
            }
            15% {
                transform: scale(1.25);
            }
            30% {
                transform: scale(1);
            }
            45% {
                transform: scale(1.15);
            }
            60% {
                transform: scale(1);
            }
        }

        /* ── ascii art (terminal vibe) ── */
        .ascii {
            font-family: 'Courier New', monospace;
            font-size: 0.55rem;
            line-height: 1.3;
            color: #334155;
            white-space: pre;
            margin: 1rem 0 0.2rem;
            opacity: 0.4;
            user-select: none;
            letter-spacing: 0.04em;
            text-align: center;
        }

        /* ── scrollable code block ── */
        .code-snip {
            background: rgba(0, 0, 0, 0.4);
            border-radius: 0.8rem;
            padding: 1rem 1.2rem;
            font-family: 'Fira Code', 'Courier New', monospace;
            font-size: 0.75rem;
            color: #94a3b8;
            overflow-x: auto;
            border: 1px solid rgba(255, 255, 255, 0.04);
            margin: 0.8rem 0;
        }
        .code-snip .kw {
            color: #a78bfa;
        }
        .code-snip .fn {
            color: #60a5fa;
        }
        .code-snip .str {
            color: #34d399;
        }
        .code-snip .cmt {
            color: #475569;
        }

        /* ── responsive tweaks ── */
        @media (max-width: 480px) {
            .hero h1 {
                font-size: 2rem;
            }
            .hero .glitch-line {
                font-size: 0.9rem;
            }
            .card {
                padding: 1.2rem;
            }
            .footer {
                flex-direction: column;
                align-items: flex-start;
            }
        }
    </style>
</head>
<body>

    <div class="readme">

        <!-- scanline effect -->
        <div class="scanline"></div>

        <!-- ──── HERO ──── -->
        <header class="hero">
            <div class="hero-badge">
                <span class="dot"></span>
                <span>open to collaborate · fullstack</span>
            </div>

            <h1>
                &lt;dev /&gt; <span style="color:#818cf8; -webkit-text-fill-color: initial;">⚡</span>
            </h1>

            <div class="glitch-line">
                <span class="typing-text">$&nbsp; building digital experiences · full‑stack</span>
                <span class="cursor"></span>
            </div>

            <div class="hero-meta">
                <span><i class="fas fa-map-pin"></i> remote · UTC+1</span>
                <span><i class="fas fa-code"></i> 8+ yrs craft</span>
                <span><i class="fas fa-rocket"></i> 12 projects shipped</span>
            </div>
        </header>

        <!-- ──── GRID 2 ──── -->
        <div class="grid-2">

            <!-- ── left: tech stack ── -->
            <div class="card">
                <h3><i class="fas fa-cube"></i> stack</h3>
                <div class="tech-tags">
                    <span>TypeScript</span>
                    <span>React</span>
                    <span>Next.js</span>
                    <span>Node.js</span>
                    <span>NestJS</span>
                    <span>GraphQL</span>
                    <span>Prisma</span>
                    <span>PostgreSQL</span>
                    <span>Redis</span>
                    <span>Docker</span>
                    <span>K8s</span>
                    <span>AWS</span>
                    <span>Tailwind</span>
                    <span>Go</span>
                    <span>Python</span>
                </div>

                <!-- ascii art -->
                <div class="ascii">
                    ════════════════════════════════
                    ║  █▀▀ █▀█ █▀▄ █▀▀ █▀█ █▀▀  ║
                    ║  █▄▄ █▄█ █▄▀ ██▄ █▀▄ ██▄  ║
                    ════════════════════════════════
                </div>
            </div>

            <!-- ── right: stats ── -->
            <div class="card">
                <h3><i class="fas fa-chart-line"></i> proficiency</h3>
                <div class="stat-item">
                    <div class="stat-label"><span>Frontend</span><span>92%</span></div>
                    <div class="stat-bar"><div class="fill" style="--target:92%;"></div></div>
                </div>
                <div class="stat-item">
                    <div class="stat-label"><span>Backend</span><span>88%</span></div>
                    <div class="stat-bar"><div class="fill green" style="--target:88%;"></div></div>
                </div>
                <div class="stat-item">
                    <div class="stat-label"><span>DevOps</span><span>76%</span></div>
                    <div class="stat-bar"><div class="fill pink" style="--target:76%;"></div></div>
                </div>
                <div class="stat-item">
                    <div class="stat-label"><span>UI/UX</span><span>68%</span></div>
                    <div class="stat-bar"><div class="fill orange" style="--target:68%;"></div></div>
                </div>
                <div class="stat-item">
                    <div class="stat-label"><span>System Design</span><span>81%</span></div>
                    <div class="stat-bar"><div class="fill cyan" style="--target:81%;"></div></div>
                </div>
            </div>

            <!-- ── left: projects ── -->
            <div class="card">
                <h3><i class="fas fa-folder-open"></i> featured</h3>
                <div class="project-item">
                    <div class="icon"><i class="fas fa-cloud"></i></div>
                    <div class="info">
                        <div class="name">Nimbus · realtime sync</div>
                        <div class="desc">CRDT + WebRTC + React</div>
                    </div>
                    <a href="#" class="link"><i class="fas fa-arrow-right"></i></a>
                </div>
                <div class="project-item">
                    <div class="icon"><i class="fas fa-robot"></i></div>
                    <div class="info">
                        <div class="name">Hermes · AI gateway</div>
                        <div class="desc">NestJS · GraphQL · LLM orchestration</div>
                    </div>
                    <a href="#" class="link"><i class="fas fa-arrow-right"></i></a>
                </div>
                <div class="project-item">
                    <div class="icon"><i class="fas fa-chart-pie"></i></div>
                    <div class="info">
                        <div class="name">Vizion · analytics dash</div>
                        <div class="desc">Next.js · D3 · ClickHouse</div>
                    </div>
                    <a href="#" class="link"><i class="fas fa-arrow-right"></i></a>
                </div>
                <div class="project-item">
                    <div class="icon"><i class="fas fa-cube"></i></div>
                    <div class="info">
                        <div class="name">Orbit · monorepo toolkit</div>
                        <div class="desc">Turborepo · pnpm · shared libs</div>
                    </div>
                    <a href="#" class="link"><i class="fas fa-arrow-right"></i></a>
                </div>
            </div>

            <!-- ── right: snippet & social ── -->
            <div class="card">
                <h3><i class="fas fa-terminal"></i> dev pulse</h3>
                <div class="code-snip">
                    <span class="cmt">// ⚡ daily driver</span><br />
                    <span class="kw">const</span> <span class="fn">build</span> = <span class="kw">async</span> () => {<br />
                    &nbsp;&nbsp;<span class="kw">await</span> <span class="fn">compose</span>(<span class="str">'services'</span>);<br />
                    &nbsp;&nbsp;<span class="kw">return</span> <span class="fn">deploy</span>({ <span class="str">'env'</span>: <span class="str">'prod'</span> });<br />
                    };
                </div>
                <div class="social-row">
                    <a href="#"><i class="fab fa-github"></i> github</a>
                    <a href="#"><i class="fab fa-linkedin-in"></i> linkedin</a>
                    <a href="#"><i class="fab fa-x-twitter"></i> x</a>
                    <a href="#"><i class="fas fa-envelope"></i> email</a>
                    <a href="#"><i class="fab fa-dev"></i> dev.to</a>
                </div>
            </div>

        </div>

        <!-- ──── FOOTER ──── -->
        <div class="footer">
            <div class="badge-group">
                <span><i class="far fa-calendar-alt"></i> 2026 · v3.2</span>
                <span><i class="fas fa-code-branch"></i> main</span>
                <span><i class="fas fa-check-circle" style="color:#34d399;"></i> 12/12 checks</span>
            </div>
            <div>
                crafted with <span class="heart">❤</span> · full‑stack <span style="color:#818cf8;">✦</span> infinite loop
            </div>
        </div>

    </div>

</body>
</html>

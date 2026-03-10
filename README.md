
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>ЧЁРТОВА СТУДИЯ</title>
  <style>
    :root{
      --bg:#040912;
      --card:rgba(15,24,37,.82);
      --card-2:rgba(10,18,29,.92);
      --line:rgba(255,255,255,.08);
      --text:#f4f7fb;
      --muted:#9fb1c4;
      --blue:#2485ff;
      --blue-2:#63b0ff;
      --shadow:0 24px 60px rgba(0,0,0,.40);
      --container:1440px;
    }

    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{
      margin:0;
      font-family:Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      color:var(--text);
      background:
        radial-gradient(circle at 12% 18%, rgba(36,133,255,.16), transparent 24%),
        radial-gradient(circle at 78% 28%, rgba(36,133,255,.10), transparent 20%),
        radial-gradient(circle at 50% 100%, rgba(36,133,255,.06), transparent 25%),
        linear-gradient(180deg, #03070f 0%, #06111d 45%, #03070d 100%);
      overflow-x:hidden;
    }

    body::before{
      content:"";
      position:fixed;
      inset:0;
      pointer-events:none;
      opacity:.45;
      background-image:
        radial-gradient(circle, rgba(255,255,255,.055) 0 1px, transparent 1px),
        radial-gradient(circle, rgba(255,255,255,.035) 0 1px, transparent 1px);
      background-size:200px 200px, 320px 320px;
      background-position:0 0, 100px 120px;
      animation:bgDrift 16s ease-in-out infinite;
    }

    @keyframes bgDrift{
      0%,100%{transform:translateY(0)}
      50%{transform:translateY(-14px)}
    }

    a{text-decoration:none;color:inherit}
    button{font:inherit}
    img{max-width:100%;display:block}

    .container{width:min(var(--container), calc(100% - 40px)); margin:0 auto}

    @media (min-width:1800px){
      .container{width:min(1680px, calc(100% - 72px));}
    }

    .site-header{
      position:sticky;
      top:0;
      z-index:80;
      width:100%;
      backdrop-filter:blur(14px);
      background:rgba(4,10,18,.55);
      border:none;
      box-shadow:none;
    }

    .nav{
      min-height:78px;
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:24px;
      border:none;
      box-shadow:none;
    }

    .brand{font-size:34px; font-weight:800; letter-spacing:-.05em}

    .nav-links{display:flex; align-items:center; gap:34px; color:#dce7f2}
    .nav-links a{position:relative; font-size:16px}
    .nav-links a::after{
      content:"";
      position:absolute;
      left:0;
      bottom:-8px;
      width:0;
      height:2px;
      border-radius:999px;
      background:linear-gradient(90deg,var(--blue-2),transparent);
      transition:width .25s ease;
    }
    .nav-links a:hover::after{width:100%}

    .cta, .ghost-btn, .project-link{
      border:none;
      cursor:pointer;
      transition:transform .2s ease, box-shadow .2s ease, background .2s ease, border-color .2s ease, opacity .2s ease;
      font:inherit;
    }

    .cta{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      height:52px;
      padding:0 28px;
      border-radius:14px;
      font-weight:700;
      color:#fff;
      background:linear-gradient(180deg,var(--blue-2),var(--blue));
      border:1px solid rgba(255,255,255,.09);
      box-shadow:0 14px 34px rgba(36,133,255,.24);
      white-space:nowrap;
    }

    .project-link, .ghost-btn{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      min-height:46px;
      padding:0 18px;
      border-radius:14px;
      font-weight:700;
      white-space:nowrap;
      background:rgba(255,255,255,.05);
      color:#d9e8ff;
      border:1px solid rgba(255,255,255,.08);
    }

    .cta:hover, .ghost-btn:hover, .project-link:hover{transform:translateY(-2px)}

    .hero{
      min-height:760px;
      display:grid;
      grid-template-columns:1.08fr .92fr;
      gap:46px;
      align-items:center;
      padding:82px 0 88px;
      position:relative;
    }

    .hero-copy{position:relative; z-index:2}
    h1{margin:0 0 16px; max-width:760px; font-size:74px; line-height:1.01; letter-spacing:-.06em}
    .lead{margin:0 0 28px; max-width:780px; font-size:29px; line-height:1.28; color:#edf3fb}

    .stats{
      width:min(740px,100%);
      display:flex;
      overflow:hidden;
      border-radius:22px;
      background:rgba(17,27,39,.76);
      border:1px solid rgba(255,255,255,.08);
      box-shadow:var(--shadow);
      margin:0 0 28px;
    }
    .stat{flex:1; padding:22px 26px 20px; border-right:1px solid rgba(255,255,255,.06)}
    .stat:last-child{border-right:none}
    .stat-label{margin-bottom:10px; font-size:13px; text-transform:uppercase; letter-spacing:.10em; color:#90a4b8}
    .stat-value{margin-bottom:10px; font-size:62px; line-height:1; font-weight:800; letter-spacing:-.06em; color:var(--blue-2); text-shadow:0 0 24px rgba(36,133,255,.22)}
    .stat-sub{font-size:21px; color:#e8eef7; line-height:1.22}

    .hero-visual{position:relative; height:620px; display:flex; align-items:center; justify-content:center}
    .ring{
      width:420px;
      height:420px;
      border-radius:50%;
      border:4px solid rgba(255,255,255,.76);
      box-shadow:0 0 40px rgba(255,255,255,.18), inset 0 0 34px rgba(255,255,255,.04);
      animation:ringPulse 4.6s ease-in-out infinite;
    }
    .soft-orb{position:absolute; border-radius:50%; filter:blur(12px); background:radial-gradient(circle, rgba(36,133,255,.34), transparent 68%); animation:orbFloat 7s ease-in-out infinite}
    .orb-1{width:180px; height:180px; top:100px; left:80px}
    .orb-2{width:140px; height:140px; right:90px; bottom:120px; animation-delay:-2.6s}
    .app{
      position:absolute;
      width:214px;
      height:214px;
      border-radius:34px;
      display:flex;
      align-items:center;
      justify-content:center;
      border:2px solid rgba(255,255,255,.16);
      background:linear-gradient(180deg,#1b2a8b,#0b0a84);
      box-shadow:0 28px 42px rgba(0,0,0,.34), 0 0 28px rgba(36,133,255,.10);
      overflow:hidden;
    }
    .app::before{
      content:"";
      position:absolute;
      inset:0;
      background:linear-gradient(135deg, rgba(255,255,255,.12), transparent 40%, transparent 60%, rgba(255,255,255,.08));
      transform:translateX(-100%);
      animation:shine 4.8s linear infinite;
    }
    .app.ae{top:88px; left:78px; animation:float1 5s ease-in-out infinite}
    .app.pr{bottom:96px; right:84px; animation:float2 5.8s ease-in-out infinite}
    .app span{position:relative; z-index:1; font-size:108px; font-weight:800; letter-spacing:-.06em; color:#a8a8ff}

    @keyframes shine{0%{transform:translateX(-120%)} 20%,100%{transform:translateX(120%)}}
    @keyframes ringPulse{0%,100%{transform:scale(1)} 50%{transform:scale(1.03)}}
    @keyframes orbFloat{0%,100%{transform:translateY(0)} 50%{transform:translateY(-16px)}}
    @keyframes float1{0%,100%{transform:translateY(0) rotate(-2deg)} 50%{transform:translateY(-14px) rotate(2deg)}}
    @keyframes float2{0%,100%{transform:translateY(0) rotate(2deg)} 50%{transform:translateY(14px) rotate(-2deg)}}

    .section{padding:36px 0}
    .section-title{margin:0 0 20px; font-size:46px; letter-spacing:-.04em}

    .projects{display:grid; grid-template-columns:repeat(2,1fr); gap:24px}

    .project-card, .about-card, .review-card, .modal-panel{
      position:relative;
      background:var(--card);
      border:1px solid var(--line);
      border-radius:26px;
      box-shadow:var(--shadow);
      overflow:hidden;
    }

    .project-card, .review-card{transition:transform .28s ease, box-shadow .28s ease, border-color .28s ease; isolation:isolate}
    .project-card::before, .review-card::before{
      content:"";
      position:absolute;
      inset:-1px;
      border-radius:inherit;
      padding:1px;
      background:linear-gradient(135deg, rgba(99,176,255,0), rgba(99,176,255,.68), rgba(99,176,255,0));
      -webkit-mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
      -webkit-mask-composite:xor;
      mask-composite:exclude;
      opacity:0;
      transition:opacity .28s ease;
      pointer-events:none;
    }
    .project-card:hover, .review-card:hover{transform:translateY(-8px); box-shadow:0 28px 68px rgba(0,0,0,.44), 0 0 34px rgba(36,133,255,.12); border-color:rgba(99,176,255,.22)}
    .project-card:hover::before, .review-card:hover::before{opacity:1}

    .project-meta{padding:16px 18px 0; color:#8ea1b3; font-size:14px; text-transform:uppercase; letter-spacing:.06em}
    .project-cover{
      margin:12px 12px 0;
      aspect-ratio:16/9;
      border-radius:20px;
      overflow:hidden;
      position:relative;
      background:linear-gradient(135deg, #121d2c, #1a3353 60%, #10243c);
      cursor:pointer;
      background-size:cover;
      background-position:center;
    }
    .project-cover::before{
      content:"";
      position:absolute;
      inset:0;
      background:linear-gradient(180deg, rgba(0,0,0,.06), rgba(0,0,0,.20));
      pointer-events:none;
    }

    .cover-inner{position:relative; z-index:1; width:100%; height:100%; padding:24px}
    .cover-badge{
      position:absolute;
      top:16px;
      left:16px;
      display:flex;
      align-items:center;
      gap:6px;
      padding:6px 10px;
      font-size:12px;
      font-weight:600;
      color:#fff;
      background:rgba(0,0,0,0.35);
      backdrop-filter:blur(8px);
      border-radius:8px;
      box-shadow:0 6px 18px rgba(0,0,0,0.25);
    }
    .cover-icon{
      position:absolute;
      left:50%;
      top:50%;
      transform:translate(-50%,-50%);
      width:76px;
      height:76px;
      border-radius:22px;
      background:rgba(7,15,26,.56);
      border:1px solid rgba(255,255,255,.12);
      display:flex;
      align-items:center;
      justify-content:center;
      box-shadow:0 18px 34px rgba(0,0,0,.24);
    }
    .cover-icon svg{width:34px; height:34px; fill:white; opacity:.95}

    .project-body{padding:18px}
    .project-title{margin:0 0 12px; min-height:80px; font-size:24px; line-height:1.18; letter-spacing:-.03em}
    .project-desc{margin:0 0 16px; color:#d5e0ea; font-size:16px; line-height:1.45}
    .project-actions{display:flex; gap:12px; flex-wrap:wrap; align-items:center}
    .chip-row{display:flex; gap:10px; flex-wrap:wrap; margin-top:16px}
    .chip{padding:10px 14px; border-radius:12px; font-size:14px; color:#c8d5e3; background:rgba(255,255,255,.04); border:1px solid rgba(255,255,255,.06)}

    .about-card{max-width:980px; padding:34px}
    .about-card::after{content:""; position:absolute; top:-80px; right:-80px; width:220px; height:220px; border-radius:50%; background:radial-gradient(circle, rgba(36,133,255,.16), transparent 66%); pointer-events:none}
    .about-card h3{margin:0 0 16px; font-size:40px; letter-spacing:-.04em}
    .about-card p{margin:0 0 16px; color:#d8e1ea; font-size:22px; line-height:1.45}

    .reviews{display:grid; grid-template-columns:repeat(3,1fr); gap:20px}
    .review-card{padding:22px; background:var(--card-2)}
    .review-label{margin-bottom:14px; color:#96a3b1; font-size:14px; text-transform:uppercase}
    .review-head{display:flex; gap:16px; align-items:flex-start}
    .review-avatar{position:relative; width:62px; height:62px; flex:0 0 62px; border-radius:50%; border:1px solid rgba(255,255,255,.08); background:linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.02)); box-shadow:inset 0 0 22px rgba(255,255,255,.03), 0 0 20px rgba(36,133,255,.08)}
    .review-avatar::before{content:""; position:absolute; left:50%; top:16px; transform:translateX(-50%); width:16px; height:16px; border-radius:50%; background:#d7e3ee}
    .review-avatar::after{content:""; position:absolute; left:50%; bottom:10px; transform:translateX(-50%); width:30px; height:18px; background:#d7e3ee; border-radius:18px 18px 12px 12px}
    .review-name{margin:0 0 6px; font-size:20px; font-weight:700}
    .review-text{margin:0; color:#e3e8ef; font-size:16px; line-height:1.35}

    .footer{margin-top:54px; border-top:1px solid rgba(255,255,255,.06); background:rgba(2,8,14,.55)}
    .footer-inner{min-height:92px; display:flex; align-items:center; justify-content:space-between; gap:20px; flex-wrap:wrap; color:#c6d1dd}
    .footer-links{display:flex; gap:20px; flex-wrap:wrap}

    .modal{
      position:fixed;
      inset:0;
      z-index:120;
      display:grid;
      place-items:center;
      padding:24px;
      opacity:0;
      pointer-events:none;
      transition:opacity .22s ease;
      overflow-y:auto;
      overscroll-behavior:contain;
      -webkit-overflow-scrolling:touch;
    }
    .modal.open{opacity:1; pointer-events:auto}
    .modal-backdrop{position:absolute; inset:0; background:rgba(1,5,10,.70); backdrop-filter:blur(10px)}
    .modal-panel{
      position:relative;
      z-index:1;
      width:min(860px, 100%);
      padding:22px;
      transform:translateY(18px) scale(.98);
      transition:transform .24s ease;
      background:rgba(10,16,25,.95);
      max-height:min(860px, calc(100dvh - 48px));
      overflow-y:auto;
      -webkit-overflow-scrolling:touch;
    }
    .modal.open .modal-panel{transform:translateY(0) scale(1)}
    .modal-header{display:flex; justify-content:space-between; align-items:flex-start; gap:16px; margin-bottom:18px; position:static; background:transparent}
    .modal-title{margin:0; font-size:34px; line-height:1.05; letter-spacing:-.04em}
    .modal-sub{margin:8px 0 0; color:#aebdcb; font-size:16px}

    .close-btn{
      width:44px;
      height:44px;
      border-radius:14px;
      border:1px solid rgba(255,255,255,.08);
      background:rgba(255,255,255,.04);
      cursor:pointer;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:0;
      flex:0 0 44px;
      position:relative;
      font-size:0;
      line-height:0;
      color:transparent;
    }
    .close-btn::before{
      content:"×";
      color:#fff;
      font-size:28px;
      line-height:1;
      display:block;
      transform:translateY(-1px);
    }

    .modal-grid{display:grid; grid-template-columns:1.05fr .95fr; gap:20px}
    .modal-cover{
      min-height:320px;
      border-radius:22px;
      border:1px solid rgba(255,255,255,.08);
      overflow:hidden;
      position:relative;
      background-size:cover;
      background-position:center;
    }
    .modal-cover::before{
      content:"";
      position:absolute;
      inset:0;
      background:inherit;
      background-size:cover;
      background-position:center;
      transform:scale(1);
      opacity:1;
    }
    .modal-cover::after{
      content:"";
      position:absolute;
      left:0;
      right:0;
      bottom:0;
      height:140px;
      background:linear-gradient(to top, rgba(0,0,0,.55), rgba(0,0,0,0));
      pointer-events:none;
    }
    .modal-cover .cover-inner{position:relative; z-index:1; padding:28px; height:100%}
    .modal-content{border-radius:22px; background:rgba(255,255,255,.03); border:1px solid rgba(255,255,255,.06); padding:20px}
    .modal-content h4{margin:0 0 12px; font-size:20px}
    .modal-content p{margin:0 0 14px; color:#d6e0ea; line-height:1.52}
    .modal-list{margin:0; padding-left:18px; color:#d8e2ed; line-height:1.55}
    .modal-actions{display:flex; gap:12px; flex-wrap:wrap; margin-top:18px}

    .reveal{opacity:0; transform:translateY(20px); transition:opacity .65s ease, transform .65s ease}
    .reveal.visible{opacity:1; transform:translateY(0)}

    @media (max-width:1180px){
      h1{font-size:58px}
      .lead{font-size:25px}
      .stat-value{font-size:52px}
      .stat-sub{font-size:19px}
      .reviews{grid-template-columns:1fr}
    }

    @media (max-width:980px){
      .nav{min-height:70px}
      .nav-links{display:none}
      .hero{grid-template-columns:1fr; min-height:auto; padding-top:42px}
      .hero-visual{height:420px}
      .ring{width:290px; height:290px}
      .app{width:156px; height:156px}
      .app span{font-size:78px}
      .app.ae{top:36px; left:calc(50% - 150px)}
      .app.pr{bottom:42px; right:calc(50% - 150px)}
      .projects{grid-template-columns:1fr}
      .modal{place-items:start center; padding:16px}
      .modal-panel{width:100%; max-height:calc(100dvh - 32px); margin-top:max(0px, env(safe-area-inset-top))}
      .modal-grid{grid-template-columns:1fr}
      .modal-cover{min-height:260px}
    }

    @media (max-width:640px){
      .container{width:min(var(--container), calc(100% - 26px))}
      .brand{font-size:22px}
      .cta{height:46px; padding:0 18px}
      h1{font-size:44px}
      .lead{font-size:19px}
      .stats{flex-direction:column}
      .stat{border-right:none; border-bottom:1px solid rgba(255,255,255,.07)}
      .stat:last-child{border-bottom:none}
      .stat-value{font-size:44px}
      .stat-sub{font-size:18px}
      .section-title{font-size:34px}
      .about-card p{font-size:18px}
      .about-card h3{font-size:32px}
      .project-title{min-height:auto; font-size:22px}
      .project-actions{flex-direction:column; align-items:stretch}
      .project-actions .project-link, .project-actions .ghost-btn{width:100%}
      .modal{padding:max(10px, env(safe-area-inset-top)) 10px max(10px, env(safe-area-inset-bottom))}
      .modal-panel{padding:14px; max-height:calc(100dvh - max(12px, env(safe-area-inset-top)) - max(12px, env(safe-area-inset-bottom))); border-radius:20px}
      .modal-header{margin-bottom:14px}
      .modal-title{font-size:24px}
      .modal-sub{font-size:14px; line-height:1.4}
      .modal-cover{min-height:220px}
      .modal-content{padding:16px}
      .modal-content p, .modal-list{font-size:15px; line-height:1.5}
      .modal-actions{flex-direction:column}
      .modal-actions .cta, .modal-actions .ghost-btn{width:100%}
    }
  </style>
</head>
<body>
  <header class="site-header">
    <div class="container nav">
      <a href="#top" class="brand">ЧЁРТОВА СТУДИЯ</a>
      <nav class="nav-links">
        <a href="#works">Работы</a>
        <a href="#about">Обо мне</a>
        <a href="#reviews">Отзывы</a>
      </nav>
      <a class="cta" href="https://t.me/ch8rti" target="_blank" rel="noopener">Telegram</a>
    </div>
  </header>

  <main id="top" class="container">
    <section class="hero reveal">
      <div class="hero-copy">
        <h1>Привет, я Влад — видеомонтажёр.</h1>
        <p class="lead">Специализируюсь на монтаже горизонтальных видео с анимациями и motion-графикой в Adobe Premiere Pro и Adobe After Effects.</p>

        <div class="stats">
          <div class="stat">
            <div class="stat-label">навыки</div>
            <div class="stat-value">Ae</div>
            <div class="stat-sub">motion-графика и анимации</div>
          </div>
          <div class="stat">
            <div class="stat-label">монтаж</div>
            <div class="stat-value">Pr</div>
            <div class="stat-sub">качественный монтаж роликов</div>
          </div>
        </div>

        <a class="cta" href="https://t.me/ch8rti" target="_blank" rel="noopener">Заказать монтаж</a>
      </div>

      <div class="hero-visual" aria-hidden="true">
        <div class="soft-orb orb-1"></div>
        <div class="soft-orb orb-2"></div>
        <div class="ring"></div>
        <div class="app ae"><span>Ae</span></div>
        <div class="app pr"><span>Pr</span></div>
      </div>
    </section>

    <section id="works" class="section reveal">
      <h2 class="section-title">Горизонтальные видео</h2>
      <div class="projects">
        <article class="project-card">
          <div class="project-meta">проект №1</div>
          <div class="project-cover open-project" data-project="memory" style="background-image:url('https://img.youtube.com/vi/d7Ow-mqDBMg/maxresdefault.jpg');">
            <div class="cover-inner">
              <div class="cover-badge">▶ YouTube</div>
              <div class="cover-icon" aria-hidden="true">
                <svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"></path></svg>
              </div>
            </div>
          </div>
          <div class="project-body">
            <h3 class="project-title">Я создал систему, чтобы ЗАПОМИНАТЬ ВСЁ быстро</h3>
            <p class="project-desc">Динамичный монтаж с акцентом на удержание внимания, чистую структуру, крупные акценты и понятную подачу мысли.</p>
            <div class="project-actions">
              <button class="project-link open-project" data-project="memory">Открыть кейс</button>
              <a class="ghost-btn" href="https://www.youtube.com/watch?v=d7Ow-mqDBMg&t=2s" target="_blank" rel="noopener">Полное видео</a>
            </div>
            <div class="chip-row">
              <div class="chip">24+ тыс. просмотров</div>
              <div class="chip">22.7+ тыс. подписчиков</div>
              <div class="chip">монтаж + анимации</div>
            </div>
          </div>
        </article>

        <article class="project-card">
          <div class="project-meta">проект №2</div>
          <div class="project-cover open-project" data-project="battle" style="background-image:url('https://img.youtube.com/vi/ExHY8cCCz_g/maxresdefault.jpg');">
            <div class="cover-inner">
              <div class="cover-badge">▶ YouTube</div>
              <div class="cover-icon" aria-hidden="true">
                <svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"></path></svg>
              </div>
            </div>
          </div>
          <div class="project-body">
            <h3 class="project-title">15 ЗАВОЕВАТЕЛЕЙ БОРЮТСЯ ЗА $200,000,000!, БИТВА СИЛЬНЕЙШИХ!...</h3>
            <p class="project-desc">Монтаж с быстрым темпом, напряжением, эмоциональными акцентами и визуальными элементами, которые усиливают вовлечение.</p>
            <div class="project-actions">
              <button class="project-link open-project" data-project="battle">Открыть кейс</button>
              <a class="ghost-btn" href="https://www.youtube.com/watch?v=ExHY8cCCz_g&t=57s" target="_blank" rel="noopener">Полное видео</a>
            </div>
            <div class="chip-row">
              <div class="chip">16+ тыс. просмотров</div>
              <div class="chip">180+ тыс. подписчиков</div>
              <div class="chip">motion-графика</div>
            </div>
          </div>
        </article>
      </div>
    </section>

    <section id="about" class="section reveal">
      <h2 class="section-title">Обо мне</h2>
      <div class="about-card">
        <h3>Влад, 19 лет</h3>
        <p>Создаю динамичные ролики с современной motion-графикой, анимациями и эффектами, которые удерживают внимание зрителя и делают видео более качественным и интересным.</p>
        <p>У меня есть опыт монтажа разных форматов видео, но сейчас я специализируюсь именно на горизонтальных роликах для YouTube и других платформ.</p>
        <p>Если вам нужен качественный и современный монтаж — буду рад поработать с вашим проектом.</p>
        <a class="cta" href="https://t.me/ch8rti" target="_blank" rel="noopener">Заказать монтаж</a>
      </div>
    </section>

    <section id="reviews" class="section reveal">
      <h2 class="section-title">Отзывы</h2>
      <div class="reviews">
        <article class="review-card">
          <div class="review-label">отзыв №1</div>
          <div class="review-head">
            <div class="review-avatar" aria-hidden="true"></div>
            <div>
              <h3 class="review-name">Максим</h3>
              <p class="review-text">Быстро сделал монтаж, результат именно такой, как и ожидал. Без проблем вносит правки, работать комфортно. Остался доволен.</p>
            </div>
          </div>
        </article>
        <article class="review-card">
          <div class="review-label">отзыв №2</div>
          <div class="review-head">
            <div class="review-avatar" aria-hidden="true"></div>
            <div>
              <h3 class="review-name">Алексей</h3>
              <p class="review-text">Заказывал несколько раз монтаж видео, всё сделано на высоком уровне. Работает быстро и с полной отдачей. Остался доволен.</p>
            </div>
          </div>
        </article>
        <article class="review-card">
          <div class="review-label">отзыв №3</div>
          <div class="review-head">
            <div class="review-avatar" aria-hidden="true"></div>
            <div>
              <h3 class="review-name">Даниил</h3>
              <p class="review-text">Качественно выполнил работу, правильно понял ТЗ, без проблем внёс мелкие правки и в принципе комфортно работать. Советую к работе.</p>
            </div>
          </div>
        </article>
      </div>
    </section>
  </main>

  <footer class="footer">
    <div class="container footer-inner">
      <div>Портфолио Влада</div>
      <div class="footer-links">
        <a href="#works">Работы</a>
        <a href="#about">Обо мне</a>
        <a href="#reviews">Отзывы</a>
        <a href="https://t.me/ch8rti" target="_blank" rel="noopener">Telegram</a>
      </div>
    </div>
  </footer>

  <div class="modal" id="projectModal" aria-hidden="true">
    <div class="modal-backdrop"></div>
    <div class="modal-panel">
      <div class="modal-header">
        <div>
          <h3 class="modal-title" id="modalTitle"></h3>
          <p class="modal-sub" id="modalSubtitle"></p>
        </div>
        <button class="close-btn" id="closeModal" aria-label="Закрыть"></button>
      </div>
      <div class="modal-grid">
        <div class="modal-cover" id="modalCover"></div>
        <div class="modal-content">
          <h4>Что сделано в проекте</h4>
          <p id="modalDescription"></p>
          <h4>Сильные стороны</h4>
          <ul class="modal-list" id="modalList"></ul>
          <div class="modal-actions">
            <a class="cta" id="modalYoutube" target="_blank" rel="noopener">Смотреть полное видео</a>
            <a class="ghost-btn" href="https://t.me/ch8rti" target="_blank" rel="noopener">Заказать похожий монтаж</a>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script>
    const projectData = {
      memory: {
        title: 'Я создал систему, чтобы ЗАПОМИНАТЬ ВСЁ быстро',
        subtitle: 'Образовательный ролик / удержание внимания / чистая структура',
        youtube: 'https://www.youtube.com/watch?v=d7Ow-mqDBMg&t=2s',
        description: 'В этом проекте акцент сделан на динамичный ритм, читаемую подачу, усиление смысловых моментов и аккуратную motion-графику, которая помогает зрителю не терять фокус.',
        coverStyle: "background-image:url('https://img.youtube.com/vi/d7Ow-mqDBMg/maxresdefault.jpg');",
        cover: `
          <div class="cover-inner">
            <div class="cover-badge">Образовательный формат</div>
            <div class="cover-icon" aria-hidden="true">
              <svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"></path></svg>
            </div>
          </div>
        `,
        list: [
          'плавная структура повествования без провисаний',
          'визуальные акценты на ключевых мыслях',
          'динамичный монтаж и анимации для удержания внимания',
          'оформление под YouTube и образовательный контент'
        ]
      },
      battle: {
        title: '15 ЗАВОЕВАТЕЛЕЙ БОРЮТСЯ ЗА $200,000,000!, БИТВА СИЛЬНЕЙШИХ!...',
        subtitle: 'Игровой ролик / эмоции / напряжение / скорость',
        youtube: 'https://www.youtube.com/watch?v=ExHY8cCCz_g&t=57s',
        description: 'Этот проект построен на быстром темпе, визуальном напряжении и сильных эмоциональных переходах. Монтаж усиливает ощущение масштаба и помогает держать высокий уровень вовлечения до конца ролика.',
        coverStyle: "background-image:url('https://img.youtube.com/vi/ExHY8cCCz_g/maxresdefault.jpg');",
        cover: `
          <div class="cover-inner">
            <div class="cover-badge">Игровой формат</div>
            <div class="cover-icon" aria-hidden="true">
              <svg viewBox="0 0 24 24"><path d="M8 5v14l11-7z"></path></svg>
            </div>
          </div>
        `,
        list: [
          'быстрый ритм и усиление драматургии',
          'динамичные переходы и работа с напряжением',
          'motion-графика и визуальные акценты',
          'монтаж под игровой и развлекательный YouTube-контент'
        ]
      }
    };

    const modal = document.getElementById('projectModal');
    const modalTitle = document.getElementById('modalTitle');
    const modalSubtitle = document.getElementById('modalSubtitle');
    const modalDescription = document.getElementById('modalDescription');
    const modalList = document.getElementById('modalList');
    const modalYoutube = document.getElementById('modalYoutube');
    const modalCover = document.getElementById('modalCover');
    const closeModalBtn = document.getElementById('closeModal');

    function openProject(key){
      const data = projectData[key];
      if(!data) return;
      modalTitle.textContent = data.title;
      modalSubtitle.textContent = data.subtitle;
      modalDescription.textContent = data.description;
      modalYoutube.href = data.youtube;
      modalList.innerHTML = data.list.map(item => `<li>${item}</li>`).join('');
      modalCover.innerHTML = data.cover;
      modalCover.style.cssText = data.coverStyle;
      modal.classList.add('open');
      modal.setAttribute('aria-hidden','false');
      document.body.style.overflow = 'hidden';
    }

    function closeProject(){
      modal.classList.remove('open');
      modal.setAttribute('aria-hidden','true');
      document.body.style.overflow = '';
    }

    document.querySelectorAll('.open-project').forEach(el => {
      el.addEventListener('click', () => openProject(el.dataset.project));
    });

    document.querySelector('.modal-backdrop').addEventListener('click', closeProject);
    closeModalBtn.addEventListener('click', closeProject);
    document.addEventListener('keydown', (e) => {
      if(e.key === 'Escape') closeProject();
    });

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if(entry.isIntersecting) entry.target.classList.add('visible');
      });
    }, {threshold: .12});

    document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
  </script>
</body>
</html>

<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Win11小助手 · 把 Windows 11 变成你顺手的样子</title>
<meta name="description" content="Win11小助手：顶部热区一键操控、窗口智能管理、全局快捷键、截图备忘录、定时关机。轻量、无广告、为 Win11 而生。免费下载 V2.6.3.2">
<style>
  :root{
    --bg:#ffffff;
    --bg-soft:#f6f8fc;
    --bg-card:#ffffff;
    --ink:#16202e;
    --ink-soft:#5a6678;
    --line:#e6ebf2;
    --brand:#2563eb;
    --brand-2:#0ea5e9;
    --brand-grad:linear-gradient(120deg,#2563eb 0%,#0ea5e9 100%);
    --ok:#16a34a;
    --warn:#d97706;
    --shadow:0 10px 30px rgba(22,40,80,.08);
    --radius:18px;
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html{scroll-behavior:smooth}
  body{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI","PingFang SC","Microsoft YaHei",Roboto,Helvetica,Arial,sans-serif;color:var(--ink);background:var(--bg);line-height:1.6;-webkit-font-smoothing:antialiased}
  a{color:inherit;text-decoration:none}
  .wrap{max-width:1120px;margin:0 auto;padding:0 22px}
  .btn{display:inline-flex;align-items:center;gap:8px;font-weight:600;padding:13px 24px;border-radius:12px;transition:.18s transform,.18s box-shadow;cursor:pointer;border:1px solid transparent;font-size:15px}
  .btn-primary{background:var(--brand-grad);color:#fff;box-shadow:0 8px 20px rgba(37,99,235,.28)}
  .btn-primary:hover{transform:translateY(-2px);box-shadow:0 12px 26px rgba(37,99,235,.36)}
  .btn-baidu{background:#2932e1;color:#fff;box-shadow:0 8px 16px rgba(41,50,225,.25)}
  .btn-baidu:hover{transform:translateY(-2px);box-shadow:0 12px 22px rgba(41,50,225,.35)}
  .btn-lan{background:#4f46e5;color:#fff;box-shadow:0 8px 16px rgba(79,70,229,.25)}
  .btn-lan:hover{transform:translateY(-2px)}
  .btn-ghost{background:#fff;color:var(--brand);border-color:var(--line)}
  .btn-ghost:hover{border-color:var(--brand);transform:translateY(-2p)}

  /* NAV */
  header.nav{position:sticky;top:0;z-index:50;background:rgba(255,255,255,.88);backdrop-filter:saturate(160%) blur(12px);border-bottom:1px solid var(--line)}
  .nav-inner{display:flex;align-items:center;justify-content:space-between;height:64px}
  .logo{display:flex;align-items:center;gap:10px;font-weight:800;font-size:18px}
  .logo img{width:34px;height:34px;border-radius:8px;object-fit:contain}
  .nav-links{display:flex;gap:26px;font-size:15px;color:var(--ink-soft)}
  .nav-links a:hover{color:var(--brand)}
  @media(max-width:780px){.nav-links{display:none}}

  /* HERO */
  .hero{padding:70px 0 48px;background:radial-gradient(1200px 480px at 80% -10%,rgba(37,99,235,.09),transparent 60%),var(--bg)}
  .badge{display:inline-flex;align-items:center;gap:8px;background:#eef4ff;color:var(--brand);font-weight:600;font-size:13px;padding:7px 14px;border-radius:999px;border:1px solid #dbe7ff}
  .badge .pulse{width:8px;height:8px;border-radius:50%;background:var(--ok);box-shadow:0 0 0 4px rgba(22,163,74,.18);animation:pulse 2s infinite}
  @keyframes pulse{0%,100%{opacity:1}50%{opacity:.5}}
  .hero h1{font-size:clamp(32px,5.2vw,54px);line-height:1.12;margin:18px 0 14px;letter-spacing:-.5px}
  .hero h1 .grad{background:var(--brand-grad);-webkit-background-clip:text;background-clip:text;color:transparent}
  .hero p.lead{font-size:17px;color:var(--ink-soft);max-width:660px;line-height:1.7}
  .hero-cta{display:flex;gap:12px;margin-top:28px;flex-wrap:wrap}
  .hero-note{margin-top:14px;font-size:13px;color:var(--ink-soft)}
  .hero-note b{color:var(--ink)}

  /* SCREENSHOTS GALLERY */
  .gallery{margin-top:44px;display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:14px}
  .gallery img{width:100%;border-radius:14px;border:1px solid var(--line);object-fit:cover;aspect-ratio:auto;box-shadow:var(--shadow);transition:.2s transform}
  .gallery img:hover{transform:scale(1.02)}

  /* STATS */
  .stats{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-top:42px}
  .stat{background:var(--bg-card);border:1px solid var(--line);border-radius:14px;padding:18px;text-align:center}
  .stat .n{font-size:26px;font-weight:800;background:var(--brand-grad);-webkit-background-clip:text;background-clip:text;color:transparent}
  .stat .t{font-size:13px;color:var(--ink-soft);margin-top:2px}
  @media(max-width:680px){.stats{grid-template-columns:repeat(2,1fr)}}

  /* SECTION */
  section{padding:64px 0}
  .sec-head{text-align:center;max-width:680px;margin:0 auto 40px}
  .sec-head .kicker{color:var(--brand);font-weight:700;font-size:14px;letter-spacing:1px;text-transform:uppercase}
  .sec-head h2{font-size:clamp(26px,3.6vw,38px);margin:10px 0 12px;letter-spacing:-.3px}
  .sec-head p{color:var(--ink-soft);font-size:16px}

  /* FEATURES GRID */
  .grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
  @media(max-width:880px){.grid{grid-template-columns:repeat(2,1fr)}}
  @media(max-width:560px){.grid{grid-template-columns:1fr}}
  .card{background:var(--bg-card);border:1px solid var(--line);border-radius:var(--radius);padding:22px;transition:.18s transform,.18s box-shadow,.18s border-color}
  .card:hover{transform:translateY(-4px);box-shadow:var(--shadow);border-color:#d7e2f5}
  .card .ico{width:46px;height:46px;border-radius:12px;background:#eef4ff;display:grid;place-items:center;font-size:22px;margin-bottom:14px}
  .card h3{font-size:17px;margin-bottom:8px}
  .card p{font-size:14px;color:var(--ink-soft);line-height:1.65}

  /* SHORTCUT TABLE */
  .keys{background:var(--bg-soft);border:1px solid var(--line);border-radius:var(--radius);overflow:hidden}
  .krow{display:grid;grid-template-columns:180px 1fr;gap:14px;padding:14px 22px;border-bottom:1px solid var(--line);align-items:center}
  .krow:last-child{border-bottom:none}
  .krow:nth-child(odd){background:#fbfcfe}
  .key{display:inline-block;background:#fff;border:1px solid var(--line);border-bottom-width:3px;border-radius:8px;padding:4px 11px;font-weight:700;font-size:13px;color:var(--brand)}
  .krow .desc{font-size:14px;color:var(--ink-soft)}
  @media(max-width:560px){.krow{grid-template-columns:1fr;gap:6px}}

  /* WHY */
  .why{display:grid;grid-template-columns:repeat(2,1fr);gap:18px}
  @media(max-width:680px){.why{grid-template-columns:1fr}}
  .why .item{display:flex;gap:14px;background:var(--bg-card);border:1px solid var(--line);border-radius:14px;padding:18px}
  .why .tick{width:30px;height:30px;flex:0 0 30px;border-radius:8px;background:#eafaf0;color:var(--ok);display:grid;place-items:center;font-weight:800;font-size:16px}
  .why h4{font-size:15px;margin-bottom:4px}
  .why p{font-size:13px;color:var(--ink-soft);line-height:1.55}

  /* CHANGELOG */
  .timeline{position:relative;max-width:720px;margin:0 auto;padding-left:26px}
  .timeline::before{content:"";position:absolute;left:7px;top:6px;bottom:6px;width:2px;background:var(--line)}
  .tl{position:relative;margin-bottom:22px}
  .tl::before{content:"";position:absolute;left:-23px;top:6px;width:14px;height:14px;border-radius:50%;background:var(--brand);box-shadow:0 0 0 4px #eaf1ff}
  .tl .ver{font-weight:800;color:var(--brand)}
  .tl .date{font-size:12px;color:var(--ink-soft);margin-left:8px}
  .tl ul{margin:8px 0 0 2px;padding-left:18px;color:var(--ink-soft);font-size:14px}
  .tl li{margin:3px 0}

  /* FAQ */
  .faq{max-width:760px;margin:0 auto}
  .qa{border:1px solid var(--line);border-radius:14px;padding:18px 20px;margin-bottom:12px;background:var(--bg-card)}
  .qa h4{font-size:15px;margin-bottom:6px}
  .qa p{font-size:14px;color:var(--ink-soft);line-height:1.6}

  /* DOWNLOAD SECTION */
  .dl-section{background:var(--bg-soft)}
  .dl-grid{display:grid;grid-template-columns:1fr 1fr;gap:18px;max-width:800px;margin:0 auto}
  @media(max-width:600px){.dl-grid{grid-template-columns:1fr}}
  .dl-card{background:var(--bg-card);border:1px solid var(--line);border-radius:var(--radius);padding:24px;text-align:center}
  .dl-card h3{font-size:18px;margin-bottom:6px}
  .dl-card .sub{font-size:13px;color:var(--ink-soft);margin-bottom:18px}
  .dl-links{display:flex;flex-direction:column;gap:10px}
  .dl-links a{display:inline-flex;align-items:center;justify-content:center;gap:8px;font-weight:600;padding:12px 18px;border-radius:10px;font-size:14px}

  .warn-box{max-width:800px;margin:24px auto 0;background:#fffbeb;border:1px solid #fde68a;border-radius:14px;padding:16px 20px;display:flex;gap:12px;align-items:start;font-size:13px;color:#92400e;line-height:1.6}
  .warn-box .wico{font-size:20px;flex-shrink:0}

  footer{padding:34px 0;border-top:1px solid var(--line);color:var(--ink-soft);font-size:13px;text-align:center}
  footer a{color:var(--brand)}
</style>
</head>
<body>

<!-- NAV -->
<header class="nav">
  <div class="wrap nav-inner">
    <div class="logo"><img src="img/logo.png" alt="Win11小助手"> Win11小助手</div>
    <nav class="nav-links">
      <a href="#features">核心功能</a>
      <a href="#screenshots">软件截图</a>
      <a href="#shortcuts">快捷键</a>
      <a href="#changelog">更新日志</a>
      <a href="#faq">常见问题</a>
    </nav>
    <div style="display:flex;gap:10px">
      <a class="btn btn-primary" href="#download">免费下载</a>
    </div>
  </div>
</header>

<!-- HERO -->
<section class="hero">
  <div class="wrap">
    <span class="badge"><span class="pulse"></span> V2.6.3.2 最新版已发布</span>
    <h1>把 Windows 11 变成<br><span class="grad">你顺手的样子</span></h1>
    <p class="lead">顶部热区一键操控、窗口智能管理、全局快捷键、截图备忘录、定时关机——全方位简化电脑操作，让日常效率直接拉满。</p>
    <div class="hero-cta">
      <a class="btn btn-primary" href="https://wouyou.lanzouv.com/i8Jjo3vtf1rc" target="_blank">⬇ Win10/11 下载</a>
      <a class="btn btn-ghost" href="https://wouyou.lanzouv.com/iUzXs3vtf3ah" target="_blank">⬇ Win7 下载</a>
      <a class="btn btn-ghost" href="#download">更多下载方式</a>
    </div>
    <p class="hero-note"><b>兼容 Windows 7 / 10 / 11</b> · 轻量无广告 · 即开即用 · 本地运行不联网</p>

    <!-- REAL SCREENSHOT GALLERY -->
    <div class="gallery" id="screenshots">
      <img src="img/settings-menu.png" alt="设置菜单 - 关于/提醒时间/操作手册/自定义快捷键/默认浏览器/Win10经典右键等选项" loading="lazy">
      <img src="img/timer-dialog.png" alt="定时关机与定时提醒 - 支持两种互斥模式" loading="lazy">
      <img src="img/operation-manual.png" alt="操作手册 - 全功能快捷键一览表" loading="lazy">
      <img src="img/custom-hotkey.png" alt="自定义快捷键管理器 - 绑定任意程序到全局快捷键" loading="lazy">
    </div>
    <p style="text-align:center;margin-top:12px;font-size:13px;color:var(--ink-soft)">↑ 真实软件截图 — 设置菜单 · 定时关机 · 操作手册 · 自定义快捷键</p>

    <div class="stats">
      <div class="stat"><div class="n">8+</div><div class="t">核心效率模块</div></div>
      <div class="stat"><div class="n">3 键</div><div class="t">顶部热区联动</div></div>
      <div class="stat"><div class="n">0 广告</div><div class="t">纯净无打扰</div></div>
      <div class="stat"><div class="n">V2.6.3.2</div><div class="t">稳定迭代中</div></div>
    </div>
  </div>
</section>

<!-- FEATURES -->
<section id="features">
  <div class="wrap">
    <div class="sec-head">
      <div class="kicker">CORE FEATURES</div>
      <h2>一个助手，管好你的 Windows</h2>
      <p>从点击到快捷键，从窗口到系统，常用操作都被收进了顺手的位置。</p>
    </div>
    <div class="grid">
      <div class="card"><div class="ico">🖱️</div><h3>顶部热区三键联动</h3><p>屏幕顶部左 / 右 / 中键分别绑定文件管理器、浏览器、全局搜索、媒体切歌、音量调节、任务管理器等，鼠标一碰即达。</p></div>
      <div class="card"><div class="ico">🪟</div><h3>窗口智能管理</h3><p>单击标题栏置顶 / 取消置顶；双击自动缩放居中；底部右侧窗口并排贴靠 / 还原，多窗不打架。</p></div>
      <div class="card"><div class="ico">⌨️</div><h3>自定义全局快捷键</h3><p>自由绑定任意程序到自定义组合键，随时开关，把常用动作绑到你最顺手的按键上。</p></div>
      <div class="card"><div class="ico">⚡</div><h3>一键系统操作</h3><p>关机、重启、锁屏、清空回收站、批量关闭软件、禁用 Win 键……繁琐动作一次点击搞定。</p></div>
      <div class="card"><div class="ico">✂️</div><h3>截图 & 备忘录</h3><p>Alt+S 快速截图，Alt+Z 随手记备忘录，灵感与画面都不溜走。</p></div>
      <div class="card"><div class="ico">🔧</div><h3>默认浏览器 & 经典右键</h3><p>一键切换默认浏览器，一键回归 Win10 经典右键菜单，老习惯也能留住。</p></div>
      <div class="card"><div class="ico">⏰</div><h3>定时关机 / 提醒</h3><p>定时关机与定时提醒两种互斥模式，每天到点自动提醒（提前 5 分钟），省电省心不误事。</p></div>
      <div class="card"><div class="ico">📘</div><h3>内置操作手册</h3><p>全功能快捷键一览表随时可查，可选功能一目了然，新手也能秒上手。</p></div>
    </div>
  </div>
</section>

<!-- HOTZONE -->
<section id="hotzone" style="background:var(--bg-soft)">
  <div class="wrap">
    <div class="sec-head">
      <div class="kicker">TOP HOTZONE</div>
      <h2>核心玩法：屏幕顶部的“三键魔法”</h2>
      <p>不需要记复杂组合，把鼠标移到屏幕最顶端，按不同键就能触发不同功能。</p>
    </div>
    <div class="grid">
      <div class="card"><div class="ico">🖱️</div><h3>左键</h3><p>打开此电脑（文件管理器）、打开下载目录、任务视图、显示桌面</p></div>
      <div class="card"><div class="ico">🖱️</div><h3>右键</h3><p>搜索 Everything、打开默认浏览器设置、打开下载目录</p></div>
      <div class="card"><div class="ico">🖱️</div><h3>中键</h3><p>播放/暂停、上一曲、下一曲、调媒体音量、调系统音量、打开任务管理器</p></div>
    </div>
  </div>
</section>

<!-- SHORTCUTS -->
<section id="shortcuts">
  <div class="wrap">
    <div class="sec-head">
      <div class="kicker">SHORTCUTS</div>
      <h2>常用快捷键一览</h2>
      <p>也可以全部在设置里自定义、随时开关。</p>
    </div>
    <div class="keys">
      <div class="krow"><span class="key">Alt + S</span><span class="desc">打开截图工具</span></div>
      <div class="krow"><span class="key">Alt + Z</span><span class="desc">打开 / 关闭备忘录</span></div>
      <div class="krow"><span class="key">Ctrl+Alt+Shift+7</span><span class="desc">重启电脑</span></div>
      <div class="krow"><span class="key">Ctrl+Alt+Shift+8</span><span class="desc">关机</span></div>
      <div class="krow"><span class="key">Ctrl+Alt+Shift+9</span><span class="desc">注销</span></div>
      <div class="krow"><span class="key">Ctrl+Alt+Shift+0</span><span class="desc">睡眠 + 锁屏</span></div>
      <div class="krow"><span class="key">Ctrl+Alt+Shift+Del</span><span class="desc">清空回收站</span></div>
      <div class="krow"><span class="key">单击标题栏</span><span class="desc">窗口置顶 / 取消置顶</span></div>
      <div class="krow"><span class="key">双击标题栏</span><span class="desc">调整窗口尺寸并居中</span></div>
      <div class="krow"><span class="key">屏幕底部右侧</span><span class="desc">窗口并排贴靠 / 还原</span></div>
      <div class="krow"><span class="key">Win + Q</span><span class="desc">启动 QQ（可配置）</span></div>
      <div class="krow"><span class="key">Win + W</span><span class="desc">启动微信（可配置）</span></div>
      <div class="krow"><span class="key">Ctrl+Shift+Q</span><span class="desc">关闭 QQ（窗口显示状态下）</span></div>
      <div class="krow"><span class="key">Ctrl+Alt+E</span><span class="desc">关闭所有浏览器</span></div>
    </div>
  </div>
</section>

<!-- WHY US -->
<section id="why" style="background:var(--bg-soft)">
  <div class="wrap">
    <div class="sec-head">
      <div class="kicker">WHY WIN11 小助手</div>
      <h2>为什么选它</h2>
      <p>不是又一个“全家桶”，而是为你每天重复的那几件事减负。</p>
    </div>
    <div class="why">
      <div class="item"><div class="tick">✓</div><div><h4>轻量纯净</h4><p>无广告、无后台偷跑、无内购，专注效率本身，不拖慢系统。</p></div></div>
      <div class="item"><div class="tick">✓</div><div><h4>多版本支持</h4><p>同时提供 Win10/Win11 版本和 Win7 版本，老机器也不掉队。</p></div></div>
      <div class="item"><div class="tick">✓</div><div><h4>高度可定制</h4><p>热区、全局快捷键都能按你的习惯改，不是它教你，是你定义它。</p></div></div>
      <div class="item"><div class="tick">✓</div><div><h4>持续迭代</h4><p>V2.6.1.2 → V2.6.3.2，每版都有真实功能更新，越用越顺。</p></div></div>
    </div>
  </div>
</section>

<!-- CHANGELOG -->
<section id="changelog">
  <div class="wrap">
    <div class="sec-head">
      <div class="kicker">CHANGELOG</div>
      <h2>更新日志</h2>
      <p>每一次更新，都来自真实使用场景的打磨。</p>
    </div>
    <div class="timeline">
      <div class="tl"><span class="ver">V2.6.3.2</span><span class="date">最新</span><ul><li>定时关机和定时提醒两种互斥模式</li></ul></div>
      <div class="tl"><span class="ver">V2.6.3.1</span><ul><li>定时关机里增加提醒功能</li></ul></div>
      <div class="tl"><span class="ver">V2.6.3.0</span><ul><li>增加定时关机</li></ul></div>
      <div class="tl"><span class="ver">V2.6.2.0</span><ul><li>全面优化更新，修复之前所有版本不稳定的问题</li><li>新增屏幕底部右边：窗口并排贴靠 / 窗口还原</li></ul></div>
      <div class="tl"><span class="ver">V2.6.1.6</span><ul><li>新增备忘录 打开 / 关闭 Alt+Z</li></ul></div>
      <div class="tl"><span class="ver">V2.6.1.5</span><ul><li>新增截图功能 Alt+S</li><li>操作手册增加可选功能</li><li>默认浏览器设置，屏幕顶部中间区域右键可打开</li></ul></div>
      <div class="tl"><span class="ver">V2.6.1.2</span><ul><li>新增自定义快捷键</li><li>新增 Win10 经典右键</li></ul></div>
    </div>
  </div>
</section>

<!-- FAQ -->
<section id="faq" style="background:var(--bg-soft)">
  <div class="wrap">
    <div class="sec-head">
      <div class="kicker">FAQ</div>
      <h2>常见问题</h2>
    </div>
    <div class="faq">
      <div class="qa"><h4>Win11小助手收费吗？</h4><p>当前版本完全免费使用，无广告、无内购套路。</p></div>
      <div class="qa"><h4>支持哪些系统？</h4><p>提供两个版本：Win10/Win11 通用版 + Win7 专用版，下载时选对应版本即可。</p></div>
      <div class="qa"><h4>会收集我的数据吗？</h4><p>本地运行、不联网上传，你的操作与内容都在自己电脑上。</p></div>
      <div class="qa"><h4>微软杀毒报毒怎么办？</h4><p>部分杀软可能对未签名程序误报，属正常现象。如遇误报，请在杀软中「还原」或「允许」即可。</p></div>
      <div class="qa"><h4>快捷键和顶部热区能改吗？</h4><p>可以。全局快捷键在「自定义快捷键管理器」里自由绑定和开关；顶部热区功能可在设置中调整。</p></div>
      <div class="qa"><h4>怎么更新到最新版？</h4><p>下载最新安装包覆盖安装即可，配置通常会保留。</p></div>
    </div>
  </div>
</section>

<!-- DOWNLOAD -->
<section id="download" class="dl-section">
  <div class="wrap">
    <div class="sec-head">
      <div class="kicker">DOWNLOAD</div>
      <h2>立即下载</h2>
      <p>选择你的系统版本和下载渠道，免费获取 Win11小助手 V2.6.3.2。</p>
    </div>
    <div class="dl-grid">
      <!-- WIN10/11 -->
      <div class="dl-card">
        <h3>Windows 10 / 11</h3>
        <p class="sub">推荐大多数用户使用</p>
        <div class="dl-links">
          <a class="btn btn-lan" href="https://wouyou.lanzouv.com/i8Jjo3vtf1rc" target="_blank">☁️ 蓝奏云下载</a>
          <a class="btn btn-baidu" href="https://pan.baidu.com/s/1wmUvZnb0HYodVsHLDvSdvA?pwd=vcg8" target="_blank">🔵 百度网盘下载 (密码: vcg8)</a>
        </div>
      </div>
      <!-- WIN7 -->
      <div class="dl-card">
        <h3>Windows 7</h3>
        <p class="sub">专为 Win7 用户优化</p>
        <div class="dl-links">
          <a class="btn btn-lan" href="https://wouyou.lanzouv.com/iUzXs3vtf3ah" target="_blank">☁️ 蓝奏云下载</a>
          <a class="btn btn-baidu" href="https://pan.baidu.com/s/1tyhUXjfoy8Zqqr7jUgDb-Q?pwd=4u4j" target="_blank">🔵 百度网盘下载 (密码: 4u4j)</a>
        </div>
      </div>
    </div>
    <!-- WARNING -->
    <div class="warn-box">
      <span class="wico">⚠️</span>
      <div><strong>温馨提示：</strong>微软 Defender 等杀毒软件可能对未签名的本地程序产生误报，这是常见情况，非病毒。<strong>如遇误报请在杀软中选择「还原」或「添加信任」即可正常使用。</strong></div>
    </div>
    <div style="text-align:center;margin-top:26px;display:flex;gap:12px;justify-content:center;flex-wrap:wrap">
      <a class="btn btn-primary" href="https://github.com/nbshopping/WinHelp/releases" target="_blank">📦 从 GitHub Releases 下载</a>
      <a class="btn btn-ghost" href="https://github.com/nbshopping/WinHelp" target="_blank">🐙 查看项目源码</a>
    </div>
  </div>
</section>

<footer>
  <div class="wrap">
    © 2026 Win11小助手 · 为更顺手的 Windows 而生 · <a href="#download">下载</a> · <a href="#faq">帮助</a>
  </div>
</footer>

</body>
</html>

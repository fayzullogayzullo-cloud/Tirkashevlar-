<!doctype html>
<html lang="uz">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Fermerlik darslari — Videolar</title>
  <meta name="description" content="Fermerlik darslari: chorva, dehqonchilik, sabzavotchilik va meva yetishtirish bo'yicha amaliy videolar to'plami." />
  <style>
    :root{
      --accent:#2f6b2f;
      --muted:#333;
      --card:#ffffffcc;
      --glass: rgba(255,255,255,0.08);
      --radius:10px;
      --gap:14px;
    }
    @media (prefers-color-scheme:dark){
      :root{
        --accent:#6bb46b;
        --muted:#ddd;
        --card:#0f1114cc;
        --glass: rgba(0,0,0,0.25);
      }
    }

    {box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Inter, Roboto, Arial, sans-serif;color:var(--muted)}
    /* Background image (beautiful farm image). Change URL to use your own. */
    body{
      background-image: url('https://th.bing.com/th/id/OIP.j7wtyBkgvqBa7XPiCzLalQHaDC?w=348&h=143&c=7&r=0&o=7&cb=12&dpr=1.3&pid=1.7&rm=3');
      background-size: cover;
      background-position: center;
      background-attachment: fixed;
      position: relative;
    }
    /* subtle overlay for readability */
    body::before{
      content:"";
      position:fixed;
      inset:0;
      background: linear-gradient(180deg, rgba(0,0,0,0.35), rgba(255,255,255,0.04));
      pointer-events:none;
      z-index:0;
    }

    .app{display:flex;min-height:100vh;gap:0;position:relative;z-index:1}
    .sidebar{
      width:260px;padding:18px;flex-shrink:0;
      display:flex;flex-direction:column;gap:12px;
      background: linear-gradient(180deg, rgba(47,107,47,0.95), rgba(31,79,31,0.95));
      color:#fff;
      border-right: 1px solid rgba(255,255,255,0.04);
      backdrop-filter: blur(6px);
    }
    .logo{font-weight:700;font-size:1.1rem}
    nav a{color:inherit;text-decoration:none;padding:8px;border-radius:8px;display:block}
    nav a:hover, nav a.active{background:rgba(255,255,255,0.06)}
    .main{flex:1;padding:18px}
    header.header{display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:12px}
    .controls{display:flex;gap:10px;align-items:center}
    .search{padding:8px;border-radius:8px;border:1px solid rgba(0,0,0,0.08);min-width:180px}
    .video-list{display:grid;gap:var(--gap);grid-template-columns:repeat(auto-fit,minmax(260px,1fr))}
    .video{background:var(--card);padding:12px;border-radius:10px;box-shadow:0 2px 8px rgba(0,0,0,0.12)}
    .video h3{margin:0 0 8px 0;font-size:1rem;color:var(--muted)}
    .thumb{position:relative;border-radius:8px;overflow:hidden;background:#000}
    .thumb img{display:block;width:100%;height:auto;object-fit:cover}
    .play-btn{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;background:linear-gradient(180deg, rgba(0,0,0,0.0), rgba(0,0,0,0.28));color:#fff;font-weight:700;font-size:1.2rem;cursor:pointer}
    .meta{display:flex;justify-content:space-between;align-items:center;margin-top:8px}
    .link{font-size:0.9rem;color:var(--accent);text-decoration:none}

    /* Floating call widget: top-right */
    .call-widget{
      position:fixed;
      top:18px;
      right:18px;
      z-index:80;
      display:flex;
      flex-direction:column;
      align-items:center;
      gap:6px;
      font-family:inherit;
    }
    .call-button{
      display:flex;
      align-items:center;
      gap:8px;
      background:linear-gradient(180deg,#ffffffaa, #ffffff88);
      color:var(--accent);
      padding:10px 12px;
      border-radius:999px;
      box-shadow: 0 6px 18px rgba(0,0,0,0.18);
      border: none;
      cursor: pointer;
      font-weight:700;
      backdrop-filter: blur(4px);
    }
    .call-button small{display:block;font-size:0.85rem;color:rgba(0,0,0,0.7)}
    .call-label{
      font-size:0.85rem;
      color:#fff;
      background: rgba(0,0,0,0.36);
      padding:4px 8px;
      border-radius:8px;
      cursor:pointer;
      user-select:none;
    }
    /* panel that appears under "Call" label */
    .call-panel{
      margin-top:8px;
      background: linear-gradient(180deg, rgba(255,255,255,0.95), rgba(255,255,255,0.88));
      color:var(--muted);
      border-radius:10px;
      padding:10px;
      box-shadow: 0 6px 20px rgba(0,0,0,0.25);
      display:none;
      min-width:220px;
      text-align:left;
    }
    .call-panel.open{display:block}
    .call-option{display:flex;justify-content:space-between;align-items:center;padding:8px;border-radius:8px;cursor:pointer;background:transparent}
    .call-option:hover{background:rgba(0,0,0,0.04)}
    .call-option a{color:var(--accent);text-decoration:none;font-weight:600}
    .call-meta{font-size:0.85rem;color:rgba(0,0,0,0.6)}

    /* small close button in panel */
    .call-close{background:transparent;border:0;color:var(--muted);cursor:pointer;font-weight:700;padding:6px}

    /* mobile adjustments */
    @media (max-width:800px){
      .sidebar{position:fixed;left:-320px;top:0;height:100%;z-index:40;transition:left .22s}
      .sidebar.open{left:0}
      .call-widget{right:12px;top:12px}
      .call-panel{min-width:180px}
    }

    /* focus */
    a:focus, button:focus, input:focus{outline:3px solid rgba(47,107,47,0.18);outline-offset:3px}
  </style>
</head>
<body>
  <!-- Floating call widget placed at top-right -->
  <div class="call-widget" id="callWidget" aria-live="polite">
    <button class="call-button" id="callButton" aria-haspopup="true" aria-expanded="false" title="Qo'ng'iroq">
      <span style="display:inline-flex;align-items:center;gap:8px">
        <!-- simple phone icon using SVG for crispness -->
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" aria-hidden="true" focusable="false">
          <path d="M21 16.5a2 2 0 0 0-1.8-2c-1.1-.2-2.4-.3-3.7.2-.4.1-.8 0-1.1-.2l-2.1-1.6a16.2 16.2 0 0 1-3.1-3.1L9.1 7.8c-.3-.3-.4-.7-.2-1.1.5-1.3.4-2.6.2-3.7A2 2 0 0 0 7 1.8 2 2 0 0 0 4.5 3C3 6.3 4.7 11.1 8 14.4c3.3 3.3 8.1 5 11.4 3.5a2 2 0 0 0 1.1-2.4z" fill="#2f6b2f"/>
        </svg>
        <span>+998 94 258 60 45</span>
      </span>
      <small style="margin-left:6px">CALL</small>
    </button>

    <!-- a visible label under button which also toggles the panel -->
    <div id="callLabel" class="call-label" role="button" tabindex="0" aria-controls="callPanel" aria-expanded="false">Call</div>

    <!-- hidden panel shown when pressing label -->
    <div id="callPanel" class="call-panel" role="dialog" aria-hidden="true" aria-label="Call options">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:6px">
        <strong>Bog'lanish</strong>
        <button class="call-close" id="callPanelClose" aria-label="Yopish">✕</button>
      </div>
      <div class="call-option" id="makeCall">
        <span>To'g'ridan-to'g'ri qo'ng'iroq</span>
        <a href="tel:+998942586045" id="telLink">Call</a>
      </div>
      <div class="call-option" id="copyNumber" style="margin-top:6px">
        <span>Raqamni nusxalash</span>
        <button id="copyBtn" class="call-close" aria-label="Nusxalash">Copy</button>
      </div>
      <div style="margin-top:8px;font-size:0.9rem;color:rgba(0,0,0,0.6)">
        Qo'ng'iroq ishlamasa, raqamni nusxalab telefoningizdan qo'ng'iroq qiling.
      </div>
    </div>
  </div>

  <div class="app" id="app">
    <aside class="sidebar" id="sidebar" aria-label="Bosh sahifa menyusi">
      <div class="logo">Fermerlik Darslari</div>
      <p style="margin:0 0 8px 0;color:rgba(255,255,255,0.9)">Amaliy va nazariy videolar</p>
      <nav aria-label="Kategoriyalar" id="category-nav">
        <a href="#" class="sidebar-link active" data-category="livestock">Dehqonchilik</a>
        <a href="#" class="sidebar-link" data-category="crop-farming">Dehqonchilik</a>
        <a href="#" class="sidebar-link" data-category="vegetable-farming">Sabzavotchilik</a>
        <a href="#" class="sidebar-link" data-category="fruit-farming">Meva Yetishtirish</a>
      </nav>
    </aside>

    <main class="main" id="main">
      <header class="header">
        <div><strong id="category-title">Kategoriya</strong></div>
        <div class="controls" role="search" aria-label="Videolarni qidirish">
          <input id="search" class="search" placeholder="Video nomi bo'yicha izlash..." aria-label="Qidiruv" />
        </div>
      </header>

      <section>
        <h2 id="section-title">Videolar</h2>
        <div style="margin:10px 0;color:rgba(255,255,255,0.9);font-size:0.95rem" id="status">Yuklanmoqda...</div>
        <div id="video-list" class="video-list" aria-live="polite"></div>
      </section>
    </main>
  </div>

  <script>
    (function(){
      // Keep previous app functionality (simplified fallback)
      const fallback = {
        "livestock": [
          { "title": "1-dars", "link": "https://youtu.be/Wz3G2MAx_rw?si=5znLP4OGrm7WXDLM" },
          { "title": "2-dars", "link": "https://www.youtube.com/live/1WWM53nZGcU?si=wtwsPSNgPbib3Lpk" }
        ],
        "crop-farming": [
          { "title": "1-dars", "link": "https://www.youtube.com/watch?v=2Vv-BfVoq4g" },
          { "title": "2-dars", "link": "https://www.youtube.com/watch?v=kJQP7kiw5Fk" }
        ],
        "vegetable-farming": [
          { "title": "1-dars", "link": "https://www.youtube.com/watch?v=VbfpW0pbvaU" }
           { "title": "2-dars", "link": "https://www.youtube.com/watch?v=VbfpW0pbvaU" }
        ],
        "fruit-farming": [
          { "title": "1-dars", "link": "https://www.youtube.com/watch?v=09R8_2nJtjg" } 
          { "title": "2-dars", "link": "https://www.youtube.com/watch?v=VbfpW0pbvaU" }
        ]
      };

      const statusEl = document.getElementById('status');
      let videosData = fallback;

      fetch('videos.json').then(r => {
        if(!r.ok) throw new Error('No videos.json');
        return r.json();
      }).then(json => {
        videosData = json;
      }).catch(()=> {
        // fallback stays
      }).finally(()=> {
        statusEl.textContent = '';
        init();
      });

      const links = document.querySelectorAll('.sidebar-link');
      const listEl = document.getElementById('video-list');
      const categoryTitle = document.getElementById('category-title');
      const searchEl = document.getElementById('search');

      function init(){
        links.forEach(link => {
          link.addEventListener('click', (e) => {
            e.preventDefault();
            links.forEach(l=>l.classList.remove('active'));
            link.classList.add('active');
            const cat = link.dataset.category;
            categoryTitle.textContent = link.textContent;
            searchEl.value = '';
            loadVideos(cat);
          });
          link.setAttribute('tabindex','0');
          link.addEventListener('keydown', (e) => { if(e.key==='Enter') link.click(); });
        });

        const firstCategory = links[0]?.dataset.category || 'livestock';
        categoryTitle.textContent = links[0]?.textContent || 'Kategoriya';
        loadVideos(firstCategory);

        searchEl.addEventListener('input', () => {
          const active = document.querySelector('.sidebar-link.active');
          const cat = active?.dataset.category || firstCategory;
          loadVideos(cat, searchEl.value.trim());
        });
      }

      function loadVideos(category, filter=''){
        const videos = (videosData[category] || []).filter(v => v.title.toLowerCase().includes(filter.toLowerCase()));
        displayVideos(videos, category);
      }

      function youtubeIdFromUrl(url){
        try{
          const u = new URL(url);
          if(u.hostname.includes('youtube.com')){
            if(u.pathname.startsWith('/watch')) return u.searchParams.get('v');
            if(u.pathname.startsWith('/embed/')) return u.pathname.split('/embed/')[1];
            return null;
          }
          if(u.hostname === 'youtu.be') return u.pathname.slice(1);
        }catch(e){
          return url;
        }
        return null;
      }

      function getThumbnailUrl(videoLink){
        const id = youtubeIdFromUrl(videoLink);
        if(!id) return '';
        return `https://i.ytimg.com/vi/${id}/hqdefault.jpg`;
      }

      function displayVideos(videos){
        listEl.innerHTML = '';
        if(!videos || videos.length === 0){
          listEl.innerHTML = '<p style="color:rgba(255,255,255,0.9)">Bu kategoriyada video yo‘q.</p>';
          return;
        }
        videos.forEach(video => {
          const wrap = document.createElement('article');
          wrap.className = 'video';
          wrap.setAttribute('tabindex','0');

          const title = document.createElement('h3');
          title.textContent = video.title;

          const thumbWrap = document.createElement('div');
          thumbWrap.className = 'thumb';
          thumbWrap.setAttribute('role','button');
          thumbWrap.setAttribute('aria-label','Videoni ochish: ' + video.title);
          thumbWrap.tabIndex = 0;

          const thumbImg = document.createElement('img');
          const thumb = getThumbnailUrl(video.link);
          thumbImg.src = thumb || '';
          thumbImg.alt = video.title + ' — video thumbnail';
          thumbImg.loading = 'lazy';

          const playBtn = document.createElement('div');
          playBtn.className = 'play-btn';
          playBtn.textContent = '▶︎ Play';

          thumbWrap.appendChild(thumbImg);
          thumbWrap.appendChild(playBtn);

          function openVideo(){
            const id = youtubeIdFromUrl(video.link);
            if(!id){
              window.open(video.link, '_blank', 'noopener');
              return;
            }
            const src = `https://www.youtube.com/embed/${id}?autoplay=1&rel=0`;
            // open in new tab (keeps page lightweight) or you can implement modal playback if you prefer
            window.open(src, '_blank', 'noopener');
          }

          thumbWrap.addEventListener('click', openVideo);
          thumbWrap.addEventListener('keydown', (e) => { if(e.key === 'Enter' || e.key === ' ') { e.preventDefault(); openVideo(); } });

          const meta = document.createElement('div');
          meta.className = 'meta';

          const externalLink = document.createElement('a');
          const id = youtubeIdFromUrl(video.link);
          externalLink.href = id ? `https://www.youtube.com/watch?v=${id}` : video.link;
          externalLink.target = '_blank';
          externalLink.rel = 'noopener';
          externalLink.className = 'link';
          externalLink.textContent = 'YouTube’da ochish';

          meta.appendChild(externalLink);

          wrap.appendChild(title);
          wrap.appendChild(thumbWrap);
          wrap.appendChild(meta);

          listEl.appendChild(wrap);
        });
      }

      /* -------------------------
         Call widget behavior
         ------------------------- */
      const callLabel = document.getElementById('callLabel');
      const callPanel = document.getElementById('callPanel');
      const callPanelClose = document.getElementById('callPanelClose');
      const copyBtn = document.getElementById('copyBtn');
      const callButton = document.getElementById('callButton');
      const telLink = document.getElementById('telLink');

      function toggleCallPanel(open){
        const isOpen = typeof open === 'boolean' ? open : !callPanel.classList.contains('open');
        if(isOpen){
          callPanel.classList.add('open');
          callPanel.setAttribute('aria-hidden','false');
          callLabel.setAttribute('aria-expanded','true');
          callButton.setAttribute('aria-expanded','true');
          // focus first actionable element for keyboard users
          copyBtn.focus();
        } else {
          callPanel.classList.remove('open');
          callPanel.setAttribute('aria-hidden','true');
          callLabel.setAttribute('aria-expanded','false');
          callButton.setAttribute('aria-expanded','false');
        }
      }

      callLabel.addEventListener('click', ()=> toggleCallPanel());
      callLabel.addEventListener('keydown', (e)=> { if(e.key === 'Enter' || e.key === ' ') { e.preventDefault(); toggleCallPanel(); }});
      callButton.addEventListener('click', ()=> {
        // open phone dialer on supported devices
        window.location.href = 'tel:+998942586045';
      });

      callPanelClose.addEventListener('click', ()=> toggleCallPanel(false));

      // copy number
      copyBtn.addEventListener('click', () => {
        const tel = '+998 94 258 60 45';
        if(navigator.clipboard && navigator.clipboard.writeText){
          navigator.clipboard.writeText(tel).then(() => {
            showTempMessage('Raqam nusxalandi');
          }).catch(() => {
            showTempMessage('Nusxalash imkoni yo‘q — qo‘lda nusxa oling');
          });
        } else {
          // fallback
          const ta = document.createElement('textarea');
          ta.value = tel;
          document.body.appendChild(ta);
          ta.select();
          try{
            document.execCommand('copy');
            showTempMessage('Raqam nusxalandi');
          }catch(e){
            showTempMessage('Nusxalash imkoni yo‘q — qo‘lda nusxa oling');
          }
          ta.remove();
        }
      });

      // close panel when clicking outside
      document.addEventListener('click', (e) => {
        const path = e.composedPath ? e.composedPath() : (e.path || []);
        if(!path.includes(document.getElementById('callWidget')) && callPanel.classList.contains('open')){
          toggleCallPanel(false);
        }
      });

      // ESC to close
      document.addEventListener('keydown', (e) => {
        if(e.key === 'Escape') toggleCallPanel(false);
      });

      function showTempMessage(msg, ms = 2000){
        // tiny ephemeral message near the call widget
        const el = document.createElement('div');
        el.textContent = msg;
        el.style.position = 'fixed';
        el.style.right = '18px';
        el.style.top = '86px';
        el.style.background = 'rgba(0,0,0,0.75)';
        el.style.color = '#fff';
        el.style.padding = '8px 12px';
        el.style.borderRadius = '8px';
        el.style.zIndex = 90;
        document.body.appendChild(el);
        setTimeout(()=> el.remove(), ms);
      }

    })();
  </script>
</body>
</html>

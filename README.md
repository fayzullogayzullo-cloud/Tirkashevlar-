<!doctype html>
<html lang="uz">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Fermerlik darslari — Videolar</title>
  <meta name="description" content="Fermerlik darslari: chorva, dehqonchilik, sabzavotchilik va meva yetishtirish bo'yicha amaliy videolar to'plami." />
  <style>
    :root{
      --bg:#f6f8f1;
      --accent:#2f6b2f;
      --muted:#6b6b6b;
      --card:#ffffff;
      --radius:10px;
      --gap:14px;
    }
    @media (prefers-color-scheme:dark){
      :root{
        --bg:#0f1110;
        --accent:#6bb46b;
        --muted:#9aa0a8;
        --card:#121416;
      }
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Inter, Roboto, Arial, sans-serif;background:var(--bg);color:var(--muted)}
    .app{display:flex;min-height:100vh;gap:0}
    .sidebar{
      width:260px;background:linear-gradient(180deg,var(--accent),#1f4f1f);color:#fff;padding:18px;flex-shrink:0;
      display:flex;flex-direction:column;gap:12px;
    }
    .logo{font-weight:700;font-size:1.1rem}
    nav a{color:inherit;text-decoration:none;padding:8px;border-radius:8px;display:block}
    nav a:hover, nav a.active{background:rgba(255,255,255,0.06)}
    .main{flex:1;padding:18px}
    header.header{display:flex;align-items:center;justify-content:space-between;gap:12px;margin-bottom:12px}
    .controls{display:flex;gap:10px;align-items:center}
    .search{padding:8px;border-radius:8px;border:1px solid rgba(0,0,0,0.08);min-width:180px}
    .phone-icon{background:#fff;color:var(--accent);border-radius:8px;padding:8px 10px;border:none;cursor:pointer}
    .video-list{display:grid;gap:var(--gap);grid-template-columns:repeat(auto-fit,minmax(260px,1fr))}
    .video{background:var(--card);padding:12px;border-radius:10px;box-shadow:0 2px 8px rgba(0,0,0,0.06);color:initial}
    .video h3{margin:0 0 8px 0;font-size:1rem;color:inherit}
    .thumb{position:relative;border-radius:8px;overflow:hidden;background:#000}
    .thumb img{display:block;width:100%;height:auto;object-fit:cover}
    .play-btn{
      position:absolute;inset:0;display:flex;align-items:center;justify-content:center;background:linear-gradient(180deg, rgba(0,0,0,0.0), rgba(0,0,0,0.28));
      color:#fff;font-weight:700;font-size:1.2rem;cursor:pointer;backdrop-filter:blur(2px)
    }
    .meta{display:flex;justify-content:space-between;align-items:center;margin-top:8px}
    .link{font-size:0.9rem;color:var(--accent);text-decoration:none}
    /* Mobile */
    .hamburger{display:none;background:transparent;border:0;color:var(--muted);font-weight:700;padding:8px;cursor:pointer}
    @media (max-width:800px){
      .sidebar{position:fixed;left:-320px;top:0;height:100%;z-index:40;transition:left .22s}
      .sidebar.open{left:0}
      .app{padding-left:0}
      .hamburger{display:inline-block}
    }
    /* toast */
    .toast{position:fixed;right:16px;bottom:16px;background:#111;color:#fff;padding:10px 14px;border-radius:8px;display:none;z-index:60}
    .visually-hidden{position:absolute!important;height:1px;width:1px;overflow:hidden;clip:rect(1px,1px,1px,1px);white-space:nowrap}
    /* focus */
    a:focus, button:focus, input:focus{outline:3px solid rgba(47,107,47,0.18);outline-offset:3px}
    /* responsive iframe modal */
    .modal{position:fixed;inset:0;background:rgba(0,0,0,0.75);display:flex;align-items:center;justify-content:center;padding:18px;z-index:50;display:none}
    .modal.open{display:flex}
    .modal-content{width:min(1000px,95%);aspect-ratio:16/9;background:#000;border-radius:8px;overflow:hidden}
    .modal-close{position:absolute;right:18px;top:18px;background:#fff;border-radius:6px;padding:6px;border:0;cursor:pointer}
  </style>
</head>
<body>
  <div class="app">
    <aside class="sidebar" id="sidebar" aria-label="Bosh sahifa menyusi">
      <div class="logo">Fermerlik Darslari</div>
      <p style="margin:0 0 8px 0;color:rgba(255,255,255,0.9)">Amaliy va nazariy videolar</p>
      <nav aria-label="Kategoriyalar" id="category-nav">
        <a href="#" class="sidebar-link active" data-category="livestock">Chorva Dehqonchilik</a>
        <a href="#" class="sidebar-link" data-category="crop-farming">Dehqonchilik</a>
        <a href="#" class="sidebar-link" data-category="vegetable-farming">Sabzavotchilik</a>
        <a href="#" class="sidebar-link" data-category="fruit-farming">Meva Yetishtirish</a>
      </nav>
      <div style="margin-top:auto;font-size:0.9rem">
        <div>Bog'lanish:</div>
        <div style="display:flex;gap:8px;align-items:center;margin-top:6px">
          <a href="tel:+998942586045" class="link" id="phone-link">+998 94 258 60 45</a>
          <button class="phone-icon" id="phone-copy" aria-label="Telefon raqamini nusxalash">Nusxa</button>
        </div>
      </div>
    </aside>

    <main class="main">
      <header class="header">
        <div style="display:flex;align-items:center;gap:10px">
          <button class="hamburger" id="hamburger" aria-controls="sidebar" aria-expanded="false" aria-label="Menyuni ochish">☰</button>
          <div><strong id="category-title">Kategoriya</strong></div>
        </div>

        <div class="controls" role="search" aria-label="Videolarni qidirish">
          <input id="search" class="search" placeholder="Video nomi bo'yicha izlash..." aria-label="Qidiruv" />
          <button class="phone-icon" id="phone-icon" title="Bog'lanish">+998 94 258 60 45</button>
        </div>
      </header>

      <section>
        <h2 id="section-title">Videolar</h2>
        <div style="margin:10px 0;color:var(--muted);font-size:0.95rem" id="status">Yuklanmoqda...</div>
        <div id="video-list" class="video-list" aria-live="polite"></div>
      </section>
    </main>
  </div>

  <div class="modal" id="modal" role="dialog" aria-modal="true" aria-label="Video oynasi">
    <div class="modal-content" id="modal-content" tabindex="0"></div>
    <button class="modal-close" id="modal-close" aria-label="Yopish">✕</button>
  </div>

  <div class="toast" id="toast" role="status" aria-live="polite"></div>

  <script>
    (function(){
      // Inline fallback data, but app will try to fetch videos.json first.
      const fallback = {
        "livestock": [
          { "title": "Introduction to Livestock Farming", "link": "https://www.youtube.com/watch?v=dQw4w9WgXcQ" },
          { "title": "Livestock Management Basics", "link": "https://www.youtube.com/watch?v=3JZ_D3ELwOQ" }
        ],
        "crop-farming": [
          { "title": "Basics of Crop Farming", "link": "https://www.youtube.com/watch?v=2Vv-BfVoq4g" },
          { "title": "Effective Crop Techniques", "link": "https://www.youtube.com/watch?v=kJQP7kiw5Fk" }
        ],
        "vegetable-farming": [
          { "title": "Vegetable Garden Tips", "link": "https://www.youtube.com/watch?v=VbfpW0pbvaU" }
        ],
        "fruit-farming": [
          { "title": "Fruit Tree Care", "link": "https://www.youtube.com/watch?v=09R8_2nJtjg" }
        ]
      };

      const statusEl = document.getElementById('status');
      let videosData = fallback;

      // Try to fetch videos.json if present (CORS-friendly when served from same origin)
      fetch('videos.json').then(r => {
        if(!r.ok) throw new Error('No videos.json');
        return r.json();
      }).then(json => {
        videosData = json;
      }).catch(()=> {
        // keep fallback
      }).finally(()=> {
        statusEl.textContent = '';
        init();
      });

      const links = document.querySelectorAll('.sidebar-link');
      const listEl = document.getElementById('video-list');
      const categoryTitle = document.getElementById('category-title');
      const searchEl = document.getElementById('search');
      const sidebar = document.getElementById('sidebar');
      const hamburger = document.getElementById('hamburger');
      const phoneCopy = document.getElementById('phone-copy');
      const phoneIcon = document.getElementById('phone-icon');
      const modal = document.getElementById('modal');
      const modalContent = document.getElementById('modal-content');
      const modalClose = document.getElementById('modal-close');
      const toast = document.getElementById('toast');

      function init(){
        // Setup category links
        links.forEach(link => {
          link.addEventListener('click', (e) => {
            e.preventDefault();
            links.forEach(l=>l.classList.remove('active'));
            link.classList.add('active');
            const cat = link.dataset.category;
            categoryTitle.textContent = link.textContent;
            searchEl.value = '';
            loadVideos(cat);
            closeSidebarOnMobile();
          });
          // keyboard accessibility
          link.setAttribute('tabindex','0');
          link.addEventListener('keydown', (e) => { if(e.key==='Enter') link.click(); });
        });

        // default
        const firstCategory = links[0]?.dataset.category || 'livestock';
        categoryTitle.textContent = links[0]?.textContent || 'Kategoriya';
        loadVideos(firstCategory);

        searchEl.addEventListener('input', () => {
          const active = document.querySelector('.sidebar-link.active');
          const cat = active?.dataset.category || firstCategory;
          loadVideos(cat, searchEl.value.trim());
        });

        phoneCopy.addEventListener('click', () => {
          const tel = '+998 94 258 60 45';
          navigator.clipboard?.writeText(tel).then(() => showToast('Telefon raqami nusxalandi')).catch(() => {
            // fallback select
            showToast('Nusxalash muammosi, iltimos qo\'lda nusxa oling');
          });
        });

        phoneIcon.addEventListener('click', ()=> showToast('Telefon: +998 94 258 60 45'));

        // mobile hamburger
        hamburger.addEventListener('click', () => {
          const isOpen = sidebar.classList.toggle('open');
          hamburger.setAttribute('aria-expanded', String(isOpen));
        });

        // modal controls
        modalClose.addEventListener('click', closeModal);
        modal.addEventListener('click', (e)=> { if(e.target === modal) closeModal(); });
        document.addEventListener('keydown', (e)=> { if(e.key==='Escape') closeModal(); });

        // improve keyboard focus behavior
        modalContent.addEventListener('keydown', (e)=> {
          if(e.key === 'Tab') e.stopPropagation();
        });
      }

      function closeSidebarOnMobile(){
        if(window.innerWidth <= 800){
          sidebar.classList.remove('open');
          hamburger.setAttribute('aria-expanded','false');
        }
      }

      function showToast(text, ms = 2600){
        toast.textContent = text;
        toast.style.display = 'block';
        setTimeout(()=> { toast.style.display = 'none'; }, ms);
      }

      function loadVideos(category, filter=''){
        const videos = (videosData[category] || []).filter(v => v.title.toLowerCase().includes(filter.toLowerCase()));
        displayVideos(videos, category);
      }

      // Utility: extract YouTube video id from many URL forms
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
          // may be an id already
          return url;
        }
        return null;
      }

      function getThumbnailUrl(videoLink){
        const id = youtubeIdFromUrl(videoLink);
        if(!id) return '';
        return `https://i.ytimg.com/vi/${id}/hqdefault.jpg`;
      }

      function displayVideos(videos, category){
        listEl.innerHTML = '';
        if(!videos || videos.length === 0){
          listEl.innerHTML = '<p>Bu kategoriyada video yo‘q.</p>';
          return;
        }
        videos.forEach(video => {
          const wrap = document.createElement('article');
          wrap.className = 'video';
          wrap.setAttribute('tabindex','0');

          const title = document.createElement('h3');
          title.textContent = video.title;
          title.id = 'title-' + Math.random().toString(36).slice(2,9);

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

          // click or enter loads real iframe in modal (lazy load)
          function openVideo(){
            const id = youtubeIdFromUrl(video.link);
            if(!id){
              // open raw link new tab if not youtube
              window.open(video.link, '_blank', 'noopener');
              return;
            }
            const src = `https://www.youtube.com/embed/${id}?autoplay=1&rel=0`;
            modalContent.innerHTML = `<iframe src="${src}" title="${escapeHtml(video.title)}" width="100%" height="100%" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>`;
            modal.classList.add('open');
            modalContent.focus();
          }

          thumbWrap.addEventListener('click', openVideo);
          thumbWrap.addEventListener('keydown', (e) => { if(e.key === 'Enter' || e.key === ' ') { e.preventDefault(); openVideo(); } });

          const meta = document.createElement('div');
          meta.className = 'meta';

          const externalLink = document.createElement('a');
          // make a watch url to open on youtube directly
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

      function closeModal(){
        modal.classList.remove('open');
        modalContent.innerHTML = '';
      }

      // small helper to sanitize title in attribute
      function escapeHtml(s){
        return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
      }

    })();
  </script>
</body>
</html>

<!doctype html>
<html lang="uz">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <title>Fermerlik darslari</title>
    <style>
        body { font-family: Arial, sans-serif; margin:0; display:flex; min-height:100vh; }
        .sidebar { width:240px; background:#2f6b2f; color:#fff; padding:16px; box-sizing:border-box; }
        .sidebar .logo { font-weight:bold; margin-bottom:12px; }
        .sidebar a { color:#fff; display:block; padding:8px 6px; text-decoration:none; border-radius:4px; }
        .sidebar a:hover, .sidebar a.active { background:rgba(255,255,255,0.08); }
        .main { flex:1; padding:20px; box-sizing:border-box; background:#f6f8f1; }
        header.header { display:flex; justify-content:space-between; align-items:center; margin-bottom:16px; }
        .video { margin-bottom:18px; }
        .video h3 { margin:6px 0; }
        iframe { max-width:100%; border:0; }
        .video-list { display:grid; gap:14px; grid-template-columns: repeat(auto-fit,minmax(300px,1fr)); }
        .phone-icon { cursor:pointer; padding:6px 8px; background:#fff; border-radius:4px; color:#2f6b2f; }
    </style>
</head>
<body>
    <aside class="sidebar" id="sidebar">
        <div class="logo">Fermerlik Darslari</div>
        <nav>
            <a href="#" class="sidebar-link active" data-category="livestock">Chorva Dehqonchilik</a>
            <a href="#" class="sidebar-link" data-category="crop-farming">Dehqonchilik</a>
            <a href="#" class="sidebar-link" data-category="vegetable-farming">Sabzavotchilik</a>
            <a href="#" class="sidebar-link" data-category="fruit-farming">Meva Yetishtirish</a>
        </nav>
    </aside>

    <main class="main">
        <header class="header" id="header">
            <div><strong id="category-title">Kategoriya</strong></div>
            <div>
                <button class="phone-icon" id="phone-icon" title="Bog'lanish">+998 94 258 60 45</button>
            </div>
        </header>

        <section class="video-section">
            <h2 id="section-title">Videolar</h2>
            <div id="video-list" class="video-list"></div>
        </section>
    </main>

    <script>
    document.addEventListener('DOMContentLoaded', () => {
        // JSON data (agar xohlasangiz alohida videos.json ga o'zgartiring)
        const videosData = {
            "livestock": [
                { "title": "Introduction to Livestock Farming", "link": "https://www.youtube.com/embed/dQw4w9WgXcQ" },
                { "title": "Livestock Management Basics", "link": "https://www.youtube.com/embed/3JZ_D3ELwOQ" }
            ],
            "crop-farming": [
                { "title": "Basics of Crop Farming", "link": "https://www.youtube.com/embed/2Vv-BfVoq4g" },
                { "title": "Effective Crop Techniques", "link": "https://www.youtube.com/embed/kJQP7kiw5Fk" }
            ],
            "vegetable-farming": [
                { "title": "Vegetable Garden Tips", "link": "https://www.youtube.com/embed/VbfpW0pbvaU" }
            ],
            "fruit-farming": [
                { "title": "Fruit Tree Care", "link": "https://www.youtube.com/embed/09R8_2nJtjg" }
            ]
        };

        const links = document.querySelectorAll('.sidebar-link');
        const listEl = document.getElementById('video-list');
        const categoryTitle = document.getElementById('category-title');

        links.forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                links.forEach(l=>l.classList.remove('active'));
                link.classList.add('active');
                const cat = link.dataset.category;
                categoryTitle.textContent = link.textContent;
                loadVideos(cat);
            });
        });

        document.getElementById('phone-icon').addEventListener('click', () => {
            alert('Telefon: +998 94 258 60 45');
        });

        // Load first category by default
        const firstCategory = links[0].dataset.category;
        categoryTitle.textContent = links[0].textContent;
        loadVideos(firstCategory);

        function loadVideos(category) {
            const videos = videosData[category] || [];
            displayVideos(videos);
        }

        function displayVideos(videos) {
            listEl.innerHTML = '';
            if (videos.length === 0) {
                listEl.innerHTML = '<p>Bu kategoriyada video yo‘q.</p>';
                return;
            }
            videos.forEach(video => {
                const wrap = document.createElement('div');
                wrap.className = 'video';

                const title = document.createElement('h3');
                title.textContent = video.title;

                const iframe = document.createElement('iframe');
                iframe.width = '560';
                iframe.height = '315';
                iframe.src = video.link;
                iframe.allow = "accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture";
                iframe.allowFullscreen = true;

                const link = document.createElement('a');
                const watchUrl = video.link.includes('/embed/') ? video.link.replace('/embed/','/watch?v=') : video.link;
                link.href = watchUrl;
                link.target = '_blank';
                link.textContent = 'YouTube’da ochish';

                wrap.appendChild(title);
                wrap.appendChild(iframe);
                wrap.appendChild(link);

                listEl.appendChild(wrap);
            });
        }
    });
    </script>
</body>
</html>

<iframe src="https://debeatzgh1.github.io/-Firebase-Login-Popup/" width="100%" height="400" frameborder="0" allowfullscreen></iframe>





<iframe src="https://msha.ke/debeatzgh" width="100%" height="400" frameborder="0" allowfullscreen></iframe>




<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeBeatzGH | Master Ecosystem</title>
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700;900&display=swap');

        :root {
            --bg-color: #0d1117;
            --text-color: #ffffff;
            --glass: rgba(15, 15, 20, 0.95);
            --border: rgba(255, 255, 255, 0.1);
            --accent: #FF1493; /* Deep Pink */
            --yt-red: #FF0000;
            --ui-cyan: #00f2ff;
        }

        body.light-mode {
            --bg-color: #f0f2f5;
            --text-color: #1c1e21;
            --glass: rgba(255, 255, 255, 0.95);
            --border: rgba(0, 0, 0, 0.1);
        }

        body { 
            background: var(--bg-color); 
            color: var(--text-color); 
            font-family: 'Inter', sans-serif;
            transition: background 0.5s ease;
            margin: 0; min-height: 200vh; scroll-behavior: smooth;
            overflow-x: hidden;
        }

        /* --- 1. TOP FLOATING BANNERS --- */
        .banner-container {
            position: fixed; bottom: 15px; left: 50%; transform: translateX(-50%);
            z-index: 9999; display: flex; flex-direction: column; align-items: center;
        }

        .master-banner {
            width: 350px; height: 50px; background: var(--glass);
            backdrop-filter: blur(15px); border: 1px solid var(--border);
            border-radius: 50px; display: flex; align-items: center;
            justify-content: space-between; padding: 0 6px 0 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .text-slider { flex: 1; height: 20px; overflow: hidden; margin-right: 10px; }
        .slide-inner { display: flex; flex-direction: column; animation: slideUp 6s infinite; }
        .slide-inner span { height: 20px; font-size: 0.7rem; font-weight: 800; display: flex; align-items: center; gap: 8px; white-space: nowrap; }

        @keyframes slideUp {
            0%, 25% { transform: translateY(0); }
            33%, 58% { transform: translateY(-20px); }
            66%, 91% { transform: translateY(-40px); }
            100% { transform: translateY(0); }
        }

        .launch-btn { padding: 6px 16px; border-radius: 50px; border: none; color: white; font-weight: 900; font-size: 0.65rem; cursor: pointer; text-transform: uppercase; }

        /* --- 2. MASTER OVERLAY --- */
        #master-overlay {
            position: fixed; inset: 0; background: rgba(0,0,0,0.98);
            z-index: 10001; display: none; flex-direction: column;
            animation: fadeIn 0.3s ease;
        }

        .overlay-nav { height: 55px; background: #111; display: flex; align-items: center; justify-content: space-between; padding: 0 20px; border-bottom: 2px solid var(--accent); }
        #master-frame { width: 100%; flex-grow: 1; border: none; background: white; }

        /* --- 3. SOCIAL & UTILITY DOCK --- */
        .social-dock {
            position: fixed; right: 25px; bottom: 30px;
            display: flex; flex-direction: column; align-items: center; gap: 10px;
            background: var(--glass); padding: 12px 10px; border-radius: 50px;
            border: 1px solid var(--border); backdrop-filter: blur(15px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.4); z-index: 10000;
            opacity: 0; transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .social-dock.show, .social-dock.is-locked { opacity: 1; transform: translateY(0); }
        .social-dock.is-locked { border-color: var(--accent); }

        .dock-icon { width: 38px; height: 38px; display: flex; align-items: center; justify-content: center; border-radius: 50%; color: var(--text-color); transition: 0.3s; cursor: pointer; }
        .dock-icon:hover { transform: scale(1.15); color: var(--accent); }

        .dev-tag { font-size: 7px; font-weight: 900; color: #2ea44f; text-transform: uppercase; letter-spacing: 0.5px; text-align: center; }

        #backToTop { width: 36px; height: 36px; background: rgba(255,255,255,0.05); border-radius: 50%; display: none; align-items: center; justify-content: center; cursor: pointer; transition: 0.3s; }
        #backToTop.visible { display: flex; }

        .share-toast { position: absolute; right: 55px; background: var(--accent); color: white; padding: 4px 10px; border-radius: 4px; font-size: 10px; font-weight: 800; opacity: 0; pointer-events: none; transition: 0.3s; }

        /* Helpers */
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        .sep { width: 20px; height: 1px; background: var(--border); margin: 5px 0; }
    </style>
</head>
<body>

    <div class="banner-container">
        <div id="ban-prod" class="master-banner" style="border-color: var(--accent);">
            <div class="text-slider">
                <div class="slide-inner">
                    <span style="color: var(--accent);">🚀 PRODUCTIVITY HUB</span>
                    <span style="color: var(--accent);">💡 TOOLS & STRATEGY</span>
                    <span style="color: var(--accent);">📈 SCALE YOUR BUSINESS</span>
                </div>
            </div>
            <button class="launch-btn" style="background: var(--accent);" onclick="launch('https://msha.ke/debeatzgh', 'Productivity Hub')">Open</button>
        </div>

        <div class="flex gap-4 mt-3 bg-black/40 p-2 rounded-full border border-white/5 backdrop-blur-md">
            <div onclick="switchBanner('prod')" class="w-3 h-3 rounded-full bg-pink-500 cursor-pointer hover:scale-125 transition"></div>
            <div onclick="switchBanner('ent')" class="w-3 h-3 rounded-full bg-red-600 cursor-pointer hover:scale-125 transition"></div>
            <div onclick="switchBanner('ui')" class="w-3 h-3 rounded-full bg-cyan-400 cursor-pointer hover:scale-125 transition"></div>
        </div>
    </div>

    <div id="master-overlay">
        <div class="overlay-nav" id="overlay-header">
            <span id="overlay-title" class="font-bold text-[10px] tracking-widest uppercase text-white">Resource Loader</span>
            <button onclick="closeOverlay()" class="text-[10px] border border-white/20 px-4 py-1 rounded text-gray-400 hover:text-white">CLOSE [ESC]</button>
        </div>
        <iframe id="master-frame" src=""></iframe>
    </div>

    <div class="social-dock" id="socialDock">
        <div class="dev-tag">Live<span id="git-date" class="block text-white opacity-40">...</span></div>
        
        <div class="dock-icon" onclick="toggleTheme()" title="Toggle Theme"><i class="fas fa-sun" id="theme-ico"></i></div>
        
        <div class="sep"></div>
        
        <a href="https://www.instagram.com/debeatzgh" target="_blank" class="dock-icon"><i class="fab fa-instagram"></i></a>
        <a href="https://debeatzgh1.github.io/blogs/" target="_blank" class="dock-icon"><i class="fas fa-rss"></i></a>
        
        <div class="sep"></div>
        
        <div class="dock-icon" onclick="copyLink(event)"><i class="fas fa-share-alt"></i><div class="share-toast" id="toast">Copied!</div></div>
        
        <div id="backToTop" onclick="window.scrollTo({top:0})"><i class="fas fa-chevron-up"></i></div>
    </div>

    <script>
        const banners = {
            prod: { el: document.getElementById('ban-prod'), color: '#FF1493', title: 'Productivity' },
            ent: { url: 'https://debeatzgh1.github.io/E-Hub-/', color: '#FF0000', title: 'Entertainment' },
            ui: { url: 'https://debeatzgh1.github.io/me-/', color: '#00f2ff', title: 'UI Browser' }
        };

        const overlay = document.getElementById('master-overlay');
        const frame = document.getElementById('master-frame');
        const header = document.getElementById('overlay-header');
        const dock = document.getElementById('socialDock');
        let isLocked = false;

        // 1. Banner Logic
        function switchBanner(mode) {
            const b = banners[mode];
            const bannerEl = document.getElementById('ban-prod');
            bannerEl.style.borderColor = b.color;
            // Update Inner Text
            const inner = bannerEl.querySelector('.slide-inner');
            inner.innerHTML = mode === 'ent' ? 
                `<span style="color:${b.color}">🎵 ENTERTAINMENT HUB</span><span style="color:${b.color}">🎬 STREAM CONTENT</span><span style="color:${b.color}">🔴 LIVE PLAYLISTS</span>` :
                mode === 'ui' ?
                `<span style="color:${b.color}">🖥️ UI & INTERFACES</span><span style="color:${b.color}">🎨 DESIGN SYSTEMS</span><span style="color:${b.color}">📂 PORTFOLIO VIEW</span>` :
                `<span style="color:${b.color}">🚀 PRODUCTIVITY HUB</span><span style="color:${b.color}">💡 TOOLS & STRATEGY</span><span style="color:${b.color}">📈 SCALE BUSINESS</span>`;
            
            const btn = bannerEl.querySelector('.launch-btn');
            btn.style.background = b.color;
            btn.onclick = () => launch(mode === 'prod' ? 'https://msha.ke/debeatzgh' : b.url, b.title);
        }

        // 2. Overlay Logic
        function launch(url, title) {
            document.getElementById('overlay-title').innerText = title;
            header.style.borderBottomColor = window.getComputedStyle(document.querySelector('.launch-btn')).backgroundColor;
            frame.src = url;
            overlay.style.display = 'flex';
            document.body.style.overflow = 'hidden';
        }

        function closeOverlay() {
            overlay.style.display = 'none';
            frame.src = "";
            document.body.style.overflow = 'auto';
        }

        // 3. Dock & Theme Logic
        function toggleTheme() {
            document.body.classList.toggle('light-mode');
            const isLight = document.body.classList.contains('light-mode');
            document.getElementById('theme-ico').className = isLight ? 'fas fa-moon' : 'fas fa-sun';
            isLocked = true; dock.classList.add('is-locked');
        }

        async function copyLink(e) {
            e.stopPropagation();
            await navigator.clipboard.writeText(window.location.href);
            const t = document.getElementById('toast');
            t.style.opacity = "1"; setTimeout(() => t.style.opacity = "0", 2000);
        }

        // 4. GitHub Pulse
        async function getGit() {
            try {
                const r = await fetch('https://api.github.com/repos/debeatzgh1/debeatzgh/commits/main');
                const d = await r.json();
                const date = new Date(d.commit.author.date);
                document.getElementById('git-date').innerText = date.toLocaleDateString('en-US', {month:'short', day:'numeric'});
            } catch(e) { document.getElementById('git-date').innerText = "Recent"; }
        }

        // 5. Scroll & Auto-Fade
        window.onscroll = () => {
            const btt = document.getElementById('backToTop');
            if(window.scrollY > 300) btt.classList.add('visible'); else btt.classList.remove('visible');
        };

        function startBreathe() {
            if(isLocked) return;
            dock.classList.add('show');
            setTimeout(() => { if(!isLocked) dock.classList.remove('show'); }, 4000);
        }

        document.addEventListener('keydown', (e) => { if(e.key === "Escape") closeOverlay(); });

        getGit();
        setInterval(startBreathe, 8000);
        setTimeout(startBreathe, 1000);
    </script>
</body>
</html>

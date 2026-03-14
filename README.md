
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
            position: fixed; top: 15px; left: 50%; transform: translateX(-50%);
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





# Floating Buttons Script 🚀

This repository contains a **JavaScript snippet** that dynamically injects a **bottom-center floating button group** on any website, ideal for Blogger pages, WordPress themes, or any HTML-based site.
<p align="center">
  <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/07/designacleanandmodernpromotionalgraphicshowcasingfloatingactionbuttonsonawebpageinterface7387608098757600163.jpg" alt="Firebase Front-End Components Preview" width="600"/>
</p>
---

## 🎯 Features

- Responsive floating button group at **bottom center**
- Fully customizable **text**, **URL**, and **background color** for each button
- Lightweight and dependency-free script
- Perfect for promos, contact links, home links, or social buttons

---

## 📦 File

### `floating-buttons.js`

The core script that:
- Waits for the page to load
- Creates a styled button wrapper `<div>`
- Inserts button `<a>` elements based on the `buttons` array

---

## 🛠️ Setup Instructions

1. Clone or download this repo.
2. Adjust the `buttons` array in `floating-buttons.js` with your desired labels, links, and colors.
3. Push `floating-buttons.js` to your GitHub repository.
4. Enable **GitHub Pages** on this repo (Settings → Pages → select `main` branch).
5. Your script will be available at:



# 🚀 DeBeatzGH – AI Tools & Side Hustle Hub  

![DeBeatzGH Thumbnail](https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designamodernminimalisticdesignfeaturinganai-themedicon28likeabraincircuitorrobot29overlaidwithdebeatzghoraitoolshustles6089986211026037047.jpg)  

## 🌟 About  
Welcome to **[DeBeatzGH](https://debeatzgh.wordpress.com/)** — your go-to hub for **AI tools, side hustle strategies, blogging resources, and digital growth guides**.  

Our platform is built to help **students, creators, startups, and professionals** unlock the power of AI, monetize their skills, and thrive in today’s digital economy.  

### ✨ What You’ll Find  
- 💡 Explore **AI prompts, tools, and hacks**  
- 📈 Discover **side hustle strategies & online income ideas**  
- ✍️ Access **blogging & digital business guides**  
- 🚀 Stay ahead with **regular updates and fresh insights**  

---

## 👉 Get Started  
🔥 **Start your journey today → [Visit DeBeatzGH](https://debeatzgh.wordpress.com/)**  

---
<!-- README: DebeatzGH Digital Store (HTML-friendly for GitHub) -->
<div align="center">
  <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener">
    <img
      src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg"
      alt="DebeatzGH Digital Store"
      style="max-width:100%; border-radius:16px;"
    />
  </a>

  <h1 style="margin-top: 14px;">DebeatzGH Digital Store</h1>
  <p style="max-width:780px;">
    Your hub for AI insights, tech tutorials, side-hustle playbooks, and productivity tools.
    Learn, build, and launch digital projects faster.
  </p>

  <!-- CTAs -->
  <p>
    <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin:4px; border-radius:999px; text-decoration:none; font-weight:600; border:1px solid #2563eb;">
      🚀 View Live App
    </a>
    <a href="https://github.com/debeatzgh1/Personal-Portfolio-site-" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin:4px; border-radius:999px; text-decoration:none; font-weight:600; border:1px solid #111827;">
      ⭐ Star this Repo
    </a>
  </p>
</div>

<hr/>

<h2>Overview</h2>
<p>
  <strong>DebeatzGH</strong> helps beginners and creators build profitable digital assets:
  blogs, affiliate funnels, AI-assisted content, and more. Explore tutorials, tools, and
  ready-to-use components to speed up your workflow.
</p>

<h2>Features</h2>
<ul>
  <li><strong>AI & Tech Learning:</strong> Bite-sized guides for modern tools and workflows.</li>
  <li><strong>Side-Hustle Playbooks:</strong> Practical steps to validate and launch ideas.</li>
  <li><strong>Productivity Toolkit:</strong> Reusable widgets, templates, and scripts.</li>
  <li><strong>Beginner-Friendly:</strong> Clear explanations, curated resources, and examples.</li>
</ul>

<h2>Quick Start</h2>
<ol>
  <li>Clone:
    <pre><code>git clone https://github.com/debeatzgh1/Personal-Portfolio-site-</code></pre>
  </li>
  <li>Enter folder:
    <pre><code>cd debeatzgh</code></pre>
  </li>
  <li>Install deps (adjust to your stack):
    <pre><code># Node
npm install
npm run dev

# or Python
pip install -r requirements.txt
python app.py</code></pre>
  </li>
  <li>Open in browser:
    <pre><code>http://localhost:3000</code></pre>
  </li>
</ol>

<h2>Project Links</h2>
<ul>
  <li>🌐 Live App: <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener">socialcreator.com/debeatzgh</a></li>
  <li>🖼️ Thumbnail: <a href="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg" target="_blank" rel="noopener">View image</a></li>
</ul>

<h2>Contributing</h2>
<p>
  Contributions are welcome! Open an issue for bugs or ideas. For changes, fork the repo,
  create a feature branch, and submit a pull request.
</p>

<h2>License</h2>
<p>
  Released under the <a href="./LICENSE">MIT License</a>.
</p>

<hr/>

<div align="center">
  <p><em>If this project helps you, consider giving it a star. It really helps! ⭐</em></p>
  <p>
    <a href="https://www.socialcreator.com/debeatzgh" target="_blank" rel="noopener"
       style="display:inline-block; padding:10px 16px; margin-top:6px; border-radius:10px; text-decoration:none; font-weight:600; border:1px solid #2563eb;">
      Open DebeatzGH Now →
    </a>
  </p>
</div>


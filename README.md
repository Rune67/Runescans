<!doctype html>

<html lang="en">  
<head>  
<meta charset="utf-8" />  
<meta name="viewport" content="width=device-width,initial-scale=1" />  
<title>RuneScans — Premium Manhwa Reader</title>  
<style>  
:root{  
  --primary:#2d2d6b;  
  --accent:#6366f1;  
  --bg:#f4f4f9;  
  --bg-dark:#0f1226;  
  --text:#222;  
  --muted:#666;  
  --card:#ffffff;  
  --card-dark:#1f2233;  
  --radius:12px;  
}  
*{box-sizing:border-box}  
body{  
  margin:0;font-family:Inter,Arial,sans-serif;background:var(--bg);color:var(--text);-webkit-font-smoothing:antialiased;  
}  
body.dark{background:var(--bg-dark);color:#e6e9ff}  
.header{  
  background:linear-gradient(135deg,var(--primary),var(--accent));color:#fff;text-align:center;padding:34px 16px 28px;  
}  
.header h1{font-size:28px;margin:0 0 6px;letter-spacing:1px}  
.header p{margin:0 0 18px;opacity:.95}  
.search-container{max-width:720px;margin:0 auto;position:relative}  
.search-bar{width:100%;padding:12px 14px 12px 44px;border-radius:999px;border:0;font-size:15px}  
.search-icon{position:absolute;left:14px;top:50%;transform:translateY(-50%);opacity:.9}  
.dark-toggle{position:fixed;right:12px;top:12px;padding:10px 12px;border-radius:10px;border:0;background:rgba(255,255,255,0.08);color:#fff;cursor:pointer;z-index:999}  
nav{display:flex;gap:8px;justify-content:center;padding:12px;background:var(--card);border-bottom:1px solid #e8e8f0;position:sticky;top:0;z-index:90}  
body.dark nav{background:var(--card-dark);border-color:#222}  
nav button{border:2px solid var(--primary);background:none;color:var(--primary);padding:8px 14px;border-radius:10px;cursor:pointer;font-weight:600}  
nav button.active,nav button:hover{background:var(--primary);color:#fff}  
.container{max-width:1200px;margin:28px auto;padding:0 18px}  
.section{display:none}  
.section.active{display:block}  
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:18px}  
.grid.featured{grid-template-columns:repeat(auto-fit,minmax(260px,1fr))}  
.card{  
  background:var(--card);border-radius:var(--radius);overflow:hidden;box-shadow:0 8px 24px rgba(18,24,47,0.06);cursor:pointer;transition:all .18s ease;  
}  
body.dark .card{background:var(--card-dark);box-shadow:0 8px 30px rgba(0,0,0,0.45)}  
.card:hover{transform:translateY(-6px)}  
.card img{width:100%;height:280px;object-fit:cover;display:block}  
.card-content{padding:12px}  
.card-title{font-weight:700;font-size:16px;margin-bottom:6px}  
.card-meta{display:flex;justify-content:space-between;align-items:center;font-size:13px;color:var(--muted);margin-bottom:8px}  
.genre{display:inline-block;padding:6px 8px;border-radius:999px;background:#f3f4f6;color:#374151;font-size:12px;margin-right:6px}  
body.dark .genre{background:#2b2b3c;color:#cbd5ff}  
.filters{display:flex;gap:10px;justify-content:center;margin-bottom:18px;flex-wrap:wrap}  
.filter-select{padding:8px;border-radius:8px;border:1px solid #e6e6f0;background:var(--card);min-width:140px}  .reader-header{display:flex;justify-content:space-between;align-items:center;gap:12px;padding:14px;background:var(--card);border-radius:12px;margin-bottom:18px;flex-wrap:wrap}
body.dark .reader-header{background:var(--card-dark)}
.reader-controls{display:flex;gap:8px;align-items:center}
.btn{background:var(--primary);border:0;color:#fff;padding:8px 12px;border-radius:10px;cursor:pointer;font-weight:600}
.btn.secondary{background:#6b7280}
.btn:disabled{opacity:.5;cursor:not-allowed}

.pages{display:flex;flex-direction:column;gap:18px;align-items:center}
.pages img{width:100%;max-width:850px;border-radius:10px;box-shadow:0 8px 30px rgba(2,6,23,0.08)}

.modal{position:fixed;left:0;top:0;width:100%;height:100%;background:rgba(0,0,0,0.6);display:none;align-items:center;justify-content:center;z-index:9999;padding:18px}
.modal.active{display:flex}
.modal-content{background:var(--card);border-radius:12px;padding:18px;max-width:980px;width:100%;max-height:90vh;overflow:auto}
body.dark .modal-content{background:var(--card-dark)}
.modal-grid{display:grid;grid-template-columns:220px 1fr;gap:18px}
.chapters-list{max-height:260px;overflow:auto}
.chapter-item{padding:10px;border-radius:8px;border:1px solid #eee;margin-bottom:8px;cursor:pointer}
body.dark .chapter-item{border-color:#333}
.chapter-item:hover{background:var(--primary);color:#fff}

.footer{background:#0b0b12;color:#aaa;text-align:center;padding:20px;margin-top:36px;border-top:1px solid rgba(255,255,255,0.02)}

/* small tweaks mobile */
@media (max-width:720px){
.card img{height:200px}
.header h1{font-size:22px}
.modal-grid{grid-template-columns:1fr}
}
</style>

</head>  
<body>  <button class="dark-toggle" onclick="toggleDark()" id="darkBtn">🌙</button>

<header class="header">  
  <h1>RuneScans</h1>  
  <p>Premium manhwa translations — credit to original creators.</p>  
  <div class="search-container" style="margin-top:12px">  
    <span class="search-icon">🔎</span>  
    <input id="searchInput" class="search-bar" placeholder="Search titles, authors, genres..." oninput="handleSearch(this.value)">  
  </div>  
</header>  <nav>  
  <button onclick="navTo('home')" class="active">Home</button>  
  <button onclick="navTo('library')">Library</button>  
  <button onclick="navTo('latest')">Latest</button>  
  <button onclick="navTo('about')">About</button>  
</nav>  <main class="container">    <section id="home" class="section active">  
    <h2 style="text-align:center;margin-bottom:12px">🔥 Featured</h2>  
    <div id="featured-grid" class="grid featured"></div>  <h2 style="text-align:center;margin:28px 0 12px">All Series</h2>  
<div id="home-grid" class="grid"></div>

  </section>    <section id="library" class="section">  
    <h2 style="text-align:center;margin-bottom:12px">Library</h2>  <div class="filters">  
  <select id="genreFilter" class="filter-select" onchange="applyFilters()">  
    <option value="">All Genres</option>  
  </select>  
  <select id="statusFilter" class="filter-select" onchange="applyFilters()">  
    <option value="">All Status</option>  
    <option value="ongoing">Ongoing</option>  
    <option value="completed">Completed</option>  
    <option value="hiatus">Hiatus</option>  
  </select>  
  <button class="btn secondary" onclick="clearFilters()">Clear</button>  
</div>  

<div id="library-grid" class="grid"></div>

  </section>    <section id="latest" class="section">  
    <h2 style="text-align:center;margin-bottom:12px">Latest Updates</h2>  
    <div id="latest-grid" class="grid"></div>  
  </section>    <section id="reader" class="section">  
    <div class="reader-header">  
      <div>  
        <h2 id="reader-title" style="margin:0">Reader</h2>  
        <div id="reader-subtitle" style="color:var(--muted);font-size:14px"></div>  
      </div>  
      <div class="reader-controls">  
        <button class="btn secondary" onclick="prevChapter()" id="prevChapBtn">← Prev Chap</button>  
        <button class="btn" onclick="navTo('library')">Library</button>  
        <button class="btn secondary" onclick="nextChapter()" id="nextChapBtn">Next Chap →</button>  
      </div>  
    </div>  <div id="reader-pages" class="pages"></div>  

<div style="text-align:center;margin-top:18px;">  
  <div id="chapter-nav" style="display:flex;gap:6px;flex-wrap:wrap;justify-content:center"></div>  
</div>

  </section>    <section id="about" class="section">  
    <h2 style="text-align:center;margin-bottom:12px">About RuneScans</h2>  
    <div style="max-width:760px;margin:0 auto;text-align:center;color:var(--muted);line-height:1.6">  
      <p>We assemble translations for the love of stories. This demo is for development/testing — always credit and support original creators and official publishers.</p>  
    </div>  
  </section>  </main>  <div id="series-modal" class="modal" aria-hidden="true">  
  <div class="modal-content" role="dialog" aria-modal="true">  
    <button class="modal-close" onclick="closeModal()" style="position:absolute;right:14px;top:12px;border:none;background:none;font-size:22px;cursor:pointer">✕</button>  
    <div id="modal-body"></div>  
  </div>  
</div>  <footer class="footer">© 2025 RuneScans — Demo. Support creators.</footer>  <script>  
// ---------- DATA (add more series by copying object) ----------  
const seriesData = [  
  {  
    id: 'tbate',  
    title: "The Beginning After The End",  
    description: "King Grey has unrivaled strength, wealth, and prestige in a world governed by martial ability. Reincarnated into a new world filled with magic and monsters, he must find a new purpose.",  
    genres: ["Fantasy","Action","Adventure","Reincarnation"],  
    status: "ongoing",  
    rating: 9.3,  
    author: "TurtleMe",  
    artist: "Fuyuki23",  
    cover: "https://i.ibb.co/7CgFgjxN/The-Beginning-After-the-End-Cover.jpg",  
    chapters: [  
      {  
        number: 1,  
        title: "Chapter 1",  
        pages: [  
"https://i.ibb.co/BKLNzMLf/mnWqBo.jpg",  
"https://meo.comick.pictures/0--RakS48THQjg3.jpg",  
"https://meo.comick.pictures/1-IZwNenqlv2e2i.jpg",  
"https://meo.comick.pictures/2-P_GZdP5PkumHr.jpg",  
"https://meo.comick.pictures/3-vgfJrdAJZmqdq.jpg",  
"https://meo.comick.pictures/4-mXDMdiuAMq1qN.jpg",  
"https://meo.comick.pictures/5-nUn7nys3Q5QjC.jpg",  
"https://meo.comick.pictures/6-JS531MnQP2yMQ.jpg",  
"https://meo.comick.pictures/7-HF_VtdQfLiL_e.jpg",  
"https://meo.comick.pictures/8-lVb26MtNwUQkZ.jpg",  
"https://meo.comick.pictures/9-75So2Nn5eckZ4.jpg",  
"https://i.ibb.co/b5CLjwvN/The-Beginning-After-the-End-Chapter-1-11.jpg",  
"https://i.ibb.co/nMrYMSSn/The-Beginning-After-the-End-Chapter-1-12.jpg",  
"https://i.ibb.co/xSkNmc5q/The-Beginning-After-the-End-Chapter-1-13.jpg",  
"https://i.ibb.co/TD1tFg18/The-Beginning-After-the-End-Chapter-1-14.jpg",  
"https://i.ibb.co/0pB7Grjr/The-Beginning-After-the-End-Chapter-1-15.jpg",  
"https://i.ibb.co/BVPLN7ff/The-Beginning-After-the-End-Chapter-1-16.jpg",  
"https://i.ibb.co/Y7mpypj0/The-Beginning-After-the-End-Chapter-1-17.jpg",  
"https://i.ibb.co/Swyjpg9n/The-Beginning-After-the-End-Chapter-1-18.gif",  
"https://i.ibb.co/mVhPpqLn/The-Beginning-After-the-End-Chapter-1-19.jpg",  
"https://i.ibb.co/9HMgtrxH/The-Beginning-After-the-End-Chapter-1-20.jpg",  
"https://i.ibb.co/23jV67DT/The-Beginning-After-the-End-Chapter-1-21.jpg",  
"https://i.ibb.co/4wZkWc8n/The-Beginning-After-the-End-Chapter-1-22.jpg",  
"https://i.ibb.co/nqPqkT2V/The-Beginning-After-the-End-Chapter-1-23.jpg",  
"https://i.ibb.co/Kx8nGhYT/The-Beginning-After-the-End-Chapter-1-24.jpg",  
"https://i.ibb.co/tw36r7k9/The-Beginning-After-the-End-Chapter-1-25.jpg",  
"https://i.ibb.co/v676Z9jT/The-Beginning-After-the-End-Chapter-1-26.gif",  
"https://i.ibb.co/cKF3NJMS/The-Beginning-After-the-End-Chapter-1-27.jpg",  
"https://i.ibb.co/Xx7DJNf3/The-Beginning-After-the-End-Chapter-1-28.jpg",  
"https://i.ibb.co/YFZjWpn1/The-Beginning-After-the-End-Chapter-1-29.jpg",  
"https://i.ibb.co/0R0LcCpZ/The-Beginning-After-the-End-Chapter-1-30.gif",  
"https://i.ibb.co/cBGmj4h/The-Beginning-After-the-End-Chapter-1-31.jpg",  
"https://i.ibb.co/C56Z3tT3/The-Beginning-After-the-End-Chapter-1-32.jpg",  
"https://i.ibb.co/GQLdrTYs/The-Beginning-After-the-End-Chapter-1-33.jpg",  
"https://i.ibb.co/5x29GXV6/The-Beginning-After-the-End-Chapter-1-34.jpg",  
"https://i.ibb.co/Fqq8B8xY/The-Beginning-After-the-End-Chapter-1-35.jpg",  
"https://i.ibb.co/8gJB9FwF/The-Beginning-After-the-End-Chapter-1-36.jpg",  
"https://i.ibb.co/MDLBK6wh/The-Beginning-After-the-End-Chapter-1-37.jpg",  
"https://i.ibb.co/m55KfSvn/The-Begining-After-the-End-Chapter-1-38.jpg".replace('The-Begining','The-Beginning'),  
"https://i.ibb.co/k2pbr6XW/The-Beginning-After-the-End-Chapter-1-39.jpg",  
"https://i.ibb.co/0ymBHWCN/The-Beginning-After-the-End-Chapter-1-40.gif",  
"https://i.ibb.co/wFxtgwM6/The-Beginning-After-the-End-Chapter-1-41.jpg",  
"https://i.ibb.co/ZzZWX81N/The-Beginning-After-the-End-Chapter-1-42.gif",  
"https://i.ibb.co/BKCy8SbZ/The-Beginning-After-the-End-Chapter-1-43.jpg",  
"https://i.ibb.co/Wp3Pc4CS/The-Beginning-After-the-End-Chapter-1-44.jpg",  
"https://i.ibb.co/TDVywTB6/The-Beginning-After-the-End-Chapter-1-45.gif",  
"https://i.ibb.co/Xx5MrgyX/The-Beginning-After-the-End-Chapter-1-46.gif",  
"https://i.ibb.co/Qj87C6Gk/The-Beginning-After-the-End-Chapter-1-47.gif",  
"https://i.ibb.co/1GMnwTkx/The-Beginning-After-the-End-Chapter-1-48.jpg",  
"https://i.ibb.co/HDNk8hJr/The-Beginning-After-the-End-Chapter-1-49.jpg",  
"https://i.ibb.co/hJGsPVLv/The-Beginning-After-the-End-Chapter-1-50.jpg"  
        ]  
      }  
    ]  
  },  
  // sample additional series (covers are placeholders; replace with real covers if you have them)  
  {  
    id: 'solo',  
    title: 'Solo Leveling',  
    description: 'An E-rank hunter rises.',  
    genres: ['Action','Adventure'],  
    status: 'completed',  
    rating: 9.5,  
    author: 'Chugong',  
    artist: 'DUBU',  
    cover: 'https://images.unsplash.com/photo-1609743522653-52354461eb27?auto=format&fit=crop&w=400&q=80',  
    chapters: [  
      { number: 1, title: 'Chapter 1', pages: ['https://images.unsplash.com/photo-1578662996442-48f60103fc96?auto=format&fit=crop&w=800&q=80'] }  
    ]  
  },  
  {  
    id: 'tower',  
    title: 'Tower of God',  
    description: 'Bam climbs the Tower.',  
    genres: ['Fantasy','Adventure'],  
    status: 'ongoing',  
    rating: 9.0,  
    author: 'SIU',  
    artist: 'SIU',  
    cover: 'https://images.unsplash.com/photo-1541963463532-d68292c34d19?auto=format&fit=crop&w=400&q=80',  
    chapters: [  
      { number: 1, title: 'Headon\'s Floor', pages: ['https://images.unsplash.com/photo-1581833971358-2c8b550f87b3?auto=format&fit=crop&w=800&q=80'] }  
    ]  
  }  
];  
  
// ---------- STATE ----------  
let currentSeries = null;    // object ref  
let currentChapterIndex = 0;  
let filtered = seriesData.slice();  
  
// ---------- UTIL ----------  
function el(t, props={}, ...kids){  
  const E = document.createElement(t);  
  for(const k in props) { if(k.startsWith('on') && typeof props[k] === 'function') E.addEventListener(k.slice(2), props[k]); else E.setAttribute(k, props[k]); }  
  kids.flat().forEach(n => { if(typeof n === 'string') E.appendChild(document.createTextNode(n)); else if(n) E.appendChild(n); });  
  return E;  
}  
  
// ---------- NAV / INIT ----------  
function navTo(id, btn){  
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));  
  document.querySelectorAll('nav button').forEach(b => b.classList.remove('active'));  
  document.getElementById(id).classList.add('active');  
  if(btn) btn.classList.add('active');  
}  
function toggleDark(){  
  document.body.classList.toggle('dark');  
  document.getElementById('darkBtn').textContent = document.body.classList.contains('dark') ? '☀️' : '🌙';  
}  
  
// ---------- RENDER ----------  
function renderAll(){  
  renderFeatured();  
  renderGrid('home-grid', filtered);  
  renderGrid('library-grid', filtered);  
  renderGrid('latest-grid', filtered.slice(0,8));  
  populateGenreSelect();  
}  
function renderFeatured(){  
  const f = filtered.slice(0,3);  
  const g = document.getElementById('featured-grid');  
  g.innerHTML = '';  
  f.forEach(s => g.appendChild(seriesCard(s,true)));  
}  
function renderGrid(id, data){  
  const wrap = document.getElementById(id);  
  wrap.innerHTML = '';  
  data.forEach(s => wrap.appendChild(seriesCard(s)));  
}  
function seriesCard(series, big=false){  
  const card = el('div',{class:'card',onclick:()=>openSeriesModal(series)});  
  const img = document.createElement('img');  
  img.src = series.cover;  
  img.loading = 'lazy';  
  card.appendChild(img);  
  
  const cont = el('div',{class:'card-content'});  
  const meta = el('div',{class:'card-meta'}, el('span',{}, series.status), el('span',{}, '⭐ '+series.rating));  
  cont.appendChild(meta);  
  cont.appendChild(el('h3',{class:'card-title'}, series.title));  
  const genres = el('div',{class:'genres'});  
  series.genres.slice(0,3).forEach(g => genres.appendChild(el('span',{class:'genre'}, g)));  
  cont.appendChild(genres);  
  card.appendChild(cont);  
  return card;  
}  
  
// ---------- SEARCH / FILTERS ----------  
function handleSearch(q){  
  q = q.trim().toLowerCase();  
  if(!q){ filtered = seriesData.slice(); renderAll(); return; }  
  filtered = seriesData.filter(s =>  
    s.title.toLowerCase().includes(q) ||  
    s.description.toLowerCase().includes(q) ||  
    s.author.toLowerCase().includes(q) ||  
    s.genres.join(' ').toLowerCase().includes(q)  
  );  
  renderAll();  
}  
function populateGenreSelect(){  
  const set = new Set();  
  seriesData.forEach(s => s.genres.forEach(g => set.add(g)));  
  const sel = document.getElementById('genreFilter');  
  const current = sel.value || '';  
  sel.innerHTML = '<option value=\"\">All Genres</option>';  
  Array.from(set).sort().forEach(g => { sel.appendChild(el('option',{value:g},g)); });  
  sel.value = current;  
}  
function applyFilters(){  
  const g = document.getElementById('genreFilter').value;  
  const st = document.getElementById('statusFilter').value;  
  filtered = seriesData.filter(s => ( !g || s.genres.includes(g) ) && ( !st || s.status === st ));  
  renderAll();  
}  
function clearFilters(){  
  document.getElementById('genreFilter').value = '';  
  document.getElementById('statusFilter').value = '';  
  document.getElementById('searchInput').value = '';  
  filtered = seriesData.slice();  
  renderAll();  
}  
  
// ---------- MODAL / SERIES VIEW ----------  
function openSeriesModal(series){  
  currentSeries = series;  
  const modal = document.getElementById('series-modal');  
  const body = document.getElementById('modal-body');  
  body.innerHTML = '';  
  
  // modal grid  
  const left = el('div',{}, el('img',{src:series.cover, style:'width:100%;border-radius:8px;', loading:'lazy'}));  
  const right = el('div',{},  
    el('h2',{}, series.title),  
    el('p',{}, series.description),  
    el('p',{}, 'Author: ' + (series.author||'—')),  
    el('p',{}, 'Status: ' + (series.status||'—')),  
    el('div',{style:'margin-top:10px;'}, ...series.genres.map(g=>el('span',{class:'genre', style:'margin-right:6px'}, g)))  
  );  
  
  const topGrid = el('div',{class:'modal-grid'});  
  topGrid.appendChild(left);  
  topGrid.appendChild(right);  
  body.appendChild(topGrid);  
  
  // chapters list  
  body.appendChild(el('h4',{}, 'Chapters'));  
  const list = el('div',{class:'chapters-list'});  
  series.chapters.slice().reverse().forEach((ch,i) => { // reversed to show latest on top  
    const ci = el('div',{class:'chapter-item', onclick:()=>openChapterByObject(series, series.chapters.length-1-i)}, `Chapter ${ch.number}: ${ch.title}`);  
    list.appendChild(ci);  
  });  
  body.appendChild(list);  
  
  modal.classList.add('active');  
  modal.setAttribute('aria-hidden','false');  
}  
  
function closeModal(){  
  const modal = document.getElementById('series-modal');  
  modal.classList.remove('active');  
  modal.setAttribute('aria-hidden','true');  
}  
  
// ---------- READER ----------  
function openChapterByObject(seriesObj, chapterIndex){  
  // find series by id in data (so state is consistent)  
  currentSeries = seriesObj;  
  currentChapterIndex = chapterIndex;  
  loadReader();  
  closeModal();  
  navTo('reader', document.querySelector("nav button[onclick=\"navTo('library')\"]"));  
  // add active to reader nav  
  document.querySelectorAll('nav button').forEach(b=>b.classList.remove('active'));  
  document.querySelector("nav button[onclick=\"navTo('library')\"]")?.classList.remove('active');  
  // mark reader section active  
  document.querySelectorAll('.section').forEach(s=>s.classList.remove('active'));  
  document.getElementById('reader').classList.add('active');  
}  
  
function loadReader(){  
  if(!currentSeries) return;  
  const chapter = currentSeries.chapters[currentChapterIndex];  
  if(!chapter) return;
  document.getElementById('reader-title').textContent = currentSeries.title + ' — Chapter ' + chapter.number;  
  document.getElementById('reader-subtitle').textContent = chapter.title || '';  
  const pages = document.getElementById('reader-pages');  
  pages.innerHTML = '';  
  
  // chapter navigation buttons  
  const chapterNav = document.getElementById('chapter-nav');  
  chapterNav.innerHTML = '';  
  currentSeries.chapters.forEach((ch, idx) => {  
    const b = el('button',{class:'btn secondary', onclick:()=>{ currentChapterIndex = idx; loadReader(); }}, 'Ch '+ch.number);  
    chapterNav.appendChild(b);  
  });  
  

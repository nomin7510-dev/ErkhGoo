# ErkhGoo
Goo_Bday
<!doctype html>
<html lang="mn">
<head>
<meta charset="utf-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1"/>
<title>🎀 Goomaral-ийн Surprise (Түгжээтэй)</title>
<style>
  :root{
    --bg1:#fff0f5; --bg2:#ffe6f0; --accent:#ff69b4; --muted:#6b6b6b;
  }
  *{box-sizing:border-box}
  body{
    margin:0; font-family:Inter, "Poppins", system-ui, sans-serif;
    background: linear-gradient(180deg,var(--bg1),var(--bg2));
    color:#222; min-height:100vh; display:flex; align-items:center; justify-content:center;
    padding:24px;
  }
  .wrap{width:100%;max-width:980px;background:rgba(255,255,255,0.9);border-radius:18px;padding:22px;box-shadow:0 12px 40px rgba(0,0,0,0.08); position:relative; overflow:hidden;}
  header{display:flex;align-items:center;gap:16px;}
  .logo{width:72px;height:72px;border-radius:14px;background:linear-gradient(45deg,#ffd6e8,#ffc1e3);display:flex;align-items:center;justify-content:center;font-size:28px;color:#fff;box-shadow:0 6px 18px rgba(255,105,180,0.14)}
  h1{margin:0;font-size:28px;color:var(--accent)}
  p.lead{margin:6px 0 0;color:var(--muted)}

  /* locked view */
  .locked{margin-top:18px;padding:18px;border-radius:12px;background:linear-gradient(180deg,rgba(255,255,255,0.6),rgba(255,255,255,0.4));border:1px solid rgba(255,105,180,0.08)}
  .countdown{display:flex;gap:10px;justify-content:center;margin-top:12px}
  .cd-item{background:#fff;padding:10px 12px;border-radius:10px;min-width:70px;text-align:center;box-shadow:0 6px 16px rgba(0,0,0,0.05)}
  .cd-item .num{font-weight:700;font-size:18px;color:#111}
  .cd-item .lbl{font-size:12px;color:var(--muted)}

  /* inputs */
  .inputs{display:flex;gap:12px;margin-top:14px;flex-wrap:wrap}
  textarea, input[type="text"], input[type="file"]{width:100%;padding:10px;border-radius:10px;border:1px solid #eee}
  .col{flex:1;min-width:220px}
  .btn{background:var(--accent);color:#fff;padding:10px 12px;border-radius:10px;border:0;cursor:pointer}
  .small{font-size:13px;color:var(--muted);margin-top:8px}

  /* content (after unlock) */
  .content{display:none;margin-top:18px}
  .hero{display:flex;gap:18px;align-items:center}
  .hero .left{flex:1}
  .hero .right{width:320px}
  .message-box{padding:14px;border-radius:12px;background:rgba(255,255,255,0.85);border:1px dashed rgba(255,105,180,0.08)}
  .reveal{margin-top:12px}
  .reveal .secret{background:#fff;padding:12px;border-radius:10px;min-height:60px;display:flex;align-items:center;justify-content:center;font-size:16px;color:var(--muted)}
  .reveal button{margin-top:8px}

  /* gallery */
  .gallery{margin-top:14px;display:flex;gap:10px;align-items:center}
  .thumb{width:120px;height:80px;border-radius:8px;object-fit:cover;border:1px solid #eee}
  .carousel{position:relative;width:100%;height:380px;border-radius:12px;overflow:hidden;background:#fff;display:flex;align-items:center;justify-content:center}
  .carousel img{max-width:100%;max-height:100%;object-fit:contain}

  /* hearts background */
  .hearts{position:absolute;inset:0;pointer-events:none;z-index:-1}

  footer{margin-top:18px;text-align:center;color:var(--muted);font-size:13px}
  @media (max-width:880px){ .hero{flex-direction:column} .hero .right{width:100%} .carousel{height:260px} }
</style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="logo">G♡</div>
      <div>
        <h1>Goomaral-д зориулсан гэнэтийн бэлэг</h1>
        <p class="lead">🎀 Romantic • Cute • Lofi — 2026-10-17-нд нээгдэх</p>
      </div>
    </header>

    <!-- LOCKED view -->
    <div id="locked" class="locked">
      <div style="text-align:center">
        <strong style="font-size:18px">⏳ Энэ хуудас 2025.10.17-нд нээгдэнэ</strong>
        <div class="countdown" id="countdown">
          <div class="cd-item"><div class="num" id="cd-days">--</div><div class="lbl">өдөр</div></div>
          <div class="cd-item"><div class="num" id="cd-hours">--</div><div class="lbl">цаг</div></div>
          <div class="cd-item"><div class="num" id="cd-mins">--</div><div class="lbl">мин</div></div>
          <div class="cd-item"><div class="num" id="cd-secs">--</div><div class="lbl">сек</div></div>
        </div>
      </div>

      <div style="margin-top:14px">
        <div class="small">Хэн нэгэн одоо мэндчилгээ бичиж хадгалж болно — хуудас нээгдсэн үед тэр мессеж автоматаар харагдана.</div>

        <div class="inputs" style="margin-top:10px">
          <div class="col">
            <label>Таны мэндчилгээ (Goomaral-д зориулсан богино үг)</label>
            <textarea id="guestMessage" rows="3" placeholder="Жишээ: Амжилт, хайр, инээмсэглэл..."></textarea>
          </div>

          <div style="width:220px">
            <label>Зураг оруулах (хамгийн их 5)</label>
            <input id="imageInput" type="file" accept="image/*" multiple>
            <div class="small">Upload-с зургуудаа оруулна уу. (Тодруулга: энэ нь таны браузер дээр л хадгалагдана)</div>
          </div>
        </div>

        <div style="display:flex;gap:10px;margin-top:12px">
          <button id="saveBtn" class="btn">💾 Мессеж & зураг хадгалах</button>
          <button id="clearBtn" class="btn" style="background:#aaa">🗑 Цэвэрлэх</button>
        </div>
        <div id="saveStatus" class="small" style="margin-top:8px;color:green"></div>
      </div>
    </div>

    <!-- CONTENT (shown after unlock) -->
    <div id="content" class="content">
      <div class="hearts" id="hearts"></div>

      <div class="hero">
        <div class="left">
          <div class="message-box">
            <h2>🎂 Happy Birthday, Goomaral 💕</h2>
            <p style="margin:6px 0 0;color:var(--muted)">Чамайг инээмсэглэл, хайр, аз жаргалаар дүүрэн өдөр угтаасай ✨</p>

            <div class="reveal">
              <div id="secret" class="secret" style="margin-top:12px">🔒 Нууц мессеж хаалттай байна</div>
              <button id="revealBtn" class="btn" style="margin-top:8px">🔓 Мессежийг нээнэ</button>
            </div>

            <div style="margin-top:12px">
              <h4 style="margin:6px 0">Guest мессежүүд:</h4>
              <div id="guestList" style="min-height:40px;color:var(--muted)"></div>
            </div>
          </div>
        </div>

        <div class="right">
          <div class="carousel" id="carousel">
            <img id="carouselImg" src="" alt="Goomaral images" />
          </div>
          <div style="display:flex;gap:8px;margin-top:8px;align-items:center;justify-content:center">
            <button id="prev" class="btn" style="background:#fff;color:var(--accent);border:1px solid #ffd6e8">◀</button>
            <div id="thumbs" style="display:flex;gap:6px;overflow:auto;padding:4px"></div>
            <button id="next" class="btn" style="background:#fff;color:var(--accent);border:1px solid #ffd6e8">▶</button>
          </div>
        </div>
      </div>

      <!-- audio -->
      <audio id="music" loop>
        <source src="https://cdn.pixabay.com/download/audio/2023/03/09/audio_8bb6c34e58.mp3?filename=lofi-chill-14100.mp3" type="audio/mpeg">
      </audio>
    </div>

    <footer>Энэхүү хуудас нь таны браузер дээр мессеж/зурагыг түр хадгалдаг (сэрвэргүй). Хэрвээ та нийтэд ил болгохыг хүсвэл GitHub Pages эсвэл Netlify дээр байрлуулж, бусдад линк явуулна.</footer>
  </div>

<script>
/* ========== Settings ========== */
const unlockDate = new Date("2025-10-17 06:10:00"); // local time
const STORAGE_KEY = "goomaral_bday_v1";

/* ========== Countdown ========== */
function pad(n){return n<10?("0"+n):n}
function updateCountdown(){
  const now = new Date();
  let diff = Math.max(0, unlockDate - now);
  const days = Math.floor(diff / (1000*60*60*24));
  diff -= days * (1000*60*60*24);
  const hours = Math.floor(diff / (1000*60*60));
  diff -= hours * (1000*60*60);
  const mins = Math.floor(diff / (1000*60));
  diff -= mins * (1000*60);
  const secs = Math.floor(diff/1000);

  document.getElementById("cd-days").textContent = days;
  document.getElementById("cd-hours").textContent = pad(hours);
  document.getElementById("cd-mins").textContent = pad(mins);
  document.getElementById("cd-secs").textContent = pad(secs);

  if(new Date() >= unlockDate){
    showContent();
    clearInterval(cdInterval);
  }
}
const cdInterval = setInterval(updateCountdown, 500);
updateCountdown();

/* ========== Save guest message & images to localStorage ========== */
const saveBtn = document.getElementById("saveBtn");
const clearBtn = document.getElementById("clearBtn");
const guestMessageEl = document.getElementById("guestMessage");
const imageInput = document.getElementById("imageInput");
const saveStatus = document.getElementById("saveStatus");

saveBtn.addEventListener("click", async ()=>{
  const msg = guestMessageEl.value.trim();
  const files = Array.from(imageInput.files || []);
  // read images as data URLs (limit to 5)
  const images = [];
  for(let i=0;i<Math.min(files.length,5);i++){
    const f = files[i];
    if(!f.type.startsWith("image/")) continue;
    const data = await readFileAsDataURL(f);
    images.push(data);
  }
  // load old
  let data = JSON.parse(localStorage.getItem(STORAGE_KEY) || "{}");
  if(!data.messages) data.messages = [];
  if(msg) data.messages.push({text: msg, at: new Date().toISOString()});
  // append images
  if(!data.images) data.images = [];
  data.images = data.images.concat(images).slice(0,5); // keep up to 5
  localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
  saveStatus.textContent = "✅ Хадгалсан! (Хуудас нээгдсэн үед харагдана)";
  setTimeout(()=>saveStatus.textContent="",3000);
  guestMessageEl.value = "";
  imageInput.value = "";
});

clearBtn.addEventListener("click", ()=>{
  if(confirm("Та жинхэнэ local хадгалсан өгөгдлөө устгахдаа итгэлтэй байна уу?")){
    localStorage.removeItem(STORAGE_KEY);
    saveStatus.textContent = "🗑 Устгасан";
    setTimeout(()=>saveStatus.textContent="",2000);
  }
});

function readFileAsDataURL(file){
  return new Promise((res,rej)=>{
    const r = new FileReader();
    r.onload = ()=>res(r.result);
    r.onerror = ()=>rej();
    r.readAsDataURL(file);
  });
}

/* ========== Unlock: show content, load images & messages ========== */
const contentEl = document.getElementById("content");
const lockedEl = document.getElementById("locked");
const music = document.getElementById("music");
const secretEl = document.getElementById("secret");
const revealBtn = document.getElementById("revealBtn");
const guestList = document.getElementById("guestList");

// hearts floating
function spawnHeart(){
  const hearts = document.getElementById("hearts");
  const el = document.createElement("div");
  el.style.position="absolute";
  el.style.left = (Math.random()*100) + "%";
  el.style.bottom = "-30px";
  el.style.width = (12+Math.random()*18) + "px";
  el.style.height = el.style.width;
  el.style.transform = "rotate(45deg)";
  el.style.background = `hsl(${300 + Math.random()*40},80%,72%)`;
  el.style.opacity = 0.9;
  el.style.borderRadius = "4px";
  el.style.boxShadow="0 8px 18px rgba(0,0,0,0.06)";
  hearts.appendChild(el);
  const dur = 4000 + Math.random()*3000;
  el.animate([{transform:"translateY(0) rotate(45deg)", opacity:1},{transform:"translateY(-800px) rotate(45deg)", opacity:0}],{duration:dur, easing:"linear"});
  setTimeout(()=>el.remove(), dur+50);
}

let heartInt;
function startHearts(){ heartInt = setInterval(spawnHeart, 400); }
function stopHearts(){ clearInterval(heartInt); }

// show content
function showContent(){
  lockedEl.style.display = "none";
  contentEl.style.display = "block";
  // play music (try)
  music.play().catch(()=>{ /* autoplay block possible; user can press button */ });

  // load data
  const data = JSON.parse(localStorage.getItem(STORAGE_KEY) || "{}");
  // messages
  guestList.innerHTML = "";
  if(data.messages && data.messages.length){
    data.messages.forEach(m=>{
      const d = document.createElement("div");
      d.style.padding="8px"; d.style.borderBottom="1px solid #faf0f7";
      d.innerHTML = `<strong style="color:var(--accent)">${new Date(m.at).toLocaleString()}</strong><div style="margin-top:6px;color:#333">${escapeHtml(m.text)}</div>`;
      guestList.appendChild(d);
    });
  } else {
    guestList.innerHTML = `<div class="small" style="color:var(--muted)">Одоогоор мессеж байхгүй</div>`;
  }

  // images to carousel
  const imgs = (data.images || []);
  const carouselImg = document.getElementById("carouselImg");
  const thumbs = document.getElementById("thumbs");
  thumbs.innerHTML = "";
  if(imgs.length){
    let idx = 0;
    carouselImg.src = imgs[idx];
    imgs.forEach((src,i)=>{
      const t = document.createElement("img");
      t.src = src; t.className="thumb"; t.style.width="72px"; t.style.height="52px"; t.style.borderRadius="6px";
      t.style.objectFit="cover"; t.style.cursor="pointer";
      t.addEventListener("click", ()=>{ idx = i; carouselImg.src = imgs[idx]; });
      thumbs.appendChild(t);
    });
    document.getElementById("prev").onclick = ()=>{ idx = (idx-1+imgs.length)%imgs.length; carouselImg.src = imgs[idx]; }
    document.getElementById("next").onclick = ()=>{ idx = (idx+1)%imgs.length; carouselImg.src = imgs[idx]; }
  } else {
    carouselImg.src = "";
    document.getElementById("carousel").innerHTML = `<div style="color:var(--muted)">Оруулсан зураг алга</div>`;
  }

  // reveal button action
  revealBtn.onclick = ()=> {
    const data = JSON.parse(localStorage.getItem(STORAGE_KEY) || "{}");
    const firstMsg = (data.messages && data.messages.length) ? data.messages[data.messages.length-1].text : null;
    if(firstMsg){
      secretEl.textContent = firstMsg;
      secretEl.style.color = "#111";
      revealBtn.style.display = "none";
    } else {
      secretEl.textContent = "Одоогоор нууц мессеж байхгүй";
    }
  };

  startHearts();
}

/* ========== Utility ========== */
function escapeHtml(unsafe) {
  return unsafe.replace(/[&<"']/g, function(m){ return ({'&':'&amp;','<':'&lt;','"':'&quot;',"'":'&#039;'}[m]); });
}

/* If already past unlock when page loads */
if(new Date() >= unlockDate) {
  showContent();
  clearInterval(cdInterval);
}
</script>
</body>
</html>

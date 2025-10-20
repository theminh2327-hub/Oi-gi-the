<!doctype html>
<html lang="vi">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Chúc mừng 20/10 🌸</title>
<style>
  :root{
    --bg1: #fff5f8;
    --bg2: #fff0ea;
    --accent: #ff5c8a;
    --muted: #6b6b6b;
    --card: rgba(255,255,255,0.85);
    --glass: rgba(255,255,255,0.6);
  }
  *{box-sizing:border-box}
  body{
    margin:0;
    font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    background: linear-gradient(160deg,var(--bg1),var(--bg2));
    min-height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    padding:28px;
    color:#222;
  }

  .frame{
    width:100%;
    max-width:920px;
    background: linear-gradient(180deg, rgba(255,255,255,0.85), rgba(255,255,255,0.9));
    border-radius:18px;
    padding:28px;
    box-shadow: 0 10px 40px rgba(20,20,40,0.08);
    display:grid;
    grid-template-columns: 1fr 420px;
    gap:22px;
    align-items:center;
  }

  .left{
    padding:14px 8px;
  }

  h1{
    margin:0 0 6px 0;
    font-size:28px;
    letter-spacing:0.2px;
  }
  p.lead{
    margin:0 0 14px 0;
    color:var(--muted);
    line-height:1.5;
  }

  .link-card{
    display:inline-flex;
    align-items:center;
    gap:12px;
    background:var(--card);
    padding:12px 16px;
    border-radius:12px;
    cursor:pointer;
    text-decoration:none;
    color:inherit;
    box-shadow: 0 6px 18px rgba(0,0,0,0.06);
    transition:transform .16s ease, box-shadow .16s ease;
  }
  .link-card:hover{ transform: translateY(-4px); box-shadow: 0 12px 30px rgba(0,0,0,0.08); }

  .link-card .emoji{
    font-size:28px;
    transform:translateY(-2px);
  }

  .meta{
    font-size:13px;
    color:#444;
  }

  .right{
    display:flex;
    align-items:center;
    justify-content:center;
    position:relative;
  }

  .flower {
    width:100%;
    max-width:380px;
    border-radius:12px;
    background: linear-gradient(180deg,#fff,#fff0f6);
    padding:18px;
    box-shadow: 0 8px 30px rgba(0,0,0,0.04);
    text-align:center;
  }

  .flower svg{ width:160px; height:auto; display:block; margin:0 auto 6px auto; }

  .cta {
    display:flex;
    gap:10px;
    margin-top:12px;
    justify-content:center;
    flex-wrap:wrap;
  }

  button, .btn {
    border:0;
    background:var(--accent);
    color:white;
    padding:10px 14px;
    border-radius:10px;
    cursor:pointer;
    font-weight:600;
    box-shadow: 0 8px 18px rgba(255,92,138,0.16);
  }
  .btn.secondary{
    background:transparent;
    color:var(--accent);
    border:1px solid rgba(255,92,138,0.12);
    box-shadow:none;
    font-weight:700;
  }
  small{display:block; color:var(--muted); margin-top:8px;}

  /* Modal */
  .modal-bg{
    position:fixed;
    inset:0;
    display:flex;
    align-items:center;
    justify-content:center;
    background:rgba(10,10,20,0.35);
    z-index:80;
    opacity:0;
    pointer-events:none;
    transition:opacity .18s ease;
  }
  .modal-bg.show{
    opacity:1;
    pointer-events:auto;
  }
  .modal{
    width:min(720px,94%);
    border-radius:14px;
    padding:22px;
    background:linear-gradient(180deg, #fff, #fff7fb);
    box-shadow: 0 20px 60px rgba(10,10,30,0.2);
    position:relative;
    overflow:hidden;
  }
  .modal .title{ font-size:22px; margin:0 0 8px 0; }
  .modal .msg{ color:#333; line-height:1.6; }

  .close-x{
    position:absolute;
    right:12px; top:10px;
    border-radius:8px; padding:6px; cursor:pointer;
    background:transparent; border:0; font-size:18px;
  }

  /* confetti canvas fills modal */
  canvas.confetti{
    position:absolute; inset:0; pointer-events:none;
  }

  /* responsive */
  @media (max-width:880px){
    .frame{ grid-template-columns:1fr; }
    .right{ order:-1; margin-bottom:4px; }
    .flower svg{ width:120px; }
  }
</style>
</head>
<body>
  <div class="frame" role="main" aria-labelledby="title">
    <div class="left">
      <h1 id="title">Chúc mừng 20/10 — Ngày Phụ nữ Việt Nam 🌸</h1>
      <p class="lead">Gửi đến những người phụ nữ xung quanh bạn: mẹ, chị, bạn bè — một lời chúc ấm áp và chân thành. Click nút bên dưới để mở hộp quà kỹ thuật số nhé.</p>

      <a class="link-card" id="openGreeting" role="button" title="Mở lời chúc">
        <span class="emoji">💐</span>
        <div>
          <div style="font-weight:700">Mở lời chúc 20/10</div>
          <div class="meta">Nhấn để hiện lời chúc, hiệu ứng confetti và nút chia sẻ</div>
        </div>
      </a>

      <div style="margin-top:18px;">
        <div style="display:flex; gap:10px; align-items:center; flex-wrap:wrap">
          <button class="btn" id="copyShare">Sao chép nội dung (copy)</button>
          <button class="btn secondary" id="downloadBtn">Tải về (.html)</button>
        </div>
        <small>Tip: Lưu file rồi gửi cho người nhận, hoặc upload lên Drive/GitHub Pages để có link công khai.</small>
      </div>
    </div>

    <div class="right">
      <div class="flower" aria-hidden="true">
        <!-- simple flower SVG -->
        <svg viewBox="0 0 120 120" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="hoa">
          <g transform="translate(60,60)">
            <g id="petals" fill="#ff9bb3" stroke="#ff5c8a" stroke-width="0.8">
              <ellipse rx="18" ry="28" transform="rotate(0) translate(0,-36)"/>
              <ellipse rx="18" ry="28" transform="rotate(45) translate(0,-36)"/>
              <ellipse rx="18" ry="28" transform="rotate(90) translate(0,-36)"/>
              <ellipse rx="18" ry="28" transform="rotate(135) translate(0,-36)"/>
              <ellipse rx="18" ry="28" transform="rotate(180) translate(0,-36)"/>
              <ellipse rx="18" ry="28" transform="rotate(225) translate(0,-36)"/>
              <ellipse rx="18" ry="28" transform="rotate(270) translate(0,-36)"/>
              <ellipse rx="18" ry="28" transform="rotate(315) translate(0,-36)"/>
            </g>
            <circle r="14" fill="#ffd27a" stroke="#ffb84a" stroke-width="0.6"/>
          </g>
        </svg>
        <div style="font-weight:700; margin-top:8px">20/10 — Chúc bạn luôn rạng rỡ</div>
        <div style="color:var(--muted); margin-top:6px">Gửi lời chúc dễ thương chỉ trong 1 click.</div>
      </div>
    </div>
  </div>

  <!-- Modal -->
  <div class="modal-bg" id="modalBg" aria-hidden="true">
    <div class="modal" role="dialog" aria-modal="true" aria-labelledby="modalTitle">
      <button class="close-x" id="closeModal" aria-label="Đóng">&times;</button>
      <h2 class="title" id="modalTitle">💐 Chúc mừng 20/10</h2>
      <p class="msg" id="greetingText">
        Nhân ngày Phụ nữ Việt Nam 20/10, chúc bạn luôn tươi cười, tràn đầy năng lượng và được trân trọng mỗi ngày. Cảm ơn vì đã là chính mình — mạnh mẽ, dịu dàng, thông minh và đáng yêu. ❤️
      </p>

      <div class="cta">
        <button class="btn" id="shareBtn">Sao chép lời chúc</button>
        <button class="btn secondary" id="downloadModalBtn">Tải lời chúc (.txt)</button>
      </div>

      <canvas class="confetti" id="confettiCanvas"></canvas>
    </div>
  </div>

<script>
/* Basic interactions: open modal, confetti, copy, download */
const openGreeting = document.getElementById('openGreeting');
const modalBg = document.getElementById('modalBg');
const closeModal = document.getElementById('closeModal');
const confettiCanvas = document.getElementById('confettiCanvas');
const copyShare = document.getElementById('copyShare');
const shareBtn = document.getElementById('shareBtn');
const downloadBtn = document.getElementById('downloadBtn');
const downloadModalBtn = document.getElementById('downloadModalBtn');
const greetingText = document.getElementById('greetingText');

openGreeting.addEventListener('click', () => {
  modalBg.classList.add('show');
  startConfetti();
  modalBg.setAttribute('aria-hidden','false');
});

closeModal.addEventListener('click', () => {
  modalBg.classList.remove('show');
  stopConfetti();
  modalBg.setAttribute('aria-hidden','true');
});

modalBg.addEventListener('click', (e) => {
  if (e.target === modalBg) {
    modalBg.classList.remove('show');
    stopConfetti();
    modalBg.setAttribute('aria-hidden','true');
  }
});

/* Copy greeting to clipboard (full HTML + short note) */
function copyToClipboard(text){
  navigator.clipboard.writeText(text).then(()=>{
    alert('Đã sao chép — gửi cho người nhận nào! 🎉');
  }).catch(()=>{ alert('Không thể sao chép tự động. Hãy bôi đen và Ctrl+C.'); });
}

copyShare.addEventListener('click', () => {
  const text = `${greetingText.innerText}\n\n— Gửi từ: Lời chúc 20/10`;
  copyToClipboard(text);
});
shareBtn.addEventListener('click', () => {
  const text = `${greetingText.innerText}\n\nChúc bạn ngày 20/10 thật vui! 🌸`;
  copyToClipboard(text);
});

/* Download file helpers */
downloadBtn.addEventListener('click', () => {
  const html = document.documentElement.outerHTML;
  downloadFile('chuc-mung-20-10.html', html);
});
downloadModalBtn.addEventListener('click', () => {
  downloadFile('loi-chuc-20-10.txt', greetingText.innerText);
});
function downloadFile(filename, content){
  const blob = new Blob([content], {type: 'text/plain;charset=utf-8'});
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = filename;
  document.body.appendChild(a);
  a.click();
  a.remove();
  URL.revokeObjectURL(url);
}

/* Simple confetti animation (small, lightweight) */
let confettiCtx, confettiRunning=false, confettiParts=[];
function resizeCanvas(){
  confettiCanvas.width = confettiCanvas.clientWidth;
  confettiCanvas.height = confettiCanvas.clientHeight;
}
function startConfetti(){
  if(confettiRunning) return;
  confettiRunning = true;
  confettiCtx = confettiCanvas.getContext('2d');
  resizeCanvas();
  window.addEventListener('resize', resizeCanvas);
  confettiParts = createParticles(90);
  requestAnimationFrame(confettiLoop);
  // stop after 4s automatically
  setTimeout(stopConfetti, 4000);
}
function stopConfetti(){
  confettiRunning = false;
  confettiCtx && confettiCtx.clearRect(0,0,confettiCanvas.width, confettiCanvas.height);
  window.removeEventListener('resize', resizeCanvas);
}
function createParticles(n){
  const arr=[];
  for(let i=0;i<n;i++){
    arr.push({
      x: Math.random()*confettiCanvas.width,
      y: Math.random()*confettiCanvas.height*0.2,
      vx: (Math.random()-0.5)*2.2,
      vy: 1 + Math.random()*3.2,
      size: 6 + Math.random()*8,
      rot: Math.random()*360,
      speedR: (Math.random()-0.5)*6,
      color: randomColor(),
      life: 0,
      ttl: 80 + Math.random()*60
    });
  }
  return arr;
}
function randomColor(){
  const palette = ['#ff5c8a','#ffd27a','#9be7ff','#c1ffb3','#ff9bb3'];
  return palette[Math.floor(Math.random()*palette.length)];
}
function confettiLoop(){
  if(!confettiRunning) return;
  confettiCtx.clearRect(0,0,confettiCanvas.width, confettiCanvas.height);
  confettiParts.forEach(p=>{
    p.x += p.vx;
    p.y += p.vy;
    p.vy += 0.06;
    p.rot += p.speedR;
    p.life++;
    confettiCtx.save();
    confettiCtx.translate(p.x, p.y);
    confettiCtx.rotate(p.rot * Math.PI/180);
    confettiCtx.fillStyle = p.color;
    confettiCtx.fillRect(-p.size/2, -p.size/2, p.size, p.size*0.6);
    confettiCtx.restore();
    if(p.y > confettiCanvas.height + 30 || p.life > p.ttl){
      // respawn at top
      p.x = Math.random()*confettiCanvas.width;
      p.y = -10;
      p.vx = (Math.random()-0.5)*2.2;
      p.vy = 1 + Math.random()*3.2;
      p.life = 0;
      p.ttl = 60 + Math.random()*80;
    }
  });
  requestAnimationFrame(confettiLoop);
}

/* accessibility: keyboard close */
document.addEventListener('keydown', (e)=>{
  if(e.key === 'Escape' && modalBg.classList.contains('show')){
    modalBg.classList.remove('show');
    stopConfetti();
  }
});
</script>
</body>
</html>
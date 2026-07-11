
<style>
@import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@400;500;600;700&display=swap');
*{margin:0;padding:0;box-sizing:border-box}
body{background:#000;color:#e0e0e0;font-family:'Rajdhani',sans-serif;overflow-x:hidden}
canvas#bg{position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;pointer-events:none}
.wrapper{position:relative;z-index:1;max-width:780px;margin:0 auto;padding:0 20px 60px}
.hero{text-align:center;padding:60px 0 40px;position:relative}
.glitch-name{font-size:clamp(2.2rem,5vw,3.5rem);font-weight:700;color:#00ffff;letter-spacing:6px;text-transform:uppercase;position:relative;display:inline-block;animation:glitch-anim 4s infinite}
.glitch-name::before,.glitch-name::after{content:attr(data-text);position:absolute;top:0;left:0;width:100%;height:100%}
.glitch-name::before{color:#ff00ff;animation:glitch-1 4s infinite;clip-path:polygon(0 0,100% 0,100% 45%,0 45%)}
.glitch-name::after{color:#00ff88;animation:glitch-2 4s infinite;clip-path:polygon(0 55%,100% 55%,100% 100%,0 100%)}
@keyframes glitch-1{0%,90%,100%{transform:translateX(0)}91%{transform:translateX(-3px)}93%{transform:translateX(3px)}95%{transform:translateX(-2px)}}
@keyframes glitch-2{0%,90%,100%{transform:translateX(0)}92%{transform:translateX(3px)}94%{transform:translateX(-3px)}96%{transform:translateX(2px)}}
.sub-title{font-family:'Share Tech Mono',monospace;color:#9b00ff;font-size:0.85rem;letter-spacing:3px;margin-top:10px;opacity:0;animation:fadeUp 0.8s 0.3s forwards}
.typing-bar{display:inline-flex;align-items:center;gap:8px;background:rgba(0,255,255,0.04);border:1px solid rgba(0,255,255,0.15);border-radius:4px;padding:10px 20px;margin:24px auto 0;font-family:'Share Tech Mono',monospace;font-size:0.8rem;color:#00ffcc;opacity:0;animation:fadeUp 0.8s 0.5s forwards}
.typing-bar .cursor{width:8px;height:14px;background:#00ffff;animation:blink 1s infinite}
@keyframes blink{0%,50%{opacity:1}51%,100%{opacity:0}}
@keyframes fadeUp{from{opacity:0;transform:translateY(16px)}to{opacity:1;transform:translateY(0)}}

.section-label{font-family:'Share Tech Mono',monospace;color:#9b00ff;font-size:0.65rem;letter-spacing:4px;text-transform:uppercase;margin-bottom:16px;display:flex;align-items:center;gap:10px}
.section-label::before{content:'';display:block;width:24px;height:1px;background:#9b00ff}
.section-label::after{content:'';flex:1;height:1px;background:linear-gradient(90deg,#9b00ff22,transparent)}

.identity-card{background:rgba(0,255,255,0.02);border:1px solid rgba(0,255,255,0.12);border-radius:8px;padding:24px 28px;margin:40px 0 36px;font-family:'Share Tech Mono',monospace;font-size:0.8rem;line-height:2;opacity:0;animation:fadeUp 0.8s 0.6s forwards;position:relative;overflow:hidden}
.identity-card::before{content:'';position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,transparent,#00ffff,#9b00ff,transparent);animation:scan 3s linear infinite}
@keyframes scan{0%{transform:translateX(-100%)}100%{transform:translateX(100%)} }
.id-row{display:flex;gap:12px}
.id-key{color:#9b00ff;min-width:120px}
.id-val{color:#00ffcc}

.tech-grid{display:flex;flex-wrap:wrap;gap:8px;margin:24px 0 36px;opacity:0;animation:fadeUp 0.8s 0.8s forwards}
.tech-badge{font-family:'Share Tech Mono',monospace;font-size:0.7rem;padding:6px 14px;border:1px solid rgba(0,255,255,0.2);border-radius:3px;color:#00ffcc;background:rgba(0,255,255,0.03);cursor:default;transition:all 0.25s;position:relative;overflow:hidden}
.tech-badge:hover{border-color:#00ffff;background:rgba(0,255,255,0.1);color:#fff;transform:translateY(-2px);box-shadow:0 0 16px rgba(0,255,255,0.2)}
.tech-badge.purple{border-color:rgba(155,0,255,0.3);color:#cc88ff}
.tech-badge.purple:hover{border-color:#9b00ff;background:rgba(155,0,255,0.1);box-shadow:0 0 16px rgba(155,0,255,0.2)}

.projects-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin:24px 0 36px}
@media(max-width:520px){.projects-grid{grid-template-columns:1fr}}
.proj-card{background:rgba(255,255,255,0.02);border:1px solid rgba(255,255,255,0.08);border-radius:8px;padding:20px;transition:all 0.3s;cursor:default;position:relative;overflow:hidden}
.proj-card::after{content:'';position:absolute;inset:0;opacity:0;transition:opacity 0.3s;background:radial-gradient(circle at var(--mx,50%) var(--my,50%),rgba(0,255,255,0.06),transparent 60%)}
.proj-card:hover{border-color:rgba(0,255,255,0.3);transform:translateY(-3px);box-shadow:0 8px 32px rgba(0,255,255,0.08)}
.proj-card:hover::after{opacity:1}
.proj-card.purple-glow:hover{border-color:rgba(155,0,255,0.3);box-shadow:0 8px 32px rgba(155,0,255,0.08)}
.proj-card.purple-glow::after{background:radial-gradient(circle at var(--mx,50%) var(--my,50%),rgba(155,0,255,0.06),transparent 60%)}
.proj-icon{font-size:1.4rem;margin-bottom:10px}
.proj-title{font-size:1rem;font-weight:700;color:#fff;margin-bottom:4px;letter-spacing:1px}
.proj-sub{font-family:'Share Tech Mono',monospace;font-size:0.68rem;color:#9b00ff;margin-bottom:10px}
.proj-desc{font-size:0.82rem;color:#999;line-height:1.6;margin-bottom:12px}
.proj-tags{display:flex;flex-wrap:wrap;gap:5px;margin-bottom:12px}
.proj-tag{font-family:'Share Tech Mono',monospace;font-size:0.62rem;padding:2px 8px;border:1px solid rgba(0,255,255,0.15);color:#00ffcc88;border-radius:2px}
.proj-status{font-family:'Share Tech Mono',monospace;font-size:0.65rem;display:flex;align-items:center;gap:6px}
.status-dot{width:6px;height:6px;border-radius:50%;flex-shrink:0}
.dot-red{background:#ff3366;box-shadow:0 0 6px #ff3366;animation:pulse-dot 1.5s infinite}
.dot-yellow{background:#ffaa00;box-shadow:0 0 6px #ffaa00}
.dot-green{background:#00ff88;box-shadow:0 0 6px #00ff88}
.dot-blue{background:#00aaff;box-shadow:0 0 6px #00aaff}
@keyframes pulse-dot{0%,100%{opacity:1}50%{opacity:0.4}}

.objectives-block{font-family:'Share Tech Mono',monospace;font-size:0.78rem;line-height:2.1;background:rgba(0,0,0,0.4);border:1px solid rgba(155,0,255,0.15);border-radius:8px;padding:22px 24px;margin:24px 0 36px;opacity:0;animation:fadeUp 0.8s 1s forwards}
.obj-row{display:flex;gap:12px;padding:3px 0;transition:background 0.2s;border-radius:4px;padding:4px 6px;cursor:default}
.obj-row:hover{background:rgba(0,255,255,0.04)}
.obj-key{color:#9b00ff;min-width:160px;flex-shrink:0}
.obj-val{color:#ccc}

.connect-row{display:flex;gap:12px;justify-content:center;flex-wrap:wrap;margin:24px 0;opacity:0;animation:fadeUp 0.8s 1.1s forwards}
.connect-btn{font-family:'Share Tech Mono',monospace;font-size:0.75rem;padding:10px 22px;border-radius:4px;text-decoration:none;transition:all 0.25s;display:inline-flex;align-items:center;gap:8px;letter-spacing:1px}
.connect-btn.cyan{border:1px solid rgba(0,255,255,0.4);color:#00ffff;background:transparent}
.connect-btn.cyan:hover{background:rgba(0,255,255,0.1);box-shadow:0 0 20px rgba(0,255,255,0.2);transform:translateY(-2px)}
.connect-btn.purple{border:1px solid rgba(155,0,255,0.4);color:#cc88ff;background:transparent}
.connect-btn.purple:hover{background:rgba(155,0,255,0.1);box-shadow:0 0 20px rgba(155,0,255,0.2);transform:translateY(-2px)}

.footer-mantra{text-align:center;font-family:'Share Tech Mono',monospace;font-size:0.75rem;color:#555;line-height:2.2;margin-top:48px;padding-top:32px;border-top:1px solid rgba(255,255,255,0.06)}
.footer-mantra span{display:block;transition:color 0.3s}
.footer-mantra span:hover{color:#00ffcc}
</style>

<canvas id="bg"></canvas>

<div class="wrapper">
  <div class="hero">
    <div class="glitch-name" data-text="ArjunMP-sudo">ArjunMP-sudo</div>
    <div class="sub-title">AI ENGINEER &nbsp;/&nbsp; CYBERSECURITY ENGINEER &nbsp;/&nbsp; MAKER</div>
    <div class="typing-bar">
      <span id="typed-text"></span>
      <div class="cursor"></div>
    </div>
  </div>

  <div class="section-label">identity matrix</div>
  <div class="identity-card">
    <div class="id-row"><span class="id-key">ALIAS</span><span class="id-val">ArjunMP-sudo</span></div>
    <div class="id-row"><span class="id-key">ROLE</span><span class="id-val">Student | Maker | Builder</span></div>
    <div class="id-row"><span class="id-key">DOMAINS</span><span class="id-val">AI Engineering | Cybersecurity | IoT | Networking</span></div>
    <div class="id-row"><span class="id-key">HARDWARE</span><span class="id-val">ESP32 | Arduino | DIY Electronics</span></div>
    <div class="id-row"><span class="id-key">CORE LANG</span><span class="id-val">Python</span></div>
    <div class="id-row"><span class="id-key">READING</span><span class="id-val">C# | Embedded Systems</span></div>
    <div class="id-row"><span class="id-key">MISSION</span><span class="id-val">AI Engineer | Cybersecurity Researcher</span></div>
    <div class="id-row"><span class="id-key">STATUS</span><span class="id-val">[ ACTIVE ] &nbsp;[ BUILDING ] &nbsp;[ LEARNING ]</span></div>
  </div>

  <div class="section-label">tech stack</div>
  <div class="tech-grid">
    <div class="tech-badge">Python</div>
    <div class="tech-badge purple">C#</div>
    <div class="tech-badge">ESP32</div>
    <div class="tech-badge">Arduino</div>
    <div class="tech-badge">Git</div>
    <div class="tech-badge purple">VS Code</div>
    <div class="tech-badge">Linux</div>
    <div class="tech-badge">Cybersecurity</div>
    <div class="tech-badge purple">IoT</div>
    <div class="tech-badge">Networking</div>
    <div class="tech-badge purple">AI / ML</div>
    <div class="tech-badge">Embedded Systems</div>
  </div>

  <div class="section-label">active projects</div>
  <div class="projects-grid" id="proj-grid">
    <div class="proj-card" onmousemove="trackMouse(event,this)">
      <div class="proj-icon">🛡️</div>
      <div class="proj-title">NYX PROBE</div>
      <div class="proj-sub">ESP32 Pentesting Platform</div>
      <div class="proj-desc">Multi-function hardware security toolkit — WiFi analysis, BLE/Bluetooth assessment, port scanning, GPS wardriving, and HID attacks with OLED menu UI.</div>
      <div class="proj-tags">
        <span class="proj-tag">ESP32</span><span class="proj-tag">WiFi 802.11</span><span class="proj-tag">BLE</span><span class="proj-tag">C++</span>
      </div>
      <div class="proj-status"><div class="status-dot dot-red"></div><span style="color:#ff3366">ACTIVE DEVELOPMENT</span></div>
    </div>
    <div class="proj-card purple-glow" onmousemove="trackMouse(event,this)">
      <div class="proj-icon">🚀</div>
      <div class="proj-title">TVC ROCKET</div>
      <div class="proj-sub">Thrust Vector Control</div>
      <div class="proj-desc">DIY stabilized rocket with IMU-based attitude control, TVC gimbal mechanics, and real-time servo correction during ascent.</div>
      <div class="proj-tags">
        <span class="proj-tag">ESP32</span><span class="proj-tag">IMU</span><span class="proj-tag">Servo</span><span class="proj-tag">Avionics</span>
      </div>
      <div class="proj-status"><div class="status-dot dot-yellow"></div><span style="color:#ffaa00">IN PROGRESS</span></div>
    </div>
    <div class="proj-card" onmousemove="trackMouse(event,this)">
      <div class="proj-icon">💻</div>
      <div class="proj-title">PCxHOOK</div>
      <div class="proj-sub">Python Remote Command Tool</div>
      <div class="proj-desc">Execute any shell command on a remote PC over LAN/WAN. Lightweight, auto-starting, port-forward ready for remote device management.</div>
      <div class="proj-tags">
        <span class="proj-tag">Python</span><span class="proj-tag">Networking</span><span class="proj-tag">LAN/WAN</span>
      </div>
      <div class="proj-status"><div class="status-dot dot-green"></div><span style="color:#00ff88">LIVE</span></div>
    </div>
    <div class="proj-card purple-glow" onmousemove="trackMouse(event,this)">
      <div class="proj-icon">🔩</div>
      <div class="proj-title">DIY ELECTRONICS</div>
      <div class="proj-sub">Custom Hardware Builds</div>
      <div class="proj-desc">Sensor arrays, custom PCBs, motor drivers, and embedded system prototypes — building and learning from scratch.</div>
      <div class="proj-tags">
        <span class="proj-tag">Hardware</span><span class="proj-tag">PCB Design</span><span class="proj-tag">Prototyping</span>
      </div>
      <div class="proj-status"><div class="status-dot dot-blue"></div><span style="color:#00aaff">ONGOING</span></div>
    </div>
  </div>

  <div class="section-label">current objectives</div>
  <div class="objectives-block">
    <div class="obj-row"><span class="obj-key">🐍 Python</span><span class="obj-val">Deep-diving into system-level scripting</span></div>
    <div class="obj-row"><span class="obj-key">⚙️  ESP32</span><span class="obj-val">Expanding embedded systems & wireless security</span></div>
    <div class="obj-row"><span class="obj-key">🛡️  NYX Probe</span><span class="obj-val">Completing firmware, adding advanced modules</span></div>
    <div class="obj-row"><span class="obj-key">🚀 TVC Rocket</span><span class="obj-val">Building a working stabilized prototype</span></div>
    <div class="obj-row"><span class="obj-key">🤖 AI / ML</span><span class="obj-val">Learning models, agents & applied intelligence</span></div>
    <div class="obj-row"><span class="obj-key">🔐 End Goal</span><span class="obj-val">AI Engineer | Cybersecurity Engineer | Security Researcher</span></div>
  </div>

  <div class="section-label">connect</div>
  <div class="connect-row">
    <a class="connect-btn cyan" href="https://github.com/ArjunMP-sudo">⬡ GitHub</a>
    <a class="connect-btn purple" href="https://instagram.com/mp_arjun177">◈ Instagram</a>
  </div>

  <div class="footer-mantra">
    <span>> Understand systems.</span>
    <span>> Break limits.</span>
    <span>> Build smarter.</span>
    <span>> Secure everything.</span>
  </div>
</div>

<script>
const canvas = document.getElementById('bg');
const ctx = canvas.getContext('2d');
let W, H, particles = [], mouse = {x: -9999, y: -9999};

function resize(){W = canvas.width = window.innerWidth; H = canvas.height = window.innerHeight}
resize();
window.addEventListener('resize', resize);

window.addEventListener('mousemove', e => { mouse.x = e.clientX; mouse.y = e.clientY; });

class Particle {
  constructor(){this.reset()}
  reset(){
    this.x = Math.random()*W;
    this.y = Math.random()*H;
    this.vx = (Math.random()-0.5)*0.3;
    this.vy = (Math.random()-0.5)*0.3;
    this.r = Math.random()*1.5+0.3;
    this.cyan = Math.random()>0.5;
    this.alpha = Math.random()*0.5+0.1;
    this.life = 0;
    this.maxLife = 200+Math.random()*300;
  }
  update(){
    this.x+=this.vx; this.y+=this.vy;
    this.life++;
    let dx=this.x-mouse.x, dy=this.y-mouse.y, dist=Math.sqrt(dx*dx+dy*dy);
    if(dist<120){let f=((120-dist)/120)*0.4;this.vx+=dx/dist*f;this.vy+=dy/dist*f}
    if(this.x<0||this.x>W||this.y<0||this.y>H||this.life>this.maxLife)this.reset();
  }
  draw(){
    let a=this.alpha*(1-this.life/this.maxLife);
    ctx.beginPath();ctx.arc(this.x,this.y,this.r,0,Math.PI*2);
    ctx.fillStyle=this.cyan?`rgba(0,255,255,${a})`:`rgba(155,0,255,${a})`;
    ctx.fill();
  }
}

for(let i=0;i<120;i++) particles.push(new Particle());

function connectParticles(){
  for(let i=0;i<particles.length;i++){
    for(let j=i+1;j<particles.length;j++){
      let dx=particles[i].x-particles[j].x, dy=particles[i].y-particles[j].y;
      let d=Math.sqrt(dx*dx+dy*dy);
      if(d<90){
        ctx.beginPath();
        ctx.moveTo(particles[i].x,particles[i].y);
        ctx.lineTo(particles[j].x,particles[j].y);
        let a=(1-d/90)*0.12;
        ctx.strokeStyle=`rgba(0,255,255,${a})`;
        ctx.lineWidth=0.5;
        ctx.stroke();
      }
    }
  }
}

function drawGrid(){
  ctx.strokeStyle='rgba(0,255,255,0.015)';
  ctx.lineWidth=0.5;
  let sz=60;
  for(let x=0;x<W;x+=sz){ctx.beginPath();ctx.moveTo(x,0);ctx.lineTo(x,H);ctx.stroke()}
  for(let y=0;y<H;y+=sz){ctx.beginPath();ctx.moveTo(0,y);ctx.lineTo(W,y);ctx.stroke()}
}

function loop(){
  ctx.clearRect(0,0,W,H);
  drawGrid();
  particles.forEach(p=>{p.update();p.draw()});
  connectParticles();
  requestAnimationFrame(loop);
}
loop();

function trackMouse(e,el){
  let r=el.getBoundingClientRect();
  el.style.setProperty('--mx',((e.clientX-r.left)/r.width*100)+'%');
  el.style.setProperty('--my',((e.clientY-r.top)/r.height*100)+'%');
}

const phrases=[
  'Cybersecurity | IoT | Networking',
  'ESP32 | Embedded Systems | Hardware Hacker',
  'Python Developer | AI Engineer | Builder',
  'NYX Probe — Multi-Pentesting Tool',
  'TVC Rocket | PCxHOOK | DIY Electronics',
  'Future AI & Cybersecurity Engineer 🛡️'
];
let pi=0, ci=0, deleting=false, el=document.getElementById('typed-text'), pause=0;
function typeLoop(){
  if(pause>0){pause--;setTimeout(typeLoop,50);return}
  let t=phrases[pi];
  if(!deleting){
    el.textContent=t.slice(0,ci+1);ci++;
    if(ci>=t.length){deleting=true;pause=40}
    setTimeout(typeLoop,55);
  } else {
    el.textContent=t.slice(0,ci-1);ci--;
    if(ci<=0){deleting=false;pi=(pi+1)%phrases.length;pause=10}
    setTimeout(typeLoop,28);
  }
}
typeLoop();

let observer=new IntersectionObserver(entries=>{
  entries.forEach(e=>{if(e.isIntersecting)e.target.style.animationPlayState='running'});
},{threshold:0.1});
document.querySelectorAll('[style*="animation"]').forEach(el=>observer.observe(el));
</script>

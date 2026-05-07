
<style>
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;800&family=Inter:wght@300;400;500;600&display=swap');

*{margin:0;padding:0;box-sizing:border-box}

:root{
  --neon-blue:#00d4ff;
  --neon-purple:#a855f7;
  --neon-pink:#f0abfc;
  --neon-green:#00ff88;
  --neon-amber:#fbbf24;
  --dark-bg:#020817;
  --card-bg:rgba(15,23,42,0.85);
  --card-border:rgba(0,212,255,0.25);
  --text-main:#e2e8f0;
  --text-dim:#94a3b8;
}

.site{
  font-family:'Inter',sans-serif;
  background:var(--dark-bg);
  color:var(--text-main);
  overflow-x:hidden;
  min-height:100vh;
}

canvas#stars{
  position:absolute;top:0;left:0;width:100%;height:100%;
  pointer-events:none;z-index:0;
}

.hero{
  position:relative;
  min-height:340px;
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  text-align:center;
  padding:40px 20px 30px;
  overflow:hidden;
}

.hero-bg{
  position:absolute;inset:0;
  background:radial-gradient(ellipse 80% 60% at 50% 0%,rgba(168,85,247,0.18) 0%,transparent 70%),
             radial-gradient(ellipse 60% 40% at 80% 100%,rgba(0,212,255,0.12) 0%,transparent 60%),
             radial-gradient(ellipse 50% 40% at 20% 80%,rgba(0,255,136,0.08) 0%,transparent 60%);
  z-index:0;
}

.hero-orb{
  position:absolute;
  border-radius:50%;
  filter:blur(40px);
  animation:orbFloat 6s ease-in-out infinite;
}
.orb1{width:200px;height:200px;background:rgba(168,85,247,0.15);top:-60px;left:10%;animation-delay:0s}
.orb2{width:150px;height:150px;background:rgba(0,212,255,0.12);top:20px;right:10%;animation-delay:-2s}
.orb3{width:120px;height:120px;background:rgba(0,255,136,0.1);bottom:0;left:40%;animation-delay:-4s}

@keyframes orbFloat{0%,100%{transform:translateY(0) scale(1)}50%{transform:translateY(-20px) scale(1.1)}}

.hero-content{position:relative;z-index:1;}

.orbit-ring{
  width:90px;height:90px;
  border:1.5px solid rgba(0,212,255,0.4);
  border-radius:50%;
  display:flex;align-items:center;justify-content:center;
  margin:0 auto 18px;
  position:relative;
  animation:spinRing 8s linear infinite;
}
.orbit-ring::before{
  content:'';position:absolute;
  width:10px;height:10px;
  border-radius:50%;
  background:var(--neon-blue);
  top:-5px;left:50%;transform:translateX(-50%);
  box-shadow:0 0 12px var(--neon-blue);
}
.orbit-ring::after{
  content:'';position:absolute;
  width:8px;height:8px;border-radius:50%;
  background:var(--neon-purple);
  bottom:-4px;right:10px;
  box-shadow:0 0 10px var(--neon-purple);
}
.orbit-nucleus{
  width:36px;height:36px;border-radius:50%;
  background:radial-gradient(circle,rgba(0,212,255,0.5),rgba(168,85,247,0.3));
  display:flex;align-items:center;justify-content:center;
  font-size:16px;
  box-shadow:0 0 20px rgba(0,212,255,0.4);
}

@keyframes spinRing{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}

.hero h1{
  font-family:'Orbitron',sans-serif;
  font-size:clamp(20px,5vw,32px);
  font-weight:800;
  background:linear-gradient(135deg,#00d4ff 0%,#a855f7 50%,#f0abfc 100%);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;
  background-clip:text;
  line-height:1.2;margin-bottom:10px;
  letter-spacing:-0.5px;
}
.hero-sub{
  font-size:13px;color:var(--text-dim);line-height:1.6;max-width:400px;margin:0 auto 16px;
}
.dev-badge{
  display:inline-flex;align-items:center;gap:8px;
  background:rgba(0,212,255,0.08);
  border:0.5px solid rgba(0,212,255,0.3);
  border-radius:20px;padding:6px 16px;
  font-size:12px;color:var(--neon-blue);
  font-weight:500;letter-spacing:0.5px;
}
.dev-badge span{color:var(--neon-purple);font-weight:600;}

.stats-row{
  display:flex;justify-content:center;gap:20px;
  margin-top:20px;flex-wrap:wrap;
}
.stat-chip{
  text-align:center;
  background:rgba(255,255,255,0.04);
  border:0.5px solid rgba(255,255,255,0.1);
  border-radius:12px;padding:10px 18px;
  min-width:80px;
}
.stat-chip .num{
  font-family:'Orbitron',sans-serif;
  font-size:18px;font-weight:700;
  background:linear-gradient(135deg,var(--neon-blue),var(--neon-purple));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.stat-chip .lbl{font-size:10px;color:var(--text-dim);margin-top:2px;text-transform:uppercase;letter-spacing:0.5px;}

.section-label{
  text-align:center;padding:16px 20px 12px;
  font-size:11px;color:var(--text-dim);text-transform:uppercase;letter-spacing:2px;
  font-weight:500;
}

.chapters-3d{
  padding:0 16px 16px;
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(130px,1fr));
  gap:12px;
}

.ch-card{
  position:relative;
  background:var(--card-bg);
  border:0.5px solid var(--card-border);
  border-radius:16px;
  padding:16px 12px 14px;
  cursor:pointer;
  transition:all 0.25s cubic-bezier(0.4,0,0.2,1);
  backdrop-filter:blur(10px);
  text-align:center;
  overflow:hidden;
}
.ch-card::before{
  content:'';position:absolute;inset:0;
  background:linear-gradient(135deg,transparent 40%,rgba(255,255,255,0.03));
  pointer-events:none;
}
.ch-card::after{
  content:'';position:absolute;
  top:-50%;left:-50%;width:200%;height:200%;
  background:conic-gradient(transparent 90deg,rgba(0,212,255,0.06) 180deg,transparent 270deg);
  animation:shimmer 4s linear infinite;
  pointer-events:none;opacity:0;transition:opacity 0.3s;
}
.ch-card:hover::after{opacity:1;}
@keyframes shimmer{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}

.ch-card:hover{
  transform:translateY(-4px) scale(1.02);
  border-color:rgba(0,212,255,0.6);
  box-shadow:0 12px 30px rgba(0,212,255,0.15),0 0 0 1px rgba(0,212,255,0.1);
}
.ch-card.active{
  border-color:rgba(168,85,247,0.7);
  box-shadow:0 0 20px rgba(168,85,247,0.2),0 8px 20px rgba(168,85,247,0.15);
  background:rgba(168,85,247,0.08);
}

.ch-icon-wrap{
  width:44px;height:44px;border-radius:12px;
  display:flex;align-items:center;justify-content:center;
  margin:0 auto 10px;font-size:20px;
  position:relative;z-index:1;
}
.ch-num-badge{
  font-size:9px;font-weight:600;letter-spacing:0.5px;
  padding:2px 8px;border-radius:8px;margin-bottom:6px;
  display:inline-block;text-transform:uppercase;
}
.ch-name{font-size:11px;font-weight:500;color:var(--text-main);line-height:1.3;position:relative;z-index:1;}

.lesson-panel{
  margin:0 16px 24px;
  background:rgba(15,23,42,0.9);
  border:0.5px solid rgba(168,85,247,0.3);
  border-radius:20px;
  overflow:hidden;
  backdrop-filter:blur(20px);
  box-shadow:0 20px 60px rgba(0,0,0,0.5);
  display:none;
}

.lesson-hdr{
  padding:20px 22px 18px;
  border-bottom:0.5px solid rgba(255,255,255,0.06);
  position:relative;
  overflow:hidden;
}
.lesson-hdr::before{
  content:'';position:absolute;top:0;left:0;right:0;height:2px;
  background:linear-gradient(90deg,var(--neon-blue),var(--neon-purple),var(--neon-pink));
}
.lesson-hdr-inner{display:flex;align-items:flex-start;gap:14px;}
.lesson-icon-box{
  width:50px;height:50px;border-radius:14px;
  display:flex;align-items:center;justify-content:center;
  font-size:22px;flex-shrink:0;
  position:relative;
}
.lesson-icon-box::after{
  content:'';position:absolute;inset:-1px;border-radius:15px;
  background:linear-gradient(135deg,var(--neon-blue),var(--neon-purple));
  z-index:-1;opacity:0.6;
}
.lesson-hdr h2{
  font-family:'Orbitron',sans-serif;
  font-size:15px;font-weight:700;
  background:linear-gradient(135deg,var(--neon-blue),var(--neon-purple));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  margin-bottom:4px;line-height:1.3;
}
.lesson-hdr p{font-size:12px;color:var(--text-dim);}

.tabs-wrap{
  display:flex;gap:6px;padding:14px 16px 0;
  flex-wrap:wrap;
  overflow-x:auto;
  scrollbar-width:none;
}
.tabs-wrap::-webkit-scrollbar{display:none;}
.tab-pill{
  padding:5px 14px;border-radius:20px;
  border:0.5px solid rgba(255,255,255,0.12);
  background:transparent;
  color:var(--text-dim);font-size:12px;cursor:pointer;
  transition:all 0.2s;white-space:nowrap;
  font-family:'Inter',sans-serif;
}
.tab-pill:hover{border-color:rgba(0,212,255,0.4);color:var(--neon-blue);}
.tab-pill.active{
  background:linear-gradient(135deg,rgba(0,212,255,0.15),rgba(168,85,247,0.15));
  border-color:rgba(0,212,255,0.5);color:var(--neon-blue);
}

.lesson-body{padding:18px 20px 20px;}

.analogy{
  background:rgba(251,191,36,0.06);
  border-left:2px solid var(--neon-amber);
  border-radius:0 10px 10px 0;
  padding:12px 14px;margin-bottom:14px;
}
.analogy .albl{font-size:10px;color:var(--neon-amber);font-weight:600;letter-spacing:1px;text-transform:uppercase;margin-bottom:5px;}
.analogy p{font-size:13px;color:var(--text-main);line-height:1.65;}

.fcard{
  background:rgba(255,255,255,0.04);
  border:0.5px solid rgba(255,255,255,0.1);
  border-radius:10px;padding:10px 14px;
  display:flex;justify-content:space-between;align-items:center;
  margin:7px 0;gap:10px;
}
.fcard .formula{
  font-family:'Orbitron',sans-serif;font-size:13px;
  color:var(--neon-blue);font-weight:600;
  text-shadow:0 0 10px rgba(0,212,255,0.3);
}
.fcard .meaning{font-size:11px;color:var(--text-dim);text-align:right;max-width:160px;line-height:1.4;}

.memory{
  background:rgba(168,85,247,0.08);
  border-left:2px solid var(--neon-purple);
  border-radius:0 10px 10px 0;
  padding:12px 14px;margin:12px 0;
}
.memory .mlbl{font-size:10px;color:var(--neon-purple);font-weight:600;letter-spacing:1px;text-transform:uppercase;margin-bottom:5px;}
.memory p{font-size:13px;color:var(--text-main);line-height:1.65;}

.slabel{font-size:11px;color:var(--text-dim);text-transform:uppercase;letter-spacing:0.8px;margin:14px 0 7px;font-weight:500;}

.izone{
  background:rgba(0,212,255,0.05);
  border:0.5px solid rgba(0,212,255,0.2);
  border-radius:12px;padding:14px;margin:12px 0;
}
.izone h4{font-size:10px;color:var(--neon-blue);text-transform:uppercase;letter-spacing:1px;margin-bottom:10px;font-weight:600;}
.slider-r{display:flex;align-items:center;gap:10px;margin:6px 0;}
.slider-r label{font-size:12px;color:var(--text-dim);min-width:70px;}
.slider-r input[type=range]{flex:1;accent-color:var(--neon-blue);}
.slider-r span{font-size:12px;color:var(--neon-blue);min-width:60px;text-align:right;font-weight:500;}

.result-box{
  background:rgba(0,0,0,0.3);border:0.5px solid rgba(0,212,255,0.2);
  border-radius:10px;text-align:center;padding:12px;margin-top:10px;
}
.result-box .rval{
  font-family:'Orbitron',sans-serif;font-size:22px;font-weight:700;
  background:linear-gradient(135deg,var(--neon-blue),var(--neon-green));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.result-box .runit{font-size:11px;color:var(--text-dim);margin-top:2px;}

.tip-tag{
  display:inline-flex;align-items:center;gap:5px;
  background:rgba(0,255,136,0.08);
  border:0.5px solid rgba(0,255,136,0.25);
  color:var(--neon-green);
  border-radius:20px;padding:4px 12px;
  font-size:11px;font-weight:500;margin:3px;
}

.nav-row{display:flex;justify-content:space-between;margin-top:18px;gap:10px;}
.nav-b{
  padding:8px 20px;border-radius:10px;
  border:0.5px solid rgba(255,255,255,0.15);
  background:transparent;color:var(--text-dim);
  font-size:12px;cursor:pointer;transition:all 0.2s;
  font-family:'Inter',sans-serif;
}
.nav-b:hover{border-color:rgba(0,212,255,0.4);color:var(--neon-blue);}
.nav-b.next{
  background:linear-gradient(135deg,rgba(0,212,255,0.15),rgba(168,85,247,0.15));
  border-color:rgba(0,212,255,0.4);color:var(--neon-blue);font-weight:500;
}

.footer{
  text-align:center;padding:24px 16px 28px;
  border-top:0.5px solid rgba(255,255,255,0.06);
  position:relative;
}
.footer::before{
  content:'';position:absolute;top:0;left:20%;right:20%;height:0.5px;
  background:linear-gradient(90deg,transparent,var(--neon-purple),var(--neon-blue),transparent);
}
.footer-logo{
  font-family:'Orbitron',sans-serif;
  font-size:11px;font-weight:600;
  background:linear-gradient(135deg,var(--neon-blue),var(--neon-purple));
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  letter-spacing:2px;margin-bottom:6px;
}
.footer p{font-size:11px;color:var(--text-dim);}
.footer .dev{color:var(--neon-purple);font-weight:600;}

.progress-track{height:2px;background:rgba(255,255,255,0.06);margin:0 16px 16px;}
.progress-glow{height:100%;background:linear-gradient(90deg,var(--neon-blue),var(--neon-purple));transition:width 0.5s;box-shadow:0 0 8px var(--neon-blue);}

.ch-colors{
  electro:['#00d4ff','rgba(0,212,255,0.12)','rgba(0,212,255,0.2)'],
}

</style>

<div class="site">

<canvas id="stars"></canvas>

<div class="hero">
  <div class="hero-bg"></div>
  <div class="hero-orb orb1"></div>
  <div class="hero-orb orb2"></div>
  <div class="hero-orb orb3"></div>
  <div class="hero-content">
    <div class="orbit-ring">
      <div class="orbit-nucleus">⚛</div>
    </div>
    <h1>Class 12 Physics<br>Universe</h1>
    <p class="hero-sub">Holographic 3D learning experience — every concept visualized, every formula alive</p>
    <div class="dev-badge">Developed by <span>&nbsp;Aryan Barolia</span></div>
    <div class="stats-row">
      <div class="stat-chip"><div class="num">11</div><div class="lbl">Chapters</div></div>
      <div class="stat-chip"><div class="num">50+</div><div class="lbl">Concepts</div></div>
      <div class="stat-chip"><div class="num">12</div><div class="lbl">Simulations</div></div>
      <div class="stat-chip"><div class="num">∞</div><div class="lbl">Memory</div></div>
    </div>
  </div>
</div>

<div class="progress-track"><div class="progress-glow" id="pg" style="width:0%"></div></div>

<div class="section-label">Choose Your Chapter</div>

<div class="chapters-3d" id="grid"></div>

<div class="lesson-panel" id="panel">
  <div class="lesson-hdr">
    <div class="lesson-hdr-inner">
      <div class="lesson-icon-box" id="lico"></div>
      <div><h2 id="ltit"></h2><p id="lsub"></p></div>
    </div>
  </div>
  <div class="tabs-wrap" id="tw"></div>
  <div class="lesson-body" id="lb"></div>
</div>

<div class="footer">
  <div class="footer-logo">Physics Universe 3D</div>
  <p>Crafted with passion by <span class="dev">Aryan Barolia</span> · Class 12 CBSE · 2025</p>
</div>

</div>

<script>
const C = document.getElementById('stars');
const ctx = C.getContext('2d');
let stars=[];
function initStars(){
  C.width=C.offsetWidth;C.height=C.offsetHeight;
  stars=[];
  for(let i=0;i<120;i++){
    stars.push({x:Math.random()*C.width,y:Math.random()*C.height,r:Math.random()*1.2+0.3,a:Math.random(),d:Math.random()*0.003+0.001,t:Math.random()*Math.PI*2});
  }
}
function drawStars(){
  ctx.clearRect(0,0,C.width,C.height);
  stars.forEach(s=>{
    s.t+=s.d;
    const a=0.3+0.5*Math.abs(Math.sin(s.t));
    ctx.beginPath();ctx.arc(s.x,s.y,s.r,0,Math.PI*2);
    ctx.fillStyle=`rgba(255,255,255,${a})`;ctx.fill();
  });
  requestAnimationFrame(drawStars);
}
initStars();drawStars();
window.addEventListener('resize',initStars);

const chapters=[
  {icon:'⚡',num:'Ch 1',name:'Electric Charges & Fields',clr:'#00d4ff',bg:'rgba(0,212,255,0.12)'},
  {icon:'🔋',num:'Ch 2',name:'Electrostatic Potential',clr:'#a855f7',bg:'rgba(168,85,247,0.12)'},
  {icon:'🌊',num:'Ch 3',name:'Current Electricity',clr:'#00ff88',bg:'rgba(0,255,136,0.1)'},
  {icon:'🧲',num:'Ch 4-5',name:'Magnetism & Forces',clr:'#f0abfc',bg:'rgba(240,171,252,0.1)'},
  {icon:'💡',num:'Ch 6',name:'EM Induction',clr:'#fbbf24',bg:'rgba(251,191,36,0.1)'},
  {icon:'📡',num:'Ch 7-8',name:'EM Waves & AC',clr:'#00d4ff',bg:'rgba(0,212,255,0.1)'},
  {icon:'🔍',num:'Ch 9',name:'Ray Optics',clr:'#a855f7',bg:'rgba(168,85,247,0.1)'},
  {icon:'🌈',num:'Ch 10',name:'Wave Optics',clr:'#00ff88',bg:'rgba(0,255,136,0.1)'},
  {icon:'🌑',num:'Ch 11',name:'Dual Nature of Light',clr:'#fbbf24',bg:'rgba(251,191,36,0.1)'},
  {icon:'⚛️',num:'Ch 12',name:'Atoms & Nuclei',clr:'#f0abfc',bg:'rgba(240,171,252,0.1)'},
  {icon:'💻',num:'Ch 13',name:'Semiconductors',clr:'#00ff88',bg:'rgba(0,255,136,0.1)'},
];

const lessons=[
  {icon:'⚡',title:'Electric Charges & Fields',sub:'The invisible force that runs the universe',
   tabs:['Big Idea','Coulomb\'s Law','Electric Field','Gauss\'s Law','Recall'],
   content:[
    `<div class="analogy"><div class="albl">Real-life analogy</div><p>Think of charge like <strong>personality</strong> — positive people attract negative people, similar personalities repel. Charge is just this "personality" of matter at atomic scale.</p></div>
     <div class="fcard"><span class="formula">q = ne</span><span class="meaning">Charge = multiple of e = 1.6×10⁻¹⁹ C</span></div>
     <div class="fcard"><span class="formula">e = 1.6×10⁻¹⁹ C</span><span class="meaning">Quantum of charge (electron)</span></div>
     <div class="tip-tag">🔒 Charge is conserved — never created or destroyed</div>
     <div class="tip-tag">⚛ Charge is quantized — always integer × e</div>`,
    `<div class="analogy"><div class="albl">Like gravity, but electric</div><p>Coulomb's law is Newton's gravity for charges. More charge = more force. More distance = less force (inverse square law).</p></div>
     <div class="fcard"><span class="formula">F = kq₁q₂/r²</span><span class="meaning">Coulomb force · k = 9×10⁹ N·m²/C²</span></div>
     <div class="izone"><h4>⚡ Live Force Calculator</h4>
     <div class="slider-r"><label>q₁ (μC)</label><input type=range min=1 max=10 value=3 id=q1 oninput=calcCoul()><span id=q1v>3 μC</span></div>
     <div class="slider-r"><label>q₂ (μC)</label><input type=range min=1 max=10 value=3 id=q2 oninput=calcCoul()><span id=q2v>3 μC</span></div>
     <div class="slider-r"><label>r (m)</label><input type=range min=1 max=10 value=3 id=rr oninput=calcCoul()><span id=rrv>3 m</span></div>
     <div class="result-box"><div class="rval" id=fval>27.0 mN</div><div class="runit">Coulomb Force</div></div></div>
     <div class="memory"><div class="mlbl">Memory hook</div><p>F·orce = k × q₁ × q₂ / r² — "Force keeps quarrels (charges) squared!"</p></div>`,
    `<div class="analogy"><div class="albl">Smell from a perfume bottle</div><p>Electric field is like smell — stronger near source, weaker far away. It tells you: "If I place a test charge HERE, what force would it feel?"</p></div>
     <div class="fcard"><span class="formula">E = F/q = kQ/r²</span><span class="meaning">Field = force per unit +ve charge</span></div>
     <div class="fcard"><span class="formula">σ = q/A</span><span class="meaning">Surface charge density</span></div>
     <div class="fcard"><span class="formula">λ = q/L</span><span class="meaning">Linear charge density</span></div>
     <div class="memory"><div class="mlbl">Visualize it</div><p>Field lines EXIT positive charges and ENTER negative charges. They never cross. Denser lines = stronger field!</p></div>`,
    `<div class="analogy"><div class="albl">Gauss — the clever shortcut</div><p>Draw any closed imaginary surface (Gaussian surface). Count the field lines through it = always proportional to charge INSIDE. Shape doesn't matter — only enclosed charge!</p></div>
     <div class="fcard"><span class="formula">φ = q_enc/ε₀</span><span class="meaning">Gauss's Law — total flux = q/ε₀</span></div>
     <div class="fcard"><span class="formula">E = σ/ε₀</span><span class="meaning">Just outside conductor</span></div>
     <div class="fcard"><span class="formula">E = σ/2ε₀</span><span class="meaning">Near infinite plane of charge</span></div>
     <div class="memory"><div class="mlbl">Secret weapon — 3 symmetries only</div><p>Gauss works EASILY for: Spherical (point charge) · Cylindrical (long wire) · Planar (infinite sheet). Spot symmetry → apply Gauss → instant answer!</p></div>`,
    `<div class="memory"><div class="mlbl">5-year recall bank</div><p>⚡ F = kq₁q₂/r² (Coulomb)<br>🌀 E = kQ/r² (point charge field)<br>📦 φ = q/ε₀ (Gauss's Law)<br>🔒 E = 0 inside conductor, charge only on surface!</p></div>
     <div class="analogy"><div class="albl">Story method</div><p>Two queen bees (charges) in a hive — they feel each other's force (Coulomb). Each creates a scent cloud (field). Draw a bubble around one (Gauss surface) — count scent lines through bubble = enclosed charge/ε₀. Done!</p></div>`
   ]},
  {icon:'🔋',title:'Electrostatic Potential & Capacitance',sub:'Energy stored in electric fields',
   tabs:['Potential','Energy','Capacitors','Dielectrics','Recall'],
   content:[
    `<div class="analogy"><div class="albl">Height = Potential</div><p>Electric potential is like ALTITUDE. A ball rolls down from high to low height — a positive charge moves from high to low potential. Energy is stored when you push "uphill"!</p></div>
     <div class="fcard"><span class="formula">V = kQ/r</span><span class="meaning">Potential due to point charge</span></div>
     <div class="fcard"><span class="formula">E = −dV/dr</span><span class="meaning">Field is −ve gradient of potential</span></div>
     <div class="memory"><div class="mlbl">Equipotential surfaces</div><p>On an equipotential surface V is constant → NO WORK needed to move charge along it! Field lines are always PERPENDICULAR to equipotentials.</p></div>`,
    `<div class="fcard"><span class="formula">U = kq₁q₂/r</span><span class="meaning">Potential energy of a charge pair</span></div>
     <div class="fcard"><span class="formula">W = q(V₁−V₂)</span><span class="meaning">Work done moving charge</span></div>
     <div class="fcard"><span class="formula">V = W/q</span><span class="meaning">Potential = Work per unit charge</span></div>`,
    `<div class="analogy"><div class="albl">Capacitor = rechargeable spring</div><p>Two metal plates store charge like a spring stores energy. Push charge in → spring compresses → energy stored. Let go → energy released! Used in cameras, phones, circuits.</p></div>
     <div class="fcard"><span class="formula">C = Q/V = ε₀A/d</span><span class="meaning">Capacitance in Farads</span></div>
     <div class="fcard"><span class="formula">U = ½CV²</span><span class="meaning">Energy stored in capacitor</span></div>
     <div class="izone"><h4>📦 Capacitor Explorer</h4>
     <div class="slider-r"><label>Area (m²)</label><input type=range min=1 max=10 value=5 id=ca oninput=calcCap()><span id=cav>5 m²</span></div>
     <div class="slider-r"><label>Distance (mm)</label><input type=range min=1 max=10 value=2 id=cd oninput=calcCap()><span id=cdv>2 mm</span></div>
     <div class="result-box"><div class="rval" id=capval>22.1 pF</div><div class="runit">Capacitance</div></div></div>
     <div class="fcard"><span class="formula">C = C₁+C₂</span><span class="meaning">Parallel: capacitances ADD</span></div>
     <div class="fcard"><span class="formula">1/C = 1/C₁+1/C₂</span><span class="meaning">Series: reciprocals add</span></div>`,
    `<div class="analogy"><div class="albl">Dielectric magic</div><p>Fill the gap with glass/mica — material polarizes, lets you store MORE charge without raising voltage. Capacitance multiplied by dielectric constant K!</p></div>
     <div class="fcard"><span class="formula">C = Kε₀A/d</span><span class="meaning">K = dielectric constant (≥1)</span></div>
     <div class="fcard"><span class="formula">E = E₀/K</span><span class="meaning">Field reduces by K inside material</span></div>
     <div class="memory"><div class="mlbl">K values to remember</div><p>Air = 1 · Mica ≈ 6 · Glass ≈ 7 · Water ≈ 80<br>Higher K = more capacitance!</p></div>`,
    `<div class="memory"><div class="mlbl">Quick fire recall</div><p>⚡ V = kQ/r · W = qΔV · C = ε₀A/d · U = ½CV² · Series: 1/C = sum of 1/C · Parallel: C = sum of C</p></div>`
   ]},
  {icon:'🌊',title:'Current Electricity',sub:'The flow of charge that powers the world',
   tabs:['Current & Drift','Resistance','Kirchhoff Laws','Wheatstone','Recall'],
   content:[
    `<div class="analogy"><div class="albl">Current = Water in a pipe</div><p>More pressure (voltage) = more flow (current). Narrower pipe (more resistance) = less flow. This is Ohm's Law in everyday life — every wire you see is living this equation!</p></div>
     <div class="fcard"><span class="formula">I = Q/t = nAev_d</span><span class="meaning">Current = charge/sec = electrons×area×drift speed</span></div>
     <div class="fcard"><span class="formula">v_d = eEτ/m</span><span class="meaning">Drift velocity of electrons</span></div>
     <div class="memory"><div class="mlbl">Mind-bending fact</div><p>Electrons drift at ~mm/s but electric field spreads at speed of light. Like a pipe already full of water — push one end, other end flows instantly!</p></div>`,
    `<div class="fcard"><span class="formula">V = IR</span><span class="meaning">Ohm's Law — the fundamental law!</span></div>
     <div class="fcard"><span class="formula">R = ρL/A</span><span class="meaning">Resistance from material (ρ = resistivity)</span></div>
     <div class="fcard"><span class="formula">R_t = R₀(1+αΔT)</span><span class="meaning">Resistance changes with temperature</span></div>
     <div class="izone"><h4>🔌 Ohm's Law Calculator</h4>
     <div class="slider-r"><label>Voltage (V)</label><input type=range min=1 max=24 value=9 id=vv oninput=calcOhm()><span id=vvv>9 V</span></div>
     <div class="slider-r"><label>Resistance (Ω)</label><input type=range min=1 max=20 value=3 id=rv oninput=calcOhm()><span id=rvv>3 Ω</span></div>
     <div class="result-box"><div class="rval" id=ohm_i>3.0 A</div><div class="runit">Current</div></div></div>
     <div class="fcard"><span class="formula">P = VI = I²R = V²/R</span><span class="meaning">Power — 3 forms, all equivalent!</span></div>`,
    `<div class="analogy"><div class="albl">Traffic rules for current</div><p>KCL: At any road junction, cars in = cars out. Current in = Current out at any node. KVL: On any loop of road, net altitude change = 0. Same for voltage drops!</p></div>
     <div class="fcard"><span class="formula">ΣI_in = ΣI_out</span><span class="meaning">KCL — junction rule (charge conservation)</span></div>
     <div class="fcard"><span class="formula">ΣV_loop = 0</span><span class="meaning">KVL — loop rule (energy conservation)</span></div>`,
    `<div class="analogy"><div class="albl">Balance beam analogy</div><p>Wheatstone bridge is a balance beam. When perfectly balanced (null condition — galvanometer reads 0), you can find ANY unknown resistance precisely. No calibration error!</p></div>
     <div class="fcard"><span class="formula">P/Q = R/S</span><span class="meaning">Balanced Wheatstone Bridge</span></div>
     <div class="fcard"><span class="formula">l₁/l₂ = R₁/R₂</span><span class="meaning">Meter bridge ratio</span></div>
     <div class="fcard"><span class="formula">ε = I(R+r)</span><span class="meaning">EMF = terminal V + internal drop</span></div>`,
    `<div class="memory"><div class="mlbl">Current electricity in one breath</div><p>⚡ I=Q/t · V=IR · R=ρL/A · P=VI<br>🔀 KCL: current in = out · KVL: voltage loop = 0<br>⚖️ Wheatstone: P/Q = R/S when balanced<br>🔋 EMF = V_terminal + Ir</p></div>`
   ]},
  {icon:'🧲',title:'Magnetism & Moving Charges',sub:'Forces between magnets and currents',
   tabs:['Lorentz Force','Biot-Savart','Ampere\'s Law','Magnetic Materials','Recall'],
   content:[
    `<div class="analogy"><div class="albl">The sideways punch</div><p>A moving charge in a magnetic field feels a force SIDEWAYS — perpendicular to both its motion AND the field. Like a spinning top wobbling sideways when you tap it, not in the direction you pushed!</p></div>
     <div class="fcard"><span class="formula">F = qvBsinθ</span><span class="meaning">Lorentz force on moving charge</span></div>
     <div class="fcard"><span class="formula">F = BILsinθ</span><span class="meaning">Force on current-carrying conductor</span></div>
     <div class="fcard"><span class="formula">r = mv/qB</span><span class="meaning">Radius of circular path in B field</span></div>
     <div class="memory"><div class="mlbl">Fleming's Left Hand Rule</div><p>Forefinger → Field · Middle finger → Current · Thumb → Force. "FBI" — Force, B-field, current I.</p></div>`,
    `<div class="fcard"><span class="formula">dB = μ₀Idlsinθ/4πr²</span><span class="meaning">Biot-Savart law — field from wire element</span></div>
     <div class="fcard"><span class="formula">B = μ₀I/2πr</span><span class="meaning">Long straight wire at distance r</span></div>
     <div class="fcard"><span class="formula">B = μ₀NI/2R</span><span class="meaning">Center of circular loop</span></div>
     <div class="fcard"><span class="formula">B = μ₀nI</span><span class="meaning">Inside solenoid (n = turns/meter)</span></div>`,
    `<div class="analogy"><div class="albl">Gauss's Law for magnetism</div><p>Ampere's Law is the magnetic version of Gauss's Law. Walk around any closed loop — the sum of B·dl = μ₀ × current through the loop. Brilliant shortcut with symmetry!</p></div>
     <div class="fcard"><span class="formula">∮B·dl = μ₀I</span><span class="meaning">Ampere's Circuital Law</span></div>
     <div class="fcard"><span class="formula">τ = NIABsinθ = mBsinθ</span><span class="meaning">Torque on current loop</span></div>
     <div class="fcard"><span class="formula">m = NIA</span><span class="meaning">Magnetic dipole moment</span></div>`,
    `<div class="memory"><div class="mlbl">Dia / Para / Ferro</div><p><strong>Diamagnetic</strong> (bismuth): repelled, χ negative, μᵣ slightly &lt; 1<br><strong>Paramagnetic</strong> (aluminium): attracted weakly, χ small positive<br><strong>Ferromagnetic</strong> (iron): STRONGLY attracted, forms magnetic domains!</p></div>
     <div class="fcard"><span class="formula">B = μ₀μᵣH</span><span class="meaning">B inside a magnetic material</span></div>`,
    `<div class="memory"><div class="mlbl">Magnetism master recall</div><p>⚡ F = qvBsinθ (Lorentz) · r = mv/qB (circular motion)<br>🔁 B = μ₀I/2πr (wire) · B = μ₀nI (solenoid)<br>⚖️ τ = mBsinθ (torque on loop)<br>🧲 Ferro > Para > Dia in magnetic response</p></div>`
   ]},
  {icon:'💡',title:'Electromagnetic Induction',sub:'How generators and transformers work',
   tabs:['Faraday\'s Law','Lenz\'s Law','Self/Mutual Induction','AC Generator','Recall'],
   content:[
    `<div class="analogy"><div class="albl">The magic of CHANGE</div><p>Faraday's insight: only a CHANGING magnetic field creates current. Static field does nothing — only change matters! Like wind only pushes you when moving, not in still air.</p></div>
     <div class="fcard"><span class="formula">ε = −dΦ/dt</span><span class="meaning">Induced EMF = −rate of change of flux</span></div>
     <div class="fcard"><span class="formula">Φ = BAcosθ</span><span class="meaning">Magnetic flux through a surface</span></div>
     <div class="fcard"><span class="formula">ε = NΔΦ/Δt</span><span class="meaning">For N turns of coil</span></div>`,
    `<div class="analogy"><div class="albl">Nature is a stubborn rebel</div><p>Lenz's Law: induced current flows to OPPOSE the change that caused it. Push magnet in → induced current creates field opposing motion. Like nature saying "Don't change me!"</p></div>
     <div class="memory"><div class="mlbl">Real example</div><p>Drop a magnet through a copper tube — it falls in SLOW MOTION! Every tiny movement induces current opposing its fall. Maglev train braking uses this principle.</p></div>`,
    `<div class="fcard"><span class="formula">ε = −L(dI/dt)</span><span class="meaning">Self-induced EMF (L = inductance)</span></div>
     <div class="fcard"><span class="formula">L = μ₀N²A/l</span><span class="meaning">Inductance of solenoid</span></div>
     <div class="fcard"><span class="formula">V₁/V₂ = N₁/N₂</span><span class="meaning">Transformer turns ratio</span></div>
     <div class="memory"><div class="mlbl">Transformer insight</div><p>Step-up transformer: N₂ > N₁ → V₂ > V₁ but I₂ &lt; I₁ (energy conserved!). Power grids use step-up (long transmission) then step-down (home use).</p></div>`,
    `<div class="analogy"><div class="albl">Spin to get electricity</div><p>Spin a coil in a magnetic field → flux changes → EMF is induced → AC current flows. Faster spin + stronger field = more voltage. This is every power plant on Earth!</p></div>
     <div class="fcard"><span class="formula">ε = ε₀sinωt</span><span class="meaning">AC output of generator</span></div>
     <div class="fcard"><span class="formula">ε₀ = NBAω</span><span class="meaning">Peak EMF depends on N, B, A, angular speed</span></div>`,
    `<div class="memory"><div class="mlbl">EMI in one story</div><p>⚡ Change flux → EMF (Faraday) · EMF fights change (Lenz) · Coil has inductance = electrical inertia · Spin coil → AC → transformer steps voltage up/down · This is why electricity travels thousands of km to your home!</p></div>`
   ]},
  {icon:'📡',title:'EM Waves & AC Circuits',sub:'Invisible waves and alternating current',
   tabs:['EM Spectrum','AC Basics','LCR Resonance','Power Factor','Recall'],
   content:[
    `<div class="analogy"><div class="albl">Light is electric + magnetic!</div><p>Maxwell's genius: a changing E field creates B field, and changing B field creates E field. They sustain each other — a wave that travels through vacuum at c = 3×10⁸ m/s. Light, radio, X-rays are all EM waves!</p></div>
     <div class="fcard"><span class="formula">c = 1/√(μ₀ε₀) = 3×10⁸ m/s</span><span class="meaning">Speed of light from Maxwell's theory</span></div>
     <div class="memory"><div class="mlbl">EM Spectrum (low→high frequency)</div><p>Radio → Microwave → Infrared → Visible → UV → X-rays → Gamma rays<br>"Raging Martians Invade Venus Using X-ray Guns"</p></div>`,
    `<div class="fcard"><span class="formula">V = V₀sinωt</span><span class="meaning">AC voltage (sinusoidal)</span></div>
     <div class="fcard"><span class="formula">V_rms = V₀/√2 ≈ 0.707V₀</span><span class="meaning">RMS value (what voltmeter shows)</span></div>
     <div class="fcard"><span class="formula">X_L = ωL</span><span class="meaning">Inductive reactance (Ω)</span></div>
     <div class="fcard"><span class="formula">X_C = 1/ωC</span><span class="meaning">Capacitive reactance (Ω)</span></div>
     <div class="memory"><div class="mlbl">ELI the ICE man</div><p><strong>ELI</strong>: Voltage (E) leads current (I) in Inductor (L) by 90°<br><strong>ICE</strong>: Current (I) leads voltage (E) in Capacitor (C) by 90°</p></div>`,
    `<div class="analogy"><div class="albl">Resonance = radio tuning</div><p>At resonance, X_L = X_C — they cancel! Circuit draws maximum current. This is exactly how a radio tunes to a station — adjust capacitor until resonant frequency matches the station's frequency!</p></div>
     <div class="fcard"><span class="formula">f₀ = 1/(2π√LC)</span><span class="meaning">Resonant frequency of LCR circuit</span></div>
     <div class="fcard"><span class="formula">Z = √(R²+(X_L−X_C)²)</span><span class="meaning">Impedance (total AC resistance)</span></div>
     <div class="izone"><h4>📻 Resonance Calculator</h4>
     <div class="slider-r"><label>L (mH)</label><input type=range min=10 max=100 value=50 id=ll oninput=calcRes()><span id=llv>50 mH</span></div>
     <div class="slider-r"><label>C (μF)</label><input type=range min=1 max=20 value=10 id=cc oninput=calcRes()><span id=ccv>10 μF</span></div>
     <div class="result-box"><div class="rval" id=f0val>225 Hz</div><div class="runit">Resonant frequency</div></div></div>`,
    `<div class="fcard"><span class="formula">P = V_rms·I_rms·cosφ</span><span class="meaning">Real power in AC circuit</span></div>
     <div class="fcard"><span class="formula">cosφ = R/Z</span><span class="meaning">Power factor (0 to 1)</span></div>
     <div class="memory"><div class="mlbl">Power factor insight</div><p>Pure R: cosφ = 1 (all power consumed). Pure L or C: cosφ = 0 (no power consumed, just stored and returned!). Real circuits have cosφ between 0 and 1.</p></div>`,
    `<div class="memory"><div class="mlbl">EM+AC master recall</div><p>🌊 EM waves travel at c = 3×10⁸ m/s · E and B oscillate perpendicular<br>⚡ AC: V_rms = V₀/√2 · Resonance: f₀ = 1/(2π√LC)<br>🧠 ELI the ICE man for phase!<br>📻 Resonance = radio tuning principle</p></div>`
   ]},
  {icon:'🔍',title:'Ray Optics',sub:'How mirrors and lenses shape light',
   tabs:['Mirrors','Refraction','Lenses','Prism & Dispersion','Recall'],
   content:[
    `<div class="analogy"><div class="albl">Mirror = perfect ball bounce</div><p>Light bounces off a mirror like a ball off a wall: angle in = angle out. Concave mirror focuses (satellite dish). Convex mirror spreads (rear-view mirror — wider view, objects appear smaller).</p></div>
     <div class="fcard"><span class="formula">1/v + 1/u = 1/f</span><span class="meaning">Mirror formula (new Cartesian sign convention)</span></div>
     <div class="fcard"><span class="formula">f = R/2</span><span class="meaning">Focal length = half radius of curvature</span></div>
     <div class="fcard"><span class="formula">m = −v/u = h′/h</span><span class="meaning">Magnification</span></div>
     <div class="memory"><div class="mlbl">Sign convention — always</div><p>All distances from pole. Direction of incident light = +ve. Opposite = −ve. Object on left → u is ALWAYS negative!</p></div>`,
    `<div class="analogy"><div class="albl">Car going from road to mud</div><p>Light slows in denser media. When it slows at an angle, one side slows before the other → it turns (bends). The denser the medium, the more it bends!</p></div>
     <div class="fcard"><span class="formula">n₁sinθ₁ = n₂sinθ₂</span><span class="meaning">Snell's Law — fundamental!</span></div>
     <div class="fcard"><span class="formula">n = c/v</span><span class="meaning">Refractive index = c/speed in medium</span></div>
     <div class="fcard"><span class="formula">sinθ_c = n₂/n₁</span><span class="meaning">Critical angle (for TIR, n₁ > n₂)</span></div>
     <div class="memory"><div class="mlbl">Optical fiber — TIR magic</div><p>Light hits the glass-air boundary at > critical angle → bounces back completely (Total Internal Reflection). Light travels thousands of km inside fiber this way. Your internet uses this!</p></div>`,
    `<div class="fcard"><span class="formula">1/f = (n−1)(1/R₁−1/R₂)</span><span class="meaning">Lens maker's formula</span></div>
     <div class="fcard"><span class="formula">P = 1/f (in metres)</span><span class="meaning">Power of lens in Diopters</span></div>
     <div class="fcard"><span class="formula">P = P₁+P₂+…</span><span class="meaning">Lenses in contact: powers add!</span></div>
     <div class="izone"><h4>🔍 Lens Calculator</h4>
     <div class="slider-r"><label>Object u (cm)</label><input type=range min=-50 max=-5 value=-20 id=lu oninput=calcLens()><span id=luv>−20 cm</span></div>
     <div class="slider-r"><label>Focal f (cm)</label><input type=range min=5 max=30 value=10 id=lf oninput=calcLens()><span id=lfv>10 cm</span></div>
     <div class="result-box"><div class="rval" id=lv>20.0 cm</div><div class="runit">Image distance v</div></div></div>`,
    `<div class="analogy"><div class="albl">Prism = music equalizer for light</div><p>White light is a MIX of all colors. Prism bends each color differently (violet most, red least) → splits into rainbow VIBGYOR. Different wavelengths = different refractive indices!</p></div>
     <div class="fcard"><span class="formula">δ = (n−1)A</span><span class="meaning">Deviation by thin prism</span></div>
     <div class="memory"><div class="mlbl">VIBGYOR wavelength rule</div><p>Violet = shortest λ → bends MOST (highest n). Red = longest λ → bends LEAST. "Violent Vikings Insist Gently: Bending Red last!"</p></div>`,
    `<div class="memory"><div class="mlbl">Ray optics master formulas</div><p>🔍 Mirror/Lens: 1/v + 1/u = 1/f<br>🌊 Snell: n₁sinθ₁ = n₂sinθ₂<br>💡 TIR: sinθ_c = n₂/n₁ (fiber optics!)<br>🌈 n_violet > n_red → dispersion<br>👓 Power of lens: P = 1/f(m)</p></div>`
   ]},
  {icon:'🌈',title:'Wave Optics',sub:'Interference, diffraction & polarization',
   tabs:['Huygens & Interference','Young\'s YDSE','Diffraction','Polarization','Recall'],
   content:[
    `<div class="analogy"><div class="albl">Waves can ADD and CANCEL</div><p>Two waves meeting: crests + crests = brighter (constructive). Crest + trough = darkness (destructive). Huygens: every point on a wavefront IS a new source of secondary wavelets. Beautiful and simple!</p></div>
     <div class="fcard"><span class="formula">Δx = nλ</span><span class="meaning">Constructive: path difference = nλ (bright)</span></div>
     <div class="fcard"><span class="formula">Δx = (2n+1)λ/2</span><span class="meaning">Destructive: (2n+1)λ/2 (dark)</span></div>`,
    `<div class="analogy"><div class="albl">Young proved Newton wrong in 1801!</div><p>Shine light through two tiny slits → alternating bright and dark bands on screen. This ONLY happens if light is a wave. Newton said particles, Young showed waves. Game-changer!</p></div>
     <div class="fcard"><span class="formula">β = λD/d</span><span class="meaning">Fringe width (D=screen dist, d=slit sep)</span></div>
     <div class="izone"><h4>🌈 YDSE Fringe Calculator</h4>
     <div class="slider-r"><label>λ (nm)</label><input type=range min=400 max=700 value=550 id=yw oninput=calcYDSE()><span id=ywv>550 nm</span></div>
     <div class="slider-r"><label>D (m)</label><input type=range min=1 max=5 value=2 id=yd oninput=calcYDSE()><span id=ydv>2 m</span></div>
     <div class="slider-r"><label>d (mm)</label><input type=range min=1 max=5 value=1 id=ys oninput=calcYDSE()><span id=ysv>1 mm</span></div>
     <div class="result-box"><div class="rval" id=ydse_b>1.10 mm</div><div class="runit">Fringe width β</div></div></div>`,
    `<div class="analogy"><div class="albl">Waves bend around corners</div><p>Sound travels around walls (you can hear around corners). Light also bends around tiny edges — but needs very narrow slits because wavelength is so small. Single slit gives central bright band + weaker sides.</p></div>
     <div class="fcard"><span class="formula">sinθ = λ/a</span><span class="meaning">First dark fringe — single slit (width a)</span></div>
     <div class="fcard"><span class="formula">Δθ = 1.22λ/D</span><span class="meaning">Rayleigh criterion — resolution limit</span></div>`,
    `<div class="analogy"><div class="albl">Polarization — one-direction vibration</div><p>Normal light vibrates in ALL directions. Polarized light vibrates in ONE direction only (like rope shaking only up-down). Polaroid sunglasses filter glare from roads and water using this!</p></div>
     <div class="fcard"><span class="formula">I = I₀cos²θ</span><span class="meaning">Malus's Law — intensity after polarizer</span></div>
     <div class="fcard"><span class="formula">tanθ_B = n</span><span class="meaning">Brewster's angle — perfect polarization</span></div>`,
    `<div class="memory"><div class="mlbl">Wave optics in 4 lines</div><p>🌊 Constructive: Δx = nλ · Destructive: Δx = (2n+1)λ/2<br>🔬 YDSE: β = λD/d (thinner slit = wider fringes!)<br>📐 Diffraction: sinθ = λ/a (single slit)<br>☀️ Malus: I = I₀cos²θ (polarization)</p></div>`
   ]},
  {icon:'🌑',title:'Dual Nature of Light',sub:'Wave AND particle — physics gets delightfully weird',
   tabs:['Photoelectric Effect','de Broglie Wave','Davisson-Germer','Key Graphs','Recall'],
   content:[
    `<div class="analogy"><div class="albl">Einstein's Nobel Prize idea (1921)</div><p>Light isn't just a wave — it comes in packets called PHOTONS. When photons hit a metal surface, they knock out electrons IF photon energy is high enough. This is the photoelectric effect — it powers every solar cell!</p></div>
     <div class="fcard"><span class="formula">E = hf = hc/λ</span><span class="meaning">Energy of one photon · h = 6.63×10⁻³⁴ J·s</span></div>
     <div class="fcard"><span class="formula">KE_max = hf − φ</span><span class="meaning">Kinetic energy of ejected electron</span></div>
     <div class="fcard"><span class="formula">eV₀ = hf − φ</span><span class="meaning">Stopping potential V₀</span></div>
     <div class="memory"><div class="mlbl">Critical insight for exams</div><p>Intensity does NOT change KE — only changes number of electrons! Only FREQUENCY determines KE. More intensity = more electrons, same speed. Higher frequency = faster electrons!</p></div>`,
    `<div class="analogy"><div class="albl">If light is a particle, matter is a wave!</div><p>de Broglie's revolutionary idea: if light (a wave) behaves like particles (photons), then particles should behave like waves! Every moving object has a wavelength. For electrons, it's measurable!</p></div>
     <div class="fcard"><span class="formula">λ = h/mv = h/p</span><span class="meaning">de Broglie wavelength of any matter</span></div>
     <div class="fcard"><span class="formula">λ = h/√(2mKE)</span><span class="meaning">For particle with kinetic energy KE</span></div>
     <div class="memory"><div class="mlbl">Why we don't see our wave</div><p>Your wavelength = h/mv. You're huge and fast → λ is incredibly tiny (10⁻³⁵ m) — undetectable! Electrons are tiny and slow → λ ≈ atomic spacing → DETECTABLE!</p></div>`,
    `<div class="analogy"><div class="albl">Electrons diffracting like X-rays!</div><p>Davisson and Germer fired electrons at nickel crystal and got diffraction patterns — just like X-rays diffract. Proof! Electrons ARE waves. de Broglie won Nobel Prize 1929. Electron microscopes use this.</p></div>
     <div class="fcard"><span class="formula">f₀ = φ/h</span><span class="meaning">Threshold frequency (minimum for emission)</span></div>
     <div class="fcard"><span class="formula">λ_min = hc/eV</span><span class="meaning">Minimum X-ray wavelength at voltage V</span></div>`,
    `<div class="memory"><div class="mlbl">Two key graph facts</div><p>KE vs Frequency: STRAIGHT LINE, slope = h, x-intercept = f₀, y-intercept = −φ<br>KE vs Intensity: HORIZONTAL LINE — KE doesn't change with intensity! (Most common exam trap!)</p></div>`,
    `<div class="memory"><div class="mlbl">Dual nature 30-second recall</div><p>🌊 Light = wave (interference) AND particle (photoelectric effect)<br>⚛ Matter = particle (momentum) AND wave (λ=h/p)<br>📸 Only FREQUENCY matters for KE in photoelectric!<br>🔬 Davisson-Germer proved de Broglie correct</p></div>`
   ]},
  {icon:'⚛️',title:'Atoms & Nuclei',sub:'The secret life inside the atom',
   tabs:['Atomic Models','Bohr Model','Hydrogen Spectrum','Radioactivity','Recall'],
   content:[
    `<div class="analogy"><div class="albl">Rutherford's gold foil shock</div><p>Thomson said atom is "plum pudding" — electrons scattered in positive dough. Rutherford fired alpha particles at gold foil — most passed through, a FEW bounced STRAIGHT BACK. Conclusion: tiny, dense NUCLEUS at center. Mostly empty space!</p></div>
     <div class="memory"><div class="mlbl">Size comparison</div><p>If atom = football stadium, nucleus = a marble in the center. Everything else is empty space. Mind-blowing!</p></div>`,
    `<div class="fcard"><span class="formula">r_n = n²a₀/Z</span><span class="meaning">Radius of nth orbit (a₀ = 0.529 Å)</span></div>
     <div class="fcard"><span class="formula">E_n = −13.6/n² eV</span><span class="meaning">Energy of nth orbit in hydrogen</span></div>
     <div class="fcard"><span class="formula">L = nh/2π</span><span class="meaning">Angular momentum quantization</span></div>
     <div class="memory"><div class="mlbl">Bohr's 4 postulates</div><p>1. Electrons orbit in fixed circular orbits · 2. L = nh/2π (quantized!) · 3. Orbiting electron doesn't radiate · 4. Emission/absorption when jumping orbits</p></div>`,
    `<div class="analogy"><div class="albl">Spectral lines = atom's fingerprint</div><p>Electrons jumping between energy levels release photons of specific energies (specific colors). Each element has unique spectral pattern — like a fingerprint. Astronomers use this to identify elements in stars millions of light-years away!</p></div>
     <div class="fcard"><span class="formula">1/λ = R(1/n₁²−1/n₂²)</span><span class="meaning">Rydberg formula for hydrogen spectrum</span></div>
     <div class="memory"><div class="mlbl">Spectral series to remember</div><p>Lyman → UV (n₁=1) · Balmer → Visible (n₁=2) · Paschen → IR (n₁=3)<br>Mnemonic: "LBP" — Lyman, Balmer, Paschen → UV, Visible, Infrared</p></div>`,
    `<div class="fcard"><span class="formula">N = N₀e^(−λt)</span><span class="meaning">Radioactive decay law</span></div>
     <div class="fcard"><span class="formula">T½ = 0.693/λ</span><span class="meaning">Half-life formula</span></div>
     <div class="fcard"><span class="formula">ΔE = Δmc²</span><span class="meaning">Mass defect → binding energy (Einstein!)</span></div>
     <div class="memory"><div class="mlbl">Half-life trick</div><p>After n half-lives: N = N₀ × (½)ⁿ<br>1 half-life → 50% · 2 → 25% · 3 → 12.5% · 10 → ~0.1%</p></div>`,
    `<div class="memory"><div class="mlbl">Atoms & Nuclei full recall</div><p>⚛ Bohr: E_n = −13.6/n² eV · r_n = n²a₀<br>🌈 Rydberg: 1/λ = R(1/n₁²−1/n₂²) · Balmer = visible<br>☢️ Radioactive: N = N₀e^−λt · T½ = 0.693/λ<br>💥 Nuclear binding: E = Δmc²</p></div>`
   ]},
  {icon:'💻',title:'Semiconductors',sub:'The silicon revolution — foundation of all electronics',
   tabs:['Energy Bands','p-n Junction','Diode Applications','Transistors','Recall'],
   content:[
    `<div class="analogy"><div class="albl">Energy bands — why materials differ</div><p>Electrons in solids live in "energy bands." Conductors: bands overlap (electrons move freely). Insulators: huge gap (electrons can't jump). Semiconductors: SMALL gap — push electrons across with heat, light, or voltage!</p></div>
     <div class="fcard"><span class="formula">n-type: Si + P (5e⁻)</span><span class="meaning">Extra electron = negative majority carriers</span></div>
     <div class="fcard"><span class="formula">p-type: Si + B (3e⁻)</span><span class="meaning">Hole = positive majority carriers</span></div>
     <div class="memory"><div class="mlbl">Doping analogy</div><p>Pure Si = neutral crowd. Add phosphorus atom (5 valence e⁻) → one free electron floating around = n-type. Add boron (3 valence e⁻) → one missing electron (hole) = p-type. Simple!</p></div>`,
    `<div class="analogy"><div class="albl">The one-way door</div><p>Join p-type + n-type silicon. Electrons rush from n to p, holes from p to n → depletion layer forms → built-in barrier. Forward bias removes barrier → current flows. Reverse bias increases barrier → no current!</p></div>
     <div class="fcard"><span class="formula">Forward bias: +V to p, −V to n</span><span class="meaning">Current flows freely (diode ON)</span></div>
     <div class="fcard"><span class="formula">Reverse bias: +V to n, −V to p</span><span class="meaning">No significant current (diode OFF)</span></div>`,
    `<div class="memory"><div class="mlbl">Diode applications</div><p>Rectifier: AC → DC conversion · LED: electron-hole recombination releases photon · Photodiode: photon creates electron-hole pair → current · Zener: maintains constant voltage (voltage regulator)</p></div>
     <div class="fcard"><span class="formula">V = Vz (Zener)</span><span class="meaning">Zener maintains constant output voltage</span></div>`,
    `<div class="analogy"><div class="albl">Transistor = electronic valve</div><p>Three layers: Emitter, Base, Collector (EBC sandwich). Tiny current at Base controls HUGE current from Emitter to Collector. This is amplification! Use as on/off = switch. Billions of these = your CPU chip!</p></div>
     <div class="fcard"><span class="formula">I_E = I_B + I_C</span><span class="meaning">KCL at transistor</span></div>
     <div class="fcard"><span class="formula">β = I_C/I_B</span><span class="meaning">Current gain (typically 100-500)</span></div>
     <div class="fcard"><span class="formula">A_v = −β·R_C/R_i</span><span class="meaning">Voltage gain of CE amplifier</span></div>`,
    `<div class="memory"><div class="mlbl">Semiconductors — the chip of civilization</div><p>💻 Si: 4 valence electrons → shares with 4 neighbors<br>⊕ Dope with B → p-type · Dope with P → n-type<br>🔀 p-n junction = diode = rectifier = LED<br>⚡ 2 junctions = transistor = amplifier = switch<br>🌐 10 billion transistors = your smartphone's brain!</p></div>`
   ]},
];

let ac=null,at=0;

function renderGrid(){
  const g=document.getElementById('grid');
  g.innerHTML=chapters.map((c,i)=>`
    <div class="ch-card ${ac===i?'active':''}" onclick="openCh(${i})" style="border-color:${ac===i?c.clr.replace(')',',0.6)').replace('rgb','rgba'):'rgba(0,212,255,0.15)'}">
      <div class="ch-icon-wrap" style="background:${c.bg};">
        <span style="font-size:20px">${c.icon}</span>
      </div>
      <div class="ch-num-badge" style="background:${c.bg};color:${c.clr};border:0.5px solid ${c.clr}30">${c.num}</div>
      <div class="ch-name">${c.name}</div>
    </div>
  `).join('');
}

function openCh(i){
  ac=i;at=0;
  renderGrid();
  renderLesson();
  const p=document.getElementById('panel');
  p.style.display='block';
  document.getElementById('pg').style.width=((i+1)/chapters.length*100)+'%';
  setTimeout(()=>p.scrollIntoView({behavior:'smooth',block:'nearest'}),100);
}

function renderLesson(){
  if(ac===null)return;
  const l=lessons[ac];
  const ch=chapters[ac];
  document.getElementById('lico').textContent=l.icon;
  document.getElementById('lico').style.background=ch.bg;
  document.getElementById('ltit').textContent=l.title;
  document.getElementById('lsub').textContent=l.sub;
  document.getElementById('tw').innerHTML=l.tabs.map((t,i)=>
    `<button class="tab-pill ${i===at?'active':''}" onclick="switchTab(${i})">${t}</button>`
  ).join('');
  document.getElementById('lb').innerHTML=l.content[at]+`
    <div class="nav-row">
      <button class="nav-b" onclick="prevTab()">← Previous</button>
      <button class="nav-b next" onclick="nextTab()">Next →</button>
    </div>`;
}

function switchTab(i){at=i;renderLesson();}
function nextTab(){
  if(at<lessons[ac].tabs.length-1){at++;renderLesson();}
  else if(ac<chapters.length-1){openCh(ac+1);}
}
function prevTab(){if(at>0){at--;renderLesson();}}

function calcCoul(){
  const q1=+document.getElementById('q1').value,q2=+document.getElementById('q2').value,r=+document.getElementById('rr').value;
  document.getElementById('q1v').textContent=q1+' μC';
  document.getElementById('q2v').textContent=q2+' μC';
  document.getElementById('rrv').textContent=r+' m';
  document.getElementById('fval').textContent=(9e9*q1*1e-6*q2*1e-6/(r*r)*1000).toFixed(1)+' mN';
}
function calcCap(){
  const a=+document.getElementById('ca').value,d=+document.getElementById('cd').value*1e-3;
  document.getElementById('cav').textContent=document.getElementById('ca').value+' m²';
  document.getElementById('cdv').textContent=document.getElementById('cd').value+' mm';
  document.getElementById('capval').textContent=(8.85e-12*a/d*1e12).toFixed(1)+' pF';
}
function calcOhm(){
  const v=+document.getElementById('vv').value,r=+document.getElementById('rv').value;
  document.getElementById('vvv').textContent=v+' V';
  document.getElementById('rvv').textContent=r+' Ω';
  document.getElementById('ohm_i').textContent=(v/r).toFixed(1)+' A';
}
function calcLens(){
  const u=+document.getElementById('lu').value,f=+document.getElementById('lf').value;
  document.getElementById('luv').textContent=u+' cm';
  document.getElementById('lfv').textContent=f+' cm';
  const v=1/(1/f-1/u);
  document.getElementById('lv').textContent=isFinite(v)?v.toFixed(1)+' cm':'∞';
}
function calcYDSE(){
  const lam=+document.getElementById('yw').value*1e-9,D=+document.getElementById('yd').value,d=+document.getElementById('ys').value*1e-3;
  document.getElementById('ywv').textContent=document.getElementById('yw').value+' nm';
  document.getElementById('ydv').textContent=D+' m';
  document.getElementById('ysv').textContent=document.getElementById('ys').value+' mm';
  document.getElementById('ydse_b').textContent=(lam*D/d*1000).toFixed(2)+' mm';
}
function calcRes(){
  const L=+document.getElementById('ll').value*1e-3,C=+document.getElementById('cc').value*1e-6;
  document.getElementById('llv').textContent=document.getElementById('ll').value+' mH';
  document.getElementById('ccv').textContent=document.getElementById('cc').value+' μF';
  document.getElementById('f0val').textContent=Math.round(1/(2*Math.PI*Math.sqrt(L*C)))+' Hz';
}

renderGrid();
</script>

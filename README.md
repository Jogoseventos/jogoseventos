<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>After Party Hosted by Travis Scott</title>
<style>
/* RESET */
* { margin:0; padding:0; box-sizing:border-box; font-family:'Arial', sans-serif; }
body { background:#111; color:#fff; overflow-x:hidden; }

/* HEADER */
header { background: rgba(0,0,0,0.8); padding:20px 40px; display:flex; justify-content:space-between; align-items:center; position:fixed; width:100%; top:0; z-index:1000; transition: background 0.3s; }
header.scrolled { background: rgba(0,0,0,1); }
header h1 { font-size:1.5rem; font-weight:bold; }
nav ul { list-style:none; display:flex; gap:20px; }
nav ul li a { color:#fff; text-decoration:none; transition: color 0.3s; }
nav ul li a:hover { color:#ff3c00; }
.menu-toggle { display:none; flex-direction:column; cursor:pointer; gap:5px; }
.menu-toggle span { width:25px; height:3px; background:#fff; }

/* HERO */
.hero { height:100vh; position:relative; display:flex; justify-content:center; align-items:center; text-align:center; overflow:hidden; }
.hero video { position:absolute; top:50%; left:50%; min-width:100%; min-height:100%; width:auto; height:auto; z-index:0; transform:translate(-50%,-50%); object-fit:cover; filter:brightness(0.6); animation:videoZoom 20s infinite alternate; }
@keyframes videoZoom { 0%{transform:translate(-50%,-50%) scale(1);} 100%{transform:translate(-50%,-50%) scale(1.05);} }
.hero-content { position:relative; z-index:2; animation:fadeInUp 1s ease forwards; }
.hero-content h2 { font-size:3rem; margin-bottom:20px; }
.hero-content p { font-size:1.2rem; margin-bottom:20px; }

/* PARTICLES */
#particles { position:absolute; top:0; left:0; width:100%; height:100%; z-index:1; }

/* BUTTONS */
.btn { display:inline-block; padding:12px 30px; border-radius:5px; text-decoration:none; color:#fff; transition:all 0.3s; animation:pulse 2s infinite; cursor:pointer; border:none; font-size:1rem; }
.gradient-btn { background:linear-gradient(45deg,#ff3c00,#ff8a00); background-size:200% 200%; animation:gradientShift 3s ease infinite; }
@keyframes gradientShift { 0%{background-position:0% 50%}50%{background-position:100% 50%}100%{background-position:0% 50%} }
.btn:hover { transform:scale(1.05); }

/* SECTIONS */
section { padding:100px 40px 60px; max-width:1200px; margin:0 auto; }
section h3 { font-size:2rem; margin-bottom:30px; opacity:0; transform:translateY(50px); transition:all 0.8s ease; }
section.visible h3 { opacity:1; transform:translateY(0); }
section p { line-height:1.6; margin-bottom:15px; opacity:0; transform:translateY(30px); transition:all 0.8s ease; }
section.visible p { opacity:1; transform:translateY(0); }

/* TICKETS */
.tickets { display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr)); gap:20px; margin-top:40px; }
.ticket-card { background:#1c1c1c; padding:20px; border-radius:10px; border:2px solid transparent; transition:transform 0.3s,border 0.3s,box-shadow 0.3s; cursor:pointer; }
.ticket-card:hover { transform:translateY(-10px) rotate(-1deg); border:2px solid #ff3c00; box-shadow:0 10px 20px rgba(255,60,0,0.5); }
.ticket-card h4 { margin-bottom:10px; color:#ff3c00; }
.ticket-card p { margin-bottom:15px; }

/* MODAL */
.modal { display:none; position:fixed; z-index:2000; left:0; top:0; width:100%; height:100%; overflow:auto; background:rgba(0,0,0,0.85); }
.modal-content { background:#222; margin:5% auto; padding:20px; border-radius:10px; max-width:800px; text-align:center; position:relative; }
.close { position:absolute; top:10px; right:15px; font-size:24px; cursor:pointer; color:#fff; }

/* COUNTER */
.counter-section { text-align:center; margin:50px 0; }
.counter { display:flex; justify-content:center; gap:30px; flex-wrap:wrap; }
.counter div { background:#1c1c1c; padding:20px 30px; border-radius:10px; }
.counter div span { display:block; font-size:2rem; color:#ff3c00; }
.counter div p { margin-top:5px; font-size:1rem; }

/* FOOTER */
footer { background:#000; text-align:center; padding:20px; margin-top:40px; }

/* ANIMATIONS */
@keyframes fadeInUp { from{opacity:0; transform:translateY(50px);} to{opacity:1; transform:translateY(0);} }
@keyframes pulse {0%,100%{transform:scale(1);}50%{transform:scale(1.05);} }

/* RESPONSIVE */
@media(max-width:768px){
  nav ul{display:none; flex-direction:column; gap:10px; background:#111; position:absolute; top:70px; right:0; width:200px; padding:20px; border-radius:5px;}
  nav ul.active{display:flex;}
  .menu-toggle{display:flex;}
  .hero-content h2{font-size:2rem;}
  .hero-content p{font-size:1rem;}
  .tickets{grid-template-columns:1fr;}
  .counter{flex-direction:column; gap:15px;}
}
</style>
</head>
<body>

<header>
  <h1>After Party</h1>
  <nav>
    <div class="menu-toggle" id="mobile-menu"><span></span><span></span><span></span></div>
    <ul class="nav-list">
      <li><a href="#details">Detalhes</a></li>
      <li><a href="#tickets">Ingressos</a></li>
      <li><a href="#countdown-section">Contador</a></li>
      <li><a href="#contact">Contato</a></li>
    </ul>
  </nav>
</header>

<section class="hero">
  <canvas id="particles"></canvas>
  <video autoplay muted loop>
    <source src="imagens/hero.mp4" type="video/mp4">
  </video>
  <div class="hero-content">
    <h2>Hosted by Travis Scott</h2>
    <p>Uma experiência única que você não vai querer perder!</p>
    <button class="btn gradient-btn open-checkout" data-product="VIP">Comprar Ingressos</button>
  </div>
</section>

<section class="details" id="details">
  <h3>Detalhes do Evento</h3>
  <p>Data: 12 de Setembro de 2025</p>
  <p>Local: São Paulo, Brasil</p>
  <p>Venha viver uma noite inesquecível com música, dança e muita energia!</p>
</section>

<section class="tickets-section" id="tickets">
  <h3>Ingressos</h3>
  <div class="tickets">
    <div class="ticket-card" data-product="VIP">
      <img src="imagens/vip.jpg" alt="VIP" style="width:100%; border-radius:8px; margin-bottom:10px;">
      <h4>VIP</h4>
      <p>Acesso completo ao evento e área VIP.</p>
      <button class="btn gradient-btn open-checkout">Comprar</button>
    </div>
    <div class="ticket-card" data-product="Geral">
      <img src="imagens/geral.jpg" alt="Geral" style="width:100%; border-radius:8px; margin-bottom:10px;">
      <h4>Geral</h4>
      <p>Acesso ao evento principal.</p>
      <button class="btn gradient-btn open-checkout">Comprar</button>
    </div>
    <div class="ticket-card" data-product="Early Bird">
      <img src="imagens/earlybird.jpg" alt="Early Bird" style="width:100%; border-radius:8px; margin-bottom:10px;">
      <h4>Early Bird</h4>
      <p>Desconto especial para os primeiros compradores.</p>
      <button class="btn gradient-btn open-checkout">Comprar</button>
    </div>
  </div>
</section>

<div class="modal" id="checkout-modal">
  <div class="modal-content">
    <span class="close">&times;</span>
    <h3 id="modal-title">Finalizar Compra</h3>
    <p>Confira e finalize seu ingresso abaixo:</p>
    <iframe id="checkout-frame" src="" width="100%" height="500px" frameborder="0"></iframe>
  </div>
</div>

<section class="counter-section" id="countdown-section">
  <h3>Contagem regressiva para o evento</h3>
  <div class="counter" id="countdown">
    <div><span id="days">00</span><p>Dias</p></div>
    <div><span id="hours">00</span><p>Horas</p></div>
    <div><span id="minutes">00</span><p>Minutos</p></div>
    <div><span id="seconds">00</span><p>Segundos</p></div>
  </div>
</section>

<footer id="contact">
  <p>&copy; 2025 After Party. Todos os direitos reservados.</p>
</footer>

<script>
// Menu mobile
const mobileMenu=document.getElementById('mobile-menu');
const navList=document.querySelector('nav ul');
mobileMenu.addEventListener('click',()=>navList.classList.toggle('active'));

// Scroll suave
document.querySelectorAll('nav ul li a').forEach(link=>{
  link.addEventListener('click',e=>{
    e.preventDefault();
    navList.classList.remove('active');
    document.querySelector(link.getAttribute('href')).scrollIntoView({behavior:'smooth'});
  });
});

// Parallax hero
const heroContent=document.querySelector('.hero-content');
window.addEventListener('scroll',()=>{
  const top=window.scrollY;
  heroContent.style.transform=`translateY(${top*0.2}px)`;
  document.querySelector('header').classList.toggle('scrolled',top>50);
});

// Fade-in seções
const sections=document.querySelectorAll('section');
function revealOnScroll(){
  const triggerBottom=window.innerHeight*0.85;
  sections.forEach(section=>{
    if(section.getBoundingClientRect().top<triggerBottom){
      section.classList.add('visible');
    }
  });
}
window.addEventListener('scroll',revealOnScroll);
window.addEventListener('load',revealOnScroll);

// Modal checkout com iframe
const modal=document.getElementById('checkout-modal');
const openBtns=document.querySelectorAll('.open-checkout');
const closeModal=document.querySelector('.close');
const iframe=document.getElementById('checkout-frame');
let currentProduct='';

openBtns.forEach(btn=>{
  btn.addEventListener('click',()=>{
    currentProduct=btn.parentElement.dataset.product||btn.dataset.product;
    document.getElementById('modal-title').innerText=`Comprar Ingresso - ${currentProduct}`;
    iframe.src=`https://checkout.perfectpay.com/?product=${encodeURIComponent(currentProduct)}`;
    modal.style.display='block';
  });
});
closeModal.addEventListener('click',()=>modal.style.display='none');
window.addEventListener('click',e=>{if(e.target==modal)modal.style.display='none';});

// Countdown
function countdown(){
  const countDate=new Date("Sep 12, 2025 20:00:00").getTime();
  const now=new Date().getTime();
  const gap=countDate-now;
  const second=1000,minute=second*60,hour=minute*60,day=hour*24;
  document.getElementById('days').innerText=Math.floor(gap/day);
  document.getElementById('hours').innerText=Math.floor((gap%day)/hour);
  document.getElementById('minutes').innerText=Math.floor((gap%hour)/minute);
  document.getElementById('seconds').innerText=Math.floor((gap%minute)/second);
}
setInterval(countdown,1000);
countdown();

// Particles
const canvas=document.getElementById('particles');
const ctx=canvas.getContext('2d');
let particlesArray=[];
function initParticles(){for(let i=0;i<100;i++){particlesArray.push({x:Math.random()*canvas.width,y:Math.random()*canvas.height,r:Math.random()*2+1,d:Math.random()*50});}}
function resizeCanvas(){canvas.width=window.innerWidth;canvas.height=window.innerHeight;initParticles();}
window.addEventListener('resize',resizeCanvas);
resizeCanvas();
let angle=0;
function animateParticles(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  particlesArray.forEach(p=>{ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2,false);ctx.fillStyle='rgba(255,255,255,0.6)';ctx.fill();});
  angle+=0.01;
  particlesArray.forEach(p=>{p.y+=Math.cos(angle+p.d)+1+p.r/2;p.x+=Math.sin(angle)*2;if(p.x>canvas.width+5||p.x<0||p.y>canvas.height){p.x=Math.random()*canvas.width;p.y=-10;}});
  requestAnimationFrame(animateParticles);
}
animateParticles();
</script>

</body>
</html>

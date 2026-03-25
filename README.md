<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Euphoria RUST</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet">

<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Orbitron',sans-serif;}

body{
background:#000;
color:#fff;
}

/* VIDEO */
#bg-video{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
object-fit:cover;
z-index:-4;
}

/* ЗАТЕМНЕНИЕ */
body::before{
content:"";
position:fixed;
width:100%;
height:100%;
background:rgba(0,0,0,0.6);
z-index:-3;
}

/* ПЕРЕЛИВ */
body::after{
content:"";
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
background:linear-gradient(270deg, #ff0000, #ff5500, #ff0000, #000000);
background-size:600% 600%;
animation:gradientFlow 15s ease infinite;
z-index:-2;
opacity:0.25;
pointer-events:none;
}

@keyframes gradientFlow{
0%{background-position:0% 50%;}
50%{background-position:100% 50%;}
100%{background-position:0% 50%;}
}

/* ЧАСТИЦЫ */
#particles-js{
position:fixed;
width:100%;
height:100%;
z-index:-1;
}

/* НЕОН */
#cursor-glow{
position:fixed;
width:300px;
height:300px;
background:radial-gradient(circle, rgba(255,0,0,0.4) 0%, transparent 70%);
border-radius:50%;
pointer-events:none;
transform:translate(-50%, -50%);
z-index:0;
transition:0.05s;
}

/* NAV */
nav{
position:fixed;
top:0;
width:100%;
background:rgba(0,0,0,0.8);
backdrop-filter:blur(10px);
display:flex;
justify-content:center;
gap:30px;
padding:15px;
z-index:1000;
}

nav a{
color:#fff;
text-decoration:none;
cursor:pointer;
transition:0.3s;
}

nav a:hover{
color:#ff5500;
}

/* LOGIN */
.login{
position:absolute;
right:20px;
top:10px;
}

.login a{
background:#00c6ff;
padding:8px 15px;
border-radius:20px;
color:white;
text-decoration:none;
}

/* PAGES */
.page{
display:none;
padding:120px 20px;
text-align:center;
animation:fade 0.5s;
}

.page.active{
display:block;
}

@keyframes fade{
from{opacity:0;}
to{opacity:1;}
}

/* HERO */
.hero{
height:100vh;
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
}

/* SOCIAL */
.social-grid{
display:grid;
grid-template-columns:repeat(3,200px);
gap:25px;
margin-top:30px;
}

.social{
height:150px;
display:flex;
justify-content:center;
align-items:center;
border-radius:20px;
font-size:20px;
text-decoration:none;
color:white;
transition:0.3s;
}

.social:hover{
transform:scale(1.1);
box-shadow:0 0 30px white;
}

.discord{background:#5865F2;}
.telegram{background:#0088cc;}
.vk{background:#4c75a3;}

/* BUTTON */
.button{
margin-top:20px;
padding:15px 30px;
border:none;
border-radius:30px;
background:#ff5500;
color:white;
cursor:pointer;
}

/* INFO */
.info-buttons{
margin-top:30px;
display:flex;
flex-direction:column;
gap:15px;
align-items:center;
}

.info-btn{
width:300px;
padding:15px;
border:none;
border-radius:15px;
background:linear-gradient(45deg,#ff0000,#ff8800);
color:white;
cursor:pointer;
}

.info-content{
max-height:0;
overflow:hidden;
opacity:0;
transition:0.5s;
width:80%;
text-align:left;
}

.info-content.open{
max-height:2000px;
opacity:1;
margin-bottom:20px;
}
</style>
</head>

<body>

<video autoplay muted loop playsinline id="bg-video">
<source src="bg.mp4" type="video/mp4">
</video>

<div id="particles-js"></div>
<div id="cursor-glow"></div>

<nav>
<a onclick="openPage('home')">Главная</a>
<a onclick="openPage('info')">Информация</a>
<a href="https://euphoriarust.gamestores.app/" target="_blank">Магазин</a>

<div class="login">
<a href="#">🔐 Войти</a>
</div>
</nav>

<div id="home" class="page active">
<div class="hero">
<h1>💀 EUPHORIA RUST 💀</h1>

<div class="social-grid">
<a class="social discord" href="https://discord.gg/HctpAHPMpS" target="_blank">Discord</a>
<a class="social telegram" href="https://t.me/EuphoriaRustBot" target="_blank">Telegram</a>
<a class="social vk" href="https://vk.com/feed" target="_blank">VK</a>
</div>

<button class="button" onclick="copyIP(this)">📋 IP: 185.189.255.102:35100</button>
</div>
</div>

<div id="info" class="page">

<h2>📘 Информация</h2>

<div class="info-buttons">

<button class="info-btn" onclick="toggleBlock('rulesBlock')">
📜 Правила
</button>

<div id="rulesBlock" class="info-content">
<p>1.0 Любое сотрудничество с читерами (покупка информации, помощь в рейдах, передача ресурсов и т.п.) — бан от 120 дней до 1 года или пожизненно.</p>
<p>1.1 Использование читов, макросов или их наличие на ПК за последний год запрещено. Наказание применяется даже если софт не использовался. Признание также подпадает под данный пункт. [ban]</p>
<p>1.2 Клан-лидеры обязаны следить за своими участниками и не допускать игроков с читами. В противном случае возможен бан всего клана. [ban]</p>
<p>1.3 Запрещена любая помощь читерам, игра с ними, а также взаимодействие с багоюзерами и игроками, обошедшими бан. [ban]</p>
<p>1.4 Запрещено использовать и распространять информацию о багах (багоюз). [ban]</p>
<p>1.5 Запрещено покупать или заказывать услуги читеров (рейды, разведка и т.п.). [ban]</p>

<p>2.1 Запрещена реклама сторонних проектов, серверов и программ прямо в игре. [mute \ kick \ ban]</p>
<p>2.2 Запрещено разжигать межнациональную рознь и вести политические споры в игровом чате. [mute]</p>
<p>2.3 Запрещена продажа или покупка игровых ценностей за реальные деньги вне официального магазина. [ban]</p>
<p>2.4 Запрещено использовать никнеймы, схожие с администрацией. [предупреждение \ ban]</p>
<p>2.5 Запрещена клевета, дезинформация и распространение ложной информации о сервере или администрации. [mute \ ban]</p>
<p>2.7 Запрещены оскорбления администрации проекта. [mute \ ban]</p>

<p>3.1 Администрация имеет право в любой момент провести проверку игрока на наличие читов через Discord / AnyDesk / RustDesk. Отказ от проверки — [ban]</p>
<p>3.1 Выход из игры во время проверки без разрешения администратора расценивается как отказ. [ban]</p>
<p>3.2 Запрещён стримснайп (использование информации со стримов для получения преимущества). [kick \ ban]</p>
<p>3.3 Запрещена травля, преследование игрока и раскрытие личной информации. [mute \ ban]</p>
<p>3.4 Запрещены призывы к нарушению правил и провокации игроков. [ban]</p>
</div>

<button class="info-btn" onclick="toggleBlock('teamBlock')">
👥 NO LIMIT игроков
</button>

<div id="teamBlock" class="info-content">
<p>На сервере <b>EuphoriaRust X2</b> отсутствует ограничение на количество игроков в команде.</p>
<p>Вы можете играть в любом составе без лимитов и ограничений.</p>
</div>

<button class="info-btn" onclick="toggleBlock('respectBlock')">
💬 Уважайте игроков
</button>

<div id="respectBlock" class="info-content">
<p>Ну пожалуйста (:</p>
</div>

</div>
</div>
</div>

<!-- ПОДКЛЮЧЕНИЕ БИБЛИОТЕК -->
<script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>

<script>
function openPage(id){
document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
document.getElementById(id).classList.add('active');
}

function copyIP(btn){
navigator.clipboard.writeText("client.connect 185.189.255.102:35100");
btn.innerText="✅ Скопировано!";
setTimeout(()=>btn.innerText="📋 IP: 185.189.255.102:35100",2000);
}

function toggleBlock(id){
document.getElementById(id).classList.toggle("open");
}

document.addEventListener("mousemove",(e)=>{
const glow=document.getElementById("cursor-glow");
glow.style.left=e.clientX+"px";
glow.style.top=e.clientY+"px";
});

particlesJS("particles-js",{
particles:{
number:{value:60},
color:{value:"#ff0000"},
line_linked:{enable:true,color:"#ff0000"},
move:{speed:1.5}
}
});
</script>

</body>
</html>

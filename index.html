<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Pet Goose 🪿</title>
<style>
body {
  margin: 0;
  overflow: hidden;
  background: linear-gradient(180deg, #b3eaff, #f7f7f7);
  height: 100vh;
  cursor: none;
}

#goose {
  position: absolute;
  width: 140px;
  height: 140px;
  pointer-events: none;
  transform-origin: center center;
}

#goose img {
  width: 100%;
  height: 100%;
  user-select: none;
}

#cursor {
  position: absolute;
  width: 24px;
  height: 24px;
  background: radial-gradient(circle at 8px 8px, #ff7a7a, #c10000);
  border-radius: 50%;
  pointer-events: none;
  transform: translate(-50%, -50%);
}

.heart {
  position: absolute;
  color: #ff5a8a;
  font-size: 20px;
  animation: floatUp 1.2s ease-out forwards;
}

@keyframes floatUp {
  0% { transform: translateY(0); opacity: 1; }
  100% { transform: translateY(-60px); opacity: 0; }
}
</style>
</head>
<body>

<div id="goose">
  <img id="gooseImg" src="https://upload.wikimedia.org/wikipedia/commons/8/88/Cartoon_goose.svg" alt="goose">
</div>
<div id="cursor"></div>

<audio id="hugSound" src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_d8f62fef92.mp3?filename=pop-86917.mp3"></audio>
<audio id="quackSound" src="https://cdn.pixabay.com/download/audio/2023/02/28/audio_b0f6e3d1b8.mp3?filename=duck-quack-101563.mp3"></audio>

<script>
const goose = document.getElementById('goose');
const gooseImg = document.getElementById('gooseImg');
const cursor = document.getElementById('cursor');
const hugSound = document.getElementById('hugSound');
const quackSound = document.getElementById('quackSound');

let mouseX = window.innerWidth/2;
let mouseY = window.innerHeight/2;
let gooseX = 100;
let gooseY = 100;
let hugging = false;
let lastMouseX = mouseX;
let lastMouseY = mouseY;
let lastMouseTime = Date.now();

document.addEventListener('mousemove', e => {
  mouseX = e.clientX;
  mouseY = e.clientY;
});

function makeHeart(x,y){
  const h = document.createElement('div');
  h.className='heart';
  h.textContent='❤️';
  h.style.left=x+'px';
  h.style.top=y+'px';
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),1200);
}

function moveGoose(){
  const dx = mouseX - gooseX;
  const dy = mouseY - gooseY;
  const dist = Math.sqrt(dx*dx + dy*dy);

  const now = Date.now();
  const dt = now - lastMouseTime;
  const speed = Math.sqrt((mouseX - lastMouseX)**2 + (mouseY - lastMouseY)**2)/(dt||1);

  if(!hugging){
    if(speed>2.5){
      gooseImg.style.filter='brightness(0.8) sepia(0.5)';
      gooseImg.style.transform='rotate(-10deg)';
    } else {
      gooseImg.style.filter='';
      gooseImg.style.transform='';
    }

    // Slow movement: smaller factor
    if(dist>10){
      gooseX += dx*0.025; // slower
      gooseY += dy*0.025;
    }

    if(dist<50) startHug();
  }

  // Flap wings visually
  const flap = 1 + Math.sin(now*0.02)*0.05;
  goose.style.transform=`translate(${gooseX}px,${gooseY}px) scaleX(${dx<0?-1:1}) scale(${flap})`;

  cursor.style.left=mouseX+'px';
  cursor.style.top=mouseY+'px';

  lastMouseTime=now;
  lastMouseX=mouseX;
  lastMouseY=mouseY;
}

function startHug(){
  if(hugging) return;
  hugging=true;

  quackSound.currentTime=0;
  quackSound.play();

  hugSound.currentTime=0;
  hugSound.volume=0.2;
  hugSound.play();

  let t=0;
  const hugInterval=setInterval(()=>{
    t++;
    goose.style.transform=`translate(${gooseX}px,${gooseY}px) scale(${1+Math.sin(t*0.3)*0.1}) rotate(${Math.sin(t*0.3)*8}deg)`;
    makeHeart(mouseX+Math.random()*20-10, mouseY-30);
  },100);

  const lagInterval=setInterval(()=>{
    const lag = Math.sin(Date.now()*0.02)*0.1;
    cursor.style.transform=`translate(-50%,-50%) scale(${1+lag})`;
  },30);

  setTimeout(()=>{
    clearInterval(hugInterval);
    clearInterval(lagInterval);
    hugging=false;
  },2000);
}

// Goose looks away after 25s
setTimeout(()=>{
  gooseImg.style.transform='rotate(25deg) scale(1.05)';
  quackSound.currentTime=0;
  quackSound.play();
  setTimeout(()=>{
    gooseImg.style.transform='';
  },3000);
},25000);

setInterval(moveGoose,20);
</script>

</body>
</html>

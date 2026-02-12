# murtaza-website
<!DOCTYPE html>
<html lang="en">

<head>
<meta charset="UTF-8">
<title>Murtaza Rafiq</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">

<style>
body {
    margin: 0;
    padding: 0;
    height: 100vh;
    font-family: 'Poppins', sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(270deg, #ff512f, #dd2476, #ff7b54, #ff4f70);
    background-size: 800% 800%;
    animation: gradientBG 20s ease infinite;
    overflow: hidden;
}

@keyframes gradientBG {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
}

#particles {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    z-index: -1;
}

.box {
    background: rgba(255, 255, 255, 0.95);
    padding: 40px 30px;
    border-radius: 20px;
    text-align: center;
    box-shadow: 0 20px 50px rgba(0,0,0,0.3);
    animation: zoomIn 0.8s forwards;
}

@keyframes zoomIn {
    0% { transform: scale(0); opacity:0; }
    60% { transform: scale(1.05); opacity:1; }
    100% { transform: scale(1); }
}

img {
    width: 180px;
    border-radius: 50%;
    margin-bottom: 20px;
    box-shadow: 0 0 20px rgba(255,255,255,0.7);
    transition: transform 0.3s;
}
img:hover { transform: scale(1.1); }

.social-btn {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 12px 20px;
    margin: 8px;
    border-radius: 12px;
    background: #dd2476;
    color: white;
    font-weight: 600;
    font-size: 16px;
    text-decoration: none;
    transition: all 0.4s ease;
    box-shadow: 0 0 10px #dd2476;
}

.social-btn img {
    width: 25px;
    height: 25px;
    margin-right: 10px;
    filter: invert(1);
}

.social-btn:hover {
    transform: scale(1.1);
    box-shadow: 0 0 20px #ff512f, 0 0 30px #dd2476;
}

h1 {
    opacity: 0;
    animation: fadeIn 1s forwards;
    animation-delay: 0.5s;
}

@keyframes fadeIn {
    to { opacity: 1; }
}

.hashtags {
    margin-top: 20px;
    font-size: 14px;
    color: #dd2476;
    font-weight: 600;
}

.hashtags p {
    margin: 0;
}

footer {
    position: fixed;
    bottom: 10px;
    width: 100%;
    text-align: center;
    font-size: 14px;
    color: #ffffff;
    font-weight: 600;
    text-shadow: 1px 1px 5px rgba(0,0,0,0.5);
}

@media(max-width:600px){
    .box { padding: 30px 20px; }
    img { width: 140px; }
    .social-btn { font-size: 14px; padding: 10px 15px; }
    .social-btn img { width: 20px; height: 20px; margin-right: 6px; }
}
</style>
</head>

<body>

<canvas id="particles"></canvas>

<div class="box">
    <h1>Murtaza Rafiq</h1>
    
    <img src="murtaza.jpg" alt="Murtaza Rafiq">

    <!-- Buttons -->
    <a href="https://youtube.com/@murtazarafiq" target="_blank" class="social-btn">
        <img src="https://cdn-icons-png.flaticon.com/512/1384/1384060.png" alt="YouTube Icon"> YouTube
    </a>

    <a href="https://www.instagram.com/emminerrr" target="_blank" class="social-btn">
        <img src="https://cdn-icons-png.flaticon.com/512/1384/1384063.png" alt="Instagram Icon"> Instagram
    </a>

    <a href="https://emminerrworld.com/home" target="_blank" class="social-btn">
        <img src="https://cdn-icons-png.flaticon.com/512/1828/1828817.png" alt="Website Icon"> Academy
    </a>

    <a href="https://www.instagram.com/_thespeedykart" target="_blank" class="social-btn">
        <img src="https://cdn-icons-png.flaticon.com/512/1384/1384063.png" alt="Instagram Icon"> Instagram
    </a>

    <a href="https://apps.apple.com/in/app/the-speedykart/id6523429465" target="_blank" class="social-btn">
        <img src="https://cdn-icons-png.flaticon.com/512/888/888857.png" alt="iOS Icon"> iOS App
    </a>

    <a href="https://play.google.com/store/apps/details?id=com.speedy.speedycustomer" target="_blank" class="social-btn">
        <img src="https://cdn-icons-png.flaticon.com/512/888/888857.png" alt="Android Icon"> Android App
    </a>

    <!-- Hashtags -->
    <div class="hashtags">
        <p>#MurtazaRafiq #YouTube #Instagram #Academy #Apps</p>
    </div>
</div>

<!-- Footer with developer name -->
<footer>
    <p>Website Developed by UFAIQ DAR</p>
</footer>

<script>
// Particle JS
const canvas = document.getElementById('particles');
const ctx = canvas.getContext('2d');
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let particlesArray = [];
const colors = ['#ff512f','#dd2476','#ff7b54','#ff4f70'];

class Particle {
    constructor(){
        this.x = Math.random()*canvas.width;
        this.y = Math.random()*canvas.height;
        this.size = Math.random()*3+1;
        this.speedX = Math.random()*1-0.5;
        this.speedY = Math.random()*1-0.5;
        this.color = colors[Math.floor(Math.random()*colors.length)];
    }
    update(){
        this.x += this.speedX;
        this.y += this.speedY;
        if(this.x<0||this.x>canvas.width) this.speedX*=-1;
        if(this.y<0||this.y>canvas.height) this.speedY*=-1;
    }
    draw(){
        ctx.fillStyle = this.color;
        ctx.beginPath();
        ctx.arc(this.x,this.y,this.size,0,Math.PI*2);
        ctx.fill();
    }
}

function initParticles(){
    particlesArray = [];
    for(let i=0;i<100;i++){
        particlesArray.push(new Particle());
    }
}
function animateParticles(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    particlesArray.forEach(p=>{
        p.update();
        p.draw();
    });
    requestAnimationFrame(animateParticles);
}
initParticles();
animateParticles();

window.addEventListener('resize',()=>{
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    initParticles();
});
</script>

</body>
</html>

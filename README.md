<!DOCTYPE html>
<html lang="pl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Portfolio Maturalne - Informatyka</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    scroll-behavior:smooth;
}

body{
    font-family:'Poppins',sans-serif;
    background:#0f172a;
    color:white;
    overflow-x:hidden;
    transition:0.4s;
}

body.light{
    background:#f4f4f4;
    color:#111;
}

#loader{
    position:fixed;
    width:100%;
    height:100vh;
    background:#020617;
    z-index:999999;
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
}

.loader-circle{
    width:80px;
    height:80px;
    border:8px solid rgba(255,255,255,0.1);
    border-top:8px solid #3b82f6;
    border-radius:50%;
    animation:spin 1s linear infinite;
}

@keyframes spin{
    100%{
        transform:rotate(360deg);
    }
}

#loader p{
    margin-top:20px;
    color:white;
    letter-spacing:2px;
}

#particles{
    position:fixed;
    width:100%;
    height:100%;
    top:0;
    left:0;
    overflow:hidden;
    z-index:-1;
}

.particle{
    position:absolute;
    background:rgba(59,130,246,0.5);
    border-radius:50%;
    animation:float linear infinite;
}

@keyframes float{
    from{
        transform:translateY(100vh);
    }
    to{
        transform:translateY(-10vh);
    }
}

#progressBar{
    position:fixed;
    top:0;
    left:0;
    height:5px;
    background:linear-gradient(to right,#3b82f6,#06b6d4);
    width:0%;
    z-index:99999;
}

nav{
    position:fixed;
    width:100%;
    top:0;
    z-index:999;
    background:rgba(2,6,23,0.85);
    backdrop-filter:blur(10px);
    display:flex;
    justify-content:center;
    gap:30px;
    padding:20px;
}

nav a{
    color:white;
    text-decoration:none;
    font-weight:500;
    position:relative;
}

nav a::after{
    content:'';
    position:absolute;
    width:0%;
    height:2px;
    background:#3b82f6;
    bottom:-5px;
    left:0;
    transition:0.3s;
}

nav a:hover::after{
    width:100%;
}

.hero{
    min-height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    text-align:center;
    padding:20px;
    background:
    linear-gradient(rgba(2,6,23,0.8),rgba(2,6,23,0.9)),
    url('https://images.unsplash.com/photo-1515879218367-8466d910aaa4?q=80&w=1600');
    background-size:cover;
    background-position:center;
}

.hero h1{
    font-size:5rem;
    animation:fadeUp 1s ease;
}

.hero p{
    margin-top:20px;
    font-size:1.3rem;
    color:#cbd5e1;
    max-width:700px;
    animation:fadeUp 1.5s ease;
}

.hero button{
    margin-top:40px;
    padding:15px 35px;
    border:none;
    border-radius:15px;
    background:linear-gradient(135deg,#2563eb,#06b6d4);
    color:white;
    font-size:1rem;
    cursor:pointer;
    transition:0.4s;
}

.hero button:hover{
    transform:scale(1.1);
    box-shadow:0 0 25px #3b82f6;
}

@keyframes fadeUp{
    from{
        opacity:0;
        transform:translateY(40px);
    }
    to{
        opacity:1;
        transform:translateY(0);
    }
}

.container{
    width:90%;
    max-width:1200px;
    margin:auto;
}

section{
    margin:100px 0;
    padding:40px;
    border-radius:25px;
    background:rgba(30,41,59,0.7);
    backdrop-filter:blur(12px);
    border:1px solid rgba(255,255,255,0.08);
    transition:0.5s;
    opacity:0;
    transform:translateY(50px);
}

section.show{
    opacity:1;
    transform:translateY(0);
}

section:hover{
    transform:translateY(-10px);
    box-shadow:0 0 30px rgba(59,130,246,0.25);
}

h2{
    margin-bottom:20px;
    color:#60a5fa;
    font-size:2.2rem;
}

.projects{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:25px;
}

.card{
    background:#111827;
    padding:25px;
    border-radius:20px;
    transition:0.4s;
}

.card:hover{
    transform:translateY(-10px) scale(1.03);
    box-shadow:0 0 25px rgba(59,130,246,0.5);
}

.card h3{
    color:#60a5fa;
    margin-bottom:15px;
}

.timeline{
    border-left:4px solid #3b82f6;
    padding-left:30px;
}

.timeline-item{
    margin-bottom:40px;
    position:relative;
}

.timeline-item::before{
    content:'';
    position:absolute;
    width:18px;
    height:18px;
    background:#3b82f6;
    border-radius:50%;
    left:-40px;
    top:5px;
}

.stats{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
    gap:20px;
}

.stat{
    background:#111827;
    padding:30px;
    border-radius:20px;
    text-align:center;
}

.stat h3{
    font-size:3rem;
    color:#3b82f6;
}

.faq-item{
    margin-bottom:20px;
    background:#111827;
    border-radius:15px;
    overflow:hidden;
}

.faq-question{
    padding:20px;
    cursor:pointer;
    font-weight:bold;
}

.faq-answer{
    max-height:0;
    overflow:hidden;
    transition:0.4s;
    padding:0 20px;
}

.faq-item.active .faq-answer{
    max-height:200px;
    padding:20px;
}

.newsletter form{
    display:flex;
    flex-wrap:wrap;
    gap:15px;
}

.newsletter input{
    flex:1;
    padding:15px;
    border:none;
    border-radius:12px;
    background:#111827;
    color:white;
}

.newsletter button{
    padding:15px 30px;
    border:none;
    border-radius:12px;
    background:#2563eb;
    color:white;
    cursor:pointer;
}

.contact form{
    display:flex;
    flex-direction:column;
    gap:15px;
}

.contact input,
.contact textarea{
    padding:15px;
    border:none;
    border-radius:12px;
    background:#111827;
    color:white;
}

.contact button{
    padding:15px;
    border:none;
    border-radius:12px;
    background:#06b6d4;
    color:white;
    cursor:pointer;
}

#topBtn{
    position:fixed;
    bottom:30px;
    right:30px;
    width:60px;
    height:60px;
    border:none;
    border-radius:50%;
    background:#2563eb;
    color:white;
    font-size:22px;
    cursor:pointer;
    display:none;
    z-index:9999;
}

footer{
    text-align:center;
    padding:40px;
    background:#020617;
    margin-top:100px;
}

@media(max-width:768px){

    .hero h1{
        font-size:3rem;
    }

    nav{
        flex-wrap:wrap;
        gap:15px;
    }

    section{
        padding:25px;
    }
}

</style>
</head>

<body>

<div id="loader">
    <div class="loader-circle"></div>
    <p>Ładowanie portfolio...</p>
</div>

<div id="particles"></div>

<div id="progressBar"></div>

<nav>
    <a href="#about">Teoria</a>
    <a href="#projects">Projekty</a>
    <a href="#timeline">Nauka</a>
    <a href="#faq">FAQ</a>
    <a href="#contact">Kontakt</a>
</nav>

<section class="hero">
    <h1>Portfolio Maturalne</h1>
    <p>
        Nowoczesne portfolio do nauki informatyki, algorytmów,
        programowania i przygotowania do matury.
    </p>

    <button onclick="scrollToSection()">
        Rozpocznij
    </button>
</section>

<div class="container">

<section id="about">
    <h2>Selection Sort</h2>

    <p>
        Selection Sort to prosty algorytm sortowania oparty
        na wyszukiwaniu najmniejszego elementu.
    </p>

    <br>

<pre>
for(int i = 0; i &lt; n - 1; i++) {
    int minIndex = i;

    for(int j = i + 1; j &lt; n; j++) {
        if(tab[j] &lt; tab[minIndex]) {
            minIndex = j;
        }
    }

    swap(tab[i], tab[minIndex]);
}
</pre>

</section>

<section id="projects">

<h2>Projekty</h2>

<div class="projects">

<div class="card">
    <h3>Bubble Sort</h3>
    <p>Sortowanie bąbelkowe z animacją.</p>
</div>

<div class="card">
    <h3>Selection Sort</h3>
    <p>Algorytm wyboru z analizą O(n²).</p>
</div>

<div class="card">
    <h3>SQL</h3>
    <p>Bazy danych i zapytania.</p>
</div>

<div class="card">
    <h3>Rekurencja</h3>
    <p>Funkcje rekurencyjne i przykłady.</p>
</div>

</div>
</section>

<section id="timeline">

<h2>Timeline Nauki</h2>

<div class="timeline">

<div class="timeline-item">
    <h3>2024</h3>
    <p>Początek nauki programowania.</p>
</div>

<div class="timeline-item">
    <h3>2025</h3>
    <p>Algorytmy i struktury danych.</p>
</div>

<div class="timeline-item">
    <h3>2026</h3>
    <p>Przygotowanie do matury.</p>
</div>

</div>

</section>

<section>

<h2>Statystyki</h2>

<div class="stats">

<div class="stat">
    <h3 id="counter1">0</h3>
    <p>Zadań</p>
</div>

<div class="stat">
    <h3 id="counter2">0</h3>
    <p>Algorytmów</p>
</div>

<div class="stat">
    <h3 id="counter3">0</h3>
    <p>Projektów</p>
</div>

</div>

</section>

<section class="newsletter">

<h2>Newsletter</h2>

<p>
Zapisz się i otrzymuj nowe materiały maturalne.
</p>

<br>

<form id="newsletterForm">
    <input type="email" placeholder="Twój email" required>
    <button type="submit">Zapisz się</button>
</form>

<br>

<div id="newsletterMessage"></div>

</section>

<section id="faq">

<h2>FAQ</h2>

<div class="faq-item">
    <div class="faq-question">
        Czy portfolio jest responsywne?
    </div>

    <div class="faq-answer">
        Tak, działa na telefonach i komputerach.
    </div>
</div>

<div class="faq-item">
    <div class="faq-question">
        Czy zawiera JavaScript?
    </div>

    <div class="faq-answer">
        Tak, użyto nowoczesnego JavaScriptu.
    </div>
</div>

</section>

<section class="contact" id="contact">

<h2>Kontakt</h2>

<form>
    <input type="text" placeholder="Imię">
    <input type="email" placeholder="Email">
    <textarea rows="5" placeholder="Wiadomość"></textarea>

    <button type="submit">
        Wyślij
    </button>
</form>

</section>

</div>

<button id="topBtn">
↑
</button>

<footer>
    <p>
        Portfolio maturalne © 2026
    </p>

    <br>

    <p>
        🔥 Pan Turek jest najlepszy 🔥
    </p>

    <br>

    <p id="visits"></p>
</footer>

<script>

window.addEventListener("load",()=>{

    setTimeout(()=>{
        document.getElementById("loader").style.display="none";
    },1200);

});

const particles = document.getElementById("particles");

for(let i=0;i<60;i++){

    const p = document.createElement("div");

    p.classList.add("particle");

    let size = Math.random()*6+2;

    p.style.width=size+"px";
    p.style.height=size+"px";

    p.style.left=Math.random()*100+"vw";

    p.style.animationDuration=
    Math.random()*15+5+"s";

    p.style.opacity=Math.random();

    particles.appendChild(p);
}

const sections =
document.querySelectorAll("section");

window.addEventListener("scroll",()=>{

    sections.forEach(sec=>{

        const top =
        window.scrollY;

        const offset =
        sec.offsetTop - 500;

        if(top > offset){
            sec.classList.add("show");
        }

    });

});

window.addEventListener("scroll",()=>{

    let scroll =
    document.documentElement.scrollTop;

    let height =
    document.documentElement.scrollHeight -
    document.documentElement.clientHeight;

    let progress =
    (scroll/height)*100;

    document.getElementById("progressBar")
    .style.width = progress + "%";

});

const topBtn =
document.getElementById("topBtn");

window.addEventListener("scroll",()=>{

    if(window.scrollY > 500){
        topBtn.style.display="block";
    }else{
        topBtn.style.display="none";
    }

});

topBtn.onclick = ()=>{
    window.scrollTo({
        top:0,
        behavior:"smooth"
    });
};

function scrollToSection(){

    document.getElementById("about")
    .scrollIntoView({
        behavior:"smooth"
    });

}

const faq =
document.querySelectorAll(".faq-item");

faq.forEach(item=>{

    item.addEventListener("click",()=>{

        item.classList.toggle("active");

    });

});

function animateCounter(id,target){

    let count = 0;

    let speed = target/100;

    const counter =
    document.getElementById(id);

    const interval = setInterval(()=>{

        count += speed;

        counter.innerText =
        Math.floor(count);

        if(count >= target){

            counter.innerText = target;

            clearInterval(interval);

        }

    },20);

}

animateCounter("counter1",150);
animateCounter("counter2",35);
animateCounter("counter3",18);

const form =
document.getElementById("newsletterForm");

form.addEventListener("submit",(e)=>{

    e.preventDefault();

    document.getElementById("newsletterMessage")
    .innerHTML = `
    ✅ Dziękujemy za zapisanie!<br>
    🔥 Pan Turek jest najlepszy 🔥
    `;

    form.reset();

});

let visits =
localStorage.getItem("visits");

if(!visits){
    visits = 0;
}

visits++;

localStorage.setItem("visits",visits);

document.getElementById("visits")
.innerText =
"Odwiedziny strony: " + visits;

const darkBtn =
document.createElement("button");

darkBtn.innerText="🌙";

darkBtn.style.position="fixed";
darkBtn.style.left="20px";
darkBtn.style.bottom="20px";
darkBtn.style.width="60px";
darkBtn.style.height="60px";
darkBtn.style.borderRadius="50%";
darkBtn.style.border="none";
darkBtn.style.background="#111827";
darkBtn.style.color="white";
darkBtn.style.cursor="pointer";
darkBtn.style.zIndex="9999";

document.body.appendChild(darkBtn);

darkBtn.addEventListener("click",()=>{

    document.body.classList.toggle("light");

});

</script>

</body>
</html>

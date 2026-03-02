<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday My Love ❤️</title>

<style>
body{
margin:0;
font-family:'Segoe UI',sans-serif;
background:#ffe6eb;
color:#ff4d6d;
overflow:hidden;
}

.page{
display:none;
height:100vh;
justify-content:center;
align-items:center;
flex-wrap:wrap;
position:relative;
text-align:center;
}
.active{ display:flex; }

/* LEFT */
.left{ flex:1; padding:20px; }
.left h1{ font-size:42px; text-shadow:2px 2px 10px white; }
.subtitle{ font-size:18px; color:#444; }

/* BUTTON */
button{
padding:10px 20px;
border:none;
border-radius:25px;
background:#ff4d6d;
color:white;
cursor:pointer;
margin:10px;
box-shadow:0 4px 10px rgba(0,0,0,0.2);
}

/* IMAGE */
.right{ flex:1; position:relative; }
.circle-img{
width:260px;
height:260px;
border-radius:50%;
object-fit:cover;
border:8px solid #ff4d6d;
box-shadow:0 0 25px #ff4d6d;
}

/* FLOAT */
.float{
position:absolute;
font-size:30px;
animation:float 3s infinite ease-in-out;
}
@keyframes float{
0%{transform:translateY(0);}
50%{transform:translateY(-20px);}
100%{transform:translateY(0);}
}

/* MODAL */
.modal{
position:fixed;
top:0;left:0;
width:100%;height:100%;
background:rgba(0,0,0,0.6);
display:none;
justify-content:center;
align-items:center;
}
.modal-content{
background:white;
padding:25px;
width:90%;
max-width:500px;
border-radius:15px;
max-height:80vh;
overflow:auto;
}
#wishText{ white-space:pre-line; color:#333; }

/* LOCK GRID */
.photo-grid{
display:grid;
grid-template-columns:repeat(2,120px);
gap:15px;
}
.photo-box{
width:120px;
height:120px;
background:#ffb3c1;
display:flex;
justify-content:center;
align-items:center;
border-radius:15px;
font-size:40px;
}

/* GAME */
#gameArea{
position:relative;
width:100%;
height:60vh;
overflow:hidden;
}

.balloon{
position:absolute;
bottom:-60px;
font-size:35px;
cursor:pointer;
}

</style>
</head>
<body>

<!-- PAGE 1 -->
<div class="page active" id="page1">

<div class="left">
<h1>🎉 Happy Birthday My Love</h1>
<div class="subtitle">You are the most special person in my life 💕</div>
<button onclick="openModal()">Click for Surprise 💌</button>
</div>

<div class="right">
<img src="gf.jpg" class="circle-img">
<div class="float" style="top:10%;left:10%;">🎈</div>
<div class="float" style="top:20%;right:10%;">❤️</div>
</div>

</div>

<!-- MODAL -->
<div class="modal" id="modal">
<div class="modal-content">
<h3>To My Love ❤️</h3>
<div id="wishText"></div>
<br>
<button onclick="goPage2()">Next</button>
</div>
</div>

<!-- PAGE 2 -->
<div class="page" id="page2" style="flex-direction:column;">
<h2>DO YOU LOVE ME ❤️</h2>
<button onclick="goLove()">YES 💕</button>
<button id="noBtn" onmouseover="moveNo()">NO 😒</button>
</div>

<!-- PAGE 3 LOVE -->
<div class="page" id="pageLove" style="flex-direction:column;">
<h1 id="loveText" style="font-size:40px;"></h1>
<button onclick="switchPage('pageGift')">Next 💌</button>
</div>

<!-- PAGE 4 GIFT -->
<div class="page" id="pageGift" style="flex-direction:column;">
<h2>Select One 🎁</h2>
<button onclick="giftWarning()">Gift 🎁</button>
<button onclick="switchPage('pageMemory')">Memory 💖</button>
<p id="warning" style="color:red;"></p>
</div>

<!-- PAGE 5 MEMORY LOCK -->
<div class="page" id="pageMemory" style="flex-direction:column;">
<h2>Tap To Unlock 🔒</h2>
<div class="photo-grid">
<div class="photo-box" onclick="startGame()">🔒</div>
<div class="photo-box" onclick="startGame()">🔒</div>
<div class="photo-box" onclick="startGame()">🔒</div>
<div class="photo-box" onclick="startGame()">🔒</div>
</div>
</div>

<!-- PAGE 6 GAME -->
<div class="page" id="pageGame" style="flex-direction:column;">
<h2>Pop 5 Balloons 🎈</h2>
<div id="gameArea"></div>
<p id="score">0 / 5</p>
</div>

<!-- PAGE 7 CONGRATS -->
<div class="page" id="pageCongrats" style="flex-direction:column;">
<h1 style="color:gold;text-shadow:0 0 20px yellow;">CONGRATULATIONS ✨</h1>
<p>রুপা বউ তুমি পেরেছো 💖</p>
<button onclick="switchPage('pageGallery')">See Photos</button>
</div>

<!-- PAGE 8 GALLERY -->
<div class="page" id="pageGallery" style="flex-direction:column;">
<h2>Our Beautiful Memories ❤️</h2>

<img src="memory1.jpg" width="120">
<img src="memory2.jpg" width="120"><br>
<img src="memory3.jpg" width="120">
<img src="memory4.jpg" width="120">

<br>
<button onclick="showFinalGift()">Open Final Gift 🎁</button>
<img src="photo.jpg" id="finalPhoto" width="200" style="display:none;margin-top:15px;">
</div>

<script>

/* PAGE SWITCH */
function switchPage(id){
document.querySelectorAll(".page").forEach(p=>p.classList.remove("active"));
document.getElementById(id).classList.add("active");
}

/* WISH LETTER */
var text=`প্রিয় জান,  
  
শুভ জন্মদিন আমার ভালোবাসা। 🎂💖  
আজকের এই বিশেষ দিনে আমি শুধু একটা কথাই বলতে চাই — তুমি আমার জীবনের সবচেয়ে সুন্দর প্রাপ্তি। তিন বছরেরও বেশি সময় ধরে আমরা একসাথে আছি। এই সময়টায় রাগ ছিল, অভিমান ছিল, ভুল বোঝাবুঝি ছিল… কিন্তু সব কিছুর মাঝেও আমাদের ভালোবাসাটা কখনো কমে যায়নি। বরং আরও গভীর হয়েছে।  
  
আমি জানি, এতদিনে তোমাকে ঠিকভাবে বড় কোনো গিফট দিতে পারিনি। তোমার প্রাপ্যটা সবসময় দিতে পারিনি। কিন্তু বিশ্বাস করো, আমার মন থেকে তোমার জন্য ভালোবাসা আর সম্মান কখনো কম ছিল না। আমার সামর্থ্য যতটুকু, তার চেয়েও বেশি ভালোবাসা আমি তোমাকে দিতে চাই।  
  
আমাদের সম্পর্কটা শুধু আজকের না — এটা আমাদের ভবিষ্যতেরও। আমি চাই আমরা একসাথে পূর্ণতা পাই, একসাথে স্বপ্ন দেখি, একসাথে সব রাগ-অভিমান পেরিয়ে জীবনের প্রতিটা মুহূর্ত কাটাই।  
  
তুমি আমার শান্তি, তুমি আমার হাসি, তুমি আমার ভরসা। তোমার হাতটা যেন কোনোদিন না ছুটে যায়।  
  
আল্লাহর কাছে শুধু এই দোয়া করি — তোমার জীবন সুখে, স্বাস্থ্যে আর সফলতায় ভরে উঠুক। আর সেই সুখের প্রতিটা মুহূর্তে যেন আমি তোমার পাশে থাকতে পারি।  
  
শুভ জন্মদিন আমার জান।  
অনেক অনেক ভালোবাসা রইলো তোমার জন্য। ❤️  
  
তোমার জামাই 💕`;
var i=0;

function openModal(){
document.getElementById("modal").style.display="flex";
typeWriter();
}
function typeWriter(){
if(i<text.length){
document.getElementById("wishText").innerHTML+=text.charAt(i);
i++;
setTimeout(typeWriter,20);
}
}
function goPage2(){
document.getElementById("modal").style.display="none";
switchPage("page2");
}

/* NO BUTTON MOVE */
function moveNo(){
let btn=document.getElementById("noBtn");
btn.style.position="absolute";
btn.style.top=Math.random()*80+"%";
btn.style.left=Math.random()*80+"%";
}

/* LOVE TEXT */
function goLove(){
switchPage("pageLove");
let msg="I LOVE YOU ❤️";
let j=0;
let target=document.getElementById("loveText");
target.innerHTML="";
let inter=setInterval(()=>{
if(j<msg.length){
target.innerHTML+=msg[j];
j++;
}else clearInterval(inter);
},150);
}

/* GIFT WARNING */
function giftWarning(){
document.getElementById("warning").innerText="⚠ আগে Memory দেখো!";
}

/* GAME */
let score=0;
let interval;

function startGame(){
switchPage("pageGame");
score=0;
document.getElementById("score").innerText="0 / 5";
interval=setInterval(createBalloon,800);
}

function createBalloon(){
let b=document.createElement("div");
b.className="balloon";
b.innerHTML="🎈";
b.style.left=Math.random()*90+"%";

b.onclick=function(){
b.remove();
score++;
document.getElementById("score").innerText=score+" / 5";
if(score>=5){
clearInterval(interval);
switchPage("pageCongrats");
}
};

document.getElementById("gameArea").appendChild(b);

let move=setInterval(()=>{
b.style.bottom=parseInt(b.style.bottom||-60)+3+"px";
if(parseInt(b.style.bottom)>500){
b.remove();
clearInterval(move);
}
},20);
}

/* FINAL GIFT */
function showFinalGift(){
document.getElementById("finalPhoto").style.display="block";
}

</script>
</body>
</html>

# Emma.-
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Drakon System</title>

<style>

body{
margin:0;
background:#020202;
color:#00ffd5;
font-family:monospace;
display:flex;
justify-content:center;
align-items:center;
height:100vh;
text-align:center;
}

.panel{
width:90%;
max-width:650px;
padding:30px;
border:1px solid #00ffd5;
box-shadow:0 0 20px #00ffd5;
background:black;
border-radius:12px;
}

.hidden{display:none;}

button{
margin-top:20px;
padding:12px 22px;
background:#00ffd5;
border:none;
color:black;
font-weight:bold;
border-radius:6px;
}

input{
padding:12px;
width:80%;
text-align:center;
font-size:18px;
border-radius:6px;
border:none;
}

#message{
white-space:pre-line;
line-height:1.9;
}

.stat{
color:gold;
margin:10px;
font-size:18px;
}

</style>
</head>

<body>

<audio id="music" loop>
<source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8c8a73467.mp3">
</audio>

<!-- BOOT -->
<div id="boot" class="panel">
<h2 id="bootText"></h2>
</div>

<!-- LOGIN -->
<div id="login" class="panel hidden">
<h3 id="names"></h3>

<p>ENTER PASSWORD</p>
<input id="pass">
<br>
<button onclick="unlock()">UNLOCK</button>

<p id="error"></p>
</div>

<!-- GREETING -->
<div id="greet" class="panel hidden">
<p id="message"></p>
<button onclick="showReward()">ACCEPT REWARD</button>
</div>

<!-- REWARD -->
<div id="reward" class="panel hidden">
<h2>SYSTEM STATUS</h2>

<p>Name: Drakon</p>
<p>Race: Human</p>

<div id="stats"></div>

<p>System Blessing Installed ✔</p>

</div>

<script>

/* SAFE ELEMENT REFERENCES */
const bootDiv=document.getElementById("boot");
const loginDiv=document.getElementById("login");
const greetDiv=document.getElementById("greet");
const rewardDiv=document.getElementById("reward");

const bootText=document.getElementById("bootText");
const namesText=document.getElementById("names");
const message=document.getElementById("message");
const stats=document.getElementById("stats");

/* BOOT */
const bootMsg=
"SYSTEM INITIALIZING...\n"+
"CORE REBOOT...\n"+
"SEARCHING HOST...\n"+
"HOST FOUND.";

let i=0;

function boot(){
if(i<bootMsg.length){
bootText.innerHTML+=bootMsg.charAt(i);
i++;
setTimeout(boot,30);
}else{
setTimeout(()=>{
bootDiv.classList.add("hidden");
loginDiv.classList.remove("hidden");
showNames();
},1000);
}
}
boot();

/* NAMES */
const names="Emmanuel\nSunbola\nPraise";
let n=0;

function showNames(){
if(n<names.length){
namesText.innerHTML+=names.charAt(n);
n++;
setTimeout(showNames,60);
}
}

/* PASSWORD */
function unlock(){

let value=document
.getElementById("pass")
.value.trim().toLowerCase();

if(value==="drakon"){

/* START MUSIC */
let music=document.getElementById("music");
music.volume=0;
music.play();

let vol=0;
let fade=setInterval(()=>{
if(vol<1){
vol+=0.05;
music.volume=vol;
}else clearInterval(fade);
},200);

loginDiv.classList.add("hidden");
greetDiv.classList.remove("hidden");

typeMessage();

}else{
document.getElementById("error")
.innerText="ACCESS DENIED";
}
}

/* GREETING */
const greetMsg=`Today is more than a birthday.

Emmanuel.
Sunbola.
Praise.

May your life be filled with joy,
success,
and happiness.

May inspiration guide you.
May motivation strengthen you.

Soon,
you shall live the life you truly desire.

Happy Birthday, Drakon.`;

let g=0;

function typeMessage(){
if(g<greetMsg.length){
message.innerHTML+=greetMsg.charAt(g);
g++;
setTimeout(typeMessage,25);
}
}

/* REWARD */
function showReward(){

greetDiv.classList.add("hidden");
rewardDiv.classList.remove("hidden");

const perks=[
"Wealth +100",
"Health +100",
"Happiness +100"
];

let p=0;

function load(){
if(p<perks.length){
let div=document.createElement("div");
div.className="stat";
div.innerText=perks[p];
stats.appendChild(div);
p++;
setTimeout(load,600);
}
}
load();
}

</script>

</body>
</html>

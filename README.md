# Mnkhgrl
<!DOCTYPE html>
<html lang="mn">
<head>
<meta charset="UTF-8">
<title>For You</title>

<style>
body{
  margin:0;
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  background:radial-gradient(circle at top,#ff5f8a,#7a001f);
  overflow:hidden;
  font-family:-apple-system;
}

/* gift box */
#gift{
  width:160px;
  height:120px;
  background:#c8002d;
  position:relative;
  cursor:pointer;
  border-radius:10px;
  box-shadow:0 20px 40px rgba(0,0,0,.4);
  animation:float 2s infinite ease-in-out;
}

#gift:before{
  content:"";
  position:absolute;
  width:30px;
  height:120px;
  background:#ffccd5;
  left:65px;
}
#gift:after{
  content:"";
  position:absolute;
  width:160px;
  height:30px;
  background:#ffccd5;
  top:45px;
}

/* lid */
#lid{
  width:180px;
  height:40px;
  background:#ff0033;
  position:absolute;
  top:-40px;
  left:-10px;
  border-radius:8px;
  transition:1s;
}

/* message */
#msg{
  position:absolute;
  display:none;
  color:white;
  font-size:34px;
  font-weight:700;
  text-align:center;
  text-shadow:0 0 20px rgba(255,255,255,.8);
  animation:pop 1s ease forwards;
}

/* floating words */
.word{
  position:fixed;
  font-size:18px;
  color:white;
  animation:fly 3s ease forwards;
  pointer-events:none;
}

/* hearts */
.heart{
  position:fixed;
  font-size:20px;
  animation:burst 2.5s ease forwards;
  pointer-events:none;
}

@keyframes float{
  0%,100%{transform:translateY(0)}
  50%{transform:translateY(-10px)}
}
@keyframes pop{
  from{opacity:0;transform:scale(.5)}
  to{opacity:1;transform:scale(1)}
}
@keyframes fly{
  to{transform:translateY(-120px);opacity:0}
}
@keyframes burst{
  to{
    transform:translate(
      calc(-100px + 200px * var(--x)),
      calc(-100px + 200px * var(--y))
    );
    opacity:0;
  }
}
</style>
</head>

<body>

<div id="gift">
  <div id="lid"></div>
</div>

<div id="msg">
  Suwdaa<br>би чамд хайртай ❤️
</div>

<script>
const words=[
  "Хайр","Чи минийх","Үүрд","Сэтгэл","Аз жаргал",
  "Only you","Love","Forever","❤️"
];

gift.onclick=()=>{
  lid.style.transform="rotateX(140deg) translateY(-60px)";
  gift.style.animation="none";
  gift.style.display="none";
  msg.style.display="block";

  for(let i=0;i<25;i++){
    setTimeout(makeHeart,i*40);
    setTimeout(makeWord,i*80);
  }
}

function makeHeart(){
  const h=document.createElement("div");
  h.className="heart";
  h.innerHTML="❤️";
  h.style.left=window.innerWidth/2+"px";
  h.style.top=window.innerHeight/2+"px";
  h.style.setProperty("--x",Math.random());
  h.style.setProperty("--y",Math.random());
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),3000);
}

function makeWord(){
  const w=document.createElement("div");
  w.className="word";
  w.innerHTML=words[Math.floor(Math.random()*words.length)];
  w.style.left=50+Math.random()*100+"px";
  w.style.bottom="120px";
  document.body.appendChild(w);
  setTimeout(()=>w.remove(),3000);
}
</script>

</body>
</html>

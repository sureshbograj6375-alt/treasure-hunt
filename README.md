function draw(){

background();
drawObjects();
drawPlayer();

document.getElementById("score").textContent=score;
document.getElementById("life").textContent=life;
document.getElementById("level").textContent=level;

if(gameOver||win){

ctx.fillStyle="black";
ctx.font="40px Arial";
ctx.textAlign="center";

ctx.fillText(
gameOver?"GAME OVER":"LEVEL COMPLETE!",
400,200
);

}
}

function loop(){
update();
draw();
requestAnimationFrame(loop);
}

function control(id,key){
let b=document.getElementById(id);

b.addEventListener("pointerdown",e=>{
e.preventDefault();
keys[key]=true;
});

["pointerup","pointercancel","pointerleave"]
.forEach(event=>{
b.addEventListener(event,()=>{
keys[key]=false;
});
});
}

control("left","left");
control("right","right");

document.getElementById("jump").onclick=()=>{
if(player.ground&&!gameOver&&!win){
player.vy=-12;
player.ground=false;
}
};

document.getElementById("restart").onclick=()=>{
location.reload();
};

loop();
</script>
</body>
</html># treasure-hunt
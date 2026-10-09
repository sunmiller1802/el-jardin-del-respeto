<!DOCTYPE html>
<html lang="es"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>El Jardín del Respeto</title>
<style>
:root{--bg:#f8ece9;--card:#fff;--ink:#4a2f33;--ac:#b76e79;--ac2:#f1d3d3;--ok:#4f9a70;--y:#ffe7a8;--b:#cfe8f5;--g:#d6efd8;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#2b1d20;--card:#3a272b;--ink:#f6e6e4;--ac:#d99aa3;--ac2:#5a3b40;--y:#6b5a2e;--b:#2f4656;--g:#2f4d36}}
body{margin:0;font-family:"Trebuchet MS",Verdana,sans-serif;background:var(--bg);color:var(--ink);font-size:20px}
body.big{font-size:26px}
body.hc{--bg:#000;--card:#000;--ink:#fff;--ac:#ffd400;--ac2:#222;--y:#222;--b:#222;--g:#222}
body.hc .opt,body.hc #g{border:3px solid #fff}
body.calm{--bg:#eef3f1;--card:#fafcfb;--ac:#7d9a94;--ac2:#d4e2de;--y:#e6eee9;--b:#e3ecef;--g:#e0ece4;--ink:#2f3d3a}
main{max-width:780px;margin:0 auto;padding:10px}
h1{font-size:1.3em;text-align:center;margin:4px 0}
#g{background:var(--card);border-radius:28px;padding:14px;text-align:center;box-shadow:0 3px 12px #0002}
#g.fl{animation:flash .7s}
.row{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin:8px 0}
.chip{font:inherit;font-size:.8em;border:2px solid var(--ac);background:var(--card);color:var(--ink);border-radius:999px;padding:6px 14px;cursor:pointer;min-height:44px}
.chip.on,.chip[aria-pressed=true]{background:var(--ac);color:#fff}
body.hc .chip.on,body.hc .chip[aria-pressed=true]{color:#000}
.tiles,.row2{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:12px;margin:12px 0}
.opt{font:inherit;font-weight:bold;color:var(--ink);border:3px solid transparent;border-radius:26px;padding:12px;background:var(--ac2);cursor:pointer;min-height:120px;transition:transform .15s}
.opt:nth-child(4n+1){background:var(--y)}.opt:nth-child(4n+2){background:var(--b)}.opt:nth-child(4n+3){background:var(--g)}
.opt .e{display:block;font-size:3.6em;line-height:1.1}
.opt:disabled{opacity:.45}.opt[hidden]{display:none}
.opt.ok{background:var(--ok);color:#fff;opacity:1}
.opt.main{background:var(--ac);color:#fff;width:100%}
body.hc .opt.main{color:#000}
.opt.sc{outline:8px solid var(--ac);transform:scale(1.05)}
.opt:active{transform:scale(.96)}
.mas{display:flex;align-items:center;gap:10px;text-align:left}
.bear{font-size:3.4em;display:inline-block}
.bear.ok{animation:jump .6s 3}.bear.no{animation:shake .5s}
.bub{background:var(--ac2);border-radius:18px;padding:8px 12px;font-weight:bold;flex:1}
.gd{font-size:1.1em;letter-spacing:2px;margin:6px 0;word-break:break-all}
.ban{display:flex;justify-content:space-between;align-items:center;gap:8px}
.big1{font-size:7em;line-height:1.1;animation:bob 2s ease-in-out infinite}
.cap{font-weight:bold;font-size:1.05em;margin:4px 0}
.msg{min-height:1.6em;font-weight:bold}
.cf{position:fixed;top:-40px;font-size:1.7em;pointer-events:none;animation:fall 2.2s linear forwards;z-index:9}
@keyframes fall{to{transform:translateY(110vh) rotate(360deg)}}
@keyframes jump{50%{transform:translateY(-20px) scale(1.2)}}
@keyframes shake{25%{transform:rotate(-12deg)}75%{transform:rotate(12deg)}}
@keyframes bob{50%{transform:translateY(-8px) scale(1.05)}}
@keyframes flash{30%{box-shadow:0 0 0 14px var(--ok)}}
@media (prefers-reduced-motion:reduce){.bear,.cf,.big1,#g{animation:none!important}}
</style></head><body>
<main><h1>🌷 El Jardín del Respeto</h1>
<div class="row" id="bar" role="group" aria-label="Ayudas"></div>
<div id="g" role="main" aria-live="polite"></div></main>
<script>
const $=i=>document.getElementById(i);
const AV=["🦊","🐸","🐼","🐰","🐯","🦁"],NM=["zorro","rana","panda","conejo","tigre","león"],FL=["🌸","🌼","🌷","🌻","🌺"];
const MW=[["🙏","Por favor"],["💐","Gracias"],["🙇","Perdón"],["🚪","Permiso"]];
const TY=[["vis","👁️","Visual"],["aud","👂","Auditiva"],["mot","🦽","Motriz"],["cog","🧠","Intelectual"],["tea","🧩","Autismo"],["otra","✨","Otra"]];
const CH=[["speak","🔊","Voz"],["mute","🔇","Sin sonidos de premio"],["big","🔠","Letra grande"],["hc","🌗","Contraste"],["scan","⏯","Barrido (un solo botón)"],["calm","🌿","Calma"],["listen","🎤","Responder hablando (micrófono)"]];
const G=[
{k:"yn",ic:"💗",n:"¿Es respeto?",it:[["🤝","Compartir los juguetes",1],["👊","Pegar a un amigo",0],["👂","Escuchar al amigo",1],["😝","Burlarse de otro",0],["🎈","Invitar a todos a jugar",1]]},
{k:"mw",ic:"✨",n:"Palabras mágicas",it:[["🧸","Quieres el juguete de tu amigo",0],["🎁","Te regalaron un dulce",1],["🦶","Pisaste a tu amigo sin querer",2],["🚶","Quieres pasar entre dos amigos",3]]},
{k:"opt",ic:"🆘",n:"Ayuda al amigo",it:[["😢","Tu amigo llora. ¿Qué haces?",[["🤗","Abrazo",1],["🙈","No miro",0],["😝","Me burlo",0]]],["🤕","Tu amigo se cayó. ¿Qué haces?",[["🙋","¿Estás bien?",1],["🏃","Me voy",0],["😂","Me río",0]]],["🧍","Un niño está solo. ¿Qué haces?",[["🎈","Lo invito",1],["🙅","Lo ignoro",0],["🚫","Le digo no",0]]],["🚪","Un amigo no puede abrir la puerta. ¿Qué haces?",[["🙋","¿Te ayudo?",1],["😝","Me burlo",0],["🚶","Paso de largo",0]]]]},
{k:"do",ic:"💃",n:"Baile del respeto",it:[["👋","¡Saluda a un amigo con la mano, o como tú puedas!"],["🤗","¡Manda un abrazo grande a tus amigos!"],["👏","¡Aplaude bajito, o mueve tus manos!"],["🤫","¡Silencio! Todos escuchamos"],["💐","¡Dile gracias a quien está a tu lado!"],["💃","¡Bailen juntos, cada quien a su manera!"]]},
{k:"opt",ic:"🎭",n:"Caritas",it:[["😢","Tu amigo está así. ¿Cómo se siente?",[["😢","Triste",1],["😄","Feliz",0],["😠","Enojado",0]]],["😠","Tu amigo está así. ¿Cómo se siente?",[["😠","Enojado",1],["😴","Con sueño",0],["😄","Feliz",0]]],["😨","Tu amigo está así. ¿Cómo se siente?",[["😨","Con miedo",1],["😄","Feliz",0],["😋","Con hambre",0]]],["🥳","Tu amigo está así. ¿Cómo se siente?",[["🥳","Feliz",1],["😢","Triste",0],["😠","Enojado",0]]]]},
{k:"fish",ic:"🎣",n:"Pesca corazones",it:[["🎣","¡Pesca lo que sí es respeto! Toca todos los corazones buenos.",[["🤝","Compartir",1],["👊","Pegar",0],["👂","Escuchar",1],["😝","Burlarse",0],["🙏","Por favor",1],["🙅","Excluir",0]]],["🎣","¡Pesca las palabras amables!",[["💐","Gracias",1],["😡","Gritar",0],["🙇","Perdón",1],["🙄","Ignorar",0],["🚪","Permiso",1],["😠","Insultar",0]]],["🎣","¡Pesca las buenas acciones con los amigos!",[["🎈","Invitar",1],["🏃","Empujar",0],["⏳","Esperar turno",1],["😠","Quitar juguete",0],["🧸","Compartir",1],["🙈","Ignorar",0]]]]},
{k:"opt",ic:"🙋",n:"¿Puedo?",it:[["🤗","Quieres abrazar a un amigo. ¿Qué haces?",[["🙋","Pregunto: ¿puedo?",1],["🏃","Lo abrazo corriendo",0],["😶","Lo agarro",0]]],["🙅","Tu amigo dice: no quiero abrazos. ¿Qué haces?",[["👍","Respeto su no",1],["🤗","Lo abrazo igual",0],["😡","Me enojo",0]]],["🧸","Ese juguete es de otro niño. ¿Qué haces?",[["🙋","Pido permiso",1],["✋","Lo agarro",0],["🏃","Me lo llevo",0]]],["🛑","Un amigo dice: alto, no me gusta. ¿Qué haces?",[["🛑","Paro enseguida",1],["😂","Sigo jugando",0],["😝","Me burlo",0]]]]},
{k:"do",ic:"🔄",n:"Ronda de amigos",it:[["🔄","¡Hagan una ronda: tómense de las manos o hagan un círculo, como puedan!"],["🗣️","¡Cada uno diga el nombre de un amigo!"],["😊","¡Sonríe al amigo que está a tu lado!"],["⏳","¡Esperen su turno en una fila!"],["🧸","¡Compartan un juguete con un amigo!"]]}
];
const TOT=G.reduce((a,g)=>a+g.it.length,0);
const S={o:{speak:1},n:3,yes:null,ty:{},gi:0,r:0,done:[],g:0,t:0,tm:null,sp:"",cur:null};
function say(t,add,cb){if(!S.o.speak||!window.speechSynthesis){if(cb)cb();return}if(!add)speechSynthesis.cancel();const id=S.sid=(S.sid||0)+1;const u=new SpeechSynthesisUtterance(t);u.lang="es-CO";u.rate=.85;u.pitch=1.2;
 if(cb){let d=0;const go=()=>{if(!d&&id==S.sid){d=1;cb()}};u.onend=go;setTimeout(go,1500+t.length*85)}speechSynthesis.speak(u)}
function beep(f,d){if(S.o.mute)return;setTimeout(()=>{try{const a=new(window.AudioContext||window.webkitAudioContext)(),o=a.createOscillator(),g=a.createGain();o.frequency.value=f;g.gain.value=.06;o.connect(g);g.connect(a.destination);o.start();o.stop(a.currentTime+.14)}catch(e){}},d||0)}
function conf(){if(S.o.calm)return;for(let i=0;i<22;i++){const x=document.createElement("span");x.className="cf";x.textContent=FL[i%5];x.style.left=Math.random()*100+"vw";x.style.animationDelay=Math.random()*.6+"s";document.body.appendChild(x);setTimeout(()=>x.remove(),2600)}}
function apply(){["big","hc","calm"].forEach(k=>document.body.classList.toggle(k,!!S.o[k]));if(!S.o.scan)stopScan();if(!S.o.listen)stopListen();if(!S.o.speak&&window.speechSynthesis)speechSynthesis.cancel()}
function bar(){const b=$("bar");b.innerHTML="";CH.forEach(([k,e,l])=>{const c=document.createElement("button");c.className="chip";c.textContent=e;c.title=l;c.setAttribute("aria-label",l);c.setAttribute("aria-pressed",!!S.o[k]);c.onclick=()=>{S.o[k]=!S.o[k];apply();bar();if((k=="scan"||k=="listen")&&S.cur)S.cur()};b.appendChild(c)})}
function gd(){let s=Array.from({length:TOT},(_,i)=>i<S.g?FL[i%5]:"🌱").join("");return s+(S.g>=TOT?"🦋🦋🦋":"")}
function hdr(m){return `<div class="mas"><span class="bear" id="bear">🐻</span><div class="bub" id="bub">${m}</div></div><div class="gd" id="gd">${gd()}</div>`}
function mas(c,t){const b=$("bear");if(!b)return;b.className="bear "+c;$("bub").textContent=t}
function sb(){return (S.o.scan?'<button class="opt main" id="el"><span class="e">✅</span>ELEGIR</button>':"")+(S.o.listen?'<button class="opt main" id="mic" style="min-height:80px"><span class="e">🎤</span>Hablar</button>':"")}
function stopScan(){stopListen();clearInterval(S.tm);S.tm=null;document.querySelectorAll(".sc").forEach(z=>z.classList.remove("sc"))}
function sels(){return [...document.querySelectorAll("#o .opt:not(:disabled):not([hidden])")]}
function startScan(){stopScan();if($("mic"))$("mic").onclick=()=>listenNow();if(!S.o.scan)return;let k=-1;const f=()=>{const bs=sels();if(!bs.length)return;bs.forEach(z=>z.classList.remove("sc"));k=(k+1)%bs.length;bs[k].classList.add("sc");if(S.o.speak)say(bs[k].textContent.trim())};f();S.tm=setInterval(f,3200);if($("el"))$("el").onclick=scanPick}
function scanPick(){const b=document.querySelector("#o .opt.sc");if(b)b.click()}
const SR=window.SpeechRecognition||window.webkitSpeechRecognition;
const norm=t=>t.toLowerCase().normalize("NFD").replace(/[\u0300-\u036f]/g,"").replace(/[^a-z0-9ñ ]/g," ").replace(/\s+/g," ").trim();
const NUM={uno:1,"1":1,primero:1,primera:1,dos:2,"2":2,segundo:2,segunda:2,tres:3,"3":3,tercero:3,cuatro:4,"4":4,cinco:5,"5":5,seis:6,"6":6,siete:7,"7":7,ocho:8,"8":8};
function match(a,labels){let best=-1,bs=0;const hs=a.map(norm);labels.forEach((lab,i)=>{const l=norm(lab);if(!l)return;let sc=0;for(const h of hs){const w=h.split(" ");let x=0;if(l.length<=3){if(w.includes(l))x=50}else if(h.includes(l))x=100;else{for(const t of l.split(" "))if(t.length>=4&&w.includes(t))x+=t.length}if(x>sc)sc=x}if(sc>bs){bs=sc;best=i}});
 if(best>=0)return best;for(const h of hs)for(const x of h.split(" "))if(NUM[x]&&NUM[x]<=labels.length)return NUM[x]-1;return -1}
function stopListen(){S.lid=(S.lid||0)+1;try{S.rec&&S.rec.abort()}catch(e){}S.rec=null}
function listenNow(r){if(!S.o.listen)return;r=r||0;if(!SR){if(!S.nsr){S.nsr=1;say("Este navegador no entiende la voz. Toca las opciones.")}return}
 stopListen();const id=S.lid,rec=new SR();S.rec=rec;rec.lang="es-CO";rec.maxAlternatives=3;let got=0;
 rec.onresult=e=>{got=1;hear([...e.results[0]].map(x=>x.transcript))};
 rec.onerror=e=>{if(e.error=="not-allowed"||e.error=="service-not-allowed"){got=1;say("Necesito permiso para el micrófono. Puedes tocar las opciones.")}};
 rec.onend=()=>{if(id!=S.lid||got)return;if(r<2)say("No te escuché. Dime tu respuesta, o di repetir.",0,()=>listenNow(r+1))};
 try{rec.start();if($("bub"))$("bub").textContent="🎤 Te escucho…"}catch(e){}}
function hear(a){
 if(S.cur==fin&&a.some(t=>/\b(otra|jugar|repetir|si|vamos)\b/.test(norm(t)))&&$("a")){$("a").click();return}
 for(const t of a){const h=norm(t);
  if(/\b(repetir|repite|repitelo)\b/.test(h)){say(S.sp,0,()=>listenNow());return}
  if(/\b(sortear|sorteo|ruleta|cambiar turno)\b/.test(h)&&$("tb")){spin();return}
  const nx=$("nx");if(nx&&!nx.hidden&&/\b(siguiente|continuar|sigue|seguir|listo|vamos)\b/.test(h)){nx.click();return}
  if(/\b(terminar|finalizar)\b/.test(h)&&$("fn")){fin();return}}
 const bs=[...document.querySelectorAll("[data-j],[data-i]")].filter(b=>!b.disabled);
 const j=match(a,bs.map(b=>b.textContent));
 if(j>=0){bs[j].click();return}
 S.miss=(S.miss||0)+1;if(S.miss<=3)say("No entendí. Prueba otra vez, o di repetir.",0,()=>listenNow())}
function setup(){stopScan();S.cur=null;S.done=[];S.g=0;S.t=0;
 $("g").innerHTML=`<div class="mas"><span class="bear">🐻</span><div class="bub">¡Hola! Soy Respi. ¡Vamos a jugar con el respeto!</div></div>
 <h2>👩‍🏫 Para el adulto</h2><p>¿Cuántos niños juegan?</p><div class="row">${[2,3,4,5,6].map(k=>`<button class="chip ${S.n==k?"on":""}" data-n="${k}">${k}</button>`).join("")}</div>
 <p>¿Hay niños con alguna discapacidad?</p><div class="row"><button class="chip ${S.yes===1?"on":""}" data-y="1">Sí</button><button class="chip ${S.yes===0?"on":""}" data-y="0">No</button></div>
 ${S.yes?`<p>¿Cuál? (puede marcar varias)</p><div class="row">${TY.map(([k,e,l])=>`<button class="chip ${S.ty[k]?"on":""}" data-t="${k}">${e} ${l}</button>`).join("")}</div>`:""}
 ${S.yes&&S.ty.vis?'<p><small>🎤 Visual: el juego hablará y escuchará las respuestas por el micrófono. Permita el micrófono cuando el navegador lo pida.</small></p>':""}<div id="o"><button class="opt main" id="go"><span class="e">▶️</span>¡A jugar!</button></div>`;
 document.querySelectorAll("[data-n]").forEach(b=>b.onclick=()=>{S.n=+b.dataset.n;setup()});
 document.querySelectorAll("[data-y]").forEach(b=>b.onclick=()=>{S.yes=+b.dataset.y;setup()});
 document.querySelectorAll("[data-t]").forEach(b=>b.onclick=()=>{S.ty[b.dataset.t]=!S.ty[b.dataset.t];setup()});
 $("go").onclick=()=>{const t=S.ty,o={speak:1};if(S.yes){if(t.vis){o.big=1;o.hc=1;o.listen=1}if(t.mot){o.big=1;o.scan=1}if(t.cog){o.simple=1;o.big=1}if(t.tea){o.mute=1;o.calm=1}if(t.aud)o.aud=1}S.o=o;apply();bar();menu()}}
function menu(){stopScan();S.cur=menu;if(S.done.length==G.length)return fin();
 $("g").innerHTML=`${hdr("¡Elijan un juego!")}<div id="o" class="tiles">${G.map((g,i)=>`<button class="opt" data-i="${i}" ${S.done.includes(i)?"disabled":""}><span class="e">${g.ic}</span>${g.n}${S.done.includes(i)?" ✅":""}</button>`).join("")}</div>${S.done.length>=3?'<button class="chip" id="fn">🏁 Terminar y ver el jardín</button>':""}${sb()}`;
 if($("fn"))$("fn").onclick=fin;
 document.querySelectorAll("[data-i]").forEach(b=>b.onclick=()=>{S.gi=+b.dataset.i;S.r=0;play()});
 const en=G.filter((g,i)=>!S.done.includes(i));S.miss=0;S.sp=S.o.listen?"¡Elijan un juego! Digan el nombre. "+en.map(g=>g.n).join(". "):"¡Elijan un juego!";say(S.sp,0,()=>listenNow());startScan()}
function play(){stopScan();S.cur=play;const g=G[S.gi],k=g.k,it=g.it[S.r],sim=S.o.simple;let sp,ops=[];S.found=0;
 if(k=="yn"){sp="¿Esto es respeto? "+it[1]+". ¿Sí o no?";ops=[["💗","Sí",it[2]==1],["💔","No",it[2]==0]]}
 else if(k=="mw"){sp="¿Qué palabra mágica usas? "+it[1];ops=MW.map((m,j)=>[m[0],m[1],j==it[2]]);if(sim){const w=ops.filter(x=>!x[2]);ops=[ops.find(x=>x[2]),w[S.r%w.length]]}}
 else if(k=="opt"){sp=it[1];ops=it[2].map(x=>[x[0],x[1],x[2]==1]);if(sim)ops=[ops.find(x=>x[2]),ops.find(x=>!x[2])]}
 else if(k=="fish"){sp=it[1];ops=it[2].map(x=>[x[0],x[1],x[2]==1]);if(sim)ops=ops.filter(x=>x[2]).slice(0,2).concat(ops.filter(x=>!x[2]).slice(0,2));S.need=ops.filter(x=>x[2]).length}
 else{sp=it[1];ops=[["✅","¡Hecho!",true]]}
 if(k=="mw"||k=="opt")ops=ops.map((_,j)=>ops[(j+S.r)%ops.length]);
 const L=S.o.listen;let full=k=="mw"||k=="opt"||(k=="fish"&&L)?sp+" "+ops.map(o=>o[1]).join(", o ")+".":sp;if(L&&k=="do")full+=" Di hecho cuando terminen.";if(L&&S.n>1)full="Le toca al "+NM[S.t]+". "+full;S.sp=full;S.miss=0;
 $("g").innerHTML=`${hdr(g.n)}<div class="ban"><button class="chip" id="tb" title="Sortear turno">🎡 Le toca a <b id="av">${AV[S.t]}</b></button><button class="chip" id="rp" aria-label="Repetir">🔊 Repetir</button><b>${S.r+1}/${g.it.length}</b></div>
 <div class="big1">${it[0]}</div><p class="cap">${k=="yn"||k=="mw"?it[1]:sp}</p>
 <div id="o" class="row2">${ops.map((o,j)=>`<button class="opt ${k=="do"?"main":""}" data-j="${j}"><span class="e">${o[0]}</span>${o[1]}</button>`).join("")}<button class="opt main" id="nx" hidden><span class="e">➡️</span></button></div><div class="msg" id="m"></div>${sb()}`;
 document.querySelectorAll("[data-j]").forEach(b=>b.onclick=()=>pick(b,ops[+b.dataset.j][2],g));
 $("tb").onclick=spin;$("rp").onclick=()=>say(S.sp);
 say(full,0,()=>listenNow());startScan()}
function spin(){let k=0;const tm=setInterval(()=>{S.t=Math.floor(Math.random()*S.n);$("av").textContent=AV[S.t];beep(400+k*25);if(++k>16){clearInterval(tm);say("¡Le toca al "+NM[S.t]+"!",0,()=>listenNow())}},90)}
function pick(b,ok,g){if(b.disabled)return;
 if(ok&&g.k=="fish"){S.found++;if(S.found<S.need){b.disabled=true;b.classList.add("ok");beep(659);mas("ok","¡Sigue buscando! "+S.found+"/"+S.need);say("¡Bien! Busca más.",0,()=>listenNow());startScan();return}}
 if(ok){const e=$("g");e.classList.add("fl");setTimeout(()=>e.classList.remove("fl"),800);[523,659,784].forEach((f,i)=>beep(f,i*130));
  document.querySelectorAll("#o .opt[data-j]").forEach(z=>z.disabled=true);b.classList.add("ok");S.g++;$("gd").textContent=gd();
  mas("ok","¡Muy bien! 🎉");say((S.n>1?"¡Muy bien, "+NM[S.t]+"!":"¡Muy bien!")+(S.g>=TOT?" ¡El jardín floreció!":"")+(S.o.listen?" Di siguiente para continuar.":""),0,()=>listenNow());conf();
  const n=$("nx");n.hidden=false;n.onclick=()=>{S.r++;S.t=(S.t+1)%S.n;if(S.r>=g.it.length){S.done.push(S.gi);menu()}else play()};startScan()}
 else{beep(300);b.disabled=true;mas("no","¡Casi! Prueba otra vez 💪");say("¡Casi! Prueba otra vez.",0,()=>listenNow())}}
function fin(){stopScan();S.cur=fin;
 $("g").innerHTML=`<div class="bear ok" style="font-size:6em">🐻</div><h2>¡Lo logramos juntos! 🎉</h2><div class="gd">${gd()}</div><div style="font-size:3em">${AV.slice(0,S.n).join(" ")}</div><p><b>Un abrazo grande para todos 🤗</b></p><div id="o"><button class="opt main" id="a"><span class="e">🔁</span>Jugar otra vez</button></div>${sb()}`;
 $("a").onclick=()=>{S.done=[];S.g=0;menu()};conf();[523,659,784,1047].forEach((f,i)=>beep(f,i*150));
 S.sp="¡Lo logramos juntos! Somos amigos que se respetan. Un abrazo grande para todos."+(S.o.listen?" Di otra vez para jugar de nuevo.":"");say(S.sp,0,()=>listenNow());startScan()}
document.addEventListener("keydown",e=>{
 if(e.key=="r"||e.key=="R")say(S.sp);
 else if(S.o.scan&&(e.key==" "||e.key=="Enter")&&$("el")){e.preventDefault();scanPick()}});
bar();setup();
</script></body></html>

---
layout: post
published: true
title: Wenn die Schweiz 10'000 Einwohner hätte
date: 2026-10-11 12:00:00 +0200
description: "Wie viele Menschen würden in einem Jahr polizeilich beschuldigt, und aus welchen Bevölkerungsgruppen kämen sie? Die Kriminalstatistik 2025 im Kleinen."
---

Wie viele Menschen würden in einem Jahr wegen Gewalt, eines Sexualdelikts oder Diebstahls polizeilich beschuldigt? Und aus welchen Bevölkerungsgruppen kämen sie?

Kriminalstatistiken sprechen in grossen Zahlen: 92'147 Personen hat die Polizei 2025 wegen einer Straftat nach dem Strafgesetzbuch registriert.[^1] Solche Zahlen sind schwer greifbar, und in der Debatte über Herkunft und Kriminalität werden sie oft als Anteile genannt, ohne dass klar wird, wie gross die Gruppen überhaupt sind.

Deshalb verkleinern wir die Schweiz hier auf 10'000 Einwohnerinnen und Einwohner. Jede Figur steht für rund 913 reale Menschen. Die Zusammensetzung nach Staatsangehörigkeit, Aufenthaltsstatus, Geschlecht und Alter entspricht der tatsächlichen Wohnbevölkerung Ende 2025.[^2]

<div class="k10">
<style>
.k10{--k-top:57px;--k-ink:#000;--k-muted:#555;--k-line:#000;--k-gewalt:#E5383B;--k-sexual:#B832C9;--k-vermoegen:#F09A00;margin:32px 0}
.k10 *,.k10 *::before,.k10 *::after{box-sizing:border-box}
.k10 .k-scrolly{position:relative;max-width:640px;margin:0 auto}
.k10 .k-sticky{position:sticky;top:var(--k-top);z-index:2;background:#fff;margin:0 -16px;padding:8px 16px 10px}
.k10 .k-stage{width:100%;max-width:min(100%,52vh);margin:0 auto}
.k10 .k-labels{position:relative;height:36px;margin-bottom:6px}
.k10 .k-lab{position:absolute;bottom:0;font-size:10px;line-height:1.25;color:var(--k-muted);white-space:nowrap;transform:translateX(-50%);text-align:center}
.k10 .k-lab b{display:block;color:var(--k-ink);font-weight:700;font-size:11px;text-transform:uppercase;letter-spacing:.02em}
.k10 .k-lab .k-hit{font-weight:700;color:var(--k-ink)}
.k10 .k-tick{position:absolute;bottom:-6px;width:1px;height:6px;background:var(--k-line)}
.k10 .k-box{position:relative;width:100%;aspect-ratio:1/1}
.k10 canvas{display:block;width:100%;height:100%}
.k10 #k-cv{cursor:crosshair}
.k10 .k-asylnote{text-align:right;font-size:12px;color:var(--k-muted);margin-top:4px;min-height:18px}
.k10 .k-asylnote b{color:var(--k-ink)}
.k10 .k-lens{position:absolute;width:150px!important;height:150px!important;border-radius:50%;border:1px solid #000;background:#fff;pointer-events:none;opacity:0;transition:opacity .12s}
.k10 .k-tip{position:absolute;pointer-events:none;background:#000;color:#fff;font-size:12px;line-height:1.4;padding:4px 6px;white-space:nowrap;opacity:0;transition:opacity .12s;transform:translate(-50%,-120%)}
.k10 .k-steps{position:relative;z-index:1;padding-top:4px}
.k10 .k-step{display:block;margin-bottom:16px}
.k10 .k-step:last-child{margin-bottom:0}
.k10 .k-step .k-card{filter:blur(2.5px);opacity:.5;transition:filter .4s,opacity .4s}
.k10 .k-step.active .k-card{filter:none;opacity:1}
@media (prefers-reduced-motion: reduce){.k10 .k-step .k-card{transition:none}}
.k10 .k-card{background:#fff;outline:1px solid #000;padding:16px;font-size:15px}
.k10 .k-card h3{margin:0 0 10px}
.k10 .k-card p{margin:0 0 .7em}
.k10 .k-card p:last-child{margin-bottom:0}
.k10 .k-card .k-note{font-size:13px;color:var(--k-muted)}
.k10 ~ table{border-collapse:collapse;width:100%;font-variant-numeric:tabular-nums;font-size:14px;margin:8px 0 16px}
.k10 ~ table th,.k10 ~ table td{padding:6px;border-bottom:1px solid #000}
.k10 ~ table th{text-transform:uppercase;font-size:12px}
@media (max-width:480px){.k10 ~ table{display:block;overflow-x:auto;font-size:12px}.k10 ~ table th,.k10 ~ table td{padding:5px 3px}.k10 ~ table th{font-size:10px}}
.k10 .k-big{font-weight:800;font-size:40px;line-height:1;letter-spacing:-.02em;display:block;margin:2px 0 8px}
</style>
<div class="k-scrolly" aria-label="Scroll-Grafik">
<div class="k-sticky">
<div class="k-stage">
<div class="k-labels" id="k-labels"></div>
<div class="k-box" id="k-box">
<canvas id="k-cv" role="img" aria-label="100 mal 100 Figuren, nach Gruppe, Geschlecht und Alter"></canvas>
<canvas class="k-lens" id="k-lens" width="300" height="300" aria-hidden="true"></canvas>
<div class="k-tip" id="k-tip"></div>
</div>
<div class="k-asylnote" id="k-asylnote"></div>
</div>
</div>
<div class="k-steps" id="k-steps"></div>
</div>
{% raw %}
<script>
(()=>{
const M={"cells":[{"g":"CH","s":"M","b":"0-9","n":351,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"CH","s":"M","b":"10-17","n":309,"gewalt":1,"sexual":1,"vermoegen":2},{"g":"CH","s":"M","b":"18-34","n":683,"gewalt":2,"sexual":1,"vermoegen":5},{"g":"CH","s":"M","b":"35-64","n":1394,"gewalt":4,"sexual":1,"vermoegen":5},{"g":"CH","s":"M","b":"65+","n":782,"gewalt":1,"sexual":0,"vermoegen":1},{"g":"CH","s":"W","b":"0-9","n":333,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"CH","s":"W","b":"10-17","n":292,"gewalt":0,"sexual":0,"vermoegen":1},{"g":"CH","s":"W","b":"18-34","n":668,"gewalt":1,"sexual":0,"vermoegen":1},{"g":"CH","s":"W","b":"35-64","n":1452,"gewalt":2,"sexual":0,"vermoegen":2},{"g":"CH","s":"W","b":"65+","n":967,"gewalt":0,"sexual":0,"vermoegen":1},{"g":"AUSL","s":"M","b":"0-9","n":132,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"AUSL","s":"M","b":"10-17","n":101,"gewalt":1,"sexual":0,"vermoegen":1},{"g":"AUSL","s":"M","b":"18-34","n":340,"gewalt":2,"sexual":1,"vermoegen":4},{"g":"AUSL","s":"M","b":"35-64","n":692,"gewalt":4,"sexual":1,"vermoegen":5},{"g":"AUSL","s":"M","b":"65+","n":116,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"AUSL","s":"W","b":"0-9","n":126,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"AUSL","s":"W","b":"10-17","n":95,"gewalt":0,"sexual":0,"vermoegen":1},{"g":"AUSL","s":"W","b":"18-34","n":303,"gewalt":1,"sexual":0,"vermoegen":1},{"g":"AUSL","s":"W","b":"35-64","n":610,"gewalt":1,"sexual":0,"vermoegen":2},{"g":"AUSL","s":"W","b":"65+","n":109,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"ASYL","s":"M","b":"0-9","n":9,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"ASYL","s":"M","b":"10-17","n":13,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"ASYL","s":"M","b":"18-34","n":31,"gewalt":1,"sexual":0,"vermoegen":2},{"g":"ASYL","s":"M","b":"35-64","n":19,"gewalt":0,"sexual":0,"vermoegen":1},{"g":"ASYL","s":"M","b":"65+","n":3,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"ASYL","s":"W","b":"0-9","n":8,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"ASYL","s":"W","b":"10-17","n":9,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"ASYL","s":"W","b":"18-34","n":17,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"ASYL","s":"W","b":"35-64","n":29,"gewalt":0,"sexual":0,"vermoegen":0},{"g":"ASYL","s":"W","b":"65+","n":7,"gewalt":0,"sexual":0,"vermoegen":0}],"groups":{"CHM":{"n":3519},"CHW":{"n":3712},"AUSLM":{"n":1381},"AUSLW":{"n":1243},"ASYLM":{"n":75},"ASYLW":{"n":70}},"ueb":{"gewalt":2.1,"sexual":0.9,"vermoegen":13.9}};
const GROUPS=[['CH','M','Schweizer'],['CH','W','Schweizerinnen'],['AUSL','M','Ausländer'],['AUSL','W','Ausländerinnen'],['ASYL','M','Asylanten'],['ASYL','W','Asylantinnen']];
const SHORT={CHM:'Schweizer',CHW:'Schweizerinnen',AUSLM:'Ausl. ♂',AUSLW:'Ausl. ♀'};
const BANDS=['0-9','10-17','18-34','35-64','65+'];
const BANDTXT={'0-9':'0–9 Jahre','10-17':'10–17 Jahre','18-34':'18–34 Jahre','35-64':'35–64 Jahre','65+':'65 Jahre und älter'};
const CATS=['gewalt','sexual','vermoegen'];
const CATTXT={gewalt:'Leib und Leben',sexual:'Sexuelle Integrität',vermoegen:'Vermögen'};
const GTXT={CH:'Schweizer Staatsangehörige',AUSL:'Ausländer/in, ansässig (B, C)',ASYL:'Asylant/in (N, F, S)'};
// population in greyscale, accused persons in colour
const C={CHM:'#000000',CHW:'#000000',AUSLM:'#777777',AUSLW:'#777777',ASYLM:'#B5B5B5',ASYLW:'#B5B5B5',gewalt:'#E5383B',sexual:'#B832C9',vermoegen:'#F09A00',fade:.25};
const fmt=n=>n.toLocaleString('de-CH').replace(/[’,]/g,"'");
const reduce=matchMedia('(prefers-reduced-motion: reduce)').matches;
const root=document.querySelector('.k10');

// seeded rng
let seed=20251231; const rnd=()=>{seed=(seed*1664525+1013904223)>>>0;return seed/4294967296};
const shuffle=a=>{for(let i=a.length-1;i>0;i--){const j=Math.floor(rnd()*(i+1));[a[i],a[j]]=[a[j],a[i]]}return a};

// build persons
const P=[];
for(const [g,s] of GROUPS){
  for(const b of BANDS){
    const c=M.cells.find(x=>x.g===g&&x.s===s&&x.b===b);
    const tags=[];
    for(const k of CATS) for(let i=0;i<c[k];i++) tags.push(k);
    while(tags.length<c.n) tags.push(null);
    shuffle(tags);
    for(const t of tags) P.push({g,s,b,cat:t,j:rnd()});
  }
}
// grouped order = P order (group, band); column-major fill
P.forEach((p,i)=>{p.gi=i});
const mixOrder=shuffle([...P.keys()]);
mixOrder.forEach((pi,pos)=>{P[pi].mi=pos});
// layout: men first
const SEXSP=[];
{let i=0;for(const sx of ['M','W']){const mem=P.filter(p=>p.s===sx).sort((a,b)=>a.gi-b.gi);const a=i;for(const p of mem)p.si=i++;SEXSP.push({name:sx==='M'?'Männer':'Frauen',a,b:i,mem})}}
const posOf=(idx,colMajor)=>colMajor?[Math.floor(idx/100),idx%100]:[idx%100,Math.floor(idx/100)];

// group spans for labels
const spans=[];{let i=0;for(const [g,s,name] of GROUPS){const n=M.groups[g+s].n;spans.push({g,s,name,a:i,b:i+n,n});i+=n}}

const STEPS=[
 {key:'mix',layout:'mix',hl:null},
 {key:'sort',layout:'grp',hl:null},
 {key:'gewalt',layout:'grp',hl:['gewalt']},
 {key:'sexual',layout:'grp',hl:['sexual']},
 {key:'vermoegen',layout:'grp',hl:['vermoegen']},
 {key:'all',layout:'grp',hl:CATS},
 {key:'sex',layout:'sex',hl:CATS},
];
const catTotal=k=>P.filter(p=>p.cat===k).length;
const groupHit=(sp,cats)=>P.slice(sp.a,sp.b).filter(p=>cats.includes(p.cat)).length;
const fmtd=x=>x.toFixed(x<1?1:0);

function storyHTML(i){
  const G=M.groups, u=M.ueb;
  const ch=G.CHM.n+G.CHW.n, au=G.AUSLM.n+G.AUSLW.n, as=G.ASYLM.n+G.ASYLW.n;
  switch(STEPS[i].key){
   case 'mix': return `<h3>10'000 Menschen</h3><p>So sähe die Schweizer Wohnbevölkerung im Kleinen aus: ${fmt(ch)} Schweizer Staatsangehörige, ${fmt(au)} ansässige Ausländerinnen und Ausländer und ${as} Personen aus der Asylbevölkerung.</p><p class="k-note">Farbe und Kopfform zeigen die Gruppe: schwarz mit rundem Kopf für Schweizer, grau mit eckigem Kopf für ansässige Ausländer, hellgrau mit Rauten-Kopf für die Asylbevölkerung. Frauen tragen Rock, Kinder sind kleiner, Menschen ab 65 gehen am Stock. Wer mit der Maus über das Raster fährt, sieht die Figuren in einer Lupe vergrössert.</p>`;
   case 'sort': return `<h3>Nach Gruppen geordnet</h3><p>Jede Spalte fasst 100 Personen. Die Schweizer füllen gut 72 Spalten, die ansässigen Ausländer 26. Die ganze Asylbevölkerung passt in anderthalb Spalten ganz rechts.</p><p class="k-note">Innerhalb jeder Gruppe stehen oben links die Jüngsten, unten rechts die Ältesten.</p>`;
   case 'gewalt': return `<h3>Leib und Leben</h3><span class="k-big" style="color:var(--k-gewalt)">${catTotal('gewalt')}</span><p>Personen würden in einem Jahr wegen eines Delikts gegen Leib und Leben beschuldigt, von der Tätlichkeit bis zum Tötungsdelikt.</p><p class="k-note">Dazu kämen rund ${fmtd(u.gewalt)} Beschuldigte ohne Wohnsitz in der Schweiz.</p>`;
   case 'sexual': return `<h3>Sexuelle Integrität</h3><span class="k-big" style="color:var(--k-sexual)">${catTotal('sexual')}</span><p>Personen würden wegen eines Sexualdelikts beschuldigt, fast ausschliesslich Männer. Der grösste Teil betrifft Pornografie, sexuelle Belästigung und Vergewaltigung.</p><p class="k-note">Dazu käme rund eine weitere beschuldigte Person ohne Wohnsitz in der Schweiz.</p>`;
   case 'vermoegen': return `<h3>Vermögen</h3><span class="k-big" style="color:var(--k-vermoegen)">${catTotal('vermoegen')}</span><p>Personen würden wegen eines Vermögensdelikts beschuldigt, am häufigsten Ladendiebstahl, übriger Diebstahl, Sachbeschädigung und Betrug.</p><p class="k-note">Hier fallen Personen ohne Wohnsitz stark ins Gewicht, darunter der sogenannte Kriminaltourismus: Es kämen rund ${fmtd(u.vermoegen)} weitere Beschuldigte dazu, vor allem bei Einbruch und Taschendiebstahl.</p>`;
   case 'all': { const t=P.filter(p=>p.cat).length; return `<h3>Alles zusammen</h3><span class="k-big">${t} von 10'000</span><p>Rund ${(t/100).toFixed(1)} % der Bevölkerung würden in einem Jahr in einer dieser drei Kategorien beschuldigt. ${fmt(10000-t)} Menschen nicht.</p><p class="k-note">Pro Kopf sind die Anteile in der Asylbevölkerung und bei Männern höher; in absoluten Zahlen stellen Schweizer Männer die grösste Gruppe.</p>`;}
   case 'sex': { const [m,w]=SEXSP.map(sp=>({n:sp.b-sp.a,h:sp.mem.filter(p=>p.cat).length})); const t=m.h+w.h; return `<h3>Männer zuerst</h3><p>Ordnet man die 10'000 Menschen nur nach Geschlecht, stehen links ${fmt(m.n)} Männer, rechts ${fmt(w.n)} Frauen. Die beiden Hälften sind fast gleich gross, die Beschuldigten aber nicht.</p><span class="k-big">${Math.round(m.h/t*100)} %</span><p>der Beschuldigten im Modell sind Männer: ${m.h} Männer gegenüber ${w.h} Frauen.</p><p class="k-note">Das gilt in allen Gruppen: Bei Schweizern und ansässigen Ausländern werden Männer rund dreimal so häufig beschuldigt wie Frauen, in der Asylbevölkerung fast sechsmal so häufig.</p>`;}
  }
}

// canvas
const cv=document.getElementById('k-cv'),mainCtx=cv.getContext('2d'),box=document.getElementById('k-box'),tip=document.getElementById('k-tip');
let ctx=mainCtx;let W=0,cell=0,dpr=1;
function resize(){dpr=Math.min(window.devicePixelRatio||1,2);W=box.clientWidth;cell=W/100;cv.width=Math.round(W*dpr);cv.height=Math.round(W*dpr);ctx.setTransform(dpr,0,0,dpr,0,0);drawLabels();draw()}

let step=0, tPos=1, fromSorted='mix', toSorted='mix', tHl=1, prevHl=null, curHl=null, anim=null, started=false;
const ease=t=>t<.5?4*t*t*t:1-Math.pow(-2*t+2,3)/2;

function personXY(p,mode){return mode==='mix'?posOf(p.mi,false):posOf(mode==='sex'?p.si:p.gi,true)}
function hlLevel(p,set){return set&&p.cat&&set.includes(p.cat)?1:0}

function drawFigure(x,y,s,p,fill,alpha,glow){
  const k={'0-9':.55,'10-17':.75,'18-34':.95,'35-64':1,'65+':.92}[p.b];
  const cx=x+s/2, base=y+s*.96, h=s*.9*k;
  ctx.globalAlpha=alpha;
  if(glow>0){ctx.fillStyle=fill;ctx.globalAlpha=alpha*.3*glow;ctx.beginPath();ctx.arc(cx,y+s/2,s*1.15,0,6.283);ctx.fill();ctx.globalAlpha=alpha}
  if(s<5.5){ // tiny screens: dots
    ctx.fillStyle=fill;ctx.beginPath();ctx.arc(cx,y+s/2,s*.36*(.6+.4*k),0,6.283);ctx.fill();return}
  const hr=h*(p.b==='0-9'?.2:.16), headY=base-h+hr;
  const bodyTop=headY+hr*1.15, bodyH=base-bodyTop;
  ctx.fillStyle=fill;
  if(p.s==='M'){const bw=h*(p.b==='35-64'?.42:.36);ctx.fillRect(cx-bw/2,bodyTop,bw,bodyH*.62);ctx.fillRect(cx-bw/2,bodyTop+bodyH*.6,bw*.38,bodyH*.4);ctx.fillRect(cx+bw/2-bw*.38,bodyTop+bodyH*.6,bw*.38,bodyH*.4)}
  else{const bw=h*(p.b==='35-64'?.56:.5);ctx.beginPath();ctx.moveTo(cx-bw*.18,bodyTop);ctx.lineTo(cx+bw*.18,bodyTop);ctx.lineTo(cx+bw/2,base-bodyH*.2);ctx.lineTo(cx-bw/2,base-bodyH*.2);ctx.closePath();ctx.fill();ctx.fillRect(cx-bw*.22,base-bodyH*.22,bw*.12,bodyH*.22);ctx.fillRect(cx+bw*.1,base-bodyH*.22,bw*.12,bodyH*.22)}
  headPath(p.g,cx,headY,hr);
  ctx.fill();
  if(p.b==='65+'){ctx.lineWidth=Math.max(.8,s*.08);ctx.strokeStyle=fill;ctx.beginPath();ctx.moveTo(cx+h*.34,base);ctx.lineTo(cx+h*.34,bodyTop+bodyH*.15);ctx.lineTo(cx+h*.24,bodyTop+bodyH*.08);ctx.stroke()}
}
function headPath(g,cx,cy,r){
  ctx.beginPath();
  if(g==='CH'){ctx.arc(cx,cy,r,0,6.283)}
  else if(g==='AUSL'){const a=r*.92;ctx.rect(cx-a,cy-a,2*a,2*a)}
  else {const a=r*1.25;ctx.moveTo(cx,cy-a);ctx.lineTo(cx+a,cy);ctx.lineTo(cx,cy+a);ctx.lineTo(cx-a,cy);ctx.closePath()}
}
function draw(){
  if(!W) return;
  ctx.clearRect(0,0,W,W);
  const th=ease(tHl);
  for(const p of P){
    const [x0,y0]=personXY(p,fromSorted),[x1,y1]=personXY(p,toSorted);
    let lt=ease(tPos); if(fromSorted!==toSorted){lt=ease(Math.min(1,Math.max(0,(tPos*1.35-p.j*.35))))}
    const x=(x0+(x1-x0)*lt)*cell, y=(y0+(y1-y0)*lt)*cell;
    const a=hlLevel(p,prevHl), b=hlLevel(p,curHl);
    const lvl=a+(b-a)*th;
    const dim=(prevHl?1:0)+((curHl?1:0)-(prevHl?1:0))*th;
    const alpha= lvl>0 ? 1 : 1-(1-C.fade)*dim;
    let fill=C[p.g+p.s];
    if(lvl>0){fill=mix(fill,C[p.cat],lvl)}
    drawFigure(x,y,cell,p,fill,alpha,lvl);
  }
  ctx.globalAlpha=1;
}
function hex(c){c=c.replace('#','');return [0,2,4].map(i=>parseInt(c.substr(i,2),16))}
function mix(a,b,t){if(t>=1)return b;const A=hex(a),B=hex(b);return `rgb(${A.map((v,i)=>Math.round(v+(B[i]-v)*t)).join(',')})`}

function animate(){
  const dur=reduce?1:(fromSorted!==toSorted?1700:650);
  const t0=performance.now(), sPos=tPos<1, sHl=tHl<1;
  cancelAnimationFrame(anim);
  const tick=now=>{const t=Math.min(1,(now-t0)/dur);if(sPos)tPos=t;if(sHl)tHl=t;draw();if(t<1)anim=requestAnimationFrame(tick)};
  anim=requestAnimationFrame(tick);
}

function drawLabels(){
  const el=document.getElementById('k-labels'), st=STEPS[step], mode=st.layout;
  const an=document.getElementById('k-asylnote');
  const narrow=box.clientWidth<=480;
  if(mode==='sex'){
    let h='';
    SEXSP.forEach(sp=>{const hit=sp.mem.filter(p=>p.cat).length;h+=`<div class="k-lab" style="left:${(sp.a+sp.b)/2/100}%"><b>${sp.name}</b><span class="k-hit">${hit} von ${fmt(sp.b-sp.a)}</span></div><div class="k-tick" style="left:${sp.b/100}%"></div>`});
    el.innerHTML=h; an.innerHTML=''; return}
  if(mode==='mix'){an.innerHTML='';el.innerHTML=`<div class="k-lab" style="left:50%"><b>Zufällig verteilt</b>so wie man Menschen auf der Strasse begegnet</div>`;return}
  let h='';
  spans.forEach(sp=>{
    if(sp.g==='ASYL') return;
    const mid=(sp.a+sp.b)/2/100;
    const hit=st.hl?groupHit(sp,st.hl):null;
    h+=`<div class="k-lab" style="left:${mid}%"><b>${narrow?SHORT[sp.g+sp.s]:sp.name}</b>${hit!==null?`<span class="k-hit">${narrow&&sp.g==='AUSL'?hit:`${hit} von ${fmt(sp.n)}`}</span>`:fmt(sp.n)}</div>`;
    h+=`<div class="k-tick" style="left:${sp.b/100}%"></div>`;
  });
  const asy=spans.filter(s=>s.g==='ASYL');const hitA=st.hl?asy.reduce((a,s)=>a+groupHit(s,st.hl),0):null;
  el.innerHTML=h;
  an.innerHTML=`<b>Asylanten und Asylantinnen</b> in den letzten anderthalb Spalten: ${hitA!==null?`${hitA} von ${asy[0].n+asy[1].n} beschuldigt`:`${asy[0].n+asy[1].n} Personen`}`;
}

function go(i){
  i=Math.max(0,Math.min(STEPS.length-1,i));
  if(i===step && started) return; started=true;
  const next=STEPS[i];
  fromSorted=toSorted; toSorted=next.layout; tPos=(fromSorted===toSorted)?1:0;
  prevHl=curHl; curHl=next.hl; tHl=(JSON.stringify(prevHl)===JSON.stringify(curHl))?1:0;
  step=i;
  root.querySelectorAll('.k-step').forEach((el,j)=>el.classList.toggle('active',j===i));
  drawLabels();
  animate();
}
// build step cards
const stepsEl=document.getElementById('k-steps');
STEPS.forEach((s,i)=>{const d=document.createElement('div');d.className='k-step';d.innerHTML=`<div class="k-card">${storyHTML(i)}</div>`;stepsEl.appendChild(d)});
// keep the graphic below the site's sticky navigation
const stickyEl=root.querySelector('.k-sticky');
function navHeight(){const n=document.querySelector('nav');return n&&getComputedStyle(n).position==='sticky'?n.offsetHeight:0}
function layout(){root.style.setProperty('--k-top',navHeight()+'px')}
// scroll-driven: the last step whose top has passed the bottom of the graphic
function onScroll(){
  const line=navHeight()+stickyEl.offsetHeight+24; let best=0;
  root.querySelectorAll('.k-step').forEach((el,j)=>{if(el.getBoundingClientRect().top<line)best=j});
  go(best);
}
addEventListener('resize',()=>{layout();onScroll()});
addEventListener('scroll',()=>requestAnimationFrame(onScroll),{passive:true});
// tooltip and lens
const grid=new Array(10000);
function rebuildGrid(){for(const p of P){const [c,r]=personXY(p,toSorted);grid[r*100+c]=p}}
const lens=document.getElementById('k-lens'),lctx=lens.getContext('2d');
cv.addEventListener('mousemove',e=>{
  const r=cv.getBoundingClientRect(),c=Math.floor((e.clientX-r.left)/cell),row=Math.floor((e.clientY-r.top)/cell);
  if(c<0||c>99||row<0||row>99){tip.style.opacity=0;return}
  rebuildGrid();const p=grid[row*100+c];if(!p)return;
  tip.innerHTML=`${GTXT[p.g]}, ${p.s==='M'?'Mann':'Frau'}, ${BANDTXT[p.b]}${p.cat?`<br><b>Beschuldigt: ${CATTXT[p.cat]}</b>`:''}`;
  tip.style.left=(c+.5)*cell+'px';tip.style.top=row*cell+'px';tip.style.opacity=1;
  drawLens(c,row);
});
cv.addEventListener('mouseleave',()=>{tip.style.opacity=0;lens.style.opacity=0});
function drawLens(c,row){
  const N=7,S=300/N; lctx.clearRect(0,0,300,300);
  ctx=lctx;
  for(let dy=-3;dy<=3;dy++)for(let dx=-3;dx<=3;dx++){
    const cc=c+dx,rr=row+dy; if(cc<0||cc>99||rr<0||rr>99) continue;
    const p=grid[rr*100+cc]; if(!p) continue;
    const on=curHl&&p.cat&&curHl.includes(p.cat);
    drawFigure((dx+3)*S,(dy+3)*S,S,p,on?C[p.cat]:C[p.g+p.s],on||!curHl?1:Math.max(.35,C.fade*2),on?1:0);
  }
  ctx.globalAlpha=1; ctx=mainCtx;
  let lx=(c+.5)*cell+24, ly=row*cell-170; if(lx+150>W) lx=(c+.5)*cell-174; if(ly<0) ly=row*cell+24;
  lens.style.left=lx+'px';lens.style.top=ly+'px';lens.style.opacity=1;
}

new ResizeObserver(resize).observe(box);
layout(); go(0); onScroll();
if(document.fonts)document.fonts.ready.then(()=>{layout();onScroll()});
})();
</script>
{% endraw %}
</div>

## Die Zahlen im Überblick

Im Modell mit 10'000 Einwohnern ergeben sich pro Jahr diese Beschuldigten. Weil sich in einem so kleinen Modell nur ganze Personen darstellen lassen, steht in Klammern jeweils der exakte Erwartungswert.[^1]

| Gruppe          | Personen | Gewalt    | Sexual    | Vermögen    |
|:----------------|---------:|----------:|----------:|------------:|
| Schweizer       | 3'519    | 8 (8.3)   | 3 (3.4)   | 13 (12.8)   |
| Schweizerinnen  | 3'712    | 3 (2.7)   | 0 (0.2)   | 5 (4.8)     |
| Ausländer       | 1'381    | 7 (7.1)   | 2 (1.9)   | 10 (10.3)   |
| Ausländerinnen  | 1'243    | 2 (2.2)   | 0 (0.2)   | 4 (3.5)     |
| Asylanten       | 75       | 1 (1.2)   | 0 (0.4)   | 3 (3.3)     |
| Asylantinnen    | 70       | 0 (0.2)   | 0 (0.0)   | 0 (0.5)     |
| Ohne Wohnsitz   | –        | (2.1)     | (0.9)     | (13.9)      |

Gewalt entspricht dem StGB-Titel «Leib und Leben» (inkl. Tätlichkeiten), Sexualdelikte dem Titel «Sexuelle Integrität», Vermögensdelikte dem Titel «Vermögen». Personen ohne Wohnsitz sind keine Einwohner und deshalb nicht im Raster.

## Was die Grafik zeigt und was nicht

In absoluten Zahlen stellen Schweizer Männer die grösste Gruppe der Beschuldigten, schlicht weil sie die grösste Bevölkerungsgruppe sind. Pro Kopf sind die Anteile bei ansässigen ausländischen Männern etwa doppelt so hoch, in der Asylbevölkerung deutlich höher. Frauen werden in allen Gruppen viel seltener beschuldigt als Männer; bei Sexualdelikten fast nie.

Ein Teil dieser Unterschiede hängt mit dem Alter zusammen: Die ansässige ausländische Bevölkerung und vor allem die Asylbevölkerung sind jünger als die Schweizer Bevölkerung, und junge Männer werden in allen Gruppen am häufigsten beschuldigt. Die Grafik bildet die tatsächliche Bevölkerung ab und ist deshalb bewusst nicht altersbereinigt.

Wichtig ist auch, was «beschuldigt» bedeutet. Gezählt wird, wer in einer Anzeige oder polizeilichen Ermittlung einer Straftat verdächtigt wird, unabhängig davon, ob später eine Verurteilung folgt. Delikte, die nie angezeigt werden, fehlen. Und eine Person kann in mehreren Kategorien beschuldigt sein; im Raster erscheint sie nur einmal.

Für die Asylbevölkerung kommt ein statistischer Effekt hinzu: Die Bevölkerungszahl ist ein Stichtagswert per Ende Jahr, die Beschuldigten werden aber über das ganze Jahr gezählt. Wer im Laufe des Jahres einreiste, beschuldigt wurde und wieder ausreiste, fehlt im Bevölkerungsbestand. Die Anteile dieser Gruppe sind deshalb eher überschätzt.

## Methode

Beschuldigte Personen 2025 nach Aufenthaltsstatus, Geschlecht und Altersklasse gemäss Polizeilicher Kriminalstatistik.[^1] Bevölkerung per 31.12.2025 gemäss STATPOP, Asylbevölkerung inklusive nichtständiger Wohnbevölkerung (Ausweise N, F, S).[^2] Ansässige Ausländer: Ausweise B, C, Ci und EDA. Skaliert auf 10'000 Einwohner mit Rundung nach der Methode der grössten Reste.

## Referenzen

[^1]: [Bundesamt für Statistik. (2026). Polizeiliche Kriminalstatistik: Beschuldigte Personen (px-x-1903020100_102).](https://www.pxweb.bfs.admin.ch/pxweb/de/px-x-1903020100_102/px-x-1903020100_102.px/)

[^2]: [Bundesamt für Statistik. (2026). STATPOP: Ständige und nichtständige Wohnbevölkerung (px-x-0103010000_102).](https://www.pxweb.bfs.admin.ch/pxweb/de/px-x-0103010000_102/px-x-0103010000_102.px/)

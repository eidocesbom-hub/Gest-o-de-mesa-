<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Gestão de mesas</title>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@400;600;800&display=swap" rel="stylesheet">
<style>
:root{--bg:#f1f3f0;--card:#fff;--ink:#1b2a2f;--mut:#64747a;--line:#d9dfdc;--acc:#f2b705;--accink:#1b2a2f;--free:#2a9d5c;--busy:#d62828;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#141c1f;--card:#1e292d;--ink:#eef2f0;--mut:#93a3a9;--line:#33434a}}
:root[data-theme="dark"]{--bg:#141c1f;--card:#1e292d;--ink:#eef2f0;--mut:#93a3a9;--line:#33434a}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:"Bricolage Grotesque",system-ui,-apple-system,"Segoe UI",sans-serif;line-height:1.4}
main{max-width:720px;margin:0 auto;padding:16px}
h1{font-size:1.5rem;font-weight:800;margin:0}
h2{font-size:1.1rem;margin:0 0 8px}
h3{font-size:.95rem;margin:14px 0 4px;color:var(--mut)}
header{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px;gap:8px}
button,input,select{font:inherit;color:inherit}
button{cursor:pointer;border:1px solid var(--line);background:var(--card);border-radius:10px;padding:10px 14px;min-height:44px}
button:focus-visible,input:focus-visible,select:focus-visible{outline:3px solid var(--acc);outline-offset:2px}
button.p{background:var(--acc);color:var(--accink);border-color:var(--acc);font-weight:600}
button.d{color:var(--busy)}
input,select{width:100%;padding:10px 12px;min-height:44px;border:1px solid var(--line);border-radius:10px;background:var(--card)}
.card{background:var(--card);border:1px solid var(--line);border-radius:14px;padding:14px;margin-bottom:12px}
.row{display:flex;gap:8px;align-items:center;justify-content:space-between}
.col{display:grid;gap:8px}
.tabs{display:flex;gap:8px;margin-bottom:12px}
.tabs button.on{background:var(--ink);color:var(--bg)}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(140px,1fr));gap:10px}
.t{text-align:left;border-left:6px solid var(--free);padding:12px}
.t.busy{border-left-color:var(--busy)}
.t b{font-size:1.6rem;display:block}
.mut{color:var(--mut);font-size:.9rem}
.ov{position:fixed;inset:0;background:rgba(0,0,0,.5);display:flex;align-items:flex-end;justify-content:center;z-index:9}
.sheet{background:var(--bg);width:100%;max-width:720px;max-height:90%;overflow:auto;border-radius:18px 18px 0 0;padding:16px 16px calc(16px + env(safe-area-inset-bottom,0px))}
.qty{display:flex;gap:6px;align-items:center}
.qty button{min-width:44px;padding:0}
.tot{font-size:1.3rem;font-weight:800}
</style>
</head>
<body>
<main id="app"></main>
<script>
const K='gestao-mesas-v1';
const MENU=[['X-Burger',22],['X-Salada',24],['X-Bacon',27],['Hot dog',15],['Batata frita',18],['Refrigerante',7],['Suco natural',10],['Água',4]];
const esc=s=>String(s).replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]));
const brl=v=>v.toLocaleString('pt-BR',{style:'currency',currency:'BRL'});
function load(){try{const r=localStorage.getItem(K);if(r)return JSON.parse(r)}catch(e){}
return{adminPin:'1234',waiters:[],tables:Array.from({length:8},(_,i)=>({n:i+1,w:null,items:{}}))}}
function save(){try{localStorage.setItem(K,JSON.stringify(S))}catch(e){}}
let S=load();if(!S.menu){S.menu=MENU.map(([name,price],i)=>({id:'p'+i,name,price}));S.tables.forEach(t=>{const n={};Object.entries(t.items).forEach(([i,q])=>n['p'+i]=q);t.items=n})}
if(!S.cats){S.cats=[{id:'c1',name:'Lanches'},{id:'c2',name:'Porções'},{id:'c3',name:'Bebidas'}];const m={p0:'c1',p1:'c1',p2:'c1',p3:'c1',p4:'c2',p5:'c3',p6:'c3',p7:'c3'};S.menu.forEach(x=>x.cat=m[x.id]||'')}
const groups=()=>{const g=S.cats.map(c=>({name:c.name,items:S.menu.filter(m=>m.cat===c.id)}));const o=S.menu.filter(m=>!S.cats.some(c=>c.id===m.cat));if(o.length)g.push({name:'Sem categoria',items:o});return g.filter(x=>x.items.length)};
let errC='';
let U=null,tab='mesas',open=null,err='';
const total=t=>Object.entries(t.items).reduce((a,[i,q])=>{const m=S.menu.find(x=>x.id===i);return a+(m?m.price*q:0)},0);
const wname=id=>id==='admin'?'Admin':(S.waiters.find(w=>w.id===id)||{name:'—'}).name;
const canEdit=t=>U&&(U.admin||t.w===null||t.w===U.id);

function login(){return `<div class="card col"><h1>Gestão de mesas</h1><p class="mut">Entre como garçom ou como administrador.</p>
<label>Perfil<select id="who"><option value="admin">Administrador</option>${S.waiters.map(w=>`<option value="${w.id}">Garçom: ${esc(w.name)}</option>`).join('')}</select></label>
<label>PIN<input id="pin" type="password" inputmode="numeric" autocomplete="off"></label>
${err?`<p style="color:var(--busy);margin:0" role="alert">${err}</p>`:''}
<button class="p" data-a="login">Entrar</button>
${S.waiters.length?'':'<p class="mut">Ainda não há garçons. Entre como administrador (PIN inicial 1234) para adicionar.</p>'}</div>`}

function tables(){return `<div class="grid">${S.tables.map(t=>`<button class="t ${t.w!==null?'busy':''}" data-a="open" data-n="${t.n}"><span class="mut">Mesa</span><b>${t.n}</b>
${t.w!==null?`<span>${esc(wname(t.w))}</span><br><span class="mut">${brl(total(t))}</span>`:'<span style="color:var(--free)">Livre</span>'}</button>`).join('')}</div>
${U.admin?'<div class="row" style="margin-top:12px"><button data-a="addTable">Adicionar mesa</button><button class="d" data-a="delTable">Remover última mesa</button></div>':''}`}

function waiters(){return `<div class="card col"><h2>Novo garçom</h2>
<label>Nome<input id="wn" autocomplete="off"></label>
<label>PIN (4 dígitos)<input id="wp" inputmode="numeric" maxlength="4" autocomplete="off"></label>
${err?`<p style="color:var(--busy);margin:0" role="alert">${err}</p>`:''}
<button class="p" data-a="addW">Adicionar garçom</button></div>
<div class="card"><h2>Garçons (${S.waiters.length})</h2>${S.waiters.length?S.waiters.map(w=>`<div class="row" style="padding:6px 0"><span>${esc(w.name)}</span><button class="d" data-a="delW" data-id="${w.id}">Remover</button></div>`).join(''):'<p class="mut">Nenhum garçom ainda. Adicione o primeiro acima.</p>'}</div>
<div class="card col"><h2>PIN do administrador</h2><input id="ap" inputmode="numeric" maxlength="4" placeholder="Novo PIN"><button data-a="setAp">Salvar PIN</button></div>`}

function products(){const opts=S.cats.map(c=>`<option value="${c.id}">${esc(c.name)}</option>`).join('');
return `<div class="card col"><h2>Categorias (${S.cats.length})</h2>
${S.cats.map(c=>`<div class="row"><span>${esc(c.name)}</span><button class="d" data-a="delC" data-id="${c.id}">Remover</button></div>`).join('')||'<p class="mut">Nenhuma categoria ainda.</p>'}
<label>Nova categoria<input id="cn" autocomplete="off" placeholder="Ex.: Sobremesas"></label>
${errC?`<p style="color:var(--busy);margin:0" role="alert">${errC}</p>`:''}
<button class="p" data-a="addC">Adicionar categoria</button></div>
<div class="card col"><h2>Novo produto</h2>
<label>Nome<input id="pn" autocomplete="off"></label>
<label>Categoria<select id="pc">${opts}<option value="">Sem categoria</option></select></label>
<label>Preço (R$)<input id="pp" inputmode="decimal" placeholder="0,00" autocomplete="off"></label>
${err?`<p style="color:var(--busy);margin:0" role="alert">${err}</p>`:''}
<button class="p" data-a="addP">Adicionar produto</button></div>
<div class="card"><h2>Produtos (${S.menu.length})</h2>${groups().map(g=>`<h3>${esc(g.name)}</h3>`+g.items.map(m=>`<div class="row" style="padding:6px 0"><span>${esc(m.name)}<br><span class="mut">${brl(m.price)}</span></span><button class="d" data-a="delP" data-id="${m.id}">Remover</button></div>`).join('')).join('')||'<p class="mut">Nenhum produto ainda. Adicione o primeiro acima.</p>'}</div>`}

function sheet(){const t=S.tables.find(x=>x.n===open);if(!t)return'';const ed=canEdit(t);
return `<div class="ov" data-a="close"><div class="sheet" data-stop="1"><div class="row"><h2>Mesa ${t.n}</h2><button data-a="close">Fechar</button></div>
<p class="mut">${t.w!==null?'Atendida por '+esc(wname(t.w)):'Livre'}${ed?'':' — só o garçom da mesa ou o admin pode alterar.'}</p>
${S.menu.length?'':'<p class="mut">Nenhum produto cadastrado. O admin pode adicionar na aba Produtos.</p>'}${groups().map(g=>`<h3>${esc(g.name)}</h3>`+g.items.map(({id:i,name:n,price:p})=>`<div class="row" style="padding:6px 0"><span>${n}<br><span class="mut">${brl(p)}</span></span><div class="qty">
<button data-a="dec" data-i="${i}" aria-label="Menos ${n}" ${ed?'':'disabled'}>−</button><b style="min-width:1.5em;text-align:center">${t.items[i]||0}</b><button data-a="inc" data-i="${i}" aria-label="Mais ${n}" ${ed?'':'disabled'}>+</button></div></div>`).join('')).join('')}
<div class="row" style="margin-top:12px"><span class="tot">${brl(total(t))}</span><button class="p" data-a="pay" ${ed&&t.w!==null?'':'disabled'}>Fechar conta</button></div></div></div>`}

function draw(){const a=document.getElementById('app');
if(!U){a.innerHTML=login();return}
a.innerHTML=`<header><h1>${U.admin?'Administrador':esc(U.name)}</h1><button data-a="out">Sair</button></header>
${U.admin?`<div class="tabs"><button class="${tab==='mesas'?'on':''}" data-a="tab" data-t="mesas">Mesas</button><button class="${tab==='garcons'?'on':''}" data-a="tab" data-t="garcons">Garçons</button><button class="${tab==='cardapio'?'on':''}" data-a="tab" data-t="cardapio">Produtos</button></div>`:''}
${U.admin&&tab==='garcons'?waiters():U.admin&&tab==='cardapio'?products():tables()}${open!==null?sheet():''}`}

document.addEventListener('click',e=>{
const b=e.target.closest('[data-a]');if(!b)return;
if(b.dataset.a==='close'&&e.target.closest('[data-stop]')&&!e.target.closest('button'))return;
const a=b.dataset.a,v=id=>document.getElementById(id).value.trim();err='';errC='';
if(a==='login'){const w=v('who'),p=v('pin');
 if(w==='admin'){if(p===S.adminPin){U={admin:true};tab='mesas'}else err='PIN incorreto.'}
 else{const x=S.waiters.find(k=>k.id===w);if(x&&x.pin===p)U={id:x.id,name:x.name};else err='PIN incorreto.'}}
else if(a==='out'){U=null;open=null}
else if(a==='tab'){tab=b.dataset.t}
else if(a==='open'){open=+b.dataset.n}
else if(a==='close'){open=null}
else if(a==='addTable'){S.tables.push({n:S.tables.length+1,w:null,items:{}})}
else if(a==='delTable'){const t=S.tables[S.tables.length-1];if(t&&t.w===null&&S.tables.length>1)S.tables.pop();else err='x'}
else if(a==='addW'){const n=v('wn'),p=v('wp');
 if(!n)err='Informe o nome do garçom.';else if(!/^\d{4}$/.test(p))err='O PIN precisa ter 4 dígitos.';
 else if(S.waiters.some(w=>w.name.toLowerCase()===n.toLowerCase()))err='Já existe um garçom com esse nome.';
 else S.waiters.push({id:'w'+Date.now(),name:n,pin:p})}
else if(a==='delW'){const id=b.dataset.id;S.waiters=S.waiters.filter(w=>w.id!==id);S.tables.forEach(t=>{if(t.w===id){t.w=null;t.items={}}})}
else if(a==='addP'){const n=v('pn'),p=parseFloat(v('pp').includes(',')?v('pp').replace(/\./g,'').replace(',','.'):v('pp'));
 if(!n)err='Informe o nome do produto.';else if(!(p>0))err='Informe um preço maior que zero.';
 else S.menu.push({id:'p'+Date.now(),name:n,cat:v('pc'),price:Math.round(p*100)/100})}
else if(a==='addC'){const n=v('cn');if(!n)errC='Informe o nome da categoria.';else if(S.cats.some(c=>c.name.toLowerCase()===n.toLowerCase()))errC='Já existe uma categoria com esse nome.';else S.cats.push({id:'c'+Date.now(),name:n})}
else if(a==='delC'){const id=b.dataset.id;S.cats=S.cats.filter(c=>c.id!==id);S.menu.forEach(m=>{if(m.cat===id)m.cat=''})}
else if(a==='delP'){const id=b.dataset.id;S.menu=S.menu.filter(m=>m.id!==id);S.tables.forEach(t=>{delete t.items[id];if(!Object.keys(t.items).length)t.w=null})}
else if(a==='setAp'){const p=v('ap');if(/^\d{4}$/.test(p))S.adminPin=p;else err='O PIN precisa ter 4 dígitos.'}
else if(a==='inc'||a==='dec'){const t=S.tables.find(x=>x.n===open);if(t&&canEdit(t)){const i=b.dataset.i;
 if(a==='inc'){if(t.w===null)t.w=U.admin?'admin':U.id;t.items[i]=(t.items[i]||0)+1}
 else if(t.items[i]){t.items[i]--;if(!t.items[i])delete t.items[i]}}}
else if(a==='pay'){const t=S.tables.find(x=>x.n===open);if(t&&canEdit(t)){t.w=null;t.items={};open=null}}
if(err==='x')err='';
save();draw()});
draw();
</script>
</body>
</html>

# site-notepad-
[notepadpp.html](https://github.com/user-attachments/files/34556511/notepadpp.html)
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>new 1 - Notepad++</title>
<style>
:root{--bg:#f0f0f0;--bar:#f0f0f0;--line:#a0a0a0;--ed:#fff;--tx:#000;--gut:#e4e4e4;--gutx:#808080;--cur:#e8e8ff;--hov:#cde8ff;--tabon:#fff;--tab:#e8e8e8;--menu:#fff;
--k:#0000ff;--s:#808080;--c:#008000;--n:#ff8000;--t:#000080}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#2b2b2b;--bar:#2b2b2b;--line:#555;--ed:#1e1e1e;--tx:#ddd;--gut:#2b2b2b;--gutx:#888;--cur:#2a2d3e;--hov:#3a4a60;--tabon:#1e1e1e;--tab:#3a3a3a;--menu:#333;--k:#569cd6;--s:#ce9178;--c:#6a9955;--n:#d19a66;--t:#4ec9b0}}
*{box-sizing:border-box}
html,body{height:100%;margin:0}
:root{padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
body{background:var(--bg);color:var(--tx);font:12px "Segoe UI",Tahoma,Arial,sans-serif;display:flex;flex-direction:column;overflow:hidden;user-select:none}
#menu{display:flex;background:var(--bar);padding:1px 2px;position:relative;z-index:5;overflow-x:auto}
.mt{padding:3px 8px;cursor:default;white-space:nowrap}
.mt:hover,.mt.on{background:var(--hov)}
#dd{position:fixed;background:var(--menu);border:1px solid var(--line);box-shadow:2px 2px 4px rgba(0,0,0,.3);padding:2px;min-width:230px;display:none;z-index:9}
.mi{display:flex;justify-content:space-between;gap:30px;padding:4px 22px 4px 26px;cursor:default;white-space:nowrap}
.mi:hover{background:var(--hov)}.mi.dis{color:#999}.mi i{font-style:normal;color:#777}
.sep{height:1px;background:var(--line);margin:3px 2px;opacity:.5}
#tool{display:flex;gap:1px;padding:2px 4px;border-top:1px solid var(--line);border-bottom:1px solid var(--line);overflow-x:auto}
.tb{width:24px;height:24px;border:1px solid transparent;display:grid;place-items:center;font-size:15px;cursor:default;flex:none}
.tb:hover{border-color:#88b4e0;background:var(--hov)}
.ts{width:1px;background:var(--line);margin:2px 4px;flex:none}
#tabs{display:flex;background:var(--bar);padding:3px 2px 0;border-bottom:1px solid var(--line);overflow-x:auto;min-height:26px}
.tab{display:flex;align-items:center;gap:5px;padding:3px 6px 3px 8px;border:1px solid var(--line);border-bottom:0;background:var(--tab);margin-right:1px;cursor:default;white-space:nowrap;border-top:3px solid transparent}
.tab.on{background:var(--tabon);border-top-color:#ff8000;position:relative;top:1px}
.tab svg{width:13px;height:13px}.tab .x{width:14px;height:14px;line-height:12px;text-align:center;border-radius:2px;color:#888}
.tab .x:hover{background:#e04040;color:#fff}
#main{flex:1;display:flex;min-height:0;background:var(--ed)}
#gut{width:54px;background:var(--gut);color:var(--gutx);overflow:hidden;text-align:right;padding-right:6px;font:13px/18px Consolas,"Courier New",monospace;padding-top:2px;border-right:1px solid var(--line);flex:none}
#gut div{height:18px}#gut .cl{color:var(--tx);font-weight:bold}
#fold{width:14px;background:var(--gut);border-right:1px solid var(--line);flex:none}
#wrap{position:relative;flex:1;min-width:0}
#cl{position:absolute;left:0;right:0;height:18px;background:var(--cur);pointer-events:none}
#hl,#ta{position:absolute;inset:0;margin:0;padding:2px 6px;font:13px/18px Consolas,"Courier New",monospace;white-space:pre;overflow:auto;border:0;tab-size:4;letter-spacing:0}
#hl{overflow:hidden;pointer-events:none;color:var(--tx)}
#ta{background:transparent;color:transparent;caret-color:var(--tx);resize:none;outline:0;user-select:text;-webkit-text-fill-color:transparent}
#ta::selection{background:rgba(0,120,215,.35)}
.k{color:var(--k);font-weight:bold}.s{color:var(--s)}.c{color:var(--c)}.n{color:var(--n)}.t{color:var(--t);font-weight:bold}
#st{display:flex;border-top:1px solid var(--line);background:var(--bar);white-space:nowrap;overflow:hidden}
#st div{padding:2px 8px;border-right:1px solid var(--line)}#st div:first-child{flex:1;min-width:0;overflow:hidden;text-overflow:ellipsis}
#st div:last-child{border:0}
@media (max-width:620px){#st div:nth-child(n+3){display:none}}
</style>
</head>
<body>
<div id="menu"></div><div id="dd"></div>
<div id="tool"></div>
<div id="tabs"></div>
<div id="main"><div id="gut"></div><div id="fold"></div>
<div id="wrap"><div id="cl"></div><pre id="hl"></pre><textarea id="ta" spellcheck="false" autocapitalize="off" autocomplete="off"></textarea></div></div>
<div id="st"><div id="s1"></div><div id="s2"></div><div id="s3">Windows (CR LF)</div><div id="s4">UTF-8</div><div id="s5">INS</div></div>
<input type="file" id="fi" hidden>
<script>
var $=function(i){return document.getElementById(i)},ta=$('ta'),hl=$('hl'),gut=$('gut'),cl=$('cl');
var LANGS={txt:'Fichier texte normal',html:'Hyper Text Markup Language file',css:'Cascade Style Sheets File',js:'JavaScript file',py:'Python file',json:'JSON file'};
var KW={js:'var let const function return if else for while do switch case break continue new this class extends import export from default try catch finally throw typeof async await true false null undefined',
py:'def class return if elif else for while in import from as try except finally raise with lambda pass break continue and or not is None True False print',
json:'true false null',css:'important'};
var docs=[],cur=0,count=1,zoom=13;
function mk(name,text,lang){docs.push({name:name||'new '+(count++),text:text||'',lang:lang||'txt',saved:true})}
function esc(s){return s.replace(/&/g,'&amp;').replace(/</g,'&lt;')}
function hi(src,lang){
 if(lang==='txt')return esc(src);
 var re;
 if(lang==='html')re=/(<!--[\s\S]*?-->)|(<\/?[a-zA-Z][^>]*>?)|()()/g;
 else re=new RegExp('('+(lang==='py'?'#.*':lang==='css'?'\\/\\*[\\s\\S]*?\\*\\/':'\\/\\/.*|\\/\\*[\\s\\S]*?\\*\\/')+')|("(?:\\\\.|[^"\\\\\\n])*"?|\'(?:\\\\.|[^\'\\\\\\n])*\'?)|(\\b\\d+\\.?\\d*\\b)|([A-Za-z_][\\w-]*)','g');
 var kws=(KW[lang]||'').split(' '),out='',last=0,m;
 while((m=re.exec(src))){
  if(m[0]==='')re.lastIndex++;
  out+=esc(src.slice(last,m.index));last=m.index+m[0].length;var cls='',t=m[0];
  if(lang==='html'){cls=m[1]?'c':m[2]?'k':''}
  else{cls=m[1]?'c':m[2]?'s':m[3]?'n':(m[4]&&kws.indexOf(m[4])>-1)?'k':''}
  out+=cls?'<span class="'+cls+'">'+esc(t)+'</span>':esc(t)}
 return out+esc(src.slice(last))}
function render(){
 var d=docs[cur],v=ta.value;d.text=v;
 hl.innerHTML=hi(v,d.lang)+'\n';
 var n=v.split('\n').length,g='';for(var i=1;i<=n;i++)g+='<div>'+i+'</div>';gut.innerHTML=g;
 pos()}
function pos(){
 var v=ta.value,p=ta.selectionStart,b=v.slice(0,p).split('\n'),ln=b.length,col=b[ln-1].length+1,sel=Math.abs(ta.selectionEnd-p),
 sl=sel?v.slice(Math.min(p,ta.selectionEnd),Math.max(p,ta.selectionEnd)).split('\n').length:0;
 $('s1').textContent=LANGS[docs[cur].lang]+'     length : '+v.length+'     lines : '+v.split('\n').length;
 $('s2').textContent='Ln : '+ln+'     Col : '+col+'     Sel : '+sel+' | '+sl;
 cl.style.top=(2+(ln-1)*zoomLH()-ta.scrollTop)+'px';
 var g=gut.children;for(var i=0;i<g.length;i++)g[i].className=(i===ln-1)?'cl':'';
 scr()}
function zoomLH(){return Math.round(zoom*18/13)}
function scr(){hl.scrollTop=ta.scrollTop;hl.scrollLeft=ta.scrollLeft;gut.scrollTop=ta.scrollTop;cl.style.top=(2+(ta.value.slice(0,ta.selectionStart).split('\n').length-1)*zoomLH()-ta.scrollTop)+'px'}
var DISK=function(c){return '<svg viewBox="0 0 16 16"><path fill="'+c+'" d="M1 1h12l2 2v12H1z"/><path fill="#fff" d="M4 1h7v5H4zM4 9h8v6H4z"/><path fill="'+c+'" d="M8 2h2v3H8z"/></svg>'};
function tabs(){
 var h='';docs.forEach(function(d,i){h+='<div class="tab'+(i===cur?' on':'')+'" data-i="'+i+'">'+DISK(d.saved?'#2f6fd0':'#e03030')+'<span>'+esc(d.name)+'</span><span class="x" data-x="'+i+'">×</span></div>'});
 $('tabs').innerHTML=h;document.title=docs[cur].name+' - Notepad++'}
function show(i){cur=i;ta.value=docs[i].text;tabs();ta.style.fontSize=hl.style.fontSize=zoom+'px';render();ta.focus()}
function nouveau(){mk();show(docs.length-1)}
function fermer(i){if(i==null)i=cur;if(docs.length===1){docs[0]=({name:'new '+(count++),text:'',lang:'txt',saved:true});show(0);return}
 docs.splice(i,1);show(Math.min(cur>i?cur-1:cur,docs.length-1))}
function ouvrir(){$('fi').click()}
$('fi').onchange=function(e){var f=e.target.files[0];if(!f)return;var r=new FileReader();r.onload=function(){
 var x=(f.name.split('.').pop()||'').toLowerCase(),m={html:'html',htm:'html',css:'css',js:'js',py:'py',json:'json'};
 mk(f.name,r.result,m[x]||'txt');show(docs.length-1)};r.readAsText(f);e.target.value=''};
var EXT={txt:'txt',html:'html',css:'css',js:'js',py:'py',json:'json'},MIME={txt:'text/plain',html:'text/html',css:'text/css',js:'text/javascript',py:'text/x-python',json:'application/json'};
function enreg(){var d=docs[cur],a=document.createElement('a');
 d.name=d.name.replace(/\.(txt|html?|css|js|json|py)$/i,'')+'.'+EXT[d.lang];
 a.href=URL.createObjectURL(new Blob([d.text],{type:MIME[d.lang]+';charset=utf-8'}));
 a.download=d.name;a.click();d.saved=true;tabs()}
function ex(c){ta.focus();document.execCommand(c)}
function coller(){ta.focus();navigator.clipboard.readText().then(function(t){document.execCommand('insertText',false,t)}).catch(function(){})}
function chercher(){var q=prompt('Rechercher :');if(!q)return;var i=ta.value.indexOf(q,ta.selectionEnd);if(i<0)i=ta.value.indexOf(q);
 if(i<0){alert('Impossible de trouver le texte "'+q+'"');return}ta.focus();ta.setSelectionRange(i,i+q.length);pos()}
function aller(){var n=parseInt(prompt('Aller à la ligne :'),10);if(!n)return;var L=ta.value.split('\n'),p=0;for(var i=0;i<Math.min(n-1,L.length-1);i++)p+=L[i].length+1;
 ta.focus();ta.setSelectionRange(p,p);ta.scrollTop=Math.max(0,(n-5)*zoomLH());pos()}
function zm(d){zoom=d===0?13:Math.max(8,Math.min(40,zoom+d));ta.style.fontSize=hl.style.fontSize=gut.style.fontSize=zoom+'px';ta.style.lineHeight=hl.style.lineHeight=gut.style.lineHeight=zoomLH()+'px';
 [].forEach.call(gut.children,function(x){x.style.height=zoomLH()+'px'});render()}
function lang(l){docs[cur].lang=l;render()}
function insDate(){ta.focus();document.execCommand('insertText',false,new Date().toLocaleString('fr-FR'))}
function maj(f){var s=ta.selectionStart,e=ta.selectionEnd;if(s===e)return;ta.focus();document.execCommand('insertText',false,f(ta.value.slice(s,e)));}
function about(){alert('Notepad++ v8.6\n\nReproduction web de l\'interface. Éditeur de texte, aucune donnée n\'est envoyée.')}
var N=function(l,f,k){return [l,f,k]},S=null;
var M={
'Fichier':[N('Nouveau',nouveau,'Ctrl+N'),N('Ouvrir...',ouvrir,'Ctrl+O'),S,N('Enregistrer',enreg,'Ctrl+S'),S,N('Fermer',fermer,'Ctrl+W')],
'Édition':[N('Annuler',function(){ex('undo')},'Ctrl+Z'),N('Rétablir',function(){ex('redo')},'Ctrl+Y'),S,N('Couper',function(){ex('cut')},'Ctrl+X'),N('Copier',function(){ex('copy')},'Ctrl+C'),N('Coller',coller,'Ctrl+V'),N('Supprimer',function(){ex('delete')},'Suppr'),N('Sélectionner tout',function(){ta.focus();ta.select();pos()},'Ctrl+A'),S,N('Insérer date et heure',insDate),N('EN MAJUSCULES',function(){maj(function(t){return t.toUpperCase()})},'Ctrl+Maj+U'),N('en minuscules',function(){maj(function(t){return t.toLowerCase()})},'Ctrl+U')],
'Recherche':[N('Rechercher...',chercher,'Ctrl+F'),N('Aller à...',aller,'Ctrl+G')],
'Affichage':[N('Zoom avant',function(){zm(1)},'Ctrl+Molette'),N('Zoom arrière',function(){zm(-1)}),N('Restaurer le zoom par défaut',function(){zm(0)})],
'Encodage':[N('ANSI'),N('UTF-8',function(){$('s4').textContent='UTF-8'}),N('UTF-8 avec BOM',function(){$('s4').textContent='UTF-8-BOM'}),N('UTF-16 BE BOM',function(){$('s4').textContent='UTF-16 BE BOM'})],
'Langage':[N('Texte normal',function(){lang('txt')}),S,N('CSS',function(){lang('css')}),N('HTML',function(){lang('html')}),N('JavaScript',function(){lang('js')}),N('JSON',function(){lang('json')}),N('Python',function(){lang('py')})],
'Paramètres':[N('Préférences...',function(){alert('Les préférences ne sont pas disponibles dans cette version web.')})],
'Outils':[N('Hash MD5',function(){})],
'Macro':[N('Démarrer l\'enregistrement')],
'Exécution':[N('Exécuter...',function(){alert('Exécution impossible dans le navigateur.')},'F5')],
'Greffons':[N('Administrateur de greffons...')],
'Fenêtres':[N('Dupliquer',function(){mk(docs[cur].name+' (2)',docs[cur].text,docs[cur].lang);show(docs.length-1)}),N('Fermer tous',function(){docs=[];mk();show(0)})],
'?':[N('À propos de Notepad++...',about,'F1')]};
var open=null,dd=$('dd');
function buildMenu(){var h='';Object.keys(M).forEach(function(k){h+='<div class="mt" data-m="'+k+'">'+k+'</div>'});$('menu').innerHTML=h}
function showMenu(el){var k=el.dataset.m;open=k;[].forEach.call(document.querySelectorAll('.mt'),function(x){x.classList.toggle('on',x===el)});
 var h='';M[k].forEach(function(it,i){h+=it?'<div class="mi'+(it[1]?'':' dis')+'" data-i="'+i+'"><span>'+it[0]+'</span><i>'+(it[2]||'')+'</i></div>':'<div class="sep"></div>'});
 dd.innerHTML=h;dd.style.display='block';var r=el.getBoundingClientRect();dd.style.left=Math.min(r.left,innerWidth-dd.offsetWidth-2)+'px';dd.style.top=r.bottom+'px'}
function closeMenu(){open=null;dd.style.display='none';[].forEach.call(document.querySelectorAll('.mt'),function(x){x.classList.remove('on')})}
$('menu').onclick=function(e){var el=e.target.closest('.mt');if(!el)return;open===el.dataset.m?closeMenu():showMenu(el)};
$('menu').onmouseover=function(e){var el=e.target.closest('.mt');if(el&&open&&open!==el.dataset.m)showMenu(el)};
dd.onclick=function(e){var el=e.target.closest('.mi');if(!el)return;var it=M[open][+el.dataset.i];closeMenu();if(it&&it[1])it[1]()};
document.addEventListener('mousedown',function(e){if(!e.target.closest('#dd,#menu'))closeMenu()});
var TB=[['⬜',nouveau,'Nouveau'],['📂',ouvrir,'Ouvrir'],['💾',enreg,'Enregistrer'],0,['✂',function(){ex('cut')},'Couper'],['⧉',function(){ex('copy')},'Copier'],['📋',coller,'Coller'],0,['↶',function(){ex('undo')},'Annuler'],['↷',function(){ex('redo')},'Rétablir'],0,['🔍',chercher,'Rechercher'],0,['＋',function(){zm(1)},'Zoom avant'],['－',function(){zm(-1)},'Zoom arrière']];
var th='';TB.forEach(function(b,i){th+=b?'<div class="tb" data-b="'+i+'" title="'+b[2]+'">'+b[0]+'</div>':'<div class="ts"></div>'});$('tool').innerHTML=th;
$('tool').onclick=function(e){var el=e.target.closest('.tb');if(el)TB[+el.dataset.b][1]()};
$('tabs').onclick=function(e){var x=e.target.closest('[data-x]');if(x){fermer(+x.dataset.x);return}var t=e.target.closest('.tab');if(t)show(+t.dataset.i)};
$('tabs').onauxclick=function(e){var t=e.target.closest('.tab');if(t&&e.button===1)fermer(+t.dataset.i)};
ta.addEventListener('input',function(){docs[cur].saved=false;tabs();render()});
['keyup','click','select','focus'].forEach(function(ev){ta.addEventListener(ev,pos)});
ta.addEventListener('scroll',scr);
ta.addEventListener('keydown',function(e){
 if(e.key==='Tab'){e.preventDefault();document.execCommand('insertText',false,'\t')}
 if(e.ctrlKey&&!e.shiftKey){var k=e.key.toLowerCase(),a={n:nouveau,o:ouvrir,s:enreg,w:fermer,f:chercher,g:aller};if(a[k]){e.preventDefault();a[k]()}}});
ta.addEventListener('wheel',function(e){if(e.ctrlKey){e.preventDefault();zm(e.deltaY<0?1:-1)}},{passive:false});
ta.addEventListener('keyup',function(e){if(e.key==='Insert'){var s=$('s5');s.textContent=s.textContent==='INS'?'OVR':'INS'}});
buildMenu();
mk('new 1','// Bienvenue dans Notepad++ (version web)\n// Tapez ici, ouvrez un fichier ou changez de langage dans le menu Langage.\n\nfunction bonjour(nom) {\n    var message = "Bonjour, " + nom + " !";\n    console.log(message);\n    return 42;\n}\n\nbonjour("monde");\n','js');
show(0);
</script>
</body>
</html>

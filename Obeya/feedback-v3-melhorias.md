# Feedback layer — melhorias para a skill (proposta v3)

Compilado das mudanças feitas no `feedback-v2` durante a aplicação no Digital Obeya.
Tudo continua **drop-in, sem dependências**. As mudanças abaixo podem ser portadas para
`assets/comentarios-dropin.html` e documentadas no `SKILL.md`.

---

## 1. Lista mostra TODOS os comentários (não só a visão atual)

**Problema:** na v2 a lista era filtrada pela visão atual (`shown`), então comentários de
outras visões "sumiam" da lista.
**Agora:** os **pinos** continuam por visão (board × modal), mas a **lista mostra tudo**, com
um selo indicando a visão de cada item, e o contador reflete o total.

No `render()`, troque o bloco da lista por:

```js
list.innerHTML=''; var all=comments.slice().sort(function(a,b){return a.n-b.n});
if(!all.length){list.innerHTML='<p style="color:#94a3b8;font-size:13px;padding:6px">No comments yet.</p>';}
all.forEach(function(c){var it=document.createElement('div');it.className='rv-item'+(c.resolved?' resolved':'');
  var vw=(c.view&&c.view.indexOf('modal:')===0)?('Modal · '+c.view.slice(6)):'Board';
  it.innerHTML='<div class="h"><span class="b">'+c.n+'</span> '+esc(c.author||'—')+' <span class="rv-vw">'+esc(vw)+'</span>'+(c.resolved?' ✓':'')+'</div><div class="t">'+esc(c.text)+'</div><div class="when">'+new Date(c.ts).toLocaleString('en-US')+'</div>';
  it.addEventListener('click',function(){
    if((c.view||'doc')===viewKey()){                                  // mesma visão: rola + abre o pino
      var a=getAnchor(viewKey());
      try{(a.scrollTo?a:window).scrollTo({top:c.yPct*scH(a)-160,behavior:'smooth'});}catch(e){}
      var pin=layer.querySelector('.rv-pin[data-n="'+c.n+'"]');openPop(c,pin);
    } else { openPop(c,null); }                                       // outra visão: abre o popup com o texto
  });
  list.appendChild(it);});
countEl.textContent=all.length;
```

CSS do selo de visão:

```css
.rv-item .h .rv-vw{margin-left:auto;font-weight:600;color:#94a3b8;font-size:10.5px;background:#f1f5f9;padding:1px 7px;border-radius:99px}
```

---

## 2. Não inserir comentário ao clicar em elementos clicáveis

**Problema:** no modo comentário, qualquer clique virava pino — inclusive em botões, abas,
inputs etc.
**Agora:** só cria pino ao clicar em **áreas não clicáveis**. Heurística portátil: interativos
nativos + qualquer elemento com `cursor:pointer` na árvore.

```js
function rvInteractive(el){
  var n=el;
  while(n && n.nodeType===1 && n!==document.body){
    if(n.matches && n.matches('a,button,input,select,textarea,label,[role="button"],[tabindex],[contenteditable],[onclick]')) return true;
    var cs=getComputedStyle(n); if(cs && cs.cursor==='pointer') return true;
    n=n.parentElement;
  }
  return false;
}
```

E na 1ª linha do listener de clique (logo após o guard de `#rv-bar,...`):

```js
document.addEventListener('click',function(ev){
  if(!commentMode) return;
  if(ev.target.closest('#rv-bar,#rv-toggle,#rv-panel,#rv-pop,.rv-pin')) return;
  if(rvInteractive(ev.target)) return;          // <— novo guard
  ...
});
```

> Opcional: expor `RV_CONFIG.skipSelector` para o projeto adicionar classes clicáveis
> próprias (ex.: `.tab, .expand, .rcode`). No Obeya usei uma lista estendida dessas classes.

---

## 3. Três estados de visibilidade (painel → botão → sliver) e recolhido por padrão

**Problema:** a barra de 270px ficava aberta por padrão, na frente do conteúdo.
**Agora:**
- **Padrão = recolhido**: aparece só um **botão redondo 💬** no canto.
- Clicar no 💬 abre o **painel**.
- No topo do painel: **—** recolhe para o botão; **×** esconde tudo num **sliver fino na borda**
  (`#rv-nub`), que ao ser clicado traz o botão de volta.

HTML (topo do bloco):

```html
<button id="rv-toggle" title="Review comments">💬</button>
<div id="rv-nub" title="Show review"></div>
<div id="rv-bar">
  <div class="rv-top"><span class="dot"></span> <span id="rv-title">Review comments</span>
    <span style="margin-left:auto;cursor:pointer" id="rv-min" title="Collapse to button">—</span>
    <span style="cursor:pointer;margin-left:10px;font-size:16px" id="rv-hide" title="Hide in the corner">×</span>
  </div>
  ...
```

CSS (recolhido por padrão + botão redondo + sliver):

```css
#rv-bar{display:none; position:fixed; top:14px; right:14px; /* ...resto igual... */}
#rv-toggle{position:fixed;top:14px;right:14px;z-index:9001;background:#0f172a;color:#fff;border:0;border-radius:50%;width:42px;height:42px;padding:0;text-align:center;line-height:42px;font-weight:700;font-size:18px;cursor:pointer;box-shadow:0 6px 18px rgba(2,6,23,.3);display:block;font-family:inherit}
#rv-nub{position:fixed;top:16px;right:0;width:9px;height:46px;border-radius:8px 0 0 8px;background:#0f172a;cursor:pointer;z-index:9001;display:none;box-shadow:-2px 2px 10px rgba(2,6,23,.3);transition:width .12s}
#rv-nub:hover{width:15px}
```

JS (handlers das 3 transições):

```js
document.getElementById('rv-min').onclick   =function(){bar.style.display='none';  tgl.style.display='block'; };           // painel -> botão
document.getElementById('rv-toggle').onclick=function(){bar.style.display='block'; tgl.style.display='none';  nub.style.display='none';}; // botão -> painel
document.getElementById('rv-hide').onclick  =function(){bar.style.display='none';  tgl.style.display='none';  nub.style.display='block';}; // painel -> sliver
document.getElementById('rv-nub').onclick   =function(){nub.style.display='none';  tgl.style.display='block'; };           // sliver -> botão
// (bar = #rv-bar, tgl = #rv-toggle, nub = #rv-nub)
```

---

## 4. Botão "List" alterna abrir/fechar

```js
document.getElementById('rv-listbtn').onclick=function(){panel.classList.toggle('open')};
```

---

## 5. Interface em inglês (i18n)

A v2 vinha em PT. Sugestão: deixar os textos em EN por padrão (ou expor `RV_CONFIG.i18n`).
Mapeamento usado:

| PT (v2) | EN (v3) |
|---|---|
| Revisão de comentários | Review comments |
| Seu nome (revisor) / ex.: Maria | Your name (reviewer) / e.g., Maria |
| 💬 Ativar modo comentário / ✋ Sair do modo comentário | 💬 Enable comment mode / ✋ Exit comment mode |
| 📋 Lista | 📋 List |
| ⬇ Exportar / ⬆ Importar comentários | ⬇ Export / ⬆ Import comments |
| Comentários | Comments |
| Nenhum comentário ainda. | No comments yet. |
| Pino # / Salvar / Resolver / Reabrir / Excluir | Pin # / Save / Resolve / Reopen / Delete |
| Anônimo | Anonymous |
| Importados N comentário(s). / Não encontrei comentários… | Imported N comment(s). / No comments found in this file. |
| (data) `toLocaleString('pt-BR')` | `toLocaleString('en-US')` |
| tooltips | Collapse to button / Hide in the corner / Show review |

---

## Resumo (para o changelog do SKILL.md)

- **Lista global**: mostra todos os comentários (board + modais) com selo de visão; clique navega até o pino (ou abre o texto se for de outra visão).
- **Anti-clique acidental**: não cria pino sobre elementos interativos (`cursor:pointer`/nativos).
- **3 níveis de visibilidade**: painel ▸ botão 💬 ▸ sliver na borda; **recolhido por padrão** para não cobrir a tela.
- **List** com toggle (abre/fecha).
- **Textos em inglês** (i18n).

> Compatibilidade preservada: prefixo `rv-`, sem dependências, export/import iguais
> (campo `view` por comentário mantido), impressão/PDF ainda escondem a barra.

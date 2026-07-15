# Publicar no GitHub Pages — Digital Obeya

Base do site: **https://electradv.github.io/solvace-ui-prototypes/**
(repositório `solvace-ui-prototypes`, já servido por Pages).

> Não consigo dar `push` por aqui (o `.git` fica na pasta-pai, fora do meu acesso, e
> publicar exige suas credenciais). Abaixo está tudo pronto + os comandos para você subir.

## 1. Árvore de pastas (recomendada)

```
solvace-ui-prototypes/                  ← raiz do repo (Pages)
├─ .nojekyll                            ← na RAIZ (garante servir _arquivos e subpastas)
├─ index.html                           ← Knowledge Center (já existe)
└─ Obeya/                               ← módulo Digital Obeya
   ├─ index.html                        ← redireciona p/ obeya-board.html   (novo)
   ├─ qa-index.html                     ← catálogo de QA do módulo          (novo)
   ├─ obeya-board.html                  ← protótipo principal (v atual)
   ├─ solvace-widgets-gallery.html
   ├─ us-66499-feed-zoom-filtro-barra.html
   ├─ us-66506-widget-e-configuracao.html
   ├─ widget-pizza-prototipo.html
   ├─ modo-atualizacao-troca-de-board.html
   └─ (docs) FIREBASE-SETUP.md · feedback-v3-melhorias.md
```

## 2. URLs (estáveis para cards do Azure DevOps)

| O quê | URL |
|---|---|
| Board (pasta) | `https://electradv.github.io/solvace-ui-prototypes/Obeya/` |
| Board (direto) | `https://electradv.github.io/solvace-ui-prototypes/Obeya/obeya-board.html` |
| QA do módulo | `https://electradv.github.io/solvace-ui-prototypes/Obeya/qa-index.html` |
| US-66506 | `https://electradv.github.io/solvace-ui-prototypes/Obeya/us-66506-widget-e-configuracao.html` |
| US-66499 | `https://electradv.github.io/solvace-ui-prototypes/Obeya/us-66499-feed-zoom-filtro-barra.html` |
| Galeria | `https://electradv.github.io/solvace-ui-prototypes/Obeya/solvace-widgets-gallery.html` |

## 3. Regras de links (subpath-safe)
- **Sempre relativos** (`obeya-board.html`, `./qa-index.html`) — nunca comece com `/`,
  pois o site vive num subcaminho (`/solvace-ui-prototypes/`).
- Para um estado específico, use **hash**: `obeya-board.html#andon` (a página pode ler
  `location.hash` se quiser abrir num modo).
- Imagens/SVG externos (ex.: thumbnails do YouTube) carregam normal quando online.

## 4. Publicar (rode na sua máquina, na raiz do repo)
```bash
cd /Users/guilhermepezoti/solvace-ui-prototypes
git add Obeya/obeya-board.html Obeya/index.html Obeya/qa-index.html \
        Obeya/FIREBASE-SETUP.md Obeya/feedback-v3-melhorias.md Obeya/GITHUB-PAGES.md
git commit -m "Obeya: board v2 (lib widgets, dados DOB-67, camada de revisão + Firebase)"
git push
```
- Garanta um arquivo **`.nojekyll` na raiz** do repo (se ainda não existir): `touch .nojekyll && git add .nojekyll`.
- Pages → Settings → Pages: branch `main` (ou `gh-pages`) / pasta `/root`. (Já configurado, pois o site está no ar.)
- Em ~1 min, o board fica em `…/solvace-ui-prototypes/Obeya/`.

## 5. Fluxo de QA (cards do Azure)
1. No card, cole a **URL da tela** (US-XXXXX) — link estável.
2. Revisão direto no protótipo: botão **💬** (canto) → **Enable comment mode** → clicar nos
   pontos → comentar. Com **Firebase** ligado (ver `FIREBASE-SETUP.md`), os comentários
   são compartilhados entre revisores em tempo real; sem Firebase, use **Export/Import**.
3. Resolva/feche comentários no painel **List**.

## 6. Versionamento (v1/v2 sem quebrar links)
- O link canônico do card aponta sempre para o nome estável: `obeya-board.html`.
- Para preservar uma versão antiga ao publicar uma nova:
  - copie a atual para um snapshot **antes** de sobrescrever: `Obeya/v1/obeya-board.html`
    (ou `obeya-board-v1.html`), e mantenha `obeya-board.html` como a **versão corrente**.
  - assim `…/Obeya/obeya-board.html` sempre é a mais recente, e `…/Obeya/v1/…` guarda o histórico.
- Evite renomear o arquivo corrente (quebraria os links já colados nos cards).

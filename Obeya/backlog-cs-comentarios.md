# Board CS — comentários classificados, traduzidos e com solução

**Fonte:** camada de revisão do link do CS (`rv_comments/obeya_board_cs`, isolado do seu). **42 comentários** — autores: Omar, Vince e anônimos.
Marcação do próprio CS entre parênteses: **(Y)** concordam/fazer · **(N)** nota/nice-to-have · **(?)** avaliar · **(New US)** nova user story.

---

## 🔴 Alta — bugs e fluxo central

| Nº | Autor · Local | Comentário (PT) | Solução proposta |
|----|----|----|----|
| 37 | Anon · board | (Y) Clicar aqui no update mode não funciona | Bug — habilitar edição/clique nesse widget no update (provável tabela/registro) |
| 39 | Anon · board | (?) Tentei clicar nesses botões várias vezes e não funcionam | Bug — corrigir os botões que não respondem |
| 40 | Anon · board | (?) Este aqui também não funciona | Bug — mesmo caso do #39 |
| 41 | Anon · editModal | (?) Ao trocar o Source, tudo que foi configurado no General some (bug). Concorrentes começam pelo Source → config (diário/mensal) → formatação condicional; faz mais sentido de UX | Preservar o estado ao trocar Source **+ reordenar abas**: Source → Geral/Config → Formatação |
| 18 | Vince · fullModal | (Y) Deveria dar pra fechar o zoom do indicador clicando no fundo | Clique no backdrop fecha o fullModal |
| 35 | Anon · fullModal | (Y) Ao abrir o zoom, sair clicando no fundo (não só no X) | Mesmo do #18 — fechar pelo backdrop |
| 2 | Omar · board | (Y) O Kanban de Action Plan deveria ocupar a tela cheia | Abrir o Kanban em fullscreen |
| 5 | Omar · batchModal | (Y) Permitir download/upload de Excel | Botões importar/exportar Excel no batch update |

---

## 🟡 Média — melhorias de UX / produtividade / visual

| Nº | Autor · Local | Comentário (PT) | Solução proposta |
|----|----|----|----|
| 1 | Omar · fullModal | (N) O espaço entre o widget (gráfico) e o painel Feed/Ações à direita ficou estranho | Reduzir o gap / ajustar largura do drawer no zoom |
| 8 | Vince · fullModal | (N) Setas ‹ › para ir ao próximo indicador sem fechar e reabrir o zoom | Navegação prev/next entre indicadores no fullModal |
| 13 | Vince · board | (Y) Em gráfico grande, mostrar no rodapé (toggle): dono do indicador, planos de ação relacionados, nº de comentários. Ver Fabriq | Rodapé informativo em widgets grandes (configurável) |
| 14 | Vince · board | (Y) Em indicador grande, seletor de período (1d/7d/30d) no topo direito. Ver Fabriq | Já temos os filtros no zoom — levar ao widget grande no board |
| 33 | Anon · board | (?) Falta legenda/valores nos gráficos; clientes rastreiam números grandes e querem vê-los no gráfico | Exibir valores nas barras + legenda |
| 23 | Vince · board | (Y) Clicar no avatar da pessoa filtra o Action Plan e o board pelos indicadores dela (estilo Andon, cinza nos demais) | Filtro por pessoa (destaque/cinza como o Andon) |
| 30 | Vince · board | (Y) Clique direito no action plan → menu: escalar / reagendar (menos cliques) | Menu de contexto no action plan |
| 31 | Anon · board | (Y) Concorrentes têm um botão que insere o valor da data atual, bem direto | Botão "inserir hoje" no update |
| 4 | Omar · board | (New US) Mudar a cor do dia no update mode só clicando na data | No update, clicar no dia do calendário cicla o status/cor |
| 16 | Vince · board | (?) No update, arrastar o target de um dia com a "mãozinha"; CTRL + arrastar aplica ao período todo | Target arrastável por datapoint (+ atalho p/ período) |
| 6 | Omar · batchModal | (New US) No upload de Excel permitir qualquer frequência (hoje só diário) | Seletor de frequência no import |
| 26 | Vince · board | (?) Deixar o Defect mais visual: ícone/título/total à esquerda, status com números à direita. Ver Fabriq | Redesenhar o cabeçalho do Defect Tag |
| 36 | Anon · board | (?) Clicar deveria abrir pela linha inteira do registro, não só pelo N° (ex.: DFT-150) | Linha inteira clicável |
| 24 | Vince · board | (?) Ícone com nº de comentários não lidos no feed do widget (por usuário) | Badge de não lidos no feed |
| 27 | Vince · board | (?) Ao passar o mouse num alerta Andon, mostrar preview das regras do Andon | Tooltip com as regras do Andon |
| 10 | Vince · apPlanTable | (?) Trocar a coluna para "DUE DATE" para bater com o campo do action plan | Renomear "Expected date" → "Due date" |
| 9 | Vince · board | (?) Nome da sala em negrito em cima (mais importante) e o DOB-xxx menor embaixo | Ajustar hierarquia do cabeçalho da sala |
| 17 | Vince · fullModal | (N) Por que Feed antes do Action Plan? Listar a ação mais comum primeiro | Reordenar abas (Action Plan primeiro, se for o mais usado) |
| 28 | Vince · board | (N) Ícone padrão à esquerda do título de cada widget (toggle nas config) | Ícone opcional por widget |
| 7 | Omar · fullModal | (N) Poder adicionar um texto/comentário ao lado da barra | Anotação por datapoint |
| 15 | Vince · board | (?) Ao passar o mouse num valor, mudar levemente a cor da barra (feedback) | Highlight da barra no hover |
| 11 | Vince · doc:edit | (N) Redimensionar só a largura (lateral) ou só a altura (base) | Handles de resize lateral e inferior |
| 19 | Vince · board | (N) Usar os 3 gestos: clique = zoom, duplo = update, direito = editar | Mapear clique/duplo/direito |
| 25 | Vince · doc:edit | (N) Entrar na config (Edit) com duplo clique | Duplo clique abre a configuração |
| 20 | Vince · board | (N) Duplo clique no título da sala/board = renomear (como no Excel) | Rename inline por duplo clique |
| 21 | Vince · doc:edit | (?) Multi-seleção fora do padrão: SHIFT+clique = intervalo, CTRL+clique = alternar | Ajustar a multi-seleção ao padrão |
| 22 | Vince · board | (New US) Arrastar um action plan criado por engano para um indicador (long-click + drag), animação "+1 action plan", atualiza a origem | Drag-and-drop de action plan para indicador |
| 29 | Vince · doc:edit | (?) No edit + multi-seleção, clique direito → "Put into a container" (widgets vizinhos) com cor de fundo e nome | Agrupar widgets num container |
| 42 | Anon · board | (N) No topo: data atual + calendário para voltar no tempo e ver o layout do DoB em dias anteriores | Navegação temporal do board |
| 38 | Anon · board | (?) Os botões aqui estão pequenos | Aumentar área/tamanho dos botões |

---

## 🟢 Baixa / já resolvido

| Nº | Autor · Local | Comentário (PT) | Situação |
|----|----|----|----|
| 32 | Anon · board | (?) Números e círculos do calendário muito pequenos, difícil ver datas | ✅ **Já feito** — calendário agora responsivo e maior |

---

## Resumo

- **Total:** 42 · **🔴 Alta:** 8 · **🟡 Média:** 33 · **🟢 Baixa/feito:** 1
- **Bugs a investigar (prioridade máxima):** #37, #39, #40, #41.
- **Pedido recorrente (2x):** fechar o zoom clicando no fundo (#18, #35) — rápido de fazer.
- **Referência citada pelo CS:** "Fabriq" (#13, #26, #33) para inspiração visual/informacional.
- **Já contemplado no protótipo:** #32 (calendário responsivo); #14 (filtros de período já existem no zoom — falta levar ao board).

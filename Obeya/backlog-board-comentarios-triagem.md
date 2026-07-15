# Digital Obeya — Board · Triagem dos comentários (pinos de revisão)

**Fonte:** camada de revisão ao vivo (Firestore `rv_comments/obeya_board_v1`). **61 comentários abertos** (não resolvidos), mapeados ao widget onde o pino foi colocado (via posição x/y sobre o canvas 2200×4140).
Legenda de criticidade: 🔴 Alta (bug / comportamento errado vs produto / regressão) · 🟡 Média (UX / padronização / visual) · 🟢 Baixa (dúvida / decisão de PO / dependência externa).
Textos originais foram interpretados (estavam com muitos erros de digitação).

---

## 🔴 Alta

| # | Widget (pino) | O que foi dito | Solução proposta |
|----|----|----|----|
| 197 | Schedule On Time | "Down/Up é só no modo Update. Tem outro download aqui que é o **download da base**. Revisar todos." | Definir 2 ações distintas: **Import/Export (up/down)** só no Update, acima do widget; **Download da base** como ação separada no zoom. Hoje só removi o Upload do zoom — falta criar o "download da base" e padronizar em todos. |
| 235 | Production Plan | "Não é assim que funciona o status. Temos **checkbox com cores só em tabela**." | Rever o widget **Line Status** (semáforo) e o status em tabelas: usar checkboxes coloridos em tabela conforme o produto real (confirmar o comportamento esperado). |
| 247 | Production Calendar | "Cortando ícones." | O rodapé do calendário está com ícones cortados. Remover os ícones do rodapé do calendário (como fiz nos registros) ou ajustar a altura para não cortar. |
| 248 / 249 | Records | "Por que esse widget tem **borda em update mode**?" | Records (tabela pura) não deveria receber a borda de "editável" (`up-editable`) no update. Remover a borda de datapoint das tabelas puras. |
| 256 | Schedule On Time | "Não faz sentido esse ícone de editar, só toma espaço. Já tem a borda para isso." | Remover o ícone/lápis de editar no update mode; manter só a borda como indicação de editável. |
| 263 | Absenteism | "Ficou minúsculo o gauge." | **Regressão** do meu ajuste de fit. Rebalancear o gauge para ocupar melhor o card (aumentar sem estourar o rodapé). |
| 264 / 266 | RCA 1-pager / Records | "A ideia é boa, mas não faz sentido o texto quase todo cortado." | Permitir 2 linhas / aumentar a área de texto dos cards RCA e linhas de Records para não truncar demais. |
| 268 | Defect Tags | "Não é assim o calendário de etiqueta." | Rever o **calendário do Defect** (meu #212 não bate com a lógica real de etiquetas) — confirmar o formato esperado. |
| 269 / 271 / 272 / 273 | Defect (Safety Briefing / Incident / Defect Tags) | Kanban de etiquetas: "não adicionamos assim abaixo", "não são esses os status", "padronizar com action plan", "mostrar as fotos". | Refazer o **kanban do Defect**: status corretos das etiquetas, disposição igual ao kanban de AP, sem o "+ Add" embaixo, e miniatura de foto nos cards. |
| 287 | Defect Tag - Kuka | "Algumas cores erradas dos status." | Corrigir o mapeamento de cores dos status do Defect. |
| 291 | Defect Tag - Kuka | "Barra de target muito diferente (até a cor) do board." | Padronizar a barra/linha de target do Defect com a dos gráficos do board. |
| 297 | Kanban de Action Plan | "Não são essas as colunas do kanban de planos de ação." | Usar as colunas corretas do kanban de AP (confirmar quais são as oficiais). |
| 303 | Checklist | "Checklist tem funcionamento diferente, checar." | Rever o widget de Checklist conforme o produto (ligado a #218) + completar padronização (falta totalizador e filtro). |

---

## 🟡 Média

### Tooltips (padronizar em todos)
| # | Widget | O que foi dito | Solução |
|----|----|----|----|
| 131 | KPI radar | Falta tooltip | Adicionar tooltip nos pontos do radar. |
| 132 | Records | Tooltips fora do padrão | Padronizar (mesmo estilo dos demais). |
| 139 | Non Conformity Shift 3 | Tooltip deveria ter o tamanho exato do nome | Ajustar largura do tooltip ao conteúdo. |
| 141 | Non Conformity Shift 2 | Tooltip com % que não faz sentido | Mostrar % só quando fizer sentido. |
| 227 | Productivity Trend | Faltam tooltips nos datapoints | Adicionar tooltip. |
| 228 | Units Today | Falta tooltip Actual e Target | Adicionar Actual/Target. |
| 229 | Safety Pyramid | Faltam tooltips | Adicionar tooltip. |
| 246 | Safety Incidents | "O que é a % entre parênteses? Revisar todos" | Rever o significado/uso da % no tooltip em todos. |
| 260 | Production Calendar | Tooltips fora do preto padrão | Padronizar cor do tooltip (#1c2434). |

### Kanban / Action Plan
| # | Widget | O que foi dito | Solução |
|----|----|----|----|
| 160 | Kanban | Temos outras visualizações no kanban | Prever outras views. |
| 164 | Kanban | "A gente não muda status aqui (veja colunas)" | Não trocar status inline — status vem da coluna. |
| 167 | Kanban | Faltam itens | Revisar itens/colunas. |
| 262 | Action Plan | "Conferir o kanban; padronizar os cards" | Padronizar os cards do kanban. |
| 298 | Action Plan | "Precisa ser mais largo" | Alargar o modal/cards do kanban. |
| 171 | Action Plan | "Os 3 pontinhos precisam de modal?" | Kebab dos itens abre modal de ação. |
| 186 | Action Plan | "1 linha só para caber mais planos" | (parcial: compactei) avaliar layout 1-linha. |
| 299 | Team messages (batch) | "Item Area não tem" | Incluir campo **Area** no modal de lote. |
| 300 | Action Plan (batch) | "Já trazemos algumas linhas em branco?" | Confirmar/abrir com linhas em branco (hoje abre com 3). |

### Visual / padronização
| # | Widget | O que foi dito | Solução |
|----|----|----|----|
| 136 | Action Plan | Aumentar o número da bolinha | Aumentar a fonte do contador (`.apcount`). |
| 165 | Presence / tabela | Cabeçalho em MAIÚSCULO | Uppercase nos cabeçalhos de tabela. |
| 187 | Agenda | Modal flutuante entre bordas | Rever o zoom/modal da agenda. |
| 261 | Incident Shift 1 | Espaço não aproveitado | Aproveitar melhor a área do gráfico. |
| 283 | Container (Quality split) | Difícil sair da edição do nome | Enter / clique-fora confirma e sai. |
| 288 | Feed (Line Logbook) | Textos do feed maiores que o resto | Alinhar tamanho de fonte. |
| 301 | Share | Botão fora de padrão | Padronizar o botão share (ligado a #182). |
| 239 / 240 / 241 / 242 | Line Logbook / AP / Defect | "Size do quê? Color do quê? Diferente por seleção; botões inconsistentes" | Clarear labels da barra de edição por tipo de seleção e padronizar os botões. |

---

## 🟢 Baixa (dúvidas / decisões de PO / dependências)

| # | Widget | O que foi dito | Encaminhamento |
|----|----|----|----|
| 135 | Quality split | "O que quer dizer on target?" | Esclarecer label. |
| 175 | Units/indicador | "O 100% é bem maior que o 100% real" | Confirmar se é fonte ou proporção. |
| 180 | Incident Shift 2 | "Fechar qual padrão de barras" | **Decisão de PO.** |
| 191 | Presence | "Qual o critério de ordenação?" | Definir critério. |
| 244 | Line Logbook | "O que fazemos com KAI?" | Definição de produto. |
| 170 | — | "Preciso das telas da Fabriq" | **Dependência externa.** |
| 218 | Checklist | "Não tem zoom (ok) + existe 'analytics'" | Zoom já removido; definir o "analytics". |
| 293 | Criação de sala | "Se confidencial deveria abrir visitante" | Regra de convidados ao marcar confidencial. |
| 294 | Presence | "Por que já vem preenchido em board novo?" | Default da presença em board novo. |
| 295 | — | "Não acho que seja 0 o default" | Rever valor default. |
| 296 | — | "Não faz sentido isso com toggle?" | Rever controle (toggle). |
| 169 | Team messages | "Fica minimizada até incluir?" | ✅ Minimizar já implementado. |
| 155 | Container | "Confirmação ao apagar container" | ✅ Já implementado. |

---

## Resumo
- **13 itens 🔴 Alta** — a maioria concentrada em **Defect (kanban/calendário/cores/target)**, **tabelas em update (borda/ícone de editar)**, **regressões (gauge do Absenteism)** e **regra de download/upload (#197)**.
- **~26 itens 🟡 Média** — grande bloco de **tooltips** (padronizar em todos) + refinos de **kanban** e barra de **edição**.
- **~13 itens 🟢 Baixa** — dúvidas e decisões de PO (não codar antes de fechar).

**Sugestão de ataque:** 1) Defect (kanban/calendário/cores) — maior bloco crítico; 2) tabelas em update (borda/ícone #248/#249/#256); 3) gauge Absenteism (#263); 4) padronização de tooltips (#131/227/228/229/246/260…); 5) regra de download/upload (#197).

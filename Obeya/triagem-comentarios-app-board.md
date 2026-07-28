# Triagem de comentários abertos — App + Board

Fonte: camada de revisão (Firestore `rv_comments`). **92 comentários abertos** — `obeya_app_v1` (obeya.html): 37 · `obeya_board_v1` (obeya-board.html): 55.
Criticidade: 🔴 Alta (bug / comportamento errado) · 🟡 Média (UX / padronização / feature) · 🟢 Baixa (dúvida / decisão de PO).
✅ = já implementado no código (só voltou a "aberto" no Firestore porque a página ao vivo sobrescreveu; precisa re-resolver).

---

## obeya.html (app) — 37 abertos

### 🔴 Alta (9)
| # | Tela | O que foi dito | Solução proposta |
|---|---|---|---|
| 3 | Add user (modal) | Droplist de nome abre rolagem estranha / "não abre nada" | Corrigir o multiselect de usuários: abertura + overflow/scroll do modal |
| 4 | Add user (modal) | Droplist de usuários fora do padrão / não abre | Reconstruir droplist no padrão (multiselect com avatares) e garantir abertura |
| 35 | Action plans | Filtro com bug / "cadê os outros filtros?" | Corrigir o filtro e trazer os demais filtros no padrão |
| 57 | Criar sala (wizard) | Toast fica atrás da tela | Ajustar z-index do toast acima do modal |
| 62 | Criar sala (wizard) | Não dá para trocar de foto na galeria de templates | Corrigir a troca de foto/seleção na galeria |
| 63 / 64 | Action plans | "In Approval" e "Completed" com a mesma cor | Cores distintas para cada status |
| 68 | Action plans | Ao clicar em editar abre um toast que não existe | Corrigir ação de editar (remove toast fantasma / abre edição real) |
| 72 | Action plans | Cores de "In Approval" e "Completed" invertidas | Corrigir o mapeamento de cores |

### 🟡 Média (22)
| # | Tela | O que foi dito | Solução proposta |
|---|---|---|---|
| 8 | Settings › Notif | Ícone estranho (ref. ícones do KC) | Padronizar o ícone conforme KC |
| 11 / 49 | Criar sala (modal) | Favorito deveria ser estrela | Usar ícone de estrela no favorito |
| 12 / 50 | Criar sala (modal) | Se confidencial, abrir seleção de visitantes | Ao marcar confidencial, abrir droplist de visitantes (igual board #293) |
| 18 / 52 / 55 | Criar sala / wizard | Visitantes podem ser Áreas e Times também | Permitir Áreas/Times além de usuários |
| 23 | Room search | Título em negrito muito pesado (visão card); pensar cross-módulo | Reduzir peso tipográfico do título do card |
| 25 | Room search | Thumb parece largo demais (foto paisagem) | Ajustar thumbnail ao padrão de foto paisagem |
| 33 / 54 | Action plans / rooms | Padronizar ícones (ref. KC) | Padronizar ícones conforme KC |
| 45 | Room search | Vai mudar padrão de todos os filtros? Faltam filtros | Definir/alinhar o padrão de filtros |
| 46 | Room search | Cabeçalho diferente do KC | Alinhar cabeçalho ao KC |
| 47 | Criar sala (modal) | Faltam ícones/avatares nos usuários | Adicionar avatares |
| 48 | Criar sala (modal) | Faltam marcadores de campo obrigatório | Marcar obrigatórios (asterisco/bolinha) |
| 51 | Criar sala (modal) | Precisa mais de 1 dono | Owner como multiselect |
| 53 | Room search | Barra inferior fora do padrão fechado | Ajustar a floating bar ao padrão |
| 58 | Criar sala (wizard) | Campo faltando deveria ter msg abaixo | Validação inline (mensagem sob o campo) |
| 67 | Action plans | Não precisa de "view"/ícone de plano de ação | Remover o elemento indevido |
| 70 | Action plans | Cards deveriam ter kebab (3 pontinhos) com submenu | Adicionar kebab com submenu nos cards |
| 73 | Action plans | Faltam alternadores de visão calendário/kanban | Adicionar toggle de visões |

### 🟢 Baixa — dúvida / decisão de PO (6)
| # | Tela | O que foi dito |
|---|---|---|
| 56 | Wizard | "Vai ser esse padrão? (pensa nos registros)" |
| 60 | Wizard | Qual valor no hover da miniatura do template? |
| 66 | Action plans | "Não é claro assim, certo?" |
| 71 | Action plans | "amarelo" (nota de cor, vago) |
| 75 | Settings › Notif | "Temos esse indicador assim?" |
| 76 | Dialog | "Vide padrão" |

---

## obeya-board.html (board) — 55 abertos

### 🔴 Alta — pendente (8)
| # | Tela | O que foi dito | Solução proposta |
|---|---|---|---|
| 197 | Board | Down/Up é só no Update; existe outro "download da base" (rever todos) | Separar Import/Export (update) do "Download da base"; padronizar em todos |
| 316 | Update mode | Não dá para alterar cores no update | Habilitar edição de cor no update |
| 317 | Update mode | Ao inserir linha, abre desformatada | Corrigir formatação da nova linha |
| 326 | Criar sala (modal) | Droplists de seleção travados | Corrigir os droplists |
| 330 | Defect kanban | Ordem das colunas errada | Corrigir a ordem das colunas |
| 331 | Defect kanban | Cores dos status de etiqueta erradas | Corrigir o mapeamento de cores |
| 336 | Presença | Ordem dos dias invertida | Inverter a ordem dos dias |
| 338 | Board | Atalhos 7D/14D… não abrem o nº certo de dias | Corrigir os atalhos de período |

### 🔴 Alta — já feito ✅ (2)
| # | Tela | O que foi dito | Status |
|---|---|---|---|
| 287 | Defect | Cores erradas dos status | ✅ corrigido |
| 297 | AP kanban | Colunas erradas do kanban de AP | ✅ corrigido |

### 🟡 Média — pendente (18)
| # | Tela | O que foi dito | Solução proposta |
|---|---|---|---|
| 160 | AP kanban | Temos outras visualizações no kanban | Prever outras views |
| 167 | AP batch | Faltam itens | Rever itens/colunas do batch |
| 239 / 240 / 241 / 242 | Edit toolbar | "Size/Color do quê?", muda por seleção, botões inconsistentes | Clarear labels por tipo de seleção e padronizar botões (precisa print do app) |
| 291 | Full (widget) | Barra de target diferente (até a cor) do board | Padronizar a barra de target |
| 307 | Board | Zoom deveria abrir sempre maior; modal igual ao daqui | Padronizar o tamanho/modal do zoom |
| 315 | Defect calendário | Calendário pequeno no modal | Ajustar tamanho do calendário ao modal |
| 318 | Update mode | Poder escolher inserir linha acima/abaixo | Opção acima/abaixo |
| 320 | Board | Faltam tooltips nas barras | Adicionar tooltips |
| 321 | Update mode | Ícones deixam a linha muito alta | Reduzir altura da linha |
| 323 | AP batch | Deveria parecer com a tela do IS | Alinhar layout ao padrão IS |
| 327 | Board | Tooltips fora do padrão | Padronizar tooltips |
| 329 | Defect kanban | Modo mostrar/não mostrar foto | Toggle de foto nos cards |
| 332 | Galeria widget | Faltam ícones e textos | Adicionar ícones+labels |
| 333 | Full (widget) | Links não aparecem no update | Mostrar links no update |
| 340 | Full (feed) | 2 filtros não fazem sentido; convergir | Unificar os filtros |

### 🟡 Média — já feito ✅ (11)
| # | O que foi dito | Status |
|---|---|---|
| 139 | Tooltip do tamanho do nome | ✅ |
| 155 | Confirmação ao apagar container | ✅ |
| 229 | Faltam tooltips | ✅ |
| 261 | Espaço não aproveitado (gráfico) | ✅ |
| 283 | Difícil sair da edição do nome do container | ✅ (Enter/✓/✕) |
| 288 | Fonte do feed maior que o resto | ✅ |
| 298 | Modal batch mais largo | ✅ |
| 301 | Botão share fora de padrão | ✅ |
| 303 | Checklist funciona diferente | ✅ (analytics) |
| 319 | Usar "." e não "," | ✅ pivot (verificar demais widgets) |
| 322 | Botão deveria ser "Incluir" | ✅ |

### 🟢 Baixa — dúvida / decisão de PO (6)
| # | Tela | O que foi dito |
|---|---|---|
| 135 | Board | O que quer dizer "on target"? |
| 191 | Board | Qual o critério de ordenação? |
| 265 | Board | Como abre o filtro? |
| 294 | Novo board | Por que a presença já vem preenchida? |
| 300 | AP batch | Já trazemos linhas em branco? |
| 339 | Full (feed) | O que abre nos 3 pontinhos do feed? |

### ⚪ Pinos em branco (10) — sem texto
#334, #341, #342, #343, #344, #345, #346, #347, #348, #349 → revisar/apagar (sem conteúdo).

---

## Resumo
- **App (37):** 9 🔴 (a maioria bugs em modais — droplists de usuário, toast atrás do modal, galeria de templates, cores de status em Action plans) · 22 🟡 (padronização com KC, favorito=estrela, confidencial→visitantes, filtros, kebab nos cards) · 6 🟢.
- **Board (55):** 8 🔴 pendentes + 2 ✅ · 18 🟡 pendentes + 11 ✅ · 6 🟢 · 10 pinos em branco. **13 itens já estão implementados** — só precisam ser re-marcados como resolvidos.
- **Ataque sugerido:** 1) bugs de modal no app (#3/#4/#57/#62/#68); 2) cores de status Action plans (#63/#72); 3) bugs de update mode no board (#316/#317/#326/#330/#331/#336/#338); 4) padronização KC/ícones/filtros no app; 5) re-resolver os 13 ✅ e limpar os 10 pinos em branco.

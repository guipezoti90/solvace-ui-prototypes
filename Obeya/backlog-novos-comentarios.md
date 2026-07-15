# Obeya — Novos comentários (rodada pós-deploy) por prioridade

**Fonte:** camada de revisão ao vivo (Firestore). **Work board** (`rv_comments/obeya_board_v1`): 116 comentários, **novos #128–243** (Renato + anônimos). **CS** (`rv_comments/obeya_board_cs`): novos **#44–52**.
**Contexto:** é majoritariamente feedback sobre o que acabou de subir (container, kanban fullscreen, target arrastável, hover, calendário) + uma varredura de consistência entre widgets.
Legenda: 🔴 Alta (bug/bloqueio/consistência central) · 🟡 Média (UX/visual/padronização) · 🟢 Baixa (dúvida/label/ajuste fino).

---

## 🔴 Alta

| # (coment.) | Tema | O que foi dito | Solução proposta |
|----|----|----|----|
| 197, 192, 194, 196, 198, 199, 200, 202, 203, 207, 211, 218, 224, 231, 232 | **Padronizar download/upload/zoom em TODOS os widgets** | "Down/Up é só no modo Update; tem outro download que é o da base (rever todos os widgets)"; vários widgets sem zoom (mensagem, RCA, defeito, registro, time, analytics); outros com down/up onde não deveria | Definir e aplicar a regra única: **zoom em todo widget**; **import/export (up/down) só no Update**; **download-da-base** como ação separada e padronizada. Passar widget a widget corrigindo. |
| 45 (CS) | **Bug: batch update em tela cheia** | "updating widgets in full screen mode doesn't work" | Investigar o fluxo de batch no fullModal (Apply/captura das células) e corrigir a gravação. |
| 179 | **Bug: Stop da agenda** | Clicar em Stop (mesmo sem ter iniciado) abre o sumário; deveria estar desabilitado | Desabilitar Stop enquanto a reunião não começou; só habilitar após Play. |
| 133, 134, 224, 225 | **Widget Registro (Records)** | Não tem edição; não tem zoom; falta link no registro | Tornar Records editável no Update + abrir no zoom + adicionar link do registro (padrão dos demais). |
| 162, 208, 221, 223 | **Botão "+ Adicionar" faltando** | Cadê o botão de adicionar plano (kanban) e de adicionar no modo reunião | Incluir ação "+" no kanban de Action Plan e nos widgets em modo reunião. |

---

## 🟡 Média

### Refinamentos das features recém-lançadas
| # | Tema | O que foi dito | Solução |
|----|----|----|----|
| 147 | Container (#29) | Como muda o título e a **cor de fundo** do container? | Deixar o título editável mais óbvio + adicionar seletor de cor de fundo do container. |
| 155 | Container (#29) | Colocar **confirmação ao apagar** container | Diálogo de confirmação no X do container. |
| 157, 163 | Kanban fullscreen (#2) | Sobra muito espaço em cima; precisa ser mais largo | Reduzir o topo do kanban e ampliar a área útil. |
| 158, 159, 160, 161, 164 | Kanban | Cards de AP iguais aos do board; filtros no topo; outras visualizações; upload/download; "não muda status aqui" | Alinhar cards ao padrão do board; barra de filtros; remover troca de status inline (usar colunas). |
| 49 (CS) | Target arrastável (#16) | Os "pontinhos" ficaram estranhos; deixar mais discretos (preto, bolinhas menores) | Reduzir/escurecer as alças de target (`.mb-tgt`). |
| 51 (CS) | Hover atalhos | O hover foi feito mas não ficou evidente | Reforçar o realce no hover (contraste/animação da barra). |
| 46 (CS) | Calendário | Poder definir **em que dia da semana o calendário começa** | Opção de "início da semana" na config do calendário. |
| 47 (CS) | Calendário (#) | Ao clicar nos dias, questiona o popup que abre | Validar/ajustar o editor de datapoint do dia (recém-adicionado). |

### Tooltips
| # | O que foi dito | Solução |
|----|----|----|
| 176, 177, 227, 228, 229, 131, 141 | Tooltips faltando em datapoints; formato deve ser **dd/mm/aaaa**; rótulos **Actual e Target**; % sem sentido; padronizar em todos os widgets | Padronizar o tooltip (data completa + Actual/Target + %) e garantir em todos os datapoints/widgets. |

### Rodapé / consistência de widgets
| # | O que foi dito | Solução |
|----|----|----|
| 209, 210, 212, 234 | "Não tem essas coisas no rodapé" (defeito, time e outros) | Levar o rodapé informativo (dono/planos/comentários — #13) aos demais widgets grandes. |
| 204 | Zoom do widget de mensagem deveria ser bem maior | Ampliar o zoom do widget de mensagens. |
| 233, 236, 238 | Espaço branco: widget Time, **Room Settings** (ainda), widget de edição | Revisar alturas/paddings (Room Settings segue com sobra na tela do revisor). |

### Layout / dados
| # | O que foi dito | Solução |
|----|----|----|
| 173 | Ícone é alerta de plano atrasado, não Andon | Corrigir tooltip/semântica do ícone. |
| 175 | O 100% aqui é bem maior que o 100% real | Ajustar a escala do indicador. |
| 183 | Ao redimensionar não deveria aumentar o espaçamento (inferior tb) | Manter espaçamento fixo no resize. |
| 186 | 1 linha só por plano para caber mais na tela | Compactar linhas do Action Plan. |
| 215 | Foto quebrando a tabela (lógica de UI errada) | Rever layout de tabela com foto (não quebrar a linha). |
| 235 | Status não funciona assim — checkbox com cores só em tabela | Rever o widget de Status conforme o comportamento real. |
| 235, 239, 240, 241, 242 | Barra de edição: "Size do quê?", "Color do quê?", botões diferentes por seleção | Clarear rótulos e padronizar a toolbar de edição por tipo de seleção. |
| 128, 129, 136 | Cor verde de fundo; fundo para o KAI; aumentar o número da bolinha | Ajustes visuais pontuais. |
| 174, 180 | Definir padrão de clique na linha; fechar padrão de barras e aplicar a todos | **Decisões de PO/UX** a fechar antes de aplicar. |
| 44 (CS) | Adicionar widget mais rápido: hover no catálogo mostra a explicação e 1 clique inclui | Simplificar o fluxo do catálogo (hover + clique único). |
| 48, 50 (CS) | Controle redundante (só precisa atualizar o "Customizado"); falta botão fechar | Remover duplicidade no filtro do zoom; adicionar botão fechar no painel indicado. |

---

## 🟢 Baixa (dúvidas, labels, ajustes finos)

| # | O que foi dito |
|----|----|
| 130, 137, 178, 201 | "Espaço sobrando", "não ficou pequeno?", alinhamento — ajustes pontuais |
| 135, 138, 140, 214, 218, 185, 205 | Dúvidas de clareza ("o que é on target / essa bolinha / esse ícone / esses botões / share / Full message") — revisar labels/tooltips |
| 139 | Tooltip do tamanho exato do nome |
| 165, 213, 191 | Cabeçalho de tabela em MAIÚSCULO; ordenação de coluna; critério de ordenação |
| 168 | Renomear botão para "Incluir" |
| 169, 171, 172, 187, 206, 219, 220, 181 | Dúvidas de fluxo (minimizar até incluir, kebab com modal, read-receipts, nome vs número) |
| 160, 166, 167 | "Outras visualizações", "esse item não tem", "faltam itens" (vagos — pedir detalhe) |
| 170 | Precisa das telas da **Fabriq** para definir (dependência externa) |
| 243 | Revisar versão **mobile** (esforço grande, planejar à parte) |
| vazios | **Pinos em branco** (#142–146, 148–154, 156, 184, 188–190, 195, 216, 217, 222, 226, 230, 237; CS #52) — limpar da camada |

---

## Resumo

- **Work board:** ~90 comentários com conteúdo + ~26 pinos em branco (limpar).
- **CS:** 8 com conteúdo (#44–51) + 1 vazio (#52).
- **Prioridade máxima (fazer primeiro):**
  1. Padronizar **download/upload/zoom** em todos os widgets (regra do #197) — maior bloco.
  2. **Bug** batch update em tela cheia (CS #45).
  3. **Bug** Stop da agenda abrindo sumário (#179).
  4. **Records** editável + link + zoom (#133/134/224/225).
  5. Botão **"+ adicionar"** (kanban e modo reunião).
- **Decisões de PO a fechar antes de codar:** padrão de clique na linha (#174), padrão de barras (#180), telas da Fabriq (#170).
- **Refino rápido das features novas:** target dots mais discretos (CS#49), hover mais evidente (CS#51), confirmação ao apagar container (#155), título+cor do container (#147).

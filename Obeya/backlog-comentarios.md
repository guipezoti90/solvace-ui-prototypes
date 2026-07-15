# Obeya — Backlog de comentários sem tratativa

**Fonte:** camada de revisão (Firestore `rv_comments/obeya_board_v1`) — leitura ao vivo do board publicado.
**Situação:** 64 comentários no total → **62 abertos** (com texto) + 2 em branco. Nenhum está marcado como *Resolved* na ferramenta, por isso **todos** constam como "sem tratativa". O campo **Status** abaixo reflete o que já foi implementado no código (a validar/“fechar” na camada) vs. o que segue pendente.

Legenda de status: ✅ implementado (validar e marcar resolvido) · 🔧 pendente · ⚠️ depende de definição/PO

---

## 🔴 Alta — quebra de funcionamento ou fluxo central

| Nº | Local | Comentário | Solução proposta | Status |
|----|-------|------------|------------------|--------|
| 17 | Agenda (meetModal) | Planos não funcionam em lista; precisa formato grade/tabela para editar rápido e subir em batch | Substituir a lista de planos por **tabela editável** estilo *batch update* (edição inline, múltiplas linhas, botão “subir em batch”) | 🔧 |
| 119 | Agenda (meetModal) | Planos precisam de grade (mesmo ponto do #17) | Mesma tabela editável do #17 | 🔧 |
| 90 | Widget ampliado (fullModal) | No **update mode** essa não é a tela; deveria ser uma tabela só daquele widget | No update, o modal lateral do widget ampliado = **tabela editável** (batch-style) apenas daquele widget | 🔧 |
| 77 | Edição (editModal) | A aba **Related Widget** não funciona assim | Redesenhar a aba conforme o comportamento real (mapear regra com PO) | 🔧 |
| 78 | Edição (editModal) | A aba **Andon** não funciona assim | Redesenhar a aba Andon conforme a regra real de Andon | 🔧 |
| 47 | Batch (batchModal) | Colunas mais estreitas, “3 pontinhos” (kebab) nos títulos e ícone de **tela cheia** | Ajustar grid de colunas + menu kebab por coluna + botão de fullscreen para preencher mais espaço | 🔧 |
| 49 | Batch (batchModal) | Não faz sentido ter a coluna **Result** aqui | Remover a coluna Result do batch | 🔧 |
| 15 | Agenda (meetModal) | Falta ação de **excluir** | Botão de excluir (reunião/plano) com confirmação | 🔧 |
| 18 | Action Plan batch (apBatchModal) | Modal vai precisar ser **mais largo** | Aumentar a largura do modal de batch | 🔧 |
| 115 | Board (update) | Ao clicar na barra no update, abrir para atualizar **somente aquele datapoint** | Clique no datapoint → mini-editor do valor daquele ponto | 🔧 |
| 91 | Board (update) | Update mode deveria permitir **editar esse ícone** | Tornar o ícone editável no update | 🔧 |
| 123 | Widget ampliado (fullModal) | Falta a parte de **Upload** | Adicionar seção de upload no modal | 🔧 |

---

## 🟡 Média — padronização, fidelidade visual e overflow

| Nº | Local | Comentário | Solução proposta | Status |
|----|-------|------------|------------------|--------|
| 61 | fullModal | Letras parecem maiores que as do quadro | Igualar tamanho de fonte ao do board | 🔧 |
| 124 | fullModal | Letras parecem muito grandes | Reduzir fonte para casar com o quadro | 🔧 |
| 63 | fullModal | Padronizar **Planos de Ação** com o quadro | Alinhar layout da seção ao padrão do board | 🔧 |
| 64 | fullModal | Padronizar **RCA** com o quadro | Alinhar layout do RCA ao padrão | 🔧 |
| 67 | fullModal | Padronizar **Projetos** com os demais | Alinhar layout de Projetos | 🔧 |
| 68 | fullModal | Para que essa 2ª linha? | Remover a 2ª linha (subtítulo redundante) | 🔧 |
| 71 | editModal | Para que a segunda linha? | Ocultar subtítulo redundante (ligado ao #84) | 🔧 |
| 44 | Board | Mostrar como fica quando estoura (rolagem interna como presença, ou paginação) | Rolagem interna/paginação no overflow | ✅ (presença/tabelas) — validar nos demais |
| 79 | Board (edit) | O cabeçalho do widget na edição fica por cima e não rola junto ao chegar no topo | Header **sticky** dentro da área de edição | 🔧 |
| 108 | Board (edit) | Aproveitar melhor os espaços laterais para caber mais tópicos na altura | Revisar grid/colunas laterais | 🔧 |
| 86 | Board | Widget maior deveria ter **ícone de filtros** (não o customizado) | Ícone de filtro padrão em widgets grandes | 🔧 |
| 76 | editModal | Ficou confusa a aba de **Link** | Simplificar/clarear a aba Link | 🔧 |
| 74 | editModal | Definir depois o que vai em cada seção por widget | Mapear conteúdo por tipo de widget | ⚠️ |
| 116 | Board | Tooltip da pessoa fora do padrão | Padronizar tooltip de avatar (nome + cargo) | 🔧 |
| 9 | Board | Salas deveriam estar em ordem | Ordenar o seletor de salas | 🔧 |
| 31 | Board | Oferecer 1 gráfico com **eixo Y** (opção que temos) | Adicionar variação com eixo Y na paleta | 🔧 |
| 32 | Board | Oferecer 1 gráfico com **linha de target** (opção que temos) | Adicionar variação com target na paleta | 🔧 |
| 92 | Board | Fazer ícones novos de **Pizza** e **Spider** chart | Criar os 2 ícones | 🔧 |
| 111 | Board | Testar as barrinhas propostas pela OSEDEA lado a lado | Protótipo comparativo das barras | ⚠️ |
| 132 | Board (edit) | A foto nunca deveria abrir assim | Rever o lightbox/abertura da foto | 🔧 |
| 133 | Board (edit) | O fundo da galeria está apagado e confunde com a tela | Aumentar contraste do fundo da galeria | 🔧 |
| 118 | Board | Ganhar espaço aqui para caber mais itens da agenda | Compactar itens da agenda | 🔧 |
| 127 | Board | Os números deveriam aumentar também | Escalar os números junto com o widget | 🔧 |
| 138 | Board | Números ficaram ilegíveis | Ajustar tamanho/contraste dos números | 🔧 |
| 137 | Board | O que é esse número? | Adicionar label/legenda ao número | 🔧 |
| 126 | Board | Falta o **link do registro** | Adicionar link para o registro | 🔧 |
| 125 | Board | Colocar o **sobrenome** da pessoa | Exibir nome + sobrenome | 🔧 |
| 128 | Board | Colocar cor verde de fundo | Aplicar fundo verde no elemento | 🔧 |

---

## 🟢 Baixa — ajuste fino, dúvida ou já implementado

| Nº | Local | Comentário | Solução proposta | Status |
|----|-------|------------|------------------|--------|
| 16 | meetModal | “Daily?” (dúvida sobre recorrência) | Confirmar recorrência e expor seletor (daily/semanal…) | ⚠️ |
| 102 | Board | “Não ficou muito espaço não?” | Reduzir espaçamento no ponto indicado | ⚠️ |
| 117 | Board | Não gostou da linha serrilhada/pontilhada | Trocar por linha sólida sutil | 🔧 |
| 131 | Board (edit) | Falta espaçamento na outra direção | Ajustar gap vertical | 🔧 |
| 139 | Board | Seria legal deixar mover isso também | Tornar o componente arrastável | 🔧 |
| 114 | Board | Ver se dá pra fazer esse componente móvel | Componente móvel | ✅ (barra de zoom/update já é móvel) |
| 8 | Board | Falta tooltip do usuário | Tooltip no avatar | ✅ |
| 10 | Board | Tooltip do nome da sala quando estourar | Tooltip no nome truncado | ✅ |
| 27 | Board | Falta tooltip | Tooltip no elemento | ✅ |
| 45 | Board | Tooltip da série | Tooltip por série | ✅ |
| 11 | Board | Mostrar o target (com uma linha) | Linha de meta no gráfico | ✅ |
| 23 | Board | Esse texto é só um link, não precisa | Remover texto, manter só o link | ✅ |
| 38 | Board | Textos do cabeçalho muito claros | Escurecer textos do cabeçalho | ✅ |
| 101 | Board | Falta um tracinho separando zoom do update mode | Separador (cor escura de contraste) | ✅ |
| 122 | Board | O ícone de transcript era do KAI, não? | Logo KAI no transcript | ✅ |
| 84 | Board (edit) | Subtítulo não deveria vir por default ao adicionar widget | Subtítulo off por default + toggle | ✅ |
| 69 | editModal | Difícil ver qual texto é de qual aba | Clareza/identificação das abas | ✅ |
| 70 | editModal | “Edit NOME DO WIDGET” | Título dinâmico com o nome do widget | ✅ |
| 72 | editModal | Negrito + texto maior não bastam para quebrar em subseções | Separadores visuais de subseção | ✅ |
| 73 | editModal | Evitar nomes diferentes por botão (multilíngua) | Padronizar rótulos dos botões | ✅ |
| 129 | roomModal | Falta quebra visível entre subseções | Separador entre subseções | ✅ |

---

## Resumo

- **Total aberto:** 62 · **🔴 Alta:** 12 · **🟡 Média:** 29 · **🟢 Baixa:** 21
- **Já implementado (a fechar na camada):** ~17 (todos os ✅) — posso marcá-los como *Resolved* em lote.
- **Maior bloco pendente real:** edição/batch/update — #17, #90, #77, #78, #47, #49 (formato grade/tabela e abas que “não funcionam assim”).

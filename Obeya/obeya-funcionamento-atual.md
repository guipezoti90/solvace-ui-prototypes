# Digital Obeya — Funcionamento atual (estudo do app em produção)

Estudo feito no app real (sandbox `sandboxefeso.solvacelabs.com/digitalobeya`), sala de teste **DOB-12064 "teste ux"**, para guiar a construção da configuração no novo design.

---

## 1. Estrutura geral / navegação

- **Lista de salas** (tela inicial do Digital Obeya): tabela com colunas **N°** (DOB-xxxxx), **Sala** (nome), **Tipo**, **Membros**, **Status** (Ativo/Inativo).
  - Topo: busca ("Digite aqui…"), botão de **filtro**, botão de **favoritos** (estrela), alternância **lista/grade** e um **kebab** (⋮).
  - Cada linha tem uma estrela (favoritar) e o número da sala é um link que abre o board.
- **Board da sala** (`/digitalobeya/Board?...RoomPage|id=12064`): abre em nova aba.
  - **Topo:** logo Solvace, sino (notificações), localização ("Sandbox English"), avatar do usuário.
  - **Abas de boards** (logo abaixo do topo): cada sala tem 1+ **boards** (ex.: "Quadro"). As abas ficam à esquerda.
  - **Canvas** central (whiteboard) onde ficam os widgets, posicionáveis livremente.
  - **KAI**: avatar no canto inferior esquerdo.
  - **Barra flutuante inferior-direita:** `DOB-12064` + label **Atualizar** com toggle + **zoom** (100%, −, +) + **kebab "Mais Opções"** (⋮).

### Estados / modos
1. **Standard** (visualização).
2. **Update mode** ("Atualizar" / "Ativar modo atualização"): toggle na barra inferior. Widgets ficam editáveis para inserir/atualizar valores (ver Batch update).
3. **Edit mode**: acionado pelo **kebab → lápis**. Mostra o **grid** no canvas, habilita inserir/mover/redimensionar widgets, adicionar boards e configurar.

### Coluna de FABs (no edit mode / "Mais Opções")
O kebab inferior-direito expande uma coluna vertical de botões azuis:
- **Andon** (triângulo de alerta)
- **Reproduzir** (play-circle) — modo apresentação/replay
- **Focar/centralizar** (scan)
- **Imagem** (captura/fundo)
- **Atualizar/refresh**
- **Configurações da sala** (engrenagem)
- **Editar / Fechar** (lápis ↔ X)

---

## 2. Catálogo de widgets (26 tipos, 7 categorias)

Acessado no edit mode pelo **"+" inferior-esquerdo** → painel com **busca** + **abas de categoria** (Todos, Indicadores, Tabelas, Módulos, Reuniões, Elementos visuais, Outros). Cada item tem **miniatura de preview + nome + descrição + "+"** para adicionar.

**Indicadores**
- **Número** — Exibição de um valor numérico
- **Gráfico** — Uma ou mais séries de valor numérico em formato gráfico
- **Gráfico customizado** — Séries de valor numérico em formato gráfico (customizável)
- **Calendário** — Uma única série de valor numérico em formato calendário
- **Status** — 3 cores de status em formato de farol
- **Medidor** — Valor numérico em formato de medidor (gauge)

**Tabelas**
- **Tabela** — Tabela configurada em um criador de tabelas
- **Excel** — Exibe/edita tabelas no formato Excel (OnlyOffice)

**Módulos**
- **Registros** — Lista de registros dos módulos Solvace
- **Checks** — Lista de registros dos módulos Checklist, LIL, Assessment e Centerline
- **Tendência** — Gráfico de tendência de questões (Checklist, LIL, Centerline)
- **Defeito** — Lista de etiquetas de defeitos pendentes de um equipamento
- **Plano de Ação** — Planos de ação
- **1-pager** — Lista de registros de análise de causa raiz associados aos widgets do quadro/sala

**Reuniões**
- **Feed** — Componente de feed (mensagens, imagens e arquivos)
- **Documentos** — Criação/armazenamento de documentos office online
- **Agenda** — Lista de tópicos da reunião e controle do tempo
- **Presença** — Lista de presença de usuários em reuniões
- **Time** — Lista de membros de um time
- **Pesquisa** — Resultado de perguntas e enquetes realizadas em reuniões

**Elementos visuais**
- **Imagens** — Uma ou mais imagens ou vídeos
- **Html** — Renderização de conteúdo HTML
- **Texto** — Textos via editor de texto
- **Quadro Branco** — Ferramenta de mural colaborativa
- **Tableau** — Renderização de conteúdo Tableau

**Outros**
- **Recado** — Recados e atualizações entre membros da sala

> Adicionar = clicar no "+" do item (toast "Adicionado com sucesso"); o widget entra no canvas no tamanho padrão **180×180**.

---

## 3. Widget no board (barra de ferramentas por widget)

Ao passar o mouse / selecionar um widget no edit mode, aparece no topo do card uma barra com 4 ações + um selo de tamanho:
1. **Abrir/expandir** (ver em tela cheia)
2. **Duplicar**
3. **Configurações** (engrenagem) → abre o modal de Configurações
4. **Excluir** (lixeira)
- **Selo "180 x 180"** no rodapé do card com um lápis = **redimensionar** (tamanho em px).

---

## 4. Modal de Configurações do widget

Modal **centralizado** (título "Configurações"), com **abas no topo** e **preview do widget abaixo do formulário**:

**Abas:** `Geral` · `Avançado` · `Fonte` · `Links` · `Widgets Relacionados (n)` · `Andon`

### Aba Geral (exemplo completo: widget Número)
- **Mostrar Título** (checkbox)
- **Título** (texto)
- **Tamanho** (select: **Pequeno / Médio / Grande**)
- **Cor** (seletor de cor)
- **Casas decimais** (radio: **Sem / Uma / Duas / Três**)
- **Mostrar objetivo** (checkbox)
- **Aplicar Formatação Condicional** (checkbox) → cores **Abaixo do Objetivo / No Objetivo / Acima do Objetivo**, campo **Andon**, **Tolerância do Objetivo** (número + cor) e select de direção (**Abaixo do target / Acima do target**)
- **Formato exibição** (select: **Padrão / Reduzido**)

### Aba Fonte (origem dos dados)
- **TIPO DE FONTE** (select; só permite 1 item). Para Número = **Manual** (valor inserido na mão pelo update mode). Widgets de módulo (Registros, Checks, etc.) puxam dados das fontes Solvace.

### Outras abas
- **Avançado:** opções extras (ex.: vínculo de **Área** — 1-Safety, 2-Quality, 3-Environment, 4-Maintenance, 5-Steerco, 6-Management… — e responsáveis/usuários).
- **Links:** vínculos/links do widget.
- **Widgets Relacionados:** associação a outros widgets (contador no título da aba).
- **Andon:** configuração de andon do widget.

> O **Gráfico** (visto no Figma "Edit Chart widget") segue o mesmo padrão: Título (+toggle), Tamanho, Cor, **Type** (Per hour / Daily / Weekly / Monthly / Monthly fixed calendar), **Goals & Target** (Show target, Conditional Formatting, Below/On/Above/Andon).

---

## 5. Batch update / Update mode

- Acionado pelo toggle **"Atualizar"** (tooltip **"Ativar modo atualização"**) na barra inferior-direita.
- Com o modo ligado, os widgets ficam **editáveis** para inserir/atualizar valores (cada widget ganha um **kebab** próprio); widgets de fonte **Manual** (Número, Status, Gráfico manual, etc.) permitem digitar o valor direto.
- É o fluxo usado em reuniões para **atualizar os indicadores em lote** antes/durante a daily.

---

## 6. Configuração de Sala (engrenagem na coluna de FABs)

Modal com painel lateral (logo, **DOB-12064**, status **Ativo**) + formulário:
- **Sala** (nome)
- **Tipo** (select: Basic, Meeting board, Daily meeting, Line board, automation… — define o template/comportamento da sala)
- **Donos** (owners; ex.: Solvace Administrator)
- **Descrição** (opcional)
- **Membros** (multi-seleção de usuários)
- **Confidential** (toggle)
- **Favoritar** (estrela)
- Rodapé: **kebab → Inativar** (salas têm status Ativo/Inativo, não exclusão direta), **Cancelar**, **Salvar**.

---

## 7. Configuração de Board (aba "Quadro" → engrenagem, no edit mode)

Modal "Editar":
- **Nome** (nome do board/aba)
- **Cor de Fundo** (background do canvas)
- **Atualização Automática** (toggle) + **Intervalo em segundos**
- **Responsivo mobile** (toggle, ligado por padrão)
- Rodapé: **kebab** (mais ações, ex.: excluir board), **Cancelar**, **Salvar**.
- **Adicionar board:** botão **"+"** no canto superior direito cria um novo board (nova aba) dentro da sala.

---

## 8. Implicações para o novo design (o que falta construir)

1. **Catálogo completo de 26 widgets** com categorias (hoje o protótipo tem ~10). Cada item: preview + nome + descrição + add.
2. **Modal/drawer de Configurações** com as 6 abas (Geral, Avançado, Fonte, Links, Widgets Relacionados, Andon) — o novo design usa **drawer à direita + preview do widget à esquerda**.
3. **Campos por tipo de widget** (Geral varia por tipo; documentado em detalhe para Número; Gráfico via Figma). Faltam capturar em detalhe os demais (Calendário, Status, Medidor, Tabela, módulos, reuniões…).
4. **Fonte de dados** (Manual vs. módulos Solvace) — base do "Avançado/Fonte".
5. **Update/Batch mode** — alternar widgets para edição de valores.
6. **Config de Sala** e **Config de Board** (já mapeadas acima).
7. **Multi-boards por sala** (abas) + adicionar board.

> Próximo passo sugerido: escolher por quais widgets começar e detalhar a aba Geral/Fonte de cada um (posso voltar ao app e capturar campo a campo).

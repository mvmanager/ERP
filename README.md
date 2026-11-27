# ERP para indústria de papelão ondulado

Sistema de gestão novo, feito do zero para indústria de papelão ondulado.
Nome do produto ainda provisório.

Este repositório começa pelo **protótipo de telas aprovado**. O sistema de verdade
(banco de dados, servidor, login) será construído em cima dessas decisões.

## Protótipo

Abra os arquivos da pasta `prototipo/` direto no navegador (duplo clique):

| Arquivo | O que mostra |
|---|---|
| `prototipo/tela-inicial-e-comercial.html` | Tela inicial, áreas de cada módulo e a área Vendas do Comercial. Clique em **Comercial** e depois em **Vendas**. |
| `prototipo/caixinhas-de-papelao.html` | Os seis desenhos de caixa usados no efeito dos módulos. |
| `prototipo/estilos-de-tela-pesquisa.html` | Pesquisa inicial: nove estilos de organizar telas usados por outros sistemas. |

Fotos das telas estão em `docs/fotos/`. As fotos 03 a 06 são de antes da divisão em
áreas (a barra de cima mostrava só "Comercial", sem "› Vendas"); o comportamento das
janelas continua o mesmo.

Para ver o protótipo sem baixar nada: https://claude.ai/artifact/KrHFXtBn5s9YtySNMPGRM1
(link privado do dono da conta).

Os números, clientes e pedidos do protótipo são **exemplos**. A busca do assistente
usa uma lista fixa de telas e relatórios; no sistema real ela consultará o catálogo
do sistema (com IA) respeitando o que cada usuário pode acessar.

## Decisões aprovadas

### Visual
- Cores puxadas para o papelão (kraft), com tema claro e escuro.
- Textura leve de papel no fundo e a **onda do papelão** (flute) como detalhe da marca.
- Na barra de cima aparece só o **logo**, sem o nome do sistema.

### Tela inicial
- Saudação pequena com o nome do usuário e "Bom dia / Boa tarde / Boa noite" pelo horário.
- **Busca no sistema** pequena, à direita da saudação. O assistente:
  - encontra a tela, relatório ou ação e leva até ela;
  - quando não existe exatamente, mostra o que tem de mais próximo;
  - quando não existe nada parecido, oferece **pedir ao desenvolvedor uma análise**
    (gera um protocolo; no sistema real vai para uma fila de melhorias).
- **Módulos em destaque** (grade de cartões, estilo "aplicativos"). Cada módulo grande
  é dividido em **áreas**, porque pessoas diferentes trabalham em áreas diferentes:

  | Módulo | Áreas |
  |---|---|
  | Comercial | Vendas, Portal do representante, Crédito, Faturamento, NFe, Expedição |
  | Industrial | Engenharia industrial, Engenharia de produto, Pesagem, PCP, Segurança, Reporte de produção, Manutenção |
  | Suprimentos | Compras, Materiais |
  | Qualidade | Laboratório, Qualidade, RNC, FSC |
  | Financeiro | Administração financeira, Contas a pagar, Contas a receber |
  | Controladoria | Fiscal, Contabilidade, Custos, Ativo imobilizado |
  | Recursos Humanos | Folha de pagamento, Treinamento |
  | Suporte | Chamados, Usuários e permissões |
  | Gerencial | Relatórios |

  - Cartões **compactos** (metade do tamanho original): ícone ao lado do nome e, embaixo,
    os nomes das áreas em letra pequena. Seis cartões por linha no computador.
  - Ao passar o mouse: o cartão sobe, inclina levemente, ganha uma luz suave e uma
    **desenho que representa o módulo** entra pelo canto, no estilo papelão: caixa com
    etiqueta de preço (Comercial), fábrica (Industrial), bobina de papel (Suprimentos),
    selo (Qualidade), nota e moedas (Financeiro), balança de pratos (Controladoria),
    pessoas (Recursos Humanos), boia (Suporte), gráfico subindo (Gerencial).
    Todos os desenhos estão em `docs/fotos/11-desenhos-dos-modulos.png`.
  - **Só estes 9 módulos.** Orçamentos, Engenharia de Produto e Cadastros foram retirados:
    o que eles faziam vai virar parte de algum módulo acima (a definir).
  - Selo vermelho com a quantidade de pendências do módulo.
- A seção **Pendências** foi retirada da tela inicial (o selo vermelho nos cartões continua).
- **Meus atalhos** (abaixo dos módulos): área personalizada onde cada pessoa deixa os
  **relatórios** que mais usa, para abrir com um clique.
  - Cada atalho mostra o nome do relatório e onde ele fica (ex.: "Comercial › Vendas").
  - Botão **＋ Criar atalho** abre uma janela com a lista de relatórios, separados por
    módulo e área, com busca. "+ Adicionar" coloca nos atalhos; clicar de novo tira.
  - Só aparecem relatórios dos **módulos e áreas liberados para a pessoa**.
  - Para tirar um atalho: passar o mouse e clicar no ✕.
  - Cada pessoa vê só os próprios atalhos. No protótipo eles ficam guardados no
    navegador; no sistema real, no cadastro do usuário (aparecem em qualquer computador).

### Cada módulo na sua própria aba (padrão para todos)
- Clicar num módulo na tela inicial abre o módulo numa **aba nova** (no aplicativo
  instalado, numa **janela nova**, agrupada no mesmo ícone da barra de tarefas).
  Assim a pessoa troca de módulo com **Alt+Tab** sem largar o que estava fazendo.
- O título da aba mostra o módulo e a área (ex.: "Comercial › Vendas"), para achar fácil.
- Pedir um módulo que **já está aberto** só traz a aba dele para a frente, do jeito que
  a pessoa deixou (não abre outra cópia nem volta para o começo).
- Numa aba de módulo, o **logo** e o **"‹ Início"** levam para a aba da tela inicial.
- Trocar de área dentro do módulo acontece na mesma aba.
- Se o navegador bloquear abas novas, o módulo abre na mesma aba.
  No link de visualização do Claude o protótipo roda dentro de outra página, que não deixa
  abrir aba nova: ali o módulo abre na mesma aba e aparece um aviso.
- No sistema publicado, o ERP poderá ser **instalado como aplicativo** pelo Chrome ou
  Edge: ícone próprio na barra de tarefas e na área de trabalho, janela sem barra de
  endereço. (Não dá para mostrar isso no link do protótipo.)
- Os **atalhos de relatório** da tela inicial abrem na **mesma aba** (decidido).

### Áreas do módulo (padrão para todos)
- Clicar num módulo que tem áreas abre a **tela de áreas**, no **mesmo layout da tela
  inicial**: botão **‹ Voltar** (volta para a tela de onde a pessoa veio; se abriu direto,
  para o Início), título do módulo **pequeno** (ícone e nome na mesma linha do Voltar, sem frases de apoio) e
  uma grade de cartões compactos, um por área. Cada área também tem o **seu desenho**
  ao passar o mouse (ex.: caminhão com caixas em Expedição, capacete em Segurança,
  balança com display em Pesagem, frasco em Laboratório, crachá com cadeado em Usuários e permissões) e o selo
  de pendências de cada área.
- No sistema real, cada pessoa vê só as áreas liberadas para ela.

### Dentro de uma área (padrão para todos)
- Barra de cima baixa e colada à esquerda: logo, "‹ Áreas" (volta para as áreas do
  módulo), ícone e nome do módulo, **› nome da área** e os **tópicos** da área (cada
  um abre uma lista com seus itens).
- **Logo** → tela inicial. **Ícone do módulo** → início do módulo (tela de áreas).
- Se os tópicos não couberem numa linha, a página percebe sozinha e passa os tópicos para
  uma segunda linha (vale para qualquer quantidade de tópicos).
- Dentro da área a barra fica enxuta para caber todos os tópicos numa linha: sem relógio,
  sem o nome do usuário (só a bolinha com a inicial) e sem o aviso "mais tópicos". Em telas
  estreitas os tópicos descem para uma segunda linha; no celular as listas ocupam a largura
  da tela.
- O nome da área é só informativo: **não há troca rápida de área pela barra de cima**
  (foi retirada para não confundir com os tópicos). Para mudar de área, volta-se às áreas.
- Área sem tópicos definidos mostra "tópicos a definir".
- A área abre **vazia** (só um desenho discreto ao fundo). Nada aparece até
  a pessoa escolher um item — para não confundir quem usa.
- Cada área guarda **as suas próprias janelas**: ao trocar de área elas ficam
  guardadas e reaparecem quando a pessoa volta.
- Cada item abre numa **janela**:
  - abre **grande** (ocupando toda a área); o botão □ alterna para um tamanho menor;
  - pode ser **arrastada** pela barra de título, até passar da borda do monitor;
  - **muda de tamanho** pelo canto inferior direito (mínimo 520 × 340);
  - várias janelas abertas ao mesmo tempo; pedir uma já aberta só a traz para a frente;
  - **clicar fora** das janelas minimiza todas;
  - janelas minimizadas ficam num cantinho no **canto inferior esquerdo** (só aparecem
    as minimizadas); clicar traz de volta;
  - "–" minimiza e "✕" fecha, sempre visíveis.
- Barra de título da janela numa linha só: ícone pequeno, nome e o caminho ao lado.

### Suporte
- Módulo de administração do sistema. **Só o administrador (dono do sistema) e o TI
  veem este módulo.** Os demais usuários não enxergam o cartão do Suporte.
- No protótipo o cartão aparece para todos, só para demonstração.
- Os outros usuários abrem chamados sem entrar no módulo: pelo botão **? Ajuda** (abaixo)
  e pelo "pedir ao desenvolvedor uma análise" do assistente de busca.
- **Chamados** tem o tópico **Fila de chamados**: lista com todos os chamados (print,
  texto, quem pediu, de qual tela, data e situação), filtro por situação e, ao abrir um,
  botões para **marcar em andamento / resolvido / reabrir** e campo para **responder**.
  Responder um chamado aberto já o passa para "em andamento".
- O selo da área Chamados mostra quantos estão abertos.

### Ajuda: chamados com print da tela (em todas as telas)
- Botão **?** na barra de cima, ao lado do sino, com duas opções:
  **Abrir chamado** e **Meus chamados**.
- **Abrir chamado** liga o **modo de captura**: a tela ganha uma moldura e aparece uma
  faixa embaixo. A pessoa navega até a tela que quer mostrar (pode abrir módulo, área,
  janela) e clica em **Capturar esta tela** (ou Cancelar).
- Abre o formulário com o **print**, a **tela de onde veio** (preenchida sozinha, ex.:
  "Comercial › Vendas › Prospects e clientes"), o **tipo** (erro no sistema, dúvida,
  pedido de melhoria, acesso ou permissão) e **o que você precisa**. Dá para capturar
  outra tela antes de enviar.
- Ao enviar, gera um **protocolo** (CH-ano-número, ex.: CH-2026-0004).
- **Meus chamados**: cada pessoa vê só os seus, com a situação (Aberto, Em andamento,
  Resolvido), o print, o texto e as respostas do suporte.
- No protótipo os chamados ficam guardados só no navegador (e já vêm 3 de exemplo);
  no sistema real ficam no banco de dados e as imagens no armazenamento de arquivos.
- **Chamados:** onde chegam os pedidos de ajuda e de melhoria dos usuários (inclusive os
  pedidos de análise feitos pelo assistente de busca da tela inicial).
- **Usuários e permissões:** criar usuários e definir quais módulos e áreas cada um vê.

### Comercial › Portal do representante (tópicos definidos até agora)
- É a área **onde os próprios representantes trabalham** (externos). A administração dos
  representantes (cadastro, metas, comissões) fica em **Vendas**, onde trabalha o pessoal
  interno.
- O representante **não lança pedido e não cadastra cliente**. Ele faz **solicitações**,
  preenchendo todos os dados do cliente e do produto; o pessoal interno analisa, cadastra o
  prospect/cliente e, quando a solicitação de orçamento é aprovada, **converte em pedido**.
  (A forma de deixar isso "autêntico e dinâmico" será pensada ao desenhar a tela.)
- **Solicitações:** Solicitar orçamento · Pedir amostra · Pedir clichê · Pedir
  desenvolvimento de produto (faca, caixa nova, mudança de projeto) · Minhas solicitações
  (acompanha todas: em análise, aprovada, virou pedido).
- **Meus clientes:** Carteira de clientes (só os dele, com resumo e últimas compras).
- **Meus pedidos:** Acompanhar pedidos — **em que etapa** cada pedido está (programado,
  produção, expedição…). Sem as notas fiscais.
- **Agenda:** Agenda · Registrar visita ou contato (aparece para o interno em
  Vendas › Follow-up › Atividades dos representantes).
- **Meus números:** Minhas comissões · Minhas vendas × meta.
- **Quem trata as solicitações (decidido):**
  - **Orçamento:** representante solicita → **Controladoria › Custos** calcula custo e preço
    (motor de precificação e calculadora de caixa) → **Comercial › Vendas › Orçamentos**
    negocia, aprova e converte em pedido. O representante acompanha cada etapa em
    "Minhas solicitações".
  - **Amostra, clichê e desenvolvimento:** → **Industrial › Engenharia de produto**.

### Controladoria › Custos (tópicos definidos até agora)
- **Orçamentos:** Fila de solicitações de orçamento · Calcular preço (motor de precificação
  e calculadora de caixa do sistema atual).

### Industrial › Engenharia de produto (proposta inicial)
- Área nova (no lugar do antigo módulo "Engenharia de Produto"). Recebe as solicitações
  de amostra, clichê e desenvolvimento do Portal do representante e do pessoal interno.
- **Solicitações:** Solicitações recebidas · **Amostras:** Amostras · **Clicheria:** Clichês ·
  **Facas:** Facas · **Desenvolvimento:** Desenvolvimento de produto (projeto e ficha técnica).
- Desenho ao passar o mouse: a caixa planificada com as linhas de corte (faca).

### Comercial › Vendas (tópicos definidos até agora)
- **Orçamentos:** Orçamentos (chegam de Custos já com preço: consultar, negociar, aprovar e
  converter em pedido).
- **Cadastros** (baseado no menu do sistema atual), em grupos:
  - Prospects e clientes · Áreas de vendas · Representantes · Supervisores de vendas ·
    Metas de vendas
  - Prazos de pagamento
  - Parâmetros de vendas (inclui definir quais **atributos extras** o cliente pode ter)
- **Não terão menu próprio** (viram campos/listas de escolha **dentro do cadastro de
  prospect e cliente**): Assuntos, Grupo de empresas, Segmento econômico, Meios de
  comunicação, Tipos de bloqueio na entrega, Nosso prazo × prazo do cliente, Motivos de
  alteração de data de entrega / quantidade do pedido.
- Também ficam **dentro da ficha do prospect/cliente** (decidido): **Histórico do cliente**,
  **Produto × endereço de entrega**, **Unidades do cliente**,
  **Alterar nome fantasia**, **Endereços de cobrança**, **Endereços de entrega** (o cliente
  pode ter vários) e os valores dos **Atributos extras** (aba "Informações extras"). Ideia: tudo que é de um cliente específico fica na ficha dele.
- Listas de tópicos com mais de 8 itens abrem em **duas colunas**, para caber na tela.
- **Operações** (no sistema atual se chama "Eventos": são ações que a gente executa),
  com os itens separados por títulos de grupo dentro do menu:
  - **Preços:** Negociação de preço · Tabela de preços · Preço por intervalo de m²
  - **Programas do cliente:** Importação de pedidos por EDI · Analisador de programas do cliente
  - **Liberações:** Bloqueio de entrega de produto · Bloqueio em item de pedido ·
    Confirmar previsão de embarque (manual)
  - **Não entram:** Digitação, Revisão e Cancelamento de programa, Marcar programas como
    transformados, Relacionar convênios produto × prospect.
  - **Vão para a ficha do cliente:** Histórico do cliente · Produto × endereço de entrega.
  - **Vai para o Portal do representante:** Agenda dos representantes (lá se chama "Agenda").
- **Pedidos** (baseado no menu do sistema atual): Pedidos (lançar, consultar, imprimir) ·
  **Alterar pedido** · Liberação de pedidos · Cancelar item ou entrega
  - **Alterar pedido** é uma janela só que junta as 13 alterações do sistema atual: data de
    entrega e quantidade, prazo de pagamento do item, preço, OC de uma entrega, advertência
    por entrega, comissão do item, representante, endereço de entrega, endereço de
    cobrança, destinação do item, cliente do pedido, transação do item, transportador e
    tipo de frete. A pessoa abre o pedido e muda o que precisa; **cada usuário só altera os
    campos que tiver permissão**.
  - **Não entram:** Importar pedidos via arquivo EDI (já está em Operações) e Gerar
    entrega a partir de pedido horizonte planejado.
- **Comissões** (7 itens do sistema atual viraram 4):
  - **Regras de comissão:** quanto ganha cada representante e supervisor, inclusive por
    produto (junta "Definir comissão de representante", "Definir comissão do supervisor" e
    "Agente × produtos").
  - **Notas de crédito de comissão:** emitir e desfazer na mesma janela.
  - **Acerto de comissões:** fechamento do período.
  - **Relatório de comissões.**
- **Follow-up** (funcionalidade própria, será criada do zero): Follow-up · Atividades dos
  representantes (os dois tratam de acompanhamento; podem até virar uma coisa só).
- **Consultas** e **Relatórios**: o antigo "Demonstrativos" (27 itens) dividido em dois.
  - **Consultas:** Entregas (consulta de entregas + plano de entregas) · Atendimentos (SAC) ·
    Ocorrências e alterações (ocorrências dos pedidos, alterações de data de entrega e de
    embarque, ocorrências de bloqueio de entrega e de preço por intervalo de m²).
  - **Relatórios:** Análise de vendas (junta vendas por representante, por representante
    meta × real, por supervisor meta × real, por grupo de produtos, comparativo e ranking) ·
    Previsão de faturamento · Evolução de preços (por produto ou por cliente) · Produtos
    não vendidos · Indicador OTIF (On Time In Full).
  - Consulta/relação de pedidos, pedidos por cliente e pedidos faturados ficam em
    **Pedidos › Pedidos** (com filtros). Últimas compras e ocorrências do cliente vão para
    a **ficha do cliente**. Relação de entregas geradas de pedidos HP **sai**.
  - "Depois vemos se tiramos algo": a lista pode encolher.
- Outros tópicos serão acrescentados conforme forem definidos.

## Próximos passos
1. **Mapa de funcionalidades (passo atual):** fechar, "no grosso", os tópicos e as
   funcionalidades de **todas** as áreas de todos os módulos, a partir dos menus do
   sistema atual (prints) e de propostas onde não houver equivalente. Decidir também em
   qual módulo entram orçamentos, engenharia de produto (amostras, clicheria, facas) e os
   cadastros gerais.
   Níveis: **Módulo › Área › Tópico › Funcionalidade**.
   Decidido: o preço dos orçamentos é calculado em Controladoria › Custos e a aprovação e
   conversão em pedido ficam em Comercial › Vendas › Orçamentos; engenharia de produto
   virou área do Industrial. Falta decidir onde ficam os cadastros gerais.
2. Desenhar o conteúdo das janelas, começando por **Prospects e clientes**
   (Comercial › Vendas › Cadastros).
3. Montar o sistema de verdade:
   - aplicação em Docker, banco PostgreSQL e configurações fora do código, para poder
     trocar de hospedagem sem retrabalho;
   - trazer o **motor de precificação** do Novo Comercial (sistema atual, pasta
     `shared/precificacao/` do CRM Salute), que já é feito só de cálculos e foi
     conferido contra demonstrativos de custo do ERP;
   - trazer a calculadora de caixa (eslote por cilindro de cada impressora).

## Hospedagem (plano)
- **Durante a construção:** Render, na mesma conta já usada, com dados fictícios.
- **Quando estiver pronto:** migrar para o **Google Cloud, região São Paulo**
  (Cloud Run + Cloud SQL), usando os 3 meses de teste grátis para os testes finais e
  o primeiro cliente piloto. Só abrir a conta do Google Cloud na hora da migração,
  porque os 90 dias contam a partir do cadastro.
- Com o primeiro contrato: ligar alta disponibilidade do banco, Cloud Armor e
  ambiente de testes separado; o custo entra no preço do contrato.

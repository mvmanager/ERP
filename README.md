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
- **Regra para todas as telas: compacto, sem espaço ocioso** (pedido do usuário). Quadros,
  campos e listas bem juntos, rótulos curtos, vários campos por linha, listas em uma linha por
  item. Espaço sobrando gera confusão visual.
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
  - **Automação:** os motores (precificação, calculadora de caixa) ficam **dentro dos módulos
    internos** e trabalham sozinhos quando a solicitação chega: em Custos, o preço já vem
    calculado e a pessoa só confere e ajusta exceções. A mesma ideia pode valer para outras
    solicitações (ex.: amostra já gerar a planificação da caixa).
  - **A decidir ao desenhar a tela:** preço calculado dentro das regras vai direto para
    Vendas, ou Custos sempre confere antes? (Meio-termo comum: passa direto se estiver dentro
    das regras; para em Custos só quando foge delas.)

### Suprimentos (o que já veio de outras áreas)

### Suprimentos › Materiais (a partir do sistema atual: ~60 itens → 23)
- Estoque de **matéria-prima**. Tudo de um material fica na **ficha do material**; cada
  inventário é uma tela com as etapas dentro.
- **Operações:** Recebimento (+ justificativas para liberar) · Movimentação do estoque ·
  Remessas, transferências e devoluções · Administração do estoque (inclui implantar/alterar
  CMU) · Emissão de etiquetas.
- **Materiais:** Materiais (ficha: classificação, qualificações, crítico/importante, tipo de
  papel, embalagens × materiais, categoria FSC, alteração de subgrupo).
- **Estoque de segurança:** Previsão de consumo e estoque de segurança (inclui política por
  subgrupo; veio da Engenharia de produto) · Análise do estoque de segurança (inclui
  políticas de estoque).
- **Inventário:** Inventário rotativo (8 itens atuais) · Inventário geral (11 itens atuais).
- **Cadastros:** Classificação de materiais · Unidades de medida e conversões · Depósitos e
  localizações · Embalagens internas · Modelos de etiqueta · Controle da Polícia Federal ·
  Aprovadores de requisição · Parâmetros.
- **Consultas:** Movimentação e saldos (+ boletins) · Consumos e requisições · Materiais
  críticos · Industrialização e consignação · FSC.
- **Cadastro único:** Depósitos e localizações (Materiais) e Armazéns e localizações
  (Expedição) serão o mesmo cadastro, aparecendo nas duas áreas.

### Suprimentos › Compras (a partir do sistema atual: ~48 itens → 17)
- A compra anda em etapas (requisição → cotação → ordem de compra); cada etapa é uma tela.
  Tudo do fornecedor fica na **ficha do fornecedor**.
- **Processo de compra:** Requisições de compra (pedir, assinar, confirmar, aprovar, empenho de
  verbas) · Cotações (solicitar normal e N/N, emitir, registrar normal e simplificado,
  alterar, analisar, cancelar proposta) · Ordens de compra (registrar, imprimir, enviar por
  e-mail, alterar, validar alterações, cancelar) · Sugestão de ressuprimento · Importação.
- **Fornecedores:** Fornecedores (com endereços, nome fantasia, limite de crédito para
  compras, materiais × fornecedor/embalagem/referências e listas de preço) · Avaliação de
  fornecedores (IQF).
- **Preços e serviços:** Tabela de preços de chapas · Serviços de terceiros (inclui OS de
  terceiros para estoque, vinda do PCP, tabela de preços de serviços e confirmação da
  execução).
- **Cadastros:** Condições de pagamento · Grupos de compras · Alçadas de aprovação · Observações
  padrão para OC · Equivalência de qualidades · Parâmetros.
- **Consultas:** Gestão de entregas (inclui entregas parciais) · Gestão de compras.
- **Para outros lugares:** Transportadores → Expedição › Transporte de cargas (cadastro único
  de transportadoras). "Informe retroativo de últimas compras" parece ferramenta de
  implantação (carga de histórico) — sem menu, a confirmar.
- A pensar depois: Condições de pagamento (Compras) e Prazos de pagamento (Vendas) podem ser
  um cadastro só.

### Financeiro › Administração financeira (a partir do sistema atual: 29 itens → 15)
- **Operações:** Conta corrente · Orçamento e verbas (planejamento orçamentário + distribuição e
  transferência de verbas + cadastro de verbas) · Projetos (com o encerramento).
- **Cadastros:** Bancos e contas (bancos/portador + agências + contas) · Rubricas e
  responsáveis (grupos, rubricas, administradores, níveis, rubricas × administradores) ·
  Operações e tipos de documento · Arquivos bancários (GAE + códigos de ocorrência de retorno) ·
  Indicadores e índices financeiros · Feriados · Parâmetros.
- **Consultas:** Saldos bancários · Fluxo de caixa (inclui comparativo ingressos × desembolsos) ·
  Orçamento, verbas e projetos · Prazo médio de recebimento e pagamento.
- **"Exportar dados das contas correntes p/ contabilidade" sai do menu:** no sistema novo o
  Financeiro e a Contabilidade conversam sozinhos (lançamento automático).
- A pensar: Feriados pode ser um cadastro único da empresa, usado também pelo calendário do PCP.

### Financeiro › Contas a pagar (a partir do sistema atual: 46 itens → 17)
- CCP (conta a pagar) passa a se chamar só **conta a pagar**.
- **Contas a pagar:** Contas a pagar (registro, alteração, transformação, aprovação/conferência,
  prorrogação, revisão de vencimentos, imprimir) · Chegada de boletos e PIX (registro de
  chegada de bloquetos/PIX QR Code + leitura de arquivo de boletos) · Obrigações.
- **Pagamentos:** Agenda e autorização de pagamentos (agenda, autorização, desfazer
  agendamento, pagamentos × vencimentos) · Liquidação e retorno bancário (liquidação, retorno
  de pagamentos eletrônicos, estorno) · Cheques (avulsos, reemissão, cancelamento, cópia,
  blocos, controle) · Créditos com fornecedores (acertos, desfazer, transferir entre parceiros
  do grupo) · Fundo fixo.
- **Cadastros:** Tipos e formas de pagamento (tipos, formas e × banco) · Classificação de
  despesas · Parâmetros.
- **Consultas:** Posição de contas a pagar (consulta geral, consulta, pendentes, distribuição no
  tempo, por classificação de despesa) · Pagamentos realizados (diários, com fundo fixo,
  pré-datados, emissão de recibos) · Remessa e retorno bancário (+ bloquetos não recebidos) ·
  Títulos em cartório · DARFs no período · Saldos de créditos dos parceiros.

### Financeiro › Contas a receber (a partir do sistema atual: 41 itens → 16)
- **Títulos a receber:** Títulos a receber (registros, cancelar título, abatimentos,
  prorrogações, redestinação de portador/carteira, histórico) · Pagamento antecipado.
- **Cobrança:** Agenda de recebimentos (+ desfazer agendamento) · Cobrança bancária (retorno da
  cobrança eletrônica, instruções de alteração escritural, solicitação de baixa, reemissão de
  boletos) · Baixa de recebimentos (informe de liquidação individual e agrupado) · Cartório
  (movimentação) · Créditos com clientes (acerto, desfazer, transferir entre parceiros do grupo;
  saldos de créditos).
- **Cadastros:** Taxas bancárias (+ bancos × taxas) · Parâmetros.
- **Consultas:** Posição de títulos a receber (consulta de títulos, distribuição no tempo,
  resumo por banco, situação, pendentes, por agendar; e os "Meus relatórios" por parceiro, por
  banco e por data de emissão) · Títulos em atraso · Duplicatas e borderôs · Limites de caução
  e desconto · Remessa e retorno bancário · Faturamento × contas a receber · Alterações em
  títulos.
- **Cobrança automática (ideia para depois):** lembrete por e-mail/WhatsApp antes e depois do
  vencimento, com o boleto ou PIX.

### Controladoria › Fiscal (a partir do sistema atual: ~64 itens → 18)
- **Operações:** Escrituração (entradas + revisão do boletim de entrada + saídas + conferir notas
  próprias) · Apuração de impostos (IPI, ICMS, PIS/COFINS, exportar apuração, exclusão de
  resumos, informações adicionais E115) · Obrigações e arquivos fiscais (EFD ICMS/IPI, EFD
  Contribuições, EFD-Reinf, GIA, SINCO, DNF, ISSQN eletrônico) · Valorização dos estoques.
- **Cadastros:** Convênios de impostos e Aplicação dos convênios (vieram do Faturamento) ·
  Classificação fiscal e NCM (+ unidade e NCM Siscomex, tabela IBPT) · Alíquotas e tributações
  (alíquotas especiais e do ICMS, reduções, tributações ICMS/IPI, exclusões PIS/COFINS) ·
  Naturezas e transações de entrada (+ natureza × transação) · Impostos municipais (grupos de
  serviços e atividades, serviços, atividades, registro ISSQN) · Regras fiscais (retenção de
  tributos, regras das notas próprias, fórmulas sobre boletins) · Códigos de ajuste e
  observações · Parâmetros (inclui tabela de produtos para o DNF).
- **Consultas:** Livros fiscais (registros de entradas, saídas e inventário, apurações e
  termos) · Declarações (GI/ICMS, Sintegra, DIPJ, DFC) · Conferências fiscais (notas ×
  registros, resumo por CFOP/UF, débitos/créditos PIS/COFINS).
- **Foram para Custos:** Demonstrativo dos custos de venda · Estoque de produtos em elaboração.
- **Conferir com a contabilidade:** várias obrigações do menu atual podem não existir mais
  (Sintegra, DIPJ, GIA em alguns estados, SINCO, DNF). E a **reforma tributária (IBS/CBS)**
  precisa entrar desde o começo.

### Qualidade › Qualidade e Laboratório (a partir da "Garantia da Qualidade": 20 itens → 12)
- **Qualidade** — *Certificados:* Certificados de qualidade (veio do Faturamento).
  *Padrões:* Padrões de qualidade (proposta, análise, consenso e padrões × setores na mesma
  tela) · Lista mestra dos padrões · Arquivo inativo (controle + destruição).
  *Cadastros:* Tipos e famílias de padrões · Homologação de marcas · Parâmetros (inclui
  personalização do código do relatório). *Consultas:* Rastreabilidade de lotes (lote de
  fabricação × lotes de insumos).
- **Laboratório** (módulo Laboratório atual + parte da Garantia da Qualidade):
  *Inspeções:* Inspeção de materiais (recebimento, amostras, revalidação de AR, troca de lote
  do fornecedor) · Inspeção de produtos (produtos + amostras de acabados).
  *Ensaios:* Ensaios e amostragem (ensaios + intervalos p/ amostragem) · Ensaios por material e
  produto (material × ensaio, subgrupo × ensaio, produto × ensaio, copiar ensaios) · Métodos
  de análise · Contratipos.
  *Instrumentos:* Instrumentos de medição (cadastro + movimentação) · Aferições.
  *Consultas:* ARs e histórico de inspeção (ARs por vencimento, movimentação do AR, histórico,
  skip lote) · Rejeitados e material para testes · Inspeção de produtos (inclui
  acompanhamento por lote da onduladeira).
- **RNC** e **FSC** ficaram **para depois** (decisão do usuário).

### Controladoria › Contabilidade (a partir do sistema atual: ~52 itens → 13)
- **Operações:** Lançamentos (+ lançamentos em aberto) · **Contabilização automática** — as 10
  "Contabilização de…" (requisições, contas a receber, contas pagas, contas correntes, encontro
  de contas, movimentos de produtos, recálculos de custos e de subproduto/cola/bagaço, folha,
  ativo imobilizado) e a "Interface contábil" deixam de ser feitas à mão: cada área lança
  sozinha e aqui há um painel para acompanhar e corrigir · Períodos e exercício (abertura,
  encerramento, fechamento, reabertura, despublicar demonstrativos) · Obrigações contábeis (ECD,
  ECF, FCONT parcial, SINCO).
- **Cadastros:** Plano de contas (grupos contábeis, categorias, aglutinação, plano referencial
  ECD) · Contas de clientes, fornecedores e outros (os 7 "× Plano de contas" ficam também na
  ficha de cada um) · Históricos e lançamentos padrão · Parâmetros (inclui classificação para
  conciliação).
- **Relatórios:** Balancete (normal e referencial) · Livros contábeis (diário, razão, livro caixa,
  termos, listagem de lançamentos) · Demonstrações financeiras (balanço, DRE, DFC método direto,
  lucros/prejuízos acumulados, custo dos produtos vendidos) · Conciliação contábil (+ folha) ·
  Saldos das contas.
- Conferir com a contabilidade: FCONT e SINCO podem estar extintos.

### Controladoria › Custos (a partir do sistema atual: ~45 itens → 17)
- **Área que vai mudar bastante** (aviso do usuário): aqui entram o motor de precificação e a
  calculadora de caixa do sistema atual.
- **Orçamentos:** Fila de solicitações de orçamento · Calcular preço (inclui simulação de preço
  de venda/orçamento, individual e em lote). Alterar, imprimir, enviar e detalhes do orçamento
  ficam na tela de **Orçamentos de Vendas**.
- **Custo padrão:** Custo padrão (uma tela, por tipo: mão de obra, célula, máquina, serviço de
  terceiros, produto em processo, material, tipo de papel).
- **Custo hora e rateios:** Rateio de gastos fixos (regras C.I.F., gastos fixos não
  automatizados, MLC GF) · Custo hora das máquinas (apuração + confirmação) · Custo hora da
  mão de obra (regras de rateio M.O., apuração, confirmação, MLC MO) · Pós-cálculo (alteração +
  pós-cálculo físico).
- **Cadastros:** Centros de custo (+ aplicação, setores, altera aplicação × CC, delega domínios)
  · Mão de obra e cargos (+ cargos × mão de obra) · Mark-up (+ percentuais) · Parâmetros.
- **Consultas:** Demonstrativo de custos (+ por cliente, custo padrão × última compra) · Margem
  de contribuição (+ cálculo de preço por cliente) · Custos de venda e Estoque em elaboração
  (vieram do Fiscal) · Custos indiretos e consumo · Histórico de orçamentos (por
  representante, por onda, reprovados, simulações, relação).
- "Utilização da Polícia Federal" → Suprimentos › Materiais › Controle da Polícia Federal.
  Cargos também existem no RH: ao desenhar, usar um cadastro só.

### Controladoria › Ativo imobilizado (a partir do sistema atual: 29 itens → 10)
- **Bens:** Bens (implantação, confirmação de inclusão, ativação, reclassificação, apólice) ·
  Movimentação de bens (transferência interna, desmembramento, baixa total) · Construção em
  andamento.
- **Cálculos:** Depreciação e créditos (depreciação acelerada normal e incentivada, cálculo de
  depreciação/amortização/exaustão/CIAP/PIS/COFINS, desfazer cálculo).
- **Cadastros:** Grupos e classificação de bens · Leis e apólices · Parâmetros (inclui
  implantação do CIAP, PIS e COFINS).
- **Consultas:** Inventário de bens (inventário, bens do ativo, ficha do bem, aquisições,
  baixas, reclassificações) · Resumo dos cálculos (cálculos, CIAP, PIS, COFINS) · Histórico de
  movimentos.
- Ligação: as **máquinas** da Engenharia industrial são bens do ativo — ao desenhar, ligar os
  dois cadastros.

### Industrial › Engenharia industrial, Manutenção e Reporte (a partir do sistema atual)
- No sistema atual, o menu "Engenharia Industrial" é quase todo **manutenção**. Foi dividido
  (21 itens → 13), e **UO** (unidade operacional) passou a se chamar **Máquina**:
- **Engenharia industrial** — *Cadastros:* Máquinas (UO + tipos + grupos) · Motivos de
  parada · Motivos de refugo e perda · Operações e células · Roteiros de produção (os dois
  vieram da Engenharia de produto) · Parâmetros. *Capacidade:* Previsão de utilização das
  máquinas (previsão + detalhe).
- **Manutenção** — *Ordens de serviço:* Ordens de serviço (abrir, autorizar, prometer prazo,
  emitir e alocar pessoal na mesma tela) · Fila de OS a atender (inclui as pendentes).
  *Preventiva:* Programa de preventiva e lubrificação (com a agenda) · Tarefas de preventiva e
  lubrificação. *Cadastros:* Grupos de manutenção. *Consultas:* Histórico e análise de OS
  (encerradas, por máquina, por período) · Histórico dos componentes.
- **Reporte de produção** — *Apontamentos:* Ajuste de paradas e máquina ociosa. *Consultas*
  (vieram do PCP): Produção por período (relatório + volume produzido) · Paradas · Refugo
  (por OF + estratificação) · Apontamentos.

### Industrial › Pesagem e apontamentos do Reporte de produção
- **Deixados para depois** (decisão do usuário). Têm ligação com a balança e com as máquinas
  (ver "Ligação com equipamentos da fábrica").

### Industrial › Segurança (a partir do sistema atual: 15 itens → 8)
- No sistema atual cuida de **EPI e uniforme**.
- **Entregas:** Entrega de EPI e uniforme (retirada, estorno, implantação e comprovante
  assinado) · Revalidação de EPI.
- **Planejamento:** Previsão de consumo de EPI.
- **Cadastros:** EPIs por função (Funções + Função × EPI) · EPIs e uniformes por funcionário
  (Usuário × EPI/uniforme + Usuário × função) · Parâmetros.
- **Consultas:** Alertas de EPI (tempo de uso esgotado, CA vencido, retirada pendente) ·
  Consumo de EPI (curva ABC).
- Observação: funções e funcionários são dados de RH; a Segurança usa esses cadastros.
- Possíveis acréscimos (não existem hoje, a decidir): registro de acidentes/incidentes,
  inspeções de segurança, CIPA.

### Industrial › PCP (a partir do sistema atual: ~60 itens → 16)
- Tudo de uma **OF (ordem de fabricação)** fica dentro da própria OF.
- **Pedidos:** Pedidos a programar (liberar no PCP ou devolver para Vendas).
- **Ordens de fabricação:** Ordens de fabricação (gerar, alterar quantidade e chapas, recursos
  empenhados, troca de máquina, observação, histórico padrão, cancelar OF/saldo, ajustar mão
  de obra, encerrar OF da integração Aucavili) · Emissão de OF e etiquetas.
- **Programação:** Programação da onduladeira (submenus "Corrugado") · Sequenciamento da
  produção (sequenciar, alterar, cancelar).
- **Materiais:** Necessidades de materiais (explosão dos pedidos, compras para OF, sugestão de
  compra de chapas, empenhados) · Revisão de consumos (demanda independente, baixa automática).
- **Capacidade:** Horas extras e jornada · Paradas previstas (máquinas e ferramentas).
- **Cadastros:** Calendário, turnos e equipes · Regras de produção (transferência, bloqueio de
  máquina para sequenciar, lavagem de tinteiros, histórico padrão) · Corrugado · Parâmetros
  (inclui layouts do PCA e volume para carga máquina).
- **Consultas:** Painel de atividades (PCA) · Andamento das OFs · Carga máquina e utilização.
- **Foram para outras áreas:** relatórios de produção, paradas, refugo e apontamentos →
  Reporte de produção · OS de terceiros para estoque → Suprimentos › Compras (Serviços).
- **A confirmar:** "Auditor lógico operacional" (ferramenta técnica? tirar ou levar ao
  Suporte). "Meus relatórios" do PCP já é coberto pelos Meus atalhos da tela inicial.

### Industrial › Engenharia de produto (a partir do sistema atual, enxuto)
- Recebe as solicitações de amostra, clichê e desenvolvimento do Portal do representante.
  O menu atual tem 38 itens: 12 ficam aqui e 5 vão para outras áreas (o resto foi juntado).
- **Desenvolvimento:** Requisições de desenvolvimento (RD) (inclui as solicitações do Portal) ·
  Amostras.
- **Produtos:** Produtos — a **ficha técnica completa** numa tela (Produtos + Estruturas +
  Atributos extras + Extrair componentes + Alteração de subgrupo).
- **Ferramental:** Facas (com imagem e tipos de lâmina) · Clichês (fichas de impressão) ·
  Ferramental de terceiros (solicitar, acompanhar, concluir).
- **Cadastros:** Classificação de produtos (família, grupo, subgrupo, segmento de mercado,
  grupo FSC) · Corrugado (ondas, papéis e composições) · Textos padrão de advertência ·
  Parâmetros (inclui motivos e conteúdo padrão da RD).
- **Consultas:** Estrutura e onde é usado · Produtos por cliente (cliente × produto,
  relacionamentos, facas e fichas de impressão por cliente).
- **Foram para outras áreas:** Operações, Células e Roteiros de produção → Engenharia
  industrial · Estoque de segurança (previsão, alteração de consumo, parâmetros, análises) →
  Suprimentos › Materiais · Serviços de terceiros → Suprimentos › Compras.
- O usuário avisou que muita coisa daqui vai mudar; a lista pode encolher mais.
- Desenho ao passar o mouse: a caixa planificada com as linhas de corte (faca).

### Comercial › Crédito (definido, a partir do sistema atual)
- **Análises:** Análise de crédito · Liberação de pedidos pelo crédito (junta "por data de
  entrega" e "pela gerência" numa fila só) · Situação da documentação (conferir os
  documentos de todos os clientes e grupos).
- A **documentação do cliente** (contrato social, balanço etc.) fica guardada **na ficha do
  cliente**; o Crédito confere a situação de todos.
- **Consultas:** Itens reprovados pelo crédito.
- **Configurações:** Política de crédito (com o histórico de alterações dentro) · Parâmetros
  de crédito.
- O nome "pelo crédito" evita confusão com a "Liberação de pedidos" de Vendas › Pedidos.

### Comercial › Faturamento (proposta, a partir do sistema atual)
- Padrão de nomes para todas as áreas: **Eventos → Operações**, **Demonstrativos → Consultas**.
- **Cadastros:** Transações de nota fiscal · Grupos de faturamento · Mensagens padronizadas ·
  Parâmetros de faturamento. (Os convênios de impostos foram para Controladoria › Fiscal.)
- **Operações** (do antigo Eventos), em grupos:
  - **Faturamento:** Composição de faturas · Notas fiscais (especial, manual, de romaneio ou
    de devolução de cliente — escolhe o tipo na tela) · Desconto no item da nota.
  - **Embarque:** Aviso de embarque (gerar e ajustar) · Informe de material retornado ·
    Declaração de exportação.
- **Consultas:** a definir (falta o print de Demonstrativos).
- **Movidos (decidido):** Convênios de impostos e Aplicação dos convênios → Controladoria ›
  Fiscal (são regras fiscais; o Faturamento só usa) · Conferência de fretes → Expedição ·
  Certificados de qualidade → Qualidade › Qualidade (o conteúdo vem do laboratório; o
  Faturamento só pede o certificado quando a nota precisa).
- Cancelamento, estorno, inutilização de número e carta de correção **vão para NFe**.

### Comercial › NFe (proposta, a partir do sistema atual)
- Parte fiscal eletrônica das notas (o que se faz com a Receita). Junta o menu de NFe do
  sistema atual (10 itens) e os 4 que vieram do Faturamento → 7 funcionalidades.
- **Operações:**
  - **Notas:** Gerenciar notas (situação na SEFAZ, DANFE e, a partir da própria nota:
    cancelar, estornar, carta de correção) · Lotes de envio · Inutilizar número de nota
    (junta a solicitação de inutilização da NFe e a do Faturamento).
  - **Distribuição:** Distribuição das notas (envio ao cliente e transportador + histórico
    de envios) · Exportar XML.
- **Configurações** (só administrador e TI): Forma de emissão (direto na SEFAZ ou por um
  provedor externo; certificado digital) · Parâmetros de NFe (inclui os schemas de
  validação dos XMLs).
- **Preparado para provedor externo de NFe:** a emissão funciona por uma "peça de encaixe"
  — direto na SEFAZ ou por um provedor especializado (que se adapta às mudanças da
  Receita). As telas de uso (Gerenciar notas, Distribuição etc.) são as mesmas nos dois
  casos, e dá para trocar de provedor sem mexer no resto do sistema.

### Comercial › Expedição (proposta, a partir do sistema atual)
- Expedição cuida do **produto pronto, do armazém até o cliente** (inclui o armazém de produto
  acabado e o inventário dele). A matéria-prima (bobinas, chapas, insumos) fica em
  **Suprimentos › Materiais**.
- **Cadastros:** Armazéns e localizações (Armazém + SISLOC) · Embalagens (Embalagens +
  Embalagens móveis + Produto × Embalagem) · Etiquetas e volumes · Transporte de cargas ·
  Parâmetros de expedição.
- **Operações:**
  - **Estoque:** Movimentar estoque não embalado · Embalar produto · Manutenção de volumes ·
    Transformação de produtos · Transferir de localização · Reparo e reprocessamento.
  - **Entregas:** Planejar entregas · Confirmar previsão de embarque (veio de Vendas) ·
    Embarques · Conferência de fretes (veio do Faturamento).
  - **Terceiros:** Embalagens de terceiros (o antigo "Implanta movimento de embalagens de
    terceiros").
- **Inventário:** Inventário (abertura, fichas e fechamento) · Coletor e leituras (coletor +
  comprovação de leituras).
- **Consultas** (o antigo Demonstrativos + Demonstrativo de inventário): Movimentação e saldos ·
  Volumes · Embalagens de terceiros · Embarques e entregas · Inventário de produtos.
- Os submenus do sistema atual (Etiquetas e volumes, Transporte de cargas, Planejar entregas,
  Embarques, Coletor, Fichas…) serão detalhados quando desenharmos as telas.

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
- Também ficam **dentro da ficha do prospect/cliente** (decidido): **Documentação** (contrato
  social, balanço etc., usada pelo Crédito), **Histórico do cliente**,
  **Produto × endereço de entrega**, **Unidades do cliente**,
  **Alterar nome fantasia**, **Endereços de cobrança**, **Endereços de entrega** (o cliente
  pode ter vários) e os valores dos **Atributos extras** (aba "Informações extras"). Ideia: tudo que é de um cliente específico fica na ficha dele.
- Listas de tópicos com mais de 8 itens abrem em **duas colunas**, para caber na tela.
- **Operações** (no sistema atual se chama "Eventos": são ações que a gente executa),
  com os itens separados por títulos de grupo dentro do menu:
  - **Preços:** Negociação de preço · Tabela de preços · Preço por intervalo de m²
  - **Programas do cliente:** Importação de pedidos por EDI · Analisador de programas do cliente
  - **Bloqueios:** Bloqueio de entrega de produto · Bloqueio em item de pedido
  - Confirmar previsão de embarque (manual) **foi para Expedição › Entregas**.
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
  - **Regras de comissão:** quanto ganha cada representante, inclusive por cliente e
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

## Mapa completo
- O mapa de todas as áreas e funcionalidades, gerado do protótipo, fica em
  `docs/mapa-de-funcionalidades.md` (atualizar sempre que o mapa mudar).

## Próximos passos
1. **Mapa de funcionalidades (fechado por enquanto; faltam Pesagem, apontamentos, RNC, FSC,
   RH, Usuários e permissões e Relatórios gerenciais):** fechar, "no grosso", os tópicos e as
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

## Telas desenhadas por dentro

### Prospects e clientes (Comercial › Vendas › Cadastros) — primeira versão para aprovar
- Feita **do nosso jeito** (o diferencial está nesses detalhes). O sistema atual serviu só de
  referência de campos: `docs/referencias/cadastro-prospect-cliente.md`.
- **Lista** com busca (nome, CNPJ, cidade), filtros (todos, clientes, prospects, inativos) e
  botão **＋ Novo prospect**.
- **Novo prospect começa pelo CNPJ** (aprovado): consulta a base pública da Receita e preenche
  razão social, fantasia, endereço, situação cadastral (alerta se não estiver ativa), natureza
  jurídica, porte, data de abertura, CNAE (sugere o segmento) e telefone/e-mail quando houver.
  Inscrição estadual vem do SINTEGRA (alguns estados só por serviço pago). CEP também
  preenche o endereço sozinho.
- **Cadastro em etapas:** no prospect só o essencial (CNPJ, representante, área, contato,
  interesse); fiscal, financeiro, crédito, entrega e cobrança só quando **virar cliente**.
- Reconsulta periódica da Receita: **não por enquanto** (decisão do usuário).
- **Prospect e cliente na mesma ficha:** botão **Virar cliente** — nada é recadastrado; aparecem
  as seções de fiscal, financeiro e crédito.
- **Abre num resumo**, não num formulário: faturamento 12 meses, margem, pedidos em aberto,
  atraso, crédito usado × limite, últimos pedidos e histórico. Para prospect: interesse e
  últimos contatos.
- **Seções** na lateral (no lugar das 14 abas do sistema atual): Resumo · Dados da empresa ·
  Endereços e unidades · Contatos · Comercial · Entrega e logística · Fiscal e nota ·
  Financeiro e crédito · Avisos · Informações extras · Histórico · Integrações (só TI).
- **Ver primeiro, editar depois:** os campos aparecem como texto; o botão **Editar** libera e
  mostra **Salvar / Cancelar**.
- **Avisos por setor** (no sistema atual, "Advertências") **aparecem sozinhos** na tela de cada setor quando trabalhar com
  o cliente (a de Vendas já aparece no topo da ficha).
- **Contatos** marcados para receber automaticamente cobrança, NF-e, certificado e EDI.
- **Configurações técnicas** (EDI, e-mail do certificado) ficam na seção **Integrações**, só
  para administrador e TI.
- Fotos: `docs/fotos/34-clientes-lista.png` a `37-prospect.png`.
- Ajuste pendente: no celular, a barra de cima cobre o cabeçalho da ficha ao rolar.

### Pedidos (Comercial › Vendas › Pedidos › Pedidos) — primeira versão para aprovar
- **Lista** compacta em tabela (pedido, cliente, OC, emissão, entrega, valor, etapa), busca por
  número/OC/cliente e filtros: Em aberto · No crédito · Em produção · Faturados · Todos.
- **Pedido aberto** mostra a **linha de etapas**: Lançado → Crédito → PCP → Produção → Expedição →
  Faturado → Entregue (etapa atual em destaque; vermelho quando bloqueado), o aviso do cliente,
  cliente e entrega, itens (produto, medidas, onda, **quantidade em unidades**, **peso** em kg/t,
  **preço unitário**, total e **entregas**), totais (quantidade, peso, mercadorias, IPI, total) e o **andamento** (quem fez o quê e quando). Ações: Imprimir ·
  Enviar ao cliente · Alterar (abre "Alterar pedido").
- **Novo pedido** (pela lista ou pelo botão "Novo pedido" da ficha do cliente): escolhe o
  cliente e o sistema **preenche** local de entrega, cobrança, prazo, frete e transportador do
  cadastro; mostra os **produtos que o cliente já compra** com o **último preço**; um clique
  inclui o item; totais recalculam na hora; **cada item pode ter várias entregas** (data +
  quantidade; "+ entrega"), e o sistema avisa "faltam/sobram" e não grava se a soma das
  entregas não bater com a quantidade do item; **confere o crédito** enquanto digita e, se passar
  do limite livre, o pedido vai para aprovação do Crédito ao gravar.
- **Preço por faixa de quantidade** (como a empresa trabalha): cada produto tem preço unitário
  por faixa (ex.: 1.000+, 2.000+, 5.000+, 10.000+). Ao digitar a quantidade, o preço unitário
  segue a faixa sozinho ("faixa 5.000+"); se a pessoa digitar outro preço, vira **"negociado"**
  e para de seguir a faixa. As faixas aparecem nos produtos sugeridos.
- **De onde vêm as faixas (confirmado):** do cálculo de **Custos** (motor de precificação) quando
  o orçamento é aprovado; ficam valendo para aquele **cliente + produto** até um novo orçamento.
- **Cobra-se por unidade**, mas cada item mostra o **R$/kg** (parâmetro de mercado) e o rodapé
  mostra o **R$/kg médio** do pedido.
- **Chapas** também podem ser vendidas por kg (marcadas "chapa · un ou kg"); a precificação é
  sempre conjunta (unidade e kg).
- Fotos: `docs/fotos/39-pedidos-lista.png` a `42-pedido-bloqueado.png`.

### Comissões (Comercial › Vendas › Comissões) — primeira versão para aprovar
- **Regras de comissão:** tabela com quem recebe, vale para (todos / cliente / produto / grupo),
  %, base (valor sem IPI, total da nota ou margem), quando paga (no recebimento ou
  no faturamento) e vigência. Exceções marcadas. **Supervisão não ganha comissão** (decidido).
  A regra mais
  específica vale primeiro: produto › cliente › padrão do representante.
- **Acerto de comissões:** por período, uma linha por representante (faturado, recebido,
  comissão, ajustes, a pagar, situação Aberto → Conferido → Nota gerada → Pago), com detalhe por
  nota/título e ajuste manual. "Fechar período" só depois de conferir todos; gera as notas de
  crédito e manda para Contas a pagar.
- **Notas de crédito:** lista com PDF e **Desfazer** (exige motivo, fica no histórico).
- **Como a empresa paga hoje (decidido):** comissão **no faturamento** — o que é faturado no mês
  é pago no **dia 15 do mês seguinte** (vencimento em Contas a pagar). **No futuro** passará a
  ser **no recebimento** (só o que o cliente pagou): o sistema já tem essa opção em "Quando paga";
  basta trocar nas regras.
- **Relatório:** comissão por representante nos últimos meses, total e mini-gráfico de tendência;
  exportar planilha.

### Portal do representante — primeira versão para aprovar
- O representante vê **só o que é dele** (carteira, pedidos, comissões) e **nunca custo ou
  margem**, só preço. Não lança pedido nem cadastra cliente: faz **solicitações**.
- **Solicitar orçamento** (o coração do Portal), em 4 blocos numa tela:
  1. **Cliente:** da carteira (puxa contato e local de entrega) ou **cliente novo** (CNPJ com busca
     na Receita + contato; Vendas cadastra depois).
  2. **Produto:** **repetir** um que o cliente já compra (dizendo o que muda) ou **produto novo**:
     escolhe o tipo com desenho (caixa normal, com tampa, corte e vinco, bandeja, chapa), medidas
     internas, onda, papel, impressão, peso do conteúdo, empilhamento, ambiente (seco, úmido,
     câmara fria) e FSC. "Não sei — Custos sugere" onde cabe.
  3. **Quantidades:** escolhe várias (500, 1.000, 2.000, 5.000, 10.000…) — Custos devolve o preço
     unitário de cada uma; preço-alvo do cliente, prazo e concorrente atual (opcionais).
  4. **Anexos** (foto, desenho, arte) e observações.
  Ao enviar: protocolo **SO-ano-número** e vai para Custos.
- **Pedir amostra / clichê / desenvolvimento:** formulário curto, vai para Engenharia de produto.
- **Minhas solicitações:** todas, com etapa (Orçamento: Enviada → Em Custos → Preço pronto →
  Aprovada → Virou pedido). Com preço pronto mostra a tabela por quantidade, **PDF para o
  cliente** e **Cliente aceitou** (avisa Vendas). Campo de conversa com quem está tratando.
- **Carteira de clientes:** só os dele; ficha resumida (compras, último pedido, crédito
  ok/atenção — sem valores de limite —, contatos, produtos que compra, últimos pedidos, avisos)
  e atalho "Solicitar orçamento" já com o cliente.
- **Acompanhar pedidos:** cada pedido com a linha de etapas.
- **Agenda** e **Registrar visita ou contato** (vai para Vendas › Follow-up).
- **Minhas comissões** (mês, por nota, pagamento dia 15, últimos meses) e **Vendas × meta**.

## Integrações entre módulos (anotadas até agora)
**Regra:** ao desenhar ou construir qualquer tela, as integrações dela são anotadas aqui **na
mesma hora**. Lista viva: cada tela desenhada acrescenta aqui o que recebe e entrega. Quando todos os
módulos tiverem suas funcionalidades, faremos uma **revisão geral de integrações**.

| De | Para | O quê |
|---|---|---|
| Portal do representante (solicitação de orçamento) | Controladoria › Custos | dados do cliente e do produto para calcular |
| Custos (motor de precificação) | Vendas › Orçamentos | orçamento com faixas de preço |
| Vendas › Orçamentos (aprovado) | Pedidos | faixas de preço por cliente + produto |
| Portal (amostra, clichê, desenvolvimento) | Industrial › Engenharia de produto | solicitações |
| Ficha do cliente | Pedidos | entrega, cobrança, prazo, frete, transportador, avisos |
| Ficha do cliente (crédito) ↔ Crédito | Pedidos | limite livre; pedido acima do limite vai para aprovação |
| Avisos do cliente | todas as áreas (Expedição, Faturamento, Produção…) | aviso automático ao trabalhar com o cliente |
| Pedidos | PCP › Pedidos a programar | pedido liberado pelo crédito |
| PCP / Produção / Expedição / Faturamento | Pedidos (etapas) | andamento do pedido |
| Pedidos (andamento) | Portal › Meus pedidos | etapa de cada pedido do representante |
| Faturamento | NFe | notas para transmitir |
| Todas as áreas | Contabilidade | lançamentos automáticos |
| Engenharia industrial (máquinas) ↔ Ativo imobilizado | — | mesma máquina, um cadastro ligado |
| Materiais ↔ Expedição | — | depósitos e localizações (cadastro único) |
| Compras ↔ Expedição | — | transportadoras (cadastro único) |
| Ajuda (chamados) | Suporte › Chamados | print, texto, protocolo |
| Faturamento (notas do mês) — no futuro Contas a receber (recebimentos) | Vendas › Comissões › Acerto | base de cálculo da comissão |
| Comissões › Regras | Acerto de comissões | % por representante, cliente e produto |
| Pedidos › Alterar pedido | Comissões | comissão específica de um item |
| Acerto (fechar período) | Notas de crédito de comissão + Financeiro › Contas a pagar | valor a pagar a cada representante, vencimento dia 15 do mês seguinte |
| Notas de crédito (desfazer) | Contas a pagar | retira o valor |
| Acerto / Notas | Portal › Minhas comissões | o que cada representante vê |
| Devoluções (Faturamento) | Acerto | estorno de comissão |
| Portal › Solicitar orçamento | Controladoria › Custos (fila) | cliente, produto, medidas, quantidades, anexos |
| Portal › Solicitar orçamento (cliente novo) | Vendas › Prospects e clientes | dados para cadastrar (CNPJ, contato) |
| Custos (preço pronto) | Portal › Minhas solicitações | preço unitário por quantidade (sem custo/margem) |
| Portal › "Cliente aceitou" | Vendas › Orçamentos | aprovar e converter em pedido |
| Portal › Pedir amostra / clichê / desenvolvimento | Industrial › Engenharia de produto | solicitação com anexos |
| Engenharia de produto (andamento) | Portal › Minhas solicitações | etapa da amostra/clichê/desenvolvimento |
| Ficha do cliente + Pedidos | Portal › Carteira | resumo do cliente, sem custo e sem limite de crédito |
| Pedidos (etapas) | Portal › Acompanhar pedidos | etapa de cada pedido do representante |
| Portal › Registrar visita | Vendas › Follow-up › Atividades dos representantes | o que foi conversado e próximo passo |
| Metas de vendas (Vendas › Cadastros) + Faturamento | Portal › Vendas × meta | meta e realizado |

## Ligação com equipamentos da fábrica (plano)
- O sistema poderá receber dados de **máquinas** (velocidade, metros, caixas, paradas),
  **balança**, **leitores de código de barras / impressoras de etiquetas** e **sensores**
  instalados em máquinas antigas.
- Como o sistema fica na nuvem, um **pequeno computador na fábrica (gateway)** lê os
  equipamentos na rede local e envia os dados. No começo **só leitura** (o sistema não
  comanda as máquinas).
- Ordem sugerida: balança → código de barras e etiquetas → onduladeira → demais máquinas.
- Usos: Industrial › Reporte de produção e Manutenção automáticos, Pesagem sem digitação,
  faixa "Fábrica agora" da tela inicial com dados reais.
- Para começar será preciso a lista das máquinas (marca, modelo, ano, se têm CLP/IHM).
- Construir o sistema já preparado para receber esses dados.

## Segurança (regra de construção)
- Protótipo: só visual, dados fictícios.
- Sistema de verdade: dados e regras sensíveis **só no servidor**; a tela recebe só o que o
  usuário pode ver; permissões conferidas no servidor a cada ação; segredos (certificado
  digital, senhas de serviços, chaves) em cofre de segredos, nunca no código; senhas com hash;
  HTTPS; custos/margens/precificação nunca vão para a tela de quem não pode ver; auditoria de
  alterações sensíveis.
- **RLS (segurança por linha) no banco desde o início** (decidido): o próprio banco só devolve
  as linhas que cada um pode ver — separa as **empresas** (nenhuma vê dados de outra), a
  **carteira de cada representante** e as **comissões**. É uma segunda tranca, além da
  conferência no servidor.

### Segurança automática na construção (decidido)
- Gitleaks antes de cada envio de código e na checagem automática do GitHub; Opengrep e
  verificação de bibliotecas a cada mudança (falha grave barra); OWASP ZAP toda noite no
  ambiente de testes; revisão completa antes de cada versão
  (`docs/seguranca/checagem-de-seguranca.docx`).
- Testes automáticos de isolamento (empresa × empresa, representante × carteira, rota por ID).
- Validação de entradas no servidor, limite de tentativas de login, verificação em duas etapas
  obrigatória para administrador e TI, auditoria, backup criptografado com teste de restauração.

## Hospedagem (plano)
- **Durante a construção:** Render, na mesma conta já usada, com dados fictícios.
- **Quando estiver pronto:** migrar para o **Google Cloud, região São Paulo**
  (Cloud Run + Cloud SQL), usando os 3 meses de teste grátis para os testes finais e
  o primeiro cliente piloto. Só abrir a conta do Google Cloud na hora da migração,
  porque os 90 dias contam a partir do cadastro.
- Com o primeiro contrato: ligar alta disponibilidade do banco, Cloud Armor e
  ambiente de testes separado; o custo entra no preço do contrato.

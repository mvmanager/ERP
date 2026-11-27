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
  | Comercial | Vendas, Crédito, Faturamento, NFe, Expedição |
  | Industrial | Engenharia industrial, Pesagem, PCP, Segurança, Reporte de produção, Manutenção |
  | Suprimentos | Compras, Materiais |
  | Qualidade | Laboratório, Qualidade, RNC, FSC |
  | Financeiro | Administração financeira, Contas a pagar, Contas a receber |
  | Controladoria | Fiscal, Contabilidade, Custos, Ativo imobilizado |
  | Recursos Humanos | Folha de pagamento, Treinamento |
  | Suporte | Portaria, Suporte |
  | Gerencial | Relatórios |

  - Cartões **compactos** (metade do tamanho original): ícone ao lado do nome e, embaixo,
    os nomes das áreas em letra pequena. Seis cartões por linha no computador.
  - Ao passar o mouse: o cartão sobe, inclina levemente, ganha uma luz suave e uma
    **caixinha de papelão** entra pelo canto (onda em Industrial, pilha no pallet em
    Suprimentos, caixa que abre nos demais).
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
- No sistema publicado, o ERP poderá ser **instalado como aplicativo** pelo Chrome ou
  Edge: ícone próprio na barra de tarefas e na área de trabalho, janela sem barra de
  endereço. (Não dá para mostrar isso no link do protótipo.)
- A decidir: se os atalhos de relatório da tela inicial também abrem em aba nova.

### Áreas do módulo (padrão para todos)
- Clicar num módulo que tem áreas abre a **tela de áreas**, no **mesmo layout da tela
  inicial**: botão **‹ Voltar** (volta para a tela de onde a pessoa veio; se abriu direto,
  para o Início), título do módulo **pequeno** (ícone e nome na mesma linha do Voltar, sem frases de apoio) e
  uma grade de cartões compactos, um por área, com a mesma caixinha
  ao passar o mouse (pilha no pallet em Expedição e Materiais, onda em PCP e Reporte de
  produção, faca em Engenharia industrial) e o selo de pendências de cada área.
- No sistema real, cada pessoa vê só as áreas liberadas para ela.

### Dentro de uma área (padrão para todos)
- Barra de cima baixa e colada à esquerda: logo, "‹ Áreas" (volta para as áreas do
  módulo), ícone e nome do módulo, **› nome da área** e os **tópicos** da área (cada
  um abre uma lista com seus itens). O logo volta para a tela inicial.
- Clicar no nome da área abre a lista das outras áreas do módulo, para **trocar de
  área sem voltar**.
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

### Comercial › Vendas (tópicos definidos até agora)
- **Cadastros:** Prospects e clientes; Endereços de entrega.
- **Pedidos:** Consultar pedidos; Imprimir pedidos; Alterar pedidos.
- Outros tópicos serão acrescentados conforme forem definidos.

## Próximos passos
1. Desenhar o conteúdo das janelas, começando por **Prospects e clientes**
   (Comercial › Vendas › Cadastros).
2. Definir os tópicos das demais áreas e em qual módulo entram orçamentos,
   engenharia de produto (amostras, clicheria, facas) e os cadastros gerais.
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

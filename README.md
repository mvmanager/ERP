# ERP para indústria de papelão ondulado

Sistema de gestão novo, feito do zero para indústria de papelão ondulado.
Nome do produto ainda provisório.

Este repositório começa pelo **protótipo de telas aprovado**. O sistema de verdade
(banco de dados, servidor, login) será construído em cima dessas decisões.

## Protótipo

Abra os arquivos da pasta `prototipo/` direto no navegador (duplo clique):

| Arquivo | O que mostra |
|---|---|
| `prototipo/tela-inicial-e-comercial.html` | Tela inicial e módulo Comercial (aprovados). Clique em **Comercial** para entrar no módulo. |
| `prototipo/caixinhas-de-papelao.html` | Os seis desenhos de caixa usados no efeito dos módulos. |
| `prototipo/estilos-de-tela-pesquisa.html` | Pesquisa inicial: nove estilos de organizar telas usados por outros sistemas. |

Fotos das telas estão em `docs/fotos/`.

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
- **Módulos em destaque** (grade de cartões, estilo "aplicativos"):
  Comercial, Orçamentos, Engenharia de Produto, PCP, Produção, Estoque, Compras,
  Qualidade, Expedição, Financeiro, Indicadores e Cadastros.
  - Amostras, clicheria, facas e desenvolvimento ficam dentro de **Engenharia de Produto**.
  - Ao passar o mouse: o cartão sobe, inclina levemente, ganha uma luz suave e uma
    **caixinha de papelão** entra pelo canto (faca em Engenharia, onda em Produção,
    pilha no pallet em Expedição, caixa que abre nos demais).
  - Selo vermelho com a quantidade de pendências do módulo.
- **Pendências** abaixo dos módulos: só aparecem os módulos com solicitações esperando
  o usuário, com a quantidade por tipo.

### Dentro de um módulo (padrão para todos)
- Barra de cima baixa e colada à esquerda: logo, "‹ Início", ícone e nome do módulo,
  e os **tópicos** do módulo (cada um abre uma lista com seus itens).
- A área do módulo abre **vazia** (só um desenho discreto ao fundo). Nada aparece até
  a pessoa escolher um item — para não confundir quem usa.
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

### Comercial (tópicos definidos até agora)
- **Cadastros:** Prospects e clientes; Endereços de entrega.
- **Pedidos:** Consultar pedidos; Imprimir pedidos; Alterar pedidos.
- Outros tópicos serão acrescentados conforme forem definidos.

## Próximos passos
1. Desenhar o conteúdo das janelas, começando por **Prospects e clientes**.
2. Definir os demais tópicos do Comercial e dos outros módulos.
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

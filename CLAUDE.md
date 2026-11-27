# ERP para indústria de papelão — instruções para o Claude

## Ao iniciar uma conversa nova neste projeto

Antes de qualquer outra coisa, diga ao usuário onde o projeto parou e qual é o
próximo passo, com estas palavras (pode adaptar levemente):

> O protótipo da **tela inicial**, das **áreas de cada módulo** e do **Comercial › Vendas** está salvo
> aqui no repositório (`prototipo/tela-inicial-e-comercial.html`, link para ver:
> https://claude.ai/artifact/KrHFXtBn5s9YtySNMPGRM1, fotos em
> `docs/fotos/` e todas as decisões no `README.md`).
>
> Agora estamos montando o **mapa de funcionalidades** de todo o sistema, "no grosso":
> para cada módulo e área, quais **tópicos** (menus) e **funcionalidades** (itens que abrem
> janelas) existem. Os detalhes de cada tela vêm depois. Já está fechado:
> a área **Comercial › Vendas** inteira (Cadastros, Operações, Pedidos, Follow-up,
> Comissões, Consultas, Relatórios, Orçamentos), o **Portal do representante** e uma
> proposta para **Industrial › Engenharia de produto** e **Controladoria › Custos ›
> Orçamentos**, **Comercial › Crédito** e uma proposta para **Faturamento** e **NFe**
> (falta o print de Demonstrativos do Faturamento) e **Expedição** — o Comercial inteiro
> tem mapa inicial. No Industrial já estão Engenharia industrial, Engenharia de produto,
> PCP, Manutenção, Segurança e parte do Reporte de produção. O mapa geral fica em
> `docs/mapa-de-funcionalidades.md`. Pesagem e apontamentos do Reporte ficaram para
> depois. Suprimentos (Compras e Materiais) e Qualidade (Qualidade e Laboratório) já têm
> mapa; RNC e FSC ficaram para depois. O Financeiro inteiro já tem mapa. Próximo:
> Controladoria (Fiscal já tem mapa; faltam Contabilidade, Ativo imobilizado e resto de
> Custos); depois RH,
> Suporte e Gerencial. Padrão de nomes: Eventos → Operações, Demonstrativos → Consultas. Me
> mande o print do menu equivalente no sistema atual, ou peça uma proposta.

Depois disso, siga o que o usuário pedir. Quando o próximo passo mudar, atualize
esta seção para a conversa seguinte saber de onde continuar.

## Contexto

- Sistema de gestão (ERP) novo, feito do zero para indústria de papelão ondulado.
  Nome do produto ainda não definido (no protótipo não aparece nome, só o logo).
- O usuário fala português e não é programador: explique em linguagem de negócio,
  sem jargão técnico, e mostre as telas com fotos/prints quando mudar algo visual.
- Ele prefere ver e aprovar o visual no protótipo antes de construir de verdade.
- Níveis do sistema: **Módulo › Área › Tópico › Funcionalidade** (o usuário chamava
  funcionalidade de "característica"). As decisões ficam no `README.md` e o mapa completo
  em `docs/mapa-de-funcionalidades.md` (gerado a partir dos dados do protótipo).
- O usuário autorizou mover funcionalidades para o setor mais apropriado e avisar quando
  algo parecer fora do lugar.
- Todas as decisões de tela já aprovadas estão no `README.md`. Siga-as em telas novas
  (cores de papelão, módulos que abrem vazios, itens abrindo em janelas móveis etc.).

## Origem e reaproveitamento

- O sistema atual da empresa é o CRM Salute (`mvmanager/crm-salute`). Daqui só se
  aproveita o **motor de precificação** do Novo Comercial (`shared/precificacao/`
  naquele repositório) e a calculadora de caixa (`shared/calculadoraCaixa.ts`).
- O resto é construído do zero neste repositório.

## Hospedagem (plano)

- Construção na Render (mesma conta do sistema atual), com dados fictícios.
- Migração para Google Cloud, região São Paulo, quando estiver pronto.
- Construir pensando nessa mudança: Docker, PostgreSQL, configurações fora do
  código e arquivos enviados num armazenamento separado.

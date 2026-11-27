# ERP para indústria de papelão — instruções para o Claude

## Ao iniciar uma conversa nova neste projeto

Antes de qualquer outra coisa, diga ao usuário onde o projeto parou e qual é o
próximo passo, com estas palavras (pode adaptar levemente):

> O protótipo da **tela inicial**, das **áreas de cada módulo** e do **Comercial › Vendas** está salvo
> aqui no repositório (`prototipo/tela-inicial-e-comercial.html`, link para ver:
> https://claude.ai/artifact/KrHFXtBn5s9YtySNMPGRM1, fotos em
> `docs/fotos/` e todas as decisões no `README.md`).
>
> O **mapa de funcionalidades** "no grosso" está fechado por enquanto: 24 das 31 áreas,
> ~308 funcionalidades, em `docs/mapa-de-funcionalidades.md` (decisões no `README.md`).
> Ficaram para depois: Pesagem, apontamentos do Reporte, RNC, FSC, RH (Folha e
> Treinamento), Suporte › Usuários e permissões e Gerencial › Relatórios.
>
> Agora estamos na fase de **construção**: desenhar cada tela por dentro e montar a base do
> sistema de verdade. Já desenhadas no protótipo: a **ficha de Prospects e clientes**
> (aprovada, com ajustes de compactação) e **Pedidos** (primeira versão, esperando aprovação).
> Ver README › Telas desenhadas por dentro.
> Regra: o sistema atual é só referência de campos; o desenho é do nosso jeito.

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
- **Regra de desenho: telas compactas, sem espaço ocioso** (quadros e campos juntos, rótulos
  curtos, vários campos por linha). Vale para tudo.
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

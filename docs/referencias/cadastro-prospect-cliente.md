# Referência: cadastro de prospect e cliente no sistema atual

Usado **só como referência** para não esquecer nenhuma informação. A tela nova é desenhada
do nosso jeito (decisão do usuário: "o nosso diferencial será nesses detalhes").

## Prospect (sistema atual, tela VD118)

**Aba Geral**
- Prospect (código) · Data de cadastro
- Nome / Razão social
- Natureza jurídica · CNPJ / CPF
- CEP · Estado · Município · Logradouro · Tipo de logradouro · Número
- Status (ativo…) · Como tomou conhecimento da empresa?
- Área de vendas
- Tolerância de entrega (−) e (+)
- Exige selo FSC · Aceita impressão do selo FSC
- Produtos / serviços de interesse (texto livre)

**Aba Contato** (vários contatos por prospect)
- Nome · Departamento · DDD · Fone · Ramal · Fax · Celular · E-mail · Data de nascimento · Status

## Cliente (sistema atual, tela VD007)

**Aba Gerais**
- Cliente (código) · Nome / Razão social · Natureza jurídica · CNPJ / CPF
- Indicador de I.E. · Inscrição estadual
- Segmento econômico · Status · Código original · Nosso código no cliente
- Quadro "Relacionamento atual"

**Aba Endereço**
- CEP (com pesquisa de endereço e "montar auxílio ao endereço") · País · Estado · CEP único
- Município · Bairro · Logradouro · Número · Tipo de logradouro · Complemento · Caixa postal
- DDD · Fax · Fone

**Aba Adicionais**
- Transportador · Redespacho · Suframa · Data do cadastro · Avisar embarque
- Grupo de empresa · Área de vendas · Origem do cadastro
- Tolerância de entrega (−) e (+) · Emite certificado
- Tipo de pedido · Confirmar pedido · Qtde produto por NF · Qtde pedido por NF · Qtde dias transporte · Frete
- Exige selo FSC · Aceita impressão do selo FSC
- Usar distribuição do mesmo volume para vários itens do romaneio

**Aba Regras para vendas**
- Política de preço padrão · Índice de encargos (%)
- Transação para pedidos · Convênio ICMS · Convênio IPI
- Prazo de pagamento · Mensagem padrão
- Regra para data de embarque do pedido · Regra para controle de embalagens retornáveis
- Tolerância para data de entrega do pedido (para menos / para mais, em dias)
- Regime especial ICMS (número, válido até) · Termo de acordo IPI (número, válido até)

**Aba Regras para vendas II** (opções sim/não)
- Obedece regra crédito de ICMS · Aceita entrega com data anterior à atual
- Usar referência do cliente no item da NF-e · Enviar "Grupo compra" no XML da NF-e
- Enviar a OC nos dados complementares da NF-e · Definir quantidade de casas decimais
- Total da substituição tributária na primeira parcela
- Não mostrar revisão do produto no XML e no DANFE
- Mostrar na devolução de embalagens por grupo de empresa

**Aba Contatos** (vários)
- Nome · DDD · Fone · Ramal · Fax · Celular · E-mail · Departamento · Data de nascimento ·
  Status · CPF · Área de interesse
- Usos do contato: remessa eletrônica de títulos a receber · envio do arquivo de distribuição
  da NF-e · envio de certificado da qualidade · envio do EDI

**Outras abas (conteúdo ainda não enviado):** Entrega / Cobrança · Advertências · Restrições de vencimento ·
Padrões EDI · Atributos extras · Certificados · Financeiro · Ocorrências (na consulta).

**Consulta:** navegação registro a registro e "aproximar por" (busca).
**Relatório:** filtros por faixa de clientes, UF, município, representante, segmento; situação
(ativos/inativos); resumido ou completo; ordem por código ou razão social; "só clientes sem área
de vendas/representante"; imprimir, visualizar, exportar para planilha.

## Já decidido que entra na ficha (ver README)
Unidades do cliente, alterar nome fantasia, endereços de cobrança e de entrega (vários),
atributos extras, documentação (crédito), histórico do cliente, produto × endereço de entrega,
últimas compras, ocorrências, assuntos, grupo de empresas, segmento econômico, meios de
comunicação, tipos de bloqueio na entrega, nosso prazo × prazo do cliente, motivos de alteração
de data de entrega/quantidade, conta contábil.

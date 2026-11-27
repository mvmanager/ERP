Checagem de segurança

Ferramentas e pedido de revisão para testar a segurança dos sistemas.
Este documento pode ser enviado para outros chats ou pessoas para fazer
o mesmo trabalho.

1\. Quando fazer

- **Quando o sistema estiver pronto**, antes de colocar no ar para os
  usuários (pedido registrado no projeto).

- Antes de cada nova versão importante.

- Sempre que mexer em login, permissões, senhas ou dados de clientes.

- Uma vez por mês, como rotina.

**Ordem sugerida:** Gitleaks → Opengrep (e Bandit, se houver Python) →
revisão com o pedido do item 3 → OWASP ZAP no ambiente de testes.

2\. Ferramentas

| **Ferramenta** | **O que faz**                                                                                                                                        | **Quando usar**                                                            |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| Gitleaks       | Procura senhas, tokens e chaves esquecidas no código e em todo o histórico do git.                                                                   | Antes de subir código e em toda checagem. Pega a falha "chave exposta".    |
| Opengrep       | Lê o código-fonte (várias linguagens, inclusive JavaScript/TypeScript) e aponta trechos perigosos com arquivo e linha. É a versão aberta do Semgrep. | Em toda checagem. Pega input sem tratamento, rotas sem conferência e mais. |
| Bandit         | Lê código Python e aponta trechos perigosos com arquivo e linha.                                                                                     | Só se o sistema tiver partes em Python.                                    |
| OWASP ZAP      | Testa o sistema funcionando, por fora, como um atacante faria (formulários, páginas, rotas).                                                         | Com o sistema rodando, só no ambiente de testes e com autorização.         |

Como rodar (para o TI)

Gitleaks: procura segredos no repositório e no histórico

gitleaks detect --source . -v

Opengrep: análise do código com regras de segurança

opengrep scan --config \[pasta-ou-pacote-de-regras-de-seguranca\] .

Bandit: análise de código Python

bandit -r . -f txt

OWASP ZAP: teste rápido do sistema rodando (ambiente de testes)

docker run -t zaproxy/zap-stable zap-baseline.py -t
https://endereco-de-testes

> Atenção: só rode o OWASP ZAP contra sistemas da própria empresa e, de
> preferência, no ambiente de testes. Testar sistema de terceiros sem
> autorização é proibido.

3\. Pedido de revisão (copiar e colar)

Cole o texto abaixo num chat de IA junto com o código (ou o acesso ao
repositório):

> Revise este código atrás destas falhas de segurança:
>
> 1\. Banco sem tranca: tabelas sem RLS (segurança por linha) ou sem
> controle de acesso; usuário do banco com mais poder do que precisa;
> banco acessível de fora.
>
> 2\. Chave exposta: senhas, tokens, chaves de API, certificados ou
> dados de conexão escritos no código, em arquivos do repositório, no
> histórico do git ou enviados para o front-end (tela/navegador).
>
> 3\. Input sem tratamento: dado vindo do usuário (formulário, URL,
> arquivo enviado, API) usado sem validar ou limpar, abrindo espaço para
> SQL injection, XSS, upload malicioso e afins.
>
> 4\. Rota entregando dado pelo ID: endpoint que mostra, altera ou apaga
> um registro só pelo ID informado, sem conferir se aquele
> usuário/empresa tem direito a ele (IDOR).
>
> Para cada problema encontrado, liste arquivo por arquivo e linha por
> linha: arquivo, linha, qual das falhas é, gravidade (crítica, alta,
> média, baixa), por que é perigoso e como corrigir (com o trecho
> corrigido).
>
> No final, faça um resumo com o total de problemas por falha e por
> gravidade, e diga o que corrigir primeiro.

4\. O que cada falha significa

1.  **Banco sem tranca:** o banco deixa qualquer um ver ou mexer em
    dados que não são dele. No nosso ERP a proteção é o RLS (segurança
    por linha): cada empresa só vê o que é dela, cada representante só a
    sua carteira e a sua comissão.

2.  **Chave exposta:** senha ou chave escrita no código. Quem vê o
    código, ou o histórico dele, consegue entrar nos serviços. Tem que
    ficar num cofre de segredos, nunca no código.

3.  **Input sem tratamento:** o sistema confia no que o usuário digita.
    Um texto malicioso pode apagar dados, roubar sessão ou invadir.

4.  **Rota entregando dado pelo ID:** trocar o número no endereço (ex.:
    /pedido/4521 para /pedido/4522) mostra o pedido de outro cliente ou
    de outra empresa. O servidor precisa conferir o dono a cada pedido.

5\. Como pedir este documento ao Claude

Em qualquer conversa do projeto ERP, peça: "me envie o documento de
checagem de segurança". O arquivo fica no repositório em
docs/seguranca/checagem-de-seguranca.docx (e em versão texto em
docs/seguranca/checagem-de-seguranca.md).

# Pull Requests e Code Review

<!-- Este arquivo explica o workflow de Pull Requests e revisão de código no GitHub -->

## 📋 Objetivos de Aprendizagem

- Compreender o conceito e o propósito de um Pull Request.

- Dominar o fluxo de trabalho completo, desde a criação da branch até o merge.

- Aplicar boas práticas ao solicitar e realizar revisões de código (Code Review).

- Entender os diferentes estados e tipos de merge de um Pull Request.

## 🎯 Introdução
Pull Requests são o coração da colaboração em projetos de software modernos. Eles criam um ambiente seguro para que o código seja analisado, testado e discutido por outros desenvolvedores antes de ser integrado à base principal do projeto, evitando a introdução de bugs e garantindo o alinhamento com os padrões da equipe.

## O que é um Pull Request (PR)?

Um **Pull Request** (ou *Merge Request*, em algumas plataformas) é um **pedido formal para revisar e integrar mudanças** de uma branch em outra, geralmente da sua branch de trabalho para a `main`. Ele não é um comando do Git, e sim uma funcionalidade oferecida por plataformas de hospedagem de código como **GitHub**, **GitLab** e **Bitbucket**.

Na prática, um PR é o ponto de encontro entre o seu código e o resto do time: é onde a equipe lê, comenta, sugere alterações e finalmente decide se as mudanças entram (ou não) no projeto.

#### Onde Acontece

Pull Requests são uma feature da plataforma, não do Git em si:

| Plataforma | Nome usado    |
| ---------- | ------------- |
| GitHub     | Pull Request  |
| GitLab     | Merge Request |
| Bitbucket  | Pull Request  |

#### Anatomia de um Pull Request

Todo PR é composto por alguns elementos principais:

- **Title (título)**: resumo curto do que o PR faz.
- **Description (descrição)**: contexto, motivação e detalhes das mudanças.
- **Commits**: lista de commits que serão integrados.
- **Files changed**: diff com as alterações em cada arquivo (adições em verde, remoções em vermelho).
- **Comments / Reviews**: discussões, sugestões e aprovações feitas pelo time.

```
┌─────────────────────────────────────────────────────────┐
│ #42  Adiciona autenticação por token                    │
│ ─────────────────────────────────────────────────────── │
│ feature/auth-token  →  main                             │
│                                                         │
│ Description:                                            │
│   Implementa login via JWT conforme a issue #37.        │
│                                                         │
│ ▸ Commits (3)        ▸ Files changed (5)   ▸ Checks ✅  │
│ ▸ Reviewers: @ana, @bruno   Status: Open                │
└─────────────────────────────────────────────────────────┘
```

#### Fluxo Básico

Em poucas palavras, o ciclo de vida de um PR segue quatro etapas:

```
1. push branch  →  você envia sua branch para o repositório remoto
2. criar PR     →  abre o pedido de revisão na plataforma
3. review       →  o time discute, sugere mudanças e aprova
4. merge        →  as alterações são integradas à branch alvo (ex: main)
```


#### Status de um Pull Request

Um PR passa por diferentes estados ao longo do seu ciclo de vida:

| Status                | Significado                                                       |
| --------------------- | ----------------------------------------------------------------- |
| **Draft**             | Rascunho — trabalho em progresso, ainda não pronto para revisão.  |
| **Open**              | Aberto — pronto para ser revisado pelo time.                      |
| **Changes requested** | Revisor pediu alterações antes de aprovar.                        |
| **Approved**          | Aprovado — autorizado a ser integrado.                            |
| **Merged**            | Mesclado — alterações integradas à branch alvo.                   |
| **Closed**            | Fechado sem merge — descartado ou substituído por outro PR.       |

### Pull Request vs Merge

É comum confundir PR com merge, mas são coisas diferentes:

- **Commit** é uma ação **local**: você registra uma mudança no seu repositório.
- **Merge** é a operação técnica do Git que integra duas branches.
- **Pull Request** é o **processo de colaboração** que envolve revisar essas mudanças *antes* de fazer o merge.

Em outras palavras: você poderia simplesmente fazer `git merge` direto na `main` e pular o PR. Isso funciona, mas você perde toda a etapa de revisão, discussão e validação automática que o PR oferece.

| Aspecto       | Merge direto         | Pull Request               |
| ------------- | -------------------- | -------------------------- |
| Revisão       | Nenhuma              | Code review pelo time      |
| Discussão     | Não há espaço formal | Comentários linha a linha  |
| CI/CD         | Roda depois do merge | Roda **antes** do merge    |
| Rastreabilidade | Só no histórico    | Histórico + contexto + decisões |


### Por que Usar Pull Requests?

Além dos pontos comparados na tabela acima, o PR é o lugar onde o time aplica convenções de estilo, arquitetura e qualidade — mantendo a base de código coerente ao longo do tempo. Como bônus, PRs antigos viram documentação viva: registram **por que** aquela mudança foi feita, quem revisou e quais alternativas foram consideradas.

## Workflow com Pull Requests

O fluxo tradicional de trabalho em projetos colaborativos ou Open Source segue um padrão claro de etapas.

### Visão Geral

```
1. Fork do repositório (para projetos onde você não tem permissão de escrita)
2. Clone do seu fork para a máquina local
3. Criar uma nova Branch (ex: feature/nova-tela)
4. Fazer mudanças no código e commits
5. Push da branch para o seu fork no GitHub
6. Abrir o Pull Request na interface do GitHub
7. Revisão de código e discussão com a equipe
8. Ajustes locais e novos pushes (se necessário)
9. Aprovação do Pull Request
10. Merge na branch principal
```

## Criando um Pull Request

### Pré-requisitos

**Antes de abrir um PR, certifique-se de que:**

- Suas alterações estão em uma branch separada (nunca trabalhe direto na main).

- Seu código está testado localmente e funcionando.

- Seus commits possuem mensagens claras e descritivas.
- As alterações estão alinhadas com a issue que você se propôs a resolver.

### Passo a Passo

#### 1. Fazer Push da Branch

Primeiro, envie sua branch local para o repositório remoto:

```bash
git push origin nome-da-sua-branch
```

#### 2. Abrir PR no GitHub

Acesse a página do repositório no GitHub. Logo após fazer o push, o GitHub geralmente exibe um banner amarelo com o botão "Compare & pull request". Caso não apareça, vá até a aba "Pull requests" e clique no botão verde "New pull request", selecionando a sua branch como origem e a main como destino.

#### 3. Preencher Informações

Uma comunicação clara no Pull Request economiza tempo de todos os colaborados e envolvidos.

##### Título do PR

O título deve ser conciso e usar o padrão do projeto (ex: Conventional Commits).

- Exemplo ideal: feat: "adiciona autenticação por JWT na API."

- Exemplo ruim: atualizando arquivos.

##### Descrição
A descrição deve fornecer todo o contexto necessário para o revisor.

**Sempre inclua:**

- O que foi feito e qual problema isso resolve.

- Como o revisor pode testar as alterações localmente.

- Screenshots ou GIFs caso tenha alterado a interface (Front-end).
#### 4. Referenciar Issues

Você pode vincular o seu PR a uma Issue existente no GitHub. Se você usar palavras-chave específicas na descrição, o GitHub fechará a issue automaticamente quando o PR sofrer o merge.

Exemplos:  Closes #123, Fixes #456, Resolves #102.

## Anatomia de um Bom Pull Request

Um Pull Request, também conhecido como PR, é uma solicitação para que alterações feitas em uma branch sejam revisadas e, se aprovadas, incorporadas a outra branch do projeto, geralmente a branch principal.

Um bom Pull Request facilita o trabalho dos revisores, reduz riscos de erros, melhora a qualidade do código entregue e contribui para um histórico mais organizado dentro do repositório.

Quando bem estruturado, o PR permite que outras pessoas entendam rapidamente:

- O que foi alterado;
- Por que a alteração foi feita;
- Como testar a mudança;
- Quais impactos podem existir no sistema;
- Quais partes do código precisam de mais atenção na revisão.

---

### Tamanho

Pull Requests devem ser o menor possível, desde que ainda representem uma entrega coerente. PRs muito grandes, com centenas ou milhares de linhas de código, são mais difíceis de revisar, aumentam a chance de bugs passarem despercebidos e costumam demorar mais para serem aprovados.

O ideal é que cada PR tenha um objetivo claro e bem delimitado. Se uma funcionalidade for muito grande, ela deve ser dividida em partes menores, como criação de estrutura inicial, implementação da regra de negócio, criação de testes e ajustes de interface.

#### Exemplo de PR muito grande

```text
Implementa cadastro completo de usuários, login, recuperação de senha, tela administrativa, permissões e testes.
```

Esse tipo de PR concentra muitas responsabilidades em uma única entrega, dificultando a revisão e aumentando o risco de falhas.

#### Exemplo de divisão melhor

```text
PR 1: Cria estrutura inicial do módulo de usuários
PR 2: Implementa cadastro de usuários
PR 3: Implementa autenticação e login
PR 4: Adiciona recuperação de senha
PR 5: Cria testes automatizados do módulo
```

Essa divisão torna a revisão mais simples, permite aprovações mais rápidas e facilita a identificação de problemas caso algum erro seja introduzido.

Além disso, PRs menores ajudam o time a manter um fluxo contínuo de entrega, evitando grandes blocos de código parados por muito tempo aguardando revisão.

---

### Commits

Mantenha o histórico de commits limpo e organizado. Cada commit deve representar uma unidade lógica de mudança, ou seja, uma alteração com propósito claro dentro do desenvolvimento.

Evite commits genéricos ou pouco explicativos, pois eles dificultam a compreensão do histórico do projeto.

#### Exemplos de commits ruins

```text
Arrumando erro
Teste
Ajustes
Mudanças finais
Agora vai
```

Esses nomes não explicam o que foi alterado e dificultam futuras investigações no código.

#### Exemplos de commits melhores

```text
Adiciona validação de campos obrigatórios no cadastro de usuários
Corrige cálculo do valor total do pedido
Cria testes unitários para o serviço de autenticação
Refatora método de busca de produtos por categoria
Atualiza documentação do fluxo de Pull Request
```

Um bom commit ajuda outros desenvolvedores a entenderem a evolução do código e facilita investigações futuras, principalmente quando for necessário identificar quando um problema foi introduzido.

Também é importante evitar misturar assuntos diferentes no mesmo commit. Por exemplo, se você corrigiu um bug e também atualizou uma documentação, o ideal é separar essas alterações em commits diferentes.

#### Exemplo de separação adequada

```text
Corrige validação de e-mail no cadastro de usuários
Atualiza documentação do fluxo de cadastro
```

Dessa forma, o histórico fica mais claro e organizado.

---

### Descrição Clara

A descrição do Pull Request deve explicar de forma objetiva o que foi feito, por que foi feito e como a alteração pode ser testada. Nunca deixe a descrição em branco, pois o revisor precisa entender o contexto antes de analisar o código.

Quando o repositório possuir um template de PR, ele deve ser preenchido corretamente. Esse template normalmente inclui campos como descrição da alteração, tipo de mudança, evidências de teste e checklist.

#### Exemplo de descrição ruim

```text
Ajustes no cadastro.
```

Essa descrição é muito genérica e não ajuda o revisor a entender o objetivo da alteração.

#### Exemplo de descrição melhor

```markdown
## Descrição

Este PR implementa a validação dos campos obrigatórios no cadastro de usuários, garantindo que nome, e-mail e senha sejam informados antes do envio do formulário.

## O que foi alterado

- Adicionada validação no formulário de cadastro
- Incluídas mensagens de erro para campos obrigatórios
- Criados testes para validar os cenários de erro
- Ajustada a resposta da API para retornar mensagens mais claras

## Como testar

1. Acessar a tela de cadastro de usuários
2. Tentar enviar o formulário sem preencher os campos obrigatórios
3. Verificar se as mensagens de erro são exibidas corretamente
4. Preencher todos os campos e confirmar se o cadastro é realizado com sucesso
```

Uma descrição clara reduz dúvidas durante a revisão e evita comentários desnecessários pedindo explicações adicionais.

Além disso, uma boa descrição serve como documentação histórica da mudança. No futuro, outros desenvolvedores poderão consultar o PR para entender o motivo de determinada alteração ter sido realizada.

---

### Testes

Sempre teste as suas alterações localmente antes de abrir um Pull Request. Certifique-se de que a nova funcionalidade está funcionando conforme o esperado e que nenhuma parte existente do sistema foi quebrada.

Se o projeto possuir testes automatizados, execute-os na sua máquina antes de enviar o PR. Isso ajuda a garantir que a alteração não causou regressões.

#### Exemplos de comandos comuns para execução de testes

```bash
npm test
```

```bash
mvn test
```

```bash
gradle test
```

```bash
pytest
```

Além dos testes automatizados, também é importante realizar testes manuais quando a alteração envolver telas, fluxos de usuário ou integrações.

#### Exemplo de checklist de testes

```text
- [x] Executei os testes automatizados
- [x] Testei a funcionalidade localmente
- [x] Validei os principais cenários de erro
- [x] Verifiquei se não houve impacto em funcionalidades relacionadas
- [x] Incluí evidências, prints ou logs quando necessário
```

Quando possível, inclua no Pull Request evidências dos testes realizados, como prints da tela, logs de execução ou resultado dos testes automatizados. Isso aumenta a confiança do revisor e torna o processo de aprovação mais rápido.

#### Exemplo de evidência no PR

```text
Testes executados com sucesso:

- npm test
- Teste manual do fluxo de cadastro
- Validação dos cenários de erro no formulário
- Conferência da resposta da API no navegador
```

Testar antes de abrir um PR demonstra responsabilidade técnica e reduz retrabalho para o time.

---

### Título do Pull Request

O título do Pull Request deve ser claro, objetivo e indicar exatamente qual alteração está sendo proposta.

Um bom título ajuda o time a entender rapidamente o conteúdo do PR, mesmo antes de abrir a descrição completa.

#### Exemplo de título ruim

```text
Alterações gerais
```

#### Exemplo de título melhor

```text
Adiciona validação de campos obrigatórios no cadastro de usuários
```

Outro exemplo:

```text
Corrige cálculo de desconto no fechamento do pedido
```

O título deve evitar termos vagos como "ajustes", "correções diversas" ou "melhorias gerais", a menos que estejam muito bem explicados na descrição.

---

### Escopo Bem Definido

Um bom Pull Request deve ter escopo bem definido. Isso significa que ele deve resolver um problema específico ou entregar uma parte clara da funcionalidade.

Evite misturar muitas alterações diferentes no mesmo PR, como correção de bug, refatoração, alteração visual e nova funcionalidade ao mesmo tempo.

#### Exemplo de escopo ruim

```text
Corrige bug no login, altera layout da tela inicial, refatora serviço de usuários e atualiza documentação.
```

#### Exemplo de escopo melhor

```text
Corrige bug no login quando o usuário informa senha inválida.
```

Caso existam outras melhorias identificadas durante o desenvolvimento, o ideal é criar novos PRs ou novas tarefas para tratar esses pontos separadamente.

Essa prática facilita a revisão, reduz riscos e melhora o controle sobre o que está sendo entregue.

---

### Revisão de Código

A revisão de código é uma etapa importante do Pull Request. Ela permite que outros desenvolvedores analisem a solução proposta, identifiquem possíveis problemas e sugiram melhorias.

Ao abrir um PR, é importante solicitar revisão das pessoas corretas, preferencialmente alguém que conheça a área do sistema alterada ou que tenha contexto sobre a funcionalidade.

Durante a revisão, o autor do PR deve estar aberto a feedbacks e responder aos comentários de forma clara e respeitosa.

#### Boas práticas durante a revisão

```text
- Responder aos comentários dos revisores
- Explicar decisões técnicas quando necessário
- Corrigir os pontos levantados
- Evitar discussões pessoais
- Manter o foco na qualidade do código
```

A revisão não deve ser vista como uma crítica pessoal, mas como uma prática colaborativa para melhorar a qualidade do software.

---

### Checklist Antes de Abrir um Pull Request

Antes de abrir um Pull Request, é recomendado revisar alguns pontos importantes.

```text
- [ ] O PR possui um objetivo claro?
- [ ] O tamanho do PR está adequado?
- [ ] Os commits possuem mensagens explicativas?
- [ ] A descrição do PR foi preenchida corretamente?
- [ ] Os testes automatizados foram executados?
- [ ] A funcionalidade foi testada manualmente?
- [ ] O código segue o padrão do projeto?
- [ ] Não foram incluídas alterações desnecessárias?
- [ ] O PR está vinculado a uma issue, tarefa ou card?
- [ ] Foram adicionadas evidências quando necessário?
```

Esse checklist ajuda a evitar problemas simples e melhora a qualidade da entrega antes mesmo da revisão.

---

### Boas Práticas Complementares

Além dos pontos anteriores, um bom Pull Request também deve seguir algumas boas práticas adicionais:

- Ter um título claro e objetivo;
- Estar relacionado a uma tarefa, issue ou card do projeto;
- Não misturar muitas alterações diferentes no mesmo PR;
- Evitar mudanças desnecessárias de formatação em arquivos não relacionados;
- Manter o código alinhado ao padrão do projeto;
- Solicitar revisão das pessoas corretas;
- Responder aos comentários dos revisores de forma clara e respeitosa;
- Atualizar a documentação quando necessário;
- Garantir que a branch esteja atualizada com a branch principal;
- Evitar subir arquivos temporários, logs ou configurações locais.

#### Exemplo de arquivos que não devem ser enviados

```text
.env
logs/
node_modules/
target/
.idea/
.DS_Store
```

Esses arquivos geralmente são específicos do ambiente local ou gerados automaticamente, e não devem fazer parte do Pull Request.

---

### Exemplo de Estrutura de Pull Request

Abaixo está um exemplo de estrutura que pode ser utilizada na descrição de um Pull Request:

```markdown
## Descrição

Descreva de forma objetiva o que foi alterado neste PR.

## Motivação

Explique por que essa alteração foi necessária.

## O que foi alterado

- Item 1
- Item 2
- Item 3

## Como testar

1. Passo 1
2. Passo 2
3. Passo 3

## Evidências

Inclua prints, logs ou resultados de testes, se necessário.

## Checklist

- [ ] Testei localmente
- [ ] Executei os testes automatizados
- [ ] Atualizei a documentação, se necessário
- [ ] Verifiquei possíveis impactos em outras áreas
```

Essa estrutura torna o Pull Request mais organizado e facilita o trabalho de quem irá revisar.

---

### Conclusão

Um Pull Request bem estruturado demonstra organização, responsabilidade técnica e colaboração com o time.

Ao manter PRs pequenos, commits claros, descrições completas e testes bem executados, o processo de revisão se torna mais rápido, seguro e eficiente.

Mais do que apenas enviar código, abrir um bom Pull Request é uma forma de comunicar bem uma mudança, facilitar o trabalho dos revisores e contribuir para a qualidade geral do projeto.

## Code Review: Revisando PRs

### O que é Code Review?

O Code Review (Revisão de Código) é a prática de analisar e avaliar o código escrito por outro desenvolvedor antes que ele seja integrado oficialmente ao projeto principal (a branch `main`). Pense nisso como uma "revisão de texto" antes de publicar um livro: o objetivo não é julgar o autor, mas sim garantir que a obra final tenha a melhor qualidade possível, esteja livre de erros estruturais ou lógicos, e siga os padrões estabelecidos pelo projeto.

### Por que é importante?

O processo de Code Review é uma das ferramentas mais valiosas na engenharia de software moderna, pois atua como a última linha de defesa antes da produção. Sua importância reside em:

- **Prevenção de Bugs:** Um segundo (ou terceiro) par de olhos tem muito mais facilidade para identificar falhas lógicas, variáveis esquecidas ou problemas de segurança que passaram despercebidos pelo autor original.
- **Manutenção de Padrões:** Ajuda a garantir que todo o código do projeto siga o mesmo estilo e a mesma arquitetura, evitando que o repositório vire uma bagunça ("código espaguete").
- **Economia de Tempo:** Corrigir um erro durante a fase de revisão é infinitamente mais rápido e barato do que consertar um bug depois que ele já está rodando em produção.

### Benefícios para a equipe

Além das vantagens técnicas, o Code Review transforma a cultura da equipe de desenvolvimento:

- **Distribuição de Conhecimento:** Quando você lê o código de um colega, você aprende novas abordagens e funções. Ao mesmo tempo, o autor recebe dicas valiosas. Isso nivela o conhecimento técnico de todo o time.
- **Responsabilidade Compartilhada:** Se um bug chega à produção, a responsabilidade não é apenas de quem escreveu o código, mas também de quem o revisou e aprovou. A qualidade se torna um esforço coletivo.
- **Integração de Novos Membros:** Para desenvolvedores iniciantes, o Code Review é a melhor forma de entender as regras de negócio e os padrões do projeto de forma prática e supervisionada.
- **Comunicação Mais Forte:** O processo de revisão, quando focado no código e não na pessoa, exercita a empatia, a argumentação técnica e a comunicação construtiva dentro do grupo.

### Exemplo Prático: O que analisar em um Code Review?

Imagine que um colega submeteu o seguinte trecho de código em Python em um Pull Request:

``` python
# Código original na PR
def calc(v, t):
    return v + (v * t)
```
#### Como agir na revisão?
Em vez de focar apenas se o código funciona ou criticar as escolhas do autor, você deve avaliar a legibilidade e a manutenibilidade para o futuro do projeto. Um bom comentário de revisão seria:

> "A lógica do cálculo está ótima! Como sugestão, o que acha de renomearmos a função e as variáveis para ficarem mais descritivas, como calcular_preco_final(valor_produto, taxa_imposto)? Assim fica muito mais fácil para outros desenvolvedores entenderem o contexto no futuro!"

Este exemplo demonstra perfeitamente como o Code Review melhora o código e distribui boas práticas sem ofender o autor original.

### Como Ser um Bom Revisor
Revisar código exige empatia e atenção aos detalhes.

#### 1. Entender o Contexto
Nunca comece a ler o código diretamente. Leia a Issue associada, entenda o requisito de negócio e leia a descrição do PR.

#### 2. Revisar o Código

**O que você deve procurar durante a leitura:**

- O código resolve o problema proposto na Issue?

- A lógica está clara e fácil de entender?

- Existem vazamentos de memória, problemas de performance ou falhas de segurança?

- Os nomes de variáveis e funções fazem sentido?

- A documentação e os testes foram atualizados?
  
#### 3. Fazer Comentários Construtivos

O foco deve ser sempre a melhoria do código, nunca criticar o autor.

##### Exemplos de Bons Comentários

Exemplos de Bons Comentários:
```
✅ "Boa explicação! Sugiro adicionar um exemplo de uso para tornar mais claro."
✅ "Este código pode simplificar se usarmos a função map() do Javascript. O que você acha?"
✅ "Encontrei um typo na linha 23: 'comit' → 'commit'"
```

##### Exemplos de Comentários Ruins

Evitar esses tipos de comentários:
```
❌ "Está errado." (Não explica o porquê nem como melhorar)
❌ "Não sei por que você fez assim." (Tom agressivo)
❌ "Eu faria diferente." (Se não agrega valor à performance ou arquitetura, é apenas preciosismo)
```

#### 4. Usar Sugestões

O GitHub possui a funcionalidade "Add a suggestion" (Ctrl + G ou o ícone de documento com o +/-). Ela permite que você digite o código corrigido direto no comentário, e o autor pode aceitar a sugestão com um clique, aplicando o commit automaticamente.

#### 5. Solicitar Alterações ou Aprovar

**Ao finalizar a revisão no botão "Review changes", escolha a ação correta:**

- Comment: Apenas dúvidas e observações leves, sem aprovar ou bloquear.

- Approve: O código está excelente e liberado para merge.

- Request changes: O código tem problemas que precisam obrigatoriamente ser corrigidos antes de ser integrado.
  
## Respondendo a Code Review

### Como Autor do PR

Quando você abre um Pull Request, outras pessoas podem revisar sua contribuição e deixar comentários, sugestões ou pedidos de alteração. Isso é normal em projetos colaborativos e faz parte do processo de melhoria do conteúdo.

O objetivo da revisão não é apontar erros de forma negativa mas ajudar para que o Pull Request fique mais claro, correto e útil para todos que vão ler a documentação.

<!-- TODO: Como lidar com feedback -->

#### Recebendo Feedback

Ao receber feedback, leia cada comentário com calma antes de responder. Muitas vezes, o revisor está tentando ajudar a melhorar uma explicação, corrigir um detalhe ou deixar o texto mais fácil de entender para iniciantes.

A revisão deve ser vista como uma oportunidade de aprendizado. Mesmo que seja necessário fazer ajustes, isso não significa que sua contribuição está ruim. Significa apenas que ela pode ficar ainda melhor.

Boas práticas ao receber feedback:

- agradeça pelas sugestões;
- responda com educação;
- pergunte quando não entender algum comentário;
- aceite ajustes que deixem o conteúdo mais claro;
- mantenha o foco na melhoria do Pull Request.

Exemplo de resposta adequada:

```text
Obrigado pela sugestão! Vou ajustar essa parte para deixar a explicação mais clara.
```

<!-- TODO: Atitude positiva, não defensiva -->

#### Discutindo Construtivamente

Nem sempre o autor do Pull Request vai concordar imediatamente com uma sugestão. Nesses casos, é importante conversar de forma respeitosa e explicar o motivo da sua escolha.

Uma boa discussão deve focar no conteúdo, não na pessoa. Em vez de apenas recusar uma sugestão, tente explicar seu ponto de vista e abrir espaço para uma solução melhor.

Exemplo de resposta construtiva:

```text
Entendi sua sugestão. Eu escrevi dessa forma para deixar o exemplo mais simples para iniciantes. Você acha melhor manter assim ou detalhar um pouco mais?
```

Evite respostas curtas ou defensivas, como:

```text
Não vou mudar.
```

ou:

```text
Está certo do meu jeito.
```

Esse tipo de resposta pode dificultar a colaboração. O ideal é manter um diálogo educado e buscar a melhor solução para o projeto.


<!-- TODO: Quando discordar respeitosamente -->

#### Fazendo Alterações
Para atualizar um PR com as mudanças solicitadas pelo revisor, basta alterar o código localmente, commitar e fazer o push novamente na mesma branch:

Quando uma revisão solicitar mudanças, faça os ajustes na mesma branch usada para abrir o Pull Request. Não é necessário criar outro Pull Request.

Depois de editar o arquivo solicitado, use o Git para registrar e enviar as alterações novamente.

Fluxo básico:

```bash
# veja o que foi alterado
git status

# adicione o arquivo modificado
git add docs/04-pull-requests-e-review.md

# faça um novo commit
git commit -m "docs: ajusta seção sobre code review"

# envie para seu fork
git push origin nome-da-sua-branch
```

Depois do `git push`, o Pull Request será atualizado automaticamente no GitHub. Isso significa que o revisor verá as novas alterações no mesmo PR, sem que você precise abrir outro.

#### Marcar Conversas como Resolvidas

Depois de corrigir um comentário da revisão, responda explicando o que foi alterado. Em seguida marque a conversa como resolvida no GitHub.

Exemplo de resposta:

```text
Ajustei a explicação conforme sugerido e adicionei um exemplo prático.
```

Marcar conversas como resolvidas ajuda revisores e professores a acompanharem o que já foi corrigido e o que ainda precisa de atenção.

#### Referência

Para se aprofundar no fluxo de colaboração com Git e GitHub, consulte:

- [Pro Git Book (PT-BR)](https://git-scm.com/book/pt-br/v2)
## Estados de um Pull Request

Durante o seu ciclo de vida, um Pull Request passará por diferentes estados visíveis na plataforma:

### Draft (Rascunho)

Indica que o PR ainda está em desenvolvimento. É útil para mostrar à equipe o que você está construindo e pedir opiniões precoces, mas o botão de merge fica bloqueado. Revisores não são notificados de um Draft PR.

### Open (Aberto)

O PR está finalizado pelo autor e pronto para revisão. O código está aguardando o Code Review e a execução da pipeline de testes.

### Changes Requested

Um revisor analisou o código e marcou o PR exigindo modificações. O merge fica bloqueado até que o autor faça os ajustes e o revisor mude o status para "Approved".

### Approved

A revisão foi concluída com sucesso por um ou mais membros da equipe. O código foi validado tecnicamente e está liberado para integração.

### Merged

O estado final de sucesso. O código contido na branch do PR foi integrado oficialmente na branch de destino (ex: main) e já faz parte da base do projeto.

### Closed

O PR foi encerrado sem que o código fosse mesclado. Isso acontece se a feature for cancelada, se a abordagem adotada foi descartada, ou se houver um erro irreversível no PR.

## Merge de Pull Requests

### Tipos de Merge no GitHub


### Tipos de Merge no GitHub

Ao finalizar um Pull Request, o GitHub oferece três estratégias para integrar suas alterações à branch principal. Entender cada uma é essencial para manter um histórico limpo e colaborativo.

---

#### 1️.    Merge Commit (Merge tradicional)

**O que faz:** Cria um novo commit de "merge" que une as duas branches, preservando todo o histórico individual de cada uma.

**Diagrama:**

```
main:     A---B---C---M
                 \ /
feature:          D---E

```

**Quando usar:**
- Projetos open-source com múltiplos contribuidores
- Quando é importante preservar o histórico completo de cada feature
- Para rastrear exatamente quando e como uma feature foi integrada

**Comando equivalente no Git:**
```bash
git checkout main
git merge --no-ff feature-branch
```

**Vantagens:**
- Histórico completo e auditável
- Fácil de reverter se necessário
- Mostra claramente o contexto da feature

**Desvantagens:**
- Histórico pode ficar "poluído" com muitos merges
- Mais commits para navegar em projetos grandes

---

#### 2️.   Squash and Merge (Compactar e mesclar)

**O que faz:** Combina **todos os commits** da sua branch em **um único commit** antes de integrar à main.

**Diagrama:**
```
main:     A---B---C---[D+E+F]
                 \
feature:          D---E---F
```

**Quando usar:**
- Features pequenas com muitos commits de "WIP" ou correções
- Quando o histórico detalhado da feature não é relevante
- Para manter a branch main limpa e linear

**Comando equivalente no Git:**
```bash
git checkout main
git merge --squash feature-branch
git commit -m "feat: adiciona funcionalidade X completa"
```

**Vantagens:**
- Histórico da main limpo e objetivo
- Cada feature = 1 commit na main
- Ideal para deploy e changelogs

**Desvantagens:**
- Perde-se o histórico detalhado da feature
- Pode dificultar debugging se algo der errado
- Autores originais dos commits podem ser perdidos (configurável)

---

#### 3️.   Rebase and Merge (Rebase e mesclar)

**O que faz:** "Reescreve" os commits da sua branch como se tivessem sido feitos **em cima da main mais recente**, criando um histórico linear.

**Diagrama:**
```
main:     A---B---C---D'---E'---F'
                 \
feature:          D---E---F  (antes do rebase)
```

**Quando usar:**
- Quando se deseja um histórico completamente linear
- Para projetos que seguem filosofia "one branch, one commit"
- Em equipes que preferem `git pull --rebase`

**Comando equivalente no Git:**
```bash
git checkout feature-branch
git rebase main
git checkout main
git merge feature-branch  # fast-forward merge
```

**Vantagens:**
- Histórico linear e fácil de ler
- Sem commits de merge extras
- Ideal para `git bisect` e debugging

**Desvantagens:**
- Reescreve o histórico (cuidado com branches compartilhadas!)
- Pode causar conflitos complexos durante o rebase
- Não recomendado para branches públicas

---

#### Tabela de Decisão: Qual Merge Usar?

#### Tabela de Decisão: Qual Merge Usar?

| Cenário | Merge Commit | Squash | Rebase |
|---------|-------------|--------|--------|
| Feature grande com múltiplos desenvolvedores | Recomendado | Não recomendado | Com cautela |
| Correção rápida de bug | Não recomendado | Recomendado | Recomendado |
| Histórico detalhado é importante | Recomendado | Não recomendado | Com cautela |
| Main deve ter histórico linear | Não recomendado | Recomendado | Recomendado |
| Branch pública/compartilhada | Recomendado | Com cautela | Não recomendado |
| Preparando release/changelog | Não recomendado | Recomendado | Recomendado |

**Legenda:**
- **Recomendado**: Estratégia ideal para o cenário.
- **Não recomendado**: Evite usar nesta situação.
- **Com cautela**: Pode ser usado, mas exige atenção a detalhes específicos.


> **Dica**: Na dúvida, comece com **Squash and Merge** para features pequenas e **Merge Commit** para features complexas. Evite Rebase em branches que outras pessoas estão usando.

---

#### Cuidados Importantes

1. **Nunca faça rebase em branches públicas** que outras pessoas estão usando — isso reescreve o histórico e quebra o trabalho alheio.
2. **Comunique sua equipe** sobre a estratégia de merge adotada no projeto.
3. **Teste sempre** após o merge, especialmente ao usar rebase.
4. **Use mensagens de commit claras** — elas são ainda mais importantes no squash!

## Conflitos em Pull Requests

Conflitos ocorrem quando você e outro desenvolvedor alteram exatamente as mesmas linhas do mesmo arquivo, ou quando alguém deleta um arquivo que você estava modificando. O Git não sabe qual alteração manter e pausa para intervenção humana.

### Resolvendo na Interface do GitHub

Se o conflito for simples (mudança em linhas de texto comuns), o próprio GitHub oferece o botão "Resolve conflicts" no PR. Ele abrirá um editor web onde você pode remover as marcações do Git e escolher o trecho final de código.

### Resolvendo Localmente

```bash
# Atualiza as informações do repositório original
git fetch upstream

# Traz as atualizações da main para a sua branch (pode gerar o conflito aqui)
git merge upstream/main

# -> Abra o VS Code, encontre os arquivos marcados com conflito e ajuste o código.

# Salve, adicione as correções e finalize o merge
git add .
git commit -m "fix: resolve conflitos de merge com a main"
git push origin sua-branch
```

## CI/CD e Checks

Pull Requests modernos dependem de automação (Pipelines) para manter a integridade do código.

### Status Checks

São rotinas que o GitHub executa automaticamente sempre que um PR é aberto ou atualizado. Geralmente incluem:

- Linters: Verificam se a indentação e os padrões de código estão corretos.

- Testes Unitários: Rodam a suíte de testes da aplicação para garantir que nada quebrou.

- Segurança: Analisam vulnerabilidades em pacotes instalados.
Muitos repositórios exigem que todos os Status Checks fiquem verdes (passos com sucesso) antes de habilitar o botão de merge.

### Como Lidar com Checks Falhando

Se aparecer um "X" vermelho no seu PR:

1. Clique em "Details" ao lado do check que falhou.

2. Leia o log do terminal (geralmente apontará o erro exato e a linha).

3. Faça a correção no seu ambiente local, teste.

4. Faça o commit e o push novamente. O check rodará de forma automática.

## Templates de Pull Request

Muitos projetos utilizam um arquivo especial chamado PULL_REQUEST_TEMPLATE.md na raiz do repositório ou na pasta .github. Ele carrega um formulário automático toda vez que alguém clica em "New pull request". Isso ajuda a padronizar a documentação, forçando os desenvolvedores a preencherem checklists de testes, documentação e descrição.

## Boas Práticas

### Para quem Abre PRs

- Descreva bem as mudanças: Forneça contexto; explique o que e o porquê, não apenas o como.

- Mantenha PR focado: Uma funcionalidade/correção por PR.

- Seja responsivo a feedback: Acompanhe seu PR e responda rapidamente aos revisores.

- Teste antes de abrir: O Code Review não substitui o teste do próprio desenvolvedor.

### Para Revisores

- Seja respeitoso e construtivo: Promova um ambiente seguro para o aprendizado coletivo.

- Revise em tempo hábil: PRs parados por muitos dias atrapalham o cronograma e geram conflitos de código.

- Explique o "porquê" das sugestões: Compartilhe a referência ou documentação junto com a crítica.

- Reconheça bom trabalho: Elogie arquiteturas inteligentes e códigos bem escritos.

## Etiqueta de Code Review

### Código de Conduta

O ambiente de engenharia deve focar no produto, não em vaidades pessoais. Seja empático ao escrever comentários; lembre-se que texto não transmite tom de voz e pode soar rude se for curto demais. Critique a linha de código, jamais a capacidade de quem o escreveu.

### Tom de Comunicação

Utilize verbos colaborativos. Ao invés de usar o imperativo ("Mude essa função", "Corrija isso"), utilize sugestões abertas ("O que acha de extrairmos essa lógica para um módulo separado?", "Acredito que se usarmos o parâmetro X, o ganho de performance será melhor.").

## Ferramentas Úteis

### GitHub CLI

```bash
gh pr create
# Lista os PRs abertos no repositório
gh pr list
# Visualiza os detalhes e status do PR atual
gh pr view
# Realiza o merge do PR via linha de comando
gh pr merge
```

### Navegação no GitHub

O GitHub web possui atalhos de teclado produtivos em um PR:

- Na aba Files changed, pressione t para abrir a árvore de navegação de arquivos.

- Pressione v para visualizar o arquivo completo (não apenas o bloco com diferença).

- Clique no símbolo + na linha de código específica para abrir o painel de comentário localizado.

## Exemplos Práticos

### Exemplo 1: Primeiro Pull Request

**Você é encarregado de adicionar um botão na página de login.**

1. Cria a branch feat/btn-login.

2. Adiciona o HTML e CSS do botão.

3. Faz o push e abre o PR com o título: feat: adiciona botão de login social.

4. Na descrição, anexa uma foto do antes/depois da tela.
   
### Exemplo 2: Revisando um PR

**Você é o revisor do PR acima. Lê o código e nota que o botão não é responsivo no mobile.**

1. Seleciona o arquivo CSS e deixa um comentário na linha: "A classe do botão está com largura fixa. O que acha de usarmos width: 100% com um max-width para comportar telas menores?"

2. Coloca o status do PR como "Request Changes".

### Exemplo 3: Respondendo a Feedback

O autor recebe a notificação da falha de responsividade.

1. Corrige o CSS no VS Code, altera para width: 100%.

2. Faz o commit: git commit -m "style: ajusta responsividade do botão de login".

3. Dá git push.

4. No GitHub, clica em "Resolve conversation" e pede uma re-revisão. O revisor aprova e faz o merge.

## Métricas e Estatísticas

### Tempo de Revisão

É a métrica de quanto tempo um PR fica aberto até o primeiro comentário do revisor. Manter esse tempo baixo impede o acúmulo de tarefas, evita conflitos drásticos com outras features sendo desenvolvidas em paralelo e mantém o desenvolvedor focado no contexto do código recém-escrito.

### Taxa de Aprovação

Quantas idas e vindas (Request Changes) o PR precisou até ser aprovado. Uma taxa muito alta frequentemente indica problemas na especificação da tarefa original (Issue mal escrita) ou falta de alinhamento prévio da arquitetura da solução entre a equipe.

## Erros Comuns

### Erro 1: PR Muito Grande

Um Pull Request contendo 45 arquivos modificados e 2.000 linhas de código quase nunca será revisado de forma minuciosa (o chamado "LGTM" cego - Looks Good To Me). Solução: Divida o trabalho.

### Erro 2: Não Atualizar com a Main

Criar um PR de uma branch que está desatualizada há 3 semanas em relação à main. Isso gera conflitos e testes quebrados na pipeline. Solução: Sempre faça um git pull upstream main antes de iniciar seu dia e antes de abrir o PR.

### Erro 3: Não Testar Antes de Abrir

Abrir o PR com código que nem sequer compila localmente, confiando apenas nas automações do GitHub. Isso desperdiça recursos de CI e tempo da equipe.

### Erro 4: Não Responder a Comentários

Fazer alterações locais baseadas nos feedbacks, mas dar "push" ignorando as threads de conversa no GitHub, deixando o revisor confuso se a sugestão foi adotada, modificada ou descartada.

## Exercícios

**Para consolidar o conhecimento, tente praticar estas rotinas:**
1. Acesse o repositório deste guia, faça um fork, altere um arquivo e crie seu primeiro Pull Request em Draft para observar o estado e o bloqueio de Merge.

2. Peça a um colega para criar um Pull Request e pratique o envio de uma sugestão de Código com o status "Comment".

3. Receba um "Request Changes" no seu PR, modifique o arquivo no seu VS Code, faça o push e veja o PR atualizar automaticamente, finalizando ao clicar em "Resolve conversation".

4. Simule um conflito: crie duas branches baseadas na main, altere a mesma linha nas duas, faça o push e abra os dois PRs. Dê o merge no primeiro e tente dar o merge no segundo para praticar a resolução no editor do GitHub.

## Workflow Diagram

Fluxograma básico de um Pull Request:
```
Local                   Remoto (GitHub)
  
[ main ]                  [ main ]
   |                         | (10. Merge)
   |-- (3. Branch)           ^
   |                         | (9. Approve)
[ feature ]               [ feature PR ]
   |                         ^
   |-- (4. Commits)          | (7. Code Review)
   |                         |
   +------------------> (6. Open PR)
      (5. Push)
```

## Recursos Adicionais

Para aprofundar seu conhecimento na gestão do repositório, consulte estes links oficiais e guias de mercado:

- [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/)

- [eng-practices](https://google.github.io/eng-practices/review/)

- [GitHub Pull Request Documentation](https://docs.github.com/en/pull-requests)
- [Code Review Best Practices](https://google.github.io/eng-practices/review/)

## Resumo

Pull Requests e revisões de código são habilidades interpessoais e técnicas tão cruciais quanto o próprio ato de programar. Eles garantem a saúde do sistema, distribuem conhecimento, uniformizam padrões e criam um ambiente cooperativo. Ao dominar PRs pequenos, bem documentados e a arte de um feedback construtivo, você se torna um profissional pronto para atuar em times de engenharia de ponta.


# Revisão de Código: Como ser um bom revisor

A revisão de código (code review) é uma etapa essencial para manter a qualidade e consistência de qualquer projeto colaborativo. Mais do que apontar erros, é uma oportunidade de ensinar, aprender e melhorar o código em equipe.

## Antes de começar: mentalidade

- **A revisão é sobre o código, não sobre a pessoa.** Critique a implementação, não o autor.
- **Não leve para o lado pessoal.** Você e o revisor estão no mesmo time. Um código revisado em 10 minutos foi escrito em horas. Tenha humildade para ouvir.
- **Faça elogios.** Se algo ficou bom, diga! Isso incentiva os contribuidores.
- **Existem várias soluções para o mesmo problema.** Distinga entre boas práticas e gosto pessoal.

Fonte: [Dev.to](https://dev.to/christiantld/boas-praticas-de-code-review-para-bons-programadores-3999)[reference:0]

## O que revisar?

Use um checklist mental. Alguns pontos importantes:

- ✅ **Propósito:** Entendo o que o código faz? Ele cumpre o que a issue/PR descreve?
- ✅ **Lógica:** Existem bugs óbvios? Casos extremos (edge cases) foram tratados?
- ✅ **Segurança:** Validação de entrada? Risco de injeção SQL, XSS, etc.?
- ✅ **Performance:** Loops desnecessários? Consultas repetidas (N+1)?
- ✅ **Manutenibilidade:** Nomes de variáveis são claros? Funções fazem uma coisa só? Código complexo tem comentários?

Fonte: Google Engineering Practices[reference:1]

## Como dar feedback

### ✨ Escreva comentários objetivos e construtivos

Prefira frases como "Eu sugiro que..." em vez de acusações diretas.

- ❌ Evite: "Você está fazendo errado."
- ✅ Prefira: "O código faz X, mas talvez seja melhor Y porque Z."

### 🔍 Faça perguntas

Se algo não ficou claro, pergunte. Isso abre diálogo em vez de gerar conflito.

- Exemplo: "Não entendi por que essa validação foi feita aqui. Você pode explicar?"

### 📏 Use comentários em linha

No GitHub, você pode clicar no número de uma linha nos arquivos alterados ("Files changed") e deixar um comentário bem específico. Se quiser sugerir uma correção, use o botão `+/-` de "suggestion".

### 📦 Priorize o feedback

Separe o que é crítico (correção obrigatória) do que é sugestão de estilo.

- Exemplo de sugestão não bloqueante: *"[nit] Considere trocar esta variável de 'x' para 'userCount' para ficar mais claro. Não é impeditivo."*

Fonte: Code Review Excellence Playbook[reference:2]

## Como finalizar uma revisão no GitHub

Depois de comentar todas as linhas e sugerir mudanças, clique no botão **"Review changes"** (perto do canto superior direito). Você verá três opções:

| Opção            | Quando usar                                                                  |
| ---------------- | ---------------------------------------------------------------------------- |
| **Comment**      | Feedback geral sem aprovação. Útil se você pretende fechar o PR após revisar.|
| **Approve**      | O código está bom e pode ser mesclado (merge).                               |
| **Request changes** | Há problemas que precisam ser corrigidos antes do merge.                  |

Sempre agradeça ao contribuidor pelo esforço! Um simples "obrigado" faz muita diferença, especialmente para novos colaboradores.

Fonte: GitHub Docs[reference:3] e Carpentries GitHub Skills[reference:4]

## Dicas bônus

- **Limite o tamanho do PR:** Até 400 linhas por revisão. PRs muito grandes são cansativos e menos revisados.
- **Revisão não é formatação:** Use linters para isso. Foque em lógica e segurança.
- **Teste localmente se possível:** Para mudanças complexas, baixe o branch e teste na sua máquina.
- **Use o checklist do projeto** se houver um.

Fonte: Code Review Best Practices[reference:5]

---

## 💡 Boas práticas em um piscar de olhos

| Faça ✅                                 | Evite ❌                                   |
| --------------------------------------- | ------------------------------------------ |
| Critique o código, não a pessoa         | "Você fez isso errado"                     |
| Pergunte ("você considerou X?")         | Exija mudanças sem explicação              |
| Elogie partes boas                      | Foque só nos problemas                     |
| Seja específico e sugira melhorias      | Use sarcasmo ou hipérbole ("sempre", "nunca") |
| Forneça referências                     | Faça comentários vagos                     |

---

## 📚 Referências

- [Boas práticas de Code Review (Dev.to)](https://dev.to/christiantld/boas-praticas-de-code-review-para-bons-programadores-3999)
- [Google Engineering Practices – Code Review](https://google.github.io/eng-practices/review/)
- [GitHub Docs: About pull request reviews](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/about-pull-request-reviews)
- [Luizalabs – Guia de boas práticas para revisão de código](https://github.com/luizalabs/dev-guide/blob/master/code-review/README.md)
- [A practical guide for better, faster code reviews (GitHub)](https://github.com/mawrkus/pull-request-review-guide)

## 👥 Contribuidores

- [@marcos-vinicius](https://github.com/MarcosvvMarques) 

- [@RfaelDePadua](https://github.com/RfaelDePadua) - Seção "O que é um Pull Request (PR)?"
- [@cristianomendes3](https://github.com/cristianomendes3)

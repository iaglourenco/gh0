# Pull Requests e Code Review

<!-- Este arquivo explica o workflow de Pull Requests e revisão de código no GitHub -->

## 📋 Objetivos de Aprendizagem

<!-- TODO: Objetivos sobre PRs e revisão de código -->

## 🎯 Introdução

<!-- TODO: Por que Pull Requests são fundamentais para colaboração -->

## O que é um Pull Request (PR)?

<!-- TODO: Conceito de Pull Request -->
<!-- Não é um comando Git, é uma feature do GitHub -->

### Pull Request vs Merge

<!-- TODO: Diferença entre PR e merge direto -->

### Por que Usar Pull Requests?

<!-- TODO: Benefícios -->
<!-- Revisão, discussão, CI/CD, histórico, aprendizado -->

## Workflow com Pull Requests

<!-- TODO: Fluxo completo Fork → Branch → PR → Review → Merge -->

### Visão Geral

```
1. Fork do repositório
2. Clone do seu fork
3. Criar branch
4. Fazer mudanças e commits
5. Push para seu fork
6. Abrir Pull Request
7. Revisão e discussão
8. Ajustes (se necessário)
9. Aprovação
10. Merge
```

## Criando um Pull Request

### Pré-requisitos

<!-- TODO: O que você precisa antes de abrir PR -->

### Passo a Passo

#### 1. Fazer Push da Branch

```bash
# TODO: Comando para push
# git push origin nome-da-branch
```

#### 2. Abrir PR no GitHub

<!-- TODO: Interface do GitHub -->
<!-- Botão "Compare & pull request" -->
<!-- Descrição da tela de criação de PR -->

#### 3. Preencher Informações

<!-- TODO: Título, descrição, reviewers, labels, etc. -->

##### Título do PR

<!-- TODO: Boas práticas para título -->

##### Descrição

<!-- TODO: O que incluir na descrição -->
<!-- Contexto, mudanças, screenshots, etc. -->

#### 4. Referenciar Issues

<!-- TODO: Como linkar issues -->
<!-- Closes #123, Fixes #456, etc. -->

## Anatomia de um Bom Pull Request

### Tamanho

<!-- TODO: PRs pequenos vs grandes -->
<!-- PRs focados são melhores -->

### Commits

<!-- TODO: Commits limpos e organizados -->

### Descrição Clara

<!-- TODO: Template de descrição -->

### Testes

<!-- TODO: Garantir que tudo funciona -->

## Code Review: Revisando PRs

### O que é Code Review?

<!-- TODO: Processo de revisão por pares -->

### Por que Revisar Código?

<!-- TODO: Benefícios -->
<!-- Qualidade, bugs, aprendizado, padrões, etc. -->

### Como Ser um Bom Revisor

<!-- TODO: Atitudes e práticas -->

#### 1. Entender o Contexto

<!-- TODO: Ler a issue e descrição do PR -->

#### 2. Revisar o Código

<!-- TODO: O que procurar -->
<!-- Correção, clareza, design, testes, documentação -->

#### 3. Fazer Comentários Construtivos

<!-- TODO: Como comentar de forma útil -->

##### Exemplos de Bons Comentários

<!-- TODO: Comentários construtivos e respeitosos -->

```
✅ "Boa explicação! Sugiro adicionar um exemplo de uso para tornar mais claro."
✅ "Este código pode simplificar se usarmos... O que você acha?"
✅ "Encontrei um typo na linha 23: 'comit' → 'commit'"
```

##### Exemplos de Comentários Ruins

<!-- TODO: Evitar estes tipos -->

```
❌ "Está errado."
❌ "Não sei por que você fez assim."
❌ "Eu faria diferente."
```

#### 4. Usar Sugestões

<!-- TODO: Feature de sugestão do GitHub -->
<!-- Botão de suggestion -->

#### 5. Solicitar Alterações ou Aprovar

<!-- TODO: Request changes vs Approve vs Comment -->

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
git push origin fnd-lip/responde-code-review
```

Depois do `git push`, o Pull Request será atualizado automaticamente no GitHub. Isso significa que o revisor verá as novas alterações no mesmo PR, sem que você precise abrir outro.

#### Marcar Conversas como Resolvidas

Depois de corrigir um comentário da revisão, responda explicando o que foi alterado. Em seguida marque a conversa como resolvida no GitHub.

Exemplo de resposta:

```text
Ajustei a explicação conforme sugerido e adicionei um exemplo prático.
```

Marcar conversas como resolvidas ajuda revisores e professores a acompanharem o que já foi corrigido e o que ainda precisa de atenção.
<!-- TODO: Quando resolver threads de discussão -->

Para se aprofundar no fluxo de colaboração com Git e GitHub, consulte:

- [Pro Git Book (PT-BR)](https://git-scm.com/book/pt-br/v2)
## Estados de um Pull Request

### Draft (Rascunho)

<!-- TODO: PRs em progresso -->

### Open (Aberto)

<!-- TODO: Pronto para revisão -->

### Changes Requested

<!-- TODO: Aguardando alterações -->

### Approved

<!-- TODO: Aprovado para merge -->

### Merged

<!-- TODO: Integrado ao código base -->

### Closed

<!-- TODO: Fechado sem merge -->

## Merge de Pull Requests

### Tipos de Merge no GitHub

#### Merge Commit

<!-- TODO: Preserva todo histórico -->

#### Squash and Merge

<!-- TODO: Combina commits em um -->

#### Rebase and Merge

<!-- TODO: Reaplica commits linearmente -->

### Quando Usar Cada Tipo

<!-- TODO: Contextos e preferências de equipe -->

## Conflitos em Pull Requests

<!-- TODO: Como aparecem e como resolver -->
<!-- (Detalhes no capítulo 06) -->

### Resolvendo na Interface do GitHub

<!-- TODO: Editor de conflitos do GitHub -->

### Resolvendo Localmente

```bash
# TODO: Atualizar branch com main
# git fetch upstream
# git merge upstream/main
# Resolver conflitos
# git push
```

## CI/CD e Checks

<!-- TODO: Verificações automáticas em PRs -->
<!-- (Detalhes no capítulo 07 - GitHub Actions) -->

### Status Checks

<!-- TODO: O que são checks obrigatórios -->

### Como Lidar com Checks Falhando

<!-- TODO: Ver logs, corrigir, push novamente -->

## Templates de Pull Request

<!-- TODO: Como templates ajudam -->
<!-- PULL_REQUEST_TEMPLATE.md -->

## Boas Práticas

<!-- TODO: Lista de boas práticas -->

### Para quem Abre PRs

- <!-- Descreva bem as mudanças -->
- <!-- Mantenha PR focado -->
- <!-- Seja responsivo a feedback -->
- <!-- Teste antes de abrir -->

### Para Revisores

- <!-- Seja respeitoso e construtivo -->
- <!-- Revise em tempo hábil -->
- <!-- Explique o "porquê" das sugestões -->
- <!-- Reconheça bom trabalho -->

## Etiqueta de Code Review

### Código de Conduta

<!-- TODO: Respeito, empatia, foco no código não na pessoa -->

### Tom de Comunicação

<!-- TODO: Como se comunicar de forma profissional -->

## Ferramentas Úteis

### GitHub CLI

```bash
# TODO: Comandos gh para PRs
# gh pr create
# gh pr list
# gh pr view
# gh pr merge
```

### Navegação no GitHub

<!-- TODO: Atalhos de teclado -->
<!-- Abas: Conversation, Commits, Checks, Files changed -->

## Exemplos Práticos

### Exemplo 1: Primeiro Pull Request

<!-- TODO: Passo a passo completo para iniciante -->

### Exemplo 2: Revisando um PR

<!-- TODO: Processo de revisão passo a passo -->

### Exemplo 3: Respondendo a Feedback

<!-- TODO: Como iterar no PR -->

## Métricas e Estatísticas

### Tempo de Revisão

<!-- TODO: Por que revisar rapidamente importa -->

### Taxa de Aprovação

<!-- TODO: Iterações até aprovação -->

## Erros Comuns

### Erro 1: PR Muito Grande

<!-- TODO: Como evitar -->

### Erro 2: Não Atualizar com a Main

<!-- TODO: PR desatualizado, conflitos -->

### Erro 3: Não Testar Antes de Abrir

<!-- TODO: PR quebrado -->

### Erro 4: Não Responder a Comentários

<!-- TODO: Comunicação é essencial -->

## Exercícios

<!-- TODO: Exercícios práticos -->

1. <!-- Abrir seu primeiro PR -->
2. <!-- Revisar PR de um colega -->
3. <!-- Responder a feedback e atualizar PR -->
4. <!-- Resolver conflito em PR -->

## Workflow Diagram

<!-- TODO: Diagrama visual do fluxo de PR -->

## Recursos Adicionais

<!-- TODO: Links sobre PRs e code review -->

- [GitHub Pull Request Documentation](https://docs.github.com/en/pull-requests)
- [Code Review Best Practices](https://google.github.io/eng-practices/review/)
- <!-- Mais recursos -->

## Resumo

<!-- TODO: Pontos principais sobre PRs e code review -->

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->

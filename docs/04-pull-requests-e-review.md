# Pull Requests e Code Review

<!-- Este arquivo explica o workflow de Pull Requests e revisão de código no GitHub -->

## 📋 Objetivos de Aprendizagem

<!-- TODO: Objetivos sobre PRs e revisão de código -->

## 🎯 Introdução

<!-- TODO: Por que Pull Requests são fundamentais para colaboração -->

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
Pull Requests trazem benefícios que vão muito além de "juntar código":

- 🔍 **Code review** — outra pessoa lê seu código antes de ele entrar em produção, ajudando a pegar bugs, melhorar o design e compartilhar conhecimento.
- 💬 **Discussão estruturada** — dúvidas, sugestões e decisões ficam registradas no próprio PR, junto às linhas de código a que se referem.
- ⚙️ **CI/CD antes do merge** — testes automatizados, linters e checks rodam sobre o PR, garantindo que código quebrado não chegue à `main`.
- 📐 **Padrões consistentes** — o PR é o ponto onde o time aplica convenções de estilo, arquitetura e qualidade, mantendo a base de código coerente ao longo do tempo.
- 📚 **Histórico e aprendizado** — PRs antigos viram documentação viva: por que aquela mudança foi feita? Quem revisou? Quais alternativas foram consideradas?

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

<!-- TODO: Como lidar com feedback -->

#### Recebendo Feedback

<!-- TODO: Atitude positiva, não defensiva -->

#### Discutindo Construtivamente

<!-- TODO: Quando discordar respeitosamente -->

#### Fazendo Alterações

```bash
# TODO: Como atualizar o PR
# 1. Fazer mudanças localmente
# 2. Commit
# 3. Push (atualiza PR automaticamente)
```

#### Marcar Conversas como Resolvidas

<!-- TODO: Quando resolver threads de discussão -->

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
[@RfaelDePadua](https://github.com/RfaelDePadua) - Seção "O que é um Pull Request (PR)?"

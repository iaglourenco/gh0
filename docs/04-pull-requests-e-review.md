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

Antes de abrir um PR, certifique-se de ter:

- Uma conta no GitHub
- Um repositório com pelo menos uma branch diferente da `main` (ou um fork com uma branch)
- Commits feitos nessa branch com as suas alterações
- Permissão de escrita no repositório, ou um fork próprio

### Passo a Passo

#### 1. Fazer Push da Branch

Envie sua branch local para o GitHub com o comando:

```bash
git push origin nome-da-branch
```

Se for a primeira vez que você envia essa branch, o Git pode sugerir o comando completo:

```bash
git push --set-upstream origin nome-da-branch
```

#### 2. Abrir PR no GitHub

Após o push, acesse o repositório no GitHub. Você verá um **banner amarelo** no topo da página com uma mensagem como:

> "sua-branch had recent pushes X seconds ago"

Clique no botão verde **"Compare & pull request"** para iniciar a criação do PR.

Caso o banner não apareça, você também pode:
1. Clicar na aba **Pull requests**
2. Clicar em **New pull request**
3. Selecionar a branch de origem no menu **compare**

**Ao abrir a tela de criação do PR, verifique:**

- **Base branch**: a branch que vai *receber* as mudanças (geralmente `main`)
- **Compare branch**: a sua branch com as mudanças que você quer propor

**Criando PR a partir de um Fork:**

Se você está contribuindo para um repositório que não é seu (como neste projeto), o fluxo é o mesmo, mas você deve:

1. Navegar ao repositório **original** (upstream)
2. Clicar em **Compare & pull request** no banner
3. Clicar em **compare across forks**
4. Selecionar o repositório base (original) e a branch de destino
5. Selecionar o seu fork e a sua branch de origem

#### 3. Preencher Informações

Após confirmar as branches, preencha as informações do PR nos campos à direita:

- **Reviewers**: pessoas que você quer que revisem (ex: colegas, professor)
- **Assignees**: a pessoa responsável pelo PR (geralmente você mesmo)
- **Labels**: categorias como `documentation`, `bug`, `enhancement`
- **Milestone**: sprint ou marco relacionado

##### Título do PR

O título deve ser curto, descritivo e escrito no **imperativo** (como se fosse um comando):

```
✅ "Adiciona explicação sobre git commit"
✅ "Corrige typo na seção de branching"
✅ "Preenche conteúdo da seção git init"

❌ "Minha contribuição"
❌ "atualizei o arquivo"
❌ "WIP"
```

##### Descrição

A descrição é o lugar para **explicar o contexto e as mudanças**. Um bom modelo:

```markdown
## O que este PR faz?
Descreva o propósito principal das mudanças.

## O que mudou?
- Item 1 que foi alterado
- Item 2 que foi adicionado

## Como testar?
Passo a passo para verificar que as mudanças funcionam.

## Issues relacionadas
Fecha #Número-da-issue
```

> Se ainda não estiver pronto para revisão, clique na seta ao lado de **"Create pull request"** e selecione **"Create Draft Pull Request"**. PRs em rascunho não podem ser mergeados até serem marcados como prontos.

#### 4. Referenciar Issues

Você pode vincular seu PR a uma issue usando palavras-chave especiais na descrição. Quando o PR for mergeado, a issue será fechada automaticamente:

```markdown
Closes #123
Fixes #456
Resolves #789
```

Você pode referenciar múltiplas issues e de outros repositórios:

```markdown
Closes #123, Fixes #456
Closes usuario/repositorio#789
```

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

Cenário: você quer contribuir com o projeto `gh0` preenchendo uma seção de um arquivo de documentação.

```bash
# Passo 1: Fazer fork do repositório no GitHub (botão Fork)

# Passo 2: Clonar seu fork
git clone https://github.com/SEU-USUARIO/gh0.git
cd gh0

# Passo 3: Configurar o upstream
git remote add upstream https://github.com/iaglourenco/gh0.git

# Passo 4: Criar uma branch descritiva
git switch -c seu-nome/adiciona-secao-git-init

# Passo 5: Fazer as alterações no arquivo indicado na issue
# (editar docs/02-comandos-essenciais.md, por exemplo)

# Passo 6: Adicionar e fazer commit
git add docs/02-comandos-essenciais.md
git commit -m "docs: adiciona explicação sobre git init"

# Passo 7: Enviar a branch para o seu fork
git push origin seu-nome/adiciona-secao-git-init
```

Agora acesse o GitHub, clique em **"Compare & pull request"** no banner amarelo, preencha o título, a descrição (com `Closes #Número-da-issue`) e clique em **"Create pull request"**.

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

Fluxo completo de uma contribuição via Pull Request:

```
[Repositório Original]
        |
        | fork
        ↓
 [Seu Fork no GitHub]
        |
        | git clone
        ↓
 [Seu Computador (local)]
        |
        | git switch -c feature/minha-contribuicao
        ↓
  [Nova Branch local]
        |
        | editar arquivos
        | git add + git commit
        ↓
  [Commits na Branch]
        |
        | git push origin feature/minha-contribuicao
        ↓
 [Branch no Seu Fork]
        |
        | Abrir Pull Request no GitHub
        ↓
  [Pull Request Aberto]
        |
        |--- CI/CD checks (automático)
        |--- Revisão por pares
        |--- Discussão e ajustes
        ↓
     [Aprovado]
        |
        | Merge
        ↓
[Repositório Original (main)]
```

## Recursos Adicionais

<!-- TODO: Links sobre PRs e code review -->

- [GitHub Pull Request Documentation](https://docs.github.com/en/pull-requests)
- [Code Review Best Practices](https://google.github.io/eng-practices/review/)
- [Beginner's Guide to GitHub: Creating a Pull Request](https://github.blog/developer-skills/github/beginners-guide-to-github-creating-a-pull-request/)
- [Creating a Pull Request from a Fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork)
- <!-- Mais recursos -->

## Resumo

Um **Pull Request** é a principal forma de colaborar no GitHub. Ele não é um comando Git, mas uma funcionalidade da plataforma que permite propor, revisar e discutir mudanças antes de integrá-las ao projeto.

**Para criar um PR:**
1. Crie uma branch, faça commits e envie com `git push origin nome-da-branch`
2. No GitHub, clique em **Compare & pull request** no banner amarelo
3. Selecione a **branch de destino** (base) e a **branch de origem** (compare)
4. Preencha um título descritivo, uma descrição clara e vincule a issue com `Closes #Número`
5. Clique em **Create pull request** (ou **Draft** se ainda não estiver pronto)
6. Aguarde revisão, responda aos comentários e atualize o PR com novos commits
7. Após aprovado, o mantenedor faz o merge

**Boas práticas essenciais:**
- PRs pequenos e focados são melhores do que PRs grandes
- Descreva bem o que foi feito e por quê
- Teste as mudanças antes de abrir o PR
- Seja responsivo: responda comentários em tempo hábil
- Revisores: sejam construtivos, empáticos e expliquem o porquê das sugestões

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->

- [@gomesgeorgelucas](https://github.com/gomesgeorgelucas) - Passo a passo de como criar um Pull Request

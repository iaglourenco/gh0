# Branching e Merge

<!-- Este arquivo explica como trabalhar com branches e fazer merge no Git -->

## 📋 Objetivos de Aprendizagem

<!-- TODO: Objetivos de aprendizagem sobre branches e merge -->

## 🎯 Introdução

<!-- TODO: Por que branches são importantes? -->
<!-- Desenvolvimento paralelo, experimentação segura, organização -->

## O que são Branches?

<!-- TODO: Conceito de branch -->
<!-- Analogia: linha do tempo alternativa, universo paralelo, etc. -->

### Por que Usar Branches?

<!-- TODO: Benefícios de trabalhar com branches -->

### Visualizando Branches

<!-- TODO: Como branches funcionam visualmente -->
<!-- Use diagramas ASCII ou descrição clara -->

```
main:     A---B---C---D
               \
feature:        E---F
```

## Branch Principal (main/master)

<!-- TODO: O que é a branch principal -->
<!-- Histórico: master → main -->
<!-- Por que geralmente é protegida -->

## Trabalhando com Branches

### Listar Branches

```bash
# TODO: Comando para listar branches
# git branch
# git branch -a (incluindo remotas)
```

### Criar uma Nova Branch

```bash
# TODO: Como criar branch
# git branch <nome-da-branch>
# Convenções de nomenclatura
```

#### Boas Práticas de Nomenclatura

<!-- TODO: Padrões de nomes de branches -->
<!-- Exemplos: feature/login, fix/bug-123, docs/readme -->

### Trocar de Branch

```bash
# TODO: Como mudar de branch
# git checkout <branch>
# git switch <branch> (comando novo recomendado)
```

### Criar e Trocar em Um Comando

```bash
# TODO: Atalho para criar e trocar
# git checkout -b <nome>
# git switch -c <nome>
```

## Estados do Working Directory

<!-- TODO: O que acontece quando você troca de branch? -->
<!-- Arquivos mudam, mudanças não commitadas, etc. -->

### Mudanças Não Commitadas

<!-- TODO: Como Git lida com mudanças não salvas ao trocar branch -->

## Merge: Unindo Branches

<!-- TODO: Conceito de merge -->

### O que é Merge?

Merge é o processo de integrar as alterações de uma branch em outra no Git.

Ele é necessário porque permite desenvolver funcionalidades de forma isolada em feature branches, testar as mudanças e depois incorporá-las à branch principal de forma controlada. A branch que recebe o merge é chamada de branch base.

Um fluxo comum é: criar branch -> implementar -> testar -> fazer merge -> deletar a branch. Alguns cenários comuns são `feature` -> `main`, `hotfix` -> `main` e merge em `staging` antes de enviar para `production`.

O resultado pode ser um fast-forward ou um novo commit de merge, dependendo do histórico das branches.

### Sintaxe Básica

```bash
git switch main
git merge <nome-da-branch>
```

Para realizar um merge:

1. Acesse a branch de destino (branch base)
2. Execute o comando `git merge` com o nome da branch de origem

### Exemplo de Merge

```bash
git switch -c feature/login
# faz alterações e commits

git switch main
git merge feature/login
```

Nesse processo, o Git integra o histórico da branch `feature/login` na branch `main`.

## Tipos de Merge

### Fast-Forward Merge

O fast-forward merge acontece quando a branch base não possui commits novos em relação à branch que será mesclada.

Nesse caso, o Git apenas "avança" o ponteiro da branch, sem criar um novo commit de merge.

```
Antes:
main:    A---B
              \
feature:       C---D

Depois (fast-forward):
main:    A---B---C---D
```

### Three-Way Merge

Ocorre quando existem commits diferentes em ambas as branches.

Nesse caso, o Git cria um novo commit de merge para unir os históricos.

```
Antes:
main:    A---B---C
              \
feature:       D---E

Depois (merge commit):
main:    A---B---C---F
              \     /
feature:       D---E
```

Esse novo commit (`F`) é chamado de merge commit.

### Merge Commit

Um merge commit registra a união de duas branches. Ele tem dois parents: um da branch base e outro da branch que foi integrada.

## Estratégias de Merge

### --ff (Fast-Forward)

<!-- TODO: Comportamento padrão -->

```bash
# TODO: Explicar opção --ff
```

### --no-ff (No Fast-Forward)

<!-- TODO: Forçar merge commit -->

```bash
# TODO: Quando usar --no-ff
```

### --squash

<!-- TODO: Comprimir commits -->

```bash
# TODO: Exemplo de squash merge
```

## Deletando Branches

```bash
# TODO: Como deletar branch local
# git branch -d <branch> (seguro)
# git branch -D <branch> (forçado)

# Deletar branch remota
# git push origin --delete <branch>
```

### Quando Deletar Branches

<!-- TODO: Após merge, branches antigas, etc. -->

## Visualizando o Grafo

```bash
# TODO: Ver histórico de branches
# git log --graph --oneline --all
```

## Branch Tracking

<!-- TODO: Conceito de tracking branches -->

### Upstream Branch

<!-- TODO: O que é upstream -->

```bash
# TODO: Configurar upstream
# git branch -u origin/<branch>
# git push -u origin <branch>
```

## Exemplos Práticos

### Exemplo 1: Feature Branch Workflow

<!-- TODO: Fluxo completo de desenvolvimento de feature -->

```bash
# 1. Criar branch
# 2. Desenvolver feature
# 3. Fazer merge
# 4. Deletar branch
```

### Exemplo 2: Merge de Múltiplas Features

<!-- TODO: Cenário com várias branches -->

### Exemplo 3: Desfazendo um Merge

<!-- TODO: Como reverter merge (git reset, git revert) -->

## Boas Práticas

<!-- TODO: Lista de boas práticas com branches -->

- <!-- Manter branches pequenas e focadas -->
- <!-- Commits frequentes -->
- <!-- Merge regularmente da main -->
- <!-- Deletar branches após merge -->
- <!-- Nomear branches descritivamente -->

## Workflows Comuns

### Feature Branch Workflow

<!-- TODO: Explicar esse workflow -->

### Gitflow

<!-- TODO: Introdução básica ao Gitflow -->
<!-- (Detalhado no capítulo 07) -->

## Conflitos de Merge

<!-- TODO: Introdução básica a conflitos -->
<!-- (Detalhado no capítulo 06 - Resolução de Conflitos) -->

### O que São

<!-- TODO: Quando ocorrem -->

### Exemplo Simples

<!-- TODO: Exemplo básico de conflito e resolução rápida -->

## git stash

<!-- TODO: Salvando mudanças temporariamente -->

### Quando Usar Stash

<!-- TODO: Cenários de uso -->

```bash
# TODO: Comandos stash básicos
# git stash
# git stash pop
# git stash list
```

## Comparando Branches

```bash
# TODO: Como ver diferenças entre branches
# git diff <branch1>..<branch2>
```

## Erros Comuns

### Erro 1: Merge na Branch Errada

<!-- TODO: Como evitar e como reverter -->

### Erro 2: Deletar Branch Sem Merge

<!-- TODO: Perda de trabalho, recuperação -->

### Erro 3: Não Atualizar a Main Antes de Criar Branch

<!-- TODO: Por que isso causa problemas -->

## Exercícios

<!-- TODO: Exercícios práticos -->

1. <!-- Criar branch, fazer commits, fazer merge -->
2. <!-- Experimentar fast-forward vs three-way merge -->
3. <!-- Visualizar grafo de branches -->
4. <!-- Deletar branches após merge -->

## Diagrama de Workflow

<!-- TODO: Diagrama visual do fluxo de trabalho com branches -->

## Recursos Adicionais

<!-- TODO: Links sobre branching e merging -->

- [Learn Git Branching](https://learngitbranching.js.org/)
- [Atlassian Git Branching Tutorial](https://www.atlassian.com/git/tutorials/using-branches)
- <!-- Mais recursos -->

## Resumo

<!-- TODO: Pontos principais sobre branches e merge -->

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->

# Branching e Merge

<!-- Este arquivo explica como trabalhar com branches e fazer merge no Git -->

## 📋 Objetivos de Aprendizagem

- Compreender o que são branches e como funcionam
- Criar, listar, trocar e deletar branches
- Entender o papel do HEAD
- Trabalhar com múltiplas linhas de desenvolvimento paralelas
- Aplicar boas práticas de nomenclatura

## 🎯 Introdução

Branches são fundamentais para o desenvolvimento de software moderno. Eles permitem trabalhar em paralelo sem interferir no código principal, facilitando experimentação segura, correção de bugs e desenvolvimento de novas funcionalidades de forma organizada.

## O que são Branches?

Uma **branch** (ramificação) é uma referência leve que aponta para um commit específico no histórico do repositório. Em termos técnicos, um branch é simplesmente um ponteiro (pointer) para um hash SHA-1 de um commit.

### Analogia Visual

Pense em uma árvore:

- O **tronco** representa a branch principal (main)
- Os **galhos** são branches secundárias
- Cada commit é um ponto na história onde você tomou um caminho diferente

### Como Funcionam

```
Commit:    A        B        C        D        (main)
              ↓        ↓        ↓        ↓
            1a2b3c   4d5e6f   7g8h9i   0j1k2l   (hash dos commits)
              │
              └─ Another-branch (ponteiro para C)
```

Cada branch armazena apenas o hash do commit mais recente. O Git entãofollow a cadeia de commits pais para construir o histórico completo.

### Por que Usar Branches?

| Benefício                         | Descrição                                                                            |
| ---------------------------------- | -------------------------------------------------------------------------------------- |
| **Isolamento**               | Cada feature ou correção pode ser desenvolvida isoladamente                          |
| **Desenvolvimento Paralelo** | Multiple desenvolvedores podem trabalhar em diferentes funcionalidades simultaneamente |
| **Experimentação Segura**  | Alterações experimentais não afetam o código em produção                         |
| **Organização**            | Separação clara entre trabalho em andamento e código estável                       |

### Ciclo de Vida de uma Branch

1. **Criar** - Iniciar uma nova linha de desenvolvimento
2. **Trabalhar** - Fazer commits com alterações
3. **Merge** - Integrar as mudanças à branch destino
4. **Deletar** - Remover a branch após a integração

### Visualizando Branches

Um branch é simplesmente um ponteiro (reference) que aponta para um commit específico. O Git usa essa referência para navegar pelo histórico de commits.

#### Diagrama de Múltiplas Branches

```
       main:     A---B---C---D---E
                │
                └─ feature/login:       F---G---H
                           │
                           └─ bugfix/error:        I---J
```

- **A, B, C, D, E**: Commits na branch main
- **F, G, H**: Commits na branch feature/login (começa a partir de E)
- **I, J**: Commits na branch bugfix/error (começa a partir de H)

#### HEAD: O Ponteiro Atual

O **HEAD** é uma referência especial que indica o commit (e branch) atual onde você está trabalhando.

```
HEAD -> main -> D (você está na branch main, no commit D)
```

Quando você muda de branch, o HEAD é atualizado para apontar para a nova branch.

## Branch Principal (main/master)

A branch **main** (anteriormente chamada de **master**) é a branch padrão do repositório. Ela representa a linha principal de desenvolvimento e, geralmente, contém o código que está em produção.

### Características

- É criada automaticamente ao inicializar um repositório Git
- Geralmente contém o código mais estável e deployável
- Frequentemente protegida em repositórios remotos (não permite push direto)
- Serve como base para criar outras branches

### Histórico: master → main

Recentemente, a comunidade Git mudou de **master** para **main** como nome padrão, adotando uma linguagem mais inclusiva. Repositórios novos já usam **main** por padrão.

## Trabalhando com Branches

### Listar Branches

```bash
# Listar branches locais
git branch

# Listar todas as branches (locais e remotas)
git branch -a

# Listar branches com último commit
git branch -v

# Listar branches que já foram mescladas na branch atual
git branch --merged

# Listar branches que ainda não foram mescladas
git branch --no-merged
```

### Criar uma Nova Branch

```bash
# Criar uma nova branch (sem trocar para ela)
git branch <nome-da-branch>

# Exemplo
git branch feature/login
```

#### Boas Práticas de Nomenclatura

Use nomes descritivos e consistentes para suas branches:

| Prefixo                 | Uso                   | Exemplo                    |
| ----------------------- | --------------------- | -------------------------- |
| `feature/`            | Novas funcionalidades | `feature/login-social`   |
| `fix/` ou `bugfix/` | Correção de bugs    | `fix/bug-login-123`      |
| `hotfix/`             | Correções urgentes  | `hotfix/erro-producao`   |
| `docs/`               | Documentação        | `docs/readme-atualizado` |
| `refactor/`           | Refatoração         | `refactor/auth-service`  |
| `experiment/`         | Experimentos          | `experiment/nova-api`    |

### Dicas

- Use letras minúsculas e hifens para separar palavras
- Inclua o número da issue quando aplicável: `feature/login-#123`
- Mantenha nomes curtos mas descritivos

### Trocar de Branch

```bash
# Trocar para uma branch existente
git checkout <nome-da-branch>

# OU (comando mais moderno)
git switch <nome-da-branch>

# Exemplo
git checkout feature/login
git switch feature/login
```

> **Nota:** O `git switch` é recomendado pois é mais específico que `git checkout` (que também serve para outras coisas).

### Criar e Trocar em Um Comando

```bash
# Criar e trocar para nova branch em um comando
git checkout -b <nome-da-branch>

# OU (comando mais moderno)
git switch -c <nome-da-branch>

# Exemplo
git checkout -b feature/login
git switch -c feature/login
```

> `-c` significa "create" (criar)

## Estados do Working Directory

Quando você troca de branch, o Git altera o conteúdo do seu diretório de trabalho para refletir o estado da branch selecionada.

### O que Acontece ao Trocar de Branch

1. O Git identifica o commit pela nova branch
2. Os arquivos no diretório de trabalho são atualizados para esse commit
3. O ponteiro HEAD é atualizado para apontar para a nova branch

### Cenário Comum

```
1. Você está na branch main com arquivos da versão 1.0
2. Troca para feature/nova-func
3. Seus arquivos agora mostram a versão com a nova funcionalidade
4. Trabalha e faz commits nessa versão
5. Troca de volta para main
6. Seus arquivos voltam para a versão original
```

### Mudanças Não Commitadas

Se você tiver alterações não salvas (não commitadas) e tentar trocar de branch, o Git impedirá a troca para evitar perda de trabalho.

```bash
# Você estar em main com mudanças não commitadas
$ git status
On branch main
Changes not staged for commit:
  modified:   arquivo.txt

# Tentando trocar de branch
$ git checkout feature/nova
error: Your local changes would be overwritten by checkout.
Please commit them or stash them before you switch branches.
```

#### Soluções

1. **Fazer commit** das mudanças antes de trocar
2. **Stash** (salvar temporariamente): `git stash`

```bash
# Salvar mudanças temporariamente
git stash

# Trabalhar na nova branch
git checkout feature/nova
# ... fazer trabalho ...

# Voltar para a branch anterior
git checkout main

# Restaurar as mudanças salvas
git stash pop
```

## Merge: Unindo Branches

<!-- TODO: Conceito de merge -->

### O que é Merge?

<!-- TODO: Integrar mudanças de uma branch em outra -->

### Sintaxe Básica

```bash
# TODO: Como fazer merge
# git merge <nome-da-branch>
# Primeiro checkout para branch destino, depois merge
```

### Exemplo de Merge

```bash
# TODO: Exemplo completo
# 1. Criar feature branch
# 2. Fazer commits
# 3. Voltar para main
# 4. Fazer merge
```

## Tipos de Merge

### Fast-Forward Merge

<!-- TODO: O que é fast-forward -->

<!-- Quando acontece: quando não há commits divergentes -->

```
Antes:
main:    A---B
              \
feature:       C---D

Depois (fast-forward):
main:    A---B---C---D
```

### Three-Way Merge

<!-- TODO: O que é three-way merge -->

<!-- Quando acontece: quando há commits em ambas as branches -->

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

### Merge Commit

<!-- TODO: O que é um merge commit -->

<!-- Tem dois parents -->

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

Este conteúdo é colaborativo. Contribuidores deste arquivo:

- [@daniballester](https://github.com/daniballester) - Issue #19 - Seção "O que são Branches"

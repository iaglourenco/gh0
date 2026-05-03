# Comandos Essenciais do Git

<!-- Este arquivo documenta os comandos Git fundamentais que todo desenvolvedor deve conhecer -->

## 📋 Objetivos de Aprendizagem

<!-- Liste aqui os objetivos de aprendizagem deste capítulo -->
<!-- Ao final, o aluno deve saber usar os comandos básicos do Git -->

<!-- TODO: Adicione 3-5 objetivos de aprendizagem -->

## 🎯 Introdução

<!-- Introdução sobre comandos Git e sua importância -->
<!-- Por que aprender linha de comando? -->

## Estrutura dos Comandos Git

<!-- TODO: Explique a estrutura geral dos comandos Git -->
<!-- Formato: git <comando> <opções> <argumentos> -->

###  Obtendo Ajuda

<!-- TODO: Como obter ajuda sobre comandos Git -->

```bash
# TODO: Adicione comandos para obter ajuda
# git help <comando>
# git <comando> --help
```

## git init

<!-- TODO: Explique o comando git init -->
<!-- O que faz? Quando usar? O que acontece nos bastidores? -->

### Sintaxe

```bash
# TODO: Sintaxe do comando
```

### Quando Usar

<!-- TODO: Cenários de uso -->

### Exemplo Prático

```bash
# TODO: Exemplo completo de uso
# 1. Criar pasta
# 2. Executar git init
# 3. Verificar resultado
```

### O que Acontece

<!-- TODO: O que git init faz no sistema de arquivos? -->
<!-- Pasta .git criada, etc. -->

## git clone

<!-- TODO: Explique o comando git clone -->

### Sintaxe

```bash
# TODO: Sintaxe básica e variações
```

### Diferença entre init e clone

<!-- TODO: Quando usar cada um? -->

### Exemplo Prático

```bash
# TODO: Exemplo de clone de um repositório
```

### Clonando seu Fork

<!-- TODO: Como clonar um fork do GitHub -->

## git add

<!-- TODO: Explique o comando git add -->
<!-- Staging area concept -->

### Sintaxe

```bash
# TODO: Diferentes formas de usar git add
# git add <arquivo>
# git add .
# git add -A
# git add -u
```

### Staging Area

<!-- TODO: O que é staging area? -->
<!-- Por que existe? Qual sua utilidade? -->

### Exemplos

```bash
# TODO: Exemplos práticos
# Adicionar um arquivo específico
# Adicionar todos os arquivos
# Adicionar arquivos por padrão
```

### Boas Práticas

<!-- TODO: Quando adicionar arquivos específicos vs. tudo -->

## git status

<!-- TODO: Explique git status -->

### O que Mostra

<!-- TODO: Tipos de informação que git status exibe -->
<!-- Arquivos modificados, staged, untracked, etc. -->

### Exemplo de Saída

```bash
# TODO: Mostre exemplo de saída do git status
# Explique cada parte
```

### Quando Usar

<!-- TODO: Por que verificar status frequentemente -->

## git commit

O comando `git commit` cria um registro permanente das mudanças que foram
adicionadas à área de staging com `git add`. Cada commit funciona como um ponto
salvo na história do projeto, contendo um identificador único, autor, data,
mensagem descritiva e o conjunto de alterações incluídas.

Use commits para dividir o trabalho em etapas pequenas e compreensíveis. Assim,
fica mais fácil revisar mudanças, desfazer problemas e entender a evolução do
código ao longo do tempo.
## git commit

O comando `git commit` salva as alterações da *staging area* no histórico do repositório, criando um novo ponto na linha do tempo do projeto.

### Sintaxe

```bash
git commit -m "Mensagem"
git commit -am "Mensagem"
```

- `-m`: define a mensagem do commit  
- `-a`: adiciona automaticamente arquivos já rastreados

---

### Componentes de um commit

Cada commit contém:

- SHA-1 hash (identificador único)
- Autor e email
- Timestamp
- Mensagem
- Alterações realizadas

---

### Boas práticas de mensagem

- Use verbo no imperativo: "Add", "Fix", "Update"  
- Seja claro e descritivo  
- Limite a 72 caracteres  

Exemplos:

Boa:
```text
Add login button
Fix authentication bug
```

Ruim:
```text
Fix stuff
Update things
```

---

### Opções úteis

```bash
git commit --amend
```

Permite alterar o último commit.

---

### Commit vazio

```bash
git commit --allow-empty -m "Mensagem"
```

Usado para marcar eventos ou disparar pipelines.

---

### Verificação

```bash
git log
```

Exibe o histórico de commits.

---

### Atomicidade

Um commit deve representar uma única mudança lógica.

---

### Conceitos

- Mensagem de commit  
- Atomicidade  
- Rastreabilidade  
- Histórico limpo


## git log

<!-- TODO: Explique git log -->

### Visualizando Histórico

<!-- TODO: O que git log mostra -->

### Opções Úteis

```bash
# TODO: Variações do git log
# git log --oneline
# git log --graph
# git log --author="nome"
# git log --since="2 weeks ago"
```

### Interpretando a Saída

<!-- TODO: Como ler as informações do git log -->

## git diff

<!-- TODO: Explique git diff -->

### Tipos de Diff

```bash
# TODO: Diferentes usos de git diff
# git diff (working directory vs staged)
# git diff --staged (staged vs último commit)
# git diff HEAD (working vs último commit)
# git diff <commit1> <commit2>
```

### Lendo a Saída

<!-- TODO: Como interpretar a saída do diff -->
<!-- + verde = adicionado, - vermelho = removido -->

### Exemplo Prático

<!-- TODO: Exemplo de uso -->

## git restore

<!--  TODO: Explique git restore (comando moderno) -->

### Desfazendo Mudanças

```bash
# TODO: Como desfazer alterações
# git restore <arquivo> (working directory)
# git restore --staged <arquivo> (unstage)
```

### Diferença de git checkout

<!-- TODO: restore é o novo comando recomendado -->

## git rm

<!-- TODO: Explique git rm -->

### Removendo Arquivos

```bash
# TODO: Como remover arquivos do Git
```

### Diferença de rm normal

<!-- TODO: rm vs git rm -->

## git mv

<!-- TODO: Explique git mv -->

### Renomeando/Movendo Arquivos

```bash
# TODO: Como renomear ou mover arquivos
```

## Fluxo de Trabalho Básico

<!-- TODO: Diagrama ou descrição do fluxo -->

```
1. Modificar arquivos (Working Directory)
2. git add (Staging Area)
3. git commit (Repository)
4. Repetir
```

### Exemplo Completo

```bash
# TODO: Exemplo de fluxo completo
# 1. Clonar/criar repositório
# 2. Fazer mudanças
# 3. Ver status
# 4. Adicionar
# 5. Committar
# 6. Ver log
```

## Comandos de Consulta

### git show

<!-- TODO: Ver detalhes de um commit específico -->

### git blame

<!-- TODO: Ver quem modificou cada linha -->

## Exemplos Práticos

### Exemplo 1: Criando Primeiro Repositório

<!-- TODO: Passo a passo completo -->

### Exemplo 2: Clonando e Contribuindo

<!-- TODO: Clone → modificar → commit workflow -->

### Exemplo 3: Desfazendo Alterações

<!-- TODO: Quando e como usar restore -->

## Erros Comuns

### Erro 1: Esquecer de git add

<!-- TODO: Commit vazio, como evitar -->

### Erro 2: Mensagem de commit vaga

<!-- TODO: Importância de mensagens claras -->

### Erro 3: Committar arquivos errados

<!-- TODO: Como verificar antes de commit -->

### Erro 4: Confundir git reset e git restore

<!-- TODO: Diferenças e quando usar cada um -->

## Exercícios

<!-- TODO: Crie exercícios práticos -->

1. <!-- Criar repositório e fazer primeiro commit -->
2. <!-- Modificar arquivo, ver diff, committar -->
3. <!-- Explorar histórico com git log -->
4. <!-- Desfazer alterações com restore -->
5. <!-- Clonar repositório e explorar -->

## Tabela de Referência Rápida

Legenda de badges:

- ⭐ muito usado
- ❗ importante
- ⚠️ cuidado

Para mais detalhes de qualquer comando, use `git help <comando>` ou `git <comando> --help` (veja também [Obtendo Ajuda](#obtendo-ajuda)).

### Setup

| Comando | Propósito | Exemplo |
|---------|-----------|---------|
| ❗ `git config --global user.name "Seu Nome"` | Define o nome padrão do autor dos commits. | `git config --global user.name "Maria Silva"` |
| ❗ `git config --global user.email "voce@email.com"` | Define o e-mail padrão do autor dos commits. | `git config --global user.email "maria@email.com"` |
| ❗ `git init` | Inicializa um novo repositório local ([detalhes](#git-init)). | `git init` |
| ⭐ `git clone <url>` | Clona um repositório remoto para sua máquina ([detalhes](#git-clone)). | `git clone https://github.com/org/projeto.git` |

### Básico

| Comando | Propósito | Exemplo |
|---------|-----------|---------|
| ⭐ `git status` | Mostra o estado atual dos arquivos ([detalhes](#git-status)). | `git status` |
| ⭐ `git add <arquivo>` | Adiciona um arquivo à staging area ([detalhes](#git-add)). | `git add docs/02-comandos-essenciais.md` |
| ⭐ `git add -A` | Adiciona todas as alterações (novos, modificados e removidos). | `git add -A` |
| ⭐ `git commit -m "mensagem"` | Registra as alterações staged no histórico ([detalhes](#git-commit)). | `git commit -m "docs: adiciona tabela rápida"` |
| ⭐ `git log --oneline --graph` | Exibe histórico resumido com gráfico ([detalhes](#git-log)). | `git log --oneline --graph --decorate` |
| ⭐ `git diff` | Mostra diferenças não staged ([detalhes](#git-diff)). | `git diff` |
| ❗ `git show <hash>` | Mostra detalhes de um commit específico ([detalhes](#git-show)). | `git show a1b2c3d` |

### Branching

| Comando | Propósito | Exemplo |
|---------|-----------|---------|
| ⭐ `git branch` | Lista branches locais. | `git branch` |
| ❗ `git branch -a` | Lista branches locais e remotas. | `git branch -a` |
| ⭐ `git switch -c <branch>` | Cria e troca para uma nova branch. | `git switch -c feature/login` |
| ⭐ `git switch <branch>` | Troca para uma branch existente. | `git switch main` |
| ❗ `git merge <branch>` | Mescla outra branch na branch atual. | `git merge feature/login` |
| ⚠️ `git rebase <branch>` | Reescreve histórico aplicando commits sobre outra base. | `git rebase main` |

### Remote

| Comando | Propósito | Exemplo |
|---------|-----------|---------|
| ❗ `git remote -v` | Lista URLs remotas configuradas. | `git remote -v` |
| ⭐ `git fetch` | Baixa atualizações do remoto sem mesclar. | `git fetch origin` |
| ⭐ `git pull` | Atualiza branch atual com mudanças remotas (fetch + merge/rebase). | `git pull origin main` |
| ⭐ `git push` | Envia commits locais para o remoto. | `git push origin main` |
| ❗ `git push -u origin <branch>` | Publica branch e define upstream para próximos pushes/pulls. | `git push -u origin feature/login` |

### Desfazer

| Comando | Propósito | Exemplo |
|---------|-----------|---------|
| ⭐ `git restore <arquivo>` | Descarta mudanças locais não staged ([detalhes](#git-restore)). | `git restore README.md` |
| ⭐ `git restore --staged <arquivo>` | Remove arquivo da staging area sem perder conteúdo ([detalhes](#git-restore)). | `git restore --staged README.md` |
| ❗ `git commit --amend` | Ajusta o último commit (mensagem e/ou conteúdo). | `git commit --amend -m "fix: corrige título"` |
| ⚠️ `git reset --soft HEAD~1` | Volta um commit mantendo alterações em staging. | `git reset --soft HEAD~1` |
| ❗ `git revert <hash>` | Cria novo commit para desfazer um commit anterior, sem reescrever histórico. | `git revert a1b2c3d` |

### Versão em 2 colunas (PDF/impressão)

| Coluna 1 | Coluna 2 |
|---------|---------|
| **Setup**<br>`git config --global user.name`<br>`git config --global user.email`<br>`git init`<br>`git clone`<br><br>**Básico**<br>`git status`<br>`git add <arquivo>`<br>`git add -A`<br>`git commit -m`<br>`git log --oneline --graph`<br>`git diff`<br>`git show <hash>` | **Branching**<br>`git branch`<br>`git branch -a`<br>`git switch -c <branch>`<br>`git switch <branch>`<br>`git merge <branch>`<br>`git rebase <branch>`<br><br>**Remote**<br>`git remote -v`<br>`git fetch`<br>`git pull`<br>`git push`<br>`git push -u origin <branch>`<br><br>**Desfazer**<br>`git restore <arquivo>`<br>`git restore --staged <arquivo>`<br>`git commit --amend`<br>`git reset --soft HEAD~1`<br>`git revert <hash>` |

## Recursos Adicionais

<!-- TODO: Links para documentação oficial e tutoriais -->

- [Git Reference Manual](https://git-scm.com/docs)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- <!-- Adicione mais -->

## Resumo

<!-- TODO: Pontos principais que os alunos devem lembrar -->

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->
- [@esleiu](https://github.com/esleiu) - Seção tabela de referência rápida

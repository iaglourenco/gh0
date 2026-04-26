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

<!-- TODO: Explique git commit -->

### Sintaxe

```bash
# TODO: Formas de fazer commit
# git commit -m "mensagem"
# git commit (abre editor)
# git commit -am "mensagem"
```

### Anatomia de um Bom Commit

<!-- TODO: O que é um bom commit? -->

### Mensagens de Commit

<!-- TODO: Como escrever boas mensagens -->
<!-- Ver também capítulo 05 sobre boas práticas -->

```bash
# Exemplo de BOA mensagem
# TODO: Adicione exemplos

# Exemplo de MÁ mensagem
# TODO: Adicione exemplos ruins
```

### Exemplo Prático

```bash
# TODO: Fluxo completo: modificar → add → commit
```

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

O fluxo de trabalho no Git segue três etapas principais: **modificar**, **adicionar** e **commitar**. Entender esse ciclo é fundamental para usar o Git de forma eficiente.

### As Três Etapas

```mermaid
graph LR
    A[Working Directory] -->|git add| B[Staging Area]
    B -->|git commit| C[Repository]
    
    A -.-|Editando arquivos| A
    B -.-|Preparando mudanças| B
    C -.-|Histórico salvo| C
```

1. **Working Directory**: Onde você edita seus arquivos
2. **Staging Area**: Área de preparação - marca o que vai no commit
3. **Repository**: Histórico permanente dos projetos

### Exemplo Completo

```bash
# 1. Clone ou crie o repositório
git clone https://github.com/usuario/repositorio.git
# ou
git init

# 2. Faça mudanças nos arquivos
# (edite, crie ou delete arquivos)

# 3. Verifique o status
git status

# 4. Adicione as mudanças à staging area
git add .
# ou adicione um arquivo específico
git add arquivo.md

# 5. Faça o commit
git commit -m "Descrição clara do que foi feito"

# 6. Verifique o histórico
git log
```

### Dicas Práticas

- Sempre verifique o `git status` antes de commitar
- Use `git add .` para adicionar todos os arquivos
- Use `git add arquivo-especifico.md` para adicionar apenas um arquivo
- Commite frequentemente com mensagens descritivas

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

<!-- TODO: Crie uma tabela com comandos e descrições -->

| Comando | O que faz | Quando usar |
|---------|-----------|-------------|
| `git init` | <!-- --> | <!-- --> |
| `git clone` | <!-- --> | <!-- --> |
| `git add` | <!-- --> | <!-- --> |
| `git commit` | <!-- --> | <!-- --> |
| `git status` | <!-- --> | <!-- --> |
| `git log` | <!-- --> | <!-- --> |
| `git diff` | <!-- --> | <!-- --> |
| `git restore` | <!-- --> | <!-- --> |

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

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

O fluxo de trabalho no Git segue um ciclo organizado: **modificar → adicionar → commitar → enviar**. Entender cada etapa é fundamental para trabalhar de forma eficiente.

### Sequência Completa do Git

```
init/clone → edit files → git status → git add → git status → git commit → git push
```

### Diagrama Visual do Fluxo

```mermaid
graph TD
    subgraph "1. Ambiente Local"
        A[Working Directory] -->|git add| B[Staging Area]
        B -->|git commit| C[Local Repository]
    end
    
    subgraph "2. Ambiente Remoto"
        C -->|git push| D[Remote Repository]
        D -->|git pull| C
    end
    
    E[GitHub/GitLab] <-.-> D
    F[origin] <--> D
    G[upstream] <--> D
end
```

### Exemplo Prático Completo (passo-a-passo)

```bash
# 1. Iniciar ou clonar repositório
git clone https://github.com/usuario/repositorio.git
# Output: Cloning into 'repositorio'...
# remote: Enumerating objects: 10, done.

# 2. Criar branch de trabalho
git checkout -b docs/fluxo-trabalho-basico
# Output: Switched to a new branch 'docs/fluxo-trabalho-basico'

# 3. Modificar arquivos (edit files)
echo "# Novo arquivo" > novo.md

# 4. Verificar status (antes do add)
git status
# Output: On branch docs/fluxo-trabalho-basico
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#     novo.md

# 5. Adicionar à staging area
git add novo.md
git status
# Output: On branch docs/fluxo-trabalho-basico
# Changes to be committed:
#   new file:   novo.md

# 6. Fazer commit
git commit -m "docs: adiciona arquivo de exemplo"
# Output: [docs/fluxo-trabalho-basico abc1234] docs: adiciona arquivo de exemplo
#  1 file changed, 1 insertion(+)
#  create mode 100644 novo.md

# 7. Enviar para remoto (push)
git push origin docs/fluxo-trabalho-basico
# Output: Enumerating objects: 5, done.
# To https://github.com/usuario/repositorio.git
#  * [new branch] docs/fluxo-trabalho-basico -> docs/fluxo-trabalho-basico
# Branch 'docs/fluxo-trabalho-basico' set up to track remote branch from 'origin'.
```

### Entendendo os Remotes: origin e upstream

Quando você faz um fork de um projeto, dois remotes são configurados:

| Remote | Descrição | Quando usar |
|--------|-----------|-------------|
| **origin** | Seu fork no GitHub (sua cópia) | Para onde você faz `push` das suas alterações |
| **upstream** | Repositório original do projeto | Para buscar atualizações com `git fetch` ou `git pull` |

```bash
# Verificar remotes configurados
git remote -v

# Exemplo de saída:
# origin    https://github.com/seu-usuario/gh0.git (fetch)
# origin    https://github.com/seu-usuario/gh0.git (push)
# upstream  https://github.com/professor/gh0.git (fetch)
# upstream  https://github.com/professor/gh0.git (push)

# Atualizar fork com upstream
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

### Branch Workflow Básico

Trabalhe sempre em uma branch separada da main:

```bash
# Criar e mudar para nova branch
git checkout -b nome-da-branch

# Ciclo completo de trabalho
git add .                              # Adicionar todas as mudanças
git commit -m "tipo: descrição"       # Commitar com mensagem clara
git push -u origin nome-da-branch      # Enviar pela primeira vez

# Nas próximas vezes, apenas:
git push
```

### ✅ Checklist do Aluno

Após completar o ciclo, verifique:

- [ ] Repositório clonado ou iniciado com `git clone` ou `git init`
- [ ] Branch de trabalho criada com `git checkout -b`
- [ ] Arquivos modificados/adicionados no editor
- [ ] `git status` executado **antes** do `git add` (verificar mudanças)
- [ ] `git add` executado para adicionar à staging area
- [ ] `git status` executado **depois** do `git add` (confirmar staging)
- [ ] `git commit` feito com mensagem clara e descritiva
- [ ] `git push` enviado para o remoto (origin)

**Sequência feita com sucesso? ✓**

### Comando Rápido (atalho para repetição)

Para repetir o ciclo N vezes durante o dia (após a primeira configuração da branch):

```bash
# Atalho do ciclo completo
git add . && git commit -m "update" && git push
```

### Próximos Passos

Agora que você dominou o fluxo básico, explore:

- **[03-branching-e-merge.md](03-branching-e-merge.md)** - Criando e gerenciando branches
- **[04-pull-requests-e-review.md](04-pull-requests-e-review.md)** - Enviando PRs para revisão

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
- [@Giseleptbr](https://github.com/Giseleptbr) - Seção git commit
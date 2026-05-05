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

O comando `git restore` foi introduzido no Git 2.23 (junto com o `git switch`) para separar as responsabilidades que antes ficavam sobrecarregadas no `git checkout`. Seu propósito principal é **desfazer mudanças** em arquivos, permitindo restaurá-los para estados anteriores, seja no diretório de trabalho (*working directory*) ou na área de preparação (*staging area*).

Por padrão, `git restore <arquivo>` restaura o conteúdo do arquivo no diretório de trabalho a partir do **index/staging area**. Como o index normalmente reflete o `HEAD`, isso muitas vezes equivale à versão do último commit, mas não sempre. Para restaurar explicitamente a partir de um commit ou outro ponto do histórico, use `--source`.

### Desfazendo Mudanças

O `git restore` possui duas áreas de atuação principais, dependendo de onde as modificações estão no seu repositório:

#### 1. Desfazer mudanças no diretório de trabalho
Se você modificou um arquivo, mas **não o adicionou** com `git add`, pode descartar as mudanças no diretório de trabalho e restaurá-lo para o conteúdo que está no **index** (que normalmente coincide com o último commit, quando não há mudanças staged):

```bash
# Descarta todas as modificações não "staged" do arquivo
git restore <arquivo>

# Exemplo prático:
git restore index.html
```

> ⚠️ **Cuidado:** Esta operação é destrutiva. As alterações locais ainda não adicionadas ao staging serão perdidas permanentemente e não poderão ser recuperadas.

#### 2. Remover da área de preparação (Unstage)
Se você adicionou um arquivo com `git add` por engano e deseja removê-lo da *staging area* (sem perder as modificações no arquivo físico):

```bash
# Remove o arquivo do staging area (unstage)
git restore --staged <arquivo>

# Exemplo prático:
git restore --staged config.js
```

#### 3. Restaurar de um commit específico
Você também pode buscar a versão de um arquivo de um commit passado ou branch específica, em vez do último commit (HEAD):

```bash
# Restaura o arquivo para a versão de um commit específico
git restore --source=<hash-do-commit> <arquivo>

# Exemplo prático: recuperando um arquivo de 3 commits atrás
git restore --source=HEAD~3 estilos.css
```

### Exemplo Prático: Recuperação de Arquivo Deletado

Um dos usos mais valiosos do `git restore` é recuperar arquivos deletados acidentalmente. Se você excluiu um arquivo importante no seu sistema (mas não comitou a exclusão), você pode trazê-lo de volta facilmente:

```bash
# O arquivo foi deletado acidentalmente no sistema de arquivos
$ rm arquivo_importante.txt

# Verificando o status
$ git status
# deleted:    arquivo_importante.txt

# Recuperando o arquivo do último commit
$ git restore arquivo_importante.txt
```

### Diferenças e Alternativas

É importante entender como o `git restore` se compara a outros comandos de desfazer no Git:

#### `git restore` vs `git revert`
- O **`git restore`** restaura o conteúdo de arquivos no diretório de trabalho e/ou na área de stage, **sem alterar o histórico de commits**.
- O **`git revert`** atua sobre commits já registrados no histórico, **criando um novo commit de reversão** para desfazer as alterações de um commit anterior.

#### `git restore` vs `git checkout`
Antes do Git 2.23, o comando `git checkout` era usado tanto para trocar de branches quanto para restaurar arquivos. Essa dupla função causava confusão. A alternativa antiga para `git restore <arquivo>` era `git checkout -- <arquivo>`. Embora o `checkout` ainda funcione para este propósito por questões de compatibilidade, o uso do **`restore` é a prática recomendada moderna** por ser mais claro, seguro e ter uma intenção única e explícita.

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
- [@hailtonDavid](https://github.com/hailtonDavid) - Seção git restore
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

O comando `git status` mostra o estado atual do repositório do ponto de vista
do seu diretório de trabalho. Ele compara o `working directory`, a
`staging area` e o último commit para indicar o que foi modificado, o que já
está pronto para commit e o que ainda não está sendo rastreado pelo Git.

### Sintaxe

```bash
git status
git status -s
git status --porcelain
```

- `git status`: saída completa, pensada para leitura humana.
- `git status -s`: saída curta (`--short`), útil para inspeção rápida.
- `git status --porcelain`: formato estável para parsing automático em scripts
  e ferramentas.

### O que Mostra

- A branch atual, por exemplo `On branch main`.
- O estado do `working directory`, com arquivos modificados mas ainda não
  adicionados ao stage.
- O estado da `staging area`, com arquivos que já entrarão no próximo commit.
- A diferença entre arquivos rastreados (`tracked`) e não rastreados
  (`untracked`).
- Se a árvore está limpa, com mensagens como
  `nothing to commit, working tree clean`.

Um arquivo `tracked` já faz parte do histórico do Git ou já foi adicionado com
`git add`. Um arquivo `untracked` existe na pasta do projeto, mas o Git ainda
não acompanha esse arquivo.

### Exemplo de Saída

```bash
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   app.js
        new file:   notas.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
        modified:   README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        debug.log
```

- `On branch main`: informa em qual branch você está trabalhando.
- `Changes to be committed`: arquivos que já estão na `staging area`.
- `Changes not staged for commit`: mudanças feitas em arquivos rastreados, mas
  que ainda não foram preparadas com `git add`.
- `Untracked files`: arquivos novos que o Git ainda não está rastreando.

### Cores e Significado

Na maioria dos terminais, o Git usa cores para destacar o estado dos arquivos:

- Vermelho: arquivos `untracked` ou modificados que ainda não foram adicionados
  ao stage.
- Verde: arquivos já adicionados à `staging area` e prontos para entrar no
  próximo commit.

As cores podem variar conforme o terminal e a configuração do Git, mas a ideia
principal continua a mesma: vermelho pede atenção, verde indica que o arquivo
já foi preparado.

### Saída Curta

```bash
git status -s
```

```text
M  app.js
 M README.md
?? debug.log
A  notas.txt
```

- A primeira coluna representa a `staging area`.
- A segunda coluna representa o `working directory`.
- `M  app.js`: arquivo modificado e já adicionado ao stage.
- ` M README.md`: arquivo modificado, mas ainda não adicionado ao stage.
- `?? debug.log`: arquivo novo e não rastreado.
- `A  notas.txt`: arquivo novo já adicionado ao stage.

### Exemplo Passo a Passo

1. Criando um arquivo novo:

```bash
touch notas.txt
git status
```

O Git mostrará `notas.txt` em `Untracked files`, indicando que o arquivo existe,
mas ainda não está sendo rastreado.

2. Modificando um arquivo já rastreado:

```bash
echo "Nova linha" >> README.md
git status
```

Agora o status mostrará duas situações ao mesmo tempo:

`README.md` aparecerá em `Changes not staged for commit`, enquanto
`notas.txt` continuará em `Untracked files`.

3. Adicionando as mudanças com `git add`:

```bash
git add notas.txt README.md
git status
```

Depois do `git add`, ambos passarão para `Changes to be committed`, o que
significa que já estão na `staging area`.

### Parsing Automático

`git status --porcelain` existe para automações. Ele remove textos explicativos
e mantém um formato previsível, facilitando o uso em scripts, hooks e
ferramentas de integração.

Se a automação também precisar da branch atual, uma variação comum é:

```bash
git status --porcelain -b
```

### Quando Usar

- Antes de executar `git add`, para confirmar o que mudou.
- Antes de `git commit`, para garantir que apenas os arquivos certos entrarão no
  commit.
- Depois de merges, rebases ou pulls, para verificar se restou algo pendente.
- Sempre que houver dúvida sobre a atividade atual no repositório.
- Em conjunto com `.gitignore`, para evitar que arquivos temporários, logs,
  builds e dependências poluam o status.

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

<!-- TODO: Crie uma tabela com comandos e descrições -->

| Comando | O que faz | Quando usar |
|---------|-----------|-------------|
| `git init` | <!-- --> | <!-- --> |
| `git clone` | <!-- --> | <!-- --> |
| `git add` | <!-- --> | <!-- --> |
| `git commit` | <!-- --> | <!-- --> |
| `git status` | Mostra o estado do working directory e da staging area | Antes de adicionar, commitar ou revisar mudanças |
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
- [@AIWASS23](https://github.com/AIWASS23) - Seção git status
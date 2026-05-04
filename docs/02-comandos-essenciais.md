# Comandos Essenciais do Git

Este arquivo documenta os comandos Git fundamentais que todo desenvolvedor deve conhecer

## 📋 Objetivos de Aprendizagem

<!-- Liste aqui os objetivos de aprendizagem deste capítulo -->
<!-- Ao final, o aluno deve saber usar os comandos básicos do Git -->
Ao final deste capítulo, você será capaz de:
- Iniciar repositórios do zero ou clonar projetos existentes.
- Dominar o ciclo de vida dos arquivos através da Staging Area.
- Criar registros históricos significativos utilizando commits atômicos.
- Inspecionar alterações e navegar pelo histórico de desenvolvimento com precisão.

<!-- TODO: Adicione 3-5 objetivos de aprendizagem -->

## 🎯 Introdução

<!-- Introdução sobre comandos Git e sua importância -->
<!-- Por que aprender linha de comando? -->
Dominar a linha de comando (CLI) é o que diferencia o desenvolvedor de alta performance do usuário casual. Na área de IA, onde frequentemente operamos em servidores remotos (via SSH) ou em instâncias na nuvem para treinar modelos, a interface gráfica nem sempre está disponível. A CLI é mais rápida, permite automação e oferece controle total sobre as operações do Git.

## Estrutura dos Comandos Git

<!-- TODO: Explique a estrutura geral dos comandos Git -->
<!-- Formato: git <comando> <opções> <argumentos> -->

A sintaxe do Git segue um padrão lógico:
git <comando> <opções> <argumentos>
- git: O executável principal.
- comando: A ação (ex: commit, add).
- opções: Modificadores que começam com - ou -- (ex: -m, --global).
- argumentos: O alvo da ação (ex: nome do arquivo ou link do repositório).

###  Obtendo Ajuda

<!-- TODO: Como obter ajuda sobre comandos Git -->

```bash
# Comandos para obter ajuda
git help commit       # Abre o manual completo no navegador
git commit --help     # Abre o manual no terminal
```

## git init

<!-- TODO: Explique o comando git init -->
O comando git init transforma um diretório comum em um repositório Git.

### Sintaxe

```bash
git init
```

### Quando Usar

<!-- TODO: Cenários de uso -->
Sempre que você iniciar um projeto novo localmente e quiser começar a versioná-lo.

### Exemplo Prático

```bash
# TODO: Exemplo completo de uso
# 1. Criar pasta
# 2. Executar git init
# 3. Verificar resultado
mkdir meu-projeto-ia
cd meu-projeto-ia
git init
ls -a   # Você verá a pasta oculta .git criada
```

### O que Acontece

<!-- TODO: O que git init faz no sistema de arquivos? -->
<!-- Pasta .git criada, etc. -->
O Git cria uma subpasta oculta chamada .git. Ela contém toda a estrutura do banco de dados do repositório, incluindo configurações, objetos de histórico e referências de branches. Nunca apague esta pasta, ou você perderá todo o histórico do projeto.

## git clone

<!-- TODO: Explique o comando git clone -->
Cria uma cópia idêntica de um repositório remoto na sua máquina.

### Sintaxe

```bash
# TODO: Sintaxe básica e variações
git clone <url-do-repositorio>
```

### Diferença entre init e clone

<!-- TODO: Quando usar cada um? -->
- init: Para projetos que começam "do nada" no seu PC.
- clone: Para baixar um projeto que já existe no GitHub ou em outro servidor

### Exemplo Prático

```bash
# TODO: Exemplo de clone de um repositório
git clone https://github.com/seujoao/abc.git
```

### Clonando seu Fork

<!-- TODO: Como clonar um fork do GitHub -->
Após clicar no botão "Fork" no GitHub, você deve clonar a sua versão:
```bash
git clone https://github.com/SEU-USUARIO/abc.git
```

## git add

<!-- TODO: Explique o comando git add -->
<!-- Staging area concept -->
Move as alterações do diretório de trabalho para a Staging Area.

### Sintaxe

```bash
# TODO: Diferentes formas de usar git add
git add arquivo.py    # Adiciona um arquivo específico
git add .             # Adiciona todas as mudanças (novos, modificados e deletados)
git add -u            # Adiciona apenas arquivos que já eram rastreados e foram modificados
```

### Staging Area

<!-- TODO: O que é staging area? -->
<!-- Por que existe? Qual sua utilidade? -->
É uma área intermediária, como uma "caixa de saída". Ela permite que você selecione exatamente quais mudanças devem fazer parte do próximo commit, permitindo commits focados e organizados.

### Exemplos

A Staging Area é o local onde você prepara o próximo "snapshot" do seu modelo ou código.
```bash

git add train_model.py       # Adicionar um arquivo específico
git add *.py                 # Adicionar todos os arquivos
git add                      # Adicionar arquivos por padrão
git add -A                   # Adicionar arquivos por padrão
git add -u                   # Adicionar apenas modificações de arquivos já rastreados
```

### Boas Práticas

<!-- TODO: Quando adicionar arquivos específicos vs. tudo -->
Evite o git add . indiscriminado em projetos de IA. Você pode acabar adicionando acidentalmente datasets pesados (.csv, .h5) ou modelos de gigabytes que não deveriam estar no Git.

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
# TODO: Formas de fazer commit
git commit -m "feat: add resnet50 architecture" # git commit -m "mensagem"
git commit                                      # git commit (abre editor)
git commit -am                                  # -am "mensagem. fix: corrige erro no carregamento do dataset
git commit -m                                   # feat: adiciona camada de dropout ao modelo"
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

<!-- TODO: O que é um bom commit? -->
Um commit deve ser atômico: deve resolver apenas uma coisa (um bug, uma feature, uma documentação). Se você mudou 10 arquivos com 3 propósitos diferentes, faça 3 commits separados.

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
Interpretando a Saída

### Visualizando Histórico

<!-- TODO: O que git log mostra -->
Exibe a lista cronológica de todos os commits realizados.
Ao rodar git log, você verá:
- commit : O ID único (SHA-1) daquela versão.
- Author: Quem fez a alteração.
- Date: Quando foi feita.
- Mensagem: O porquê da alteração.

### Opções Úteis

```bash
git log --oneline    # Versão resumida (ID e mensagem)
git log --graph      # Visualização visual das ramificações
git log -p           # Mostra o log com as diferenças de código (diff) incluídas
git log --oneline --graph --decorate # Este comando mostra o histórico como um gráfico visual, essencial para ver onde as branches de funcionalidades de IA se ramificam da main.
```

### Interpretando a Saída

<!-- TODO: Como ler as informações do git log -->

## git diff

<!-- TODO: Explique git diff -->
Mostra a diferença textual entre estados dos arquivos.

### Tipos de Diff

```bash
git diff             # O que eu mudei mas ainda não dei 'git add'
git diff --staged    # O que está no 'stage' vs o último commit
```

### Lendo a Saída

<!-- TODO: Como interpretar a saída do diff -->
<!-- + verde = adicionado, - vermelho = removido -->
- Linhas em vermelho (precedidas por -): Foram removidas.
- Linhas em verde (precedidas por +): Foram adicionadas.

### Exemplo Prático

<!-- TODO: Exemplo de uso -->
O diff compara o que foi escrito.
- git diff: Compara o Working Directory com a Staging Area.
- git diff --staged: Compara a Staging Area com o último commit.
- git diff HEAD~1 HEAD: Compara o penúltimo commit com o último. Excelente para revisar métricas de treino entre versões.

## git restore

<!--  TODO: Explique git restore (comando moderno) -->
Comando moderno para desfazer bagunças.

### Desfazendo Mudanças

```bash
git restore script.py           # Descarta mudanças locais (volta ao estado do último commit)
git restore --staged script.py  # Tira o arquivo da Staging Area, mas mantém o código alterado
```

### Diferença de git checkout

<!-- TODO: restore é o novo comando recomendado -->
Antigamente, o checkout fazia tudo, o que era confuso. O git restore é o comando moderno e específico para:
- git restore <arquivo>: Limpa a bagunça no Working Directory.
- git restore --staged <arquivo>: Tira do "palco" (unstage).

## git rm

<!-- TODO: Explique git rm -->
git rm: Remove o arquivo do disco e já prepara a deleção no Git.

### Removendo Arquivos

```bash
rm arquivo.txt                     # Apaga apenas do disco. O Git ainda verá o arquivo como "deleted" mas não preparado.
git rm arquivo.txt                 # Apaga do disco e já prepara a deleção para o commit.
```

## git mv

<!-- TODO: Explique git mv -->
git mv: Renomeia ou move um arquivo, mantendo o rastro do histórico.

### Renomeando/Movendo Arquivos

```bash
git mv antigo_nome.py novo_nome.py #     Renomeia o arquivo e mantém o histórico vinculado ao novo nome.
```

## Fluxo de Trabalho Básico

<!-- TODO: Diagrama ou descrição do fluxo -->

```
1. Modificar arquivos.
2. git status (para conferir).
3. git add <arquivos> (preparar).
4. git commit -m "mensagem" (gravar).
```

### Exemplo Completo

```bash
# TODO: Exemplo de fluxo completo
mkdir classificador-imagens
cd classificador-imagens
git init
echo "print('Iniciando modelo')" > main.py
git add main.py
git commit -m "initial commit"
```

## Comandos de Consulta

### git show

<!-- TODO: Ver detalhes de um commit específico -->
Mostra tudo o que mudou em um commit específico.

### git blame

<!-- TODO: Ver quem modificou cada linha -->
Mostra linha por linha quem foi o último a alterar o arquivo (essencial para depuração em equipe).

## Exemplos Práticos

### Exemplo 1: Criando Primeiro Repositório

```bash
mkdir classificador-imagens
cd classificador-imagens
git init
echo "print('Iniciando modelo')" > main.py
git add main.py
git commit -m "initial commit"
```

### Exemplo 2: Clonando e Contribuindo

<!-- TODO: Clone → modificar → commit workflow -->
1. git clone <url>
2. git checkout -b feature/melhoria-acuracia (Cria branch nova)
3. Modifica código...
4. git add .
5. git commit -m "feat: altera learning rate"

### Exemplo 3: Desfazendo Alterações

<!-- TODO: Quando e como usar restore -->
Você alterou o arquivo config.json e o código parou de rodar:
git restore config.json (O arquivo volta imediatamente ao estado do último commit).

## Erros Comuns

### Erro 1: Esquecer de git add

<!-- TODO: Commit vazio, como evitar -->
O commit fica vazio ou incompleto. Solução: Sempre rode git status antes de commitar.

### Erro 2: Mensagem de commit vaga

<!-- TODO: Importância de mensagens claras -->
"Update" não explica nada. Solução: Use o padrão: tipo: descrição curta (ex: docs: atualiza guia de instalação).

### Erro 3: Committar arquivos errados

<!-- TODO: Como verificar antes de commit -->
Adicionar senhas ou datasets de 2GB. Solução: Crie um arquivo .gitignore e verifique com git diff --staged antes de finalizar.

### Erro 4: Confundir git reset e git restore

<!-- TODO: Diferenças e quando usar cada um -->
- restore: Altera o conteúdo dos arquivos.
- reset: Altera para onde a branch aponta na história (nível de commit).

## Exercícios

<!-- TODO: Crie exercícios práticos -->

1. Crie um repositório chamado projeto-teste, crie um arquivo notas.txt e faça seu primeiro commit.
2. Modifique o notas.txt, use git diff para ver o que mudou e depois committe.
3. Use git log --oneline para ver seus dois commits.
4. Modifique o arquivo novamente, mas use git restore para apagar essa última mudança sem committar.

## Tabela de Referência Rápida

<!-- TODO: Crie uma tabela com comandos e descrições -->

| Comando | O que faz | Quando usar |
|---------|-----------|-------------|
| `git init` | Cria um novo repositório local | No início de um projeto |
| `git clone` | Copia um repositório remoto | Ao baixar um projeto do GitHub |
| `git add` | Adiciona arquivos ao Stage | Antes de cada commit |
| `git commit` | Salva o histórico | Após terminar uma tarefa lógica |
| `git status` | Mostra o estado do working directory e da staging area | Antes de adicionar, commitar ou revisar mudanças |
| `git log` | Lista o histórico | Para revisar o que foi feito |
| `git diff` | Exibe as alterações textuais entre os estados dos arquivos (quem entrou e quem saiu) | Antes de dar git add para revisar o que você escreveu, ou após o add (com --staged) para validar o pacote |
| `git restore` | Desfaz alterações no diretório de trabalho ou remove arquivos da área de preparação | Quando você comete um erro no código e quer voltar ao estado do último commit, ou quando adicionou um arquivo ao stage por engano |

## Recursos Adicionais

<!-- TODO: Links para documentação oficial e tutoriais -->

- [Git Reference Manual](https://git-scm.com/docs)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Cheat Sheet do GitHub](https://training.github.com/downloads/pt_BR/github-git-cheat-sheet.pdf)

## Resumo

<!-- TODO: Pontos principais que os alunos devem lembrar -->
Este capítulo cobriu a base operacional da linha de comando. Aqui estão os pontos fundamentais que você deve carregar para sua carreira:

- A CLI é Soberana: O uso do terminal (Git Bash) permite maior controle e velocidade, além de ser o padrão em ambientes de servidores de IA.
- O Fluxo é Sagrado: Lembre-se sempre da sequência Modificar → Status → Add → Status → Commit. O git status é o seu diagnóstico constante.
- A Staging Area é sua Revisão: Não pule a fase de preparação. Use-a para garantir que cada commit tenha apenas um objetivo (seja atômico).
- Commits são Documentação: Um bom commit com uma mensagem clara (feat:, fix:, docs:) economiza horas de depuração e facilita o trabalho em equipe.
- Segurança em Primeiro Lugar: Com comandos como git log e git diff, você nunca está "cego". Você sempre sabe o que mudou e quem mudou.
- Desfazer é Normal: O Git é projetado para ser resiliente. Errou no código? git restore. Errou no stage? git restore --staged. Nada é permanente até que você envie para o servidor.
- Diferença de Escopo:
  - git init inicia o projeto.
  - git clone baixa um projeto existente.
  - git rm remove e já avisa o Git.

---

```bash
git commit -m "Criei o Guia Completo sobre Comandos Essenciais do Git"
```

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@Tom-Junior](https://github.com/Tom-Junior) - Seção todas
-->
- [@Giseleptbr](https://github.com/Giseleptbr) - Seção git commit
- [@AIWASS23](https://github.com/AIWASS23) - Seção git status
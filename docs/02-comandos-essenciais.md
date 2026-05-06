# Comandos Essenciais do Git

Este arquivo documenta os comandos Git fundamentais que todo desenvolvedor deve conhecer

## 📋 Objetivos de Aprendizagem

Ao final deste capítulo, você será capaz de:
- Inicializar novos repositórios e clonar projetos existentes.
- Utilizar o ciclo básico de salvamento no Git (add, commit, status).
- Visualizar o histórico e as diferenças entre as alterações realizadas.
- Desfazer pequenas mudanças e compreender os estados dos arquivos no Git.

## 🎯 Introdução

A linha de comando (ou terminal) é a interface principal e mais poderosa para interagir com o Git. Embora existam diversas interfaces gráficas, aprender os comandos fundamentais ajuda a entender como o Git realmente funciona por baixo dos panos, facilitando a resolução de problemas e dando mais flexibilidade e velocidade ao seu fluxo de trabalho de desenvolvimento.

## Estrutura dos Comandos Git

A estrutura geral da maioria dos comandos Git segue o seguinte padrão:
`git <comando> <opções> <argumentos>`

Por exemplo, no comando `git commit -m "mensagem"`, `commit` é o comando, `-m` é uma opção (flag) e `"mensagem"` é o argumento dessa opção.

A sintaxe do Git segue um padrão lógico:
git <comando> <opções> <argumentos>
- git: O executável principal.
- comando: A ação (ex: commit, add).
- opções: Modificadores que começam com - ou -- (ex: -m, --global).
- argumentos: O alvo da ação (ex: nome do arquivo ou link do repositório).

###  Obtendo Ajuda

Se você esquecer o que um comando faz ou quais opções ele aceita, o próprio Git possui manuais integrados muito detalhados:

```bash
# Mostra uma ajuda rápida sobre um comando específico no terminal
git <comando> -h
git add -h

# Abre o manual completo (geralmente no navegador ou paginador) sobre o comando
git help <comando>
git help commit
```

## git init

O comando `git init` é usado para criar um novo repositório Git em branco ou para reinicializar um existente. Ele transforma um diretório normal (pasta do seu computador) em um repositório Git, permitindo que você comece a rastrear as alterações nele.

### Sintaxe

```bash
git init
```

### Quando Usar

Você deve usar o `git init` quando estiver começando um projeto do zero na sua máquina local e quiser colocá-lo sob controle de versão.

### Exemplo Prático

```bash
# 1. Cria uma nova pasta para o projeto
mkdir meu-novo-projeto

# 2. Entra na pasta
cd meu-novo-projeto

# 3. Inicializa o repositório Git
git init

# 4. Verifica o resultado
ls -a # Você verá uma pasta oculta chamada .git
```

### O que Acontece

Ao rodar `git init`, o Git cria uma pasta oculta chamada `.git` dentro do seu diretório atual. Essa pasta contém todos os metadados, banco de dados de objetos e configurações necessárias para o controle de versão. Seu diretório agora é o "Working Directory".

## git clone

O comando `git clone` é usado para copiar um repositório existente, geralmente de um servidor remoto (como o GitHub), para o seu computador local.

### Sintaxe

```bash
git clone <url-do-repositorio>

# Opcional: especificar um nome de pasta diferente
git clone <url-do-repositorio> <nome-da-pasta>
```
#### Variantes Comuns:

Clonar em um diretório específico:
```bash
git clone <url> <nome-do-diretorio>
```

Clonar apenas uma branch específica:
```bash
git clone -b <branch> <url>
```

Clonar com profundidade limitada (histórico reduzido):
```bash
git clone --depth 1 <url>
```

Clonar usando SSH:
```bash
git clone git@github.com:usuario/repositorio.git
```

Clonar usando HTTPS:
```bash
git clone https://github.com/usuario/repositorio.git
```

### Diferença entre init e clone
`git init`:
- Cria um novo repositório Git vazio localmente;
- Não possui histórico nem conexão com repositórios remotos;
- Usado para iniciar um projeto do zero.

`git clone`:
- Copia um repositório existente, incluindo todo o histórico e branches;
- Configura automaticamente a origem remota (`origin`);
- Usa-se quando se deseja trabalhar com um projeto já existente, seja para contribuir ou para ter uma cópia local.

| Critério              | `git init`        | `git clone`           |
|----------------------|-----------------|-----------------------|
| Ponto de partida     | Projeto novo    | Projeto existente     |
| Histórico            | Vazio           | Completo              |
| Remote origin        | Não configurado | Configurado automaticamente |

### Exemplo Prático

```bash
# Clonar um repositório do GitHub
git clone https://github.com/usuario/projeto-exemplo.git

# Entrar na pasta do projeto clonado
cd projeto-exemplo
```
Isso irá:
1. Criar uma pasta chamada `git` no diretório atual;
2. Baixar todo o repositório do Git, incluindo seu histórico completo;
3. Configurar a origem remota para `origin`.

Depois disso, basta entrar no diretório (`cd git`) e começar a trabalhar com o repositório clonado.

### Clonando seu Fork

Um fork é uma cópia de um repositório feita dentro da sua conta (por exemplo, no GitHub).

Passos:

1. Faça um fork do repositório original (clicando em "Fork" na interface do GitHub);
2. Copie a URL do seu fork;
3. Use `git clone` com a URL do seu fork para obter uma cópia local.

```bash
git clone https://github.com/seu-usuario/repositorio.git
```

Opcionalmente, você pode adicionar o repositório original como upstream para manter seu fork atualizado:

```bash
cd repositorio
git remote add upstream https://github.com/usuario-original/repositorio.git
```

E, por fim, para atualizar seu fork com as mudanças do repositório original:

```bash
git fetch upstream
git switch main
git merge upstream/main
```

## git add

O comando `git add` é usado para selecionar quais arquivos modificados você quer preparar para o seu próximo commit. Ele move as alterações do seu diretório de trabalho para a **Staging Area** (Área de Preparação).

### Sintaxe

```bash
# Adiciona um arquivo específico
git add index.html

# Adiciona vários arquivos
git add arquivo1.txt arquivo2.txt

# Adiciona todos os arquivos modificados e novos na pasta atual
git add .

# Adiciona todos os arquivos do projeto (modificados, novos e deletados)
git add -A
```

### Staging Area

A **Staging Area** é como se fosse uma "caixa" ou "sala de espera" onde você coloca os arquivos que farão parte do seu próximo commit.
Ela existe para que você tenha um controle preciso do que será salvo. Em vez de salvar todas as modificações do seu projeto de uma vez, você pode agrupar alterações relacionadas (criando *commits seletivos*).

### Exemplos

Imagine que você modificou 3 arquivos, mas 2 deles são sobre o formulário de contato e 1 é um ajuste no rodapé. Você pode "commitar" de forma organizada:

```bash
# 1. Verifique as mudanças
git status

# 2. Adicione apenas os dois arquivos do formulário:
git add formulario.html
git add css/form.css

# 3. Se precisar ver o que já está na Staging Area (pronto para o commit):
git diff --staged

# 4. Caso tenha adicionado um arquivo por engano, você pode desfazer o add:
git restore --staged css/form.css
```

### Boas Práticas

Evite usar `git add .` às cegas. Sempre verifique quais arquivos foram modificados usando `git status` antes. Prefira adicionar arquivos individualmente ou por partes lógicas para garantir que seus commits tenham um único propósito bem definido.

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
*Na saída acima: `index.html` está na staging area; `style.css` foi modificado, mas não está preparado; `script.js` é um arquivo novo que o Git não conhece.*

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

O comando `git log` é usado para visualizar o histórico de commits do seu repositório. Ele mostra informações detalhadas sobre cada commit realizado, incluindo autor, data, mensagem e identificador único (hash).

## Sintaxe Básica

**Formato padrão (detalhado):**

```bash
git log
```

Este comando exibe:
- **Hash do commit**: Identificador único (ex: `a1b2c3d4e5f6...`)
- **Autor**: Nome e e-mail de quem fez o commit
- **Data**: Quando o commit foi realizado
- **Mensagem**: Descrição do que foi feito

**Formato resumido (uma linha por commit):**

```bash
git log --oneline
```

Mostra apenas o hash abreviado e a mensagem do commit, ideal para ter uma visão geral rápida do histórico.

## Entendendo o Output

Quando você executa `git log`, verá algo assim:

```
commit a1b2c3d4e5f6g7h8i9j0 (HEAD -> main, origin/main)
Author: João Silva <joao@email.com>
Date:   Mon May 1 14:30:00 2023 -0300

    docs: adiciona seção sobre git init

commit k9l8m7n6o5p4q3r2s1t0
Author: Maria Santos <maria@email.com>
Date:   Mon May 1 10:15:00 2023 -0300

    fix: corrige exemplo de git clone
```

**Elementos importantes:**
- **(HEAD -> main, origin/main)**: Indica onde está o ponteiro HEAD e os branches
- **Hash do commit**: Identificador único de 40 caracteres (exibido completo)
- **Author**: Nome e e-mail configurados no Git
- **Date**: Data e hora do commit com timezone
- **Mensagem**: Descrição do que foi alterado

## Opções Úteis

**Visualização gráfica de branches:**
```bash
git log --graph
```
Mostra um gráfico ASCII com a estrutura de branches e merges.

**Ver todos os branches:**
```bash
git log --all
```
Exibe commits de todos os branches, não apenas o atual.

**Mostrar referências (tags e branches):**
```bash
# Mostra cada commit em apenas uma linha (Hash e Mensagem)
git log --oneline

# Mostra o histórico em forma de árvore/grafo (útil quando há múltiplas branches)
git log --graph --oneline

# Filtra commits de um autor específico
git log --author="Antonio"

# Filtra commits recentes
git log --since="2 weeks ago"
```
Indica onde estão as branches e tags no histórico.

**Combinando opções (recomendado):**
```bash
git log --oneline --graph --all
```
Formato compacto com visualização gráfica de todos os branches.

## Filtros de Busca

**Por autor:**
```bash
git log --author="João Silva"
```

**Por mensagem de commit:**
```bash
git log --grep="docs"
```
Busca commits que contenham "docs" na mensagem.

**Por período:**
```bash
git log --since="2 weeks ago"
git log --until="2023-05-01"
```

**Combinando filtros:**
```bash
git log --author="Maria" --since="1 month ago" --oneline
```

## Exemplo Prático

Para ver um histórico visual completo do projeto:

```bash
git log --oneline --graph --all --decorate
```

Resultado esperado:

```
* a1b2c3d (HEAD -> main, origin/main) docs: adiciona seção sobre git init
* k9l8m7n (feat/nova-funcionalidade) feat: implementa nova feature
| * b2c3d4e (fix/correcao-bug) fix: corrige erro de digitação
|/
* m7n6o5p docs: atualiza README
* q3r2s1t Initial commit
```

**Interpretando o gráfico:**
- `*` = Commit
- `|` = Linha do branch
- `/` = Merge ou divergência de branches
- Os hashes são abreviados (7 caracteres)
- As referências (HEAD, branches) aparecem entre parênteses

## git log vs git reflog

**git log:**
- Mostra o histórico de **commits** do projeto
- Lista apenas commits que fazem parte do histórico oficial
- Útil para ver o que foi desenvolvido

**git reflog:**
- Mostra **todas as ações** realizadas no repositório local
- Inclui mudanças de branch, resets, rebases, merges
- Útil para recuperar trabalho perdido

Exemplo de quando usar cada um:
- "Quais commits foram feitos no projeto?" → `git log`
- "Fiz um reset errado, como voltar?" → `git reflog`

## Navegando no Pager

Quando o histórico é longo, o Git usa um pager (less) para exibir o conteúdo:

- **Descer**: Seta para baixo ou Enter
- **Subir**: Seta para cima
- **Próxima página**: Espaço
- **Buscar**: Digite `/` seguido do termo
- **Sair**: Pressione `q`

**Dica**: Se você não quiser usar o pager, adicione `--no-pager`:
```bash
git --no-pager log --oneline
```

## git diff

O comando `git diff` é essencial para visualizar as diferenças entre várias versões do seu projeto. Ele mostra exatamente o que mudou (linhas adicionadas, modificadas ou removidas) entre o diretório de trabalho (*working directory*), a área de preparação (*staging area*), commits específicos ou branches.

### Tipos de Diff e Casos de Uso

Existem diferentes formas de usar o `git diff` dependendo do que você deseja comparar:

```bash
# 1. Compara Working Directory vs Staging Area
# Mostra mudanças que você fez mas ainda NÃO adicionou com 'git add'
git diff

# 2. Compara Staging Area vs Último Commit (HEAD)
# Mostra o que vai entrar no próximo commit
git diff --staged
# (Nota: 'git diff --cached' é um sinônimo exato)

# 3. Compara Working Directory vs Último Commit
# Mostra TODAS as mudanças desde o último commit (staged ou não)
git diff HEAD

# 4. Compara dois commits específicos
git diff <commit1> <commit2>

# 5. Compara duas branches
git diff main..feature-branch
```

### Opções Úteis

Você pode refinar a saída do `git diff` com algumas opções importantes:

```bash
# Mostra apenas um resumo das mudanças (arquivos alterados e total de linhas)
git diff --stat

# Mostra apenas os nomes dos arquivos que mudaram
git diff --name-only

# Compara as mudanças de um arquivo específico em dois commits
git diff <commit1> <commit2> -- caminho/do/arquivo.txt

# Compara as mudanças de um arquivo específico no working tree
git diff -- caminho/do/arquivo.txt

# Compara as mudanças staged de um arquivo específico
git diff --staged -- caminho/do/arquivo.txt

# Atalho: Compara com o commit anterior ao atual
git diff HEAD~1
```

### Lendo a Saída (Unified Diff Format)

O `git diff` usa o formato *Unified Diff*. Entender sua estrutura é fundamental:

```diff
diff --git a/index.html b/index.html
index 8b3c4f..3d1a2c 100644
--- a/index.html
+++ b/index.html
@@ -10,4 +10,5 @@
     <h1>Bem-vindo</h1>
-    <p>Texto antigo</p>
+    <p>Texto atualizado</p>
+    <button>Clique aqui</button>
 </body>
```

**Como interpretar:**

- `--- a/arquivo`: Versão original/antiga.
- `+++ b/arquivo`: Versão nova/modificada.
- `@@ -10,4 +10,5 @@`: Contexto. Indica que as mudanças começam ao redor da linha 10.
- Linhas começando com `-` (geralmente em vermelho): Foram **removidas**.
- Linhas começando com `+` (geralmente em verde): Foram **adicionadas**.
- Linhas sem sinal: Contexto inalterado para ajudar na localização.

### Ferramentas Visuais

Se a leitura no terminal for difícil em mudanças muito grandes, você pode usar ferramentas visuais (GUI) configuradas previamente:

```bash
# Abre a ferramenta visual de diff configurada (ex: VSCode, Meld, KDiff3)
git difftool
```

## git restore

O `git restore` é um comando moderno introduzido em versões mais recentes do Git para desfazer alterações e remover arquivos da staging area de forma mais intuitiva que o antigo `git reset` e partes do `git checkout`.

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
# Desfaz as alterações de um arquivo no Working Directory (volta para o estado do último commit)
# CUIDADO: Isso APAGA suas alterações não salvas definitivamente!
git restore index.html

# Remove o arquivo da Staging Area (Unstage), mas MANTÉM as alterações no arquivo
git restore --staged index.html
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
git rm: Remove o arquivo do disco e já prepara a deleção no Git.

### Removendo Arquivos

```bash
# Remove o arquivo e prepara a remoção
git rm arquivo-obsoleto.txt
git commit -m "chore: remove arquivo obsoleto"
```

### Diferença de rm normal

Se você usar o comando de terminal normal `rm arquivo.txt`, o arquivo some, mas o Git o registra como uma "Change not staged". Você teria que rodar `git add arquivo.txt` para preparar a remoção. O `git rm` faz os dois passos de uma vez.

## git mv

Usado para mover ou renomear arquivos.

### Renomeando/Movendo Arquivos

```bash
# Renomear um arquivo
git mv nome-antigo.txt nome-novo.txt

# Mover um arquivo para uma pasta
git mv arquivo.txt pasta/arquivo.txt
```
O Git reconhece automaticamente como uma alteração do tipo renomeação, deixando preparado (staged) para o commit.

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
    
    D -.->|sync| E[GitHub]
    D <-->|push/pull| F[origin]
    D <-->|fetch| G[upstream]
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
git clone https://github.com/meu-usuario/projeto.git
cd projeto
# [Eu edito alguns arquivos de código]
git status
git add app.js index.html
git commit -m "feat: adiciona lógica inicial do app"
git log --oneline
```

### Próximos Passos

Agora que você dominou o fluxo básico, explore:

- **[03-branching-e-merge.md](03-branching-e-merge.md)** - Criando e gerenciando branches
- **[04-pull-requests-e-review.md](04-pull-requests-e-review.md)** - Enviando PRs para revisão

## Comandos de Consulta

### git show

Mostra o conteúdo detalhado, mensagens e as alterações de um commit específico.

```bash
# Ver os detalhes do último commit (HEAD)
git show HEAD

# Ver detalhes de um commit através de seu Hash
git show a1b2c3d
```

### git blame

Mostra quem modificou cada linha de um arquivo por último, exibindo o autor e o hash do commit. Ótimo para descobrir quem causou aquele bug ou tirar dúvidas com o autor do trecho de código.

```bash
git blame arquivo.txt
```

## Exemplos Práticos

### Exemplo 1: Criando Primeiro Repositório

```bash
mkdir novo-site
cd novo-site
git init
echo "# Meu Novo Site" > README.md
git status
git add README.md
git commit -m "docs: cria o README inicial"
git log --oneline
```

### Exemplo 2: Clonando e Contribuindo

```bash
git clone https://github.com/exemplo/repositorio.git
cd repositorio
# Editar um arquivo
git status
git diff
git add .
git commit -m "fix: corrige erro de digitação"
```

### Exemplo 3: Desfazendo Alterações

```bash
# Se eu fiz uma alteração indesejada num arquivo
git status
git restore index.html # Minha alteração errada some, volto ao código limpo do último commit
```

## Erros Comuns

### Erro 1: Esquecer de git add

Fazer um `git commit` achando que as alterações serão salvas, mas o Git diz que não há nada para commitar. 
**Solução:** Sempre rode `git status` e `git add` antes.

### Erro 2: Mensagem de commit vaga

Escrever `git commit -m "ok"` ou `git commit -m "mudanças"`. Em seis meses, você não fará ideia do que isso significa. 
**Solução:** Descreva **o que** mudou de forma resumida e direta.

### Erro 3: Committar arquivos errados

Fazer um `git add .` às cegas e acidentalmente adicionar senhas, chaves de API ou arquivos pesados/pessoais que não deveriam ir para o repositório.
**Solução:** Sempre use `git status` antes de adicionar, e aprenda sobre `.gitignore`.

### Erro 4: Confundir git reset e git restore

- `git restore`: Trabalha nos arquivos. Usado para desfazer modificações em arquivos soltos.
- `git reset`: Trabalha na linha do tempo. Usado para voltar ou desfazer commits inteiros (veja no capítulo de resolução de problemas).

## Exercícios

1. Crie uma nova pasta no seu computador chamada `treino-git` e transforme-a em um repositório Git usando `git init`.
2. Crie um arquivo `anotacoes.txt`, adicione um texto qualquer, e faça seu primeiro `commit`.
3. Altere o texto desse arquivo. Rode `git diff` para visualizar a alteração no terminal, depois adicione (`add`) e comite (`commit`).
4. Visualize seu histórico com `git log --oneline`.
5. Modifique o arquivo de novo, mas não adicione (sem `add`). Use o comando `git restore` para descartar a sua mudança e confirme rodando `git status`.

## Tabela de Referência Rápida

Legenda de badges:

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

- [Git Reference Manual - Comandos Principais](https://git-scm.com/docs)
- [Git Cheat Sheet Interativo](https://ndpsoftware.com/git-cheatsheet.html)
- [Aprenda Git Branching (Visual e Prático)](https://learngitbranching.js.org/)

## Resumo

- O ciclo de vida do salvamento de arquivos no Git é essencialmente: `Modificar -> git add -> git commit`.
- **`git status`** é o seu melhor amigo. Use sem moderação.
- O histórico é valioso e permanente (`git log`).
- O **`git diff`** mostra *exatamente* o que mudou, enquanto o status mostra *onde* mudou.
- Você pode sempre recuar de erros nos arquivos modificados usando **`git restore`**.

---

```bash
git commit -m "Criei o Guia Completo sobre Comandos Essenciais do Git"
```

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir: -->
- [@idarlandias](https://github.com/idarlandias) - Seção Comando git add
<!-- Adicione seu nome quando contribuir:
- [@Tom-Junior](https://github.com/Tom-Junior) - Seção todas
-->
- [@Giseleptbr](https://github.com/Giseleptbr) - Seção git commit
- [@AIWASS23](https://github.com/AIWASS23) - Seção git status
- [@hailtonDavid](https://github.com/hailtonDavid) - Seção git diff
- [@esleiu](https://github.com/esleiu) - Seção tabela de referência rápida
- [@Giseleptbr](https://github.com/Giseleptbr) - Seção git commit
- [@hailtonDavid](https://github.com/hailtonDavid) - Seção git restore

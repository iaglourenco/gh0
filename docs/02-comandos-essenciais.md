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

O comando `git clone` é usado para criar uma cópia local de um repositório remoto. Ele baixa todo o histórico do projeto (commits, branches e arquivos) e configura automaticamente a origem remota (normalmente chamada de `origin`). Ao executar `git clone`, você não apenas obtém os arquivos atuais, mas todo o histórico de versionamento, permitindo trabalhar plenamente com o repositório.

### Sintaxe

```bash
git clone <url-do-repositorio>
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
git clone https://github.com/git/git.git
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
# Adiciona um arquivo específico:
git add nome-do-arquivo.txt

# Adiciona todos os arquivos modificados e novos na pasta atual:
git add .

# Adiciona TODAS as alterações no repositório inteiro (incluindo arquivos apagados):
git add -A
# ou
git add --all
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

Evite usar `git add .` se você modificou muitas coisas diferentes que não têm relação entre si. Prefira adicionar os arquivos um a um (`git add <arquivo>`) ou em pequenos grupos para garantir que seus commits contem uma história lógica e bem dividida.

## git status

<!-- TODO: Explique git status -->
O melhor amigo do desenvolvedor. Mostra o estado atual das três áreas do Git.

### O que Mostra

<!-- TODO: Tipos de informação que git status exibe -->
<!-- Arquivos modificados, staged, untracked, etc. -->
- Arquivos Untracked (novos, que o Git ainda não conhece).
- Arquivos Modified (alterados, mas não adicionados ao stage).
- Arquivos Staged (prontos para o commit).

### Exemplo de Saída

```bash
On branch main                                      # Você está na branch principal (a oficial).
Changes to be committed:                            # Arquivos que já estão na STAGING AREA.
  (use "git restore --staged <file>..." to unstage) # Comando para remover do stage se desistir.
        new file:   model.py                        # Este arquivo será gravado no próximo commit.

Changes not staged for commit:                      # Arquivos no WORKING DIRECTORY (ainda não preparados).
  (use "git add <file>..." to update what will be committed) # Sugestão: use 'add' para preparar.
        modified:   README.md                       # O arquivo foi alterado, mas o Git ainda não o "empacotou".
```

### Quando Usar

<!-- TODO: Por que verificar status frequentemente -->
Antes de cada git add (para ver o que mudou) e antes de cada git commit (para conferir o que está sendo gravado).

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
git log --decorate
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
| `git status` | Mostra o estado atual | O tempo todo (entre comandos) |
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
<!-- Adicione seu nome quando contribuir: -->
- [@idarlandias](https://github.com/idarlandias) - Seção Comando git add
<!-- Adicione seu nome quando contribuir:
- [@Tom-Junior](https://github.com/Tom-Junior) - Seção todas
-->
- [@Giseleptbr](https://github.com/Giseleptbr) - Seção git commit
- [@hailtonDavid](https://github.com/hailtonDavid) - Seção git restore

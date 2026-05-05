# Ferramentas e Recursos

<!-- Este arquivo apresenta ferramentas, extensões e recursos para trabalhar com Git e GitHub -->

## 📋 Objetivos de Aprendizagem

<!-- TODO: Objetivos sobre ferramentas e recursos -->

## 🎯 Introdução

<!-- TODO: Git além da linha de comando -->
<!-- Ecossistema Rico de ferramentas -->

## Git GUI Tools

### GitHub Desktop

<!-- TODO: Cliente oficial do GitHub -->

#### Características

<!-- TODO: Interface simples, integração GitHub -->

#### Quando Usar

<!-- TODO: Iniciantes, operações básicas -->

#### Download

<!-- TODO: Link e instruções -->

### GitKraken

<!-- TODO: Cliente visual poderoso -->

#### Características

<!-- TODO: Graph visual, merge tool, integrações -->

#### Recursos Avançados

<!-- TODO: GitFlow integrado, resolução de conflitos -->

#### Planos

<!-- TODO: Free vs Pro -->

### SourceTree

<!-- TODO: Cliente da Atlassian -->

#### Características

<!-- TODO: Gratuito, Git Flow, visualização -->

#### Plataformas

<!-- TODO: Windows e macOS -->

### Tower

<!-- TODO: Cliente premium -->

#### Características

<!-- TODO: Interface refinada, recursos avançados -->

### Outros

<!-- TODO: GitFiend, Fork, SmartGit -->

## Extensions e Plugins

### VS Code

O VS Code permite instalar extensões para adicionar novos recursos ao editor, como integração com Git, suporte a linguagens de programação, temas, atalhos, ferramentas de produtividade e integração com plataformas como o GitHub.

Para instalar uma extensão no VS Code:

1. Abra o **Visual Studio Code**;
2. Clique no ícone de **Extensions** na barra lateral esquerda;
3. Ou use o atalho `Ctrl + Shift + X`;
4. Pesquise pelo nome da extensão desejada;
5. Clique em **Install**;
6. Após a instalação, algumas extensões podem pedir para reiniciar o VS Code ou configurar opções adicionais.

Também é possível instalar extensões diretamente pelo terminal usando o comando:

```bash
code --install-extension nome-da-extensao
code --install-extension eamodio.gitlens
```
**Fonte:** [Documentação oficial do VS Code sobre extensões](https://code.visualstudio.com/docs/getstarted/extensions)

#### GitLens

Extensão popular para o VS Code que melhora a integração com o Git, permitindo visualizar informações detalhadas sobre commits, autores, histórico de arquivos e alterações no código diretamente no editor.

##### Recursos

- **Blame inline:** mostra, ao lado de cada linha do código, quem fez a última alteração, quando ela foi feita e em qual commit.
- **Histórico de arquivo:** permite visualizar todas as alterações feitas em um arquivo ao longo do tempo.
- **Comparações:** facilita comparar versões diferentes de um arquivo, commits ou branches.
- **Graph:** exibe um grafo visual do histórico do repositório, mostrando commits, branches, merges e tags.

> **Em outras IDEs**
>
> - **IntelliJ IDEA:** possui recursos nativos parecidos com o GitLens, como histórico de arquivos, comparação entre versões, visualização de commits e o recurso **Annotate**, que mostra quem alterou cada linha do código.
> - **Sublime Text / Sublime Merge:** o Sublime Text pode ser usado junto com o **Sublime Merge** para visualizar histórico, commits, branches e alterações do repositório de forma gráfica.

**Fonte:** [GitLens no Visual Studio Marketplace](https://marketplace.visualstudio.com/itemdetails?itemName=eamodio.gitlens)

#### Git Graph

Extensão para o VS Code que permite visualizar o histórico de commits do repositório em formato de grafo. Ela ajuda a entender melhor a evolução do projeto, mostrando branches, merges, tags e commits de maneira visual e organizada.

##### Recursos

- **Visual log:** exibe os commits em uma linha do tempo gráfica, facilitando a leitura do histórico.
- **Branches:** mostra as ramificações do projeto e ajuda a entender em qual branch cada alteração foi feita.
- **Merges:** permite visualizar quando branches foram unidas ao projeto principal.
- **Tags:** identifica versões importantes do projeto, como releases.
- **Comparações:** facilita comparar commits e verificar quais arquivos foram modificados.

> **Em outras IDEs**
>
> - **IntelliJ IDEA:** possui a aba **Git Log**, que permite visualizar commits, branches, merges e tags em formato gráfico, funcionando como uma alternativa ao Git Graph.
> - **Sublime Text / Sublime Merge:** o **Sublime Merge** oferece uma visualização gráfica do histórico do repositório, mostrando commits, branches e merges de forma clara e organizada.

**Fonte:** [Git Graph no Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)

#### GitHub Pull Requests

Extensão do VS Code que permite gerenciar **Pull Requests** e **Issues** do GitHub diretamente no editor. Com ela, é possível visualizar PRs, revisar alterações, comentar trechos de código, aprovar ou solicitar mudanças e acompanhar discussões sem precisar sair do VS Code.

##### Recursos

- **Listagem de Pull Requests:** mostra os PRs abertos no repositório diretamente dentro do VS Code.
- **Revisão de código:** permite analisar arquivos modificados, comparar alterações e verificar o que será incorporado ao projeto.
- **Comentários em trechos de código:** possibilita comentar linhas específicas durante a revisão.
- **Aprovação ou solicitação de mudanças:** ajuda no fluxo de revisão, permitindo aprovar um PR ou pedir ajustes antes do merge.
- **Integração com Issues:** permite acompanhar tarefas, problemas e discussões relacionadas ao projeto.

> **Em outras IDEs**
>
> - **IntelliJ IDEA:** possui integração com GitHub, permitindo visualizar Pull Requests, revisar alterações, comentar código e acompanhar branches diretamente pela IDE.
> - **Sublime Text / Sublime Merge:** o fluxo de Pull Requests costuma ser feito com apoio do navegador ou do GitHub Desktop. O **Sublime Merge** pode auxiliar na visualização dos commits, branches e alterações antes de abrir ou revisar um PR no GitHub.

**Fontes:** [GitHub Pull Requests no VS Code](https://code.visualstudio.com/blogs/2018/09/10/introducing-github-pullrequests); [GitHub Pull Requests](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)


#### Settings e Keybindings para Git

Além de instalar extensões, o VS Code permite configurar preferências e atalhos relacionados ao Git. Por exemplo, é possível criar atalhos para abrir o Git Graph, acessar o painel de controle de versão, visualizar histórico de arquivos ou abrir rapidamente a Command Palette.

Alguns atalhos úteis são:

- `Ctrl + Shift + G`: abrir o painel de Source Control;
- `Ctrl + Shift + P`: abrir a Command Palette;
- `Ctrl + Shift + X`: abrir a aba de extensões;
- `Ctrl + '` : abrir o terminal integrado.

#### Ganhos de produtividade

O uso dessas extensões aumenta a produtividade porque reduz a necessidade de executar comandos Git manualmente no terminal para tarefas visuais e repetitivas. O GitLens facilita a análise de autoria e histórico, o Git Graph melhora a visualização dos commits, o GitHub Pull Requests centraliza revisões de código no editor e o Gitmoji ajuda a padronizar mensagens de commit.

Dessa forma, o desenvolvedor consegue trabalhar com mais organização, rapidez e clareza dentro do próprio VS Code.


### JetBrains IDEs

<!-- TODO: Git integrado -->

#### Recursos

<!-- TODO: Merge tool, history, branches -->

### Sublime Text

<!-- TODO: Package Sublime Merge -->

### Vim

<!-- TODO: vim-fugitive plugin -->

## Terminal Tools

### tig

<!-- TODO: Interface ncurses para Git -->

```bash
# TODO: Instalação e uso básico
```

### lazygit

<!-- TODO: TUI simples para Git -->

```bash
# TODO: Instalação e uso
```

### gh (GitHub CLI)

A CLI oficial do GitHub (`gh`) traz as funcionalidades do GitHub diretamente para o seu terminal. Ela permite gerenciar repositórios, issues, pull requests e até GitHub Actions sem precisar abrir o navegador.

#### Comandos Principais

```bash
# Autenticar-se na sua conta do GitHub
gh auth login

# Clonar um repositório do GitHub (alternativa conveniente ao git clone)
gh repo clone <owner>/<repo>

# Listar issues abertas no repositório atual
gh issue list

# Visualizar detalhes de uma issue específica
gh issue view <numero-da-issue>

# Criar um novo Pull Request a partir da branch atual
gh pr create --title "feat: adiciona nova funcionalidade" --body "Detalhes aqui"

# Listar e verificar o status de GitHub Actions
gh run list
```

### hub

<!-- TODO: Extensão Git para GitHub (predecessor do gh) -->

## Diff Tools

### Meld

<!-- TODO: Diff e merge visual -->

### Beyond Compare

<!-- TODO: Ferramenta comercial poderosa -->

### KDiff3

<!-- TODO: Open source -->

### P4Merge

<!-- TODO: Gratuito da Perforce -->

### Configurando Diff Tool

```bash
# TODO: git config --global diff.tool meld
```

## Merge Tools

<!-- TODO: Ferramentas para resolver conflitos -->

### Configurando

```bash
# TODO: git config --global merge.tool
```

### Usando

```bash
# TODO: git mergetool
```

## Shell Enhancements

### Oh My Zsh

<!-- TODO: Framework para Zsh -->

#### Git Plugin

<!-- TODO: Aliases e prompts -->

### Bash Git Prompt

<!-- TODO: Mostrar branch no prompt -->

### Starship

<!-- TODO: Cross-shell prompt moderno -->

## Comandos Avançados

### git bisect

O `git bisect` é uma ferramenta de **busca binária** (binary search) usada para encontrar exatamente qual commit introduziu um bug no seu projeto. 

Imagine que você descobriu um bug no código hoje, mas tem certeza de que a aplicação estava funcionando perfeitamente há duas semanas (uns 50 commits atrás). Em vez de testar esses 50 commits um por um para descobrir onde o código quebrou, o `git bisect` automatiza essa busca. Ele divide o histórico pela metade repetidamente, reduzindo drasticamente o número de testes que você precisa fazer.

#### Exemplo de Uso (Passo a Passo)

Para começar a investigação, você precisa de duas referências: um ponto no histórico onde o bug existe (geralmente o commit atual) e um commit mais antigo onde você tem certeza de que o bug não existia.

```bash
# 1. Inicie o modo de investigação do bisect
git bisect start

# 2. Diga ao Git que o commit atual está quebrado (tem o bug)
git bisect bad

# 3. Informe o hash de um commit antigo que você sabe que estava bom (sem o bug)
git bisect good 5a2b1c3

# =========================================================================
# A partir daqui, o Git fará uma "viagem no tempo" e mudará o seu código 
# para um commit exatamente na metade do caminho entre o bom e o ruim.
# =========================================================================

# 4. Teste o seu código manualmente (rode o app, execute testes locais, etc.).
# Se o bug AINDA estiver acontecendo nessa versão, diga ao Git:
git bisect bad

# Se o bug NÃO estiver acontecendo (o código está funcionando), diga ao Git:
git bisect good

# O Git repetirá o processo, cortando as opções pela metade e pedindo para
# você testar novamente, até isolar o commit exato. Quando terminar, ele 
# exibirá uma mensagem como: "1a2b3c4 is the first bad commit".

# 5. Após descobrir o commit culpado (ou se quiser cancelar a investigação), 
# encerre o bisect para que o Git devolva seu projeto ao estado atual (HEAD):
git bisect reset
```

### git cherry-pick

O comando `git cherry-pick` permite que você escolha um commit específico de uma branch e o aplique em outra, sem precisar fazer o *merge* (mesclagem) de toda a branch. 

Imagine que você está em uma árvore e quer pegar apenas uma cereja específica, e não o galho inteiro. É exatamente isso que o comando faz! Ele é extremamente útil em situações como:
* Você corrigiu um bug em uma branch de desenvolvimento e quer levar **apenas** essa correção para a branch principal (main/produção).
* Você fez um commit na branch errada por acidente e quer copiá-lo para a branch correta.

#### Comandos Cherry-pick

Para usar este comando, você precisa saber o **hash** (o código de identificação único) do commit que deseja "pescar". Você pode encontrar esse hash usando o comando `git log`.

Veja as principais formas de utilizá-lo:

```bash
# Aplica um único commit específico na sua branch atual
git cherry-pick 5a2b1c3

# Aplica múltiplos commits específicos de uma só vez (separados por espaço)
git cherry-pick 5a2b1c3 8f4d9e2

# Aplica um intervalo de commits (do commit mais antigo ao mais recente)
# Nota: O primeiro commit (A) não é incluído por padrão na cópia.
git cherry-pick commitA..commitB

# Para incluir o commitA no intervalo, adicione o acento circunflexo (^)
git cherry-pick commitA^..commitB
```

**Lidando com conflitos**
Assim como em um merge, o Git pode encontrar conflitos ao tentar aplicar o código (se as mesmas linhas tiverem sido alteradas de formas diferentes nas branches). Quando isso acontece, o Git pausa o processo para você resolver.
```bash
# 1. Resolva os conflitos manualmente no seu editor de código.
# 2. Adicione os arquivos resolvidos na área de stage:
git add arquivo-resolvido.js

# 3. Diga ao Git para continuar a aplicar o cherry-pick:
git cherry-pick --continue

# Caso desista no meio do conflito e queira cancelar tudo, voltando ao estado anterior:
git cherry-pick --abort
```

### git rebase

O `git rebase` é uma ferramenta avançada para integrar alterações de uma branch em outra. A grande diferença dele para o `git merge` é que o rebase **reescreve o histórico** do projeto.

Em vez de criar um "commit de merge" (que junta duas linhas do tempo e deixa o gráfico com ramificações), o rebase pega os commits da sua branch atual, os "levanta", e os aplica um a um exatamente no topo da branch de destino. O resultado final é um histórico perfeitamente linear, como se você tivesse começado a trabalhar a partir da versão mais recente do código.

#### Rebase Interativo

A flag `-i` (interativo) transforma o rebase em uma verdadeira máquina do tempo. Ele permite que você edite, junte, reorganize ou exclua commits antigos da sua branch antes de enviá-la para o repositório remoto.

```bash
# Inicia o rebase interativo focando nos últimos 3 commits da branch atual
git rebase -i HEAD~3

# =========================================================================
# O Git abrirá seu editor de texto padrão com uma lista (do mais antigo no topo 
# para o mais recente embaixo). Por padrão, todos vêm com a palavra 'pick':
# =========================================================================
# pick 1a2b3c4 Adiciona o componente de botão
# pick 5d6e7f8 Corrige erro de digitação na cor do botão
# pick 9g0h1i2 Atualiza o README.md

# Você deve alterar a palavra 'pick' para a ação que deseja realizar:

# 1. REWORD (r): Altera apenas a mensagem do commit (o código fica intacto)
# Ex: r 1a2b3c4 Adiciona o componente de botão (o Git pedirá a nova mensagem depois)

# 2. SQUASH (s): Junta este commit com o commit imediatamente acima dele
# Ex: s 5d6e7f8 Corrige erro de digitação (este código será fundido com o 1a2b3c4)

# 3. EDIT (e): Pausa o rebase neste ponto para você modificar arquivos no código
# Ex: e 9g0h1i2 Atualiza o README.md (após editar, rode 'git commit --amend' e 'git rebase --continue')

# 4. DROP (d): Exclui o commit permanentemente do seu histórico
# Ex: d 9g0h1i2 Atualiza o README.md (joga o commit inteiro no lixo)
```

#### Quando Usar

A principal utilidade do rebase é limpar e organizar o seu histórico local antes de abrir um Pull Request (PR) ou enviar o código para a equipe.

Se durante o seu desenvolvimento você fez dezenas de commits quebrados ou com mensagens ruins (ex: "wip", "teste", "agora vai"), você pode usar o git rebase -i para fazer um squash, transformando toda essa bagunça em um único commit limpo, funcional e bem documentado. Além disso, o rebase é ótimo para manter sua branch de trabalho atualizada com a main sem poluir o histórico com dezenas de "commits de merge" desnecessários.

#### Quando NÃO Usar

A Regra de Ouro do Git: Nunca faça rebase em branches públicas ou compartilhadas!

Jamais faça rebase na main, develop ou em uma branch (feature) que outro colega esteja trabalhando junto com você. Como o rebase destrói os commits antigos e cria novos commits (com novos hashes), se você fizer isso em um histórico que já foi baixado por outras pessoas, o Git de todos da equipe vai quebrar e entrar em conflito.

O rebase deve ser usado estritamente no seu ambiente local (na sua branch isolada) antes de compartilhá-la com o mundo.

### git stash

Como mencionado no Capítulo 03, o `git stash` funciona como uma "gaveta temporária" para o seu código. 

Ele é extremamente útil quando você está trabalhando em uma funcionalidade, mas precisa trocar de branch rapidamente (para corrigir um bug crítico, por exemplo) e não quer fazer um commit de um código incompleto. O `git stash` guarda essas alterações inacabadas com segurança e deixa o seu diretório de trabalho limpo, exatamente no estado do último commit.

#### Comandos Stash

Abaixo estão os principais comandos para gerenciar o seu stash, com exemplos práticos:

**1. Salvando alterações (stash)**
Guarda as suas modificações atuais (arquivos modificados e na área de *stage*).

```bash
# Salva as alterações rapidamente (o Git cria uma mensagem automática)
git stash

# Salva as alterações com uma mensagem descritiva (recomendado)
git stash push -m "WIP: validação do formulário de contato"

# Salva incluindo arquivos novos que ainda não são rastreados pelo Git (untracked)
git stash -u
#### Comandos Stash
```

**2. Listando o que está guardado (list)**
```bash
# Lista todos os stashes armazenados
git stash list

# Saída de exemplo que aparecerá no terminal: 
# stash@{0}: On main: WIP: validação do formulário de contato
# stash@{1}: On develop: Ajustes no CSS do cabeçalho
```

**3. Recuperando e removendo o código (pop)**
```bash
# Aplica e remove o stash mais recente (stash@{0})
git stash pop

# Aplica e remove um stash específico da lista
git stash pop stash@{1}
```

**4. Recuperando sem remover da lista (apply)**
```bash
# Aplica o stash mais recente sem apagá-lo da lista
git stash apply

# Aplica um stash específico sem apagá-lo da lista
git stash apply stash@{1}
```

**5. Descartando um stash (drop)**
```bash
# Apaga apenas o stash mais recente
git stash drop

# Apaga um stash específico
git stash drop stash@{1}
```

**6. Limpando todos os stashes (clear)**
```bash
# Esvazia a "gaveta" completamente (use com cautela!)
git stash clear
```

### git reflog

O `git reflog` (Reference Logs) é a sua **rede de segurança definitiva** no Git. Ele funciona como uma "caixa preta" ou um diário oculto que registra absolutamente *todas* as movimentações que você faz no seu repositório local (mudanças de branch, commits, resets, rebases, etc.).

Diferente do `git log`, que mostra apenas o histórico "oficial" da branch atual, o reflog registra por onde o seu ponteiro `HEAD` (onde você estava trabalhando) passou ao longo do tempo. 

**Por que isso é incrível?** No Git, quase nada é deletado de verdade imediatamente. Se você deletar uma branch por acidente, fizer um `reset --hard` no lugar errado, ou destruir seu histórico com um `rebase` mal feito, os seus commits não somem; eles apenas ficam "órfãos" no limbo do Git. O `git reflog` permite que você encontre o *hash* desses commits perdidos e os traga de volta à vida.

> **Nota:** O reflog é estritamente local e individual. Ele registra apenas as ações feitas no seu computador e é limpo automaticamente pelo Git após um período (geralmente de 30 a 90 dias).

#### Recuperando commits "perdidos"

Aqui está o passo a passo de como usar o reflog para salvar o seu dia quando algo der muito errado:

```bash
# 1. Visualize o diário de todas as suas ações recentes
git reflog

# =========================================================================
# O Git mostrará uma lista parecida com esta (do mais recente para o mais antigo):
# =========================================================================
# 5a2b1c3 (HEAD -> main) HEAD@{0}: reset: moving to HEAD~1
# 9g0h1i2 HEAD@{1}: commit: Adiciona funcionalidade de pagamento <-- (O COMMIT PERDIDO!)
# 5a2b1c3 HEAD@{2}: checkout: moving from feature-pagamento to main
# =========================================================================

# 2. Identifique o hash do commit que você quer recuperar na lista (ex: 9g0h1i2).

# 3. RECUPERAÇÃO (OPÇÃO A): Criar uma nova branch a partir do commit perdido.
# Esta é a opção mais segura, pois salva o código sem alterar a sua branch atual.
git checkout -b branch-salvadora 9g0h1i2

# 3. RECUPERAÇÃO (OPÇÃO B): Forçar a sua branch atual a voltar para aquele commit.
# Use com cautela! Isso fará a sua branch atual "viajar no tempo" de volta
# para o estado exato daquele commit.
git reset --hard 9g0h1i2
```

### git clean

<!-- TODO: Remover arquivos untracked -->

```bash
# TODO: git clean -fd (cuidado!)
```

### git reset

O comando `git reset` é o "botão de desfazer" do Git. Diferente do `rebase` (que reorganiza) ou do `revert` (que cria um novo commit desfazendo algo), o `reset` literalmente **volta no tempo**. 

Ele pega o ponteiro da sua branch atual (onde você está trabalhando) e o arrasta para um commit anterior no histórico, como se os commits que vieram depois nunca tivessem existido.

O comportamento do `reset` muda drasticamente dependendo da *flag* (opção) que você usa. Ele possui três níveis de intensidade: `--soft`, `--mixed` e `--hard`.

#### Os 3 Níveis de Reset

Entender a diferença entre eles é a chave para não perder código acidentalmente.

* **`--soft` (O mais gentil):** Volta no tempo, mas mantém todas as suas alterações na área de *stage* (prontas para serem commitadas novamente). Ótimo para quando você fez um commit pequeno demais e quer desfazê-lo apenas para adicionar mais um arquivo ao mesmo pacote.
* **`--mixed` (O padrão):** Volta no tempo e tira as alterações da área de *stage*. Seus arquivos continuam modificados no seu computador (Diretório de Trabalho), mas você terá que rodar `git add` de novo. É excelente para quando você quer refazer os commits de uma forma diferente.
* **`--hard` (O destruidor):** ⚠️ **Cuidado!** Volta no tempo e apaga **absolutamente tudo** o que foi feito depois daquele commit. O seu Diretório de Trabalho ficará idêntico ao que era no passado. Use apenas quando tiver certeza de que quer jogar as alterações recentes no lixo.

```bash
# Volta 1 commit para trás, mas mantém as mudanças no stage (prontas para commit)
git reset --soft HEAD~1

# Volta 1 commit para trás e tira as mudanças do stage (você não perde o código)
# Como o --mixed é o padrão, omitir a flag tem o mesmo efeito
git reset --mixed HEAD~1
git reset HEAD~1

# Volta 1 commit para trás e DELETA todas as mudanças daquele commit
# Seu código voltará exatamente para o estado do commit anterior
git reset --hard HEAD~1

# ==========================================
# Usando Hashes em vez de atalhos (HEAD~):
# ==========================================
# Se você quer voltar para um ponto específico no tempo, você pode 
# usar o hash do commit desejado.

# Descarta todos os commits até o hash '5a2b1c3' (jogando as alterações fora)
git reset --hard 5a2b1c3
```

#### Diferença reset vs revert

<!-- TODO: reset reescreve, revert cria novo commit -->

### git blame

<!-- TODO: Ver quem modificou cada linha -->

```bash
# TODO: git blame arquivo.md
```

### git tag

O comando `git tag` funciona como um marcador de página definitivo ou uma "etiqueta" colada em um momento específico do seu histórico. 

Diferente das branches (que se movem para a frente a cada novo commit), uma tag é estática; ela sempre apontará para o mesmo commit. Por causa dessa característica, as tags são o padrão universal da comunidade de desenvolvimento para **marcar pontos de lançamento (releases)** ou versões estáveis do seu software (ex: `v1.0.0`, `v2.1.3`, `beta-v1`).

Existem dois tipos principais de tags:
* **Lightweight (Leves):** É apenas um nome apontando para um commit. Ideal para marcações temporárias e uso pessoal.
* **Annotated (Anotadas):** São as recomendadas para lançamentos oficiais. Elas guardam o nome de quem criou, a data, o e-mail e uma mensagem (exatamente como um commit).

#### Criando e Gerenciando Tags

Abaixo estão os comandos para criar tags anotadas (recomendado) e compartilhá-las com a sua equipe:

```bash
# ==========================================
# 1. Criando Tags para Releases
# ==========================================
# Cria uma tag anotada (flag -a) na sua branch/commit atual, 
# incluindo uma mensagem descritiva (flag -m)
git tag -a v1.0.0 -m "Release 1.0: Lançamento inicial para produção"

# Se você esqueceu de taguear e já fez outros commits, 
# pode aplicar a tag em um commit passado usando o hash dele:
git tag -a v0.9.0 5a2b1c3 -m "Versão Beta"

# ==========================================
# 2. Listando e Visualizando
# ==========================================
# Lista todas as tags que existem no seu repositório local
git tag

# Mostra os detalhes de uma tag específica (autor, data e o código do commit)
git show v1.0.0

# ==========================================
# 3. Enviando Tags para o Remoto (GitHub/GitLab)
# ==========================================
# ATENÇÃO: O comando 'git push' normal NÃO envia tags automaticamente!
# Você precisa enviá-las de forma explícita.

# Envia uma tag específica para o repositório remoto
git push origin v1.0.0

# Envia TODAS as suas tags locais de uma só vez para o remoto
git push origin --tags
```

## Aliases Úteis

### Configurando Aliases

```bash
# TODO: Exemplos de aliases úteis
# git config --global alias.st status
# git config --global alias.co checkout
# git config --global alias.lg "log --graph --oneline"
```

### Aliases Recomendados

<!-- TODO: Lista de aliases populares -->

## Git LFS

### O que É

<!-- TODO: Large File Storage -->

### Quando Usar

<!-- TODO: Vídeos, imagens grandes, binários -->

### Instalação

```bash
# TODO: git lfs install
```

### Uso

```bash
# TODO: git lfs track "*.psd"
```

## Geradores e Helpers

### gitignore.io

<!-- TODO: Gerar .gitignore templates -->

### choosealicense.com

<!-- TODO: Escolher licença para projeto -->

### keepachangelog.com

<!-- TODO: Padrão para CHANGELOG -->

### Semantic Release

<!-- TODO: Automatizar releases -->

## Learning Resources

### Interactive

#### Learn Git Branching
É a ferramenta visual mais famosa para entender como os commits e as branches se comportam.
- **Link:** [https://learngitbranching.js.org/](https://learngitbranching.js.org/)
- **Quando usar:** Quando tiver dificuldade em visualizar o que o `merge` ou `rebase` fazem com o grafo.
- **Destaque:** Traduzido para Português.

#### Oh My Git!
Um jogo interativo de código aberto que utiliza uma interface de cartas.
- **Link:** [https://ohmygit.org/](https://ohmygit.org/)
- **Quando usar:** Para aprender de forma lúdica, ideal para quem está fugindo de documentações densas no início.

#### GitHub Skills (Antigo Learning Lab)
Cursos hands-on baseados em repositórios reais com feedback automático.
- **Link:** [https://skills.github.com/](https://skills.github.com/)

### Books

#### Pro Git (O Livro)
A "bíblia" oficial do Git, escrita por Scott Chacon e Ben Straub.
- **Link:** [https://git-scm.com/book/pt-br/v2](https://git-scm.com/book/pt-br/v2)
- **Nível:** Iniciante (capítulos 1-3) ao Avançado (capítulos 7-10).
- **Idioma:** Português e Inglês.

#### Git from the Bottom Up
Focado em como o Git funciona "por baixo do capô" (objetos, hashes e referências).
- **Link:** [https://jwiegley.github.io/git-from-the-bottom-up/](https://jwiegley.github.io/git-from-the-bottom-up/)
- **Nível:** Avançado.

### Cheat Sheets

Aqui estão algumas das melhores "colas" (cheat sheets) gratuitas para você salvar nos favoritos ou imprimir, servindo como uma referência rápida para os comandos mais utilizados:

- [GitHub Git Cheat Sheet Oficial](https://training.github.com/downloads/pt_BR/github-git-cheat-sheet/)
- [Atlassian Git Cheat Sheet](https://www.atlassian.com/br/git/tutorials/atlassian-git-cheatsheet)
- [Git Tower Cheat Sheet](https://www.git-tower.com/learn/cheat-sheets/git-pt)
- [Git Flow Cheat Sheet](https://danielkummer.github.io/git-flow-cheatsheet/index.pt_BR.html)

### Video Courses

<!-- TODO: YouTube channels, cursos online -->

### Blogs e Tutoriais

<!-- TODO: Recursos de qualidade -->

- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [GitHub Guides](https://guides.github.com/)

## Documentation

### Official Git Docs
Referência técnica absoluta para todos os comandos e protocolos.
- **Site:** [git-scm.com](https://git-scm.com/doc)
- **Idioma:** Inglês.

### GitHub Docs
Documentação completa da plataforma, cobrindo desde Issues até Actions e Segurança.
- **Site:** [docs.github.com](https://docs.github.com/pt)
- **Idioma:** Português disponível.

### Man Pages
Você pode acessar a documentação direto no seu terminal:
```bash
git help <comando>
# Exemplo: git help commit
```

## Troubleshooting Tools

### Git Doctor

```bash
# TODO: git fsck (verificar integridade)
```

### Git Log Filtering

```bash
# TODO: Filtros avançados de log
# --author, --since, --grep, -S
```

### git show

<!-- TODO: Inspecionar commits específicos -->

## Productivity Tips

### Keyboard Shortcuts

<!-- TODO: Atalhos do GitHub -->

### Browser Extensions

#### Octotree

<!-- TODO: Navegação em árvore -->

#### Refined GitHub

<!-- TODO: Melhorias na interface -->

#### OctoLinker

<!-- TODO: Navegação entre arquivos -->

## Community Resources

### GitHub Community Forum

<!-- TODO: Fazer perguntas -->

### Stack Overflow

<!-- TODO: Tag [git] e [github] -->

### Reddit

<!-- TODO: r/git, r/github -->

## Configurações Avançadas

### Git Config Global

```bash
# TODO: Configurações úteis
# core.autocrlf
# pull.rebase
# rerere.enabled
```

### Git Attributes

<!-- TODO: .gitattributes file -->

### Git Hooks

<!-- TODO: Automação local -->

#### Pre-commit

<!-- TODO: Lint, format antes de commit -->

#### Pre-push

<!-- TODO: Rodar testes antes de push -->

## GitHub Features

### Emoji in Commits

O uso de emojis em commits ajuda a identificar rapidamente o tipo de alteração feita no projeto. Uma das convenções mais conhecidas é o **Gitmoji**, que associa cada emoji a uma intenção específica do commit.

Essa prática pode ser combinada com **Conventional Commits**, deixando as mensagens mais padronizadas, legíveis e fáceis de entender no histórico do Git.

Exemplos:

- ✨ `feat: adiciona nova funcionalidade`
- 🐛 `fix: corrige bug no login`
- 📝 `docs: atualiza documentação`
- 🎨 `style: melhora formatação do código`
- ♻️ `refactor: reorganiza estrutura interna`
- ✅ `test: adiciona testes unitários`

Exemplo completo:

```bash
git commit -m "✨ feat: adiciona autenticação com GitHub"
```

> **Em outras IDEs**
>
> - **IntelliJ IDEA:** o Gitmoji pode ser usado diretamente no campo de mensagem de commit, junto com o padrão de escrita definido pela equipe, como `✨ feat: adiciona nova funcionalidade`.
> - **Sublime Text / Sublime Merge:** também permite escrever mensagens de commit com emojis. O uso do Gitmoji não depende de uma extensão específica, pois está relacionado à forma como o desenvolvedor escreve e padroniza os commits.

**Fonte:** [Gitmoji — An emoji guide for your commit messages](https://gitmoji.dev/)

### Markdown Tips

<!-- TODO: Recursos avançados de Markdown -->

#### Task Lists

```markdown
- [x] TODO: Exemplo
- [ ] Tarefa pendente
```

#### Collapsible Sections

```markdown
<details>
<summary>TODO: Clique para expandir</summary>

Conteúdo oculto

</details>
```

## Continuous Integration

### Travis CI

<!-- TODO: Integração popular -->

### CircleCI

<!-- TODO: Alternativa -->

### Jenkins

<!-- TODO: Self-hosted -->

## Monitoring e Analysis

### GitStats

<!-- TODO: Estatísticas do repositório -->

### CodeClimate

<!-- TODO: Análise de qualidade -->

### Codecov

<!-- TODO: Cobertura de testes -->

## Backup e Mirror

### Backup Strategies

<!-- TODO: Como fazer backup de repos -->

### Mirroring

```bash
# TODO: git clone --mirror
```

## Exemplos Práticos

### Exemplo 1: Setup Completo de Ambiente

<!-- TODO: Do zero a produtivo -->

### Exemplo 2: Usando GitKraken

<!-- TODO: Walkthrough da ferramenta -->

### Exemplo 3: Aliases e Produtividade

<!-- TODO: Configurar ambiente otimizado -->

## Erros Comuns

### Erro 1: Conflitar Ferramentas GUI e CLI

<!-- TODO: Entender o que cada ferramenta faz -->

### Erro 2: Depender Só de GUI

<!-- TODO: Aprender CLI também -->

## Recomendações

### Para Iniciantes

<!-- TODO: GitHub Desktop + VS Code + GitLens -->

### Para Intermediários

<!-- TODO: GitKraken + CLI + Oh My Zsh -->

### Para Avançados

⚠️ **AVISO - ZONA DE PERIGO:** As ferramentas e configurações desta seção são voltadas para *Power Users*. Elas assumem que você entende profundamente a arquitetura interna do Git (ponteiros, reflogs, árvores e a diferença real entre as áreas de *stage* e *working directory*). Com grande poder, vem a responsabilidade de poder destruir seu histórico local se você não souber o que está fazendo. Proceda com cautela!

#### O Poder Supremo da CLI

Enquanto interfaces gráficas (GUIs) como GitKraken ou a aba de controle de versão do VS Code são excelentes e confortáveis, um usuário avançado de Git domina o terminal. A Interface de Linha de Comando (CLI) é o único lugar onde você tem 100% de acesso às ferramentas de baixo nível (*plumbing* commands) do Git, sem as abstrações ou "travas de segurança" que as ferramentas visuais impõem.

#### Tig: O Canivete Suíço do Terminal

Se você quer a visualização de uma GUI sem sair do terminal, o `tig` é a resposta. Ele é uma interface em modo texto (ncurses) para o Git, que funciona como um navegador de repositório ultrarrápido.

* **Por que usar?** É absurdamente rápido para investigar o histórico de commits, fazer `blame` em arquivos e, principalmente, realizar o *staging* interativo de blocos de código específicos (adicionar apenas algumas linhas de um arquivo modificado ao invés do arquivo inteiro).

```bash
# Nota: O tig precisa ser instalado separadamente (via brew, apt-get, choco, etc).

# Abre um navegador de histórico interativo e colorido (substitui o git log)
# Use as setas para navegar e 'Enter' para dividir a tela e ver os diffs do commit
tig

# Abre a visualização de status (perfeito para staging interativo cirúrgico)
# Use 'u' para adicionar (update) arquivos inteiros ou partes do código (chunks) ao stage
tig status

# Inspeciona rapidamente o que foi alterado entre duas branches
tig main..minha-feature
```

#### Custom Aliases (Modo Turbo)

Digitar comandos longos repetidamente é perda de tempo. Usuários avançados moldam o Git para o seu próprio fluxo de trabalho configurando Aliases (atalhos personalizados).

Você pode configurá-los editando manualmente o seu arquivo `~/.gitconfig` ou rodando os comandos abaixo no terminal. Aqui estão os atalhos definitivos para acelerar seu fluxo:

```bash
# ==========================================
# 1. A Árvore Perfeita (git lg)
# ==========================================
# Esqueça o 'git log' padrão. Este alias cria um gráfico colorido, 
# mostrando branches, datas relativas e autores de forma incrivelmente legível.
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

# Uso: git lg
# Uso com limite: git lg -10 (mostra os últimos 10)

# ==========================================
# 2. Correção Rápida (git amend)
# ==========================================
# Esqueceu de adicionar um arquivo no último commit? Adicione-o no stage
# e use este atalho para mesclá-lo ao último commit sem abrir o editor de texto.
git config --global alias.amend "commit --amend --no-edit"

# ==========================================
# 3. O Botão de Arrependimento (git undo)
# ==========================================
# Desfaz o seu último commit instantaneamente, mas joga todas as suas 
# modificações de volta na área de stage prontas para uso.
git config --global alias.undo "reset --soft HEAD~1"

# ==========================================
# 4. A Opção Nuclear (git nuke) ☢️
# ==========================================
# Limpa completamente o seu diretório de trabalho. Ele reseta tudo para 
# o último commit e DELETA todos os arquivos novos/não rastreados (untracked).
# CUIDADO: Arquivos não rastreados apagados aqui NÃO vão para o reflog!
git config --global alias.nuke "!git reset --hard HEAD && git clean -fd"
```

## Resumo

<!-- TODO: Principais ferramentas e recursos -->

### Essenciais

- <!-- Git CLI -->
- <!-- GitHub Desktop ou GitKraken -->
- <!-- VS Code com GitLens -->
- <!-- GitHub CLI (gh) -->

### Recursos de Aprendizagem

- <!-- Pro Git Book -->
- <!-- Learn Git Branching -->
- <!-- GitHub Learning Lab -->

---

## 👥 Contribuidores
<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->
<!-- Adicione seu nome quando contribuir: -->

- [@p-esteves](https://github.com/p-esteves) - Seções de Recursos de Aprendizagem e Documentação (#64, #65)
- [@camiwr](https://github.com/camiwr) - Seção Extensions e Plugins & GitHub Features
- [@idarlandias](https://github.com/idarlandias) - Seção Cheat Sheets

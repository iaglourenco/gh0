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

#### GitLens

<!-- TODO: Extensão popular para Git -->

##### Recursos

- <!-- Blame inline -->
- <!-- Histórico de arquivo -->
- <!-- Comparações -->
- <!-- Graph -->

#### Git Graph

<!-- TODO: Visualizar grafo de commits -->

#### GitHub Pull Requests

<!-- TODO: Gerenciar PRs no VS Code -->

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

<!-- TODO: CLI oficial do GitHub -->

#### Comandos Principais

```bash
# TODO: gh repo, gh pr, gh issue, gh workflow
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

<!-- TODO: Debugging binário para encontrar bugs -->

```bash
# TODO: Exemplo de uso
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

<!-- TODO: Histórico de referências -->

```bash
# TODO: Recuperar commits "perdidos"
```

### git clean

<!-- TODO: Remover arquivos untracked -->

```bash
# TODO: git clean -fd (cuidado!)
```

### git reset

<!-- TODO: Desfazer commits -->

```bash
# TODO: --soft, --mixed, --hard
```

#### Diferença reset vs revert

<!-- TODO: reset reescreve, revert cria novo commit -->

### git blame

<!-- TODO: Ver quem modificou cada linha -->

```bash
# TODO: git blame arquivo.md
```

### git tag

<!-- TODO: Criar tags para releases -->

```bash
# TODO: git tag -a v1.0.0 -m "Release 1.0"
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

<!-- TODO: Jogo interativo -->
<!-- https://learngitbranching.js.org/ -->

#### GitHub Learning Lab

<!-- TODO: Cursos hands-on -->

### Books

#### Pro Git

<!-- TODO: Livro completo e gratuito -->
<!-- https://git-scm.com/book/pt-br/v2 -->

#### Git from the Bottom Up

<!-- TODO: Entendimento profundo -->

### Cheat Sheets

<!-- TODO: Links para cheat sheets -->

- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Atlassian Git Cheat Sheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

### Video Courses

<!-- TODO: YouTube channels, cursos online -->

### Blogs e Tutoriais

<!-- TODO: Recursos de qualidade -->

- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [GitHub Guides](https://guides.github.com/)

## Documentation

### Official Git Docs

<!-- TODO: git-scm.com -->

### GitHub Docs

<!-- TODO: docs.github.com -->

### Man Pages

```bash
# TODO: git help <comando>
# man git-<comando>
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

<!-- TODO: Gitmoji, conventional commits -->

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

<!-- TODO: CLI + tig + custom aliases -->

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

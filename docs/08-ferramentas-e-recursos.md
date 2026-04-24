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

<!-- TODO: Aplicar commits específicos -->

```bash
# TODO: Sintaxe e exemplos
```

### git rebase

<!-- TODO: Reescrever histórico -->

#### Rebase Interativo

```bash
# TODO: git rebase -i
# Squash, reword, edit, drop
```

#### Quando Usar

<!-- TODO: Limpar histórico antes de PR -->

#### Quando NÃO Usar

<!-- TODO: Nunca em branches públicas -->

### git stash

<!-- TODO: Já mencionado em cap 03, detalhes aqui -->

#### Comandos Stash

```bash
# TODO: stash, pop, apply, list, drop, clear
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

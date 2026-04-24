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
<!-- Adicione seu nome quando contribuir: -->
- [@idarlandias](https://github.com/idarlandias) - Seção Cheat Sheets

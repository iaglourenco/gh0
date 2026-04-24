# Ferramentas e Recursos

Este capítulo apresenta ferramentas, extensões e recursos para trabalhar com Git e GitHub de forma mais produtiva, tanto para iniciantes quanto para usuários avançados.

## Objetivos de Aprendizagem

Ao final deste capítulo, você será capaz de:

- escolher ferramentas adequadas para seu nível e sistema operacional;
- usar interfaces gráficas e de terminal de forma complementar;
- configurar recursos de diff/merge para resolver conflitos com mais segurança;
- aplicar comandos avançados para depuração e recuperação de histórico;
- montar um ambiente de trabalho mais eficiente para colaboração no GitHub.

## 🎯 Introdução

Git é muito mais do que comandos no terminal. Existe um ecossistema completo de GUIs, extensões de IDE, CLIs auxiliares e recursos de aprendizado que aceleram tarefas do dia a dia.

Não existe "melhor ferramenta universal". O ideal é combinar:

- uma base sólida de CLI do Git;
- uma GUI para visualização e operações mais complexas;
- integrações no editor para manter fluxo contínuo de trabalho.

## Git GUI Tools

### GitHub Desktop

Cliente oficial do GitHub com foco em simplicidade.

#### Características

- interface amigável para commits, branches e pull requests;
- integração direta com conta GitHub;
- histórico visual e comparação de alterações.

#### Quando Usar

- para iniciantes que ainda estão se adaptando ao terminal;
- em fluxos de contribuição com operações básicas e frequentes.

#### Download

- [https://desktop.github.com/](https://desktop.github.com/)

### GitKraken

Cliente visual avançado com ótimo grafo de commits.

#### Características

- visualização de histórico e branches em formato de grafo;
- ferramentas de merge/rebase com interface clara;
- integrações com GitHub, GitLab, Bitbucket e Jira.

#### Recursos Avançados

- suporte facilitado a Git Flow;
- resolução de conflitos com interface visual;
- filtros de histórico e navegação rápida.

#### Planos

- versão gratuita para uso pessoal;
- versões pagas com recursos corporativos e colaboração ampliada.

### SourceTree

Cliente gratuito da Atlassian para Git.

#### Características

- gerenciamento de branch, stash e histórico;
- suporte a Git Flow;
- boa visualização de diferenças.

#### Plataformas

- Windows
- macOS

### Tower

Cliente premium com foco em produtividade para equipes.

#### Características

- interface refinada;
- recursos avançados de histórico e resolução de conflitos;
- fluxos guiados para operações complexas.

### Outros

- **Fork**: rápido, moderno e com boa experiência em diff/merge;
- **SmartGit**: opção robusta para ambientes corporativos;
- **GitFiend**: alternativa mais simples para uso cotidiano.

## Extensões e Plugins

### VS Code

#### GitLens

Extensão popular para ampliar capacidades de Git no editor.

##### Recursos

- blame inline (quem alterou e quando);
- histórico por arquivo/linha;
- comparação de revisões;
- visualização de grafo de commits.

#### Git Graph

Mostra o histórico em formato de grafo dentro do VS Code, facilitando entendimento de merges e branches.

#### GitHub Pull Requests and Issues

Permite abrir, revisar e comentar PRs sem sair do editor.

### JetBrains IDEs

As IDEs JetBrains (IntelliJ, WebStorm, PyCharm etc.) possuem integração nativa com Git.

#### Recursos

- merge tool integrado;
- histórico e comparação de revisões;
- gerenciamento visual de branches e commits.

### Sublime Text

Uma opção comum é integrar com o **Sublime Merge** para fluxo Git visual.

### Vim

O plugin **vim-fugitive** adiciona comandos poderosos para Git no Vim.

## Terminal Tools

### tig

Interface em modo texto (ncurses) para explorar histórico de commits.

```bash
# Instalação (Ubuntu/Debian)
sudo apt install tig

# Abrir histórico do repositório
tig
```

### lazygit

TUI simples e moderna para operações Git frequentes.

```bash
# Exemplo com Scoop (Windows)
scoop install lazygit

# Executar no diretório do repositório
lazygit
```

### gh (GitHub CLI)

CLI oficial do GitHub para issues, PRs, ações e muito mais.

#### Comandos Principais

```bash
# Autenticar
gh auth login

# Criar PR
gh pr create

# Listar issues
gh issue list

# Executar workflow manualmente
gh workflow run <nome-do-workflow>
```

### hub

Ferramenta legada (predecessora do `gh`). Hoje, prefira `gh` para novos fluxos.

## Diff Tools

### Meld

Ferramenta visual gratuita para comparação e merge de arquivos.

### Beyond Compare

Ferramenta comercial muito completa para diff de texto, pastas e binários.

### KDiff3

Opção open source com suporte a merge de 3 vias.

### P4Merge

Ferramenta gratuita da Perforce para diff e merge visual.

### Configurando Diff Tool

```bash
git config --global diff.tool meld
git config --global difftool.prompt false
```

## Merge Tools

Ferramentas de merge ajudam a resolver conflitos com segurança visual.

### Configurando

```bash
git config --global merge.tool meld
git config --global mergetool.prompt false
```

### Usando

```bash
git mergetool
```

## Shell Enhancements

### Oh My Zsh

Framework para Zsh com plugins de produtividade.

#### Git Plugin

Adiciona aliases úteis e informações de branch no prompt.

### Bash Git Prompt

Mostra estado da branch e arquivos alterados direto no terminal.

### Starship

Prompt moderno e multiplataforma para PowerShell, Bash, Zsh e Fish.

## Comandos Avançados

### git bisect

Encontra o commit que introduziu um bug usando busca binária.

```bash
git bisect start
git bisect bad
git bisect good <commit-antigo-conhecido>
# testar a cada etapa e marcar:
git bisect good
git bisect bad
git bisect reset
```

### git cherry-pick

Aplica commits específicos em outra branch.

```bash
git cherry-pick <hash-do-commit>
```

### git rebase

Reaplica commits sobre outra base para manter histórico linear.

#### Rebase Interativo

```bash
git rebase -i HEAD~5
# ações comuns: pick, reword, edit, squash, drop
```

#### Quando Usar

- para limpar histórico antes de abrir PR;
- para atualizar branch de feature com `main` sem merge commit extra.

#### Quando NÃO Usar

- em branches públicas já compartilhadas sem alinhamento com o time.

### git stash

Guarda mudanças temporariamente sem commit.

#### Comandos Stash

```bash
git stash
git stash list
git stash apply
git stash pop
git stash drop stash@{0}
```

### git reflog

Registro de movimentações de HEAD, útil para recuperar estados "perdidos".

```bash
git reflog
git checkout <hash-antigo>
```

### git clean

Remove arquivos não rastreados.

```bash
git clean -n   # simulação
git clean -fd  # remove de fato (cuidado)
```

### git reset

Move ponteiros e desfaz estágios/commits locais.

```bash
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1
```

#### Diferença reset vs revert

- `reset`: reescreve histórico local;
- `revert`: cria novo commit desfazendo alterações (mais seguro em branch pública).

### git blame

Mostra quem alterou cada linha de um arquivo.

```bash
git blame docs/08-ferramentas-e-recursos.md
```

### git tag

Marca versões importantes (releases).

```bash
git tag -a v1.0.0 -m "Release 1.0.0"
git push origin v1.0.0
```

## Aliases Úteis

### Configurando Aliases

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.lg "log --graph --oneline --decorate --all"
```

### Aliases Recomendados

- `st`: status rápido;
- `lg`: log com grafo;
- `co`: troca de branch;
- `last`: último commit (`log -1 HEAD`).

## Git LFS

### O que É

Git LFS (Large File Storage) é uma extensão para versionar arquivos grandes sem inflar o histórico principal do Git.

### Quando Usar

- imagens pesadas;
- vídeos;
- binários e assets de design.

### Instalação

```bash
git lfs install
```

### Uso

```bash
git lfs track "*.psd"
git add .gitattributes
git add arquivo.psd
git commit -m "chore: adiciona rastreamento de arquivos grandes com lfs"
```

## Geradores e Helpers

### gitignore.io

Gera `.gitignore` com base em linguagem, framework e editor.

- [https://www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore)

### choosealicense.com

Ajuda a escolher licença apropriada para seu projeto.

- [https://choosealicense.com/](https://choosealicense.com/)

### keepachangelog.com

Referência de padrão para escrever `CHANGELOG.md`.

- [https://keepachangelog.com/pt-BR/1.1.0/](https://keepachangelog.com/pt-BR/1.1.0/)

### Semantic Release

Automatiza versionamento e publicação com base em commits convencionais.

## Recursos de Aprendizagem

### Interativos

#### Learn Git Branching

Simulador visual excelente para praticar branch, merge e rebase.

- [https://learngitbranching.js.org/](https://learngitbranching.js.org/)

#### GitHub Skills

Cursos práticos oficiais dentro do próprio GitHub.

- [https://skills.github.com/](https://skills.github.com/)

### Livros

#### Pro Git

Livro completo e gratuito, disponível em português.

- [https://git-scm.com/book/pt-br/v2](https://git-scm.com/book/pt-br/v2)

#### Git from the Bottom Up

Leitura para entender conceitos internos do Git.

### Cheat Sheets

- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Atlassian Git Cheat Sheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

### Blogs e Tutoriais

- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)
- [GitHub Docs](https://docs.github.com/pt)

## Documentação

### Official Git Docs

- [https://git-scm.com/doc](https://git-scm.com/doc)

### GitHub Docs

- [https://docs.github.com/pt](https://docs.github.com/pt)

### Man Pages

```bash
git help <comando>
man git-<comando>
```

## Troubleshooting Tools

### Integridade do Repositório

```bash
git fsck
```

### Filtros de Log

```bash
git log --author="nome"
git log --since="2 weeks ago"
git log --grep="fix"
git log -S "texto-procurado"
```

### git show

Inspeciona um commit específico (autor, data, diff e mensagem).

```bash
git show <hash-do-commit>
```

## Dicas de Produtividade

### Atalhos de Navegação no GitHub

- pressione `t` para buscar arquivos rapidamente no repositório;
- pressione `.` para abrir o editor web do GitHub.

### Extensões de Navegador

#### Octotree

Adiciona árvore de arquivos no GitHub web.

#### Refined GitHub

Melhora a interface do GitHub com vários ajustes úteis.

#### OctoLinker

Facilita navegação entre símbolos e arquivos referenciados.

## Recursos da Comunidade

### GitHub Community Forum

- [https://github.community/](https://github.community/)

### Stack Overflow

Use as tags `git` e `github` para encontrar dúvidas similares.

### Reddit

Comunidades como `r/git` e `r/github` podem ser úteis para troca de experiências.

## Configurações Avançadas

### Git Config Global

```bash
git config --global core.autocrlf true
git config --global pull.rebase false
git config --global rerere.enabled true
```

### Git Attributes

Use `.gitattributes` para padronizar EOL, tratamento de binários e regras de diff.

### Git Hooks

Automatizam verificações antes de commit/push.

#### Pre-commit

Rodar lint e formatadores para evitar commits com problemas simples.

#### Pre-push

Rodar testes para reduzir falhas em CI.

## Recursos do GitHub

### Commits Semânticos

Padronize mensagens com Conventional Commits (`feat:`, `fix:`, `docs:` etc.) e, se quiser, use Gitmoji.

### Dicas de Markdown

#### Task Lists

```markdown
- [x] Documento revisado
- [ ] Link validado
```

#### Collapsible Sections

```markdown
<details>
<summary>Clique para expandir</summary>

Conteúdo complementar aqui.

</details>
```

## Continuous Integration

### GitHub Actions

Principal opção para CI/CD em projetos hospedados no GitHub.

### CircleCI

Alternativa popular em pipelines com foco em velocidade e paralelismo.

### Jenkins

Solução self-hosted altamente customizável.

## Monitoring e Analysis

### GitStats

Geração de estatísticas de contribuição e evolução do repositório.

### CodeClimate

Análise de qualidade e métricas de manutenibilidade.

### Codecov

Relatórios de cobertura de testes integrados ao PR.

## Backup e Mirror

### Estratégias de Backup

- espelhar repositórios críticos;
- manter remotos secundários;
- realizar backups periódicos de artefatos e releases.

### Mirroring

```bash
git clone --mirror <url-origem>
cd repo.git
git push --mirror <url-destino>
```

## Exemplos Práticos

### Exemplo 1: Setup Completo de Ambiente

1. instalar Git e configurar nome/email;
2. instalar VS Code + GitLens;
3. autenticar `gh` com `gh auth login`;
4. criar aliases básicos de produtividade.

### Exemplo 2: Fluxo de PR com GUI + CLI

1. criar branch pela CLI;
2. editar e revisar diffs na GUI;
3. abrir PR com `gh pr create`.

### Exemplo 3: Recuperação de Erro com reflog

1. identificar hash antigo com `git reflog`;
2. restaurar estado com `git checkout` ou `git reset`.

## Erros Comuns

### Erro 1: Misturar GUI e CLI sem entender estado do repositório

Antes de cada ação crítica, valide `git status` para evitar confusão.

### Erro 2: Depender só de GUI

Aprender o básico da CLI é essencial para debugging e automação.

## Recomendações

### Para Iniciantes

- GitHub Desktop
- VS Code com GitLens
- comandos básicos de Git no terminal

### Para Intermediários

- GitKraken ou SourceTree
- `gh` para fluxo de issues/PR
- aliases e melhorias de shell

### Para Avançados

- CLI como base principal
- `lazygit`/`tig` para navegação rápida
- hooks, CI e versionamento semântico

## Resumo

Ferramentas não substituem fundamentos de Git, mas aceleram o trabalho e reduzem erros quando usadas com estratégia.

### Essenciais

- Git CLI
- uma GUI (GitHub Desktop, GitKraken, SourceTree ou similar)
- VS Code com GitLens
- GitHub CLI (`gh`)

### Recursos de Aprendizagem

- Pro Git Book
- Learn Git Branching
- GitHub Skills

---

## 👥 Contribuidores

Este conteúdo é colaborativo. Adicione seu nome ao contribuir:

- [@douglaslpo](https://github.com/douglaslpo) - Estruturação e preenchimento do capítulo 08

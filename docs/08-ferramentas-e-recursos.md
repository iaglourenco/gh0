# Ferramentas e Recursos

<!-- Este arquivo apresenta ferramentas, extensões e recursos para trabalhar com Git e GitHub -->

## 📋 Objetivos de Aprendizagem

Ao final deste capítulo, você será capaz de:
- Conhecer e escolher interfaces gráficas (GUIs) para trabalhar com Git.
- Instalar e configurar extensões em editores de código (como VS Code) para otimizar o fluxo de trabalho.
- Descobrir ferramentas avançadas de terminal para aumentar a produtividade.
- Acessar recursos de aprendizado, cheatsheets e tutoriais para aprofundamento contínuo.

## 🎯 Introdução

Embora a linha de comando seja a forma mais pura e poderosa de interagir com o Git, ela não é a única. O ecossistema em torno do Git e do GitHub é gigantesco. Existem ferramentas visuais que tornam a resolução de conflitos mais fácil, extensões de editores que mostram quem escreveu cada linha de código em tempo real, e ferramentas de terminal que adicionam "superpoderes" ao seu fluxo diário. Conhecer essas ferramentas é essencial para trabalhar de forma profissional e eficiente.

## Git GUI Tools (Interfaces Gráficas)

Nem tudo precisa ser feito no terminal. As interfaces gráficas (GUIs) são excelentes para visualizar a árvore de histórico (commits) e para revisar o que você modificou antes de fazer um commit.

### GitHub Desktop

O cliente oficial e gratuito criado pelo próprio GitHub.

#### Características
Possui uma interface extremamente limpa e amigável. Foca em simplificar o fluxo básico de commit, push, pull e criação de Pull Requests. Não possui recursos avançados de Git.

#### Quando Usar
Ideal para iniciantes que ainda se sentem intimidados pela linha de comando, ou para designers e gerentes de produto que precisam versionar arquivos, mas não precisam dos recursos complexos do Git.

#### Download
Disponível em: [desktop.github.com](https://desktop.github.com/)

### GitKraken

Um dos clientes Git visuais mais poderosos, populares e bonitos do mercado.

#### Características
Seu maior destaque é o "Commit Graph" visual, lindamente renderizado no centro da tela. Possui uma ferramenta de resolução de conflitos nativa fantástica e integrações diretas com GitHub, GitLab e Bitbucket.

#### Recursos Avançados
Suporte nativo a Git Flow, arrastar e soltar (drag and drop) para fazer rebase ou merge, e um terminal integrado.

#### Planos
Possui versão gratuita (apenas para repositórios públicos e locais) e planos Pro pagos para uso comercial e repositórios privados.
Disponível em: [gitkraken.com](https://www.gitkraken.com/)

### SourceTree

A alternativa gratuita e poderosa mantida pela Atlassian (empresa criadora do Jira e Bitbucket).

#### Características
100% gratuito. Suporta repositórios grandes e possui uma interface muito completa para usuários avançados, incluindo suporte total a Git Flow e LFS.

#### Plataformas
Disponível para Windows e macOS.

### Tower

Conhecido como "o cliente Git para profissionais", é uma ferramenta premium (paga).

#### Características
Interface nativa incrivelmente refinada para macOS (e também disponível para Windows). Oferece recursos como "Desfazer" global (Ctrl+Z para ações do Git), gerenciamento avançado de submódulos e suporte excelente a drag-and-drop.

### Outros Clientes
- **GitFiend:** Interface simples e open source.
- **Fork:** Rápido, leve e muito amado por desenvolvedores experientes.
- **SmartGit:** Focado em usuários que lidam com projetos gigantescos.

## Extensions e Plugins (Extensões de Editores)

A maneira mais produtiva de usar o Git hoje em dia é integrá-lo diretamente ao editor onde você escreve o código.

### VS Code (Visual Studio Code)

O VS Code já vem com um painel de "Source Control" excelente nativamente, mas algumas extensões o tornam perfeito:

#### GitLens

Provavelmente a extensão de Git mais famosa do mundo. 

##### Recursos
- **Blame inline:** Mostra sutilmente ao lado da linha de código quem a escreveu e quando (ex: *Antonio, há 2 anos • fix: corrige cálculo de imposto*).
- **Histórico de arquivo:** Permite viajar no tempo para ver como o arquivo era em commits passados.
- **Visualização de diffs:** Comparações visuais extremamente detalhadas.

#### Git Graph

Uma extensão simples que adiciona uma aba no VS Code mostrando a árvore (grafo) colorida de todos os commits e branches do repositório, permitindo fazer checkout, cherry-pick e merge com cliques do mouse.

#### GitHub Pull Requests and Issues

Extensão oficial do GitHub. Permite revisar PRs, comentar linhas de código e gerenciar Issues sem nunca sair do VS Code.

### JetBrains IDEs (IntelliJ, WebStorm, PyCharm)

As IDEs da JetBrains possuem uma das melhores integrações Git do mercado construída diretamente no núcleo do programa, sem precisar de plugins.

#### Recursos
Destaca-se pela sua ferramenta de resolução de "Three-way Merge", considerada por muitos como a melhor da indústria para resolver conflitos de código complexos.

### Sublime Text

A mesma empresa que cria o Sublime Text oferece o **Sublime Merge**, um cliente Git incrivelmente leve, rápido e com integração perfeita ao editor.

### Vim / Neovim

Para os puristas do terminal, o plugin **vim-fugitive** do Tim Pope é essencial. Ele é tão poderoso que seu criador o chama de "um cliente Git tão impressionante que deveria ser ilegal".

## Terminal Tools (Ferramentas de Linha de Comando)

Para quem prefere não sair do terminal, mas quer interfaces mais ricas.

### tig

Uma interface em modo texto (TUI) baseada em ncurses. Ela transforma o seu terminal em uma interface navegável do `git log`.

```bash
# Ubuntu
sudo apt install tig
# macOS
brew install tig

# Para usar, basta digitar:
tig
```

### lazygit

Uma ferramenta moderna, escrita em Go, que oferece uma interface visual maravilhosa (TUI) diretamente no seu terminal, controlada quase totalmente por atalhos de teclado fáceis de memorizar.

```bash
# Instalação macOS
brew install lazygit

# Para usar:
lazygit
```

### gh (GitHub CLI)

A ferramenta oficial de linha de comando do GitHub. Permite trazer toda a experiência do site (PRs, Issues, Actions) para o seu terminal.

#### Comandos Principais

```bash
# Clona um repositório rapidamente
gh repo clone organizacao/projeto

# Cria um Pull Request do seu terminal
gh pr create --title "Minha feature" --body "Detalhes"

# Lista as issues abertas
gh issue list

# Verifica o status dos testes (GitHub Actions)
gh run list
```

### hub

O predecessor não-oficial (mas muito famoso) do `gh`. Ele funcionava como um "wrapper" em cima do comando `git`, adicionando superpoderes como `git pull-request`. Hoje em dia, é recomendado migrar para o `gh`.

## Diff Tools e Merge Tools

Quando o conflito aperta, as ferramentas nativas podem não ser suficientes. Você pode configurar o Git para abrir ferramentas externas focadas exclusivamente em comparar textos.

### Ferramentas Populares
- **Meld:** Muito popular no Linux, open source, visualiza e resolve conflitos de 3 vias muito bem.
- **Beyond Compare:** Ferramenta comercial poderosíssima para comparação de arquivos, pastas e dados.
- **KDiff3:** Ferramenta open source clássica e robusta.
- **P4Merge:** Ferramenta gratuita da Perforce, com interface limpa e excelente para merges de 3 vias.

### Configurando no Git

Você pode definir uma ferramenta globalmente. Exemplo usando o Meld:

```bash
# Define a ferramenta de Diff
git config --global diff.tool meld

# Define a ferramenta de Merge
git config --global merge.tool meld

# Para usá-las, em vez de "git diff" ou resolver manual:
git difftool
git mergetool
```

## Shell Enhancements (Melhorias no Terminal)

Seu terminal não precisa ser preto e branco.

### Oh My Zsh

Framework incrivelmente popular para quem usa o shell `Zsh` (padrão atual do macOS).

#### Git Plugin
O Oh My Zsh possui um plugin `git` que adiciona dezenas de aliases úteis e modifica o "prompt" (a linha onde você digita os comandos) para mostrar em qual branch você está, e se há arquivos modificados (geralmente com um `X` vermelho ou um `*` amarelo).

### Starship

Um prompt cross-shell (funciona no Bash, Zsh, PowerShell, Fish) moderno, rápido e escrito em Rust. Ele mostra o status do seu repositório Git de forma elegante, além de detectar as linguagens do seu projeto (mostrando o ícone do Node.js, Python, etc.).

## Comandos Avançados do Git

Comandos poderosos que podem salvar o seu dia:

### git bisect

Uma ferramenta de "busca binária" incrível para encontrar bugs. Se você sabe que o bug não existia há 50 commits atrás, o `git bisect` pula automaticamente pelos commits passados, pedindo para você testar ("Tá quebrado aqui? E aqui?"), achando o commit culpado em poucos passos.

```bash
git bisect start
git bisect bad HEAD        # A versão atual tem o bug
git bisect good f4b82c     # O commit de um mês atrás estava funcionando
# O Git fará o checkout no meio do caminho. Teste e responda com "git bisect good" ou "git bisect bad".
```

### git cherry-pick

Pega um commit específico de qualquer lugar do projeto (outra branch, por exemplo) e aplica uma cópia exata dele na branch em que você está agora. Útil se você só quer pegar um "hotfix" de outra branch sem fazer merge do resto.

```bash
git cherry-pick <hash-do-commit>
```

### git rebase

A alternativa ao `git merge`. Ele reescreve a linha do tempo, pegando os seus commits novos e colocando-os perfeitamente no topo das novidades da linha principal, criando uma linha reta e sem "commits de merge" extras.

#### Rebase Interativo (`-i`)

O "editor de vídeo" do Git. Permite juntar vários commits em um só (Squash), renomear mensagens passadas (Reword), editar commits antigos ou deletá-los (Drop).

```bash
# Inicia um rebase interativo dos últimos 3 commits
git rebase -i HEAD~3
```

#### Regra de Ouro do Rebase
**NUNCA use rebase em branches públicas** (como `main`) que outras pessoas já baixaram. Ele reescreve a história, causando confusão para o resto do time. Use apenas na sua branch pessoal antes de abrir um PR.

### git stash

A "gaveta" do Git. 

```bash
git stash          # Guarda arquivos modificados e limpa o working directory
git stash pop      # Tira o último item guardado e aplica no código
git stash list     # Lista todas as gavetas guardadas
git stash drop     # Joga fora a gaveta especificada
```

### git reflog

O "seguro de vida" final do Git. É o histórico secreto que guarda TUDO o que você fez (mesmo deletar branches ou commits forçados). Se você destruiu algo com `reset --hard` por acidente, o reflog tem o hash do commit perdido para você recuperá-lo.

```bash
git reflog
git checkout <hash-encontrado-no-reflog>
```

### git reset

Mapeia o ponteiro da sua branch para um commit anterior, efetivamente desfazendo commits.

```bash
git reset --soft HEAD~1   # Desfaz o commit, mas mantém as alterações no palco (staging area)
git reset --mixed HEAD~1  # Padrão. Desfaz o commit e tira do palco (mantém as modificações no arquivo)
git reset --hard HEAD~1   # PERIGOSO: Desfaz o commit e APAGA DEFINITIVAMENTE as alterações do seu PC
```

#### Diferença reset vs revert
- `git reset`: Apaga a história (volta no tempo).
- `git revert <hash>`: Cria um NOVO commit que desfaz matematicamente o que o commit antigo fez. É a forma segura de desfazer coisas na branch `main`.

### git clean

Apaga todos os arquivos não-rastreados (untracked) do seu diretório. Cuidado, pois arquivos novos que não ganharam `git add` serão perdidos para sempre.

```bash
git clean -fd
```

## Aliases Úteis

Cansado de digitar os mesmos comandos longos? Crie atalhos!

### Configurando Aliases

Você pode adicionar isso no seu arquivo `~/.gitconfig`:

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm commit
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

O comando `git lg` acima vai gerar uma árvore visual lindíssima e colorida do seu histórico direto no terminal.

## Git LFS (Large File Storage)

### O que É
O Git foi feito para texto. Colocar arquivos binários gigantes (como vídeos `.mp4`, arquivos 3D ou PSDs de Photoshop) faz o repositório ficar lento e pesado. O Git LFS substitui esses arquivos grandes no repositório por pequenos arquivos de ponteiro, enquanto armazena o conteúdo real num servidor otimizado.

### Instalação e Uso

```bash
git lfs install
# Avisa ao Git LFS para cuidar de todos os arquivos de Photoshop
git lfs track "*.psd" 
git add .gitattributes
```

## Geradores e Helpers (Ajudantes Web)

Ferramentas web gratuitas para iniciar projetos mais rápido:

- **[gitignore.io](https://www.toptal.com/developers/gitignore):** Digite as tecnologias que você usa (ex: Node, Python, Windows) e ele gera o `.gitignore` perfeito.
- **[choosealicense.com](https://choosealicense.com/):** Não é advogado? Este site do GitHub te ajuda a escolher a licença Open Source correta para o seu projeto.
- **[keepachangelog.com](https://keepachangelog.com/):** Um padrão da indústria sobre como escrever um bom arquivo `CHANGELOG.md`.

## Learning Resources (Recursos de Aprendizagem)

### Interativos
- **[Learn Git Branching](https://learngitbranching.js.org/):** Provavelmente a melhor forma visual de entender branches e rebases brincando num jogo.
- **GitHub Skills:** Cursos gratuitos e práticos do próprio GitHub que criam repositórios reais para você treinar ações automatizadas.

### Livros (Gratuitos)
- **[Pro Git](https://git-scm.com/book/pt-br/v2):** O livro oficial e completo (disponível em Português). Leitura obrigatória para quem quer dominar a ferramenta.

### Cheat Sheets (Colas)
- [GitHub Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
- [Atlassian Git Cheat Sheet](https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet)

## Troubleshooting Tools (Resolvendo Problemas Ocultos)

### Git Doctor
O repositório está estranho ou corrompido? Verifique a integridade interna do banco de dados do Git:
```bash
git fsck
```

### Git Log Filtering (Filtros Avançados)

Procurando uma agulha no palheiro? O `git log` é incrível:
```bash
git log --author="Antonio"    # Só commits dessa pessoa
git log --since="2023-01-01"  # Só a partir desta data
git log --grep="fix: "        # Só commits cuja mensagem tenha essa palavra
git log -S "funcaoQuebrada()" # Só commits que adicionaram ou apagaram esse trecho de código específico!
```

## Configurações Avançadas

Algumas configurações globais que valem ouro:

```bash
# Como o Git deve lidar com quebras de linha entre Windows (CRLF) e Mac/Linux (LF)
git config --global core.autocrlf true # No Windows
git config --global core.autocrlf input # No Mac/Linux

# Faz com que o "git pull" sempre faça rebase em vez de criar commits de merge sujos
git config --global pull.rebase true

# Ativa a mágica do RERERE (Reuse Recorded Resolution): 
# O Git lembra como você resolveu um conflito difícil e resolve sozinho se acontecer de novo no futuro!
git config --global rerere.enabled true
```

## Community Resources (Comunidades)

Preso num erro estranho?
- **Stack Overflow:** Procure nas tags `[git]` e `[github]`. Quase todas as dúvidas de Git já foram respondidas lá.
- **Reddit:** Comunidades engajadas em `r/git` e `r/github`.
- **GitHub Community Forum:** O fórum oficial para dúvidas e anúncios da plataforma.

## Resumo

### Essenciais Diários
- Domine os conceitos na **CLI (linha de comando)** primeiro.
- Adote uma ferramenta como **VS Code com GitLens** para facilitar revisões constantes.
- Para gerenciar repositórios visualmente e resolver conflitos difíceis, considere o **GitKraken** ou o editor nativo da sua IDE (como as da JetBrains).

### Não Pare de Aprender
- Explore o `git rebase -i` e o `git cherry-pick` quando estiver confortável com o básico.
- Sempre tenha o link do **[Learn Git Branching](https://learngitbranching.js.org/)** guardado para visualizar mentalmente como o Git funciona.

---

## 👥 Contribuidores

Este conteúdo é colaborativo. Contribuidores deste arquivo:
- [@bigauke](https://github.com/bigauke) (Antonio Daniel de Souza Linhares) - Preenchimento do conteúdo sobre Ferramentas e Recursos.
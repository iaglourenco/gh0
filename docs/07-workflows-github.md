# Workflows no GitHub

<!-- Este arquivo explica diferentes workflows e recursos do GitHub -->

## 📋 Objetivos de Aprendizagem

Ao final deste módulo, você será capaz de:

- Entender os principais workflows de colaboração com Git e GitHub
- Escolher o workflow adequado para cada tipo de projeto
- Utilizar recursos como Issues, Projects, Actions e Pages
- Automatizar tarefas com GitHub Actions
- Publicar sites estáticos com GitHub Pages
- Proteger branches e gerenciar contribuições com segurança

## 🎯 Introdução

O GitHub vai muito além de simplesmente hospedar código. É uma **plataforma completa de colaboração e automação** que oferece ferramentas para gerenciar projetos, automatizar processos, publicar documentação e muito mais.

Conhecer os workflows e recursos disponíveis é fundamental para trabalhar de forma eficiente em equipe.

## O que é um Workflow?

Um **workflow de desenvolvimento** é um conjunto de práticas, convenções e processos que uma equipe adota para colaborar em um projeto de software. Ele define como o código é escrito, revisado, integrado e entregue.

Escolher um bom workflow ajuda a:
- Evitar conflitos de código
- Garantir qualidade com revisões
- Manter o histórico organizado
- Facilitar a integração contínua

## Fork Workflow

### O que é Fork?

Fork é uma **cópia completa de um repositório na sua conta do GitHub**. Você passa a ter controle total sobre essa cópia, podendo fazer alterações sem afetar o repositório original. É a base para contribuições em projetos open source.

### Quando Usar

- Contribuir para projetos **open source** sem acesso de escrita direto
- Experimentar mudanças sem risco ao projeto original
- Criar sua própria versão personalizada de um projeto
- Em disciplinas e cursos colaborativos (como este!)

### Passo a Passo

#### 1. Fork do Repositório

Acesse o repositório original no GitHub e clique no botão **"Fork"** no canto superior direito. Escolha sua conta como destino. O GitHub criará uma cópia em `https://github.com/SEU-USUARIO/repositorio`.

#### 2. Clone do Fork

```bash
git clone https://github.com/SEU-USUARIO/gh0.git
cd gh0
```

#### 3. Configurar Upstream

```bash
git remote add upstream https://github.com/iaglourenco/gh0.git
# Verifique:
git remote -v
```

#### 4. Criar Branch

```bash
git switch -c seu-nome/descricao-da-tarefa
# Exemplo:
git switch -c davidamascen07/docs-github-pages
```

#### 5. Fazer Mudanças e Commit

```bash
git add docs/07-workflows-github.md
git commit -m "docs: adiciona seção sobre GitHub Pages"
```

#### 6. Push para Fork

```bash
git push origin seu-nome/descricao-da-tarefa
```

#### 7. Abrir Pull Request

Após o push, o GitHub exibirá um banner **"Compare & pull request"**. Clique nele, preencha título e descrição (use `Closes #NUMERO` para linkar a issue) e clique em **"Create pull request"**.

#### 8. Manter Fork Atualizado

```bash
git fetch upstream
git switch main
git merge upstream/main
git push origin main
```

### Vantagens

- **Segurança**: o repositório original nunca é afetado
- **Experimentação livre**: teste ideias sem medo
- **Contribuições externas**: qualquer pessoa pode contribuir
- **Rastreabilidade**: todo trabalho fica registrado via PRs

## GitHub Flow

### O que é

GitHub Flow é um workflow **simples e ágil** criado pelo GitHub, ideal para projetos com deploy contínuo. Baseia-se em uma única branch principal (`main`) sempre estável e branches curtas para cada funcionalidade.

### Princípios

1. `main` está **sempre deployável** — nunca quebre a branch principal
2. Crie **branches com nomes descritivos** para cada tarefa
3. Abra **Pull Requests** cedo para discussão e feedback
4. Faça **deploy imediatamente** após o merge na main

### Fluxo Completo

```
main → branch → commits → PR → review → merge → deploy
```

### Quando Usar

Ideal para projetos web com **deploy contínuo** (ex: SaaS, aplicações web), equipes pequenas e projetos onde uma única versão em produção é suficiente.

## Git Flow

### O que é

Git Flow é um workflow **mais estruturado**, criado por Vincent Driessen, indicado para projetos com ciclos de release definidos. Utiliza múltiplas branches com papéis específicos.

### Branches Principais

#### main (ou master)

Contém o **código em produção**. Apenas código testado e aprovado chega aqui, geralmente via merge de `release` ou `hotfix`.

#### develop

Branch de **desenvolvimento ativo**. Todas as features são integradas aqui antes de ir para produção.

### Branches de Suporte

#### feature/*

Branches para **novas funcionalidades**. Partem de `develop` e são mescladas de volta em `develop` ao concluir. Ex: `feature/login-social`

#### release/*

Branches de **preparação de release**. Partem de `develop`, recebem apenas correções de bugs e são mescladas em `main` e `develop`. Ex: `release/v1.2.0`

#### hotfix/*

Branches para **correções urgentes em produção**. Partem de `main` e são mescladas em `main` e `develop`. Ex: `hotfix/corrige-login`

### Fluxo Visual

```
main     ─────────────────────────────────────► produção
           ↑ hotfix          ↑ release
develop  ──────────────────────────────────────
              ↑ feature   ↑ feature
```

### Quando Usar

Ideal para projetos com **releases planejadas** e versionamento semântico (v1.0, v2.1...), como bibliotecas, apps mobile e software corporativo.

### Ferramentas

A extensão `git-flow` automatiza o fluxo:
```bash
# Instalar (Linux/Mac)
brew install git-flow

# Iniciar git flow no projeto
git flow init

# Criar feature
git flow feature start minha-feature

# Finalizar feature
git flow feature finish minha-feature
```

## Trunk-Based Development

### O que é

Trunk-Based Development é um workflow onde **todos os desenvolvedores commitam frequentemente na branch principal** (`main`/`trunk`). Branches são curtíssimas (horas, não dias).

### Características

- **Integração contínua real**: código integrado várias vezes ao dia
- **Feature flags**: funcionalidades novas ficam ocultas até estarem prontas
- **Testes automatizados**: essenciais para garantir qualidade
- **Branches efêmeras**: vivem menos de 1 dia

### Quando Usar

Indicado para **equipes maduras** com cultura forte de testes, CI/CD bem estruturado e desenvolvedores experientes. Muito usado em grandes empresas como Google e Facebook.

## Issues

### O que São Issues

Issues são o **sistema de rastreamento de tarefas** do GitHub. Funcionam como um quadro de discussão para reportar bugs, sugerir funcionalidades, fazer perguntas e organizar o trabalho do projeto.

### Tipos de Issues

- **Bug**: algo não está funcionando corretamente
- **Feature**: solicitação de nova funcionalidade
- **Question**: dúvida ou pedido de esclarecimento
- **Documentation**: melhoria ou correção na documentação
- **Task**: tarefa de trabalho a ser realizada

### Criando Issues

Clique em **"New issue"** e preencha:
- **Título**: claro e objetivo (ex: `[BUG] Login falha com email inválido`)
- **Descrição**: contexto, passos para reproduzir, comportamento esperado
- **Labels**: categorize a issue
- **Assignees**: atribua responsáveis
- **Milestone**: vincule a um objetivo/sprint

### Templates de Issues

Crie templates em `.github/ISSUE_TEMPLATE/` para padronizar a abertura de issues. O GitHub oferece templates prontos para bug reports e feature requests, ou você pode criar os seus.

### Labels

Labels são **etiquetas coloridas** que categorizam e filtram issues e PRs. Facilite muito a organização e a busca de itens por tipo, prioridade ou status.

#### Labels Comuns

- `bug` - Algo não está funcionando
- `enhancement` - Nova funcionalidade ou melhoria
- `documentation` - Melhorias na documentação
- `good first issue` - Bom para iniciantes no projeto
- `help wanted` - Precisa de ajuda da comunidade
- `wontfix` - Não será corrigido/implementado

### Milestones

Milestones **agrupam issues por objetivo ou release**. Permitem acompanhar o progresso de uma versão ou sprint, mostrando quantas issues estão abertas/fechadas para aquele marco.

### Assignees

Assignees são os **responsáveis por uma issue ou PR**. Um item pode ter múltiplos assignees. Aparece no perfil da pessoa e facilita saber quem está trabalhando no quê.

### Linking Issues e PRs

Use palavras-chave na descrição do PR para **fechar issues automaticamente** após o merge:

```
Closes #58
Fixes #58
Resolves #58
```

Após o merge do PR, a issue #58 será fechada automaticamente.

## Projects

### GitHub Projects

GitHub Projects é uma ferramenta de **gestão de projeto estilo Kanban** integrada ao GitHub. Permite organizar issues e PRs em quadros visuais com colunas customizáveis.

### Criando um Project

1. Acesse a aba **"Projects"** no repositório ou perfil
2. Clique em **"New project"**
3. Escolha um template (Board, Table, Roadmap)
4. Adicione issues e PRs ao projeto

### Colunas

Colunas padrão de um projeto Kanban:
- **To Do**: tarefas planejadas mas não iniciadas
- **In Progress**: trabalho em andamento
- **In Review**: aguardando revisão
- **Done**: concluído

### Automatização

O GitHub Projects suporta **automações baseadas em eventos**: quando um PR é aberto, move para "In Progress"; quando é mergeado, move para "Done". Configure em Settings do projeto.

### Views

- **Board**: visualização Kanban com cartões em colunas
- **Table**: visualização em planilha com campos customizáveis
- **Roadmap**: linha do tempo para planejamento de longo prazo

## GitHub Actions

### O que São Actions

GitHub Actions é a plataforma de **CI/CD e automação** do GitHub. Permite criar workflows que rodam automaticamente em resposta a eventos no repositório (push, PR, issue, etc.).

### Casos de Uso

- **Testes automatizados**: rodar testes a cada push
- **Build**: compilar o projeto automaticamente
- **Deploy**: publicar em produção após merge na main
- **Linting**: verificar qualidade do código
- **Notificações**: avisar no Slack/Discord
- **Geração de releases**: criar tags e changelogs

### Workflow File

```yaml
# .github/workflows/exemplo.yml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Executar testes
        run: echo "Rodando testes..."
```

### Eventos (Triggers)

```yaml
on:
  push:              # a cada push
  pull_request:      # quando PR é aberto/atualizado
  schedule:          # agendado (cron)
    - cron: '0 8 * * 1'  # toda segunda às 8h
  workflow_dispatch: # execução manual
  release:           # quando release é publicada
```

### Jobs e Steps

- **Workflow**: o arquivo YAML inteiro (`.github/workflows/*.yml`)
- **Job**: conjunto de steps que rodam em uma mesma máquina virtual
- **Step**: comando individual (run) ou action reutilizável (uses)
- **Runner**: a máquina virtual que executa o job (`ubuntu-latest`, `windows-latest`, `macos-latest`)

### Exemplo: CI Básico

```yaml
name: Testes

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Instalar dependências
        run: npm install

      - name: Rodar testes
        run: npm test

      - name: Verificar linting
        run: npm run lint
```

### Marketplace

O [GitHub Marketplace](https://github.com/marketplace?type=actions) oferece **milhares de Actions pré-prontas** criadas pela comunidade. Exemplos populares:
- `actions/checkout` — faz o checkout do repositório
- `actions/setup-node` — configura Node.js
- `actions/upload-artifact` — salva arquivos do build
- `peaceiris/actions-gh-pages` — deploy para GitHub Pages

## GitHub Pages

### O que é

GitHub Pages é um serviço gratuito do GitHub que permite **hospedar sites estáticos diretamente de um repositório**. É amplamente usado para documentação técnica, portfólios pessoais e landing pages de projetos open source.

### Casos de Uso

- **Documentação de projetos**: transformar arquivos Markdown em site navegable
- **Portfólio pessoal**: exibir seus projetos e habilidades
- **Landing pages**: página de apresentação de um software
- **Blogs**: usando Jekyll ou outros geradores estáticos
- **Slides**: apresentações no formato web

### Habilitando Pages

1. Acesse o repositório no GitHub
2. Clique em **Settings** (engrenagem, menu superior)
3. No menu lateral, clique em **Pages**
4. Em **"Source"**, selecione a branch desejada (ex: `main`)
5. Escolha a pasta (`/ (root)` ou `/docs`)
6. Clique em **Save**
7. Aguarde alguns minutos — o GitHub exibirá a URL do seu site: `https://seu-usuario.github.io/repositorio`

### Fontes

- **`main` branch** — publica a partir da branch principal (pasta raiz ou `/docs`)
- **`docs/` folder** — publica apenas o conteúdo da pasta `/docs` da branch `main`
- **`gh-pages` branch** — branch dedicada exclusivamente ao conteúdo do site

### Jekyll

O GitHub Pages usa **Jekyll** como gerador de sites estáticos por padrão. Ele converte automaticamente arquivos Markdown (`.md`) em HTML.

Para personalizar o tema, crie um arquivo `_config.yml` na raiz do repositório:

```yaml
# _config.yml
title: Documentação Git & GitHub
description: Projeto colaborativo de documentação
theme: minima
```

**Temas disponíveis** (suportados nativamente):
- `minima` — simples e limpo
- `cayman` — ideal para projetos
- `slate` — tema escuro elegante
- `minimal` — mínimo e rápido

O build do Jekyll ocorre **automaticamente** a cada push. Não é necessário instalar nada localmente.

### Custom Domain

Você pode usar seu **próprio domínio** (ex: `docs.meusite.com`) com GitHub Pages:

1. Em **Settings > Pages**, insira seu domínio no campo **"Custom domain"**
2. No seu provedor de DNS, crie um registro CNAME apontando para `seu-usuario.github.io`
3. O GitHub provisiona automaticamente um **certificado HTTPS gratuito** via Let's Encrypt
4. Marque **"Enforce HTTPS"** para garantir conexões seguras

> O certificado HTTPS é gerado automaticamente — não há custo adicional.

## GitHub Discussions

### O que São

GitHub Discussions é um **fórum de comunidade** integrado ao repositório. É o espaço para conversas abertas, dúvidas, ideias e anlúncios — sem a formalidade de uma issue.

### Quando Usar

- **Q&A**: responder dúvidas da comunidade
- **Ideias**: sugestões que ainda não são issues concretas
- **Anlúncios**: comunicados sobre novas versões ou mudanças
- **Mostrar e contar**: compartilhar projetos feitos com a ferramenta

### Diferença de Issues

| Issues | Discussions |
|--------|-------------|
| Tarefas e bugs concretos | Conversas e ideias abertas |
| Tem status aberto/fechado | Pode ser marcada como respondida |
| Linkada a PRs e commits | Formato de fórum com respostas |
| Fluxo de trabalho | Comunidade e suporte |

## GitHub Wiki

### O que É

GitHub Wiki é um espaço de **documentação colaborativa** vinculado ao repositório. Funciona como um wiki tradicional, com páginas interligadas em Markdown.

### Quando Usar

- Documentação **extensa** que não cabe no README
- **Knowledge base** sobre como usar ou contribuir
- Guias internos de equipe
- FAQ do projeto

## GitHub Gists

### O que São

Gists são uma forma simples de **compartilhar trechos de código (snippets)** sem precisar criar um repositório completo. Cada gist é um mini-repositório Git.

### Tipos

- **Públicos**: visíveis para todos, indexáveis por buscadores
- **Secretos**: acessíveis apenas por quem tem o link (não são privados!)

## Code Owners

### Arquivo CODEOWNERS

O arquivo `CODEOWNERS` define **revisores automáticos por arquivo ou pasta**. Quando um PR toca esses arquivos, os usuários listados são solicitados automaticamente para revisar.

```
# CODEOWNERS
# Toda a pasta /docs/ deve ser revisada pelo time de documentacao
/docs/ @documentacao-team

# Arquivos JavaScript revisados por @javascript-team
*.js @javascript-team

# Usuário específico para arquivos de configuração
*.yml @devops-lead
```

## Branch Protection

### O que É

Branch protection é um conjunto de **regras para proteger branches críticas** (como `main`), impedindo pushes diretos, exigindo revisões e garantindo qualidade.

### Regras Comuns

- **Require pull request**: proibir push direto na branch
- **Require reviews**: exigir N aprovações antes do merge
- **Require status checks**: testes devem passar antes do merge
- **Require conversation resolution**: todos os comentários resolvidos
- **Restrict push**: apenas certos usuários/times podem fazer push

### Configurando

1. Acesse **Settings > Branches**
2. Clique em **"Add branch ruleset"** (ou "Add rule" em repositórios clássicos)
3. Digite o nome da branch (ex: `main`)
4. Marque as regras desejadas
5. Clique em **Save changes**

## Security

### Dependabot

Dependabot é um bot que **monitora dependências do projeto** e abre PRs automaticamente quando encontra versões com vulnerabilidades de segurança ou atualizadas. Configure em **Settings > Security > Dependabot**.

### Security Advisories

Permitem **reportar vulnerabilidades de segurança** de forma privada antes da divulgação pública (responsible disclosure). Acesse em **Security > Advisories**.

### Secret Scanning

Recurso que **escaneia commits em busca de segredos expostos** (tokens, senhas, chaves de API). Se detectar, envia alerta imediato. Ativo automaticamente em repositórios públicos.

## Notifications

### Configurar Notificações

Acesse **Settings > Notifications** para configurar como receber alertas:
- **Email**: notificações por e-mail
- **Web**: sino de notificações no GitHub
- **Mobile**: app GitHub para iOS/Android

### Watching

Nos repositórios, você pode definir o nível de acompanhamento:
- **Not watching**: apenas quando mencionado
- **Participating and @mentions**: issues/PRs que você participa
- **Watching**: todas as atividades do repositório
- **All activity**: absolutamente tudo

### Unsubscribe

Em qualquer issue ou PR, role até o final e clique em **"Unsubscribe"** para parar de receber notificações daquele item específico.

## GitHub CLI

### Instalação

```bash
# Windows (winget)
winget install GitHub.cli

# Mac (Homebrew)
brew install gh

# Linux (Ubuntu/Debian)
sudo apt install gh

# Autenticar
gh auth login
```

### Comandos Úteis

```bash
# Clonar repositório
gh repo clone usuario/repositorio

# Criar PR
gh pr create --title "docs: minha contribuição" --body "Closes #58"

# Listar issues abertas
gh issue list

# Ver status do PR
gh pr status

# Disparar workflow manualmente
gh workflow run nome-do-workflow.yml

# Fazer fork
gh repo fork usuario/repositorio --clone
```

## Integrations & Apps

### GitHub Apps

Aplicativos que se integram ao GitHub para adicionar funcionalidades. Instale em **Settings > Integrations > GitHub Apps**.

### Popular Apps

- **Slack** — notificações de PRs e issues no canal
- **Discord** — alertas da equipe
- **Codecov** — cobertura de testes
- **SonarCloud** — qualidade e segurança do código
- **Renovate** — atualização automática de dependências

## Exemplos Práticos

### Exemplo 1: Contribuir para Open Source

```bash
# 1. Fork pelo GitHub (botão Fork)
# 2. Clone seu fork
git clone https://github.com/SEU-USUARIO/projeto.git
cd projeto

# 3. Configure upstream
git remote add upstream https://github.com/ORIGINAL/projeto.git

# 4. Crie branch
git switch -c fix/corrige-bug-login

# 5. Faça alterações, commit e push
git add .
git commit -m "fix: corrige validação de login"
git push origin fix/corrige-bug-login

# 6. Abra PR no GitHub
```

### Exemplo 2: Criar Documentação com Pages

```bash
# 1. Certifique-se que existe um README.md na raiz
# 2. Acesse Settings > Pages
# 3. Source: branch 'main', pasta '/ (root)'
# 4. Save
# Site disponível em: https://seu-usuario.github.io/repositorio

# Para personalizar com Jekyll:
cat > _config.yml << 'EOF'
title: Minha Documentação
description: Projeto incrivel
theme: cayman
EOF

git add _config.yml
git commit -m "docs: configura tema Jekyll"
git push
```

### Exemplo 3: Automatizar Testes com Actions

```yaml
# .github/workflows/ci.yml
name: CI

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm ci
      - run: npm test
```

## Workflows de Equipe

### Async vs Sync

Com Git e GitHub, equipes podem trabalhar de forma **totalmente assíncrona**: cada pessoa contribui no seu tempo, PRs ficam abertos para revisão, e o histórico de commits documenta as decisões. Isso elimina a necessidade de estar online ao mesmo tempo.

### Code Review Culture

- Revise o código, não a pessoa
- Explique o motivo dos comentários
- Use perguntas ao invés de ordens ("O que acha de...?")
- Aprove quando estiver bom o suficiente, não perfeito
- Agradecer boas contribuições também é parte da cultura

### Release Management

Use **tags e releases** para marcar versões estáveis:
```bash
# Criar tag
git tag -a v1.0.0 -m "Versão 1.0.0"
git push origin v1.0.0
```
No GitHub, crie uma Release a partir da tag para anexar changelogs e binários.

## Erros Comuns

### Erro 1: Não Atualizar Fork

Se você não sincronizar seu fork com o repositório original, seu código fica desatualizado e os PRs geram conflitos. Sempre execute antes de começar:
```bash
git fetch upstream
git merge upstream/main
```

### Erro 2: Ignorar Issues

Trabalhar sem vincular issues é um erro comum. Issues documentam **o porquê** de cada mudança. Sempre crie ou comente em uma issue antes de começar e use `Closes #N` no PR.

### Erro 3: Não Configurar Branch Protection

Deixar a branch `main` desprotegida permite pushes diretos acidentais que podem quebrar o projeto. Configure regras de proteção logo no início do projeto.

## Boas Práticas

- **Documente o workflow** da equipe no CONTRIBUTING.md
- **Use templates** de issues e PRs para padronizar contribuições
- **Automatize o que puder** com GitHub Actions (testes, lint, deploy)
- **Comunique mudanças** de processo via Discussions ou README
- **Faça revisões regulares** do estado das issues e do backlog
- **Mantenha o fork atualizado** antes de começar qualquer tarefa
- **Nomeie branches de forma descritiva**: `usuario/acao-contexto`
- **Escreva commits atômicos**: uma mudança lógica por commit

## Exercícios

1. **Fork e contribua**: faça fork deste repositório, adicione conteúdo e abra um PR
2. **Crie um GitHub Project**: organize as issues abertas em um quadro Kanban
3. **Configure GitHub Pages**: publique este repositório como site estático
4. **Crie um workflow de CI**: arquivo `.github/workflows/ci.yml` que roda um comando simples a cada push

## Recursos Adicionais

<!-- TODO: Links sobre workflows -->

- [GitHub Flow Guide](https://guides.github.com/introduction/flow/)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Pages](https://pages.github.com/)
- <!-- Mais recursos -->

## Resumo

Neste módulo você aprendeu os principais workflows e recursos do GitHub:

| Recurso | Para que serve |
|---------|---------------|
| **Fork Workflow** | Contribuir em projetos sem acesso direto |
| **GitHub Flow** | Workflow simples para deploy contínuo |
| **Git Flow** | Workflow estruturado para releases |
| **Issues** | Rastrear tarefas, bugs e melhorias |
| **Projects** | Gestão visual no estilo Kanban |
| **Actions** | Automação de CI/CD e tarefas |
| **Pages** | Hospedar sites estáticos gratuitamente |
| **Branch Protection** | Garantir qualidade na branch principal |

Combinando esses recursos, você terá um fluxo de trabalho profissional e colaborativo.

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
- [@Davidamascen07](https://github.com/Davidamascen07) - Seção GitHub Pages e conteúdo completo do arquivo

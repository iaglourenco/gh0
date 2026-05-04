# Workflows no GitHub

<!-- Este arquivo explica diferentes workflows e recursos do GitHub -->

## 📋 Objetivos de Aprendizagem

<!-- TODO: Objetivos sobre workflows colaborativos -->

## 🎯 Introdução

<!-- TODO: GitHub além de hospedagem de código -->
<!-- Plataforma completa de colaboração e automação -->

## O que é um Workflow?

<!-- TODO: Definição de workflow de desenvolvimento -->
<!-- Conjunto de práticas e processos para colaborar -->

## Fork Workflow

### O que é Fork?

<!-- TODO: Cópia do repositório na sua conta -->

### Quando Usar

<!-- TODO: Projetos open source, contribuições externas -->

### Passo a Passo

#### 1. Fork do Repositório

<!-- TODO: Botão Fork no GitHub -->

#### 2. Clone do Fork

```bash
# TODO: git clone SEU-FORK
```

#### 3. Configurar Upstream

```bash
# TODO: git remote add upstream REPO-ORIGINAL
```

#### 4. Criar Branch

```bash
# TODO: git checkout -b feature/minha-contribuicao
```

#### 5. Fazer Mudanças e Commit

```bash
# TODO: git add e git commit
```

#### 6. Push para Fork

```bash
# TODO: git push origin feature/minha-contribuicao
```

#### 7. Abrir Pull Request

<!-- TODO: PR do fork para repositório original -->

#### 8. Manter Fork Atualizado

```bash
# TODO: git fetch upstream
# git merge upstream/main
```

### Vantagens

<!-- TODO: Segurança, experimentação, contribuições externas -->

## GitHub Flow

### O que é

Workflow de desenvolvimento simples e ágil chamado GitHub Flow, onde todas as mudanças partem da branch main e retornam para ela via Pull Request.

### Princípios

1. Main está sempre pronta para deploy (deployable)
2. Uso de branches curtas e descritivas
3. Pull Requests são usados para discussão e revisão de código
4. Mudanças só entram na main após review e aprovação

### Fluxo Completo

```
main → branch → commits → PR → review → merge → deploy
```

### Quando Usar

Projetos que utilizam deploy contínuo (Continuous Deployment) e precisam de agilidade no desenvolvimento, especialmente em equipes pequenas ou médias.

### GitHub Flow vs Git Flow

- GitHub Flow é mais simples e direto
- Não possui branches de release ou develop
- Ideal para deploy contínuo
- Git Flow é mais estruturado e indicado para projetos com versões planejadas

## Git Flow

### O que é

<!-- TODO: Workflow mais estruturado -->

### Branches Principais

#### main (ou master)

<!-- TODO: Código em produção -->

#### develop

<!-- TODO: Desenvolvimento atual -->

### Branches de Suporte

#### feature/*

<!-- TODO: Novas funcionalidades -->

#### release/*

<!-- TODO: Preparação de release -->

#### hotfix/*

<!-- TODO: Correções urgentes em produção -->

### Fluxo Visual

<!-- TODO: Diagrama do Git Flow -->

### Quando Usar

<!-- TODO: Projetos com releases planejadas -->

### Ferramentas

<!-- TODO: git-flow extension -->

## Trunk-Based Development

### O que é

<!-- TODO: Todos commitam em uma branch principal -->

### Características

<!-- TODO: Integração contínua, feature flags -->

### Quando Usar

<!-- TODO: Equipes maduras, CI/CD forte -->

## Issues

### O que São Issues

<!-- TODO: Sistema de rastreamento de tarefas -->

### Tipos de Issues

<!-- TODO: Bugs, features, questions, documentation -->

### Criando Issues

<!-- TODO: Título, descrição, labels, assignees -->

### Templates de Issues

<!-- TODO: .github/ISSUE_TEMPLATE/ -->

### Labels

<!-- TODO: Organização com labels -->

#### Labels Comuns

- `bug` - <!-- Algo não está funcionando -->
- `enhancement` - <!-- Nova funcionalidade -->
- `documentation` - <!-- Melhorias na documentação -->
- `good first issue` - <!-- Bom para iniciantes -->
- `help wanted` - <!-- Precisa de ajuda -->

### Milestones

<!-- TODO: Agrupar issues por objetivo/release -->

### Assignees

<!-- TODO: Atribuir responsáveis -->

### Linking Issues e PRs

<!-- TODO: Closes, Fixes, Resolves -->

## Projects

### GitHub Projects

<!-- TODO: Gestão de projeto estilo Kanban -->

### Criando um Project

<!-- TODO: Passo a passo -->

### Colunas

<!-- TODO: To Do, In Progress, Done -->

### Automatização

<!-- TODO: Auto-move baseado em eventos -->

### Views

<!-- TODO: Board, Table, Roadmap -->

## GitHub Actions

### O que São Actions

GitHub Actions é um recurso do GitHub usado para automatizar tarefas dentro de um repositório. Com ele, é possível executar testes, validar código, gerar documentação, publicar aplicações e criar fluxos de CI/CD diretamente a partir de eventos do próprio GitHub.

Na prática, uma Action ajuda a responder perguntas como:

- O código continua funcionando depois de um novo commit?
- Um Pull Request pode ser revisado com segurança?
- Os testes passam antes de permitir o merge?
- Uma aplicação pode ser publicada automaticamente?

Um workflow do GitHub Actions é definido por um arquivo YAML dentro da pasta `.github/workflows/`.

### Casos de Uso

GitHub Actions pode ser usado em diferentes situações, por exemplo:

- Rodar testes automaticamente quando alguém faz `push`
- Validar Pull Requests antes do merge
- Executar tarefas agendadas com `schedule`
- Publicar documentação ou sites estáticos
- Fazer deploy de uma aplicação
- Verificar formatação, lint ou qualidade do código

Esse tipo de automação ajuda equipes a manterem qualidade, consistência e segurança no desenvolvimento.

### Arquivo de Workflow

Um workflow é criado dentro do diretório:

```text
.github/workflows/
```

O arquivo normalmente usa a extensão `.yml` ou `.yaml`.

Exemplo:

```text
.github/workflows/ci.yml
```

Um exemplo básico de estrutura seria:

```yaml
name: CI básico

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  teste:
    runs-on: ubuntu-latest

    steps:
      - name: Baixar o código do repositório
        uses: actions/checkout@v4

      - name: Executar comando de teste
        run: echo "Testes executados com sucesso"
```

Nesse exemplo:

- `name` define o nome do workflow
- `on` indica quais eventos iniciam a automação
- `jobs` agrupa as tarefas executadas
- `runs-on` define o ambiente de execução
- `steps` lista os passos executados dentro do job
- `uses` chama uma Action pronta
- `run` executa um comando no terminal

### Eventos

Eventos são situações que disparam um workflow. Os mais comuns são `push`, `pull_request` e `schedule`.

#### push

Executa o workflow quando alguém envia commits para uma branch.

```yaml
on:
  push:
    branches: [main]
```

#### pull_request

Executa o workflow quando um Pull Request é aberto, atualizado ou reaberto.

```yaml
on:
  pull_request:
    branches: [main]
```

#### schedule

Executa o workflow em horários programados usando sintaxe cron.

```yaml
on:
  schedule:
    - cron: "0 9 * * 1"
```

Esse exemplo executa o workflow toda segunda-feira às 09:00 UTC.

### Jobs e Steps

Um workflow pode ter um ou mais jobs. Um job é um conjunto de etapas executadas em um mesmo ambiente. Cada job pode rodar em uma máquina virtual, como `ubuntu-latest`, `windows-latest` ou `macos-latest`.

Os steps são executados em ordem dentro de cada job. Eles podem executar comandos com `run` ou usar Actions prontas com `uses`.

### Matrix Builds

Matrix builds permitem executar o mesmo job em diferentes versões ou ambientes.

```yaml
name: Testes com matriz

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  testes:
    runs-on: ubuntu-latest

    strategy:
      matrix:
        python-version: ["3.8", "3.9", "3.10"]

    steps:
      - name: Baixar código
        uses: actions/checkout@v4

      - name: Configurar Python
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}

      - name: Verificar versão do Python
        run: python --version
```

Nesse caso, o mesmo job será executado três vezes: uma com Python 3.8, outra com Python 3.9 e outra com Python 3.10.

### Actions mais usadas

Algumas Actions prontas são muito comuns:

- `actions/checkout`: baixa o código do repositório para o ambiente do workflow
- `actions/setup-node`: configura uma versão do Node.js
- `actions/setup-python`: configura uma versão do Python
- `actions/upload-artifact`: salva arquivos gerados durante o workflow
- `actions/download-artifact`: baixa arquivos gerados por outro job

### Exemplo: CI Básico

CI significa Integração Contínua. A ideia é testar automaticamente cada mudança antes que ela seja incorporada ao projeto principal.

```yaml
name: CI Node.js

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Baixar código
        uses: actions/checkout@v4

      - name: Configurar Node.js
        uses: actions/setup-node@v4
        with:
          node-version: "20"

      - name: Instalar dependências
        run: npm install

      - name: Rodar testes
        run: npm test
```

Esse workflow executa testes quando há `push` na branch `main` ou quando alguém abre um Pull Request para `main`.

### CI/CD Básico

CI/CD combina duas ideias:

- CI: integração contínua, usada para testar e validar mudanças automaticamente
- CD: entrega ou implantação contínua, usada para publicar aplicações de forma automatizada

Um fluxo básico pode ser:

```text
commit → push → workflow → testes → aprovação → merge → deploy
```

Esse processo reduz erros manuais e aumenta a confiança na entrega de software.

### Ligação com Branch Protection

GitHub Actions também pode ser usado junto com regras de proteção de branch.

Por exemplo, uma equipe pode configurar a branch `main` para aceitar merge apenas quando:

- O Pull Request for aprovado
- Os testes do workflow passarem
- A branch estiver atualizada
- Não houver conflitos

Assim, o workflow de CI funciona como uma barreira de qualidade antes do código entrar na branch principal.

### Marketplace

O GitHub Marketplace reúne Actions criadas pela comunidade e por empresas. Ele permite encontrar automações prontas para testes, deploy, análise de segurança, publicação de pacotes e integração com ferramentas externas.

Antes de usar uma Action de terceiros, é importante verificar se o projeto é confiável, bem mantido e possui documentação clara.

## GitHub Pages

### O que é

<!-- TODO: Hospedagem estática gratuita -->

### Casos de Uso

<!-- TODO: Documentação, portfolio, landing pages -->

### Habilitando Pages

<!-- TODO: Settings → Pages -->

### Fontes

- <!-- main branch -->
- <!-- docs/ folder -->
- <!-- gh-pages branch -->

### Jekyll

<!-- TODO: Gerador de sites estáticos integrado -->

### Custom Domain

<!-- TODO: Usar domínio próprio -->

## GitHub Discussions

### O que São

<!-- TODO: Fórum de comunidade -->

### Quando Usar

<!-- TODO: Q&A, ideias, anúncios -->

### Diferença de Issues

<!-- TODO: Discussions = conversas, Issues = tarefas -->

## GitHub Wiki

### O que É

<!-- TODO: Documentação colaborativa -->

### Quando Usar

<!-- TODO: Docs extensas, knowledge base -->

## GitHub Gists

### O que São

<!-- TODO: Compartilhar snippets de código -->

### Tipos

<!-- TODO: Públicos vs secretos -->

## Code Owners

### Arquivo CODEOWNERS

<!-- TODO: Definir revisores por arquivo/pasta -->

```
# TODO: Exemplo de CODEOWNERS
# /docs/ @documentacao-team
# *.js @javascript-team
```

## Branch Protection

### O que É

<!-- TODO: Regras para proteger branches -->

### Regras Comuns

- <!-- Require PR -->
- <!-- Require reviews -->
- <!-- Require status checks -->
- <!-- Require conversation resolution -->
- <!-- Restrict push -->

### Configurando

<!-- TODO: Settings → Branches → Add rule -->

## Security

### Dependabot

<!-- TODO: Alertas de segurança em dependências -->

### Security Advisories

<!-- TODO: Reportar vulnerabilidades -->

### Secret Scanning

<!-- TODO: Detectar secrets commitados -->

## Notifications

### Configurar Notificações

<!-- TODO: Email, web, mobile -->

### Watching

<!-- TODO: Níveis de watching em repos -->

### Unsubscribe

<!-- TODO: Como parar de receber notificações -->

## GitHub CLI

### Instalação

```bash
# TODO: Como instalar gh CLI
```

### Comandos Úteis

```bash
# TODO: Exemplos de comandos gh
# gh repo clone
# gh pr create
# gh issue list
# gh workflow run
```

## Integrations & Apps

### GitHub Apps

<!-- TODO: Integrar serviços externos -->

### Popular Apps

- <!-- Slack -->
- <!-- Discord -->
- <!-- Trello -->
- <!-- Codecov -->

## Exemplos Práticos

### Exemplo 1: Contribuir para Open Source

<!-- TODO: Fork workflow completo -->

### Exemplo 2: Criar Documentação com Pages

<!-- TODO: Setup de GitHub Pages -->

### Exemplo 3: Automatizar Testes com Actions

<!-- TODO: Workflow de CI -->

## Workflows de Equipe

### Async vs Sync

<!-- TODO: Trabalho assíncrono com Git -->

### Code Review Culture

<!-- TODO: Estabelecer cultura de revisão -->

### Release Management

<!-- TODO: Como gerenciar releases -->

## Erros Comuns

### Erro 1: Não Atualizar Fork

<!-- TODO: Fork desatualizado -->

### Erro 2: Ignorar Issues

<!-- TODO: Importância de documentar trabalho -->

### Erro 3: Não Configurar Branch Protection

<!-- TODO: Main desprotegida -->

## Boas Práticas

<!-- TODO: Lista de boas práticas para workflows -->

- <!-- Documentar workflow da equipe -->
- <!-- Usar templates -->
- <!-- Automatizar o que puder -->
- <!-- Comunicar mudanças -->
- <!-- Regular reviews -->

## Exercícios

<!-- TODO: Exercícios práticos -->

1. <!-- Fork um repositório e contribuir -->
2. <!-- Criar GitHub Project para organizar issues -->
3. <!-- Configurar GitHub Pages -->
4. <!-- Criar workflow de CI simples -->

## Recursos Adicionais

<!-- TODO: Links sobre workflows -->

- [GitHub Flow Guide](https://guides.github.com/introduction/flow/)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Pages](https://pages.github.com/)
- <!-- Mais recursos -->

## Resumo

<!-- TODO: Principais workflows e recursos GitHub -->

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->
[Lucas Gabriel Carvalho dos Ramos](https://github.com/LucasGCRamos) - Explicação sobre GitHub Flow
[Carol Anely Miranda Guzman](https://github.com/Carolanely) - Introdução sobre GitHub Actions

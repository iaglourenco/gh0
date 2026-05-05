# Workflows no GitHub

<!-- Este arquivo explica diferentes workflows e recursos do GitHub -->

## 📋 Objetivos de Aprendizagem

- Entender o que são workflows de desenvolvimento e por que são necessários
- Dominar o Fork Workflow para contribuições em projetos Open Source
- Conhecer os principais modelos de branching (GitHub Flow, Git Flow, Trunk-Based)
- Utilizar recursos avançados do GitHub (Issues, Projects, Actions, Pages)
- Aplicar boas práticas de segurança e colaboração na plataforma

## 🎯 Introdução

O GitHub evoluiu de um simples serviço de hospedagem de código para uma plataforma completa de colaboração e automação de engenharia de software. Hoje, ele oferece ferramentas integradas para gerenciamento de projetos, integração contínua (CI/CD), segurança de código e publicação de documentação.

## O que é um Workflow?

Um **workflow** (fluxo de trabalho) de desenvolvimento é um conjunto padronizado de práticas, regras e processos que uma equipe adota para colaborar no mesmo código-fonte. Ele define como as branches são criadas, como o código é revisado e como as versões chegam à produção, garantindo organização e minimizando conflitos.

## Fork Workflow

### O que é Fork?

Um **Fork** é uma cópia completa de um repositório de outra pessoa para a sua própria conta no GitHub. Diferentemente de um simples clone local, o fork cria um repositório remoto sob o seu controle, permitindo que você faça alterações livremente sem afetar o projeto original.

### Quando Usar

O Fork Workflow é o padrão absoluto para:
- Contribuir para projetos **Open Source** (onde você não tem permissão de escrita).
- Fazer grandes experimentações baseadas em um projeto existente.
- Criar a sua própria versão de um software livre.

### Passo a Passo

#### 1. Fork do Repositório

Acesse a página do repositório original no GitHub e clique no botão **"Fork"** no canto superior direito. Isso criará uma cópia do repositório na sua conta (`seu-usuario/nome-do-repo`).

#### 2. Clone do Fork

Baixe a SUA cópia (o fork) para a sua máquina local:

```bash
git clone https://github.com/seu-usuario/nome-do-repo.git
cd nome-do-repo
```

#### 3. Configurar Upstream

Para manter seu fork atualizado com as mudanças que acontecem no projeto original, adicione o repositório original como um controle remoto chamado `upstream`:

```bash
git remote add upstream https://github.com/dono-original/nome-do-repo.git
```

#### 4. Criar Branch

Nunca trabalhe diretamente na branch `main`. Crie uma branch específica para a sua contribuição:

```bash
git switch -c feature/minha-contribuicao
```

#### 5. Fazer Mudanças e Commit

Faça suas alterações no código, adicione os arquivos e crie commits com mensagens claras:

```bash
git add .
git commit -m "feat: adiciona nova funcionalidade XYZ"
```

#### 6. Push para Fork

Envie a branch com as suas alterações para o SEU fork no GitHub:

```bash
git push origin feature/minha-contribuicao
```

#### 7. Abrir Pull Request

Vá até a página do repositório original no GitHub. Você verá um aviso sobre a sua nova branch com um botão **"Compare & pull request"**. Clique nele, preencha a descrição explicando o que você fez e submeta o PR para avaliação dos mantenedores.

#### 8. Manter Fork Atualizado

Antes de começar uma nova contribuição (ou se o seu PR estiver demorando), mantenha a sua branch `main` sincronizada com o projeto original:

```bash
# Baixa as novidades do repositório original
git fetch upstream

# Garante que você está na sua main
git switch main

# Atualiza a sua main local apenas se for possível avançar em fast-forward
git merge --ff-only upstream/main

# Atualiza o seu fork no GitHub
git push origin main
```

### Vantagens

- **Segurança:** Mantenedores do projeto original não precisam dar permissão de escrita para estranhos.
- **Experimentação Livre:** Você pode "quebrar" o seu fork à vontade sem medo de estragar o projeto principal.
- **Escalabilidade:** Permite que milhares de pessoas contribuam para um mesmo projeto de forma organizada.

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

<!-- TODO: CI/CD automação de workflows -->

### Casos de Uso

<!-- TODO: Testes, build, deploy, linting -->

### Workflow File

```yaml
# TODO: Exemplo básico de workflow
# .github/workflows/exemplo.yml
```

### Eventos (Triggers)

<!-- TODO: on: push, pull_request, schedule, etc. -->

### Jobs e Steps

<!-- TODO: Estrutura de um workflow -->

### Exemplo: CI Básico

```yaml
# TODO: Workflow para rodar testes
```

### Marketplace

<!-- TODO: Actions pré-prontas -->

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

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

As Issues no GitHub são usadas para organizar tarefas, reportar problemas e discutir melhorias em um projeto.

Elas funcionam como um sistema de gerenciamento de tarefas, permitindo acompanhar o progresso do trabalho e facilitar a colaboração entre os membros da equipe.

### Tipos de Issues

As issues podem representar diferentes tipos de atividades:

- **Bug**: algo não está funcionando corretamente
- **Feature**: sugestão de nova funcionalidade
- **Question**: dúvidas sobre o projeto
- **Documentation**: melhorias ou criação de documentação
- **Discussion**: ideias e debates

### Criando Issues

Para criar uma issue:

1. Acesse a aba "Issues" do repositório
2. Clique em "New Issue"
3. Adicione um título claro e objetivo
4. Descreva o problema ou sugestão com detalhes
5. Adicione labels, assignees e milestones (se necessário)
6. Clique em "Submit new issue"

Uma boa issue deve ser clara, objetiva e conter contexto suficiente para que outra pessoa consiga entender e trabalhar nela.

### Templates de Issues

Os templates de issues são modelos pré-definidos que ajudam a padronizar a criação de novas issues.

Eles ficam localizados na pasta:

.github/ISSUE_TEMPLATE/

Com templates, é possível garantir que todas as informações importantes sejam preenchidas, como descrição, passos para reproduzir um bug e comportamento esperado.

### Labels

Labels são etiquetas usadas para categorizar issues e facilitar a organização.

Exemplos de labels comuns:

- bug → problemas no sistema
- enhancement → melhorias
- documentation → mudanças na documentação
- good first issue → ideal para iniciantes
- help wanted → precisa de ajuda

Labels ajudam a priorizar e identificar rapidamente o tipo de tarefa.

#### Labels Comuns

- `bug` - <!-- Algo não está funcionando -->
- `enhancement` - <!-- Nova funcionalidade -->
- `documentation` - <!-- Melhorias na documentação -->
- `good first issue` - <!-- Bom para iniciantes -->
- `help wanted` - <!-- Precisa de ajuda -->

### Milestones

Milestones são usados para agrupar issues relacionadas a um objetivo específico, como uma versão ou sprint.

Exemplo:
- Versão 1.0
- Sprint 2

Eles ajudam a acompanhar o progresso de entregas maiores dentro do projeto.

### Assignees

Assignees definem quem é responsável por trabalhar em uma issue.

Ao atribuir uma issue a alguém, fica claro quem está responsável pela tarefa, evitando duplicidade de trabalho.

### Linking Issues e PRs


É possível vincular issues a Pull Requests utilizando palavras-chave no commit ou na descrição do PR.

Exemplos:

```bash
Fixes #54
Closes #10
Relates #20
```

Quando um Pull Request com "Fixes" ou "Closes" é mergeado, a issue correspondente é fechada automaticamente.

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

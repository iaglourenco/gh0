# Conceitos Básicos de Git e GitHub

<!-- Este arquivo introduz os conceitos fundamentais de controle de versão, Git e GitHub -->

## 📋 Objetivos de Aprendizagem

<!-- Liste aqui os objetivos de aprendizagem deste capítulo -->
<!-- Exemplo: "Ao final deste capítulo, você será capaz de..." -->

<!-- TODO: Adicione 3-5 objetivos de aprendizagem -->

## 🎯 Introdução

<!-- Escreva uma introdução geral sobre controle de versão e sua importância -->
<!-- Por que aprender Git? Onde é usado? -->
<!-- Mantenha entre 100-200 palavras -->

## O que é Controle de Versão?

<!-- TODO: Explique o que é controle de versão -->
<!-- Dicas:
- Por que precisamos de controle de versão?
- Quais problemas ele resolve?
- Exemplos do dia a dia (Google Docs histórico, Ctrl+Z, etc.)
- Diferença entre controle de versão local vs distribuído
-->

### Benefícios do Controle de Versão

<!-- TODO: Liste os principais benefícios -->
<!-- Exemplos: histórico completo, colaboração, backup, experimentação segura, etc. -->

## O que é Git?

<!-- TODO: Explique o que é Git -->
<!-- Dicas:
- Sistema de controle de versão distribuído
- Criado por Linus Torvalds em 2005
- Usado por milhões de desenvolvedores
- Software livre e open source
-->

### Características Principais do Git

<!-- TODO: Liste as características que tornam o Git especial -->
<!-- Exemplos: distribuído, rápido, integridade de dados, branching, etc. -->

### Como o Git Funciona?

<!-- TODO: Explique o modelo básico de funcionamento do Git -->
<!-- Dicas:
- Snapshots (não diferenças)
- Estados dos arquivos (working directory, staging area, repository)
- Commits como pontos na história
- Use diagramas ou exemplos visuais se possível
-->

## O que é GitHub?

O GitHub é uma **plataforma web de hospedagem de código** baseada em Git. Ela pega tudo que o Git faz localmente, ou seja, rastreia mudanças, cria histórico e gerencia branches, mas adiciona uma camada de colaboração, revisão de código e automação acessível pelo navegador. Fundado em **abril de 2008** por Tom Preston-Werner, Chris Wanstrath e PJ Hyett, o GitHub se tornou rapidamente o lar da maioria dos projetos open source do mundo. Em **junho de 2018**, a **Microsoft adquiriu o GitHub por US$ 7,5 bilhões**, mantendo-o independente e expandindo os recursos gratuitos, incluindo repositórios privados ilimitados para contas gratuitas. Hoje em dia, o GitHub é muito mais do que um lugar para guardar código, é onde equipes colaboram de forma distribuída, empresas constroem produtos e desenvolvedores mostram seu trabalho, esse modelo de desenvolvimento aberto e colaborativo ficou conhecido como **social coding**. É usado por desenvolvedores individuais como portfólio técnico, por equipes no dia a dia de desenvolvimento e por grandes projetos open source como Linux, React e Python. A plataforma está disponível em **[github.com](https://github.com)**, basta criar uma conta gratuita para começar.

> **Git ≠ GitHub.** Git é a ferramenta de controle de versão; GitHub é a plataforma que usa Git por baixo dos panos. Você pode usar Git sem o GitHub, mas não o contrário

O plano **Free** já inclui repositórios públicos e privados ilimitados e é mais do que suficiente para a maioria dos desenvolvedores. Para equipes, o plano **Team** (US$ 4/usuário/mês) adiciona revisões obrigatórias e permissões avançadas. Consulte os valores atualizados em [github.com/pricing](https://github.com/pricing).

Além do GitHub, existem alternativas que valem conhecer: o **[GitLab](https://gitlab.com)** se destaca pela opção de self-hosting e CI/CD robusto; o **[Bitbucket](https://bitbucket.org)** é popular em equipes que usam o ecossistema Atlassian (Jira, Confluence); e o **[Gitea](https://gitea.io)** é uma opção leve e open source para quem quer controle total da infraestrutura.


### Recursos do GitHub

- **Repositórios remotos** — hospeda seu código na nuvem, servindo como fonte
  de verdade compartilhada para toda a equipe
- **Pull Requests (PRs)** — mecanismo para propor, revisar e discutir alterações
  antes de incorporá-las ao código principal
- **Issues** — sistema integrado para rastrear bugs, tarefas e sugestões
- **GitHub Actions** — plataforma de CI/CD nativa que roda testes e deploys
  automaticamente a cada push ou PR
- **GitHub Pages** — hospedagem gratuita de sites estáticos direto de um repositório

## Diferença entre Git e GitHub

<!-- TODO: Explique claramente a diferença -->
<!-- Esta é uma confusão comum! Seja muito claro aqui -->

<!-- Use uma tabela comparativa, por exemplo:
| Git | GitHub |
|-----|--------|
| ... | ...    |
-->

### Analogia Útil

<!-- TODO: Crie uma analogia para ajudar a entender a diferença -->
<!-- Exemplo: Git é como um sistema de arquivos com histórico, GitHub é como o Google Drive para Git -->

## Conceitos Fundamentais

### Repositório (Repository)

<!-- TODO: O que é um repositório? -->
<!-- Tipos: local vs remoto -->

### Commit

<!-- TODO: O que é um commit? -->
<!-- Por que commits são importantes? -->
<!-- Estrutura de um commit: snapshot, mensagem, autor, timestamp -->

### Branch

<!-- TODO: Introdução básica ao conceito de branch -->
<!-- (Explicação detalhada virá no capítulo 03) -->

### Histórico

<!-- TODO: O que é o histórico do Git? -->
<!-- Como visualizar? Para que serve? -->

### Clone vs Fork

<!-- TODO: Explique a diferença entre clone e fork -->

## Instalação do Git

### Windows

<!-- TODO: Como instalar Git no Windows -->
<!-- Link para download: https://git-scm.com/download/win -->

### macOS

<!-- TODO: Como instalar Git no macOS -->
<!-- Homebrew, Xcode, download direto -->

### Linux

<!-- TODO: Como instalar Git no Linux -->
<!-- Comandos para Ubuntu/Debian, Fedora, Arch -->

### Verificando a Instalação

<!-- TODO: Como verificar se o Git foi instalado corretamente -->

```bash
# TODO: Adicione o comando para verificar versão do Git
```

## Configuração Inicial

<!-- TODO: Configure Git pela primeira vez -->

```bash
# TODO: Adicione comandos para configurar nome e email
# git config --global user.name "Seu Nome"
# git config --global user.email "seu@email.com"
```

### Por que Configurar Nome e Email?

<!-- TODO: Explique a importância dessas configurações -->

## Criando uma Conta no GitHub

<!-- TODO: Passo a passo para criar conta no GitHub -->

1. <!-- Passo 1 -->
2. <!-- Passo 2 -->
3. <!-- Passo 3 -->

## Exemplos Práticos

### Exemplo 1: Cenário sem Controle de Versão

<!-- TODO: Descreva um cenário caótico sem controle de versão -->
<!-- Exemplo: múltiplas cópias de arquivo, versões conflitantes, etc. -->

### Exemplo 2: Mesmo Cenário com Git

<!-- TODO: Mostre como Git resolve o problema do Exemplo 1 -->

## Erros Comuns

<!-- TODO: Liste erros comuns de iniciantes -->

### Erro 1: Confundir Git com GitHub

<!-- TODO: Como evitar essa confusão -->

### Erro 2: Não configurar nome e email

<!-- TODO: O que acontece e como corrigir -->

## Exercícios

<!-- TODO: Crie 3-5 exercícios práticos -->

1. <!-- Exercício 1: Instalar Git e verificar versão -->
2. <!-- Exercício 2: Configurar Git com seu nome e email -->
3. <!-- Exercício 3: Criar conta no GitHub -->

## Recursos Adicionais

<!-- TODO: Adicione links úteis para aprofundamento -->

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- <!-- Adicione mais recursos -->

## Glossário

<!-- TODO: Defina termos importantes usados neste capítulo -->

- **Commit**: <!-- Definição -->
- **Repository**: <!-- Definição -->
- **Clone**: <!-- Definição -->
- **Fork**: <!-- Definição -->

## Resumo

<!-- TODO: Faça um resumo dos pontos principais do capítulo -->
<!-- Lista de 5-8 pontos-chave que os alunos devem lembrar -->

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->

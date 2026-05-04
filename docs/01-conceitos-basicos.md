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

<!-- TODO: Explique o que é GitHub -->
<!-- Dicas:
- Plataforma de hospedagem de código
- Baseada em Git
- Ferramentas de colaboração
- Maior plataforma de código aberto do mundo
- Não é a mesma coisa que Git!
-->

### Recursos do GitHub

<!-- TODO: Liste os principais recursos do GitHub -->
<!-- Exemplos: repositórios, issues, pull requests, actions, pages, etc. -->

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

Um repositório Git é muito mais do que uma simples pasta de projeto; é um banco de dados completo que armazena todo o histórico de versões, metadados e objetos do seu trabalho.

> **Analogia:** Imagine uma pasta de projeto comum, mas que possui uma "máquina do tempo" embutida. Cada alteração salva permite que você retorne exatamente ao estado em que o projeto estava em qualquer momento do passado.

#### 1. Tipos de Repositório

*   **Repositório Local:** Reside na sua máquina pessoal. É onde você realiza o trabalho diário, cria commits e gerencia suas branches de forma offline.
*   **Repositório Remoto:** Hospedado em um servidor (como GitHub, GitLab ou Bitbucket). Ele serve como o "ponto de verdade" para a colaboração, permitindo que várias pessoas sincronizem seus repositórios locais.

#### 2. Estrutura Básica do Git

O Git organiza seu trabalho em três áreas principais:

1.  **Working Directory (Diretório de Trabalho):** É a pasta onde você visualiza e edita seus arquivos.
2.  **Staging Area (Index):** Uma área de preparação onde você marca quais arquivos alterados entrarão no próximo commit.
3.  **Repositório (Pasta .git):** Onde o Git armazena permanentemente os snapshots (fotos) do seu projeto.

#### 3. O que há dentro da pasta `.git`?

Ao iniciar um repositório, o Git cria uma pasta oculta chamada `.git`. Ela contém:

*   **Objects:** Onde o conteúdo real dos arquivos e os commits são armazenados.
*   **Refs:** Ponteiros para os commits (como branches e tags).
*   **HEAD:** Um arquivo que indica em qual branch ou commit você está trabalhando no momento.

#### 4. Sincronização: Local ↔ Remoto

A interação entre os tipos de repositório ocorre através de fluxos de sincronização:

*   **Push (Empurrar):** Envia seus commits locais para o servidor remoto.
*   **Pull (Puxar):** Traz as atualizações do servidor remoto e as mescla no seu repositório local.

**Exemplo Prático:**

```bash
# Inicia um repositório local
git init

# Conecta o repositório local a um servidor remoto
git remote add origin https://github.com/usuario/projeto.git

# Envia o conteúdo local pela primeira vez
git push -u origin main

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

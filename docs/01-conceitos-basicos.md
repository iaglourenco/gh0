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

O Git pode ser instalado em todos os principais sistemas operacionais. Abaixo você encontra o guia de instalação para Windows, macOS e Linux, incluindo o uso de gerenciadores de pacotes.

### Windows

**Opção 1: Instalador Oficial (Recomendado para iniciantes)**
1. Acesse o site oficial: [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Baixe a versão correspondente ao seu sistema (geralmente 64-bit Git for Windows Setup).
3. Execute o instalador e siga o assistente (pode deixar as opções padrão marcadas).
4. Após a instalação, você terá acesso ao Git Bash, um terminal que emula o ambiente Linux no Windows, facilitando o uso dos comandos.
**Opção 2: Usando Package Managers (Avançado)**
Se você usa gerenciadores de pacotes no Windows, pode instalar via terminal:

Via **Winget**:
```powershell
winget install --id Git.Git -e --source winget
```

Via **Chocolatey**:
```powershell
choco install git
```

### macOS

A maneira mais comum e recomendada de instalar o Git no macOS é através do gerenciador de pacotes **Homebrew**.

1. Se não tiver o Homebrew instalado, instale-o com:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
2. Instale o Git executando:
```bash
brew install git
```

*Alternativa:* Você também pode baixar o instalador oficial em [https://git-scm.com/download/mac](https://git-scm.com/download/mac).

### Linux

No Linux, a instalação é feita diretamente pelo terminal usando o gerenciador de pacotes da sua distribuição.

**Debian / Ubuntu / Linux Mint:**
```bash
sudo apt update
sudo apt install git
```

**Fedora:**
```bash
sudo dnf install git
```
*(Se estiver usando uma versão mais antiga do Fedora, pode usar `sudo yum install git`)*

**Arch Linux:**
```bash
sudo pacman -S git
```

### Verificando a Instalação

Independentemente do seu sistema operacional, após a instalação, abra o seu terminal (Prompt de Comando, PowerShell, Terminal do macOS ou Linux) e digite o seguinte comando para confirmar que o Git foi instalado com sucesso:

```bash
git --version
```

**Output de exemplo esperado:**
```text
git version 2.44.0
```
*(O número da versão pode variar dependendo de quando você instalou, mas deve mostrar "git version...")*

### Troubleshooting (Problemas Comuns)

Se você receber um erro como:
> `'git' não é reconhecido como um comando interno ou externo, um programa operável ou um arquivo em lotes.` (Windows)
> **ou**
> `bash: git: command not found` (Linux/macOS)

**Como resolver:**
1. **Reinicie o terminal:** O terminal precisa ser fechado e aberto novamente para recarregar as variáveis de ambiente.
2. **Verifique o PATH (Windows):** Se você usou o instalador manual e desmarcou a opção de adicionar o Git ao PATH, o terminal não saberá onde ele está. Reinstale o Git e certifique-se de marcar a opção *"Git from the command line and also from 3rd-party software"*.
3. **Permissões (Linux/macOS):** Se a instalação falhar por erro de permissão, lembre-se de usar `sudo` antes dos comandos de instalação com `apt`, `dnf` ou `pacman`.

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

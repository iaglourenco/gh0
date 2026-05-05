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

O GitHub é uma **plataforma web de hospedagem de código** baseada em Git. Ela pega tudo que o Git faz localmente, ou seja, rastreia mudanças, cria histórico e gerencia branches, mas adiciona uma camada de colaboração, revisão de código e automação acessível pelo navegador. 

Fundado em **abril de 2008** por Tom Preston-Werner, Chris Wanstrath e PJ Hyett, o GitHub se tornou rapidamente o lar da maioria dos projetos open source do mundo. Em **junho de 2018**, a **Microsoft adquiriu o GitHub por US$ 7,5 bilhões**, mantendo-o independente e expandindo os recursos gratuitos, incluindo repositórios privados ilimitados para contas gratuitas. 

Hoje em dia, o GitHub é muito mais do que um lugar para guardar código, é onde equipes colaboram de forma distribuída, empresas constroem produtos e desenvolvedores mostram seu trabalho, esse modelo de desenvolvimento aberto e colaborativo ficou conhecido como **social coding**. É usado por desenvolvedores individuais como portfólio técnico, por equipes no dia a dia de desenvolvimento e por grandes projetos open source como Linux, React e Python. 

A plataforma está disponível em **[github.com](https://github.com)**, basta criar uma conta gratuita para começar.

> **Git ≠ GitHub.** Git é a ferramenta de controle de versão; GitHub é a plataforma que usa Git por baixo dos panos. Você pode usar Git sem o GitHub, mas não o contrário

O plano **Free** já inclui repositórios públicos e privados ilimitados e é mais do que suficiente para a maioria dos desenvolvedores. Para equipes, o plano **Team** adiciona revisões obrigatórias e permissões avançadas. Os preços podem ser consultados com seus valores atualizados em [github.com/pricing](https://github.com/pricing).

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

Após instalar o Git, é fundamental configurar sua identidade. Essas informações serão associadas a cada *commit* que você realizar, permitindo identificar quem é o autor das alterações no projeto.

#### 1. Configuração de Identidade

Você deve configurar seu nome e e-mail. Existem dois níveis principais de configuração:
* **Global:** Aplica-se a todos os repositórios do seu usuário na máquina.
* **Local:** Aplica-se apenas ao repositório específico onde você está trabalhando.

#### Configuração Global
Para configurar em toda a sua máquina, utilize o parâmetro `--global`:

```bash
# Define seu nome de exibição
git config --global user.name "Seu Nome"

# Define seu e-mail de contato
git config --global user.email "seu.email@example.com"
```

#### Configuração Local
Se precisar usar um e-mail diferente para um projeto específico (ex: e-mail corporativo em um projeto da empresa), execute o comando dentro da pasta do projeto **sem** o `--global`:

```bash
git config user.name "Seu Nome Profissional"
git config user.email "nome.sobrenome@empresa.com"
```

#### 2. Verificação das Configurações

Para conferir se as informações foram gravadas corretamente, você pode listar as configurações atuais:

```bash
# Lista todas as configurações ativas (local + global)
git config --list

# Lista apenas as configurações globais
git config --list --global
```

#### 3. Configurações Recomendadas (Opcional)

Além da identidade, é recomendável ajustar o editor de texto padrão e o comportamento de quebra de linha.

#### Editor de Texto
Define qual editor abrirá quando o Git precisar que você escreva uma mensagem (ex: VS Code, Vim ou Notepad++):

```bash
# Exemplo para configurar o VS Code como editor padrão
git config --global core.editor "code --wait"
```

#### Tratamento de Fim de Linha (autocrlf)
Isso evita problemas de compatibilidade entre Windows (que usa CRLF) e sistemas Unix/Mac (que usam LF).

```bash
# Se você usa Windows:
git config --global core.autocrlf true

# Se você usa Mac ou Linux:
git config --global core.autocrlf input
```

#### 4. Troubleshooting (Resolução de Problemas)

* **Alterar uma configuração existente:** Basta executar o comando novamente com o novo valor. O Git sobrescreverá o anterior.
* **Remover uma configuração (Reset):** Caso queira voltar ao padrão do sistema e remover uma entrada específica:

```bash
# Remove o e-mail global
git config --global --unset user.email
```


**Observação:** Lembre-se que o Git prioriza sempre a configuração **Local** sobre a **Global**. Se você configurou um e-mail dentro da pasta do projeto, ele será usado em vez do e-mail geral da sua máquina.



### Por que Configurar Nome e Email?

A configuração de nome e e-mail não é apenas burocrática; ela é o que garante a rastreabilidade do projeto. No Git, cada alteração (commit) é "assinada".

* **Identificação de Autoria:** Em uma equipe, todos precisam saber quem fez cada modificação para tirar dúvidas ou revisar o código.
* **Histórico de Contribuições:** Sites como GitHub e GitLab usam o e-mail configurado para vincular suas alterações ao seu perfil, gerando aquele gráfico de contribuições (os quadradinhos verdes).
* **Segurança e Auditoria:** Ajuda a manter um registro claro de quando e por quem uma funcionalidade foi adicionada ou um erro foi introduzido.

> **Importante:** O Git não verifica se o e-mail é real ou se você é o dono dele, mas se você usar um e-mail diferente do que está cadastrado no seu GitHub, o commit não aparecerá vinculado ao seu perfil de usuário.


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
- [Tutorial de Configuração Git (Atlassian)](https://www.atlassian.com/br/git/tutorials/setting-up-a-repository/git-config)
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
- [Rafael Ziani de Carvalho](https://github.com/steinbukken7321) - Configuração Inicial do Git

---

---
## SSH Keys

As chaves SSH garantem uma autenticação segura e criptografada entre sua máquina local e o GitHub, eliminando a necessidade de credenciais manuais em cada operação.

### Por que utilizar SSH?
* **Segurança:** Autenticação baseada em criptografia de chave pública/privada.
* **Eficiência:** Elimina prompts de senha recorrentes.
* **Automação:** Requisito para fluxos de CI/CD e scripts automatizados.

### Gerando o Par de Chaves (Key Pair)
No terminal, execute o comando utilizando o algoritmo Ed25519 (recomendado por segurança e performance):
```bash
ssh-keygen -t ed25519 -C "saimomgozn@gmail.com"

> **Nota para sistemas legados:** Caso o ambiente não ofereça suporte ao Ed25519, utilize o RSA com 4096 bits como alternativa:
> ```bash
> ssh-keygen -t rsa -b 4096 -C "saimomgozn@gmail.com"
> ```
   
   

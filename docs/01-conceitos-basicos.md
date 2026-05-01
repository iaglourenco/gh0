# Conceitos Básicos de Git e GitHub

<!-- Este arquivo introduz os conceitos fundamentais de controle de versão, Git e GitHub -->

## 📋 Objetivos de Aprendizagem

<!-- Liste aqui os objetivos de aprendizagem deste capítulo -->
<!-- Exemplo: "Ao final deste capítulo, você será capaz de..." -->

<!-- TODO: Adicione 3-5 objetivos de aprendizagem -->
* Entender o que é controle de versão e por que ele é essencial no desenvolvimento de software
* Diferenciar claramente Git (ferramenta) de GitHub (plataforma)
* Configurar o Git no seu computador e criar uma conta no GitHub
* Compreender os conceitos fundamentais: repositório, commit, branch, histórico, clone e fork
* Aplicar os primeiros comandos Git para versionar um projeto simples


## 🎯 Introdução

<!-- Escreva uma introdução geral sobre controle de versão e sua importância -->
<!-- Por que aprender Git? Onde é usado? -->
<!-- Mantenha entre 100-200 palavras -->

O controle de versão é uma prática essencial para qualquer pessoa que trabalhe com código, documentos ou qualquer tipo de arquivo que evolua ao longo do tempo. Imagine poder voltar no tempo e recuperar uma versão anterior do seu trabalho, colaborar com outras pessoas sem sobrescrever o trabalho alheio, ou experimentar novas ideias sem medo de "quebrar" o projeto principal.
Git é a ferramenta de controle de versão distribuída mais popular do mundo, criada por Linus Torvalds em 2005. GitHub é a plataforma baseada na nuvem que hospeda repositórios Git e adiciona ferramentas poderosas de colaboração.
Aprender Git e GitHub não é mais um "diferencial" — é uma habilidade fundamental para desenvolvedores, designers, cientistas de dados e qualquer profissional que trabalhe em projetos digitais. Neste capítulo, você dará os primeiros passos nesse universo.

## O que é Controle de Versão?

<!-- TODO: Explique o que é controle de versão -->
<!-- Dicas:
- Por que precisamos de controle de versão?
- Quais problemas ele resolve?
- Exemplos do dia a dia (Google Docs histórico, Ctrl+Z, etc.)
- Diferença entre controle de versão local vs distribuído
-->

Controle de versão (ou version control) é um sistema que registra alterações em um arquivo ou conjunto de arquivos ao longo do tempo, permitindo que você recupere versões específicas posteriormente.

#### Por que precisamos de controle de versão?
* **Rastreabilidade**: Saber quem mudou o quê, quando e por quê
* **Recuperação**: Voltar a uma versão estável se algo der errado
* **Colaboração**: Múltiplas pessoas trabalhando no mesmo projeto sem conflitos
* **Experimentação**: Testar novas ideias em branches separadas sem afetar o código principal

#### Exemplos do dia a dia:


| Exemplo | Descrição | Limitação |
|---------|-----------|-----------|
| 📝 Google Docs | Histórico de versões que permite restaurar edições anteriores | Requer internet; limitado a documentos |
| 💾 Ctrl+Z | Desfazer alterações | Apenas local e temporário |
| 📁 `projeto_final_v2_AGORA_VAI.docx` | Múltiplas cópias manuais | Caótico, propenso a erros |

#### Controle de versão: Local vs. Centralizado vs. Distribuído

| Tipo | Descrição | Exemplo |
|------|-----------|---------|
| **Local** | Histórico armazenado apenas no seu computador | RCS, backups manuais |
| **Centralizado** | Um servidor central guarda o histórico; clientes baixam versões | SVN, CVS |
| **Distribuído** | Cada usuário tem uma cópia completa do histórico | **Git**, Mercurial |

### Benefícios do Controle de Versão

<!-- TODO: Liste os principais benefícios -->
<!-- Exemplos: histórico completo, colaboração, backup, experimentação segura, etc. -->


✅ **Histórico completo**: Cada alteração é registrada com autor, data e mensagem descritiva  
✅ **Colaboração eficiente**: Múltiplas pessoas podem trabalhar simultaneamente no mesmo projeto  
✅ **Backup automático**: Seu código está seguro mesmo se seu computador falhar  
✅ **Experimentação segura**: Crie branches para testar ideias sem risco para o código principal  
✅ **Revisão de código**: Facilita a análise de mudanças antes de integrá-las ao projeto  
✅ **Deploy controlado**: Marque versões específicas para lançamento em produção  

## O que é Git?

<!-- TODO: Explique o que é Git -->
<!-- Dicas:
- Sistema de controle de versão distribuído
- Criado por Linus Torvalds em 2005
- Usado por milhões de desenvolvedores
- Software livre e open source
-->

**Git** é um sistema de controle de versão distribuído (*Distributed Version Control System - DVCS*) criado por **Linus Torvalds** em 2005 para gerenciar o desenvolvimento do kernel Linux.


### Características Principais do Git

<!-- TODO: Liste as características que tornam o Git especial -->
<!-- Exemplos: distribuído, rápido, integridade de dados, branching, etc. -->

- 🆓 **Software livre e open source** (licença GPL)
- 🚀 **Extremamente rápido** e eficiente, mesmo com projetos grandes
- 🔐 **Integridade de dados**: Cada commit é identificado por um hash SHA-1 único
- 🌿 **Branching e merging poderosos**: Crie e integre ramificações com facilidade
- 📦 **Funciona offline**: A maioria das operações é local; só precisa de rede para sincronizar
- 🌍 **Usado por milhões** de desenvolvedores e empresas worldwide


### Como o Git Funciona?

<!-- TODO: Explique o modelo básico de funcionamento do Git -->
<!-- Dicas:
- Snapshots (não diferenças)
- Estados dos arquivos (working directory, staging area, repository)
- Commits como pontos na história
- Use diagramas ou exemplos visuais se possível
-->
O Git não armazena diferenças entre versões (como um *diff*), mas sim **snapshots** (instantâneos) do estado completo dos arquivos a cada commit.

#### Os três estados dos arquivos no Git:

📁 Working Directory → 📦 Staging Area → 🗄️ Repository (.git)



1. **Working Directory**: Onde você edita os arquivos
2. **Staging Area** (`git add`): Área de preparação para o próximo commit
3. **Repository** (`git commit`): Onde os snapshots são armazenados permanentemente

## O que é GitHub?

<!-- TODO: Explique o que é GitHub -->
<!-- Dicas:
- Plataforma de hospedagem de código
- Baseada em Git
- Ferramentas de colaboração
- Maior plataforma de código aberto do mundo
- Não é a mesma coisa que Git!
-->

**GitHub** é uma plataforma de hospedagem de código baseada em Git, lançada em 2008. Ela adiciona uma interface web amigável e ferramentas de colaboração ao poder bruto do Git.

### Principais características:

- 🌐 **Hospedagem de repositórios** Git na nuvem
- 👥 **Ferramentas de colaboração**: issues, pull requests, revisões de código
- 🤖 **Automação**: GitHub Actions para CI/CD
- 🌐 **GitHub Pages**: Hospede sites estáticos gratuitamente
- 🔐 **Segurança**: Autenticação em dois fatores, dependabot para atualizações
- 🌍 **Maior comunidade open source** do mundo

> ⚠️ **Importante**: GitHub **não é** Git! Git é a ferramenta de linha de comando; GitHub é um serviço que usa Git. Você pode usar Git sem GitHub, mas não pode usar GitHub sem Git.

### Recursos do GitHub

<!-- TODO: Liste os principais recursos do GitHub -->
<!-- Exemplos: repositórios, issues, pull requests, actions, pages, etc. -->


| Recurso | Descrição |
|---------|-----------|
| **Repositórios** | Armazenam seu código, histórico e configurações |
| **Issues** | Sistema de rastreamento de tarefas, bugs e melhorias |
| **Pull Requests** | Propostas de mudança com revisão colaborativa |
| **Actions** | Automação de workflows (testes, deploy, etc.) |
| **Projects** | Quadros Kanban para gerenciamento de projetos |
| **Pages** | Hospedagem gratuita para sites estáticos |
| **Gists** | Compartilhamento rápido de trechos de código |
| **Discussions** | Fórum para discussões da comunidade |
| **Copilot** | Assistente de programação baseado em IA que sugere código em tempo real |
| **Codespaces** | Ambientes de desenvolvimento completos e configuráveis na nuvem |
| **Packages** | Serviço de hospedagem e gerenciamento de pacotes (Docker, npm, Maven, etc.) |
| **Security & Dependabot** | Ferramentas que alertam sobre vulnerabilidades e atualizam dependências |
| **Wikis** | Espaço dedicado para hospedar a documentação detalhada no repositório |
| **Releases** | Sistema para empacotar, versionar e distribuir software com notas de lançamento |
| **Sponsors** | Plataforma para financiamento de desenvolvedores e projetos open source |
| **Insights / Analytics** | Painéis com métricas e estatísticas sobre tráfego e saúde do repositório |


## Diferença entre Git e GitHub

<!-- TODO: Explique claramente a diferença -->
<!-- Esta é uma confusão comum! Seja muito claro aqui -->

<!-- Use uma tabela comparativa, por exemplo:
| Git | GitHub |
|-----|--------|
| ... | ...    |
-->


Esta é uma das confusões mais comuns para iniciantes. Vamos esclarecer:

| Git | GitHub |
|-----|--------|
| Software de controle de versão (linha de comando) | Plataforma web de hospedagem de código |
| Funciona localmente no seu computador | Funciona na nuvem (servidores remotos) |
| Criado por Linus Torvalds (2005) | Criado por Chris Wanstrath, PJ Hyett e outros (2008) |
| Open source e gratuito | Gratuito para repositórios públicos; planos pagos para privados |
| Não requer internet para a maioria das operações | Requer conexão com a internet |
| Pode ser usado com qualquer host Git | Usa Git como base, mas adiciona funcionalidades próprias |


### Analogia Útil

<!-- TODO: Crie uma analogia para ajudar a entender a diferença -->
<!-- Exemplo: Git é como um sistema de arquivos com histórico, GitHub é como o Google Drive para Git -->


> 🚗 **Git é como o motor do seu carro**: ele faz o trabalho essencial de versionamento, funciona localmente e você pode usá-lo sem depender de ninguém.
>
> 🅿️ **GitHub é como um estacionamento compartilhado com oficinas**: ele oferece um lugar para guardar seu carro (repositório), permite que outras pessoas vejam, sugiram melhorias (pull requests), reportem problemas (issues) e até automatizem manutenções (Actions).
>
> Você pode dirigir seu carro (usar Git) sem estacionar no GitHub, mas o GitHub torna muito mais fácil colaborar e compartilhar.

---


## Conceitos Fundamentais


### Repositório (Repository)

Um **repositório** é como uma pasta especial que o Git monitora. Ele contém:

- Todos os arquivos do seu projeto
- O histórico completo de alterações (`.git/`)
- Configurações e metadados

**Tipos**:

- 🔹 **Local**: Armazenado no seu computador (`/meu-projeto/.git`)
- 🔹 **Remoto**: Hospedado em um servidor (GitHub, GitLab, etc.)

### Commit

Um **commit** é um "ponto de salvamento" no histórico do seu projeto. Pense nele como uma foto do estado dos arquivos em um momento específico.

**Estrutura de um commit**:

```bash
commit a1b2c3d4e5f6...
Author: Seu Nome <seu@email.com>
Date:   Seg Mai 1 10:30:00 2024 -0300

    feat: adiciona função de login
```
### 📌 Conventional Commits

| Tipo | Descrição | Exemplo |
| :--- | :--- | :--- |
| `feat` | Adiciona uma nova funcionalidade | `feat: adiciona barra de busca` |
| `fix` | Corrige um bug | `fix: resolve falha na validação do formulário` |
| `docs` | Atualiza apenas a documentação | `docs: atualiza instruções no README` |
| `style` | Mudanças de formatação que não afetam a lógica do código | `style: corrige identação no arquivo CSS` |
| `refactor` | Refatoração de código que não corrige um bug nem adiciona uma feature | `refactor: simplifica lógica de cálculo` |
| `test` | Adiciona ou corrige testes | `test: adiciona teste para cálculo de juros` |
| `chore` | Atualização de tarefas de build, ferramentas ou dependências | `chore: atualiza versão do Node.js` |

---

### 🏆 Regras de Ouro para os seus Commits

* **Use o imperativo:** A mensagem deve estar no imperativo (`adiciona`, `corrige`), em vez de `adicionei` ou `corrigindo`.
* **Commits atômicos:** Devem ser pequenos e focados em uma única mudança. Não misture uma `feat` nova com um `fix` de outra coisa no mesmo commit.
* **Explique o "porquê":** Inclua o motivo da mudança no corpo da mensagem quando a razão não for óbvia.
### Branch

<!-- TODO: Introdução básica ao conceito de branch -->
<!-- (Explicação detalhada virá no capítulo 03) -->
Um branch (ramificação) é uma linha de desenvolvimento independente. Por padrão, o Git cria um branch chamado main (ou master).

```
main:    A──B──C
                \
feature-X:        D──E  ← você trabalha aqui sem afetar main
```
> 📌 Explicação detalhada de branching e merging virá no Capítulo 03.
### Histórico

<!-- TODO: O que é o histórico do Git? -->
<!-- Como visualizar? Para que serve? -->

O histórico é a linha do tempo de todos os commits do seu repositório.

```bash
git log          # Ver histórico completo
git log --oneline # Versão resumida
git log -p       # Ver histórico com as mudanças (diffs)
```

#### Para que serve?

* Entender a evolução do projeto

* Investigar quando e por que uma mudança foi feita

* Reverter alterações indesejadas

### Clone vs Fork

| Ação | O que faz | Quando usar |
| :--- | :--- | :--- |
| **Clone** | Cria uma cópia local de um repositório remoto | Quando você quer trabalhar em um projeto no seu computador |
| **Fork** | Cria uma cópia do repositório na sua conta do GitHub | Quando você quer contribuir com um projeto de terceiros ou criar sua própria versão |

**Fluxo típico de contribuição:**
```text
1. Fork no GitHub 
   → 2. Clone no seu PC 
   → 3. Cria branch 
   → 4. Faz alterações 
   → 5. Commit & Push 
   → 6. Pull Request
   ```

<!-- TODO: Explique a diferença entre clone e fork -->

## Instalação do Git

### Windows

<!-- TODO: Como instalar Git no Windows -->
<!-- Link para download: https://git-scm.com/download/win -->
1. Acesse: [https://git-scm.com/download/win](https://git-scm.com/download/win)
2. Baixe o instalador `.exe`
3. Execute e siga o assistente (configurações padrão são recomendadas)
4. Ao final, o **Git Bash** será instalado

💡 **Dica:** marque a opção **"Use Git from the Windows Command Prompt"** para usar no PowerShell/CMD.

---
### macOS

<!-- TODO: Como instalar Git no macOS -->
<!-- Homebrew, Xcode, download direto -->
#### Opção 1: Via Homebrew (recomendado)

```bash
# Se não tiver Homebrew:
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Instale o Git:
brew install git
```

#### Opção 2: Xcode Command Line Tools

```bash
xcode-select --install
```

#### Opção 3: Download direto

[https://git-scm.com/download/mac](https://git-scm.com/download/mac)

---

### Linux

<!-- TODO: Como instalar Git no Linux -->
<!-- Comandos para Ubuntu/Debian, Fedora, Arch -->

##### Ubuntu/Debian

```bash
sudo apt update
sudo apt install git
```

##### Fedora

```bash
sudo dnf install git
```

##### Arch Linux

```bash
sudo pacman -S git
```

---

### Verificando a Instalação

<!-- TODO: Como verificar se o Git foi instalado corretamente -->
```bash
git --version
# Saída esperada: git version 2.x.x
```

Se aparecer a versão, parabéns! 🎉

---

## Configuração Inicial

```bash
# Configurar nome
git config --global user.name "Seu Nome"

# Configurar email
git config --global user.email "seu@email.com"

# Editor padrão (VS Code)
git config --global core.editor "code --wait"

# Ou terminal
git config --global core.editor "nano"

# Ver configurações
git config --global --list
```

---

### Por que Configurar Nome e Email?

<!-- TODO: Explique a importância dessas configurações -->

* 🔖 **Autoria:** cada commit registra quem fez a alteração
* 🔗 **GitHub:** email vincula commits ao perfil
* 📊 **Estatísticas:** contribuições são contabilizadas

⚠️ Use um email vinculado ao GitHub.

---

## Criando uma Conta no GitHub

<!-- TODO: Passo a passo para criar conta no GitHub -->

1. Acesse [https://github.com](https://github.com)
2. Clique em **Sign up**
3. Preencha email, senha e usuário
4. Verifique seu email
5. Complete o perfil

🔐 Recomendado: ativar **2FA**

## Exemplos Práticos

### Exemplo 1: Cenário sem Controle de Versão

<!-- TODO: Descreva um cenário caótico sem controle de versão -->
<!-- Exemplo: múltiplas cópias de arquivo, versões conflitantes, etc. -->

```
site-portfolio/
├── index.html
├── style.css
├── script.js
├── index_FINAL.html
├── index_FINAL_v2.html
├── index_AGORA_VAI.html
├── style_OLD.css
├── style_BACKUP.css
└── ANOTACOES.txt
```

😰 Problemas:

* Qual versão é a correta?
* Como reverter mudanças?
* Como colaborar sem conflitos?

### Exemplo 2: Mesmo Cenário com Git

<!-- TODO: Mostre como Git resolve o problema do Exemplo 1 -->
```
site-portfolio/
├── index.html
├── style.css
├── script.js
└── .git/
```

Comandos úteis:

```bash
# Histórico
git log --oneline

# Voltar versão
git checkout a1b2c3d

# Nova branch
git checkout -b novo-menu

# Ver autor por linha
git blame index.html

# Atualizar projeto
git pull origin main

# Enviar alterações
git push origin novo-menu
```

---

## Erros Comuns

<!-- TODO: Liste erros comuns de iniciantes -->

### Erro 1: Confundir Git com GitHub

<!-- TODO: Como evitar essa confusão -->

❌ "Instalei o GitHub"
✅ Git = ferramenta | GitHub = plataforma

---

### Erro 2: Não configurar nome e email

<!-- TODO: O que acontece e como corrigir -->
```bash
git log
# Author: unknown <unknown>
```

Correção:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"

# Corrigir último commit
git commit --amend --author="Seu Nome <seu@email.com>" --no-edit
```

---

## Erro 3: Commitar arquivos sensíveis

❌ Senhas, API keys, etc.

### Prevenção:

* Use `.gitignore`
* Não commitar `.env`
* Use variáveis de ambiente

---

## Exercícios

<!-- TODO: Crie 3-5 exercícios práticos -->

1. **Instalação:** rodar `git --version`
2. **Configuração:** usar `git config`
3. **GitHub:** criar conta
4. **Repositório:**

```bash
mkdir meu-primeiro-repo
cd meu-primeiro-repo
git init
echo "# Meu Repo" > README.md
git add .
git commit -m "Primeiro commit"
git log
```

* **Exploração:** [https://github.com/explore](https://github.com/explore)

## Recursos Adicionais

- [Git Documentation](https://git-scm.com/doc) - Documentação oficial e completa do Git.
- [GitHub Docs - Get Started](https://docs.github.com/pt/get-started) - Guias oficiais do GitHub para iniciantes.
- [Git - A Simple Guide](https://rogerdudler.github.io/git-guide/index.pt_BR.html) - Um guia prático e rápido para começar sem complicações.
- [Oh Shit, Git!?!](https://ohshitgit.com/pt_BR) - Excelente site para ajudar a sair de situações difíceis e erros comuns no Git.
- [Pro Git Book](https://git-scm.com/book/pt-br/v2) - O livro completo sobre Git, gratuito e traduzido para português.

## Glossário

- **Commit**: Um "snapshot" (instantâneo) do estado dos seus arquivos em um momento específico. É um ponto no histórico do projeto salvo com um identificador único, autor, data e uma mensagem descritiva do que foi alterado.
- **Repository** (Repositório): O local (pasta) onde o seu projeto é armazenado e monitorado pelo Git. Ele contém todos os arquivos do projeto, além do diretório oculto `.git` que guarda todo o histórico de alterações.
- **Clone**: O ato de fazer o download de uma cópia exata e completa de um repositório remoto (ex: do GitHub) para o seu computador local, permitindo que você trabalhe nele offline.
- **Fork**: Uma cópia independente de um repositório de terceiros feita diretamente para a sua conta do GitHub. É usado para contribuir com projetos open source ou usar o projeto de alguém como ponto de partida para o seu.

## Resumo

- **Controle de versão é indispensável:** Permite rastrear mudanças, recuperar versões anteriores e trabalhar em equipe sem medo de perder arquivos.
- **Git ≠ GitHub:** Git é a ferramenta (motor) que roda no seu computador; GitHub é a plataforma na nuvem (estacionamento) onde você hospeda e compartilha seus repositórios Git.
- **Configuração inicial:** Sempre configure seu `user.name` e `user.email` localmente antes de começar a trabalhar para que seus commits sejam identificados corretamente.
- **Commits atômicos e claros:** Faça alterações pequenas e focadas. Use o padrão Conventional Commits (ex: `feat:`, `fix:`, `docs:`) com verbos no imperativo.
- **Clone vs Fork:** Use `clone` para baixar repositórios para a sua máquina e `fork` para criar uma cópia de um repositório alheio no seu próprio perfil do GitHub.
- **A prática leva à perfeição:** A melhor forma de aprender Git é usando no dia a dia. Crie um repositório de testes e pratique os comandos sem medo.

---

## 👥 Contribuidores

> Este conteúdo é colaborativo. Contribuidores deste arquivo:

- [@Enkiduzis](https://github.com/Enkiduzis) - Estrutura inicial, conceitos fundamentais e glossário.
<!-- Adicione seu nome quando contribuir:
- [@novo-contribuidor](https://github.com/novo-contribuidor) - Revisão da seção X e adição de links úteis.
-->
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


**Obeservação:** Lembre-se que o Git prioriza sempre a configuração **Local** sobre a **Global**. Se você configurou um e-mail dentro da pasta do projeto, ele será usado em vez do e-mail geral da sua máquina.



### Por que Configurar Nome e Email?

<!-- TODO: Explique a importância dessas configurações -->

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

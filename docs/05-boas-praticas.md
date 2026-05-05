# Boas Práticas com Git e GitHub

<!-- Este arquivo documenta boas práticas para usar Git de forma profissional -->

## 📋 Objetivos de Aprendizagem

Ao final deste capítulo, você será capaz de:
- Escrever mensagens de commit claras e padronizadas.
- Entender e aplicar o conceito de commits atômicos.
- Adotar padrões de nomenclatura e organização de branches.
- Configurar e utilizar corretamente o arquivo `.gitignore`.
- Aplicar práticas de segurança para evitar o vazamento de credenciais.

## 🎯 Introdução

Aprender os comandos do Git é apenas o começo; a verdadeira maestria está em saber como usá-los em um ambiente colaborativo. Boas práticas não são regras engessadas, mas sim convenções adotadas pela comunidade para garantir que o histórico do projeto seja legível, que o trabalho em equipe flua sem atritos e que a manutenção do código a longo prazo seja viável e segura.

## Mensagens de Commit

Mensagens de commit devem explicar de forma clara o que foi alterado no
projeto. Um bom histórico facilita revisão de código, investigação de bugs e
entendimento da evolução do sistema.

### Por que Mensagens Importam

Mensagens bem escritas ajudam a equipe a entender rapidamente o motivo de cada
alteração. Isso é importante durante code review, manutenção do projeto,
debugging e análise do histórico com comandos como `git log`.

Uma mensagem ruim, como `update`, não explica o que mudou. Já uma mensagem como
`fix: validate empty login form` mostra o tipo da alteração e o problema
resolvido.

### Estrutura de uma Boa Mensagem

Uma boa mensagem de commit deve ter uma primeira linha curta, com no máximo 72
caracteres, escrita no modo imperativo.

Use:

```text
Add feature
```

Evite:

```text
Added feature
```

Formato recomendado:

```text
tipo: resumo curto no imperativo

Explique o que foi alterado.

Explique por que a mudança foi necessária.

Explique como o sistema funciona agora.

Fixes #39
Refs #123
```

A linha em branco entre o título e o corpo é importante porque separa o resumo
da explicação detalhada.

Exemplo:

```bash
git commit -m "docs: add commit message best practices" -m "Explain how to write clear commit messages.

Describe the recommended format, conventional prefixes, issue references and git hooks.

Fixes #39
Refs #123"
```

### Corpo da Mensagem: What, Why e How Now

Quando a alteração precisar de mais contexto, use o corpo da mensagem para
responder três perguntas:

- **What:** o que foi alterado.
- **Why:** por que a alteração foi necessária.
- **How now:** como o projeto funciona depois da mudança.

Exemplo:

```text
fix: prevent duplicate user registration

Check if the email already exists before creating a new account.

This avoids duplicated users and improves data consistency.

Fixes #39
Refs #123
```

### Tipos de Commit

A convenção "Conventional Commits" estabelece prefixos para padronizar a intenção do commit:

- `feat`: Uma nova funcionalidade (feature) para o usuário.
- `fix`: Uma correção de um bug.
- `docs`: Alterações apenas na documentação (README, etc).
- `style`: Formatação, ponto e vírgula, espaços (não afeta o significado do código).
- `refactor`: Refatoração de código que não corrige bug nem adiciona funcionalidade.
- `test`: Adição ou correção de testes automatizados.
- `chore`: Tarefas de manutenção, atualização de dependências, etc.

### Exemplos de Boas Mensagens

```bash
✅ feat: adiciona autenticação via OAuth
✅ fix: corrige crash ao carregar perfil vazio no Android
✅ docs: atualiza instruções de instalação no README
✅ refactor: reorganiza estrutura de pastas dos componentes visuais
```

### Exemplos de Más Mensagens

```bash
❌ update (Muito vago: atualizou o quê?)
❌ fixes (O que foi corrigido?)
❌ changes (Mesmo problema acima)
❌ wip (Work In Progress - evite enviar isso para branches principais)
❌ aaaa teste (Nunca comite lixo no histórico público)
❌ mudanças do dia 15 (E o que foi feito no dia 15?)
```

Esse tipo de histórico é melhor do que uma sequência de commits genéricos como
`update`, `changes` ou `final`.

É altamente recomendado que as equipes documentem seu padrão de commits e o apliquem através de ferramentas automáticas para garantir a conformidade.

Git hooks podem ser usados para validar mensagens de commit antes que elas sejam
salvas no histórico.

Um hook comum para isso é o `commit-msg`, que pode verificar se a mensagem segue
um formato padrão, como Conventional Commits.

Exemplo de formato aceito:

```text
docs: add commit message best practices
```

Exemplo de formato rejeitado:

```text
added commit docs
```

Exemplo simples de hook `commit-msg`:

```bash
#!/bin/sh

commit_msg_file="$1"
commit_msg="$(head -n 1 "$commit_msg_file")"

pattern="^(feat|fix|docs|style|refactor|test|chore): .{1,72}$"

if ! echo "$commit_msg" | grep -Eq "$pattern"; then
  echo "Mensagem de commit inválida."
  echo "Use o formato: tipo: resumo curto"
  echo "Exemplo: docs: add commit message best practices"
  exit 1
fi
```

Esse tipo de validação ajuda a manter o padrão do projeto e evita mensagens
genéricas no histórico.

## Commits Atômicos

### O que São

Um commit atômico é um commit que encapsula apenas **uma única mudança lógica e coesa**. Em vez de agrupar dezenas de alterações não relacionadas no mesmo pacote, o commit atômico foca em apenas uma tarefa ou bug específico, garantindo que o histórico do projeto conte uma história clara.

### Por que Usar

- **Facilita o Code Review:** Revisores entendem as mudanças muito mais rápido.
- **Reversão Segura:** Se algo quebrar, você pode dar `git revert` apenas naquela mudança específica sem perder o trabalho de outras *features*.
- **Cherry-pick:** Permite puxar uma alteração específica para outra branch sem arrastar lixo junto.
- **Debug Simplificado:** O `git bisect` fica muito mais preciso na hora de encontrar qual commit introduziu um bug.

### Como Fazer

1. **Faça modificações pequenas:** Terminou uma função lógica? Faça o commit.
2. **Use o `git add -p`:** Se você mexeu em vários arquivos, adicione à área de preparação (staging) apenas os pedaços de código que fazem sentido juntos.
3. **Não misture refatoração com novas *features*:** Se você corrigiu a indentação de um arquivo inteiro e depois criou um botão, faça dois commits separados.

### Exemplos

```bash
# ✅ BOM: commits separados para mudanças diferentes
git commit -m "feat: adiciona validação de formato de email no backend"
git commit -m "feat: implementa feedback visual de senha fraca no frontend"
git commit -m "docs: atualiza documentação da API de login"

# ❌ RUIM: tudo misturado e difícil de rastrear
git commit -m "adiciona validações no front e back e documenta API"
```

## Organização de Branches

### Nomenclatura de Branches

Assim como as mensagens de commit, os nomes das branches devem ser autoexplicativos e usar convenções de prefixo. Use hífens para separar palavras.

#### Padrões Comuns

```text
feature/<nome-da-funcionalidade>
fix/<descricao-do-bug>
hotfix/<bug-critico-em-producao>
docs/<o-que-foi-documentado>
refactor/<o-que-foi-refatorado>

# Exemplos reais:
feature/login-oauth-google
fix/crash-botao-comprar
docs/traducao-readme-ptbr
```
#### Boas Práticas

- Use nomes descritivos: `feature/user-login` é melhor que `feature/abc123`
- Use letras minúsculas
- Prefira hífens `-` no lugar de underscores `_`
- Evite nomes muito longos
- Evite várias pessoas trabalhando na mesma branch
- Siga a convenção definida pelo projeto

#### Listar Branches

Para visualizar branches locais e remotas:

```bash
git branch -a
```

#### Prefixo com Username

Em projetos com dezenas de colaboradores, adicionar o nome do usuário ajuda a identificar o "dono" da branch.

```text
<nome-usuario>/<tipo>/<descricao>

# Exemplo:
joao-silva/feature/adiciona-barra-busca
```

### Lifetime de Branches

Branches podem ser temporárias ou permanentes, conforme o fluxo do projeto.

#### Short-Lived Branches (Branches de Vida Curta)

Branches de `feature` e `fix` devem durar pouco tempo (horas ou alguns dias). Quanto mais tempo uma branch fica separada da `main`, mais difícil e doloroso será o merge futuro (conhecido como "Merge Hell"). **Delete-as imediatamente após o merge.**

#### Long-Lived Branches (Branches de Vida Longa)

Branches como `main`, `develop` ou `release` são perenes. Elas servem como pilares do repositório onde todo o trabalho de vida curta se encontra.

## .gitignore

### O que É

O `.gitignore` é um arquivo de configuração do Git que lista padrões de arquivos e diretórios que devem ser **ignorados pelo controle de versão**. Qualquer arquivo ou pasta que corresponda a um padrão listado não será rastreado pelo Git, ou seja, não aparecerá como modificação e não poderá ser commitado acidentalmente.

---

### Por que Usar

Nem tudo que existe no seu projeto deve ir para o repositório. Os principais motivos para ignorar arquivos são:

- **Secrets e credenciais**: arquivos como `.env`, `*.key` e `credentials.json` contêm senhas, tokens e chaves de API que não devem ser expostos publicamente.
- **Dependências**: pastas como `node_modules/` e `venv/` são instaladas localmente e podem ser recriadas a qualquer momento — commitá-las aumenta o repositório sem necessidade.
- **Binários e builds**: arquivos gerados (como `dist/`, `build/`, `*.exe`) são produtos do código-fonte e não precisam ser versionados.
- **Arquivos de sistema e IDEs**: `.DS_Store`, `Thumbs.db`, `.vscode/`, `.idea/` são específicos do ambiente do desenvolvedor e não fazem parte do projeto em si.

> **Regra de ouro**: se um arquivo pode ser gerado, instalado ou contém informação sensível, ele provavelmente não deveria estar no repositório.

---

### Exemplos Comuns

```gitignore
# Dependências do projeto (baixadas dinamicamente)
node_modules/
venv/
.bundle/

# Compilados e Builds
dist/
build/
*.exe
*.dll

# Arquivos de sistema operacional
.DS_Store
Thumbs.db

# Credenciais e Secrets (CRÍTICO!)
.env
*.pem
*.key
credentials.json

# Arquivos de IDEs e Editores
.vscode/
.idea/
*.swp
```

### Globbing Patterns

O `.gitignore` usa **glob patterns** para definir quais arquivos ignorar:

| Padrão | O que ignora |
|---|---|
| `*.log` | Todos os arquivos com extensão `.log` |
| `build/` | O diretório `build` e todo seu conteúdo |
| `!important.log` | **Exceção**: não ignora este arquivo específico |
| `**/temp` | Diretório `temp` em qualquer nível da árvore |
| `doc/*.txt` | Arquivos `.txt` diretamente dentro de `doc/` |

> **Ordem importa**: coloque padrões mais **específicos antes dos mais genéricos**. Uma regra de exceção (`!`) só funciona se vier depois da regra que ignora o padrão.

---

### Templates

Não precisa escrever tudo do zero. O site **[gitignore.io](https://www.toptal.com/developers/gitignore)** gera automaticamente um `.gitignore` completo baseado na linguagem, framework ou ferramenta que você está usando.

Exemplos de templates disponíveis: `Python`, `Node`, `Java`, `React`, `Django`, `Unity`, entre muitos outros.

---

### Arquivo já Commitado

Se você acidentalmente já commitou um arquivo que deveria ser ignorado, apenas adicionar o padrão ao `.gitignore` **não resolve** — o Git continua rastreando o arquivo. Para removê-lo do rastreamento sem deletar do disco:

```bash
git rm --cached <nome-do-arquivo>
```

Para remover um diretório inteiro:

```bash
git rm -r --cached <nome-do-diretório>/
```

Depois, adicione o padrão ao `.gitignore`, faça o commit da remoção e o arquivo deixará de ser rastreado.

> ⚠️ **Atenção**: se o arquivo continha dados sensíveis (como senhas), considere rotacionar as credenciais, pois o histórico do Git ainda o conterá.

## README.md

### Importância

O **README.md** é o "cartão de visitas" do seu repositório. Ele é o primeiro arquivo renderizado quando alguém acessa o projeto no GitHub. Uma boa documentação poupa tempo de quem vai testar o código e demonstra profissionalismo, sendo um fator decisivo em processos seletivos.

### O que Incluir

Para um projeto ser considerado bem documentado, ele deve conter as seguintes seções:

*   **Título e Descrição:** Nome do projeto e um resumo claro do que ele faz.
*   **Funcionalidades (Features):** Lista do que o sistema entrega.
*   **Tecnologias:** Quais linguagens e ferramentas foram usadas.
*   **Instalação e Uso:** Comandos necessários para clonar, instalar dependências e rodar o projeto.
*   **Contribuindo:** Como outros desenvolvedores podem ajudar.
*   **Licença:** Informa se o código é aberto (MIT, Apache) ou restrito.

### Badges

Badges são pequenos selos que mostram informações dinâmicas (como se o código está funcionando ou qual a versão atual). Elas facilitam a batida de olho do recrutador.
Exemplos:
- ![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
- ![License](https://img.shields.io/badge/license-MIT-blue)

### Screenshots e GIFs

Projetos visuais **precisam** de demonstração. Se o seu projeto tem uma interface, tire um print ou grave um GIF da tela principal e insira no corpo do texto. No GitHub, você pode apenas arrastar a imagem para o editor que ele cria o link automaticamente.

### Template de Exemplo

Use o modelo abaixo como base para seus projetos:
```markdown
# 🚀 Nome do Projeto

> Uma frase curta que define o objetivo principal.

## 🏁 Como Começar
1. `git clone [https://github.com/usuario/repo.git](https://github.com/usuario/repo.git)`
2. `npm install`
3. `npm start`

## 🛠 Tecnologias
- React, Node.js e Gemini API.

## 📄 Licença
Este projeto está sob a licença MIT.

## Documentação

Além do README, repositórios profissionais mantêm outros arquivos na raiz:

### CONTRIBUTING.md

Guia detalhado sobre como desenvolvedores externos podem contribuir (como abrir issues, padrões de código, comandos para rodar testes).

### CODE_OF_CONDUCT.md

Garante um ambiente seguro e acolhedor para a comunidade, definindo comportamentos esperados e inaceitáveis.

### LICENSE

É crucial. Sem uma licença explícita, o código, mesmo público, está sob direitos autorais padrão e não pode ser legalmente modificado ou redistribuído por terceiros. Licenças comuns para open source: MIT, Apache 2.0, GPL.

### CHANGELOG.md

Um arquivo dedicado a listar as novidades, correções e alterações críticas (breaking changes) a cada nova versão lançada do projeto.

## [1.0.0] - 2025-03-01
### Added
- Versão inicial do projeto
```

### AUTHORS.md

Nem todo projeto usa, mas é uma boa prática para dar **crédito explícito** a todas as pessoas que contribuíram. O GitHub já tem o gráfico de contribuidores automático, mas o `AUTHORS.md` é uma alternativa mais personalizável e que funciona mesmo fora da plataforma.

**Exemplo de estrutura:**

```markdown
# Contribuidores

- [@fulanodetal](https://github.com/fulanodetal) - Documentação inicial
- João da Silva (joao@email.com) - Correção de bugs
- [@ciclano](https://github.com/ciclano) - Funcionalidade X
```

### SECURITY.md

Um arquivo essencial para projetos que podem ser usados por outras pessoas. Ele informa como reportar vulnerabilidades de segurança de **forma responsável** — ou seja, sem abrir uma issue pública que exporia o problema antes de ele ser corrigido.

**Seções recomendadas:**

- Como reportar uma vulnerabilidade (e-mail, formulário, etc.)
- Prazo esperado de resposta
- Quais versões ainda recebem correções de segurança

A presença desse arquivo aumenta a confiança da comunidade no projeto, pois demonstra maturidade e responsabilidade.

### Localização e Estrutura Padrão

Os arquivos de documentação essenciais devem estar localizados na raiz do repositório ou em `.github/` (para templates de issues e PRs). A estrutura padrão é:

| Arquivo | Localização | Estrutura Recomendada |
|---------|-------------|----------------------|
| `CONTRIBUTING.md` | Raiz | Pré-requisitos, fluxo de trabalho, padrões de commit, como abrir PR |
| `CHANGELOG.md` | Raiz | Formato [Keep a Changelog](https://keepachangelog.com/): versões em ordem decrescente, categorias `Added`, `Changed`, `Fixed`, `Removed`, `Security` |
| `LICENSE` | Raiz | Texto completo da licença escolhida. Use [choosealicense.com](https://choosealicense.com) para gerar |
| `SECURITY.md` | Raiz ou `.github/` | Seções: "Reportando uma Vulnerabilidade", "Processo de Resposta", "Versões Suportadas" |
| `CODE_OF_CONDUCT.md` | Raiz | Baseado no [Contributor Covenant](https://www.contributor-covenant.org/): compromisso, padrões, aplicação, escopo |
| `AUTHORS.md` | Raiz (opcional) | Lista de contribuidores com nomes, usernames e tipo de contribuição |

### Ferramentas Geradoras de Templates

Você não precisa criar esses arquivos do zero — existem ferramentas que geram os templates prontos:

| Ferramenta | Propósito | Como usar |
|------------|-----------|------------|
| **Templates do GitHub** | Criação inicial do repositório | Ao criar um repositório, marque "Add a README", "Add .gitignore" e "Add license" |
| [choosealicense.com](https://choosealicense.com) | Gerar arquivo `LICENSE` | Responda às perguntas e copie o texto gerado |
| [gitignore.io](https://gitignore.io) | Gerar `.gitignore` personalizado | Digite SO, IDE e linguagem; clique em "Generate" |
| [Contributor Covenant](https://www.contributor-covenant.org/version/2/1/code_of_conduct/) | Gerar `CODE_OF_CONDUCT.md` | Preencha o e-mail de contato e copie o Markdown gerado |
| [Keep a Changelog Generator](https://github.com/alexsoyes/keep-a-changelog-generator) (CLI) | Gerar `CHANGELOG.md` a partir de commits | Use com padrão Conventional Commits |
| **Commitizen** (`cz`) | Padronizar mensagens de commit | Instale com `npm install -g commitizen`; use `git cz` no lugar de `git commit` |
| **standard-version** | Automatizar versionamento e changelog | Execute `npx standard-version` — bumpa a versão, gera o `CHANGELOG.md` e cria a tag |
| **markdownlint** | Validar formatação de Markdown | Configure em `.markdownlint.json` e execute `markdownlint '**/*.md'` |

#### Exemplo de fluxo completo ao criar um projeto

Ao iniciar um novo repositório, um bom fluxo seria:

1. **Crie o repositório** com os templates do GitHub (README, `.gitignore`, `LICENSE`).
2. **Adicione o `CODE_OF_CONDUCT.md`** usando o Contributor Covenant Generator.
3. **Configure o `SECURITY.md`** manualmente com e-mail de contato e prazo de resposta.
4. **Padronize os commits** instalando o Commitizen e usando `git cz`.
5. **Automatize o changelog** com o `standard-version` a cada nova release.
## Histórico Limpo

Um histórico de Git deve contar a história de como o software foi construído de maneira lógica.

### Rebasing

(Conceito avançado). Permite reescrever a linha do tempo. É comum usar `git pull --rebase` em vez de `git pull` para evitar commits de merge desnecessários quando atualizamos nossa branch com a `main`, mantendo o histórico em uma linha reta.

### Squashing Commits

Antes de realizar o merge de uma branch (seja no terminal ou via Pull Request no GitHub), a técnica de "Squash" permite aglutinar 10 commits pequenos ("tentativa 1", "arrumando typo", "agora vai") em 1 único commit limpo e significativo na `main`.

### Evitar Force Push

Usar `git push --force` sobrescreve o histórico no servidor remoto com o seu histórico local.

```bash
# ⚠️ CUIDADO EXTREMO
git push --force
```
**Regra de Ouro:** Só use Force Push na **sua branch pessoal** em um PR (após fazer um rebase ou modificar commits antigos). **NUNCA, JAMAIS** use force push em branches compartilhadas (como `main` ou `develop`), pois isso destruirá o trabalho dos seus colegas.

## Commits Frequentes

### Commit Often, Push When Ready

"Faça commits frequentemente, faça push quando estiver pronto". Salve pequenos progressos locais no seu computador com `git commit`. Quando a funcionalidade inteira fizer sentido e estiver testada, mande para o GitHub com `git push`.

### Vantagens

Isso atua como um sistema de "save state" ultra granular. Se você quebrar tudo na última meia hora de trabalho, é só recuar para o commit de uma hora atrás sem perder o dia inteiro de serviço.

## Code Review Guidelines (Diretrizes de Revisão)

### Como Autor

Antes de abrir o PR para revisão:
- **Self-review primeiro:** Revise o seu próprio código no GitHub para pegar erros óbvios.
- **Testes passando:** Garanta que rodou os testes localmente.
- **Documentação:** Se mudou a API, atualizou o README?
- **Descrição:** O título e a descrição do PR explicam claramente o impacto da mudança?

### Como Revisor

Ao revisar código alheio:
- **Construtivo:** Aponte problemas com empatia, oferecendo soluções.
- **Específico:** Não diga "isso não está bom", diga "esse if/else ficaria mais legível usando um switch-case".
- **Focado:** Avalie a lógica e a arquitetura. Deixe a verificação de espaços em branco e formatação para ferramentas automáticas (Linters).

## Tags e Releases

Para marcar versões específicas de software pronto para entrega, usamos Tags.

### Versionamento Semântico (SemVer)

O padrão universal da indústria (MAJOR.MINOR.PATCH):
```text
1.0.0 - Release inicial oficial.
1.1.0 - Adicionada uma nova feature (sem quebrar o que já existia).
1.1.1 - Correção de um pequeno bug na versão anterior.
2.0.0 - Quebrou a compatibilidade (Breaking change), exige que o usuário mude como usa o software.
```

### Criar Tags no Git

```bash
# Cria uma tag "anotada" atrelada ao commit atual
git tag -a v1.0.0 -m "Release da Versão 1.0.0"

# Envia as tags para o GitHub
git push origin v1.0.0
```

### GitHub Releases

A interface do GitHub permite converter uma Tag em um "Release", onde você pode anexar notas de lançamento (Changelog) e arquivos compilados (binários, zips) para que os usuários baixem facilmente.

## Segurança: Nunca Commitar Secrets

### O que são secrets?

Secrets são informações sensíveis que dão acesso a sistemas, serviços ou dados protegidos. Se alguém obtém um secret seu, pode usar em seu nome — e o estrago pode ser real e imediato.

Exemplos comuns de secrets:

- **Chaves de API** — `GROQ_API_KEY=gsk_abc123...`, `OPENAI_API_KEY=sk-...`
- **Senhas de banco de dados** — `DATABASE_URL=postgres://user:senha@host/db`
- **Tokens de autenticação** — tokens OAuth, JWT secrets, tokens de bot (Telegram, Discord)
- **Chaves privadas** — arquivos `.pem`, `.key`, certificados SSL
- **Credenciais de cloud** — AWS Access Keys, Google Cloud service accounts

### Por que é tão perigoso?

Bots automatizados varrem repositórios públicos do GitHub **continuamente**, procurando chaves de API e senhas expostas. Quando encontram, exploram em segundos — não em horas, em segundos.

Cenários reais:

- Uma chave da AWS commitada por acidente gerou uma fatura de **US$ 14.000** em mineração de criptomoedas em poucas horas
- Tokens de bot do Telegram expostos permitiram que atacantes enviassem spam para milhares de usuários
- Chaves de API de serviços pagos (OpenAI, Google Cloud) são consumidas até estourar o limite de crédito

**Regra absoluta:** se um secret foi commitado — mesmo que por 1 segundo, mesmo que você tenha deletado logo depois — **assuma que foi comprometido**. O histórico do Git preserva tudo, e bots já podem ter capturado.

### Como prevenir: .gitignore

A primeira e mais simples defesa é o arquivo `.gitignore`. Ele diz ao Git quais arquivos **nunca** devem ser rastreados.

Adicione estas linhas ao `.gitignore` do seu projeto **antes do primeiro commit**:

```gitignore
# === SECRETS — NUNCA commitar ===
.env
.env.*
!.env.example

# Arquivos de configuração com credenciais
config.local.json
secrets/
*.key
*.pem

# Credenciais de cloud
.aws/
.gcloud/
service-account*.json
```

Explicação das linhas importantes:

- `.env` — o arquivo principal de variáveis de ambiente (onde ficam as chaves)
- `.env.*` — cobre variantes como `.env.local`, `.env.production`, `.env.development`
- `!.env.example` — o `!` é uma exceção: este arquivo **deve** ser commitado (veja abaixo por quê)
- `secrets/` — ignora uma pasta inteira de secrets
- `*.key` e `*.pem` — ignora chaves privadas e certificados

### O padrão .env + .env.example

Este é o padrão que toda equipe profissional usa:

**`.env`** (ignorado pelo Git — só existe na sua máquina):

```
GROQ_API_KEY=gsk_abc123_sua_chave_real_aqui
DATABASE_URL=postgres://admin:senha_secreta@localhost:5432/meubanco
```

**`.env.example`** (commitado no Git — mostra quais variáveis são necessárias):

```
GROQ_API_KEY=sua_chave_aqui
DATABASE_URL=postgres://usuario:senha@host:porta/banco
```

Quando um novo membro clona o repositório, ele:

1. Copia o arquivo: `cp .env.example .env`
2. Preenche com suas próprias credenciais
3. Pronto — o `.env` real nunca sai da máquina dele

### Usando variáveis de ambiente no código

Em vez de escrever a chave direto no código, carregue das variáveis de ambiente:

**Python:**

```python
import os

# ERRADO — chave exposta no código
api_key = "gsk_abc123_minha_chave_secreta"

# CERTO — carrega da variável de ambiente
api_key = os.getenv("GROQ_API_KEY")
```

Com a biblioteca `python-dotenv`, o `.env` é carregado automaticamente:

```python
from dotenv import load_dotenv
import os

load_dotenv()  # Carrega variáveis do arquivo .env
api_key = os.getenv("GROQ_API_KEY")
```

**No Google Colab**, use o recurso de Secrets (ícone de chave no painel lateral):

```python
from google.colab import userdata
api_key = userdata.get("GROQ_API_KEY")
```

### O que fazer se commitou um secret por acidente

Não entre em pânico, mas aja rápido. Siga estes passos na ordem:

**Passo 1 — Revogar o secret imediatamente**

Vá ao painel do serviço (Groq Console, AWS, Google Cloud, etc.) e **gere uma nova chave**. A antiga deve ser desativada. Não espere, não torça pra ninguém ter visto. Faça agora.

**Passo 2 — Remover o arquivo do rastreamento do Git**

```bash
# Remove o arquivo do Git mas mantém no disco
git rm --cached .env

# Adiciona ao .gitignore
echo ".env" >> .gitignore

# Commita a remoção
git commit -m "fix: remove .env do rastreamento do Git"
git push
```

**Passo 3 — Limpar o histórico do Git**

Mesmo depois de remover, o secret ainda está no histórico de commits. Para repositórios públicos, é necessário limpar:

```bash
# Usando git-filter-repo (ferramenta moderna recomendada)
pip install git-filter-repo
git filter-repo --path .env --invert-paths
git push --force --all
```

Alternativa com BFG Repo-Cleaner:

```bash
# Baixe o BFG: https://rtyley.github.io/bfg-repo-cleaner/
java -jar bfg.jar --delete-files .env
git reflog expire --expire=now --all
git gc --prune=now --aggressive
git push --force
```

### Ferramentas de prevenção

#### git-secrets

Ferramenta da AWS que bloqueia commits contendo padrões de secrets:

```bash
# Instalação
brew install git-secrets  # macOS
# ou
git clone https://github.com/awslabs/git-secrets.git
cd git-secrets && make install

# Configurar no repositório
git secrets --install
git secrets --register-aws  # Adiciona padrões de chaves AWS

# Agora, se tentar commitar uma chave AWS, o commit é bloqueado
```

#### Pre-commit hooks

Hooks são scripts que rodam automaticamente antes de cada commit. Você pode configurar um hook que escaneia por secrets:

```bash
# Instalar o framework pre-commit
pip install pre-commit

# Criar arquivo .pre-commit-config.yaml na raiz do projeto
```

```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/Yelp/detect-secrets
    rev: v1.4.0
    hooks:
      - id: detect-secrets
```

```bash
# Ativar
pre-commit install

# Agora, a cada commit, os arquivos são escaneados automaticamente
```

#### GitHub Push Protection

O próprio GitHub escaneia pushes e **bloqueia automaticamente** se detectar tokens conhecidos (AWS, Google, Stripe, etc.). Está ativo por padrão em repositórios públicos desde 2023.

### Variáveis de ambiente em CI/CD

Em pipelines de CI/CD (GitHub Actions, GitLab CI), **nunca** coloque secrets no código do workflow. Use os mecanismos nativos:

**GitHub Actions:**

1. Vá em Settings > Secrets and variables > Actions
2. Clique em "New repository secret"
3. Adicione o nome (ex: `GROQ_API_KEY`) e o valor
4. No workflow, acesse com `${{ secrets.GROQ_API_KEY }}`

```yaml
# .github/workflows/deploy.yml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Usar a chave
        env:
          API_KEY: ${{ secrets.GROQ_API_KEY }}
        run: python meu_script.py
```

Os secrets ficam criptografados e nunca aparecem nos logs — mesmo se você tentar imprimi-los.

### Educando o time

A segurança de secrets não é só técnica — é cultural. Boas práticas para equipes:

- **Onboarding:** Todo novo membro recebe orientação sobre o `.gitignore` e o padrão `.env.example` no primeiro dia
- **Revisão de PRs:** Revisores devem verificar se há secrets expostos em cada Pull Request
- **Rotação periódica:** Trocar chaves a cada 90 dias reduz o impacto de vazamentos não detectados
- **Princípio do menor privilégio:** Cada pessoa/serviço recebe apenas as permissões mínimas necessárias
- **Nunca compartilhar secrets por chat:** Nada de mandar chave de API pelo Slack, WhatsApp ou email. Use password managers (1Password, Bitwarden) ou o próprio mecanismo de secrets do GitHub

### Checklist de segurança

Antes de fazer qualquer push, verifique:

- [ ] `.env` está no `.gitignore`?
- [ ] `.env.example` existe com valores fictícios?
- [ ] Nenhuma chave de API está hardcoded no código?
- [ ] Variáveis sensíveis são carregadas via `os.getenv()` ou equivalente?
- [ ] O repositório tem pre-commit hooks ou git-secrets configurado?
- [ ] Secrets de CI/CD estão nos Settings do GitHub, não no código do workflow?

---

**Lembre-se:** Um secret exposto não pode ser "desexposto". A internet nunca esquece, e bots não dormem. Prevenir é infinitamente mais fácil do que remediar.

Se você subiu um secret acidentalmente para o GitHub:
1. **Considere o secret comprometido IMEDIATAMENTE.** A primeira ação não é arrumar o Git, é ir ao painel do serviço (AWS, Banco de Dados, etc.) e **revogar/deletar aquela chave.**
2. Existem ferramentas complexas (como o `BFG Repo-Cleaner` ou `git filter-repo`) para reescrever toda a história do repositório apagando o arquivo. Mas, por garantia, a chave revogada é a única proteção real.

## Fluxo de Trabalho (Workflows)

A escolha do modelo de fluxo (workflow) dita como a equipe colabora e integra o código. [cite_start]Atualmente, o mercado tem migrado do "lançamento de grandes versões" para a "entrega contínua", o que impacta diretamente qual modelo escolher[cite: 679].

### Git Flow

[cite_start]O GitFlow é um modelo rigoroso criado em 2010, baseado em múltiplas ramificações com funções muito específicas[cite: 626]. [cite_start]Ele é ideal para projetos que possuem ciclos de lançamento (releases) bem definidos e agendados[cite: 627].

- [cite_start]**main (ou master):** Código espelho da produção[cite: 628].
- [cite_start]**develop:** Onde a integração do dia a dia acontece[cite: 629].
- [cite_start]**feature branches:** Para novas funcionalidades (sempre saem da develop)[cite: 630].
- [cite_start]**release branches:** Para preparar uma nova versão (estabilização e limpeza de bugs antes da produção)[cite: 631].
- [cite_start]**hotfix branches:** Para correções críticas e imediatas direto em produção[cite: 632].

[cite_start]**Prós:** Excelente para releases definidas e controle rigoroso[cite: 641].
[cite_start]**Contras:** Muito complexo para entregas rápidas; pode gerar os famosos "merge hells" (conflitos gigantescos) se as branches durarem muito tempo[cite: 642].

### GitHub Flow

[cite_start]É uma versão simplificada do GitFlow e que se aproxima do Trunk-based, criada pelo próprio GitHub[cite: 670]. [cite_start]É o modelo padrão para a maioria dos projetos open source e startups[cite: 671].

[cite_start]Neste fluxo, a regra de ouro é: tudo o que está na `main` é implantável (deployable)[cite: 672]. O ciclo de vida é direto:
1. [cite_start]Cria-se uma `feature branch` descritiva a partir da `main`[cite: 673].
2. [cite_start]Abre-se um Pull Request (PR) para discussão e revisão[cite: 674].
3. [cite_start]Após o merge na `main`, o deploy é feito imediatamente[cite: 675].

### Trunk-Based Development

[cite_start]Atualmente é o modelo mais usado (e incentivado) em empresas de tecnologia de altíssima performance (como Google, Meta e Amazon)[cite: 677]. [cite_start]Todos os desenvolvedores trabalham em uma única branch principal (o "trunk" ou `main`)[cite: 649].

- [cite_start]As branches de funcionalidade são curtíssimas (duram horas ou, no máximo, um dia) ou nem existem[cite: 650].
- [cite_start]**Integração contínua (CI):** O código é testado e mesclado à `main` várias vezes ao dia[cite: 651].
- [cite_start]**Feature flags:** Como tudo vai para a `main` rápido, usa-se código "escondido" por chaves de configuração para não liberar funções incompletas para o usuário[cite: 652].

[cite_start]**Prós:** Velocidade máxima, feedback imediato e facilita muito o Continuous Deployment (CD)[cite: 654, 655].
[cite_start]**Contras:** Exige uma cultura de DevOps extremamente bem estabelecida, testes automatizados rigorosos e desenvolvedores experientes[cite: 656, 657, 658, 659, 660, 661].

## Aliases

O Git permite criar atalhos (apelidos) para comandos longos que você digita frequentemente.

### Configurando Aliases

```bash
# Atalhos para comandos básicos
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
```

Com a configuração acima, em vez de digitar `git status`, você só digita `git st`.

## Hooks

### O que São Git Hooks

Hooks são scripts que o Git executa automaticamente antes ou depois de determinadas ações (como commitar, fazer push, receber código).

### Hooks Comuns

Os times usam amplamente ferramentas (como Husky no ecossistema JavaScript ou Pre-commit no Python) para gerenciar hooks:
- **`pre-commit`:** Antes de o Git aceitar o commit, ele roda um linter de código. Se o código estiver mal formatado, o commit é abortado!
- **`commit-msg`:** Checa se a mensagem de commit que você digitou segue o padrão (ex: começa com `feat:` ou `fix:`).

## Erros Comuns a Evitar

1. **Trabalhar diretamente na Main:** Nunca faça isso. Sempre crie uma branch.
2. **Commits Gigantes:** Ninguém gosta de revisar PRs com 50 arquivos modificados e milhares de linhas alteradas. Quebre em partes menores.
3. **Mensagens Genéricas:** Mensagens como "Fix" ou "Update" matam a utilidade do histórico do Git.
4. **Esquecer de Atualizar Regularmente:** Trabalhar por 3 semanas sem puxar (pull) as novidades da `main` para a sua branch. Quando for integrar, os conflitos serão um pesadelo.
5. **Force Push na Main:** O atalho mais rápido para causar pânico em toda a equipe de engenharia.

## Checklist de Boas Práticas

### Antes de Fazer o Commit
- [ ] Meu código faz apenas uma coisa lógica? (Commit atômico).
- [ ] A mensagem do commit segue os padrões do time?
- [ ] Revisei usando `git status` e `git diff` se não adicionei arquivos indesejados acidentalmente?

### Antes de Fazer o Push
- [ ] Atualizei minha branch local e verifiquei se o código ainda funciona?
- [ ] Não há NENHUMA senha ou token hardcoded neste envio?

### Antes de Abrir o Pull Request
- [ ] Fiz uma autoleitura do meu diff na interface do GitHub para buscar erros bobos?
- [ ] A descrição do meu PR tem contexto suficiente para que alguém fora da minha equipe entenda o objetivo?
- [ ] Eu testei localmente a funcionalidade descrita?

## Ferramentas Recomendadas

Se a linha de comando assustar ou não for produtiva para você em tarefas visuais complexas, use ferramentas que ajudam a cumprir as boas práticas:

### GUIs (Interfaces Gráficas)
- **GitHub Desktop:** Oficial e muito simples para iniciantes.
- **GitKraken / SourceTree:** Ferramentas profissionais incríveis para resolver conflitos cabeludos e visualizar o grafo de milhares de commits.

### Extensions (Editores)
- **GitLens (VS Code):** Exibe exatamente quem modificou a linha de código em que seu cursor está focado, e de qual commit aquela mudança veio (o famoso e útil recurso de "Blame" inline).

## Resumo

- **Comunicação é tudo:** Use mensagens de commit baseadas em `Conventional Commits` e estruture bem os seus PRs.
- **Pequeno e Focado:** Faça `commits atômicos` e mantenha o tempo de vida das suas branches o mais curto possível.
- **Segurança primeiro:** Abrace o `.gitignore` com amor e nunca versione segredos. Se vazar, revogue a credencial no provedor na mesma hora.
- **O código não é seu, é do projeto:** Receba o *Code Review* de braços abertos, seja educado nos comentários e não leve críticas ao código para o lado pessoal.

---

## 👥 Contribuidores
-  [@ffogacalemos](https://github.com/ffogacalemos) - Seção boas práticas: .gitignor
<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir: -->
- [@ASCCJR](https://github.com/ASCCJR) - Seção Segurança
- [@idarlandias](https://github.com/idarlandias) - Seção Commits Atômicos
- [@JVictorFonseca](https://github.com/JVictorFonseca) - Seção README.md
- [@Sthefferson](https://github.com/Sthefferson) - Seção Fluxo de Trabalho

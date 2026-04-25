# Boas Práticas com Git e GitHub

<!-- Este arquivo documenta boas práticas para usar Git de forma profissional -->

## 📋 Objetivos de Aprendizagem

<!-- TODO: Objetivos sobre padrões e boas práticas -->

## 🎯 Introdução

<!-- TODO: Por que boas práticas importam -->
<!-- Trabalho em equipe, manutenibilidade, profissionalismo -->

## Mensagens de Commit

### Por que Mensagens Importam

<!-- TODO: Comunicação, histórico, debugging -->

### Estrutura de uma Boa Mensagem

<!-- TODO: Formato padrão -->

```
tipo: resumo em até 50 caracteres

Descrição detalhada (opcional) explicando:
- Por que essa mudança é necessária
- O que ela resolve
- Como funciona (se não óbvio)

Referências: #123, #456
```

### Tipos de Commit

<!-- TODO: Convenção de tipos -->

- `feat`: <!-- Nova funcionalidade -->
- `fix`: <!-- Correção de bug -->
- `docs`: <!-- Documentação -->
- `style`: <!-- Formatação, ponto e vírgula -->
- `refactor`: <!-- Refatoração de código -->
- `test`: <!-- Adicionar testes -->
- `chore`: <!-- Tarefas de manutenção -->

### Exemplos de Boas Mensagens

<!-- TODO: Exemplos reais -->

```bash
✅ feat: adiciona autenticação via OAuth
✅ fix: corrige crash ao carregar perfil vazio
✅ docs: atualiza instruções de instalação
✅ refactor: reorganiza estrutura de pastas
```

### Exemplos de  Más Mensagens

<!-- TODO: O que evitar -->

```bash
❌ update
❌ fixes
❌ changes
❌ wip
❌ aaaa teste
❌ mudanças do dia 15
```

### Convenções de Equipe

<!-- TODO: Conventional Commits, commitlint -->

### Ferramentas

<!-- TODO: commitlint, commitizen, git hooks -->

## Commits Atômicos

### O que São

<!-- TODO: Um commit = uma mudança lógica -->

### Por que Usar

<!-- TODO: Facilita review, revert, cherry-pick, debug -->

### Como Fazer

<!-- TODO: Dividir trabalho em pequenos commits coesos -->

### Exemplos

```bash
# ✅ BOM: commits separados
git commit -m "feat: adiciona validação de email"
git commit -m "feat: adiciona validação de senha"
git commit -m "docs: documenta validações"

# ❌ RUIM: tudo em um commit
git commit -m "adiciona validações e documentação"
```

## Organização de Branches

### Nomenclatura de Branches

<!-- TODO: Padrões de nomes -->

#### Padrões Comuns

```
feature/descricao
fix/descricao
hotfix/descricao
docs/descricao
refactor/descricao

# Exemplos:
feature/login-oauth
fix/bug-123
docs/readme-update
```

#### Prefixo com Username

<!-- TODO: Útil em projetos com muitos colaboradores -->

```
nome-usuario/feature/descricao

# Exemplo:
joao-silva/feature/adiciona-busca
```

### Lifetime de Branches

<!-- TODO: Branches de vida curta vs longa -->

#### Short-Lived Branches

<!-- TODO: Feature branches - deletar após merge -->

#### Long-Lived Branches

<!-- TODO: main, develop, release branches -->

## .gitignore

### O que É

<!-- TODO: Arquivo para ignorar arquivos -->

### Por que Usar

<!-- TODO: Evitar commit de arquivos desnecessários -->
<!-- Senhas, builds, dependências, etc. -->

### Exemplos Comuns

```gitignore
# TODO: Padrões comuns
# Dependências
node_modules/
venv/

# Builds
dist/
build/
*.exe

# Arquivos de sistema
.DS_Store
Thumbs.db

# Secrets
.env
*.key
credentials.json

# IDEs
.vscode/
.idea/
*.swp
```

### Templates

<!-- TODO: gitignore.io, templates do GitHub -->

### Arquivo já Commitado

<!-- TODO: Como ignorar arquivo já no repositório -->

```bash
# TODO: git rm --cached
```

## README.md

### Importância

<!-- TODO: Primeira impressão do projeto -->

### O que Incluir

<!-- TODO: Seções essenciais -->

```markdown
# Nome do Projeto

## Descrição
<!-- O que o projeto faz -->

## Instalação
<!-- Como instalar -->

## Uso
<!-- Como usar -->

## Contribuindo
<!-- Como contribuir -->

## Licença
<!-- Tipo de licença -->
```

### Badges

<!-- TODO: Shields.io, status badges -->

### Screenshots e GIFs

<!-- TODO: Imagens ajudam -->

## Documentação

### CONTRIBUTING.md

<!-- TODO: Guia de contribuição -->

### CODE_OF_CONDUCT.md

<!-- TODO: Código de conduta -->

### LICENSE

<!-- TODO: Escolher licença apropriada -->
<!-- MIT, GPL, Apache, etc. -->

### CHANGELOG.md

<!-- TODO: Histórico de mudanças -->

## Histórico Limpo

### Rebasing

<!-- TODO: Quando e como usar rebase -->
<!-- (Detalhes em capítulos avançados) -->

### Squashing Commits

<!-- TODO: Combinar commits relacionados -->

### Evitar Force Push

<!-- TODO: Quando é aceitável e quando evitar -->

```bash
# ⚠️ CUIDADO: só em branches pessoais
git push --force
```

## Commits Frequentes

### Commit Often, Push When Ready

<!-- TODO: Commitar localmente com frequência -->

### Vantagens

<!-- TODO: Pontos de recuperação, histórico detalhado -->

## Code Review Guidelines

### Como Autor

<!-- TODO: Preparar código para revisão -->

- <!-- Self-review primeiro -->
- <!-- Testes passando -->
- <!-- Documentação atualizada -->
- <!-- Descrição clara -->

### Como Revisor

<!-- TODO: Fazer boas revisões -->

- <!-- Construtivo -->
- <!-- Específico -->
- <!-- Oportuno -->
- <!-- Focado -->

## Tags e Releases

### Versionamento Semântico

<!-- TODO: SemVer - MAJOR.MINOR.PATCH -->

```
1.0.0 - Release inicial
1.1.0 - Nova feature
1.1.1 - Bug fix
2.0.0 - Breaking change
```

### Criar Tags

```bash
# TODO: git tag
# git tag -a v1.0.0 -m "Release 1.0.0"
# git push origin v1.0.0
```

### GitHub Releases

<!-- TODO: Interface de releases do GitHub -->

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


## Fluxo de Trabalho

### Git Flow

<!-- TODO: Introdução ao Gitflow -->
<!-- (Detalhes no capítulo 07) -->

### GitHub Flow

<!-- TODO: Fluxo simplificado -->

```
main → feature branch → PR → review → merge → deploy
```

### Trunk-Based Development

<!-- TODO: Alternativa moderna -->

## Aliases

### Configurando Aliases

```bash
# TODO: Atalhos úteis
# git config --global alias.co checkout
# git config --global alias.br branch
# git config --global alias.ci commit
# git config --global alias.st status
```

### Aliases Úteis

<!-- TODO: Lista de aliases recomendados -->

## Hooks

### O que São Git Hooks

<!-- TODO: Scripts automáticos -->

### Hooks Comuns

<!-- TODO: pre-commit, pre-push, commit-msg -->

### Exemplo: Pre-commit Hook

```bash
# TODO: Exemplo de hook para lint
```

## Performance

### Arquivo .gitattributes

<!-- TODO: Configurações por tipo de arquivo -->

### Large Files

<!-- TODO: Git LFS para arquivos grandes -->

### Shallow Clone

<!-- TODO: Quando usar --depth -->

## Erros Comuns a Evitar

### 1. Trabalhar na Main

<!-- TODO: Sempre usar branches -->

### 2. Commits Gigantes

<!-- TODO: Dividir em commits menores -->

### 3. Mensagens Genéricas

<!-- TODO: Ser específico -->

### 4. Não Atualizar Regularmente

<!-- TODO: Fetch/pull frequentemente -->

### 5. Force Push em Branch Compartilhada

<!-- TODO: Perigo! -->

## Checklist de Boas Práticas

<!-- TODO: Checklist completa -->

### Antes de Commit

- [ ] <!-- Código revisado -->
- [ ] <!-- Testes passando -->
- [ ] <!-- Mensagem descritiva -->
- [ ] <!-- Apenas arquivos relevantes -->

### Antes de Push

- [ ] <!-- Atualizado com remoto -->
- [ ] <!-- Build funciona -->
- [ ] <!-- Sem secrets -->

### Antes de PR

- [ ] <!-- Self-review feito -->
- [ ] <!-- Descrição completa -->
- [ ] <!-- Checks passando -->
- [ ] <!-- Documentação atualizada -->

## Ferramentas Recomendadas

### GUIs

<!-- TODO: GitKraken, SourceTree, GitHub Desktop -->

### Extensions

<!-- TODO: VS Code GitLens, Git Graph -->

### CLI Tools

<!-- TODO: tig, lazygit, gh -->

## Recursos Adicionais

<!-- TODO: Links sobre boas práticas -->

- [Conventional Commits](https://www.conventionalcommits.org/)
- [Git Best Practices](https://github.com/git-tips/tips)
- [SemVer](https://semver.org/)
- <!-- Mais recursos -->

## Resumo

<!-- TODO: Principais boas práticas a seguir -->

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->
- [@ASCCJR](https://github.com/ASCCJR) - Seção Segurança

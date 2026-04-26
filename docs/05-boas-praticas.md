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

## Segurança

### Nunca Commitar Secrets

<!-- TODO: Senhas, keys, tokens -->

### O que Evitar

<!-- TODO: Lista de arquivos perigosos -->

- `.env` com credenciais
- `config.json` com passwords
- Chaves SSH privadas
- Tokens de API
- Certificados

### Se Commitou Por Engano

<!-- TODO: Como remover do histórico -->
<!-- git filter-branch, BFG Repo-Cleaner -->
<!-- Regenerar secrets comprometidos! -->

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

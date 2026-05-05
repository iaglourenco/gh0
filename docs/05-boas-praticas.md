# Boas Práticas com Git e GitHub

<!-- Este arquivo documenta boas práticas para usar Git de forma profissional -->

## 📋 Objetivos de Aprendizagem

<!-- TODO: Objetivos sobre padrões e boas práticas -->

## 🎯 Introdução

<!-- TODO: Por que boas práticas importam -->
<!-- Trabalho em equipe, manutenibilidade, profissionalismo -->

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

É recomendado usar prefixos convencionais para indicar o tipo da alteração:

- `feat`: nova funcionalidade
- `fix`: correção de bug
- `docs`: alteração na documentação
- `style`: formatação, espaços, ponto e vírgula
- `refactor`: melhoria interna sem mudar comportamento
- `test`: criação ou alteração de testes
- `chore`: tarefas de manutenção

Exemplos:

```bash
git commit -m "feat: add user authentication"
git commit -m "fix: validate empty password field"
git commit -m "docs: update README setup guide"
git commit -m "style: format markdown lists"
```

### Exemplos de Boas Mensagens

```text
feat: add password reset flow

fix: prevent form submission with empty fields

docs: add local installation instructions

refactor: simplify user validation service
```

Essas mensagens são boas porque indicam o tipo da alteração e explicam o que foi
feito de forma objetiva.

### Exemplos de Más Mensagens

```text
update

changes

final version

fix bugs

added things

wip
```

Essas mensagens devem ser evitadas porque são genéricas e não explicam a
alteração feita no projeto.

### Referência a Issues

Quando um commit estiver relacionado a uma issue, informe isso no corpo da
mensagem.

Use palavras-chave como:

```text
Fixes #39
Closes #39
Resolves #39
Refs #123
```

Exemplo:

```text
docs: add README best practices

Explain how to write clear README files with practical examples.

Fixes #39
Refs #123
```

### Histórico Limpo

Um histórico limpo facilita a leitura do projeto com `git log`.

Exemplo:

```bash
git log --oneline
```

Saída esperada:

```text
a1b2c3d docs: add commit message best practices
b4c5d6e fix: validate empty login form
c7d8e9f feat: add user authentication
```

Esse tipo de histórico é melhor do que uma sequência de commits genéricos como
`update`, `changes` ou `final`.

### Ferramentas e Git Hooks

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
# ✅ BOM: commits separados
git commit -m "feat: adiciona validação de email"
git commit -m "feat: adiciona validação de senha"
git commit -m "docs: documenta validações"

# ❌ RUIM: tudo em um commit
git commit -m "adiciona validações e documentação"
```

## Organização de Branches

### Nomenclatura de Branches

Definir uma convenção para nomes de branches facilita a organização do projeto, melhora a comunicação da equipe e torna o histórico mais claro.

#### Padrões Comuns

Utilize prefixos conforme o tipo de alteração:

```text
feature/descricao
bugfix/descricao
hotfix/descricao
release/descricao
docs/descricao
refactor/descricao

# Exemplos:
feature/user-login
bugfix/erro-cadastro
hotfix/falha-api
release/v1-0-0
docs/readme-update
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

Útil em projetos com muitos colaboradores, pois identifica facilmente quem está trabalhando em cada tarefa.

```
nome-usuario/feature/descricao

# Exemplo:
joao-silva/feature/adiciona-busca
```

### Lifetime de Branches

Branches podem ser temporárias ou permanentes, conforme o fluxo do projeto.

#### Short-Lived Branches

Branches criadas para tarefas específicas, como features ou correções. Devem ser removidas após o merge para manter o repositório limpo.

#### Long-Lived Branches

Branches permanentes utilizadas como base do projeto, como `main`, `develop` e `release`.

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
<!-- Adicione seu nome quando contribuir: -->
- [@idarlandias](https://github.com/idarlandias) - Seção Commits Atômicos
- [@Sthefferson](https://github.com/Sthefferson) - Seção Fluxo de Trabalho

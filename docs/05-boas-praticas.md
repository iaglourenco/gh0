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
<!-- Adicione seu nome quando contribuir: -->
- [@idarlandias](https://github.com/idarlandias) - Seção Commits Atômicos
- [@JVictorFonseca](https://github.com/JVictorFonseca) - Seção README.md

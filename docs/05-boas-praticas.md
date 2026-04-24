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

### Por que Mensagens Importam

As mensagens de commit são a única forma de comunicação assíncrona permanente entre o desenvolvedor que escreveu o código hoje e o desenvolvedor que precisará dar manutenção nesse código daqui a cinco anos (que pode ser você mesmo!). Elas são fundamentais para entender o histórico, realizar debugging e reverter alterações com segurança.

### Estrutura de uma Boa Mensagem

Um formato amplamente adotado e considerado excelente é separar o assunto do corpo do commit com uma linha em branco:

```text
tipo: resumo claro do que foi feito em até 50 caracteres

Descrição detalhada (opcional) explicando:
- Por que essa mudança é necessária (o contexto)
- O que ela resolve tecnicamente
- Como funciona (caso a lógica seja complexa)

Referências a issues: Fixes #123, Resolves #456
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

### Convenções de Equipe

É altamente recomendado que as equipes documentem seu padrão de commits e o apliquem através de ferramentas automáticas para garantir a conformidade.

### Ferramentas

Ferramentas como `commitlint` validam a mensagem antes de permitir o commit. O `commitizen` fornece um prompt interativo no terminal para ajudar a formatar a mensagem corretamente, enquanto "Git Hooks" garantem que essas ferramentas rodem automaticamente.

## Commits Atômicos

### O que São

Um commit atômico é aquele que engloba **uma única e indivisível mudança lógica**. Ele deve fazer apenas uma coisa, e fazê-la por completo, sem quebrar a compilação do projeto.

### Por que Usar

- **Facilita o Code Review:** Revisores analisam pedaços pequenos de código com mais eficácia.
- **Facilita Reversões (Revert):** Se um commit introduz um bug, é fácil removê-lo se ele só tratar de uma coisa. Se ele misturar uma nova feature com a correção de um bug não relacionado, reverter o commit removerá ambas as coisas.
- **Rastreabilidade Limpa:** Fica mais fácil usar ferramentas como `git bisect` para encontrar quando um bug foi introduzido.

### Como Fazer

Divida grandes tarefas em passos menores. Se você notou um erro de formatação em um arquivo enquanto desenvolvia uma nova funcionalidade, resista à tentação de misturá-los. Faça um commit para a funcionalidade (`feat`) e outro para a formatação (`style`).

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

#### Prefixo com Username

Em projetos com dezenas de colaboradores, adicionar o nome do usuário ajuda a identificar o "dono" da branch.

```text
<nome-usuario>/<tipo>/<descricao>

# Exemplo:
joao-silva/feature/adiciona-barra-busca
```

### Lifetime de Branches (Tempo de Vida)

#### Short-Lived Branches (Branches de Vida Curta)

Branches de `feature` e `fix` devem durar pouco tempo (horas ou alguns dias). Quanto mais tempo uma branch fica separada da `main`, mais difícil e doloroso será o merge futuro (conhecido como "Merge Hell"). **Delete-as imediatamente após o merge.**

#### Long-Lived Branches (Branches de Vida Longa)

Branches como `main`, `develop` ou `release` são perenes. Elas servem como pilares do repositório onde todo o trabalho de vida curta se encontra.

## .gitignore

### O que É

Um arquivo de texto na raiz do seu projeto chamado `.gitignore`. Ele diz ao Git explicitamente quais arquivos e pastas **não devem ser rastreados** e, portanto, nunca devem ser enviados para o repositório remoto.

### Por que Usar

- Impedir o vazamento de senhas e credenciais.
- Economizar espaço e tempo ignorando pastas gigantes geradas automaticamente (como `node_modules` ou pastas de `build`).
- Evitar poluir o projeto de outras pessoas com arquivos temporários do seu sistema operacional ou editor de código.

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

### Templates

Nunca perca tempo escrevendo um `.gitignore` do zero. Use sites como o [gitignore.io](https://www.toptal.com/developers/gitignore) ou os templates oficiais oferecidos pelo próprio GitHub na criação do repositório.

### Arquivo já Commitado

Se você cometeu o erro de adicionar um arquivo e só depois colocá-lo no `.gitignore`, o Git continuará rastreando as mudanças dele. Para forçar o Git a "esquecer" o arquivo sem apagá-lo do seu computador:

```bash
git rm --cached nome-do-arquivo.txt
git commit -m "chore: remove arquivo do rastreamento e adiciona ao gitignore"
```

## README.md

### Importância

O `README.md` é a porta de entrada, o cartão de visitas e o manual de instruções do seu projeto. Um repositório sem um bom README costuma ser ignorado por outros desenvolvedores.

### O que Incluir

```markdown
# Nome do Projeto

## Descrição
Um parágrafo claro sobre o que o projeto faz, qual problema resolve e para quem ele é feito.

## Pré-requisitos
O que preciso ter instalado na minha máquina? (Ex: Node.js v18, Python 3.10).

## Instalação
Passo a passo com comandos de terminal para rodar o projeto localmente.

## Uso
Exemplos práticos de como utilizar a aplicação ou a API.

## Contribuindo
Um link para o arquivo CONTRIBUTING.md ou regras básicas.

## Licença
Declaração de direitos autorais (Ex: Licença MIT).
```

### Badges e Visuals

Use badges (como os do [Shields.io](https://shields.io/)) no topo do README para mostrar o status dos testes, versão, ou licença. Adicione **Screenshots** (capturas de tela) ou **GIFs** se o projeto tiver uma interface gráfica; imagens valem mais que mil palavras!

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

## Segurança

### Nunca Commitar Secrets

A regra número um do versionamento em nuvem: **Nunca coloque senhas, chaves de API ou tokens de banco de dados no código.** O GitHub é escaneado diariamente por robôs maliciosos que roubam credenciais expostas em segundos.

### O que Evitar e Como Resolver

Arquivos comuns que contêm segredos:
- `.env` (Use variáveis de ambiente injetadas no servidor, e no código crie um arquivo de exemplo seguro como `.env.example`).
- Chaves SSH e Certificados.
- Arquivos de configuração de banco de dados com a senha hardcoded.

### Se Commitou Por Engano

Se você subiu um secret acidentalmente para o GitHub:
1. **Considere o secret comprometido IMEDIATAMENTE.** A primeira ação não é arrumar o Git, é ir ao painel do serviço (AWS, Banco de Dados, etc.) e **revogar/deletar aquela chave.**
2. Existem ferramentas complexas (como o `BFG Repo-Cleaner` ou `git filter-repo`) para reescrever toda a história do repositório apagando o arquivo. Mas, por garantia, a chave revogada é a única proteção real.

## Fluxo de Trabalho (Workflows)

### Git Flow

Um modelo robusto que separa o projeto em branches eternas (`main` para produção, `develop` para integração) e branches de vida curta (`feature`, `release`, `hotfix`). Excelente para software instalado que necessita de controle rígido de versões.

### GitHub Flow

Um modelo mais simples e moderno focado em entrega contínua (Deploy Continuo).
```text
main (sempre em produção) → cria feature branch → abre PR → review aprovado → merge na main → deploy automático.
```

### Trunk-Based Development

Equipes muito maduras não usam branches duradouras. Todo mundo comita pequenas alterações diretamente na `main` o tempo todo, usando recursos complexos como "Feature Flags" para esconder o código não finalizado dos usuários.

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

<div align="center">

[⬅️ Capítulo Anterior: 04. Pull Requests e Review](./04-pull-requests-e-review.md)
 | 
[Capítulo Seguinte: 06. Resolução de Conflitos ➡️](./06-resolucao-conflitos.md)

</div>

## 👥 Contribuidores

Este conteúdo é colaborativo. Contribuidores deste arquivo:
- [@bigauke](https://github.com/bigauke) (Antonio Daniel de Souza Linhares) - Preenchimento do conteúdo sobre Boas Práticas.
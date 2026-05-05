# Branching e Merge

<!-- Este arquivo explica como trabalhar com branches e fazer merge no Git -->

## 📋 Objetivos de Aprendizagem

- Compreender o que são branches e como funcionam
- Criar, listar, trocar e deletar branches
- Entender o papel do HEAD
- Trabalhar com múltiplas linhas de desenvolvimento paralelas
- Aplicar boas práticas de nomenclatura

## 🎯 Introdução

Branches são fundamentais para o desenvolvimento de software moderno. Eles permitem trabalhar em paralelo sem interferir no código principal, facilitando experimentação segura, correção de bugs e desenvolvimento de novas funcionalidades de forma organizada.

## O que são Branches?

Uma **branch** (ramificação) é uma referência leve que aponta para um commit específico no histórico do repositório. Em termos técnicos, um branch é simplesmente um ponteiro (pointer) para um hash SHA-1 de um commit.

### Analogia Visual

Pense em uma árvore:

- O **tronco** representa a branch principal (main)
- Os **galhos** são branches secundárias
- Cada commit é um ponto na história onde você tomou um caminho diferente

### Como Funcionam

```
Commit:    A        B        C        D        (main)
              ↓        ↓        ↓        ↓
            1a2b3c   4d5e6f   7g8h9i   0j1k2l   (hash dos commits)
              │
              └─ Another-branch (ponteiro para C)
```

Cada branch armazena apenas o hash do commit mais recente. O Git então segue a cadeia de commits pais para construir o histórico completo.

### Por que Usar Branches?

| Benefício                         | Descrição                                                                            |
| ---------------------------------- | -------------------------------------------------------------------------------------- |
| **Isolamento**               | Cada feature ou correção pode ser desenvolvida isoladamente                          |
| **Desenvolvimento Paralelo** | Multiple desenvolvedores podem trabalhar em diferentes funcionalidades simultaneamente |
| **Experimentação Segura**  | Alterações experimentais não afetam o código em produção                         |
| **Organização**            | Separação clara entre trabalho em andamento e código estável                       |

### Ciclo de Vida de uma Branch

1. **Criar** - Iniciar uma nova linha de desenvolvimento
2. **Trabalhar** - Fazer commits com alterações
3. **Merge** - Integrar as mudanças à branch destino
4. **Deletar** - Remover a branch após a integração

### Visualizando Branches

Um branch é simplesmente um ponteiro (reference) que aponta para um commit específico. O Git usa essa referência para navegar pelo histórico de commits.

#### Diagrama de Múltiplas Branches

```
       main:     A---B---C---D---E
                │
                └─ feature/login:       F---G---H
                           │
                           └─ bugfix/error:        I---J
```

- **A, B, C, D, E**: Commits na branch main
- **F, G, H**: Commits na branch feature/login (começa a partir de E)
- **I, J**: Commits na branch bugfix/error (começa a partir de H)

#### HEAD: O Ponteiro Atual

O **HEAD** é uma referência especial que indica o commit (e branch) atual onde você está trabalhando.

```
HEAD -> main -> D (você está na branch main, no commit D)
```

Quando você muda de branch, o HEAD é atualizado para apontar para a nova branch.

## Branch Principal (main/master)

A branch **main** (anteriormente chamada de **master**) é a branch padrão do repositório. Ela representa a linha principal de desenvolvimento e, geralmente, contém o código que está em produção.

### Características

- É criada automaticamente ao inicializar um repositório Git
- Geralmente contém o código mais estável e deployável
- Frequentemente protegida em repositórios remotos (não permite push direto)
- Serve como base para criar outras branches

### Histórico: master → main

Recentemente, a comunidade Git mudou de **master** para **main** como nome padrão, adotando uma linguagem mais inclusiva. Repositórios novos já usam **main** por padrão.

## Trabalhando com Branches

### Listar Branches

Para ver quais branches existem no seu repositório local:

```bash
# Listar branches locais
git branch

# Listar todas as branches (locais e remotas)
git branch -a

# Listar branches com último commit
git branch -v

# Listar branches que já foram mescladas na branch atual
git branch --merged

# Listar branches que ainda não foram mescladas
git branch --no-merged
```

### Criar uma Nova Branch

Para criar uma ramificação a partir do ponto atual onde você está:

```bash
# Criar uma nova branch (sem trocar para ela)
git branch <nome-da-branch>

# Exemplo
git branch feature/login
```

#### Boas Práticas de Nomenclatura

Use nomes descritivos e consistentes para suas branches:

| Prefixo                 | Uso                   | Exemplo                    |
| ----------------------- | --------------------- | -------------------------- |
| `feature/`            | Novas funcionalidades | `feature/login-social`   |
| `fix/` ou `bugfix/` | Correção de bugs    | `fix/bug-login-123`      |
| `hotfix/`             | Correções urgentes  | `hotfix/erro-producao`   |
| `docs/`               | Documentação        | `docs/readme-atualizado` |
| `refactor/`           | Refatoração         | `refactor/auth-service`  |
| `experiment/`         | Experimentos          | `experiment/nova-api`    |

### Dicas

- Use letras minúsculas e hifens para separar palavras
- Inclua o número da issue quando aplicável: `feature/login-#123`
- Mantenha nomes curtos mas descritivos

### Trocar de Branch

Para navegar entre as linhas do tempo (branches):

```bash
# Trocar para uma branch existente
git checkout <nome-da-branch>

# OU (comando mais moderno)
git switch <nome-da-branch>

# Exemplo
git checkout feature/login
git switch feature/login
```

> **Nota:** O `git switch` é recomendado pois é mais específico que `git checkout` (que também serve para outras coisas).

### Criar e Trocar em Um Comando

Na prática, quase sempre que criamos uma branch, queremos ir imediatamente para ela. Existem atalhos para isso:

```bash
# Criar e trocar para nova branch em um comando
git checkout -b <nome-da-branch>

# OU (comando mais moderno)
git switch -c <nome-da-branch>

# Exemplo
git checkout -b feature/login
git switch -c feature/login
```

> `-c` significa "create" (criar)

## Estados do Working Directory

Quando você troca de branch, o Git altera o conteúdo do seu diretório de trabalho para refletir o estado da branch selecionada.

### O que Acontece ao Trocar de Branch

1. O Git identifica o commit pela nova branch
2. Os arquivos no diretório de trabalho são atualizados para esse commit
3. O ponteiro HEAD é atualizado para apontar para a nova branch

### Cenário Comum

```
1. Você está na branch main com arquivos da versão 1.0
2. Troca para feature/nova-func
3. Seus arquivos agora mostram a versão com a nova funcionalidade
4. Trabalha e faz commits nessa versão
5. Troca de volta para main
6. Seus arquivos voltam para a versão original
```

### Mudanças Não Commitadas

Se você tiver alterações não salvas (não commitadas) e tentar trocar de branch, o Git impedirá a troca para evitar perda de trabalho.

```bash
# Você está em main com mudanças não commitadas
$ git status
On branch main
Changes not staged for commit:
  modified:   arquivo.txt

# Tentando trocar de branch
$ git checkout feature/nova
error: Your local changes would be overwritten by checkout.
Please commit them or stash them before you switch branches.
```

#### Soluções

1. **Fazer commit** das mudanças antes de trocar
2. **Stash** (salvar temporariamente): `git stash`

```bash
# Salvar mudanças temporariamente
git stash

# Trabalhar na nova branch
git checkout feature/nova
# ... fazer trabalho ...

# Voltar para a branch anterior
git checkout main

# Restaurar as mudanças salvas
git stash pop
```

## Merge: Unindo Branches

### O que é Merge?

Merge é a operação de pegar as mudanças desenvolvidas em uma branch separada (ex: `feature`) e aplicá-las em outra branch (ex: `main`). É como dizer: "Ok, o código do universo paralelo está pronto, agora vamos trazê-lo para a realidade principal".

### Sintaxe Básica

Para fazer um merge, você **sempre deve estar na branch de destino** (a branch que vai receber as mudanças).

```bash
# 1. Troque para a branch que vai receber as alterações
git switch main

# 2. Execute o merge trazendo a branch desejada
git merge <nome-da-branch-feature>
```

### Assinatura de Commits de Merge (GPG Sign)

Para garantir a máxima autenticidade e segurança do código, é possível assinar digitalmente os seus merges utilizando chaves GPG. Isso prova criptograficamente que a integração no repositório foi realmente autorizada e executada por você.
```bash
# Realiza o merge e assina digitalmente a transação
git merge -S feature/nova-funcionalidade

### Exemplo de Merge

```bash
# Criar e ir para nova branch
git switch -c feature/nova-tela

# ... faço edições no código ...
git add .
git commit -m "feat: adiciona nova tela de perfil"

# Volto para a branch principal
git switch main

# Incorporo a nova funcionalidade à main
git merge feature/nova-tela
```

## Tipos de Merge

### Fast-Forward Merge

<!-- TODO: O que é fast-forward -->

<!-- Quando acontece: quando não há commits divergentes -->

### Fast-Forward Merge

Acontece quando a branch de destino (`main`) **não teve nenhum commit novo** desde que a branch de `feature` foi criada. Como o caminho é direto, o Git simplesmente move o ponteiro da `main` "para frente" (fast-forward) até o commit mais recente da `feature`.

```mermaid
gitGraph
   commit id: "A"
   commit id: "B"
   branch feature
   checkout feature
   commit id: "C"
   commit id: "D"
   checkout main
   merge feature type: FAST_FORWARD
```

### Three-Way Merge

<!-- TODO: O que é three-way merge -->

<!-- Quando acontece: quando há commits em ambas as branches -->

```
Antes:
main:    A---B---C
              \
feature:       D---E

Depois (merge commit):
main:    A---B---C---F
              \     /
feature:       D---E
```

### Merge Commit

<!-- TODO: O que é um merge commit -->

<!-- Tem dois parents -->

## Estratégias de Merge

Na linha de comando, podemos forçar o comportamento do merge através de opções (flags):

### --ff (Fast-Forward)

O Fast-Forward é o comportamento padrão do Git quando não há commits divergentes entre a branch de destino e a branch que está sendo mesclada. Em vez de criar um novo commit de merge, o Git simplesmente "avança" o ponteiro da sua branch atual para apontar para o commit mais recente da branch de origem. Isso mantém o histórico linear e direto.


```bash

# O Git tentará fazer um fast-forward por padrão se o histórico permitir
git merge feature/login

# Se você quiser garantir que o merge APENAS aconteça se for um fast-forward
# (abortando a operação caso haja conflitos ou divergências):
git merge --ff-only feature/login

```

### --no-ff (No Fast-Forward)

Esta estratégia força o Git a criar um commit de merge (com dois parents), mesmo que um fast-forward seja perfeitamente possível. A principal vantagem é a preservação histórica: fica claro no grafo do repositório onde uma feature começou e onde ela terminou, mantendo os commits daquela funcionalidade agrupados.

```bash
# Força a criação de um commit de merge explícito
git merge --no-ff feature/login

# Ao rodar esse comando, o Git abrirá o seu editor de texto padrão
# para que você confirme ou edite a mensagem do commit de merge gerado.
```

### --squash

O `squash` pega todos os commits da branch de `feature` e os comprime em uma única alteração no Working Directory, sem comitá-los automaticamente. Você então faz um único commit na branch principal com todas as novidades agregadas.

```bash
git merge --squash feature-nome
git commit -m "feat: pacote de funcionalidades finalizado"
```

### Squash vs Merge Commit: Quando usar?

A escolha entre preservar o histórico completo ou resumi-lo depende do contexto do seu trabalho e das regras da equipe:

- **Use Merge Commit (`--no-ff`):** Quando a sua branch representa uma funcionalidade grande e complexa, onde o histórico de decisões (os commits individuais) tem grande valor futuro para auditoria ou para uma possível reversão parcial.
- **Use Squash:** Quando a sua branch possui muitos commits pequenos de "trabalho em andamento" (como "wip", "arrumando erro", "tentando consertar bug"). O squash limpa essa "poluição" visual, transformando tudo em um único commit limpo e direto para a `main`.

### Estratégias Avançadas de Merge

Além das estratégias padrão, o Git possui algoritmos específicos para lidar com a forma como os arquivos são combinados durante um merge de múltiplas vias:

- **Recursive:** É o algoritmo padrão para merges de três vias (three-way merge) quando há apenas um ancestral comum. Ele constrói uma árvore de merge baseada no ancestral e é muito eficiente em detectar e lidar com arquivos renomeados de forma inteligente.
- **Resolve:** Semelhante ao recursive, mas projetado especificamente para lidar de forma segura com merges que possuem múltiplos cruzamentos de histórico. É muito seguro e rápido, mas pode falhar em situações de renomeação de arquivos muito complexas.
- **Ours:** Esta estratégia força o Git a ignorar completamente as mudanças da branch que está sendo mesclada em caso de conflito, mantendo apenas a "nossa" versão (a branch atual). O histórico registra que o merge aconteceu, mas o código permanece intocado pelas mudanças externas.
- **Theirs:** É o oposto exato da estratégia `ours`. Em caso de conflito estrutural, o Git descarta sumariamente as nossas alterações e aceita automaticamente a versão "deles" (da branch que está entrando). Deve ser utilizado com extrema cautela.



## Deletando Branches

### Deletar uma Branch Local

```bash
# Deletar branch local (apenas se já foi merged)
git branch -d <nome-da-branch>

# Forçar deleção (use com cuidado)
git branch -D <nome-da-branch>

# Exemplo
git branch -d feature/login
git branch -d bugfix/erro-correcao
```

### Deletar uma Branch Remota

```bash
# Deletar branch remota
git push origin --delete <nome-da-branch>

# Exemplo
git push origin --delete feature/nova-funcionalidade
```

### Quando Deletar Branches

- Após fazer merge na branch principal
- Quando a funcionalidade foi abandonada
- Para manter o repositório limpo

> **Nota:** Use `-d` (minúsculo) apenas se a branch já foi mesclada. Use `-D` (maiúsculo) para forçar a deleção.

## Visualizando o Grafo

O terminal pode desenhar o histórico das branches e seus merges de forma bastante ilustrativa:

```bash
git log --graph --oneline --all
```

## Branch Tracking

### Upstream Branch

Quando você envia uma branch local para o GitHub pela primeira vez, o Git precisa saber qual é a branch "gêmea" dela lá no servidor. Esse link é chamado de configuração de *upstream*.

```bash
# Ao fazer push pela primeira vez, cria a branch no remoto e vincula as duas
git push -u origin <nome-da-branch>

# A partir daí, basta digitar:
git push
```

## Exemplos Práticos

### Exemplo 1: Feature Branch Workflow

```bash
# Atualiza localmente
git pull origin main

# Cria a nova branch
git switch -c feature/dark-mode

# Trabalha...
git add .
git commit -m "feat: adiciona tema escuro"

# Retorna e integra
git switch main
git merge feature/dark-mode

# Limpa a casa
git branch -d feature/dark-mode
```

## Conventional Commits

O padrão **Conventional Commits** é uma convenção simples para formatar as mensagens de commit, tornando-as facilmente compreensíveis tanto para programadores quanto para sistemas automatizados. A estrutura básica é: `<tipo>: <descrição breve>`.

- `feat:` Adiciona uma nova funcionalidade ao projeto.
- `fix:` Resolve um bug ou erro.
- `docs:` Altera exclusivamente arquivos de documentação (como o README).
- `style:` Altera formatação, espaçamento ou indentação (sem mudar a lógica do código).
- `refactor:` Mudança estrutural no código que não corrige bug nem adiciona funcionalidade.
- `test:` Adiciona testes ausentes ou corrige testes existentes.

## Boas Práticas

```bash
# Remove o último commit (o do merge indesejado) da branch atual
git reset --hard HEAD~1
```

## Boas Práticas

- **Mantenha branches pequenas:** Elas devem durar pouco tempo, de preferência dias, não meses.
- **Commits frequentes:** Salve o progresso regularmente.
- **Merge com frequência:** Traga mudanças da `main` para a sua branch (`git merge main`) frequentemente para evitar um acúmulo gigante de alterações conflitantes no final.
- **Delete após usar:** Fez o merge, apague a branch.
- **Não comite na main:** Em times profissionais, o fluxo natural é sempre criar branch, aprovar e mergiar.

## Boas Práticas e Integração Contínua (CI/CD)

- **Sempre teste localmente antes do merge:** Nunca integre um código na branch principal sem antes rodar toda a suíte de testes na sua máquina. O código da branch de destino pode ter sido atualizado enquanto você trabalhava, o que pode quebrar a sua funcionalidade durante a junção.
- **Testes Automáticos em Pull Requests (CI/CD):** Em ambientes de desenvolvimento modernos, os repositórios são configurados com pipelines de Integração Contínua (CI). Isso significa que, ao abrir um Pull Request, robôs executam testes automatizados e validam a qualidade do código de forma independente. Um merge seguro só deve ser permitido pela equipe após o "sinal verde" de todos os testes da esteira de CI/CD.

## Estratégia Oficial da Equipe

Para o desenvolvimento deste projeto de documentação, nossa equipe utiliza a estratégia baseada no **GitHub Flow** combinada com **Squash and Merge**.

Isso significa que todo trabalho de documentação deve nascer em branches curtas e descritivas criadas a partir da `main`. A integração de volta ocorre exclusivamente via Pull Requests e, no momento da aprovação, os commits da branch de trabalho devem ser agrupados (squash) para mantermos um histórico linear, limpo e legível na ramificação principal.

## Workflows Comuns

### Feature Branch Workflow

O **Feature Branch Workflow** é o modelo base para a maioria das colaborações modernas no Git (e a base de fluxos como o GitHub Flow). A premissa principal é muito simples: todo novo desenvolvimento (seja uma nova funcionalidade, refatoração ou correção de bug) deve ser feito em uma branch dedicada, e nunca diretamente na branch `main`.

**Como funciona:**
1. A branch `main` representa o histórico oficial e deve estar sempre em um estado pronto para produção (estável).
2. Quando iniciar um trabalho, deve ser criada uma nova branch a partir da `main`, com um nome descritivo (ex: `feature/novo-layout`).
3. Desenvolve e faz os commits de forma isolada nessa nova branch.
4. Ao finalizar, é dado o push na branch para o repositório remoto e abre um **Pull Request (PR)**.
5. Após o código ser revisado e aprovado pela equipe, a branch é mesclada (merge) na `main` e, logo depois, pode ser deletada.

Esse fluxo garante que o código principal nunca seja quebrado por trabalhos em andamento e incentiva fortemente a cultura de revisão de código.

### Gitflow

O **Gitflow** é um modelo de workflow mais rigoroso e estruturado. Ele é ideal para projetos grandes, com várias equipes trabalhando simultaneamente e que possuem ciclos de lançamento (releases) programados e versionamento muito bem definido.

Diferente do Feature Branch Workflow, que gira apenas em torno de uma branch principal, o Gitflow utiliza duas branches de longa duração:
* **`main`**: Armazena *exclusivamente* o histórico de lançamentos oficiais em produção. Cada commit aqui geralmente recebe uma tag de versão.
* **`develop`**: Serve como a base de integração para todo o código novo. É o "coração" do desenvolvimento diário.

Para organizar o trabalho ao redor dessas duas, o Gitflow define três tipos de branches de suporte com papéis e tempos de vida estritos:
* **`feature/*`**: Para criar novas funcionalidades (ramificam da `develop` e fazem merge de volta na `develop`).
* **`release/*`**: Para preparar uma nova versão para produção, permitindo apenas testes e correções finais (ramificam da `develop` e fazem merge na `main` e na `develop`).
* **`hotfix/*`**: Para correções de bugs urgentes em produção (são as únicas que ramificam direto da `main` e fazem merge na `main` e na `develop`).

### Trunk-Based Development

O **Trunk-Based Development** é um modelo focado em integração contínua extrema. Em vez de manter branches de longa duração, todos os desenvolvedores integram suas pequenas mudanças (commits) diretamente na branch principal (frequentemente chamada de `trunk` ou `main`) várias vezes ao dia.

- Exige um conjunto robusto de testes automatizados para garantir que o *trunk* nunca quebre.
- Branches, quando existem, duram no máximo algumas horas (por exemplo, a implementação de uma etapa de um `feature/data-pipeline`).
- Utiliza fortemente *Feature Flags* (bandeiras de funcionalidade) para ocultar no código as funcionalidades que ainda estão inacabadas em produção.

## Conflitos de Merge

<!-- TODO: Introdução básica a conflitos -->

<!-- (Detalhado no capítulo 06 - Resolução de Conflitos) -->

### O que São

Conflitos são apenas o Git pedindo a intervenção humana para escolher qual código deve prevalecer. O Git insere marcações visuais (`<<<<<<<`, `=======`, `>>>>>>>`) no código conflitante para que você leia, decida, edite o arquivo apagando os marcadores e depois faça um commit para concluir o merge. (Esse processo é detalhado no Capítulo 06).

## git stash

Se você estiver no meio de um trabalho confuso e precisar trocar de branch urgentemente para arrumar um bug rápido na `main`, você pode usar a "gaveta" do Git: o `stash`.

### Quando Usar Stash

O comando `stash` pega todas as suas alterações não comitadas e as guarda temporariamente, limpando seu diretório. Assim, você pode trocar de branch livremente. Quando voltar, você as retira da gaveta.

```bash
# Guarda mudanças temporariamente na gaveta
git stash

# Tira a última coisa guardada da gaveta e aplica nos arquivos
git stash pop

# Vê o que tem guardado
git stash list
```

## Comparando Branches

Para ver o que tem de diferente no código da sua branch em relação à `main` antes do merge:

```bash
# Mostra o código diferente (diff) entre duas branches
git diff main..minha-branch
```

## Erros Comuns

### Erro 1: Merge na Branch Errada

Você queria fundir na `main`, mas sem perceber estava na branch `teste` e fez o merge nela.
**Solução:** Use o `git status` ou olhe a indicação no seu terminal para sempre ter certeza de qual branch está (`git switch`) antes de invocar o `git merge`. Se errar, pode ser revertido via `git reset`.

### Erro 2: Deletar Branch Sem Merge

Tentar apagar uma branch com código não finalizado usando `git branch -D` (forçado).
**Solução:** Sempre tente usar `-d` (minúsculo), o Git só permitirá deletar se tiver certeza de que as alterações já estão salvas na branch principal.

### Erro 3: Não Atualizar a Main Antes de Criar Branch

Criar uma branch a partir de uma `main` antiga na sua máquina, resultando em dezenas de conflitos na hora de integrar meses depois.
**Solução:** Sempre rode `git pull origin main` e certifique-se de ter os arquivos atualizados antes de dar o `git switch -c`.

## Exercícios

1. Crie uma nova branch chamada `docs/primeiro-teste` e troque para ela.
2. Adicione ou altere um arquivo. Faça o `git add` e o `git commit`.
3. Volte para a branch principal (`git switch main`). Observe que as suas alterações "sumiram" dos arquivos!
4. Realize a união usando `git merge docs/primeiro-teste` para que a `main` incorpore as mudanças.
5. Delete a branch usando `git branch -d docs/primeiro-teste`.

## Tabela de Referência

| Comando | Descrição |
| --- | --- |
| `git branch` | Lista as branches locais. |
| `git switch <branch>` | Troca para a branch especificada. |
| `git switch -c <branch>` | Cria uma nova branch e já troca para ela. |
| `git merge <branch>` | Junta a branch informada para dentro da branch atual. |
| `git branch -d <branch>` | Deleta a branch local (se já tiver sido mergiada). |
| `git stash` | Guarda alterações não comitadas temporariamente na gaveta. |

## Recursos Adicionais

- [Learn Git Branching (Game interativo incrível!)](https://learngitbranching.js.org/)
- [Atlassian Git Branching Tutorial](https://www.atlassian.com/git/tutorials/using-branches)
- [Fluxo de Trabalho Gitflow (Atlassian)](https://www.atlassian.com/br/git/tutorials/comparing-workflows/gitflow-workflow)
- [GitHub Flow (Documentação Oficial)](https://docs.github.com/pt/get-started/using-github/github-flow)
- <!-- Mais recursos -->

## Resumo

- **Branches** são universos paralelos de desenvolvimento que isolam as alterações.
- Use **`git switch`** para viajar entre esses universos.
- Use **`git merge`** a partir da branch de destino (ex: `main`) para fundir as alterações de outra branch.
- Sempre tente atualizar sua branch local antes de criar novos trabalhos paralelos para evitar dores de cabeça no futuro.
- Acostume-se a **deletar** as branches após os merges para manter a organização do time.

---

## 👥 Contribuidores

Este conteúdo é colaborativo. Contribuidores deste arquivo:

- [@daniballester](https://github.com/daniballester) - Issue #19 - Seção "O que são Branches"

- [@lukitkat](https://github.com/Lukitkat) - Issue #24 - Seção "Documentar estratégias de merge"



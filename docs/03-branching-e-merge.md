# Branching e Merge

<!-- Este arquivo explica como trabalhar com branches e fazer merge no Git -->

## 📋 Objetivos de Aprendizagem

<!-- TODO: Objetivos de aprendizagem sobre branches e merge -->

## 🎯 Introdução

<!-- TODO: Por que branches são importantes? -->
<!-- Desenvolvimento paralelo, experimentação segura, organização -->

## O que são Branches?

<!-- TODO: Conceito de branch -->
<!-- Analogia: linha do tempo alternativa, universo paralelo, etc. -->

### Por que Usar Branches?

<!-- TODO: Benefícios de trabalhar com branches -->

### Visualizando Branches

<!-- TODO: Como branches funcionam visualmente -->
<!-- Use diagramas ASCII ou descrição clara -->

```
main:     A---B---C---D
               \
feature:        E---F
```

## Branch Principal (main/master)

<!-- TODO: O que é a branch principal -->
<!-- Histórico: master → main -->
<!-- Por que geralmente é protegida -->

## Trabalhando com Branches

### Listar Branches

    git branch       # lista branches locais
    git branch -a    # lista todas (locais + remotas)
    git branch -r    # lista apenas branches remotas

---

### Criar uma Nova Branch

    git branch minha-feature

Esse comando cria uma nova branch, mas **não muda automaticamente para ela**.

#### Boas Práticas de Nomenclatura

- feature/login → nova funcionalidade  
- fix/bug-123 → correção de bug  
- docs/readme → documentação  
- hotfix/erro-critico → correção urgente  

---

### Trocar de Branch

    git checkout minha-feature

Ou usando o comando mais novo (recomendado):

    git switch minha-feature

---

### Criar e Trocar em Um Comando

    git checkout -b minha-feature

Ou com a sintaxe moderna:

    git switch -c minha-feature

---

### Deletando Branches

    git branch -d minha-feature   # deleta branch local (seguro)
    git branch -D minha-feature   # força deleção
    git push origin --delete minha-feature   # deleta branch remota

---

### Enviando Branch para o Repositório Remoto

    git push origin minha-feature

Esse comando envia a branch local para o repositório remoto (GitHub, por exemplo).

---

### Renomeando Branch

    git branch -m novo-nome

Ou renomeando uma específica:

    git branch -m nome-antigo novo-nome

---

### Branch Local vs Remota

- Local: existe apenas na sua máquina  
- Remota: existe no servidor (ex: GitHub)  
- Para compartilhar trabalho, é necessário fazer git push  

---

## Exemplo Prático: Feature Branch Workflow

    # 1. Criar e entrar na branch
    git checkout -b feature/login

    # 2. Fazer alterações no código
    git add .
    git commit -m "feat: adiciona tela de login"

    # 3. Enviar a branch para o repositório remoto
    git push origin feature/login

    # 4. Voltar para a branch principal
    git checkout main

    # 5. (Após merge) deletar a branch local
    git branch -d feature/login

---

## Conceitos Importantes

- Criar branch: permite desenvolver de forma isolada  
- Listar branches: visualizar locais e remotas  
- Navegar entre branches: alternar contexto de trabalho  
- Deletar branches: manter o repositório organizado  
- Local vs remoto: entender onde sua branch existe

## Estados do Working Directory

<!-- TODO: O que acontece quando você troca de branch? -->
<!-- Arquivos mudam, mudanças não commitadas, etc. -->

### Mudanças Não Commitadas

<!-- TODO: Como Git lida com mudanças não salvas ao trocar branch -->

## Merge: Unindo Branches

<!-- TODO: Conceito de merge -->

### O que é Merge?

<!-- TODO: Integrar mudanças de uma branch em outra -->

### Sintaxe Básica

```bash
# TODO: Como fazer merge
# git merge <nome-da-branch>
# Primeiro checkout para branch destino, depois merge
```

### Exemplo de Merge

```bash
# TODO: Exemplo completo
# 1. Criar feature branch
# 2. Fazer commits
# 3. Voltar para main
# 4. Fazer merge
```

## Tipos de Merge

### Fast-Forward Merge

<!-- TODO: O que é fast-forward -->
<!-- Quando acontece: quando não há commits divergentes -->

```
Antes:
main:    A---B
              \
feature:       C---D

Depois (fast-forward):
main:    A---B---C---D
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

### --ff (Fast-Forward)

<!-- TODO: Comportamento padrão -->

```bash
# TODO: Explicar opção --ff
```

### --no-ff (No Fast-Forward)

<!-- TODO: Forçar merge commit -->

```bash
# TODO: Quando usar --no-ff
```

### --squash

<!-- TODO: Comprimir commits -->

```bash
# TODO: Exemplo de squash merge
```

## Deletando Branches

```bash
# TODO: Como deletar branch local
# git branch -d <branch> (seguro)
# git branch -D <branch> (forçado)

# Deletar branch remota
# git push origin --delete <branch>
```

### Quando Deletar Branches

<!-- TODO: Após merge, branches antigas, etc. -->

## Visualizando o Grafo

```bash
# TODO: Ver histórico de branches
# git log --graph --oneline --all
```

## Branch Tracking

<!-- TODO: Conceito de tracking branches -->

### Upstream Branch

<!-- TODO: O que é upstream -->

```bash
# TODO: Configurar upstream
# git branch -u origin/<branch>
# git push -u origin <branch>
```

## Exemplos Práticos

### Exemplo 1: Feature Branch Workflow

<!-- TODO: Fluxo completo de desenvolvimento de feature -->

```bash
# 1. Criar branch
# 2. Desenvolver feature
# 3. Fazer merge
# 4. Deletar branch
```

### Exemplo 2: Merge de Múltiplas Features

<!-- TODO: Cenário com várias branches -->

### Exemplo 3: Desfazendo um Merge

<!-- TODO: Como reverter merge (git reset, git revert) -->

## Boas Práticas

<!-- TODO: Lista de boas práticas com branches -->

- <!-- Manter branches pequenas e focadas -->
- <!-- Commits frequentes -->
- <!-- Merge regularmente da main -->
- <!-- Deletar branches após merge -->
- <!-- Nomear branches descritivamente -->

## Workflows Comuns

### Feature Branch Workflow

<!-- TODO: Explicar esse workflow -->

### Gitflow

<!-- TODO: Introdução básica ao Gitflow -->
<!-- (Detalhado no capítulo 07) -->

## Conflitos de Merge

<!-- TODO: Introdução básica a conflitos -->
<!-- (Detalhado no capítulo 06 - Resolução de Conflitos) -->

### O que São

<!-- TODO: Quando ocorrem -->

### Exemplo Simples

<!-- TODO: Exemplo básico de conflito e resolução rápida -->

## git stash

<!-- TODO: Salvando mudanças temporariamente -->

### Quando Usar Stash

<!-- TODO: Cenários de uso -->

```bash
# TODO: Comandos stash básicos
# git stash
# git stash pop
# git stash list
```

## Comparando Branches

```bash
# TODO: Como ver diferenças entre branches
# git diff <branch1>..<branch2>
```

## Erros Comuns

### Erro 1: Merge na Branch Errada

<!-- TODO: Como evitar e como reverter -->

### Erro 2: Deletar Branch Sem Merge

<!-- TODO: Perda de trabalho, recuperação -->

### Erro 3: Não Atualizar a Main Antes de Criar Branch

<!-- TODO: Por que isso causa problemas -->

## Exercícios

<!-- TODO: Exercícios práticos -->

1. <!-- Criar branch, fazer commits, fazer merge -->
2. <!-- Experimentar fast-forward vs three-way merge -->
3. <!-- Visualizar grafo de branches -->
4. <!-- Deletar branches após merge -->

## Diagrama de Workflow

<!-- TODO: Diagrama visual do fluxo de trabalho com branches -->

## Recursos Adicionais

<!-- TODO: Links sobre branching e merging -->

- [Learn Git Branching](https://learngitbranching.js.org/)
- [Atlassian Git Branching Tutorial](https://www.atlassian.com/git/tutorials/using-branches)
- <!-- Mais recursos -->

## Resumo

<!-- TODO: Pontos principais sobre branches e merge -->

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->

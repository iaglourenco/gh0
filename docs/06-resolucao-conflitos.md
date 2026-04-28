# Resolução de Conflitos

<!-- Este arquivo ensina como identificar, entender e resolver conflitos de merge no Git -->

## 📋 Objetivos de Aprendizagem

<!-- TODO: Objetivos sobre resolução de conflitos -->

## 🎯 Introdução

<!-- TODO: Conflitos são normais e esperados! -->
<!-- Não tenha medo - todo desenvolvedor lida com eles -->

### Mensagem Importante

<!-- TODO: Encorajar alunos -->
<!-- Conflitos não são erros - são oportunidades de aprendizado -->

## O que São Conflitos de Merge?

<!-- TODO: Definição -->
<!-- Quando Git não consegue resolver automaticamente -->

### Por que Conflitos Acontecem?

<!-- TODO: Explicar causas -->

1. <!-- Duas pessoas editam a mesma linha -->
2. <!-- Mudanças em linhas próximas -->
3. <!-- Um deleta arquivo que outro modificou -->
4. <!-- Refatorações que afetam mesmo código -->

### Cenário Típico

<!-- TODO: Exemplo visual de como conflito surge -->

```
Pessoa A                     Pessoa B
   |                            |
   |---edita linha 10           |
   |                            |---edita linha 10
   |                            |
   |---commit                   |---commit
   |                            |
   |---push → main              |---push → CONFLITO!
```

## Identificando Conflitos

### Git Avisa

Quando um conflito acontece, o Git interrompe o merge e mostra uma mensagem informando que não conseguiu resolver tudo automaticamente. Isso normalmente ocorre quando duas branches alteraram a mesma parte de um arquivo.

Um exemplo comum de mensagem é:

```bash
Auto-merging docs/06-conflitos.md
CONFLICT (content): Merge conflict in docs/06-conflitos.md
Automatic merge failed; fix conflicts and then commit the result.
```

Essa mensagem indica que o Git tentou juntar as alterações, mas encontrou um conflito no arquivo `docs/06-conflitos.md`. A partir desse momento, o merge fica pausado até que o conflito seja resolvido.

### Comandos para Verificar

O comando mais importante para identificar arquivos em conflito é:

```bash
git status
```

Durante um conflito, ele mostra uma seção parecida com esta:

```bash
Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   docs/06-conflitos.md
```

O termo `both modified` significa que o mesmo arquivo foi modificado nas duas branches. Para visualizar as diferenças com mais detalhes, também é possível usar:

```bash
git diff
```

Esse comando ajuda a localizar exatamente onde estão os marcadores de conflito dentro do arquivo.

## Anatomia de um Conflito

### Marcadores de Conflito

Quando o Git não consegue decidir qual versão manter, ele adiciona marcadores diretamente no arquivo. Esses marcadores mostram o começo, a separação e o fim da área em conflito.

```markdown
<<<<<<< HEAD
Seu código ou texto atual
=======
Código ou texto vindo da outra branch
>>>>>>> nome-da-branch
```

Esses símbolos não fazem parte do conteúdo final. Eles são apenas uma indicação temporária para que a pessoa resolva manualmente o conflito.

### Entendendo Cada Parte

- `<<<<<<< HEAD`: marca o começo da seção em conflito. Tudo que aparece abaixo dessa linha, até o separador, representa a versão da branch atual.
- `=======`: separa as duas versões conflitantes. Acima dele está a versão atual; abaixo dele está a versão que veio da outra branch.
- `>>>>>>> nome-da-branch`: marca o fim da seção em conflito. O nome exibido indica de qual branch veio a alteração recebida.

Em outras palavras, o Git está dizendo: “existem duas versões possíveis para este trecho; escolha qual delas deve ficar”.

### Contexto: Quem Alterou e Quando

Antes de decidir qual versão manter, é importante entender o contexto das mudanças. Nem sempre a melhor solução é simplesmente escolher uma das versões. Às vezes, o ideal é combinar as duas.

Alguns comandos úteis para investigar o histórico são:

```bash
git log --oneline --graph
```

Mostra o histórico de commits de forma resumida e visual.

```bash
git blame docs/06-conflitos.md
```

Mostra quem alterou cada linha do arquivo e em qual commit.

```bash
git show <hash-do-commit>
```

Mostra os detalhes de um commit específico.

Esses comandos ajudam a entender quem fez a alteração, quando ela foi feita e qual era a intenção por trás da mudança.

### Exemplo Completo

Imagine que duas pessoas editaram a mesma introdução de um documento.

Antes da resolução, o arquivo pode ficar assim:

```markdown
## Introdução ao Git

<<<<<<< HEAD
Git é um sistema de controle de versão distribuído criado em 2005.
=======
Git é uma ferramenta de versionamento de código muito popular.
>>>>>>> feature/atualiza-intro
```

Nesse exemplo:

- a versão acima de `=======` veio da branch atual;
- a versão abaixo de `=======` veio da branch `feature/atualiza-intro`;
- os marcadores indicam exatamente onde o conflito começa, onde as versões se separam e onde o conflito termina.

Depois de analisar as duas versões, uma resolução possível seria combinar as informações:

```markdown
## Introdução ao Git

Git é um sistema de controle de versão distribuído, criado em 2005,
e muito popular para versionamento de código.
```

Depois da resolução, os marcadores `<<<<<<<`, `=======` e `>>>>>>>` devem ser removidos completamente.

## Resolvendo Conflitos Manualmente

### Passo a Passo

#### 1. Identificar Arquivos com Conflito

Use `git status` para ver quais arquivos estão em conflito:

```bash
git status
```

Exemplo de saída:

```bash
Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   docs/06-conflitos.md
```

Enquanto houver arquivos nessa seção, o conflito ainda não foi resolvido.

#### 2. Abrir Arquivo no Editor

Abra o arquivo indicado pelo `git status` no seu editor de código, como VS Code, Sublime Text ou outro editor de sua preferência.

No VS Code, por exemplo:

```bash
code docs/06-conflitos.md
```

#### 3. Analisar as Versões

Leia com atenção as duas partes do conflito:

```markdown
<<<<<<< HEAD
Versão da branch atual
=======
Versão da outra branch
>>>>>>> nome-da-branch
```

Antes de escolher, tente entender o objetivo de cada alteração. Uma versão pode corrigir um erro, enquanto a outra pode adicionar uma informação importante.

#### 4. Decidir o que Manter

Existem quatro opções principais:

- manter apenas sua versão;
- manter apenas a versão da outra branch;
- combinar as duas versões;
- escrever uma nova versão melhor que substitua ambas.

A melhor escolha depende do contexto da alteração.

#### 5. Editar o Arquivo

Depois de decidir, edite o arquivo deixando apenas o conteúdo final.

Exemplo de conflito:

```markdown
<<<<<<< HEAD
Git ajuda equipes a controlar versões de arquivos.
=======
Git permite acompanhar o histórico de alterações em um projeto.
>>>>>>> feature/melhora-descricao
```

Exemplo resolvido:

```markdown
Git ajuda equipes a controlar versões de arquivos e acompanhar o histórico de alterações em um projeto.
```

#### 6. Remover TODOS os Marcadores

Depois da edição, remova todos os marcadores adicionados pelo Git:

```txt
<<<<<<< HEAD
=======
>>>>>>> nome-da-branch
```

Se algum desses marcadores ficar no arquivo, o conflito não foi resolvido corretamente.

#### 7. Testar

Antes de finalizar, verifique se o arquivo ficou correto.

Em arquivos de documentação, leia o trecho alterado e confira se o Markdown continua bem formatado. Em arquivos de código, rode os testes ou execute o projeto.

#### 8. Marcar como Resolvido

Depois de resolver o arquivo, use `git add` para avisar ao Git que o conflito foi tratado:

```bash
git add docs/06-conflitos.md
```

Isso não é apenas “adicionar um arquivo”. Nesse contexto, o `git add` marca o conflito como resolvido.

#### 9. Completar o Merge

Depois que todos os conflitos forem resolvidos e adicionados, finalize o merge com um commit:

```bash
git commit
```

Também é possível escrever uma mensagem diretamente:

```bash
git commit -m "resolve: conflito em documentação de Git"
```

## Ferramentas para Resolver Conflitos

### Edição Manual

A forma mais direta de resolver um conflito é abrir o arquivo, analisar os marcadores, escolher o conteúdo final e remover os marcadores manualmente.

Essa abordagem é boa para conflitos simples e ajuda a entender exatamente o que está acontecendo.

### Ferramenta Visual

Editores como o VS Code mostram botões para facilitar a resolução, como:

- Accept Current Change;
- Accept Incoming Change;
- Accept Both Changes;
- Compare Changes.

Essas opções ajudam a escolher rapidamente entre a versão atual, a versão recebida ou a combinação das duas.

Mesmo usando uma ferramenta visual, é importante revisar o resultado final antes de fazer o commit.

### Abortar o Merge

Se a resolução ficou confusa ou se você percebeu que começou o merge errado, é possível abortar o processo e voltar ao estado anterior:

```bash
git merge --abort
```

Esse comando cancela o merge em andamento e restaura o repositório para o estado em que ele estava antes da tentativa de merge.

## Estratégias de Resolução

### Aceitar Completamente Uma Versão

```bash
# TODO: Usar theirs ou ours
# git checkout --ours arquivo.md
# git checkout --theirs arquivo.md
```

### Combinar Mudanças

<!-- TODO: Quando faz sentido mesclar -->

### Reescrever

<!-- TODO: Quando nenhuma versão está ideal -->

## Ferramentas de Merge

### Editor de Texto

<!-- TODO: Resolver manualmente -->

### VS Code

<!-- TODO: Interface visual do VS Code -->
<!-- Botões: Accept Current, Accept Incoming, Accept Both -->

### Git GUI Tools

#### GitKraken

<!-- TODO: Interface de merge do GitKraken -->

#### SourceTree

<!-- TODO: Interface de merge do SourceTree -->

### git mergetool

```bash
# TODO: Configurar e usar mergetool
```

### Configurando Merge Tool

```bash
# TODO: Configurar ferramenta padrão
# git config --global merge.tool vimdiff
# git config --global merge.tool meld
```

## Tipos de Conflitos

### Conflito de Conteúdo

<!-- TODO: Mais comum - mesmas linhas editadas -->

### Conflito de Renomeação

<!-- TODO: Arquivo renomeado em branches diferentes -->

### Conflito de Deleção

<!-- TODO: Um deleta, outro modifica -->

### Conflito de Estrutura

<!-- TODO: Mudanças em estrutura de pastas -->

## Prevenindo Conflitos

### Comunicação

<!-- TODO: Avisar equipe sobre mudanças grandes -->

### Pull/Fetch Frequente

<!-- TODO: Manter branch atualizada -->

```bash
# TODO: Atualizar frequentemente
# git fetch origin
# git merge origin/main
```

### Commits Pequenos e Frequentes

<!-- TODO: Menos mudanças = menos conflitos -->

### Dividir Trabalho

<!-- TODO: Trabalhar em partes diferentes do código -->

### Feature Flags

<!-- TODO: Evitar branches de longa duração -->

## Resolvendo Conflitos em Pull Requests

### Conflitos no GitHub

<!-- TODO: GitHub mostra conflitos em PRs -->

### Método 1: Resolver Localmente

```bash
# TODO: Passos para resolver localmente
# 1. git fetch upstream
# 2. git merge upstream/main
# 3. Resolver conflitos
# 4. git push
```

### Método 2: GitHub Interface

<!-- TODO: Resolver na interface web (se simples) -->

### Atualizar Branch com Main

```bash
# TODO: Manter PR atualizado
```

## Abortando um Merge

### Quando Abortar

<!-- TODO: Se você  fez algo errado ou quer recomeçar -->

### Como Abortar

```bash
# TODO: git merge --abort
```

### Efeito

<!-- TODO: Volta ao estado anterior ao merge -->

## Conflitos Complexos

### Múltiplos Arquivos

<!-- TODO: Resolver um por vez -->

### Conflitos Grandes

<!-- TODO: Estratégias para muitos conflitos -->

### Quando Pedir Ajuda

<!-- TODO: Não tenha medo de pedir ajuda -->
<!-- Professor, colegas, issue no projeto -->

## Exemplos Práticos

### Exemplo 1: Conflito Simples

<!-- TODO: Demonstração passo a passo -->

```
Cenário:
- Você edita README linha 5
- Colega edita README linha 5
- Colega faz merge primeiro
- Você tenta merge → conflito
```

<!-- TODO: Resolução completa -->

### Exemplo 2: Conflito em Múltiplos Arquivos

<!-- TODO: Como organizar a resolução -->

### Exemplo 3: Conflito de Código

<!-- TODO: Exemplo com código (não apenas docs) -->

## Dicas e Truques

### Usar Git Log para Contexto

```bash
# TODO: Ver histórico para entender mudanças
# git log --oneline --graph
```

### Git Diff para Ver Mudanças

```bash
# TODO: Comparar versões
```

### Git Blame para Rastrear

```bash
# TODO: Ver quem mudou o quê
# git blame arquivo.md
```

### Comunicar com o Autor

<!-- TODO: Perguntar intenção das mudanças -->

## Fluxo de Trabalho Anti-Conflito

<!-- TODO: Workflow que minimiza conflitos -->

1. <!-- Fetch regularmente -->
2. <!-- Merge main na sua branch frequentemente -->
3. <!-- PRs pequenos -->
4. <!-- Comunicação -->
5. <!-- Feature flags -->

## Erros Comuns

### Erro 1: Não Remover Marcadores

<!-- TODO: Deixar <<<<< no código -->

### Erro 2: Marcar como Resolvido Sem Testar

<!-- TODO: Resolver mas código quebrado -->

### Erro 3: Aceitar Mudanças Sem Entender

<!-- TODO: Importância de entender AMBAS as versões -->

### Erro 4: Fazer Force Push

<!-- TODO: Perigo em branches compartilhadas -->

## Conflitos em Diferentes Arquivos

### Markdown

<!-- TODO: Conflitos em documentação -->

### Código

<!-- TODO: Conflitos em código fonte -->

### JSON/YAML

<!-- TODO: Arquivos de configuração -->

### Binários

<!-- TODO: Imagens, PDFs - escolher uma versão -->

## Exercícios

<!-- TODO: Exercícios práticos com conflitos -->

1. <!-- Criar conflito intencional e resolver -->
2. <!-- Resolver conflito simulado -->
3. <!-- Usar mergetool -->
4. <!-- Resolver conflito em PR -->

## Checklist de Resolução

<!-- TODO: Passo a passo para sempre seguir -->

- [ ] Identificar arquivos em conflito
- [ ] Entender ambas as versões
- [ ] Decidir abordagem
- [ ] Editar arquivo
- [ ] Remover marcadores
- [ ] Testar mudanças
- [ ] git add
- [ ] git commit
- [ ] Verificar que tudo funciona

## Recursos Adicionais

<!-- TODO: Links sobre resolução de conflitos -->

- [Git Merge Conflicts](https://git-scm.com/docs/git-merge#_how_conflicts_are_presented)
- [GitHub Resolving Conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts)
- <!-- Mais recursos -->

## Resumo

<!-- TODO: Pontos principais sobre resolução de conflitos -->

### Lembre-se

- Conflitos são normais
- Não tenha medo
- Entenda ambas as versões
- Teste antes de finalizar
- Peça ajuda se precisar

---

## 👥 Contribuidores

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir:
- [@seu-usuario](https://github.com/seu-usuario) - Seção X
-->
- [@joaomarafiotti](https://github.com/joaomarafiotti) - Marcadores de conflito

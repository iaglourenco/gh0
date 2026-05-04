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
   Um conflito de merge ocorre quando o Git, apesar de sua inteligência algorítmica, encontra uma ambiguidade que não pode ser resolvida automaticamente. Isso acontece tipicamente quando duas ramificações (branches) distintas alteram a mesma linha de um arquivo de formas diferentes, ou quando uma branch deleta um arquivo que outra modificou. 

<!-- Quando Git não consegue resolver automaticamente -->
   Tecnicamente, o Git falha ao tentar aplicar um 'Three-way merge', pois as mudanças são divergentes a partir do ancestral comum, exigindo que a inteligência humana intervenha para decidir qual estado final preserva a integridade lógica do sistema.

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
// <<<<<<< HEAD
Seu código ou texto atual
// =======
Código ou texto vindo da outra branch
// >>>>>>> nome-da-branch
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
Observação: esse exemplo assume que a branch principal se chama "main".

// <<<<<<< joao-marafiotti/marcadores-conflito
Imagine que duas pessoas editaram a mesma introdução de um documento.

Antes da resolução, o arquivo pode ficar assim:
// =======
Crie um repositório com `git init`.
// >>>>>>> main

Crie um arquivo exemplo.py (isso vai variar de acordo com o sistema operacional)

#### Primeiro commit

Crie o primeiro commit

```bash
git add .
git commit -m "criação do arquivo"
git log --graph
```
O resultado do `git log` deve ser dessa forma(mudando o autor):
![primeiro commit](assets/exemplo-conflito-primeiro-commit.png)

#### Criando Commit em Outra Branch

Crie outra branch

```bash
git switch -c teste
git log --graph
```

Deve ter o mesmo commit que a main(ou master).

Insira o código em exemplo.py:

```python
def calcular_media(valores):
    total = 0
    for v in valores:
        total += v
    
    print("Processando valores...")
    media = total / len(valores)
    
    # Linha 10 (diferença aqui)
    resultado = f"Média calculada: {media}"
    
    return resultado


dados = [10, 20, 30]
print(calcular_media(dados))
```

Crie um novo commit:


```bash
git add .
git commit -m "codigo escrito com mensagem 'Média calculada'"
git log --graph
```

![segundo commit teste](assets/exemplo-conflito-commit2-teste.png)

#### Criando o Segundo Commit em main

Volte para a main

```bash
git switch main
```

Troque o código de exemplo.py para esse (mesmo código com uma diferença na linha 10):

```python
def calcular_media(valores):
    total = 0
    for v in valores:
        total += v
    
    print("Processando valores...")
    media = total / len(valores)
    
    # Linha 10 (diferença aqui)
    resultado = f"Valor médio final: {media}"
    
    return resultado


dados = [10, 20, 30]
print(calcular_media(dados))
```

Crie um novo commit:

```bash
git add .
git commit -m "codigo escrito com mensagem 'Valor médio final'"
git log --graph
```

![segundo commit main](assets/exemplo-conflito-commit2-main.png)

#### Fazendo o Merge e Resolvendo o Conflito

Tenha certeza de que está na main.

```bash
git switch main
git merge teste
```

Vai aparecer a mensagem de conflito:

![mensagem de conflito](assets/exemplo-conflito-mensagem-de-conflito.png)

e o arquivo terá na linha 10 onde houve conflito.

```python
// <<<<<<< HEAD
    resultado = f"Média calculada: {media}"
// =======
    resultado = f"Valor médio final: {media}"
// >>>>>>> teste
```

// <<<<<<< joao-marafiotti/marcadores-conflito
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
// =======
troque para (não esquecendo a identação):

```python
    resultado = f"Média: {media}"
```

e faça um commit para resolver o conflito:

```bash
git add .
git commit -m "conflito resolvido"

git log --graph --oneline
```

![commits finais](assets/exemplo-conflito-final.png)

Se tentar fazer um `git merge teste`, irá retornar "Already up to date".
// >>>>>>> main

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
// <<<<<<< HEAD
Versão da branch atual
// =======
Versão da outra branch
// >>>>>>> nome-da-branch
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
// <<<<<<< HEAD
Git ajuda equipes a controlar versões de arquivos.
// =======
Git permite acompanhar o histórico de alterações em um projeto.
// >>>>>>> feature/melhora-descricao
```

Exemplo resolvido:

```markdown
Git ajuda equipes a controlar versões de arquivos e acompanhar o histórico de alterações em um projeto.
```

#### 6. Remover TODOS os Marcadores

Depois da edição, remova todos os marcadores adicionados pelo Git:

```txt
// <<<<<<< HEAD
// =======
// >>>>>>> nome-da-branch
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

#### Para priorizar a nossa versão em conflitos automáticos
```bash
# git merge -Xours nome-da-branch
```

#### Para priorizar a versão que está vindo de fora
```bash
# git merge -Xtheirs nome-da-branch
```
   Em cenários onde a escala de mudanças é massiva, a resolução manual linha a linha torna-se inviável. As estratégias de estratégia de recursão permitem automatizar essa decisão. A opção -Xours orienta o Git a favorecer sistematicamente a versão da branch atual (aquela em que você está), sendo ideal para proteger configurações locais ou códigos core que não podem ser alterados. Já a -Xtheirs prioriza a branch que está sendo integrada, sendo a escolha correta quando você está absorvendo uma 'hotfix' ou uma atualização crítica de terceiros que deve sobrescrever o estado atual.

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

   A resolução de conflitos via terminal em arquivos complexos (como códigos ou grandes datasets JSON) é propensa a erros. O uso do git difftool atua na fase de pré-análise, permitindo uma inspeção visual comparativa antes de qualquer alteração. Uma vez identificada a colisão, o git mergetool invoca uma interface gráfica (GUI) que segmenta o arquivo em três painéis: a base comum, a versão local e a versão remota. Essa visualização tripartida é fundamental para que o desenvolvedor possa compor uma solução híbrida que aproveite o melhor de ambas as versões.

### VS Code

<!-- TODO: Interface visual do VS Code -->
<!-- Botões: Accept Current, Accept Incoming, Accept Both -->

### Git GUI Tools

#### GitKraken

<!-- TODO: Interface de merge do GitKraken -->

#### SourceTree

<!-- TODO: Interface de merge do SourceTree -->

### git mergetool

#### O mergetool abre uma interface visual para resolver conflitos
```bash
# git mergetool
```

#### O difftool permite comparar as versões antes de decidir
```bash
# git difftool
```

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

Embora ferramentas ajudem a resolver, a melhor prática é a prevenção através de fluxos de trabalho inteligentes. Commits pequenos e atômicos, aliados a Pull/Fetch frequentes, garantem que a divergência entre a sua branch e a main seja mínima. Em sistemas de missão crítica, como os desenvolvidos em eletrônica aeroespacial, a fragmentação de tarefas em arquivos distintos e o uso de interfaces bem definidas são as defesas primárias contra colisões de código massivas.

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

A resolução de conflitos pode se tornar excessivamente complexa se houver muitos arquivos alterados simultaneamente. Nestes casos, o comando git merge --abort funciona como um 'botão de pânico'. Ele interrompe o processo de integração e restaura o repositório ao estado exato em que estava antes do comando de merge ser disparado. É uma prática recomendada usar o abort sempre que houver dúvida sobre a integridade da resolução manual, permitindo ao desenvolvedor reavaliar a estratégia de integração sem deixar o repositório em um estado 'sujo' ou quebrado.

### Retorna ao estado anterior caso o merge esteja muito complexo
```bash
# TODO: git merge --abort
```

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

#### Use o git blame para identificar quem editou a linha e converse com o autor para entender a intenção do código original.

   A resolução técnica de um conflito é apenas metade do trabalho. A outra metade é política/social. O comando git blame deve ser usado como uma ferramenta de rastreabilidade para identificar o autor da mudança divergente. Antes de concluir o merge, uma breve consulta ao autor evita a deleção de lógicas intencionais (edge cases) que podem não ser óbvias à primeira vista.

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
<!-- Adicione seu nome quando contribuir: Filipe Alves de Sousa
- [@seu-usuario](https://github.com/filipe19) - Estratégias e Ferramentas de Resolução (#46)
-->
- [@joaomarafiotti](https://github.com/joaomarafiotti) - Marcadores de conflito

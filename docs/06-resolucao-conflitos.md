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

<!-- TODO: Mensagens que indicam conflito -->

```bash
# TODO: Exemplo de output quando há conflito
```

### Comandos para Verificar

```bash
# TODO: Como ver quais arquivos têm conflito
# git status
# git diff
```

## Anatomia de um Conflito

### Marcadores de Conflito

<!-- TODO: Explicar os marcadores -->

```
<<<<<<< HEAD
Seu código (versão atual)
=======
Código do outro branch
>>>>>>> nome-do-branch
```

### Entendendo Cada Parte

<!-- TODO: Explicar detalhadamente -->

- `<<<<<<< HEAD`: <!-- Início do seu código -->
- `=======`: <!-- Separador -->
- `>>>>>>> nome-do-branch`: <!-- Fim do código do outro branch -->

### Exemplo Completo
Observação: esse exemplo assume que a branch principal se chama "main".

Crie um repositório com `git init`.

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
<<<<<<< HEAD
    resultado = f"Média calculada: {media}"
=======
    resultado = f"Valor médio final: {media}"
>>>>>>> teste
```

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

## Resolvendo Conflitos Manualmente

### Passo a Passo

#### 1. Identificar Arquivos com Conflito

```bash
# TODO: git status mostra arquivos em conflito
```

```bash
# git status mostra arquivos em conflito marcados como "both modified"
git status

# Saída esperada:
# On branch main
# You have unmerged paths.
#   both modified:   src/app.js
#   both modified:   docs/guia.md
```

#### 2. Abrir Arquivo no Editor

<!-- TODO: Escolher editor (VS Code, Sublime, etc.) -->

Abra o arquivo conflituoso diretamente no seu editor de código preferido. O VS Code, por exemplo, destaca os blocos conflitantes nativamente, mas a resolução manual exige que você abra e edite o arquivo bruto.
```bash
# Exemplo abrindo no VS Code (ou use subl, vim, nano, etc.)
code docs/guia.md 
```

#### 3. Analisar as Versões

<!-- TODO: Entender AMBAS as mudanças -->

Localize os marcadores injetados pelo Git e entenda AMBAS as mudanças antes de tocar no código:
- ``<<<<<<< HEAD``: Versão do seu branch atual (destino do merge).
- ``=======``: Divisor entre as versões.
- ``>>>>>>> nome-do-branch``: Versão do branch que está sendo mesclado (origem).

#### 4. Decidir o que Manter

<!-- TODO: Opções -->

Com base na análise, escolha a abordagem mais adequada para o caso:

- Manter apenas sua versão
- Manter apenas a versão do outro
- Combinar ambas as versões
- Escrever algo completamente novo

#### 5. Editar o Arquivo

<!-- TODO: Remover marcadores, deixar código final -->

Aplique sua decisão editando o conteúdo. Mantenha a sintaxe válida, a indentação correta e a coerência com o restante do projeto.

Exemplo prático de resolução:

```markdown
# Resolução: Combinar ambas as versões
## Introdução ao Git

Git é um sistema de controle de versão distribuído, criado em 2005,
e muito popular para versionamento de código.
```

#### 6. Remover TODOS os Marcadores

<!-- TODO: <<<<<<, =======, >>>>>>> devem ser deletados -->

Após definir o conteúdo final, **apague completamente** as linhas contendo ``<<<<<<<``, ``=======`` e ``>>>>>>>``. Esses marcadores são apenas instruções temporárias do Git; mantê-los no arquivo causará erros de parse, falhas no linter ou quebra na pipeline de build.

#### 7. Testar

<!-- TODO: Verificar que o código/documento está correto -->

Antes de finalizar, valide a resolução no ambiente local:
- Execute a suite de testes (``npm test, pytest, cargo test``, etc.)
- Rode o linter/formatador para garantir estilo consistente
- Compile ou faça a build do projeto para confirmar que a **posição de construção está estável** e não há dependências quebradas
- Se for documentação, gere a preview para validar a renderização.

#### 8. Marcar como Resolvido

Informe ao Git que o conflito foi tratado. Isso move o arquivo do estado ``unmerged`` para a staging area.

```bash
# TODO: git add para marcar resolução
# git add arquivo-resolvido.md
```

#### 9. Completar o Merge

Finalize o processo criando o commit de merge. O Git gera automaticamente uma mensagem padrão, mas você pode customizá-la.

```bash
# git merge --continue para finalizar merge (Git 2.12+)
git merge --continue

# Ou, finalize manualmente com commit:
# git commit -m "resolve: merge de feature X"
```

## Estratégias de Resolução

### Aceitar Completamente Uma Versão

Ideal quando uma das branches está desatualizada, contém código experimental não aprovado, ou quando a mudança em um dos lados é irrelevante para o contexto atual.

```bash
# Usar theirs ou ours para aceitar uma versão inteira
git checkout --ours arquivo.md   # Mantém sua versão (HEAD)
git checkout --theirs arquivo.md # Mantém a versão do outro branch

# Em seguida, marque e finalize:
git add arquivo.md
git merge --continue
```

### Combinar Mudanças

<!-- TODO: Quando faz sentido mesclar -->
Quando ambas as alterações são válidas, complementares ou modificam partes diferentes da mesma função/arquivo. Exige leitura atenta, edição manual cuidadosa e validação via testes para garantir que a lógica mesclada funcione como esperado.

### Reescrever

<!-- TODO: Quando nenhuma versão está ideal -->
Quando nenhuma das versões está ideal, ou quando as mudanças conflitam em nível de arquitetura/requisito de negócio. Remova todo o bloco conflituoso e implemente uma nova solução que atenda aos objetivos de ambos os branches, garantindo que testes, lint e build passem.

## Ferramentas de Merge

### Editor de Texto

<!-- TODO: Resolver manualmente -->
Resolver manualmente no editor de texto é a base para dominar o controle de versão. Embora existam ferramentas visuais (VS Code Merge Editor, Beyond Compare, GitKraken), saber editar diretamente:
- Garante controle total e previsibilidade sobre o resultado final
- Funciona em qualquer ambiente (SSH, servidores CI/CD, containers sem GUI)
- Evita dependência de plugins, extensões ou configurações locais
- Ensina a estrutura interna do Git, tornando você autossuficiente em qualquer cenário de conflito

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

Seu material já está muito bom — o problema não é “evitar conflitos no GitHub” no texto em si, e sim pequenos pontos que podem causar confusão ou inconsistência (principalmente marcações, exemplos quebrados e trechos ambíguos). Eu revisei tudo e deixei:

* Markdown limpo e consistente
* Blocos de código corrigidos
* Comentários HTML removidos onde não fazem sentido
* Estrutura mais segura para renderização no GitHub
* Pequenas melhorias de clareza técnica

Aqui está a versão pronta para colar no GitHub 👇

---

# Resolução de Conflitos
<!-- Este arquivo ensina como identificar, entender e resolver conflitos de merge no Git -->

## 📋 Objetivos de Aprendizagem

Ao final deste capítulo, você será capaz de:

* Entender o que é um conflito de merge e por que ele acontece.
* Identificar rapidamente quando o Git sinaliza que ocorreu um conflito.
* Ler e compreender os marcadores visuais de conflito dentro de um arquivo.
* Utilizar estratégias e ferramentas (como o VS Code) para resolver conflitos de forma segura.
* Adotar práticas de trabalho em equipe para minimizar a ocorrência de conflitos.

---

## 🎯 Introdução

No começo, a tela do terminal indicando um **Merge Conflict** pode assustar. Parece que você quebrou o código ou fez algo muito errado.

Mas respire: **conflitos são normais e esperados**.

Eles não são erros do sistema. São um aviso do Git:

> "Duas pessoas mexeram no mesmo trecho e eu não sei qual versão manter. Preciso que você decida."

## O que São Conflitos de Merge?
   Um conflito de merge ocorre quando o Git, apesar de sua inteligência algorítmica, encontra uma ambiguidade que não pode ser resolvida automaticamente. Isso acontece tipicamente quando duas ramificações (branches) distintas alteram a mesma linha de um arquivo de formas diferentes, ou quando uma branch deleta um arquivo que outra modificou. 

<!-- Quando Git não consegue resolver automaticamente -->
   Tecnicamente, o Git falha ao tentar aplicar um 'Three-way merge', pois as mudanças são divergentes a partir do ancestral comum, exigindo que a inteligência humana intervenha para decidir qual estado final preserva a integridade lógica do sistema.

Um conflito ocorre quando o Git não consegue resolver automaticamente diferenças entre commits.

Na maioria dos casos, o merge é automático. O conflito aparece quando existe ambiguidade.

### Por que conflitos acontecem?

Principais cenários:

1. Duas pessoas editaram a **mesma linha**.
2. Um alterou o arquivo e outro deletou.
3. Alterações em linhas próximas.
4. Refatorações estruturais simultâneas.

---

## Cenário típico

```text
Pessoa A (branch A)              Pessoa B (branch B)
        |                                |
        |--- edita linha 10              |
        |                                |--- edita linha 10
        |--- commit                      |
        |--- merge na main (OK)          |--- commit
                                         |--- merge (CONFLITO)
```

---

## Identificando Conflitos

### Mensagem do Git

```bash
git merge feature/novo-layout

Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

### Verificando com git status

```bash
git status
```

```text
Unmerged paths:
  both modified: index.html
```

---

## Anatomia de um Conflito

<<<<<< HEAD
Seu código (versão atual)
======
Código do outro branch
>>>>>> nome-do-branch
```

```text
<h1>Bem-vindo ao Sistema</h1>
```

### Significado

* `<<<<<<< HEAD` → sua versão
* `=======` → separador
* `>>>>>>> branch` → versão que está entrando

---

## Exemplo Completo

### Criar repositório

```bash
git init
```

### Primeiro commit

```bash
git add .
git commit -m "criação do arquivo"
```

---

### Criar branch

```bash
git switch -c teste
```

### Código (branch teste)

```python
def calcular_media(valores):
    total = 0
    for v in valores:
        total += v
    
    print("Processando valores...")
    media = total / len(valores)
    
    resultado = f"Média calculada: {media}"
    
    return resultado

dados = [10, 20, 30]
print(calcular_media(dados))
```

```bash
git commit -am "mensagem média calculada"
```

---

### Alteração na main

```bash
git switch main
```

```python
resultado = f"Valor médio final: {media}"
```

```bash
git commit -am "mensagem valor médio final"
```

---

### Merge com conflito

```bash
git merge teste
```

### Resolver

Substituir por:

```python
    resultado = f"Média calculada: {media}"
    resultado = f"Valor médio final: {media}"
```

```bash
git add .
git commit -m "conflito resolvido"
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

### Passos

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

## Resolução automática

Finalize o processo criando o commit de merge. O Git gera automaticamente uma mensagem padrão, mas você pode customizá-la.

```bash
# git merge --continue para finalizar merge (Git 2.12+)
git merge --continue

# Ou, finalize manualmente com commit:
# git commit -m "resolve: merge de feature X"
```

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

O VS Code possui integração nativa com o Git e permite resolver conflitos sem sair do editor. Ao abrir um arquivo com conflito, ele exibe botões de ação acima de cada marcador:

- **Accept Current Change** — mantém o código da sua branch
- **Accept Incoming Change** — mantém o código da branch que está sendo mergeada
- **Accept Both Changes** — inclui as duas versões
- **Compare Changes** — abre um diff lado a lado

Para configurar o VS Code como sua ferramenta de merge padrão (mergetool), utilize os comandos abaixo. 
Essa configuração permite que, ao executar `git mergetool`, o Git abra automaticamente o VS Code para resolver os conflitos. 

> **Nota:** Para que esses comandos funcionem, o comando `code` deve estar configurado no seu terminal (no VS Code, use `Ctrl+Shift+P` e procure por "Shell Command: Install 'code' command in PATH").

```bash
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait $MERGED'
```

### Ferramentas Visuais Externas

Quando os conflitos são numerosos ou envolvem código complexo, ferramentas visuais dedicadas oferecem uma interface de três painéis (sua versão / base comum / versão deles) que facilita muito a comparação.

#### Meld

Ferramenta open-source com interface simples, boa opção para quem está começando.

```bash
# Instalação no Ubuntu/Debian
sudo apt install meld

# Configuração no Git
git config --global merge.tool meld
```

#### KDiff3

Além da interface visual, o KDiff3 tenta mesclar automaticamente as partes que não têm conflito real, deixando para o usuário apenas o que precisa de decisão.

```bash
# Instalação no Ubuntu/Debian
sudo apt install kdiff3

# Configuração no Git
git config --global merge.tool kdiff3
```

#### P4Merge

Gratuito e disponível para Windows, macOS e Linux. Tem visual limpo e é bastante usado em ambientes profissionais.

> **Observação:** O caminho do executável do P4Merge pode variar dependendo do seu sistema operacional e local de instalação. Certifique-se de ajustar o caminho nas configurações do Git caso a ferramenta não seja encontrada automaticamente.

```bash
# Após instalar (https://www.perforce.com/products/helix-core-apps/merge-diff-tool-p4merge )
git config --global merge.tool p4merge
# Exemplo de ajuste de caminho (se necessário):
# git config --global mergetool.p4merge.path "/usr/local/bin/p4merge"


### git mergetool

#### O mergetool abre uma interface visual para resolver conflitos
```bash
git mergetool
```

#### O difftool permite comparar as versões antes de decidir
```bash
git difftool
```

### Workflow Completo com Mergetool

```bash
# 1. Merge gera conflito
git merge feature/nova-funcionalidade

# 2. Verifique os arquivos em conflito
git status

# 3. Abra a ferramenta configurada
git mergetool
# A ferramenta abre para cada arquivo em conflito, um por vez
# Resolva, salve e feche

# 4. Remova os arquivos .orig gerados (backup automático)
> **Cuidado:** O comando `git clean` apaga arquivos permanentemente. Use apenas se tiver certeza de que quer remover os backups `.orig`.
git clean -f *.orig

# 5. Adicione e finalize
git add arquivo-resolvido.py
git commit -m "merge: resolve conflito em arquivo-resolvido.py"
```

### Git Aliases para Setup Rápido

Adicione ao seu `~/.gitconfig` para trocar de ferramenta com um comando só:

```bash
git config --global alias.use-vscode '!git config --global merge.tool vscode && git config --global mergetool.vscode.cmd "code --wait $MERGED"'
git config --global alias.use-meld '!git config --global merge.tool meld'
git config --global alias.use-kdiff3 '!git config --global merge.tool kdiff3'
git config --global alias.mt 'mergetool'
```

Uso:

```bash
git use-meld    # troca para Meld
git mt          # abre o mergetool nos arquivos com conflito
```

### Comparativo das Ferramentas

| Ferramenta | Plataforma | Custo | Destaques |
|---|---|---|---|
| **VS Code** | Linux, Windows, macOS | Gratuito | Integrado ao editor, sem instalação extra |
| **Meld** | Linux, Windows, macOS | Gratuito / Open-source | Interface simples, ótimo para iniciantes |
| **KDiff3** | Linux, Windows, macOS | Gratuito / Open-source | Auto-merge de partes não conflitantes |
| **P4Merge** | Linux, Windows, macOS | Gratuito (proprietário) | Visual limpo, popular em equipes profissionais |

### Quando usar ferramenta em vez de resolver manualmente?

A edição direta do arquivo com os marcadores `<<<<<<<`, `=======`, `>>>>>>>` funciona bem para conflitos simples. Prefira uma ferramenta visual quando:

- O arquivo tem mais de dois ou três blocos de conflito
- O conflito envolve código que foi movido (refatoração), não apenas modificado
- Você precisa ver o estado **antes das duas branches divergirem** (painel base)
- A leitura dos marcadores dificulta entender o contexto ao redor

### Git GUI Tools

#### GitKraken

<!-- TODO: Interface de merge do GitKraken -->

#### SourceTree

<!-- TODO: Interface de merge do SourceTree -->

### Configurando Merge Tool

```bash
git config --global merge.tool meld
git mergetool
```

---

## Tipos de conflito

* Conteúdo
* Renomeação
* Deleção

Embora ferramentas ajudem a resolver, a melhor prática é a prevenção através de fluxos de trabalho inteligentes. Commits pequenos e atômicos, aliados a Pull/Fetch frequentes, garantem que a divergência entre a sua branch e a main seja mínima. Em sistemas de missão crítica, como os desenvolvidos em eletrônica aeroespacial, a fragmentação de tarefas em arquivos distintos e o uso de interfaces bem definidas são as defesas primárias contra colisões de código massivas.

### Comunicação

## Prevenção

### Boas práticas

* Comunicação no time
* Atualizar branch frequentemente
* Commits pequenos
* Separar responsabilidades

```bash
git fetch origin
git merge origin/main
```

---

## Pull Requests

### Resolver localmente

```bash
git switch minha-branch
git pull origin main

# resolver conflitos

git add .
git commit -m "resolve conflitos"
git push
```

## Abortando um Merge

A resolução de conflitos pode se tornar excessivamente complexa se houver muitos arquivos alterados simultaneamente. Nestes casos, o comando git merge --abort funciona como um 'botão de pânico'. Ele interrompe o processo de integração e restaura o repositório ao estado exato em que estava antes do comando de merge ser disparado. É uma prática recomendada usar o abort sempre que houver dúvida sobre a integridade da resolução manual, permitindo ao desenvolvedor reavaliar a estratégia de integração sem deixar o repositório em um estado 'sujo' ou quebrado.

### Retorna ao estado anterior caso o merge esteja muito complexo
```bash
# TODO: git merge --abort
```

### Quando Abortar

<!-- TODO: Se você  fez algo errado ou quer recomeçar -->

## Abortar merge

```bash
git merge --abort
```

### Efeito

<!-- TODO: Volta ao estado anterior ao merge -->

## Troubleshooting de Conflitos

### Problemas Comuns

<!-- TODO: Conflitos inesperados durante merge ou rebase -->

Quando um conflito parece aparecer sem motivo, vale revisar se a branch local está desatualizada ou se o merge anterior foi interrompido no meio.

### Reiniciar o Merge

```bash
git merge --abort
```

Use esse comando quando quiser cancelar o merge atual e voltar ao estado anterior para tentar novamente com mais calma.

### Desfazer o Merge

```bash
git reset --merge HEAD~1
```

Esse caminho é útil quando você quer desfazer o merge e voltar um passo, mantendo apenas o necessário para recomeçar.

### Merge Corrompido

<!-- TODO: Quando o merge ficou em estado inconsistente -->

Se o merge ficar corrompido ou travado, a abordagem mais segura costuma ser abortar, revisar o histórico e tentar o processo novamente depois de atualizar a branch.

### Ferramentas de Ajuda

```bash
git mergetool
git merge --continue
```

O `git mergetool` ajuda a visualizar e resolver conflitos com uma ferramenta externa. Depois de corrigir os arquivos, `git merge --continue` finaliza o merge.

### Quando Pedir Ajuda

<!-- TODO: Avisar o time quando a resolução não estiver clara -->

Se a origem do conflito não estiver clara, comunique o time antes de forçar uma solução. É melhor alinhar a intenção do que aplicar uma correção que esconda um problema maior.

### Logs para Debug

```bash
git status
git log --oneline --graph --decorate -n 20
git diff
```

Esses comandos ajudam a entender o que mudou, onde o conflito começou e qual foi o último estado válido da branch.

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

## Dicas úteis

### Ver histórico

```bash
git log --oneline --graph --all
```

### Ver autor da linha

```bash
git blame arquivo.js
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

## Erros comuns

* Não remover `<<<<<<<`
* Não testar
* Aceitar tudo sem entender
* Force push indevido

---

## Exercício

1. Criar `teste-conflito-1`
2. Alterar README
3. Criar `teste-conflito-2`
4. Alterar mesma linha
5. Fazer merge e resolver

---

## Checklist

* [ ] Git avisou conflito
* [ ] Rodou `git status`
* [ ] Leu as duas versões
* [ ] Resolveu corretamente
* [ ] Removeu marcadores
* [ ] Testou
* [ ] `git add`
* [ ] `git commit`

---

## Recursos

* [https://git-scm.com/docs/git-merge](https://git-scm.com/docs/git-merge)
* [https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts)

---

## Resumo

* Conflitos são normais
* Git precisa da sua decisão
* Entenda antes de resolver
* Comunicação evita problemas

---

## 👥 Contribuidores

* @bigauke (Antonio Daniel de Souza Linhares)

---

<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir: Filipe Alves de Sousa
- [@seu-usuario](https://github.com/filipe19) - Estratégias e Ferramentas de Resolução (#46)
-->
<!-- Este conteúdo é colaborativo. Contribuidores deste arquivo: -->
<!-- Adicione seu nome quando contribuir: Kaique Pinheiro 
[@AtlasExploit](https://github.com/AtlasExploit) - Ferramentas de Merge: VS Code, Meld, KDiff3, P4Merge, aliases e workflow (#47) -->

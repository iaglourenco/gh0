# Resolução de Conflitos

<!-- Este arquivo ensina como identificar, entender e resolver conflitos de merge no Git -->

## 📋 Objetivos de Aprendizagem

Ao final deste capítulo, você será capaz de:
- Entender o que é um conflito de merge e por que ele acontece.
- Identificar rapidamente quando o Git sinaliza que ocorreu um conflito.
- Ler e compreender os marcadores visuais de conflito dentro de um arquivo.
- Utilizar estratégias e ferramentas (como o VS Code) para resolver conflitos de forma segura.
- Adotar práticas de trabalho em equipe para minimizar a ocorrência de conflitos.

## 🎯 Introdução

No começo, a tela do terminal indicando um "Merge Conflict" pode assustar. Parece que você quebrou o código ou fez algo de muito errado. Mas respire fundo: **conflitos são normais e esperados!** 

Não tenha medo deles. Todo desenvolvedor, do júnior ao sênior, lida com conflitos regularmente. Eles não são "erros" do sistema, mas sim uma rede de segurança do Git avisando: *"Ei, duas pessoas mexeram no mesmo lugar e eu não sou inteligente o suficiente para saber qual versão é a correta. Preciso que um humano decida."*

## O que São Conflitos de Merge?

Um conflito de merge ocorre quando o Git é incapaz de resolver automaticamente as diferenças de código entre dois commits concorrentes. Na maioria das vezes, o Git faz o merge de alterações de forma perfeitamente automática. O conflito só surge quando a alteração é ambígua.

### Por que Conflitos Acontecem?

O Git pedirá sua ajuda principalmente nestes cenários:
1. Duas pessoas editaram a **mesma linha** do mesmo arquivo em branches diferentes.
2. Uma pessoa alterou um arquivo, enquanto a outra pessoa deletou esse exato mesmo arquivo.
3. Ocorreram mudanças em linhas imediatamente adjacentes que o Git não consegue mesclar com segurança.
4. Refatorações estruturais (como mover uma pasta inteira) enquanto outra pessoa editava um arquivo dentro dessa pasta.

### Cenário Típico

Veja como um conflito nasce no dia a dia de uma equipe:

```text
Pessoa A (na branch A)               Pessoa B (na branch B)
         |                                     |
         |--- edita a linha 10 do index.html   |
         |                                     |--- edita a linha 10 do index.html
         |--- faz o commit                     |
         |--- faz o merge na main (Sucesso!)   |--- faz o commit
                                               |--- tenta fazer o merge na main (CONFLITO!)
```

## Identificando Conflitos

### O Git Avisa

Quando você tenta fazer um merge (ou dar um `git pull`) e há um conflito, o Git interrompe a operação imediatamente e exibe uma mensagem clara:

```bash
$ git merge feature/novo-layout
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

### Comandos para Verificar

Se você se perder no meio de um processo, o `git status` é o seu melhor amigo. Ele listará exatamente quais arquivos precisam da sua atenção.

```bash
$ git status
On branch main
You have unmerged paths.
  (fix conflicts and run "git commit")

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   index.html
```

## Anatomia de um Conflito

### Marcadores de Conflito

Quando você abre o arquivo conflitante (`index.html` no nosso exemplo) no seu editor de código, você verá que o Git modificou o arquivo e injetou "marcadores visuais" estranhos.

```text
<<<<<<< HEAD
<h1>Bem-vindo ao Meu Site!</h1>
=======
<h1>Bem-vindo ao Nosso Novo App!</h1>
>>>>>>> feature/novo-layout
```

### Entendendo Cada Parte

- `<<<<<<< HEAD`: Indica o início do bloco de conflito. O código logo abaixo desta linha é o código **atual** da branch em que você está (geralmente a `main` recebendo o merge).
- `=======`: É a linha divisória. Ela separa a sua versão atual da versão que está tentando entrar.
- `>>>>>>> feature/novo-layout`: Indica o fim do bloco de conflito. O código logo acima desta linha é a modificação vinda da outra branch.

## Resolvendo Conflitos Manualmente

Resolver um conflito significa simplesmente editar o arquivo de texto para que ele fique com a versão final desejada, e apagar as marcações do Git.

### Passo a Passo

#### 1. Identificar Arquivos com Conflito
Rode `git status` e veja a lista sob "Unmerged paths".

#### 2. Abrir Arquivo no Editor
Abra o arquivo no seu editor preferido (VS Code, Sublime, Bloco de Notas).

#### 3. Analisar as Versões
Leia as duas versões propostas pelo Git (acima e abaixo dos `=======`). Tente entender o que seu colega tentou fazer na versão dele e o que você fez na sua.

#### 4. Decidir o que Manter
Você tem controle total. Pode:
- Manter apenas a versão atual (a de cima).
- Manter apenas a versão que está entrando (a de baixo).
- Manter ambas (combinar o código).
- Apagar tudo e escrever um código inteiramente novo que acomode as duas ideias.

#### 5. Editar o Arquivo
Neste exemplo, vamos decidir combinar as ideias para uma frase melhor:

```markdown
# Antes (com marcadores):
<<<<<<< HEAD
<h1>Bem-vindo ao Meu Site!</h1>
=======
<h1>Bem-vindo ao Nosso Novo App!</h1>
>>>>>>> feature/novo-layout

# Depois (minha edição final manual):
<h1>Bem-vindo ao Nosso Novo App e Site!</h1>
```

#### 6. Remover TODOS os Marcadores
É crucial garantir que você apagou as linhas `<<<<<<< HEAD`, `=======` e `>>>>>>> branch`. Se você esquecer, elas vão virar código e quebrar sua aplicação!

#### 7. Testar
Salve o arquivo e rode a aplicação localmente para garantir que não quebrou nada.

#### 8. Marcar como Resolvido
No terminal, diga ao Git que aquele arquivo específico foi consertado:
```bash
git add index.html
```

#### 9. Completar o Merge
Quando não houver mais arquivos em conflito (verifique com `git status`), finalize a operação:
```bash
git commit -m "Merge branch 'feature/novo-layout', resolvendo conflito no título"
```

## Estratégias de Resolução Automática

Se você tem 100% de certeza de qual versão deve prevalecer, não precisa abrir o arquivo para apagar marcações. Pode usar a linha de comando:

### Aceitar Completamente Uma Versão

```bash
# Mantém a versão da branch que ESTÁ RECEBENDO o merge (onde você está)
git checkout --ours arquivo-conflitante.txt

# Mantém a versão da branch QUE ESTÁ ENTRANDO
git checkout --theirs arquivo-conflitante.txt

# Depois faça o add e commit
git add arquivo-conflitante.txt
git commit
```

## Ferramentas de Merge

Resolver conflitos no bloco de notas é sofrido. Use as ferramentas modernas!

### VS Code

O Visual Studio Code detecta os marcadores do Git e coloca botões clicáveis super práticos logo acima do conflito:
- **Accept Current Change:** Mantém o que já estava lá (sua versão).
- **Accept Incoming Change:** Aceita o que está vindo da outra branch.
- **Accept Both Changes:** Mantém as duas linhas juntas.
- **Compare Changes:** Abre uma tela dividida comparando o arquivo inteiro.

### Git GUI Tools (GitKraken / SourceTree)

Interfaces gráficas de Git costumam ter editores visuais de resolução de três vias (Three-way merge tool), mostrando sua branch na esquerda, a do colega na direita, e o resultado final no meio.

### Configurando Merge Tool

Se você prefere ferramentas dedicadas (como Meld ou KDiff3), pode configurá-las no Git:
```bash
# Configura o Meld como ferramenta padrão de resolução
git config --global merge.tool meld

# Quando der conflito, basta rodar:
git mergetool
```

## Tipos de Conflitos

### Conflito de Conteúdo
O clássico que vimos acima: edição da mesma linha em duas branches.

### Conflito de Renomeação
Você editou um arquivo, mas seu colega renomeou esse arquivo na outra branch.

### Conflito de Deleção
Você atualizou um arquivo de estilos, mas seu colega decidiu deletar esse arquivo porque reestruturou o layout.
O Git perguntará: "Queremos manter a sua edição ou deletar o arquivo como seu colega sugeriu?"

## Prevenindo Conflitos

A melhor resolução é não ter o conflito.

### Comunicação
A regra de ouro: converse com sua equipe. Se você vai fazer uma grande refatoração que renomeia várias pastas, avise no chat do time para que as pessoas não mexam ali naquelas horas.

### Pull/Fetch Frequente
Nunca trabalhe dias seguidos isolado na sua branch. Atualize-a com o que a equipe está fazendo na `main`.
```bash
git fetch origin
git merge origin/main
```

### Commits Pequenos e Frequentes
Branches de vida curta (que duram um ou dois dias) raramente dão conflitos massivos, pois não dá tempo do projeto original mudar tanto assim.

### Dividir Trabalho
Arquiteturas de software bem feitas, baseadas em pequenos módulos ou componentes independentes, reduzem a chance de duas pessoas precisarem editar o mesmo arquivo simultaneamente.

## Resolvendo Conflitos em Pull Requests

### Conflitos no GitHub
Quando você abre um PR e o GitHub diz que há conflitos, o botão de Merge fica desativado e cinza.

### Método Recomendado: Resolver Localmente
Nunca tente resolver conflitos grandes de código pela interface web do GitHub. Faça na sua máquina para poder testar.

```bash
# 1. Vá para a sua branch do PR
git switch minha-branch

# 2. Traga as últimas novidades da branch principal
git pull origin main 
# (Isto vai disparar o conflito na sua máquina)

# 3. Resolva os conflitos no VS Code
# 4. Adicione e comite
git add .
git commit -m "Merge origin/main e resolve conflitos"

# 5. Mande de volta pro GitHub
git push
# O PR atualizará sozinho e o botão ficará verde!
```

## Abortando um Merge

Se você tentou fazer um merge, gerou uma teia de conflitos terríveis em 20 arquivos, entrou em pânico e quer desistir e voltar ao estado seguro anterior:

```bash
git merge --abort
```
O Git limpa toda a tentativa de merge e restaura seus arquivos exatamente como estavam antes de você rodar o comando `git merge`.

## Conflitos Complexos

### Múltiplos Arquivos
Se o `git status` mostrar 5 arquivos em conflito, não se desespere. Resolva e faça `git add` em um de cada vez. É um trabalho metódico.

### Quando Pedir Ajuda
Se o conflito envolver uma lógica de negócio complexa escrita por um colega que você não entende completamente, **não adivinhe**. Chame o colega para uma ligação rápida e resolvam o conflito juntos ("Pair Programming"). Melhor gastar 10 minutos conversando do que introduzir um bug silencioso em produção.

## Dicas e Truques

### Usar Git Log para Contexto
Se não entende de onde veio a mudança conflitante:
```bash
git log --oneline --graph --all
```

### Git Blame para Rastrear
Descubra quem foi o autor da linha que está entrando em conflito com você para saber a quem perguntar:
```bash
git blame arquivo-com-problema.js
```

## Erros Comuns

1. **Não Remover Marcadores:** Comitar os sinais `<<<<<<<` junto com o código. Isso fatalmente causará um erro de sintaxe e derrubará a aplicação.
2. **Marcar como Resolvido Sem Testar:** Só porque você apagou os marcadores, não significa que a lógica conjunta dos dois códigos faz sentido. Teste o projeto.
3. **Aceitar Mudanças Sem Entender:** Clicar "Accept Both Changes" cegamente só para se livrar do erro.
4. **Fazer Force Push após um Merge problemático:** Pode corromper o histórico do repositório remoto.

## Exercícios

1. Crie uma branch `teste-conflito-1`. Altere a primeira linha do arquivo `README.md` e faça o commit.
2. Volte para a `main`, crie outra branch chamada `teste-conflito-2`. Altere a MESMA primeira linha do `README.md` escrevendo algo diferente, e faça commit.
3. Vá para a `main`. Faça o merge de `teste-conflito-1` (Sucesso).
4. Tente fazer o merge de `teste-conflito-2` (Conflito!).
5. Abra o arquivo, veja os marcadores, resolva o texto manualmente, faça o `add` e finalize o commit.

## Checklist de Resolução

Sempre siga este fluxo para não se perder:
- [ ] Identificar a interrupção (Git avisou do conflito).
- [ ] Rodar `git status` para listar os arquivos problemáticos.
- [ ] Abrir o editor e ler ambas as versões do conflito (HEAD vs Incoming).
- [ ] Decidir a resolução lógica final.
- [ ] Apagar todos os marcadores (`<<<<`, `====`, `>>>>`).
- [ ] Salvar o arquivo e testar a aplicação.
- [ ] Rodar `git add <arquivo>`.
- [ ] Rodar `git commit` para selar a resolução.

## Recursos Adicionais

- [Documentação Oficial Git sobre Conflitos](https://git-scm.com/docs/git-merge#_how_conflicts_are_presented)
- [Tutorial Interativo de Resolução no GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts)

## Resumo

### Lembre-se
- **Conflitos são normais e frequentes.** Não há motivo para pânico.
- O Git confia em você para tomar a decisão correta quando não há certeza matemática.
- Entenda sempre a intenção da sua mudança e a intenção da mudança do seu colega antes de misturá-las.
- Comunique-se intensamente com a equipe para manter sua branch atualizada e os conflitos raros e pequenos.


---

<div align="center">

[⬅️ Capítulo Anterior: 05. Boas Práticas](./05-boas-praticas.md)
 | 
[Capítulo Seguinte: 07. Workflows no GitHub ➡️](./07-workflows-github.md)

</div>

## 👥 Contribuidores

Este conteúdo é colaborativo. Contribuidores deste arquivo:
- [@bigauke](https://github.com/bigauke) (Antonio Daniel de Souza Linhares) - Preenchimento do conteúdo sobre Resolução de Conflitos.
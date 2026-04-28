# Pull Requests e Code Review

<!-- Este arquivo explica o workflow de Pull Requests e revisão de código no GitHub -->

## 📋 Objetivos de Aprendizagem

- Compreender o conceito e o propósito de um Pull Request.

- Dominar o fluxo de trabalho completo, desde a criação da branch até o merge.

- Aplicar boas práticas ao solicitar e realizar revisões de código (Code Review).

- Entender os diferentes estados e tipos de merge de um Pull Request.

## 🎯 Introdução
Pull Requests são o coração da colaboração em projetos de software modernos. Eles criam um ambiente seguro para que o código seja analisado, testado e discutido por outros desenvolvedores antes de ser integrado à base principal do projeto, evitando a introdução de bugs e garantindo o alinhamento com os padrões da equipe.

## O que é um Pull Request (PR)?

Um Pull Request é um pedido formal para que as alterações feitas em uma branch específica sejam puxadas ("pulled") e mescladas ("merged") em outra branch (geralmente a main). É importante saber que o Pull Request não é um comando do Git, mas sim uma funcionalidade fornecida por plataformas de hospedagem de código, como o GitHub, GitLab ou Bitbucket.

### Pull Request vs MergeS

A principal diferença é que um Pull Request (PR) é uma solicitação formal para revisar e integrar o código (um processo colaborativo), enquanto o Merge é a ação técnica de juntar esse código de uma branch para outra. O PR ocorre antes do merge, permitindo discussões e testes. 

### Por que Usar Pull Requests?

- Revisão de Código: Permite que outros desenvolvedores encontrem erros antes que cheguem à produção.
  
- Discussão Técnica: Cria um fórum para debater a melhor abordagem para resolver um problema.

- Integração Contínua (CI/CD): Permite rodar testes e linters automaticamente na branch isolada.

- Histórico e Documentação: Mantém um registro do motivo pelo qual uma alteração foi feita e de quem a aprovou.

- Aprendizado: Desenvolvedores menos experientes aprendem lendo o código dos mais experientes (e vice-versa).
  
## Workflow com Pull Requests

O fluxo tradicional de trabalho em projetos colaborativos ou Open Source segue um padrão claro de etapas.

### Visão Geral

```
1. Fork do repositório (para projetos onde você não tem permissão de escrita)
2. Clone do seu fork para a máquina local
3. Criar uma nova Branch (ex: feature/nova-tela)
4. Fazer mudanças no código e commits
5. Push da branch para o seu fork no GitHub
6. Abrir o Pull Request na interface do GitHub
7. Revisão de código e discussão com a equipe
8. Ajustes locais e novos pushes (se necessário)
9. Aprovação do Pull Request
10. Merge na branch principal
```

## Criando um Pull Request

### Pré-requisitos

**Antes de abrir um PR, certifique-se de que:**

- Suas alterações estão em uma branch separada (nunca trabalhe direto na main).

- Seu código está testado localmente e funcionando.

- Seus commits possuem mensagens claras e descritivas.
- As alterações estão alinhadas com a issue que você se propôs a resolver.

### Passo a Passo

#### 1. Fazer Push da Branch

Primeiro, envie sua branch local para o repositório remoto:

```bash
git push origin nome-da-sua-branch
```

#### 2. Abrir PR no GitHub

Acesse a página do repositório no GitHub. Logo após fazer o push, o GitHub geralmente exibe um banner amarelo com o botão "Compare & pull request". Caso não apareça, vá até a aba "Pull requests" e clique no botão verde "New pull request", selecionando a sua branch como origem e a main como destino.

#### 3. Preencher Informações

Uma comunicação clara no Pull Request economiza tempo de todos os colaborados e envolvidos.

##### Título do PR

O título deve ser conciso e usar o padrão do projeto (ex: Conventional Commits).

- Exemplo ideal: feat: "adiciona autenticação por JWT na API."

- Exemplo ruim: atualizando arquivos.

##### Descrição
A descrição deve fornecer todo o contexto necessário para o revisor.

**Sempre inclua:**

- O que foi feito e qual problema isso resolve.

- Como o revisor pode testar as alterações localmente.

- Screenshots ou GIFs caso tenha alterado a interface (Front-end).
#### 4. Referenciar Issues

Você pode vincular o seu PR a uma Issue existente no GitHub. Se você usar palavras-chave específicas na descrição, o GitHub fechará a issue automaticamente quando o PR sofrer o merge.

Exemplos:  Closes #123, Fixes #456, Resolves #102.

## Anatomia de um Bom Pull Request

### Tamanho
Pull Requests devem ser o menor possível. PRs com milhares de linhas de código são difíceis de revisar, escondem bugs facilmente e demoram para ser aprovados. Se a funcionalidade for muito grande, divida em PRs menores.

### Commits

Mantenha o histórico limpo. Evite commits como **Arrumando Erro** ou **Teste**. Cada commit deve representar uma unidade lógica de mudança e ter uma mensagem explicativa.

### Descrição Clara

Utilize templates de PR (se o repositório tiver um) e não deixe a descrição em branco. O revisor precisa entender seu raciocínio antes de ler as linhas de código.

### Testes

Utilize templates de PR (se o repositório tiver um) e não deixe a descrição em branco. O revisor precisa entender seu raciocínio antes de ler as linhas de código.

## Code Review: Revisando PRs

### O que é Code Review?

É a prática sistemática de analisar o código escrito por outro desenvolvedor. O objetivo é encontrar possíveis falhas estruturais, de lógica ou de segurança antes que o código seja efetivamente mesclado.

### Por que Revisar Código?

- **Qualidade:** Garante que o código atende aos padrões da arquitetura do projeto.
- **Prevenção de Bugs:** Dois pares de olhos veem melhor que um.

- **Compartilhamento de Conhecimento:** Evita que apenas uma pessoa saiba como determinada parte do sistema funciona.

### Como Ser um Bom Revisor
Revisar código exige empatia e atenção aos detalhes.

#### 1. Entender o Contexto
Nunca comece a ler o código diretamente. Leia a Issue associada, entenda o requisito de negócio e leia a descrição do PR.

#### 2. Revisar o Código

**O que você deve procurar durante a leitura:**

- O código resolve o problema proposto na Issue?

- A lógica está clara e fácil de entender?

- Existem vazamentos de memória, problemas de performance ou falhas de segurança?

- Os nomes de variáveis e funções fazem sentido?

- A documentação e os testes foram atualizados?
  
#### 3. Fazer Comentários Construtivos

O foco deve ser sempre a melhoria do código, nunca criticar o autor.

##### Exemplos de Bons Comentários

Exemplos de Bons Comentários:
```
✅ "Boa explicação! Sugiro adicionar um exemplo de uso para tornar mais claro."
✅ "Este código pode simplificar se usarmos a função map() do Javascript. O que você acha?"
✅ "Encontrei um typo na linha 23: 'comit' → 'commit'"
```

##### Exemplos de Comentários Ruins

Evitar esses tipos de comentários:
```
❌ "Está errado." (Não explica o porquê nem como melhorar)
❌ "Não sei por que você fez assim." (Tom agressivo)
❌ "Eu faria diferente." (Se não agrega valor à performance ou arquitetura, é apenas preciosismo)
```

#### 4. Usar Sugestões

O GitHub possui a funcionalidade "Add a suggestion" (Ctrl + G ou o ícone de documento com o +/-). Ela permite que você digite o código corrigido direto no comentário, e o autor pode aceitar a sugestão com um clique, aplicando o commit automaticamente.

#### 5. Solicitar Alterações ou Aprovar

**Ao finalizar a revisão no botão "Review changes", escolha a ação correta:**

- Comment: Apenas dúvidas e observações leves, sem aprovar ou bloquear.

- Approve: O código está excelente e liberado para merge.

- Request changes: O código tem problemas que precisam obrigatoriamente ser corrigidos antes de ser integrado.
  
## Respondendo a Code Review

### Como Autor do PR

Lidar com revisões faz parte do dia a dia da engenharia de software e exige maturidade.
  
#### Recebendo Feedback

Mantenha uma atitude positiva. O revisor não está avaliando suas habilidades profissionais, mas sim garantindo a qualidade do produto final. Não leve apontamentos técnicos para o lado pessoal.

#### Discutindo Construtivamente

Se você discorda de um apontamento, argumente de forma técnica e respeitosa. Explique o motivo pelo qual você tomou aquela decisão de design. O Code Review é um diálogo.

#### Fazendo Alterações
Para atualizar um PR com as mudanças solicitadas pelo revisor, basta alterar o código localmente, commitar e fazer o push novamente na mesma branch:

```bash
# Faça as modificações nos arquivos
git add .
git commit -m "refactor: ajusta lógica conforme revisão de código"
git push origin sua-branchte)
```

#### Marcar Conversas como Resolvidas

Quando você aplicar a correção pedida em um comentário, clique no botão "Resolve conversation" para ocultar a thread e mostrar ao revisor que aquele ponto foi tratado.

## Estados de um Pull Request

Durante o seu ciclo de vida, um Pull Request passará por diferentes estados visíveis na plataforma:

### Draft (Rascunho)

Indica que o PR ainda está em desenvolvimento. É útil para mostrar à equipe o que você está construindo e pedir opiniões precoces, mas o botão de merge fica bloqueado. Revisores não são notificados de um Draft PR.

### Open (Aberto)

O PR está finalizado pelo autor e pronto para revisão. O código está aguardando o Code Review e a execução da pipeline de testes.

### Changes Requested

Um revisor analisou o código e marcou o PR exigindo modificações. O merge fica bloqueado até que o autor faça os ajustes e o revisor mude o status para "Approved".

### Approved

A revisão foi concluída com sucesso por um ou mais membros da equipe. O código foi validado tecnicamente e está liberado para integração.

### Merged

O estado final de sucesso. O código contido na branch do PR foi integrado oficialmente na branch de destino (ex: main) e já faz parte da base do projeto.

### Closed

O PR foi encerrado sem que o código fosse mesclado. Isso acontece se a feature for cancelada, se a abordagem adotada foi descartada, ou se houver um erro irreversível no PR.

## Merge de Pull Requests

### Tipos de Merge no GitHub

O GitHub oferece três maneiras principais de concluir a integração de um PR:

#### Merge Commit

Cria um commit explícito de junção (Merge). Ele preserva exatamente a árvore de commits e o histórico de tudo o que foi feito na branch.

- Vantagem: Histórico fiel à realidade.

- Desvantagem: Pode deixar a árvore do Git confusa e poluída.
  
#### Squash and Merge

Pega todos os commits da sua branch do PR e os comprime em um único commit na branch principal.

- Vantagem: Mantém a main extremamente limpa, com apenas um commit por funcionalidade.

- Desvantagem: O detalhamento granular de como o desenvolvedor chegou à solução é perdido.

#### Rebase and Merge

Reaplica cada um dos commits do PR diretamente no topo da branch de destino, de forma sequencial, sem criar um commit de merge.

- Vantagem: Histórico linear, limpo e detalhado.

- Desvantagem: Exige que a equipe tenha mais proficiência em Git, pois resolver conflitos de rebase pode ser complexo.

### Quando Usar Cada Tipo

- Squash: Ideal para branches de funcionalidades longas e com commits de correção rápida (ex: wip, arrumando typo).

- Merge Commit: Ideal para repositórios onde a rastreabilidade absoluta de cada etapa de desenvolvimento é exigida.

- Rebase: Ideal para equipes pequenas e experientes que valorizam um histórico linear perfeito.

## Conflitos em Pull Requests

Conflitos ocorrem quando você e outro desenvolvedor alteram exatamente as mesmas linhas do mesmo arquivo, ou quando alguém deleta um arquivo que você estava modificando. O Git não sabe qual alteração manter e pausa para intervenção humana.

### Resolvendo na Interface do GitHub

Se o conflito for simples (mudança em linhas de texto comuns), o próprio GitHub oferece o botão "Resolve conflicts" no PR. Ele abrirá um editor web onde você pode remover as marcações do Git e escolher o trecho final de código.

### Resolvendo Localmente

```bash
# Atualiza as informações do repositório original
git fetch upstream

# Traz as atualizações da main para a sua branch (pode gerar o conflito aqui)
git merge upstream/main

# -> Abra o VS Code, encontre os arquivos marcados com conflito e ajuste o código.

# Salve, adicione as correções e finalize o merge
git add .
git commit -m "fix: resolve conflitos de merge com a main"
git push origin sua-branch
```

## CI/CD e Checks

Pull Requests modernos dependem de automação (Pipelines) para manter a integridade do código.

### Status Checks

São rotinas que o GitHub executa automaticamente sempre que um PR é aberto ou atualizado. Geralmente incluem:

- Linters: Verificam se a indentação e os padrões de código estão corretos.

- Testes Unitários: Rodam a suíte de testes da aplicação para garantir que nada quebrou.

- Segurança: Analisam vulnerabilidades em pacotes instalados.
Muitos repositórios exigem que todos os Status Checks fiquem verdes (passos com sucesso) antes de habilitar o botão de merge.

### Como Lidar com Checks Falhando

Se aparecer um "X" vermelho no seu PR:

1. Clique em "Details" ao lado do check que falhou.

2. Leia o log do terminal (geralmente apontará o erro exato e a linha).

3. Faça a correção no seu ambiente local, teste.

4. Faça o commit e o push novamente. O check rodará de forma automática.

## Templates de Pull Request

Muitos projetos utilizam um arquivo especial chamado PULL_REQUEST_TEMPLATE.md na raiz do repositório ou na pasta .github. Ele carrega um formulário automático toda vez que alguém clica em "New pull request". Isso ajuda a padronizar a documentação, forçando os desenvolvedores a preencherem checklists de testes, documentação e descrição.

## Boas Práticas

### Para quem Abre PRs

- Descreva bem as mudanças: Forneça contexto; explique o que e o porquê, não apenas o como.

- Mantenha PR focado: Uma funcionalidade/correção por PR.

- Seja responsivo a feedback: Acompanhe seu PR e responda rapidamente aos revisores.

- Teste antes de abrir: O Code Review não substitui o teste do próprio desenvolvedor.

### Para Revisores

- Seja respeitoso e construtivo: Promova um ambiente seguro para o aprendizado coletivo.

- Revise em tempo hábil: PRs parados por muitos dias atrapalham o cronograma e geram conflitos de código.

- Explique o "porquê" das sugestões: Compartilhe a referência ou documentação junto com a crítica.

- Reconheça bom trabalho: Elogie arquiteturas inteligentes e códigos bem escritos.

## Etiqueta de Code Review

### Código de Conduta

O ambiente de engenharia deve focar no produto, não em vaidades pessoais. Seja empático ao escrever comentários; lembre-se que texto não transmite tom de voz e pode soar rude se for curto demais. Critique a linha de código, jamais a capacidade de quem o escreveu.

### Tom de Comunicação

Utilize verbos colaborativos. Ao invés de usar o imperativo ("Mude essa função", "Corrija isso"), utilize sugestões abertas ("O que acha de extrairmos essa lógica para um módulo separado?", "Acredito que se usarmos o parâmetro X, o ganho de performance será melhor.").

## Ferramentas Úteis

### GitHub CLI

```bash
gh pr create
# Lista os PRs abertos no repositório
gh pr list
# Visualiza os detalhes e status do PR atual
gh pr view
# Realiza o merge do PR via linha de comando
gh pr merge
```

### Navegação no GitHub

O GitHub web possui atalhos de teclado produtivos em um PR:

- Na aba Files changed, pressione t para abrir a árvore de navegação de arquivos.

- Pressione v para visualizar o arquivo completo (não apenas o bloco com diferença).

- Clique no símbolo + na linha de código específica para abrir o painel de comentário localizado.

## Exemplos Práticos

### Exemplo 1: Primeiro Pull Request

**Você é encarregado de adicionar um botão na página de login.**

1. Cria a branch feat/btn-login.

2. Adiciona o HTML e CSS do botão.

3. Faz o push e abre o PR com o título: feat: adiciona botão de login social.

4. Na descrição, anexa uma foto do antes/depois da tela.
   
### Exemplo 2: Revisando um PR

**Você é o revisor do PR acima. Lê o código e nota que o botão não é responsivo no mobile.**

1. Seleciona o arquivo CSS e deixa um comentário na linha: "A classe do botão está com largura fixa. O que acha de usarmos width: 100% com um max-width para comportar telas menores?"

2. Coloca o status do PR como "Request Changes".

### Exemplo 3: Respondendo a Feedback

O autor recebe a notificação da falha de responsividade.

1. Corrige o CSS no VS Code, altera para width: 100%.

2. Faz o commit: git commit -m "style: ajusta responsividade do botão de login".

3. Dá git push.

4. No GitHub, clica em "Resolve conversation" e pede uma re-revisão. O revisor aprova e faz o merge.

## Métricas e Estatísticas

### Tempo de Revisão

É a métrica de quanto tempo um PR fica aberto até o primeiro comentário do revisor. Manter esse tempo baixo impede o acúmulo de tarefas, evita conflitos drásticos com outras features sendo desenvolvidas em paralelo e mantém o desenvolvedor focado no contexto do código recém-escrito.

### Taxa de Aprovação

Quantas idas e vindas (Request Changes) o PR precisou até ser aprovado. Uma taxa muito alta frequentemente indica problemas na especificação da tarefa original (Issue mal escrita) ou falta de alinhamento prévio da arquitetura da solução entre a equipe.

## Erros Comuns

### Erro 1: PR Muito Grande

Um Pull Request contendo 45 arquivos modificados e 2.000 linhas de código quase nunca será revisado de forma minuciosa (o chamado "LGTM" cego - Looks Good To Me). Solução: Divida o trabalho.

### Erro 2: Não Atualizar com a Main

Criar um PR de uma branch que está desatualizada há 3 semanas em relação à main. Isso gera conflitos e testes quebrados na pipeline. Solução: Sempre faça um git pull upstream main antes de iniciar seu dia e antes de abrir o PR.

### Erro 3: Não Testar Antes de Abrir

Abrir o PR com código que nem sequer compila localmente, confiando apenas nas automações do GitHub. Isso desperdiça recursos de CI e tempo da equipe.

### Erro 4: Não Responder a Comentários

Fazer alterações locais baseadas nos feedbacks, mas dar "push" ignorando as threads de conversa no GitHub, deixando o revisor confuso se a sugestão foi adotada, modificada ou descartada.

## Exercícios

**Para consolidar o conhecimento, tente praticar estas rotinas:**
1. Acesse o repositório deste guia, faça um fork, altere um arquivo e crie seu primeiro Pull Request em Draft para observar o estado e o bloqueio de Merge.

2. Peça a um colega para criar um Pull Request e pratique o envio de uma sugestão de Código com o status "Comment".

3. Receba um "Request Changes" no seu PR, modifique o arquivo no seu VS Code, faça o push e veja o PR atualizar automaticamente, finalizando ao clicar em "Resolve conversation".

4. Simule um conflito: crie duas branches baseadas na main, altere a mesma linha nas duas, faça o push e abra os dois PRs. Dê o merge no primeiro e tente dar o merge no segundo para praticar a resolução no editor do GitHub.

## Workflow Diagram

Fluxograma básico de um Pull Request:

Local                   Remoto (GitHub)
  
[ main ]                  [ main ]
   |                         | (10. Merge)
   |-- (3. Branch)           ^
   |                         | (9. Approve)
[ feature ]               [ feature PR ]
   |                         ^
   |-- (4. Commits)          | (7. Code Review)
   |                         |
   +------------------> (6. Open PR)
      (5. Push)

## Recursos Adicionais

Para aprofundar seu conhecimento na gestão do repositório, consulte estes links oficiais e guias de mercado:

- [Convevtional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0/)

- [eng-pratices](https://google.github.io/eng-practices/review/)

- [GitHub Pull Request Documentation](https://docs.github.com/en/pull-requests)
- [Code Review Best Practices](https://google.github.io/eng-practices/review/)

## Resumo

Pull Requests e revisões de código são habilidades interpessoais e técnicas tão cruciais quanto o próprio ato de programar. Eles garantem a saúde do sistema, distribuem conhecimento, uniformizam padrões e criam um ambiente cooperativo. Ao dominar PRs pequenos, bem documentados e a arte de um feedback construtivo, você se torna um profissional pronto para atuar em times de engenharia de ponta.

## 👥 Contribuidores

- [@marcos-vinicius](https://github.com/MarcosvvMarques) 


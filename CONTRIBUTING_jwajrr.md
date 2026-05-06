# 🤝 Guia de Contribuição

Bem-vindo(a) ao projeto de documentação colaborativa! Estamos muito felizes que você queira contribuir. Este guia vai te ajudar a fazer sua primeira contribuição com sucesso.

## 📚 Índice

- [Pré-requisitos](#pré-requisitos)
- [Fluxo de Trabalho Completo](#fluxo-de-trabalho-completo)
- [Padrões de Commit](#padrões-de-commit)
- [Como Revisar Pull Requests](#como-revisar-pull-requests)
- [Resolução de Conflitos](#resolução-de-conflitos)
- [Boas Práticas](#boas-práticas)
- [Problemas Comuns](#problemas-comuns)
- [Precisa de Ajuda?](#precisa-de-ajuda)

## ✅ Pré-requisitos

Antes de começar, certifique-se de ter:

- [ ] Git instalado no seu computador ([Download Git](https://git-scm.com/downloads))
- [ ] Uma conta no GitHub ([Criar conta](https://github.com/signup))
- [ ] Editor de texto (recomendamos [VS Code](https://code.visualstudio.com/))
- [ ] Conhecimento básico de Markdown ([Guia Markdown](https://www.markdownguide.org/basic-syntax/))

## 🔄 Fluxo de Trabalho Completo

Siga **todos os passos** abaixo para fazer sua contribuição:

### Passo 1: Encontrar uma Issue Disponível

1. Acesse a aba [Issues](../../issues) do repositório
2. Procure por issues com a label `status:disponivel`
3. Leia a descrição da issue completamente
4. Escolha uma issue compatível com seu nível

### Passo 2: Reivindicar a Issue

1. **Comente na issue** dizendo que você vai trabalhar nela
2. Exemplo: "Olá! Gostaria de trabalhar nesta issue."
3. Aguarde o professor atribuir a issue a você
4. **Não comece sem comentar primeiro!** Isso evita duplicação de trabalho

### Passo 3: Fazer Fork do Repositório

1. Clique no botão **Fork** no canto superior direito desta página
2. Isso cria uma cópia do repositório na sua conta do GitHub
3. Agora você tem seu próprio repositório para trabalhar

### Passo 4: Clonar seu Fork

Abra o terminal e execute:

```bash
# Substitua SEU-USUARIO pelo seu nome de usuário do GitHub
git clone https://github.com/SEU-USUARIO/gh0.git

# Entre na pasta do projeto
cd gh0
```

### Passo 5: Configurar o Repositório Upstream

Isso permite que você mantenha seu fork atualizado com o repositório original:

```bash
# Adicione o repositório original como "upstream"
git remote add upstream https://github.com/iaglourenco/gh0.git

# Verifique se foi adicionado corretamente
git remote -v
```

Você deve ver algo assim:

```
origin    https://github.com/SEU-USUARIO/gh0.git (fetch)
origin    https://github.com/SEU-USUARIO/gh0.git (push)
upstream  https://github.com/iaglourenco/gh0.git (fetch)
upstream  https://github.com/iaglourenco/gh0.git (push)
```

### Passo 6: Criar uma Branch

**NUNCA trabalhe diretamente na branch `main`!**

```bash
# Crie e mude para uma nova branch
# Use um nome descritivo: seu-nome/descricao-tarefa
git switch -c seu-nome/adiciona-secao-git-init

# Exemplos de bons nomes de branch:
# joao-silva/explica-git-commit
# maria-santos/adiciona-exemplos-merge
# pedro-oliveira/corrige-typo-readme
```

### Passo 7: Fazer as Alterações

1. Abra o arquivo indicado na issue (ex: `docs/02-comandos-essenciais.md`)
2. Leia os comentários `<!-- -->` que indicam o que escrever
3. Adicione o conteúdo solicitado
4. Siga a estrutura já existente no arquivo
5. Use Markdown corretamente (veja [sintaxe Markdown](https://www.markdownguide.org/basic-syntax/))

**Dicas importantes:**

- Escreva de forma clara e didática
- Use exemplos práticos sempre que possível
- Adicione blocos de código com a sintaxe correta:

  ````markdown
  ```bash
  git commit -m "Mensagem descritiva"
  ```
  ````

- Revise ortografia e gramática
- Teste se o Markdown está renderizando corretamente

### Passo 8: Fazer Commit das Alterações

```bash
# Verifique o que foi modificado
git status

# Adicione os arquivos alterados
git add docs/02-comandos-essenciais.md

# Faça o commit com uma mensagem descritiva
git commit -m "docs: adiciona explicação sobre git init"
```

**Veja a seção [Padrões de Commit](#padrões-de-commit) para escrever boas mensagens!**

### Passo 9: Enviar para seu Fork (Push)

```bash
# Envie sua branch para o seu fork no GitHub
git push origin seu-nome/adiciona-secao-git-init
```

### Passo 10: Abrir um Pull Request

1. Acesse seu fork no GitHub
2. Você verá um banner **"Compare & pull request"** — clique nele
3. Preencha o template do Pull Request:
   - Descreva o que você fez
   - Referencie a issue (ex: `Closes #42`)
   - Marque todos os checkboxes da checklist
4. Clique em **"Create Pull Request"**

### Passo 11: Responder às Revisões

1. Outro aluno irá revisar seu Pull Request
2. Seja receptivo aos comentários e sugestões
3. Se pedirem alterações:

   ```bash
   # Faça as alterações nos arquivos
   # Adicione e commite novamente
   git add .
   git commit -m "docs: ajusta exemplo conforme revisão"

   # Envie as alterações
   git push origin seu-nome/adiciona-secao-git-init
   ```

4. O Pull Request será atualizado automaticamente

### Passo 12: Aguardar o Merge

Após aprovação do revisor, o professor fará o merge do seu Pull Request. Parabéns pela contribuição!

## 📝 Padrões de Commit

Use mensagens de commit claras e descritivas seguindo este formato:

```
tipo: descrição breve do que foi feito
```

### Tipos de Commit

- `docs:` — Adição ou alteração de documentação
- `fix:` — Correção de erros ou typos
- `style:` — Formatação, indentação (sem mudança de conteúdo)
- `refactor:` — Reorganização de conteúdo sem adicionar/remover
- `feat:` — Nova seção ou funcionalidade

### Exemplos de Boas Mensagens

✅ **BOM:**

```bash
git commit -m "docs: adiciona seção sobre git clone"
git commit -m "fix: corrige exemplo de git merge"
git commit -m "docs: explica diferença entre Git e GitHub"
git commit -m "style: melhora formatação dos blocos de código"
```

❌ **RUIM:**

```bash
git commit -m "alterações"
git commit -m "atualização"
git commit -m "fix"
git commit -m "mudei umas coisas"
```

### Regras para Commits

- Use verbos no **presente** ("adiciona", não "adicionou")
- Primeira letra **minúscula** (exceto nomes próprios)
- **Não** use ponto final
- Seja **específico** sobre o que foi feito
- Mantenha a linha com **menos de 72 caracteres**

## 👀 Como Revisar Pull Requests

Parte do projeto é revisar as contribuições de colegas. Veja como fazer uma boa revisão:

### Passo a Passo da Revisão

1. **Abra o Pull Request** que foi atribuído a você
2. **Leia a descrição** para entender o objetivo
3. **Veja os arquivos alterados** na aba "Files changed"
4. **Verifique:**
   - ✅ O conteúdo está correto e claro?
   - ✅ A ortografia e gramática estão corretas?
   - ✅ O Markdown está formatado corretamente?
   - ✅ Os exemplos de código fazem sentido?
   - ✅ O texto é adequado para iniciantes?
   - ✅ A issue foi resolvida completamente?

### Como Comentar

**Para comentar em uma linha específica:**

1. Passe o mouse sobre a linha
2. Clique no ícone **+** azul
3. Escreva seu comentário
4. Clique em **"Start a review"**

**Tipos de comentários:**

- **Sugestões**: Use o botão de sugestão para propor mudanças diretas
- **Perguntas**: Peça esclarecimentos se algo não está claro
- **Elogios**: Reconheça partes bem feitas!

### Exemplo de Bom Comentário

✅ **Construtivo:**

> "Boa explicação! Sugiro adicionar um exemplo prático de como usar o `git init` em um projeto real. Isso ajudaria iniciantes a entenderem melhor o contexto."

❌ **Não construtivo:**

> "Está errado."

### Submeter a Revisão

Após revisar tudo:

1. Clique em **"Review changes"** (canto superior direito)
2. Escreva um resumo da revisão
3. Escolha uma opção:
   - **Comment**: Apenas comentários gerais
   - **Approve**: Aprovar o Pull Request
   - **Request changes**: Solicitar alterações antes de aprovar
4. Clique em **"Submit review"**

### Quando Aprovar

Aprove um Pull Request quando:

- O conteúdo está correto e completo
- Não há erros de ortografia ou gramática significativos
- O Markdown está formatado corretamente
- A issue foi resolvida
- Todos os comentários anteriores foram respondidos ou resolvidos

## ⚔️ Resolução de Conflitos

Conflitos de merge acontecem quando duas pessoas editam a mesma parte de um arquivo. **Isso é normal e esperado!**

### Por Que Acontecem?

1. Você cria uma branch baseada na `main`
2. Enquanto você trabalha, outra pessoa abre um Pull Request
3. O Pull Request dela é aprovado e o merge é feito
4. Agora a `main` mudou, mas sua branch não tem essas mudanças
5. Quando você abre seu PR, há um conflito

### Como Resolver

#### Opção 1: Atualizar sua Branch (Recomendado)

```bash
# Certifique-se de estar na sua branch
git switch sua-branch

# Busque as atualizações do repositório original
git fetch upstream

# Faça merge da main atualizada na sua branch
git merge upstream/main
```

Se houver conflitos, o Git vai mostrar algo assim:

```
Auto-merging docs/02-comandos-essenciais.md
CONFLICT (content): Merge conflict in docs/02-comandos-essenciais.md
Automatic merge failed; fix conflicts and then commit the result.
```

#### Opção 2: Resolver o Conflito Manualmente

1. Abra o arquivo com conflito no editor
2. Procure pelos marcadores de conflito:

   ```markdown
   ## git init

   <<<<<<< HEAD
   Este comando inicializa um repositório Git.
   =======
   Este comando cria um novo repositório Git vazio.
   >>>>>>> upstream/main
   ```

3. Os marcadores significam:
   - `<<<<<<< HEAD`: Sua versão
   - `=======`: Separador
   - `>>>>>>> upstream/main`: Versão da main

4. **Edite o arquivo** para manter o que faz sentido (pode combinar as duas versões):

   ```markdown
   ## git init

   Este comando inicializa um novo repositório Git vazio.
   ```

5. **Delete os marcadores** (`<<<<<<<`, `=======`, `>>>>>>>`)

6. Salve o arquivo e finalize:

   ```bash
   git add docs/02-comandos-essenciais.md
   git commit -m "resolve: conflito na seção git init"
   git push origin sua-branch
   ```

### Ferramentas para Ajudar

- **VS Code**: Tem botões visuais para aceitar uma versão ou combinar as duas
- **Comando Git**: `git mergetool` abre a ferramenta de merge configurada

### Quando Pedir Ajuda

Se você:

- Não entende o que causou o conflito
- Não sabe qual versão manter
- Tem medo de perder trabalho
- Já tentou e não conseguiu

**Peça ajuda ao professor ou abra uma issue de pergunta!**

## ✨ Boas Práticas

### Durante o Desenvolvimento

- ✅ Trabalhe em **uma issue por vez**
- ✅ Faça **commits pequenos e frequentes**
- ✅ Teste o Markdown antes de fazer commit (VS Code: `Ctrl+Shift+V`)
- ✅ **Mantenha seu fork atualizado** antes de começar qualquer trabalho:

  ```bash
  git fetch upstream
  git switch main
  git merge upstream/main
  git push origin main
  ```

- ✅ Use linguagem simples e acessível
- ✅ Adicione exemplos práticos sempre que possível

### Durante a Revisão

- ✅ Seja **respeitoso e construtivo**
- ✅ Faça sugestões, não ordens
- ✅ Explique **por que** algo deve mudar
- ✅ Reconheça o esforço do colega
- ✅ Seja específico nos comentários

### Evite

- ❌ Trabalhar diretamente na branch `main`
- ❌ Fazer Pull Requests muito grandes (máximo ~300 linhas)
- ❌ Copiar e colar conteúdo sem entender
- ❌ Ignorar comentários de revisão
- ❌ Usar `git push --force` (pode sobrescrever o trabalho de outros!)
- ❌ Fazer commits sem mensagem descritiva
- ❌ Esquecer de atualizar seu fork antes de começar

## 🚨 Problemas Comuns

### "Esqueci de fazer fork!"

Se você já clonou o repositório original:

1. Faça o fork agora pelo GitHub
2. Aponte o `origin` para o seu fork:

   ```bash
   git remote set-url origin https://github.com/SEU-USUARIO/gh0.git
   git push origin sua-branch
   ```

### "Commitei na branch main por engano!"

```bash
# Crie uma nova branch a partir do seu commit atual
git switch -c minha-branch

# Volte para a main
git switch main

# Resete a main para o estado do upstream
git reset --hard upstream/main

# Suas alterações estão salvas em minha-branch
git switch minha-branch
git push origin minha-branch
```

### "Meu Pull Request tem muitos commits!"

Não se preocupe! O importante é que o conteúdo final esteja correto. O professor pode fazer squash no momento do merge.

### "Fiz push mas não vejo meu código no repositório original"

Isso está correto! O push vai para **seu fork**. Para que o código apareça no repositório original, você precisa:

1. Abrir um Pull Request
2. Passar pela revisão
3. Ser aprovado
4. Professor fazer o merge

### "Markdown não está renderizando corretamente"

- Use o preview do VS Code (`Ctrl+Shift+V`)
- Verifique a sintaxe dos blocos de código (precisam de três crases)
- Confira se listas têm uma linha em branco antes
- Verifique a indentação dos itens aninhados

## 💡 Precisa de Ajuda?

Não hesite em pedir ajuda! Todos estamos aprendendo.

### Recursos Disponíveis

1. **Documentação do projeto**:
   - Este arquivo (CONTRIBUTING.md)
   - [README.md](README.md)
   - [Documentação em docs/](docs/)

2. **Issues de pergunta**:
   - [Abra uma issue](../../issues/new/choose) do tipo "Pergunta"
   - Descreva sua dúvida em detalhes
   - Inclua mensagens de erro, se houver

3. **Professor**:
   - Entre em contato através do fórum da disciplina

4. **Colegas**:
   - Peça ajuda no grupo da turma
   - Compartilhe o que você já aprendeu

### Recursos Externos

- [Documentação Git](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com)
- [Guia Markdown](https://www.markdownguide.org/)
- [Pro Git Book (PT-BR)](https://git-scm.com/book/pt-br/v2)

## 🎯 Resumo Visual do Fluxo

```
1. Encontrar Issue → 2. Comentar → 3. Fork → 4. Clone → 5. Upstream
                                                                ↓
                                                          6. Branch
                                                                ↓
                                                        7. Alterações
                                                                ↓
                                                          8. Commit
                                                                ↓
                                                           9. Push
                                                                ↓
                                                            10. PR
                                                                ↓
11. Merge ← Aprovação ← Revisão ← 12. Responder Feedback
```

---

## 🙏 Agradecimentos

Obrigado por contribuir com este projeto! Sua participação é essencial para o sucesso do aprendizado colaborativo.

**Bons estudos e boas contribuições!**

---

Última atualização: Abril de 2026

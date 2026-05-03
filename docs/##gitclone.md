## git clone

O comando `git clone` é usado para criar uma cópia local de um repositório remoto. Ele baixa todo o histórico do projeto (commits, branches e arquivos) e configura automaticamente a origem remota (normalmente chamada de `origin`). Ao executar `git clone`, você não apenas obtém os arquivos atuais, mas todo o histórico de versionamento, permitindo trabalhar plenamente com o repositório.

### Sintaxe

```bash
git clone <url-do-repositorio>
```
#### Variantes Comuns:

Clonar em um diretório específico:
```bash
git clone <url> <nome-do-diretorio>
```

Clonar apenas uma branch específica:
```bash
git clone -b <branch> <url>
```

Clonar com profundidade limitada (histórico reduzido):
```bash
git clone --depth 1 <url>
```

Clonar usando SSH:
```bash
git clone git@github.com:usuario/repositorio.git
```

Clonar usando HTTPS:
```bash
git clone https://github.com/usuario/repositorio.git
```

### Diferença entre init e clone
`git init`:
- Cria um novo repositório Git vazio localmente;
- Não possui histórico nem conexão com repositórios remotos;
- Usado para iniciar um projeto do zero.

`git clone`:
- Copia um repositório existente, incluindo todo o histórico e branches;
- Configura automaticamente a origem remota (`origin`);
- Usa-se quando se deseja trabalhar com um projeto já existente, seja para contribuir ou para ter uma cópia local.

### Exemplo Prático

```bash
git clone https://github.com/git/git.git
```
Isso irá:
- 1. Criar uma pasta chamada `git` no diretório atual;
- 2. Baixar todo o repositório do Git, incluindo seu histórico completo;
- 3. Configurar a origem remota para `origin`.

Depois disso, basta entrar no diretório (`cd git`) e começar a trabalhar com o repositório clonado.

### Clonando seu Fork

Um fork é uma cópia de um repositório feita dentro da sua conta (por exemplo, no GitHub).

Passos:

- 1. Faça um fork do repositório original (clicando em "Fork" na interface do GitHub);
- 2. Copie a URL do seu fork;
- 3. Use `git clone` com a URL do seu fork para obter uma cópia local.

```bash
git clone https://github.com/seu-usuario/repositorio.git
```

Opcionalmente, você pode adicionar o repositório original como upstream para manter seu fork atualizado:

```bash
cd repositorio
git remote add upstream https://github.com/usuario-original/repositorio.git
```

E, por fim, para atualizar seu fork com as mudanças do repositório original:

```bash
git fetch upstream
git merge upstream/main
```
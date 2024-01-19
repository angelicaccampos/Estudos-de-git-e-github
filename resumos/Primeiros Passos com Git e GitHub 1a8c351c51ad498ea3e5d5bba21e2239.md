# Primeiros Passos com Git e GitHub

# Criando e Clonando Repositórios

- **Clonando um Repositório Existente**

Para obter uma copia de um diretório:

```bash
$ git clone URL
```

Para mudar o nome da pasta do diretório que voce quer clonar use (opcional):

```bash
$ git clone url clonado
```

- **Transformar um diretório local que não está sob controle de versão, num repositório GIT.**

Primeiro criamos uma pasta pelo terminal dentro de uma pasta, usamos o comando:

```bash
$ mkdir repo-local
```

Para entrar dentro dessa pasta usamos o comando:

```bash
$ cd repo-local/
```

Para transformar essa pasta em um repositório usamos o comando:

```bash
$ git init
```

Sempre fazer a inicialização do git

Para saber as configurações de um repositório é necessário abrir o bash na pasta do repositório e usar os comandos:

```bash
$ cd .git
```

```bash
$ cat config
```

Quando criamos um repositório localmente ele não está vinculado a um repositório remoto .Para saber se o repositório está vinculado remotamente

```bash
$ git remot -v
```

Para adicionar um repositório local a um repo remoto se necessário volte para main usando o comando

```bash
$ cd ..
```

Para adicionar use:

```bash
$ git remote add origin https://github.com/angelicaccampos/remoto.git
```

> *Oque começar com “.” (.git) é uma pasta oculta.*
> 

> *O Git não reconhece pasta ou diretórios vazios. Use .gitkeep para reconhecer arquivos vazios*
> 

> *O diretório .git é responsável pelo controle de versionamento do código.*
> 

# Salvando Alterações no Repositório Local

Para ver a arvore de trabalho:

```bash
$ git status
```

Para adicionar um read.me

```bash
$ touch README.md
```

Agora precisamos adicionar o arquivo a area de preparação 

```bash
$ git add README.md
```

Criei o commit usando 

```bash
$ git commit -m"commit inicial"
```

Para saber todas as informações dos commit

```bash
$ git log
```

Alguns arquivos não devem receber commit, para ignorados:

```bash
$ echo resumos/ > .gitignore
```

Para remover a pasta do git ignore:

```bash
$ echo > .gitignore
```

Se voce quiser adicionar vários arquivos:

```bash
$ git add .
```

> *Este site eu usei para escrever o README.md do meu repositório, para inserir o markdown escrito basta copiar o código fonte e colar no bloco de notas que voce abriu do arquivo README.md e salvar*
> 
> 
> [readme.so](https://readme.so/pt/editor)
> 

> *Use o guia do GitHub para entender o markdown*
> 
> 
> [Guia de início rápido de gravação no GitHub - GitHub Docs](https://docs.github.com/pt/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github)
> 

> *Após fazer o push do readme é possível edita-lo no repositório remoto*
> 

> *Os arquivos podem ser editados com md no editor do próprio repositório no GitHub, essas edições serão salvas como commit*
> 

> *O GitHub tem o vscode online, basta clicar ” .” para abrir e editar os arquivos do repositório, é preciso estar logado na sua conta. Faça o commit direto do vscode*
> 

# Desfazendo Alterações no Repositório Local

Como remover o versionamento 

```bash
$ rm -rf .git
```

Como alterar a ultima mensagem do ultimo commit

```bash
$ git commit --amend -m"add gitigonore"
```

Descartar mudanças de um arquivo:

```bash
$ git restore ARQUIVO
```

Como “juntar” um commit anterior ao posterior

****reset soft****

```bash
$ git reset --soft HEAD~
```

> *As alterações devem ser feitas antes de serem enviadas para o repositório remoto para evitar conflitos*
> 

![Untitled](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled.png)

![Untitled](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%201.png)

![Untitled](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%202.png)

![O ultimo commit some](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%203.png)

O ultimo commit some

****reset mixed****

```bash
$ git reset --mixed HEAD~
```

****reset hard****

```bash
$ git reset --hard HEAD~
```

Como ter um histórico detalhado das alterações:

```bash
$ git reflog
```

Criar vários arquivos de uma vez:

```bash
$ touch resumos/aula01.md resumos/aula02.md
```

Como apagar um arquivo da area de preparação

```bash
$ git restore --staged resumos/aula02.md
```

# Enviando e Baixando Alterações com o Repositório Remoto

Para enviar os arquivos do repositório local para o remoto após fazer a conexão:

```bash
$ git push -u origin main
```

Para salvar as alterações localmente feitas no repositório remoto ou pelo vscode online:

```bash
$ git pull
```

> *As mudanças/commits feitas de forma remota não são salvas localmente*
> 

# Trabalhando com Branches - Criando, Mesclando, Deletando e Tratando Conflitos

Como criar uma branch de teste, após criar o arquivo, adiciona-lo e fazer o commit dele:

```bash
$ git checkout -b teste
```

![Untitled](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%204.png)

![Agora a branch teste está apontando para o commit 4 e a main está apontando para o commit 3](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%205.png)

Agora a branch teste está apontando para o commit 4 e a main está apontando para o commit 3

Como mudar de branch:

```bash
$ git checkout main
```

Para ver os últimos commits de cada branch

```bash
$ git branch -v
```

 Como mesclar a branch main e outra branch:

```bash
$ git merge teste
```

Visualize todas as branches:

```bash
$ git branch
```

Excluindo branches:

```bash
$ git branch -d teste
```

- **Possíveis conflitos de merge (comuns quando se trabalha em equipe)**

Esses conflitos acontece quando temos alterações concorrentes. Quando tem mudanças de varias pessoas na mesma linha do código, o git entende qual a alteração deve ser mantida. 

Quando esse tipo de conflito acontece o git faz voce escolher qual mudança voce quer que seja salva e manda uma mensagem indicando um conflito de merging 

> *Branch = ramo, é uma ramificação do projeto.*
> 

> *Usada para fazer testes sem afetar a branch principal a main*
> 

![Untitled](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%206.png)

![Untitled](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%207.png)

![Untitled](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%208.png)

> *As branches funcionam de forma independente, então as alterações se mantem dentro da branch que foram criadas*
> 

> *Pesquisar as convenções para nomear as branches e as mensagens dos commits*
> 

> *As branches criadas localmente também devem ser enviadas para o repositório remoto*
> 

> *Conflito de merge: ocorrem quando alterações concorrentes são feitas na mesma linha de um arquivo ou quando uma pessoa edita um arquivo e outra pessoa exclui o mesmo arquivo.*
> 

# Trabalhando com Branches - Comandos Úteis no Dia a Dia

Se voce criar um commit remotamente e queira salva-lo localmente sem que seja mesclado com o local 

```bash
$ git fetch origin main
```

Para ver a diferença de conteúdo voce pode usar esse comando para checar o commit feito remotamente  

```bash
$ git diff main origin/main
```

Para apenas baixar esse commit para o local:

```bash
$ git merge origin/main
```

Clonar apenas uma branch

```bash
$ git clone https://github.com/angelicaccampos/Estudos-de-git-e-github.git --branch teste --single-branch
```

Para entrar na nova branch:

```bash
$ cd Estudos-de-git-e-github
```

![Untitled](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%209.png)

Quando deletamos um arquivo essa ação é mostrada no status

![Untitled](Primeiros%20Passos%20com%20Git%20e%20GitHub%201a8c351c51ad498ea3e5d5bba21e2239/Untitled%2010.png)

Para que essa modificação não seja levada para uma branch criada posterior mente usamos esse código

```bash
$ git stash
```

Para listar essas modificações arquivadas:

```bash
$ git stash list
```

```bash
$ git stash apply
```

> *git pull = git fetch + git merge*
>
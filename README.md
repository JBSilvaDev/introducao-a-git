# 0 - Configurando Git to up GitHub with SSH key

## Usar comando 
    $ ssh-keygen -t rsa -b 4096 -C "jbsilva.dev@outlook.com"
    $ ssh-keygen -t ed25519 -C "jbsilva.dev@outlook.com"
## Para pegar a chave use o comando (Entrar na pasta para pegar nome do arquivo correto)
    $ cd ~/.ssh
    $ cat ~/.ssh/id_rsa.pub 
    ou
    $ cd ~/.ssh
    $ cat ~/.ssh/id_ed25519.pub
### A chave SSH ira aparecer no GITBASH, copiar a chave e informar no perfil do github SSH ---- > https://github.com/settings/keys > SSH and GPG keys

## Usar comando apos inserir o SSH no GitHub
    $ eval `ssh-agent -s`
    $ ssh-add ~/.ssh/<Nome do arquivo Id>
    $ git config --global user.email "jbsilva.dev@outlook.com"
    $ git config --global user.name "JB Silva"


## Testando se a chave SSH esta OK upando um arquivo qualquer em um novo diretorio no github
    $ git init
    $ git add .
    $ git commit -m "first commit"
    $ git branch -M main
    $ git remote add origin git@github.com:JB3005/Nome do diretorio.git
    $ git push -u origin main


-----------------------------------------------------------------------

# 1 - [COMANDOS DO DIA-A-DIA]

## Inicializar o git para rastrear arquivos locais de um projeto (sempre que iniciar um novo projeto)
    $ git init

## Verificar se existe alguma pendência a ser adicionada a HEAD
    $ git status
    

## Atualiza o repositório local com as alterações publicadas/atualizadas que já estão no github
    $ git pull origin main

## Exibe o relatorio de alterações realizadas no projeto
    $ gitk

## Adiciona as alterações na HEAD (sempre após alterar os códigos)
    $ git add .

## Comitar as alterações realizadas e já adicionadas (sempre após realizar o comando "git add.")
    $ git commit -m "Mensagem aqui"

## Publicar/subir as alterações para o github para a HEAD main (sempre após realizar o comando "git commit -m "nomedocommit")
    $ git push origin main

-----------------------------------------------------------------------

# 2 - [PRINCIPAIS COMANDOS GIT]

## Configurar o nome de usuario do git'
    $ git config --global user.name "Seu Nome"

## Configurar o email do usuario do git'
    $ git config --global user.email email@example.com

## Em caso de erro no certificado'
    $ git config --global http.sslVerify false

## Exibe todas as alterações realizadas no projeto'
    $ git log

## Exibe a última alteração realizada no projeto'
    $ git log -p -1

## Exibe as chaves e descrição das alterações'
    $ git log --pretty=oneline

## Editar o último commit'
    $ git commit --amend -m "Mensagem aqui (edicao)"

## Remover um arquivo que já foi adicionado add'
    $ git reset HEAD nomedoarquivo.extesao

## Remover as alterações indesejadas realizadas no arquivo especificado para o último commit, caso não tenha sido realizado o git add . ainda'
    $ git checkout -- nomedoarquivo.extensao

## Remover todas as alterações realizadas em todos os arquivos desde o último commit, caso não tenha sido realizado o "git add. " ainda'
    $ git checkout.

## Remover o arquivo especificado localmente'
    $ git rm nomedoarquivo.extensao'

## Exclui uma pasta vazia'
    $ git rmdir

## move arquivos ou pastas de uma origem para um destino informado
    $ git mv <origem> <destino>

## copia um arquivo ou pasta de uma origem para um destino
    $ git cp <origem> <destino>

## Cria uma tag para marcar o projeto com a versão e uma mensagem'
    $ git tag -a "1.0.0" -m "Mensagem aqui"

## Com a chave do commit é possível criar tags de versão para commits anteriores'
    $ git tag -a "0.1.0" CHAVE -m "Mensagem aqui"

## Exibe as informações de uma versão'
    $ git checkout "0.1.0"

## Deleta uma tag de acordo com a versão informada'
    $ git tag -d "0.1.0"

## Subir uma tag para o github'
    $ git push origin main --follow-tags

## Voltar uma pasta no diretorio'
    $ cd../

## Navegar uma pasta dentro do diretorio'
    $ cd nomedapasta/pasta

## Acessar o historico de alterações que já foram adicionadas, mas estão aguardando envio
    $ git diff --staged
para o github'

## Deletar commit que ainda não tenha sido enviado para o GITHUB'
    $ git reset --hard HEAD~1

## Caso queira deletar um commit específico basta usar o comando passando o id do commit'
    $ git reset --hard <sha1-commit-id>

## Visualizar as origens dos remotes /links do git'
    $ git remote -v

## Remover destinos (Links) de repositorios GITHUB'
    $ git remote rm origin

## Clonar um projeto do GITHUB para uma pasta especifica'
    $ git clone https://github.com/... NOME-DA-PASTA

## Criar uma nova pasta com o nome especificado'
    $ mkdir nomeDaPasta

## Criar um novo arquivo com o nome e extensão expecificada'
    $ touch nomeDoArquivo.extensao

## Remover o arquivo. git de uma pasta que está fazendo o rastreamento das alterações'
    $ rm -rf .git

## Lista a relação de "Heads" referente as alterações comitadas, identificar o indice para o qual deseja retornar'
    $ git reflog

## Retornar o projeto para uma "Head" específica, usar o comando acima para encontrar o índice desejado sem alterar os códigos'
    $ git reset HEAD@{indice}

## Voltar os códigos para uma versão de alteração desejada, passando o id da versão'
    $ git reset --hard 66c2555

## Realizar uma atualização forçada do código no github. Subirá mesmo se houver um conflito de versão'
    $ git push --force

## Esconder um arquivo na stash (o arquivo fica congelado para o git)
    $ git stash push <arquivo>

## Listar arquivos que estão na stash do git
    $ git stash list

## Retornar o arquivo da stash (descongelar)
    $ git stash pop <arquivo>

-----------------------------------------------------------------------

# 3 - [TRABALHANDO COM BRANCHS]

## Cria um novo ambiente e já altera o diretorio para o ambiente de teste criado'

### Faça as alterações desejadas no projeto
### Faça os commits
    $ git checkout -b nomedoambienteteste

### Saia do ambiente de teste e volte para o ambiente de produção
### Geralmente o nome do ambiente em produção é main'
    $ git commit -a -m "Mensagem aqui" ou "git commit -am "Mensagem aqui"

### Realize a implementação do ambiente de produção
    $ git checkout main

### deletar ambiente de teste
    $ git merge nomeambienteteste

### Criar uma nova branch no github
    $ git branch -d nomeambienteteste

### Realizar o merge de um arquivo específico de outra branch para a main
### Com a branch main ativa execute o seguinte comando
    $ git push --set-upstream origin MinhaNovaBrach

    $ git checkout brachSecundaria filename.js

-----------------------------------------------------------------------

# 4 - [ATUALIZAR UM FORK]


## 'Criar uma head com o nome desejado o mais comum é usar upstream direcionando para o link originado do fork'
    $ git remote add upstream https://github.com/code.......

## 'Realizar a atualização'
    $ git fetch upstream

## 'Atualizar o repositório local'
    $ git rebase upstream/main

-----------------------------------------------------------------------

# 5 - [TRABALHAR EM EQUIPE]

## A maneira mais fácil de trabalhar em equipe é criar um repositório no GITHUB e convidar um usuário para ser contribuidor:

### 1-Crie o repositório novo ou entre em um já existente
### 2-Vá em settings
### 3-Vá na aba access
### 4-Encontrar o usuário informando seu username e envie o convite
https://github.com/usuario/repositorio/settings/access

-----------------------------------------------------------------------
# 6 Upando e clonando arquivos para o GitHub

## Esse comando só é executado a primeira vez, para subir o projeto para o GITHUB -> Subir o projeto inicial pelo terminal ou manual direto no github
    $ git push -u origin main

## Caso opte em subir o projeto manual OU o mesmo já esteja no gihub é necessário dar um gitclone em todos os terminais locais que forem trabalhar no desenvolvimento
    $ git clone https://github.com/...git NOME-DA-PASTA

## Atualizar o projeto local com as alterações do servidor sempre que for iniciar o desenvolvimento
    $ git pull origin main
-----------------------------------------------------------------------

# 7 - [CRIANDO ALIAS PARA COMANDOS GIT]

## Abrir o arquivo de configuração global
$ git config --global --edit
## Criar uma tag de alias
    [alias]
    s = !git status
    c = !git add --all && git commit -m
    l = !git log --pretty=format:'%C(yellow)%h%C(red)%d %C(white)%s - %C### (cyan)%cn,%C(green)%cr'

## Assim toda vez que for digitado o comando "$ git s" será executado o camando '$ git status' e assim sucessivamente

Fonte:
https://git-scm.com/book/pt-br/v1/Primeiros-passos-Configura%C3%A7%C3%A3o-Inicial-do-Git
https://www.git-scm.com/docs/git-config
https://www.youtube.com/watch?v=WVLhm1AMeYE

# 8 - [CONFIGURAÇÃO INICIAL GIT COM GITBASH]

    git config --global user.name "JB Work"
    git config --global user.email jbsilva.dev@outlook.com
## Configurar para VSCode
    git config --global core.editor "code -w"
## Verificar configurações feitas
    git config --list
## Configurar nova chave GitHub (criando chave SSH)
    ssh-keygen -t rsa -b 4096 -C "jbsilva.dev@outlook.com"
## Pegando chave criada
### Copiar a chave para Gitub
    cat ~/.ssh/id_rsa.pub
## Iniciar o agente ssh em background
    eval `ssh-agent -s`
    ssh-add ~/.ssh/id_ed25519
## Pegando dados do repositorio online GitHub
### Na pasta que deseja clonar os dados execulte o cod:
    git clone <link ssh ou http>

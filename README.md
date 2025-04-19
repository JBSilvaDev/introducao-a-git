Download [aqui](https://git-scm.com/downloads)

# Configurando Git para HTTPS
> Esta configuração sera exibida nos commits realizados pelo git ao gitHub
- `git config --global user.name "JB Silva"`
- `git config --global user.email "jbsilva.dev@outlook.com"`
- `git config --global http.sslVerify false` (evita erro de certificado nos commits)

# Configurando a branch principal
- `git config --global init.defaultBranch main` (configura a branch principal como main)

# Autenticação token para o git HTTPS
- Criar um token no gitHub
  - ir em configurações > developer settings > personal access tokens > tokens (classic) > generate new token
- Copiar o token gerado
- Setar token gerado no git
  - `git config --global credential.helper store`
- Executar `git clone https://github.com/...` inserir usuario e senha (token) quando solicitado
- O token sera salvo em `~/.git-credentials` (pode ser editado ou removido)
- A partir de agora o git ira usar o token para autenticar os commits

# Configuração SSH
- Para verificar se a chave foi criada ou se existe outras chaves no computador, executar:
  - `ls -al ~/.ssh`
- Executar um dos comandos abaixo:
  - `ssh-keygen -t ed25519 -C "jbsilva.dev@outlook.com"`
  - `ssh-keygen -t rsa -b 4096 -C "jbsilva.dev@outlook.com"`
- Inserir uma senha para a chave (opcional)
- Para iniciar a granação da chave SSH, executar:
  - `eval "$(ssh-agent -s)"`
  - `ssh-add ~/.ssh/<Nome do arquivo Id>.pub` (geralmente id_rsa ou id_ed25519)
- Ir para configurações do gitHub > SSH and GPG keys > New SSH key
  - Adicionar um título para a chave (ex: Laptop JB Silva)
  - Selecionar o tipo de chave (Autenticação SSH)
- Colar a chave SSH gerada no computador (arquivo id_rsa.pub ou id_ed25519.pub)
  - Para pegar a chave use o comando (Entrar na pasta para pegar nome do arquivo correto)
    - `cd ~/.ssh`
    - `cat ~/.ssh/id_rsa.pub`
    - *ou*
    - `cat ~/.ssh/id_ed25519.pub`

# Clona um repositório da origem para local
- `git clone link.git`

# Inicializar o git para rastrear arquivos locais de um projeto (sempre que iniciar um novo projeto)
- `git init`

# Verifica situação do repo local em relação ao repo origem
- `git status`

# Adiciona as alterações o repo local
- `git add .` (Adiciona todos itens do projeto)
- `git commit -m "mensagem de commit"` (Registra as alterações no repo local)
- `git add arquivoNome.py` (Adiciona apenas um item)
- `git commit arquivoNome.py -m "mensagem de commit` (Registra as alterações no repo local)
- `git commit . -m "mensagem de commit"` (Adiciona e registra todas as alterações no repo local)

# Envia repo local para repo github
- `git init`
- `git add .` (Adiciona todos itens do projeto)
- `git branch -M main`
- `git commit . -m "mensagem de commit"` (Adiciona e registra todas as alterações no repo local)
- `git remote add origin link.git`
- `git push origin main`

# Salva os registros no repo origem
- `git push` (Salva na branch principal *main*)
- `git push origin branchName` (Salva em branch especifica)

# Atualiza o repositório local com as alterações publicadas/atualizadas que já estão repo origem
- `git pull origin main`
- `git pull link.git`

# Verifica historio de commits realizados
- `git log`
- `git log --oneline`
- `git log --pretty=oneline`

# Altera menssagem do commit
- `git commit --amend -m "Mensagem aqui (edicao)"`

# Restaurar commit anterior
- Obtenha o codigo hash do commit que a ser restaurado com `git log`
- `git restore --source codHash .` (Restaura tudo do commit)
- `git restore --source codHash arquivoNome.py` (Restaura apenas um arquivo do commit)
- Fazer novo commit e salvar no repo origem

# Mostra as diferenças entre os arquivos ou commits
- `git diff`

# Apagando commits
- `git reset --hard commitHash`

# Reverte commit
- `git revert commitHash`

# Reverte add
- `git reset HEAD arquivoNome.py`

# Cria uma tag para marcar o projeto com a versão e uma mensagem'
- `git tag -a "1.0.0" -m "Mensagem aqui"`

# Com a chave do commit é possível criar tags de versão para commits anteriores'
- `git tag -a "0.1.0" commitHash -m "Mensagem aqui"`

# Informações de uma versão'
- `git checkout "0.1.0"` (Lista as versoes)
- `git tag -d "0.1.0"` (Deleta versão)
- `git push origin main --follow-tags` (Upload da versão)

# Branchs no repositorio
- `git branch` (Verifica branchs existentes)
- `git branch -M main` (Seleciona a branch para fazer upload dos arquivos)
- `git checkout -b branchName` (Cria nova branch)
- `git switch branchName`  ou `git checkout branchName` (Alterna entre branchs)
- `git merge branchName` (Mescla branchs com a principal, necessario esta com a main setada)
- `git branch -d branchName` (Deleta branch local)	

# Conflitos de merge

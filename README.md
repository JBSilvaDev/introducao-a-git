Download [Git aqui](https://git-scm.com/downloads)
# Configurando Git to up GitHub with SSH key

## Usar comando 
- `ssh-keygen -t rsa -b 4096 -C "jbsilva.dev@outlook.com"`
- `ssh-keygen -t ed25519 -C "jbsilva.dev@outlook.com"`
## Para pegar a chave use o comando (Entrar na pasta para pegar nome do arquivo correto)
- `cd ~/.ssh`
- `cat ~/.ssh/id_rsa.pub`
- *ou*
- `cd ~/.ssh`
- `cat ~/.ssh/id_ed25519.pub`
### A chave SSH ira aparecer no GITBASH, copiar a chave e informar no perfil do github SSH ---- > https://github.com/settings/keys > SSH and GPG keys

## Usar comando apos inserir o SSH no GitHub
- `eval ssh-agent -s`
- `ssh-add ~/.ssh/<Nome do arquivo Id>`
- `git config --global user.email "jbsilva.dev@outlook.com"`
- `git config --global user.name "JB Silva"`

# Configurando Git para HTTPS
- `git config --global user.name "JB Silva"`
- `git config --global user.email "jbsilva.dev@outlook.com"`
- `git config --global http.sslVerify false` (evita erro de certificado nos commits)

> Inicializar o git para rastrear arquivos locais de um projeto (sempre que iniciar um novo projeto)
- `git init`
> Verifica situação do repo local em relação ao repo origem
- `git status`
> Adiciona as alterações o repo local
- `git add .` (Adiciona todos itens do projeto)
- `git commit -m "menssagem de commit"` (Registra as alterações no repo local)
- `git add arquivoNome.py` (Adiciona apenas um item)
- `git commit arquivoNome.py -m "menssagem de commit` (Registra as alterações no repo local)
- `git commit . -m "menssagem de commit"` (Adiciona e registra todas as alterações no repo local)
> Envia repo local para repo github
- `git init`
- `git add .` (Adiciona todos itens do projeto)
- `git commit . -m "menssagem de commit"` (Adiciona e registra todas as alterações no repo local)
- `git remote add origin link.git`
- `git push origin main`
> Salva os registros no repo origem
- `git push` (Salva na branch princimal *main*)
- `git push origin branchName` (Salva em branch especifica)
> Clona um repositório da origem para local
- `git clone link.git`
> Atualiza o repositório local com as alterações publicadas/atualizadas que já estão repo origem
- `git pull origin main`
- `git pull link.git`
> Verifica historio de commits realizados
- `git log`
- `git log --oneline`
- `git log --pretty=oneline`
> Altera menssagem do commit
- `git commit --amend -m "Mensagem aqui (edicao)"`
> Restaurar commit anterior
- Obtenha o codigo hash do commit que a ser restaurado com `git log`
- `git restore --source codHash .` (Restaura tudo do commit)
- `git restore --source codHash arquivoNome.py` (Restaura apenas um arquivo do commit)
- Fazer novo commit e salvar no repo origem
> Mostra as diferenças entre os arquivos ou commits
- `git diff`
> Apagando commits
- `git reset --hard commitHash`
> Reverte commit
- `git revert commitHash`
> Reverde add
- `git reset HEAD arquivoNome.py`
> Cria uma tag para marcar o projeto com a versão e uma mensagem'
- `git tag -a "1.0.0" -m "Mensagem aqui"`
> Com a chave do commit é possível criar tags de versão para commits anteriores'
- `git tag -a "0.1.0" commitHash -m "Mensagem aqui"`
> Informações de uma versão'
- `git checkout "0.1.0"` (Lista as versoes)
- `git tag -d "0.1.0"` (Deleta versão)
- `git push origin main --follow-tags` (Upload da versão)
> Branchs no repositorio
- `git branch` (Verifica branchs existentes)
- `git checkout -b branchName` (Cria nova branch)
- `git switch branchName` (Alterna entre branchs)
- `git merge branchName` (Mescla branchs com a principal, necessario esta com a main setada)

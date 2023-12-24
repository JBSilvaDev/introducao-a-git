Add colaborador a um projeto direto no site do github
projeto>settings>collaborators

clonar repositorio
repositorio>code>https - copiar link
terminal `git clone link.git`

verificar historico de commits
terminal `git log`
ou historios em uma linha
terminal `git log --oneline`

atualizar o projeto local
terminal `git pull link.git`

verificar alterações no projeto local
terminal `git status`

gravar atualização arquivo local
terminal `git commit arquivoNome.py -m "menssagem de commit"`
ou gravação de todos arquivos locais
terminal `git commit . -m "menssagem de commit"`

salvar o(s) commits na cloud
terminal `git push origin main` (main é o nome da branch)
terminal `git push` (faz push para branch principal)

voltar uma versao de registro
terminal `git status` (para obter o codigo hash do commit desejado)
web clicar em historio (relogio) e copiar o codigo hash do commit desejado
terminal `git restore --source codHash .` (para restaurar tudo deste commit)
terminal `git restore --source codHash arquivoNome.py` (para restaurar apenas um arquivo deste commit)
terminal `git commit . -m "menssagem de commit"`
terminal `git push`

adicionar arquivo ou modificação
terminal `git add arquivoNome.py`
terminal `git commit arquivoNome.py -m "menssagem de commit`
terminal `git push`
adicionar todas modificação de uma vez
terminal `git add .`
terminal `git commit -m "menssagem de commit"`

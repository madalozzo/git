# config

Lista as configurações para o repositório
```
git config --list
```

Lista as configurações globais
```
git config --global --list
```

Define a configuração de nome de usuário e email globalmente
```
git config --global user.name "nome"
git config --global user.email "email"
```
 
Remove as configurações globalmente
```
git config --global --unset user.name
git config --global --unset user.email
git config --global --unset credential.helper

git config --global --unset-all
```

Define o editor padrão globalmente. Lista https://git-scm.com/book/en/v2/Appendix-C:-Git-Commands-Setup-and-Config
```
git config --global core.editor "code --wait"
git config --global core.editor "vim"
```

# init

Inicializa um repositório Git
```
git init
```

Inicializa um repositório Git especificando um branch
```
git init -b [nome_branch]
```

# clone
Faz o clone do repositório remoto para a máquina local
```
git clone [url]
```
# remote

Altera ou adiciona um repositório remoto para um repositório local
```
git remote set-url origin [url_do_repositorio]
```

Adiciona um repositório remoto para um repositório local
```
git remote add origin [url_do_repositorio]
```

Mostra o repositório remoto do repositório atual
```
git remote -v
```

Remove o remote
```
git remote remove [nome_do_remote]
```

# status

Mostra o status do repositório, com o que tem na área de preparação, diretório de trabalho, arquivos não versionados, conflitos de merge e nome do branch atual.
```
git status
git status -s
```

Mostra o status do repositório, incluindo arquivos ignorados pelo .gitignore 
```
git status --ignored
```

# add

Adiciona um arquivo específico na área de preparação
```
git add [nome_arquivo]
```

Adiciona todos os arquivos novos e editados a partir do diretório atual
```
git add .
```

Adiciona todos os arquivos novos, editados e deletados a partir do diretório atual
```
git add --all
```

Adiciona arquivos no modo interativo, permitindo selecionar quais arquivos adicionar
```
git add -i
```

Adiciona apenas os arquivos editados e deletados, não adiciona arquivos novos
```
git add -u
```

# restore
Remove as alterações de um arquivo específico do diretório de trabalho (antes de stage)
```
git restore [nome_arquivo]
```

Remove as alterações do stage de um arquivo específico mas mantém no diretório de trabalho (faz o inverso do git add)
```
git restore --staged [nome_arquivo]
```

Remove todos os arquivos do stage mas mantém no diretório de trabalho
```
git restore --staged .
```

Remove as alterações de todos os arquivos do diretório de trabalho (antes de stage)
```
git restore .
```

# commit

Faz commit das modificações que estão na área de preparação já com a mensagem
```
git commit -m "mensagem"
```

Faz commit das modificações que estão na área de preparação, abrindo um editor para escrever a mensagem
```
git commit
```

Faz commit das modificações que estão na área de preparação sobre o último commit já feito
```
git commit --amend -m "mensagem"
```

# diff
Mostra diferenças desde o último commit
```
git diff
```

Mostra diferenças de um arquivo específico
```
git diff [nome_arquivo]
```

Compara o penúltimo com o último commit
```
git diff HEAD~1 HEAD
```

Compara 2 hashes
```
git diff [commit_hash] [commit_hash]
```

Mostra diferenças staged (adicionadas), igual a --cached
```
git diff --staged
```

Mostra todas as mudanças desde o último commit (staged + unstaged)
```
git diff HEAD 
```

Compara 2 branches
```
git diff [branch1] [branch2]
```

Compara um arquivo entre 2 branches diferentes
```
git diff [branch1] [branch2] [arquivo]
```

# show 
Mostra as mudanças do último commit
```
git show HEAD
```

Mostra as mudanças do commit específico
```
git show [commit_hash]
```

Mostra uma tag
```
git show [tag]
```

Mostra estatísticas de um commit
```
git show --stat [commit_hash]
```

# log
Mostra o log do branch
```
git log 
```

Mostra o log de todos os branches
```
git log --all
```

Mostra os logs de todos os branches com o gráfico na lateral
```
git log --all --graph
```

Mostra os logs, um por linha, pode ser usado em conjunto com os comandos acima
```
git log --oneline
```

Encontra os commits que contêm o arquivo 
```
git log -- [nome_arquivo]
```

Mostra commits com estatísticas de arquivos alterados
```
git log --stat
```

Mostra apenas os commits de um autor
```
git log --author="nome"
```

# fetch
Atualiza o histórico mas não atualiza os arquivos
```
git fetch 
git fetch --all
```

# pull
Atualiza os arquivos do branch local conforme o remote
```
git pull
```

# branch
Mostra os branches locais
```
git branch
```

Mostra os branches remotos
```
git branch -r
```

Mostra os branches locais e remotos
```
git branch -a
```

Mostra os branches locais e remotos com detalhes
```
git branch -vva
```

Mostra os branches que já foram mergeados e não mergeados
```
git branch --merged
git branch --no-merged
```

Cria um branch local. Este comando não faz o pull do branch remoto
```
git branch [nome_do_branch]
```

Renomeia o branch atual
```
git branch -m [nome]
```

Deleta um branch local
```
git branch -d [nome_branch]
```

Deleta um apontamento para branch remoto (não deleta o branch remoto, para isso procure o comando na seção 'push')
```
git branch -r -d origin/[nome_branch]
```

# switch
Cria o branch e muda para ele
```
git switch -c [nome_do_branch]
```

Muda para um branch existente
```
git switch [nome_do_branch]
```

# checkout
Baixa e muda para o branch remoto
```
git checkout -t origin/[nome_do_branch]
```

Cria um branch local e vincula com o branch remoto existente
```
git checkout -b [nome_do_branch_local] origin/[nome_do_branch_remoto]
```

Vincula um branch local existente a um branch remoto
```
git checkout --track origin/[nome_do_branch_remoto]
```

# push
Faz o push para o repositório remoto, desde que o upstream já esteja configurado
```
git push
```

Faz o push para o remote e branch específico e define o apontamento local
```
git push -u origin [branch-remoto]
```

Faz o push de uma tag específica
```
git push origin [nome_tag]
```

Faz o push de todas as tags
```
git push origin --tags
```

Faz o push de todo o repositório para o remote, incluindo tags e branches, útil ao criar um novo repositório a partir de um 'git init' ou migração de outra ferramenta.
```
git push --mirror origin
```

Remove um branch remoto
```
git push --delete origin [nome_branch]
ou 
git push origin :[nome_branch]
```

# revert
Reverte um commit, inclusive os que já foram feitos push
```
git revert [hash_commit]
```

# reset 
Atenção: git reset não é seguro para reverter commits que já foram para branches compartilhados. Em branches compartilhados use o git revert.

Desfaz o último commit e mantém alterações no diretório de trabalho (modo padrão --mixed)
```
git reset HEAD~1
```

Move o HEAD para o commit especificado, alterações ficam em stage
```
git reset --soft [commit]
```

Move o HEAD para o commit especificado, alterações ficam no diretório de trabalho
```
git reset --mixed [commit]
```

Move o HEAD para o commit especificado e apaga tudo depois dele
```
git reset --hard [commit]
```

Descarta tudo que não foi commitado
```
git reset --hard HEAD
```

# merge
Faz o merge do branch indicado para o branch atual
```
git merge [nome_branch]
```

Faz o merge do branch indicado para o branch atual, sem fast-forward, mantendo o histórico do branch
```
git merge --no-ff [nome_branch]
```

# rebase
Faz o rebase do branch indicado (normalmente a main) para o branch atual
Atenção: Só faça rebase no seu branch. Rebase em branches compartilhados causam problemas de histórico
```
git rebase [nome_branch]
```

Continua um rebase após resolver conflitos
```
git rebase --continue
```

Aborta um rebase em andamento
```
git rebase --abort
```

Pula um commit durante rebase
```
git rebase --skip
```

# cherry-pick
Aplica um commit de outro branch no HEAD do branch atual fazendo commit automático
```
git cherry-pick [hash]
```

Aplica um commit de outro branch no HEAD do branch atual sem fazer commit automático
```
git cherry-pick --no-commit [hash]
```

# blame
Mostra o histórico das alterações dos arquivos e seus autores
```
git blame [nome-do-arquivo]
```

# grep
Procura uma string no repositório
```
git grep [texto]
```

Procura uma string ignorando o case
```
git grep -i [texto]
```

Procura uma string e mostra também as linhas ao redor
```
git grep -n -C 2 [texto]
```

Procura uma string em um commit específico
```
git grep [texto] [hash]
```

# clean
Mostra quais arquivos não rastreados seriam apagados (dry-run)
```
git clean -n
```

Apaga arquivos não rastreados
```
git clean -f
```

# stash
Armazena todos os arquivos modificados  
```
git stash
```

Armazena todos os arquivos modificados e também os não rastreados
```
git stash -u
```

Armazena todos os arquivos modificados e aplica um nome 
```
git stash push -m "teste stash"
```

Lista todos os stashes
```
git stash list
```

Mostra o conteúdo do stash
```
git stash show stash@{numero_stash} -p
```

Restaura os arquivos do último stash
```
git stash pop
```

Restaura um stash específico
```
git stash apply stash@{numero_stash} 
```

Descarta o último stash
```
git stash drop
```

Cria um branch novo a partir do stash e faz switch para ele
```
git stash branch [nome_branch] stash@{numero_stash}
```

Apaga um único stash
```
git stash drop stash@{numero_stash}
```

Remove todos os stashes
```
git stash clear
```

# tag
Mostra as tags
```
git tag -n
```

Cria uma tag apontando para o commit atual
```
git tag [nome_tag]
```

Cria uma tag apontando para um commit específico
```
git tag [nome_tag] [hash_commit]
```

Cria uma tag com mensagem
```
git tag -a [nome_tag] -m [mensagem]
```

Deleta uma tag local
```
git tag -d [nome_tag]
```

Envia uma tag específica
```
git push origin [nome_tag]
```

Envia todas as tags
```
git push origin --tags
```

Deleta uma tag remota
```
git push --delete origin [nome_tag]
```

# alias
Cria alias para facilitar os comandos
```bash
git config --global alias.s status
git s
```
O comando acima vai permitir que o 'git status' seja chamado somente com 'git s'

Cria alias para facilitar os comandos
```bash
git config --global alias.lg "log --oneline --graph --all"
git lg
``` 

Pode ser feito para qualquer comando, inclusive para parâmetros
```
git config --global alias.unstage 'reset HEAD --'
```

# .gitignore
O .gitignore é um arquivo na raiz do repositório que contém uma lista de padrões para ignorar outros arquivos. Arquivos já rastreados não são afetados pelo .gitignore.
Exemplo de .gitignore para ignorar logs e um arquivo específico temp.txt
```
*.log
temp.txt
```
Repositório de gitignores: https://github.com/github/gitignore

Use o git status para listar arquivos ignorados pelo .gitignore 
```
git status --ignored
```

Mostra o padrão do gitignore que fez com que o arquivo fosse ignorado
```
git check-ignore -v [nome_arquivo]
```

# bisect
Inicia o processo do bisect
```
git bisect start
```

Marca que o status atual está com o erro ou inconsistência
```
git bisect bad
```

Marca qual hash ou tag está sem o erro
```
git bisect good [hash_ou_tag]
```

Mostra o log do bisect até o momento
```
git bisect log
```

Mostra os prováveis commits até o momento
```
git bisect visualize
```

Finaliza o git bisect e volta para o HEAD
```
git bisect reset
```

# reflog
Exibe o histórico completo de ações e commits, inclusive de branches deletados e resets
```
git reflog
```

Use o git branch ou git reset para alcançar estes estados
```
git branch [novo_branch] [hash]
git reset --hard [hash]
```

# fsck
Verifica se o repositório está íntegro
```
git fsck
```

Referências:
https://git-scm.com/book/en/v2
https://www.atlassian.com/br/git/glossary#commands
https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet
https://github.com/github/gitignore
https://training.github.com/downloads/pt_BR/github-git-cheat-sheet/
(Gramática, ortografia e consistência corrigidas pelo Github Copilot)
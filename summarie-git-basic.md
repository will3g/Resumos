# Ficando ninja no GIT

### **Você tem que saber isso!**

> **HEAD:** Estado atual do nosso código, ou seja, onde o Git nos colocou.

> **Working tree:** Local onde os arquivos realmente estão sendo armazenados e editados.

> **Index:** Local onde o Git armazena o que será commitado, ou seja, o local entre a working tree e o repositório Git em si.

# Como criar um repositório no GitHub? 
>GIF

# Iniciando o monitoramento do GIT

Com o **git init** dizemos para o GIT monitorar a pasta atual.
> **``git init``**

----

> **``git init --bare``**

Com o comando **``git init --bare``** nós criamos um repositório que não terá a **working tree**, ou seja, **``não conterá uma cópia dos nossos arquivos``**. 
Como o **repositório servirá apenas como servidor**, para que outros membros da equipe **sincronizem seus trabalhos**, assim **poupamos espaço de armazenamento**.

# Linkando o repositório local com o repositório remoto do GitHub

Desta forma teremos um link do nosso repositório local com o repositório remoto, que está armazenado em ``caminho/para/o/repositorio.git``

**Comando:**
```
git remote add <url.git>
```

# Adicionando arquivos

Para fazer push em um repositório remoto, é necessário adicionar o arquivo que queremos comitar.

**Comando:**

> **``git add .  ``** Adiciona todos os arquivos que foram alterados ou não comitados para o repositório remoto.

> **``git add <nome-arquivo.extensão>``**  Adiciona um único arquivo (*ou única pasta*) para ser comitado no repositório remoto.

# *Commits*

**Commit:** um commit é a forma de salvar um estado ou versão do nosso código.

> **IMPORTANTE!!! ```Não devemos realizar commit de uma aplicação que não esteja funcionando.```**

 
**Comando:** 
```
git commit -m "mensagem"
```
> - **OBS 1:** Para **desfazer uma alteração** antes de **adicioná-la para commit** (*com git add*), podemos utilizar o comando ```git checkout -- <arquivos>```

> - **OBS 2:** para **desfazer uma alteração após adicioná-la para ``commit``**, antes **precisamos executar o ``git reset HEAD <arquivos>``** e depois podemos desfazê-las com **``git checkout -- <arquivos>``**

> - **OBS 3:** Para **revertermos as alterações realizadas em um commit**, o comando **`git revert`** pode ser a solução. O comando **``git revert``** gera um **novo commit** informando que alterações foram desfeitas

## "Manipulação" de commits

O **git rebase** adiciona o commit antes ou depois de algo já comitado.

**Comando:**
```
 git git rebase <branch>
```
> **Diferença de merge e rebase:** O **merge** **junta os trabalhos** e gera um merge commit. O **rebase** *aplica os commits de **outra branch na branch atual***.

## Histórico de commits:

Podemos verificar o histórico de commits, através do **git log**, podendo ser:
```
git log
git log --oneline
git log -p
git log --pretty="parametros de formatação"
```
**OBS:**
```
git log --graph 
```
Mostra com detalhes e desenhos como o gráfico da sua "**estrutura**" de *branches* e *commits* se encontram atualmente

# Ignorando arquivos

Criando o **``.gitignore``** na **pasta raiz do seu projeto**, podemos ignorar arquivos ou pastas. **Para fazer o Git ignorar** o monitoramento desses arquivos, dentro de **``.gitignore``** passamos o nome (*ou caminho*) desse **"target"**.

# Fazendo **``push``** (ou *"upload"* para os não Íntimos)

Com esse comando enviamos as alterações da nossa aplicação para o repositório remoto. *Claro, depois de adicionar e commitar*. 

**Comando:**

```
git push [repositorio] <branch>
```
Basta substituir **[repositorio]** pelo **nome que demos ao repositório local** ao adicioná-lo.
### **Relembrar é viver!**
> Lembra do **``git remote add origin <url.git>``**?

O origin é o "nome" do seu repositório local, então quando você enviar seus arquivos ficará da seguinte maneira:

```
git push origin <branch>
```

> **Outro exemplo seria ```git push origin develop```**.


# Clonando um repositório remoto

Faz o "**download**" de um repositório pela primeira vez, clonando-o para a sua máquina.

**Comando:**
```
git clone url-do-repositorio.git
```

# Baixando as atualizações do projeto clonado

O **Git** compara os arquivos do repositório remoto com o repositório local e baixa as atualizações (*ou diferença desses arquivos*) para o nosso repositório local.

**Comando:**
```
git pull
```

# Visuzalizando diferenças

> **git diff:** Mostra a diferença antes de adicionar o arquivo. Vemos as alterações em nossos arquivos que não foram adicionadas para commit (*com git add*)

> **git diff <(hash-commit)..(hash-commit)>** mostra a diferença entre esses dois commits. O "**..**" é como se fosse um "**até**".

> **git diff entre arquivos:** É possível **comparar as alterações feitas entre um commit e outro**, através do comando **`git diff <commit1>..<commit2>`**;

> **diff em branchs:** É possível **comparar as alterações entre duas branches** com **``git diff <branch1>..<branch2>``**


# Tagueamento de versões

 Podemos marcar um ponto em nossa aplicação (*ou um marco*).

 **Comando:**
```
git tag -a <versão> -m "mensagem"
```

> **OBS:** A tag gera uma **Release**, ou seja, conseguimos **baixar um arquivo compactado** com o nosso código neste ponto. O **GitHub** nos dá a possibilidade de baixar um arquivo compactado contendo o código no estado em que a **tag** foi gerada.

# Branch

 É uma ``branch`` (*ou ramo*) ou uma linha de commits separada, em que pode ser utilizada para desenvolver funcionalidades independentes. Com ``branches`` separados, podemos evitar que o código de uma funcionalidade interfira em outras.

Se dermos o comando **git branch** vamos visualizar as *branches* locais:
```
master
develop
*titulo
```
> Temos três **branches** e a selecionada é a **``*titulo``**!

Desta forma colocaremos o **``HEAD`` na branch master**, ou seja, faremos com que o nosso código esteja no estado que o deixamos com o último commit na master.
 
> **OBS:** Em seguida, uniremos o trabalho da branch titulo com a branch atual ``(master)``.

## Mudando de branch

Podemos trocar de branch com o comando ``git checkout <nome-da-branch>``.

```
master
develop
*titulo
```

> **Relembrar é viver!** 
>
> Lembre-se de **``git branch``** para **visualizar todos os ramos**.

 # Merge

 Fazer um **merge** (*ou "**mergeiar**"*) é unir o nosso trabalho da branch atual **``(titulo)``** com a branch principal **``(master)``**

 Podemos fazer um merge da seguinte maneira:
```
git checkout master
```
em seguida:
```
git merge titulo
```

> **``ATENÇÃO!``** 
>
>Vai abrir uma nova janela em **``vim``**. Aperte **CTRL+O**, depois **Enter** e por fim **CTRL-X**.

Pronto, já *"mergeiamos"* as duas *branches*, agora precisamos fazer o **push** das alterações.

Então:
```
git checkout master
git push
```

> **Diferença de merge e rebase:** 
>
>O **merge** **junta os trabalhos** e gera um merge commit. O **rebase** *aplica os commits de **outra branch na branch atual***.


# **CRTL+Z** do GIT:

> **``git checkout -- <nome do arquivo>``** Remove o aquivo modificado que está pronto para ser comitado (que ainda não foi adicionado e comitado)

> **``git reset HEAD <node do arquivo>``** Serve para remover o arquivo que já foi adicionado e comitado (**fazendo sair de verdinho para vermlho**)

> **``git reset HEAD``** Depois de adicionar com git add, para desfazer uma alteração, precisamos tirá-la deste estado, com git reset.

> **``git revert <hash do commit>``** Desfaz aquele commit para o commit anterior. Se já realizamos o commit, o comando **git revert** pode nos salvar


# Manipulando arquivos adicionados e commits na memória volátil


> **``git stash``** Serve para salvar o código temporariamente na memóra volátil.

> **``git stash list``** Lista tudo que está salvo temporariamente na memória volátil.

> **``git stash apply``** Pega tudo que foi salvo na memória volátil e coloca no repositorio atual.

> **``git stash apply <numero>``** Por meio do **git stash list** temos noção e podemos selecionar o commit queremos aplicar à este repositório atual.

> **``git stash drop <numero>``** Remove determinado item da stash.

> **``git stash pop``** Aplica e remove a última alteração que foi adicionada na stash

# Viajando no tempo

Com o GIT podemos viajar no tempo em que se encontra o commit selecionado. A partir desse pulo no tempo, temos que criar uma nova branch e fazer um novo commit dentro dessa nova branch.

**Comando:**
```
git log --oneline
git checkout <hash-commit>
```

o comando git checkout serve para deixar o nosso código em determinado estado. A descrição do comando **``git checkout --help``**, em uma tradução livre é: "**Atualizar os arquivos na working tree para ficarem na versão especificada**. [...]". 

Basicamente, podemos deixar o nosso código no estado do último commit de uma branch, de um commit específico, ou mesmo tags.


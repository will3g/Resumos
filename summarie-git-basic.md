**git init --bare:** Com este comando nós criamos um repositório que não terá a working tree, ou seja, não conterá uma cópia dos nossos arquivos. Como o repositório servirá apenas como servidor, para que outros membros da equipe sincronizem seus trabalhos, poupamos espaço de armazenamento desta forma.
___

**HEAD:** Estado atual do nosso código, ou seja, onde o Git nos colocou.
___

**Working tree:** Local onde os arquivos realmente estão sendo armazenados e editados.
___

**Index:** Local onde o Git armazena o que será commitado, ou seja, o local entre a working tree e o repositório Git em si.
___

**Commit:** um commit é a forma de salvar um estado ou versão do nosso código, comando git commit. **IMPORTANTE!!!** ```Não devemos realizar commit de uma aplicação que não esteja funcionando.```

**OBS:**
 Para *desfazer uma alteração* antes de **adicioná-la para commit** (*com git add*), podemos utilizar o comando ```git checkout -- <arquivos>```;

 **OBS2:** para desfazer uma alteração após adicioná-la para commit, antes precisamos executar o git reset HEAD <arquivos> e depois podemos desfazê-las com git checkout -- <arquivos>;

 **OBS3:** Para revertermos as alterações realizadas em um commit, o comando `git revert` pode ser a solução. O comando **git revert** gera um **novo commit** informando que alterações foram desfeitas;

___

**git add . ou git add <nome-arquivo.extensão>**: adiciona arquivos para serem commitados com git add . ou git add <nome-arquivo.extensão>.
___

**histórico de commits**: Podemos verificar o histórico de commits, através do **git log**, podendo ser >
```
git log
git log --oneline
git log -p
git log --pretty="parametros de formatação"
```
OBS: 
```
git log --graph 
```
Mostra com detalhes e desenhos como o gráfico da sua "estrutura" de branches e commits se encontram atualmente
___

**Ignorar arquivos ou pastas:** Criando o .gitignore na pasta raiz do seu projeto, podemos ignorar arquivos ou pastas. Para fazer o Git ignorar o monitoramento desses arquivos, dentro de .gitignore passamos o nome (ou caminho) desse "target".
___

**Linkando repositório local com repositório remoto** git remote add nome-repositorio caminho/para/o/repositorio: Desta forma teremos um link do nosso repositório local com o repositório remoto, que chamamos de nome-repositorio, que está armazenado em caminho/para/o/repositorio.
___

**git push [repositorio] master:** Desta forma, nós enviamos as alterações em nosso branch master para o repositório remoto. Basta substituir [repositorio] pelo nome que demos ao repositório ao adicioná-lo. Já para trazer os dados que estiverem no repositório remoto, podemos utilizar o git pull [repositorio] master.
___

**git clone:** Faz o download de um repositório pela primeira vez, clonando-o com o comando git clone <url.git>
___

**git pull:** Atualiza o nosso repositório local (já clonado) com os dados no repositório remoto, utilizando git pull;
___
**git push:** Com esse comando enviamos nossa alteração de código para o GitHub. 

  ```git push origin <nome-branch> > Exemplo, git push origin develop```
___

**Como criar um repositório no GitHub:**  GIF


___

**git diff:** > Mostra a diferença antes de adicionar o arquivo. Vemos as alterações em nossos arquivos que não foram adicionadas para commit (*com git add*)

**git diff <(hash-commit)..(hash-commit)>** mostra a diferença entre esses dois commits. O ".." é como se fosse um "até".

**git diff entre arquivocs:** É possível comparar as alterações feitas entre um commit e outro, através do comando `git diff <commit1>..<commit2>`;

**diff em branchs:** É possível comparar as alterações entre duas branches com ``git diff <branch1>..<branch2>``
___

**git tag -a <versão> -m "mensagem" >**  Dessa forma marcamos um ponto em nossa aplicação (ou um marco).

**OBS:** A tag gera uma Release, ou seja, conseguimos baixar um arquivo compactado com o nosso código neste ponto. O GitHub nos dá a possibilidade de baixar um arquivo compactado contendo o código no estado em que a tag foi gerada.

___

# Branch

 É uma branch (*ou ramo*) ou uma linha de commits separada, em que pode ser utilizada para desenvolver funcionalidades independentes. Com branches separados, podemos evitar que o código de uma funcionalidade interfira em outras.

 
**Merge:** Podemos fazer um merge da seguinte maneira ``git checkout master`` em seguida ``git merge titulo``.
```
git checkout master  // branch titulo
git merge titulo     // branch master
```
 Desta forma colocaremos o HEAD na branch master, ou seja, faremos com que o nosso código esteja no estado que o deixamos com o último commit na master. Depois, uniremos o trabalho da branch titulo com a branch atual (master).

 **git rebase**: O ``git rebase <branch>`` Adiciona o commit no antes ou depois de algo já comitado.
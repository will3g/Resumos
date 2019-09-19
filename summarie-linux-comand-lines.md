# **Lista de comandos mais usados no Linux**

 Numa manutenção de rotina usa-se os comandos em momentos de **monitoração** e (ou) **urgência**:

> **ls**: Lista todos os arquivos do diretório
    
> **df**: Mostra a quantidade de espaço usada no disco rígido
    
> **top**: Mostra o uso da memória
    
> **cd**: Acessa uma determinada pasta (diretório)
    
> **mkdir**: Cria um diretório
    
> **rm**: Remove um arquivo/diretório
    
> **cat**: Abre um arquivo
    
> **vi**: Abre o editor vi (lê-se viai) para editar/criar arquivos

## **Comandos de Controle e Acesso**
> **exit**: Terminar a sessão, ou seja, a shell (mais ajuda digitando man sh ou man csh)
    
> **logout**: Des-logar, ou seja, terminar a sessão atual, mas apenas na C shell e na bash shell
    
> **passwd**: Mudar a password do nosso utilizador (usuário logado)
    
> **rlogin**: Logar de forma segura em outro sistema Unix/Linux
    
> **ssh**: Sessão segura, vem de secure shell, e permite-nos logar num servidor remoto através do protocolo ssh
    
> **slogin**: Versão segura do rlogin
    
> **yppasswd**: Mudar a password do nosso utilizador nas páginas amarelas (yellow pages)


## **Comandos de Comunicações**

> **mail**: Enviar e receber emails
> **mesg**: Permitir ou negar mensagens de terminal e pedidos de conversação (talk requests)
> **pine**: Outra forma de enviar e receber emails, uma ferramenta rápida e prática
> **talk**: Falar com outros utilizadores que estejam logados no momento
> **write**: Escrever para outros utilizadores que estejam logados no momento


## **Comandos de Ajuda e Documentação**

> **apropos**: Localiza comandos por pesquisa de palavra-chave

> **find**: Localizar arquivos, como por exemplo: find . -name *.txt -print, para pesquisa de arquivos de texto do diretório atual

> **info**: Abre o explorador de informações

> **man**: Manual muito completo, pesquisa informação acerca de todos os comandos que necessitemos de saber, **como por exemplo: man find**

> **whatis**: Descreve o que um determinado comando é/faz

> **whereis**: Localizar a página de ajuda (man page), código fonte, ou arquivos binários, de um determinado programa


## **Comandos de Edição de Texto**

> **emacs**: Editor de texto screen-oriented

> **pico**: Editor de texto screen-oriented, também chamado de nano

> **sed**: Editor de texto stream-oriented

> **vi**: Editor de texto full-screen

> **vim**: Editor de texto full-screen melhorado (vi improved)


## **Comandos de Gestão de Arquivos e Directorias**

> **cd**: Mudar de diretório atual, como por exemplo cd diretório, cd .., cd /

> **chmod**: Mudar a proteção de um arquivo ou diretório, como por exemplo chmod 777, parecido com o attrib do MS-DOS

> **chown**: Mudar o dono ou grupo de um arquivo ou diretório, vem de change owner

> **chgrp**: Mudar o grupo de um arquivo ou diretório

> **cmp**: Compara dois arquivos

> **comm**: Seleciona ou rejeita linhas comuns a dois arquivos selecionados

> **cp**: Copia arquivos, como o copy do MS-DOS

> **crypt**: Encripta ou Descripta arquivos (apenas CCWF)

> **diff**: Compara o conteúdo de dois arquivos ASCII

> **file**: Determina o tipo de arquivo

> **grep**: Procura um arquivo por um padrão, sendo um filtro muito útil e usado, **por exemplo** um **cat a.txt** | **grep ola** irá **mostrar-nos apenas as linhas do arquivo a.txt** que contenham a palavra ***“ola”***

> **gzip**: Comprime ou expande arquivo

> **ln**: Cria um link a um arquivo

> **ls**: Lista o conteúdo de uma diretório, semelhante ao comando dir no MS-DOS

> **lsof**: Lista os arquivos abertos, vem de list open files

> **mkdir**: Cria uma diretório, vem de make directory”

> **mv**: Move ou renomeia arquivos ou diretórios

> **pwd**: Mostra-nos o caminho por inteiro da diretório em que nos encontramos em dado momento, ou seja um pathname

> **quota**: Mostra-nos o uso do disco e os limites

> **rm**: Apaga arquivos, vem de remove, e é semelhante ao comando del no MS-DOS, é preciso ter cuidado com o comando rm * pois apaga tudo sem confirmação por defeito

> **rmdir**: Apaga diretório, vem de remove directory

> **stat**: Mostra o estado de um arquivo, útil para saber por exemplo a hora e data do último acesso ao mesmo

> **sync**: Faz um **flush aos buffers do sistema de arquivos**, **sincroniza os dados no disco com a memória**, ou seja escreve todos os dados presentes nos buffers da memória para o disco

> **sort**: **Ordena**, **une** ou **compara texto**, podendo ser usado para extrair informações dos arquivos de texto ou mesmo para ordenar dados de outros comandos como por exemplo listar arquivos ordenados pelo nome

> **tar**: Cria ou extrai arquivos, muito usado como programa de backup ou compressão de arquivos

> **tee**: Copia o input para um standard output e outros arquivos

> **tr**: Traduz caracteres

> **umask**: Muda as proteções de arquivos

> **uncompress**: Restaura um arquivo comprimido

> **uniq**: Reporta ou apaga linhas repetidas num arquivo

> **wc**: Conta linhas, palavras e mesmo caracteres nu> arquivo


## **Exibição ou Impressão de Arquivos**

> **cat**: Mostra o conteúdo de um arquivo, como o comando type do MD-DOS, e é **muito usado também para concatenar arquivos**, como **por exemplo** fazendo ```cat a.txt b.txt > c.txt”``` para **juntar** o **arquivo** ```a.txtb.txt``` num único de nome ```c.txt```

> **fold**: Encurta, ou seja, faz um fold das linhas longas para caberem no dispositivo de output

> **head**: Mostra as primeiras linhas de um arquivo, como por exemplo com head -10 a.txt, ou usado como filtro para mostrar apenas os primeiros x resultados de outro comando

> **lpq**: Examina a spooling queue da impressora

> **lpr**: Imprime um arquivo

> **lprm**: Remove jobs da spooling queue da impressora

> **more**: Mostra o conteúdo de um arquivo, mas apenas um ecrã de cada vez, ou mesmo output de outros comandos, **como por exemplo** ```ls | more```

> **less**: Funciona como o more, mas com menos features, menos características e potenciais usos

> **page**: Funciona de forma parecida com o comando more, mas exibe os ecrãs de forma invertida ao comando more

> **pr**: Pagina um arquivo para posterior impressão

> **tail**: Funciona de forma inversa ao comando head, mostra-nos as últimas linhas de um arquivo ou mesmo do output de outro comando, quando usado como filtro

> **zcat**: Mostra-nos um arquivo comprimido

> **xv**: Serve para exibir, imprimir ou mesmo manipular imagens

> **gv**: Exibe arquivos **ps** e **pdf**

> **xpdf**: Exibe arquivos **pdf**, usa o **gv**


## **Comandos de Transferência de Arquivos**

> **ftp**: Vem de file transfer protocol, e permite-nos, usando o protocolo de transferência de arquivos ftp, transferir arquivos entre vários hosts de uma rede, como a um servidor de ftp para enviar ou puxar arquivos

> **rsync**: Sincroniza de forma rápida e flexível dados entre dois computadores

> **scp**: Versão segura do rcp


## **Comandos de Notícias ou Rede**

> **netstat**: Mostra o estado da rede

> **rsh**: Um shell em outros sistemas UNIX

> **ssh**: Versão segura do rsh

> **nmap**: Poderoso port-scan, para visualizarmos portas abertas num dado host

> **ifconfig**: Visualizar os ips da nossa máquina, entre outras funções relacionadas com ips

> **ping**: Pingar um determinado host, ou seja, enviar pacotes icmp para um determinado host e medir tempos de resposta, entre outras coisas


## **Comandos de Controlo de Processos**

> **kill**: Mata um processo, como por exemplo kill -kill 100 ou kill -9 100 ou kill -9 %1

> **bg**: Coloca um processo suspenso em background

> **fg**: Ao contrário do comando bg, o fg traz de volta um processo ao foreground

> **jobs**: Permite-nos visualizar jobs em execução, quando corremos uma aplicação em background, poderemos ver esse job com este comando, e termina-lo com um comando kill -9 %1, se for o jobnúmero 1, por exemplo

> **top**: Lista os processos que mais cpu usam, útil para verificar que processos estão a provocar um uso excessivo de memória, e quanta percentagem decpu cada um usa em dado momento
    
> **^y**: Suspende o processo no próximo pedido de input

> **^z**: Suspende o processo actual


## **Comandos de Informação de Estado**

> **clock**: Define a hora do processador

> **date**: Exibe a data e hora

> **df**: Exibe um resumo do espaço livre em disco

> **du**: Exibe um resumo do uso do espaço em disco

> **env**: Exibe as variáveis de ambiente

> **finger**: Pesquisa informações de utilizadores

> **history**: Lista os últimos comandos usados, muito útil para lembrar também de que comandos foram usados para fazer determinada acção no passado ou o que foi feito em dada altura

> **last**: Indica o último login de utilizadores

> **lpq**: Examina a spool queue

> **manpath**: Mostra a path de procura para as páginas do comando man

> **printenv**: Imprime as variáveis de ambiente

> **ps**: Lista a lista de processos em execução, útil para saber o pid de um processo para o mandar abaixo com o comando kill, entre outras coisas

> **pwd**: Mostra-nos o caminho por inteiro do diretório em que nos encontramos em dado momento, ou seja um pathname

> **set**: Define variáveis da sessão, ou seja, da shell, na C shell, na bash ou na ksh

> **spend**: Lista os custos ACITS UNIX até à data time Mede o tempo de execução de programas

> **uptime**: Diz-nos há quanto tempo o sistema está funcional, quando foi ligado e o seu uptime

> **w**: Mostra-nos quem está no sistema ou que comando cada job está a executar

> **who**: Mostra-nos quem está logado no sistema

> **whois**: Serviço de diretório de domínios da Internet, permite-nos saber informações sobre determinados domínios na Internet, quando um domínio foi registado, quando expira, etc

> **whoami**: Diz-nos quem é o dono da shell



## **Comandos de Processamento de Texto**

> **abiword**: Processador de Texto Open Source

> **addbib**: Cria ou modifica bases de dados 
bibliográficas
> **col**: Reverte o filtro a line feeds

> **diction**: Identifica sentenças com palavras

> **diffmk**: Marca diferenças entre arquivos

> **dvips**: Converte arquivos TeX DVI em arquivos PostScript

> **explain**: Explica frases encontradas pelo programa diction

> **grap**: Preprocessador pic para desenhar gráficos, usado em tarefas elementares de análises de dados

> **hyphen**: Encontra palavras com hífens

> **ispell**: Verifica a ortografia de forma interativa

> **latex**: Formata texto em LaTeX, que é baseado no TeX

> **pdfelatex**: Para documentos LaTeX em formato pdf

> **latex2html**: Converter LaTeX para html

> **lookbib**: Encontra referências bibliográficas

> **macref**: Cria uma referência cruzada listando arquivos de macros nroff/troff

> **ndx**: Cria uma página de indexação para um documento
> **neqn**: Formata matemáticas com nroff

> **nroff**: Formata texto para exibição simples

> **pic**: Produz simples imagens para troff input

> **psdit**: Filtra um output troff para a Apple LaserWriter

> **ptx**: Cria uma indexação permutada mas não em CCWF

> **refer**: Insere referências de bases de dados bibliográficas

> **roffbib**: Faz o run off de uma base de dados bibliográfica

> **sortbib**: Ordena uma base de dados bibliográfica

> **spell**: Encontra erros de ortografia

> **style**: Analisa as características superficiais de um documento

> **tbl**: Formata tabelas para nroff/troff

> **tex**: Formata texto

> **tpic**: Converte arquivos pic source em comandos TeX

> **wget**: Permite-nos fazer o download completo de páginas web, com todos os arquivos, de forma fácil e não interactiva, sem exigir por isso presença do utilizador, respeitando também o arquivorobots.txt


## **Web**

> **html2ps**: Conversor de html para ps

> **latex2html**: Conversor de LaTeX para html

> **lynx**: Navegador web baseado em modo de texto, ou seja, é um web browser que nos permite abrir todo o tipo de páginas visualizando apenas os textos elinks, não vendo assim as imagens, e sendo por isso bastante rápido, mas requere prática para ser manuseado

> **netscape**: Navegador web da Netscape

> **sitecopy**: Aplicação que nos permite manter fácil e remotamente web sites

> **weblint**: Verificador de sintaxes e de estilos html



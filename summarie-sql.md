# Comandos MySQL via terminal

## Neste resumo se encontra alguns dos comandos mais usados e uma explicação básica deles.

# **DQL**: 

É a parte em SQL mais utilizada e que vamos abordar com foco nesse artigo. O comando **SELECT** permite ao usuário especificar uma consulta (query) como uma descrição do resultado desejado. Esse comando é composto de várias claúsulas e opçãoes, possibilitando elaborar consultas das mais simples as mais elaboradas.

# **Palavras chaves em SQL:**

**FROM ->** utilizada para especificar a tabela que vamos selecionar os registros.

**WHERE ->** utilizada para especificar as condições que devem reunir os registros que serão selecionados.

**GROUP BY ->** utilizada para separar os registros selecionados em grupos específicos.

**HAVING ->** utilizada para separar os registros selecionados em grupos específicos.

**ORDER BY ->** utilizada para ordenar os registros selecionados com uma ordem específica.

**DISTINCT ->** utilizada para selecionar dados sem repetição.

**UNION ->** utilizada para combinar os resultados de duas consultas SQL em uma única tabela para todas as linhas correspondentes.

# **Operações lógicas:**

**Menor:** ```<```

**Menor ou igual:** ```<=```

**Igual:** ```=```

**Maior:** ```>```

**Maior ou igual:** ```>=```

**Diferente:** ```<>```

**Between:** utilizado para especificar valores dentro de um intervalo fechado.

**Like:** utilizado na comparação de um modelo e para especificar registros de um banco de dados ``like`` e a extensão ``%``, significa buscar todos os resultados com o mesmo início da extensão (``vamos ver com calma mais adiante``).

**In:** utilizado para verificar se o valor procurado está dentro de uma lista. Exemplo: ```valor In(1,2,3,4);```

# Funções de agregação

Funções de agregação (como os exemplos a seguir) são usadas dentro de uma cláusula ``SELECT`` em grupos de registros para devolver um único valor que se aplica a um grupo de registros.

**AVG:** utilizado para calcular a média dos valores de um campo selecionado.

**COUNT:** utilizado para devolver o número de registros de seleção.

**SUM:** utilizado para devolver a soma de todos os valores de uma coluna específica.

**MAX:** utilizado para devolver o valor mais alto de um campo especificado.

**MIN:** utilizado para devolver o valor mais baixo de um campo especificado.

# Começando a entender melhor o **MySQL**

## Para entrar no **MySQL**: 
```
mysql -u root -p 
```
## Exibindo os **databases** existentes: 
```
show databases;
```
## Escolhendo um **database** para ser utilizado:
```
use {nome-do-banco};
```
## Exibindo as tabelas existentes:
```
show tables;
```
## Criando um banco de dados:
```
create database {nome-do-banco};
```
## Criando uma tabela para o seu banco de dados existente:
```
create table {nome-tabela} ({atributos});
```
**Exemplo**:  
```
                          -> Nome da coluna
                          |
                          |   -> Tipo inteiro
                          |   |
                          |   |     -> Auto incremental
                          |   |     |
                          |   |     |               -> Chave primária
                          |   |     |               |
    create table COMPRAS (id int auto_increment primary key, valor double, data date, descricao varchar(255), recebido boolean);
                    |                                                                     |        |
                    -> Nome da tabela                                                     |        -> Tipo (setado com um MÁX de 255 caracteres)
                                                                                           -> Nome da tabela

```

## Inserindo valores na tabela:

**Query:**
```
    insert into {nome-tabela} values ({passando os valores});
```

**Lembrando que as tabelas existentes são: ```valor(double), data(date), descricao(varchar(255)), recebido(boolean)```**

**Exemplo**:  

```
insert into COMPRAS values (100.0, 2019-05-12, 'compras de dezembro', 1);
```
**ou melhor...**
```
insert into COMPRAS (valor, data, descricao, recebido) values (100.0, '2019-05-12', 'compras de dezembro', 1);
```

# **Consultas**

## As consultas em banco de dados SQL tem um comando inicial chamado **select**:

**Query:**
```
select {coluna ou tudo} from {tabela-desejada};
```

**Exemplo**:
```
      -> Executa a operação de consulta
      |    -> Seleciona todas as colunas
      |    |         -> Tabela que será realizada a consulta
      |    |         |
    select * from compras;
```

## Selecionando colunas:

**Query:**
```
select {nome-coluna-a, nome-coluna-b, nome-coluna-c} from {nome-tabela};
```

**Exemplo**:
```
       -> Selecione
       |     -> A coluna valor
       |     |     -> e a coluna data
       |     |     |           -> da tabela compras
       |     |     |           |
    select valor, data from compras;
```

## Fazendo operações aritméticas:

**Query:**
```
    select {coluna-a ```operação``` {valor desejado}} from {nome-tabela};
```

**Exemplo**:
```
                        -> Operação matemática
                        | -> Valor desejado
                        | |
    select valor, valor * 3, data from compras;
```

## Filtros de busca e condições:

**OBS:** É possível utilizar **```>=```** ```(maior ou igual)```, **```<=```** ```(menor ou igual)``` e **```<>```** ```(diferente)```

**Query:**
```
select {parâmetro} from {tabela} where {condição}
```

**Exemplo**:
```
                                    -> Condição do filtro
           -> Selecione tudo        |
           |                        |
    select * from compras where valor > 1000;   }---> Vai filtrar todos os valores maior que 1000
                    |
                    -> Tabela compras

```
```

    select * from compras where produto=10;     }---> Vai exibir todas as informações do produto 10

```
```
    select * from compras where (valor > 1000 and valor < 3000) or (data < '2019-02-12');
```

## Selecionando dados e "**renomeando**" na query e utilizando **GroupBy**:

```Essa query no final vai juntar as informações dessas três colunas```
```
select {coluna-a} as {col-a}, {coluna-b} as {col-b}, {coluna-c} as {col-c} from {nome-tabela} col-a, col-b, col-c;
```

**Exemplo**:
```
    select descricao as desc, month(data) as mes, year(data) as ano, sum(valor) as preço, count(valor) as qtd, round(avg(valor)) from compras group by mes, ano order by ano, mes;
```

# Usando comando **like**:

**OBS**: O caractere **```%```** funciona como um coringa, não importa o que houver para frente (ou para trás), vai buscar no sistema todos os celulares existentes.

```
           -> Selecione tudo
           |
           |         -> Tabela compras      -> "Pegue"
           |         |                      |
           |         |                      |       -> Onde existir essa string
           |         |      -> Onde         |       |
           |         |      |               |       |
    select * from compras where descricoes like '%celular%';    }---> Vai buscar no sistema todos os celulares
                                    |            |       |
                                    |            |       -> Ignore tudo depois dessa string
                                    |            |
                                    |            -> Ignore tudo antes dessa string
                                    |
                                    -> Na coluna descricoes
```

# Usando tipo **boolean** em consultas:
**Query:**
```
    select {parametro} from {tabela} where {condição};
```

**Exemplo**:
```
    select * from compras where recebido=1;
```
```
    select * from compras where recebido=true;
```
```
    select * from compras where recebido is true;
```

# Importando arquivo SQL por linha de comando:
**Query:**
```
    mysql -u root -p {nome-banco} < {nome-arquivo}.sql
```
# Consultas efetuadas com o comando **between**:
```
    select {paramentro} from {nome-banco} where ({condição_a} between {condição_b});
```
**Exemplo**:
```
    select * from compras where (valor>=200 and valor<=700);
```
```
    select * from compras where (valor between 200 and 700);
```
```
    select * from compras where (data between '2018-02-25' and '2019-12-21');
```

# Atualizando tabelas:
**Query:**
```
    update {nome-tabela} set {onde-você-quer-alterar};
```
**```Dessa maneira, todos os registros na coluna descricoes vai ser alterado para "campo emergencial"```**
```
                    -> Selecione
                    |     -> Coluna descriocoes
                    |     |
    update compras set descricoes='compra emergencial';
```
Obs: ```Na query acima estamos passando os comandos para o SQL alterar (ou modificar) os dados da coluna descricoes de todos os registros.```

## Com **ID** ficaria assim:
```
    update compras set descricoes='compra emergencial' where id=2;
```
Obs: ```Na query acima estamos passando os comandos para o SQL alterar (ou modificar) a coluna descricoes do ID (ou registro) número 2 e deixe os demais como estão.```

## Atualizando as compras com base em datas:
```
    update compras set descricoes='compra comum' where data not between '2019-10-01' and '2020-01-20';
```
Obs: ```O update foi utilizado com o where para restringir as compras que serão afetadas pela alteração que desejamos.```

# Comando **delete**:

## Excluindo todas as compras efetuadas antes de 2019:
```
    delete from compras where data < '2019-01-01';
```
Obs: ```Podemos utilizar o sinal de menor "<" e maior ">", mas no caso utilizado estamos dizendo que queremos apagar todos os dados que são menores que a data 2019-01-01.```

## Excluindo um ID específico (ou registro):
```
    delete from compras where id=44;
```
Obs: ```Vai excluir a linha específica do banco de dados.```

## **ATENÇÃO!!!** Nunca faça isso (a não ser que te passaram para fazer):
```
    delete from compras;
```
Obs: ```Com esse comando vamos excluir a tabela compras, então tome cuidado.```

# Exibindo a estrutura da tabela:
```
    desc compras;
```
Obs: ```Dessa forma vai mostrar a tabela e seus atríbutos, sem exibir os dados.```

# Verificando se tem algum campo nulo em nosso BD:
```
    select * from compras where descricoes is null;
```

# Inserindo um novo campo como nulo: 
```
    insert into compras (valor, data, descricoes, recebido) values (100.0, '2019-12-20', null, 1);
```

# Alterando uma coluna para não aceitar campo nulo:
```
    alter table compras modify column descricoes text not null;
```
Obs: ```Em  "...modify column descricoes text not null;" estamos passando para o SQL que queremos que esta coluna seja alterada para não ter valor nulo.```

# Adicionando um valor default(padrão) à coluna:
```
    alter table compras modify column recebido tiny int(1) default '0';
```
Obs: ```Estamos dizendo para o MySQL para alterar a coluna recebido(que é um boolean) na tabela compras, para um valor padrão '0' (ou false).```

# Criando uma nova coluna para a estrutura da nossa tabela:
```
    alter table compras add column forma_pag enum('cartao', 'boleto', 'dinheiro');
```
Obs: ```O "enum" define os valores padrões, só eses valores serão aceitos nessa coluna.```

# Inserindo valores nessa nova coluna:
```
    insert into compras (valor, data, descricoes, forma_pag) values (100.0, '2019-11-26', 'celular', 'cartao');
```

# Caso queiramos alterar a coluna:
```
    alter table compras change forma_pag enum('cartao', 'boleto');
```
Obs: ```O "change" modifica a coluna em outras palavras, recebe a coluna que quereos alterar```

# Atualizando todos os valores nulos da coluna forma_pag:
```
    update compras set forma_pag='boleto' where forma_pag is null;
```
Obs: ```Coloque os valores(ou troque) nulos dessa coluna para o valor 'boleto'. Logo todos os valores nulos se tornam 'boletos'.```

# Somando valores de uma coluna:
```
    select sum(valor) from compras;
```
##  Apartir de uma data:
```
    select sum(valor) from compras where data > '2019-10-01';
```
## Somando o número de vendas (não o valor):
```
    select count(valor) from compras where data > '2019-10-01';
```
## Colando número de vendas e valor na mesma exibição de dados:
```
    select count(valor) sum(valor) from compras where data > '2019-10-01';
```
## Mudando nomes na query para deixa-la mais legível:
```
    select sum(valor) as total_valor, count(valor) as quantidade_vendas from compras;
```
Obs: ``O "as" que faz a mudança de nome, exemplo: sum(valor) agora é total_valor. E apartir desse comando o total_valor e quantidade_vendas são atribuidos como nome das colunas do resultado.``

## Somando os valores das vendas recebidas:
```
    select sum(valor) from compras where recebido=1;
```
## Somando os valores recebidos e não recebidos, exibindo de forma organizada (utilizando **group by**):
```
    select recebido, sum(valor) from compras where data > '2019-10-01' group by recebido;
```
##  E caso queiramos usar datas, ficaria:
```
    select recebido, sum(valor) from compras where data > '2019-10-01' group by recebido;
```
##  Selecioando mês, ano e somando valor:
```
    select month(data), year(data), sum(valor) from compras group by month(data), year(data);
```
##  Deixando o ano e mês em ordem crescente:
```
    select month(data), year(data), sum(valor) from compras group by month(data), year(data) order by year(data), month(data);
```

# O comando **Inner join**:

Exemplo:
```
    select * from pessoa inner join paises on pessoa.id=paises.id;
```

## **Relembrar é viver**:

**Inner join**: é a junção interna usando as consultas equivalentes resultantes das intersecções das duas tabelas, ou seja, as duas linhas que as duas tabelas tem em comum.

**On**: É utilizado quando se tem nomes de colunas diferentes ou iguais entre as tabelas.

**Using**: É utilizado quando ambas tabelas compartilham uma coluna com o mesmo nome.
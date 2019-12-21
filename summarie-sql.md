# Comandos MySQL via terminal

Neste resumo se encontra alguns dos comandos mais usados e uma explicação básica deles.

-------------------------------

Para entrar no **MySQL**: 
- > mysql -u root -p 

Exibindo os **databases** existentes: 
- > show databases;

Escolhendo um **database** para ser utilizado:
- > use {nome-do-banco};

Exibindo as tabelas existentes:
- > show tables;

Criando um banco de dados:
- > create database {nome-do-banco};

Criando uma tabela para o seu banco de dados existente:
- > create table {nome-tabela} ({atributos});

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

Inserindo valores na tabela:
- > insert into {nome-tabela} values ({passando os valores})

Lembrando que as tabelas existentes são: ```valor(double), data(date), descricao(varchar(255)), recebido(boolean)```

**Exemplo**:  

```
insert into COMPRAS values (100.0, 2019-05-12, 'compras de dezembro', 1);
```
**ou melhor...**
```
insert into COMPRAS (valor, data, descricao, recebido) values (100.0, '2019-05-12', 'compras de dezembro', 1);
```

## **Consultas**

As consultas em banco de dados SQL tem um comando inicial chamado **select**:

- > select {coluna ou tudo} from {tabela-desejada};

**Exemplo**:
```
      -> Executa a operação de consulta
      |    -> Seleciona todas as colunas
      |    |         -> Tabela que será realizada a consulta
      |    |         |
    select * from compras;
```

Selecionando colunas:

- > select {nome-coluna-a, nome-coluna-b, nome-coluna-c} from {nome-tabela};

**Exemplo**:
```
       -> Selecione
       |     -> A coluna valor
       |     |     -> e a coluna data
       |     |     |           -> da tabela compras
       |     |     |           |
    select valor, data from compras;
```

Fazendo operações aritméticas:

- > select {coluna-a ```operação``` {valor desejado}} from {nome-tabela};

**Exemplo**:
```
                        -> Operação matemática
                        | -> Valor desejado
                        | |
    select valor, valor * 3, data from compras;
```

Filtros de busca e condições:

**OBS:** É possível utilizar **```>=```** ```(maior ou igual)```, **```<=```** ```(menor ou igual)``` e **```<>```** ```(diferente)```

- > select {parâmetro} from {tabela} where {condição}

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

Selecionando dados e "**renomeando**" na query e utilizando **GroupBy**:

```Essa query no final vai juntar as informações dessas três colunas```
- > select {coluna-a} as {col-a}, {coluna-b} as {col-b}, {coluna-c} as {col-c} from {nome-tabela} col-a, col-b, col-c;

**Exemplo**:
```
    select descricao as desc, month(data) as mes, year(data) as ano, sum(valor) as preço, count(valor) as qtd, round(avg(valor)) from compras group by mes, ano order by ano, mes;
```

Usando comando **like**:

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

Usando tipo **boolean** em consultas:

- > select {parametro} from {tabela} where {condição};

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

Importando arquivo SQL por linha de comando:

- > mysql -u root -p {nome-banco} < {nome-arquivo}.sql

As consultas podem ser efetuadas com o comando **between**:

- > select {paramentro} from {nome-banco} where ({condição_a} between {condição_b});

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

Atualizando tabelas:

> upadte {nome-tabela} set {onde-você-quer-alterar};

```Dessa maneira, todos os registros na coluna descricoes vai ser alterado para "campo emergencial"```
```
                    -> Selecione
                    |     -> Coluna descriocoes
                    |     |
    update compras set descricoes='compra emergencial';
```
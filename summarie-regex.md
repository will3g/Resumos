
# Ficando ninja em expressões regulares

### Links para testar expressões regulares:

1. **rubular.com/**

2. **regex101.com/**

3. **regexr.com**

# Resumão

## Classes e Quantifiers

## Quantifier

- **``{n}``** exatamente n vezes
- **``{n,}``** no mínimo n vezes
- **``{n,m}``** no mínimo n, no máximo m vezes
- **``?``** zero ou uma vez
- **``+``** uma ou mais vezes
- **``*``** zero ou mais vezes

## Classes de char - []

- **``[A-ZÇÕÔÉÈÊÂÁÀÃÌÍÚÙÛÓÒÔÕ]`` e ``[a-zçôõêéèãâàáíìùúûóò]``**
- **``[A-Z]``** letras de **A** até **Z**
- **``[123]``** - **1**,**2** ou **3**
- **``\d``** todos os dígitos **``[0-9]``**
- **``\s``** whitespace **``[ \t\r\n\f]``** (*o \s faz tudo isso*)
- **``\w``** wordchar **``[A-Za-z0-9_]``**

## Âncoras

- **``\b``** word boundary
- **``^``** início do alvo
- **``$``** fim do alvo

## Grupos
- **``(\w+)``** grupo de word chars
- **``(\w+)?``** grupo opcional
- **``(?:\w+)``** non-capturing group (*não captura o grupo especifícado*)

# Trabalhando com espaços

  - **``\t``** é um tab.

  - **``\r``** é carriage return.

  - **``\n``** é newline.

  - **``\f``** é form feed.

  A definição do **``\s``** pode variar um pouco entre as implementações, mas normalmente é um atalho para **``[\t\r\n\f]``**.

# Relembrar é viver:
O símbolo **+** é um outro atalho para definir a quantidade e agora já conhecemos todos:

* **```?```** - zero ou uma vez.

* **```*```** - zero ou mais vezes.

* **```+```** - uma ou mais vezes.

* **```|```** - funciona como **OU**

* **"``.``"** ponto significa qualquer caractere;

> **Obs:** se quisermos procurar pelo **``"*"``** ou **``"."``** literalmente (*sem significado especial*), devemos utilizar o caractere **``"\"``**.

* **```{n}```** - exatamente n vezes.

* **```{n,}```** - no mínimo n vezes.

* **```{n,m}```** - no mínimo n vezes, no máximo m vezes.
  
* **``a{3}``** **letra "a" 3 vezes**.
  
* **``\d*``** **Um digito, zero ou mais vezes**.

* As chaves **"``{``"** e **"``}``"** servem para definir uma quantidade de caracteres específicos que é desejado encontrar

- Uma classe de caracteres predefinida é **```\d```**, que significa qualquer dígito.

- Existem vários *meta-char*, como **```.```** ou **```*```**.

- Existem quantifiers que definem quantas vezes um caractere deve aparecer:

- **```{1}```** é um quantifier que significa uma vez.

- **```*```** é um quantifier que significa zero, uma ou mais vezes
     
- **```.```** é um meta-char que significa qualquer char.
     
- Com **```\```** podemos escapar meta-chars, por exemplo **```\.```**

- Com **```{0,1}```** ou **```?```** definimos que o caractere pode ou não existir

- Podemos definir facilmente a classe de qualquer caractere com o **[A-Z]**.

- Conhecemos todos os quantifiers como **?**, **+**, * e **{n}**.

- **\s** significa whitespace e é um atalho para **[ \t\r\n\f]**.

- **\w** significa word char e é uma atalho para **[A-Za-z0-9_]**.

- Existem âncoras predefinidas que selecionam uma posição dentro do alvo.

- ```\b``` é uma âncora que seleciona um word boundary, isso é o início ou fim da palavra.

- ```^``` é uma âncora que seleciona o início da string alvo.

- ```$``` é uma âncora que seleciona o fim do alvo.

- ```Non-Capturing group``` - **(?:de\s+)** (não deve devolver o grupo formado pela preposição ```de``` e por um ```\s```)

- ```Quantifier``` - **[a-z]?** (a classe deve ocorrer **zero** ou **uma** vez).

- Declaramos um grupo com **``(``** e **``)``**, podendo ter grupos e subgrupos. Um grupo é retornado na hora de executar, são úteis para selecionar uma parte do match.

- Através do **``?:``**, dizemos que **não queremos ver esse grupo na resposta**

- Para deixar a regex (*o quantifier*) **"preguiçoso"** usamos **``?``**, exemplo: **``[a-z]+?``**

- Dessa forma **``<h1>`blablabla</\1>``** fazemos com que a **``duas tags``** passadas entre **``<``** e **``>``** sejam iguais.

# CPF: Pegando o digito verificador:
**Alvo** > ``123.456.789-99``

**Regex** > 
``?:\d{3}.\d{3}.\d{3}-(\d{2})`` **ou** 
``\d{3}[-.]?\d{3}[.-]?\d{3}[.-]?(\d{2})``

**Retorno** > ``|[0]| 99``

# Pegando CNPJ:
**Alvo** > ``15.123.321/8883-22``

**Regex** > ``\d{2}.\d{3}.\d{3}/\d{4}-\d{2}``

# Pegando IPs:
**Alvos** > 
 > 126.1.112.34 

 > 128.126.12.244

 > 192.168.0.34

**Regex** > ``\d{3}.\d{1,3}.\d{1,3}.\d{1,3}``

# Pegando CEP:
**Alvo** > ``04155-854``

**Regex** > ``\d{5}-\d{3}``

# Pegando TEL:
**Alvo** > ``(11)6355-6693``

**Regex** > ``\(\d{0,2}\)\d{4}-\d{4}``

# Pegando **CNPJ**: (*Com e sem chars*)
**Alvo** > ``15.123.321/8883-22``

**Regex** > ``\d{2}.{0,1}\d{3}.{0,1}\d{3}/{0,1}\d{4}-{0,1}\d{2}``

# Pegando **IPs**: (*Com e sem chars*)
**Alvos** > 
  > 126.1.112.34 

  > 128.126.12.244
  
  > 192.168.0.34

**Regex** > ``\d{3}.{0,1}\d{1,3}.{0,1}\d{1,3}.{0,1}\d{1,3}``

# Pegando **CEP**: (*Com e sem chars*)
**Alvo** > ``04155-854``

**Regex** > ``\d{5}-?\d{3}``

# Pegando **Tel**: (*Com e sem chars*)
**Alvo** > ``(11)6355-6693``

**Regex** > ``\(?\d{0,2}\)?\d{4}-?\d{4}``

# Pegando tag ``<code>and</code>``:
**Alvo** > No <code>for</code>, o valor de <code>i</code> começa de zero e é incrementado a cada volta enquanto <code>i < 10</code>, portando o bloco de código do for é executado 10 vezes.

**Regex** > ``</?code>``


# Pegando a data:
**Alvo** > ``28 de Março de 1991``

**Regex** > ``[1-3]?\d\s+de\s+[A-Z][a-zç]{3,8}\s+de\s+[12]\d{3}``

# Retornando somente o ano dessa Data:
**Alvo** > ``28 de Março de 199[0]``

**Regex** > ``[1-3]?\d\s+de\s+[A-Z][a-zç]{3,8}\s+de\s+([12]\d{3}[0]``

**Retorna (em *array*)** > ``|[0]| 1991``

> **OBS:** Porém aqui tem um problema, se não existir o "de" a regex quebra

# Retornando somente o ano dessa Data e ignorando o "**``de``**":
**Alvo** > ``28 Março 1991``

**Regex** > ``[1-3]?\d\s+(de\s+)?[A-Z][a-zç]{3,8}\s+(de\s+)?([12]\d{3})``

**Retorna (em *array*)** > ``|[0]|  |[1]|  |[2]| 1991``

# Retornando somente o ano dessa Data:
**Alvo** > ``28 de Março de 1991``

**Regex** > ``([1-3]?\d)\s+(?:de\s+)?([A-Z][a-zç]{3,8})\s+(?:de\s+)?([12]\d{3})``

**Retorna** > ``|[0]| 28 |[1]| Março |[2]| 1991``

# Horário:
**Alvo** > ``13h32min16s``

**Regex** > ``\d{2}h\d{2}min\d{2}s``

# Placa do carro:
**Alvo** > ``KMG-8089``

**Regex** > ``[A-Z]{3}-\d{4}``


# Pegando notas de 7.2 até 7.9 e nomes dos alunos:
**Alvo** > ``9.8 - Robson, 7.1 - Teresa, 4.5 - Armênio, 6.5 - Zulu, 7.7 - Stefania, 7.8 - João, 5.0 - Romeu, 7.2 - Pompilho, 3.1 - Reinaldo, 7.3 - Bernadete, 4.7 - Cinério``

**Regex** > ``7.[2-9]\s-\s+[A-Z][a-zã]+``


# Pegando nota com espaço em TAB:
**Alvo** > ``10 - Bruce, 9.5 - Miranda, 7.9    - Bob, 10 - Zimbabue, 7.5 - Bety``

**Regex** > ``[7]\.[5-9]\s+-\s+\w+``


# Pegando o alvo e dando um único match:
**Alvo** > ``?classes+poderosas*``

**Regex** > ``[a-z?*+]+``


# Pegando o alvo e dando um limite de 10 chars:
**Alvo** > ``bgA5Bgfwxz``

**Regex** > ``[a-z-A-Z-0-9]{10}``

# Pegando o alvo exato da regex:
**Alvo:** ``aaa aaaa aaa aaaa aaa``

**Regex:** ``\baaa\b``

**Saída:** 
```
aaa Posição: [0-2]
aaa Posição: [6-9]
aaa Posição: [13-16]
```
# Excluindo o alvo exato da regex:
**Alvo:** ``aaa aaaa aaa aaaa aaa``

**Regex:** ``\Baaa\B``

**Saída:** 
```
aaaa Posição: [2-6]
aaaa Posição: [9-13]
```
# Pegando todo alvo validando o início e final:
**Alvo** > ``http://127.0.0.1:5500/index.html``

**Regex** > ``^http://.+\.html$``

# Pegando erro do MySQL com base no ``Caused by:``
**Alvo** > ``Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure``

**Regex** > ``^Caused by:.*``

# Pegando erro do MySQL e retornando a causa e descrição:
**Alvo** > ``Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure``

**Regex** > ``(Caused[\s\w:.]+):([\w\s]+) ou (^Caused by:.*):(.*)``

**Retorno (em *array*)** > 

**|[0]|** 
```Caused by: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException``` **|[1]|**  ```Communications link failure```


# Pegando o alvo data:
**Alvo** > ``Data: 02/09/1964 e Data:02/09/1964``

**Regex** > ``^Data:[\s]?[0-9]{2}\/[0-9]{2}\/[0-9]{4}$``

# Pegando arquivo do tipo html:
**Alvo** > ```arquivo-expressao-regular.html```

**Regex** > ```.*\.html$```

# Utilizando regex em Django:
**url** > ```regex_url = r'(.*/exercises/\d+/answer/\d+)$'```

Vai pegar a url que contenha ```exercises``` e ```answer```.

# Palavra secreta:
**Alvo** > ``Z171PZ7AZ23PZ7819AZ78GZ1AZ99IZ34O``

**Regex** > ``Z\d+(\w)``

**Retorno** > ``Z171P ||| `` [P] `` | Z7A ||| `` [A] `` | Z23P ||| `` [P] `` | Z7819A ||| `` [A] `` | Z78G ||| `` [G] `` | Z1A ||| `` [A] `` | Z99I ||| `` [I] `` | Z34O ||| `` [O]

# Validando email Caelum ou Alura:
```|```: funciona como um **"OU"**

**Alvo** > super.mario5@alura.com.br

**Regex** > ``([a-z.]{4,14}[a-z\d])@(caelum|alura).com.br$``

**Retorno** > 

``super.mario5@alura.com.br`` |[0]| 
``super.mario5`` |[1]|
``alura`` |[2]|

**ou**

``alex.kid5@caelum.com.br`` |[0]| ``alex.kid5`` |[1]| ``caelum`` |[2]|

# Validando qualquer email:

**Alvo** > donkey.kong@kart.com.br

**Regex** > 
```
([A-Z-a-z][A-Z-a-z-0-9._-]{4,20})@(gmail|hotmail|yahoo|outlook|[A-Z-a-z-0-9.]{3,20}).(com.br|com|org|net|info|[A-Z-a-z]{2,4})
```
**``OU``**
```
^([\w-]\.?)+@([\w-]+\.)+([A-Za-z]{2,4})+$
```

**Retorno** > 
        ``|[0]| donkey.kong 
        |[1]| kart 
        |[2]| com 
        |[3]| br``

**Testando emails:**
O que deve ser pego pela **```regex```**:
> **``OBS:``** retorno em *array*
```
donkey.kong@kart.com.br                   
Retorno ->  |[0]| donkey.kong      
            |[1]| kart                 
            |[2]| com       
            |[3]| br

bowser1@games.info                        
Retorno ->  |[0]| bowser1          
            |[1]| games                
            |[2]| info

super-mario@nintendo.JP                   
Retorno ->  |[0]| super-mario      
            |[1]| nintendo             
            |[2]| JP

TEAM.donkey-kong@MARIO.kart1.nintendo.com 
Retorno ->  |[0]| TEAM.donkey-kong 
            |[1]| MARIO.kart1.nintendo 
            |[2]| com
```

**E aqui alguns **``exemplos``** do que **``não``** pegar:**
```
toad@kart...com
wario@kart@nintendo.com
yoshi@nintendo
daisy@nintendo.b
..@email.com
```
**Expressão regular:**
```
  ^([\w-]\.?)+@([\w-]+\.)+([A-Za-z]{2,4})+$
```

- A regex usa âncoras no início **``^``** e fim **``$``** para garantir o match inteiro;

- Antes do **``@``**, temos: **``^([\w-]\.?)+``**

- Definimos uma classe com word-chars e hífen, seguido por um ponto opcional: **``[\w-]\.?``**

- Essa classe pode se repetir uma ou mais vezes, então criamos um grupo e **``+``** ao final: **``([\w-]\.?)+``**

- Depois do **``@``**, temos:
**``([\w-]+\.)+``**, que é bastante parecido com o anterior ao **``@``**, porém com o **``.``** obrigatório,

- **``([A-Za-z]{2,4})+$``**, que é o final da nossa regex, seleciona o domínio do email, como br, com, us. 

- O mínimo de letras dessa parte final devem ser 2 e no máximo 4.

------

## Pegando nome, rua, número e cep:

**Regex:** 
```
([\w\s]+)\|(?:\d{2}\/\d{2}/\d{4})\|([\w\s]+)\|(\d{1,4})\|(\d{5}-\d{3})\|(?:[\w\s]{10,})
```
**``OU``**
```
^([\w\s]+)\|(?:\d{2}\/\d{2}/\d{4})\|([\w\s]+)\|(\d{1,4})\|(\d{5}-\d{3})\|(?:[\w\s]{10,})$
```

**Alvo:**
```
1 - Nico Steppat|14/05/1977|Rua Buarque de Macedo|50|22222-222|Rio de Janeiro

2 - Romulo Henrique|14/06/1993|Rua do Lins|120|12345-322|Rio de Janeiro

3 - Leonardo Cordeiro|01/01/1995|Rua de Campo Grande|01|00001-234|Rio de Janeiro
```
**retorno (em *array*)**:
```
1 - |[0]| Nico Steppat       
    |[1]| Rua Buarque de Macedo 
    |[2]| 50  
    |[3]| 22222-222

2 - |[0]| Romulo Henrique    
    |[1]| Rua do Lins           
    |[2]| 120 
    |[3]| 12345-322

3 - |[0]| Leonardo Cordeiro  
    |[1]| Rua de Campo Grande   
    |[2]| 01  
    |[3]| 00001-234
```

- Declaramos um grupo com ().

- Podemos ter grupos e subgrupos.

- Um grupo é retornado na hora de executar, são úteis para selecionar uma parte do match.

- Através do ?:, dizemos que não queremos ver esse grupo na resposta

# Quantifiers gananciosos (*ou preguiçosos*):

**Alvo** > **``papel``**

**Regex** > **``[a-z]+?``**

**Retorno** > **p | a | p | e | l**

> **OBS:** Para deixar a regex (o quantifier) "preguiçoso" usamos **``?``**, exemplo: **``[a-z]+?``**

## Tag ``<h1>...</h1>`` pegando até onde queremos [^>]:

**Alvo** > ``<h1 class="text-left">Expressões regulares</h1>``

**Regex** > ``<h1[^>]+>``

**Retorno** > ``<h1 class="text-left">``

## Tag ``<h1>...</h1>``:

> **OBS:** Temos um problema, a expressão aceita tags diferentes. 
```
Exemplo >>>  <h1>...<h2>
```

**Alvo** > ``<h1 class="text-left">Expressões regulares</h1>``

**Regex** > ``<h1.+?>([\s\wôõãâíìáàêéèúù]+)</h1>``

**Retorno** > ``<h1 class="text-left">Expressões regulares</h1>`` **|[0]|** ``Expressões regulares``

## Tag ``<h1>...</h1>`` melhorado e utilizando **back-references:**

> **OBS:** Agora o a tag tem que ser igual -> <h2></h2>

**Alvo** > ``<h1 class="text-left">Expressões regulares</h1>``

**Regex** > ``<(h1|h2).+?>([\s\wôõãâíìáàêéèúù]+)</\1>``

**Retorno** > ``<h1 class="text-left">Expressões regulares</h1>`` **|[0]|** ``Expressões regulares``

- Essa negação é algo muito comum nas regexes. Há circunstâncias em que é *mais fácil* 
definir o que **não queremos** *em vez* **de dizer o que queremos**. A negação **^** ajuda nisso. 
Isso também é a razão da existência de classes como *\W* (**com W maiúsculo**) e *\D* 
(**com D maiúsculo**).

- O *\W* é a non-word char, ou seja tudo que não é um word char. *\W* é um atalho para **[^\w]**.

- A classe *\D*, por sua vez, é um non-digit, ou seja, *\D* é um atalho para **[^\d]**

- Repare também que não usamos a meta-char **^** como âncora pois aparece dentro de uma classe **[^>]**.

## Pegando ``tags`` de ``p1`` até ``p9``:

> **OBS:** Para deixar a regex (o quantifier) preguiçoso usamos ``?``**:** ``[a-z]+?``

**Alvo** > 
```
  <soap:Envelope xmlns:soap="http://www.w3.org/2001/12/soap-envelope"                 
  soap:encodingStyle="http://www.w3.org/2001/12/soap-encoding">  

  <soap:Body xmlns:m="http://www.caelum.com.br/produto">   
    <m:GetStock>     
      <p3> dsfdsf </p3>   
    </m:GetStock> 
    </soap:Body>  
  </soap:Envelope>
```

**Regex** > **``<(p[1-9])>.*<\/\1>``**

**Retorno** > **|[0]| p3 |[1]|  dsfdsf** 

 - No primeiro grupo há uma tag de prioridade que pode ir de 1 até 9, por isso: **<(p[1-9])>**

 - Podemos ter qualquer item no meio: **``*.``**

 - E por último, usamos o **BackReference** para garantir que a tag será fechada com a mesma tag usada na abertura, escapando a barra de fechamento da tag: **<\/\1>**

# Negação

**String** > ``Z171PZ7AZ23PZ7819AZ78GZ1AZ99IZ34O``

**Regex** > ``[^Z\d]`` *Não queremos números e nem a letra Z*

**Retorno** > ``P | A | P | A | G | A | I | O``



# Links e tags

**String** > ``<a href="www.youtube.com.br"> YouTube </a> ``

**Regex** > ``<(a)\s+href="(.+)"(?:>(.*)<\/\1>)``

**Retorno** > **|||** ``a`` **|||** ``www.youtube.com.br`` **|||**  ``YouTube``


# Usando REGEX no Java Script:

Declarando o alvo:
```
let target = "11a22b33c";
```

Dessa forma não é necessário colocar, por exemplo, **\\d** e nem **\\w**, para excapar a barra, apenas **\d** e **\w**.

> **OBS:** Com **RegExp** ficaria -> ``var exp = new RegExp('(\\d\\d)(\\w)', 'g');``.
```
let exp = /(\d\d)(\w)/g;
```

Testando o *match* entre a expressão e o valor do alvo:

> **OBS:** A função **.test()** retornará *``true``* apenas se o alvo seguir o padrão da expressão.
```
exp.test(target);
```

Saída no console:
```
["11a", "11", "a"]
```
---
Executando o seguinte código:
```
var alvo = '11a22b33c';
var exp  = /(\d\d)(\w)/g;
var resultado = null;

while(resultado = exp.exec(alvo)){
  console.log(resultado);
  console.log(exp.lastIndex);
}
```

Teremos como saída:
```
// var alvo = '11a22b33c';

Array(3) [ "11a", "11", "a" ]

Array(3) [ "22b", "22", "b" ]

Array(3) [ "33c", "33", "c" ]   
```

## **Uso de Regex e .replace()**

Declaramos o alvo:
```
let anoMesDia = '2007-12-26';
```

Declaramos a **Regex**:
```
let exp = /-/g;
```

Agora usamos o método **.replace()** para substituir os ``hífens`` por ``barras``:
```
anoMesDia = anoMesDia.replace(exp, '/');
console.log(anoMesDia);
```

Teremos como saída:
```
'2019/12/26'
```
> **OBS:** Se tivéssemos omitido o **``g``** da expressão, ele **trocaria apenas o ``primeiro hífen``**.

## **Uso de Regex e .split()**

> **OBS:** A função **``<string>.split()``** nela, podemos passar um separador que ele se encarregará de criar um *array* com cada item ``considerando o separador utilizado``.

Declarando o alvo:
```
var arquivo = '100,200-150,200;20';
```

Declarando a expressão:
```
var exp = /[,;-]/;
```

Passando a expressão regular para o método **.split()**:
```
var valores = arquivo.split(exp);
console.log(valores);
```

Saída:
```
["100", "200", "150", "200", "20"]
```

## **O retorno de match!**

Declarando o alvo:
```
var codigos = 'A121B12112C12212F12G01';
```

Definindo a expressão regular:
```
var exp = /[A-Za-z]\d+/g
```

Toda ``string`` em *``JavaScript``* possui o método **``match``**. Ele aceita uma expressão regular e retorna em um array todas as partes do alvo que atendem a expressão regular. 
```
var codigosExtraidos = codigos.match(exp);
console.log(codigosExtraidos);
```

Saída:
```
["A121", "B12112", "C12212", "F12", "G01"]
```

# A praticidade do atributo ``pattern``:

O **HTML5** introduziu para as **tags input** o atributo **``pattern``**, que recebe como atributo expressões regulares. 

Quando o formulário for submetido e o ``valor digitado pelo usuário não for compatível com a expressão``, o próprio navegador exibirá *automágicamente* uma mensagem para o usuário indicando que o campo é ``inválido``. 

> **OBS:** é importante que o **``input``** **faça parte de um formulário**, caso contrário a validação não será aplicada.


**Exemplo:**

Fazendo com que nosso input aceite apenas números:

```
<!doctype html>
<head>
    <meta charset="UTF-8">
    <title>Testando pattern</title>
</head>
<body>
    <form>
        <input pattern="[0-9]*">
        <input type="submit" value="Enviar dados">
    </form>
</body>
```
Entretanto, podemos utilizar tipos no input. Alguns são:

- O ```<input type="number">``` só aceita números e seu design muda um pouco.

- E ```<input type="email">``` verifica se é do tipo email.

# Usando REGEX no Python:

Primeiramente devemos importar o módulo **re**:

> O módulo **re** é *responsável* pelas expressões regulares.
```
import re
```

Definindo a expressão regular:
```
exp = r'(\d\d)(\w)'
```

Definindo o alvo:
```
alvo = '11a22b33c'
```

Em seguida tentamos dar **match** do alvo com a expressão regular:
> **OBS:** É parecido com a função **``.test()``** do **``JS``**
```
resultado = re.search(regexp, alvo)
```

Podemos usar a função .group() para pegar o valor que queremos de acordo com a posição do grupo:
```
resultado.group()    // Saída: '11a'
resultado.group(0)   // Saída: '11a'
resultado.group(1)   // Saída: '11'
resultado.group(2)   // Saída: 'a'
```

Podemos pegar a quantidade de arrays (*ou conjuntos*) que se encontram dentro de um array maior:
```
Um exemplo seria >>>

[0,3] [
        [11a],  // Posição 0
        [11],   // Posição 1
        [a],    // Posição 2
      ]

[0,3] -> Conjunto 0 que contém 3 posições dentro dele.
```

Saída:
```
resultado.start()   // Saída: '0'
resultado.end()     // Saída: '3'
```

## **O método **.findall()** e **.finditer()**:**


> **OBS:** O método **re.findall( )** retornará todos os *matches*, como uma lista de *strings*.
```
resultados = re.findall(exp, alvo)
print resultados
```
Saída:

 > **OBS:** Temos os três grupos que foram achados: ```('11', 'a'), ('22', 'b')``` e ```('33', 'c')```.
```
[('11', 'a'), ('22', 'b'), ('33', 'c')]
```

Podemos imprimir os grupos separadamente chamando seus índices:
```
resultado[0]    Saída -> ('11', 'a')

resultado[1]    Saída -> ('22', 'b')

resultado[2]    Saída -> ('33', 'c')
```
Ou fazendo um for:
```
for grupo in resultado:
  print grupo

------------------
| Saída:         |
| ('11', 'a')    |
| ('22', 'b')    |
| ('33', 'c')    |
------------------
```
E para concatenar os elementos, podemos fazer:
```
for grupo in resultado:
  print grupo[0] + grupo[1]


------------------
| Saída:         |
|         11a    |
|         22b    |
|         33c    |
------------------
```
----
Também podemos fazer da seguinte forma:
```
resultados = re.finditer(exp, alvo)

for item in resultados:
  print "%s | %s | %s [%s,%s]" % (item.group(),
                                  item.group(2), 
                                  item.start(), 
                                  item.end())
```
Saída:
```
    11a | 11 | a [0,3]
    22b | 22 | b [3,6]
    33c | 33 | c [6,9]
```

## **Alterando o separador de uma data**

Substituindo hífens por barras:
```
  import re

  regex = '-'
  novotexto = '/'

  alvo = '2019-12-26'

  resultado = re.sub(regex, novotexto, alvo)
  print resultado
```
Saída:
```
2019/12/26
```
---
Primeiramente devemos importar o módulo de expressão regular:
```
import re
```

Definindo o alvo:
```
alvo = '2007-12-31'
```

Definindo a regex:
```
regex = '\s-\s'
```

Devemos substituir todos os lugares que condizerem com a expressão passada, por isso definimos:
```
novotexto = ': '
```

O método **``re.sub``** recebe uma **expressão regular como primeiro parâmetro**, **o segundo que deve substituir** e **o terceiro é a ``string alvo``.**
```
regexp = 'expressão - regular'
resultado = re.sub(regex, novotexto, regexp)
```

Se imprimirmos o valor de **resultado**, temos:
```
print resultado
>>>  expressão: regular
```
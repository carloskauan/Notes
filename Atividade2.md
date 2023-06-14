## Atividade: Concatenação de Strings
### Questão 1: Concatenação básica

Considere as variáveis abaixo:

~~~js
var nome = "João";
var sobrenome = "Silva";
~~~

Qual a saída da seguinte concatenação de strings?

~~~js
var resultado = nome + " " + sobrenome;
console.log(resultado);
~~~

a) "João Silva"

b) "JoãoSobrenome Silva"

c) "nome sobrenome"

d) "JoãoSilva"


### Questão 2: Concatenação de número e string

Considere as variáveis abaixo:

~~~js
var idade = 30;
var texto = "A idade é: ";
~~~
Qual a saída da seguinte concatenação de strings?
~~~js
var resultado = texto.concat(idade);
console.log(resultado);
~~~

a) "A idade é: 30"

b) "A idade é: idade"

c) "30 A idade é:"

d) "idade A idade é:"

### Questão 3: Concatenação de múltiplas strings

Considere as variáveis abaixo:

~~~js
var palavra1 = "Hello";
var palavra2 = "World";
var palavra3 = "!";
~~~
Qual a saída da seguinte concatenação de strings?
~~~js
var resultado = palavra1.concat(" ", palavra2 + palavra3);
console.log(resultado);
~~~

a) "Hello World!"

b) "HelloWorld!"

c) "Hello World!"

d) "HelloWorld !"

### Questão 4: Concatenação de strings com template literals

Considere as variáveis abaixo:

~~~js
var nome = "Maria";
var idade = 25;
~~~

Qual a saída da seguinte concatenação de strings usando template literals?

~~~js
var resultado = `Olá, ${nome}! Você tem ${idade} anos.`;
console.log(resultado);
~~~~

a) "Olá, Maria! Você tem 25 anos."

b) "Olá, ${nome}! Você tem ${idade} anos."

c) "Olá, ${nome}! Você tem idade anos."

d) "Olá, ! Você tem anos."


## Desafio

Implemente um trecho de código em JavaScript que realiza uma série de manipulações de strings em um array de frases. O objetivo é calcular o tamanho de cada frase, transformar todas as letras em letras maiúsculas, transformar todas as letras em letras minúsculas, remover espaços em branco no início e no final de cada frase, substituir uma palavra por outra, verificar se cada frase começa com uma determinada letra ou palavra, verificar se cada frase termina com uma determinada letra ou palavra e verificar se cada frase contém uma determinada palavra. 

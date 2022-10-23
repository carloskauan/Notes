## Introdução ##
Não devemos por ; no final da linhas
Assim como no C devemos importar pacotes para utilizar algumas funções

## Arquivo principal ##
Para indicar que aquele arquivo e o principal devemos colocara a primeira linha do codigo como
~~~go
package main
~~~

## Variaveis ##
As variavei são tipadas e declaradas com var mas seu tipo e expecificado dps do nome da variavel

~~~gol
var nome string = "Caralho"
~~~

As variaveis do tipo float existem dois tipo float32 para reais pequenos e float64 para reais grandes equivalente ao double
~~~go
var taxa float32 = 1.05
var pi float64 = 3.1415926535897932384626433832795028841971
~~~
Quando uma variavel e iniciada sem nem um valor ela assume o valor de zero quando numero e de uma string vazia quando string
E possivel iniciar uma variavel sem definir o tipo, então o compilador defini o tipo de acordo com o conteudo;
~~~go
var nome = "Carlos"
~~~
No caso das variaveis float quando não declaradas o tipo o compilador usa sempre o maior float64

E tambem temos a declaração curta de variaveis aonde não precizamos por o prefixo var e nem o tipo
~~~go
nome := "Carlos"
~~~

## Funções de modulos ##
As funções de modulos sempre tem o nome do modulo e a primeira letra da função maiuscula
~~~go
modulo.Func()
~~~

## Println ##
Para poder printar algo devemos primeiro importar o pacote fmt

~~~go
import "fmt"
~~~
E dar dar o comando print

~~~go
fmt.Println("Kraaiiiii", var,"Nossaaa")
~~~

## Scanf ##
Para receber entrada de dados usamos o scanf
~~~go
fmt.Scanf("%d", &var)
~~~
Na funçao scanf usamos o especificador de formato para dizer que esperamos um inteiro e passamos o ponteiro da nossa variavel para a função guardar o a entrada.

Porem uma forma mais simples de entrar com dados e usando a função scan que não precisa de especificador de formato
~~~go
fmt.Scan(&var)
~~~
Na função scan so e preciso passar o endereço de memoria da variavel

## TypeOf ##
Para verificarmos os tipos das variaveis usamos o comando TypeOf importado do pacote reflect

~~~go
import "reflect"
~~~
Seu comando...
~~~go
reflect.TypeOf(variavel)
~~~

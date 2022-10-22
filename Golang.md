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

~~~go
var nome string = "Caralho"
~~~

As variaveis do tipo float existem dois tipo float32 para reais pequenos e float64 para reais grandes equivalente ao double

~~~go
var taxa float32 = 1.05
var pi float64 = 3.1415926535897932384626433832795028841971
~~~

## Funções de modulos ##
As funções de modulos sempre tem o nome do modulo e a primeira letra da função maiuscula
~~~go
modulo.Func()
~~~

## Print ##
Para poder printar algo devemos primeiro importar o pacote fmt

~~~go
import "fmt"
~~~
E dar dar o comando print

~~~go
fmt.Println("Kraaiiiii", var,"Nossaaa")
~~~

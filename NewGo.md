## Comandos
Compilação
~~~sh
go buid arquivo.go
~~~
Este comando cria um arquivo binario que pode ser executado a qualquer momento sem processamentos adicionais

Compilação + Execução
~~~sh
go run arquivo.go
~~~
Este comando compila em binarios e executa em tempo real

## Funções

Em golang temos dois tipos de funções.
#### Padrão
~~~go
func sla(n1, n2 int)int{
  return 2
}
~~~
Onde sua declaração e feita fora da função main

#### De variavel
Basicamente uma função anonima onde pode ser declarada e usada dentro da função main ou outras funções

~~~go
func main(){
  var sla = func(){
    fmt.Println("Slaa")
  }

  sla()
}
~~~

#### Multiplos retornos
Um tipo de função onde temos dois retornos diferentes sendo usados da seguinte forma
~~~go
func main(){
  var sla = func()(string, string){
    return "Slaaa111", "Slaaa222"
  }

  var sla1, sla2 string = sla()
}
~~~
Assim temos dois diferentes tipos de retorno para uma unica função

## Args

O pacote "os" oferece funções para lidar com sistema operacional independente da plataforma.

Argumentos de linha de comando são  estão disponiveis em uma variavel Chamada Args, que faz parte do pacote "os", assim seu nome em qualquer lugar fora do pacote "os" vai ser os.Args.
Args e um slice de string com comandos inseridos pelo terminal.
O primeiro elemento de os.Args[0] e o nome do comando propriamente dito e os outros elementos são os argumentos apresentados ao programa quando sua execução é iniciada

Uma forma de filtrar os argumentos e usando a fatiação com slice[m:n], ficando dessa forma:
~~~go
os.Args[1:len(os.Args)]
~~~
Esse comando faz uma fatia do slice Args , pegando somente os argumentos que não são o primeiro elemento que corresponde ao comando principal.

~~~go
var s, sep string
for i := 1; i < len(os.Args); i++ {
  s += sep + os.Args[i]
  sep = " "
}
fmt.Println(s)
~~~

Nesse metodo e feita um for para percorrer o slice de Args pulando o primeiro argumento

Tambem e possivel realizar um "foreach" para percorrer os elementos desse slice

~~~go
for _, arg := range os.Args[1:]{
  s += sep + os.Args[i]
  sep = " "
}
fmt.Println(s)
~~~

Esse processos podem ser custosos para a cpu mas existe um metodo join que junta todos os elementos do slice em uma string só , separada por algum tipo de seperador da seguinte forma

~~~go
fmt.Println(strings.Join(os.Args[1:], " "))
~~~

Mas caso formatação não seja de fato necessaria podemos apenas imprimir os agumentos com

~~~go
fmt.Println(os.Args[1:])
~~~

## Medir tempo de execução

Para medir o tempo que um codigo leva para ser executado usamos o pacote time com sua função/objeto time.Now() da seguinte forma

~~~go
import(
  "fmt"
  "time"
)

func main(){
  start := time.Now()

  //codigo a ser medido o tempo de execução

  fmt.Println(time.Since(start).Seconds())
}
~~~
Em "start" vai ser iniciado a contagem do tempo e vai ser verificado em segundos usando o time.Since.

## Econtrando linhas duplicadas

Chamado de dup, e inspirado no comando uniq do Unix. Usamos da seguinte forma

~~~go
1:  import (
2:    "bufio"
3:    "fmt"
4:    "os"
5:  )
6:
7:  func main() {
8:    counts := make(map[string]int)
9:    input := bufio.NewScanner(os.Stdin)
10:  
11:   for input.Scan() {
12:     counts[input.Text()]++
13:	  }
15:
16:   fmt.Println(counts)
17:
18:   for line, n := range counts {
19:     if n > 1 {
20:			 fmt.Printf("%d\t%s\n", n, line)
21:		 }
22:    }
23:  }
~~~
Linha 8: Temos A criação do nosso map que armazena um conjunto de chaves valores e oferece operações para armazenar, recuperar ou testar um item, que nesse caso sera o que armazenara as linhas digitas. Dentro map definimos que a chave sera do tipo string e o valor será do tipo inteiro

linha 9: Instancia o pacote bufio para a entrada de dados pelo terminal

Linha 11: Inicio do for que esta se repetindo enquanto tiver entrada de dados, ctrl + c para encerrar a entrada de dados

Linha 12: E pego o valor em texto da entrada e registra no map como chave caso não exista dentro do map com valor 1(++) caso ja exista e feito um incremento no valor daquela chave

Linha 13 a 20 : E feito uma varredura no map como um for each e para as chaves caso o valor seja maior que 1 imprime quantas vezes a chave foi repetida e o seu valor

## Especifiadores de formato 
Especificador   | Tipo de dado
:---------: | :------:
%d | Int
%x, %o, %b | Int hexadecimal, otal e binario
%f, %g, %e | Floats
%t |  Booleano
%c | Char e codigos unicode
%s | String
%T | Qualquer tipo

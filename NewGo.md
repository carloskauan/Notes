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

## Enontrando linhas duplicadas

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
20:			  fmt.Printf("%d\t%s\n", n, line)
21:		  }
22:    }
23:  }
~~~



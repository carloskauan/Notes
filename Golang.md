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
## Constantes
Para usarmos constantes temos que declara-las fora da função main e antes de qualquer outra função

~~~go
package main
import "fmt"

const id = 15

func main(){
  fmt.Println(id)
}
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
## If Else ##
Em Go as condicional if e else if so aceitam expressões que retornam booleans e não tem os parenteses seguindo o formato

~~~go
if var == 1{
  codigo
}else if var == 2{
  codigo
}else{
  codigo
}
~~~

## Switch ##
No Switch a estrutura segue o mesmo padrão de outras linguagens so que não existe a necessidade de usar o break pois a execução para apos usar executar cada case

~~~go
switch var{
  case 1:
    coding
  case 2:
    coding
  default:
    coding
}
~~~

## Funções ##
Em go as funções em levam o prefixo func
As funções sem retorno não precisam de nem um indicativo
~~~go
func showDates(){

}
~~~
E funções com retorno devem seguir a seguinte sintax
~~~go
func returnNumber() int{

}
~~~
Aonde o tipo e localizado na frente do nome da função depois dos parenteses
E o retorno e convencional
~~~go
return 0
~~~
### Função com multiplos retornos ###
Nas funções tambem conseguimos ter mais de um retorno seguindo a seguinte estrutura
~~~go
func nameIdade() (int, string){
  var idade int
  var nome string
  
  return idade, nome
}
~~~
Para guardamos os valores dos retornos nas variaveis...
~~~go
nome, idade := nameIdade()
~~~
Os valores são guardados na mesma ordem do return, aonde nome retorna primeiro e idade logo em seguida
E quando não queremos utilizar um dos valores do retorno utilizamos o _ para ignorar
~~~go
_, idade := nameIdade() //Ignorar o retorno nome
nome, _ := nameIdade() //Ignorar o retorno idade
~~~
Isso se aplica para n retornos

## Exit ##
Para sair de forma correta do sistema pode usar o pacote os e a função exit para dar encerramento seguro do programa
~~~go
import "os"
os.Exit(0)
~~~
Use 0 para indicar que tudo ocorreu sem erros e -1 para indicar que algo deu errado

## Net/http ##
O pacote utilizado para fazer requisições a internet e o net/http
~~~go
import "net/http"
~~~
### Get ###
O para realizar um get usamos o comando
~~~go
http.Get("url")
~~~
O metodo http.Get tem dois tipos de retorno o primeiro a resposta da requisição e o segundo erro
~~~go
resp, err = http.Get("Url")
~~~
## Laços de repetição ##
Em Go não temos o WHile então todos os loops são feitos com for
Um for sem nem um parametro roda infinitamente
~~~go
for{

}
~~~
Podemos utilizar um for normalmente
~~~go
for c := 1; c <= 10; c++{

}
~~~
### Percorrer um array ###
Podemos utiliar a propriedade range para percorrer um array
~~~go
for index, elemento := range array{

}
~~~
A função range retorna 2 valores, o index na primeira posição e o elemento da vez na segunda opçãom, essas variaveis são utilizadas dentro do loop.
## Array ##
Arrays tem um Tamanho fixo e deve ser declarado seu tipo
~~~go
var arry [4]string
~~~
Mas temos uma abstração de array chamada slice aonde seu tamanho e variavel
~~~go
arry := []string{"Jubileu","Jãozin","Maria"}
~~~
Para ler quantos elementos um array tem e qual sua capacidade usamos a função len() e cap()
~~~go
len(array)//Retorna quantos itens tem no array
cap(array)//Retorna a capacidade do array
~~~
Para adicionarmos um novo elemento ao array usamos a função append
~~~
append(array, "Dado")
~~~
Sempre que um array com sua capacidade maxima e tem um item adicionado o slice cria um novo array com o tamanho do array anterior dobrado
##  Append
Para adicionar um elemento ao array usavos o metodo append
~~~go
var nomes []string
nomes = append(nomes, elemento)
~~~

## Sleep
Para darmos um sleep precisamos importar o pacote "time" e usarmos função sleep e seus parametros
~~~go
import "time"

func main(){
  time.Sleep( 6 * time.Minute)
}
~~~
Na função sleep o primeiro parametro e a quantidade e o segundo e a medida Minute, Second, Hour

## Ler arquivos 
Para ler aqrquivos usamos o pacote os e a seguinte função
~~~go
aquivo, erro := os.Open("Caminho")
arquivo.Close() 
~~~
A primeira variavel armazena o arquivo e a segunda um possivel erro. Mas essa função retornar puramente o ponteiro do arquivo
Para ler de uma forma mais util usaremos o pacote io/ioutil e para ler o arquivo a função readfile.E use a função close para fechar um arquivo apos acabar de utilizar o arquivo

~~~go
import 'io/ioutil"

resp, err := ioutil.ReadFile("caminho")
~~~
Essa função retornar um conjunto de bytes mas para transformar em algo legivel convertemos o resp em string para usar e darmos print por exemplo
Porem esse metodo faz somente a leitura do arquivo inteiro e podemos utilizar outro metodo para ler algo especifico do arquivo
Usamos o pacote bufio e a função os.open que vimos acima e a função buffio.newreader() da seguinte forma
~~~go
import(
  "os"
  "bufio"
)

cont, err := os.Open("caminho")
lido := bufio.NewReader(cont)
linha, err := lido.ReadString('\n')
~~~
Em lido e feito a leitura do conteudo do ponteiro da variavel cont que utiliza a o os.Open, e em linha e armazenado o fatiamente da leitura do conteudo. Nos parametros dp readstring e passao o byte limite de ate aonde a leitura vai ser feita
>Esse parametro de limite de leitura deve ser declardo com aspas simples pois indica o byte de quebra de linha, ou seja so sera lido ate final na primeira linha

Podemos encerrar a leitura de um arquivo quando se chega ao final com a um erro de EOF end of file verificando a variavel err
~~~go
linha, err := leitor.ReadString('\n')
if err == io.EOF{
  break
}
~~~
Um dos metods que permite criar e ler um arquivo caso ele não exista e o seguinte
~~~go
arquivo, err := os.ReadFile("arquivo", flag, permissão)
~~~
O metodo readfile tem alguns argumentos a mais como suas Flasg de permissão para tratar arquivos
~~~go
// Exactly one of O_RDONLY, O_WRONLY, or O_RDWR must be specified.
O_RDONLY int = syscall.O_RDONLY // open the file read-only.
O_WRONLY int = syscall.O_WRONLY // open the file write-only.
O_RDWR   int = syscall.O_RDWR   // open the file read-write.
// The remaining values may be or'ed in to control behavior.
O_APPEND int = syscall.O_APPEND // append data to the file when writing.
O_CREATE int = syscall.O_CREAT  // create a new file if none exists.
O_EXCL   int = syscall.O_EXCL   // used with O_CREATE, file must not exist.
O_SYNC   int = syscall.O_SYNC   // open for synchronous I/O.
O_TRUNC  int = syscall.O_TRUNC  // truncate regular writable file when opened.
~~~
Tbm podendo-se usar varias flags atraves do operador And |
E tamos o parametro de permissão de sistema sendo ele 0666 o padrão.
Exemplo de utilização
~~~go
arquivo, err := os.OpenFile("logs.txt", os.O_RDWR | os.O_CREATE, 0666
~~~
Suas flags tem a permissão de leitura e escrita os.O_RDWR e a permissão de criação de arquivo caso o mesmo não exista os.O_CREATE
E a permissão padrão do sistema
### Cortar espaços
Para tirar carcteres vazio, espaços e quebras de linha de uma string

## Tratar erros
Para tratar erros de uma função usamos o if 
~~~go
resp, err := http.Get("www.go.dev")
if err != nil{
  fmt.Println(err)
}
~~~

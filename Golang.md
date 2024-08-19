# Introdução #
Não devemos por ; no final da linhas
Assim como no C devemos importar pacotes para utilizar algumas funções

## Compilação
 Para compilarmos um projeto ou arquivo go para um so especifico usamos
~~~go
GOOS=windows go build name.go
~~~

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

## Registrar tempo
Para registrarmos tempo em go usamos essa formatação
~~~go
import "time"

time.Now().Format("02/01/2006 15:04:05")
~~~
[Tabela para formatação](https://go.dev/src/time/format.go) 

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
arquivo, err := os.OpenFile("logs.txt", os.O_RDWR | os.O_CREATE | os.O_APPEND, 0666
~~~
Suas flags tem a permissão de leitura e escrita os.O_RDWR e a permissão de criação de arquivo caso o mesmo não exista os.O_CREATE
E a permissão padrão do sistema
Para escrever algo no arquivo usamos os write string
~~~go
arquivo.WriteString("Dados")
~~~
E devemos adicionar a flag os.O_APPEND para que novos registros sejam alocados no arquivo e os antigos não sejam sobrescritos
>Essa função requer que tudo que seja passado como parametro seja convertido para string
### Cortar espaços
Para tirar carcteres vazio, espaços e quebras de linha de uma string usamo a string trim space
~~~go
import "strings"

strings.TrimSpaces(" STrinsf")
~~~
## Tratar erros
Para tratar erros de uma função usamos o if 
~~~go
resp, err := http.Get("www.go.dev")
if err != nil{
  fmt.Println(err)
}
~~~
# Orientação a Objeto

### Struct

Go tambem e uma linguagem orientada a objeto e a forma da estrutura mais basica e uma struct em go
~~~go
type Nome struct{
  nome string
  idade int
  saldo float32
  amigos string
}
~~~
### Instancia
E para instanciar uma struct em um variavel fazemos assim
~~~go
type Pessoa struct{
  nome string
  diade int
  saldo flaot32
  amigo string
}

var nome1 Pessoa = Pessoa{ //Forma completa
  nome: "Carlos",
  idade: 19,
  saldo: 0.0
}

nome2 := Pessoa{ //Forma rapida
  nome: "Kauan",
  idade: "20",
  saldo: "2.50"
}
~~~
>Essas formas utilizamos quando quisermos popular atributos especificos, ou seja, quando queremos que alguns não recebam valor e outros recebam. Assim devemos informar somente os campos que devem que recebam valores EX:
~~~go
nome3 := Pessoas{nome:"Gabriel", saldo := 12.90}
~~~
Assim somento os atributos nome e saldo recebem valores enquanto idade continuara zerado

Tambem temos uma forma mais fapida para instancia a struct
~~~go
nome4 := Pessoa{"Arthur", 19, 800.54}
~~~
Nesta forma e necessario que todos o valores sejam settados em ordem

Para acessarmos as os valores da instancia podemos chamar a instancia inteira ou um atributo especifico
~~~go
fmt.Println(nome2)
fmt.Println(nome1.idade)
~~~
Ao chamarmos a instancia inteira e retornadado um array com todos os atributos da instancia.
Tambem podemos atribuir de uma forma mais comum a outras linguagens de programação e usando ponteiros
~~~go
var nome5 *Pessoa
nome5 = new(Pessoa)
nome5.nome = "João"
nome5.idade = "25"
nome5.saldo = "0.0"
~~~
Dessa fora temos uma instancia da struct usando ponteiros
>Usando & temos o endereço de memoria e usando * temos o conteudo do endereço
~~~go
fmt.Println(&nome5) //Retorna o endereço de memoria
fmt.Println(*nome5) //Retorna o conteudo do endereço de memoria
~~~
O metodo da struct a referencia com o (this *NomeStruct) para referenciar a struct usando so o this.atributos para acessar os atributos dentro dos metodos

### Metodos
Os metodos da struct ficam fora do bloco do codigo da struct
~~~go
func (this *Pessoa) Falar struct{
  fmt.Println(this.nome,"Esta falando...")
}
~~~
### Relações entre structs
Para realizarmos operações entre structs devemos fazer o seguinte no metodo
~~~go
func (this *Pessoa) fazerAmigo(amigo *Pessoa){
  this.amigo = amigo.nome
  amigo.amigo = this.nome
}
~~~
Aqui nesse metodo dizemos que queremos adicionar uma pessoa como amigo de outra então nos parametros passamos amigo com o tipo da classe e o * porque queremos recebr um endereço de memoria como parametro
~~~go
nome5.fazerAmigo(&nome4)
~~~
Na hora de chamarmos a função e passarmos a outra instancia devemos utilizar o & junto com o nome da instancia, pois assim estamos passando o ponteiro como parametro 

### Visibilidade
Para tornarmos os atributos de uma struct visiveis em outros documentos devemos colocar os nomes dos campos com letras maiusculas assim
>Atributos com letras minusculas so são visiveis  somente dentro do arquivo da struct

## Ponteiros
Para indicarmos o endereço de memoria(ponteiro) de uma variavel usamos os & em uma variavel
ex:
~~~go
x := 5
y := &x
~~~
Assim y recebe o endereço de memoria de x
~~~go
*y = 10
~~~
Para definir um novo valor pra ser aramazenada no endereço de memoria de x que esta em y usamos a referencia de ponteiro o * assim e possivel manipular o endereço de memoria
>Sempre que quisermos manipular o endereço de memoria utilizamos o *

## Modularização(pacotes)
Para separarmos arquivos em modulos/pacotes devemos fazemos o seguinte
~~~go
///src/pkg/arquivo1.go

package arquivo1

func somar(a int, b int){
  return a+b
}
~~~
O package deve conter o nome que sera chamado
E para chamarmos esse modulo usamos
~~~go
///src/main.go

package main

import c "pkg/arquivo1"

func main(){
  soma := c.somar(1, 2)
}
~~~
O go sempre pocura os arquivos de importação dentra da pasta src então não e necessario colocar src
Voce deve colocar o caminho da pasta a partir do diretorio principal
Antes do caminho podemos utilizar um apelidado no qual sera uma forma de referenciar o pacote chamado dentro do codigo principal

### Gerenciador de dependencias
Em casos de problemas ao importar podemos usar o comando ```go mod``` no terminal para criarmos o gerenciador de dependencias 
Esse gerenciador e semelhante ao package.json do nodejs aonde estão listado todas nossas dependencias do projeto e tambem a versão do go utilizada no projeto juntamente com outras informações

# Back-end

##Subir server

Para Subirmos um servidor em go usamos o pacote net/http usando a função

~~~go
http.ListenAndServe(":PORTA", nil)
~~~
Assim ja temos um servidor ativo.

## Carregar arquivos html

Para respondermos a resquisição de com um arquivo html temos preimeiro que criar uma pasta para os templetes htmls e carregarmos eles dentro de uma variavel ou constante
~~~go
import "html/template"

const temp = tamplate.Must(temaplate.ParseGlob(("caminhoView/*.html"))
~~~
Assim pegamos todos os arquivos de uma pasta e carregamos dentro do constante temp para podermos usar nas respostas das requisições.
Para o go poder entender os arquivos htmls temos que fazer uma pequena auteração no codigo da seguinte forma
~~~html
{{define "index"}}
<!DOCTYPE html>
<html lang="pt-br" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Loja</title>
  </head>
  <body>
    Bem vindo a loja
  </body>
</html>
{{end}}
~~~
Adicionamos a linha {{define "index"}} alterando pro nome do aqruivo no começo e {{end}} no final para que o tample entenda que e um arquivo a ser rendereizado numa determinada rota

## Roteamento
Na definição de rotas usamos o handle func do net/http para definirmos a rota e a função de resposta
~~~go
http.HandleFunc("/rota", home)
~~~
>Em home e aonde chamaremos a função que criamos pra resposta da requisição na rota
E na função de resposta temos a segeuinte estrutura
~~~go
func home(w http.ResponseWrite,c http.Resquest){
  temp.ExecTemplate(w,"index", nil)
}
~~~
A função temp.ExecTemplate(w, "index", nil) e aonde usamos os templetes carregados da pasta na constante. E dentro dos parametros dessa função temos w que respresenta a resposta e "index" o nome do arquivo a ser carregado e.

### Form value
Quando precisamos pegar valores do formulario usamos req.FormValue() 
~~~go
req.FormValue("nome")
~~~
Essa função pega um dado mandando pelo metodo post

### Query params
Para pegar o um valor que veio na url usamos
~~~go
id := req.URL.Query().Get("id")
~~~
Para montar uma url com query params
~~~html
<a href="/id?id=5"></a>
~~~
Assim passamos o id 5 como query param

### POST
Quando precisamos pegar uma requisição do metodo post usamos
~~~go
func Update(res http.ResponseWriter, req *http.Request){
  if req.Method == "POST"{
  
  }
  http.Redirect(res, req, "/", 301)
}
~~~
Nesse caso pegamos a requisição de metodo post e dps redirecionamos pra rota principal 

## View Engine
O pacote html/teplate funciona como view engine podendo renderizar  as paginas html, epegar informações do  back e utilizar no front e usar trechos de codigo no html como ejs.
Na função de resposta pra rquisição exectempalte o ultimo parametros utilizamos um dados para passar e ser usado no front

~~~go
type Data struct{
  Nome string
}

datas := Data{Nome: "Carlos"}
temp.ExecuteTemplate(resp, "index", datas)
~~~
O ultimo parametro passamos a variavel ou array com os dados que queremos passar pro front
>Essa variavel deve ser uma instancia de uma struct para assim no front chamarmos os nomes de suas propriedades

E para usarmos um dado passado pro front usamos

~~~html
<h1>{{.Nome}}</h1>
~~~
>Sempre usando o as 2 {} e o 

### Partials
Para partials usamos o seguinte esquema. O arquivo que recebera a partial tera o nome com _ na frente e seu conteudo da seguinte mareira
>_header.html
~~~html
{{define "_header"}}
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Dark Store</title>
</head>
{{end}}
~~~
E na importação
>index.html
~~~go
{{template "_header"}}
~~~
Assim importamos a partial

### range
Para renderizar recursos automaticamaneto no html utilizamos a propriedade range
~~~html
<body>
  {{range .}}
  <p>{{.Nome}}<p>
  {{end}}
</body>
~~~
>Precisamos de uma vetor para usarmos esse metodo

Esse metodo fara uma leitura na no array puxand elemento por elemento e renderizando no html.

## Mysql

### Conexão
Para fazermos conexão com banco de dados mysql precisamos da biblioteca dos seguintes pacotes
~~~go
"database/sql"
_"github.com/go-sql-driver/mysql"
~~~
>O _ indica que não usaremos o pacote imdediatamente mas sim ao longo do codigo

Para instalar o mysql driver usamos o comando 
~~~sh
$ go get -u github.com/go-sql-driver/mysql
~~~

E apara conectar...
~~~go
db, err = sql.Open("mysql", "user:senha@tcp(host:porta)/banco")
~~~
Essa função retorna a conexão com o banco na variavel db e é com ela que faremos as outras coisas

### Exec
A função exec e utilizada quando não queremos nem um retorno sendo assim, com ela poedemos executar trechos de codigo sql
~~~go
_, err := db.Exec(fmt.Sprintf("INSERT INTO products (nome, descr, price, quant) VALUES ('%s', '%s', %f, %d)", name, descr, price, quant))
~~~
Atraves dessa função conseguimos fazer a maioria  das operações de um crud
>A funão sprintf converte tudo em string e recebe dados com os especificadores de formato como no c

### Query

Para fazermos uma query e utilzar esses dados primeiro devemos criar uma struct que vai representar a estrutura da tabla tanto para query quando inserts
~~~go
type Product struct{
  Id int
  Nome, Desc string
  Price float64
  Quant int
}
~~~
E logo em seguida criar uma função para pegar os dados do banco e disponibilizar para uso
~~~go
func Get()[]*Product{
  products := []*Product{}
  res, err := db.Query("SELECT * FROM products")
  if err != nil{
    fmt.Println("Erro ao ao realizar query\n", err)
    return nil
  }
  for res.Next(){
    var product Product
    if err := res.Scan(&product.Id, &product.Nome, &product.Desc, &product.Price, &product.Quant); err != nil{
      fmt.Println("Erro no scan\n",err)
      return nil
    }
    products = append(products, &product)
  }
  return products
}
~~~
Essa função deve retornar um ponteiro de array no qual sera um slice do mesmo tipo da strcut que criamos, esse array recebera os dados dessa structs.

Com a função db.query e feita uma query que busca todos os os registro da tabela no banco, esses registros vem em forma de array de ponteiros no qual precismos tratar.

O tratamento do array consiste em iterar  o array de resposta jogando seus dados dentro de uma variavel que recebera uma instancia da struct que sera jogado dentro da slice que armazenara o resultado final.

No for res.Next e aonde a ieteração do array de resposta acontece.

O res.Scan e responsavelpor pegar o elemento da vez(Que e um registro do banco) e salvar em algum lugar. Nesse caso em product(Do tipo Product) que declaramos dentro do next.Nessa 

Dps so jogamos a varaivel com os dados daquela iteração dentro do slice coma função append
E no final dps de organizar tudo retornamos o slice com todos os registros em ordem.

### Prapare
Para prepara o comando sql para execução usamos o metodo prepare
~~~go
    res, err := db.Prepare("update products set nome=?, descr=?, price=?, quant=? where id=?")
  if err != nil{
    fmt.Println("Erro ao ataualizar produtos", err)
  }
  _, err = res.Exec(nome, descr, price, quant, id)
  if err != nil{
    fmt.Println("Erro ao ataualizar produtos", err)
  }
~~~
Assim preparamos o comando e dps executamos com exec substituindo o ? pelos dados

### Close
Para fecharmos a conexão com o banco de dados usamos o camando
~~~go
defer db.Close()
~~~

### Sql Rows
Para settar umas var para receber dados do banco precisamos importar o database/sql e usar o tipo sql rows
~~~go
import "database/sql"

var db *sql.Rows
~~~

## MVC

Para criarmos um projeto com padrão MVC precisamos da seguinte estrutura de pastas.
* database / Que sera responsavel pela conexão com banco de dados
* models / Que sera responsavel pelas opreações do banco de dados
* router / Que sera responsavel por carregar nossas rotas
* controller / Que sera responsavel por carregar a logica de cada rota

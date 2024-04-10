<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT-r2eyxsfh-SqC6eFiFDvkaiKRln0IB-c8GvHpFuTKgg&s"><\img>
## Json
Para respondermos uma rota com uma json usamos 
~~~go
import(
  "encoding/json"
)

json.NewEncoder(res).Encode(var)
~~~
>Isso dentro de uma rota

O metodo newEncoder server para codificarmos uma struct em em formato json, Ideal para responder uma requisição com dados em json

~~~go
json.NewDecoder(req.Body).Decoder(&var)
~~~
Ja o metodo newDecoder server para decodificar o formato json e joga-lo dentro de uma ou struct

## Struct Json Models
Para definirmos uma struct pra receber um json usamos
~~~go
type Personalites struct {
  Nome string  `json:"nome"`
  History string `json:"history"`
}
~~~
## Gorilla Mux
Gorilla mux eu manipulador de rotas. Para sua instalação usamos 
~~~
go get -u github.com/gorilla/mux
~~~
E para sua importação no codigo
~~~go
import 
"github.com/gorilla/mux"
~~~
Para sua utilização temos que passarmos suas configurações nos arquivos de rotas da seguinte forma
~~~go
func HandleRequest() {
  rmux := mux.NewRouter()
  rmux.HandleFunc("/", controllers.Home)
  rmux.HandleFunc("/api/personas", controllers.AllPersonas)
  log.Fatal(http.ListenAndServe(":7070", rmux))
}
~~~
Settamos o new router e nas handle func ao inves de http passa a instancia do mux e da instancia do server passamos o mux como parametro, Assim o proprio mux lidara com o roteamento

### Pegando elementos da rota
Para passarmos um elemento pela rota usamos o seguinte ednpoint
~~~go
rmux.HandleFunc("/api/personas/{id}", controllers.OnePersona)
~~~
Assim o campo id podera ser pego no controller na rota da seguinte forma
~~~go
func OnePersona(res http.ResponseWriter, req *http.Request){
  vars := mux.Vars(req)
  id := vars["id"]
  for _, persona := range models.Personas{
    if strconv.Itoa(persona.Id) == id{
      json.NewEncoder(res).Encode(persona)
    }
  }
}
~~~
Nesse caso eu estou instanciando o var do mux para poder pegar o id que veio na rota e aramazenar na variavel id, dps um range para comparar o id que foi pego no endpoint com o id de um outro lugar

### Definindo metodo 
Para definir um determinado metodo em uma rota passamos
~~~go
rmux.HandleFunc("/api/persona/{id}", constrollers.sla).Methods("Get")
~~~
## Docker
### Imagens
#### POSTGRES
~~~yml
version: '3'
services:
  postgres:
    image: "postgres"
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=senha
      - POSTGRES_DB=banco
    ports:
      - "5432:5432"
    volumes:
      - ./migration/docker-database-initial.sql:/docker-entrypoint-initdb.d/docker-database-initial.sql

  pgadmin-compose:
    image: dpage/pgadmin4
    environment:
      PGADMIN_DEFAULT_EMAIL: "email"
      PGADMIN_DEFAULT_PASSWORD: "senha"
    ports:
      - "54321:80"
    depends_on:
      - postgres
~~~
#### MYSQL
~~~yml
version: "3"

services:
  db:
    container_name: mysql8
    image: mysql:8.0
    environment:
      MYSQL_DATABASE: banco
      MYSQL_USER: carlos
      MYSQL_PASSWORD: 1597
      MYSQL_ROOT_PASSWORD: 1597
    ports:
      - '3306:3306'
    volumes:
      - ./migration/docker-database-initial.sql:/docker-entrypoint-initdb.d/docker-database-initial.sql
    adminer:
      image: adminer
      resert: always
      ports:
        -8080:8080
~~~
#### Subir imagem
~~~sh
sudo docker-compose up -d
~~~

#### Derrubar imagem
~~~sh
sudo docker-compose down
~~~

#### Resetar imagem
~~~sh
sudo docker-compose restart
~~~

#### Ver containers ativos
~~~sh
sudo docker ps -a
~~~

## Middlewares
E muito comun precisarmos adicionar os mesmos procedimentos em rotas , e para evitarmos a replicação de codigos usamos middlewares.E usamaos da seguinte maneira
~~~go
func Name(next http.Handler) http.Handler{
  return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request){
  
      next.ServeHTTP(w, r)
  })
}
~~~
Criamos um arquivo e passamos a estrutura nessa forma dentro dessa função passamos o que queremos e retornamos o response writer e o request. E para utilizar esse middleware com gorilla mox settamos no arquivo de rotas
~~~go
rmux.Use(NameMiddleware)
~~~
Assim nosso roteador usa o middleware e sera aplicado a todas as rotas

## Gorm

>Lembresse de criar uma struct para representar a tabela do banco para ser exportada como tipo

### Instalação
Para importamos o gorm primeiro precisamos baixa-lo 
~~~
go get -u gorm.io/gorm
~~~
E tambem precisamos do driver do banco que vc vai usar, postgres, mysql, sqlite, sql server
Usamos go get com os seguintes modulos
* gorm.io/driver/mysql
* gorm.io/driver/postgres
* gorm.io/driver/sqlite
* gorm.io/driver/sqlserver

### Conexão
Uma conexão com banco postgres
~~~go
import(
  "log"
  "gorm.io/gorm"
  "gorm.io/driver/postgres"
)
 var(
   DB *gorm.DB
   err error
 )

 func ConnectDB(){
   connector := "host=localhost user=root password=root dbname=root port=5432 sslmode=disable"
   DB, err = gorm.Open(postgres.Open(connector))
   if err != nil{
     log.Panic("Error ao conectar com o banco de dados")
   }
 }
~~~

### Query all
Encontrar todos os dados do banco
~~~go
var p []Pessoas
DB.Find(&p)
~~~
Priemiro declaramos uma slice do tipo model do banco, realizamos a query no banco e jogamos esses dados dentro desse array
>Esse array recebera objetos

### Query one
Encontrar um registro especifico
~~~go
var p Pessoas
DB.First(&p, id)
~~~
Declaramos uma variavel para receber os dados e temos que passar o id dos registros que queremos

### Create
Criar um novo registro
~~~go
DB.Create(&p)
~~~
A vairevel p e do tipo model do banco ja com os dados preenchidos

### Delete
Deletar registros
~~~go
database.DB.Delete(&p, id)
~~~
Recebe o id do registro e uma variavel aonde sera jogando o registro que foi apagado, se os registros retornarem vazios significa que foi apagado com sucesso

### Edit
Editar registros
~~~go
DB.First(&editPersona, id)
DB.Save(&editPersona)
~~~
Para editar primeiro precisamos pegar o registro que queremos guarda-lo numa var do tipo do model e dps passaramos essa var na Save para ser atualizada

>DB deve ser uma instancia da conexão com o bancod e dados

## Auto migrations
Para criarmos as tabelas no banco a partir do gorm usamos
~~~go
type Student struct{
  gorm.Model
  Name string `json:"name"`
  CPF string `json:"cpf"`
  RG string `json:"rg"`
}
~~~
Primeiro temos que criar a struct com a correspondencia em json e a grom.Model, isso ira incluir os campos que o gorm necessita

Para execurtamos essa automigration temos que chamar
~~~go
DB.AutoMigrate(&Student{})
~~~
Passando uma o ponteiro de uma instancia da struct. Assim uma table sera criada com o tipo daquela strcut
>Auto migrations sempre tera que ser chamado no final do arquivo de conexão com o banco de dados

## Cors
Devido as politicas dos Cors , não e possivel acessar e consumir informações de diferentes dominios por padrão então temo que habilitar na hora da instancia do servidor. Para isso precisamos  baixar o pacote handdlers do gorilla com
~~~
got get github.com/gorilla/handlers
~~~
E para subir o servidor juntamente como mux usamos
~~~go
import(
  "github.com/gorilla/mux"
  "github.com/gorilla/handlers"
)

log.Fatal(http.ListenAndServe(":7070", handlers.CORS(handlers.AllowedOrigins([]string{"*"}))(rmux)))
~~~
Assim habilitamos o consumo de dados das outras aplicações

# Gin
### Intalação
O Gin e um Framework back end, para baixarmos usamos o seguinte comando.
~~~go
go get -u github.com/gin-gonic/gin
~~~
E fazer as importação pra utilização nos arquivos
~~~go
import "github.com/gin-gonic/gin"
~~~
Para podermos usar o Gin primeiro temos que instancia-lo com
~~~go
app := gin.Default()
~~~
Assim temos a instancia padrão do Gin e podemos utilizar para criar rotas e subir o servidor.

### Subir o servidor
Como nas o utras linguagens a instancia do servidor deve ser a ultima linha.
~~~go
app.Run()
~~~

### Rotas
Para criar rotas usamos
~~~go
app.GET("/rota", function Rota1(c *gin.Context))
app.POST("/rota2", function Rota2(c *gin.Context))
~~~
O metodo da rota vira dps da instancia do gin, logo apos o endingpoint daquela rota e em seguida a função que lidará com aquela rota
> Sempre passan o c *gin.Context como parametro da função

### Query params
Para pegar parametros pela urla usamos
~~~go
name := c.Params.ByName("nome do parametro")
~~~

### Resposta para uma requisição
Para responder uma requisição com um arquivo json usa-se
~~~go
c.JSON(200, gin.H{
  "Resp":"Conteudo"
 })
~~~
Assim conseguimos mandar um arquivo json como resposta de uma requisição.
> Quando recebemos uma query do banco, apenas passamos a variavel que recebeu os dados com o c.JSON

~~~go
c.JSON(200, varModel)
~~~

## Criptografia
https://gowebexamples.com/password-hashing/

## Validação de email
https://gosamples.dev/validate-email/

## Envio de email com gomail
~~~
go get gopkg.in/mail.v2"
~~~
Codigo exemplo
https://stackoverflow.com/questions/71675901/golang-send-mail-via-office365-smtp

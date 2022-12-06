## Json
Para respondermos uma rota com uma json usamos 
~~~go
import(
  "encoding/json"
  "net/http"
)

json.NewEncoder(res).Encode(models.Personas)
~~~
>Isso dentro de uma rota

## Struct Json
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

## Gorm

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

### Pegar registros
~~~go
DB.First(&p, id)
DB.Find(&p)
~~~
>&p A variavel que ira armazenar os dados, ela deve ser do tipo da struct criado pra representar a table do banco

First para pegar um elemento com o ID
Find para pegar todos os elementos

First para pegar um unico elemento

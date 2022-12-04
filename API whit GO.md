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

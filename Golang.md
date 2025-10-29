# 🦦 Guia Completo de Go (Golang)

## 📘 Introdução

No Go, **não utilizamos `;` no final das linhas** (exceto em casos muito específicos, como múltiplos comandos na mesma linha).  
Assim como em C, devemos **importar pacotes** para utilizar determinadas funções e recursos.

---

## ⚙️ Compilação

Para compilar um projeto ou arquivo Go para um sistema operacional específico, usamos:

```go
GOOS=windows go build name.go
```

---

## 🏁 Arquivo Principal

O arquivo principal do programa deve começar com:

```go
package main
```

Isso indica ao compilador que o arquivo é o ponto de entrada da aplicação.

---

## 💾 Variáveis

A declaração de variáveis em Go segue o formato:

```go
var nome tipo = valor
```

### Exemplos

```go
var taxa float32 = 1.05
var pi float64 = 3.14159265358979323846
```

> **float32** → usado para números decimais menores  
> **float64** → usado para maior precisão (equivalente ao `double` em outras linguagens)

### Valores padrão

Quando uma variável é declarada sem valor inicial:
- Números → `0`
- Strings → `""` (string vazia)
- Booleanos → `false`

### Inferência de tipo

Podemos declarar variáveis sem especificar o tipo — o compilador infere automaticamente:

```go
var nome = "Carlos"
```

> Para floats, o Go usa **float64** como padrão.

### Declaração curta

Forma simplificada de declaração:

```go
nome := "Carlos"
```

Também podemos declarar várias variáveis em sequência:

```go
var nome, altura, solteiro = "Marcos", 1.85, false
```

### Declaração curta em funções com múltiplos retornos

```go
content1, err := os.Open()
content2, err := os.Open()
```

Na primeira linha, `content1` e `err` são criadas.  
Na segunda, apenas `content2` é nova — `err` já existe e recebe um novo valor.  
É obrigatório que **pelo menos uma variável nova seja criada** para usar `:=`.

```go
content1, err := os.Open() // ok
content1, err := os.Open() // erro — nenhuma variável nova
content1, err = os.Open()  // correto — apenas atribuição
```

---

## 🔒 Constantes

Constantes devem ser declaradas **fora da função `main`** e antes de qualquer outra função:

```go
package main
import "fmt"

const id = 15

func main() {
  fmt.Println(id)
}
```

---

## 🔢 Tipos Primitivos

- **Inteiros:** `int8`, `int16`, `int32`, `int64`  
  (O `int` padrão ajusta-se à arquitetura do sistema — 32 ou 64 bits)
- **Alias:**
  - `rune` → `int32`
  - `byte` → `uint8`

---

## 📦 Funções de Módulos

Funções exportadas por módulos devem ter a **primeira letra maiúscula**:

```go
modulo.Func()
```

---

## 🖨️ Println

Para exibir algo no console, importamos o pacote `fmt`:

```go
import "fmt"

fmt.Println("Olá,", nome, "!")
```

---

## ⌨️ Entrada de Dados (Scan e Scanf)

### Usando `Scanf`
```go
fmt.Scanf("%d", &idade)
```
Usa um especificador de formato (`%d` para inteiros) e requer o **ponteiro da variável** (`&`).

### Usando `Scan`
```go
fmt.Scan(&nome)
```
Não exige especificadores, apenas o ponteiro.

---

## 🔍 Verificar Tipo (`reflect.TypeOf`)

```go
import "reflect"
fmt.Println(reflect.TypeOf(variavel))
```

---

## 🔁 Estruturas Condicionais

### `if` / `else if` / `else`

```go
if x == 1 {
  // ...
} else if x == 2 {
  // ...
} else {
  // ...
}
```

### `switch`

```go
switch opcao {
case 1:
  // ...
case 2:
  // ...
default:
  // ...
}
```

> Não é necessário `break` — a execução para automaticamente após cada `case`.

---

## 🔧 Funções

### Declaração simples
```go
func showDates() {}
```

### Com retorno
```go
func returnNumber() int {
  return 0
}
```

### Com múltiplos retornos
```go
func nameIdade() (int, string) {
  return 19, "Carlos"
}
```

Uso:
```go
idade, nome := nameIdade()
```

Ignorando valores:
```go
_, nome := nameIdade()
```

---

## 🚪 Encerrar o Programa

```go
import "os"
os.Exit(0) // 0 = sucesso, -1 = erro
```

---

## ⏰ Trabalhar com Tempo

```go
import "time"
fmt.Println(time.Now().Format("02/01/2006 15:04:05"))
```

🔗 [Tabela de formatação de tempo](https://go.dev/src/time/format.go)

---

## 🌐 Requisições HTTP

```go
import "net/http"
```

### GET Request
```go
resp, err := http.Get("https://site.com")
```

Retorna a resposta e um possível erro.

---

## 🔁 Laços de Repetição

### `for` tradicional
```go
for i := 0; i < 10; i++ {
  fmt.Println(i)
}
```

### Loop infinito
```go
for { }
```

### Percorrer arrays/slices
```go
for i, valor := range lista {
  fmt.Println(i, valor)
}
```

---

## 🧮 Arrays e Slices

### Array
```go
var nomes [4]string
```

### Slice (tamanho dinâmico)
```go
nomes := []string{"João", "Maria", "José"}
```

### Funções úteis
```go
len(nomes) // quantidade de itens
cap(nomes) // capacidade do slice
```

### Adicionar elementos
```go
nomes = append(nomes, "Carlos")
```

---

## 💤 Pausar Execução

```go
import "time"

time.Sleep(6 * time.Minute)
```

Unidades: `Second`, `Minute`, `Hour`

---

## 📂 Leitura e Escrita de Arquivos

### Abrir e fechar
```go
arquivo, err := os.Open("caminho")
defer arquivo.Close()
```

### Ler conteúdo inteiro
```go
import "io/ioutil"

dados, _ := ioutil.ReadFile("arquivo.txt")
fmt.Println(string(dados))
```

### Ler linha a linha
```go
import (
  "os"
  "bufio"
  "io"
)

arquivo, _ := os.Open("arquivo.txt")
leitor := bufio.NewReader(arquivo)

for {
  linha, err := leitor.ReadString('\n')
  if err == io.EOF {
    break
  }
  fmt.Print(linha)
}
```

---

## 🧱 Structs (Programação Orientada a Objetos)

### Declaração
```go
type Pessoa struct {
  Nome  string
  Idade int
  Saldo float64
}
```

### Instanciação
```go
p1 := Pessoa{"Carlos", 19, 500.0}
p2 := Pessoa{Nome: "Maria", Idade: 22}
```

### Ponteiros e Métodos
```go
func (p *Pessoa) Falar() {
  fmt.Println(p.Nome, "está falando...")
}
```

### Relações entre structs
```go
func (p *Pessoa) FazerAmigo(amigo *Pessoa) {
  p.Amigo = amigo.Nome
  amigo.Amigo = p.Nome
}
```

---

## 🧩 Modularização (Pacotes)

### Estrutura
```
src/
 ├─ main.go
 └─ pkg/
     └─ arquivo1.go
```

### arquivo1.go
```go
package arquivo1

func Somar(a, b int) int {
  return a + b
}
```

### main.go
```go
package main
import c "pkg/arquivo1"

func main() {
  soma := c.Somar(2, 3)
}
```

---

## 🌍 Back-End com Go

### Subir servidor
```go
import "net/http"
http.ListenAndServe(":8080", nil)
```

### Carregar HTML
```go
import "html/template"

var tpl = template.Must(template.ParseGlob("views/*.html"))
```

### Rotas
```go
http.HandleFunc("/", Home)

func Home(w http.ResponseWriter, r *http.Request) {
  tpl.ExecuteTemplate(w, "index", nil)
}
```

---

## 🗃️ Banco de Dados (MySQL)

### Conexão
```go
import (
  "database/sql"
  _ "github.com/go-sql-driver/mysql"
)

db, err := sql.Open("mysql", "user:senha@tcp(localhost:3306)/banco")
```

### Execução de comandos SQL
```go
db.Exec("INSERT INTO produtos (nome, preco) VALUES (?, ?)", "Mouse", 49.90)
```

### Consulta (`Query`)
```go
rows, _ := db.Query("SELECT id, nome FROM produtos")
for rows.Next() {
  var id int
  var nome string
  rows.Scan(&id, &nome)
}
```

### Fechar conexão
```go
defer db.Close()
```

---

## 🧠 MVC no Go

Estrutura recomendada:
```
/database     → Conexão com o banco
/models       → Operações com o banco
/controllers  → Lógica das rotas
/router       → Definição de rotas
/views        → Templates HTML
```

---

## 🔄 Auto Reload com Air

Instalação:
```bash
go install github.com/air-verse/air@latest
```

Execução:
```bash
air
```

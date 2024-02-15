## Comandos
Compilação
~~~
go buid arquivo.go
~~~
Este comando cria um arquivo binario que pode ser executado a qualquer momento sem processamentos adicionais

Compilação + Execução
~~~
go run arquivo.go
~~~
Este comando compila em binarios e executa em tempo real

## Args

O pacote "os" oferece funções para lidar com sistema operacional independente da plataforma.

Argumentos de linha de comando são  estão disponiveis em uma variavel Chamada Args, que faz parte do pacote "os", assim seu nome em qualquer lugar fora do pacote "os" vai ser os.Args.
Args e um slice de string com comandos inseridos pelo terminal.
O primeiro elemento de os.Args[0] e o nome do comando propriamente dito e os outros elementos são os argumentos apresentados ao programa quando sua execução é iniciada

Uma forma de filtrar os argumentos e usando a fatiação com slice[m:n], ficando dessa forma:
~~~
os.Args[1:len(os.Args)]
~~~
Esse comando faz uma fatia do slice Args , pegando somente os argumentos que não são o primeiro elemento que corresponde ao comando principal.

## Compilação

![image](https://user-images.githubusercontent.com/89313841/223324453-e215cbe7-bffe-4361-8e46-f4616524ceb6.png)

O codigo escrito em C# e precompilado para uma linguagem intermediaria chamada bytecode

Logo depois ele e executado pelo CRL(Common language runtime) a maquina virtual que executara o o programa no seu ambiente.

![image](https://user-images.githubusercontent.com/89313841/223324829-16ca3372-0401-4cd5-9fcc-c7ac68a1f51e.png)

## Estrutura

~~~CS
using System;
namespace NomeProjeto
{
  class Program
  {
    static void Main(string[] args)
    {
      Console.Writeline("Hello")
    }
  }
}
~~~

#### using System

Referencia para o namespace system, uma lib com funções basicas de entrada e saida do c#

#### namespace NomeProjeto{}

Namespace e um agrupamento de classes relacionadas daquele projeto.Essa declaração de namespace diz que esse sera o nome do agrupamento das classes do seu projeto

#### class Program{}

declaração da classe do seu programa. Nome da classe geralmente e o mesmo do seu arquivo

#### static void main(string[] args){}

Função principal e entry point do seu programa

## Tipos Basicos

https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/built-in-types-table

Todos os tipos tem seu nome da lib padrão do C# e seu nome do namespace do .net Framework

![image](https://user-images.githubusercontent.com/89313841/223333146-8f47f39b-5c4e-49cd-baab-309c70b38b09.png)
>OS primeiros 8 tipos são todos para numeros inteiros mudando apenas seu range e se e nagativo ou positivo

Assim para a declaração de uma variavel int poderiamos ter

~~~cs
sbyte x = 100;
SByte y = 200;
~~~
>Nuemros declarados como long por converão utilizamos o caractere "L" no final para indicar um numero longo

A varievel x sendo umma declaração com tipo basico do c# e a variavel y sendo uma declaração com o tipo basico fornecido pelo .net framewrok, sendo assim so possivel sua utilizção com sua importação

#### OVERFLOW de numeros

Quando uma operão entre numeros estrapola o limite de um tipo de dado, com asseguir

~~~cs
sbyte x = 127;
x++;
~~~

O tipo s byte tem o renge de -128 ate 127, fazendo a seguinte operação o range e estrapola, n C# quando isso acontece o valor definido apos a operação e o valor do limite oposto. Isso e uma caracteristica da representação dos numeros do C# chamada complemento a dois. Assim o valor da variavel x ao final da execução seria -128

#### char

Os tipos char recebem apenas caracteres. Os caracteres devem estar e aspas simples , tambem e possivel escerver um caractere com seu codigo unicode assim sendo necessario um \u antes do seu codigo
~~~cs
char x = 'A';
char y = '\u0041';
~~~

#### float

O tipo float deve conter o carcter f no final do numero, pois sem o carctere o compilador vai entender que o numero e tipo double
~~~cs
float peso = 99.50f;
~~~

#### string

Strings não são um tipo basico de dados

![image](https://user-images.githubusercontent.com/89313841/223514543-28fbb026-e66d-43eb-b777-fd39eca6321d.png)

Uma string e imutavel, ou seja uma vez criada não poder ser mudada.

Mas mesmo assim e possivel mudar o valor de uma variavel

~~~cs
string nome = "Jão Kleber";
nome = "Kleber";
~~~

O que acontece e que quando vc atribui um novo valor a essa var uma nova string e criada do zero.

>Strings são declaradas entre aspas duplas ""

#### object

São tipos genericos que podem armazenar todos os tipos de informação;


~~~cs
object nome = "João";
object altura = 1.85f;
object idade = 18;
object gender = 'M';
~~~

#### MinValue MaxValue

Todos os tipos numericos receben uma proprieadade chamada MaxValue e MinValue, que retornara o maior e o menor valor que podera ser armazenado.

~~~cs
int n1 = int.MinValue;
int n2 = int.MaxValue;
sbyte n3 = sbyte.MaxValue;
double n4 = double.MaxValue;
long n5 = long.MinValue;
~~~

## Comandos de saida

### Write r Writeline

Write e Writeline severvem para exibir informações so que o writeline quebra a linha e o write não

No caso de um numero float, podemos formatar a quantidade de casas exibidas assim

~~~cs
float saldo = 12.5675f;
Console.Writeline(saldo.ToString("F2"));
~~~

Assim sera formatado com o numero de duas casas

### Formatar flloat com .

Para formatarmos um numero float com o . ao inves de  , temos que fazer uso do namespace System.Gloabalization

~~~cs
using System.Globalization;
~~~

E tbm devemos aplicar a formatação da exibição da seguinte maneira

~~~cs
float saldo = 123.3214334f;
Console.Writeline(saldo.ToString("F2", CultureInfo.InvariantCulture));
~~~
## Templete string

Para adicionarmos valores e variaveis a uma sitring usamos dois metodos

#### Interpolação
~~~cs
int idade = 19;
double saldo = 182.34342;
string nome = "Carlos Kauan";

System.Console.WriteLine("{0} tem {1} anos e tem saldo igual a {2:F2} reais", nome, idade, saldo);
~~~
Assim adiocionando fora da string os valores em suas respectivas posições.


#### Placeholders
~~~cs
int idade = 19;
double saldo = 182.34342;
string nome = "Carlos Kauan";

System.Console.WriteLine($"{nome} tem {idade} anos e tem saldo igual a {saldo:F2} reais");
~~~

Usando o $"" assim podemos abrir uma chaves e passar o valor dentro da propria string;

## Conversão de tipos numericos

#### Implicita
A convsersão implicita acontece quando queremos converter um tipo menor(em bytes) para um maior, assim sendo possivel a converção implicita.

Ex:
~~~cs
float x;
double y;

x = 123.34f
y = x;
~~~

Assim o tipo float tendo o tamanho de 4 bytes e o double 8 bytes, assim cabendo perfeitamente e a converção implicita acontecendo

#### Casting

Quando não e possivel fazer uma converção implicita usamos o casting, e quando queremos converter um tipo maior(em bytes) para um tipo menor, usamos o seguinte artificio.

Ex:
~~~cs
float x;
double y;

y = 34234.5645645654;
a = (float)y;
~~~

Assim o valor que era double agora sera float

>Realizando este tipo de casting, o valor sera sujeito a perda de de valores.

#### Divisão de inteiros

Para podermos dividir inteiros temos que realizar o casting da operação pois o compiladaor podera entender que o resultado da operação

Ex:
~~~cs
float x = 5;
int y = 2;

double z = (double) x/y;
~~~

## Potencia e raiz quadrada

#### Potencia
~~~cs
double y = 4.0;
double potencia = Math.Pow(x, 2);
~~~

#### Raiz
~~~cs
double y = 4.0;
double potencia = Math.Sqrt(x);
~~~

## Console.ReadeLine()
Comando para entrada de dados padrão, retorna uma string

### Armazenar diferentes tipos de dados

O readeline so le valores inteiros, e pra armazenar esses valores em variaveis do seu tipo temos que ralizar um parse

~~~cs
int x = int.Parse(Console.ReadLine());
~~~
Convertendo o valor lido em string para int, o mesmo se aplica para outros tipos

### Armazenamento de float

Para armazenar o numero float corretamente precisamos definir sua leitura como ponto
~~~cs
double f = float.Parse(Console.ReadLine(), CultureInfo.InvariantCulture);
~~~

## type.parse()
Uma forma de converter string para outros tipos, e valido para todos os tipo
~~~cs
int i = int.Parse(Console.ReadLine());
char o = char.Parse(Console.ReadLine());
sbyte e = sbyte.Parse(Console.ReadLine());
~~~

## var.Split(' ');
Transforma um array em um vetor

Ex:
~~~cs
string a = "Maria Jose";
string[] vet = a.Split(' ');
~~~
Assim a var maria sera dividida e separada por espaço, definido dentro do split eo vetor tera Maria na posição 0 e Jose na posição 1

## Funções
Para cirar funções usamos 
~~~cs
static void Nome(){}
~~~
> Sempre em baixo da função pricipal

# Orientação a obejeto
## Inatancia de uma classe
Para de finir uma classe devemos fazer o seguinte

~~~cs
namespace Name{
  class Carro{
    public string Nome;
    public string Modelo;
  }
}
~~~

Aonde public define se o atributo sera ou não visivel fora da classe

Para instanciarmos uma classe usamos

~~~cs
Carro x = new Carro();
~~~
As classes tbm funcionam como tipos

### Alocação de memoria de classes
O c# aloca variaveis e objetos em memorias diferentes chamadas stack e heap

#### Stack
Local da memoria aonde e guardado variaveis estaticas

#### Heap
Local da memoria aonde as coisas são alocadas dinamicamente, aonde o nome da variavel da instancia na realidade e um ponteiro que aponta pro local da memoria aonde esta o objeto instanciado
#### Metodo ToString
Para definirmos od metodo tostring devemos utilizar
~~~cs
public override string ToString(){
   return "Slaa"
}
~~~

Usamos a palavra override no metodo para sobrescrever o metodo ja existente dentro da super class object

>Toda classe em C# euma subclasse de object

### Membros estaticos
São menbros quefazem sentido independentimente de de instancia de classes

Uma classe que possui somente menbros estaticos não pode ser instanciada

para criar uma classe com menbros estaticos usamos o chamada

~~~cs
public static int Div(int a, int b){}
~~~
>Isso dentro de uma classe, o mesmo serve para variaveis

### Metodo Construtor

Para definirmos um metedo construtor pra uma classe devemos definir um metododo com o mesmo nome da classe
~~~cs 
class Carro{
  public string Nome;
  public Carro(string nome){
    Nome = nome;
  }
}
~~~
Assim definimos um metodo construtor com parametros.

### Sobrecarga - override
Podemos definir mais de um metodo consctrutor mdaundo aepenas a quantide de parametros

~~~cs
public Carro(string nome, int ano, float preço){
  
}

public Carro(string nome, int ano){

}

public Carro(){

}
~~~
Assim quando o metodo e instanciado o que sera acionado sera somente o que tem a quantidade de parametros passado apenas

### This

A palavra this serve tanto para referenciar a instancia do proprio obejeto quanto para aproveitar metodos construtores

~~~cs
public Carro(string nome,float preço){
  Nome = nome;
  Preco = preco;
  
}

public Carro(string nome, float preço, int ano):this(nome, ano){
  Ano = ano;
}
~~~
Assim os atributos nome e preco serão definido pelo primeiro construtor que sera aproveitado pelo segundo, e o atributo ano sera definido pelo segundo.

### Get Sett Properties

Para definirmos uma proprieadade usamos
~~~cs
  public Name{
    get{}
    set{}
  }
~~~
E tbm existe tbm como criar auto properties, propriedades que se auto inplementam.

~~~cs
public string Nome{get; private set;}
~~~

### Modificadores de acesso

![image](https://github.com/carloskauan/Notes/assets/89313841/ff5a5bd7-b380-4dbc-9d3d-69a945a5432d)


## Classes são tipos de referencia

Variaveis cujos os tipos são classes não devem ser entendidas como caixas, mas sim ponteiros, que indicam um lugar na memoria.

![image](https://user-images.githubusercontent.com/89313841/234627399-2a6cbb3d-bd66-412d-8b38-b5f93856058f.png)

### Valor null

Tipos de refencia aceitam o valor "null" , que indica que a variavel aponta pra ninguem.

### Structs

Structs são caixas que armazenam os valores e não ponteiros

![image](https://user-images.githubusercontent.com/89313841/234629230-2acb048c-c49a-451a-a5cb-3b04a9a88dcf.png)

Os tipos primarios de dados são structs

Tambem podemos criar nosso proprios tipos structs

~~~cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace Structs{
    struct Point{
        public double x, y;
        public override string ToString(){
            return $"({x},{y})";
        }
    }
}
~~~

E para instanciarmos essa struct e usarmos ela , e feito o mesmo processo das classes normais

~~~cs
Point mp = new Point();

System.Console.WriteLine(mp);
~~~

Os tipos scrutcts São mais performaticos.

### Scruct vs Classe

![image](https://user-images.githubusercontent.com/89313841/235808600-f37f3a8b-6d37-4f59-ac8d-9d9f12268727.png)


### Garbage collector
Objetos alocados dinamicamente, quando não possuem mais referencias para eles , serão deslocados dinamicamente pelo garbage collector

Varivaeis locais são  deslocadas imediatamente quando seu escopo local sai de execução 

### Nullable

Recurso utilizado para permitir valores nulos em variaveis do tipo valor

~~~cs
string? nome = null;
~~~

Assim a variavel nome do tipo string pode tbm receber valores nulos

O valor nullable tem 3 operações basicas

#### x.GetValueOrDefault()

Uma operação aonde se em caso da falta do valor de uma valor pra variavel e retornado o valor padrão do tipo basico da variavel, assim existe um retorno ao inves de retornar null

~~~cs
int? x = null;

Console.WriteLine(x.GetValueOrDefault);
~~~

Aonde o retorno do console write seria o numero 0, pois e o valor padrão do tipo inteiro

#### x.Value

Operação aonde e retornado o valor dentro de uma variavel do tipo nullable, se caso dentro dessa variavel tiver null, e retornado um erro pois esse metodo so e possivel ser usado em var nullable com valores

~~~cs
double? x = 1.5;

System.Console.WriteLine(x.Value);
~~~

O valor exibido seria de 1.5 pois

#### Operador de coalescência nula

Quando queremos atribuir a uma variavel nullable outra de valor normal e queremos fazer uma atribuição com uma verificação

~~~cs
double? x = null;
double y =  x ?? 0.0;

System.Console.WriteLine(y);
~~~

Aonde a saida do cw seria 0.0, pois caso x seja null, o valor atribuido a variavel y e o de 0.0, e caso x tenha um valos !null, o valor sera atrbuido a y.

## Vetores

Para criarmos um vetor usamos

~~~cs
string[] x = new string[n]
~~~
## Modificadores de parametros

Para criar um função que possa receber uma quantidade variavel de parametros usamos os modificadores de parametros da seguinte forma

~~~cs
public static int Sum(params int [] numbers){

}
~~~

Nesse caso na chamada da função usariamos

~~~cs
Teste.Sum(1, 2, 3, 4, 5, 6)
Teste.Sum(1, 2, 3)
~~~

Assim os valores passados como parametros na função, ficam na ordem de inserção dentro do vetor passado na declaração da função <code>params int [] numbers</code>

### ref

O moddificador de paramtro faz com que o parametro aponte difertamente para a varaivel que esta sendo passado e não fazendo uma copia temporia e salvando ela n seu escolpo
~~~cs
public static int Triple(ref int x){

}
~~~
Assim indicando que so vai ser aceito tipos de referencia, e na chamada da função temos que usar

~~~cs
int a = 10;
Teste.Triple(ref a);
~~~
assim passamos a referencia da variavel a como parametro

### out
Diferente do ref que exigue que a variavel tenha que ter sido iniciada, o out não necessita disto, funcionando assim com varaiveis de saida, ou seja, servido para armazenar saidas de valores de uma função
~~~cs
public static int Triple(int a, out int triple){
  triple = a * 3;
}
~~~

Sendo necessario ser feito assim na implementação

~~~cs
int a = 10;
int result;
Teste.Triple(a, out result);
~~~
Assim a variavel result vai receber o valor do triplo calculcado dentro da função

## Boxing e Unboxing

### Boxing
Boxing e a conversão de um objeto tipo valor para um tipo referencia compativel. Por exemplo

~~~cs
int x = 20;
Object obj = x;
~~~

Object e um tipo generico aonde aponta para um espaço na memoria heap, x uma variavel de tipo inteiro aonde esta na memoria stack, quando escrevemos o codigo acima, criamos uma variavel na memoria stack chamada obj que aponta para um espaço na memoria heap que contem o valor de x, ou seja 20;

### Unboxing

Unboxing e o precesso inverso do boxing.Por exemplo 
~~~cs
int x = 20;
Object obj = x;
int y = (int) obj;
~~~
Temos uma variavel de tipo generico(referencia) e queremos converter para um tipo valor compativel, assim ao inves de termos uma referencia de obj na stack apontando para heap, temos um copia do valor que esta no espaço de memoria heap referenciado por obj na memoria stack e convertido para inteiro na variavel y.
> E para o unboxing e necessario fazer o casting e que seja um valor compativel

## Foreach
~~~cs
string[] names = new string[] {"maria", "karina", "Angela"};

foreach(string element in names){
 System.Console.WriteLine(element);
}
~~~

## Listas

Listas são providas da classe List e do Namespace System.Collections.Generics, tendo a seguinte unitizização
#### Import
~~~c#
using System.Collections.Generics;
~~~

#### Utilização
~~~c#
List<string> nomes = new List<string>();//Inicialização vazia;
List<int> notas = new List<int>(){10, 5, 3};//Inicailização com valores settados
~~~

### Caracteristicas
* Estrutura Homogenea (dados dos mesmo tipo)
* Ordenada (elementos acessados por meio de posições)
* Iniciada vazia e tamanho e inserção dimanica de acordo com a quantidade de elementos inseridos
* Cada elemento ocupa um no da lista 

#### Add
~~~c#
listName.Add(element);
~~~
Adiciona elementos no final da lista

#### Insert

~~~c#
listName.Insert(2, elemente);
~~~
> Metodo recebe dois parametros, o primeiro e o index para inserção do elemento e o segundo o proprio elemento a ser inserido

Este metodo adiciona um elmento em uma posição especifica fazendo com que o elemnto que esta naquela posição seja empurrado para a proxima e assim com os elementos subsequentes 
     
#### Find e FindLast

Este metodo realiza uma pesquisa e retorna o item encontrado

~~~cs
List<string> names = new List<string>();
names.Add("SALLY");
names.Add("ARMANDO");
names.Add("JOÃO");
names.Add("MARIANA");

foreach (var item in names){
  System.Console.WriteLine(item);
}

System.Console.WriteLine(names.Find(e => e[0] == 'S'));
System.Console.WriteLine(names.FindLast(e => e[0] == 'S'));
~~~
>Metodo utiliza expressão lambda e tbm pode usar função normal

~~~cs
static void Main(string[] args){
      List<string> names = new List<string>();
      names.Add("SALLY");
      names.Add("ARMANDO");
      names.Add("JOÃO");
      names.Add("MARIANA");

      foreach (var item in names){
        System.Console.WriteLine(item);
      }

      System.Console.WriteLine(names.Find(Sla));
    }

    static bool Sla(string e){
      return e[0] == 'M';
    }
~~~

#### FindIndex FindLastIndex

Assim como a função Find e FindLast mas ao inves de retornar o elemento retorna o index do elemento na list

~~~cs
names.FindIndex(e => e[0] == 'S');
names.FindLastIndex(e => e[0] == 'S');
~~~

#### Remove

Comandos para remover um elemento de uma lisa, seja ele um elemento especifico e unico com o Remove ou varios elementos de acordo com o predicato com o RemoveAll

~~~cs
names.Remove("SALLY");
names.Remove(e => e[0] == 'A');
~~~
> No exemplo usamos o remove para retirar "SALLY" da lista e no removeall retiramos todos os nomes que começam com a letra "A";

Tambem temos comandos para retirar elemento de um index especifico  como removeat e para remove elementos em um range com removerange

~~~cs
names.RemoveAt(2);
names.RemoveRange(1, 3); // Primeiro paramaetro e a posição de inicio e o segundo quantos elementos serão removidos a partir dele
~~~
> No removeat estamos removendo o elemento na posição da lista que se refere a "JOÃO" e no removerange estamos removendo 3 elementos a partir da posição 1 que seriam "ARMANDO", "JOÃO" e "MARIANA".

## Compilação

![image](https://user-images.githubusercontent.com/89313841/223324453-e215cbe7-bffe-4361-8e46-f4616524ceb6.png)

O codigo escarito em C# e precompilado para uma linguagem intermediaria chamada bytecode

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

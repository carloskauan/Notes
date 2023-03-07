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

A varievel x sendo umma declaração com tipo basico do c# e a variavel y sendo uma declaração com o tipo basico fornecido pelo .net framewrok, sendo assim so possivel sua utilizção com sua importação

### JVM

Java assim como C# e uma mistura de entra compilada e interpretada aonde primeiramente existe uma camada extra entre a compilação e execução do codigo

Java utiliza o conceito de maquina virtual, aonde existe, entre o sistema operacional e a aplicação , uma camada extra responsavel por por traduzir e executar o codigo previamente compilado em bytecode  para as respectivas chamadas do sistema operacional aonde ele esta rodando  no momento 

![modcomp](https://github.com/carloskauan/Notes/assets/89313841/270da8b3-877b-42fb-adc0-34cb01a5ca05)


Dessa forma seu programa apos desenvolvido pode ser executado em qualquer sistema operacional

### Estrutura basica

~~~java
public class myProgram{
  static void main(String[] args){
    System.out.println("Hello World");
  }
}
~~~

> O nome da classe deve ter o mesmo nome do arquivo

### Compilação e execução manual

Para compilarmos um arquivo java em byte code primeiro devemos ter certeza que o jdk que baixamos e o forncido pela propria oracle e usarmos o seguinte comando

~~~sh
javac myProgram.cs
~~~
> Lembre-se de esta no diretorio aonde seu arquivo esta salvo

Este comando gera uma arquivo .class com o mesmo nome do seu arquivo .java, esse e seu arquivo em bytecode usado pela jvm para a execução do que foi programado no seu arquivo .java

E para executar o programa que ja esta em formato bytecode(.class) usamos
~~~sh
java myProgram
~~~

Tambem podemos visulizar o conteudo de um arquivo .class usando o comando 
~~~sh
javap -c myProgram.class
~~~
> Devemos nos certificar que o caminho do java esteja devidamento adicionado ao path

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

### Variaveis

Toda variavel em java necessita da sua declaração de tipo que não pode ser muadado depois de declarado

~~~java
int idade;
~~~

Assim a varivel e iniciada sem nem um valor

### Orientação a objeto

#### Private

  Atributos de uma classe que so podem ser acessados dentro da classe da classe de origem

#### Public

  Atributos que podem ser acessados e visiveis dentro de fora da classe de origem

#### Protected

  Atributos que pode ser acessados fora da classe de origem e mas não são visiveis fora da classe de origem

#### Implemnetação

Classe Pessoa com atributo privado e protected, com metodos gett e sett para manipulação dos atributos privados
~~~java
public class Pessoa {
  protected String nome;
  private int idade;

  public String getNome(){
    return nome;
  }

  public void setNome(String nome){
    this.nome = nome;
  }

  public int getIdade(){
    return idade;
  }

  public void setIdade(int idade){
    this.idade = idade;
  }

  public void showDados(){
    System.out.println(this.nome+"\t"+this.idade);
  }
}
~~~~

Classe que implemnte a classe pessoa e manipula e atrbui seus metodos
~~~java
public class App {
    public static void main(String[] args) throws Exception {
        Pessoa pessoa1 = new Pessoa();

        pessoa1.setIdade(20);
        pessoa1.setNome("Carlos Kauan");

        pessoa1.showDados();
    }
}
~~~

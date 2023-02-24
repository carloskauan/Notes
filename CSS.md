## Box Model

~~~css
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
~~~

## houver

~~~css
 .class:hover{
  proprieadades
 }
~~~
Para transformar um elemnto quando mouse passar por cima

## Seletores
#### .class1.class2

Seleciona um elemto que tem duas classes ao mesmo tem

#### .class1 > .calss2

Seleciona somente filhas diretas de uma tag pai

#### .pai h1+p

Seleciona diretamente somente o primeiro p apos o h1 dentro do pai

#### .pai h1~p


Seleciona diretamente TODOS os p apos o h1 dentro do pai

### Pseudo classe

Para mudarmos estados de algo com css usamos as pseudo classe  da seguinte forma

~~~css
.class{
  transition: all 1s ease-in-out;
}

.class:hover{
  background: red;
}
~~~
Assim selecionamos uma classe e adicionos uma trasição que pegara 3 parametros, o primeiro defifnido como all diz que todas os eventos receberão o efeito de transição o segundo diz quanto tempo durará e o terceiro padrões da transição

### Pseudo classes

E possivel muda um elemnto com base em outro utilizando pseudoclasse

~~~css
input:chacked + p{
  color red
}
~~~
Assim mudando a cor da tag p apos de um chack box marcada

### Pseudo elements

Uma forma de adicionar elemetos ao html pelo css

### class:not(.classNegada)

Pseudo classe de negaç aonde  aplica um estilo pra um grupo de elementos menos ao elemento selecionado dentro do not

### class:nth-chield(3)

Aplica o estilo pra um grupo de elemntos mas somento os elementos com indices descrito

### Controle de vazamento de elemento

Usando a propriedade overflow:; w possivel controlar o comportamento do elemnto quando n

### display:float;

Faz com que o elemento use so o necessario de espaço e permite que outro tipo de conteudo flutue ate sua proximidade

### clear: ;

Faz limpar o lado de um elemento 

## Unidades de medias

### em

Faz com que o lemento se comporte baseando em um elemento pai mais proximo dele

Aonde quando temos por exemplo um classe pai com 50px de tamanho usamos 1em na classse filha para saber quantas a filha tem o tamanho do pai

### rem

A medida rem e bem partecida com o o em , mas ele se baseia de no tamanho da classe root do documento , no caso o html

Para fazermos o rem ter a mesma medida que o px temos que usar aseguinte configuração

~~~css
html{
  font-size: 62.5;
}
~~~

Assim sempre que formos definir o tamnho de font size usamos rem ao inves de px.

### vw e vh;

São medidas baseadas no tamanho da viewport do navegador, vw viewport widith vh viewport height, eles vão de 0 a 100

### %

Uma medida besada no tamanho da tag pai

### vmim e vmax

São medida relacionas as menores e maiores medidas de viewport 

## Textos

ttps://www.w3schools.com/css/css_text.asp

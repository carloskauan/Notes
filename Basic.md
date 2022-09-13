<h2>Compilação</h2>

<p>Para compilar devemos usar o gcc com os seguintes comandos</p>
<code>gcc -o nome_do_executavel nome_do_arquivo.c</code>

<p>Para executar em um ambiente linux</p>
<code>./nome_do_executavel</code>

<h2>Função main</h2>

<p>Dentro da função maim fica todas as linhas de codigo para execução<p>
<p>E necessario lembrar que C e case sensitive então não podemes escrever a função main com caracteres Maiusculos</p>
<p>OBS:Todo final de instrução deve conter os ; no final</p>

<h2><code>#includes</code></h2>

<p>A linguagem C em si não tem uma grande quantidade de funções mas suas libs dão um grande poder a linguagem</p>

<code> #include <stdio.h> </code> 
<p>Para importar funções de entrada e saida de dados</p>

<h2>Estrutura basica</h2>

<p>A estruruta basica do c e a seguinte...</p>

<p>#include <stdio.h> //Na primeiras linhas e onde importamos nossas bibliotecas</p>
<code>int main(){};</code>
<p>//Depois vem a declaração da função main</p>
  
<h2><code>printf()</code></h2>
  
<p>A função de saida<p>
  
  <h2><code>\n</code></h2>
<p>Caractere de nova linha<p>
  
<h2><code>/* */</code></h2>
<p>Comentarios</p>  
  
<h2>Variaveis</h2>
 
<p>Os tipos de variaveis são:<p>
<p>int // Inteiro // %d marcador de valor</p>
<p>char // Strings</p>
<p>float // Numeros com virgulas</p>
<p>double // Numeros com virgula muito grandes</p>
  
<p>Para mostras as variaveis no pprint temos que usar o especificador de tipo dentro das aspas</p>
  
<code>
  int x = 5;
  printf("%d",x);
</code>

<h2><code>scanf()</code></h2>
<p>Comando pra entrada de dados</p>
  
  <p><code>scanf("%d", &var)</code> //%d Especificador de tipo e &var indicação da variavel podendo pegar mais de dois valores por comando</p>

<h2><code>sizeof()</code></h2>
<code>sizeof(valor);</code>
<p>Para medir o valor em bytes de algo</p>
  
<h2>Tamanho em bytes</h2>
<p>Char = 1</p>
<p>Int = 2</p>
<p>Float = 4</p>
<p>Double = 8</p>
  
<h2>Tamanhos de ints</h2>
<p>short = Inteiros pequenos 2 // %hd maracador de tipo</p>
<p>long = inteiros grandes 4 // %ld marcador de tipos</p>
<p>signed = inteiros com sinal (negativos e positivos)</p>
<p>unsigned = apenas positivos //%u marcador de tipo %u</p>
<p>octal = base octadecimal // %o marcador de tipo</p>
<p>hexa = base hexadecimal</p>	
<p>unsigned short int// %hu</p>
<p>unsigned long int // %lu</p>
	
<p>Analisar a necessidade antes de usar</p>

<h2><code>fflaush(stdin)</code></h2>

<p>Limpar buffer com a entrada de teclado</p>

<h2>Char com valor em int</h2>
<p>OBS: Cada caractere char tem um valor correspondente como int, octal e hexa</p>
<p>Ex:</p>
<p>A - %c = A</p>
<p>A - %d = 65</p>

<p>Tambem podemos forçar uma conversão de tipo usando (tipo)variavavel</p>
<p><code>int num = 65; printf("%c", (char)num);</code></p>
<p>Assim a conversão sera feita para a exibição</p>
	
<p>Os tipos char tambem podem utilizar variações na declarações  sendo unsigned char e signed char para delimitar os valores das suas correspondecias em ASCII, o char padrão ja e unsigned mas em alguns complidaores os valores ASCII de alguns char usam valores negativos</p>

<h2>Operadores logicos</h2>

<p>&& - And</p>
<p>|| - Or</p>
<p>! - Not</p>
	
<h2> If ternario</h2>

<p>condição ? expressão1 : expressão2;</p>
<p>Ex:</p>
<code>x = x > 100 ? 1 : 2</code>

<h2>Switch</h2>

<p>Condicional por valor conatnate de uma mesma variavel</p>
<code>switch(variavel){case 'valor': ; break default:}</code>
	
<h2>While</h2>

<p>Laço de repetição por condição</p>
<code>while(condição){	}</code>

<h2>for</h2>
 
<p>Laço de repetição para quando o numero de interaçoes e conhecida pelo usuario</p>

<code>for(x =0; x<=10; n++){ }</code>

<h2>do..while</h2>

<p>Um laço que executa primeiro e faz a verificção no final da iteração</p>
<code>do{codigo}while(condicção);</code>

<h2>break e continue</h2>

<p>O break para um laço e o continue para a iteração atual e começa a proxima</p>

<h2><code>putchar(char);</code></h2>

<p>Para imprimir um caractere unico</p>

<h2>Vetores</h2>
	
<p>Vetores devem ser declarados o seu tipo e a quantidade de elementos</p>
<code> int vet[10];</code>
<p>Quando e iniciado mas nem um valor e settado, todos os indexs são ocupados com valores aleatorios iguais as variaveis. E quando algumas posições são settadas e outras não, o resto são ocupados por 0</p>
<code>char vogais[6] = {'a', 'e', 'i', 'o', 'u'};</code>
<p>Quando um vetor não e defindo o seu tamanho, o compilador cria o vetor com mesmo tamanho da quantidade de cargas iniciais</p>
<p>Ao passar um vetor como parametro de uma função, o C não se importa com o tamanho do verto, mas ss como seu tipo apenas. E Não e dentro de uma função não e possivel saber com quantos elementos um vettor foi declarado.</p>
<p>Então na hora de passa um vetor para um função, tbm pege e passe seu tamanho</p>

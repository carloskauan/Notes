# Introdução

## Estrutura basica do html

~~~html
<!DOCTYPE html>
<html lang="pt-BR">
  <head>
  <meta charset="utf-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>
  </title>
</head>
<body>
  
</body>
</html>
~~~

## Tags gerais

>Utilizamos o . pra podermos vizualizar as tags

Tag      | Descrição
:--------: | :------:
<.!DOCTYPE html>| Defini o tipo de documento como html
<.meta charset="utf-8"> | Definir utf-8 como caracteres padrão
<.a href="url" target="_blanc"> | Texto linkavel com a tag target que defini como a nova aba sera aberta
<.img src="" alt="" width="" height=""> | Imagens 
<.br/> | Quebra de linha
<.hr/> | Linha horizontal 
<.span> | Conteiner generico inline
<.div> | Conteiner generico em bloco
<.header> | Indica cabeçalho
<.section> | Conteiner generico mais atual
<.div> | Conteiner generico
<.article> |


## Tags de texto

Tag      | Descrição
:--------: | :------:
<.h1>  | Paragrafo, vai de 1 a 6
<.p>| Pargrafo padr
<.b>| Negrito com semantica
<.strong> | Negrito sem semantica
<.em> | Enafase
<.i> | Italico
<.del> | Risca uma palavra indicando erro
<.s> | Risca palavra sem semantica
<.ins> | Sublinha uma palavra indicando correção de um del
<.u> | Sublinha palavra sem semantica
<.small> | Diminui o tamanho do texto
<.sup> | Eleva um texto ou plavra
<.q cite=""> | Citação com ou sem link de referencia
<.blockquote> | Bloco de citação 
<.code> | Referencia um codigo
<.pre> | Conserva a pre formatção de um texto

## Listas ae tabelas

Tag      | Descrição
:--------: | :------:
<.ul> | Lista não ordenada
<.ol type="" start=""> | Lista Ordenada
<.li> | Elemento da lista
<.dl> | Lista descrita
<.dt> | Topico de lista descrita
<.dd> | Descrição de topico

## Tabelas

Tag      | Descrição
:--------: | :------:
<.caption> | Descrição
<.table> | Tabela
<.thead> | Cebeçalho da tabela
<.tr> | Linhas
<.th> | Titulo
<.tbody> | Corpo da tabela
<.td> | linha dentro do tbody
<.tfoot> | Rodape

### Display block
 São tags que pegam a largura inteira da e quebra a linha, assim ocupando a linha inteira 

### Links de ancora

Links de ancora são links que não apontam para endereços fora da pagina mas sim para elemento dentro da sua propria pagina

~~~html 
  <a href="#id"></a>
~~~

Precisamos definir um id ao elemento e tbm podemos definir uma propriedade no css para que dessa suavemente ate o elemento em questão

~~~css
html{
  scroll-behavior: smooth;
}
~~~

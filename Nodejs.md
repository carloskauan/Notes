Sempre que iniciar um projeto Node use o = npm init

const port = process.env.PORT || 2000
-Porta fornecida ou padrão

module.exports = x; comando para tranformar algo em um módulo

require ("./caminho") ; para chamar o módulo. (obs: armazenar em uma variável)

let http = require("http"); para acessar o módulo do Protocolo http no node js

http.createServer().listen(porta); para abrir um servidor em uma porta específica

createServer(function (res, req){
    res.end("msg")
}); para devolver uma mensagem quando um usuário acessar seu servidor

---Express---
para caregar o express no código primeiro damos um require

const express = require("express")
cons app = express ()

e usamos uma variável para fazer uma cópia do mudulo inteiro

app.listen(porta, function (){}); para rodar o servidor em uma porta com uma função de call back


app.get("caminho ", function(req, res){
    res.send(" Mensagem de retorno ")
})

/:parâmetro/:parâmetro; para adicionar paramentros nas rotas

req.params; para fazer requisição dos parametros  .nome no final para acessar um parametro específico

res.sendFile(__dirname+ "caminho"); para mandar arquivos html

res.post('/rota', (req, res){
   res.send("")
})

no a html

<form method='POST' action='/rota'>


/**
 * Configurando parse express
 */
app.use(express.urlencoded({extend: false}));
app.use(express.json());

/**
 * Configurando rota statica
 */
app.use(express.static('public'));


/**
 * Configurando e declarando rotas com router
 * @method router
 */
const router = express.Router();

router.get("/categories", (req, res)=>{
  res.render("");
});

module.exports = router;


/**
 * Carregamento de rotas do router
 *Importar o router numa variavel antes de carregar ela
 */
app.use("",Categories);


------EJS-------

app.set('view engine', 'ejs')
-Definir a view engine de html

res.render(" arquivoejs ")
-Pra mandar um arquivo para ser desenhando com resposta. OBS sem extensão e caminho total

app.get("/", (req, res) => {
  var nome = 'DARK'
  var empresa = 'Caraleo'
  res.render("index.ejs", {
    nome: nome,
    empresa: empresa,
    cnpj: 1234567,
    dono: 'Carlon'
  })
})
-Passar informações para o arquivo Ejs
no EJS

<%=nome%>
-Para exibir essa variável

<%if() %>

<%} else{%>

<%}%>
-Usar condicionais para exibir algo


<% array.forEach((elemento) => {%>
    codigo
<%})%>
-Listar objetos

app.use(express.static('public'))
-Definie uma rota para arquivos staticos para uso do html

Criar uma pasta chamada partials dentro de views para por nosso pedaços de html dentro e reutilizar...

<%-include ('partials/header.ejs') %>
---------------------
/**
 * SEQUELIZEEEE
 */
Relacionamentos
Model.hasMany(Model); 1pM
Model.belongsTo(Model);1p1

Model.destroy({where:{campo:campo}}).then(); //Apagar um registro
Model.update({campo: novoValor, campo2: novoValor}, {where:{campo: campo});//Para editar um dado

slugify; // Para transformar titulos em slugs no banco de dados para serem usados em urls
__________________________________________________________
## Botão que apaga dados do banco ##

Primeiro devemos esta em uma rota em que dados do banco são passados para o ejs

Primeiramente devemos criar a seguinte estrutura
~~~html
<form method="POST" action="/categories/delete">
  <input type="hidden" name="id" value="<%= cat.id %>">
  <button class="btn btn-danger">Excluir</button>
</form>
~~~

O formulario deve se do tipo hidenn e seu valor value vair o valor do id do campo que sera mandado pra rota e pego com o req.body.id

## Evitar apagar registros instantaneamente ## 

Para evitar esse tipo de acidente devos trabalhar com javascript do front end da seguinte maneira

~~~html
<form method="POST" action="/categories/delete" onsubmit="function(event, this)">
  <input type="hidden" name="id" value="<%= cat.id %>">
  <button class="btn btn-danger">Excluir</button>
</form>
~~~
Devemos adicionar o eveneto na tag e passar a função que vamos criar no js com dois parametros, o primeiro o event que referencia os eventos e o segundo que referencia o proprio formulario

No js deve ser assim dentro da tag script no mesmo

~~~javascript
    function confirmDelete(event, form){ //Função que vai fazer a confirmação
      event.preventDefault(); // Impedir o envio do submit
      var decision = confirm("Voçê deseja apagar essa categoria?"); // Capturar confirmação
      if (decision) form.submit(); // Caso verdade o envio e feito
    }
~~~

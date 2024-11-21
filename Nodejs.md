# Express

## Estrutura inicial

Para iniciarmos o express pecisamos importar o seu modulo e carregarmos em uma varaivel sua incialização.

~~~js
const express = require("express");
const app = express();
~~~

Para iniclaizar o servidor usamos o comando

~~~js
app.listen(7070 ,function(err){
  if(err){
    console.log("ERRO AO INCIAR SERVIDOR");
  }else{
    console.log("SERVIDOR INICIADO");
  };
});
~~~

Para de fato o servidor inciar precisamos declarar suas rotas ante de inciar o servidor usando os metodos http e seu tipo de resposta
~~~js
app.get("/", (req, res)=>{
  res.send("MSG...");
});
~~~

## Parametros


# Express

## Estrutura inicial

Para iniciarmos o express pecisamos importar o seu modulo e carregarmos em uma varaivel sua incialização.

~~~js
const express = require("express");
const app = express();
~~~

Precisamos declarar suas rotas ante de inciar o servidor usando os metodos http e seu tipo de resposta
~~~js
app.get("/", (req, res)=>{
  res.send("MSG...");
});
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

## FS E SERIALIZAÇÃO JSON

ler arquivos
~~~
let dados = fs.readFileSync("./path.json", {encoding: "utf-8"})
~~~

Criar arquivos com conteudo
~~~
fs.writeFileSync("./path.json", JSON.stringify(data), {encoding: "utf-8"})
~~~

~~~
fs.appendFileSync("./path.json", JSON.stringify(newData), (err)=>{
  console.log(err)
})
~~~


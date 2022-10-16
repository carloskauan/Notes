## Spacing ##

Modelagem de box model...
[Spacing](https://getbootstrap.com/docs/5.0/utilities/spacing/)

## Tabelas ##

Para criar uma tabela usamos a tag table com a class table

~~~html
<table class="table"> <!-- use a tag table-bodered para estlizar as bordas da table -->
    <thead> <!-- Cabecalho da tabela -->
        <tr><!-- linha da tabela -->
            <th>SLA</th> <!-- Coluna da tabela -->        
        </tr>
    </thead>
    <tbody><!-- Corpo da tabela -->
        <tr>Linha do corpo
            <th></th><!-- Dado da coluna -->
        <tr>    
    </tbody>
</table> 
~~~
## Navbar ##

Para criar uma navbar

~~~html
<nav class="navbar navbar-dark bg-primary"> <!-- Criação da navvar -->
 <a class="navbar-brand myNav ps-3" href="/"> <!-- Icone da navbar -->
   MyBlog
 </a>
 <ul class="navbar-nav"> <!-- Navegação -->
   <li class="nav-item"> <!-- Iten de navegação -->
       <a class="nav-link" href="#">Link</a> <!-- Link clicavel do item -->
   </li>
 </ul>
</nav>
~~~

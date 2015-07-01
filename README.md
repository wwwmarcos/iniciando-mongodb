# iniciando-mongodb

Ao utilizar o mongodb dependendo da linguagem utilizada os métodos podem mudar um pouco, é sempre bom entender oque esta acontecendo por debaixo do panos. Nessa trilha irei mostra como executar comandos básicos diretamente no terminal/command line.
O MongoDB é um banco de dados não relacional baseado em documentos, que trabalha com databases e collections (as collections são como as tabelas no sql, me julgue) para iniciar irei listar alguns comandos básicos.

###Listando Databases:

> show dbs

Usando esse comando, o mongo ira te mostrar todos os databases existentes. Cuidado, databases sem nenhum conteúdo, pois eles  não apareceram na lista.

###Mostrar database em utilização:

> db

O comando db irá mostrar o database que você está utilizando.

###Trocando de database / criando um novo:

> use nomeDoDataBase

O comando use é utilizado tanto para selecionar um database, quanto para criar um novo, então muito cuidado para não digitar errado o nome de seu database.

###Listar collections existentes:

> show collections

O comando show collections irá listar todas as collections presentes no database selecionado, se estiver em duvidas sobre o database em utilização, use o comando db.

###Criando uma nova collection:

> db.createCollection(“nomeDaCollection”)

Ao utilizar esse comando, uma nova collection é criada com o nome passado (é obrigatório usar aspas no nome)

<hr>

#CRUD

###Salvando documentos: Save / Insert

Para inserir dados em uma collection já existente utilizamos o comando save.

> db.nomedacollection.save({nome: “Jose”, idade: 20})

<i>Note que basicamente estamos passando um JSON para ser salvo.</i>

Podemos utitilizar também o comando insert e o resultado será o mesmo.

> db.nomedacollection.insert({nome: “Jose”, idade: 20})

###Recuperando documentos: Find.

O find é semelhante ao `SELECT` do sql.

> db.nomedacollection.find()

Utilizando a função find sem passar nada, o mongo ira nos retornar todos os documentos da collection em questão, “nomedacollection” no caso.
Para visualizar melhor os resultados podemos utiliza a função `.pretty()` e o mongo ira nos
mostrar o resultado em uma sintaxe melhor.

> db.nomedacollection.find().pretty()

Pesquisando em campos específicos.

> db.nomedacollection.find({nome: "Jose"});

Esse método retornaria todos os documentos em que no campo nome, o valor fosse "Jose".

 --- Pesquisando apenas um documento:

Quando queremos trazer apenas um registro utilizamos a função `findOne()`.
Essa função retorna somente o primeiro resultado encontrado.

> db.nomedacollection.findOne({nome: "Jose"});

###Alterando documentos: Update

Existem varias formas de realizar um update, vou mostrar uma que considero mais pratica. Utilizaremos uma variável (sim, é possível)

> var auxiliar = db.nomedacollection.findOne({nome: "Jose"})

<i>Você pode ver o conteúdo da variável auxiliar, digitando o nome dela e pressionando enter.</i>

Alterando o necessário (nesse exemplo estou alterando o nome, mas qualquer coisa poderia ser alterada):

> auxiliar.nome = "Novo nome";

Veja novamente o valor da variável auxiliar, o nome já deve estar alterado.

Iniciando o update:

> db.nomedacollection.update({_id: auxiliar._id}, auxiliar);

Nesse processo você busca o _id que vai ser alterado, comparando com o _id que esta na sua variável auxiliar, depois passa a variável auxilar. É como se dissesse, "ache esse _id e substitua pelo oque está na variável auxiliar"

###Removendo documentos: Remove

Para remover um documento, precisamos passar para a função uma parte do documento, no exemplo.

> db.nomedacollection.remove({nome: “Jose”})

É necessário tomar muito cuidado com os removes, para não remover mais que o deveria. Como por exemplo no comando acima ele removeria todos os documentos com nome "Jose".
Uma solução seria atribuir apenas um documento para uma variável:

> var auxiliar = db.nomedacollection.findOne({nome: "Jose"})

E depois assim excluir o documento selecionado.

> db.nomedacollection.remove({_id: auxiliar._id})







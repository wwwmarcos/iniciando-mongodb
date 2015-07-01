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

O comando show collections irá listar todas as collections presentes no database selecionado, se estiver em duvidas sobre o database em utilização, use o comando dB (somente as que tem algum conteúdo dentro)

###Criando uma nova collection:

> db.createCollection(“nomeDaCollection”)

Ao utilizar esse comando, uma nova collection é criada com o nome passado (é obrigatório usar aspas no nome)





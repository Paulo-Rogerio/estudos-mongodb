# Estudos Mongodb

### ================
### Daemon
```bash
MongoD
```

### ================
### Versao
```bash
mongod --version
```

### ================
### Conectando no MongoD ( Console )
```bash
mongo
```

### ================
### Criando novo Banco
```bash
> use dbcurso;
```

### ================
### Listando Bases MongoD

> show dbs;
admin    0.000GB
config   0.000GB
dbcurso  0.000GB
local    0.000GB

### ================
### Criando uma collection 
### Fazendo analogia com Bancos relacionais ( Uma tabela )
### O banco de dados não é totalmente criado até que você coloque algo nele.

> db.createCollection('postagens');

### ================
### Mostrar todas collection

> show collections;

### ================
### Inserindo registro
> db.postagens.save({name: "Paulo Rogerio"});
> db.getCollection("postagens").save({name: "Camilla Moureira"});

### ================
### Consulta
> db.getCollection("postagens").find({});

### ================
### Remover todos documentos de uma collection
### Delete sem where
> db.postagens.remove({});

### ================
### Dropar Collection
> db.postagens.drop();

### ================
### Dropar Banco
> use dbcurso;
> db.dropDatabase();

### ================
db.getCollection("postagens").find({})
 
### ===============
### Controle Transacional
### Deve ser feito em parte das aplicações que necessitam desse detalhe, não deve ser aplicado em todo o banco , pois isso foje do paradigma nosql.
### Ex: pagamentos, estoque
### Ex manipular algum registro que impacta diretamente em outras collection, ou seja, preciso garantir que os dados foram manipulados com sucesso
### Em todas as collection envolvidas e caso alguma encontre problemas todo a insercoes ou alteraçoões são desfeitas.
### Uso sob medida 

### ===============
### Shared Key ( distribuir os dados em várias máquinas distintas )
### Ex: Escolhi o estado como chave, toda vez que inserir um dado com a chave GO, esse dado vai para tal servidor.

### ===============
### Operadores de agregação
### Ex: lookup ( simula um join )
 https://docs.mongodb.com/manual/reference/operator/aggregation/out/
 
 https://docs.mongodb.com/manual/reference/operator/aggregation/merge/

 https://docs.mongodb.com/manual/reference/operator/aggregation/lookup/

### ===============
### Visão Materializada
### merge ( Área temporia (intermediária) onde os dados já estao pré-processado na visao materializada )
### O mongo não recuacula toda a query, o merge garante que apenas os registros incrementais sejam 
### inseridos na collection 

### ================
### Representação de um documento

```json
> db.usuario.findOne({idade:25})          
{
    "_id" : ObjectId("11111"),            
    "primero" : "Paulo",
    "ultimo" : "Gomes", 
    "idade" : "39",
    "hobby" : [
        "Aviação",
        "Alpinismo" ],
    "recomendações" : {
        "cor" : "azul",
        "esporte" : "futebol"
    }
}
```

#================



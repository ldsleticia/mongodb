# Como importar a collection no Mongo DB?
 * Você consegue importar a collection utilizando o comando 
 ```shell
mongoimport --db <NOME_DO_SEU_DB> --collection <NOME_DA_COLLECTION> --file nomesDeSereias.json
```
Lembre-se que você precisa ter instalado em sua máquina o MongoDB Database Tools. Caso não tenha, [clique aqui:](https://www.mongodb.com/try/download/database-tools) para baixar.

# Comandos utilizados

* Criação do banco de dados:
```shell
use gamapan
```

* Criação da collection:  
```shell
db.createCollection('NomesDeSereias')
```

* Listar collections existentes
```shell
show collections
```

* Deleção a collection:  
```shell
db.Consultas.drop()
```

* Inserção de Documento:  
```shell
db.collection.insert({"_id":{"$oid":"61807fe7780a6418112b903f"},"sereia":{"nome":"Adela","origem":"Germânico"}})
```

* Atualização de Documento:  
```shell
db.getCollection('NomesDeSereias').update(
    // query 
    {
        "sereia.nome" : "Acqua"
    },
    
    // update 
    {
        $set:{"sereia.origem" : "Latim"}
    },
    
    // options 
    {
        "multi" : false,  // update only one document 
        "upsert" : false  // insert a new document, if no existing document match the query 
    }
);
```

* Remoção de Documento:
```shell
db.sereias.remove({"sereia.nome" : "Acqua"})
```

* Consulta de Documento com Projeção:
```shell
db.getCollection('sereias').find({},{"sereia" : 1, "_id" : 0})
```

* Consulta com Combinação de Seletores (AND):
```shell
db.getCollection('sereias').find({"sereia.nome": /.*A.*/, "sereia.origem": /.*Germânico*/})
```

* Consulta paginada e ordenada:
```shell
db.sereias.find().limit(1) db.sereias.find().skip(2) db.sereias.find().sort({"sereia.nome":1})
```

<p align="center">
	<img alt="Naruto Uzumaki chegando" src="https://github.com/ldsleticia/gamaPanAcademyJavaBasico/blob/main/panGamaAcademy/assets/SIRINA_MERMAID_WEB-original.jpg" />
</p>

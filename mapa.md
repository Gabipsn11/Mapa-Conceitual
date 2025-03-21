# Mapa Mental - Comandos MongoDB

## 1. **Comandos de Criação e Remoção**

### - `db.createCollection()`
  - **Função**: Cria uma nova coleção.
  - **Exemplo**: `db.createCollection("minhaColecao")`

### - `db.collection.drop()`
  - **Função**: Remove uma coleção do banco de dados.
  - **Exemplo**: `db.minhaColecao.drop()`

### - `db.collection.renameCollection()`
  - **Função**: Renomeia uma coleção.
  - **Exemplo**: `db.minhaColecao.renameCollection("novaColecao")`

### - `db.collection.convertToCapped()`
  - **Função**: Converte uma coleção para uma coleção limitada (capped).
  - **Exemplo**: `db.minhaColecao.convertToCapped(1024)`

## 2. **Comandos de Inserção**

### - `db.collection.insertOne()`
  - **Função**: Insere um único documento em uma coleção.
  - **Exemplo**: `db.minhaColecao.insertOne({ nome: "João", idade: 30 })`

### - `db.collection.insertMany()`
  - **Função**: Insere múltiplos documentos em uma coleção.
  - **Exemplo**: `db.minhaColecao.insertMany([{ nome: "Maria", idade: 25 }, { nome: "Pedro", idade: 35 }])`

### - `db.collection.save()`
  - **Função**: Insere um documento ou atualiza se já existir.
  - **Exemplo**: `db.minhaColecao.save({ _id: 1, nome: "Carlos", idade: 40 })`

## 3. **Comandos de Consulta**

### - `db.collection.find()`
  - **Função**: Retorna todos os documentos que correspondem a uma consulta.
  - **Exemplo**: `db.minhaColecao.find({ idade: { $gt: 20 } })`

### - `db.collection.findOne()`
  - **Função**: Retorna um único documento que corresponde a uma consulta.
  - **Exemplo**: `db.minhaColecao.findOne({ nome: "João" })`

### - `db.collection.distinct()`
  - **Função**: Retorna um array de valores distintos para um campo especificado.
  - **Exemplo**: `db.minhaColecao.distinct("nome")`

### - `db.collection.aggregate()`
  - **Função**: Processa dados de documentos e retorna resultados computados.
  - **Exemplo**: `db.minhaColecao.aggregate([{ $match: { idade: { $gt: 20 } } }, { $group: { _id: "$status", total: { $sum: 1 } } }])`

## 4. **Comandos de Atualização**

### - `db.collection.updateOne()`
  - **Função**: Atualiza um único documento que corresponde a uma consulta.
  - **Exemplo**: `db.minhaColecao.updateOne({ nome: "João" }, { $set: { idade: 31 } })`

### - `db.collection.updateMany()`
  - **Função**: Atualiza múltiplos documentos que correspondem a uma consulta.
  - **Exemplo**: `db.minhaColecao.updateMany({ idade: { $lt: 30 } }, { $set: { status: "jovem" } })`

### - `db.collection.replaceOne()`
  - **Função**: Substitui um único documento que corresponde a uma consulta.
  - **Exemplo**: `db.minhaColecao.replaceOne({ nome: "Ana" }, { nome: "Ana", idade: 29, cidade: "São Paulo" })`

### - `db.collection.findOneAndUpdate()`
  - **Função**: Encontra um documento e o atualiza.
  - **Exemplo**: `db.minhaColecao.findOneAndUpdate({ nome: "Carlos" }, { $set: { idade: 41 } })`

## 5. **Comandos de Remoção**

### - `db.collection.deleteOne()`
  - **Função**: Remove um único documento que corresponde a uma consulta.
  - **Exemplo**: `db.minhaColecao.deleteOne({ nome: "Pedro" })`

### - `db.collection.deleteMany()`
  - **Função**: Remove múltiplos documentos que correspondem a uma consulta.
  - **Exemplo**: `db.minhaColecao.deleteMany({ idade: { $gt: 30 } })`

### - `db.collection.findOneAndDelete()`
  - **Função**: Encontra um documento e o deleta.
  - **Exemplo**: `db.minhaColecao.findOneAndDelete({ nome: "Carlos" })`

## 6. **Comandos de Índices**

### - `db.collection.createIndex()`
  - **Função**: Cria um índice em um campo especificado.
  - **Exemplo**: `db.minhaColecao.createIndex({ nome: 1 })`

### - `db.collection.dropIndex()`
  - **Função**: Remove um índice de uma coleção.
  - **Exemplo**: `db.minhaColecao.dropIndex("nome_1")`

### - `db.collection.getIndexes()`
  - **Função**: Retorna uma lista de índices em uma coleção.
  - **Exemplo**: `db.minhaColecao.getIndexes()`

### - `db.collection.dropIndexes()`
  - **Função**: Remove todos os índices de uma coleção.
  - **Exemplo**: `db.minhaColecao.dropIndexes()`

### - `db.collection.reIndex()`
  - **Função**: Recria todos os índices de uma coleção.
  - **Exemplo**: `db.minhaColecao.reIndex()`

## 7. **Comandos de Estatísticas e Validação**

### - `db.collection.stats()`
  - **Função**: Retorna estatísticas sobre uma coleção.
  - **Exemplo**: `db.minhaColecao.stats()`

### - `db.collection.validate()`
  - **Função**: Valida a integridade de uma coleção.
  - **Exemplo**: `db.minhaColecao.validate()`

### - `db.collection.dataSize()`
  - **Função**: Retorna o tamanho dos dados de uma coleção.
  - **Exemplo**: `db.minhaColecao.dataSize()`

### - `db.collection.totalSize()`
  - **Função**: Retorna o tamanho total de uma coleção, incluindo índices.
  - **Exemplo**: `db.minhaColecao.totalSize()`

### - `db.collection.storageSize()`
  - **Função**: Retorna o tamanho de armazenamento de uma coleção.
  - **Exemplo**: `db.minhaColecao.storageSize()`

### - `db.collection.totalIndexSize()`
  - **Função**: Retorna o tamanho total dos índices de uma coleção.
  - **Exemplo**: `db.minhaColecao.totalIndexSize()`

## 8. **Comandos de Monitoramento e Observação**

### - `db.collection.watch()`
  - **Função**: Assiste mudanças em uma coleção.
  - **Exemplo**: 
    ```javascript
    const changeStream = db.minhaColecao.watch(); 
    changeStream.on("change", (change) => console.log(change));
    ```

### - `db.collection.explain()`
  - **Função**: Fornece informações sobre como uma operação será executada.
  - **Exemplo**: `db.minhaColecao.find({ idade: { $gt: 20 } }).explain("executionStats")`

### - `db.collection.countDocuments()`
  - **Função**: Conta o número de documentos que correspondem a uma consulta.
  - **Exemplo**: `db.minhaColecao.countDocuments({ idade: { $gt: 20 } })`

## 9. **Comandos de Agregação**

### - `db.collection.mapReduce()`
  - **Função**: Processa documentos e retorna resultados agregados.
  - **Exemplo**: 
    ```javascript
    db.minhaColecao.mapReduce(
      function() { emit(this.nome, 1) }, 
      function(key, values) { return Array.sum(values) },
      { out: "resultadoMapReduce" }
    );
    ```

# Criando conexão com o Banco de Dados MySQL
O banco de dados MySQL é onde estão armazenados os dados de uma aplicação. Para realizar a conexão do banco no Express é preciso ter o MySQL instalado na máquina. Além disso, é necessario instalar o módulo MySQL.

## 1. Instalação do módulo MySQL
1. Inicialize o servidor MySQL.
2. Na pasta do projeto, instale o pacote MySQL:
   ```bash
   npm install --save mysql
   ```
3. Na pasta do projeto, crie uma subpasta chamada ```utils```.
4. Na sequência, dentro da subpasta ```utils```, crie um arquivo chamado ```db.js```:
   ```javascript
   const mysql = require('mysql');
   const db = mysql.createConnection({
       host: 'localhost',
       user: 'root',
       password: '',
       port: 3306,
       database: 'dbbiblioteca',
       multipleStatements: true
   });

   db.connect(function(erro) {
     if (erro){
        throw erro;
     }
     console.log('Conectado ao BD...');
   });
   
   global.db = db;
   module.exports = db;
   ```
   **ATENÇÃO:** Por motivos de sergurança nós não subimos para o GitHub os dados de conexão do banco, pois permite a invasoes de usuaários mal-intencionados. Com isso, criamos um arquivo `.env` para armazenar dados da conexão, a qual deve ser ignorado no commit para o GitHub.

## 2. Retornando dados do banco
Para retornamos os dados do banco utilizamos o objeto da conexão `db`.
```javascript
let express = require('express');
let router = express.Router();
let db = require('../utils/db');

/* Outras rotas definidas anteriormente... */
router.get('/autores/listar', function(req, res) {
   db.query('SELECT * FROM TbAutor', [], function(erro, listagem){
      if (erro){
         res.send(erro);
      }
      res.send(listagem);
   });
});

module.exports = router;
```
- **`router.get`**:
- **`'/autores/listar'`**:
- **`db.query`**:
- **`'SELECT * FROM TbAutor'`**:
- **`[]`**:
- **`function(erro, listagem)`**:

# Rotas
Rotas são os caminhos definidos por um sistema de roteamento para direcionar as requisições do usuário para os recursos corretos de uma aplicação. 
Elas associam um endereço (URL) a uma função específica, como a exibição de uma página HTML, o processamento de um formulário ou a chamada de uma API. 
Isso permite que a aplicação responda a diferentes URLs sem que cada uma corresponda diretamente a um arquivo estático no servidor. 

## 1. Criando rotas
```JavaScript
let express = require('express');
let router = express.Router();

/* Rota principal usando a view index.ejs. */
router.get('/', function(req, res, next) {
res.render('index', { title: 'Express' });
});

/* Rota “sobre” sem usar uma view. */
router.get('/sobre', function(req, res) {
let msg = '<h2>Sobre Rotas...</h2>';
res.send(msg);
});

module.exports = router;
```

## 2. Usando parâmetros em Rotas
Para utilizamos parâmetros em rotas utlizamos ```params```.
```JavaScript
let express = require('express');
let router = express.Router();

/* Outras rotas definidas anteriormente... */

/* Rota usando 1 parâmetro enviado na URL. */
router.get('/ola/:nome', function(req, res) {
  let msg = '<h2>Olá, ' + req.params.nome + '!</h2>';
  res.send(msg);
});

/*Podemos adicionar mais de um parâmetro na rota.*/
router.get('/ola/:nome/:sobrenome', function(req, res) {
  let msg = '<h2>Olá, ' + req.params.nome + " " + req.params.sobrenome + '!</h2>';
  res.send(msg);
});

module.exports = router;
```
Também podemos utilizar o ```query``` para acessar mais de uma parâmetro na URL, desde que comece com "?" e os parâmetros sejam separados por "&".
```JavaScript
let express = require('express');
let router = express.Router();

/* Outras rotas definidas anteriormente... */
/* Rota "imc" com vários parâmetros: localhost:3000/imc/?peso=88&estatura=1.82 */
router.get('/imc', function(req, res) {
  let peso = req.query.peso;
  let estatura = req.query.estatura;

  let imc = peso / Math.pow(estatura, 2);
  let msg = '<h3>Seu IMC é ' + imc.toFixed(2) + '</h3>';
  res.send(msg);
  //Resposta: "Seu IMC é 26.57"
});

module.exports = router;
```




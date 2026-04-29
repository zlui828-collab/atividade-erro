Criando o banco:
use redefastfood

Criando collections:
db.produtos.insertMany([
  {
    nome: "X-Burger",
    preco: 15.90,
    categoria: "Lanche",
    disponivel: true
  },
  {
    nome: "Batata Frita",
    preco: 9.90,
    categoria: "Acompanhamento",
    disponivel: true
  },
  {
    nome: "Refrigerante",
    preco: 6.00,
    categoria: "Bebida",
    disponivel: true
  }
])

Criando segunda collection:
db.lojas.insertMany([
  {
    nome: "Burger Rápido Centro",
    endereco: "Rua A, 123",
    telefone: "11999999999"
  },
  {
    nome: "Burger Rápido Norte",
    endereco: "Av B, 456",
    telefone: "11888888888"
  },
  {
    nome: "Burger Rápido Sul",
    endereco: "Rua C, 789",
    telefone: "11777777777"
  }
])

Fazendo find:
db.produtos.find()
db.lojas.find()

Fazendo o backup (no terminal):
mongodump --db redefastfood --out ./backup

Excluindo o banco, após o backup:
use redefastfood
db.dropDatabase()

Fazendo o restore do banco(no terminal):
mongorestore --db redefastfood ./backup/redefastfood

Excluindo o banco novamente:
use redefastfood
db.dropDatabase()

Fazendo a exportação:
mongoexport --db redefastfood --collection produtos --out produtos.json
mongoexport --db redefastfood --collection pedidos --out pedidos.json

Fazendo a importação:
mongoimport --db redefastfood --collection produtos --file produtos.json
mongoimport --db redefastfood --collection pedidos --file pedidos.jsonCriando o banco:
use redefastfood

Criando collections:
db.produtos.insertMany([
  {
    nome: "X-Burger",
    preco: 15.90,
    categoria: "Lanche",
    disponivel: true
  },
  {
    nome: "Batata Frita",
    preco: 9.90,
    categoria: "Acompanhamento",
    disponivel: true
  },
  {
    nome: "Refrigerante",
    preco: 6.00,
    categoria: "Bebida",
    disponivel: true
  }
])

Criando segunda collection:
db.lojas.insertMany([
  {
    nome: "Burger Rápido Centro",
    endereco: "Rua A, 123",
    telefone: "11999999999"
  },
  {
    nome: "Burger Rápido Norte",
    endereco: "Av B, 456",
    telefone: "11888888888"
  },
  {
    nome: "Burger Rápido Sul",
    endereco: "Rua C, 789",
    telefone: "11777777777"
  }
])

Fazendo find:
db.produtos.find()
db.lojas.find()

Fazendo o backup (no terminal):
mongodump --db redefastfood --out ./backup

Excluindo o banco, após o backup:
use redefastfood
db.dropDatabase()

Fazendo o restore do banco(no terminal):
mongorestore --db redefastfood ./backup/redefastfood

Excluindo o banco novamente:
use redefastfood
db.dropDatabase()

Fazendo a exportação:
mongoexport --db redefastfood --collection produtos --out produtos.json
mongoexport --db redefastfood --collection pedidos --out pedidos.json

Fazendo a importação:
mongoimport --db redefastfood --collection produtos --file produtos.json
mongoimport --db redefastfood --collection pedidos --file pedidos.json
## CleanFast Lavanderias

### Briefing

Durante uma reunião presencial, a empresa **CleanFast Lavanderias** relatou a 
necessidade de organizar melhor suas informações operacionais. A empresa 
possui clientes recorrentes, diferentes tipos de serviços (lavagem, secagem, 
passadoria), pedidos com status variados, valores, datas e funcionários por 
unidade.

O cliente solicitou o uso de **MongoDB**, visando flexibilidade no armazenamento de 
dados como textos, números, datas, arrays, documentos e controle de usuários.

#### Objetivo

Desenvolver um banco de dados **MongoDB** que represente o funcionamento 
básico de uma rede de lavanderias

### Database

- Criando o banco de dados

```js
use lavanderia
```

- Criando a collection `clientes` e inserindo dois documentos nela

```js
db.clientes.insertMany([
    {
        id: "1",
        nome: "Felipe",
        telefone: "11975474363",
        endereco: "R. Augusta, 2107 - Cerqueira César, São Paulo - SP",
        ativo: true
    },

    {
        id: "2",
        nome: "Samuel",
        telefone: "11946520987",
        endereco: "R. Monteiro Lobato, 81 - Jardim Jacira, Itapecerica da Serra - SP",
        ativo: true
    }
]);
```

- Criando a collection `pedidos` e inserido um documento contendo os serviços disponibilizados pela lavanderia

```js
db.pedidos.insertMany([
    {
        id_cliente: "1",
        data_criacao: "2026-04-26",
        servicos: [
            {
                tipo: "Lavagem",
                preco: 19.99,
                quantidade: 6,
                observacoes: "Todas roupas brancas"
            }
        ],
        status: "Finalizado"
    },

    {
        id_cliente: "2",
        data_criacao: "2026-04-28",
        servicos: [
            {
                tipo: "Lavagem",
                preco: 19.99,
                quantidade: 4
            },
            {
                tipo: "Secagem",
                preco: 9.99,
                quantidade: 4
            }
        ],
        status: "Em Andamento"
    }
]);
```

- Realizando consultas na collection `pedidos`

```js
db.pedidos.find();
```

```js
db.pedidos.find(
    { status: "Em Andamento" }
);
```

- Atualizando o status de um pedido

```js
db.pedidos.updateOne(
    { id_cliente: "2" }, { $set: { status: "Finalizado" } }
);
```

- Atualizando o status dos documentos

```js
db.pedidos.updateMany(
    { status: "Finalizado", data_criacao: { $gte: "2026-04-25", $lte: "2026-04-29" }  }, { $set: { status: "Em Andamento" } }
);
```

- Armazenando os dados de um documento da collection `clientes` numa constante

```js
const cliente = db.clientes.findOne();
```

- Verificando tipo de dado dos campos da collection `clientes`

```js
typeof cliente.nome;
typeof cliente.telefone;
typeof cliente.ativo;
```

- Deletando um documento da collection `clientes`

```js
db.clientes.deleteOne({ id: "2" });
```

- Deletando mais de um documento da collection `pedidos` que atendem ao filtro especificado

```js
db.pedidos.deleteMany({ status: "Em Andamento", data_criacao: { $gte: "2026-04-25", $lte: "2026-04-29" } });
```

- Criando um utilizador no banco de dados com capacidade de leitura e escrita somente

```js
db.createUser({
    user: "Felipe",
    pwd: "Flp123",
    roles: [
        { role: "readWrite", db: "lavanderia" }
    ]
});
```

- Listando todos os utilizadores do banco de dados da lavanderia

```js
db.getUsers();
```

- Deletando o utilizador criado anteriormente

```js
db.dropUser("Felipe");
```

- Deletando a collection `pedidos` do banco de dados

```js
db.pedidos.drop();
```

- Deletando o banco de dados

```js
db.dropDatabase();
```

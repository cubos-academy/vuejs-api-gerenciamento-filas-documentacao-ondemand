![](https://i.imgur.com/xG74tOh.png)

# Documentação API Gerenciamento de Filas

Essa é uma documentação simplificada para a API de gerenciamento de filas, é importanto você entender que deve seguir todas as informações contidas aqui.


**Url da API**: https://queue-management.pedagogico.cubos.academy/

## POST `/login?userEmail=seuemail@email.com`

Essa é uma rota que serve para um administrador se autenticar.

É **importante** ressaltar que *seuemail@email.com* é onde você deve inserir o seu e-mail de uso pessoal, para que você possa ter identificação única no sistema.

A senha deve ser sempre a mesma: **abc123**


#### Body da Requisição:
```json 
{
    "email":"seuemail@email.com",
    "password":"abc123"
}
```

#### Retorno da requisição: 

```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InBlZHJvQGdtYWlsLmNvbSIsImlhdCI6MTY3NDE0ODg0MCwiZXhwIjoxNjc0MjM1MjQwfQ.Iqev2UUCVRyy1ULDDbF8-kFRmgFcm0wTEAWGrYkA8Uk"
}
```

--- 
## GET `/products`

Essa rota devolve os produtos cadastrados no banco de dados.


#### Retorno da Requisição:
```json 
[
  {
    "id": "bcb23e2c-a808-48b6-aa31-ee87c87e1f57",
    "createdAt": "2023-01-11T19:46:44.094Z",
    "updatedAt": "2023-01-11T19:46:44.094Z",
    "name": "X- Bacon ",
    "price": 22.5,
    "image": "https://assets.unileversolutions.com/recipes-v2/230412.jpg?imwidth=800"
  },
  {
    "id": "0e46e76a-4401-4fd6-bbac-756674a16e9d",
    "createdAt": "2023-01-11T19:46:44.094Z",
    "updatedAt": "2023-01-11T19:46:44.094Z",
    "name": "X-Tudo",
    "price": 28.5,
    "image": "https://embutidosbonatti.ind.br/temp/xxx-57-980x550m0.jpg"
  },
  {
    "id": "7ec6303c-332e-4424-9bff-45273038c0cc",
    "createdAt": "2023-01-11T19:46:44.094Z",
    "updatedAt": "2023-01-11T19:46:44.094Z",
    "name": "X-Salada",
    "price": 15.5,
    "image": "https://www.manollopizzaria.com.br/wp-content/uploads/2021/02/X_TUDO_DE_HAMBURGUER1-1.jpg"
  }
]

```

---

## POST `/orders`

Essa rota permite que você adicione um novo pedido no sistema.

Essa é uma rota autenticada.


#### Body da Requisição:
```json 
{
 "product_id":"0e46e76a-4401-4fd6-bbac-756674a16e9d", 
 "client_name": "João Pedro"
}
```

#### Headers da Requisição:
```json 
{
 "Authorization":"Bearer  eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InBlZHJvQGdtYWlsLmNvbSIsImlhdCI6MTY3NDE1MDcxOCwiZXhwIjoxNjc0MjM3MTE4fQ.MbIXE4qPHtXpszzBv4Eis3QXOkTqKCo0D-6WJliNOHc"
}
```


#### Retorno da requisição: 

```json
{
  "id": "eb9218bb-2aac-4795-9e0d-8419f024ed23",
  "createdAt": "2023-01-19T17:49:02.367Z",
  "updatedAt": "2023-01-19T17:49:02.367Z",
  "product_id": "0e46e76a-4401-4fd6-bbac-756674a16e9d",
  "number": "4",
  "status": "in production",
  "client_name": "João Pedro",
  "admin_email": "daniel.lopes@cubos.academy",
  "name": "X-Tudo",
  "image": "https://embutidosbonatti.ind.br/temp/xxx-57-980x550m0.jpg",
  "price": 28.5
}
```
---

## GET `/orders?userEmail=seuemail@email.com`

Essa rota devolve os produtos cadastrados no banco de dados.

É **importante** ressaltar que *seuemail@email.com* é onde você deve inserir o seu e-mail de uso pessoal, para que você possa ter identificação única no sistema.


#### Retorno da Requisição:
```json 
[
  {
    "id": "d4ecae00-f84a-4c00-88d3-d5619faaa93b",
    "createdAt": "2023-01-19T17:13:52.453Z",
    "updatedAt": "2023-01-19T17:13:52.453Z",
    "product_id": "0e46e76a-4401-4fd6-bbac-756674a16e9d",
    "number": "2",
    "status": "in production",
    "client_name": "Camila Mancini",
    "admin_email": "pedro@gmail.com",
    "name": "X-Tudo",
    "image": "https://embutidosbonatti.ind.br/temp/xxx-57-980x550m0.jpg",
    "price": 28.5
  }
]

```

---

## PUT `/orders/:order_id`

Essa rota permite que você adicione um novo pedido no sistema.

Essa é uma rota autenticada.


**order_id** = Id da order criada no post de orders


#### Body da Requisição:
```json 
{
    "status":"finish"
}
```

#### Headers da Requisição:
```json 
{
 "Authorization":"Bearer  eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InBlZHJvQGdtYWlsLmNvbSIsImlhdCI6MTY3NDE1MDcxOCwiZXhwIjoxNjc0MjM3MTE4fQ.MbIXE4qPHtXpszzBv4Eis3QXOkTqKCo0D-6WJliNOHc"
}
```

#### Retorno da requisição: 

```json
{
  "id": "ff3b6b95-b049-4465-a6d8-fb8c5b8191dc",
  "createdAt": "2023-01-19T17:52:25.275Z",
  "updatedAt": "2023-01-19T17:52:36.969Z",
  "product_id": "0e46e76a-4401-4fd6-bbac-756674a16e9d",
  "number": "5",
  "status": "finish",
  "client_name": "João Pedro",
  "admin_email": "pedro@gmail.com",
  "name": "X-Tudo",
  "image": "https://embutidosbonatti.ind.br/temp/xxx-57-980x550m0.jpg",
  "price": 28.5
}
```

# WebSocket

Essa api também dispõe de duas conexões com socket, para que as atualizações sejam fluidas no frontend. Essas conexões são:

- Quando atualizamos um pedido
    - Para isso ouviremos o emit em `orders-update-seuemail@email.com`
- Quando criamos um pedido
    - Para isso ouviremos o emit em `orders-seuemail@email.com`

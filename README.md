# Learning AdonisJS API Only

Repositório de estudo visando trabalhar com backend estruturado no framework AdonisJS.
Nesse estudo, foi iniciado um projeto com intuito de fazer um clone do Twitter, porém, possui apenas funcionalidades básicas, como autenticação JWT e CRUD de Tweets.

Tecnologias utilizadas

1. NodeJS
2. AdodisJS
3. MariaDB
4. Insomnia

## Setup

Antes de iniciar o projeto, é preciso instalar as dependencias do projeto após instalação via npm:
```bash
npm install
```
Agora, é preciso configurar nosso arquivo .ENV, localizado na raiz do projeto, para acessar seu banco de dados:

```.env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_password
DB_DATABASE=adonis
```
Em seu terminal, acesse MariaDB para criar seu banco de dados

```MariaDB Terminal
$mysql -u root -p

MariaDB> CREATE DATABASE adonis;
MariaDB> exit;

```
Com o banco de dados agora criado, estamos preparados para criar nossas tabelas e ver o funciomento do sistema

or manually clone the repo and then run `npm install`.


## Migrations

Para criar as tabelas no banco de dados, basta executar as migrations.

```js
adonis migration:run
```
## Iniciando servidor

Para iniciarmos os servidor, basta executar no terminal o comando abaixo:

```bash
adonis serve --dev
```
Pronto. Nossa aplicação já está funcionando.

##Testando as Rotas

No momento, essas são as rotas de funcionamento do sistema:

  Route         │ Verb(s)  │ Handler                     │ Middleware │ Name           │ Domain │
├───────────────┼──────────┼─────────────────────────────┼────────────┼────────────────┼────────┤
│ /register     │ POST     │ AuthController.register     │            │ /register      │        │
├───────────────┼──────────┼─────────────────────────────┼────────────┼────────────────┼────────┤
│ /authenticate │ POST     │ AuthController.authenticate │            │ /authenticate  │        │
├───────────────┼──────────┼─────────────────────────────┼────────────┼────────────────┼────────┤
│ /tweets       │ HEAD,GET │ TweetController.index       │ auth       │ tweets.index   │        │
├───────────────┼──────────┼─────────────────────────────┼────────────┼────────────────┼────────┤
│ /tweets       │ POST     │ TweetController.store       │ auth       │ tweets.store   │        │
├───────────────┼──────────┼─────────────────────────────┼────────────┼────────────────┼────────┤
│ /tweets/:id   │ HEAD,GET │ TweetController.show        │ auth       │ tweets.show    │        │
├───────────────┼──────────┼─────────────────────────────┼────────────┼────────────────┼────────┤
│ /tweets/:id   │ DELETE   │ TweetController.destroy     │ auth       │ tweets.destroy │       


Para testar o funcionamento das rotas, foi utilizado o Insomnia para cada método HTTP criado, mas pode ser usado qualquer outro software de sua preferência, como POSTMAN por exemplo.

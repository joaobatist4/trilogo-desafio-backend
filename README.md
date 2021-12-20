# Desafio Backend
⚠️ Este desafio tem o intuito de avaliar novos candidatos para possível contratação.

⚠️ O candidato deve enviar o desafio mesmo que não tenha finalizado, pois a tentativa também será avaliada;

⚠️ Deverá ser enviado o link do repositório no GitHub para que o código possa ser baixado para avaliação;

⚠️ Colocar as instruções no arquivo README.md de como deve ser preparado o ambiente para testar a aplicação;

## Descrição

A TriMania é uma loja que atua somente nas redes sociais mas que agora está avançando para a criação de um novo site de vendas. Para isso, seus desenvolvedores frontend precisam de uma api para realizar as seguintes ações: 
 - [x] ***Cadastros de usuário***
 - [x] ***Venda de produtos***
 - [x] ***Relatório de vendas***
 
 Onde:
 
 ### Cadastro de Usuários (User)
 
 Funcionalidade responsável por consultar, cadastrar, editar e excluir usuários da plataforma de vendas. As informações que devem compor o cadastro de usuário são:
 ```
{
  "id":"int"¹,
  "name":"string"¹,
  "login":"string"¹,
  "password":"string"¹,
  "cpf":"string"¹,
  "email":"string"¹,
  "birthday":"datetime",
  "creation_date":"datetime"¹,
  "address":{
    "street":"string",
    "neighborhood":"string",
    "number":"string",
    "city":"string",
    "state":"string"
  }
}
 ```
 * Deve ser possível pesquisar pelo usuário utilizando um filtro por termo, onde poderá ser filtrado pelos seu nome, email e login. 
 * A listagem de Usuários deve ser paginada com 10 elementos por página.
 * ⚠️ O usuário não poderá ser excluído se houver pedidos (Order) cadastrados para ele.
 * ⚠️ A senha do usuário não deve ser armazenada em texto plano.
  

### Venda de produtos/Pedido (Order)

Está é a funcionalidade principal da API, onde será necessário desenvolver um carrinho de compras para que seja possível realizar a venda de produtos.
Devem ser seguidas as seguintes regras:

* Um pedido poderá ter um ou mais produtos (itens);
* Um pedido só pode pertencer a um único cliente (usuário);
* Um cliente poderá ter mais de um pedido cadastrado (order);
* Um cliente só pode fazer um pedido por vez. Se o cliente começar um pedido, ele deve finalizar ou cancelar o pedido que já está em andamento;
* Deverá ter as seguintes formas de pagamento: 'cartão de crédito', 'à vista' ou 'boleto';
* Um pedido deverá ter o status *Aberto*, *Em andamento*, *Cancelado* e *Concluído*;
* O valor do item do pedido deve ser o somatório dos produtos;
* Não será possível vender produtos sem estoque disponível;

A estrutura do produto deverá ser a seguinte:
```

{
 "id"¹:"int",
 "name":"string",
 "description":"string",
 "quantity":"int",
 "price":""decimal"
}

```

A estrutura do pedido deve ser o seguinte:
```
{
  "id"¹:"int",
  "user"¹:<user_object>,
  "total_value"¹:"decimal",
  "items"¹:[
    {
      "product_id":"int"
      "price":"decimal"
      "quantity":"int",
    }
  ],
  "creation_date"¹:"datetime",
  "cancel_date":"datetime",
  "status"¹:"enumerator",
  "finished_date":"datetime"
}
```
### Relatório de Vendas
Essa funcionalidade deverá retornar informações para que seja montado um relatório de vendas para a loja.
Devem ser seguidas as seguintes regras:
* Deverão haver os seguintes filtros:
 *    Período de vendas (Data de Início e Data de Fim) ¹
 *    Status (um ou mais status ao mesmo tempo)
 *    Usuario (um ou mais usuários)

Devera conter a seguinte estrutura

```
{
  "finished_orders_amount"¹:"int",
  "cancelled_orders_amount"¹:"int",
  "orders_total_value"¹:"decimal",
  "orders"¹:<order_object>
}
```

## Técnica

Para o desenvolvimento da API, a parte técnica deverá seguir as seguintes regras:
* Deverá ser utilizado ASP.NET Core 3.1 ou superior;
* Deverá ser utilizado Entity Framework Core 3.1 ou superior;
* Utilizar o banco de dados MySql (deverá ser enviado o script de criação do banco de dados para avaliação e testes. Pode incluí-lo no repositório.);
* A API deverá conter autenticação de usuário;
* Implementação de testes unitários;

Desejável (Opcional):
* Deverá seguir o conceito de Arquitetura Limpa (https://docs.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures);
* Seguir os princípios do SOLID;

Diferenciais (Opcional):
* Implementação usando MediatR (Padrão mediator - https://github.com/jbogard/MediatR);
* Implementação de testes automatizados;
* Implementação no padrão arquitetural CQRS (Command-Query Responsability Segregation);
* Utilizar Entity Framework Core 3.1 ou superior para a escrita dos dados e Dapper para a consulta dos dados;

 ###### _____________________________________________________________________________________________________________________________________
 ###### ¹ Informações obrigatórias
 ###### ² Apenas os nomes dos usuários

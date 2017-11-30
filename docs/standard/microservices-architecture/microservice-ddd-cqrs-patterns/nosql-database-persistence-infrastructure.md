---
title: "Bancos de dados NoSQL como uma infraestrutura de persistência"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Bancos de dados NoSQL como uma infraestrutura de persistência"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e4b63511069b89cc5761ce7ed64f09e9035a56a3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a>Bancos de dados NoSQL como uma infraestrutura de persistência

Ao usar bancos de dados NoSQL para sua camada de dados de infra-estrutura, você normalmente não usa um ORM como Entity Framework Core. Em vez disso, você pode usar a API fornecida pelo mecanismo de NoSQL, como o banco de dados do Azure Cosmos, MongoDB, Cassandra, RavenDB, CouchDB ou tabelas de armazenamento do Azure.

No entanto, quando você usa um banco de dados NoSQL, especialmente um documento de banco de dados orientado como banco de dados do Azure Cosmos, CouchDB ou RavenDB, a maneira que você cria seu modelo com agregações DDD é parcialmente semelhante a como você pode fazer isso no núcleo do EF, no que diz respeito à identificação de raízes agregadas, classes de entidade filho e classes de objeto de valor. Mas, por fim, a seleção de banco de dados causará impacto em seu design.

Quando você usa um banco de dados orientado por documentos, você implementa uma agregação como um único documento serializado em JSON ou outro formato. No entanto, o uso do banco de dados é transparente de um ponto de vista do domínio modelo código. Ao usar um banco de dados NoSQL, você ainda estiver usando classes de entidade e agregação de raiz, mas a persistência com maior flexibilidade do que quando usando EF Core porque não é relacional.

A diferença é como manter o modelo. Se você tiver implementado o modelo de domínio com base em classes de entidade POCO, desconhecido para a persistência de infraestrutura, pode parecer que você podia se mover para uma infraestrutura de persistência diferente, até mesmo de relacional para NoSQL. No entanto, que não deve ser o seu objetivo. Sempre há restrições em diferentes bancos de dados fará com que você, e você não poderá ter o mesmo modelo para relacionais ou bancos de dados NoSQL. Alterar os modelos de persistência não seria trivial, como transações e operações de persistência serão muito diferentes.

Por exemplo, em um banco de dados orientado por documentos, é okey para uma raiz de agregação ter diversas propriedades de coleção filho. Em um banco de dados relacional, consultar várias propriedades de coleção filho é terrível, como voltar uma instrução SQL de todas as união de EF. Ter o mesmo modelo de domínio para bancos de dados relacionais ou bancos de dados NoSQL não é simple e não deverá usá-lo. Você realmente precisa criar seu modelo com uma compreensão de como os dados será a ser usado em cada banco de dados específico.

Um benefício ao usar bancos de dados NoSQL é que as entidades são mais desnormalizadas, portanto, você não definir um mapeamento de tabela. O modelo de domínio pode ser mais flexível do que ao usar um banco de dados relacional.

Quando você criar seu modelo de domínio com base em agregações, movendo para NoSQL e bancos de dados orientado por documentos podem ser ainda mais fácil do que usar um banco de dados relacional, porque as agregações que você cria são semelhantes às serializado documentos em um banco de dados orientado por documentos. Em seguida, você pode incluir nesses pacotes"" todas as informações que talvez seja necessário para essa agregação.

Por exemplo, o código a seguir JSON é um exemplo da implementação de uma agregação de ordem ao usar um banco de dados orientado por documentos. É semelhante à ordem de agregação que são implementados no exemplo eShopOnContainers, mas sem usar Core EF abaixo.

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

Quando você usa um C\# modelo para implementar a agregação a ser usado por algo parecido com o SDK do Azure Cosmos banco de dados, a agregação é semelhante do C\# POCO classes usadas com EF Core. A diferença é a maneira de usá-los das camadas de aplicativo e a infraestrutura, como no código a seguir:

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH DOCUMENTDB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).
// This can be saved as JSON as is without converting into rows/columns.
Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);
OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

OrderItem orderItem2 = new OrderItem
{
    Id = 20170012,
    ProductId = "123457",
    ProductName = ".NET Mug",
    UnitPrice = 15,
    Units = 1,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
orderAggregate.AddOrderItem(orderItem2);

// *** End of Domain Model Code ***
//...
// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, order);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

Você pode ver que a maneira de trabalhar com o modelo de domínio pode ser semelhante à forma como você usá-lo em sua camada de modelo de domínio quando a infraestrutura é EF. Você ainda pode usar os mesmos métodos de agregação raiz para garantir a consistência, constantes e validações dentro do agregado.

No entanto, quando você mantiver o modelo para o banco de dados NoSQL, o código e alteração de API drasticamente em comparação com o código EF principal ou qualquer outro código relacionadas a bancos de dados relacionais.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Modelagem de dados em documentos**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)

-   **Vaughn Vernon. O Ideal controlado por domínio Design de agregação repositório? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **Um independente de persistência repositório de eventos para .NET.** Repositório do GitHub.
    [*https://GitHub.com/NEventStore/NEventStore*](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
[Anterior] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Avançar] (microservice-application-layer-web-api-design.md)

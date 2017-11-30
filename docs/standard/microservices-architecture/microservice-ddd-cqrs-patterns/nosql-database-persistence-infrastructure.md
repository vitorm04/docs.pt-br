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
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="595b3-104">Bancos de dados NoSQL como uma infraestrutura de persistência</span><span class="sxs-lookup"><span data-stu-id="595b3-104">Using NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="595b3-105">Ao usar bancos de dados NoSQL para sua camada de dados de infra-estrutura, você normalmente não usa um ORM como Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="595b3-105">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="595b3-106">Em vez disso, você pode usar a API fornecida pelo mecanismo de NoSQL, como o banco de dados do Azure Cosmos, MongoDB, Cassandra, RavenDB, CouchDB ou tabelas de armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="595b3-106">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="595b3-107">No entanto, quando você usa um banco de dados NoSQL, especialmente um documento de banco de dados orientado como banco de dados do Azure Cosmos, CouchDB ou RavenDB, a maneira que você cria seu modelo com agregações DDD é parcialmente semelhante a como você pode fazer isso no núcleo do EF, no que diz respeito à identificação de raízes agregadas, classes de entidade filho e classes de objeto de valor.</span><span class="sxs-lookup"><span data-stu-id="595b3-107">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="595b3-108">Mas, por fim, a seleção de banco de dados causará impacto em seu design.</span><span class="sxs-lookup"><span data-stu-id="595b3-108">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="595b3-109">Quando você usa um banco de dados orientado por documentos, você implementa uma agregação como um único documento serializado em JSON ou outro formato.</span><span class="sxs-lookup"><span data-stu-id="595b3-109">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="595b3-110">No entanto, o uso do banco de dados é transparente de um ponto de vista do domínio modelo código.</span><span class="sxs-lookup"><span data-stu-id="595b3-110">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="595b3-111">Ao usar um banco de dados NoSQL, você ainda estiver usando classes de entidade e agregação de raiz, mas a persistência com maior flexibilidade do que quando usando EF Core porque não é relacional.</span><span class="sxs-lookup"><span data-stu-id="595b3-111">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="595b3-112">A diferença é como manter o modelo.</span><span class="sxs-lookup"><span data-stu-id="595b3-112">The difference is in how you persist that model.</span></span> <span data-ttu-id="595b3-113">Se você tiver implementado o modelo de domínio com base em classes de entidade POCO, desconhecido para a persistência de infraestrutura, pode parecer que você podia se mover para uma infraestrutura de persistência diferente, até mesmo de relacional para NoSQL.</span><span class="sxs-lookup"><span data-stu-id="595b3-113">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="595b3-114">No entanto, que não deve ser o seu objetivo.</span><span class="sxs-lookup"><span data-stu-id="595b3-114">However, that should not be your goal.</span></span> <span data-ttu-id="595b3-115">Sempre há restrições em diferentes bancos de dados fará com que você, e você não poderá ter o mesmo modelo para relacionais ou bancos de dados NoSQL.</span><span class="sxs-lookup"><span data-stu-id="595b3-115">There are always constraints in the different databases will push you back, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="595b3-116">Alterar os modelos de persistência não seria trivial, como transações e operações de persistência serão muito diferentes.</span><span class="sxs-lookup"><span data-stu-id="595b3-116">Changing persistence models would not be trivial, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="595b3-117">Por exemplo, em um banco de dados orientado por documentos, é okey para uma raiz de agregação ter diversas propriedades de coleção filho.</span><span class="sxs-lookup"><span data-stu-id="595b3-117">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="595b3-118">Em um banco de dados relacional, consultar várias propriedades de coleção filho é terrível, como voltar uma instrução SQL de todas as união de EF.</span><span class="sxs-lookup"><span data-stu-id="595b3-118">In a relational database, querying multiple child collection properties is awful, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="595b3-119">Ter o mesmo modelo de domínio para bancos de dados relacionais ou bancos de dados NoSQL não é simple e não deverá usá-lo.</span><span class="sxs-lookup"><span data-stu-id="595b3-119">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try it.</span></span> <span data-ttu-id="595b3-120">Você realmente precisa criar seu modelo com uma compreensão de como os dados será a ser usado em cada banco de dados específico.</span><span class="sxs-lookup"><span data-stu-id="595b3-120">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="595b3-121">Um benefício ao usar bancos de dados NoSQL é que as entidades são mais desnormalizadas, portanto, você não definir um mapeamento de tabela.</span><span class="sxs-lookup"><span data-stu-id="595b3-121">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="595b3-122">O modelo de domínio pode ser mais flexível do que ao usar um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="595b3-122">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="595b3-123">Quando você criar seu modelo de domínio com base em agregações, movendo para NoSQL e bancos de dados orientado por documentos podem ser ainda mais fácil do que usar um banco de dados relacional, porque as agregações que você cria são semelhantes às serializado documentos em um banco de dados orientado por documentos.</span><span class="sxs-lookup"><span data-stu-id="595b3-123">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="595b3-124">Em seguida, você pode incluir nesses pacotes"" todas as informações que talvez seja necessário para essa agregação.</span><span class="sxs-lookup"><span data-stu-id="595b3-124">Then you can include in those “bags” all the information you might need for that aggregate.</span></span>

<span data-ttu-id="595b3-125">Por exemplo, o código a seguir JSON é um exemplo da implementação de uma agregação de ordem ao usar um banco de dados orientado por documentos.</span><span class="sxs-lookup"><span data-stu-id="595b3-125">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="595b3-126">É semelhante à ordem de agregação que são implementados no exemplo eShopOnContainers, mas sem usar Core EF abaixo.</span><span class="sxs-lookup"><span data-stu-id="595b3-126">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

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

<span data-ttu-id="595b3-127">Quando você usa um C\# modelo para implementar a agregação a ser usado por algo parecido com o SDK do Azure Cosmos banco de dados, a agregação é semelhante do C\# POCO classes usadas com EF Core.</span><span class="sxs-lookup"><span data-stu-id="595b3-127">When you use a C\# model to implement the aggregate to be used by something like the Azure Cosmos DB SDK, the aggregate is similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="595b3-128">A diferença é a maneira de usá-los das camadas de aplicativo e a infraestrutura, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="595b3-128">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

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

<span data-ttu-id="595b3-129">Você pode ver que a maneira de trabalhar com o modelo de domínio pode ser semelhante à forma como você usá-lo em sua camada de modelo de domínio quando a infraestrutura é EF.</span><span class="sxs-lookup"><span data-stu-id="595b3-129">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="595b3-130">Você ainda pode usar os mesmos métodos de agregação raiz para garantir a consistência, constantes e validações dentro do agregado.</span><span class="sxs-lookup"><span data-stu-id="595b3-130">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="595b3-131">No entanto, quando você mantiver o modelo para o banco de dados NoSQL, o código e alteração de API drasticamente em comparação com o código EF principal ou qualquer outro código relacionadas a bancos de dados relacionais.</span><span class="sxs-lookup"><span data-stu-id="595b3-131">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="595b3-132">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="595b3-132">Additional resources</span></span>

-   <span data-ttu-id="595b3-133">**Modelagem de dados em documentos**
    [*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span><span class="sxs-lookup"><span data-stu-id="595b3-133">**Modeling data in DocumentDB**
[*https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data*](https://docs.microsoft.com/azure/documentdb/documentdb-modeling-data)</span></span>

-   <span data-ttu-id="595b3-134">**Vaughn Vernon. O Ideal controlado por domínio Design de agregação repositório? ** 
     [ *https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span><span class="sxs-lookup"><span data-stu-id="595b3-134">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**
[*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)</span></span>

-   <span data-ttu-id="595b3-135">**Um independente de persistência repositório de eventos para .NET.**</span><span class="sxs-lookup"><span data-stu-id="595b3-135">**A persistence agnostic Event Store for .NET.**</span></span> <span data-ttu-id="595b3-136">Repositório do GitHub.</span><span class="sxs-lookup"><span data-stu-id="595b3-136">GitHub repo.</span></span>
    [<span data-ttu-id="595b3-137">*https://GitHub.com/NEventStore/NEventStore*</span><span class="sxs-lookup"><span data-stu-id="595b3-137">*https://github.com/NEventStore/NEventStore*</span></span>](https://github.com/NEventStore/NEventStore)


>[!div class="step-by-step"]
<span data-ttu-id="595b3-138">[Anterior] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Avançar] (microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="595b3-138">[Previous] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Next] (microservice-application-layer-web-api-design.md)</span></span>

---
title: Usando bancos de dados NoSQL como uma infraestrutura de persistência
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Usando bancos de dados NoSQL como uma infraestrutura de persistência
keywords: Docker, Microsserviços, ASP.NET, Contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a6f3a991529aea6560eb12f1400ba2750795ebff
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/10/2018
---
# <a name="using-nosql-databases-as-a-persistence-infrastructure"></a>Usando bancos de dados NoSQL como uma infraestrutura de persistência

Ao usar bancos de dados NoSQL para a camada de dados da infraestrutura, normalmente, não se usa um ORM (mapeamento objeto-relacional) como o Entity Framework Core. Nesse caso, é possível usar a API fornecida pelo mecanismo NoSQL, como o Azure Cosmos DB, o MongoDB, o Cassandra, o RavenDB, o CouchDB ou as tabelas de Armazenamento do Azure.

No entanto, ao usar um banco de dados NoSQL, principalmente um banco de dados orientado a documentos como o Azure Cosmos DB, o CouchDB ou o RavenDB, a maneira de criar o modelo com agregações de DDD é parcialmente semelhante à maneira de fazer isso no EF Core, em relação à identificação de raízes agregadas, classes de entidade filha e classes de objeto de valor. Mas, por fim, a seleção do banco de dados realmente afetará o design.

Ao usar um banco de dados orientado a documentos, você implementa uma agregação como um único documento serializado em JSON ou em outro formato. No entanto, o uso do banco de dados é transparente do ponto de vista do código do modelo de domínio. Ao usar um banco de dados NoSQL, você ainda está usando classes de entidade e classes de raiz de agregação, mas com maior flexibilidade do que ao usar o EF Core porque a persistência não é relacional.

A diferença está em como persistir esse modelo. Se você implementar o modelo de domínio com base em classes de entidade POCO (objeto CRL básico), independentemente da persistência da infraestrutura, poderá parecer que é possível passar para uma infraestrutura de persistência diferente, até mesmo de relacional para NoSQL. No entanto, essa não deve ser a sua meta. Sempre há restrições em bancos de dados diferentes que o farão retroceder, portanto, não é possível usar o mesmo modelo para bancos de dados relacionais ou NoSQL. Alterar os modelos de persistência não seria tão fácil, pois as transações e as operações de persistência são muito diferentes.

Por exemplo, em um banco de dados orientado a documentos, é possível que uma raiz de agregação tenha diversas propriedades de coleção filhas. Em um banco de dados relacional, consultar várias propriedades de coleção filhas é impossível, pois o EF retorna uma instrução UNION ALL SQL. Ter o mesmo modelo de domínio para bancos de dados relacionais ou bancos de dados NoSQL não é simples e não é recomendado. Você realmente precisa criar seu modelo com uma compreensão de como os dados serão usados em cada banco de dados específico.

Um benefício de usar bancos de dados NoSQL é que as entidades são mais desnormalizadas, portanto, você não precisa definir um mapeamento de tabela. O modelo de domínio pode ser mais flexível do que ao usar um banco de dados relacional.

Ao criar o modelo de domínio baseado em agregações, passar para bancos de dados NoSQL e orientados a documentos pode ser ainda mais fácil do que usar um banco de dados relacional, porque as agregações criadas são semelhantes aos documentos serializados em um banco de dados orientado a documentos. Em seguida, é possível incluir nesses “pacotes” todas as informações que possam ser necessárias para essa agregação.

Por exemplo, o código JSON a seguir é um exemplo da implementação de uma agregação de pedido ao usar um banco de dados orientado a documentos. Ele é semelhante à agregação de pedido que foi implementada no exemplo eShopOnContainers, mas sem usar o Core EF.

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

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a>Introdução ao Azure Cosmos DB e à API nativa do Cosmos DB

O [Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/introduction) é o serviço de banco de dados distribuído globalmente da Microsoft para aplicativos críticos. O Azure Cosmos DB fornece [distribuição global turnkey](https://docs.microsoft.com/en-us/azure/cosmos-db/distribute-data-globally), [dimensionamento elástico de produtividade e armazenamento](https://docs.microsoft.com/en-us/azure/cosmos-db/partition-data) no mundo todo, latências de milissegundo no 99º percentil, [cinco níveis de consistência bem definidos](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels) e a garantia de alta disponibilidade, apoiado por [SLAs líderes no setor](https://azure.microsoft.com/support/legal/sla/cosmos-db/). O Azure Cosmos DB [indexa os dados automaticamente](http://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) sem a necessidade de lidar com o gerenciamento de esquema e de índice. Ele permite vários modelos e é compatível com modelos de dados de documento, de chave-valor, gráficos e colunares.

![](./media/image19.1.png) Figura 9-19. Distribuição global do Azure Cosmos DB

Ao usar um modelo C\# para implementar a agregação a ser usada pela API do Azure Cosmos DB, a agregação pode ser semelhante à das classes POCO do C\# usadas com o EF Core. A diferença está na maneira de usá-las nas camadas de aplicativo e de infraestrutura, como no código a seguir:

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot’s methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

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

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
orderAggregate.AddOrderItem(orderItem2);
// *** End of Domain Model Code ***

// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

Você pode ver que a maneira de trabalhar com o modelo de domínio pode ser semelhante à maneira de usá-lo na camada do modelo de domínio quando a infraestrutura é o EF. Você ainda pode usar os mesmos métodos de raiz de agregação para garantir a consistência, as invariáveis e as validações na agregação.

No entanto, ao persistir o modelo para o banco de dados NoSQL, o código e a API serão radicalmente alterados em comparação com o código do EF Core ou com qualquer outro código relacionado a bancos de dados relacionais.

## <a name="implementing-net-code-targeting-mongodb-and-azure-cosmos-db"></a>Implementando o código do .NET direcionado ao MongoDB e ao Azure Cosmos DB

### <a name="using-azure-cosmos-db-from-net-containers"></a>Usando o Azure Cosmos DB de contêineres do .NET

Você pode acessar os bancos de dados Azure Cosmos DB do código do .NET em execução em contêineres, como de qualquer outro aplicativo .NET. Por exemplo, os microsserviços Locations.API e Marketing.API no eShopOnContainers são implementados para que possam consumir bancos de dados Azure Cosmos DB.

No entanto, há uma limitação no Azure Cosmos DB do ponto de vista do ambiente de desenvolvimento do Docker. Mesmo quando há um [emulador do Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator) local capaz de ser executado em um computador de desenvolvimento local (como um PC), no final de 2017, ele passou a ser compatível apenas com o Windows, não com o Linux. 

Também existe a possibilidade de executar este emulador no Docker, mas apenas em contêineres do Windows, não em contêineres do Linux. Essa será uma limitação inicial do ambiente de desenvolvimento se seu aplicativo for implantado como contêineres do Linux, já que, no momento, não é possível implantar contêineres do Linux e do Windows no Docker para Windows ao mesmo tempo. Todos os contêineres que estão sendo implantados precisam ser do Linux ou do Windows.  

O modo de implantação mais simples e ideal para uma solução de Desenvolvimento/Teste é poder implantar os sistemas de banco de dados como contêineres juntamente com contêineres personalizados para que os ambientes de Desenvolvimento/Teste estejam sempre consistentes.

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a>Usar a API do MongoDB para contêineres locais do Linux/Windows de Desenvolvimento/Teste além do Azure Cosmos DB

Os bancos de dados Cosmos DB são compatíveis com a API do MongoDB para .NET, e com o protocolo de transmissão nativo do MongoDB. Isso significa que, usando os drivers existentes, o aplicativo escrito para o MongoDB agora pode se comunicar com o Cosmos DB e usar os bancos de dados do Cosmos DB em vez dos bancos de dados do MongoDB, conforme é mostrado na Figura 9-20.

![](./media/image19.2.png) Figura 9-20. Usando a API e o protocolo do MongoDB para acessar o Azure Cosmos DB

Essa é uma abordagem muito conveniente para prova de conceitos em ambientes do Docker com contêineres do Linux, porque a [imagem do Docker do MongoDB](https://hub.docker.com/r/_/mongo/) é uma imagem para várias arquiteturas, compatível com contêineres do Linux do Docker e do Windows do Docker.

Conforme é mostrado na imagem a 9-21, usando a API do MongoDB, o eShopOnContainers permite contêineres do Windows e do Linux do MongoDB para o ambiente de desenvolvimento local, mas também é possível passar para uma solução de nuvem de PaaS escalonável, como o Azure Cosmos DB, simplesmente [alterando a cadeia de conexão do MongoDB para apontar para o Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account). 

![](./media/image20-bis.png) Figura 9-21. eShopOnContainers usando contêineres do MongoDB para o ambiente de desenvolvimento ou para o Azure Cosmos DB para produção

O Azure Cosmos DB de produção estaria em execução na nuvem do Azure como um serviço escalonável e de PaaS.

Os contêineres do .NET Core personalizados podem ser executados em um host do Docker de desenvolvimento local (que esteja usando o Docker para Windows em um computador Windows 10) ou ser implantados em um ambiente de produção, como o Kubernetes no AKS do Azure ou no Azure Service Fabric. Nesse segundo ambiente, você implantaria somente os contêineres personalizados do .NET Core, mas não o contêiner do MongoDB, pois você estaria usando o Azure Cosmos DB na nuvem para lidar com os dados de produção.

Um benefício claro de usar a API do MongoDB é que a solução pode ser executada em ambos os mecanismos de banco de dados, MongoDB ou Azure Cosmos DB, facilitando as migrações para diferentes ambientes. No entanto, às vezes, vale a pena usar uma API nativa (ou seja, a API nativa do Cosmos DB) para aproveitar ao máximo os recursos de um mecanismo de banco de dados específico.

Para obter mais comparações entre o simples uso do MongoDB ou do Cosmos DB na nuvem, consulte [Benefícios de usar o Azure Cosmos DB, nesta página](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction). 


### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a>Analisar sua abordagem para aplicativos de produção: API do MongoDB em relação à API do Cosmos DB

No eShopOnContainers, estamos usando a API do MongoDB porque nossa prioridade era basicamente ter um ambiente de Desenvolvimento/Teste consistente usando um banco de dados NoSQL que também pudesse funcionar com o Azure Cosmos DB.

No entanto, se você planeja usar a API do MongoDB para acessar o Azure Cosmos DB no Azure para aplicativos de produção, analise as diferenças de recursos e de desempenho ao usar a API do MongoDB para acessar bancos de dados Azure Cosmos DB em comparação com o uso da API nativa do Azure Cosmos DB. Se for semelhante, você poderá usar a API do MongoDB e obter o benefício de permitir dois mecanismos de banco de dados NoSQL ao mesmo tempo. 

Você também pode usar clusters do MongoDB como o banco de dados de produção na nuvem do Azure, com o [Serviço do Azure para MongoDB](https://www.mongodb.com/scale/mongodb-azure-service). Mas esse não é um serviço de PaaS fornecido pela Microsoft. Nesse caso, o Azure está apenas hospedando essa solução proveniente do MongoDB.

Basicamente, isso é apenas um aviso de isenção de responsabilidade informando que você não deve usar sempre a API do MongoDB no Azure Cosmos DB, como fizemos no eShopOnContainers, porque essa foi uma opção conveniente para contêineres do Linux. A decisão deve ser baseada as necessidades específicas e nos testes que você precisa fazer para o aplicativo de produção.  

### <a name="the-code-using-mongodb-api-in-net-core-applications"></a>O código: usando a API do MongoDB em aplicativos .NET Core

A API do MongoDB para .NET baseia-se em pacotes NuGet que você precisa adicionar nos projetos, como o Locations.API mostrado na Figura 9-22.

![](./media/image21-bis.png) Figura 9-22. Referências de pacotes NuGet da API do MongoDB em um projeto do .NET Core

Vamos examinar o código nas seções a seguir.

#### <a name="a-model-used-by-mongodb-api"></a>Um modelo usado pela API do MongoDB

Primeiro, você precisa definir um modelo que armazenará os dados provenientes do banco de dados no espaço de memória do aplicativo. Aqui está um exemplo do modelo usado para Locais no eShopOnContainers.

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location 
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon 
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList) 
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

Você pode ver que há alguns atributos e tipos provenientes dos pacotes NuGet do MongoDB.

Os bancos de dados NoSQL normalmente são muito bem adequados para trabalhar com os dados hierárquicos não relacionais. Neste exemplo, estamos usando tipos do MongoDB criados especificamente para localizações geográficas, como `GeoJson2DGeographicCoordinates`.

#### <a name="retrieve-the-database-and-the-collection"></a>Recuperar o banco de dados e a coleção

No eShopOnContainers, criamos um contexto de banco de dados personalizado no qual podemos implementar o código para recuperar o banco de dados e as MongoCollections, como no código a seguir.

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }       
}
```

#### <a name="retrieve-the-data"></a>Recuperar os dados

No código C#, como nos controladores de API Web ou na implementação personalizada de repositórios, você pode escrever um código semelhante ao seguinte ao consultar por meio da API do MongoDB. Observe que o objeto `_context` é uma instância da classe `LocationsContext` anterior.

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a>Use uma variável de ambiente no arquivo docker-compose.override.yml para a cadeia de conexão do MongoDB

Ao criar um objeto do MongoClient, ele precisa de um parâmetro fundamental, que é exatamente o parâmetro `ConnectionString`, apontando para o banco de dados certo. No caso do eShopOnContainers, a cadeia de conexão pode apontar para um contêiner do Docker do MongoDB local ou para um banco de dados Azure Cosmos DB de "produção".  Essa cadeia de conexão vem de variáveis de ambiente definidas em arquivos `docker-compose.override.yml` usados ao implantar com o docker-compose ou o Visual Studio, como no código yml a seguir.

```yml
# docker-compose.override.yml
version: '3'
services:
  # Other services
  locations.api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}

```

A variável de ambiente `ConnectionString` é resolvida desta forma: se a variável global `ESHOP_AZURE_COSMOSDB` estiver definida no arquivo `.env` com a cadeia de conexão do Azure Cosmos DB, ela o usará para acessar o banco de dados Azure Cosmos DB na nuvem. 

O código a seguir mostra o arquivo `.env` com a variável de ambiente global da cadeia de conexão do Azure Cosmos DB, conforme implementado no eShopOnContainers:

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

Você deve remover o comentário da linha ESHOP_AZURE_COSMOSDB e atualizá-la com a cadeia de conexão do Azure Cosmos DB obtida no Portal do Azure, como explicado em [Conectar um aplicativo do MongoDB ao Azure Cosmos DB](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account).

Se a variável global `ESHOP_AZURE_COSMOSDB` estiver vazia, ou seja, estiver comentada no arquivo `.env`, o contêiner usará uma cadeia de conexão padrão do MongoDB apontando para o contêiner local do MongoDB implantado no eShopOnContainers, chamado de `nosql.data`, conforme é mostrado no código .yml a seguir. 

#### <a name="additional-resources"></a>Recursos adicionais

-   **Modelagem de dados de documento para bancos de dados NoSQL**
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data*](https://docs.microsoft.com/en-us/azure/cosmos-db/modeling-data)

-   **Vaughn Vernon. O repositório de agregação de design orientado por domínio ideal?**
    [*https://vaughnvernon.co/?p=942*](https://vaughnvernon.co/?p=942)

-   **Introdução ao Azure Cosmos DB: API para o MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-introduction)

-   **Azure Cosmos DB: criar um aplicativo Web da API MongoDB com o .NET e o Portal do Azure** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet *](https://docs.microsoft.com/en-us/azure/cosmos-db/create-mongodb-dotnet )

-   **Usar o emulador do Azure Cosmos DB para desenvolvimento e teste local** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator*](https://docs.microsoft.com/en-us/azure/cosmos-db/local-emulator)

-   **Conectar um aplicativo do MongoDB ao Azure Cosmos DB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account*](https://docs.microsoft.com/en-us/azure/cosmos-db/connect-mongodb-account)

-   **A imagem do Docker do emulador do Cosmos DB (contêiner do Windows)** 
    [*https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/*](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/)

-   **A imagem do Docker do MongoDB (contêiner do Linux e do Windows)** 
    [*https://hub.docker.com/r/_/mongo/*](https://hub.docker.com/r/_/mongo/)

-   **Usar o MongoChef (Studio 3T) com um Azure Cosmos DB: API de conta do MongoDB** 
    [*https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef*](https://docs.microsoft.com/en-us/azure/cosmos-db/mongodb-mongochef)


>[!div class="step-by-step"]
[Anterior] (infrastructure-persistence-layer-implemenation-entity-framework-core.md) [Próximo] (microservice-application-layer-web-api-design.md)

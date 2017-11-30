---
title: "Implementando conexões Entity Framework Core SQL"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementando conexões Entity Framework Core SQL"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 8600625c2022d69ebaa2645c2a8159a848b12ff0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a>Implementando conexões Entity Framework Core SQL

Para o Azure SQL DB, Entity Framework Core já fornece lógica de resiliência e repetição de conexão de banco de dados interno. Mas você precisa habilitar a estratégia de execução de Entity Framework para cada conexão DbContext, se você quiser ter [conexões EF Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).

Por exemplo, o código a seguir no nível de conexão do EF Core permite conexões de SQL que são repetidas se a conexão falhar.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 5,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Estratégias de execução e transações explícitas usando BeginTransaction e vários DbContexts

Quando novas tentativas são habilitadas em conexões EF Core, cada operação que você executar usando EF principal se torna sua própria operação repetível. Cada chamada para SaveChanges e cada consulta serão repetidas como uma unidade se ocorrer uma falha temporária.

No entanto, se seu código inicia uma transação usando BeginTransaction, você está definindo seu próprio grupo de operações que precisam ser tratados como uma unidade — tudo dentro da transação ser revertida se ocorrer uma falha. Se você tentar executar a transação ao usar uma estratégia de execução EF (política de repetição) e incluir várias chamadas SaveChanges de vários DbContexts na transação, você verá uma exceção semelhante ao seguinte.

> System. InvalidOperationException: A estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não oferece suporte a transações iniciadas pelo usuário. Use a estratégia de execução retornada por 'DbContext.Database.CreateExecutionStrategy()' para executar todas as operações na transação como uma unidade repetível.

A solução é chamar a estratégia de execução EF manualmente com um delegado que representa tudo o que precisa ser executada. Se ocorrer uma falha transitória, a estratégia de execução invocará o representante novamente. Por exemplo, o código a seguir mostram como é implementado em eShopOnContainers com dois DbContexts vários (\_catalogContext e o IntegrationEventLogContext) ao atualizar um produto e, em seguida, salvar o Objeto ProductPriceChangedIntegrationEvent, que precisa usar um DbContext diferente.

```csharp
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem
    productToUpdate)
{
    // Other code ...
    // Update current product
    catalogItem = productToUpdate;

    // Use of an EF Core resiliency strategy when using multiple DbContexts
    // within an explicit transaction
    // See:
    // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
    var strategy = _catalogContext.Database.CreateExecutionStrategy();
    await strategy.ExecuteAsync(async () =>
    {
        // Achieving atomicity between original Catalog database operation and the
        // IntegrationEventLog thanks to a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
            _catalogContext.CatalogItems.Update(catalogItem);
            await _catalogContext.SaveChangesAsync();
            // Save to EventLog only if product price changed
            if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
            transaction.Commit();
        }
    });
}
```

É o primeiro DbContext \_catalogContext e o segundo DbContext está dentro do \_integrationEventLogService objeto. A ação de confirmação é executada em vários DbContexts usando uma estratégia de execução EF.

## <a name="additional-resources"></a>Recursos adicionais

-   **Resiliência de Conexão e interceptação de comando com o Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesar de la Torre. Usando transações e conexões do Sql resiliente Entity Framework Core**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>


>[!div class="step-by-step"]
[Anterior] (implementar-tentativas-exponencial-backoff.md) [Avançar] (implement-custom-http-call-retries-exponential-backoff.md)

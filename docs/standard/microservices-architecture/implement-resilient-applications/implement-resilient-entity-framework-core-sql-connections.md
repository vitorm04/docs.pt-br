---
title: Implementar conexões SQL resilientes com o Entity Framework Core
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Implementando conexões SQL resilientes do Entity Framework Core. Essa técnica é importante principalmente ao usar o Banco de Dados SQL do Azure na nuvem.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 59db9cdb894f76f54e77732be47dc6140a594121
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484680"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implementar conexões SQL resilientes com o Entity Framework Core

Para o BD SQL do Azure, o Entity Framework Core já fornece resiliência interna de conexão de banco de dados e lógica de repetição. Mas será necessário habilitar a estratégia de execução de Entity Framework para cada conexão DbContext se desejar ter [conexões do EF Core resilientes](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).

Por exemplo, o código a seguir no nível de conexão do EF Core permite conexões SQL resilientes que serão repetidas se a conexão falhar.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Estratégias de execução e transações explícitas que usam BeginTransaction e várias DbContexts

Quando as repetições estão habilitadas nas conexões do EF Core, cada operação executada que usa o EF Core se torna sua própria operação repetível. Cada consulta e cada chamada a SaveChanges serão repetidas como uma unidade se ocorrer uma falha temporária.

No entanto, se seu código iniciar uma transação usando BeginTransaction, você estará definindo seu próprio grupo de operações que precisam ser tratadas como uma unidade – tudo dentro da transação precisará ser revertido se ocorrer uma falha. Você verá uma exceção como a seguinte se tentar executar essa transação ao usar uma estratégia de execução do EF (política de repetição) e incluirá várias chamadas SaveChanges de várias DbContexts na transação.

> System.InvalidOperationException: a estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não dá suporte a transações iniciadas pelo usuário. Use a estratégia de execução retornada por 'DbContext.Database.CreateExecutionStrategy()' para executar todas as operações na transação como uma unidade repetível.

A solução é invocar manualmente a estratégia de execução do EF com um delegado que representa tudo que precisa ser executado. Se ocorrer uma falha temporária, a estratégia de execução invocará o delegado novamente. Por exemplo, o código a seguir mostra como ele é implementado em eShopOnContainers com duas DbContexts múltiplas (\_catalogContext e o IntegrationEventLogContext) ao atualizar um produto e salvar o objeto ProductPriceChangedIntegrationEvent, que precisa usar uma DbContext diferente.

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

A primeira DbContext é \_catalogContext e a segunda DbContext está dentro do objeto \_integrationEventLogService. A ação de confirmação é executada em DbContexts múltiplos usando uma estratégia de execução do EF.

## <a name="additional-resources"></a>Recursos adicionais

-   **Resiliência de conexão do EF** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)

-   **Resiliência de conexão e interceptação de comando com o Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)

-   **Cesar de la Torre. Usando conexões e transações SQL resilientes do Entity Framework Core**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
[Anterior](implement-retries-exponential-backoff.md)
[Próximo](explore-custom-http-call-retries-exponential-backoff.md)

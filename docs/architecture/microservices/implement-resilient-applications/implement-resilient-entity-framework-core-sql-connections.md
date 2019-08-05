---
title: Implementar conexões SQL resilientes com o Entity Framework Core
description: Saiba como implementar conexões SQL resilientes com o Entity Framework Core. Essa técnica é importante principalmente ao usar o Banco de Dados SQL do Azure na nuvem.
ms.date: 10/16/2018
ms.openlocfilehash: 3bf5c1827cee1da69aeccdc9f15573c301fc9363
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674553"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a>Implementar conexões SQL resilientes com o Entity Framework Core

Para o BD SQL do Azure, o EF (Entity Framework) Core já fornece a lógica interna de resiliência e repetição de conexão de banco de dados. Mas você precisará habilitar a estratégia de execução do Entity Framework para cada conexão de <xref:Microsoft.EntityFrameworkCore.DbContext>, caso deseje [conexões resilientes do EF Core](/ef/core/miscellaneous/connection-resiliency).

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

Quando novas tentativas são habilitadas em conexões do EF Core, cada operação executada que usa o EF Core se torna sua própria operação repetível. Cada consulta e cada chamada para `SaveChanges` serão repetidas como uma unidade se ocorrer uma falha transitória.

No entanto, se seu código iniciar uma transação usando `BeginTransaction`, você estará definindo seu próprio grupo de operações que precisam ser tratadas como uma unidade. Tudo dentro da transação deverá ser revertido se ocorrer uma falha.

Ao tentar executar essa transação usando uma estratégia de execução do EF (política de repetição) e chamando `SaveChanges` de vários DbContexts, você receberá uma exceção como esta:

> System.InvalidOperationException: A estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não é compatível com transações iniciadas pelo usuário. Use a estratégia de execução retornada por 'DbContext.Database.CreateExecutionStrategy()' para executar todas as operações na transação como uma unidade repetível.

A solução é invocar manualmente a estratégia de execução do EF com um delegado que representa tudo que precisa ser executado. Se ocorrer uma falha temporária, a estratégia de execução invocará o delegado novamente. Por exemplo, o código a seguir mostra como ela é implementada no eShopOnContainers com dois DbContexts múltiplos (\_catalogContext e o IntegrationEventLogContext) ao atualizar um produto e salvar o objeto ProductPriceChangedIntegrationEvent, que precisa usar um DbContext diferente.

```csharp
public async Task<IActionResult> UpdateProduct(
    [FromBody]CatalogItem productToUpdate)
{
    // Other code ...

    var oldPrice = catalogItem.Price;
    var raiseProductPriceChangedEvent = oldPrice != productToUpdate.Price;

    // Update current product
    catalogItem = productToUpdate;

    // Save product's data and publish integration event through the Event Bus
    // if price has changed
    if (raiseProductPriceChangedEvent)
    {
        //Create Integration Event to be published through the Event Bus
        var priceChangedEvent = new ProductPriceChangedIntegrationEvent(
          catalogItem.Id, productToUpdate.Price, oldPrice);

       // Achieving atomicity between original Catalog database operation and the
       // IntegrationEventLog thanks to a local transaction
       await _catalogIntegrationEventService.SaveEventAndCatalogContextChangesAsync(
           priceChangedEvent);

       // Publish through the Event Bus and mark the saved event as published
       await _catalogIntegrationEventService.PublishThroughEventBusAsync(
           priceChangedEvent);
    }
    // Just save the updated product because the Product's Price hasn't changed.
    else
    {
        await _catalogContext.SaveChangesAsync();
    }
}
```

O primeiro <xref:Microsoft.EntityFrameworkCore.DbContext> é `_catalogContext` e o segundo `DbContext` está dentro do objeto `_integrationEventLogService`. A ação de confirmação é executada em todos os objetos `DbContext` usando uma estratégia de execução do EF.

Para atingir essa confirmação de `DbContext` múltipla, o `SaveEventAndCatalogContextChangesAsync` usa uma classe `ResilientTransaction`, como mostra o código a seguir:

```csharp
public class CatalogIntegrationEventService : ICatalogIntegrationEventService
{
    //…
    public async Task SaveEventAndCatalogContextChangesAsync(
        IntegrationEvent evt)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        await ResilientTransaction.New(_catalogContext).ExecuteAsync(async () =>
        {
            // Achieving atomicity between original catalog database 
            // operation and the IntegrationEventLog thanks to a local transaction
            await _catalogContext.SaveChangesAsync();
            await _eventLogService.SaveEventAsync(evt,
                _catalogContext.Database.CurrentTransaction.GetDbTransaction());
        });
    }
}
```

O método `ResilientTransaction.ExecuteAsync` começa basicamente uma transação usando o `DbContext` passado (`_catalogContext`) e, em seguida, faz com que o `EventLogService` use essa transação para salvar as alterações do `IntegrationEventLogContext` e, em seguida, confirmar a transação inteira.

```csharp
public class ResilientTransaction
{
    private DbContext _context;
    private ResilientTransaction(DbContext context) =>
        _context = context ?? throw new ArgumentNullException(nameof(context));

    public static ResilientTransaction New (DbContext context) =>
        new ResilientTransaction(context);

    public async Task ExecuteAsync(Func<Task> action)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts 
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        var strategy = _context.Database.CreateExecutionStrategy();
        await strategy.ExecuteAsync(async () =>
        {
            using (var transaction = _context.Database.BeginTransaction())
            {
                await action();
                transaction.Commit();
            }
        });
    }
}
```

## <a name="additional-resources"></a>Recursos adicionais

- **Resiliência de conexão e interceptação de comando com o EF em um aplicativo MVC do ASP.NET** \
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- **Cesar de la Torre. Usando conexões e transações SQL resilientes do Entity Framework Core** \
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
>[Anterior](implement-retries-exponential-backoff.md)
>[Próximo](explore-custom-http-call-retries-exponential-backoff.md)

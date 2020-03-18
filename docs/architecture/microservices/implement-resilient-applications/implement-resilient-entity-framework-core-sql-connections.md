---
title: Implementar conexões SQL resilientes com o Entity Framework Core
description: Saiba como implementar conexões SQL resilientes com o Entity Framework Core. Essa técnica é importante principalmente ao usar o Banco de Dados SQL do Azure na nuvem.
ms.date: 10/16/2018
ms.openlocfilehash: 7a047edca21d63a451e90f407b23f3358d461330
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78241059"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="54cfa-104">Implementar conexões SQL resilientes com o Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="54cfa-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="54cfa-105">Para o BD SQL do Azure, o EF (Entity Framework) Core já fornece a lógica interna de resiliência e repetição de conexão de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="54cfa-105">For Azure SQL DB, Entity Framework (EF) Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="54cfa-106">Mas você precisará habilitar a estratégia de execução do Entity Framework para cada conexão de <xref:Microsoft.EntityFrameworkCore.DbContext>, caso deseje [conexões resilientes do EF Core](/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="54cfa-106">But you need to enable the Entity Framework execution strategy for each <xref:Microsoft.EntityFrameworkCore.DbContext> connection if you want to have [resilient EF Core connections](/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="54cfa-107">Por exemplo, o código a seguir no nível de conexão do EF Core permite conexões SQL resilientes que serão repetidas se a conexão falhar.</span><span class="sxs-lookup"><span data-stu-id="54cfa-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="54cfa-108">Estratégias de execução e transações explícitas que usam BeginTransaction e várias DbContexts</span><span class="sxs-lookup"><span data-stu-id="54cfa-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="54cfa-109">Quando as repetições estão habilitadas nas conexões do EF Core, cada operação executada que usa o EF Core se torna sua própria operação repetível.</span><span class="sxs-lookup"><span data-stu-id="54cfa-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="54cfa-110">Cada consulta e cada chamada para `SaveChanges` serão repetidas como uma unidade se ocorrer uma falha transitória.</span><span class="sxs-lookup"><span data-stu-id="54cfa-110">Each query and each call to `SaveChanges` will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="54cfa-111">No entanto, se seu código iniciar uma transação usando `BeginTransaction`, você estará definindo seu próprio grupo de operações que precisam ser tratadas como uma unidade.</span><span class="sxs-lookup"><span data-stu-id="54cfa-111">However, if your code initiates a transaction using `BeginTransaction`, you're defining your own group of operations that need to be treated as a unit.</span></span> <span data-ttu-id="54cfa-112">Tudo dentro da transação deverá ser revertido se ocorrer uma falha.</span><span class="sxs-lookup"><span data-stu-id="54cfa-112">Everything inside the transaction has to be rolled back if a failure occurs.</span></span>

<span data-ttu-id="54cfa-113">Ao tentar executar essa transação usando uma estratégia de execução do EF (política de repetição) e chamando `SaveChanges` de vários DbContexts, você receberá uma exceção como esta:</span><span class="sxs-lookup"><span data-stu-id="54cfa-113">If you try to execute that transaction when using an EF execution strategy (retry policy) and you call `SaveChanges` from multiple DbContexts, you'll get an exception like this one:</span></span>

> <span data-ttu-id="54cfa-114">System.InvalidOperationException: a estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não dá suporte a transações iniciadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="54cfa-114">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="54cfa-115">Use a estratégia de execução retornada por 'DbContext.Database.CreateExecutionStrategy()' para executar todas as operações na transação como uma unidade repetível.</span><span class="sxs-lookup"><span data-stu-id="54cfa-115">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="54cfa-116">A solução é invocar manualmente a estratégia de execução do EF com um delegado que representa tudo que precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="54cfa-116">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="54cfa-117">Se ocorrer uma falha transitória, a estratégia de execução invocará o representante novamente.</span><span class="sxs-lookup"><span data-stu-id="54cfa-117">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="54cfa-118">Por exemplo, o código a seguir mostra como ela é implementada no eShopOnContainers com dois DbContexts múltiplos (\_catalogContext e o IntegrationEventLogContext) ao atualizar um produto e salvar o objeto ProductPriceChangedIntegrationEvent, que precisa usar um DbContext diferente.</span><span class="sxs-lookup"><span data-stu-id="54cfa-118">For example, the following code show how it's implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="54cfa-119">O primeiro <xref:Microsoft.EntityFrameworkCore.DbContext> é `_catalogContext` e o segundo `DbContext` está dentro do objeto `_catalogIntegrationEventService`.</span><span class="sxs-lookup"><span data-stu-id="54cfa-119">The first <xref:Microsoft.EntityFrameworkCore.DbContext> is `_catalogContext` and the second `DbContext` is within the `_catalogIntegrationEventService` object.</span></span> <span data-ttu-id="54cfa-120">A ação de confirmação é executada em todos os objetos `DbContext` usando uma estratégia de execução do EF.</span><span class="sxs-lookup"><span data-stu-id="54cfa-120">The Commit action is performed across all `DbContext` objects using an EF execution strategy.</span></span>

<span data-ttu-id="54cfa-121">Para atingir essa confirmação de `DbContext` múltipla, o `SaveEventAndCatalogContextChangesAsync` usa uma classe `ResilientTransaction`, como mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="54cfa-121">To achieve this multiple `DbContext` commit, the `SaveEventAndCatalogContextChangesAsync` uses a `ResilientTransaction` class, as shown in the following code:</span></span>

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

<span data-ttu-id="54cfa-122">O método `ResilientTransaction.ExecuteAsync` começa basicamente uma transação usando o `DbContext` passado (`_catalogContext`) e, em seguida, faz com que o `EventLogService` use essa transação para salvar as alterações do `IntegrationEventLogContext` e, em seguida, confirmar a transação inteira.</span><span class="sxs-lookup"><span data-stu-id="54cfa-122">The `ResilientTransaction.ExecuteAsync` method basically begins a transaction from the passed `DbContext` (`_catalogContext`) and then makes the `EventLogService` use that transaction to save changes from the `IntegrationEventLogContext` and then commits the whole transaction.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="54cfa-123">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="54cfa-123">Additional resources</span></span>

- <span data-ttu-id="54cfa-124">**Resiliência de conexão e interceptação de comando com EF em uma aplicação mvc ASP.NET** </span><span class="sxs-lookup"><span data-stu-id="54cfa-124">**Connection Resiliency and Command Interception with EF in an ASP.NET MVC Application** </span></span>\
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- <span data-ttu-id="54cfa-125">**Cesar de la Torre. Usando conexões e transações sql do núcleo do framework da entidade resiliente** </span><span class="sxs-lookup"><span data-stu-id="54cfa-125">**Cesar de la Torre. Using Resilient Entity Framework Core SQL Connections and Transactions** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
><span data-ttu-id="54cfa-126">[Próximo](implement-retries-exponential-backoff.md)
>[anterior](use-httpclientfactory-to-implement-resilient-http-requests.md)</span><span class="sxs-lookup"><span data-stu-id="54cfa-126">[Previous](implement-retries-exponential-backoff.md)
[Next](use-httpclientfactory-to-implement-resilient-http-requests.md)</span></span>

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
# <a name="implementing-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="fb9e0-104">Implementando conexões Entity Framework Core SQL</span><span class="sxs-lookup"><span data-stu-id="fb9e0-104">Implementing resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="fb9e0-105">Para o Azure SQL DB, Entity Framework Core já fornece lógica de resiliência e repetição de conexão de banco de dados interno.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-105">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="fb9e0-106">Mas você precisa habilitar a estratégia de execução de Entity Framework para cada conexão DbContext, se você quiser ter [conexões EF Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span><span class="sxs-lookup"><span data-stu-id="fb9e0-106">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="fb9e0-107">Por exemplo, o código a seguir no nível de conexão do EF Core permite conexões de SQL que são repetidas se a conexão falhar.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="fb9e0-108">Estratégias de execução e transações explícitas usando BeginTransaction e vários DbContexts</span><span class="sxs-lookup"><span data-stu-id="fb9e0-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="fb9e0-109">Quando novas tentativas são habilitadas em conexões EF Core, cada operação que você executar usando EF principal se torna sua própria operação repetível.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="fb9e0-110">Cada chamada para SaveChanges e cada consulta serão repetidas como uma unidade se ocorrer uma falha temporária.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-110">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="fb9e0-111">No entanto, se seu código inicia uma transação usando BeginTransaction, você está definindo seu próprio grupo de operações que precisam ser tratados como uma unidade — tudo dentro da transação ser revertida se ocorrer uma falha.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-111">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="fb9e0-112">Se você tentar executar a transação ao usar uma estratégia de execução EF (política de repetição) e incluir várias chamadas SaveChanges de vários DbContexts na transação, você verá uma exceção semelhante ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-112">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="fb9e0-113">System. InvalidOperationException: A estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não oferece suporte a transações iniciadas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-113">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="fb9e0-114">Use a estratégia de execução retornada por 'DbContext.Database.CreateExecutionStrategy()' para executar todas as operações na transação como uma unidade repetível.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-114">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="fb9e0-115">A solução é chamar a estratégia de execução EF manualmente com um delegado que representa tudo o que precisa ser executada.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-115">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="fb9e0-116">Se ocorrer uma falha transitória, a estratégia de execução invocará o representante novamente.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-116">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="fb9e0-117">Por exemplo, o código a seguir mostram como é implementado em eShopOnContainers com dois DbContexts vários (\_catalogContext e o IntegrationEventLogContext) ao atualizar um produto e, em seguida, salvar o Objeto ProductPriceChangedIntegrationEvent, que precisa usar um DbContext diferente.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-117">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

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

<span data-ttu-id="fb9e0-118">É o primeiro DbContext \_catalogContext e o segundo DbContext está dentro do \_integrationEventLogService objeto.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-118">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="fb9e0-119">A ação de confirmação é executada em vários DbContexts usando uma estratégia de execução EF.</span><span class="sxs-lookup"><span data-stu-id="fb9e0-119">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fb9e0-120">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="fb9e0-120">Additional resources</span></span>

-   <span data-ttu-id="fb9e0-121">**Resiliência de Conexão e interceptação de comando com o Entity Framework**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="fb9e0-121">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="fb9e0-122">**Cesar de la Torre. Usando transações e conexões do Sql resiliente Entity Framework Core**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="fb9e0-122">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>


>[!div class="step-by-step"]
<span data-ttu-id="fb9e0-123">[Anterior] (implementar-tentativas-exponencial-backoff.md) [Avançar] (implement-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="fb9e0-123">[Previous] (implement-retries-exponential-backoff.md) [Next] (implement-custom-http-call-retries-exponential-backoff.md)</span></span>
